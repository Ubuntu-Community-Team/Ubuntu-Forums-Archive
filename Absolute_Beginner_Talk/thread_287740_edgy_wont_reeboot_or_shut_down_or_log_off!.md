---
title: "edgy wont reeboot or shut down or log off!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tramposhay on 2006-10-29
Hi, 
I fresh installed edgy yesterday and during messing with getting video drivers and beryl working (which it does now - eventually!) I cant seem to log off- reboot or shutdown!

As soon as i click either of these options my screen goes blank flashing "no input detected." my computer stays on, and i have to manually hold the power button on the chassis to turn it off...

I think this is a video issue of some sort

At first i thought maybe it was a resolution issue, so i went off and deleted all the resolutions in xorg.conf that my monitor couldn't display.

But it still seems to be an issue.

Any help is greatly appreciated, Thanks :KS 

My rig: Running Ubuntu Egdy 64bit
AMD64 3500
ATI X850 PE Platinum
1.5 GB RAM

---

### Post by tramposhay on 2006-10-29
bump!

I've still not fixed this error! am at the near end of my tether! ](*,)

---

### Post by John.Michael.Kane on 2006-10-29
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```

As a last resort reinstall,and reinstall you ati drivers [http://ubuntuforums.org/showthread.php?t=235145](http://ubuntuforums.org/showthread.php?t=235145)

Try getting use to the machine/OS before you go install Alpha eyecandy addon's

Also read this [http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209)

---

### Post by whatintheworldisthat on 2006-10-29
Try pressing ctrl + alt + f1, login and enter the command "sudo shutdown -P now" to shutdown the computer and see if it works at all, if it doesnt press alt + f7 to go back to your desktop. It would be weird if you couldn't shutdown from the command line.

---

### Post by tramposhay on 2006-10-29
Thank you for your replys

whatintheworldisthat as soon as i hit ctrl + alt + f1 i get the 'out of range' message on my screen

SD-Plissken: i will try to reconfigure x as you have suggested ill post back with results.

thanks again..

---

### Post by spyrakos on 2006-11-19
I'm having the same problem, regardless of whether I'm using an XGL/Beryl session, or a plain Gnome session (I have set up beryl not to start up on boot but rather manually).

My solution (temporary, I hope) is somewhat strange, but works: open terminal, become su, then simply type

```
shutdown -r now
```
to reboot, or
```
shutdown -h now
```
to shut down. I found this strange, since I guess the GUI buttons should be using the same commands. Somehow though, this way the system goes down smoothly as before.

---

