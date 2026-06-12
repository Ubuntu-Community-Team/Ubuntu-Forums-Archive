---
title: "Real-time folder mirroring"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by DarwinDarak on 2005-11-13
I've been looking for ways to mirror folders for backup and found no success.  Being a newbie, the documentation for fam, gamin made no sense to me.  I heard that gnomevfs and rsync would be used together somehow, but I have no idea how to even begin.  Can anyone give me any pointers?

Thanks,

Darwin

---

### Post by davmac on 2005-11-13
Unless I misunderstand you're requirements I'm not sure realtime mirroring is what you need. If it is real time, as soon as you b*gger up a file, you'll find your mirror copy b*ggered too won't you?

I use a script that runs rsync everytime I log in and takes a mirror copy of my home directory. Just shout up if you want a copy but in essence the rsync command I use is;

rsync -av --max-size=90000000 --exclude='*.mp3' --exclude='*.bz2' \
    --exclude='*Cache*' --exclude='*.thumbnails*' \
    --exclude='*.fonts*' --exclude='*.themes*' --exclude='*lost+found*' \
    --exclude='*metafiles*' \
    /home /destdirectory 

The max-size parameter stops me mirroring anything over 90MB and the exclude parameters stops the mirroring of the stuff that would take too long or that I don't care about.

HTH,

Dave Mac

---

### Post by DarwinDarak on 2005-11-13
Sorry for being unclear.  This is for a hotel.  I'm not that worried about the data being corrupted, just the our staff keeps coming up with creative ways to crash the Windows OS.  So even if the data is safe, I can't access it conveniently.  So I'm thinking of having a Linux box monitor the smb directory and copy any changes.  When a problem occurs, I can just reinstall the windows computer with no data loss.  Rsync seems to be very useful in the copying, but I'm having problems in the monitoring.

Thanks again,

Darwin

---

### Post by davmac on 2005-11-15
Ahhha! Sounds perfectly sensible. Not something I've done myself but there is an article about this very subject at [http://www.linuxfocus.org/English/March2001/article199.shtml](http://www.linuxfocus.org/English/March2001/article199.shtml)

It is not specific to Ubuntu but, on first glance, offers a reasonably detailed explanation of how to set up FAM and IMON, Although it looks like IMON requires a kernel recompile. This should be covered elsewhere on the forum.

Hope this helps,

Dave Mac

---

### Post by megamania on 2005-11-16
[QUOTE=davmac]Just shout up if you want a copy but in essence the rsync command I use is;

rsync -av --max-size=90000000 --exclude='*.mp3' --exclude='*.bz2' \
    --exclude='*Cache*' --exclude='*.thumbnails*' \
    --exclude='*.fonts*' --exclude='*.themes*' --exclude='*lost+found*' \
    --exclude='*metafiles*' \
    /home /destdirectory 

The max-size parameter stops me mirroring anything over 90MB and the exclude parameters stops the mirroring of the stuff that would take too long 
[/QUOTE]

Dave Mac, I'm shouting up! :)

What I'm looking for is a command to create a mirror of my home directory (delete files deleted on source, add new/updated files) to a second hard disk.

If that's not the complete script, can I ask you to post the full version?

---

### Post by DarwinDarak on 2005-11-17
That link was great, but I had some problems using FAM like it suggested.  I've already tried to use FAM, but for some reason, when installing FAM, it requires to removal of pretty much everything.  Is there are reason for this?

Thanks,

Darwin

---

### Post by poptones on 2005-11-17
gam is already installed in ubuntu and pretty much everything on the desktop depends on it. gam is a subset of fam. Functionally it is a replacement for it, so when you ask to install fam you are asking to remove gamin...

Here's a command line tool that talks to fam:

[http://fileschanged.sourceforge.net/](http://fileschanged.sourceforge.net/)

There is no package in the repository but it builds in a snap if you download the source. to build it you will need libgamin-dev, help2man, and (of course) build-essentials.

---

### Post by davmac on 2005-11-19
[QUOTE=megamania]Dave Mac, I'm shouting up! :)

What I'm looking for is a command to create a mirror of my home directory (delete files deleted on source, add new/updated files) to a second hard disk.

If that's not the complete script, can I ask you to post the full version?[/QUOTE]

Here you go.

Dave Mac

---

### Post by megamania on 2005-11-20
[QUOTE=davmac]Here you go.

Dave Mac[/QUOTE]

That's very interesting and hopefully I'll manage to come up with something working for me.  :)

Thank you VERY much.

---

### Post by DarwinDarak on 2005-11-20
fileschanged works PERFECTLY, it's just what I needed.

Thanks so much,

Darwin

---

