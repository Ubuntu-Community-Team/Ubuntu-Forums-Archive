---
title: "Apt-get Missing!! Urgent!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-20
Hey all my PC shut down auto. due to load sheading the UPS was sent for repair :( and after I open it shows apt-get not install plz install it via apt-get install apt ... It irritating how to fix this I had encountered this 3'rd time plz do help me :( I have installed loads of s/w and updates and I don't wanna do that again :mad:

Hope some 1 will help :lolflag:

Regards

---

### Post by SpiritIsReality on 2007-08-20
howdy

a thought, if you still have access to the internet
you could download the package, and install it with
sudo dpkg -i apt_0.6.46.4ubuntu10_i386.deb
if your rig is i386

[http://www.google.ca/search?hl=en&q=site%3Apackages.ubuntu.com+feisty+apt&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Apackages.ubuntu.com+feisty+apt&btnG=Google+Search&meta=)
[http://packages.ubuntu.com/feisty/base/apt](http://packages.ubuntu.com/feisty/base/apt)

---

### Post by Dark Star on 2007-08-20
From where to install ? I can't acess desktop.. Should I install via Live Cd ?

---

### Post by SpiritIsReality on 2007-08-20
you got me there
hope someone helps

---

### Post by confused57 on 2007-08-20
> **Dark Star said:**
> Hey all my PC shut down auto. due to load sheading the UPS was sent for repair :( and after I open it shows apt-get not install plz install it via apt-get install apt ... It irritating how to fix this I had encountered this 3'rd time plz do help me :( I have installed loads of s/w and updates and I don't wanna do that again :mad:

Hope some 1 will help :lolflag:

Regards

I've received this error once when I installed a different distro on a separate partition...the UUID had changed, which was different from the original UUID that was being mounted in /etc/fstab.

You could use the Ubuntu live cd and check the correct UUID's of your filesystems with:
```
blkid
```

then you could mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

compare the UUID's from blkid with your UUID's in /etc/fstab.

---

### Post by dasunst3r on 2007-08-20
If you still have network access, download this package:
[ftp://ftp.utexas.edu/mirrors/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu7_i386.deb](ftp://ftp.utexas.edu/mirrors/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu7_i386.deb)

... and in the terminal, issue the command *sudo dpkg -i apt_0.7.6ubuntu7_i386.deb*

---

### Post by Dark Star on 2007-08-21
Dudes these cmd in Live Cd cause I cannot reach Desktop. :( The boot screen ends into command line interface :( After Hdd check it says apt-get missing :x

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-21
what happens when you just boot
into ubuntu
complete system freezes ???

---

### Post by Dark Star on 2007-08-21
> **<<joe>> said:**
> what happens when you just boot
into ubuntu
complete system freezes ???
System did not freez but the Disk check start and then at 80 or so % some message flash and says apt-get missing type apt-get install apt to install iit .. But it ain't worked :x

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-21
i am not going to be much help 
but i was geting the same error you have there 
i am reinstalling ubuntu right now but i have no idea :(


i have been running Ubuntu for  along time never had this problem before i wonder what broke
i think both of our harddrive our shot

---

### Post by sumguy231 on 2007-08-21
Generally stuff like this happens if something is seriously wrong with your filesystem, so if you have a LiveCD, I would say boot from it, open a terminal and run fsck on your root partition. 
```
sudo fsck <device goes here>
```
If you don't know the name of the partition, run 
```
sudo fdisk -l
```
on your install to find out.

---

### Post by metroknight on 2007-08-21
I just had that happen also to me just acouple hours ago. My hardrive is dieing on me and it screwing with everything. My screen gave me a chance to do a command to run maintance shell manually. I typed it in and just said yes to everything. I'm up and running for now.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-21
right and i ran that on the live cd and i got something about it defanly has errors.
but it didnt fix em how do i fix them ???

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-21
any one know how to fix the errors in a ext3 partiion

---

### Post by confused57 on 2007-08-21
> **<<joe>> said:**
> any one know how to fix the errors in a ext3 partiion

Maybe something in this guide will help:
[http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check](http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check)

---

### Post by SpiritIsReality on 2007-08-21
howdy

if you can get to a command prompt with the live cd
if live cd does not get to desktop gui,
try press and hold Ctrl and Alt and F3 (if that doesn't work try Alt and F3)
log in, and run command
sudo fsck -fp /dev/hd_  whatever partition your ubuntu is on
like sumguy231 said in post #11
and confused57

repeat the 
sudo fsck -fp /dev/hd_ 
(for example on my rig I would run
sudo fsck -fp /dev/hdb7 )
command until there are no more errors displayed
then restart the computer without the live cd
run command
sudo shutdown -r now
remove the cd when computer is restarting
if all goes well and your hard drive ubuntu install starts
run the command
sudo badblocks -sv /dev/hd_ whatever partition your ubuntu is on.

I can't get to [http://www.aboutdebian.com](http://www.aboutdebian.com) 
right now for some reason but it's on the second page listed here
[http://www.google.ca/search?hl=en&q=site%3Aaboutdebian.com+fsck&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aaboutdebian.com+fsck&btnG=Google+Search&meta=)

trails

---

### Post by darksidedude on 2007-08-21
all I did was type```
reboot
``` thinking it would reboot the computer, what it did was ignore the error ( which was a mistake) because I installed openarena with apt after it happened, so it is a a error that isnt really a error:) if I lost you just type reboot at the cli ( it worked for me so I thought I would pass it on)

---

### Post by SpiritIsReality on 2007-08-31
howdy

had the same error message.
confused in post #5 had the answer for what happened in my case.

with the gparted live-cd,
I deleted one of the partitions that was usually mounted at boot, 
and listed in /etc/fstab.
When I quit the gparted cd, and rebooted,
I got the same error messages, including the one about apt-get,
and ended up at a root prompt.
I commented out the listing for the partition (that was no more)
in the /etc/fstab file
nano -w /etc/fstab
ctr-x, y, enter
shutdown -r now to
reboot, I was in the saddle.

@ confused57 , thanks

@darkstar , sorry for all my b$ above, and I don't mean block size, ha!ha!

trails

---

