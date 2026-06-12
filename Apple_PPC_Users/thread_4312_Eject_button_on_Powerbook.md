---
title: "Eject button on Powerbook"
date: 2004-11-13
forum: Apple PPC Users
---

### Post by Viro on 2004-11-13
Simple question. How do I get my Powerbook's eject button to work?

---

### Post by TravisNewman on 2004-11-13
[QUOTE=Viro]Simple question. How do I get my Powerbook's eject button to work?[/QUOTE]
 You have to unmount the cd before you can eject the cd. You can either rightclick on the drive icon in "Computer" or on the desktop and choose unmount, or do a "umount /dev/cdrom" from the command line

---

### Post by sumanjay on 2004-11-13
Another technique, which mirrors the way OS X works, is to use the F12 key to unmount and eject the CD. This is very easy to enable, especially since PBButtons is installed by default when installing Ubuntu. PBButtons includes the ability to use the F12 key as well as numerous power-saving options. The following steps should help you get the eject key working-
1) Start **Synaptic**  (Computer->System Configuration->Synaptic) and after entering your password, click on the Search button.
2) Enter powerprefs into the search box and hit Enter.
3) Right click on it and mark it for installation. Hit the Apply button.
4) Once the installation is done, you can run the application by pressing Alt+F2 and typing **powerprefs** into the Run dialog box that appears. Hit Enter, of course.
5) Explore the utility; there quite a number of useful options available. The one you're after is the one with the hard drive icon. Select it and hit the "teach in" button to set the F12 key as your eject key. On my Powerbook Pismo (G3 400MHz), I can simply enter the keyboard code instead, which is 88. Don't forget to apply the changes by hitting the Set button at the bottom.
6) You might find that you need to press the Func key with the F12 key to eject the CD. If you find this tiresome, there is another option you can adjust so that pressing only the F12 key does the job. Go back to Powerprefs and select the tab with the 2 gears on it. Under the **Keyboard Mode** option, select Hotkeys with Fn key. This also has the effect of allowing you to use the F1, F2, F3 and F4 keys. You can still use them to adjust brightness and volume, but you need to hold down the Func key first.

Well, enjoy the results! Cheers!

---

### Post by TravisNewman on 2004-11-13
Slick! I'll be using that on my mac :) I knew of powerprefs, but not what it did.

---

### Post by Viro on 2004-11-14
Thanks. Powerprefs works fine since I was having trouble trying to manually configure /etc/pbbuttonsd.conf

---

### Post by sumanjay on 2004-11-14
No problem! Glad to be of help. Now, if only we had the same breadth of applications available as Gentoo! \\:D/

---

### Post by chascon on 2005-02-16
"You have to unmount the cd before you can eject the cd. You can either rightclick on the drive icon in "Computer" or on the desktop and choose unmount, or do a "umount /dev/cdrom" from the command line"

"eject" in term doe this all for you.
========================
"sumanjay  	No problem! Glad to be of help. Now, if only we had the same breadth of applications available as Gentoo! \\/"

What's that supposed to mean?  The fact "powerprefs" exists as a port means that there is enough breadth of apps.  True, I miss the variety I was used to, but you don't have to go to gentoo to get breadth of apps.  Debian has just as much.  Considering that the sarge installer is almost the same as ubuntu, and that you can print off the xconfig ubuntu set up, one should easily make it thru the debian X setup, thus allowing one to benefit from a extremely stable distro with a plethora of apps, and all with the ease of of "ubuntu" (debian really)  front apps such as synaptic etc (or debian apps some have come to know as ubuntu apps).

Gentoo is fine I sure, but not practical.  Who has the time to build from scratch for minor improvements in speed if any?

---

