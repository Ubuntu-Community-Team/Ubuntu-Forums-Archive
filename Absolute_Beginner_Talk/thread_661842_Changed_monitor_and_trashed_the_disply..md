---
title: "Changed monitor and trashed the disply."
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by radi0j0hn on 2008-01-08
My wife needed my nice 20" HP flat panel monitor so she could do some publishing layout work and show two pages at once.  So I swapped out my HP for her old Samsung flat panel, which has a max resolution of 1024x768.  The first time Ubuntu booted, it was fine, but every time after, it is an unreadable hash.
Since I can see what i am doing, I can't get to preferences and make any adjustments.

One of my boot options (restore) gives me a command line.  How can I set the resolution that way or do something to get this working?  I hate booting to Vista, but for now, it's my only choice.

TIA  John

---

### Post by Seisen on 2008-01-08
You can run ```
dpkg--reconfigure-xserver-xorg 
``` in the recovery mode and select the right resolution. This link will explain more

[http://users.bigpond.net.au/hermanzone/p7.html#Simple]("http://users.bigpond.net.au/hermanzone/p7.html#Simple")

before you actually run that command I recommend you make a backup of your xorg.conf file incase you accidently make a mistake. This can be done by typing this in the command line.

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by djbsteart1 on 2008-01-08
im in the same boat, but for me its an external monitor on laptop. it doesnt show anything so any help would be appreciated. have you checked the screen resolution? to rotate it try ctrl alt - or ctrl alt +, that might help there is also graphics setting under system-->admin-->, hope this is of help to you

---

### Post by megamania on 2008-01-08
You should backup your xorg.conf file first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

You can then try from command line:
```
sudo dpkg-reconfigure xserver-xorg
```
Just hit Enter when you're unsure about what to choose.

Hope that helps.

---

### Post by djbsteart1 on 2008-01-08
ill try when i get home, really hope so, want linux to work so much, thanks for the posts.

---

