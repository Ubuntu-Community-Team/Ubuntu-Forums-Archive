---
title: "synaptic pm deleting 2.6.15"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by helmeteye on 2006-10-10
I have what looks like a common thing, ramdisk ran out of compressed data inavlid compressed format (err=1)  kernel panic - not sincing: vfs: unable to mount root fs on unknown-block (0,0).  I am afraid to shut down.  I have opened synaptic package manager and found many kernels that are 2.6.15 etc...  The green I am assuming are the ones that are installed.  I don't believe the others are but I don't know.  I believe the green one I have now is safe I have already done a restart and it worked, but am afraid to try it again.  

     Is there something I need to delete here(withing package manager). I also saw where someone said to put # before all of the kernels with 25 in them instead of 23 within the grub.   I am completely new to this stuff and refuse to give up.  All the terminology is new to me.  I would like to get this system running so my kids can use it.  

     I am so new I don't even understand sudo yet.  Where do I go to use it?  I have opened terminal and such. I will definately be doing more research into commands and such but would like someone to help me understand even the simplist things.  

     I am very busy and haven't had time to read all of the large amount of material much less finding instructions and stuff with the search function.  This for instance: [http://users.bigpond.net.au/hermanzone/p15.htm#orientation](http://users.bigpond.net.au/hermanzone/p15.htm#orientation)  My kernel panic is a fine example.  I have found alot of stuff about it and haven't found anything I could actually, with my limited knowledge and mental capacity, use.

---

### Post by petri on 2006-10-10
Because you are new to Ubuntu and this is your second(?) post I believe you don't have that much important data already on your harddisk. I recommend you to make reinstall of Ubuntu. I have had couple of times these kernel panics and I did the reinstall. Ubuntu install is so quick :)

Last time I had kernel panic was on my Mepis partition. It somehow recognized my hd:s as hda, hde, hdg and hdh when Ubuntu recognizes them hda, hdc, hdd, hde (and hdb DVD). I did some fiddeling with grubs menu.lst in Mepis with the line ```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdg3 nomce quiet vga=791
``` I changed hdg3 to hdc3 as it is in Ubuntu. That was the cause of kernel panic and this time I didn't have to reinstall. 

What is causing yours I have no idea, the link you have to Hermans site is among the best with grub and other usefull information about installing. Another great site is [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) it is very good before, during and after installing (you do remember you can browse the internet during a DeskopCD installation?) At aysius site (psychocats) you will find a lots of usefull information like why to use aptitude instead of apt-get and so on.

And yes, the green ones in Synaptic are installed on your pc.

sudo is Switch User and DO which gives you a temporary root-rights. That is one of the most important security things in Ubuntu, in that way you don't ever run as a root which is like Administrator account in windows. There is people in these forums who tells you to open an root account and they are doing a major wrong with that recommendation. If people start to follow that advice they will ruin the Ubuntus security and it will be as vulnerable as windows. We do not want that, do we? About sudo you can read at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) and about the importance to understand when to run an ordinary sudo and when to run a graphical sudo you can read at aysius site. 

aysiu is one of the moderators of these forums.


EDIT: Welcome to Ubuntu! :D

---

### Post by helmeteye on 2006-10-11
Thanx petri,  I used my fresh install to post this thread.  I have actually restart it once.  I had re-installed it once before already and everything was working good until I did the dreaded update.  That is why I was trying to figure out if I should delete certain updates before they get installed.  I believe there is a grub update that causes the problem but I don't know.  Does anybody know what updates have the bug in them and if I should just delete said updates or go into something within the updayte and just correct whatever it is that causes the crash.

---

### Post by petri on 2006-10-11
I don't think you have to worry about updates. There was a major bug in xorg update some weeks ago and I think anything like that is not going to happen for a while :rolleyes: 

Grub update from repositories should not cause crash, are you experiencing crashes still?


EDIT: If you have only Ubuntu you don't see grub at boot. After BIOS is done hold down Escape and the grub will show up, This is quite good to know because if you are experiencing crashes with the newest kernel you can boot with an older kernel so you should be able to browse here and find ot the problem if it is update from Ubuntu or is it something else. Phew, so many word in one sentence :-k

---

### Post by helmeteye on 2006-10-21
thanx.  I just went through a long nightmare.  My bellsouth dsl was down for a couple days and they weren't picking up on the tech phone.  I got so mad I wanted to be sure it wasn't my new os so I reformatted.  That didn't go so well I just got this thing back online today.  A couple hours ago.  This newest install didn't load up all the way and things like my add/remove app doesn't work.  Updates works and and synaptic pm works so I guess I may download some stuff to fix broken apps.

---

