---
title: "My ubuntu won't boot up"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-07
I already iinstalled the OS. About 2 weeks ago, and for some reason it just wonnn't boot up. everything goes normally. But then it wonnnn't stop loadding before the login screen. Its like its frozen but you can still use the loading cursoor to move around.

P.S. I am on my Father's Win98

---

### Post by TaiQui on 2007-10-07
bump

---

### Post by tdrusk on 2007-10-07
try pressing ctrl+alt+f1 during the bootup. See if anything weird pops up.

---

### Post by TaiQui on 2007-10-07
I did that, and typed in my login. but thenn it just says:

```
 bri@main~$ 
``` what do I type in then?

---

### Post by tdrusk on 2007-10-07
I man during th bootup when it says,"ubuntu" and has a progress bar.

---

### Post by TaiQui on 2007-10-07
```
 intel-rnpg fwh not detected
ext53054: cannot initailize. EXT MID- 0000 
```

And then it just reboots. onto the loading screen of doom.

---

### Post by derred on 2007-10-07
does the Xorg server get stuck or is it just the GDM login?

Could you do a ctrl+alt+f1/login and type: "sudo /etc/init.d/gdm stop" and then "startx"

---

### Post by TaiQui on 2007-10-07
I'm not sure what you mean, but when its loading the login screen it doesn't stop, so I think it may be the GDM login.

My baackground on the other one doesn' t work but boots up

Nevermind everything works! I'm on it right now. I think I may just decide to stay with ubuntu, but will I need to do this every time?

---

### Post by derred on 2007-10-07
Glad to hear you got it to run.
If you keep getting stuck in GDM you than this is not a permanent solution. But at least we know that it's your GDM settings and not your x-server that has a problem.

You could try playing with the settings in System/Administration/Login Window. For example you could go to Security and check Enable Automatic Login if you only have one user on the machine and see if that works. You could also reinstall GDM or replace it with KDM(even give Kubuntu a try while you're at it).

I'm not much of an expert so all I can say now is good luck(or keep hanging on in the forum for someone smarter than me :) )

I'd try a sudo "dpkg-reconfigure gdm" from the command line before anything else

---

### Post by TaiQui on 2007-10-07
Kubuntu looks pretty cool. Downloading now.

---

### Post by derred on 2007-10-07
You can install kubuntu with "sudo apt-get install kubuntu-desktop" and keep ubuntu installed. Just select kdm during the install :)

---

