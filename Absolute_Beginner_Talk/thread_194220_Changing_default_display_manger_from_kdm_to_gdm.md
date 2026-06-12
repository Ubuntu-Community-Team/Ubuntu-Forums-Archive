---
title: "Changing default display manger from kdm to gdm"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Alienkind on 2006-06-11
Hi, I am a n00b. I accidently changed my default manager from gdm to kdm when I was installing *kubuntu-desktop* from Synaptic Package Manager.

I figured I wanted to play around with KDE and be able to run Dapper in both the GNOME and KDE desktops. Even though I don't think there is a difference in what happens "under the hood" between gdm and kdm, I still want to change go back to gdm.

Can someone please explain to me the proper procedure to change my default display manager to gdm? Also, can someone enlighten me if there are any differences between display managers other than the obvious aesthetic one? Help is appreciated.

---

### Post by Klaidas on 2006-06-11
Go to System -> Administration -> Login window
Select Ubuntu's welcome screen :)

---

### Post by Alienkind on 2006-06-11
Okay. Maybe I need to be more specific. When I boot ubuntu, the Kubuntu theme shows up while X/ubuntu is loading. I see the Kubuntu logo in place of the Ubuntu one when all the startup processes are shown on the lower half of the terminal window. Anyway to change this back to the other logo?

---

### Post by kaamos on 2006-06-11
You mean the splash that starts after grub?

I think this could work:
```
sudo apt-get remove kubuntu-artwork-usplash
sudo dpkg-reconfigure linux-image-$(uname -r)
```

OK, don't try this as while it might work, Klaidas' solution below looks much more sane. :)

---

### Post by Klaidas on 2006-06-11
Ooh, that one :) I had this problem when I installed Xubuntu.
Here's how to solve that
First, do
```
sudo update-alternatives --config usplash-artwork.so
```
Select usplash you want to use. Then, do
```
sudo dpkg-reconfigure usplash
```
That should work, it did for me :)

---

### Post by Alienkind on 2006-06-12
thank you. i got successfully managed to replace the kubuntu splash with the original ubuntu splash using one of those reconfigure commands posted by one of you guys.

---

