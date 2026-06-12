---
title: "dual booting with WinXP on a new harddrive?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by lenny45 on 2006-02-09
hey all, new posts,new member, noob to Linux......!  awaiting my disks!;) 

I am finally making the dive into Linux but have a coupla questions:

1-does ubuntu use the same code,commands, language as ANY of the Linux's out there? another words, will ubuntu be good enough to hip me up to Linux lingo when i confront and and all Linux issue's as a tech?

2-i just got a new Sata 250 gig drive. Can i dual boot WinXP and Ubuntu thru partitioning? is this gonna be a pain or do i need a seperate machine?

i have a 120 and 80 gig drives in my machine now with windows xp.

thanks again......

---

### Post by xXx 0wn3d xXx on 2006-02-09
Ubuntu is very simular to Mandriva and Fedora Core. Out of alot of distros I have found ubuntu to be the most user friendly and versitile distro.

About your question about dual booting: Yes, you can dual boot with windows. I do not dual boot so I don't have much of an idea on what to do. I can suggest searching the forums for "How to dual boot with windows," or dual booting with windows. 

I switched from windows 98 and xp to ubuntu and I really like it. It is a little hard at first but who can complain ? No viruses, spyware, malware, it's free and there is no need to clean out the regestry, defrag, or run disk cleanup. Make sure that if you are going to switch to ubuntu, you do so with an open mind. I don't know if I will go back to windows because I love ubuntu so much.... Sorry for the long speach but that's how I feel :)

---

### Post by Herios on 2006-02-09
hey whats going on

i'm a linux newbie too. dual booted linux and win xp on my laptop and it was fairly easy. there is some good walk throughs on the net but can't find the links right now.

as far as i know ubuntu breezy comes with 2.6.x version kernel which comes with bash  (bourne again shell) and some other shells too.i believe most linux users use bash as there command shell.breezy comes with gnome by default for  desktop, opposed to KDE.

still learning myself, try the linux documentation project for more info. hope this helped

---

### Post by lenny45 on 2006-02-09
[QUOTE=Herios]hey whats going on

i'm a linux newbie too. dual booted linux and win xp on my laptop and it was fairly easy. there is some good walk throughs on the net but can't find the links right now.

as far as i know ubuntu breezy comes with 2.6.x version kernel which comes with bash  (bourne again shell) and some other shells too.i believe most linux users use bash as there command shell.breezy comes with gnome by default for  desktop, opposed to KDE.

still learning myself, try the linux documentation project for more info. hope this helped[/QUOTE]thx yall--very helpful...

ok---i was gonna install my new hardrive and put XP on it before ubuntu arrives. out of the 250 gigs, how big should i make my partitions? 

i hope to play Unreal tournament out of linux eventually. and eventually, just run Linux. but that will be a while......anyway, i just wonder what the partition size should be for now....:confused:

---

### Post by Herios on 2006-02-09
not to sure, i think it probly depends on which os you are going to be using more

i only had 50 gigs to dice up split it four ways between windows NTFS  partition linux ext3 a swap which the intsaller sized for me and a fat32 partition so i could pass files between windows and linux. at least i hope ,never use windows now. 

if your going to do a lot of gaming on linux i would give most space to linux and maybe a bigger swap space but not really to sure , you might want to search the forums for more info

---

### Post by Herios on 2006-02-09
oh yeah i had win xp already instaled and it shrunk that partition fine.

---

### Post by veniceanonymus on 2006-02-09
Check out the thread "Is ubuntu for you?" (top thread in the begginers page) and you will found at the bottom of the page a good link to dual boot: "how to dual boot with Windows" . Or check step by step at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Bartender on 2006-02-09
lenny -
Whew, I'm gettin tired of writing the same thing over & over - here's a recent thread

[http://ubuntuforums.org/showthread.php?t=127291](http://ubuntuforums.org/showthread.php?t=127291)

follow the "hermanzone" link to the best dual-boot instructions out there.  Aysiu has this as a permanent link in his posts.  I followed the "Ubuntu + NTFS" instructions and created the FAT32 partition just like they described.
 

Whoops - venice beat me to it

At any rate, be sure to defrag your Windows install, round up your Windows CD and key code, back up any valuable data...too many things can go wrong that aren't Ubuntu's fault.  If you can, set up your computer next to an internet connected machine so you can follow those steps without any screwups.  It's important to know about the file systems - Linux can't go into NTFS but it can work with FAT32 so that's why they recommend making a partition that both OS'es can use.

If you do this, Windows will recognize the FAT32 partition w/out problems (it'll label it "D:/ Local Disk" or similar) but Ubuntu probly won't.  Editing the fstab file so that it can use the partition isn't too hard; there are lots of posts regarding the steps.

---

### Post by lenny45 on 2006-02-09
thanks guys...

hey bartender--i will check out the link. fat32 eh? wow---didn't know about that between the two os's. i will be back a lot more when the disks arrive....:-k

---

