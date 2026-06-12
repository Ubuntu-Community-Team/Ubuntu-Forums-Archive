---
title: "How to install nVIDIA graphic drivers on Ubuntu 6.10?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Nixsyc on 2006-10-29
Please delete this post.

---

### Post by DraeLee on 2006-10-29
sure here is where i just did it today with compiz also and its working fine.  

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

hopefully this helps

---

### Post by Nixsyc on 2006-10-29
Please delete this post.

---

### Post by jem7v on 2006-10-29
Did you use method one or method two on that page? Method one never worked for me, but method 2 worked very well (despite how scary it seems). Just downloading and installing nvidia-glx doesn't mean your machine is actually using them. In my case, it didn't use them properly, either. Don't forget that your /etc/X11/xorg.conf file needs to have Device... driver set to nvidia instead of nv for the fancy drivers to be activated. And you'll have to restart X/Gnome to see the change. (If you don't know how to do that, log out and press ctrl+alt+backspace)

Try using this command. If the response is "direct rendering: yes" then your card is happy and fine.

```
glxinfo | grep rendering
```

If it isn't, and neither method off that page worked? Um, well, you could try one of tseliot's methods... Here's a bit of stuff that might help maybe.
[http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823)
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)

---

### Post by Nixsyc on 2006-10-29
Please delete this post.

---

### Post by jem7v on 2006-10-29
Yes. In order to use the nice drivers (nvidia) instead of the generic drivers (nv) you need to select the nice ones. That's what that does.

---

### Post by emir0n on 2006-10-30
Hi.I have a problem with my resolution.I installed the drivers with the second method and everything is ok,but the largest resolution that i can use is 1024x768 on 50Hz.Didnt have that problem in 5.10 or 6.06.
Can u plz tell me what can i do with that ?
I have nvidia GF 6600GT,Ubuntu 6.10,17" LCD BENQ monitor.

Thx

---

