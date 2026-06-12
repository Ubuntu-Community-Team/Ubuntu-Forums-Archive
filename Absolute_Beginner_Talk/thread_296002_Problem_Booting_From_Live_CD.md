---
title: "Problem Booting From Live CD"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by flghtmstr1 on 2006-11-09
Hi everyone,

I'm having trouble booting from the Kubuntu live CD.  My computer is an AM2 Athlon 64 X2 3800+ with an X1800XT video card.  I can boot into the first menu just fine, I can get through the loading splash screen fine (if I disable apic), but when it comes time to actually load up Ubuntu, my monitor shuts off.  If I Ctrl+Alt+F1, I can get the console, but I cannot get a GUI no matter what I try.  I have tried using both headers on my video card, as well as messing around with every boot option i could think of.  The CD is not faulty.  Thanks in advance!

---

### Post by an.echte.trilingue on 2006-11-09
You need to install the driver for you ATI Radeon X1800XT.  You can install software, even to the live CD (except that you need to repeat the process every time you boot), which is what you need to do here.

If you have internet, log into the console and type enable the non-free repository by following [these instructions]("https://help.ubuntu.com/community/Repositories/CommandLine"), then:

```
sudo apt-get install *fglrx*
```

Then configure the card with

```
sudo dpkg-reconfigure xserver-xorg
```

be prepared to answer some questions about your monitor/card, but in general the defaults are fine as long as you select the fglrx driver.  Finaly, go back to your GUI and restart the Xserver with CTRL+ALT+BACKSPACE



If you don't have internet, you can try to just reconfigure your graphics card and use very conservative input, like the vesa driver and 800x600 resolution with color depth of 8.

Good luck!

---

### Post by lptr on 2006-11-18
Having an additional problem.

I did dpkg-reconfigure xserver-xorg successfully from ALT-F1 console but 

CTRL-ALT-BACK 

does not restart X. Switching back to X (ALT-F9 if I remember correctly) does not work, too.Maybe something is wrong with keyboard layout I don't know.

Anyways: How can I restart X FROM COMMAND LINE without killing all onehundredandone processes that are bound to X by hand? ](*,) 

Thanks in advance

rob*

[update]
I fiddled around again and any combination finally brought me back to display :0. I don't know. Anyways I would highly appreciate to know how it is possible to kill X-server by hand.

---

