---
title: "VMware Tools - uber newbie"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by breaking on 2008-01-23
I'm using the latest version of Ubuntu, and v6 of VMware.

I tried following all these different guides and from what i've read, it seems that I need to be in text mode by pressing alt+ctrl+f1.  I did that and entered my username, but when it asked for my password, it wouldnt let me type at all.

(I've tried installing VMware Tools from non text mode and I had no luck.

PLEASE HELP!

---

### Post by emarkd on 2008-01-23
For security, your password will never be displayed on a terminal.  It's still getting your input.  Just type your password and hit enter.

---

### Post by ryanVickers on 2008-01-23
I don't mean to be rude, but *sigh* another falls to the evil VMware...

I would recommend VirtualBox instead - I tried it, it was indescribably faster, way more *useful* features, and I have not been back since.  Plus, there is that added feeling of reliability because, unlike VMware, you **know** that if it opened one day, it will tomorrow too!

---

### Post by breaking on 2008-01-23
I can't install the tools :-/

I'm using this: [http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html](http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html)

I think I'm already in root, but I tried typing "su -" anyway and then the password and said there was an authentication failure.

---

### Post by ryanVickers on 2008-01-23
well, then maybe the password was wrong, I don't know...
But it not showing up is completely normal, everything has always done this and it always will! :p

I used to have a much simpler way, but I don't remember... and try not to *shudders at memories* :p

---

### Post by Shazaam on 2008-01-23
VMware works perfectly well for most users. Your success with VirtualBox doesn't make VMware "evil".:rolleyes:

---

### Post by emarkd on 2008-01-23
su - won't work on ubuntu because there's no root password.   try this instead:

```
sudo -s
```

type your password and it should work.  if in doubt, you can type

```
whoami
```

and it should tell you "root" if sudo -s worked properly

---

### Post by breaking on 2008-01-23
I dont think I can run VirtualBox... i'm on a 32bit machine

---

### Post by ryanVickers on 2008-01-23
> **Shazaam said:**
> VMware works perfectly well for most users. Your success with VirtualBox doesn't make VMware "evil".:rolleyes:

well, its not just me though, many people find it slow, but deal with it - I couldn't: moving a window, and scrolling through a page should not be slow... (and trust me I did everything to make it work better) :lolflag:

BTW I can render 3D at windows native speed with VirtualBox ;)

---

### Post by breaking on 2008-01-23
[http://www.howtoforge.com/vmware_tools_on_linux](http://www.howtoforge.com/vmware_tools_on_linux)

Site of the gods^

I installed it...Sorry for wasting your time :-/

I do have another quick question though if you don't mind... How can I disable the annoying internal speaker in Ubuntu?  It's so loud!

---

### Post by ryanVickers on 2008-01-23
In "System > Preferences > Sound" under "System Beep" turn it off ;)

---

