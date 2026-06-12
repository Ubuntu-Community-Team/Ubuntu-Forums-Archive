---
title: "How to connect to a WPA"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-27
I only see a WEP option

---

### Post by nunomiguelmota on 2007-04-27
A little more information would help, like what version of ubuntu it is and what program are you using to connect etc....

---

### Post by mojo123 on 2007-04-28
My router has a password but the password is a WPA password not a WEP. In the ubuntu wifi connector it only gives WEP. How can i connect to a WPA excrypted network

---

### Post by nunomiguelmota on 2007-04-29
What Ubuntu version are you using? are you using network-manager?

---

### Post by Pas3n7 on 2007-04-29
I'm having the same problem (I think) on 7.04 (feisty). When I try to connect through network manager, the only encryption options are for WEP, nothing for WPA.

I'm using a hawking hwc54d (an RaLink chip I believe) I just upgraded today, so it's pretty much a clean install.

Thanks,
Pat

---

### Post by Pas3n7 on 2007-04-29
Update: just upgraded to the latest 2500 serialmonkey CVS build. Still nothing. WPA worked fine in Dapper.

I took a screenshot if it helps.

---

### Post by nunomiguelmota on 2007-04-30
It seems that the ralink driver does not support wpasupplicant....take a look at this[ thread]("http://ubuntuforums.org/showthread.php?t=392415&highlight=feisty+ralink")

hope this helps you

---

### Post by ushills on 2007-04-30
[http://ubuntuforums.org/showthread.php?t=419709](http://ubuntuforums.org/showthread.php?t=419709)

Try the above How to:

The RT61 driver is built into the latest Feisty Fawn (you do not need to compile the RA link ones) although WPA is not available.

I uninstalled the in-built network manager, it is important to check the route as you should only have Ra0 listed not eth0 otherwise there will be a conflict.

I also needed to disable my internal ethernet card as I was getting a lot of crashes, since disabling it no problems and secure wireless.  My card is a WMP54G.

---

### Post by Pas3n7 on 2007-04-30
Well, I guess that answers my question. Guess I'm back to manual configuration.

Thanks guys.

good luck mojo, you may want to see if your problem has the same cause.

---

