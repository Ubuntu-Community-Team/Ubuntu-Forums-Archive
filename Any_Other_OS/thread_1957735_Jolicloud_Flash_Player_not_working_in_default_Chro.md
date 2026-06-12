---
title: "Jolicloud Flash Player not working in default Chromium...?"
date: 2012-04-13
forum: Any Other OS
---

### Post by VpNKBQLjz0 on 2012-04-13
So I'm using Jolicloud. So far it's amazing.

Just 1 issue... flash player isn't working..

I've tried downloading it from the Adobe website and then moving the flashplayer.so file into the plugins directory.

I have also tried reinstalling flash as was posted here:

[http://help.jolicloud.com/entries/316531-i-have-an-issue-with-flash-on-joli-os](http://help.jolicloud.com/entries/316531-i-have-an-issue-with-flash-on-joli-os)

So after trying methods 1 and 2, the 3rd one states that I should post on the ubuntu forums and ask for help in getting this to work..

Whenever I try to load a flash applet I just get the error: "Plugin Missing"

The version of Joli OS installed: Jolicloud 1.2
The brand of your device: ASUS
The model of your device: A2500D (A2D)
The feature affected (of course, Flash here): Flashplayer
The error message you get (if applicable): "Plugin Missing"
A detailed description of your issue: As written above.

Does anyone, or has anyone been able to get flash player working? I can't seem to get it working at all no matter what I do. I've tried terminal commands, compiling myself and doing everything.

A quick 'chrome:plugins' into the address bar says that Flash is/was already installed, so why does it not work when I try to load an applet?

Thanks for any and all help in advance!

---

### Post by Perfect Storm on 2012-04-13
Moved to Other OS/Distro Talk.

---

### Post by lovinglinux on 2012-04-13
Did you get the correct plugin architecture according to your browser? If you are using a 64bit browser, you need to get a 64bit plugin, otherwise it won't be detected.

If you are experiencing issues with the deb file, get the tar.gz file from Adobe, extract it and place it under ~/.mozilla/plugins in your home directory.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by ojdon on 2012-04-13
Try using this command:

```
sudo apt-get install ubuntu-restricted-extras
```

If that works then it should install flash into Chromium.

---

