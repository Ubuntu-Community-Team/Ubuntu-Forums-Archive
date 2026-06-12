---
title: "VMware?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-02-25
Okay, I am an absolute photoshop fanatic. I've tried gimp, i couldn't really get that used to it, even when i changed the menus using gimpshop. I've also tried ps hack using the registry and such and portable photoshop -- both are too slow and have key features missing. 

Anyway, the point of this message is.. i don't want to dual boot, i don't even want to use windows XP.. but i want photoshop. I installed VMware, and set everything up fine. 

Sadly, when i try to open vmware now, i get the following: 

> nick@nick-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

nick@nick-desktop:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

nick@nick-desktop:~$ 


If i restart my system 2 times, the virtual internet will shut down, then i have to go through the config process again, and then i can open vmware and boot windows.. the problem is, i have to do this each time..

can anyone help me fix this problem, so i can just open vm ware whenever i need to without having to restart my system 2 times and re do the config file ?

---

### Post by ashmew2 on 2007-02-25
how about this command in a terminal
```

killall vmware

```
and then trying the config command.
Or if that doesnt work , you could try looking in the System Monitor > Processes and killing all the processes of vmware...
Just a guess (i dont have VMware installed nemore).

Btw , have u tried using wine to run Photoshop ?

---

### Post by KIFIKA on 2007-02-25
I havn't tried the kill all yet, i'll let you know how it works. 

As for using wine, yes thats what i used to run the portable photoshop and the one where you get the registry and all, same problem it was 10 minutes to startup sometimes more and some key features and tools wouldnt work.

---

### Post by KIFIKA on 2007-02-25
Killall vmware doesn't work it tells me 

> vmware: no process killed

---

### Post by veloce on 2007-02-25
What virtual networks do you actually need?  You seem to have all of the options set up and at least one of them is screwing up.  It may be as simple as, next time you get to run vmware-config, eliminate all the networks.

Do you get any  errors when running vmware-config (when you can get it to run of course)?

---

### Post by xpod on 2007-02-25
Or Virtualbox possibly??
Really simple compared to the other methods seemingly but i`ve never tried anything other than
Virtualbox so cant confirm this

nice `n` easy though
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by veloce on 2007-02-25
> **xpod said:**
> Or Virtualbox possibly??
Really simple compared to the other methods seemingly but i`ve never tried anything other than
Virtualbox so cant confirm this

nice `n` easy though
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Yes, virtualbox could be a goer for this application.  For me, the free version is a bit nobbled (no usb, rdp, ...)

---

