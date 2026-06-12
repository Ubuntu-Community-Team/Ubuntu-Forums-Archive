---
title: "Move Ubunu to new hard drive..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by reset3x on 2007-05-15
Hi all... I am trying to move my Ubuntu install to a new hard drive.... I've scoured the forums and can't get this to work.... I want to move my installation from a 20 gig ide drive to an 80... when i followed the directions here : [http://ubuntuforums.org/showthread.php?t=256665](http://ubuntuforums.org/showthread.php?t=256665) I had noting but headaches.... My 20 gig  drive shows up as hda and my 80 gig hdb... I've been using Ubuntu for 5 months now and would hate to re-install...  Can anyone help me with this one???

---

### Post by oilchangeguy on 2007-05-15
> **reset3x said:**
> Hi all... I am trying to move my Ubuntu install to a new hard drive.... I've scoured the forums and can't get this to work.... I want to move my installation from a 20 gig ide drive to an 80... when i followed the directions here : [http://ubuntuforums.org/showthread.php?t=256665](http://ubuntuforums.org/showthread.php?t=256665) I had noting but headaches.... My 20 gig  drive shows up as hda and my 80 gig hdb... I've been using Ubuntu for 5 months now and would hate to re-install...  Can anyone help me with this one???

is the drive getting full? i've got 6.06 on a 30gb, and it uses less than 5gb.

---

### Post by L Campbell on 2007-05-15
> **reset3x said:**
> Hi all... I am trying to move my Ubuntu install to a new hard drive.... I've scoured the forums and can't get this to work.... I want to move my installation from a 20 gig ide drive to an 80... when i followed the directions here : [http://ubuntuforums.org/showthread.php?t=256665](http://ubuntuforums.org/showthread.php?t=256665) I had noting but headaches.... My 20 gig  drive shows up as hda and my 80 gig hdb... I've been using Ubuntu for 5 months now and would hate to re-install...  Can anyone help me with this one???

Are you really sure that a 're-install' is such a big deal?

I can understand that if you have a dial-up modem, it might be but, if you can burn a CD, or if you have a pen drive, its not too difficult to back up the stuff you want to 'take with you' to the new install.

---

### Post by oilchangeguy on 2007-05-15
> **L Campbell said:**
> Are you really sure that a 're-install' is such a big deal?

I can understand that if you have a dial-up modem, it might be but, if you can burn a CD, or if you have a pen drive, its not too difficult to back up the stuff you want to 'take with you' to the new install.

yes it's a big deal, if someone has everything setup the way they want it. it's not that reinstalling ubuntu is a big deal, it's everything else that'll have to be reinstalled. and i hate to say this, but this is where the windows world beats the linux world. because in doing a windows reinstall most of your programs are on a cd, easy to reinstall. with linux you'll have to remember where you found everything, add/remove, automatix, synaptic, etc. it could turn into a major headache.

---

### Post by reset3x on 2007-05-15
Thanks oilchangeguy... The problem is the the drive is 4 years old and is strarting to whine... I suspect a bearing failure..... And you're right.... I don't want to have to reinstall all of my software...

---

### Post by oilchangeguy on 2007-05-15
> **reset3x said:**
> Thanks oilchangeguy... The problem is the the drive is 4 years old and is strarting to whine... I suspect a bearing failure..... And you're right.... I don't want to have to reinstall all of my software...

i'm not sure if something like norton ghost would work, or if there is a product like this made for linux. and depending on how much space your current install uses, there is plenty of free backup/storage on the web. most give at least 5gb free. for example aol has a free program called xdrive. i don't know if you can back up the entire drive with these type's of programs, or just certain things, like my documents folder.

---

### Post by gohanssjn on 2007-05-15
Look for instructions on how to backup using **partimage**.  Then restore to the new drive, expand the partition, and compute away :D

Basic partimage instructions are here: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Here's a detailed idea :D :

Download a LiveCD and boot it.  Install partimage.
Make a partition on the 80gb drive to restore too, at least 20gb (lets call this pA).
Make another partition to write your image too, say another 20gb (pB).
Use partimage to backup the 20gb drive to pB.
Restore the image on pB to pA.
Boot, and make sure everything is working, you may have to reinstall GRUB and point it to the new drive.
Once it all works, delete pB.
Expand pA to the new size (80gb or smaller, whatever you want!)

That should do it.

---

### Post by oilchangeguy on 2007-05-15
> **gohanssjn said:**
> Look for instructions on how to backup using **partimage**.  Then restore to the new drive, expand the partition, and compute away :D

found this howto:
[http://www.g-loaded.eu/2006/01/06/partition-images-with-partimage-and-partimaged/](http://www.g-loaded.eu/2006/01/06/partition-images-with-partimage-and-partimaged/)

see partimage @ [www.partimage.org](www.partimage.org)

---

### Post by gbesso on 2007-05-15
You could try partimage from the systemrescuecd livecd: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")
You can also get it on your ubuntu install using ```
sudo apt-get install partimage
```
However, it doesn't support creating images of mounted partitions so you should use systemrescuecd, or the ubuntu livecd.

Note that partimage backs up partitions by sectors rather than actual files, so you can't extract/view files without using the image to restore a partition, and you will need to have an appropriate partition to restore into(one with a relatively similar size)

EDIT: oilchangeguy beat me to it ;)

---

### Post by pyromithrandir on 2007-05-15
You don't need to use partimage. It's pretty simple to do this without it, really. First off, you need to partition your 80 GB drive, if you haven't already.
Use > sudo fdisk /dev/hdb and just make sure you make at least one big partition to house all of your new stuff. There's no real hard in making it just one big partition, though, so you can do that. It's the easiest.
Then you have to format it, with something like> sudo mkfs.ext3 /dev/hdb1
Once you've done that, you'll need to boot to a livecd to copy everything from your old hard drive to your new hard drive. Once you're on the livecd, > sudo mkdir /mnt/oldhd /mnt/newhd
sudo mount /dev/hda1 /mnt/oldhd
sudo mount /dev/hdb1 /mnt/newhd
Then, just > sudo cp -a /mnt/oldhd /mnt/newhd That'll copy everything and keep permissions in tact, so it'll be just like old times. 
If you're going to move your new hard drive into hda position, then you're all set, otherwise you'll have to change where it says hda to hdb in a couple of files, most notably /etc/fstab.

Edit: Whoops! Forgot to mention that you'll need to install grub on your new hard drive. 
> sudo grub-install --root-directory=/mnt/newhd/ /dev/hdb

---

### Post by reset3x on 2007-05-16
Thanks pyromithrandir!!! That did the trick!!

---

