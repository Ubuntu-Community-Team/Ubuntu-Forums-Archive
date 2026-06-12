---
title: "hard drive"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by bondi007 on 2007-07-08
ive got a hard drive with all my movies on that i used in xp but it doesnt show up in ubuntu can i get it to show up

---

### Post by dreadlord_chris on 2007-07-08
> **bondi007 said:**
> ive got a hard drive with all my movies on that i used in xp but it doesnt show up in ubuntu can i get it to show up

As long as you are just wanting to **read** off the drive - pretty easy.
From a terminal type the following and post the results:
```

sudo fdisk -l

```

---

### Post by starcraft.man on 2007-07-08
> **bondi007 said:**
> ive got a hard drive with all my movies on that i used in xp but it doesnt show up in ubuntu can i get it to show up

Easy question. I assume its either Fat32 or NTFS. Either way, both are addressed by this [guide]("http://www.psychocats.net/ubuntu/mountwindows"). Follow along and I'm sure you'll understand :). Oh and if it is NTFS and you want read write access (you don't have that by default, only read access) please consult the link at bottom.

[Psychocats]("http://www.psychocats.net/ubuntu/") is a great resources.

---

### Post by bondi007 on 2007-07-08
i tried sudo fdisk -1 and it came up giberish

---

### Post by Outrunner on 2007-07-08
That's a lowercase L not a 1 (one).

```
sudo fdisk -l
```

---

### Post by bondi007 on 2007-07-08
so its sudo fdisk -L

---

### Post by bondi007 on 2007-07-08
it came up with my internal hard drive with ubuntu on it but what about my external hard drive

---

### Post by starcraft.man on 2007-07-08
> **bondi007 said:**
> it came up with my internal hard drive with ubuntu on it but what about my external hard drive

If you have an external USB drive plugged in, it should appear below in the list. Please look at the [guide]("http://www.psychocats.net/ubuntu/mountwindows") I linked to, it has clear pictures to understand. You should as the guide shows, see something like this from "sudo fdisk -l":

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1911 15350076 7 HPFS/NTFS
/dev/hda2 1912 19457 140938245 5 Extended
/dev/hda5 1912 14716 102856131 83 Linux
/dev/hda6 14717 17278 20579233+ 83 Linux
/dev/hda7 17279 17404 1012063+ 82 Linux swap / Solaris
/dev/hda8 17405 19457 16490691 83 Linux
```

If you have more than one drive, the internal is usually the first and the externals listed underneath in separate sections.

If it doesn't appear as a section with the command, lets make sure its connected and found right. Please put this command in the terminal and copy everything that is displayed after, then include it in the your next post.

```
lsusb
```

---

### Post by bondi007 on 2007-07-08
it cam up id 00000000000
like 5 times

---

### Post by starcraft.man on 2007-07-08
> **bondi007 said:**
> it cam up id 00000000000
like 5 times

Are you sure you have the USB plug in? If all entries (most computers have between 6 and 8 plugs, should have an equal number of entries) are 0s it doesn't recognize the drive. Try another plug. If it still doesn't work, I dunno. Most USB mass drives work without any trouble on Ubuntu. I just know how to fix it once its recognized, if its not detecting you got a problem. Post the model of the USB drive, and we will see if we can figure it out.

---

### Post by bondi007 on 2007-07-08
i bought the hard drive enclosure and put a hard drive in it

---

### Post by starcraft.man on 2007-07-08
> **bondi007 said:**
> i bought the hard drive enclosure and put a hard drive in it

Ok then, what was the hard drive you put in it (its model) and what was the enclosure you used? Can you check to make sure everything's plugged in right (i.e. HD to the enclosure, USB cable not damaged). If that checks, try a different USB port on your computer, then retry the command. Something must be the problem, I'm afraid USB drives are not an expertise of mine.

---

### Post by bondi007 on 2007-07-08
it works in xp and my hdd is seagate 120gb ide and the enclosure has a cd with it but its windows only

---

### Post by Myglaren on 2007-07-08
> **bondi007 said:**
> it works in xp and my hdd is seagate 120gb ide and the enclosure has a cd with it but its windows only

You shouldn't need the CD anyway - mine just worked in XP. Vista and Feisty.

---

### Post by bondi007 on 2007-07-08
its working now 

STRANGE

---

### Post by starcraft.man on 2007-07-08
> **bondi007 said:**
> its working now 

STRANGE

Ok then, thats good, might have been loose connector to the enclosure. If it didn't mount automatically, please check my link on the first page and mount it following all the pictures and text. Have a nice time :).

---

### Post by bondi007 on 2007-07-08
i opened the enclosure and fiddled with the connections and it worked 

thank you

---

