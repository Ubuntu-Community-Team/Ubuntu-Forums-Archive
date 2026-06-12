---
title: "G74SX Function Keys + Backlight"
date: 2011-08-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ds_k7 on 2011-08-30
Hello! I'm afraid to say this, but I'm pretty damn new to Linux. I've used a few other versions here and there in the past, but by no means am I a "power user", so to speak.

I just got a brand new G74SX, and I partitioned the HDD and installed Ubuntu 11.04. (I have used Ubuntu in the past, but it has been almost two years since I've touched any form of Linux. I believe the last version I used was 9.04, "Jaunty Jackalope").

I understand the G74SX is new, so there may not be much community support for it right now, but I'd like to kickstart this if I can. The three main issues which need to be tackled (I think) are:

[INDENT]1: The keyboard backlights are not working

2: The Function keys (fn+f1-f12, i.e. Screen Brightness, Mute, Volume, Backlight brightness) do not work *(I have attempted to fix this myself...from what I could gather, the kernel doesn't register the "fn" key event. I don't know where to proceed from here.)*

3: USB 3.0 support (I saw there was another thread for this, so I'm leaving it out of here)[/INDENT]


Would anyone have any idea as to where the heck I can even begin?



**Additional information**

I attempted to follow the [Hotkeys/Troubleshooting]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting") section of the wiki, which led me to the text file stored at /usr/share/doc/udev/README.keymap.txt

In that file, it instructs me to type ```
sudo /lib/udev/keymap -i input/event3
``` into the terminal in order to test the functionality of various keys. This works, except for the fact that the Fn key does not register at all! I would assume that my starting point should be to get Linux to recognize this key. Any ideas on where to begin?

---

### Post by Decessus0 on 2011-08-31
I have the same laptop, as well as the same issues you are talking about. I have been attempting to create a driver for the function keys, but no matter what I do or what I try, I can not get the function key nor the calculator key to register the keypress. I don't understand why I can not seem to get these keys to function. The backlight functions all the way up until grub loads, and then all functions cease until Windows is loaded.

I will keep you posted if I find a solution in getting them to register, but for now, we are all in the same boat.

---

### Post by telamohn on 2011-09-02
Got the same laptop, same problems.
Those keys do not work in windows either until you install asus ATK keyboard driver/filter.
You can find it [here]("http://www.asus.com/Notebooks/Gaming_Powerhouse/G74SX/#download") but no downloads for linux sadly..

By incident I discovered that the dim backlight keys worked when you're in console mode (press alt+ctrl+f1 and alt+f7 to get back)

---

### Post by vikrant82 on 2011-12-28
I used this to fix my sleep / hibernate - [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Interestingly, once laptop sleeps, and wake from sleep, the keyboard light comes up.

Function keys, were working a while back, but they are broken again now, may be since I upgraded to oneiric.

---

