---
title: "HAVP and mandatory mounting"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2006-11-15
Hi folks,

Ok disclaimer I have been working with Ubuntu Linux (and never any other distro) for approximately 3-4 weeks.

I am building a mail server and so far have postfix, amavis, clamav, mysql, virtual mail etc installed and I am going through the configuration process to try and get it all to talk to someone, anyone.

My latest adventure has me trying to install HAVP and get it going. I managed to get the directory /var/tmp/havp mounted with a mandatory lock for a user called XYZ as per the instructions on HAVP's website. When I tried to start Havp I got an error on the Clamav scanner which I tried to resolve but failed miserably. So I shutdown my testbox to give myself a break and when I start it back up if I try to start HAVP I get the error about HAVP having to have a mand lock.

I try to mand the location again (tried with the remount switch as well) but no joy it would mount with the lock.

I have tried adding an entry to /etc/fstab to see if I could do it that way but obviously I am not smart enough to do it as it failed.

Can anyone give me the entry I would have to add to the /etc/fstab in orde to have a mandatory lock on /var/tmp/havp for user XYZ permanently?

Also if anyone has any sample entries from the clamav scanner section of the HAVP.config file that I could use to try and diagnose where I made a mistake in my entries there I would also greatly appreciate it.

---

### Post by Coinnach on 2006-11-15
Can anyone help with this please?

---

### Post by i23098 on 2006-11-19
I'm having the same problem as you ](*,) 

Can someone please help :confused:

---

### Post by Coinnach on 2007-01-04
i23098,

I gave up and removed it - I will find something else to do the job.

---

