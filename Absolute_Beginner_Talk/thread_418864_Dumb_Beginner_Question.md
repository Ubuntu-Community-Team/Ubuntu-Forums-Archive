---
title: "Dumb Beginner Question"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-04-22
This may sound like a stupid question but here it goes anyway.  I'm trying to set up a network between my ubuntu desktop and my windows laptop.  On the page where it tells how to set up smbfs, it tells me I need to change to the home directory of my main user.  On the command line I type in cd /home/helixed/ .  It doesn't do anything.  It just stays on the desktop.  Can anybody explain this to me?

Thanks,

Helixed

---

### Post by RobsterUK on 2007-04-22
Please post a link to the tutorial you are following so we can see what you are doing better,

thanks

---

### Post by helixed on 2007-04-22
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Thanks,

Helixed

---

### Post by marko_4454 on 2007-04-22
> **helixed said:**
> This may sound like a stupid question but here it goes anyway.  I'm trying to set up a network between my ubuntu desktop and my windows laptop.  On the page where it tells how to set up smbfs, it tells me I need to change to the home directory of my main user.  On the command line I type in cd /home/helixed/ .  It doesn't do anything.  It just stays on the desktop.  Can anybody explain this to me?

Thanks,

Helixed

are you sure it doesnt move?? 
try this:
```
pwd
```

Does that give you /home/helixed/Desktop or /home/helixed/ ???
you can also try 

```
cd ..
```
This will be what windows would classify as "UP" a directory.

---

### Post by helixed on 2007-04-22
Okay, i guess I was in the right directory and it just wasn't showing me.  pwd returned home/helixed/, so I guess that fixes my problem.  Thanks for the help.

Helixed

---

