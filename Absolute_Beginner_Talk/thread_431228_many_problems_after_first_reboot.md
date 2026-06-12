---
title: "many problems after first reboot"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by KnowYourEnemy626 on 2007-05-02
I installed Ubuntu 7.04 two days ago. I am an experienced windows user and this is my first time running a Linux OS. I like Ubuntu alot however after my first time rebooting the system i began experiencing many problems with it. I have 3 main issues that I cant seem to solve:

1. Sound volume is extremely low

I experienced this problem from the start. Running windows, the speaker output on my laptop is I would say louder than average. In Ubuntu, with all the volume controls at maximum the speaker output is extremely low, almost to the point where it is not useful.

2. All audio programs freeze when attempting to play mp3 files.

Rhythymbox worked perfectly the first time I ran Ubuntu and played all mp3s just fine. After rebooting the system it now freezes every time attempt to play an mp3. Other audio programs seem to do the same thing.

3. Services settings window freezes

Every time i attempt to run the services settings window from  system--> administration-->services settings , the window appears but has a white space where the services should be listed. The window cannot be closed or force quit and only goes away with a reboot. Services settings worked properly during my first use of ubuntu but after the first reboot it has not functioned properly.

Help with any of these issues would be greatly appreciated. Thank you.

---

### Post by nonewmsgs on 2007-05-06
1. system - preferences sound and change which sound manager you're using.  one of those options might fix it.

2. errr.  well i would say o try to re-get the codecs.

3. tuff one.  someone greater me has to step up.

---

### Post by KnowYourEnemy626 on 2007-05-06
thanks for the suggestions

i actually solved this about 2 days ago and i forgot to post that. It turns out that the sound problem was a known issue with Toshiba laptops and Realtek sound cards. Another thread had a solution for that. The freezing Rhythymbox problem and the services settings problem mysteriously solved themselves after a few reboots. The first time they worked correctly again was of course when I was showing the problem to another Ubuntu user to get their opinion. Now everything is working great and I am able to stop using windows completely for the time being.

---

### Post by seshomaru samma on 2007-05-06
In order to kill a programme that is frozen use the application xkill
you can eaither run it from the terminal:
```
xkill
```
or make a shortcut on a panel
xkill turns your cursor into a skull and any application you click on instantly dies.

---

