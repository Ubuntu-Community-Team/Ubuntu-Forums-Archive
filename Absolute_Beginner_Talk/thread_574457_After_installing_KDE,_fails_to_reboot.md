---
title: "After installing KDE, fails to reboot"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by sixsidepentagon on 2007-10-12
I installed KDE today, and liked it. While I was using it, and adept showed up and told me to update some files, so I did. 
I was configuring some files (mostly Compiz), and was able to ctrl+alt+backspace just fine. However, and I think this may be where the problem happened, it might have been during an adept update. But even after the update, I was still able to ctrl+alt+backspace (what is that called anyway?) just fine.
Then I shut the computer down.
When I tried to reboot, I was greeted by th kubuntu load screen. When it was finished, the screen became black for a bit then came back to the load screen, but the bar didn't move. I was able to go to another tty, and logged in there. It told me that the following:
resume: libgcrypt version: 1.2.3
resume: Could not read image
The tty worked fine though.

Is there any way to fix this? Something in the back of my mind tells me that during that adept update, there might have been something like  libgcrypt version: 1.2.3 loading. Can I start gnome or KDE from the tty? And please don't tell me I'll have to reinstall, right before Gusty comes out. I spent quite a bit of time getting Ubuntu just right, and I have a couple of important files.

Thanks for all your help!
sixside

---

### Post by benerivo on 2007-10-13
I would try to install a new login manger (the kde one) as your current one is auto-logging you on to the kde desktop. Then reboot to see if it takes you to the new login screen. From here, you can login in to Gnome, and then uninstall the kde login manager so that your system is restored to what it it used to be. To do this from the terminal prompt, login as yourself and type...```
sudo apt-get install kdm
```

---

