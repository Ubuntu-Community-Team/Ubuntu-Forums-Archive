---
title: "[SOLVED] Quit not working!!!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-11-09
Guys this is strange but off late i am not able to Quit!!! :confused: What i mean is as soon as i click on the Quit/Logout button in AWN or the quit button on the menu bar the system gets stuck. The icons on the task bar and awn do not respond. i need to use the alt+ctrl bkspc to go the login window to shut down. or do the init 0 way! kindly help!!!

---

### Post by overdrank on 2007-11-09
> **badguyanil said:**
> Guys this is strange but off late i am not able to Quit!!! :confused: What i mean is as soon as i click on the Quit/Logout button in AWN or the quit button on the menu bar the system gets stuck. The icons on the task bar and awn do not respond. i need to use the alt+ctrl bkspc to go the login window to shut down. or do the init 0 way! kindly help!!!

Hi and maybe you can find some help here.
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)
Good luck and hope this helps!

---

### Post by FuturePilot on 2007-11-09
When that happens press Esc and see if it becomes responsive again. Are you using Compiz?

---

### Post by LeChacal on 2007-11-10
Sounds like the same problem that I am having.
[http://ubuntuforums.org/showthread.php?t=606172](http://ubuntuforums.org/showthread.php?t=606172)
But I am using Gnome and from the screen shot I see you are not, I don't know if that matters or if it is a lower level problem.

---

### Post by badguyanil on 2007-11-10
>  Re: Quit not working!!!
Sounds like the same problem that I am having.
[http://ubuntuforums.org/showthread.php?t=606172](http://ubuntuforums.org/showthread.php?t=606172)
But I am using Gnome and from the screen shot I see you are not, I don't know if that matters or if it is a lower level problem.

Well i am using Gnome!  it is ubuntu 7.10 guess i failed to mention it.


> When that happens press Esc and see if it becomes responsive again. Are you using Compiz?

i am using compiz. You can c AWN running on compiz effects enabled. Tried using ESC. Nothing happens. The desktop still remains nonresponsive.
I also tried the same with no desktop effects option. But still the same effect. Systems just stops responding.

---

### Post by badguyanil on 2007-11-10
> **overdrank said:**
> Hi and maybe you can find some help here.
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)
Good luck and hope this helps!

i dont c any help in there. It is not that the shutdown or restart process hangs. It is only that when i click on the Quit/Logout button nothing happens. Ideally i should get the logoff, shutdown, restart options, which i dont get. The desktop becomes unresponsive to keyboard and mouse. The only thing that works is alt+ctrl+ bksps

---

### Post by matthewcraig on 2007-11-10
I am having the same problem.  If you leave the computer alone for 5 minutes or so, the Quit window appears, finally.  I think there is something going into a time out with the power settings on my old BIOS.  This didn't happen in Feisty.  Good luck with your fix -- I have not found much information on this subject so far.

---

### Post by badguyanil on 2007-11-10
> **matthewcraig said:**
> I am having the same problem.  If you leave the computer alone for 5 minutes or so, the Quit window appears, finally.  I think there is something going into a time out with the power settings on my old BIOS.  This didn't happen in Feisty.  Good luck with your fix -- I have not found much information on this subject so far.

ok will leave the system for 5 minutes and check. Do let me know if you find the bug. It did not happen in gusty for quite some time. Only off late i have started facing the problem.

Thanx

---

### Post by badguyanil on 2007-11-10
> **FuturePilot said:**
> When that happens press Esc and see if it becomes responsive again. Are you using Compiz?

I tried ESC today and yes it became responsive again. I am using Compiz.... anything to do with that!!!

---

### Post by matthewcraig on 2007-11-10
I'm not using Compiz and I see the same thing.

---

### Post by badguyanil on 2007-11-10
bump....anyone facing similar issue and has fixed it...plz help!

---

### Post by LeChacal on 2007-11-10
I am moving on to this post it is getting more traffic than mine on this subject. What I get in comparison to what has been talked about: I am not running Compiz, and if I hit Esc it doesn't become responsive again I have to wait the few minutes. I have had this problem since I upgraded (I didn't do a clean install just download the update over 7.4) to 7.10. I have looked all over everywhere for help and this is the first that I have seen anyone else having the same problem.

---

### Post by badguyanil on 2007-11-10
Well i did a fresh install on my PC. I dont think it is the problem with upgrade. Well running Compiz or not it is the same for me too! Tried disbling the effects and quit!! but the screen hangs the same way as with Compiz running :(

---

### Post by badguyanil on 2007-11-10
OK this one is fixed. Had removed gnome-power-manager module to be loaded at startup. When clicking on quit it was trying to load the module which was taking too much of a time. have kept the same at startup now. Quit works fine!

---

### Post by matthewcraig on 2007-11-11
" Had removed gnome-power-manager module to be loaded at startup. "

What do you mean?  I would love to get this fixed.  I looked at Synaptic and saw that gnome-power-manager package is still installed, but it is possible I turned it off from starting.

---

### Post by FuturePilot on 2007-11-11
> **matthewcraig said:**
> " Had removed gnome-power-manager module to be loaded at startup. "

What do you mean?  I would love to get this fixed.  I looked at Synaptic and saw that gnome-power-manager package is still installed, but it is possible I turned it off from starting.

System>Preferences>Sessions
Uncheck Power Manager
However this will probably make your screensaver never turn off.
Does this problem always happen or is it just immediately after login if you try to quit right away?

---

### Post by matthewcraig on 2007-11-11
Yes, that matches my computer.  I had turned off Power Manager in System > Preferences > Sessions.  I will check later to find out if turning it on will fix the Quit issue.  Thanks for updating this post, badguyanil and FuturePilot!!

---

### Post by badguyanil on 2007-11-11
thanks guys for the update. Had some real urgent work so could not put in the full info. Anyways once you turn off Power Manager in System > Preferences > Sessions, while quitting there is a modile gnome-session-save which is loaded, which inturn tries to switch on the gnome-power-manager. The first logout try was taking too much time, coz the system tries to get gnome-power-manager back. Once you get the logout screen (after about a few minutes), cancel and try to logout again and it will be instant, coz then gnome-power-manager is already loaded!

---

### Post by EscapeCharacter on 2007-11-23
This is funny I had exactly the same problem. After reading your post I went to System->Preferences->Sessions as you suggested and found that the Power Manager daemon was *disabled already*. I enabled it and was instantly able to get a logout dialogue box so that I could log out, power down etc. So it appears that the exact opposite of whatever setting you find this at is probably worth a try.

I never had this problem when I installed gutsy originally. Something changed either after I tried to enable the hibernation and suspend modes (since my MB is supposed to be capable of it) through System->Admin->Power Management, or when I shut off the frequency scaling (powernowd) through System->Administration->Services.

In any case, its working now. Thanks for the help.

^]

---

### Post by DioSonoIo on 2008-02-13
I will try it when I get home but in the last days I have "played" with startup issues, so it's more than possible this is the root cause of my problem too!!!

Thanks!!:)

(to escapecharachter: u are saying the same thing!! Power manager has to be started at the boot, not at the shutdown!;))

---

### Post by levelnext on 2008-03-08
Thankyou very much guys, this helped, it's working now!

---

### Post by henriquemaia on 2008-07-09
> **badguyanil said:**
> OK this one is fixed. Had removed gnome-power-manager module to be loaded at startup. When clicking on quit it was trying to load the module which was taking too much of a time. have kept the same at startup now. Quit works fine!

What a relief! A friend of mine was having this same issue on her Ubuntu and I couldn't figure out what was the problem. But you solution did the trick. Thanks a lot for this one!

---

