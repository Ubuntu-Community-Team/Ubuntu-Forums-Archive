---
title: "kubuntu start up problem"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by stickyplaster on 2007-05-16
Hi
Hope this is in the right place.

I recently installed kubuntu 7.04 and when I boot using the default kernel I end up with a blank screen. 

I have checked/edited my xorg.conf file which seems okay and this would seem to be confirmed by the fact that when booting with the default kernel in recovery mode I can start kde perfectly well from the command line via startx.

Now I wonder if something that is started in normal mode is stopping normal loading of x but I can't see what it is.

The only thing out of the ordinary when booting is that the check disc utility seems to stall on checking a large FAT32 partition (not a boot partition) on the same HD as the kubuntu installation. It fails with status 1. However, this happens in both normal and recovery mode so I would think this was inconsequential.

Other than that there does not seem to be any problems during boot. Perhaps if someone could point me in the direction of what is not loaded in recovery mode it would be a start as there does not seem to be an Interactive Boot mode - or is there?

Or does anyone have any other ideas?

regards

---

### Post by zvacet on 2007-05-16
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by stickyplaster on 2007-05-16
Hi zvacet

Thanks for getting back. Although I am not at my machine at present I looked at the page you provided the link for.

Quote:
Sometimes new users, expecting a graphical environment after installing Ubuntu, end up at a black screen with some white text that has a login prompt. When they log in, they see this:
username@ubuntu:~$

This is not the case - I'm pretty sure kdm tries to start but just goes to a completely blank screen.

Quote:
Do you have a graphical environment installed?

I do - kde via kdm

Quote:
sudo dpkg-reconfigure xserver-xorg

I edited my xorg.conf and it all seems fine. When I startx in recovery mode everything is fine. Now, this would suggest to me my xorg.conf is okay - unless when in recovery mode startx uses some default/safe xorg.conf file and not /etc/X11/xorg.conf. 
Is this the case? If not then my xorg.conf must be okay I would have thought.

kind regards

---

### Post by stickyplaster on 2007-05-16
Hmm

Even more bizarre. If I start up via rescue mode - as described before - and reboot/restart from here, then allow the machine to boot via the normal boot everything starts up fine. If I restart from this boot, however,  I get the aforementioned blank screen/hang (nothing works). A reset - boot into rescue mode restart again with normal boot - okay again. Restart from here, however, and same problem.

I am somewhat confused.

I have just come to Ubuntu from another distro and even although Ubuntu is the first new one I have tried it looks good and I would really like to get it to work, Rather, that is, than going off elsewhere. So I hope someone can help.

regards

---

### Post by vanadium on 2007-05-16
What do you mean with a blank screen? Do you get to the graphical login manager? Or don you even get to see that one?

I have currently issues with starting Ubuntu, and they are related to the network. I need a static IP at work and have a wireless at home. Very recently, when coming from werk or getting to work 9i.e. changing network locations), I get past the login screen, but then the background is displayed. Only after a long time would the panels appear, and waiting long enough would display more elements. After commenting out all entries in /etc/network/interfaces (on a shell prompt), the system starts fast and normally. I can then select a network "location" to start networking.

---

### Post by stickyplaster on 2007-05-16
> **vanadium said:**
> What do you mean with a blank screen? Do you get to the graphical login manager? Or don you even get to see that one?

Hi
Well under the circumstances I described my blank screen is just that. It appears to be trying to start kdm then the computer hangs with a completely blank screen no login or anything else.

> **vanadium said:**
> 
I have currently issues with starting Ubuntu, and they are related to the network. I need a static IP at work and have a wireless at home. Very recently, when coming from werk or getting to work 9i.e. changing network locations), I get past the login screen, but then the background is displayed. Only after a long time would the panels appear, and waiting long enough would display more elements. After commenting out all entries in /etc/network/interfaces (on a shell prompt), the system starts fast and normally. I can then select a network "location" to start networking.

My network,  - well a NIC and router all appear fine - configured to run off DHCP

regards

---

### Post by stickyplaster on 2007-05-16
Well, I have been installing a few things and as a result, I suspect, updating some system stuff, Lo and behold a successful restart starting up as normal so fingers crossed! I don't want to speak too soon but...

Thanks for all the replies - ubuntu looks really good

regards.

---

