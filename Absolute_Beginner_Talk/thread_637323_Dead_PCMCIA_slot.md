---
title: "Dead PCMCIA slot"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by ireneybean on 2007-12-10
I suspect that my pcmcia slot may be kaput.  I have never really used it before so I don't know if this issue just started when I moved to ubuntu.

I am plugging a Netgear wg511T network adapter card into the slot.  the /var/log/messages shows no output at all when I plug in the card.  The lights on the card do not come on.  there is no ath0 device anywhere on the system that I can find.

however,   
find /sys/class/pcmcia_socket/

does give me
/sys/class/pcmcia_socket/
/sys/class/pcmcia_socket/pcmcia_socket0
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_mem
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_io
/sys/class/pcmcia_socket/pcmcia_socket0/cis
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_setup_done
/sys/class/pcmcia_socket/pcmcia_socket0/card_irq_mask
/sys/class/pcmcia_socket/pcmcia_socket0/card_eject
/sys/class/pcmcia_socket/pcmcia_socket0/card_pm_state
/sys/class/pcmcia_socket/pcmcia_socket0/card_insert
/sys/class/pcmcia_socket/pcmcia_socket0/card_vcc
/sys/class/pcmcia_socket/pcmcia_socket0/card_vpp
/sys/class/pcmcia_socket/pcmcia_socket0/card_voltage
/sys/class/pcmcia_socket/pcmcia_socket0/card_type
/sys/class/pcmcia_socket/pcmcia_socket0/power
/sys/class/pcmcia_socket/pcmcia_socket0/power/wakeup
/sys/class/pcmcia_socket/pcmcia_socket0/power/state
/sys/class/pcmcia_socket/pcmcia_socket0/device
/sys/class/pcmcia_socket/pcmcia_socket0/subsystem
/sys/class/pcmcia_socket/pcmcia_socket0/uevent

and
sudo ./etc/init.d/pcmciautils

gives me:

 * PCMCIA bridge driver already present in kernel


...
I'm thinking that it could be the card too (I do not have another one to test with) but it is new so I'm hoping it's not that...

 can anyone help me figure out what is going on?

---

### Post by spiderbatdad on 2007-12-10
this seems to be the night for this question...probably install pcmcia-cs from synaptic...look at this thread:
[http://ubuntuforums.org/showthread.php?t=570061](http://ubuntuforums.org/showthread.php?t=570061)

---

### Post by ireneybean on 2007-12-10
thanks for your quick response.  Sorry to start another thread when there's others around ... I did do a number of searches before I posted but I didn't come up with that one.

Anyway, I've worked through the info in that thread to the best of my ability and am not coming up with anything much more.  I did install pcimcia-cs.  I tried the cardctl insert and the pccardctl insert (neither gave an error, but subsequently running pccardctl status said "no card found"  I also tried rebooting my laptop with the card installed, no change.
 
not looking good for my pcmcia slot eh?

---

### Post by spiderbatdad on 2007-12-10
maybe someone in the hardware&laptops subforum will have experience...I'm sure it's a configuration issue that must be worked through.:)

---

