---
title: "New Installation"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by coho on 2008-03-28
Hi,

I'm brand new to Linux. I just installed Linux Ubuntu 7.10 on my windows xp machine on a second harddisk and everything went according to plan. No glitches and all the hardware was found by Ubuntu and is working, including wireless and a Kingston USB data traveler. I have set up my desktop and installed a lot of programs, including aMule and everything is working like a charm.Although I'm very familiar with the windows file system, I'm having some trouble finding my way around in the Ubuntu file system. As an example I simply cannot find a directory in the file system for aMule with the GUI, I can locate the aMule directory without any trouble on the console by cd(ing) from the home directory. Where in the file system is aMule installed?
I'm very happy with the way Ubuntu is working on my machine and I haven't booted into windows for days now.

---

### Post by Bachstelze on 2008-03-28
The aMule executable is most likely located in /usr/bin. You should have no need to go there, though, what are you looking for, exactly?

---

### Post by mikewhatever on 2008-03-28
Pretty much all of it is in /usr/share and /var/lib. Try <locate amule>.

---

### Post by Scotticus42 on 2008-03-28
> **coho said:**
>  Where in the file system is aMule installed?

I think what you might be interested in is where files being uploaded and downloaded by aMule are going.  If this is the case, its in your home directory at: /home/<your user name>/.aMule/

That "." at the beginning of the directory name causes it to normally be hidden.  It will show up in a terminal window if you type "ls -al" or if you select "View Hidden Files" in the Ubuntu analog of Windows Explorer.  Also, you can type "ctrl-l" (that's control lowercase-L, a bit hard to make out in this font) in the explorer program to get the location bar, and type the path in there to go the aMule directory.

> **coho said:**
> 
I'm very happy with the way Ubuntu is working on my machine and I haven't booted into windows for days now.
I'm glad to hear you're enjoying it.  I have been using Ubuntu for a few years now, and I really like it too.  Still trying to get off windows completely, though.  If it were not for Windows computer games, I would probably use Ubuntu 100% of the time.

I hope this helps.  If not, let us know!
--Scotticus

---

