---
title: "Black screen after suspend in Macbook 4.1 with Ubuntu Gnome 14.10"
date: 2015-02-04
forum: Apple Hardware Users
---

### Post by saleiro2 on 2015-02-04
Hi everybody,

I have Ubuntu Gnome 14.10 running in my Macbook 4.1 (2008) in single boot mode. Everything works fine except I can´t get the macbook to suspend (or hibernate). I have 2gb ram and a swap partition with the same size.

This is what happens:

- Close de lid and the macbook goes into suspension mode
- Open the lid, I can hear the machine starting up normaly but the screen stays black.

I know the macbook woke up from suspend mode because I can see the graphic environment in the back like you always could with screen brightness set to minimum in OSX (you know its there, but it's unusable). 

All I can do is press the power button to turn off the laptop.

Anyone can help me with this?

Thanks,

---

### Post by gerard8 on 2015-02-05
Hello,

I am using Xubuntu 14.10 in Macbook white 4.1 (2008).
Everything else works fine, screen brightness keys included, but I am having the same problem when resuming after suspend: **The screen backlight does not turn on**.
I installed Xubuntu 2 years ago (with 12.10) and I remember suspend/resume was working fine.

I have tried the advice on [this entry]("http://askubuntu.com/questions/551882/brightness-keys-not-working-and-no-obvious-interface-for-adjustment-either") and some other tips (such as resetting PRAM and SMC), but had no luck so far.

---

### Post by Sigrid_Rhling on 2015-02-05
I also experienced what I first thought was failure to resume after suspend with Lubuntu 14.04.1 on my Macbook 1,1. The screen would just stay blank and I had to press the power button to turn off the Macbook. I couldn't even figure out why the system went into suspend mode, because I had turned all of that off in Power Manager. 

Then, after reading this thread I had a closer look at the "blank" screen and found that it wasn't blank, just very dark. (Thanks for the tip, btw!) I could just make out the login box, so I entered my password and the system "resumed". The fact that the screen had locked was also irritating, because I had turned that off both in Power Manager and in Light Locker. So, I had another look at those settings and the only one that could possibly make sense was to turn Light Locker off completely. That is, not only to set Light Locker to not lock on suspend and "Automatically look the session" to "never", but where it says "Enable light-locker" the switch is now set to "off". 

And voilà, the system no longer "suspends" after 10 minutes or so and locks the screen. It does suspend when I close the lid and resumes fine when I open the lid again. 

So, try turning off Light Locker completely and let me know if that does the trick for you as well.

---

### Post by saleiro2 on 2015-02-05
No Light Locker in Ubuntu Gnome but I disabled all the locking screen option and still no luck. I think I tried all possible combinations. Been messing around with Settings and Gnome Tweak with no success. 

But I'm happy for you. :)

---

### Post by Sigrid_Rhling on 2015-02-06
Is the behavior the same if the system suspends some other way? For example, if you suspend the system by choosing suspend from the shutdown menu instead of closing the lid, does it then also not resume? Or if you set it to suspend after 5 minutes of inactivity, does that also produce the same problem?

---

### Post by saleiro2 on 2015-02-06
Yes, the exact same thing happens. No screen backlight after suspend. Running out of ideas here.

---

### Post by Sigrid_Rhling on 2015-02-07
Do the screen brightness keys work for you? I assume they work before suspending but not after resuming, but could you confirm? Also, what graphics card do you have? (I have seen a couple of posts about NVIDIA graphics card having trouble with suspend/resume.)

---

### Post by saleiro2 on 2015-02-07
Yes, the brightness keys work perfectly before suspending. They don't respond after. 

The driver is an Intel GMA X3100.

---

### Post by Sigrid_Rhling on 2015-02-08
Hrm. I don't think I can help much more. I did come across a [Xubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736") which might be of help maybe. Ignore the stuff on light locker, just try the workaround in #11. If that doesn't get you anywhere, you might try submitting a bug report. [Here]("https://wiki.ubuntu.com/DebuggingKernelSuspend") is a list on what you should include in that report.

---

### Post by saleiro2 on 2015-02-08
Thanks, I realy appreciate your help. That workaround didn't work for me. I've tried a lot of different solutions with no success. I'll keep trying. Thanks a lot.

---

### Post by arvid2000 on 2015-07-30
I just installed Ubuntu 14.04 on my Macbook 4.1 and I am experiencing the same issue.

---

### Post by b0bw on 2015-09-02
Ive been having similar issues,

 I will try to "just login" as suggested but before i do that (EDIT: this user is correct [http://ubuntuforums.org/showthread.php?t=2263908&p=13222683#post13222683](http://ubuntuforums.org/showthread.php?t=2263908&p=13222683#post13222683) about the screen just being at zero brightness)

 i may have found one source of error: 
In this post [https://help.ubuntu.com/community/MacBookAir6-2/Trusty#Finetuning_Powersave_functions](https://help.ubuntu.com/community/MacBookAir6-2/Trusty#Finetuning_Powersave_functions) there are some helpful suggestions, however 
there is also an error/inconsistency between the stated change and the actual file in question, i noted it in !!! !!! . basically the guide says tlp file contains
RESTORE_DEVICE_STATE_ON_STARTUP=1

but the tlp file in question 
([https://help.ubuntu.com/community/MacBookAir6-2/Trusty?action=AttachFile&do=view&target=tlp](https://help.ubuntu.com/community/MacBookAir6-2/Trusty?action=AttachFile&do=view&target=tlp)) 
is set to =0 and not =1 as the guide says it should be, 
and this could be causing the system to "blink the login screen" and then go dark. 
im not sure, when i tried to cp an edited =1 version of the tlp file to the /etc/default i ran into
permissions errors. so i would love some help getting that sorted out. 
ill try to "login from dark screen and see. this same error could also explain the "full brightness" and 
"full backlight" errors after logging in

---

### Post by oren2 on 2015-10-19
Latest linux kernel fix the problem, to install:
```

sudo apt-get install linux-generic-lts-vivid

```

---

