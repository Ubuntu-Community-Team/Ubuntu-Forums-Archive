---
title: "Reinstalled windows, now can't find Ubuntu!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-20
Oh no! I just reinstalled windows (over itself), and now there is no longer that menu when I turn on my computer! It just starts Windows automatically! How can I make it right! I want to be using Ubuntu! (I did not ask it to write over linux so it surely is still there.)
Thank you!
Justin

---

### Post by kepos on 2006-08-20
you hacve to reinstall grub.
i'm not shure how do you do that so someone expirienced should tell you that.
or just google for *'grub reinstall'*

---

### Post by sailor2001 on 2006-08-20
windows formats your whole drive..........you have to install ubuntu AFTER installing windows... Be sure you allow grub for dual boot

---

### Post by kepos on 2006-08-20
> **sailor2001 said:**
> windows formats your whole drive

no, they format only selected partition. so i'm sure that ubuntu is still present somewhere on drive, just reinstall grub and it should work fine.

---

### Post by ajgreeny on 2006-08-20
Yes, I think ubuntu will still be there unless you did the unthinkable and formatted the whole disk not just the windows partition.  To see how to reinstall grub look at this link:-
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)
Good luck!

---

### Post by woodlandjustin on 2006-08-20
> **ajgreeny said:**
> Yes, I think ubuntu will still be there unless you did the unthinkable and formatted the whole disk not just the windows partition.  To see how to reinstall grub look at this link:-
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)
Good luck!

That guide says:
" How to restore GRUB menu after Windows installation
Read #General Notes
Read #How to use Ubuntu Installation CD, to gain root user access
e.g. Assumed that /dev/hda is the location of /boot partition
# grub-install /dev/hda "

Then the refered part says:
" How to use Ubuntu Installation CD, to gain root user access
Read #General Notes
Boot-up computer into Ubuntu Installation CD
At "boot:" prompt, add "rescue" to the argument
boot: rescue
Follow the instructions on screen "


My question is, WHAT boot prompt? When I stick the Ubuntu CD in and turn it on, I get a menu, like "start or install ubuntu", and so on. I see no "boot prompt", nowhere to type anything. I try the option which shows more menus, like "special ways to boot" or something, but whatever I do nothing says "boot prompt".
Where is it? How do I get it?
Thank you!
Justin

---

### Post by Emerzen on 2006-08-20
You should have an option (booting from install CD) to boot into "recovery mode."  If you do, you'll get to a prompt.  It will ask you, which partition to mount as root, select the partition where Ubuntu is installed.  Once that's done and it's brought you to a prompt type:

grub-reinstall /dev/hda (if you have only one hard disk)  If more than one, lemme know, and lemme know if you have SATA or IDE hard drives.

---

### Post by Emerzen on 2006-08-21
It appears that they've changed how to get into recovery mode w/ Dapper.  (I'm not at home, so I'm trying to help you from memory, it's a common problem and easy to fix though).  When you boot your CD, if there's no option to for "rescue/recovery mode", try hitting escape to see if a prompt is brought up.  If that works, just type rescue at the prompt and follow my directions above.

---

### Post by bodhi.zazen on 2006-08-21
This is essy. It is unlikey windows over wrote Ubuntu.

1. Boot the the Ubutnu "live" CD.
2. Re-instal GRUB.
3. Confirm, and edit if needed, Ubuntu_partition/boot/grub/menu.lst

See also:
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

---

### Post by woodlandjustin on 2006-08-21
> **Emerzen said:**
> It appears that they've changed how to get into recovery mode w/ Dapper.  (I'm not at home, so I'm trying to help you from memory, it's a common problem and easy to fix though).  When you boot your CD, if there's no option to for "rescue/recovery mode", try hitting escape to see if a prompt is brought up.  If that works, just type rescue at the prompt and follow my directions above.

I press esc and it says "boot: " and so I type "rescue" and it says someting like "cannot find a kernel named rescue". Sorry that I forgot the precise wording, but it was either that or something sounding just like it.
Thsnk you for you support! Hopefully we can fix this.
Ah and I think I may have only one hard disk physically, but there are hda1, hda2 and hda5. I thin hda1 is windows and maybe hda2 linux and hda5 the linux swap partition? By the way I definitely only asked windows to install itself on hda1 where it was previously.
Thanks!
Justin.

---

### Post by Emerzen on 2006-08-21
#1  There's a way to reinstall GRUB w/ the install/live CD:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29")

I've used this method in the past and it should give you no problem, but if it does let me know where you're stuck.

#2  Download the "alternate CD" for your architecture from Ubuntu.  When you boot from this, it will give you a rescue/recovery mode option (one of the purposes of the disk).  Select rescue.  As it boots, it will ask you to select the partition where your root folder is (this is the partition where Ubuntu is installed), select it (if you're wrong you'll get an error and try a different one).  Once at prompt login as root/sudo.  Type

```
grub-reinstall /dev/hda
```

Reboot.  If you reinstalled Windows to the same partition it was installed on when you originally installed Ubuntu, you should be able to boot to it in the Grub menu.  If not, lemme know how it goes.

---

### Post by woodlandjustin on 2006-08-21
> **Emerzen said:**
> #1  There's a way to reinstall GRUB w/ the install/live CD:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29")

I've used this method in the past and it should give you no problem, but if it does let me know where you're stuck.

#2  Download the "alternate CD" for your architecture from Ubuntu.  When you boot from this, it will give you a rescue/recovery mode option (one of the purposes of the disk).  Select rescue.  As it boots, it will ask you to select the partition where your root folder is (this is the partition where Ubuntu is installed), select it (if you're wrong you'll get an error and try a different one).  Once at prompt login as root/sudo.  Type

```
grub-reinstall /dev/hda
```

Reboot.  If you reinstalled Windows to the same partition it was installed on when you originally installed Ubuntu, you should be able to boot to it in the Grub menu.  If not, lemme know how it goes.



I followed the instructions on the link. I followed these instructions:
"sudo grub

then :

grub> root (<tab>

where <tab> is an actual TAB which returns the hd that grub recognises, in my case hd0 hd1 hd2 "

 and it did this: (when I hit TAB, "hd0" appeared. I went a little off instructions by pressing TAB again and then the "Partition num [...]"appeared. Then you can see me attempting to follow next instruction.
I 

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> root (hd1)

Error 21: Selected disk does not exist

grub> root (hd0)
 Filesystem type unknown, using whole disk

grub> root (hd1)

Error 21: Selected disk does not exist

grub>

---

### Post by woodlandjustin on 2006-08-21
Situation remains unchanged from above. (11 hours no response, getting a little worried!) Thanks :)
Justin

---

### Post by confused57 on 2006-08-21
You can reinstall grub from the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

See the reply by 5-HT for designating which drive and partition to install grub on.

---

### Post by Emerzen on 2006-08-22
Sorry about the delay, I worked a 24 hour shift and went to sleep after.

Try these steps:

instead of root (hd0) -> root (hd0,1)
instead of root (hd0) -> root (sd0)

I'm going to try to reinstall grub here, to jog my memory, while you try this.  The other method I mentioned above is easier, as the alternate CD will automatically mount your root partition if you select the right one.

---

### Post by Emerzen on 2006-08-22
I'm working from the install CD now.  I had the same problem as you.  I used the direction confused57's link points you to, and that worked.  It's a great link by the way.  It's the same procedure, there's one extra command to input, which I won't repeat but the link has it clearly laid out.  Lemme know if it worked or not.  The one problem may be having to add the windows partition to your grub boot menu.

---

### Post by Drakkor on 2006-08-22
Forgot who gets credit for this,but it worked for me:

How to install Grub from a live Ubuntu cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit


That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Good Luck ! :D

---

### Post by woodlandjustin on 2006-08-22
> **confused57 said:**
> You can reinstall grub from the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

See the reply by 5-HT for designating which drive and partition to install grub on.

That did the job. Now all is well once again. Thank you all so much for your help, Emerzen especially.
Best wishes
Justin

---

