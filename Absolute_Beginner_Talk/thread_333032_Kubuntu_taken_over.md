---
title: "Kubuntu taken over?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Maxcribbin on 2007-01-06
I was running ubuntu for a while, i think ive changed the visual to KDE.
How do i get it back?

The startup screen says Kubuntu... is it better?

Ubuntu seemed faster,  is GNOME a graphical user interface?

Is this a gui preference ive changed or have i installed another os?

Thanx,

Carl

---

### Post by MkfIbK7a on 2007-01-06
well after you have installed kubuntu-desktop it does show the kubuntu loading screen 
strange huh?

---

### Post by Maxcribbin on 2007-01-06
So all ive done is install a gui?

How do i change it back?

Is GNOME a better gui?


Thanx,

Carl

---

### Post by MkfIbK7a on 2007-01-06
niether is better just boot into gnome instead of kde

---

### Post by Bachstelze on 2007-01-06
Actually, when you're at the login screen, you can use the menu to choose which DE to start (GNOME or KDE). The login screen itself doesn't matter much but if you want to rever back to GNOME's, open up a termianl and do

```
sudo dpkg-reconfigure kdm
```

and choose gdm in the list.

---

### Post by Maxcribbin on 2007-01-06
Do i need to install gnome-desktop?

It doesnt give a boot option , just goes straight to KDE

Thanx

Carl

---

### Post by Maxcribbin on 2007-01-06
Excellent, Thank you!

Carl

---

### Post by aysiu on 2007-01-06
To change the splash screen back to Ubuntu, follow [these directions](http://72.14.253.104/search?q=cache:rP8KCB0xaLoJ:doc.gwos.org/index.php/Different_usplash+site:gwos.org+different+usplash&hl=en&lr=lang_en&strip=1).

Gnome is not better than KDE. KDE is not better than Gnome. They're different. You can read about some of the differences in approach here:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

As for switching between the two, there's a part of the login screen where you can select what kind of session you want (a KDE session or a Gnome session). More details here, including screenshots:
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by MkfIbK7a on 2007-01-06
yes sorry i should have clarified i meant to change your sessions at the login screen....
im running all three DEs
KDE
GNOME
XFCE4

---

### Post by Maxcribbin on 2007-01-06
Whilst ur here...

I recently had a mess with a few repos and programs. 
installed GTK Gnutella (i think)

An now my music programs wont work.
ERRORS on all tracks.

Although with the movie and media players, they play fine.

Any ideas?

Thanx.

Carl


(I'll post this as a new thread!)

---

### Post by Maxcribbin on 2007-01-07
Ive followed the instructions and changed my splash screen.

I now wish to get gnome, where do i get it from?

And also, when i had KDE + Ubuntu GUIs it didnt give me the option of which to load at login.

How do i get the option?


Thank you,

Carl.

---

### Post by zekopeko on 2007-01-07
perhaps you have automatic login enabled? when ubuntu boots it stops at the login manager and asks for my username and pass. 

there i can change the session (KDE, GNOME etc.)

---

### Post by Maxcribbin on 2007-01-07
I have to enter my user and password but i dont have the option..?

How can i get gnome?


Thanx,

Carl.

---

### Post by Duck2006 on 2007-01-07
apt-get install ubuntu-desktop

i think thats how it's done

---

### Post by bulldog on 2007-01-07
```
sudo aptitude install ubuntu-desktop
```should do it,if it's not already there after all.:D

---

### Post by Maxcribbin on 2007-01-07
So is gnome the default gui that comes with ubuntu?

Im installing gnome art so to get some new themes, desktop is a bit boring.

Thanx,

Carl

---

### Post by wesley_of_course on 2007-01-07
Wesley here ;


                  [http://ubuntuforums.org/showthread.php?t=295524](http://ubuntuforums.org/showthread.php?t=295524)



                                  :-\"

---

### Post by Duck2006 on 2007-01-07
> So is gnome the default gui that comes with ubuntu?

Yes

---

