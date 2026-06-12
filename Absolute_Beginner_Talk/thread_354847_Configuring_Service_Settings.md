---
title: "Configuring Service Settings"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-06
I opened up the Service Setting applet in Ubuntu and am wonder which services can safely be deactivated. I see that several should be left active but some I'm not sure of.

This is a desktop computer. 

Both "Actions scheduler" (anacron) and "Actions scheduler" (atd) are active. Do both need to run? If not which can be shutdown? 

Bluetooth device management. I'm guessing since I don't use Bluetooth I can safely shut this down.

Braille display. Not needed so down it goes.

There are two Computer activity loggers (klogd and sysklogd) are both needed?

CPU Frequency manager (powernowd). Does a desktop computer need this running? My processor (P4 1600) doesn't allow frequency changes. It is fixed at 1600. 

Power management. Again two are running (acpid and apmd). This is a desktop computer, are these needed?

Speech synthesis. I don't use any speech synthesis software. Can this be shut down?

---

### Post by Patrick K on 2007-02-06
bump

---

### Post by frimilden on 2008-04-03
I am also wondering about this, so bump again.
Any input is appreciated.

---

### Post by NightwishFan on 2008-04-03
I would say if you do not use a service it is save to shut it down, although I assume it cannot hurt much to leave it on. The cpu scaler if you do not use I believe can be safely disabled. You should leave power management on. The loggers/synthesis I assume could disable as well. Just if it seems like it may cause a problem or you get a warning message leave it on.

---

### Post by frimilden on 2008-04-03
> **NightwishFan said:**
> I would say if you do not use a service it is save to shut it down, although I assume it cannot hurt much to leave it on. The cpu scaler if you do not use I believe can be safely disabled. You should leave power management on. The loggers/synthesis I assume could disable as well. Just if it seems like it may cause a problem or you get a warning message leave it on.

Thank you for the input. 
I am curious still about the "Actions Scheduler services"
Does this control update checks and the like?

---

### Post by NightwishFan on 2008-04-03
I would assume so but it may be more important than that. So I would say leave it on.

---

### Post by frimilden on 2008-04-04
> **NightwishFan said:**
> I would assume so but it may be more important than that. So I would say leave it on.

Ok thank you again for the input and swift response. 
I am quite new to Ubuntu and linux in general, so it is quite the learning experience 
after 10 years of MS Winblows so bear with me, I am sure I have many more 
Questions to come :tongue:

That being said it would be very much welcome if someone could elaborate 
more on just exactly what these services do and the consequence of shutting 
them down. 

For instance do I need both "Action Schedulers" running? If I shut down say " anacron" what is the potential fallout? What does this particular service control? 

Or what about the Computer Activity Logger services? What if I shut down say "klogd" ?

Thanks again all for taking the time to have a read and respond, it is highly appreciated. :popcorn:

---

### Post by NightwishFan on 2008-04-04
I wish I could elaborate but I am still learning myself. If I come upon some information I will be sure to inform you. Good luck. :)

---

### Post by frimilden on 2008-04-04
> **NightwishFan said:**
> I wish I could elaborate but I am still learning myself. If I come upon some information I will be sure to inform you. Good luck. :)

Ok thanks again for all your help much appreciated mate :popcorn:

---

### Post by keep-on-smiling on 2008-04-20
Hi

yes - I too would like some info on this - so "bump"

:)

---

