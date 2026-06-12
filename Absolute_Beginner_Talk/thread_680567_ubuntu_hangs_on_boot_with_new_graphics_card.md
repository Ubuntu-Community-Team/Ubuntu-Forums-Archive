---
title: "ubuntu hangs on boot with new graphics card"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by noobuntu85 on 2008-01-28
I know there are many posts like this but i still cant figure it out. I'm a noob so please reply with noob terms. (sorry for my ingnorence)

I just got a NVIDIA GEFORCE FX 5500.

install went well under windows partition but when i try to boot into ubuntu7.10 the splash screen starts to show it loading but it wont finish loading. No blank screen or anything the progress bar just stops.

I tried to boot with live cd and the same thing happens.

I did install the restricted nvidia drivers before installing the card.

Help please anyone!
thanks

---

### Post by BillDozer on 2008-01-28
Do you also have a bult-in graphics card? If yes, then try to put the motior cable into that port after the system seems to hang and see if you get a signal from that source.

---

### Post by Perfect Storm on 2008-01-28
Try first with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by noobuntu85 on 2008-01-28
It works fine with my onboard graphics card but it hangs with new card.

---

### Post by Perfect Storm on 2008-01-28
You need to reconfigure xorg (described above) when changing card.

---

### Post by noobuntu85 on 2008-01-28
> **Artificial Intelligence said:**
> Try first with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I am on ubuntu right now with my onboard card should i do this in terminal?

---

### Post by Perfect Storm on 2008-01-28
You can do that - if you installed the nvidia driver - just pick that driver when running the reconfigure command.
Afterwards restartX
If it fail
run the command in failsafe mode and choose vesadriver.

---

### Post by noobuntu85 on 2008-01-28
> **Artificial Intelligence said:**
> You can do that - if you installed the nvidia driver - just pick that driver when running the reconfigure command.
Afterwards restartX
If it fail
run the command in failsafe mode and choose vesadriver.

i tried running that in terminal and all i get is this



xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080128031459

---

### Post by BillDozer on 2008-01-28
> **noobuntu85 said:**
> It works fine with my onboard graphics card but it hangs with new card.
OK, so you did try to switch you monitor cable when the system hanged and got a working picture or did you take your new card out and started again?

If you did the first thing, I would start and go to menu System -> Administration -> Screens and Graphics and disable the on board card.

That did the trick for me...

---

### Post by noobuntu85 on 2008-01-28
how do i get to failsafe? (again sorry for my lack of ubuntu know-how)

---

### Post by Perfect Storm on 2008-01-28
Try as Billdozer suggested first. If it doesn't work. Reboot - when the Ubuntu countdown (3-2-1) appear hit [esc] as I recall it (I'm at work now so I can't be quiet sure which button), then choose failsafe mode. Remember to write down the command as you only be in CLI

---

### Post by noobuntu85 on 2008-01-28
ok so i tried both suggestions and i am not having any luck. even in failsafe it gets so far and then hangs. So I cant even get to command line. ( i'm going to cry). I figured what the heck and i would try to reinstall but even just trying to boot to live cd it hangs. any other suggestions?

---

### Post by Perfect Storm on 2008-01-28
Tried disable the onboard card in BIOS?

Where does it hang in failsafe?

---

### Post by noobuntu85 on 2008-01-28
> **Artificial Intelligence said:**
> Tried disable the onboard card in BIOS?

Where does it hang in failsafe?

I have done so in bios. it is set to my pci card.

it does not show any err. in failsafe it even says ok on loading restricted drivers.
It hangs a  diff. part each time in failsafe but only when i am using that graphics card. never when i am using the onboard.

---

### Post by noobuntu85 on 2008-01-28
is there a way just to reinstall without booting to live cd. or will this not help my problem anyways?

---

### Post by Perfect Storm on 2008-01-28
alternate CD? It's text installer.
Can you disable the PCI card and see if it boots up?

---

### Post by noobuntu85 on 2008-01-28
> **Artificial Intelligence said:**
> alternate CD? It's text installer.
Can you disable the PCI card and see if it boots up?

it boots just fine when the pci is disabled and on board is enabled and my monitor is connected to the on-board but it only happens when pci is enabled on-board disabled.

---

### Post by BillDozer on 2008-01-28
If you can log on to your system on onboard card, try to do the following:
[LIST]
[*]Log into the system
[*]Go to System -> Administration -> Screens and Graphics
[*]Change the Card type to vesa
[*]Shut down.
[*]Plug in the new card
[*]Start up again.
[/LIST]

---

### Post by noobuntu85 on 2008-01-28
i'm downloading alternate cd now. I hope this works. I miss ubuntu already and it has only been about an hour.

---

### Post by noobuntu85 on 2008-01-28
> **BillDozer said:**
> If you can log on to your system on onboard card, try to do the following:
[LIST]
[*]Log into the system
[*]Go to System -> Administration -> Screens and Graphics
[*]Change the Card type to vesa
[*]Shut down.
[*]Plug in the new card
[*]Start up again.
[/LIST]

I have also tried this with no luck. when i go into screens and graphics it shows both my graphix cards as two diff. monitors. i have tried the orig. default and i have tried switching to the other but nothing.

---

### Post by BillDozer on 2008-01-28
If it shows both cards, eventhough you have disabled the PCI card in the BIOS you can try to disable your on-board card in Ubuntu, but not in your BIOS. And try to restart.

---

### Post by noobuntu85 on 2008-01-28
ok. idon't know what else to try. nothing is working. maybe i should just leave this computer as a windose box and just build another pc for ubuntu.

---

### Post by D45 on 2008-01-28
exact same problem with my pc  . I have 5600xt (PCI)
This problem started in 7.04 and 7.10 .
6.06 and 6.10 were fine

---

### Post by syn` on 2008-01-28
I'm having the same issue on my Dell. It boots up fine as long as it's on the onboard, as soon as I set it to any of my other cards, my Radeon 9200/9250 or Nvidia 6200, I start having the same issues. It gets to the load screen and eventually just stops loading a little way through.

If you hit F6 when the live CD or boot screen comes up, remove the splash and it will show your errors around when it starts loading the hardware. I've been trying to get this to work for two-three weeks now and the reconfigure doesn't work. If it won't even boot up on the card, the configure doesn't do anything, at least not for this problem, all it did was make it so I had to reconfigure my onboard again to get it out of safe graphics.

And no, failsafe mode didn't work. noapic/nolapic, none of that.

But as long as I leave my BIOS to my onboard I can boot up and run fine. And by the way, it's not just Ubuntu. I have Live CDs for 8-9 distros and I have the same problem with all of them.

---

### Post by JoshuaRL on 2008-01-28
Seriously, Nvidia should work great.  But I think that the issue here is that the system is seeing both cards despite having switched to the PCI one in BIOS.  You should try blacklisting your onboard card so Ubuntu only sees the new one.  I can't remember how to do that, but let's both give it a look.

EDIT  Aha!  [http://ubuntuforums.org/showthread.php?t=570098](http://ubuntuforums.org/showthread.php?t=570098)  That should solve it.  And a very nice explanation why it's happening too, courtesy of Julian67.

Google and "site:ubuntuforums.org" are your friend.  :guitar:

---

