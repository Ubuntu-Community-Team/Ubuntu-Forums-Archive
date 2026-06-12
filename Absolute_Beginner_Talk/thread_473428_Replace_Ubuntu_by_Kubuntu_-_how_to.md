---
title: "Replace Ubuntu by Kubuntu - how to?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by resander on 2007-06-14
I have installed Ubuntu as a dual-boot. It boots, but the mouse is not working. Suggestions from the forum have not helped, so I want to try Kubuntu instead.

I want to use the partitions defined for Ubuntu. Can I just go ahead and install Kubuntu on top of Ubuntu, or do I have to uninstall Ubuntu in some way first? For example undo the mechanism that allows me to choose between Ubuntu or Windows XP on bootup.

---

### Post by NeoLithium on 2007-06-14
You can install Kubuntu easily with this:
```
sudo aptitude install kubuntu-desktop
```

It'll probably take a while to download everything, but then you can log out, and select KDE on the login screen by clicking the Sessions button.

---

### Post by camarojones on 2007-06-14
> **NeoLithium said:**
> You can install Kubuntu easily with this:
```
sudo aptitude install kubuntu-desktop
```

It'll probably take a while to download everything, but then you can log out, and select KDE on the login screen by clicking the Sessions button.

Sessions is under the options button at the bottom left of teh login screen if you didnt know.

---

### Post by Stephen Howard on 2007-06-14
I think you might be misunderstanding things.  Ubuntu and Kubuntu are not separate operating systems in the way that Ubuntu and Windows are.  Rather, Ubuntu is the standard Ubuntu distro using the Gnome desktop, while Kubuntu is exactly the same distribution except it uses the KDE desktop.  

You can install kde along side gnome by using apt-get:

```
sudo apt-get install kubuntu-desktop
```

That said, having a different desktop isn't going to fix your mouse - that is a lower level problem.

---

### Post by resander on 2007-06-14
Thanks!

I now understand the difference between Ubuntu and Kubuntu..

The mouse is not working with Ubuntu, but is working when I boot up Windows XP on the same PC. There is nothing physically wrong with the mouse so I think this may be a driver problem within Ubuntu. Of course, I cannot be sure so want to completely reinstall as a last resort just to check. Hence my questions in my original post.

I assume the keyboard is working because I could enter username and password. 

Are there keyboard shortcuts for bringing up the command line and navigating to and between menubar-items and desktop icons? I tried Tab/Backtab, but they had no effect.

---

### Post by Unreal223linux on 2007-06-14
Which of those commands will allow me to have gnome and kde installed? How much hard drive space does having both of them use? 

It litterally just changes the desktop environement right? If my hardware is working in one it should work in the other just the same?

---

### Post by pardesi on 2007-06-14
use this instead
```
sudo aptitude install kde-core
```
it takes very less time and is almost the same

---

### Post by avik on 2007-06-14
> Are there keyboard shortcuts for bringing up the command line and navigating to and between menubar-items and desktop icons? I tried Tab/Backtab, but they had no effect.

To get to the main menu, use Alt-F1, then use the arrow keys and enter.  To get to an application menubar, press Alt+<Key associated with a particular menu>.  So to get to the File menu, use Alt-F, since the F in File is underlined.

> It litterally just changes the desktop environement right? If my hardware is working in one it should work in the other just the same?

Yes.

---

