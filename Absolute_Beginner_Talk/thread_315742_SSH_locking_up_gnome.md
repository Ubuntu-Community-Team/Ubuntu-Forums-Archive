---
title: "SSH locking up gnome"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by ilhabia0 on 2006-12-09
I have been using edgy fro about a week now and was interested in setting it up so I could ssh to my machine.  I installed ssh and then when I restarted it booted most of the way into gnome and then locked up before finishing the panels.  I restarted gnome and then and error message came up stating that panels were already running and no panels showed up.  Restarted again and this time it just locked up totally after login.  Tried to login a couple different times with the same result so I booted up in recovery mode and uninstalled ssh.  After that I could boot up a login normally just fine.  

I was wondering if this has happened to anyone else or maybe I did something wrong when installing ssh.  I used "sudo apt-get install ssh" to install ssh, any insight on this matter would be very helpful.  Thanks in advance.

---

### Post by bluefrog on 2007-01-02
try
sudo apt-get install openssh-server

you should be fine

James

---

