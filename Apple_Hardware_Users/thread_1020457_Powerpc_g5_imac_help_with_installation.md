---
title: "Powerpc g5 imac help with installation"
date: 2008-12-24
forum: Apple Hardware Users
---

### Post by tumi2000 on 2008-12-24
I've downloaded ubuntu 8.10 and burned it into a disc, when I start up my mac holding 'c' key down yaboot 1.3.13 lunches but no matter what i boot; (live, live-powerpc64,check, check-powerpc64, driverupdates, driverupdates-powerpc64) I end up with a screwed up screen like this user [http://ubuntuforums.org/showthread.php?t=1018656](http://ubuntuforums.org/showthread.php?t=1018656)

but if I insert video=ofonly after any of the commands then I end up with a black screen with a _ icon and I cant do anything,
maybe you've noticed I diddn't mention live-nosplash commands it works (i think comes upsomething like BusyBox v1.10.2) but i don't know what to do :confused:

Can anyone tell me how to do this or make the installation work

---

### Post by tiresia on 2008-12-24
video=ofonly is an 'argument' that you give to the kernel. 
Therefore you must give it at the first yaboot prompt in this form
```
live-nosplash-powerpc64 video=ofonly
```
Check wich options you have hitting TAB.
Do not forget that the g5 is 64 bit (powerpc64)

Be aware that the Ubuntu LiveCD 8.10 doesn't work (at least didn't work for me the last time I tried it - it was a daily image).
Where did you download it?
If you want a stable LiveCD try Hardy (8.04).

On the other hand, if you want to install Ubuntu Intrepid, you should use the alternate CD. But we have also a small problem with it. Here you get the workaround for it
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by tumi2000 on 2008-12-24
Thanks for the quick reply I downloaded the daily build that is whats wrong,
downloaded the alternate image now just to find a blank cd

---

### Post by stream303 on 2008-12-24
With the alternate image, you can use what Tiresia has shown, but change the startup just a little bit:

Hit TAB at the second stage boot: prompt to stop the countdown and be sure to select "install64" or "powerpc64" - I forget exactly which one, but you'll need the 64 bit option for the G5 iMac.

After the system is installed, you may once again be greeted by a black screen.  In this case, at the second stage boot: prompt issue

```
Linux nosplash video=ofonly
or
Linux nosplash
```

If your G5 iMac is driven by nvidia, the system should pop right up without too much trouble.

There are quite a few threads showing how to add "nosplash video=ofonly" to your *append=* line in /etc/yaboot.conf and then making the system aware of that by running *sudo ybin -v*, so you won't have to do this every time you boot.

Which model do you have?
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

---

