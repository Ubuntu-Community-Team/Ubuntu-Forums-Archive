---
title: "how to copy home folder from one drive to another"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by neatokino on 2008-02-15
I have my home folder on a separate partition on my internal hard drive (running Gutsy) .  

I've bought a new internal hard drive and freshly installed gutsy, also with a separate home partition.  How do I take the /home partition off the old drive and copy it on to the new one?

TIA
Michael

---

### Post by taurus on 2008-02-15
Maybe this will give you a hint, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).

---

### Post by neatokino on 2008-02-15
Thanks, Taurus... that's the site I used to set up the /home partition, but it doesn't say anything about how to copy the /home from one disk to another.    Do I just boot off the new drive and use Nautilus to move the /home from one disk to the other???  Can I copy the /home drive from a disk while I'm booted up with it, or do I need to boot from a Live CD to make the copy?   

The psychocats site has a great how-to for setting up your home drive on a separate partition, but they don't tell you how to utilitze that separate partition when you upgrade or, in my case, want to put the /home partition on a new, bootable drive.

Any ideas on how to do it?

thanks again

Michael

---

### Post by drs305 on 2008-02-15
Here is a link to moving a home partition. If that is what the previous link was trying to do, sorry.

It doesn't appear a simple copy would work completely, as this link states:
Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide ...

and then lists the command line inputs.

Here's the link:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by neatokino on 2008-02-15
Thanks again, but I'm still not getting the information I need.  I don't need to know how to set up my hard drive with /home in a separate partition.  I've already done that, and it works well.

What I'm trying to do is to **replace the /home partition on one hard drive with the /home partition on another hard drive**.  

I'll explain this as simply as I can:

I have gutsy running on a 750GB hard drive, newly installed, with /home in a separate partition.  That drive is currently installed in my computer;  it boots up and everything runs fine.  Since gutsy was freshly installed, the settings in the /home partition have not yet been set up the way I want them.

I also have gutsy installed on a 200GB drive, with /home in a separate partition.  The /home partition DOES contain all my settings the way I want them (and has documents, music, etc.)   This had been the primary drive in my system, but I'm replacing it with the 750GB drive.  

The information on the /home partition of the 200GB drive is what I want to put on the /home partition of the 750GB drive.  Once that information is transferred, I'll either keep the 200GB drive as a bootable backup or reformat it and use it for something else.

[I]All I need to know is how to copy the information on the /home partition of the 200GB drive to the /home partition of the 750GB drive.  That's it. 
[/I]
Can anyone tell me how best to do this?

Thanks in advance again,

Michael

---

### Post by billgoldberg on 2008-02-15
"What I'm trying to do is to replace the /home partition on one hard drive with the /home partition on another hard drive. "

Just copy the files using nautilus (or whatever filemanager you use).

I would only copy the folders you really need (the folders with your themes in, documents, videos, music, ...)

---

### Post by neatokino on 2008-02-15
Thanks, bill goldberg... one more question before I do this:

which drive should I use to boot with when I do the copying?  

Do I need to boot from a Live CD, mount both drives, and then copy them using Nautilus?  Or can I boot from the new drive (the 750GB drive), mount the 200GB drive, and then use Nautilus to transfer them?

Also, I don't know which parts of the /home folder I really need... am not sure where everything is, but I do want to transfer my repository settings, my emerald and compiz themes and settings, my media settings, firefox bookmarks, and so forth in addition to specific files like documents and music.  Since I don't know where everything is, I figured that transferring everything in the /home folder would be sure to give me what I need.  Is there a problem with that?

[note:  I booted from the new drive, used Nautilus, was able to easily transfer music, docs, etc. and found hidden files which I'll transfer once the music is done-- I THINK I've figured it out]

Thanks to everyone who's helped me out here!!!

---

