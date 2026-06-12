---
title: "opened ubuntu in vmware now every time i run ubuntu out of vmware  i get xserver prob"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2006-11-30
I ran ubuntu in vmware and installed vmware-tools and ever since I cant boot into ubuntu without vmware. i keep getting an faild to start xserver error. I cant figure out how to uninstall vmware-tools so I dont know if thats the problem.

---

### Post by nickburns on 2006-11-30
So I understand, your main OS is not Ubuntu?  

Are you running Windows with vmware and Ubuntu is running on vmware?

---

### Post by cosmoshell on 2006-11-30
ubuntu was my main os but but when i was in windows i opened ubuntu in vmware. now thats the only way i can use ubuntu.

---

### Post by nickburns on 2006-11-30
Ok so you have windows as main and ubuntu on vmware.  Install was good, but when you installed vmware tools xserver broke.

I would start up vmware and boot your ubuntu.  Then when X fails, hit ok until you get to a terminal.  Once at the terminal, login and type in:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

(this will copy your config file)

then type

sudo dpkg-reconfigure xserver-xorg

this will reconfigure you xorg.conf file to a good one.

---

### Post by cosmoshell on 2006-11-30
I dont have the xserver problem when ran in vmware

---

### Post by nickburns on 2006-11-30
I'm confused by your response, you obviously have two different instances of Ubuntu, one on vmware and one that is not.  The two instances have nothing to do with each other.  In fact they cannot effect each other at all.  So either  you have a problem with the vmware version or the other.  If it is the other then you can use the same steps mentioned above to fix it.

---

### Post by AndyCooll on 2006-11-30
I'm not sure if this is clear. When using VMware it is not your "main" copy you are logging into. Your VMware version of Ubuntu is actually a completely separate installation from your "main" version of Ubuntu.

So, based upon the above can we please be clear where the problem is. What I gather you are saying is that your VMware version of Ubuntu is fine, but your "main" install version brings up errors.

In which case nickburns instructions still apply. However apply them to the version of Ubuntu that is giving you errors.

:cool:

---

### Post by cosmoshell on 2006-11-30
ok this is hard to explane. I put the ubuntu cd in computer and rebooted the computer. installed ubuntu every thing worked used ubuntu. a week later I installed windows. ubuntu still worked fine. 
then i put vmware on windows and on ubuntu. lator I ran ubuntu on vmware without a cd or iso. then i installed vmware tools on ubuntu 
while useing it on vmware. the next time i restarted and used ubuntu not windows i kept getting xserver problems. so i tried to run it agin in vmware on windows that works fine. while my computer is booted normly into just ubuntu i tried dpkg-reconfigure xserver-xorg severl time with diffrent settings same resault. faild to start xserver. There is only one ubuntu os installed on this machine. i did not install it twice. all my files that i put on the ubuntu desktop are the same regardless if i run it on its own or on vmware.

---

### Post by nickburns on 2006-11-30
There is no way the the vmware and main Ubuntu installations are the same.  I don't see how you can see your Ubuntu installation from vmware.

From what you said you have

Ubuntu on Partition 1  -with vmware software installed
                       -


Windows on Partition 2 - with vmware software installed
                       - you can see Ubuntu from Partition 1
                       - you installed vmware tool onto Partition1

Since vmware uses files on the installed partion, there is no way that Partition 2 could boot the Ubuntu Partition 1 with vmware.

---

### Post by cosmoshell on 2006-11-30
vary simple. when you go to make a virtual machine you set it up to use the physical disk not a virtual disc. you can actualy use the same virtual machine 
to open any os on your computer.
 
however if i ty to open windows useing vmware to open windows that wont work same thing if i try to open ubuntu on ubuntu.

---

### Post by nickburns on 2006-11-30
If that is the case, have you tried the above solution on the failed x startup?

---

### Post by cosmoshell on 2006-11-30
yes i tried that a long time ago

---

