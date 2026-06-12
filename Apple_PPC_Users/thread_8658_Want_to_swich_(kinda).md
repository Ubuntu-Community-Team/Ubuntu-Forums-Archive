---
title: "Want to swich (kinda)"
date: 2004-12-19
forum: Apple PPC Users
---

### Post by simsbaby on 2004-12-19
hello ok im going to install ubuntu on my ibook i want to know how i can get dule boot :confused: . i need to do this since i had my mac for a long time and dont want to lose my stuff  i have a externel hard drive that firewire can i use that? also what is the minamum space i can give ubuntu is 5gigs ok?

---

### Post by joemafia on 2004-12-19
use ipartiton to resize your mac partition and create a new partition for Ubuntu in case you don't have one. I have 6GB partition for Ubuntu. After the install and everything i still have 2.1GB left. 5GB might be too close, I recommend 6GB at least if you wanna play with Ubuntu. I'm not sure about Using an external firewire HD.

---

### Post by trash on 2004-12-19
i did a standard install on my g4, 12gb partition..

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda12             12G  2.4G  8.3G  23% /

i guess you could install the basics and add what you need later:)

---

### Post by simsbaby on 2004-12-19
ipartiton is to much.

---

### Post by ubuntu4everyone on 2004-12-29
I dont know about using a firewire disk but dual booting on one HD is easy, first you must back up your data on your firewire hd becuse this will involve reinstalling Mac OS X. After you back up your data you need to put the software recovery disk in, reboot while holding C and it will open Mac installer, go to the top bar and someware it will say disk utility, click your hd and then find the partition tab there is a drop down bar and it will say 1 partition, 2 partition,3 partition....... select 2 partitions(resize as necesary, but i would leave 10 gigs of space in the linux partition if you want to do it properly) use the 10 gig partition as free space and set the other one as hfs journeld (this will be used by mac os), click partition at the bottom of the screen (WARNING this will format HD), then continue with Mac installaition. 
After you have finished with mac installaition put the ubuntu disk in and reboot holding down C. On ubunu setup it will ask you easy questions like keyboard locaition etc ..... When you get to a notice saying  erase intire disk or manualy partition select manually partition. Choose new in the menu and on usage select swap and on size select 1 gig, then press create.then create another new one but this time on usage select format and mount point / and filesystem select ext 3.The last one to create is arguably the most important one, the bootloader so select new and on usage select as newworld bootloader or bootloader. Select continue.
That should be it but if you have any trouble private message me  :D

---

### Post by simsbaby on 2005-01-02
thanks for the info@

---

### Post by tiiim on 2005-01-02
[QUOTE=simsbaby]hello ok im going to install ubuntu on my ibook i want to know how i can get dule boot :confused: . i need to do this since i had my mac for a long time and dont want to lose my stuff  i have a externel hard drive that firewire can i use that? also what is the minamum space i can give ubuntu is 5gigs ok?[/QUOTE]

I diteched OS X completely and just use Linux on  my iBook and i prefer miles. I did dual boot for a while but i found myself slipping more and more over to the Linux side so i just jumped over and never regretted it since.

Ubuntu is easy to use and fun with the advance side if you get more into it. I had no trouble. Memory cards and things here work fine the hotplug system works well on Unbuntu.

So dual boot and let us know how it goes!

Tim  :D

---

### Post by ubuntu4everyone on 2005-01-04
did it work

---

