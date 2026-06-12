---
title: "refit lost ubuntu"
date: 2007-03-02
forum: Apple Intel Users
---

### Post by Hellnation on 2007-03-02
I am tring to do the triple boot with refit.
I followed the instructions and I got Ubuntu installed and working just fine.
But when I installed windows, I lost the option to boot to Ubuntu.

This is the first time I am using Ubuntu and OSX sooooo I am a little lost.

on a Macbook Core2Duo

-Clint

---

### Post by wlarsong on 2007-03-03
You could try uninstalling and re installing rEFit or make sure you syconrize the MBR of rEFit when you go to boot.

Preferably you are suppose to install linux last.

---

### Post by oskarloko on 2007-03-05
not really, wlarsong...

I've the same problem.
The case is XP is a boot-carnivorus system.... It has alterated your GRP-MBR information.

You must reinstall GRUB onto your Linux partition ( not on master boot record ) and REFIT will  see your ubuntu again ( and Windoz too )

Just: 
[LIST=1]
[*]insert your Ubuntu CD, reboot on REFIT
[*]boot on Ubuntu CD
[*]mount your hdd-installed ubuntu 
[*]execute /target/sbin/grub
[*]reinstall it
[*]let's rock :guitar: 
[/LIST]

---

### Post by Hellnation on 2007-03-07
Thanks for the reply guys.
but I reinstalled everything......
Well it works now, but when I try to boot into the window partition it comes up with a list of options.  Grub loads with the options for booting in Ubuntu and Ubuntu recover.. ect ect. and at the bottom is the boot to windows option.  The only problem is that the keyboard doesn't work some of the time and I have to restart several times before it allows me to select windows.
Do you know how to set the default OS to windows. (for the 3rd boot)

-Clint

---

### Post by oskarloko on 2007-03-09
Change grub config file and put your windows partition to the first place of options


Use ext3 driver on windows to change it again

---

### Post by Chrisj303 on 2007-03-11
> **oskarloko said:**
> Change grub config file and put your windows partition to the first place of options


Use ext3 driver on windows to change it again

Could you please expand on this, this could a lifesaver to me.
I had the same issue with the Tripleboot - the cursorkeys won't work most of the time (stopping me from selecting windows)..

Where could i locate the ext3 Driver in Windows?

Thanks,
chrisj303

---

