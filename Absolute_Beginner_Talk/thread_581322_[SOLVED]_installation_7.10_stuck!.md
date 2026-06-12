---
title: "[SOLVED] installation 7.10 stuck!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-10-19
the ubuntu 7.10 installation is stuck at 82%. Grub is not written...so unable to dual boot also :(. Kindly help! Screenshot attached! dono what to do!

---

### Post by Qwerty_ on 2007-10-19
Unplug your ethernet if it is connect. Since it is trying to scan the repos, I had a similar problem.

---

### Post by _simon_ on 2007-10-19
How long has it been stuck for?

---

### Post by Dr Small on 2007-10-19
It is scanning the mirror, and since the servers are loaded, it will take forever. Try disconnecting your internet.

Dr Small

---

### Post by badguyanil on 2007-10-19
Ok disconnecting the internet did the trick! Thanks for the help!
Now another problem.After i choose the ubuntu from the boot menu...the screen stays blank and screen setting LED's continously blink.this happened when i had choosen a higher resolution in windows earlier.  Gusty does not recognise my default resolution of 1024X768. it boots to a higher resolution even from the live cd! Kindly help!

---

### Post by Qwerty_ on 2007-10-19
I assume that you are able to get to a terminal of Gutsy?

If so you need to manually edit your xorg with the following command

```
sudo dpkg-reconfigure xserver-xorg 
```

That should do the trick.

---

### Post by badguyanil on 2007-10-19
cant reach to the terminal too! as soon as i select the ubuntu --generic option all i can see is loading and boom! the screen leds start blinking. Can bootusing the recovery mode though. and giving start x from the prompt! help!

---

### Post by Qwerty_ on 2007-10-19
Perhaps you can try that command from within the recovery mode though I am not sure.

---

### Post by badguyanil on 2007-10-19
yeh tried that.. and it did work. Ubuntu starts at recovery mode good...well i set it at 800X600. But as soon as i select the generic version it gives that weired blinking stuff again :(. i never had a problem with 7.04! i feel ppl have more problems with 7.10 than 7.04! i just feel that though. Thanks for the help Qwerty_  ! but still am no where close to solving the "Blinking LED's" problem :D ....

---

### Post by Qwerty_ on 2007-10-19
Ive got a new idea for you.

Once you have booted into the recovery mode.

Go to System>Administration>Restricted Drivers Manager.

And see if you can install something for your graphics card there.

---

### Post by white on 2007-10-19
I too thought it was stuck, but I waited for about 15 minutes and eventually it cleared. The servers are heavily loaded so it might take a bit.

---

### Post by badguyanil on 2007-10-19
> **white said:**
> I too thought it was stuck, but I waited for about 15 minutes and eventually it cleared. The servers are heavily loaded so it might take a bit.

that problems solved!!! check the posts... neways thanks for the advice.

---

### Post by badguyanil on 2007-10-19
> **Qwerty_ said:**
> Ive got a new idea for you.

Once you have booted into the recovery mode.

Go to System>Administration>Restricted Drivers Manager.

And see if you can install something for your graphics card there.

this doesnt seems to work...anybody else with any idea why this is happening. 7.04 was perfect installation! and i am sure this is with the screen resolution!. neways i can specify ubuntu what to use my screen resolution as during the setup! other distro's give the option of selecting the resolution!!! :confused: these problems can be easily avoided by that option!

---

### Post by badguyanil on 2007-10-19
ok guys found the problem but not the solution!

The problem is with resolution as described above. When i boot the boot screen with the scroll bar does not appear. It just gives me a blank screen (which is complained in some other thread also) and coz the resolution of the boot screen is higher than supported the LED's keep blinking. After a few secs though it shows up the fschk command line screen where it checks for the harddisk for errors. from then on it is the ubuntu i have always known. although had to dig up a lil to find this thread and fix the resolution problem 
> [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

the same thing happens while shutdown too! i mean just get a blinking LED's screen and till the CPU shuts down and i know the computer can be switched off..

so the next problem to be solved is how do i get the booting screen with the pretty orange scroll bar!
any ideas!!!!!!!!!!!

---

### Post by por100pre1 on 2007-10-19
> **badguyanil said:**
> the ubuntu 7.10 installation is stuck at 82%. Grub is not written...so unable to dual boot also :(. Kindly help! Screenshot attached! dono what to do!

It takes a while, that's normal. It seems to freeze at that stage but it will continue after a while.

---

### Post by badguyanil on 2007-10-19
Well that problem is solved as you can see! the problem now is as described above in my reply. tanx for the help though!

---

### Post by badguyanil on 2007-10-20
intalling Startup-Manager did the trick! got all set and working fine now! thanks all for help.

---

