---
title: "Debian 6 desktop?"
date: 2011-06-01
forum: Any Other OS
---

### Post by hugom on 2011-06-01
Does Debian 6 use gnome 2.x? 

I really don't like gnome 3 and do not want to install a distro with it.

I googled around and looked on the website but couldn't find to much.

Any help would be great, thanks.

---

### Post by el_koraco on 2011-06-01
yes, gnome 2.30 i think

---

### Post by krapp on 2011-06-01
GNOME 2 will be standard on Debian for at least the next 18 months or so.

---

### Post by hhh on 2011-06-01
@ hugom, you might be interested in the Live images as they're the easiest way to get Debian installed that I've found...
[http://www.debian.org/CD/live/#live-install-stable](http://www.debian.org/CD/live/#live-install-stable)

The Gnome desktop package list is here, and it uses Gnome 2.30...
[http://cdimage.debian.org/debian-cd/6.0.1-live/i386/web/debian-live-6.0.1-i386-gnome-desktop.packages](http://cdimage.debian.org/debian-cd/6.0.1-live/i386/web/debian-live-6.0.1-i386-gnome-desktop.packages)

-edit- One note about the Live CD, after install you'll find that if you do a restart it bypasses Grub entirely, which is faster and is fine if you don't dual boot frequently. Doing a full shut down works normally. If you don't like that feature, just remove the package kexec-tools.

---

### Post by juancarlospaco on 2011-06-01
ATM, Gnome 2, KDE 4, on my Debian BSD.

---

### Post by garvinrick4 on 2011-06-01
Keep a flash drive handy incase you have to download drivers to it and Debian will install
for you while in installer. I needed to fetch firmware for intel Network card but went smoothly.
Also be ready to set up /etc/sudoers first thing before post installation work.

---

### Post by krapp on 2011-06-01
> **juancarlospaco said:**
> ATM, Gnome 2, KDE 4, on my Debian BSD.

You're using kFreeBSD?

How's it going?

---

### Post by krapp on 2011-06-01
> **garvinrick4 said:**
> Keep a flash drive handy incase you have to download drivers to it and Debian will install
for you while in installer. I needed to fetch firmware for intel Network card but went smoothly.
Also be ready to set up /etc/sudoers first thing before post installation work.

???

1) Debian discourages "sudo" for a reason.

2) And, generally, if you can't do a net-install without drivers, don't do a net-install! There are ways to install Debian that don't require an Internet connection.

---

### Post by hhh on 2011-06-01
> **krapp said:**
> 1) Debian discourages "sudo" for a reason.
???
[quote=Debian Wiki]In a terminal : you can use su (or gksu) to change your identity to root.
However, it's recommended to configure and use sudo (or gksudo) to run a given command.[/quote]
[http://wiki.debian.org/Root](http://wiki.debian.org/Root)

[quote=Debian Wiki]Using sudo is better (safer) than opening a session as root for a number of reasons, including...[/quote]
[http://wiki.debian.org/sudo](http://wiki.debian.org/sudo)

---

### Post by krapp on 2011-06-01
> **hhh said:**
> ???

[http://wiki.debian.org/Root](http://wiki.debian.org/Root)


[http://wiki.debian.org/sudo](http://wiki.debian.org/sudo)

The Debian wiki is a mess. A far better indication of Debian's opinions about su/sudo is that sudo isn't enabled by default, and every which way to install Debian (as far as I know) requires setting up two passwords, as opposed to getting away with just one as Ubuntu allows.

---

### Post by garvinrick4 on 2011-06-01
> generally, if you can't do a net-install without drivers, don't do a net-install!Debian gave me a way to install firmware myself before install so as to have wlan0 at end
of install. I thought that was mighty nice of them to search my hardware to make sure
I had appropriate drivers and if not I could put them on a flash drive and they would install them
for me. Mighty nice. Used a Live Cd of Debian 6 to install and I have no complaints about
install procedure. Most of us linux users no how to use an installer to his or hers advantage, thanks for your input though.

---

### Post by hugom on 2011-06-03
Great. Thanks for everybodies help.

Really good and appreciate it guys!

cheers

---

### Post by juancarlospaco on 2011-06-03
> **krapp said:**
> You're using kFreeBSD?

How's it going?

Yes, nice, it even have Software Center :)

---

### Post by kansasnoob on 2011-06-03
Even though this is marked "solved" I'd like to point out that both Debian Squeeze and Ubuntu Lucid (aka: 10.04) use Gnome 2.30. Squeeze will presumably be supported for at least another 19 or 20 months and Lucid will be supported until April 2013.

No need for panic :)

---

