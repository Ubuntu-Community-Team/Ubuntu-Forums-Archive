---
title: "Fresh Ubuntu install will not shutdown"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-09
I have a new install of Ubuntu and it will not shutdon. it hangs at shutdown and I have a black screen with the Ubuntu logo, this happens 100% of the time, I have to manually shut it down.

Might just be some weird quirk as it always starts back up fine, not like I crashed it.

---

### Post by Hospadar on 2007-08-09
try going to a text terminal (ctrl-alt-F1) and shutting down with ```
sudo shutdown 0
``` This will give you a little more detailed info about what is actually shutting down, maybe it will help.  I've had this problem before but never actually got around to fixing it or figuring out why it happens.

---

### Post by nelamvr6 on 2007-08-09
Is it a Dell?

There's a known bug where certain Dells have trouble shutting down or re-starting.

---

### Post by macuto on 2007-08-09
This work  in some PC's:

type:
sudo gedit /etc/modules

add a new line with the following statement:

apm power_off=1

then save and reboot.

---

### Post by yogo on 2007-08-10
> **nelamvr6 said:**
> Is it a Dell?

There's a known bug where certain Dells have trouble shutting down or re-starting.

 Yeah it is a Dell, I can actually tell when it has shutdown so I just power off, never had a problem on boot so I will leave it as is for now.

PS Macuto, I will try that

---

### Post by Muchacho_Gasolino on 2007-08-12
> **Hospadar said:**
> try going to a text terminal (ctrl-alt-F1) and shutting down with ```
sudo shutdown 0
``` This will give you a little more detailed info about what is actually shutting down, maybe it will help.  I've had this problem before but never actually got around to fixing it or figuring out why it happens.

I'm trying to get that detailed info about what is shutting down, but that doesn't give me it. Even though the terminal is all text, when I sudo shutdown 0, it does the graphical shutdown and doesn't show me anything. Do you know of another way to see the text output? 

I'm having the same problem with Ubuntu not shutting down. I'm on a Thinkpad, running Kubuntu 7.04. I tried adding apm power_off=1, and that didn't help me.

---

