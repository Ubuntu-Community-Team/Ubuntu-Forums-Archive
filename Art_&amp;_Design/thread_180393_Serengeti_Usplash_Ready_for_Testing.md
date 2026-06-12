---
title: "Serengeti Usplash Ready for Testing"
date: 2006-05-22
forum: Art &amp; Design
---

### Post by j_baer on 2006-05-22
**Background:**

The Usplash graphic is constrained by a 16 color pallet which
leads to pixelation. The fancy things such as gradients  and
blending are not available. I believe much of the dissatisfaction
with the image to date is a result of this constraint.

In addition, crafting an image in this environment is not easy
and required building a custom pallet to be used by GIMP. I will
post additional details shortly in this forum.

**HowTo:**

Download the file named *serengeti-usplash.tar.gz* to a local folder
and extract the contents.

** Contents:*
inst-serengeti.sh
serengeti-usplash.so

Run the install script by typing **sudo sh inst-serengeti.sh** <return>.

The script will add the new splash screen to the alternatives list
and present the revised list. Choose serengeti_usplash by entering
the selection number and pressing <return>.

Example (1):  
=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=
*Usplash-artwork alternatives*
=================

There are 2 alternatives which provide `usplash-artwork.so'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/usplash/usplash-default.so
2 /usr/local/lib/usplash/**serengeti_usplash.so**

Press enter to keep the default[*], or type selection number: <**2**>

=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=

Next the script will reconfigure the linux image and load gedit in order for
you edit the menu.lst file.

Toward the end of the file is the linux boot lines and you should add the appropriate
vga command as shown below. If you have multiple boot lines the first will do.

vga = 785 for standard vga
vga = 788 for 800x600
**vga = 791 for 1024x768 ***
vga = 794 for 1280x1024

Example (2):
=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=
*Menu lst*
=====

title Ubuntu, kernel 2.6.15-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-386
...

=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=*=

Save, exit, reboot, and enjoy!


BTW, for those who want to peek at the boot screen before you load it please see the
mockup png attached. For those who may have forgotten, there is also a Serengeti gtk 
theme in this forum.

Cheers ...

---

### Post by phorque on 2006-05-22
Looks good. Better than both the official ones I've seen for Dapper.

---

### Post by Mathias-K on 2006-05-22
Overall, it's really nice to see that someone takes a shot at the Ubuntu art - keep going :)

However, I think there are too many different colours in your splash. Why use grey and green when Ubuntu is turning bright orange?

Also I believe the official name is not "ubuntu linux", but just "ubuntu". And it's capital LTS.

I'm all over the new orange dapper, and the new usplash is a marked improvement over the old. How much I think your work is promising, I still prefer the current one.

---

### Post by j_baer on 2006-05-22
Thanks for the reply and the suggestions. 

I'm still not convinced I have the correct solution for the grainy problem. As a proof of concept I created a usplash in greyscale and in some ways it looked sharper.

Unforunately one of the driving factors was comining up with a combination of colors which would hold up.

It's hard to believe but I tried over 60 combinations. :(

For the moment I am going to spend some time researching additional alternatives.

Cheers ...

---

### Post by Mathias-K on 2006-05-23
[QUOTE=j_baer]Thanks for the reply and the suggestions. 

I'm still not convinced I have the correct solution for the grainy problem. As a proof of concept I created a usplash in greyscale and in some ways it looked sharper.

Unforunately one of the driving factors was comining up with a combination of colors which would hold up.

It's hard to believe but I tried over 60 combinations. :(

For the moment I am going to spend some time researching additional alternatives.

Cheers ...[/QUOTE]

I've not tried your splash on my system, but if it has the same level of pixelation as the current one, I think people will still like it :)

---

### Post by pjot on 2006-05-23
If the new logout button only had been Human-ish orange instead of red it would be the perfect Ubuntu logout button! :/

---

### Post by pjot on 2006-05-23
Sorry, posted in the wrong thread :(

---

