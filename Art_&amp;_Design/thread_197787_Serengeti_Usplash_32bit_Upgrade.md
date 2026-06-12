---
title: "Serengeti Usplash 32bit Upgrade"
date: 2006-06-16
forum: Art &amp; Design
---

### Post by j_baer on 2006-06-16
The 061161 version of the serengeti usplash is complete. No major changes to image but more polish added to the 
install script (see attached screenshot).

Change log

1. Converted progress bar to a blue hue from white.
2. Added *sed editing* of the menu.lst file from the script.

**Note:** If you are running @ 800x600 or higher resolution you may consider the
640x480 image (the mockup shows this image). Otherwise please use the 640x400 image.

**To install:** Download the appropriate image and extract contents. Run *sudo sh inst-serengeti.sh* to install.

Enjoy!

*BTW:* Added the serengeti wall paper to the collection to provide start to finish
consistency to the user experience. See this forum for the post.

---

### Post by playmobiel on 2006-06-17
how do i edit the bootscreen with gimp?

---

### Post by rogeriovinhal on 2006-06-17
Is there any way I can change the monitor frequency in the usplash and in the shell ttys? 60Hz is a pain in the eyes...

Just noticed that the shutdown usplash is looking as if it had its colors inverted, like, brown turned to red, and everything looks messed up...

---

### Post by j_baer on 2006-06-18
For those who would like to use serengeti as a starting point to make their own usplash presentation I have attached a kit consisting of four files.

1. serengeti-061061.svg

This is my last revision of the boot splash

2. serengeti_color16.gpl

This is the matching gimp 16 color pallet

3. inst-pallet.sh

A quick script to copy your pallet to the right directory. Run as "*sudo*".

4. serengeti.png

A sample export png file for gimp.

**HowTo:**

Modify the top of the svg to meet your desires. Remember no gradients or 
other fancy stuff. You are limited to 16 colors.

I usually change the middle part to reflect my pallet just to keep me honest but it is not required. 
The lower part of the svg form is my work space for the text and progress bar. 
The only important thing is the colors.

When complete, select the top portion and choose export image from inkscape. Your exported image should be a 640x480 @96dpi png. 

Save ...

Open the gimp pallet file (gedit or your fav editor) and adjust the entries to match the colors you used.
I let inkscape help me with this by clicking Object > Fill and Stroke and the RGB tab.
You can have less than 16 colors but not more. In the event you do have less than 16 colors, just fill in the holes with other colors.

Save this file and copy to the appropriate gimp directory. Use my script if you are unsure.

Load your exported png into gimp and select image > mode > indexed.

Select Custom Pallet and then your pallet (name of pallet file) from the list.
I did not use Color dithering. Click <ok>

If your image turns funky, something went wrong with your pallet file. 
Otherwise you should save your image and exit.

Now you have a product which can be used to customize your usplash as
explained in the USplash Customization Howto wiki.

Good luck and have fun ...

BTW: The wiki guide identifies the pallet colors used by usplash. (0,1,2,4,8,13) are important and 
I have marked with a # on the svg file. Colors marked with an * are a reminder to me that I have 
used the color in the image.

---

### Post by zammi on 2006-06-19
Thank you for the great boot splash... I like to have a  Grub splash (Wallpaper for grub menu) as well. Any idea of extending this project to give us a grub splash as well (maintaining the consistancy from Grub screen on ward).

Example: [http://www.gnome-look.org/content/show.php?content=32976](http://www.gnome-look.org/content/show.php?content=32976)

---

### Post by rogeriovinhal on 2006-06-19
At rebooting or shutting down, the usplash colors look inverted somehow with the serengetti's usplash theme.

---

### Post by j_baer on 2006-06-20
[QUOTE=zammi]Thank you for the great boot splash... I like to have a  Grub splash (Wallpaper for grub menu) as well. Any idea of extending this project to give us a grub splash as well (maintaining the consistancy from Grub screen on ward).

Example: [http://www.gnome-look.org/content/show.php?content=32976](http://www.gnome-look.org/content/show.php?content=32976)[/QUOTE]

I believe the attached png will convert to the correct xpm grub boot splash image.

Give it a try and let us know ...

:)

---

### Post by Trespasser on 2006-06-20
j_baer,
I really enjoy your usplash creations. I have a question...your sh scripts are geared toward linux-images...what can I change for it to work with kernel-images? 

Thank you.

---

### Post by rogeriovinhal on 2006-06-21
I just edited the sh and replaced "linux-image" with "kernel-image" and it worked.

---

### Post by j_baer on 2006-06-21
[QUOTE=rogeriovinhal]I just edited the sh and replaced "linux-image" with "kernel-image" and it worked.[/QUOTE]

Wow,

Help me out. What is the difference?

:)

---

### Post by domino on 2006-06-22
[QUOTE=zammi]Thank you for the great boot splash... I like to have a  Grub splash (Wallpaper for grub menu) as well. Any idea of extending this project to give us a grub splash as well (maintaining the consistancy from Grub screen on ward).

Example: [http://www.gnome-look.org/content/show.php?content=32976](http://www.gnome-look.org/content/show.php?content=32976)[/QUOTE]
One way you can do it is to sudo copy the usplash.xpm.gz to the /boot/grub directory then edit your menu.lst. Copy what's in red and paste it just under the commented password topsecret line. Don't forget to change the (hd0,2) to reflect your disk configuration.

# password topsecret
[COLOR="Red"]splashimage=(hd0,2)/grub/usplash.xpm.gz [/COLOR]

Does anyone have a grub splashimage and usplash that compliments clear looks human blue theme? :cool:

---

### Post by rogeriovinhal on 2006-06-23
[QUOTE=j_baer]Wow,

Help me out. What is the difference?

:)[/QUOTE]

If you compile a custom kernel of your own, the package is named "kernel-image-<version>" instead of "linux-image-<version>", so, if you compile your own kernel, it is necessary to do this change on your script. :)

---

### Post by j_baer on 2006-06-24
[QUOTE=rogeriovinhal]If you compile a custom kernel of your own, the package is named "kernel-image-<version>" instead of "linux-image-<version>", so, if you compile your own kernel, it is necessary to do this change on your script. :)[/QUOTE]

rogeriovinhal,

Thanks for the info ...

---

