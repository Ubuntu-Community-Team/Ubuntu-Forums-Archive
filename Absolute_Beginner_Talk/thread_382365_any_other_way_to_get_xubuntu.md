---
title: "any other way to get xubuntu"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-03-12
is there any other way to get xubuntu 6.10 other than download from site. i've tried to download it, started in the morning as it will take at least 1 full day and more to get. got to 50% and computer froze so lost it all. I don't really won't to try again as it will take forever. i have ubuntu 6.10 on a disk but was told xubuntu would be best for my old computer i am trying it on. Any help would be appreciated

---

### Post by Kateikyoushi on 2007-03-12
There are several mirrors for xubuntu, look here. [LINK]("http://www.xubuntu.org/get")

You can install xubuntu on an ubuntu installation without trouble then remove the ubuntu gui from it. [LINK]("http://www.psychocats.net/ubuntu/xubuntu")

Depending on how old that PC is you might not be able to install ubuntu it at all, you need at least 256Mb memory to run the ubuntu live-disc.

---

### Post by kerry_s on 2007-03-12
You want to try the mini.iso net installer?
-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

It will install directly  from the net and try to reconnect when the connection gets dropped.

But i recommend taking steps, if the connections that bad, maybe even just go straight for a custom install.

type> server 
login
sudo su
nano /etc/apt/sources.list
uncomment(#) all the deb repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm xfce4 leafpad firefox synaptic
reboot
login

This will give you a totally barebone install of xfce4(mini mini xubuntu)
once you got that you can use synaptic to install what ever else you want.

---

### Post by K.Mandla on 2007-03-12
(Sorry. Just a reminder that *x-window-system-core* is now *xorg* in 6.10, so it should be

```
apt-get install **xorg** gdm xfce4 leafpad firefox synaptic
```
:oops: I make that same mistake all the time. ;) )

(Yay! Another Leafpad fan! \\:D/ )

---

### Post by aysiu on 2007-03-12
Download the Xubuntu Alternate CD .ISO via BitTorrent.

BitTorrent is less likely to freeze up, since you're downloading from multiple sources.

Then you can install Xubuntu without needing a live session.

---

### Post by kerry_s on 2007-03-12
> **K.Mandla said:**
> (Sorry. Just a reminder that *x-window-system-core* is now *xorg* in 6.10, so it should be

```
apt-get install **xorg** gdm xfce4 leafpad firefox synaptic
```
:oops: I make that same mistake all the time. ;) )

(Yay! Another Leafpad fan! \\:D/ )

Actually x-window-system-core is a metapackage that insures all the X applications get installed, it installs xorg as well as other things needed for X. It is still there in edgy and it's here in fiesty as well.

And yes, love leafpad, always use it no matter what environment. :)

---

### Post by kerry_s on 2007-03-12
Hey K.Mandla, I was wondering if you have found a way to put that "running as root" banner on leafpad? I use a gtkrc2.0 so i can tell the root apps apart, it makes the background red, letters black and yellow/white highlight for all root applications. It's not ideal but i can live with it, but i would like to add the "running as root" banner.

Sample gtk:

```
style "default"
{
	GtkTextView::cursor_color	= "black"
	
	base[NORMAL]	= "red"
	base[ACTIVE]	= "white"
	base[SELECTED]	= "yellow"
	text[NORMAL]	= "black"
	text[ACTIVE]	= "black"
	text[SELECTED]	= "black"
}
class "GtkTextView" style "default"

```

---

