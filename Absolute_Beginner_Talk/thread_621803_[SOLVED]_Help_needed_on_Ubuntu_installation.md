---
title: "[SOLVED] Help needed on Ubuntu installation"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by onlytanmoy on 2007-11-24
Dear All Linux enthusiasts n Gurus, 
Currently i am dual booting betn win vista and sabayon linux using GRUB bootloader.
i wish to remove sabayon and instal ubuntu ultimate 1.5 in its place.
also, sabayon is installed on 3 gb partition but i wish to keep at least 6 gb for ubuntu ultimate.

how can i do that widout hampering the booting of vista..i mean after i install ubuntu, i shud be able
to dual boot betn vista and ubuntu..plzz guide me step-by-step..thanks in advance.

---

### Post by banewman on 2007-11-24
Ubuntu uses grub as well. Installing ubuntu after windows gives you a grub menu that allows a choice of OS at boot time.
With the program "gparted" that's in the menu of the ubuntu live cd you can resize windows o make more room.
Choose manual partitioning during the install and use the mouse to slide the windows partition back so you have more room.  :)

---

### Post by onlytanmoy on 2007-11-24
@ banewman >> thanks for the instant reply bro.
u mean i will boot from the ubuntu dvd & then delete existing sabayon linux partition and create new partition with ext3 file system, size 6 gb, set the root to /  & setup ubuntu. 
after its done, i can again dual boot betn vista & ubuntu..right?

---

### Post by forestpixie on 2007-11-24
I think it's best to use the vista tool to resize partitions - or at least that's what I've read here.

---

### Post by banewman on 2007-11-24
Maybe ForestPixie is right - I have no windows. :)
But don't forget the swap partition. :)

---

### Post by derby007 on 2007-11-24
Like forestpixie says, I also used Vista to partition initially.
You could also use : gparted-livecd-0.3.4-10.iso to partition your system.

Good how to at : [http://www.apcmag.com/5485/dualbooting_vista_and_xp]("http://www.apcmag.com/5485/dualbooting_vista_and_xp")

I suppose when you delete the current linux system it will flux up your Grub, but dont mind as the new linux distro should fix it again after installing.

---

### Post by forestpixie on 2007-11-24
derbyoo7 - surely you mean who is Iarwain Ben-adar :)

---

### Post by onlytanmoy on 2007-11-24
thank u all for replying...i will try out the solutons u mentioned..in case i get stuck, i will again post in the thread..thanks again frends.

---

### Post by derby007 on 2007-11-24
> surely you mean who is Iarwain Ben-adar 
yes, yes, have you found him/her/it ? give me directions  :)

---

### Post by forestpixie on 2007-11-24
he lives near me - although my daughter swears he's a she and my son just wonders what's going on with that thing at the end of the lane :D

---

### Post by derby007 on 2007-11-24
I must drop by for a cup of tea, meet u by the standing stone !!

---

### Post by forestpixie on 2007-11-24
Cool - I'll be the hungry one with hairy feet :lolflag:

---

### Post by iust79 on 2007-11-24
I would like to install kiwi linux and windows xp home ed on the same coputer.
I've downloaded a live cd for kiwi linux and booted from it. when I tried to install it on the hard disk I've encountered the following problems:
   1) the installation wizzard had a page where I had to partition the hdd (windows was already install and had some othe partitions, too). It had two options: manualy and almost automaticaly (i think). on bouth gave me the warning that all the partition table could be lost. I created 2 new partitions (one / and a swap). But when I finished answering to that 7/8 configuration questions ...
  2) an error window appeared telling something about a problem with installing that could be fixed by burning the cd to less speed...
  3) after I rebooted I lost all the partitions created by windows :mad:

   Furtunatly I managed to recover them using testdisk-6.8 :)

   Now i would like to try again but:
       1) how can I  install linux without loosing again that partitions?
       2) how can I create and where on the hdd (a SATA of 250 Gb) the two linux partions. I have 1 Gb or RAM. How large should be the swap partion?


       Thanks!
                   I'm a noob in linux so be patient with me, pls :lolflag:

---

### Post by forestpixie on 2007-11-24
Firstly - welcome, 2ndly it might have been better to start a new thread but there you go.

I'm not sure about kiwi linux never heard of it, so not sure how it presents it's install options - but I would do the partitioning before you start the install - [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") can be downloaded, burnt as an iso and booted with - then you can resize and create a partition in the unallocated space.

Then when you go to install you'll have a partition to put it in

Conventionally you should have 2 times RAM I think as swap - but I have 1Gb of each and have no problems.

Before you do any resizing of your partitions make sure you have defragged the win install a couple of times first.

Most importantly make sure you have suitable backups before you start.

You should burn at slow speeds, especially if it's told you to do so ! - I do my iso burning at 4x

Hope that helps

---

### Post by iust79 on 2007-11-24
kiwi linux is  ubuntu linux costumized for Romanian users (they said is 99% ubuntu with some translations). 

I'll burn the live cd for linux again. When I downloaded it was nothing said about burning speed :(

I already have Gparted.

One more question. Does all this live cd has a bootloader too? something to allow me wich OS to load. I've read something on installing it on the first segment of the /boot partition and not on MBR (something related to the 8,5 GB limit or so). So on the free spacee on linux partion i'll create a new one for linux. but where to place it? before or after windows?
what about the filesistem? the live cd has more files sitem (I'll noticed riserfs , ext3 etc.) wich one will u recomand to use?   :confused:


                  10x

---

### Post by forestpixie on 2007-11-24
> kiwi linux is ubuntu linux costumized for Romanian users - guessed similar when I went looking!

No idea bout bootloader - I didn't worry too much when I originally had dual boot - so I just installed it as it wanted.

As far as file system to use - I've not been here long enough to even think about the different types myself, I use ext3.

---

