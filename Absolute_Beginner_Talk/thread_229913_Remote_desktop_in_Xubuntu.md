---
title: "Remote desktop in Xubuntu"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by helino on 2006-08-05
Hi, I want to acess my Xubuntu PC using remote desktop from a Ubuntu PC. Is there a remte desktop app in Xubuntu or do I have to use VNC? If it's built-in, where do  find it?

thanks

---

### Post by louis_nichols on 2006-08-05
well... even the app included for desktop sharing in Ubuntu is still vnc. I dunno if Xubuntu has any... but if it does, it's quite certainly vnc also.

I mean... why not? Is there a reason you would rather not use vnc?

Of course, there's always the ssh graphic session... If I remember well, the command is ```
ssh -X ip-number
```. I don't know how you should configure the server, though...

---

### Post by TFX360 on 2006-08-05
> **helino said:**
> Hi, I want to acess my Xubuntu PC using remote desktop from a Ubuntu PC. Is there a remte desktop app in Xubuntu or do I have to use VNC? If it's built-in, where do  find it?

thanks


It's build in, and as far as I know there is no other. RDP/RDC/mstsc is a lot better than VNC.

Configuring is done under System / Preferences / Remote Desktop.


In Ubuntu at least,


Kind regards,


TFX

---

### Post by eXisor on 2006-08-05
I use X11vnc in xubuntu, the newer version from the developer's site, because I find it's performance is better for my setup. On the windows side I use ultravnc. (The developers have platform optimised builds, whereas ubuntu just has the 386 version)

---

