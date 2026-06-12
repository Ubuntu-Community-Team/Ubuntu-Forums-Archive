---
title: "uninstalling"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-11
I had enough from ubuntu
as much as I loved it but it's not gonna work with me
it keeps on freezing, my sound is clear
and im facing loads of probs
so im gonna uninstall it

so I opened partitionmagic and I formatted drive G (on which I installed ubuntu on)
restarted, but it told me that that I have some sort of grub error: error 17 :confused:
so I installed ubuntu back so I can access my winxp

so what should I do to uninstall it and remove the OS selector at the start?

---

### Post by apollo2011 on 2005-07-11
The problem you are having is that GRUB is installed on the MBR of the first hard drive.  GRUB is expecting to find Ubuntu where it originally was and now you uninstalled it so GRUB is lost.  You will need to remove GRUB from the mbr or overwrite or...

---

### Post by trash on 2005-07-11
Hey Snitz, I so remember feeling how you feel when I started with linux. I trashed it more than a couple of times until oneday just decided to install it somewhere and play with it only when i was bored or just felt in the mood.
Maybe you are just pushing yourself too much? Why not just leave it on a partition and go back to it once and a while... use XP in the meantime.

Sorry this doesn't really answer your post, but I think it would be a waste just to ditch linux and all you have learnt so far... cuz you'll be back in a few months lol... well maybe;).

---

### Post by Snitz on 2005-07-11
[QUOTE=trash]Hey Snitz, I so remember feeling how you feel when I started with linux. I trashed it more than a couple of times until oneday just decided to install it somewhere and play with it only when i was bored or just felt in the mood.
Maybe you are just pushing yourself too much? Why not just leave it on a partition and go back to it once and a while... use XP in the meantime.

Sorry this doesn't really answer your post, but I think it would be a waste just to ditch linux and all you have learnt so far... cuz you'll be back in a few months lol... well maybe;).[/QUOTE]
 I think u're probably right mate
i'll leave it till now
but the thing is im looking for a nice OS that fits me 
and I think ubuntu is the one but it's not compatible with my motherboard as it seems and it's driving me crazy
and im so sick of windows products
the reasons that I wanna remove ubuntu is that I wanna keep on trying different OS' till I find a nice one
im now trying PCBSD

---

### Post by dcraven on 2005-07-11
Reboot with your XP CD in the drive and choose rescue. Windows will overwrite the MBR and you can forget this experience completely.

---

### Post by Snitz on 2005-07-11
[QUOTE=dcraven]Reboot with your XP CD in the drive and choose rescue. Windows will overwrite the MBR and you can forget this experience completely.[/QUOTE]
 as simple as that?

---

### Post by dcraven on 2005-07-11
[QUOTE=Snitz]as simple as that?[/QUOTE]
 Have I ever lied to you before?

---

### Post by Snitz on 2005-07-11
I rebooted and I didn't see any "rescue" option

---

### Post by Snitz on 2005-07-11
I rebooted and I didn't see any "rescue" option
it doesn't exist
so how to remove the GRUB?

---

### Post by Nanaki on 2005-07-11
[QUOTE=Snitz]I rebooted and I didn't see any "rescue" option
it doesn't exist
so how to remove the GRUB?[/QUOTE]
 Two ways:

1. use the before suggested rescue mode (boot from Windows XP disc and choose the appropiate option). When in that mode, type "fixboot" or something like that. You should recognise an option in the "help"-list.
2. use a Windows 98 bootdisk and boot from it. Type "fdisk /mbr".

edit= I tried my share of distro's. Ubuntu is the way to go, believe me.

---

### Post by Snitz on 2005-07-11
> Type "fdisk /mbr".
what will this command do?

> edit= I tried my share of distro's. Ubuntu is the way to go, believe me.
I know it is, but it's causing me problems :(

---

### Post by Nanaki on 2005-07-11
[QUOTE=Snitz]what will this command do?


I know it is, but it's causing me problems :([/QUOTE]
 Maybe try again with Breezy. :)

Anyway, it will reset your MBR. If you only have windows os's installed, this doesn't matter, as Windows keeps it boatloader on the partition of the first Windows installed, not in the MBR. So you basically delete GRUB.

---

### Post by apoc.feuer on 2005-07-12
Hi Snitz, 

Another way that I have tried over the weekend is:

1) Do you know the manufacturer of the hard drive is?

2) Below are a two links to the hard disk manufacturer website: 

-[Maxtor](http://www.maxtor.com/portal/site/Maxtor/menuitem.3c67e325e0a6b1f6294198b091346068/?channelpath=/en_us/Support/Software%20Downloads/ATA%20Hard%20Drives&downloadID=22)

-[Seagate](http://www.seagate.com/support/seatools/index.html)  

3) Seagate will require you to have a register with them while Maxtor will be pretty straight forward. 

4) Download the ultilities (Powermax for Maxtor) and (Seatools for Seagate) 

5) You either burn the iso image or use a floppy disc, Seagate you will need 2 floppy discs while you need one floppy disc for Maxtor

6) You can do a quick format or a low level format (Might take you at least 2-3 hours) with the options inside, thereafter you hard disk will be as good as new. 

Hope the above suggestion helps. (Assuming you are using a desktop PC or else you need to do a search on IBM hard drive main webpage if yours a lappyI tried it with my lappy earlier...personally Ubuntu is great and as this distro grow the help and support will be better too. (I personally find this forum useful too)

---

