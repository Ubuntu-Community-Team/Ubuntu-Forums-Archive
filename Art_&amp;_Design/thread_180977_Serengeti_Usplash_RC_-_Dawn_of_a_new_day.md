---
title: "Serengeti Usplash RC - Dawn of a new day"
date: 2006-05-23
forum: Art &amp; Design
---

### Post by j_baer on 2006-05-23
**Background:**

The Usplash graphic is constrained by a 16 color pallet which
leads to pixelation. The fancy things such as gradients are not
available. I believe much of the dissatisfaction with the image
to date is a result of this constraint.

In addition, crafting an image in this environment is not easy
and required building a custom pallet to be used by GIMP. 

**Improvements:**

Moved display colors to 256 non dithering web colors. Enlarged
the size of the graphic to further combat pixelation.

Changed layout to come into harmony with the intent of the
theme.

**Symbolism of Design:**

"*Dawn of a new day ...*"

The words and the logo represents the horizon, the logo the
spirit of the community as the sun rising against the dark of
a night sky. The green of the progress bar represents the 
richness and vitality of the community. The brighter status text 
left represents the activity of the community and the muted 
text right the suggestions and advice submitted with respect, 
love, and without prejudice.

*In short, ubuntu serengeti ...*

=======================================
**Installation Re-cap**
=======================================

**HowTo:**

Download the file named **serengeti-usplash.tar.gz** to a local folder
and extract the contents.

[I]* Contents:
inst-serengeti.sh
serengeti-usplash.so[/I]

Run the install script by typing **sudo sh inst-serengeti.sh** <return>.

The script will add the new splash screen to the alternatives list
and present the revised list. Choose serengeti_usplash by entering
the selection number and pressing <return>.

Example (1):  =========================
**Usplash-artwork alternative**
---------------------------

There are 2 alternatives which provide `usplash-artwork.so'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/usplash/usplash-default.so
2 /usr/local/lib/usplash/**serengeti_usplash.so**

Press enter to keep the default[*], or type selection number: <**2**>

=======================================

Next the script will reconfigure the linux image and load gedit in order for
you edit the menu.lst file.

Toward the end of the file is the linux boot lines and you should add the appropriate
vga command as shown below. If you have multiple boot lines the first will do.

- 8bit
vga = 769 for standard
vga = 771 for 800x600
vga = 773 for 1024x768
vga = 775 for 1280x1024

- 15bit
vga = 784 for standard
vga = 787 for 800x600
vga = 790 for 1024x768
vga = 793 for 1280x1024

- 16bit *
vga = 785 for standard
vga = 788 for 800x600
**vga = 791 for 1024x768 ***
vga = 794 for 1280x1024

- 24bit
vga = 786 for standard
vga = 789 for 800x600
vga = 792 for 1024x768
vga = 795 for 1280x1024

Example (2):  =========================
**Menu lst**
------------

title Ubuntu, kernel 2.6.15-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
...

=======================================

Save, exit, reboot, and enjoy!

**Note:** This usplash has been prepared for the 32 bit environment. A 64 bit version
will come shortly.

[I]BTW, for those who want to peek at the boot screen before you load it please see the
mockup png attached. For those who may have forgotten, there is a Serengeti gtk
theme in ubuntu art. [/I]  :)

Cheers ...

---

