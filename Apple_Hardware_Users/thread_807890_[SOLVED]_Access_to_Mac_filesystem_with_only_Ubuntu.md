---
title: "[SOLVED] Access to Mac filesystem with only Ubuntu running"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by mfox on 2008-05-26
Since I haven't been able to configure MOL to work in Hardy (yet; see [this post]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=807303")), I would at least like to be able to read and write to the Mac side of my PowerBook.  I know how to do that on an Intel Mac with Ubuntu running on VMware or Parallels using file sharing and smb.  Would it be the same on my PB with only Ubuntu running, or is there a better way?

---

### Post by cyberdork33 on 2008-05-26
> **mfox said:**
> Since I haven't been able to configure MOL to work in Hardy (yet; see [this post]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=807303")), I would at least like to be able to read and write to the Mac side of my PowerBook.  I know how to do that on an Intel Mac with Ubuntu running on VMware or Parallels using file sharing and smb.  Would it be the same on my PB with only Ubuntu running, or is there a better way?
you just mount the HFS+ filesystem in linux. 
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

Please put an indication that you are on  PPC hardware in your thread title to get the best help.

---

### Post by frog_pilot on 2008-05-26
you dont need the command line for this at all.

Simply install hfsplus, hfsprogs and hfsutils: ```
sudo apt-get install hfsplus hfsprogs hfsutils
```

If you ve done that you can mount your hfsplus drives simply by clicking on them in nautilus. or via the places menu (Places > Media (or similar)).

volumes where you disabled journaling before on the osx side will mount in r/w mode. the ones with journaling enabled will mount read only.

thats the whole thing. no tweaking of fstab or kernel modules necessary.

---

### Post by mfox on 2008-05-26
Thanks, frog_pilot, and also, cyberdork33.  I'll get those hfs utilities and try that first.  I have two volumes on the Mac side of my PowerBook and if possible, I will turn off journaling on the one I use to run as an alternate startup for system checking and repair so I can read and write to it.

---

### Post by cyberdork33 on 2008-05-26
> **mfox said:**
> Thanks, frog_pilot, and also, cyberdork33.  I'll get those hfs utilities and try that first.  I have two volumes on the Mac side of my PowerBook and if possible, I will turn off journaling on the one I use to run as an alternate startup for system checking and repair so I can read and write to it.
My link is just a bit more technical, but it is basically giving the same information.

---

### Post by mfox on 2008-05-26
Actually, cyberdork, I needed that article to tell me how to do this.  Even after all of the utilities were installed, the Mac partitions were not automatically mounted, and I had to mount them manually from the Terminal.  It did work, but is there something I should be doing to get them to be mounted automatically?

---

### Post by cyberdork33 on 2008-05-27
> **mfox said:**
> Actually, cyberdork, I needed that article to tell me how to do this.  Even after all of the utilities were installed, the Mac partitions were not automatically mounted, and I had to mount them manually from the Terminal.  It did work, but is there something I should be doing to get them to be mounted automatically?
I wouldn't mount them automatically anyway. Don't mount them in Linux unless you need something specifically, and mount them read only when you do. Once you have all the utilities and such installed, they should show in the Places menu, and double-clicking on them will mount them. If that is not working for you, I do not know what other steps you may need to take.

---

