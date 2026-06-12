---
title: "Real new"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Sandhog on 2008-01-12
I've been thinking about installing ubuntu for some time ( I have version6.06) that i've never installed, I'm no expert at this but I'm tired of all the mess with Windows. Here goes I have a160 gig HDD with Windows XP Pro on C drive and approx.80 gigs on J drive. My question is if I download Gutsy will I be able to get it to install on the J drive segment. I still want XP for the wife & the Grandchildren.
Thanks for any & all help.

---

### Post by Joeb454 on 2008-01-12
Yeah you should be able to, you'd be better to take anything off the J:\ drive and then erase the partition (you can do this from the Gutsy LiveCD) before you install :)

---

### Post by limac on 2008-01-12
while you are installing gutsy, you will have a prtition option, how you want to resize the windows partion and accordingly, your linux partition will be made, and then you can dual boot windows and linux. in other words you'll have both os's and they will each run seperately not interfearing one another.

enjoy,
limac :)

---

### Post by cotcot on 2008-01-12
[[COLOR="Red"]This link[/COLOR] ]("http://users.bigpond.net.au/hermanzone/")will help you a lot.

---

### Post by Joeb454 on 2008-01-12
This link is posted around here a lot. But it's the guide I used when I first installed Ubuntu (the guide was different back then)

And I think it'd apply to XP as well as Vista :)

[Link]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by djbsteart1 on 2008-01-12
yes. it quite simple to set up the dual boot. 
1) make sure there is nothing on j drive you want. j drive will have everything on it deleted. 
2)download the gutsy live cd, burn the iso to a disk, edit the bios settings to boot from cd and let it start up.
3) you can either play on the live cd for a bit to check that you like it, or just click the install icon on the desktop to get started.
4) follow the steps, but when it comes to setting up the drive; if the c drive and j drive are one disk with 2 partition follow this otherwise see 5. select the j drive, (identify by its size) set up a partition for swap, do this by deleting the original partition and then selecting make  new, then select swap for its file system, a guideline for its size is around twice the size of your computers ram. then use the remaining space for the install(a), or split it so you have a data partition that both gutsy and xp can see(b). 
(afor the first option, select what file system you want, ext3 or jfs are safe bets but all of the ones listed are good barring the 2 fat ones. select its mount point to "/" and press next. 
(b) if you want the data partition, set up a small partition, about 3-4gig and do as above and use the remaining space fora fat 32 partition which windows can see. mount it as media.
5) if you have 2 hard disks, you can set gutsy to install automatically on the j drive, it does swap for you. there is a radio button to select this option.
6) enter your details and continue with the install. when it finishes restart the computer and grub, the boot loader should pick up both xp and gutsy and give you a choice of which os to start. 

good luck and i hope this is clear enough to be of help. any question just ask.

---

### Post by Sandhog on 2008-01-17
Thanks for all the replys, I'll try to put your answers to good use.
Sandhog:confused::):):)

---

### Post by hyper_ch on 2008-01-17
[http://www.psychocats.net](http://www.psychocats.net)

and use a DESCRIPTIVE TOPIC TITLE and not a genereic "noob here" or "need help"

---

