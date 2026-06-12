---
title: "windows drivers?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tentel on 2007-12-02
i've been reading many how tos on how to use ndiswrapper to use the native windows drivers.



but every one of them assumes that you already have the windows drivers handy.


i have no internet connection on my laptop that is running ubuntu.



i have internet on my other computer, but i can't figure out how to find the drivers i need.

i went to the hp website and found some xp drivers, but they were a .exe file.

i saved them on a disk, but ubuntu couldn't use the file.



lspci gives me

network contoller: broadcom corporation bcm94311mcg wlan mini-pci



note:  i tried to use the restricted drives manager.  it took me a while, but i got it to work successfully.  kinda.
eveything seemed to work except that i still couldn't get online.

and also, my computer lagged very noticably.
and had problems suspending, restarting and shutting dowjn.

so i deavtivated that.




thanks
-tim

---

### Post by erfahren on 2007-12-03
how are you trying to connect to the internet? 

what version of Ubuntu?

what kind of laptop? you mentioned problems with the suspend function. That's currently a problem with Gutsy. I've seen that some laptop users got it to work but I couldn't (I reverted back to Feisty).

The shutdown/restart problem may be unrelated to that, what happens exactly when you try?

I don't know anything about using ndiswrapper, but I do know that driver .exe files oftentimes first extract somewhere before going through the actual install process. I'd try launching one on the other pc. Just cancel it if it looks like it's going to be a problem. (I've seen some drivers archived in WinZip .exe's - 7zip can open them.)

---

### Post by tentel on 2007-12-03
i'm trying to connect to a wireless network.

though when i uplug it, and then hard wire my laptop to the internet, it still doesn't work.

maybe there is just a problem with gutsy and i should use feisty?


i'm currently using gutsy.

i have a hp laptop with an AMD 64 dual-core processor.




when i was using the bcm43xx firmware from the resricted drives manager, when i would try to restart or shutdown, as it was doing so, when the screen truned black, it would start to bug out and white lines would shoot down the screen.

like static, but only horizontal.
also, when i would restart it, sometimes it would shutdown, but then not turn back on, and when i tried to shut it down, it shouldn't turn off.  it woud get almost their, and then just stop, and sit there.


but once i disabled the drivers, everything went back to normal.
when they were activated, the light on my laptop tellin me my card was on, was on, but i could not get it to find my network.


and under system>administrator> there was no network manager option, nor drivers manager.

---

### Post by erfahren on 2007-12-03
> **tentel said:**
> 
... and under system>administrator> there was no network manager option, nor drivers manager.
That's strange. Go to System > Preferences > Main Menu and see if those are unchecked to be shown in the menu. If that option isn't present either enter "alacarte" (without quotes) into the terminal to launch it.

Your shutdown/startup issue sounds the most serious right now. Maybe a video driver problem or just a problem with the correct resolution being detected. 

You said that if you disable the *drivers* in the restricted drivers manager it restarts fine. Did you try to disable just the video driver and leave the network driver enabled?

What kind of video card? lspci will list that as well (VGA compatible controller)

---

