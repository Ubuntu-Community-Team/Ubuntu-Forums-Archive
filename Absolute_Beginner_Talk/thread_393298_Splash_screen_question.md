---
title: "Splash screen question"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by ignotus on 2007-03-25
is it possible to use a flash movie as a splash screen, and for instance have it do different things after you:
a) enter wrong login/password
b) enter correnct login/password

that would be cool...

---

### Post by louis_nichols on 2007-03-25
First, there is a difference to be made between the splash screen and the login screen. They are very different thing. The splash screen deffinitely can't be made to run a flash animation. It is very limited, because it is shown while the system is loaded, so functionalities needed to do such a thing are simply not there. This is similar to how any application takes a certain time to start, before you can really make use of its functionalities. The difference, in the case of the whole operating system, is that it takes a little longer. So the splash screen can only have an image, a status bar and maybe some scrooling text.

The login window, managed by an application called GDM, is more versatile. But not as much as you'd like. It can use different applications to render the background (rather than a more-or-less static image). The most common apps used for this are screen savers. Info on how to do that can be found [here]("http://gentoo-wiki.com/TIP_Screensaver_in_Background"). But it won't be able to behave differently in case of wrong login params. It would still be pretty cool, though. The *would* is because I tried the method and couldn't make it work. I didn't have the patience to troubleshoot, either.

---

### Post by ignotus on 2007-03-25
thanx for both the info and the link. have to check it out when I get home from work tomorrow.

:)

---

### Post by ignotus on 2007-03-26
seems it only works with Breezy 5.10

[http://http://doc.gwos.org/index.php/Screensaver_as_a_desktop_background]("http://doc.gwos.org/index.php/Screensaver_as_a_desktop_background")

---

### Post by louis_nichols on 2007-03-26
Hm... that howto says about the desktop background, not the login screen. Though I guess it is possible the same situation applies, but I don't know a way to find out or sure.

---

