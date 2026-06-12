---
title: "[SOLVED] Grey Screen with Limewire (Java)"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-11-19
Hello,
I downloaded and installed Limewire (for linux, .deb) and started it up. I got through the initial setup but when the main program starts all I get is a grey window. I'm pretty sure I've had this problem when running TED (which is also java based I believe). I am running Compiz Fusion.

Thank You in advance.

---

### Post by ohjeez99 on 2007-11-25
i had a problem like this back in fiesty/edgy.  I couldnt figure it out really but what i did was turn off all desktop effects and it worked fine.  I guess give that a try?

---

### Post by jordanmthomas on 2007-11-25
Add this to your ~/.bashrc and log out and then back in and you should be able to use Java / Swing apps even with compiz running:
```
export AWT_TOOLKIT=MToolkit
```

(in case you don't know how to do that, just run this in a terminal and log out and back in)
```
echo "export AWT_TOOLKIT=MToolkit" >> ~/.bashrc
```

---

