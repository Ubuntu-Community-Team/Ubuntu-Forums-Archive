---
title: "Cannot find the modem for the life of me (imac g3 slot loading)"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by chapium on 2006-06-14
Hey everyone, I hope I can get some help on this:

I cannot find the modem on my iMac G3 slot loader.  Supposedly it works under Yellowdog, so I figure its supported hardware.

My modem does not show up under the device manager, nor lspci, nor dmesg.  (Unless its disguised as something else).  

Once I'm back to the g3, I'll be sure to post the output of those here.

Anyways, I've been googling for hours but cannot find anything that helps with this.  Nothing seems to be able to detect this beast. 

I cannot figure out what

I'm not being very detailed here, but its mainly because I cannot find any information on this.

--

Finally one important note, I'm trying to use this to send/receive faxes.  When I try to send a fax under efax or sendfax, it fails immediately without dialing.  

I'll have more updated information tommorow if this is not enough.

---

### Post by nkbj on 2006-06-14
It is a known bug which is fixed in the next kernel update: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36499](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36499)

---

### Post by nkbj on 2006-06-15
The updated kernel (2.6.15-25) has been released to the update repositories.

---

### Post by Ptero-4 on 2006-06-16
The iMac G3 modem is hardware based so it's supported, but it is IIRC in /dev/ttyS0 and there's no /dev/modem symlink. But pppconfig allows you to manually select the modem port.

---

### Post by beerstim on 2006-08-26
How do I update the kernel to (2.6.15-25) when I cannot connect to the internet.  I'm new to linux and and have a imac 400dv with xubuntu on it I guess I could take it to a friends house and do it but i don't even know how to do it.

---

