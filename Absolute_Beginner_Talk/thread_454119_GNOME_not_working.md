---
title: "GNOME not working"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-05-25
i installed pango theme but it has done something to my gnome settings (somewhere in the GUI files in sub directories of /usr i guess) and now when i login it is not displaying any text in the menu or icons or any gnome applications.   my panel menu and launchers have disappeared. from terminal (luckily i have a shortcout in my desktop) im opening the applications. 3rd party applications are working well from there.

i just want to know what to do to restore them. i dont know to remove the pango .


i once again installed gnome but still it is having the same problem. 


pls help...

---

### Post by Najand on 2007-05-25
How did you install that? Can you give us more details?

---

### Post by sankarv on 2007-05-25
i have installed pango from source and when i rebooted it all happened. I then downloaded gnome source and installed it again. all this i tried using the terminal. the problem persists still after installing gnome and rebooting the machine also.


there are some files missing in the .gnome2 directory such as sessions, main and background.xml. i copied these from other machine i have but still the problem persists.


the reason for requiring  restore is i have installed a lot of applications in the machine and it is very difficult to reconfigure/reinstall them.

---

### Post by Najand on 2007-05-25
Well, let us find where did pango install itself?
What is the output of?
```

sudo updatedb
locate pango

```

---

### Post by sankarv on 2007-05-25
these are the paths so far i have found pango but it is still searching and taking long time.

./etc/pango
./usr/lib/pango
./usr/local/etc/pango
./usr/local/lib/pango



if possible can u pls provide ur instant chat id such as aol/yahoo so that i can solve it sooner.

---

### Post by Najand on 2007-05-25
Sure you can find my yahoo messenger ID when you click on its icon.

---

### Post by sankarv on 2007-05-28
hi the problem is now solved. i came to a conclusion. since pango is a dependency of gtk changing pango (i installed pango again without knowing this) will affect gtk. so gtk needs to reinstalled for proper operation. so i installed gtk and now it is working fine.

---

