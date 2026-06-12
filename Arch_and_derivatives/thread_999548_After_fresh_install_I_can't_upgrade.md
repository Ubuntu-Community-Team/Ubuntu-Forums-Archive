---
title: "After fresh install I can't upgrade"
date: 2008-12-02
forum: Arch and derivatives
---

### Post by Jordan777 on 2008-12-02
This has been a problem that has plagued me for weeks.  I just got through installing fresh from my Arch iso for the nth time.  What's stumping me is that I can connect to my network but as soon as I try to ping google I get an unknown host error and then when I try to download packages I just keep getting a transient resolver failure.  Does anyone know what's causing this?  Sometimes it feels like Arch is determined to never install on my computer.  I've lost interest in Ubuntu and the only thing that I really want to try is Arch.

I'm using an ASUS M2N32-Sli mobo with an onboard wireless card.  It uses the realtek 8187 driver.  I just can't figure out what's causing this.  I don't think it could be my physical network because Windows works just fine.  I know the driver implementation is different but I'd hope I could at least get it to work on some Linux distribution.  

I had networking problems with Ubuntu 8.10 and that's why I can't stay with it any longer.  I'm just one of those people who needs a stable and constant internet source.

So, back to my original question. Has anyone seen a fix for this or can link me to what might be causing it?  I've changed mirrors and used only http mirrors or only ftp mirrors.  Nothing seems to work.

---

### Post by handy on 2008-12-02
Can you get a cable connection?

If you could you could setup with that & pursue the wireless stuff from a setup & running Arch install.

I'm sure you have been through all of this stuff before in your previous thread on this problem.

I can't be of any more help, I don't use wireless.

---

### Post by Jordan777 on 2008-12-02
Looks like I'm just gonna have to setup a cable connection.  I didn't before because of all the trouble I'd have to go through but I'll do it now.  I'm just determined to beat Arch.  Do you know if I have to go in and change my ethernet setting now to dhcp?  I mean I know my router and modem uses dhcp so I guess I have to go and change that option.  Hopefully I can just find the config file so I don't have to reinstall yet again.  Would you happen to know what its file pathname is?

---

### Post by handy on 2008-12-02
In the ***NETWORKING*** section of ***/etc/rc.conf*** you set dhcp, it is not a very big file for you to have a quick scan of.

---

### Post by rsambuca on 2008-12-02
Did you add your hostname to /etc/hosts?

---

### Post by fwojciec on 2008-12-02
> **Jordan777 said:**
> This has been a problem that has plagued me for weeks.  I just got through installing fresh from my Arch iso for the nth time.  What's stumping me is that I can connect to my network but as soon as I try to ping google I get an unknown host error and then when I try to download packages I just keep getting a transient resolver failure.  Does anyone know what's causing this?  Sometimes it feels like Arch is determined to never install on my computer.  I've lost interest in Ubuntu and the only thing that I really want to try is Arch.

I'm using an ASUS M2N32-Sli mobo with an onboard wireless card.  It uses the realtek 8187 driver.  I just can't figure out what's causing this.  I don't think it could be my physical network because Windows works just fine.  I know the driver implementation is different but I'd hope I could at least get it to work on some Linux distribution.  

I had networking problems with Ubuntu 8.10 and that's why I can't stay with it any longer.  I'm just one of those people who needs a stable and constant internet source.

So, back to my original question. Has anyone seen a fix for this or can link me to what might be causing it?  I've changed mirrors and used only http mirrors or only ftp mirrors.  Nothing seems to work.

What do you mean by "connecting to the network"?  Because the symptoms you list suggest that the problem is that you have no working internet connection.  You need to configure internet connection as the first thing you do after installing Arch.  Pacman, although it can be made to work with local repositories, assumes that you have a working internet connection.

The relevant wiki article is this: [http://wiki.archlinux.org/index.php/Wireless]("http://wiki.archlinux.org/index.php/Wireless")

There is also a wiki page for your wifi card: [http://wiki.archlinux.org/index.php/Rtl8187_wireless](http://wiki.archlinux.org/index.php/Rtl8187_wireless)

---

### Post by Jordan777 on 2008-12-02
I have a wireless card.  I set it up every time before I go to try installing packages.  My other computer is constantly hooked to the network and it works just fine so I don't think it's my actual network.

---

