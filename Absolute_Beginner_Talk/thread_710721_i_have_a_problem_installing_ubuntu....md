---
title: "i have a problem installing ubuntu..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by iwallet on 2008-02-28
ok, i looove linux... and i just joined this forum for advice on computers...
i remember reading about people that would have problems installing ubuntu and i would think geeze.. its so simple how can you get it wrong...
well fate has had it that i just cant seem to install ubuntu...
i recently bought a new laptop, hp dv9700z..
i have a amd turion 64 x2 2.4 gHz
2g of ram...
nvidia 8400m gs
and 2 hard disks, about 160g each
now when i ordered this laptop i was planning to make 2 separate partitions, a small-as-possible one for vista and the rest ubuntu..
i never considered the fact that there are two hard disks.. so now im planning to give each OS a hd.
vista is already installed on the main one.. and i read on the booklet that came with the computer that the second hd is not set to have a OS installed on it, so im guessing i have to get in there and set it to be a master instead of a slave. rite??!
well besides that, my problem is that i have downloaded ubuntu twice (thinking maybe it missed some file the first time) tryed to at least get to the part where it asks me where to install it... all it gives me is the first screen where it gives me 30 seconds to pick something... so i pick install, then it goes loading kernel... and then my screen just goes black... the disk spins for a while then stops... i left it like this for some time but nothing... what could be the problem??
i bought this laptop for ubuntu... why cant i get it at least to the installation part?!?!
can anyone help??! please (((

---

### Post by sx5622 on 2008-02-28
Sounds like a pretty kickin' laptop!

Since you just got the laptop and likely don't have a bunch of files you want to keep, if I were you, and I don't know for sure if you can do this with vista -  I would format both drives using ubuntu, only install ubuntu on one drive, and then install vista on the other one.  Or partition the one and leave 20 gigs or so for vista and the rest a fat32 partition.

---

### Post by Nythain on 2008-02-28
download the "alternate install" iso... via bittorrent if possible... burn at slowest freaking speed known to man... and give that a whirl... im not saying the iso is bad, but it never hurts to burn it right... im mainly saying that the alternate install iso might work better for ya... then again, it might not...

another option, as i think this whole "black screen of DOOM!!!" is mainly related to gutsy... if all else fails, you could try downloading and installing feisty then upgrading to gutsy instead of just installing gutsy, but that would be a last ditch effort if no one else can provide any better options besides "alternate install iso"

---

### Post by brettg on 2008-02-28
OK, I have a similar setup here. This is what I did. I don't know about your hp but my laptop's 2nd hdd sits in the optical drive bay meaning I cant install stuff on the 2nd hd from cd/dvd.

Warning: I am assuming /dev/sda and /dev/sdb here. Your machine might be different than mine so it is up to you to correctly identify each of your physical disks.

What you need;

Vista installation media (not a "recovery disk")
Ubuntu cd
vmware workstation (linux version) with trial key

Steps:

1) install Ubuntu to the first hd (most likely /dev/sda)

2) Install vmware workstation

(If you need to swap the CD drive for the HD do it here)

3) Give users write access to the second hd device(s):
         sudo chmod 666 /dev/sdb*

4) Create a new Vista VM using "Custom" instead of "Typical" settings :
         When it comes time to configure the hdd, choose "Use a physical drive"
         and "Entire Disk", pointing it to /dev/sdb
 
5) Mount the virtual CD drive to an iso image of the Vista DVD and install Vista in the VM

6) Make a grub entry for the vista installation:
         Because Vista believes it is installed on the first hd, you need to fool it 
         into thinking your 2nd hd is the 1st one using the map statement in grub

         title Windows Vista
         map (hd0) (hd1)
         map (hd1) (hd0)
         rootnoverify (hd1,0)
         chainloader +1


If all goes well you should have a bootable vista partition which you can also load as a virtual machine. If you don't want to purchase a proper vmware key you can use vmware player to open the vmx file and it will work fine once set up.

Good luck

---

### Post by iwallet on 2008-02-29
to answer [COLOR="Blue"]"sx5622"[/COLOR]
i will leave that as my final option because what [COLOR="Blue"]"brettg"[/COLOR/] is saying sounds good..
as for "Nythain" i have tried the alternate install... it too has stopped as a certain point... ill will give this a try tomorrow night.. or maybe sunday.. because now i have to write an essay for school :(((
thanks to all!!

---

