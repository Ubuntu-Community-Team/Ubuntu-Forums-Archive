---
title: "sshd and wlan active only after Gnome login"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by nomaed on 2008-02-27
Hi.

I am a complete *nix beginner. I installed Ubuntu last week (after struggling with FC8 for another week - wlan and sound stopped working after kernel auto update [yum] and generally lot of problems).
Ubuntu is great, everything works for now.

I have ssh enabled, but if I reboot the machine, I can remotely access it via ssh only AFTER I login in Gnome's login screen.

I suspect it is because wlan0 is connecting only after Gnome is running already. Of couse, in run-level-3 it's off as well.
How do I enable my wlan connection in boot time, without depending on the GUI?

Thanks.

p.s., using Gutsy mostly with default configuration, and added some stuff after installation but haven't change anything significan.

Also, I saw a topic that probably could have helped me ([http://ubuntuforums.org/showthread.php?t=268229](http://ubuntuforums.org/showthread.php?t=268229)) but it has no replies.

---

### Post by Origin415 on 2008-02-27
You will (probably) have to set up /etc/network/interfaces manually. As it stands, Ubuntu is using NetworkManager to start up the interface, which in turn starts when gnome logs in.

Heres a tutorial for Gentoo:
[http://gentoo-wiki.com/HOWTO_Wireless_Configuration_and_Startup](http://gentoo-wiki.com/HOWTO_Wireless_Configuration_and_Startup)

Just remember that Gentoo's /etc/conf.d/net equals Ubuntu's /etc/network/interfaces (an example of how Gentoo handles configuration better, all init.d scripts have their configuration in conf.d -- but I digress)

It will be difficult if you are trying to do WPA, but not too bad otherwise.

---

### Post by nomaed on 2008-02-27
Thanks, I'll try that as soon as I get home.

Now, about your mention of WPA, what's the problem with WPA?
I am using WPA/WPA2 with TKIP shared key.
My router is DLink DI-524b and I'm 99% sure that I can change the authorization method, but still, this one seems very simple because I also use my PDA and cellphone to login to this WiFi connection.

Thanks again.

---

