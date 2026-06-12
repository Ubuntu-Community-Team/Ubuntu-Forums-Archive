---
title: "The ubuntu progress bar after grub menu"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by arashcuzi on 2007-10-12
Okay, I've looked on site after site for something that makes sense to me (obviously with no apparent answer found).   I'm a linux uber-n00b, so I may not even be searching the right keywords, and I'm also a tad too used to the way windows works.

For example, in win XP, you can change that boot screen between the POST/manufacturer splash and the actual login screen by simply replacing it.  However, I've looked at usplash, which only changes the splash AFTER you log in where it shows you that nautilus etc. is being loaded and I've looked at grub splashes where it simply puts a nice picture behind the menu when you're selecting whether to boot your normal kernel or a recovery kernel (or in my case winXP), now, I know there is a screen in between those, because it's got the ubuntu logo and text with a progress bar showing the progress of the system in the background loading to memory and from hdd etc.  How do I change that?  So far the only thing I've been able to do is install KDE which changes it to a nice little kubuntu logo with progress bar then login choosing gnome session (cause I feel more comfortable with gde).  So, my question is, what is that screen called between the grub and ubuntu splashes called, and does anyone know a forum, site, gnome-look or other art/eye-candy page with a walk-thru on changing them and maybe a collection of premade screens?

---

### Post by Beggar on 2007-10-12
Are you referring to usplash? Thats what it sounds like, Im no expert on customizing it, but I swear I remember seeing a package in the repos which allowed you to do that.

---

### Post by arashcuzi on 2007-10-12
well, it's not usplash, because usplash doesn't load until x starts and gdm is running, the screen I'm talking about is before the login window

i've already changed the usplash theme, and it's just changes the window after you login while it's setting up your desktop environment

the ubuntu screen with the progress bar that loads over the verbose when the kernel and mounts, etc load is the one i want to change...i can't seem to find anyplace that talks about that...

usplash didn't change it, and the grub splash only put a picture behind the menu where you select which kernel version to load, and as soon as you select it, it disappears and ubuntu boot screen is shown, then login, then usplash...

unless i misconfigured something, I can't seem to change the ubuntu boot screen...

help...if it's even possible

---

### Post by Tomosaur on 2007-10-12
> **arashcuzi said:**
> well, it's not usplash, because usplash doesn't load until x starts and gdm is running, the screen I'm talking about is before the login window

i've already changed the usplash theme, and it's just changes the window after you login while it's setting up your desktop environment

the ubuntu screen with the progress bar that loads over the verbose when the kernel and mounts, etc load is the one i want to change...i can't seem to find anyplace that talks about that...

usplash didn't change it, and the grub splash only put a picture behind the menu where you select which kernel version to load, and as soon as you select it, it disappears and ubuntu boot screen is shown, then login, then usplash...

unless i misconfigured something, I can't seem to change the ubuntu boot screen...

help...if it's even possible

Actually, that IS usplash. The splash screen after you log in is just called...well, the 'splash screen'.

Usplash is what happens between grub, and the login manager loading. You can change it using the 'usplash-switcher' package. This package only works if the usplash is already installed (installation instructions should come with the usplash you download from some website)

If you want to make your OWN USplash image, look here:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

You can find other usplash themes here:
[http://www.gnome-look.org](http://www.gnome-look.org)

Unfortunately they're just bundled in with all of the other types of splash screen, so you'll need to do a search or just sift through the pile.

---

