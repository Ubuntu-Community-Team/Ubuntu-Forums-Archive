---
title: "headphones?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-05-21
i just installed ubuntu dapper on my system the other day. it works great, and now ive figued out how to unpack the necessary files to make my ipod's m4as etc play. however. now my headphones dont work when i plug them into the jack. they worked yesterday, when my ipod didnt, but now, when i plug them in, the sound still plays thru the internal speakers instead of the headphones.

i have a dell laptop.

any suggestions?

---

### Post by tgalati4 on 2007-05-21
Go to your Volume Mixer and in preferences, turn every channel and option on.  Look for Headphone Jack detect and turn that on.  Sometimes the switch gets turned off so the headphone jack doesn't wake up properly.

It's also possible that your headphone jack is jacked.  In that case, it may require repair to get it to function properly.

---

### Post by irishgoth8822 on 2007-05-22
i tried playing with my volume mixer/control and opening all the channels etc but the only options it has for picking up input devices is like mic etc. i figure since they stopped working when i unpacked all those gstreamers files, i probably did something or installed something that overrode something else, but i dont know enough to fix it.

the headphones themselves work, just not on the computer, if that helps any. i was using them with a cd player last night.

---

### Post by tgalati4 on 2007-05-22
What Dell laptop model?

Please post the output of:

aplay -l

and

lsmod

Finally, go back into volume mixer:

File-->Change Device

See if you have multiple devices that you can fiddle with.

Also, under Edit-->Preferences there is sometimes an "external amplifier" mode which will only put out line-level signals (too low for headphones) try turning that off.

Try shutting down, and removing the battery, then reboot.

---

