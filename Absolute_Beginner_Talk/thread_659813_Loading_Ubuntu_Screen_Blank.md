---
title: "Loading Ubuntu Screen Blank"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Loafers on 2008-01-06
I installed Ubuntu without any problems on my Dell Inspiron 6000

However, when I turn on computer and choose to boot to Ubuntu with grub it says loading some stuff then screen goes blank instantly for a while and then login screen appears after a while. This doesn't cause me any problems however I would like to know why it is blank...

Also is it normal for it to take a long time for Ubuntu to load?  Because it seems even longer than windows...

---

### Post by Canto on 2008-01-06
The problem you speak of is probably caused incorrect settings in the usplash.conf file. To get it working you have to do the following:

1. Enter the terminal
```
sudo gedit /etc/usplash.conf
``` 

Change the content to 
[I]#Usplash configuration file
xres=xxxx
yres=xxx[/I]

Where the x's are your current screen resolution. Most probably 1024x768

Save and close usplash.conf

2. Enter the following code in the terminal
```
sudo gedit /boot/grub/menu.lst
```

Locate the section
[PHP]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash[/PHP]

And change it to

[PHP]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
defoptions=vga=791[/PHP]

Save & exit

3. Finaly type
```
sudo update-initramfs -u -k `uname -r`
```



Let me know if this solves your problem

---

### Post by Angus77 on 2008-01-06
It solved mine!

The resolution in my /etc/usplash.conf was 1680x1680.  Is there such a monitor?:???

One thing: can you explain what the defoptions=vga=791 bit was for?  Could I have gotten away with just changing the resolution in /etc/usplash.conf?

---

### Post by Canto on 2008-01-06
> **Angus77 said:**
> 

The resolution in my /etc/usplash.conf was 1680x1680.  Is there such a monitor?:???

If it exists I would like to see it...

> 
One thing: can you explain what the defoptions=vga=791 bit was for?  Could I have gotten away with just changing the resolution in /etc/usplash.conf?

To be honest: no, I believe it's there for a reason though:) Why not google it and post an explanation?

---

### Post by zipperback on 2008-01-06
vga=791  sets your splash screen to 1024x768 in 65k color mode.

- zipperback
:popcorn:

---

### Post by Angus77 on 2008-01-06
Thanks!

Based on that info I searched around and found [here]("http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters&page=6") that if vga=872 I should get 1680x1050 in my usplash.

It ends up displaying exactly the same as when vga=791 --- meaning the image is stretched (although this is infinitely better than a black screen!).

I also tried 799 (which is what I get when I set vga=scan) and it's the same thing.

I talked about it a bit more [here]("http://http://ubuntuforums.org/showthread.php?p=4087216#post4087216").

---

### Post by aonegodman on 2008-01-07
> **Canto said:**
> 
3. Finaly type
```
sudo update-initramfs -u -k `uname -r`
```



Please explain just what this CODE will do before I try it please.

I am trying to correct the same problem on my 7.10 installed on my bootable Ext USB HD.

I am currently working from my LiveCD and making edits to my text files on my HD.

So I guess what I'm asking here, upon explanation of the code, how do I execute it in a terminal on Live session and make it have an effect on my HD? Hope this makes sense to somebody . . . Thanks!  :confused:

---

### Post by erginemr on 2008-01-08
> **aonegodman said:**
> Please explain just what this CODE will do before I try it please.

I am trying to correct the same problem on my 7.10 installed on my bootable Ext USB HD.

I am currently working from my LiveCD and making edits to my text files on my HD.

So I guess what I'm asking here, upon explanation of the code, how do I execute it in a terminal on Live session and make it have an effect on my HD? Hope this makes sense to somebody . . . Thanks!  :confused:

There is nothing wrong with the command that involves "initramfs", while the part "uname -r" is used to get your Linux kernel version. It is used to reflect the changes you have made in "/etc/usplash.conf" to the corresponding boot file that is located inside "/boot". But I know that the following alternative command also does the trick (i.e. has the same effect):
```
sudo dpkg-reconfigure usplash
```

As to your situation, I think the console command "chroot" should be the one you are looking for. It can be used to temporarily change the working root directory to the one you specify as an argument. To check it out, I have booted my system with a "PCLOS Gnome LiveCD" and from there, "chroot"ed to my hard disk as shown in the attachments.

After that point, I believe that the command
```
sudo dpkg-reconfigure usplash
```
should work on your installed system, not on the virtual Live CD environment. Besides, chances are that editing "/etc/usplash.conf" only may also reflect correctly, so you won't have to mess with any other config tools, which was the case in my system in the past.

---

### Post by Chris_Ba on 2008-01-08
New Ubuntu user. I was having the same problem with the splash screen not coming up so I did what is shown above and now my system wont boot up! I have both XP and Ubuntu set up in seperate partitions, when I choose to boot Linux I get a message "[18.734692] Kernel panic-not syncing: VFS: Unable to mount root fs on unknown block (0,0)"
What does this mean and how do I fix it? Thanks!

---

### Post by erginemr on 2008-01-09
> **Chris_Ba said:**
> New Ubuntu user. I was having the same problem with the splash screen not coming up so I did what is shown above and now my system wont boot up! I have both XP and Ubuntu set up in seperate partitions, when I choose to boot Linux I get a message "[18.734692] Kernel panic-not syncing: VFS: Unable to mount root fs on unknown block (0,0)"
What does this mean and how do I fix it? Thanks!

Can you please tell us what you did (commands and config settings) and how you did it (from your installed system or from a live cd)?

---

### Post by shareMenaPeace on 2008-01-09
Please follow this steps to fix this issue with your kernel panicing

[http://ubuntuforums.org/showthread.php?p=3999157](http://ubuntuforums.org/showthread.php?p=3999157)

---

### Post by Chris_Ba on 2008-01-09
> **Canto said:**
> The problem you speak of is probably caused incorrect settings in the usplash.conf file. To get it working you have to do the following:

1. Enter the terminal
```
sudo gedit /etc/usplash.conf
``` 

Change the content to 
[I]#Usplash configuration file
xres=xxxx
yres=xxx[/I]

Where the x's are your current screen resolution. Most probably 1024x768

Save and close usplash.conf

2. Enter the following code in the terminal
```
sudo gedit /boot/grub/menu.lst
```

Locate the section
[PHP]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash[/PHP]

And change it to

[PHP]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
defoptions=vga=791[/PHP]

Save & exit

3. Finaly type
```
sudo update-initramfs -u -k `uname -r`
```



Let me know if this solves your problem



I did exactly what is shown above from an installed system. It doesnt seem I'm able to boot from the Live CD either, it just freezes. Thanks for the link, but it looks like you need to use the Live CD to do most of what is said on those pages.. I'm thinking I should just re-install..

---

### Post by erginemr on 2008-01-09
Hold on! In my /boot folder, there are two relevant files:

```
initrd.img-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
```

So, I believe your system should also have created a backup file during that process. If this is the case, what you need to do is to boot your computer as usual, and when you see Grub menu, to select the item for normal Ubuntu install and press "e" to edit it. Go down to the line with initrd.img-.....-generic, press "e" again to edit it and add ".bak" to the end of the file name. Press "b" to temporarily boot Ubuntu with this setting (do not press Esc or you will lose your edit and will end up with the default options). 

Once (and hopefully) you boot into Ubuntu (provided that you really have a backup file as I do), use the terminal with root privileges (sudo) to go into /boot and replace your initrd file with the backup:
```
cd /boot
sudo mv initrd.img-2.6.22-14-generic.bak initrd.img-2.6.22-14-generic
```

---

### Post by CCBalla10 on 2008-01-10
THANK YOU THANK YOU SOLVED MY G/F's LAPTOP PROBLEM!!!!!!!! :guitar:

---

### Post by ubuntu-freak on 2008-01-10
sudo apt-get install startupmanager

Lets you easily modify usplash and even change the image used. Navigate to system>administration and launch it.

If you have installed Ubuntu on a system with windows on it and usplash hangs, try my guide below. 
 
[http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214)
 
Nathan

---

