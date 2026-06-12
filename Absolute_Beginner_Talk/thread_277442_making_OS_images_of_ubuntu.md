---
title: "making OS images of ubuntu"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by amdwilliam1985 on 2006-10-14
Hello, I started using ubuntu not long ago on my old desktop.  Yesterday I also put ubuntu on my laptop.  The problem is that my laptop doesn't have any softwares I installed on my desktop.  What I'm asking is that is there anyway to make an image of my desktop and then put it on my laptop so they have the same softwares.
thanks in advance.

---

### Post by Haegin on 2006-10-14
Try adding the laptop hdd into your main pc (you will need a converter from laptop 2.5" to 3.5" drives)  then use something like gparted or pq magic to copy the partition over?

---

### Post by Qrk on 2006-10-14
Ubuntu keeps a copy of all the deb packages you have installed (via apt-get, synaptic, add/remove applications, alien or downloaded) in  the folder /var/cache/apt/archives

The easiest way to install all of the applications you used to have is to copy this folder onto your laptop (say to your home folder) and:

```
cd ~/archives/
sudo dpkg -i *.deb

```

---

### Post by amdwilliam1985 on 2006-10-14
thx for the quick replys.  I think I'm going to stay away from hardware modifications, I'm not too good with laptop components.  I'm going to try to Qrk's methods once I have power at my house.  I'm from Buffalo NY area, right now we're still out of electricity at home.  I'm at my school now if you care.

---

### Post by Haegin on 2006-10-14
Actually dpkg has a set-selections and a get-selections option that uses a text file. You could use ```
dpkg --get-selections > /path/to/text/file
``` to save the selections from the installed machine to a text file then do a blank install and use ```
sudo dpkg --set-selections < path/to/text/file
``` on the new machine if you copied the text file accross. I would imagine this would be cleaner than copying the whole of /var/cache/apt/archives over.

---

