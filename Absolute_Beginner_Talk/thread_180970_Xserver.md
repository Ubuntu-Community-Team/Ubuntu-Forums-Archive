---
title: "Xserver"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by johanhartman on 2006-05-23
A few days ago I installed Linux. Amazingly the installation went without a glitch, but there is just one problem. When I first booted into ubuntu the modules loaded and after that the screen just went blank and the PC idled, since I didn't know what the monitor was supposed to display I didn't know whether the login screen was loaded or not. I asked around on the forum about this ([http://www.ubuntuforums.org/showthread.php?t=180111]("http://www.ubuntuforums.org/showthread.php?t=180111")) and someone said that I could try reconfiguring the xserver. I gues I didn't do it right 'cause now everytime I boot into ubuntu I get a message after the modules load saying that the xserver is configured incorrectly. Being a noob an' all I have absolutely no idea how to fix this, so any help will be greatly appreciated.

---

### Post by nalmeth on 2006-05-23
The command for reconfiguring X:
hit cntl-alt-F2 to get to virtual terminal
sudo dpkg-reconfigure xserver-xorg
Try the VESA video driver if the default's seem to fail.

---

### Post by Koech on 2006-05-23
You can kill x by ctrl+alt+backspace then you get a text login. Login and type:
   [COLOR="Blue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
change your driver to 'vesa' it should work.

---

### Post by johanhartman on 2006-05-23
Thanks for the replies, I have not tried them yet though. I just thought that I might add that when I first reconfigured the xserver, the xserver driver was set to "i810" by default, and I tried changing it to "ati".

I have an Intell display adapter.

---

### Post by nalmeth on 2006-05-23
Yeah, that would bork the Xserver, as the ati driver is for ATI video cards.
The iSeries drivers (i810, i710, whatever) are for intel video cards. 
The intel video should be working, but for the time being use VESA. When you want 3D acceleration, well we'll jump that bridge when we get to it. :)

---

### Post by johanhartman on 2006-05-23
Yeah that would make sense.. ](*,) .Ill try "vesa" in a min.

---

### Post by johanhartman on 2006-05-23
I tried using vesa. This kind of worked. Now when i boot it doesn't show the error screen but it goes blank again, I suppose this means its not my xserver driver that was wrong in the first place. 

Any suggestions on what the real problem could be and how to fix it?

---

### Post by Koech on 2006-05-23
Maybe you could try and check the /var/log/Xorg.0.log. Pay particular attention to the lines starting with EE, they indicate where the errors occured. I'll not be available for a while but you can post it someone else will look at it.

---

### Post by johanhartman on 2006-05-24
How do I check this. Also someone in the thread linked in the first post of this thread mentioned something about *tty*, I have noticed that when I boot it says that it is running on *tty1*. Would this have anything to do with my problem?

---

### Post by nalmeth on 2006-05-24
to view the contents of /var/log/Xorg.0.log, enter this:
```
cat /var/log/Xorg.0.log
``` cat is a command that will display contents of a text file.
I believe tty1 will be one of your devices or something. I can't say it's not related to the problem, but I can't see any reason why either :\

---

### Post by johanhartman on 2006-05-25
If this would be helpful here is a link with my PC's specs

[http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_SCALEO_L__5613220]("http://www.ciao.co.uk/Productinformation/Fujitsu_Siemens_SCALEO_L__5613220")

---

### Post by johanhartman on 2006-05-25
[QUOTE=nalmeth]to view the contents of /var/log/Xorg.0.log, enter this:
```
cat /var/log/Xorg.0.log
``` cat is a command that will display contents of a text file.
I believe tty1 will be one of your devices or something. I can't say it's not related to the problem, but I can't see any reason why either :\[/QUOTE]

I've run that command but I don't know how to scroll through the results ](*,)  the only results I can see are the last ones (which I can see are not relavant)

---

### Post by johanhartman on 2006-05-25
My graphics card chipset is Intel 845GE, would this be the cause of the problem since i can see no xserver drivers for it.
Does ubuntu 5.10 support this chipset?

---

### Post by johanhartman on 2006-05-25
If driver support is the problem then I can easily sort it out by downloading the correct driver from [http://www.intel.com/support/chipsets/sb/cs-009236.htm]("http://www.intel.com/support/chipsets/sb/cs-009236.htm"). Only problem would be that i wouldn't know how to install it on a partially working ubuntu??

---

### Post by johanhartman on 2006-05-26
Bump...
Please help!

---

### Post by ifokkema on 2006-05-26
[QUOTE=johanhartman]I've run that command but I don't know how to scroll through the results ](*,)  the only results I can see are the last ones (which I can see are not relavant)[/QUOTE]

Hi,

cat is only useful for short files, 'cause it dumps the output of the file to your console.

Try 'less', which allows you to scroll through the text using your arrow keys. Quit using 'q'.
```
less /var/log/Xorg.0.log
```

Do you happen to have two screen outputs on your video card? Maybe the wrong one is selected?

Ivo

---

### Post by johanhartman on 2006-09-25
Its been a long while since I've touched Ubuntu,but not too long ago I tried a live CD for Dapper Drake and it gave exactly the same problem as with Breezy. I am now thinking of increasing the memory for the graphics card through BIOS in a last desperate attemt to make Ubuntu work. Can someone therefore please advise me on:

[LIST=1]
[*]How much I would need to increase the memory to.
[*]Where exactly to do this and;
[*]How it will affect my PC other than making ubuntu work.
[/LIST]

If you need the current specifications of my PC there is a link to it in one my posts in this thread.

---

### Post by ifokkema on 2006-09-25
Before you try to put more memory to your video card,
- Did you eventually try the i810 driver again? Or just Vesa?
- Did you check the contents of the X log file, as mentioned above? If yes, what did you see? If no, check that first. If you don't get the logfile, no problem, just post it here.

Ivo

---

### Post by johanhartman on 2006-09-26
I tried both i810 and vesa... no luck.
I checked the log file though i didn't see anything that could be graphics related, i would post the log file if I knew how to transfer it without typing up the whole thing... maybe if you could tell me what exactly to look for I can post that.

---

### Post by ifokkema on 2006-09-26
My log file is 794 lines. If I skip the informational lines, I have 369 left. I wouldn't be able to skip these lines based on a certain pattern. I agree it's hard to tell what you need and what not when you don't know what you're looking for.

How are your console skills? Do you know how to use an USB drive through the console? If so, you could transfer the log file to there. Otherwise, you could try and use the Lynx console-based browser to post here, or use mutt to mail yourself the file :)

---

### Post by johanhartman on 2006-09-26
My console skills... what console skills, i'm willing to learn though.

---

### Post by ifokkema on 2006-09-28
> **johanhartman said:**
> My console skills... what console skills, i'm willing to learn though.
LOL
Ok, in that case I guess we'll try and mount an USB stick through the console, so you can put the file on there.

- Ctrl-Alt-F1 gets you in the first terminal. Log in and type:
```
tail -n 0 -f /var/log/messages
```
This will show any changes to /var/log/messages on the screen. (-n 0 means show the last 0 lines currently in the file; -f will have tail show any new output)

- Attach an USB stick. Watch the messages go by. Notice the name of the USB stick. Usually sda. I'm assuming sda from now on.

- Once the messages stop, type Ctrl-C. You can go up and down using Shift-PageUp and Shift-PageDown.

- Maybe Ubuntu has mounted the drive by default. Check this by typing:
```
mount
```
There will be a list of mounted devices. Is the drive mentioned there? There will be something like:
```
/dev/sda1 on /media/usb type vfat (rw)
```
there.

- If it's not mounted, type:
```
sudo fdisk -l /dev/sda
```
to see how the partitions are laid out. I'm assuming you'll see the /dev/sda1 line:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5957    45034888+   b  W95 FAT32
```

- Mount that partition:
```
sudo mkdir /media/usb
sudo mount -t auto /dev/sda1 /media/usb

```

- If it's mounted, go to that directory (my example: /media/usb).
```
cd /media/usb
```

- Copy the file.
```
cp -p /var/log/Xorg.0.log .
```

- Unmount the disk.
```
cd
sudo umount /media/usb
```
The 'cd' makes sure you're not currently on the drive, so it can unmount safely. Now you can pull it out of the system, and you've got the file on the USB drive. Now post it here.

---

### Post by johanhartman on 2006-09-29
Will do as soon as possible. Thanks alot for all the help though.

---

