---
title: "switch from x64 to x32"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by xsnslaine on 2007-01-23
I have installed x64 onto my machine, i have since realised that it wasnt a good move, with incompatabilities everywhere with some of my 'need' applications.

is there an easy way to switch from the 64bit installation to 32bit without starting all over again?

Many thanks

---

### Post by mikewhatever on 2007-01-23
I doubt it, since 64/32 bits are different OSs. You might also want to ask in 64 bits forum [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by xpod on 2007-01-23
Prossibly,although i really dont have a clue for sure.

Starting afresh though would surely be your best option.
I dont know how much you`ve done to your system but a complete re-install only takes about an hour.And thats with all the personal preferences....it actually only takes 20 minutes to re-install on this old thing:D 

Of course all pc`s are different but it sounds like what you want to do could well cost you much more time in the long run....if it`s at all possible that is?

Somebody who actually knows will tell you for sure.....i`m sure:D 
Good luck

EDIT:change that to "probably not" then.lol

---

### Post by xsnslaine on 2007-01-24
Thanks for the replies, I think i will start again if that is the case, im very keen to make the switch from windows to ubuntu, i spent a good couple of weeks on ubuntu and really liked what a saw.

I have spent alot of time trying to get the apps i require (skype, flash etc) working how i want them to work but to no avail.  Moving to 32bit i think will be the best option for me as i am only starting out with ubuntu.  although problems are the best way to learn. :)

---

### Post by lamego on 2007-01-24
Please make sure you have /home on a different partition, that makes system reinstall much easier.

---

### Post by jvc26 on 2007-01-24
You will have to install the 32bit wiping the 64bit off. It is a good idea when you repartition to have the /home partition on a different partition rather than the same as the filesystem. That way when you reinstall you can do so much faster as all your files are already in the /home partition.
Il

---

### Post by xsnslaine on 2007-01-30
When installing anf formatting my unix partition (not my home) what will happen with the boot dialog?  will that automatically know that i have removed one version of ubuntu and installed another?

I just want to make sure that i know everything i need to before i start the replacement.

---

### Post by Jussi Kukkonen on 2007-01-30
To answer your original question: when apt was designed no-one thought that an architecture could natively run binaries form another architecture -- so "upgrading architectures" was never added as a feature. I am sure that it will be added at some point. Don't hold your breath though.

> 
When installing anf formatting my unix partition (not my home) what will happen with the boot dialog? will that automatically know that i have removed one version of ubuntu and installed another?
I assume you mean the Grub selection screen? grub is normally installed on root partition so it will be removed when you format and a new one will be installed...

---

### Post by xsnslaine on 2007-01-30
> **Jussi Kukkonen said:**
> To answer your original question: when apt was designed no-one thought that an architecture could natively run binaries form another architecture -- so "upgrading architectures" was never added as a feature. I am sure that it will be added at some point. Don't hold your breath though.

I assume you mean the Grub selection screen? grub is normally installed on root partition so it will be removed when you format and a new one will be installed...

Many thanks to the confirmation about the architecture change question,  I knew it was a long shot when i first asked the question.

I was on about the Grub selection screen,  Glad i dont have to do any fiddleing with that, just a simple clear and reinstall then.

Thank you to all that helped,  Ubuntu has the best and most useful community i have seen anywhere, this is one of the main reasons i am attracted to the OS.

---

