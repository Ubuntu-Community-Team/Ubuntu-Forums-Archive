---
title: "Desktop effects won't work after using unrestricted drivers."
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-07-13
** Title edit, should be " Desktop effects won't work after using RESTRICTED drivers. " **

When I first installed Ubuntu 7.04, I could access the cool desktop effects included. I loved the wobbly windows. :popcorn:

After I enabled the Restricted Drivers, I get this error when trying to access the Desktop Effects.

> The Composite extension is not available

I have an ATI x300 PCIe 16x. Once this gets working, can I download other cool effects to plug-into the effect engine? What thing is Ubuntu using for these effects? Beryl, Compiz, XGL?

BTW: Forums are a little broke, After entering a title it like searches for other topics which are simliar I think, and a Database error pops up and messes the layout up. :o

---

### Post by DSn0wMan on 2007-07-13
The ATI X300 series is best used with the OSS driver, and the OSS driver has AIGLX support so you wont need XGL. It works with beryl, compiz, and compiz-fusion.

edit: in other words you don't need the restricted driver(fglrx).

---

### Post by kavon89 on 2007-07-13
The wobbly windows are back! :D I'll take your word for it about the driver performance, I don't have time to test a 3D game right now though. 

How do I get more effects? Is there a site I can go to and download plug-ins or something?

---

### Post by sab0403 on 2007-07-13
You probably want something like Beryl or Compiz.

Look at the stickies on the top of the beginners forum...

---

### Post by kavon89 on 2007-07-13
I'm lazy to do the Compiz/Beryl stuff, I read a benchmark of my card with it and it only could do 20-40 fps... I don't want a laggy desktop.

*waits for the next version of Ubuntu for more cool effects* :popcorn:

---

### Post by DSn0wMan on 2007-07-13
There are plenty of plugins for compiz, wich is what you have running if you enabled desktop effects. You should be able to find a number of plugins if you have the universe repository enabled.I think the standard package is called compiz-plugins. In order to manage your plugins i recommend you install compiz-settings-manager.

---

