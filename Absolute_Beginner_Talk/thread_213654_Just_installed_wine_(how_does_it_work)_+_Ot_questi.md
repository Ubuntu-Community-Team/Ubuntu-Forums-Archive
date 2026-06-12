---
title: "Just installed wine (how does it work?) + Ot question"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-11
I just installed wine through the synaptic system manager. So to see if it worked, I tried downloading dvd shrink. But when pressing on the .exe file from the desktop I get this error: Could not show
/home/"my name"/Desktop/dvdshrink32setup.exe".
Whats wrong here..

Now to my OT question. Do you think it would be an advantage to use the english distro of Ubuntu instead of ur native language when using Ubuntu and being a noobie. It seems quite stupid having to translate everything everytime. Like my errormessages. Who knows if I translated wrong.
So what do you think?

Thanks.

---

### Post by SonicChao on 2006-07-11
> **jincast90 said:**
> I just installed wine through the synaptic system manager. So to see if it worked, I tried downloading dvd shrink. But when pressing on the .exe file from the desktop I get this error: Could not show
/home/"my name"/Desktop/dvdshrink32setup.exe".
Whats wrong here..

Now to my OT question. Do you think it would be an advantage to use the english distro of Ubuntu instead of ur native language when using Ubuntu and being a noobie. It seems quite stupid having to translate everything everytime. Like my errormessages. Who knows if I translated wrong.
So what do you think?

Thanks.
First, do this:

1) 'cd' to you're directory...in this case you would

```

cd /home/<yourname>/Desktop/dvdshrink32.exe

```

Then,

```

wine dvdshrink32.exe

```

If that doesn't work, it isn't compatible with Wine.

Hope this helps,
SC

---

### Post by DavidFL on 2006-07-11
Hello.  To expand on the other reply, if what was suggested does not work it meas either 1. It will not work until possibly newer WINE versions or 2. you will have to do some tinkering. :) (Don't worry it gets easier in time)

Have you seen the Wine Application Database which often has tips and experiences regardign getting an application to work with wine?  I looked it up for you and I found this: [http://appdb.winehq.org/appview.php?iVersionId=2230](http://appdb.winehq.org/appview.php?iVersionId=2230) apparently one person at least says they were able to get one version working reasonably well.  I hope this helps you some.

---

### Post by ekarni on 2006-07-11
Let me expand on SonicChao's answer:

Wine is like an extra layer that lets Windows programs run on a Linux system by translating things back and forth.  If you want to run a Windows program on Ubuntu, you need to tell Ubuntu to run it through Wine.

To follow SonicChao's directions, you need to open up a command line.  From the Applications menu, select Accssories -> terminal, then type what he/she posted.

Regarding your English/native language question, I suppose it mostly depends on how comfortable you are with English.  As you said, it will be helpful to have the "usual" English error messages to read when you have trouble, but that's about it.  We on the forums can usually help even if your translation is far from perfect.  If having to translate English boxes every time they pop up is inconvenient for you, then definately run native language.

---

### Post by jincast90 on 2006-07-12
Thanks all! 

Ill give it a try.

---

