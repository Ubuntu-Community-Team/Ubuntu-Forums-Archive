---
title: "bootsplash screen"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-15
I recently downloaded fingerprint-bs from kde-look.org

---

### Post by sameer.india on 2008-04-15
How do I install it

---

### Post by stchman on 2008-04-15
> **sameer.india said:**
> I recently downloaded fingerprint-bs from kde-look.org

You can use StartUpManger to change your boot up screen.

Gutsy:
```
sudo apt-get install startupmanager
```

Feisty or earlier:
[http://www.stchman.com/tools/startupmanager_1.9.10-1_all.deb](http://www.stchman.com/tools/startupmanager_1.9.10-1_all.deb)

You will need to download .so files for boot splash.

To change the splash screen after you logon
```
sudo apt-get install uslpash
```

There are more usplash graphics in /usr/share/pixmaps/splash

Of course [www.gnome-look.org](www.gnome-look.org) is a great place to get Gnome themes.

---

### Post by sameer.india on 2008-04-15
This is not a *.so file.
thats what usplash is about

---

### Post by stchman on 2008-04-15
> **sameer.india said:**
> This is not a *.so file.
thats what usplash is about

The .so file is probably in the archive (.tar.gz) you have.

Usplash is the graphic you see when you are logging in.

---

### Post by sameer.india on 2008-04-15
there's no .so file in the archive

---

### Post by stchman on 2008-04-15
> **sameer.india said:**
> there's no .so file in the archive

What file is in the archive?

---

### Post by sameer.india on 2008-04-15
two images and a .cfg file

---

### Post by stchman on 2008-04-15
> **sameer.india said:**
> two images and a .cfg file

Give me a listing here of the archive.

---

### Post by sameer.india on 2008-04-16
Download it from this site
[http://www.kde-look.org/content/show.php/Fingerprint+Bootsplash+1024x768?content=29662](http://www.kde-look.org/content/show.php/Fingerprint+Bootsplash+1024x768?content=29662)

---

### Post by diplomat.x on 2008-04-16
Download it from here. You should get a .so file and a readme text file which will guide you.

[http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

---

### Post by sameer.india on 2008-04-16
but I am using KDE will that make a difference

---

### Post by diplomat.x on 2008-04-16
Yes, it will work on all ubuntu based distributions.

---

### Post by sameer.india on 2008-04-16
I was able to install it but a black patch appears in place of the light green one beside the hand

---

### Post by diplomat.x on 2008-04-17
Check the attachment. I have a black patch too. Its a bug actually. Havent found a soultion anywhere yet. See the comments  [http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

---

