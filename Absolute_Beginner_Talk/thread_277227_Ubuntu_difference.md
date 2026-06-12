---
title: "Ubuntu difference"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Evergrey on 2006-10-14
Hello everyone this is my first thread/post. I'm new to Ubuntu and new to Linux as well. I'm reading a lot but still don't understand some basics.
Like difference between some versions of Ubuntu.. Kubuntu and so on. Is it only different GUI or there is more?
And what is difference between CD and DVD versions? :-k

---

### Post by taurus on 2006-10-14
Ubuntu uses Gnome.
Kubuntu uses KDE.
Xubuntu uses XFce4.

Otherwise, the under layer is exactly the same, depending on what window manager you want to use.  However, you can have all three install on your system if you wish and at the login screen, you just pick whichever window manager you want to run for that session.  If you're not sure which one you want, play with all three and decide it yourself.

---

### Post by PriceChild on 2006-10-14
You're right, ubuntu has a standard base, upon which a desktop manager and associated packages are installed. ubuntu contains Gnome, wheras kubuntu includes KDE and xubuntu has xfce.

As a beginner i reccomend you stick to ubuntu/KDE unless you need a light system upon which you should install xfce.

A good comparison between gnome and KDE: [http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)


I'm not sure as to the difference between CD and DVD, i think it is just that the DVD contains both the desktop and alternate discs in one.

---

### Post by Sef on 2006-10-14
Gnome and KDE are really for computers with at least 256 mb of ram.  

XFCE is for computers with less than 256 mb of ram.

As for which is better that is up to you.  If you are just starting, Gnome is better because most people here use it and thus you can more people who could know an answer to your questions.

---

### Post by Evergrey on 2006-10-14
I already tried out Ubuntu Live 5.04 (I have install disc too)

What is better option by your opinion?
- Download complete 6.06 or upgrade 5.04 if possible?
- DVD version also contains Live disc or not?

@Sef I believe 2gb of ram is more than enough :)

Right now I'm running Windows XP Proffesional, and want to make dual boot... Is it better to use Partition Magic to create one more Partition for Ubuntu or use Ubuntu disk partitioner?

---

### Post by PriceChild on 2006-10-14
I would use Partition magic... i always find the live cd partitioner a tad unstable.

I would DEFINATELY download the complete 6.06 cd. It'll be a much smaller download to what you're proposing.

---

### Post by Evergrey on 2006-10-14
> **taurus said:**
> Ubuntu uses Gnome.
Kubuntu uses KDE.
Xubuntu uses XFce4.

Otherwise, the under layer is exactly the same, depending on what window manager you want to use.  However, you can have all three install on your system if you wish and at the login screen, you just pick whichever window manager you want to run for that session.  If you're not sure which one you want, play with all three and decide it yourself.

Okay, I will install Ubuntu 6.06 later, then I need to download some packet to be able to choose window manager at login screen?
If so where can I find it?

Thanks for all replies btw.

---

### Post by taurus on 2006-10-14
If you use the desktop CD (LiveCD), it comes with everything that you need to run Gnome.  And if you want to have a look at KDE or Xfce4, then open a terminal, Applications -> Accessories -> Terminal, and run

```

sudo aptitude update
sudo aptitude install kubuntu-desktop (for KDE)
sudo aptitude install xubuntu-desktop (for XFce4)

```
Then, either log out or reboot and at the login screen, you can pick whichever window manager you want to use from the Options (bottom left corner).

That's all there is to it.  ;)

---

### Post by Evergrey on 2006-10-14
Ooops, when I go to download page (Desktop CD) I get 3 types of images: 
I am not mac user so I will skip that one.

1. PC (Intel x86) desktop CD

For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.

2. 64-bit PC (AMD64) desktop CD

For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.


I'm currenty running Windows XP Proffesional on AMD Athlon64 3500+
What image is better for me? :-k

---

### Post by taurus on 2006-10-14
Do you want to run 64bit Ubuntu or do you want to run the 32bit version?  I recommand you download the PC desktop CD (x86) then...

---

### Post by Dirty Ole on 2006-10-14
> **Evergrey said:**
> Ooops, when I go to download page (Desktop CD) I get 3 types of images: 
I am not mac user so I will skip that one.

1. PC (Intel x86) desktop CD

For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.

2. 64-bit PC (AMD64) desktop CD

For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.


I'm currenty running Windows XP Proffesional on AMD Athlon64 3500+
What image is better for me? :-k

I would suggest you go for x86 version because as far as I know 64bit version has issues like XP 64bit has ie driver/codec issues.

---

