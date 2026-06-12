---
title: "Need advice regarding XP----&gt;Ubuntu"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Irv88 on 2008-04-17
Ok, so I have my laptop which I use most of the time running Ubuntu and it has for a while. I now feel comfortable with Ubuntu enough so that it does what I want and with such great communities and guides, it's easy enough to do the stuff I would usually no be able to do. I'd just like to say i'm pretty bad with computing but I know how to follow a instructions flawlessly.

I now wish to put Ubuntu on my desktop, which is were I have all my music, films, documents. As with my laptop I prefer it only to have one OS so I do not wish to have windows on a seperate partition.

**My question is, what is the simplist way in which I can install Ubuntu and keep the "my documents" folder from windows, but wiping everything else?** I would apreciate it if someone could explain how to do each part of the process.

Thanks in advance, I had a flick through previous posts and couldn't find what I was looking for.

---

### Post by SunnyRabbiera on 2008-04-17
well the best way is to get an external hard drive or burn your documents on a CD/ DVD.
when you tell ubuntu to use the entire disk it will use the entire disk, remember linux and windows use different filesystems and ways of doing things so what you ask is kind of impossible unless you backup or dual boot.

---

### Post by Irv88 on 2008-04-17
> **SunnyRabbiera said:**
> well the best way is to get an external hard drive or burn your documents on a CD/ DVD.
when you tell ubuntu to use the entire disk it will use the entire disk, remember linux and windows use different filesystems and ways of doing things so what you ask is kind of impossible unless you backup or dual boot.

This is a problem though as I don't have a external HD to use, and the file is far too large for CDs (older pc doesn't have a dvd burner). I'm talking about 150gb size of the My Documents.

---

### Post by Moop on 2008-04-17
You might want to start off with a dual boot. Then you could import all your XP stuff you want to save and when you have things the way you want, you can dump XP. 

Dual booting isn't that bad if you rarely use the 2nd os. It gets old fast though if you need to keep going back and forth. Just my two cents.

---

### Post by Tatty on 2008-04-17
I believe there is a "migration assistant" when you install ubuntu which will copy across your my documents to your new Ubuntu install.

HOWEVER: this is not to be trusted.  There is always the chance of failure when making such a big change as installing a new OS.  So you really do need to back up all of your important data before installing ubuntu.

There arent really any other options for you other than getting an external hard drive and putting all your my documents on there.  They are pretty cheap to get nowadays and it is always useful to have a backup device.  The only other thing you could do is back up all your work to another machine on your network.

---

### Post by ace007 on 2008-04-17
I agree, just Dual boot with the Windows Drive Mounted and you can make Bookmarks to your documents folder so they are readily accessible from Ubuntu.  Do you need help with the automounting process?

---

### Post by Irv88 on 2008-04-17
Yeh I do I guess, At the moment I have the "test Ubuntu first" desktop up, and am looking at all my files through the file system, however I decided maybe I could cut and paste to the desktop on Ubuntu then go for full install, firstly would this even work? Secondly, I can't as I don't have enough room left on my pc, supposidly.

---

### Post by ace007 on 2008-04-17
EDIT: Sorry, I think I got ahead of myself with the post below.  You dont have Ubuntu installed yet on your desktop?  If that is the case you need to use the LiveCD's Partition Editor (gparted) to create some space for Ubuntu.  

1.) Defrag Windows!
2.) Boot Ubuntu LiveCD
3.) Go to System>>Admin>>Partition Editor
4.) Select your hard drive (If it is the only one it should be something like /dev/hda1)
5.) Resize the main NTFS partition.  To do this you choose resize/move and then you can slide the end of the NTFS partition to the left to create space.  You can also use the text boxes for more accurate resizing.  If you have 10 GB of space, that should be more than plenty for Ubuntu.  We will also need to create a 1 GB partition for the swap file (optional, but recommended...) so add 1 GB to whatever you choose to give Ubuntu.
6.) Create Swap Space.  Select the newly unpartitioned space and choose create a partition.  You want to create a swap space that is roughly 1 GB.  The filetype should be "swap".
7.) With the remaining space, we will later create an ext3 partition.  Hold off on that for now.Select apply changes.
8.) You can now Install Ubuntu.  **_[COLOR="Red"]WARNING[/COLOR]_** Make sure on Step 4 that you choose "Guided: Use largest contiguous free space".  This will format and install Ubuntu on that 10 GB of empty space we made in the Partition Editor.
9.) Enjoy!
 


If you do not have enough space to make copies of every single thing in your documents, then the only alternatives would be to use another source of storage temporarily.  The issue is that you need to convert the windows partition (NTFS) into a Ubuntu partition (ext3).  There is no way of doing this without erasing everything that was on the NTFS partition.  It is possible for Ubuntu to read/write an NTFS partition however.  So the logical solution is to just mount the NTFS partition in Ubuntu.  You will never know that it wasn't a part of Ubuntu.

There is a process that can be done to have it work automatically after you boot up Ubuntu.  This process is called auto-mounting, and involves editing the fstab file.  This is trivial and I can even do it for you if you want to post the results of:

```

sudo fdisk -l

```

And paste your current fstab by opening it with:

```

sudo gedit /etc/fstab

```

---

### Post by Irv88 on 2008-04-17
Urgh Ok, thanks for your instructions, however I got to "move slider" bit and then got stuck... as I can't move the slider, theres also an error symbol next to the partition, and under information alot of cluster errors.

---

### Post by ace007 on 2008-04-17
is the entire partition colored?  Or partly colored and the rest is white?  If there is no white space that means the HDD is like 99% full, and you cant make space for Ubuntu on it.  If it is NOT full, I would try using the text box instead of the slider. Just tell it to end 10 GB lower than it was.  It may be an issue with the Partition Editor as well.  I've never had an error, but who knows.  Try posting the error or googling what it means.

---

### Post by Irv88 on 2008-04-18
I managed to borrow a flat mates HDD and transfer my files, got my ubuntu looking as sexy as my laptops, thanks all for posting replies.

---

