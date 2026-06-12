---
title: "Various problems"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-05-10
Hello!

I've got some problems with some programs that I thought I might ask for help about.

I can't seem to download stuff from programs such as Azureus and Frostwire. When I open Frostwire, it won't connect at all, and with Azureus, I am able to add torrent-files, but nothing happens. What can this be?

Also, I can't seem to get sound from pages in Firefox. For example movie files and such. I can play music files in XMMS, so the overall sound is okay, it's just Firefox that is dead silent. And I seem to get a lot of "Install plugin"-things with some streaming videos. But when I press the "Install plugin"-button, Firefox can't find the plugin.

---

### Post by nanotube on 2006-05-10
as to azureus or frostwire - seems like a firewall/nat problem at first glance. check and see if your firewalls let the right ports through.

as to sound.. don't know if this will help, but try going to the first link in my sig, and go to the "sound, firefox, and flash" section and read.

---

### Post by wat3r on 2006-05-10
Okay. Thanks.
I don't have any specific firewall set up. Unless Ubuntu doesn't sets up a firewall automaticly, then no, I don't have a firewall.
I will try that guide, it seems good, just have to fix some root issues first :cool:

---

### Post by Sef on 2006-05-10
Also to get sound in flash, do this:

Gnome from the terminal (Applications > Accessories > Terminal):

sudo apt-get update

sudo apt-get install alsa-oss

If you have KDE, it is Konsole

kdesu apt-get update

Kdesu apt-get install alsa-oss

---

