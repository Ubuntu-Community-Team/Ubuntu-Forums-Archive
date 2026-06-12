---
title: "Newbie Question on installing Ubuntu"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by skyhigh007 on 2005-11-28
Can you down load the Ubuntu software and installed on a windows PC ? or you need to use an CD and boot it from the Cd ?

---

### Post by Kvark on 2005-11-28
You can download an iso cd image and use the burn image feature of your burner program to burn the image onto a CD.

Then you need to boot from the CD you burned. A live CD will run Ubuntu without making any changes to your computer. An install CD will install Ubuntu on your hard disk. You can find iso images of both live and install CDs on the download site.

The tricky part of installing Ubuntu is to partition your hard disk and let Windows keep one part while you give the other part to Ubuntu so you can choose which system to load each time you boot up the computer. You might want to search the forums for a partition howto to read up a bit on that part first. The rest of the initial install is usually easy.

---

### Post by matthewstory on 2005-11-28
Not quite sure what the question is exactly, but you can download the image on a windows PC burn the image to a cd and then with the install disc create a partition for ubuntu and keep windows on the machine on its own partition.  Alternitavely you can download the live CD and boot straight from the disk.  If you can't get your computer to start either of these then it's probably the boot order, when your computer first starts up, before it loads windows hit F2 to go into set up and change the boot order so that it reads off the CD first, and then goes to the hard drive to boot.  Hope this answers your question.

Cheers,
matt

---

### Post by skyhigh007 on 2005-11-29
Thank you for your replay and i did what you guys have told me. During the installation, Ubuntu can not detect my networking configuration set up, it Cant detect the DHCP, so i skip the networking part. Second, when comes to partition, it asks me to partition the hard drive, but i already partition the hard drive. I have Drive C and Drive D and I want to install ubuntu under D drive. Looks like ubuntu cant tell whether the hard drive is partition or not. MY question is do i have to partition it again ? Also, How can i set up the DHCP so that ubuntu can recognize it ? 

Thanks

---

### Post by startailpro on 2005-11-29
Intresting. Do you a pci network card in the pc and a network port that is not connected to any pci. Or do you have just one. You say u want it on the d drive. Well linux does not see the dirives like windows so the are usually klike sda or ide. to get it on to the d drive i think u have to activate the boot flag so that is where the ubuntu will be loaded to and u have to change the system to ex3, rf, linux systems. ntfs and fat are window systmes. U will also need to have swap drive which does come in handy. If can spare 5gb for the spare drive grat if not you can put ti to 1gb or even 512mb, i cannot really remember what it the swap drive is used for but it is very handy. :KS

---

### Post by skyhigh007 on 2005-11-29
Is there an Manual on how to do that ? im new to everything

---

### Post by startailpro on 2005-11-29
I not quite sure. I think i saw one in the wiki ubuntu.

---

### Post by Brunellus on 2005-11-29
I'm not sure I understood everything in this thread, but I will try to explain.

1) yes it is possible to download ubuntu CD images in Windows.  To turn those images into bootable CDs, you must burn them as images, rather than merely copying the downloaded files onto a CD.

2) partitioning.  Linux and Windows use different and (mostly) mutually-incompatible filesystems, so linux will not and cannot install on a partition that has been formatted by windows.  If the partition is empty, you can delete the partition and the ubuntu installer will format the partition in the way it needs to be done.

3) documentation.  search for "dualboot howto" in these forums, and also consult the ubuntu wiki for installation help.

---

### Post by jasay on 2005-11-29
aysiu always points people to this site:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")
It has nice pretty pictures that guide you thorugh every step of the installaion.  Just read the first page and then lcik the button on the left that corresponds to your setup to see the installtion guide.

---

### Post by skyhigh007 on 2005-11-29
I'm trying to install Ubuntu 5.04 Hoary.  The link you have provided helps me a bit. when comes to partition diskas, the ubuntu version i have does not have the resize IDE1 master , partition (hda1) "and use free space" features.

---

