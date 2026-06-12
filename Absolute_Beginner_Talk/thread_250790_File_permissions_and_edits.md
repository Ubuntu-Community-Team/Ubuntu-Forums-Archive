---
title: "File permissions and edits"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Adventx on 2006-09-04
Ok so I just started on Ubuntu today after almost pulling all my hair out attempting to use FC5, and I'm liking Ubuntu so far but I'm still running into a few issues.

I've read a lot of threads on wlan setups and partially know some of the things about it. I was happy to see that Ubuntu found both my wireless adapters right after install, yet it wont connect to my router on either of them. And I think that I've figured out the problem but am unable to attempt it due to some issues.

I'm trying to simply drag and drop the drivers from my linksys WPC54GS V2 setup cd into my /lib/firmware folder, a very simple request, yet I'm unable to do this due to the fact I dont have permission to do anything apparently although I'm admin and have root pw. I've read threads on how to move files through terminal but apparently I cant move files from my cd because its read only, and to be honest I would like to just drag and drop any files into any folders that I want at any given time without being prompted for pw or having to go into terminal and do 20 commands just to do a simple drag and drop routine.

As for the second part of this question. Where do I find the wlan settings that Ubuntu has already found so that I cant tell it which .sys and .inf to use so that its not trying to use the broadcom one that its been attempting to use?

---

### Post by bodhi.zazen on 2006-09-04
Ubuntu uses "sudo" not "su".

for "drag and drop" try 
```
gksudo nautilus
```

---

### Post by Adventx on 2006-09-04
thank you that allowed me to drag and drop the drivers into my firmware folder, now I just need to edit my eth2 to use the driver that I just put there

---

### Post by bodhi.zazen on 2006-09-04
Not following you.

Are you trying to edit /etc/network/interfaces to enable eth2?

```
sudo nano /etc/network/interfaces
```

Or activate a driver? To activate a driver you just installed -> reboot.

---

### Post by Adventx on 2006-09-04
I'm trying to tell eth2 which driver to use instead of the broadcom driver that it wants to use now

---

### Post by bodhi.zazen on 2006-09-04
> **Adventx said:**
> I'm trying to tell eth2 which driver to use instead of the broadcom driver that it wants to use now

Err, since noone else has responded I will try.

Starting with the obvious:

1. did you try a re-boot?

2. You gave the impression you knew what you were doing or following a guide. If so, exactly what problem are you having? error message.

3. The configuration file is /etc/network/interfaces.

---

