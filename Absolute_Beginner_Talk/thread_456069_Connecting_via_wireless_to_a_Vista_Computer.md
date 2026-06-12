---
title: "Connecting via wireless to a Vista Computer"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-27
If instructions for what I want to do already exist somewhere, please point me to that thread - - my son just purchased a new Gateway laptop.  Since we could not find a computer preloaded with XP, we had to settle for one setup with Vista (the Ubuntu Community (and perhaps Linux, although Ubuntu is all of Linux about which I know anything) should feel complimented . . . much of the touted security that comes with Vista seems to have been inspired by features that are already part of Ubuntu - the dimming screen and request for confirmation before allowing system changing events to proceed, even the old pointer-to-hourglass has been replaced with an arrow sporting little circle off to the right with rotating indicator to indicate pages loading, programs loading, etc.

I could go on and on about my impressions of Vista, but, really, what I want to find out is how, with his new laptop sitting right beside me, I might network with it to transfer some files.

We are both connected via adapters to the same wireless router.

How would I go about networking the two machines?

Thanks.

Caruso

---

### Post by lazyart on 2007-05-27
The usual case (with XP mind you-- I haven't yet played with Vista) is to enable File & Print Sharing, then designate which folders to share.  From the Ubuntu side you would browse the WIndows network, then the workgroup and you would "see" the Vista computer and then the folders.

Enabling sharing on the Linux side is a bit more complicated.  Select the folder you want to share, right click and share it as SMB.  Then from console,```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```

Provided that username already has access to that folder, you can connect from the Windows box it will prompt for username and password -- use the ubuntu credentials and you're golden.

---

### Post by carusoswi on 2007-05-27
> **lazyart said:**
> The usual case (with XP mind you-- I haven't yet played with Vista) is to enable File & Print Sharing, then designate which folders to share.  From the Ubuntu side you would browse the WIndows network, then the workgroup and you would "see" the Vista computer and then the folders.

Enabling sharing on the Linux side is a bit more complicated.  Select the folder you want to share, right click and share it as SMB.  Then from console,```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```

Provided that username already has access to that folder, you can connect from the Windows box it will prompt for username and password -- use the ubuntu credentials and you're golden.

Lazyart, thanks for the repy.  I want to share a volume from my Linux machine.  I would assume that I could right click - but, when I do, no option to share the volume is presented.

Did I miss something?

Caruso

---

### Post by lazyart on 2007-05-27
Don't think you can share a whole volume-- that's probably a security no-no.  Share a folder instead.

---

