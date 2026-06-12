---
title: "Add/Remove Programs Disappeared"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by avatarmonkey on 2006-12-23
Okay, so I installed Ubuntu and I'm liking it. After moving through the settings in all the various menus, it seems the Add/Remove Programs menu option from the Applications menu just went poof. How do I get that back, please?

---

### Post by jordanmthomas on 2006-12-23
It's surely not what you're looking for exactly, but I'm not sure of the exact name of the command to launch add / remove programs, so until someone who has ubuntu and can get the name arrives, might I suggest using
system | administration | Synaptic Package Manager ?

It will be a simple fix...you just need to add an entry to your menu that launches
```
gksu *whatevertheappiscalled*
```
so don't get too worried!

---

### Post by avatarmonkey on 2006-12-23
Thanks for that reply, that is a work around a I can use. But I would really like to get that original functionality back. There were some features in that particular menu choice that I liked. So, anyone else have an idea out I get the original Add/Remove Programs option from the Applications menu back, please? In case I wasn't explicit enough, this is a new installation of the current release of Ubuntu.

---

### Post by angkor on 2006-12-23
> **avatarmonkey said:**
> Thanks for that reply, that is a work around a I can use. But I would really like to get that original functionality back. There were some features in that particular menu choice that I liked. So, anyone else have an idea out I get the original Add/Remove Programs option from the Applications menu back, please? In case I wasn't explicit enough, this is a new installation of the current release of Ubuntu.

Have a look in System -> Preferences -> Menu Layout if the Add / Remove program is checked.

---

### Post by avatarmonkey on 2006-12-24
The Add/Remove Programs menu item isn't on that list. I'd sure like it to be, but it isn't.

---

### Post by tommcd on 2006-12-24
Right click on the applications menu and select "alacarte menu editor". Browse through the listings and you should see a listing for add/remove programs. Just check it and you should have it back.

---

### Post by Mazen on 2006-12-24
```
sudo apt-get install gnome-app-install
``` should do the trick

---

