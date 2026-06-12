---
title: "WINE - help with dll"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-18
I've searched all over in the Ubuntu forums and via Yahoo, and have found one place that says Family Tree Maker can be made to successfully run in Ubuntu using WINE, however I have found no how-to for it anywhere.  Please understand I'm basically an idiot when it comes to a lot of this stuff!  The site I found was this:

[http://appdb.winehq.org/appview.php?iVersionId=3852&iTestingId=636](http://appdb.winehq.org/appview.php?iVersionId=3852&iTestingId=636)

So, I installed WINE via Synapics and then installed Family Tree Maker by using Wine file and double-clicking the executable on the CD to install it.  When I eventually got it in, it will start, but it gives this error right away:

"Cannot obtain version information for OLE2NLS.DLL.  You may need to put the file OLE2NLS.DLL in the SYSTEM directory within you Windows directory".

So, I found OLE2NLS.DLL in my Windows installation in Windows/system32, so I put it in the system32 folder under WINE in my home directory.  Same problem.  So, I copied it from there and put it in the system folder - same result.

When I click "OK" Family Tree Maker continues to start, but pieces of the Window get "lost" even I open a pop-up in it or something like that, as wherever the pop-up window was, WINE is not redrawing the FTM stuff after I exit the pop-up.

I would REALLY like to get this work as it is the only thing keeping a VM for Windows under Ubuntu.  I just put in ie6 via ies4linux so now even thought it is REALLY screwy video on somethings, but at least I can play the shockwave daily jigsaw now (stupid, huh??).:)

I really don't know what to do - does WINE expect info on dll's in the registry some how?  Also - the sight I found that said it would work said there were 4 dll's you had to copy - I only have 4 of them.  Perhaps it's because they say to use the Windows 98 dll's and my Windows installation is XP?

Thanks in advance for helping an old guy out!:):)

EDIT:   I ran Family Tree Maker from the command line to see if WINE would output any additional errors, but this is all I got:

dave@dave-ubuntu:~$ wine c:\\ftw\\ftw.exe
fixme:winspool:OpenPrinterW PRINTER_DEFAULTS ignored => (null),(nil),0x000f000c
err:x11drv:X11DRV_CreateWindow invalid window height -23
fixme:storage:StorageImpl_Commit (0x1c1500 1): stub
fixme:storage:StorageImpl_Commit (0x1c1500 1): stub
fixme:storage:StorageImpl_Commit (0x1c1500 3): stub
dave@dave-ubuntu:~$

---

### Post by anewguy on 2007-07-18
Bump.  I dunno - is there some form of limit to the number of questions you can ask here before people stop replying?

---

### Post by anewguy on 2007-07-18
bump.

---

### Post by anewguy on 2007-07-18
bump

---

### Post by anewguy on 2007-07-18
Can someone please help me with this or direct me to someplace that can? :) I've tried GRAMPS as a replacement for Family Tree Maker, and it's just personal taste but I don't like it.  I would also prefer not to have to copy over all of my images, etc., not to mention tools I have to build CD's with all kinds of stuff on them to send to my relatives.  Family Tree Maker is my last tie to Windows - I REALLY want to get it working in WINE so I can be Windows free!:)

Thanks!:)

---

### Post by smah77 on 2007-07-18
You might try looking for help in wine forums here: [http://www.linuxforums.org/forum/wine/](http://www.linuxforums.org/forum/wine/) or on irc.freenode.net in #winehq

---

### Post by cookies on 2007-07-18
Launch the app from the Terminal with the command

```
WINEDLLOVERRIDES="OLE2NLS.DLL" wine "C:\Program Files\PATH\TO\APP.exe"
```

And see what happens.

---

### Post by bodhi.zazen on 2007-07-18
From the site you posted this will work with Ubuntu 5.10 and wine 0.9.3

So .... first install Ubuntu 5.10 then wine 0.9.3 then re-install Family Tree Maker and follow these directions : > he fix is to use these files from a real Windows 98 installation:
OLE2.DLL
OLE2CONV.DLL
OLE2DISP.DLL
OLD2NLS.DLL

According to the same site this will not work with newer versions of Ubuntu or newer versions of wine.

If that fails, you may need to post as suggested by smah77

---

### Post by anewguy on 2007-07-18
> **smah77 said:**
> You might try looking for help in wine forums here: [http://www.linuxforums.org/forum/wine/](http://www.linuxforums.org/forum/wine/) or on irc.freenode.net in #winehq

Thanks!  I have been looking in Ubuntu forums for a WINE forum and never found it, so thank you!:)

---

### Post by anewguy on 2007-07-18
> **cookies said:**
> Launch the app from the Terminal with the command

```
WINEDLLOVERRIDES="OLE2NLS.DLL" wine "C:\Program Files\PATH\TO\APP.exe"
```

And see what happens.

Thanks for the reply!  I tried what you suggested but still get the same results.  Thanks anyway, though!:)

---

### Post by anewguy on 2007-07-18
> **bodhi.zazen said:**
> From the site you posted this will work with Ubuntu 5.10 and wine 0.9.3

So .... first install Ubuntu 5.10 then wine 0.9.3 then re-install Family Tree Maker and follow these directions : 

According to the same site this will not work with newer versions of Ubuntu or newer versions of wine.

If that fails, you may need to post as suggested by smah77

Thanks for the reply!  Since I am running 7.04, does that mean I will need to completely de-install it first?  Also, sorry for a dumb question, but is there a place to download Ubuntu 5.10?  I didn't realize I could click on the little icons on that page to get the details - I just went back and found what you were talking about - thanks!:)

Thanks to you and everyone who has replied!:)  I'm pretty green at this so there are probably some things that seem simple to others but I'm just not that knowledgeable.  I hope to be able to help out more in the future!:):)

---

### Post by bodhi.zazen on 2007-07-18
> **anewguy said:**
> Thanks for the reply!  Since I am running 7.04, does that mean I will need to completely de-install it first?  Also, sorry for a dumb question, but is there a place to download Ubuntu 5.10?  I didn't realize I could click on the little icons on that page to get the details - I just went back and found what you were talking about - thanks!:)

Thanks to you and everyone who has replied!:)  I'm pretty green at this so there are probably some things that seem simple to others but I'm just not that knowledgeable.  I hope to be able to help out more in the future!:):)

You do not need to un-install 7.04, just install 5.10 over the top ;)

[Ubuntu 5.10](http://old-releases.ubuntu.com/releases/5.10/)

And the old wine : [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803)

Scroll down to the very bottom of the page ;)

---

### Post by anewguy on 2007-07-18
We've been having some BAD storms here in northwest Illinois, so I finally decided that if I was just on wireless and left my laptop running on batteries I shouldn't be at too much risk, so I'm finally back here and just saw your post, bodhi.zazen:).  I really appreciate your help and will be following your links and trying things out a little later.  These storms have me pretty worried, but I did want to get back on before too much time went by so I could get your reply and say thanks!:):)

I'll let you know how it turns out!

---

### Post by bodhi.zazen on 2007-07-18
No problem. Just let us know if you get stuck somewhere :twisted:

---

