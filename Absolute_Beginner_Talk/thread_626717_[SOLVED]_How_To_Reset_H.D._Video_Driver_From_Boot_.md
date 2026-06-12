---
title: "[SOLVED] How To Reset H.D. Video Driver From Boot CD"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by dsiddens on 2007-11-29
I had a running install of Gutsy on my HP dv8000 AMD64.  I thought something was not quite right with the video so I tried setting the video driver to another choice.  When I rebooted the last I saw was the notification of GRUB beginning.  There was no color, no moving bar, no sign in.  What was on the screen was a washed out mess with a vertical line in about the middle of the screen.   

I can boot up (as I am right now) using the Live CD I made  from the .iso image.  So I can see the file structure and files on the laptop's H.D. but I don't know how to make/save changes to the selection of the video driver.

If you know how to do this and it involves the command  line, can you please post line by line entries, assuming I know nothing about the command line?   Thank you, Doug

---

### Post by Sandlst on 2007-11-29
Since you can see your laptops files, I'm guessing you know how to mount the hard drive already?  If so, you can change the video driver with this set of commands:
```
cd (wherethefilesaremounted)
```This changes the directory to where your linux partitions are mounted
```
gedit etc/X11/xorg.conf
```This will open your X-server configuration file for editing.  Scroll through the file looking for a section called "Device".  This section is your video card.  You should be able to change the driver here.  Click save when done, then exit.  ```
cd ..
```This gets you back to the livecd's home directory, where you can then unmount your files.  
Good luck, post back if you have any problems!

---

### Post by dsiddens on 2007-11-29
Sandlst,  No I don't know how to mount the laptop's internal H.D.  I'm confined to the options that are available from the Live CD.  Yes, I can see the contents of the internal H.D. by using Places>Computer>107.2 GB Volume.  They show up on the File Browser.

Doug

---

### Post by Sandlst on 2007-11-29
Alright, try this from a fresh terminal: ```
cd Desktop
``` ```
mkdir mnt
``````
sudo fdisk -l
```This command should show you all the partitions on all of your harddrives; one should be the linux one, unless you have more linux partitions it will be the only one using ext3.  It will be in the form of: hda1 hda2 hdb1 or sda1 sda2 sdb1 etc.  Once you know it, enter ```
sudo mount /dev/[COLOR="DeepSkyBlue"]sda1[/COLOR] mnt
```changing sda1 to your device from above.  Then```
sudo nano mnt/etc/X11/xorg.conf
``` and refer to my post above, starting at looking for the "Device" section.  If you are not sure what to put for the driver, try ```
vesa
```It should be safe.  When done, save and close the file, then type ```
cd ..
``````
sudo umount /dev/[COLOR="DeepSkyBlue"]sda1[/COLOR]
```Changing sda1 to your device from above.  Good luck, post back if you have any problems.

---

### Post by dsiddens on 2007-11-29
Sandlst,

At the code entry "sudo gedit mnt/etc/X11/xorg.conf" I'm returned "Cannot open display"

Doug

---

### Post by Sandlst on 2007-11-29
> **dsiddens said:**
> Sandlst,

At the code entry "sudo gedit mnt/etc/X11/xorg.conf" I'm returned "Cannot open display"

Doug
Hmmmm that is a bit troubling, if you are ok with it, you can use a command line editor instead with ```
sudo nano ~/Desktop/mnt/etc/X11/xorg.conf
```Its pretty easy to use, although there is no mouse support. when done hit F2 then Y to save.

---

### Post by dsiddens on 2007-11-30
Sandlst,

Using ctrl+alt+f1, I entered "sudo nano mnt/etc/X11/xorg.conf".  This brought forth a screen of nano 2.0.6 with the title of "mnt/etc/X11/xorg.conf". I saw no options for saving. I then entered "f2" and the screen came back to the ctrl+alt+f1 screen.  Again, no options  to save were seen.

Doug

---

### Post by Sandlst on 2007-12-03
Hmmm, from this behavior I would guess the path is messed up somehow, could you first verify the folder ```
mnt
```is visible on your desktop, and that it actually contains files (it should if the previous commands worked out correctly).  I'll change the above command to one that will definitly work if the files are mounted right, so please try it again.

---

### Post by dsiddens on 2007-12-03
Sandlst,

Using Terminal I entered mnt and it returned "command not found". 

I looked in the System>Preferences and in System>Administration and in Applications>Accessories but did not find a GUI way to mount things.

Doug

---

### Post by Sandlst on 2007-12-03
Ah sorry, I meant could you physically look on your desktop to verify the folder mnt exists, and is full of stuff.  After entering those commands from my second post, it should appear there.  If it doesn't, or the folder shows up empty, the last command will not work.

---

### Post by dsiddens on 2007-12-04
Sandlst,
Here's the results of the coding from your second post.  

Doug



Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046477

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13995   112414806   83  Linux
/dev/hda2           13996       14593     4803435    5  Extended
/dev/hda5           13996       14593     4803403+  82  Linux swap / Solaris
ubuntu@ubuntu:~/Desktop$

---

### Post by NT4usB on 2007-12-04
Hate to be a buttinsky but wouldn't it be easier to run:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in a terminal to reset the display?
Boot the laptop normally (not to the CD). When the display poops, type Ctrl+Alt+F1 to get to a terminal. Log in and type the command.

ed: if that doesn't get it, we can edit xorg from the same terminal.

---

### Post by Sandlst on 2007-12-04
> **NT4usB said:**
> Hate to be a buttinsky but wouldn't it be easier to run:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in a terminal to reset the display?
Boot the laptop normally (not to the CD). When the display poops, type Ctrl+Alt+F1 to get to a terminal. Log in and type the command.

ed: if that doesn't get it, we can edit xorg from the same terminal.

I was under the impression from the first post that the graphics were so corrupted as to not allow this, but if it can be done this would be infinitely easier, you might even try doing it blindly if you can't see anything.

If that can't be done, try running the other commands in my second post replacing /dev/sda1 with /dev/hda1, and post back the results.

---

### Post by dsiddens on 2007-12-05
Welcome NT4usB to the solution team.  

I tried your idea: booted from the H.D., then ctrl+alt+f1 and did get a terminal (with very large font size), logged in.  But at that point the screen was not showing my last line.  So I pressed on and blindly entered "sudo dpkg-reconfigure -phigh xserver-xorg"

I then rebooted, again from the H.D. but the result was the same messed up display.

Doug

---

### Post by dsiddens on 2007-12-05
Sandlst,

I went back to your 2nd post and using ctrl+alt+f1, entered 
cd Desktop
mkdir mnt
sudo fdisk -l
sudo mount /dev/hda1 mnt
sudo gedit mnt/etc/X11/xorg.conf

at that last entry above, the screen returned "cannot open display"

Doug

---

### Post by Sandlst on 2007-12-05
> **dsiddens said:**
> Sandlst,

I went back to your 2nd post and using ctrl+alt+f1, entered 
cd Desktop
mkdir mnt
sudo fdisk -l
sudo mount /dev/hda1 mnt
sudo gedit mnt/etc/X11/xorg.conf

at that last entry above, the screen returned "cannot open display"

Doug

Ill edit the post to use nano instead of gedit, which should work.  Be sure to read my post after that to see how to save files in nano.

---

### Post by NT4usB on 2007-12-05
> **dsiddens said:**
> Welcome NT4usB to the solution team.  

I tried your idea: booted from the H.D., then ctrl+alt+f1 and did get a terminal (with very large font size), logged in.  But at that point the screen was not showing my last line.  So I pressed on and blindly entered "sudo dpkg-reconfigure -phigh xserver-xorg"

I then rebooted, again from the H.D. but the result was the same messed up display.

Doug

Most LCDs you can push some buttons on the front to *automatically configure* the display while working in the terminal. Should make everything fit so you can see it.

If you're going at it blind, the steps would be:
login name *enter*
password *enter*
sudo dpkg-blabla *enter*
password *enter*

From your post, looks like you missed the part where it asked for your password after sudo.
There should be a short question/answer session when running dpkg-reconfigure. Some stuff should scroll on the screen.
If you can't see it, maybe *enter* *enter* to accept the defaults. Enough *enters* and the cursor should scroll up the screen.

Heck, as long as you're in the terminal...```
 cd /etc/X11/
``` ```
cat xorg.conf
``` and lets have a look at what's in your xorg.conf.

---

### Post by bodhi.zazen on 2007-12-05
Boot a live cd.

Mount your ubuntu parrtition in say /media/ubuntu

```
sudo mkdir /media/ubutu
sudo mount /dev/xxx /media/ubuntu
```

Then chroot and reconfigure :

```
sudo chroot /media/ubuntu /bin/bash

sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot to hard drive

---

### Post by dsiddens on 2007-12-06
bodhi.zazen,

Thank you!

That set of instructions worked.  Enter it in the How To Hall Of Fame?

Thanks again, Doug

---

