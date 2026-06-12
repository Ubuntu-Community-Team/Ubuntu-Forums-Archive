---
title: "[SOLVED] Where are the synaptics driver settings stored?"
date: 2008-07-28
forum: Arch and derivatives
---

### Post by Nergar on 2008-07-28
Where can I find what settings is my laptop currently using. I Installed archlinux but I can get the synaptics settings right, I want to use the ones used by Ubuntu because the touchpad works very well in Ubuntu.

Thanks in advance.

---

### Post by overdrank on 2008-07-28
Moved :)

---

### Post by Bachstelze on 2008-07-28
Your Synaptics Touchbad is an input device, its settings are therefore stored in your Xorg config file, just like any other's.

---

### Post by mips on 2008-07-28
> **Nergar said:**
> Where can I find what settings is my laptop currently using. I Installed archlinux but I can get the synaptics settings right, I want to use the ones used by Ubuntu because the touchpad works very well in Ubuntu.

Thanks in advance.

Check your Ubuntu xorg.conf. Do me a favour and please paste the settings here as I would like to copy them into my xorg.

---

### Post by chewearn on 2008-07-28
If you have a Dell laptop, take a look here:
[http://ubuntuforums.org/showthread.php?t=748596](http://ubuntuforums.org/showthread.php?t=748596)

---

### Post by fwojciec on 2008-07-28
Or this could be helpful as well: [http://wiki.archlinux.org/index.php/Synaptics]("http://wiki.archlinux.org/index.php/Synaptics")

---

### Post by RiceMonster on 2008-07-28
> **fwojciec said:**
> Or this could be helpful as well: []("http://wiki.archlinux.org/index.php/Synaptics")

Yep, follow that guide. That got my touchpad working better than it did on Ubuntu.

---

### Post by Nergar on 2008-07-28
Thanks to all for responding, I got it working now.

For future reference:

```
man synaptics
man synclient
```

listing current values:

```
synclient -l
```


I used Arch's wiki and synclient -l in ubuntu to get a basic idea.

---

### Post by Nergar on 2008-07-28
> **overdrank said:**
> Moved :)

BTW, I don't think this belongs in Other OS Talk. If you read the question, I want to use ubuntu settings. And they are stored in: xorg.conf

---

