---
title: "Samba problems...again..."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-28
Yes, more samba woes are coming...
My samba connection was working fine till a day ago.  Everytime i click on the ubuntu share icon on my windows box, i get the "you do not have enough permissions and network path was not found" message.  I tried reinstalling samba, allowed all connection/sources from the windows box in firestarter, i restarted the samba daemons in a terminal, and im running out of options here.  anybody got a clue?

---

### Post by user1397 on 2006-04-29
:evil:

---

### Post by user1397 on 2006-04-30
bump

---

### Post by user1397 on 2006-05-01
bump

---

### Post by Jason_25 on 2006-05-01
So instead of bumping why don't you examine your samba logs to see what is wrong.

---

### Post by user1397 on 2006-05-01
well everything seems fine:

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Mshome
   security = SHARE

   wins support = no

and:

[SHARE]
path = /home/ubuntu/Desktop
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by Jason_25 on 2006-05-01
That's your smb.conf.  Hopefully that hasn't changed since it last worked.  The samba logs are in /var/log/samba .

---

### Post by user1397 on 2006-05-01
[quote=Jason_25]That's your smb.conf.  Hopefully that hasn't changed since it last worked.  The samba logs are in /var/log/samba .[/quote]
Do you want me to post my log.nmbd file or my log.smbd file or both?

---

### Post by Jason_25 on 2006-05-01
Well check them yourself first, and if you don't see anything obvious then I guess post them both.

---

### Post by user1397 on 2006-05-01
Well in my log.nmbd file, it keeps on saying "Failed to send packet trying to register name (my computer name)"
and in my log.smbd file, it keeps on saying "Unable to open printcap file /etc/printcap for read!"
Do you know what these things mean?

---

### Post by Jason_25 on 2006-05-01
I'm not familiar with those errors.  What you might try doing is try to connect from another pc and the examine the end of the logs.  Make sure you haven't recently installed any firewalling software on either pcs.

---

### Post by user1397 on 2006-05-01
[quote=Jason_25]I'm not familiar with those errors.  What you might try doing is try to connect from another pc and the examine the end of the logs.  Make sure you haven't recently installed any firewalling software on either pcs.[/quote]
Well I have the firestarter firewall on my ubuntu box, but i allow all connections and services from the windows box. as far as i know, my windows box just has the windows firewall, i don't know if that's interfering. I do have a wireless router connected to my linux box, and my windows box is connected wirelessly to the router.  i don't know what you mean by
 [quote=Jason_25]I'm not familiar with those errors. What you might try doing is try to connect from another pc and the examine the end of the logs.[/quote]
???

---

### Post by Jason_25 on 2006-05-01
Just open the logs after you've tried to connect and scroll down to the bottom, or the top depending on how your viewing it.  Disable all firewalls until you have fixed the problem.

---

### Post by user1397 on 2006-05-02
My samba problems are fixed. it just so happened that since i have dhcp, my ip addresses were backwards, so i just told my windows box to go to the new ip and that worked!

---

