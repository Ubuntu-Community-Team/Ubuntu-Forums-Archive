---
title: "delima when booting."
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by N4t1v_U5r on 2006-05-08
I have used [this guide](http://www.pcmech.com/show/os/903/) in helping me successfully install Ubuntu 5.10 on my system. So far, the installation itself has been a huge success. So now that I have the system, it's time to solve the problems I am currently having.

Most of them I'm fairly certain I can figure out for myself, but this one I'm having seems to be confusing me. (since partitioning hard drives was never my strong point.) But I followed the guide to the point on the final partition. When I got to that part, I found that the rest of the free space on my hard drive was "unusable" I guess it's because I put the swap area at the end of the drive, but I would assume the guide would have taken that into account.

But nevertheless, every time I boot, I can no longer access my previous OS. It boots directly into Ubuntu and even when I open the menu by the ESC key, all that is listed is Ubuntu kernel 5.10 (or something along those lines)

Previously my operating system was Fedora Core 5, and I'm interested in running both of these Operating systems at the same time. (I've just started in linux and all, and I'm checking out multiple distributions.)

I'm at a loss, and I've read that the program gparted might help me out. If this is a recommendation of anyone, I might need a guide to use it (unless its simmilar to Partition magic, then I might be able to figure it out on my own.)

---

### Post by lha on 2006-05-09
Ubuntu installer usually detects other os's during install and adds them to grub's menu, so maybe you have overwritten Fedora. Please post the output of 'sudo fdisk -l' and 'cat /etc/fstab'. It'd be easier to help if you gave a bit more info... (To enter those two commands, click Applications->Accessories->Terminal.)

---

### Post by catlett on 2006-05-09
First try editing your grub menu. Open the menu list in a text format we can edit. ```
sudo gedit /boot/grub/menu.lst 
``` Now go down a couple of spaces by hitting enter and enter this 
```
title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1
```
Hit "save" on the window controls and reboot your system. As long as everything is fine when you reboot Grub will display Windows as an option.  Try it and post if there is a problem

!!!Sorry thought you were talking about windows. Obviously that won't work. You can access Fedora the same way. It just takes a little more research. You need to find out what partition Fedore is on and what kernel and initrd you are using. Then you edit it to this generic example ```
title		Linux
root		(hd0,1)
kernel	/vmlinuz root=/dev/hda2 ro
```
You need to put in the fedora specific kernel etc. This is my Debian entry which boots along side of Ubuntu title		```
Debian GNU/Linux, kernel 2.6.15-1-486 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1-486 root=/dev/hda8 ro 
initrd		/boot/initrd.img-2.6.15-1-486
savedefault
boot
```

---

### Post by N4t1v_U5r on 2006-05-09
I appreciate the help.

@Iha

Here is the output from the terminal from the commands

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

@Catlett

I get the jest of what you are suggesting. Although I'm unsure about how to find the information. I guess checking the fedora help forums right?

---

### Post by lha on 2006-05-09
[QUOTE=N4t1v_U5r]I appreciate the help.

@Iha

Here is the output from the terminal from the commands[/QUOTE]

Post also the output of 'sudo fdisk -l', please.

Also, you should take a look at what those partitions that aren't used by Ubuntu contain. I'd recommend you to get Knoppix, a fantastic live cd. When you boot it, it shows all partitions (except swap) on desktop as links and it makes it really easy to browse your hd. You could also do it from Ubuntu, but it is easier to use [Knoppix]("http://www.knoppix.org/") + it is a good idea to have a live cd just in case...

I guess you have two partitions in addition to those that show up in /etc/fstab. If this is the case, you probably don't need to fool around with Knoppix. You want to find out which partition is Fedora's root partition. If fdisk shows partitions sda1 and sda2, one of them is hopefully of type Linux and the other Swap. If not, try the Knoppix stuff I mentioned and post as what you found out.

---

### Post by N4t1v_U5r on 2006-05-09
Oh, I was under the assumtion that sudo fdisk -| brought up the option to use the other command. All that happened after I typed in the command was a > appeared in the next line. Trying it again, nothing happened after about five minutes.

I'll try out Knoppix like you suggested. It probably will come in handy in the future. And originally there was a large partition that was used by Fedora, which I resized to 100Gb, and partitioned the rest to a 130 or so main drive for Ubuntu, and a 3GB swap.

---

### Post by Mustard on 2006-05-09
[QUOTE=N4t1v_U5r]Oh, I was under the assumtion that sudo fdisk -| brought up the option to use the other command. All that happened after I typed in the command was a > appeared in the next line. Trying it again, nothing happened after about five minutes.

I'll try out Knoppix like you suggested. It probably will come in handy in the future. And originally there was a large partition that was used by Fedora, which I resized to 100Gb, and partitioned the rest to a 130 or so main drive for Ubuntu, and a 3GB swap.[/QUOTE]

You entered the command incorrectly it seems. Above you are showing a '|' character after the hyphen. It should be 'l' for Larry.

---

### Post by N4t1v_U5r on 2006-05-09
I see, thank you for that. Here's the output.

```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14       12280    98534677+  83  Linux
/dev/sda3   *       12281       14104    14651280   83  Linux
/dev/sda4           14105       30401   130905652+   5  Extended
/dev/sda5           14105       30026   127893433+  83  Linux
/dev/sda6           30027       30401     3012156   82  Linux swap / Solaris


```

---

### Post by catlett on 2006-05-09
Sorry I went off to work. I'm going into my other computer and getting my grub entry for Fedora FC5. In the meantime, what version of Fedora are you running?  I'll post within the hour with more detailed info.

---

### Post by N4t1v_U5r on 2006-05-09
Thank you for your patience. I was previously running Fedora Core 5.

Um, the latest available. I think 5.02

---

### Post by catlett on 2006-05-09
This is my fedora grub entry
```
title  Fedora Core (2.6.16-1.21111_FC5)
         root  (hd1,6)
         kernel /boot/vmlinuz-2.6.16-1.2111_FC5 ro root=LABEL=two rhgb
         initrd  /boot/initrd-2.6.16-1.2111_FC5.img  
``` 

It appears your fedora boot section is on either sda1 or sda2. So you have to edit grub with an entry pointing grub there. So we have 2 issues to deal with. Finding the right partition and finding which kernel and initrd you have.
The easiest way I can think of is to mount your partitions in Ubuntu so you can see your kernel and iniutrd and if we are real lucky you can copy and paste your grub menu fron fedora into ubuntu.
First we have to make a place for the partitions. Go to the terminal and type ```
sudo mkdir /media/fedora1
sudo mkdir /media/fedora2 

```
Now we need to mount them. To the terminal ```
sudo mount /dev/sda1 -t ext3 /media/fedora1
``` Now the other one ```
sudo mount  /dev/sda2 -t ext3 /media/fedora2
```
If everything went right there should be 2 hard disk icons on your desktop. Double click and open them. We're looking for your fedora install so the right one will have a bunch of folders. If we mounted the right ones there should be a "boot" folder. Open it and you should see the kernel and the initrd. That's where we can get the numbers. But it can be even easier. Open the "grub" folder that's in the "boot" folder. Now open the "menu.lst". This is your old grub menu.
Now go back to the terminal```
 sudo gedit /boot/grub/menu.lst
```
This will bring up your current grub menu. What you want to do is copy and paste the entry from your old menu.lst into your new menu.lst.  
In the new menu.lst hit enter a couple of times to get some space between entries. Go to the old menu.lst. Copy the section with your fedora entry (sometimes grub has a bunch of examples and advice, you don't want to copy that. Look for an entry like mine. the easiest way to tell is don't copy anything with a "#" in front of it.)
Once you copy in the old menu hit save. When you reboot grub will have that entry.
This copy/paste is the easiest way. You could edit my example and copy in your kernel number but there is no need for that.
First thing is to get your other partitions mounted. Do that and post if you have a problem. If you mount and there is nothing in the partition either we mounted the wrong ones or you erased your data. I don't think so because you have other linux partitions besides your Ubuntu.
I hope this wasn't too confusing. Post if something doesn't make sense.

---

### Post by N4t1v_U5r on 2006-05-09
The mounting went flawlessly I believe. Although I do not see a boot folder. There is a Grub folder, and I see two files called initrd-2.6.15-1.2054_FC5smp.img and initrd-2.6.16-1.2111_FC5smp.img

I'm not sure if that helps, but I can't find the old menu lst you mentioned, nor do I quite understand what you mean by the kernel. It would be a file right?

Anyways, here is a screen capture of the information I pulled up. If this is helpful any...

[[IMG]http://img288.imageshack.us/img288/2319/info2qg.th.jpg[/IMG]](http://img288.imageshack.us/my.php?image=info2qg.jpg)

---

### Post by catlett on 2006-05-09
Sorry about that. The kernel is the one that says vmlinuz. It's not a big deal if the menu.lst isn't there. I'm going to type up an entry for you. Just double check about the menu.lst. Double click the "grub" folder and see if it is there.
Be back in a few.

---

### Post by N4t1v_U5r on 2006-05-09
Yes, it's there. I have it open in gedit now. And I've also got an idea for the code, but I wouldn't want to make a mistake at this point...

---

### Post by catlett on 2006-05-09
Alright. Open up your grub menu again. ```
sudo gedit /boot/grub/menu.lst
```
Hit enter a couple of times to get some space betwen entries. Now copy and paste this into the menu.lst.
```
title  Fedora Core (2.6.15-1.2054_FC5)
          root (sd0,0)
          kernel /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=two rhgb quiet
          initrd  /boot/initrd-2.6.15-1.2054_FC5.img
```
This should be right on because I had the same kernel and initrd before my update yesterday. So this is how fedora set up my grub menu with this kernel and initrd.
Hit save in the gedit /boot.grub/menu.lst window. This should be it. Reboot your computer and look for the fedora entry in grub. Highlight it and hit enter, you should boot into fedora. Post if there are problems. 
Your fedora install is there so we can definately get grub to boot into it. Just try this first and we'll take it from there.

---

### Post by catlett on 2006-05-09
Didn't see your post. Look for an entry like my post above. You want to copy and paste by highlighting the text and right clicking to get the menu with the copy selection.
Get the new list open if you don't```
 sudo gedit /boot/grub/menu.lst
```
Hit enter a couple of times to get some space between entries. Right click again and the option of paste will be there. Hit paste and the text will be in the file. That's it. You will have a leter for letter entry for grub from the original grub that booted your computer.
If your still a little leary, post a screen shot of your old grub menu.lst and I'll pulll out the right entry for you.

---

### Post by N4t1v_U5r on 2006-05-09
Well, I did what you said. The option appeared in the GRUB boot menu. However, when I tried to boot to FC5, I got this error message.

```
Booting 'Fedora Core (2.6.15-1.2054_FC5)'
root (sd0, 0)
Error 23: Error while parsing number
press any key to continue...

```

That's all the screen said.

edit: here is the screen info about the GRUB boot options

```

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

title  Fedora Core (2.6.15-1.2054_FC5)
          root (sd0,0)
          kernel /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=two rhgb quiet
          initrd  /boot/initrd-2.6.15-1.2054_FC5.img

```

---

### Post by catlett on 2006-05-09
Did you use my entry or the old entry? It may be the (sd0,0) that is the problem. It may need to be (hd0,0).
Look in your originakl grub list and see if your entry says (hd0,0). Or more importantly see what ir lists in the section ```
root (sd0,0)
```
That may be the issue. If that says root (hd0,0) in your old list then ```
sudo gedit /boot/grub/menu.lst
```
And put in (hd0,0) or whatever is in the original list. I would bet this is the problem.
Not to repeat but go into your /media/fedora1 partition and open the grub folder to get to the grub menu.lst. Look in the list for what it says in root (hd?,?). Open up your new menu list with sudo gedit /boot/grub/menu.lst and change the (sd0,0) with (hd?,?) [meaning replace sd0,0 with the wording in your old menu]
Reboot and see what happens.

---

### Post by N4t1v_U5r on 2006-05-09
Well, the good news is the Error 23 went away... bad news is I have a new error.

```
root (hd0,0)
File system type is ext2fs, partition type 0x83
kernel /boot/Vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL= two rhgb quiet
Error 15: File not found
```

I'm no stranger to file not found, but I'm sure the path you gave me was copied right.

---

### Post by catlett on 2006-05-09
Can you post the old grub/menu.lst.

---

### Post by N4t1v_U5r on 2006-05-09
Sure, although not much has changed.
```

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

title  Fedora Core (2.6.15-1.2054_FC5)
          root (hd0,0)
          kernel /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=two rhgb quiet
          initrd  /boot/initrd-2.6.15-1.2054_FC5.img

```

---

### Post by catlett on 2006-05-09
No, not the menu list that is in ubuntu. The menu list from fedora.
Go into the partition you mounted. Fedora1. Open the "boot" folder. Open the "grub" folder. Double click on the menu.lst.
This is the grub menu from when you had fedora installed. This is the correct path to boot fedora on your computer.
I want to see if you can get into that file and post it here. This way I can compare the entries and see if there is an error on the current menu.

---

### Post by N4t1v_U5r on 2006-05-09
```
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.16-1.2111_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.16-1.2111_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.16-1.2111_FC5smp.img
title Fedora Core (2.6.15-1.2054_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.15-1.2054_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.15-1.2054_FC5smp.img

```

I see, I overlooked that. But anyways, that's everything that isn't surrounded by #s

edit: I might have just figured it out... I'll check to make sure.

---

### Post by catlett on 2006-05-09
Sorry. I had the wrong kernel posted. I think you guessed already. Erase the entry I gave you. Enter this entry you just posted. That should do it. Just take out the menu info to be safe(this tells grub what to look like). It might conflict. Just enter this
```
title Fedora Core (2.6.16-1.2111_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.16-1.2111_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.16-1.2111_FC5smp.img
title Fedora Core (2.6.15-1.2054_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.15-1.2054_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.15-1.2054_FC5smp.img
```

---

### Post by N4t1v_U5r on 2006-05-09
Well, good news is that the Error 15 went away. Bad news is that when the kernel is booting up, this set of errors occurs.

```
Incorrect Metadata area header checksum
Incorrect Metadata area header checksum
Incorrect Metadata area header checksum
unable to find volume group "VolGroup00"
unable to access resume device (/dev/VolGroup00/LogVol01)
mount: could not find filesystem '/dev/root'
setuproot: moving /dev failed: no such file or directory
setuproot: error mounting /proc: no such file or directory
setuproot: error mounting /sys: no such file or directory
switchroot: mount failed: No such file or directory
Kernel Panic - not syncing: Attempted to kill init!
```

The other problems have been more or less understandable, but I have no idea what this is.

edit: Here is what the grub list looks like now...

```

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

title Fedora Core (2.6.16-1.2111_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.16-1.2111_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.16-1.2111_FC5smp.img

title Fedora Core (2.6.15-1.2054_FC5smp)
	root (hd0,0)
	kernel /vmlinuz-2.6.15-1.2054_FC5smp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.15-1.2054_FC5smp.img

```

---

### Post by catlett on 2006-05-09
There is one last thing we can try. I don't know if it will work. What you put in should work. That is the grub entry that booted fedora before.
I'm a bit confused because the files are in the partition. We can see them.
 There is one last thing we can try, if this doesn't work something has happened to the partition.
If this fails I would copy the information out of those partitions into ubuntu. Then if you want re-install fedora.
Anyways this is another entry for grub. It is non-kernel specific. It just sends the system to the partition you specify and it looks for a kernel to boot. So once more  ```
sudo gedit /boot/grub/menu.lst
```
Erase the Fedora entries and enter this in it's place
```
title   Fedora
          rootnoverify (hd0,0)
          chainloader +1
```
That's it for my ideas. I don't understand why the last entry didn't work. 
This should work. If it doesn't I'm stumped. You can search around but I would get anything valuable to you off those partitions you mounted. You can do a reinstall of fedora if you want. Or try booting to the install disk and enter rescue mode. It's up to you.
For now, try this and see what happens.

---

### Post by N4t1v_U5r on 2006-05-09
Nope, Error 13 unrecognized executable format.

... I don't know, but I'm glad I don't have anything valuable on the Fedora partition. I'm going to sleep on it, and then tomorrow after school I'll try clearing the partition with Fedora and reinstalling it.

---

### Post by lha on 2006-05-10
[QUOTE=N4t1v_U5r]Nope, Error 13 unrecognized executable format.

... I don't know, but I'm glad I don't have anything valuable on the Fedora partition. I'm going to sleep on it, and then tomorrow after school I'll try clearing the partition with Fedora and reinstalling it.[/QUOTE]
By looking at your boot options, it seems that Fedora was using lvm. According to [this mail]("http://www.redhat.com/archives/fedora-list/2005-December/msg03227.html"), resizing physical lvm partitions is impossible. So when you resized hda2 to make room for Ubuntu, you probably destroyed Fedora's partitions. Clearing Fedora's partitions and reinstalling it sounds like a good idea to me. When you install Fedora, tell it to install grub into sda0 (the boot sector of first primary partition), not into sda (mbr). Then add
title   Fedora
          rootnoverify (hd0,0)
          chainloader +1
into Ubuntu's grub to make Fedora bootable.

---

### Post by N4t1v_U5r on 2006-05-10
I would like to personally thank both of you who helped me. After a few days, I've finally fixed it. After installing Fedora, I made sure to install grub in the right directory as Iha pointed out, and then copied my entries from Ubuntu onto the new Grub Record. Now I've got a dual boot system that actually works perfectly, with enough free space left over for another operating system. (Although I think I'll take a breather before I make another plunge into a different Operating system)

---

### Post by catlett on 2006-05-10
Glad you're up and running. Believe it or not but you now have a considerable linux portfolio. Debian and Red Hat are 2 big names in linux and you now have 2 very popular distros based on them. Ubuntu being based on Debian and Fedora being based on Red Hat (actually Fedora is the free version of Red Hat which you probably already know).
Plus you have easy access to the window managers that all linux distros use. My Fedora installed gnome,kde and xfce by default, so I assume you have the same. You can also have these in Ubuntu.
 Any other distro is going to run these by default so trying another distro won't be a big change graphically. Some of the more obscure ones go for lightweight managers but KDE and Gnome are the big ones with XFCE being a very popular lightweight window manager.
If you want KDE just ```
 sudo apt-get install kubuntu-desktop
```
Afterwards KDE wil be an option at boot when you hit on sessions.
I never installed XFCE in Ubuntu but I believe it is ```
sudo apt-get install xubuntu-desktop
```
Your thank you is appreciated and you are welcome to any help I can give. I enjoy these forums very much and I enjoy them even more when I can offer someone help. Good luck and post if you have any other issues. 
Best Regards,  Catlett

---

### Post by nanotube on 2006-05-11
well, i just happened upon this thread... and wanted to say catlett, you did a great troubleshooting job. :) (of course, it was lha who correctly spotted the lvm problem, but still...)

---

### Post by catlett on 2006-05-14
Just checked the thread again. Thanks nanotube. That means alot coming from you. You're my personal favorite forum helper. I always learn when you post. Believe it or not helping in the forums is how I have gained the majority of my knowledge. I either learn from another reply to the post or just being involved and loking for answers exposes me to new things.
I totally missed the lvm thing. I didn't know about it at all. But because of this thread I now know to ask if they had lvm before they resized and to be aware that lvm has different properties than other filesystems.
Thanks for the compliment, you made my day.:-D

---

