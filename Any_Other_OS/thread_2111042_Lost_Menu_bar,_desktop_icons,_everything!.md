---
title: "Lost Menu bar, desktop icons, everything!"
date: 2013-01-31
forum: Any Other OS
---

### Post by TheNate on 2013-01-31
I was going to ask this on the Mint forums, but I couldn't get my account to activate.

I was using Mint 13 Cinnamon, and trying to install the Classic Mint menu. I finally figured out how to install an applet (linux noob), but then everything messed up. My menu bar disapeared, and the minimize, maximize, and close buttons on the windows disapeared. Now when I reboot there isn't anything but my wallpaper and cursor. I can't seem to open a terminal or do anything but turn the PC on and off. This is really annoying, and I'd really appreciate help on getting it usable again. I'd rather not have to do a full reinstall.

Thanks:)

---

### Post by xenopeek on 2013-02-01
Hi, I have activated your account 'thenate' on the Linux Mint forums. You should be able to log in now. If you have by now forgotten your password, you can contact me through PM or email and I'll reset your password. (I'm one of the admins there.) Apologies for the inconvenience.

You may try for your problem if you can still press alt+f2 to get the run dialog and run gnome-terminal, or press ctrl+alt+f1 to switch to the virtual console. Probably undoing the steps you took to install it should get you back a normal desktop.

---

### Post by TheNate on 2013-02-01
> **xenopeek said:**
> Hi, I have activated your account 'thenate' on the Linux Mint forums. You should be able to log in now. If you have by now forgotten your password, you can contact me through PM or email and I'll reset your password. (I'm one of the admins there.) Apologies for the inconvenience.

You may try for your problem if you can still press alt+f2 to get the run dialog and run gnome-terminal, or press ctrl+alt+f1 to switch to the virtual console. Probably undoing the steps you took to install it should get you back a normal desktop.
I can get into the desktop on recovery mode, but I have no idea how to undo anything. if someone could walk me through the steps, it would really help. and ranks for setting up my account, ill see if I can log in now:)

---

### Post by DobsonM on 2013-02-02
Maybe that applet is causing cinnamon to crash or not start, go to .local/share/cinnamon/applets and delete that applet you just installed.  Log out and log back in.  I had a similar thing happen to me and that's what I did and I was away laughing.

---

### Post by TheNate on 2013-02-02
> **DobsonM said:**
> Maybe that applet is causing cinnamon to crash or not start, go to .local/share/cinnamon/applets and delete that applet you just installed.  Log out and log back in.  I had a similar thing happen to me and that's what I did and I was away laughing.

Thank you, thank you! That worked perfect):P Everything seems to be working great, though could you tell me what this means

sni-qt/1548 WARN  12:11:21.167 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

It appeared when I booted up.

---

### Post by DobsonM on 2013-02-02
> **TheNate said:**
> Thank you, thank you! That worked perfect):P Everything seems to be working great, though could you tell me what this means

sni-qt/1548 WARN  12:11:21.167 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

It appeared when I booted up.

:D
Bizarre, maybe ask at the Mint forums, I have never seen that before. I tried googling it and nothing came up other than this forum thread.

---

### Post by Dodeca on 2013-02-02
> **TheNate said:**
> Thank you, thank you! That worked perfect):P Everything seems to be working great, though could you tell me what this means

sni-qt/1548 WARN  12:11:21.167 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

It appeared when I booted up.


try here ...  [http://blog.koppi.me/2012/01/howto-fix-sni-qt19799-warn-024248-774-void-statusnotifieritemfactoryconnecttosnw-invalid-interface-to-snw_service-error-message-on-ubuntu-11-10/](http://blog.koppi.me/2012/01/howto-fix-sni-qt19799-warn-024248-774-void-statusnotifieritemfactoryconnecttosnw-invalid-interface-to-snw_service-error-message-on-ubuntu-11-10/)

---

