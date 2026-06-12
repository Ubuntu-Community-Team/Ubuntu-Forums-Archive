---
title: "Black screen"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by peaceforall on 2007-11-03
I installed Gutsy on dual boot machine.  After I input my login and password from brown screen my screen goes black, no keys work, and only my mouse works.  Can you help?

---

### Post by overdrank on 2007-11-03
> **peaceforall said:**
> I installed Gutsy on dual boot machine.  After I input my login and password from brown screen my screen goes black, no keys work, and only my mouse works.  Can you help?

Hi, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by peaceforall on 2007-11-03
Thank you.  Did what you said.  Now I have blank brown screen with no key functionality and only the mouse works?

---

### Post by overdrank on 2007-11-03
> **peaceforall said:**
> Thank you.  Did what you said.  Now I have blank brown screen with no key functionality and only the mouse works?

Ok :oops: lets try that again but lets use ```
sudo dpkg-reconfigure xserver-xorg
``` and choose vesa as the driver and on the rest of the questions if you don't know the answer then leave as the default answer given. Then when finished use the reboot again [-o<

---

### Post by peaceforall on 2007-11-03
Did what you said.  Running on MSI K9AGM2 motherboard with onboard ATI.  Got the question screens and loaded generic ati driver.  Rebooted, was running in low-res mode.  Logged in and got blank brown screen with only mouse functionality.

---

### Post by peaceforall on 2007-11-03
Can anyone help with this?

I can get to the command line before I log in, however I get a brown blank screen when I boot up.

---

### Post by beanco on 2007-11-04
i am in the smae boat as peaceforall.

except i am on feisty.

robi

---

### Post by peaceforall on 2007-11-04
Beanco,  Thanks for the note.  I'm hoping one of the UBU Wizards can help us out.  Until then I'm UBULESS.

---

### Post by beanco on 2007-11-04
yeah is is bad being UBELESS.

my wife has her work laptop at home and it has win2000 on it.

it works, it is stable, etc. but it is not Ubuntu!

I wnat to get my Ubuntu back!

robi

---

### Post by P4man on 2007-11-04
If you press control + alt + F2, can you get to the console ?

---

### Post by beanco on 2007-11-04
> **P4man said:**
> If you press control + alt + F2, can you get to the console ?

I get a console using ctrl alt F1!


robi

---

### Post by peaceforall on 2007-11-04
Yes. I can get to terminal.

---

### Post by peaceforall on 2007-11-04
I can get to console/terminal.  Now what do I do to get UBU going?

---

### Post by beanco on 2007-11-05
peaceforall.

hope somebody can help us. I will need my computer tonight to work.

Robi

---

### Post by P4man on 2007-11-05
Perhaps you can try this:
At the console, type

```

cd  /etc/X11/
sudo cp xorg.cong xorg.bak

```

(makes a backup of the file) then:

```
sudo nano -w /etc/X11/xorg.conf
```

You will get a text editor to modify the settings file for X (graphical interface).
Locate the "section device" of your video card, and change the driver line. Mine looks like this:
> 
Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nvidia"
        Busid           "PCI:3:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Change into this:
> 
Section "Device"
        Identifier      "(whatever video card you have)"
        Driver          [COLOR="Red"]"vesa"[/COLOR]
EndSection

press control+x to exit, confirm saving by pressing Y. Now try restarting X again:

> sudo /etc/init.d/gdm restart

(you may have to press control+alt+F7 to go to the X session again, not sure).

If that doesnt help, post your xorg.conf file here.

---

### Post by antiemptyv on 2007-12-26
i was having a similar issue.  try reinstalling gdm:

```
sudo aptitude reinstall gdm
```

...then logout and log back in.

hope that does it!

---

