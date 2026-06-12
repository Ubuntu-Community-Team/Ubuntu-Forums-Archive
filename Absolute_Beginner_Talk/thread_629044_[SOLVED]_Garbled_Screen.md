---
title: "[SOLVED] Garbled Screen"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Don DeGregori on 2007-12-01
Need help. 7.10 LiveCD looks OK. Installed 7.10, no problem with screen. Then decided to look at "Screens and Graphics" and maybe improve looks by changing to LCD monitor I have, a Viewsonic VA521. A VA520 was listed and thought was close enough, so selected it with 1024 x 768. Before I did this, the default was Plug n' Play, same resolution. Well, after that dumb move (if it anin't broke, don't fix it), now on reboot I have a very garbled screen I can't read.

I need to get back to Plug n' Play. I have the alternative CD for 7.10, I think it has "rescue mode". I need to make a change to some line of code to bring my screen back. Can someone show me how to do it?

Thanks, Don

---

### Post by overdrank on 2007-12-01
> **Don DeGregori said:**
> Need help. 7.10 LiveCD looks OK. Installed 7.10, no problem with screen. Then decided to look at "Screens and Graphics" and maybe improve looks by changing to LCD monitor I have, a Viewsonic VA521. A VA520 was listed and thought was close enough, so selected it with 1024 x 768. Before I did this, the default was Plug n' Play, same resolution. Well, after that dumb move (if it anin't broke, don't fix it), now on reboot I have a very garbled screen I can't read.

I need to get back to Plug n' Play. I have the alternative CD for 7.10, I think it has "rescue mode". I need to make a change to some line of code to bring my screen back. Can someone show me how to do it?

Thanks, Don

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by Don DeGregori on 2007-12-01
Thanks so much! The commands did the trick. I really did not want to re-install the OS over again! I've saved the info you gave me, just in case.

Take care, Don, Mission Hills CA, USA

---

### Post by overdrank on 2007-12-01
> **Don DeGregori said:**
> Thanks so much! The commands did the trick. I really did not want to re-install the OS over again! I've saved the info you gave me, just in case.

Take care, Don, Mission Hills CA, USA

Great glad to hear, Please mark the thread as solved under thread tools. Thanks :KS

---

