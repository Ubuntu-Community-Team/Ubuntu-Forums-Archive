---
title: "Mounting an unformatted or Fat32 Drive"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by shaunk62 on 2006-10-26
Hi All,

Well been on Ubuntu for nearly 5 days now and cant stop raving to everyone about it, especially the support that is on offer here. Makes it a joy to come over to the "alliance" from the dark side,

However...

BOZO here (me) has a spare 13Gb partition that I was going to put my data on from the old windoze XP system (I am still dual boot capable) and have the data there accessible to both XP and Ubuntu.

Well I went into SYSTEM -> Admin -> Disks, identified the drive /dev/hda8 formatted it as FAT32 vfat

Thats when I ran into a bit of trouble (sorry to be telling a story but I want you to have the facts)

I then had to create the access path and of course I made it /home. Well then of course I lost the system. I Ctrl Alt Backspace but then it would not let me in so I did a reboot in recovery. I then came back into Ubuntu and everything worked fine.

However I still dont have access to the /dev/hda8 as I dont know what access path to use. Ideally I would like to expand the memory capacity for the Home Drive while, as I said providing access to the drive for when i HAVE to go into XP (not sure why that would be except to access some old data in OneNote)

Sorry for being such a bozo, but i have trolled around the forums after doing a search for Mount Drives and have not come across anything that clarifies this for me

Thanks in advance, and rest assured there will be many converts coming (although I guess that means maybe more bozo questions ... sorry about that bit)

Shaun

---

### Post by taurus on 2006-10-26
Okay. so you want to mount /dev/hda8 so you can share files between Ubuntu and XP.  Well, here is what you need to do.  You first need to edit your /etc/fstab so that partition will be mounted automatically with read and write permissions for everybody at boot time.  To edit it, open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo cp /etc/fstab /etc/fstab.bak <-- make a backup copy just in case...
gksudo gedit /etc/fstab
```
Scroll down to the end and add the following line to it.

```

/dev/hda8   /media/share   vfat   defaults,umask=0000   0   0

```
Save it and run these three commands at the prompt.

```
sudo mkdir /media/share
sudo mount -a
df -h
```
You now should see an entry for your /media/share...

---

### Post by kidders on 2006-10-26
Hi there,

Sounds like you mounted your filesystem on top of your entire /home directory!! (Not a smart idea!) Try mounting it someplace less ... well ... critical to your system's health -- a brand new directory maybe?

Once you've found a nice home for it, modify your /etc/fstab so it mounts there by itself in future :-)

---

### Post by shaunk62 on 2006-10-26
Guys what took you so long to respond ... KIDDING ... I cant believe how great the support is here. Wish the whole world operated like this and perhaps there would be a lot less violence (hmm philosophical and probably not appropriate here)

Just for clarity I do already have a media/share for the NTFS partition which is read only which i am cool with ... I understand that it would make sense to find a new home for it maybe call it something like /xpubuntudata or whatever ... so do I need to do the things that were mentioned in the immediate response but call the /media/share   media/xpubuntudata

(that is do I substitute xpubuntudata for share)

Thanks again for making this transition something I wish I had done MONTHS ago

---

### Post by taurus on 2006-10-26
If you don't want to mount it as /media/share, then yes, you can change it to /media/xpubuntudata.  Don't forget to change that too in /etc/fstab and create a mount point it for as well.  In other words, just follow my post from above except use "xpubuntudata" in place of "share".  ;)

---

### Post by shaunk62 on 2006-10-26
Well that was pretty painless ...  of course I dont really know what all the lines meant but that is a learning experience

Now I guess that that is going to be accessible from XP as a drive letter of some description.

Thankyou so much for your help I REALLY appreciate it

---

### Post by taurus on 2006-10-26
> **shaunk62 said:**
> Well that was pretty painless ...  of course I dont really know what all the lines meant but that is a learning experience

You don't really need to know it right now.  Just spend your time learning how to use it first and when you are good at it, then learn more about the ins & outs of the system.

> 
Now I guess that that is going to be accessible from XP as a drive letter of some description.


Yes, Your Windows will be able to mount it just like it would.  It's probably D;, E:, F:,etc.

> Thankyou so much for your help I REALLY appreciate it

Wait until you get my bills!!!  :twisted:

---

### Post by shaunk62 on 2006-10-26
Ah you see that does not scare me as I come from the Windows world where that is a standard statement except if you call MS you have to pay BEFORE they solve your problem. Here in Australia it is a minimum of $40 per call, AND they dont guarantee to fix the problem as it is always someone elses problem...

Of course you do need to make money some how unless you are operating on a karmic basis in that the world will provide :) 

It will be great when I am able to help others... btw if you need any business help just give me a holler (thats what I do) barter is a wonderful thing

---

### Post by taurus on 2006-10-26
For now, it's going to be a free service and we will try hard to solve your problems and we promise we won't blame it on somebody else.  You can take that to the bank...  8)

---

### Post by grandmaster on 2006-10-27
Worked for me 

Thanks

---

