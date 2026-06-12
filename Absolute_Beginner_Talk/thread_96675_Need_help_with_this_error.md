---
title: "Need help with this error"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by startailpro on 2005-11-29
Right i got off my ass and looked at this error i just need help with making sense of this error.
(--)probed, (**)from config file, (==) default settings, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknow.

(==) Log file:"/var/log/xorg.O.log", Time:Mon Nov 28 18:13:02 2005
(==) Using config file:"/etc/x11/xorg.conf"
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_clip.o" No
symbols found
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_norm.o" No
Symbo9ls found
Skipping
"/user/x11r6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" No
symbols found
(EE) No devices detected

Fatel server error:
no screens found


 what does this mean?

---

### Post by bonzodog on 2005-11-29
Have you just installed ubuntu?  Or have you had X up before?
if you have only just installed ubuntu it means X has failed to configure itself, and dropped you back to a terminal.

You will need to run: $sudo dpkg --reconfigure xserver-xorg

That should be of some help.

---

### Post by startailpro on 2005-11-29
Yes i have just installed ubuntu but the thing is i have already done
sudo dpkq-reconfigure xserver-xorg
and i still get the same problem

---

### Post by invalid on 2005-11-29
Can you post you /etc/X11/xorg.conf file here? Maybe we can pick something out.

Cb

---

### Post by startailpro on 2005-11-29
is there a certain way to open files cause if i just typed it in and it says no such file or dictionary.

---

### Post by invalid on 2005-11-29
```
cat /etc/X11/xorg.conf
```

---

### Post by startailpro on 2005-11-29
Using the code u gave, it still says no file or dictionary esists. so i followsed the file. 
cat /etc/ exists
cat /etc/x11/ no file or dictionary exsits
how very odd

new:
i was seeing if i types it wrong and half throughtyping theses errors come up i thought they might have something to do with the problem.

usb 5-6:clear tt 1 (9042) error -71
ati remote 5-6.3:1.0: ati remote_ing_in: usb_submit_urb()=-19
usb 5-6: clear tt 1 (9042) error-19
hci_usb_isoc_rx_submit:ncio isoc rx submit failed urb fff81603767628  err-28

---

### Post by invalid on 2005-11-29
You are trying to read a file that does not exist. Note the capital X in X11. It is case sensitive.

Cb

---

### Post by startailpro on 2005-11-29
oh i didn't know an easy mistake to make now one more thing how do i paste a file from one pc to another. I am using my laptop to do this as my pc will not load to gnome cause of this error i believe.

---

### Post by startailpro on 2005-11-29
I am getting kind of desprate here. I have coursework on my other hard drive and i need to finish it next week. The reason i changed over is windows crashed and would not load again. I always wanted to go to linux so i did
:confused:

---

### Post by startailpro on 2005-11-29
:( HELP :( HELP :(  HELP :(  HELP  HELP HELP :(  HELP :(  HELP :(  HELP :(
i BEG U PLEASE HELP

---

