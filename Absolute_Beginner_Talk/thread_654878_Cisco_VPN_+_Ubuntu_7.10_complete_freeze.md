---
title: "Cisco VPN + Ubuntu 7.10 complete freeze"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by teshne on 2007-12-31
I have installed the cisco vpn client following the instructions at this web site [http://yaup.wordpress.com/2007/11/07/cisco-vpn-on-ubuntu-710/]("http://yaup.wordpress.com/2007/11/07/cisco-vpn-on-ubuntu-710/")  and I got it working fine, I can even use rdesktop to connect to my computer at the office but it all last about 10 seconds because the computer freezes completely. The only thing I can do is a hard reboot.
Does anyone else gets this problem? I am quite new to linux so I don't know how to troubleshoot this issue.

Any help would be much appreciated.

Thanks for you help.

---

### Post by blueridgedog on 2007-12-31
Is the freeze associated with usage or will it do it if set idle?

---

### Post by teshne on 2008-01-01
I left it idle and it wouldn't crash, but as soon as I try to browse on the internet (or remote on to a computer) it crashes. I think it may be crashing only when there's traffic on the tunel... I don't know.
I installed vpnc and imported the settings from my configuration file and it seems to be working fine, no freezes so far.

I would like to know what is causing the freezes when I use the Cisco vpn client though.

thanks.

---

### Post by blueridgedog on 2008-01-01
I am glad you found a solution.  As far as the cisco client goes, there is some great info here:

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

Read the updates.

---

### Post by teshne on 2008-01-02
Thanks! I will go through it when I am back at home and see if I can get the Cisco client to work, I may need to apply some patches.

Thanks again.

---

### Post by mnk0 on 2008-05-26
so you got around this error by going to vpnc ?? i was also having the same error with vpnclient-linux-x86_64-4.8.01.0640-k9.tar on hardy 8.04 ..

it would freeze just like that, i'll try the vpnc next, but just wierd is there an updated cisco vpn client??



--
OMAR

---

