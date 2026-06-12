---
title: "Default Window Manager"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-08-31
Hi!

For a while had been using kubuntu but would like to switch back to Ubuntu.
If i log out and select Gnome it allows me to log into the Gnome desktop, but even after I power down I still see the Kubuntu startup screens...
Is there a way back to the Ubuntu startup screens?

Thaks!

---

### Post by Metacarpal on 2006-08-31
I presume you mean the splash screens during intial bootup (before you login) and shutdown?

Open a Terminal (Applications > Accessories > Terminal) and type (or copy/paste):
```
sudo aptitude remove kubuntu-artwork-usplash
```
then
```
sudo aptitude update
```
and
```
sudo aptitude reinstall usplash
```

Alternately, you can go into synaptic, search for kubuntu-artwork-usplash and mark it for complete removal, then search for usplash and mark it for reinstallation.  I love the gui, but as in many cases, the command-line is much faster on this one.

---

### Post by Metacarpal on 2006-08-31
Also, if you were wanting to remove Kubuntu/KDE from your machine entirely, here's how to go to a [Gnome-only system]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by cjnkns on 2006-08-31
Thanks for you help!
I used the commands you gave me first but they didn't remove the Blue Kubuntu boot screen...
Then I copy and pasted the Gnome only info into the terminal it removed a ton of stuff but after rebott I still have the Blue Kubuntu start up after it goes through that I get the regular ubuntu user name and password screens...
That blue Kubuntu doesn't want to leave my lappy...

---

### Post by cjnkns on 2006-08-31
It seesm that when I startup the Kubuntu splash screen shows, but when I shut  down the regular Ubuntu screen shows.
This is all after I have uninstalled everything "kubuntu" supposedly.....

:confused:

---

### Post by The Mekon on 2006-08-31
This has been covered in a How To and I quote:

"NOTE: If you install the k(x)ubuntu-desktop package, there's a little bug where the splash screen (the first loading screen) gets taken over by the kubuntu one. If you want your old splash screen back, just do the following:
Paste this into a terminal:
Code:

sudo update-alternatives --config usplash-artwork.so


Choose usplash-default.so for the default brown ubuntu splash, or choose whichever one you like.

Then copy/paste this:
Code:

sudo dpkg-reconfigure linux-image-`uname -r`

and you're all set.

To change your default display manager (login window), copy/paste this if you have gnome:
Code:

sudo dpkg-reconfigure gdm

or this if you have kde:
Code:

sudo dpkg-reconfigure kdm"

It worked for me.

---

### Post by cjnkns on 2006-08-31
Thank you.. I have it working properly now.

---

