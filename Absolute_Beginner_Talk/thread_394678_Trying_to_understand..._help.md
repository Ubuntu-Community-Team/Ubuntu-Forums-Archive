---
title: "Trying to understand... help"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-27
Hey! Well, I guess I didn't set up my partition right cause my Ubuntu is telling me that I have no space left on my drive and because of that, I can't enter past my login. I am using now the live cd. Now, I read that you can't make your partitions bigger... right now, my home is 6G, my root is 3G and my swap (I didn't know what that was when set up my partitions) is 100G I was thinking that was where my files were going to go in lol. I guess I'm still in the learning process! So I will make all my partitions again, but can someone tell me how to separate them with a 120G hard drive? How much for home, root... swap? Cause all my music and pictures and movies are on my external hard drive, so that's why I know I'm suppose to have tons of space free on my 120G internal drive.

Thanks for the help!

---

### Post by Arby on 2007-03-27
How you partition your disk is very much down to personal preference. For 120Gb I would go with something like

```
/ = 10G #this is often called the 'root' partition, not to be confused with /root which is something else
Swap = 1-2G
/home = the rest of the disk
```

Basically "/" is where the operating system will be installed. /home is where you keep your personal stuff. Swap is used by the system as extra RAM. If your computer has lots of RAM you may never use any swap memory, but you should set some up just in case. The clue is in the name, if your computer runs out of memory then it 'swaps' some of it to disk i.e. it writes the information onto a spare bit of your hard drive so it can re-use that space. Then if you use something that is currently in swap it will be read back into RAM again. This process is pretty transparent to the user although you might notice a slight lag when things are being recovered from swap since reading from disk is a little slower.

Hope that made sense

Arby

---

### Post by az on 2007-03-27
> **julie_lebou said:**
> Hey! Well, I guess I didn't set up my partition right cause my Ubuntu is telling me that I have no space left on my drive and because of that, I can't enter past my login. I am using now the live cd. Now, I read that you can't make your partitions bigger... right now, my home is 6G, my root is 3G and my swap (I didn't know what that was when set up my partitions) is 100G I was thinking that was where my files were going to go in lol. I guess I'm still in the learning process! So I will make all my partitions again, but can someone tell me how to separate them with a 120G hard drive? How much for home, root... swap? Cause all my music and pictures and movies are on my external hard drive, so that's why I know I'm suppose to have tons of space free on my 120G internal drive.

Thanks for the help!

I'm a fan of the default installer option - let it parition your drive for you.  It will make one root partition and one swap partition.  You don't need a seperate home partition and you won't have this problem of making some partition(s) too small.  If everything is on one partition, you can share the drive space and will avoid such mistakes.

It is trivial to back up your home folder.  And less complicated than making a seperate home partition.

---

### Post by julie_lebou on 2007-03-27
Thanks for the help, now I understand what / home/ and swap is. Oh another thing... I guess that I will have to reinstall Beryl if I do this? If so, it sucks! It was so hard to get it working! ;-(

---

### Post by hyper_ch on 2007-03-27
If you start witht he LiveCD you should be able to alter the partition sizes with it... however make first a backup of your important data. Although normally it works like a charm there is always a slight chance of encountering a problem.

---

### Post by julie_lebou on 2007-03-27
But I can't make my partitions bigger I heard? You only can make them smaller?

---

### Post by hyper_ch on 2007-03-27
it's a two step-process... make the swap partition smaller and then the next one bigger :)

---

### Post by julie_lebou on 2007-03-27
I tried to do that.. I only could make it 1G bigger, not enough.. how come it's not working for me?

---

### Post by julie_lebou on 2007-03-27
Right now, I have a 98G unallocated in Gparted.. I wish I could just make home bigger with that

---

### Post by julie_lebou on 2007-03-27
Hyper... is it possible? am I doing something wrong^

---

### Post by Bachstelze on 2007-03-27
It would help if you posted a screenshot of your GParted window so we can see exactly how your partitions are set up.

---

### Post by dstew on 2007-03-27
You should be able to use that space to grow your /home partition. Is there another partition between the /home partition and the unallocated space? If so, you may need to move that partition out of the way, so that your /home partition can expand.

---

### Post by julie_lebou on 2007-03-27
Ok, I'm at my university right now, but when i'll be back home, I'll take a pic of my screen and post it here. It would be so much easier if I could just make my home bigger!

---

### Post by rich.bradshaw on 2007-03-27
Sorry, I know you are new but...

100G for swap! Hahahahahaha!

Ok, got that out of my system, I guess that makes sense, it's the bit that you can swap from Windows to Ubuntu right... :)

I have 512Mb RAM, and only have 512MB Swap, hardly ever gets used. In case you hadn't realised as well, swap is the same idea as virtual memory or the Windows page file, except that it is a seperate partition to ensure that it is always available.

---

### Post by zvacet on 2007-03-27
Download Gparted Live CD and you will be able to resize your partition way you want to.
[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

---

### Post by Bartender on 2007-03-27
Second the GParted recommendation.  You download GPLCD, and burn a bootable CD from the .iso download.  Same process as making the Ubuntu installer CD, if you did that.
Then boot from the GPLCD disc.
It's can be confusing (and stressful) to manuever in GPLCD at first, but once you figure out some basic steps it's kinda fun.
 
Try wiping the swap partition entirely.  Delete the partition so that it shows up as "Unallocated".  Then create your new swap partition.  You know how the partitions are mapped across the top of the page?  One of the funny little idiosyncracies I found in GPLCD is that you usually click on the partition map to tweak the partition.  Sometimes the partition map doesn't do anything, and you have to click on the text part below the map.  So if you're clicking on the map and nothing happens, try clicking on the text describing the partition on the lower half of the page.

---

### Post by julie_lebou on 2007-03-27
What's the difference between ''Gparted live cd'' and the Gparted program that I use with the ubuntu live cd?

---

### Post by Bachstelze on 2007-03-27
The GParted live CD is a live CD that has only GParted (and a few other basic tools) on it. So it is light and fast while Ubuntu Live CD has a whole desktop on it and takes forever to load.

It also has a more recent version of GParted so I would definitely recommend to use it instead of Ubuntu's live CD.

---

### Post by Toadmund on 2007-03-27
If you have 98g unallocated, just pick the option to have Ubuntu load itself into 'the largest available unallocated partition' (says something like that).
All of your swap and stuff will be automatically assigned.

Worked for me.

---

### Post by julie_lebou on 2007-03-27
This is the sreenshop of my gparted

[ATTACH]28390[/ATTACH]

---

### Post by julie_lebou on 2007-03-27
Ok, just so eveybody knows... it would be best for me to keep my stuff because i dont want to install beryl again, so if i chose to take the largest, is that going to keep all my stuff?

---

### Post by Bachstelze on 2007-03-27
Yes but it will be a bit more complicated than just resizing a partition. First, make a copy of the partition you want to grow in that huge free space you have using GParted's copy/paste feature. Then grow it so it takes the whole of it and finally edit your GRUB config and fstab so the system knows he must use this instead of the old one.

---

### Post by dstew on 2007-03-27
Expand hda1 toward the left so it starts just after the swap partition. gparted should be able to do that. Or, you could do two steps: 1) move hda1 so that it is just after the swap partition. 2) expand hda1 to the right after you have finished moving it.

---

### Post by Bachstelze on 2007-03-27
I prefer copying over moving since if something goes wrong, the old one will still be there and intact. If the new one is working fine then, you can delete the old one.

---

### Post by julie_lebou on 2007-03-28
Alright, got really sick and tired cause I really had to use my computer to do my projects for school, so I just reinstalled Ubuntu with good partitions this time! So THIS problem won't happen again! I'll be back when the next one shows up hihihi!

Thanks for the help!

---

