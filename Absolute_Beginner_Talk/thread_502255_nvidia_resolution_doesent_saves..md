---
title: "nvidia resolution doesent saves."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by paparappa on 2007-07-16
Yo!

When i'm in ubuntu 7.04 and open my nvidia X server settings i set the resolution to 1280 - 1024. I press apply, it works and then i click on "Save to X configuration file". It all works great but when i boot up the computer next time it  has the 1024x768 resolution and i have to do this process again. How can i do so it really saves it and always has this resolution?

---

### Post by johto on 2007-07-16
Hi, you could check /etc/X11/xorg.conf (make a backup before editing) and remove unnecessary resolutions down the botton section ...or put the resolution you mostly like  first on every line. If you have more than one resolution on every bit-mode, you can switch them by CRTL+ALT+(+/-) ..thats why it defaults to the first one.

---

### Post by bodhi.zazen on 2007-07-16
> **paparappa said:**
> Yo!

When i'm in ubuntu 7.04 and open my nvidia X server settings i set the resolution to 1280 - 1024. I press apply, it works and then i click on "Save to X configuration file". It all works great but when i boot up the computer next time it  has the 1024x768 resolution and i have to do this process again. How can i do so it really saves it and always has this resolution?

Yo,  you need to run that as root :

```
gksu nvidia-settings
```

When you run nvidia-settings as a user you can not modify /etc/X11/xorg.conf (as you can see).

---

### Post by Malta paul on 2007-07-16
Hi, Just a thought, Did you try >system >preferences >screen resolution, and ticking the box 'Make default for this computer' >apply ? ;)

---

### Post by oldos2er on 2007-07-16
> **bodhi.zazen said:**
> Yo,  you need to run that as root :

```
gksu nvidia-settings
```

When you run nvidia-settings as a user you can not modify /etc/X11/xorg.conf (as you can see).

 I was having the same problem, and this worked for me. Thanks!

-- 
Ann

---

### Post by paparappa on 2007-07-17
thank yall! Worked great

---

### Post by graphicw on 2007-07-18
This worked for me as well making me happy to find another answer without needing to post.  Thanks for the help on this issue.

---

