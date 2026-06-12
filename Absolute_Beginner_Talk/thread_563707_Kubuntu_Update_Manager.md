---
title: "Kubuntu Update Manager"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ev5unleash1 on 2007-09-30
Ok, Well i just switched from Ubuntu to Kubuntu and I fell in love with the features and interface it had. Now the only problem is that I cannot find the update manager. I've looked everywhere I think it would be! Any ideas? I really need that update manager because some of my hardware only works when i installed some of the updates when I had Ubuntu. Please HELP!

---

### Post by ev5unleash1 on 2007-09-30
Ok,I managed for find this command ```
sudo apt-get update -f
``` which I think updated my system. But I'm still looking for the proper shortcut that will open the Adept Updater. When I did that command it did the whole update in the Kterminal and updated then the Adept Updater came up on the taskbar and i was able to go to it. But I want a shortcut so I don't have to do that command.

---

### Post by ajgreeny on 2007-09-30
Did you reinstall or just add the **kubuntu-deskto**p package to your ubuntu?  It would probably have been easier to that if you didn't and it then gives you the option of gnome or kde at login.

To answer your question, the kubuntu update manager is adept and its various dependencies.  It should be in the system menu as Adept Manager.   Perhaps you already have it installed and just haven't noticed it.  I think synaptic is installed as well in any case, which I prefer, and nearly always use instead of adept.  If neither is already installed just open a terminal and type ```
sudo apt-get install adept synaptic
``` Both packages will be installed and you can then chose which to use.

---

### Post by overdrank on 2007-09-30
> **ev5unleash1 said:**
> Ok, Well i just switched from Ubuntu to Kubuntu and I fell in love with the features and interface it had. Now the only problem is that I cannot find the update manager. I've looked everywhere I think it would be! Any ideas? I really need that update manager because some of my hardware only works when i installed some of the updates when I had Ubuntu. Please HELP!

Hi, I believe it is adept manager and you can try and use the alt,F2 keys and enter ```
adept_notifier
```

Edit to slow lol

---

### Post by ev5unleash1 on 2007-09-30
No, I fully reformated my partition and then installed Kubuntu.

---

### Post by ev5unleash1 on 2007-09-30
Thanks, That opened the notifier. But will I have to do that everytime it does not open or is there an easy way of it opening when the computer starts?

---

