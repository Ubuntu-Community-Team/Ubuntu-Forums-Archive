---
title: "VMware questions - access to host environment (files, hardware etc.)"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by apalacheno on 2006-11-19
Hello everybody!
I plan migrating to Ubuntu shortly, but because of two applications (a professional image management application and a mobile phone management application) I'll still be bound to Windows.
Initially I thought about dual-booting Ubuntu and Windows XP, but of course it would be more convenient to run Windows XP inside Ubuntu with virtualization.

Could these programs I mentioned earlier - if run under Windows XP within a virtual machine inside Ubuntu - access the environment outside the VM? Or, to be more specific:
1. Could the image management application natively (with read/write access) access the images that are stored my Ubuntu Home folder (ext3 filesystem)?
2. Could the phone management application access the IrDa- and Bluetooth-Hardware (assuming both work under Ubuntu)?
3. Is Drag&Drop possible between Ubuntu and Windows XP?

Cheers,
apalacheno

---

### Post by tribaal on 2006-11-19
You need to understand that vmware makes two operating systems run on the same hardware. It's exactly like having two computers on the same hardware. So the way your two machines communicate is the same two machines on the same network communicate with each other: via shared folders or ssh. 
So unfortunately no drag and drop here, as far as I know.

Hope this helps you understand?

- trib'

---

### Post by Celis on 2006-11-19
Hmm, the answers to 1 and 3 are yes - you can set your Ubuntu home folder as a samba drive and read/write to it fine - and yes you can drag and drop using VMware server on a Ubuntu machine with XP running as your windows OS.

The 2nd question is tougher - I'm not sure how well blue-tooth plays in a VM environment.  You'd have to try it

---

### Post by apalacheno on 2006-11-20
Thanks for clearing things up guys!
You encouraged me to try and see how it works 8) 

Cheers,
apalacheno

---

### Post by apalacheno on 2006-11-28
Finally I have some first-hands experience with ubuntu. And I love it! :-D 

Now I've also got some answers to my questions:
1. You have to use samba to do this. It doesn't matter in fact, because you can implement the samba share as network drive in Windows, which behaves just like a normal folder.
2. Nope. Bluetooth and Infrared are not yet supported by VMware.
3. Yes, using VMware Tools this is possible.

Cheers,
Ro

---

### Post by djbon2112 on 2008-02-14
> **Celis said:**
> Hmm, the answers to 1 and 3 are yes - you can set your Ubuntu home folder as a samba drive and read/write to it fine - and yes you can drag and drop using VMware server on a Ubuntu machine with XP running as your windows OS.

Now, how would one go about doing this?

---

