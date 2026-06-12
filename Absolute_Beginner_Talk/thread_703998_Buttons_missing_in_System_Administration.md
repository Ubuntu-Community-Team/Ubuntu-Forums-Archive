---
title: "Buttons missing in System Administration"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by IcedDante on 2008-02-21
I logged in to my Ubuntu distro and found that the Synaptic Package Manager was no longer available under System->Administration like it normally is. What could cause this to disappear? I have logged in for a few weeks so I don't remember very well but I think some other links are missing here as well.

Keyring Manager
Network Tools
Printing
System Log
System Manager
and
Update Manager

are the only programs visible.

Thanks.
:popcorn:

---

### Post by overdrank on 2008-02-21
> **IcedDante said:**
> I logged in to my Ubuntu distro and found that the Synaptic Package Manager was no longer available under System->Administration like it normally is. What could cause this to disappear? I have logged in for a few weeks so I don't remember very well but I think some other links are missing here as well.

Keyring Manager
Network Tools
Printing
System Log
System Manager
and
Update Manager

are the only programs visible.

Thanks.
:popcorn:

HI and have you edited your menus, right click and choose edit menus and then you may need to add  synaptic manager.

---

### Post by IcedDante on 2008-02-21
No, I don't know how but I was delisted from the admin group. Another post details the fix for this, but I basically had to reboot into recovery mode run a usermod to add myself to the admin group (as detailed in another thread):
usermod -a -G admin userNameHere

and then reboot.

I'm not sure why, but trying "sudo usermod" didn't work, I had to be in recovery mode, and I'm not sure why I was removed from the admin group in the first place.

---

