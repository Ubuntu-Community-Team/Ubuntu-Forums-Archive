---
title: "USB-Memory - itchy and glitchy"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by c_x on 2006-08-03
Hi, I'm really new to ubuntu and linux.
First when I tried to write to an usb-memory the data didn't save.
I testad to press unmount before removing it and it worked.
Now I have another usb-memory and when i put somthing in it it saves the filename, but not the content, so if i put a 100mb big file in it and then removes it without unmounting  the file won't be saved. But the filename will be there and 100mb will be unwritable until i format it.
This can't be supposed to happen. Help!!

---

### Post by RTrev on 2006-08-03
What version of Ubuntu are you using?  I've had no problem with USB sticks (what is the correct name for these things, anyway?)

Anyway, I recall reading somewhere that there are two ways to configure the USB thingys.  One way allows faster operation, because it caches all the writes until you hit the "Eject" button.. then it flushes the cache to the USB while you wait a bit.  The other method writes directly to the USB and no flushing of the cache is needed.  Sounds to me like maybe you are using the caching method, and then not doing the eject.. so the data never really gets written to the drive.  I've just gotten in the habit of *always* right-clicking the USB icon and choosing "Eject" before unhooking my USB, and I've never had a problem.

Hope this helps a little.  I don't know much about this, but I'm sure somebody here will come along with better advice.

Bob

---

### Post by c_x on 2006-08-03
I want it to write when i press eject (that would increase the lifetime, right?), the problem is that it writes in the "addressbook" causing problem if I don't eject it.

---

### Post by RTrev on 2006-08-03
> **c_x said:**
> I want it to write when i press eject (that would increase the lifetime, right?), the problem is that it writes in the "addressbook" causing problem if I don't eject it.
I'm not sure about the address book part.. I've never used it.  I'm pretty much a Google fan, and use Gmail for all mail.  But this sounds really strange.  You didn't say what version of Ubuntu you're running?  I've used 6 different USB sticks in this fully-updated 6.06, and never had any problem.  You say "if I don't eject it."  What happens when you *do* eject it?  And why would you *not* eject it?  Just forget to?  

I have no clue about the lifetime of the devices.. but I would guess that a single large write would be easier on it.  I have NO facts to back that guess up, though.  Sorry I can't help more!

---

### Post by c_x on 2006-08-03
Sorry, when I said addressbook I meant the "filesystem addressbook" (I have no idea how to explain it)
Thanks for the help anyway!
(I'm using fully updated 6.06 too, got pissed at windows a few days ago and tested linux for the first time via livecd. Falled in love and installed it directly :)

Edit:
I formatted it to ext3 and then back to fat and somhow that solved the problem! (I did format it 2 times before but that didn't help)

---

