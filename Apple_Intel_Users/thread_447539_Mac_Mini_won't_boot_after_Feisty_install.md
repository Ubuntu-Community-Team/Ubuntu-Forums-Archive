---
title: "Mac Mini won't boot after Feisty install"
date: 2007-05-18
forum: Apple Intel Users
---

### Post by ike on 2007-05-18
Hi,

I installed Feisty in my intel mac mini without any problems. Support for this platform has really improved a lot since edgy! Really impressive.

But, the guide I was reading didn't mention rEFIt, so I didn't install that before I installed Ubuntu, and now my mac won't boot at all. I have tried holding the Alt key down while booting, but that just gives me a grey screen with a mouse pointer.. If I just start it normally i get a grey screen with a blinking folder icon with a question mark.

How can I make the mac boot into OSX so that I can install rEFIt? Preferably without reinstalling OSX.. I have done that way too many times already..

Thanks.

---

### Post by Gen2ly on 2007-05-18
I know you can use rEFIt from a CD.  There's an ISO at the rEFIt [site]("http://refit.sourceforge.net/doc/c1s5_burning.html").  If you just can have OSX boot you should be able to install rEFIt.  

Try installing from the LiveCD.  It might work.   Boot it and open the terminal type:

> sudo apt-get install refit.  

You might have to change root to do it though.  This will install in on the linux partition but it may not matter??

Also a silly thing but it may just work.  I believe the mac still uses boot information located in the memory, try Zapping the Pram.  Hold Apple + Option + P + R at boot.

---

### Post by ike on 2007-05-18
> **Dirk.R.Gently said:**
> I know you can use rEFIt from a CD.  There's an ISO at the rEFIt [site]("http://refit.sourceforge.net/doc/c1s5_burning.html").  If you just can have OSX boot you should be able to install rEFIt.  

Try installing from the LiveCD.  It might work.   Boot it and open the terminal type:

You might have to change root to do it though.  This will install in on the linux partition but it may not matter??

Also a silly thing but it may just work.  I believe the mac still uses boot information located in the memory, try Zapping the Pram.  Hold Apple + Option + P + R at boot.

I can't burn the rEFIt disk image.. Gnome/nautilus and K3B say it's not a real image file.. the extension is .cdr, which i have never seen before..

Tried renaming it to .iso, but that didn't help (it works with .img files).

---

### Post by cbrain on 2007-05-18
I think rEFIt have a .iso file on there site. It sounds like the problem maybe that your Hard Drive isn't mounting or your Logic Board if faulty. If you can boot of a cd then the problem probably lies with your Hard Drive.

---

### Post by ike on 2007-05-19
> **cbrain said:**
> I think rEFIt have a .iso file on there site.

Well, it says there is an iso, but it's the same .cdr file again.. Does anybody know how to burn a .cdr file to a disc (in ubuntu)?

---

### Post by ike on 2007-05-20
> **ike said:**
> Well, it says there is an iso, but it's the same .cdr file again.. Does anybody know how to burn a .cdr file to a disc (in ubuntu)?

Tried gnomebaker, and it said the .cdr file was not a valid image but let me burn it anyway, and it worked.

I can now boot from the cd and choose to boot ubuntu, but still no OSX... Seems like refit doesn't know there is an OSX installation on the drive?

I tried starting the EFI Shell, and it worked the first time, but now it hangs.

---

