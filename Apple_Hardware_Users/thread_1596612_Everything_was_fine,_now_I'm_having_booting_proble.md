---
title: "Everything was fine, now I'm having booting problems, low graphics errors and freezes"
date: 2010-10-14
forum: Apple Hardware Users
---

### Post by ilazria on 2010-10-14
I'm not sure what I did. Maybe it was an update somewhere. Maybe it was one of my "let's add this thingy!" moments. 

First, here's the specs on the computer:

Intel MacPro (desktop, not MacBook) early model (used to be my dad's)
4 CPUs
Intel(R) Xeon(R) CPU            5150  @ 2.66GHz
graphics card: nVidia Corporation G92 {GeForce 8800GT} (rev a2)


The problems started when things started freezing frequently. Digging through the internet, I found found some options that were supposed to help, and chose to update to the new Xorg. X11, I believe is what I did. IT seemed like the simplest option. 

Things weren't freezing randomly after that. Instead, Ubuntu consistently crashed whenever the Update Manager popped up in the background. I had to use the press-and-hold-power-button method to restart the computer. Afterwards, I could manually open the update manager to install updates, or run them from the terminal, with no problem. 

Just as I was getting ready to try to find out what to do next, I had what I believe is called screen corruption? The image on the screen got all weird, with green lines outlining stuff. It's kinda hard to explain. It was basically the same thing that happened when I used the MacOSX without SMC Fan Control, and things overheated.

So another press-and-hold restart, except now I can't boot straight to the MacOSX at all. Digging again for info, I realized I had somehow stumbled upon the way to run MacOSX on one drive and Ubuntu 10.04 on another, and use the option key to select the drive I wanted to use, basically by accident. I had no idea this was something that others were having trouble setting up, and sadly, I can't remember what I did! (thank you, stupid pills that keep me sane, but kill my memory)

Now, when I start up Ubuntu, I have to use low graphics mode. I get the low graphics error screen every time. The splash screen also looks funny, with orange and white dots (not referring to the orange dot loading bar. That is still there, working as usual) in an even pattern across the whole screen, over top of the regular splash image. 

I can still boot to Ubuntu by holding the option key and selecting that drive. As always, it takes me to the GRUB screen, where I can choose regular or recovery mode. It has also always given me the option to boot to the MacOSX, which is now the only way I can get on OSX. Before now, I could boot to OSX just by pressing the power button and letting the desktop start up on it's own. Previously, I could also enter OSX by choosing the OSX drive after holding the option key. That doesn't work now. I can't even boot to OSX in safe mode, just from the GRUB screen.

Everything runs like normal in MacOSX, and all of my files and such are there. However, I can't put the computer to sleep or run a screen saver. Don't know if this has any significance.

I also can't boot to the Snow Leopard disk. I tried to run that to do a hardware test and use disk utility, but it just won't start up. 

So, what with everything that's going on, I imagine that just doing a reinstall on both drives is the way to go, but I'm afraid to do anything. If anyone has an opinion on what's gone wrong, maybe has some guidance or experience, I'd appreciate any help. I'm backing up everything important on an external HD right now, and will probably keep digging through forum posts while I wait for someone to read this. If you need any other info or logs, let me know.

---

### Post by zeroti on 2010-10-14
Yes, a reinstall does sound like a possible solution, but you might be having hardware issues instead.. it would be really good if you could get the hardware test to boot up somehow. Did you try booting up to that by holding the option key? I'm surprised that isn't working for you. Did you do something to change your firmware?

If the hardware test is on a separate disc from the install medium, you can boot it by holding "D" on startup, but if it's the same disc, it will probably boot the installer. I'm not familiar with grub, as I'm on a ppc computer, but can you boot the test from the grub menu?

Maybe if the reinstall or personal hardware test doesn't work, you can try bringing it to the Apple store and see if they can diagnose a hardware issue.

Good luck. :)

EDIT: If you did change the firmware somehow, maybe there's a way to restore it in os x? you could try googling the apple support.

---

