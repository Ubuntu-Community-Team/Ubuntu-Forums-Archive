---
title: "Can system updates be stored?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by davidwfox on 2007-06-25
I'm running U 7.04 on two computers at home - a laptop and a desktop. Every now and again I click the update pop-up and allow the systems to download and automatically install the updates. To save using up my rather meagre download limit, on a very slow internet line, can I download the updates onto, say, a thumb drive plugged into one computer, then use those files to update both computers?

If so, how do I achieve:
a)  The download and storage onto the thumb drive; and
b)  The installation of the stored files?

---

### Post by mikewhatever on 2007-06-25
All updates packages are downloaded /var/cache/apt/archives and stay there for 30 days or so. You can copy them using this command
> sudo cp /var/cache/apt/archives/* /copy_destination

I am not sure how to install them though.

---

### Post by lukew on 2007-06-25
> **mikewhatever said:**
> All updates packages are downloaded /var/cache/apt/archives and stay there for 30 days or so. You can copy them using this command


I am not sure how to install them though.

Just run update && upgrade  from the second machine and it will install them without downloading the files as you have copied the files into its cache.

---

### Post by davidwfox on 2007-06-25
Thanks Mike - that's a start. 

I just had a look in the archives directory, there's a hundred or so files in there, and that's a lot more than the last update contained. I need to be selective; I only want to store whatever is available with whatever's there as the new update, so I can use those files to update both computers. If I allow the update files to download, say, onto my laptop, is there some way to to then filter the files that I just downloaded and copy them onto the thumb drive so I can use them to update the desktop?

And of course, how to install them?

---

### Post by davidwfox on 2007-06-25
Luke - thanks, that takes it a step further. 

If I had the entire set of files on the thumb drive, with it now plugged in to the desktop, precisely what command would I enter so that the system knew to update && upgrade using the files from the thumb drive. Or do I just copy the lot into the same (archives) directory on the desktop and then issue the update && upgrade command?

---

### Post by lukew on 2007-06-25
> **davidwfox said:**
> Luke - thanks, that takes it a step further. 

If I had the entire set of files on the thumb drive, with it now plugged in to the desktop, precisely what command would I enter so that the system knew to update && upgrade using the files from the thumb drive. Or do I just copy the lot into the same (archives) directory on the desktop and then issue the update && upgrade command?

When you run update && upgrade.

The second computer will have a list of applications it knows to update (ie those which it has installed and those which have an update in the repository). 

When you go t upgrade it looks in the archive for any files which are already in place. (It only download files which are not within the archive which are noted as updated) it will then only install files which are marked as updated.

If for example you also copy application a; which is not installed on the second computer, and run update and upgrade; it will not be installed.

---

### Post by mikewhatever on 2007-06-26
Perhaps Lukew had in mind the following command
> sudo aptitude update && sudo aptitude upgrade
However, it seems that once the packages are in var/cache/apt/archives, only the second part is needed, because we do not want to read the sources, but upgrade only.

To select the desired packages, you can try sorting them by date. You may also want to delete the packages from var/cache/apt/archives, which is done with the following
> sudo aptitude clean

---

### Post by ambush_xx on 2007-06-26
You can use aptoncd
It can bak up all the packages to an iso image

You can either burn this or restore the image to the cache folder
open synaptic and select the origin tab at the bottm left
there should be some options for aptoncd seclt that and mark all upgrades

---

### Post by lukew on 2007-06-26
> **mikewhatever said:**
> Perhaps Lukew had in mind the following command

However, it seems that once the packages are in var/cache/apt/archives, only the second part is needed, because we do not want to read the sources, but upgrade only.

To select the desired packages, you can try sorting them by date. You may also want to delete the packages from var/cache/apt/archives, which is done with the following

You still need to do the update as apt needs to be made aware of any available upgrades.

The upgrade command once run will not download any files which it finds within the cache.

---

### Post by davidwfox on 2007-06-28
Sorry for the delay responding - I've had 2 - 3 rather hectic days.

Mike - the idea of sorting by date (post #7) sounds like what I had in mind when I asked (post #4) about filtering the files in the archive. That way I can select the newly arrived files, copy them onto the thumb drive, then plug the thumb drive into the other computer and use them to upgrade / update that machine.

So, what command do I use to sort the files by date?

---

