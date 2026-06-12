---
title: "Changing, Boot,LogOn, and loading Screen"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-31
Thanks guys for all the Great help you have provided me with this Wonder Ubuntu Linux
experience !!!!! 

I have a question that I know a lot of you probably know. As I see many of the Ubuntu
Screen shots, I see very customized Ubuntu's.  I have a very nice Desktop that I have
setup but would like to change the Boot, LogOn, and Loading Screen to match.
Is this very hard and can I do it without Beryl and Compiz?  I'm using a Virtual
Machine so I'm limited in what I can do. I tried running Beryl and Emerald but I am guessing
that Virtual Box doesn't support 3D.The Orange Screens that load up before
I reach my Desktop seems a little out of place with the dark ambient look I have
Chosen.   Here is a shot of my Desktop. I'd say this isn't to bad for only
using Linux for 2 weeks.... I'm very happy and thinking of switching from Windows.

[IMG]http://img214.imageshack.us/img214/7347/cityshotby3.jpg[/IMG]

---

### Post by Steve1961 on 2007-08-31
By boot do you mean the usplash screen that shows whilst ubuntu is loading?  If so this link is a good starter:

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

The logon screen is the gdm login which you can change in system>administration>loginwindow

The gdm splash can be changed if you install gnome-splashscreen-manager

You can find lots of themes at [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by Orbital75 on 2007-08-31
Thanks for the infomation....

Yes, I mean the part of Ubuntu that show the Progress bar while loading up.
it's the 1st screen you see. 

can I get  gnome-splashscreen-manager from Apt-Get?

---

### Post by Steve1961 on 2007-08-31
> **Orbital75 said:**
> Thanks for the infomation....

Yes, I mean the part of Ubuntu that show the Progress bar while loading up.
it's the 1st screen you see. 

can I get  gnome-splashscreen-manager from Apt-Get?

yes, just apt-get it.

---

### Post by BobCFC on 2007-08-31
Then gnome-splashscreen-manager is for changing the logo that pops up after you log-in while your desktop is booting 'nautilus etc'.  This is easy to change because it is just a picture you can download from gnome-look.org


The Ubuntu logo that is on a fullscreen black background with the progress bar that you first see is the USPLASH.. and it is slightly more tricky to install because it is compressed into the boot process.  There are programs to install usplash as well.

You can also get these form gnome-look.org but be aware of the difference between gnome splash and usplash.

---

### Post by sunzaru on 2008-02-02
so... example.

i installed ubuntu, then kubuntu desktop thingy.  Now my boot and shutdown screens are that of kubuntu instead of the ubuntu screens.  I want it back to ubuntu.

I saw an article to do the following to run the manager
```
sudo update-alternatives --config usplash-artwork.so
```

But that only updates the shutdown screen.  How do i change the boot screen also?

---

### Post by Liet_Kynes on 2008-02-03
type the following in a term to get back the startup ubuntu screen

sudo update-initramfs

That should do it.

---

