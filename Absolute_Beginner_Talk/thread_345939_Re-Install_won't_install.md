---
title: "Re-Install won't install"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-01-25
Hi.  I'm fried when it comes to installing wireless and taking care of hibernate in Edgy.  I'm motivated to seek online answers but network manager and bcm43xx or whatever just wasn't working in Edgy.  I was getting ill after 3 days of trying.

So I tried to re-install Dapper.  

Now what I get is that it hangs at 64% of "Installing System" (1:47 remaining) and yes I hard-rebooted and tried to install again and again.  Each time it got hung up and stuck at the same place.  Should I cleanly delete the whole drive?  How do I do that?  (I got this machine with an empty hard drive and the original ubuntu installation went well?)

I'm starting to think I'm just screwed with ubuntu.

---

### Post by drascus on 2007-01-25
no your not screwed with ubuntu don't worry. I have had similar problems. What it really takes is to just relax and go slow and consider your options at each step. ok first on why your system is hanging and wether or not you should do a wipe of your hard drive.  I think that erasing the hard drive is a good option because right now I am not sure what the reason could be for the hang here is a free software that can do this for you [http://www.killdisk.com/](http://www.killdisk.com/)  . Ok now try to install ubuntu and see how it goes. hope that helps.
~Drascus~

---

### Post by drascus on 2007-01-25
Ok I forgot to mention what to do about the whole wireless thing. I would first get the wireless up and working with dapper. If it requires ndiswrapper like mine did this should work. Then Upgrade to edgy (there are plenty of good forum posts on upgrade procedure) after this it will probably dump your ndis libraries not to worry open synaptic and downlad your utils files again and all should work after a restart.

---

