---
title: "Skype"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-03-15
I didn't find this package searching on Synaptic.  Anyone know how to get it ?
Also, the standard install on Ubuntu doesn't have a way of compiling source.  Can anyone point me to what packages I would need to install in order to be able to do this?

Thanks for the input...

JD
Ubuntu 5.10

---

### Post by Xian on 2006-03-15
Try enabling the PLF repos, as I believe they include skype:

```
deb http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
deb-src http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
```

!! [How To Add Repos](https://wiki.ubuntu.com/AddingRepositoriesHowto) !!

---

### Post by gymsmoke on 2006-03-15
Xian~
I have all the repositories added in Synaptic with the exception of community security updates.  Skype doesn't appear.  Do I need to add the repo's you mentioned above by hand?

---

### Post by Xian on 2006-03-15
[QUOTE=gymsmoke]
I have all the repositories added in Synaptic with the exception of community security updates.  Skype doesn't appear.  Do I need to add the repo's you mentioned above by hand?[/QUOTE]

Sure, you can use that method. Just open a text editor (see below).
Then add those lines I posted at the bottom of the file.

Save, then open Synaptic and click 'Reload'.

$ sudo gedit /etc/apt/sources.list

---

### Post by FizDev on 2006-03-15
You should edit this file
```
sudo nano -w /etc/apt/sources.list
```
and then add the PLF repos that Xian talked about.

---

### Post by gymsmoke on 2006-03-15
hrm... okay, i found skype. synaptic tells me that it will also install 3 dependencies, and warns me about them.. i install them.  now, evolution mail will not start...
my guess is that skype (and/or one of its associated dependencies) is seriously brok ein 5.10 ... can i un-install this minor mess through synaptic?

---

