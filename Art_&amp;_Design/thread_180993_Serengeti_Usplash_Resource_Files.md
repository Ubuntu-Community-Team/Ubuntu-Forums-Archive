---
title: "Serengeti Usplash Resource Files"
date: 2006-05-23
forum: Art &amp; Design
---

### Post by j_baer on 2006-05-23
**Background:**

I used Inkscape to build the base Usplash image. The form is
divided into three sections, export image, pallet, and 
usplash context.

**Pallet:**

I built a GIMP pallet from the pallet section of my form. The
attached serengeti_color16.gpl files is an example. This file
must be copied to GIMP pallet directory /usr/share/inkscape/palettes.
The columns are R G B and RGBA codes for each color. I pulled
them form the Inkscape Object > Fill and Stroke section. Be sure
to select the RGB tab.

**Convert Image:**

Export the image from Inkscape (top of form) and convert using GIMP. 
Load the image in GIMP and select Image > Mode > Index from menu. 
Select customer pallet and choose <your> pallet. Experiment with the
other options and then save.

**Compile and install:**

Once the image is converted, run the install script (see
inst-template.sh). Unassigned integer errors mean your
image was not in 16 colors.

Credit:

[https://wiki.ubuntu.com/USplashCustomizationHowto?highlight=%28usplash%29](https://wiki.ubuntu.com/USplashCustomizationHowto?highlight=%28usplash%29)

Cheers ...

---

