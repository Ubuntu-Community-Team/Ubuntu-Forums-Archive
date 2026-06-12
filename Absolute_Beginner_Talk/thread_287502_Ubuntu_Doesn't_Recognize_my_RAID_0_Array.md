---
title: "Ubuntu Doesn't Recognize my RAID 0 Array"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by saumaun on 2006-10-28
I cant get ubuntu to recognize my raid 0 array. I have already created the partitions required. but it identifies my HDDs seperate.](*,)

---

### Post by DOD1951 on 2006-10-28
What does "sudo dmraid -ay -v" through terminal
give you ?

---

### Post by saumaun on 2006-10-28
command not found...

---

### Post by DOD1951 on 2006-10-28
Go System>Administration>Synaptic Package Manager.
Search for dmraid, see if your software raid format is supported. If it is mark dmraid for installation. Once installed try running dmraid -ay -v again.

---

### Post by NavmaN on 2006-10-28
Saumaun, please be more specific in describing your problems.
And yes, I am who you think I am.

---

### Post by saumaun on 2006-10-28
I searched for dmraid as u said. Nothing found. it says no package selected
](*,)

---

### Post by saumaun on 2006-10-28
Lol navid. STALKER! LOL jk. I think im pretty specific...:mrgreen:

---

### Post by DOD1951 on 2006-10-28
You probably need to add a repository. Go to settings in synaptic package manager select repositories and this is where i get stuck as I don't know which one contains dmraid so if it was me i'd check all of them. Hopefully you should then find it. I am assuming you are on Ubuntu 6.06 and not Edgy Eft.

---

### Post by saumaun on 2006-10-28
Ok. I just got a solution. Im at a friend's LAN party, and he led me into a room where he builds computer. He had a HUGE box full of at least 100 hard drives of different interfaces. He just gave me a SATA hard drive for free! So im just gonna keep my origional raid for windows and use the new one for ubuntu. Thanks soooo much for all of your help!

---

### Post by DOD1951 on 2006-10-28
No worries :)

---

### Post by Otsegoflesh on 2006-10-29
> **DOD1951 said:**
> What does "sudo dmraid -ay -v" through terminal
give you ?

i have the same problem, my raid 0 isnt being detected/ i dont know how to get the ubuntu installer to recognize my two sata drives as a raid. after adding new repositories and searching for dmraid, i found and installed that. this is what the command you said gave me:

ubuntu@ubuntu:~$ sudo dmraid -ay -v
/dev/sda: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
ubuntu@ubuntu:~$ 

what do i do now? :confused:

---

### Post by Otsegoflesh on 2006-11-05
ok i've fooled around with the alternate install cds (both 6.06 and 6.10) for raid options during installation and i've managed to set up my raid 0 the way i want. the problem is, it seems grub cant be installed on a raid. (and no, i'm not trying to dual-boot. its all or nothing.) 

so then i tried setting up multiple partitions (i have two identical sata drives - called sda and sdb) something like this:

sda:
/boot -4gigs ext2
raid 0 -76gigs ext3

sdb:
raid 0 -76gigs ext3
swap -4gigs

i've got the /boot set at the front of the first hdd like i read somewhere, and the swap partition is twice the amount of ram i have, which i also read somewhere around here. i know the /boot is kind of big, but it needs to be the same size as the swap so my raid 0 has two identical sized partitions. anyway, this formation will finish the installation but when it goes to boot, i get this:

GRUB Loading Stage1.5.

GRUB loading, please wait...

and it just hangs there forever. i've even let it "load" for over 3 hours, thinking it was due to the large /boot partition. 

so then i said "screw raid" and tried setting up the partitions differently. this time i used the same format but without the raid, i made the /boot 200mb, the swap 1gig, and the two other drives i made / and /home with max file size. this gets me no where as well, i never get past "GRUB Loading Stage1.5." 

well i've been messing around with three ubuntu linux installer cds for a few hours everyday for the past two weeks, trying everything i can. occassionally i come to these forums and search for answers or ideas i can try out but nothing is working and im pissed off about how much of a pain in the *** it has been just to install the damn thing. sure, increased usability and customization is neat, but when it takes you longer to figure something out and learn how to do it then it would have taken you to get around it in windows... thats a serious problem. i dont want to be a dick, but it didnt take me anywhere near as long as this to learn what sata drivers were and how to make a floppy with my mobo support cd for use after pressing f6 during a windows xp installation. 

i dont even know why sata drives arent as well supported as they should be, my raid 0 array with two 80 gig harddrives is twice as fast as a regular 160 ide drive when it comes to data access and storage.

thats enough of a rant, sorry for such a long post. if anyone is kind enough to help me kick the lame windows habit, i'm listening; ready and willing to learn.

---

### Post by bodhi.zazen on 2006-11-05
See if the Gentoo wiki helps: [Gentoo RAID wiki](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID)

---

