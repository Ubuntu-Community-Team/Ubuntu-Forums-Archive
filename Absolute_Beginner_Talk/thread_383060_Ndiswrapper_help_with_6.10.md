---
title: "Ndiswrapper help with 6.10"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Mold Prince on 2007-03-12
So...I just dove into linux about a week ago after years of procrastination.  I felt like a king when I got my Microsoft MN-720 wireless card working with my Dapper install.  I decided I might as well make the upgrade to Edgy, and when I did, my wireless card stopped working.  Also...in the network settings menu, I no longer see a wlan0 entry.  

The graphical version of ndiswrapper (ndisgtk I think) shows the MN-720 present.  The system log (kern.log I guess) had a lot of entries that look like this.

> ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
 

I can't find those messages in my system log...and I'm at my wits end.  Any suggestions?

Thanks.

---

### Post by berylmichael on 2007-03-12
Since you changed from Dapper to Edgy, the Ndiswrapper may have become corrupted. Try reinstalling the Ndiswrapper for Edgy.

---

### Post by Mold Prince on 2007-03-12
Okay...so I've been poking around the Edgy wikis, and it says:

> Install ndiswrapper and drivers (due to a bug in Edgy, you need to specify ndiswrapper-utils-1.8)

So...the messages I CAN find in my syslog all mention ndiswrapper ver. 1.22.  How do I uninstall 1.22 and replace it with 1.8?

Thanks

---

### Post by Mold Prince on 2007-03-13
bump

---

### Post by Mold Prince on 2007-03-13
bump

---

### Post by Mold Prince on 2007-03-13
Sorry to keep bumping this...I'm pretty much at an absolute standstill until I get this figured out.

---

### Post by pirast on 2007-03-15
just install ndiswrapper-utils-1.8 and reboot

---

