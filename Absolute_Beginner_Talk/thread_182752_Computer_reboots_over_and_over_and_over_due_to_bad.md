---
title: "Computer reboots over and over and over due to bad GRUB splash install"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-05-26
How can I boot straight to a command line so that I may remove the line that is causing this issue?  For instance, with Windows you can hit F8 and it'll take you to Safe Mode, Command Line, etc. 

My computer reboots over and over and over at the point of loading the GRUB GUI.  I know what the issue is, I just need to get into the file to roll it back.

Please help!

---

### Post by %hMa@?b&lt;C on 2006-05-26
try the mepis live cd.  it has a grub installer that will fit your needs
mepis.org

---

### Post by Getwild2 on 2006-05-26
[QUOTE=jeffc313]try the mepis live cd.  it has a grub installer that will fit your needs
mepis.org[/QUOTE]
I shouldnt have to reinstall GRUB, I just need a command line so that I can sudo nano my file.

---

### Post by NoUse on 2006-05-26
When grub loads you are prompted to hit "Esc" which will bring up the boot menu.  One of the options there is "Recovery Mode" I think that disables the splash screen and takes you to a console.

A temporary way is the get the boot menu up and highlight the default option and hit "e" you can edit the boot options.  If you delete the splash keyword it won't use splash.

If that solves the problem, you should a) report a bug at launchpad.net
b) turn off splash permenantly by doing the following.

Once you get to a command line open /boot/grub/menu.list and you'll find a line that starts with "kopt="

That is the default options that are added to all new kernels.  Take splash out of that line and then run:
```

sudo dpkg-reconfigure linux-image-`uname -r`

```

That will reconfig all kernels with the new boot options and should disable the splash screen.

---

### Post by Getwild2 on 2006-05-26
[QUOTE=NoUse]When grub loads you are prompted to hit "Esc" which will bring up the boot menu.  One of the options there is "Recovery Mode" I think that disables the splash screen and takes you to a console.

A temporary way is the get the boot menu up and highlight the default option and hit "e" you can edit the boot options.  If you delete the splash keyword it won't use splash.

If that solves the problem, you should a) report a bug at launchpad.net
b) turn off splash permenantly by doing the following.

Once you get to a command line open /boot/grub/menu.list and you'll find a line that starts with "kopt="

That is the default options that are added to all new kernels.  Take splash out of that line and then run:
```

sudo dpkg-reconfigure linux-image-`uname -r`

```

That will reconfig all kernels with the new boot options and should disable the splash screen.[/QUOTE]
Problem is that my PC reboots immediately upon reaching the GRUB menu.  For instance, it even says something about GRUB but it goes away and reboots so fast that you cant catch it.  

I'll try hitting e when I see this and I'll see what happens.  Wish me luck.

Thanks!

---

### Post by Koech on 2006-05-26
Any luck so far?

---

### Post by Getwild2 on 2006-05-26
[QUOTE=Koech]Any luck so far?[/QUOTE]
No, it boots and says GRUB Loading (and something two lines below that I cant catch), then goes to a blinking cursor in the top left of the screen.  If I hit a key, I it will sit there forever.  If I dont hit a key it'll reboot.

I thought maybe I just couldnt SEE the menu so I tried arrow keys, e, lots of things and nada.

---

### Post by NoUse on 2006-05-26
On my breezy box, it says "Grub loading please wait" on the on the line underneith it it counts down from like 2-3 seconds and says press esc to access boot menu.

If you don't see that, when you start your computer just start whacking the esc key and cross your fingers. :-)

---

### Post by Getwild2 on 2006-05-26
[QUOTE=NoUse]On my breezy box, it says "Grub loading please wait" on the on the line underneith it it counts down from like 2-3 seconds and says press esc to access boot menu.

If you don't see that, when you start your computer just start whacking the esc key and cross your fingers. :-)[/QUOTE]
Well I tried that before, and then again just now.  The menu says:

Select boot device.
1. Maxtor (HDD)
2. Sony DVD-RW
3. Floppy
4. SCSI Device

Its tricky because if I hit ESC too many times, the menu just flashes and goes away. 

I'm going to try and boot off of the the CD-ROM.

---

### Post by Getwild2 on 2006-05-26
Well I am able to get to a shell but when I try to nano the /boot/grub/menu.lst file it comes up empty.  When I cd to root and issue ls, I do not see a /boot directory.  Is it because it might be hidden or is it not mounted because I'm not far enough into loading the OS?  

I AM able to reinstall GRUB from CD-ROM, would this fix the problem?  Would it hurt anything else?  

I HAVE to go, my wife is yelling for us to leave.  I will check back later.  Any help you guys can offer would be freaking awesome!  Thanks guys!!

---

### Post by Sef on 2006-05-26
Read this to get an easy way to [Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by catlett on 2006-05-26
Get the Ubuntu live cd (or any live cd but this is ubuntu based instruction)
Boot to the cd. Open the terminal type ```
sudo fdisk -l
``` Find your Ubuntu partition. I am going to use /dev/hda3 as an example.
Now make a directory for the partition to be mounted to, for the example I am goimg to make a folder "ubuntu" in the media folder (I use the media folder because it will put an icon on your desktop). ```
sudo mkdir /media/ubuntu
``` Now mount the partition ```
sudo mount /dev/hda3 -t ext3 /media/ubuntu
```
Now your Ubuntu partition is mounted and you should be able to edit the grub list. You already know how but I'll finish in case someone stunbles upon this thread for help. ```
sudo nano /media/ubuntu/boot/grub/menu.lst
``` All you should have to do is comment out the line with the splashimage and the line for the hiddenmenu but leaving the timeout and default lines. That will leave the menu like a regular text grub menu.

---

### Post by Getwild2 on 2006-05-26
[QUOTE=catlett]Get the Ubuntu live cd (or any live cd but this is ubuntu based instruction)
Boot to the cd. Open the terminal type ```
sudo fdisk -l
``` Find your Ubuntu partition. I am going to use /dev/hda3 as an example.
Now make a directory for the partition to be mounted to, for the example I am goimg to make a folder "ubuntu" in the media folder (I use the media folder because it will put an icon on your desktop). ```
sudo mkdir /media/ubuntu
``` Now mount the partition ```
sudo mount /dev/hda3 -t ext3 /media/ubuntu
```
Now your Ubuntu partition is mounted and you should be able to edit the grub list. You already know how but I'll finish in case someone stunbles upon this thread for help. ```
sudo nano /media/ubuntu/boot/grub/menu.lst
``` All you should have to do is comment out the line with the splashimage and the line for the hiddenmenu but leaving the timeout and default lines. That will leave the menu like a regular text grub menu.[/QUOTE]
Holy freaking crap man, you are a genius!  That worked like a charm!! :p I dont know HOW to thank you, you are the man!  Also thank you also to you other guys who stuck it out with me to get this thing back up and for your suggestions.  You guys are the best!!

Thanks again, so much!!  \\:D/

EDIT: I actually also got my new GRUB splash screen to work.  I included /boot in my splash screen path when I didnt need to because /boot is on its own partition.  GRUB had no clue where to look for the splash image, so it sat at a blank screen.  I also had my / mount entered in wrong so it couldnt find my default kernel.  All is well and it looks MUCH better than that crappy black and white GRUB menu.  

Thanks again!!!  I hope I get where I can help someone else one day.

---

### Post by catlett on 2006-05-27
That's great. I only know it because I messed up my installs and grub so much I had to always fix it. Seems to be a common way to learn linux, trial and error. Anyways glad to help, see you around the forum and  " pay it forward":-D

---

### Post by Getwild2 on 2006-05-27
[QUOTE=catlett]see you around the forum and  " pay it forward":-D[/QUOTE]
Definitely! :mrgreen:

---

### Post by Rohan Kapoor on 2008-04-18
> **Getwild2 said:**
> 
EDIT: I actually also got my new GRUB splash screen to work.  I included /boot in my splash screen path when I didnt need to because /boot is on its own partition.  GRUB had no clue where to look for the splash image, so it sat at a blank screen.  I also had my / mount entered in wrong so it couldnt find my default kernel.  All is well and it looks MUCH better than that crappy black and white GRUB menu. 

Can you or somebody please explain how to do that?

---

