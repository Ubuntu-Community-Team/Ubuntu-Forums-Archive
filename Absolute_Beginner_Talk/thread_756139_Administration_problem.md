---
title: "Administration problem"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-04-15
Hi All

I dont know what I have done but I cannot open a lot of the options in Administration ,from Login Window to even Synaptic wont open.Some things will open .printing ,networktools , system monitor.
Any Ideas? 
I tried sudo synaptic in terminal and get this

sudo: /etc/sudoers is mode 0640, should be 0440

Can run without sudo and in Run application but not from the drop down menu

---

### Post by kellemes on 2008-04-15
Boot into recovery mode and type the following..
```
chmod 0440 /etc/sudoers
```
reboot.

---

### Post by bossa on 2008-04-15
Hi kellemes

When I rebooted into recovery mode all I got was a background ,right clicking to bring up terminal was no good as the terminal  was all white and would not except text. Rebooted normally , logged out and went into failsafe and followed your instructions and all is well now :). Thanks very much for your advice. Any idea what might have been the cause of this?

---

