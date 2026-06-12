---
title: "Any fixes for Dapper freezing at login for iMac G5"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by sbeltz on 2006-07-20
I updated from Ubuntu Breezy to Dapper this afternoon on my iMac G5 and I have run into the problem where it freezes at the login screen. I was able to fix the problem for Breezy by turning off the login sound and disabling the esd, but this solution does not seem to be working for Dapper. Are there any solutions at all that will fix this problem or will at least provide a workaround? Having sound is not a requirement. 
I'm desperately looking for a solution as I really need to get it my mac working again (work related pressures). Any thoughts or suggestions would be greatly appreciated. Thanks.

---

### Post by gwon on 2006-07-20
I'm sorry to tell you that you're just going to have to join the ranks of iMac owners who can't believe that the Ubuntu developers would release a **final product** with a bug that was a problem in the last release.

Join the party [[click]](http://www.ubuntuforums.org/showthread.php?t=185755)

---

### Post by sbeltz on 2006-07-20
After several hours of trying different things, I was finally able to get passed the frozen login screen. Below are instructions on what I did (there were a couple of things and I'm not sure which actually did the trick):

- Restart your machine and log into Linux, but before it gets to the login screen, force quite the process by pressing Ctl-Alt-Backspace. The OS will try to load up 6 times, but each time, kill it. Eventually a dialog box will pop up stating that there could be a problem and you have 2 minutes to fix it (unless you enter "sudo killall gdm" after logging in.)
- login
- Enter “cd /etc/X11/gdm”
- Enter “sudo nano -w gdm.conf”
- Find the line “SoundOnLogin=true” and change it to false
- Save and exit
- Enter “gconftool-2 –-type bool –-set /desktop/gnome/sound/enable_esd false”
- Enter "cd /etc/"
- Enter "sudo nano -w modules"
- snd_powermac will be listed. Insert a # at the beginning of the line.
- Save and exit
- Do a hard reboot. At the login screen you should have mouse and keyboard control.
- Celebrate!

---

### Post by gwon on 2006-07-21
How are the fans sounding? Full speed?

I may give this a try tomorrow afternoon, and I'd like to know if I need to track down the patch for the thermal control.

---

### Post by sbeltz on 2006-07-21
What I did above just got me past the frozen login screen. The fans still run continuously. I haven't figured out a workaround for that yet.

---

### Post by sbeltz on 2006-07-21
Let me correct my above statement. It looks like the fan issue has been resolved. Yesterday, when I was making the changes mentioned above to fix the login issue, the fan was running like mad. Even afterwards, the fan was quite loud. But this morning, it's running quietly and hasn't increased in volume at all. I have no clue what changed, although the computer was off all night. Nonetheless, I'm quite pleased with the results.

---

