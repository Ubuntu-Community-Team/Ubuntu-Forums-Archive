---
title: "Cable internet"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by lnenad on 2007-05-19
First off, i installed Ubuntu today, and so far i like what i see :D 

I have a Cable modem and i don't know how to set it up can anybody help ? 

(Motorola surf board)

---

### Post by Rab22 on 2007-05-19
Do you have a router? Or is your cable modem plugged into your computer?

---

### Post by lnenad on 2007-05-19
It's plugged into my computer, it says in the manual that the enthernet card is the only way to run cable modem on linux, but i don't know how to configure it?

---

### Post by k33bz on 2007-05-19
should be automatic, at least for edgy and feisty for me it was

---

### Post by diatribe on 2007-05-19
indeed, plugging the cord in should automatically connect you

---

### Post by Pluggy on 2007-05-19
did for me , I have the same modem and comcast internet

---

### Post by lnenad on 2007-05-19
I plugged it in, doesn't work ? I even swiched to DNS in ethernet config. ?

---

### Post by wormser on 2007-05-19
To start off you should get a router.  It will allow for more than one computer to be hooked up, give you a firewall and be a dhcp server.  Another guy I was helping yesterday had problems getting online connecting directly to his comcast modem, so there might be an issue.  Usually Ubuntu just works when plugged into a network that has dhcp.

Here are some things you can try.  Applications> Accessories> Terminal - type the following commands in.

```
ifconfig
```

This will show us if you have an ip address.  If not then we need to try and get one.

```
sudo dhclient
```

Once that is done try an ifconfig again to see if you have an ip address.  If you do then try pinging and try ip numbers and domain names.

Good luck and let us know how it goes.

---

### Post by xpod on 2007-05-19
Try rebooting your modem and the pc mabey?

I`m no expert but if your ip address is assigned automatically  then it should all work automatically:)

---

### Post by lnenad on 2007-05-19
Rebooted my comp and modem and internet still doesn't work ? I will try ipconfig!

---

### Post by wormser on 2007-05-19
> **xpod said:**
> Try rebooting your modem and the pc mabey?

I`m no expert but if your ip address is assigned automatically  then it should all work automatically:)

I forgot to meantion that.  It is a great trouble shooting step.  Turn off your computer and unplug the modem.  Wait 10 seconds then plug the modem back in.  Once you have block sync (all lights on) then boot the computer.

---

### Post by wormser on 2007-05-19
> **lnenad said:**
> Rebooted my comp and modem and internet still doesn't work ? I will try ipconfig!

It is i**f**config.

---

### Post by twirp on 2007-05-19
I'm having a similar issue.
I tried the "sudo dhclient"
and the internet started working, but after turning off the computer and turning it back on, the internet wasn't working and I had to run the command again...
Previous versions (of ubuntu) auto-detected and setup the card, but why isn't 7.04 doing it...

Is there a way to make it so it keeps the same network settings after restarting...?

*Edit:*
On my other computer which I upgraded to 7.04, it working fine with the internet.  On the computer I just did a clean install on, I am having the issue with.  Should I do a clean install of a previous version and upgrade to 7.04...?

---

### Post by lnenad on 2007-05-20
Yes, works with sudo dhclient :D :popcorn: ! Thanks !

---

