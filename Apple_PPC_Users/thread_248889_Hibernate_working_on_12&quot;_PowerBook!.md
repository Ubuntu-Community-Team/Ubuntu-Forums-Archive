---
title: "Hibernate working on 12&quot; PowerBook!"
date: 2006-09-01
forum: Apple PPC Users
---

### Post by APU on 2006-09-01
Hi!

I´m trying to get hibernate (Suspend to disk) working on a 12" PowerBook for some time now and know that quite some people are also interrested in this issue. I just want to tell that I was succesful for the first time now, although there are still several unsolved problems.

Firstly - Forget hibernation with the standard Ubuntu kernel. It just doesn´t work. I had to compile a vanilla 2.6.17.11 kernel (directly from [http://www.kernel.org](http://www.kernel.org) ) with enabled "swsup" Then I installed "hibernate" and adapted the /etc/hibernate/hibernate.conf skript. I commented out everything that has to do with suspend2 and uncommented the line UseSysfsPowerState disk.

To enable resuming you also have to adapt the /etc/yaboot.conf file. Add the following line to the section that belongs to your current (self compiled) kernel:

```
append="quiet resume=/dev/hda4"
```

On my system /dev/hda4 ist the swap partition - adapt this setting if it is different on your machine! Do not forget to update the boot settings in the OpenFimware with "sudo ybin -v" after you have edited the yaboot.conf file!

With everything prepared hibernation now works by using the "sudo hibernate" command BUT:

You have to switch to a console window (ctrl+alt+F1) and hibernate from this since it does not work when you are currently in X11

After resume the trackpad is not working correctly. It still works but it does not pay attention to any of the settings from /etc/X11/xorg.conf. It even does not let you deactivate it with "synclient" and reloading of the "appletouch" kernel module also does not help. It does work again after restarting X11 but this makes hibernation pretty poinltess because all open applications will be shut down if you do that.

Currently I am not aware of any other problems (even sound works after resuming and the time settings are correct too) but I am sure that there are some more as well as solutions for the problems I already encountered. Please try it out and post any solutions you come across! It would be really great to get the USB trackpad working again after resume and without having to restart X11 (This might not even be a problem for 12" PowerBooks older than my 1.5 GHz model since they use a ADB trackpad).

I did not yet try suspend2 because I´d rather like to use the "official" in-kernel solution if I can get it to work. But if there is no solution for the trackpad issue I might have to give this a try too. But not before some more serious testing of what I have got now!

APU

---

### Post by mert on 2006-09-02
Hey great news!  I'm gonna try it out and let you know how it goes. I have a 1.3 Ghz 12" powerbook so maybe I won't have the trackpad issue.
cheers

---

### Post by APU on 2006-09-03
Hmmm, I investigated a little bit more into the trackpad issue and have made the following observations:

* The Trackpad is still driven by the "appletouch" kernel module (naturally) ,so unloading this module deacitvates the trackpad. I was not able to unload the "evdev" module though. This should also have to do with the trackpad somehow.

* It seems that some low-level X11 functions are capturing and processing all input that comes from the trackpad and don´t pay attention to the X11 synaptics driver. The trackpad is perfectly usable to move the cursor around - even better than I have yet got it to work _with_ the synaptics driver. But it is impossible to disable tapping or to emulate 2nd and 3rd mouse button or even to use scrolling.

* Synclient, which can be used to tune the trackpad settings while in X11, has absolutely no effect. This adds to the theory that some low level X11 mouse routines are actually driving the trackpad and not the synaptics driver.

Now comes the question: Does anyone have an idea on how to reload the synaptics driver without reloading X11 completely? Or any other hint on how to correctly unload/reload some kernel modules to get everything working again after a hibernate-resume cycle?

Thank you very much!
APU

---

