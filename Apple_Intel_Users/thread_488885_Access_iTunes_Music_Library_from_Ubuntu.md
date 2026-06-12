---
title: "Access iTunes Music Library from Ubuntu?"
date: 2007-06-30
forum: Apple Intel Users
---

### Post by makaira on 2007-06-30
Is this possible? All of my music, which is not very much at all, is stored on the OS X partition. Is there any way I can get Rythmbox to access it?

---

### Post by thully on 2007-06-30
To do this, you will need to mount the OS X partition in Ubuntu.
Do this by adding a line to the /etc/fstab:

/dev/sda<whatever number partition OS X is - 2 for first partition normally>  /mnt  hfsplus defaults 0 1

Then, on the OS X partition go to your home directory , Get Info, and grant read permissions to everybody. That way Ubuntu has permission to access the music.

After that, in Ubuntu install the restricted extras (in add/remove programs).  That way you can play back MP3/AAC files.

Finally, in rhythmbox (or whatever music player you use),  add the directory /mnt/Users/<your user id>/Music/iTunes Music

That should do it.  If you have songs purchased from the iTunes store, these won't play unless they're iTunes Plus tracks - blame the DRM for that.

---

### Post by makaira on 2007-06-30
I followed the steps and I'm able to access the iTunes music library. The problem, however, is that all of the music is .m4a and since I have no decoder for that I am unable to play the music. I'm beginning to look for decoders now, but if you have any further suggestions please let me know.

---

### Post by makaira on 2007-06-30
I found a solution of sorts [here]("https://help.ubuntu.com/community/RestrictedFormats/AAC"). But, despite having installed these codecs, only Ryhthmbox can play the files. Amarok still says there is no way to decode them.

---

### Post by benanzo on 2007-07-01
I believe Amarok uses XINE as it's default audio backend.  In order to play restricted formats like m4a you'll need to install **libxine-extracodecs**.

```
sudo apt-get install libxine-extracodecs
```

If using Ubuntu with GNOME (not Kubuntu) I personally recommed sticking with Gstreamer-based multimedia apps like Rhythmbox, Banshee, BMPx, Listen, Exaile or Quod Libet.  All of which are excellent.

Rhythmbox is my personal favorite because of it's stability, simplicity and overall excellent functionality.  Some don't like it because you can't use it to sync with your iPod, but I find GTKPod does a much better job of that than any multifunction media player/library manager currently does.

---

### Post by TimB21 on 2007-07-01
> **thully said:**
> To do this, you will need to mount the OS X partition in Ubuntu.
Do this by adding a line to the /etc/fstab:

/dev/sda<whatever number partition OS X is - 2 for first partition normally>  /mnt  hfsplus defaults 0 1

Pardon my lack of knowledge but I'm a total newbie to Linux and Ubuntu.

I'm using Parallels and I have 4 unpartitioned internal drives (Bays 1 through 4) on my Mac Pro,  How would I mount Bay 2 (or Bay 3) for example?

Thanks! :)

-=Tim=-

---

### Post by TimB21 on 2007-07-02
Any ideas here? :)

Thanks!

-=Tim=-

---

### Post by cyberdork33 on 2007-07-02
I didn't think you could mount actual devices in parallels, rather only drive images. Now you could partition/format the drive with your mac and then store an image file on it...

---

### Post by TimB21 on 2007-07-02
With XP running inside Parallels I shared a Mac drive and then mapped it to a drive letter within XP.  I was hoping for something similar with Ubuntu. :)

Thanks!

-=Tim=-

---

### Post by ev5unleash1 on 2007-07-02
Try to see if Apple has a iTunes program for linux, I doubt it though.

---

### Post by cyberdork33 on 2007-07-02
> **TimB21 said:**
> With XP running inside Parallels I shared a Mac drive and then mapped it to a drive letter within XP.  I was hoping for something similar with Ubuntu. :)

Thanks!

-=Tim=-
  Unfortunately, I think that is specific to a windows guest... but you can do something similar via ssh:
[http://ubuntuforums.org/showthread.php?p=1932551](http://ubuntuforums.org/showthread.php?p=1932551)

---

### Post by ronocdh on 2007-07-02
> **ev5unleash1 said:**
> Try to see if Apple has a iTunes program for linux, I doubt it though.
Aside from being patently absurd, this doesn't at all address the issue the OP or TimB21 was having. Re: Tim's problem, I'm with Cyberdork in not knowing whether it's possible in emulation, but my gut says it has to be. Surely there's a way to access your OS X files from Ubuntu (running in emulation), yes? If you don't have this feature, I don't see the value in running in virtualization. Shouldn't you even be able to copy/paste between the OSes?

---

### Post by benanzo on 2007-07-02
Yes, you can share a folder from Ubuntu (virtualized) with Samba and access that folder from OS X the same as if you were accessing any shared folder.  All access comes from the network, not locally.

---

### Post by thully on 2007-07-02
On this topic - look to see if Parallels has a "shared folders" feature for Linux.  If so, use it.  I do know VMware Fusion has such a feature, and it works well.  Otherwise, you're stuck with futzing with Samba/Windows file sharing...

---

### Post by TimB21 on 2007-07-03
> **benanzo said:**
> Yes, you can share a folder from Ubuntu (virtualized) with Samba and access that folder from OS X the same as if you were accessing any shared folder.  All access comes from the network, not locally.

Can you point me in the right direction for getting started with Samba?

Thanks!

-=Tim=-

---

### Post by cyberdork33 on 2007-07-03
rather in depth, but here:
[https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html)

There are plenty of threads on this I am sure you might try searching a bit in the rest of the forum.

---

### Post by makaira on 2007-07-04
> **thully said:**
> To do this, you will need to mount the OS X partition in Ubuntu.
Do this by adding a line to the /etc/fstab:

/dev/sda<whatever number partition OS X is - 2 for first partition normally>  /mnt  hfsplus defaults 0 1

Then, on the OS X partition go to your home directory , Get Info, and grant read permissions to everybody. That way Ubuntu has permission to access the music.

After that, in Ubuntu install the restricted extras (in add/remove programs).  That way you can play back MP3/AAC files.

Finally, in rhythmbox (or whatever music player you use),  add the directory /mnt/Users/<your user id>/Music/iTunes Music

That should do it.  If you have songs purchased from the iTunes store, these won't play unless they're iTunes Plus tracks - blame the DRM for that.

Well, since the first time I successfully did this I have done a fresh install of Fiesty. Now, I'm following the same exact instructions, yet getting a different outcome. For some reason the Macintosh HD is not mounting, despite my having done the same exact thing as before.

---

### Post by thully on 2007-07-04
I dunno - that seems like the right way to configure it to me.  Just make sure the mount point for the Mac partition i correct - that's all I can think of...

---

