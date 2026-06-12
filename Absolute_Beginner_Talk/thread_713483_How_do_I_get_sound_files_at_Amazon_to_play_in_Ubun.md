---
title: "How do I get sound files at Amazon to play in Ubuntu 7.1?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Alethinon61 on 2008-03-02
Hi,

I'm an extreme newbie to Linux -- so new, in fact, that I have yet to do a single useful thing with a terminal.  My question: 

How do I get sound files to work that are found at Amazon and similar sites which use Real Player and Windows Media Player to play sound?

I know it has something to do with codices, whatever they are:-)   Please note that if you are going to direct me to a terminal, then please word your instructions as though you were speaking to an elementary school student!  (i.e. step by step, with each step clearly explained in simple terms).

Thanks,
~Sean

---

### Post by JoshuaRL on 2008-03-02
No need for the terminal on this one.

Go to Add/Remove Applications.  Search for "restricted".  You'll be looking for a package called "Ubuntu Restricted Extras".  Also, search for "helix".  That will install the helix player, capable of playing Real media.

---

### Post by Alethinon61 on 2008-03-03
> **JoshuaRL said:**
> No need for the terminal on this one.

Go to Add/Remove Applications.  Search for "restricted".  You'll be looking for a package called "Ubuntu Restricted Extras".  Also, search for "helix".  That will install the helix player, capable of playing Real media.

Thank you, JoshuaRL, that worked beautifully for Windows Media Player at Amazon's site.  I'm not sure what to do to get the Real Player music excerpts working, but I'm good for now.  I noticed that I didn't have to install Adobe Flashplayer to make YouTube work after following your instructions.

~Sean

---

### Post by linuxisfree on 2008-03-03
> **Alethinon61 said:**
> Thank you, JoshuaRL, that worked beautifully for Windows Media Player at Amazon's site. I'm not sure what to do to get the Real Player music excerpts working, but I'm good for now. I noticed that I didn't have to install Adobe Flashplayer to make YouTube work after following your instructions.
 
~Sean
 
Maybe this could help you understand why the flash videos at YouTube worked without installing Flashplayer:
 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 
EDIT: Welcome to UbuntuForums, by the way:D

---

### Post by JoshuaRL on 2008-03-03
> **Alethinon61 said:**
> Thank you, JoshuaRL, that worked beautifully for Windows Media Player at Amazon's site.  I'm not sure what to do to get the Real Player music excerpts working, but I'm good for now.  I noticed that I didn't have to install Adobe Flashplayer to make YouTube work after following your instructions.

~Sean

Go to Add/Remove again and search for "helix".  Then install the Helix Player.  It should allow you to play Real Media files.

---

### Post by ugm6hr on 2008-03-03
This is the most thorough how-to about internet streaming media in Gutsy:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by ubuntu-freak on 2008-03-03
> **JoshuaRL said:**
> No need for the terminal on this one.

Go to Add/Remove Applications.  Search for "restricted".  You'll be looking for a package called "Ubuntu Restricted Extras".  Also, search for "helix".  That will install the helix player, capable of playing Real media.

 
As far as I know, Helix and it's browser plugin doesn't support proprietry formats anymore.
 
Nathan

---

### Post by JoshuaRL on 2008-03-03
> **reassuringlyoffensive said:**
> As far as I know, Helix and it's browser plugin doesn't support proprietry formats anymore.
 
Nathan

Well thanks for the info, I'm using 64bit so it won't work for me anyway.

Sorry for the misinformation.

---

### Post by ubuntu-freak on 2008-03-03
> **JoshuaRL said:**
> Well thanks for the info, I'm using 64bit so it won't work for me anyway.

Sorry for the misinformation.

 
I was guilty of it until I did some research. The people behind Helix actually made RealPlayer for Linux, and after that they stopped supporting RM formats in Helix.
 
Nathan

---

### Post by JoshuaRL on 2008-03-03
So does that mean he should just try the player from the Real site?  I haven't tried that myself.

---

### Post by ubuntu-freak on 2008-03-05
> **JoshuaRL said:**
> So does that mean he should just try the player from the Real site?  I haven't tried that myself.

 
MPlayer's plugin should work, but it's a bit random with RM streams sometimes. There's a link to a RealPlayer deb in my how-to, it's packaged for Fiesty but works in Gutsy (the Gutsy package had the plugin missing).
 
Nathan

---

