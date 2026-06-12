---
title: "tv tuner"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by steve789 on 2006-05-14
anybody knows a good tv tuner program other then tvtime and zapping tv 
because i had try both of them and  zapping tv crashes every 10 min and tvtime dosent have as many options as zapping tv
any ideas ](*,)

---

### Post by dlai on 2006-05-14
what kind of tv card are you using? ivtv or v4l?

---

### Post by Bagnaj97 on 2006-05-14
I use kdetv and I think it's great. It's easy to use and has teletext support as well as tv.

---

### Post by sophtpaw on 2006-05-14
[QUOTE=steve789]anybody knows a good tv tuner program other then tvtime and zapping tv 
because i had try both of them and  zapping tv crashes every 10 min and tvtime dosent have as many options as zapping tv
any ideas ](*,)[/QUOTE]

I've ordered AVerTV DVB-T USB 2.0 from Avermedia     [http://www.averm.co.uk/avermedia/aver/products_digitvtuner_dvbtusb2.asp?show=2]("http://www.averm.co.uk/avermedia/aver/products_digitvtuner_dvbtusb2.asp?show=2")

It is usb but i was told it will configure in Ubuntu and there are instructions on the site.

There is also WinFast TV2000 XP Expert which is internal pci card

It would be nice if there was a list somewhere of all the ones that definitely work in Ubuntu. What i found frustrating shopping around the shops is that all the boxes recommend Windows XP etc as usual

good luck

sophtpaw

---

### Post by steve789 on 2006-05-14
I guest im going to try  kdetv ill see if it works

---

### Post by steve789 on 2006-05-14
ok i dont get this  
how do I do this 

(no extra download required)
Add the following to your /etc/apt/sources.list:
deb [http://bonca.hu/~rizsanyi/debian](http://bonca.hu/~rizsanyi/debian) sarge/
deb-src [http://bonca.hu/~rizsanyi/debian](http://bonca.hu/~rizsanyi/debian) sarge/
Update your package index and install the kdetv package:
apt-get update
apt-get install kdetv

---

### Post by Christmas on 2006-05-14
You have to add the necessary repositories for kdetv. Those are for Debian and probably you'll have dependency problems. I remember kdetv was in Ubuntu's repositories, just add the multiverse section. You can add them from Synaptic or editing your sources.list using in a terminal:
```
sudo nano /etc/apt/sources.list
```
Then enter your user password (the one that you entered when you installed Ubuntu) and edit your file.
You have to update your repositories after that:
```
sudo apt-get update
```
and after that install kdetv:
```
sudo apt-get install kdetv
```

---

### Post by sophtpaw on 2006-05-15
[QUOTE=Bagnaj97]I use kdetv and I think it's great. It's easy to use and has teletext support as well as tv.[/QUOTE]

Is this software dependent on any hardware? 
and is there a version for gnome? presumably kdetv doesn't work i gnome

thanks

sophtpaw

---

