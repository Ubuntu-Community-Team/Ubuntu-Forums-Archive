---
title: "Restart Samba Server in Ubuntu"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by echokilo on 2005-06-08
What is the command to restart the Samba Server in Ubuntu?

---

### Post by localzuk on 2005-06-08
Not on my Ubuntu box at the moment - but Debian works with /etc/init.d/smb restart
So that should work

---

### Post by NewbieNik on 2005-06-08
[QUOTE=echokilo]What is the command to restart the Samba Server in Ubuntu?[/QUOTE]
 many ways including SWAT or Webmin or use console and
smbd stop
smbd start

haven't tried smbd restart and not on smb machine.

---

### Post by echokilo on 2005-06-10
I'm only using a console so I don't have SWAT as an option.

I see that it is running, bur smbd does nothing. Are you sure it's smbd? Do I have to install a script to make that work?

---

### Post by desdinova on 2005-06-10
[QUOTE=echokilo]I'm only using a console so I don't have SWAT as an option.

I see that it is running, bur smbd does nothing. Are you sure it's smbd? Do I have to install a script to make that work?[/QUOTE]
 /etc/init.d/samba restart

---

### Post by echokilo on 2005-06-10
Thank you Desdinova!

---

### Post by didier101 on 2005-11-16
Interesting, I had the same problem, but mine only works with sh /etc/init.d/samba stop / start

---

### Post by upendar on 2008-07-07
> **echokilo said:**
> Thank you Desdinova!

fddfghjhggfg hfhkyfv hfghhjgfgfuiuyyty


regards 
upendar

---

