---
title: "Install windows but keep current kubuntu install"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by buzzmandt on 2007-06-05
OK, I'm thinking this is going to be fairly easy, but not straight forward.....
I've been a windows user that runs the occassional linux os using mandrake/mandriva for several years, but would only boot to it for internet sensative material, i.e. checking bank account, ordering online w/ credit card etc....

Since finding ubuntu (or in my case kubuntu) I'm switching to a linux user that opts for the occasional windows load for gaming and only gaming.  I've got a great install on this kubuntu, nvidia drives are good, firefox, thunderbird are nicely set up, runs nearly any video I want/need, FTP and quanta as needed, Teamspeak, etc.  This is truely a fantastic distro of linux.....

My question is.....I need to do a reinstall on my windows partition (hda1) (kubuntu on hdc1 I think that's right).  I know that the standard procedure is to install windows first, then your linux distros, opting for kubuntu as your last install.  Is there a way I can re-install windows, then install grub for my windows/kubuntu dual boot without reinstalling kubuntu?

amd 2600+
asus a7n8x-x
nvidia 6600 gt
2 Gigs Mem
1st hd as windows os
2nd hd as ntfs secondary and archive drive
3rd hd kubuntu

Linux knowledge 1-10 would be about a 4
I have searched this forum and found every answer i was looking for except this one......You guys that know your stuff and help us noobs out rock, I thank you all, and thanks in advance for this one

---

### Post by daschmidty on 2007-06-05
All you have to do is install windows again in your windows partition. The windows bootloader WILL overwrite GRUB however, so boot an ubuntu liveCD, open a terminal and do
```
sudo grub-install /dev/hda or /dev/sda(whatever your hd is identified as-your first HD, the one with windows on it)
```
this should overwrite the windows MBR with GRUB again.

---

### Post by buzzmandt on 2007-06-05
thanks, will this set up automatically like when you install kubuntu or will i have to define the locations of the boot images for each os?

---

### Post by daschmidty on 2007-06-05
It is the same procedure the installer runs on you first setup of GRUB so in theory, it should "just work" with everything..it has for me in the past with kubuntu+XP.

---

### Post by buzzmandt on 2007-06-05
Thanks, I kinda thought it was something like that but didn't know the command line and procedure......Something to know for sure since windows needs to be installed so much more often than linux.

---

### Post by daschmidty on 2007-06-05
yes it's good to know, especially when you are an os-install junkie, and do all kinds of creative things to break bootloaders...like when the systems starts up and the screen just fills with "GRUBGRUBGRUB" ;)

---

### Post by daschmidty on 2007-06-05
Apparently i made a mistake and i read somewhere that grub-install doesn't like to work sometimes from livecd's so use this method instead if you have trouble
```
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
```

---

