---
title: "firewall recomendations"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-23
could someone recomend a firewall for linux that is *current and is updated on a regular basis?* I would prefer something that is similar to firestarter (i would use fs but it seems as tho it has not been updated since 2005) that could run in the background and show me port scans etc.. similar to blackice or zone alarm.

---

### Post by kevdog on 2007-05-23
You could try guarddog, but I dont know if its going to show you port scans.

---

### Post by AtrejuT on 2007-05-23
as far as I know firestarter is only a graphical interface to configure netfilter/iptables so I don't know if it makes any difference if it wasn't updated for two years.

---

### Post by gamer_pro_2000 on 2007-05-23
Firestarter is nice.  I use it on my Feisty Fawn installation and it runs great.

---

### Post by silent1643 on 2007-05-23
> **AtrejuT said:**
> as far as I know firestarter is only a graphical interface to configure netfilter/iptables so I don't know if it makes any difference if it wasn't updated for two years.

right, i just didn't know if it should matter or not, i mean i guess it really doesn't but if i had to pick one over another it would be the one most active..

---

### Post by ggaaron on 2007-05-23
Iptables are in the kernel, so your firewall will get updated with it. I prefer guarddog as a gui, but probably they all have the same options available=)

---

### Post by silent1643 on 2007-05-23
thanks, i'll give guard dog a go :p

---

### Post by WezH on 2007-05-27
Is there any web-based management softwares? I'm running server without GUI so no Firestarter/GuardDog for me.

---

### Post by silent1643 on 2007-05-28
> **WezH said:**
> Is there any web-based management softwares? I'm running server without GUI so no Firestarter/GuardDog for me.
not sure sorry

---

### Post by ramjet_1953 on 2007-05-29
Do you need to alter your firewall settings?

By default, iptables closes all ports.

Unless you really know what you are doing and have good reason to do so, you are far better off leaving iptables well alone.

Also, you need to understand that if you are running Firestarter, or any other iptables configuration utility, those utilities need to be run in root mode. It is not wise to always have them running, as it is a serious security risk to have any application running in root mode.

Linux is not Windows and is very secure, without needing to tinker or "improve".

Get over your Windows paranoia and enjoy Linux without the security worries that you had before.

Regards,
Roger :cool:

---

### Post by wolfear on 2007-06-01
> **WezH said:**
> Is there any web-based management softwares? I'm running server without GUI so no Firestarter/GuardDog for me.

Check out Webmin.
[http://www.webmin.com]("http://www.webmin.com/index.html")

---

### Post by dandan123 on 2007-06-01
> **ggaaron said:**
> Iptables are in the kernel, so your firewall will get updated with it. I prefer guarddog as a gui, but probably they all have the same options available=)


I was trying to install guarddog but it seems to expect kde while I have gnome on Ubuntu.

Is there a gnome version available or will I have to install kde.

As you can see I'm not too familiar with Linux but I've worked a lot on Solaris.

---

