---
title: "&quot;Allow application access to keyring&quot;?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Cantabile on 2007-11-20
Hi,

I'm using the "Connect to Server" applet to connect to several remote folders through SSH. Recently I began to see this warning every time I input the password: "Allow application access to keyring?". I'm a bit confused by this "keyring", what does it mean? Also there are three options to select: Deny, Allow once and Always Allow, what do they mean? Which one should I select? 

Thanks in advance.

---

### Post by shad0w_walker on 2007-11-20
The keyring is basically what it sounds like. It's a virtual keyring which keeps an encrypted copy of your passwords, so you don't have to enter them every time you access a network server or such.

What option you want to select depends on what you prefer. Deny obviously will stop the program reading the password from the keyring. Allow once gives the program access this time then asks again next time and Allow always gives the program permanent access to the keyring.

---

### Post by Cantabile on 2007-11-20
Thanks:), then I guess I can just choose Always Allow. 

Just curious, do you know where this keyring is kept in the system? I hope it's secure enough:).

---

### Post by shad0w_walker on 2007-11-20
I don't know the exact file location (Pretty sure its in your home folder) but i believe it uses a decent level of encryption. I would say more precisely but I haven't got the details at hand and I've been up since yesterday.

---

### Post by ronmarley1 on 2007-11-20
> **Cantabile said:**
> Thanks:), then I guess I can just choose Always Allow. 

Just curious, do you know where this keyring is kept in the system? I hope it's secure enough:).

It's in your /home folder.  When there, hit Ctrl+H to show hidden files.  Look in the keyrings folder, which is inside the .gnome2 folder.

---

### Post by MeanderingCode on 2007-11-25
Anyone know why i don't have a choice to always allow the application requesting access?
Nor do i have a checkbox for the same functionality that i hear other folks have.

This is gnome-keyring i'm talking about, nm-applet requesting the access.
I'm on xubuntu gutsy.

Any ideas?
Thanks.

---

