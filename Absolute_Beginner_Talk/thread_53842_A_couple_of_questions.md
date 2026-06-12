---
title: "A couple of questions"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by anwarlorenzo on 2005-08-02
At last I installed a copy of Ubuntu on my pc(yay!)! And I'm pretty mutch happy with it but it still has some problems I can't solve.

1. I used pppoeconf to connect to my dsl connection everytime at startup but sometimes my connection gets disconnected. How do I reconnect?

2. How do I enable gkrellm to run everytime at startup(or any other program)?

3. My sound is working but I hear lots of crackles when playing mp3s with xmms. I remember that I don't have this problem when I tried knoppix. Is there a way to improve the sound?

4. How do I create shortcuts and put it on the "Applications" menu of gnome?

5. Why does gkrellm disappear after some time?

6. How do enable port 6881 for azureus(it says it's blocked or something)

7. Where does most installed programs go? Their directory I mean? And their config files?

Maybe I'll add more later. Thanks in advance! I hope to learn a lot! :)

---

### Post by frodon on 2005-08-02
[QUOTE=anwarlorenzo]At last I installed a copy of Ubuntu on my pc(yay!)! And I'm pretty mutch happy with it but it still has some problems I can't solve.

1. I used pppoeconf to connect to my dsl connection everytime at startup but sometimes my connection gets disconnected. How do I reconnect?

2. How do I enable gkrellm to run everytime at startup(or any other program)?

3. My sound is working but I hear lots of crackles when playing mp3s with xmms. I remember that I don't have this problem when I tried knoppix. Is there a way to improve the sound?

4. How do I create shortcuts and put it on the "Applications" menu of gnome?

Maybe I'll add more later. Thanks in advance! I hope to learn a lot! :)[/QUOTE]
 2. You can add it in System>Preferences>session, there is a field to specify which software you want to launch on startup.
4. If you want to create desktop shortcuts, i think a simple drag & drop from nautilus will work. Or you can create a symbolic link in your desktop folder. For specific desktop shortcuts i think you can create one using right click on desktop and specify a command (it works like that in the panel).
For keyboard shortcuts : [http://www.ubuntuforums.org/showthread.php?t=42404](http://www.ubuntuforums.org/showthread.php?t=42404).
If you want to add shortcuts in menu bar use [Smeg](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#menu-editor)  menu editor.

---

### Post by Jivicin on 2005-08-02
[QUOTE=anwarlorenzo]6. How do enable port 6881 for azureus(it says it's blocked or something)[/QUOTE]

I would check to see if firestarter (or any firewall you're using) is allowing any traffic on that port.  If it isn't, you'll need to make a rule opening the port for Azureus.

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=anwarlorenzo]
4. How do I create shortcuts and put it on the "Applications" menu of gnome?
[/QUOTE]

Smeg

[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by az on 2005-08-02
1-  In pppoeconf I think there is a keepalive option enabled by default.  When the connection dies, it is reestablished.  Why is this not working?

---

### Post by IceAxe18 on 2005-08-02
[QUOTE=anwarlorenzo]At last I installed a copy of Ubuntu on my pc(yay!)! And I'm pretty mutch happy with it but it still has some problems I can't solve.

3. My sound is working but I hear lots of crackles when playing mp3s with xmms. I remember that I don't have this problem when I tried knoppix. Is there a way to improve the sound?[/QUOTE]

You need to mute Phone in your Volume Control to eliminate the crackles. I had to do it to get rid of the crackle sounds.

---

### Post by anwarlorenzo on 2005-08-02
[QUOTE=azz]1-  In pppoeconf I think there is a keepalive option enabled by default.  When the connection dies, it is reestablished.  Why is this not working?[/QUOTE]
I think I enabled the keepalive option.

I found the problem! After some time my DNS servers disappear(I don't know why) that's why it seems that my connection dies.

Let's say I rebooted. Then I checked System->Administartion->Networking. I click on the DNS tab and I see 2 IPs. Then after some time (most of the time this starts to happen when I start firefox) I can't browse or my downloads are stopped.

 I tried to ping [www.google.com](www.google.com) but it says unknwon hostname. I checked the DNS tab again and the DNS servers are replaced with my gateway Ip 10.0.0.138. I wonder what's causing this.

[Update]
I backed up resolv.conf and after a while it got changed again and my DNS servers are back to 10.0.0.138 again. I restored the resolv.conf with the proper DNS servers and everything is working fine again. I wonder what's causing this.

Thank you so much for the help! :)

---

### Post by anwarlorenzo on 2005-08-02
frodon, poofyhairguy: smeg works great! :)

Jivicin: I'm using firestarter and I've now set up a rule. Thanks man! :)

IceAxe18: earphones you mean?I got phone and earphones muted but the sound is still terrible. Muffled with cracks. BTW it sounds fine win WinXP. [Update] I installed the mad decoder plugin for ryhtm box and it sounds great! I think the problem is with xmms' output plugins(I tried both btw ALSA and OSS).

---

