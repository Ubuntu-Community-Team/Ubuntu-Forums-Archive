---
title: "dual boot KDE and gNome"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by Derktoon on 2006-02-21
is it possible to dual boot both KDE and gNome on a single partition? or do they need to have their own little place to call /home first?

ye gods i feel like a n00b...

---

### Post by mostwanted on 2006-02-21
Well, they're desktop environments, basically just collections of programs, so it's not really dual-booting. But yes it's possible, just install the kubuntu-desktop package in Gnome or the ubuntu-desktop package in KDE, then choose another desktop to boot into when you're at the login screen.

Also, it's Gnome or GNOME (GNU Network Object Model Environment), not gNome :P

---

### Post by Beej on 2006-02-21
Gnome and KDE will share the same /home folder. All you need to do is install KDE. 

If I remember correctly, all you need to do is install kubuntu-desktop from synaptic or from terminal using "sudo apt-get install kubuntu-desktop"

Then log out of ubuntu to the GDM screen (login screen) there is a button "sessions" press this and select KDE. login as normal and welcome to KDE on Ubuntu (Kubuntu).

Beej

---

### Post by Derktoon on 2006-02-21
ok, that makes a relative amount of logical sence. the reason i wasnt sure was i had an old version of Fedora, which came packaged with KDE and Gnome (i was sure ONE of the letters was capitolized, thanks for the correction though :-P) so i wasnt sure how it was done, but for now i have KDE on there. So i assume the process will be the same but with Gnome.

---

### Post by abhaysahai on 2006-02-22
in KDE type 
sudo apt-get install ubuntu-desktop 
from the KDM or GDM whatever you have selected, select either KDE or Gnome and enjoy.

---

### Post by steevc on 2006-02-22
I started with Hoary and added the Kubuntu stuff before I upgraded to Breezy. I mainly run KDE, but I still seem to have a lot of Gnome running in the background. e.g. when I put in a CD or memory card I might get Nautilus starting.

I think that both KDM and GDM are running. Should it only be one at a time? I guess that if I had one session of each running they would both be running, but that's another issue. Even with 2 users logged in on KDE I get windows popping up on both when media is inserted. Maybe there's a way to restrict it to one user, but how would the system chose?

Sorry if this is a confused mess, but I'm just typing what's on my mind at the moment.

---

