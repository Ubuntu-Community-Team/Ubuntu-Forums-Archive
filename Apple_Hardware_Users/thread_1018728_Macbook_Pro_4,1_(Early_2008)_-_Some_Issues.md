---
title: "Macbook Pro 4,1 (Early 2008) - Some Issues"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by lat2005 on 2008-12-22
Hello,

my Macbook Pro is the following:
4,1 (Broadcom 5328 wireless rev 05) Early 2008.

OS:  Kubuntu/Ubuntu 8.10 amd64

I installed Kubuntu 8.10 by following the instructions online (Triple boot with Windows and MacOSx).

I then installed ubuntu-desktop after seeing some issues with kubuntu.
I enabled the wireless Broadcom STA driver that is in the restricted and then installed the applesmc and all the rest.

My problem is that I can't control the brightness of the LCD (or the keyboard backlight). In GNOME:
Fn + F1 results in the help.
Pressing F1 or F2 by themselves results in no change.
F3 - Nothing Happens
F4 is calculator
F5 - Music Player
F6 - Some little thing that seems to control the brightness for the keyboard show up. But I can't reduce it (by pressing it I maxed it out).

F9, F19, and F11 work as expected (controlling sound volume, mute)

How can I control LCD and keyboard brightness?

Second, my sound doesn't work, even after doing what the wiki said. Do I need to restart or does it take effect immediately?


Another Question I have is whether it's possible to use the alternate CD to install an encrypted ubuntu/kubuntu? It seems that windows has the 4 partition limitation and that encryption requires /boot that is unecrypted, violating the 4 parition limitation. Is there a workaround?


I've looked up instructions but haven't been able to fix these issues.

Thank you

---

### Post by hyperboloid on 2008-12-22
Assuming you didn't mess with the key settings in KDE, it sounds like you are getting interference between KDE & Ubuntu Desktop. You might try a fresh Ubuntu install, instead of Kubuntu. (I.e., Kubuntu + Ubuntu Desktop is probably not equivalent to Ubuntu.)

I have the same hardware running Ubuntu 8.10 and all the function keys work just fine, after following the steps in the Wiki [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid").

---

### Post by lat2005 on 2008-12-22
Sounds ok. I guess I'll redo it. Shouldn't be hard because ubuntu is the last thing that I install in triple boot anyway.

I'll come back if I have any other trouble.

---

### Post by lat2005 on 2008-12-22
Ok. I reinstalled linux with ubuntu 8.10 amd 64.

However my issue is (and has been) the wireless.

There are 2 networks, both authenticating using 802.1x. I can connect to one but not to the other. 
Their Info(This is what works in the first one, and they are the same kind of network):

802.1x dynamic WEP
PEAP
MSCHAPv2


On the one I can't connect to, and I need to, I get the nm-applet (gnome network manager) saying:  Requesting a network address from the wireless network ....

Those two little dots fill up green, but it won't get an ip address.
I tried using dhclient to get an ip address but it can't get any.

Is there a solution?
I tried to modify my /etc/networks/interfaces to add some lines:

auto eth1
iface eth1 inet dhcp

but then upon restart nm-applet doesn't start.

I also tried to use wpa_supplicant, but it tells me that the driver is busy.

Can anyone help me?

Thanks

---

### Post by cyberdork33 on 2008-12-24
try using wicd instead of nm. IDK if it supports Enterprise authentication like that, but you can try it. I seems that cerrtain types of network authentication messes up the dhcp client. This is a well-complained-about problem and there is nothing that has fixed it yet.

Check bug reports on launchpad.

---

