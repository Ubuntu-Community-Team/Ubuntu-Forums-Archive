---
title: "Installation Issues"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by ebichuhamster on 2007-03-01
Hello

I've tried several times to install Ubuntu with less than more success.  The first time I tried installing Edgy, I could do it without much trouble, but i couldn't actually get it running after I restarted the laptop.  I have an HP Pavilion dv6000 with AMD Turion 64 2x, 120 Fuji something ATA hard drive, Nvidia 128 mb, and 1Gb of RAM. 

So then i tried version 6.06 because I was told it might be more stable (to all this i've burned nearly 6 or 7 cds trying to different burning speeds and just to see if the previous was corrupt)

This version didnt even make it to the windowing system.

(I had a little trouble in the middle cause i deleted the first Ubuntu installation in a very very stupid way (i deleted the partition using Partition Magic-which led the grub to have error 17, and i couldnt even run windows) but i managed to solve it by reinstalling version 6.1.  Then the same thing happened from the beggining.  It passes the ubuntu smbol then blackscreen as if waiting to writw something. Then freeze.  

Im downloading the alternate cd to see if that works, but im seriously considering something i read in another thread (smashing up the computer and just lay off for a while, u know keep low or something)

In other words, any advice will be incredibly apreciated ^_^ thanks

---

### Post by ebichuhamster on 2007-03-01
Oh yea! 

I forgot to mention something thats been bothering me ever since i started working with the partitions:

My hard drive partitions are sda(1,2,3..) not hda(1,2,3..).  A friend said that this was nothing to be bothered about, some schosis type thing (i think). 

If any more information about my system, just ask (exept for passwd and stuff)

and no, no other error message have popped up and alt+f1 doesnt display anything so ,, cant really know.

---

### Post by Capslock118 on 2007-03-01
sda.....i know that means sata, which brings up my question: are you trying to install on a raid?

---

### Post by ebichuhamster on 2007-03-01
as i said before, im pretty new so i dont even know what a raid is...looking it up now...

so im guessing, no im not (intentionally) trying to install it on a raid,, I followed every default step set up by the installation manuals and cd

---

### Post by ebichuhamster on 2007-03-01
ok found out what raid is,, something about complex disk space and efficient management,, but this is a personal computer .. my hard drive is FUJITSU MHV2120BH PL.. if this is in fact a RAID disk ,,,then  i dont know,,

thx for the help up untill now >_<

---

### Post by ebichuhamster on 2007-03-01
ok followed a thread suggesting hardware problems,,, 

it appears that this was it, because my Network Adapter was set (for some weird default reason) to disabled.... anyways

this at least allowed me to get to the Window Manager.

Funny thing is,, when I go to shut down it does the fade away screen thing,, but a bad glitch happens:  the top of the screen has the colors all messed up, and there's a looped that continues untill i press the shut down button for 5 seconds.

Im thinking this is bad,, but i dont know

---

### Post by confused57 on 2007-03-01
> **ebichuhamster said:**
> ok followed a thread suggesting hardware problems,,, 

it appears that this was it, because my Network Adapter was set (for some weird default reason) to disabled.... anyways

this at least allowed me to get to the Window Manager.

Funny thing is,, when I go to shut down it does the fade away screen thing,, but a bad glitch happens:  the top of the screen has the colors all messed up, and there's a looped that continues untill i press the shut down button for 5 seconds.

Im thinking this is bad,, but i dont know
If you're using Edgy, you may be able to correct your shutdown problem with this fix:
[http://www.ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1714220&postcount=9)

Also, you might want to check your xorg.conf file to see what video driver you're using:
```
cat /etc/X11/xorg.conf
```
scroll down to the video controller section, if "nv" is selected, that should work OK...however, if "vesa" is selected, then I'd suggest you change it to "nv"...post back if it's "vesa".

---

### Post by ebichuhamster on 2007-03-02
Agh >_< im gonna go crazy

I was on my way to fix the shut down problems,,,, (ubuntu was loading)
when suddenly i fell (ubuntu didnt load-after the progress bar under the nice ubuntu symbol the screen was black and usually in this stage i wait 2 seconds and the window manager apears, but out of 5 reboots, no succes)

something weird is that i thought i had solved this booting issue.  Yesterday I 'enabled' a disabled networking adapter in the boot options from the BIOS setup.  Ubuntu started without problems. After a restart, it didnt want to load once more, and i thought,, what if... no it cant be. Either way i tried it: i disabled the recently enabled Network Adapter. guess what: it started.

After this evidence it's pretty clear i have some hardware problems.  Thing is this is a laptop and I beleive that a newbie like me shouldnt be snooping inside it yet.

Any possible way to diagnose what the error/problem is so that i can at least identify it with certainty?

---

### Post by teaker1s on 2007-03-03
replied on other thread, but just in case
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")
can pm for chat if you wish

---

