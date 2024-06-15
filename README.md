# xCloneCleaner

A fork of https://github.com/artyfacialintelagent/CloneCleaner

An extension for Automatic1111 to work around Stable Diffusion's "clone problem". It automatically modifies your prompts with random names, nationalities, hair style and hair color to create more variations in generated people.

# What it does

Many generations of model finetuning and merging have greatly improved the image quality of Stable Diffusion 1.5 when generating humans - but at the cost of overtraining and loss of variability. This manifests as "clones", where batch generations using the same or similar prompts but different random seeds often have identical facial features.

CloneCleaner adds randomized tokens to your prompt that varies the look of a person for every generated image seed. For example, one seed might get "Elsie from Australia, long waist-length updo ginger hair" and the next "Samreen from Bangladesh, medium shoulder-length frizzy coffee-colored hair". This makes every seed quite unique and effectively mitigates the "sameface" problem of many popular but heavily overtrained Stable Diffusion models. So it's basically wildcards, except the tiresome setup work has been done for you and you're ready to go - with lots of easy customization options to control the randomization.

A key detail is that the token randomization seed is (by default) identical to the main image seed - this ensures that the same "person" will be generated again if you modify the prompt or reload the metadata.

# Changes made in xCloneCleaner

 - renamed to xCloneCleaner - this little change fixes the issues of conflicting with sd-dynamic-prompts since extensions are run in alphabetic order
 - added male option along with male type hairstyles
 - added more hairstyles to female
 - added a random gender option (will use hairstyle according to the randomised gender)

# Upcoming changes

 - updated hair colors
 - add more names
 - add countries not included

# Installation in Automatic1111

Enter this url **manually** in auto1111's extension tab:

https://github.com/troyau/xCloneCleaner.git

# How it works

Prompts are randomized using wildcards, except they're hardcoded in the extension with logic to match ethnicity with typical names and common hair colors for each country, in order to get consistent appearance and quality of the generated images. Main steps:

1. Set the token randomization seed to the main image seed (or optionally a different random seed or a user-specified one).
2. Select a random REGION among the following: Europe (mainland incl. Russia), Anglosphere (US, Can, Aus, NZ, UK), Latin America, MENA (Middle-East & North Africa), Sub-Saharan Africa, East Asia or South Asia.
3. Select a random COUNTRY in that region - but note that CloneCleaner only has a sample of countries of each region, the database is not (yet) comprehensive.
4. Select a random FIRST NAME for people in that country.
5. Select a random MAIN HAIR COLOR (only black, brown, red, blonde, other), weighted for what is typical in that country. Then select a SPECIFIC HAIR COLOR with more "colorful" (sorry) language for more variability. Color tokens are carefully selected and limited using tricks like reduced attention and prompt editing to minimize "color bleeding" into the rest of your prompt.
6. Select random HAIR STYLE and HAIR LENGTH.
7. Assemble the prompt insert: "[FIRST NAME] from [COUNTRY], [HAIR LENGTH] [HAIR STYLE] [SPECIFIC HAIR COLOR] hair". Insert it at beginning or end of the prompt depending on user options
8. Iterate for remaining images of the batch.

Any of the above token components can be optionally excluded from the prompt randomization. There are also customization options to exclude specific regions, hair lengths and hair color.

# Sample images

Coming Soon
