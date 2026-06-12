---
title: "Can't connect to OS X SMB share"
date: 2006-02-11
forum: Apple PPC Users
---

### Post by rbanzai on 2006-02-11
I also posted this on the regular Kubuntu forum but this seems like a better place for it...

I have an OS X 10.4 machine set up for Windows sharing. I can connect to it with my XP box but I cannot connect to it from my new kubuntu setup on my old Dell PC. I have searched and seen lots of conflicting information on connecting to SMB including some posts saying "delete X and reinstall Y!" and others saying "No! Reinstall Z and delete J!" and so on and so on.

I looked at SMB setup and everything was dimmed out. I tried the "admin" button but that didn't do anything even the one time it asked for my user password. The File Sharing control panel is similarly dimmed.

I found a post with some hints for getting the SMB panel to light up so I could access it but it still didn't help.

I feel that if I can easily connect to the OS X SMB share with XP then I should be able to do it with Kubuntu but I am lost as to where the problem is.

I'm happy to post any config info anyone needs, but at this point I'm not sure what people would need to see.

If Ubuntu simply can't connect to an OS X Samba share can someone help me figure out how to at least see the Ubuntu box from the Mac and the XP machine? That would be better than no sharing at all.

thank you

---

### Post by Ptero-4 on 2006-02-12
Tiger. IIRC have a nasty version problem regarding samba. For some reason the version of the samba package in Tiger is incompatible with the one in breezy. You basically have to install a compatible samba in breezy (You can remove samba from ubuntu, but you can't change/remove/reinstall the OSX samba component b/c it's mangled within the OS).

---

### Post by rbanzai on 2006-02-12
Thanks for the info.

Goodbye Ubuntu! I need an OS that can support what my OS X and XP machines use for filesharing.:mrgreen:

---

