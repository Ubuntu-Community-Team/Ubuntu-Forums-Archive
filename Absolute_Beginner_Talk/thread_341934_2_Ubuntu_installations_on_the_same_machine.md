---
title: "2 Ubuntu installations on the same machine?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-01-19
Hello all,

I have been using Breezy for a wile and now I want to test Edgy.
Is it possible to install Edgy beside Breezy and then select what to start at startup?

I have 60GB freespace left, 1 partion where Breezy is installed.
So can I install Edgy aswell?

---

### Post by ieee488 on 2007-01-19
yes.
I had Ubuntu 5.10 and Ubuntu 6.06 both on the same PC for a brief time until I
decided Ubuntu 6.06 was all that I needed.

---

### Post by az on 2007-01-19
Yup.

The installer will offer to create a new partition for Edgy with that free space.  Just make sure that is the option offered, and not "Erase Entire disk".

If the option is not offered (for whatever reason), you can go to manual partitioning, and then pick your current partition.  Shrink it to create free (unpartitioned) space.  Then go back and the installer will once again offer you the partitioning options and this time, they should include the USE FREE SPACe one.

You should give yourself at least three or four gigs to play around with the new system.  Use more, but that is the minimum.

---

### Post by iluminate on 2007-01-19
> **azz said:**
> Yup.

The installer will offer to create a new partition for Edgy with that free space.  Just make sure that is the option offered, and not "Erase Entire disk".

If the option is not offered (for whatever reason), you can go to manual partitioning, and then pick your current partition.  Shrink it to create free (unpartitioned) space.  Then go back and the installer will once again offer you the partitioning options and this time, they should include the USE FREE SPACe one.

You should give yourself at least three or four gigs to play around with the new system.  Use more, but that is the minimum.

Thank you very much for your help and well written aswell. Lets hope Edgy provide me with the option of making a partition of free space.
Hmmm...maybe I shall not use everything whats left on the disc, then breezy will have 0 left =) Or is the swap enough?

---

### Post by taurus on 2007-01-19
Both versions can share the same swap partition so no need to create another one just because you install Edgy.

---

### Post by iluminate on 2007-01-19
> **taurus said:**
> Both versions can share the same swap partition so no need to create another one just because you install Edgy.

Did not know that! Thank you Taurus! Saved me another 2 GB of space then =)

---

### Post by taurus on 2007-01-19
I once had three Linux distros on a same machine and they were all using the same 1GB swap partition.  Everybody was happy.  ;)

---

### Post by bodhi.zazen on 2007-01-19
You likely do not need a swap sapce of > 1 Gb :p

2 Gb is likely overkill

---

### Post by directcharitycontribution on 2007-01-19
i read something about ["User-mode Linux (UML)"]("http://uml.jfdi.org/uml/Wiki.jsp").

as i am very cautious about traceability would this be effective?

---

### Post by shareMenaPeace on 2007-01-19
> **ieee488 said:**
> yes.
I had Ubuntu 5.10 and Ubuntu 6.06 both on the same PC for a brief time until I
decided Ubuntu 6.06 was all that I needed.
Im just curious why people want to stick to old versions?

When the next ubuntu release comes im hopefull to update edgy without a glitch :)

On a sidenote i had to create a media stream computer for a bar, i took an older machine (amd7) and ubuntu want boot.
So i used xubuntu which is designed for lower machine cpus -- performance.
So if i would install a 2nd OS i woould recommend at least kubuntu for some more linux impressions.

Xubuntu is very cool too, and looks like all the software runs on it aswell (eg. openOffice).

Cheers

---

### Post by shareMenaPeace on 2007-01-19
> **bodhi.zazen said:**
> You likely do not need a swap sapce of > 1 Gb :p

2 Gb is likely overkill

Err so i got 2.xgig now hehe...is this bad in someway or jsut not nessasary?

---

### Post by iluminate on 2007-01-19
I really do not know why its set to 2GB....maybe it said min. 1 GB and I set it to 2 GB.
I am doing the resizing of the free space on the disk as we speak.
First try I received an error...during the resize (Applying pending operations screen) !!!!
Now doing the second try as we speak!
What is the difference between file system ext3 and ext2 ?
Do I have to specify the /swap again or does it already know where the swap is?

The setup looks like this now -
dev/hda1 ext3 50 GB boot
New partition ext3 17 GB  (creating it as we speak....Live CD is a fantastic invention) =)

dev/hda2 Extended 2.16 GB
    -dev/hda5 linux-swap

---

### Post by az on 2007-01-19
> **iluminate said:**
> I really do not know why its set to 2GB....maybe it said min. 1 GB and I set it to 2 GB.
I am doing the resizing of the free space on the disk as we speak.
First try I received an error...during the resize (Applying pending operations screen) !!!!
Now doing the second try as we speak!
What is the difference between file system ext3 and ext2 ?
Do I have to specify the /swap again or does it already know where the swap is?

The setup looks like this now -
dev/hda1 ext3 50 GB boot
New partition ext3 17 GB  (creating it as we speak....Live CD is a fantastic invention) =)

dev/hda2 Extended 2.16 GB
    -dev/hda5 linux-swap

If you are using the automatic partitioning, it will figure out how much swap to use.  It's likely that you used that the first time and it figured you needed that much.  For example, if you have one gig of ram and lots of disk space, it will give you a two gig swap space.

Ext2 is and Ext3 filesystem without a journal.

If you pick guided partitioning, it will find the swap.

You can't hibernate (suspend-to-disk) and share a swap.  The contents of your ram is put in the swap space.  If you boot another OS which uses that space, your saved session will be lost.

---

### Post by hal10000 on 2007-01-19
> Do I have to specify the /swap again or does it already know where the swap is
you have to tell th partitioner to use you swap on /dev/hda5 (don't forget the leading slash)
> What is the difference between file system ext3 and ext2 ?
ext3 is a so called "journaling file system" (like ntfs, reiserfs, xfs and others). Journallig file systems can boot faster than others because there's no need for extensively file system checks during boot time. The advantage of ext3 is it' downward-compatibility with the older ext2 file system.

---

### Post by iluminate on 2007-01-19
EEhhmm....how long should it take to resize the partition from 70GB to 55GB ?
Still on the first step, resizing..1 hour has elapsed! Normal?

---

### Post by iluminate on 2007-01-19
> **azz said:**
> If you are using the automatic partitioning, it will figure out how much swap to use.  It's likely that you used that the first time and it figured you needed that much.  For example, if you have one gig of ram and lots of disk space, it will give you a two gig swap space.

Ext2 is and Ext3 filesystem without a journal.

If you pick guided partitioning, it will find the swap.

You can't hibernate (suspend-to-disk) and share a swap.  The contents of your ram is put in the swap space.  If you boot another OS which uses that space, your saved session will be lost.

Thanks! I am not using the automatic partition feature, but the manual one. The automatic did not show correct amount of GB!!
Is there a bug or something in Edgy partitioning? Because its still resizing the partition....and now it has finished...:-D 

Now mounting points...heh..
My guess is that the new install shoudl be mounted on "/" root 
The swap has the checkbox "reformat" selected by default...do a reformat?
The old partition, containing Breezy has mount point /media/hda1 <<< this Ok?

---

### Post by iluminate on 2007-01-19
OK thank you all very much for your help! I am up and running and GRUB seemed to find the old Breezy version, and it looked OK.
During the setup Breezy (old version) was mounted on /media/hda1, and now in Edgy I can browse my files...which is a good sign! Then I know I have not formated them =)
Many thanks!

---

### Post by dannyboy79 on 2007-01-19
> **shareMenaPeace said:**
> Im just curious why people want to stick to old versions?

When the next ubuntu release comes im hopefull to update edgy without a glitch :)

On a sidenote i had to create a media stream computer for a bar, i took an older machine (amd7) and ubuntu want boot.
So i used xubuntu which is designed for lower machine cpus -- performance.
So if i would install a 2nd OS i woould recommend at least kubuntu for some more linux impressions.

Xubuntu is very cool too, and looks like all the software runs on it aswell (eg. openOffice).

Cheers

don't mean to hi-jack the thread but could you tell us what you to ubuntu to make it a media streamer? what ended up being the "player" for the media that you were streaming from xubuntu? I am asking because I can't for the life of me get xbmps (or whatever that special prototcol is) or ccxstream to work in linux. No matter what my xbox media center 2.0 will not see the stream even though it's set to autodiscover it???

---

### Post by shareMenaPeace on 2007-01-19
> **dannyboy79 said:**
> don't mean to hi-jack the thread but could you tell us what you to ubuntu to make it a media streamer? what ended up being the "player" for the media that you were streaming from xubuntu? I am asking because I can't for the life of me get xbmps (or whatever that special prototcol is) or ccxstream to work in linux. No matter what my xbox media center 2.0 will not see the stream even though it's set to autodiscover it???

Installed this with automatix along with some codecs
vlc 
exile
rythem box
realplayer
media player

I dont know the protocols you refering to but maybe 1 of the codec packs instlled them?

---

### Post by dannyboy79 on 2007-01-19
> **shareMenaPeace said:**
> vlc 
exile
rythem box
realplayer
media player

ok, so those are what you installed to play the media. now what did you have streaming it??? or did you misspeak and have not really setup a media streaming xubuntu install? when you say media streamer, that would mean that you have content on your xubuntu machine that you want to be displayed (streamed) onto another device. so maybe you can explain better as to what you did for this bar.

---

### Post by shareMenaPeace on 2007-01-19
> **dannyboy79 said:**
> ok, so those are what you installed to play the media. now what did you have streaming it??? or did you misspeak and have not really setup a media streaming xubuntu install? when you say media streamer, that would mean that you have content on your xubuntu machine that you want to be displayed (streamed) onto another device. so maybe you can explain better as to what you did for this bar.
I meant to stream i.e. a radio stream with rythembox music player, from the internet.

---

