---
title: "My friend messed my fresh 7.10 install"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by makko on 2008-03-31
Hi Guys,

I was just using ubuntu and the update manager was running/installing updates.

My friend ten proceeds to open some billiards game from his external hard drive..

The screen then goes blank and then there is just a blank screen that just shows my background..

same thing happens any time I login now..no desktop!

What can I do to fix this??

Thanks in advance..

Makko

---

### Post by Het Irv on 2008-03-31
If you have a fresh install and have not configured any, reinstalling won't be that much of a pain.

But try this first:
When you come to the blank desktop, press Alt-F2
In the box that pops-up type "teminal" and press Enter.
In the terminal type ```
sudo apt-get install ubuntu-desktop
```If that installs correctly you may have to restart your desktop (Ctrl-Alt-Backspace)

---

### Post by makko on 2008-03-31
Ok i've already used the desktop and browsed the net and stuff so the desktop should be fine.

I'll go and try it now though..I'll report back.

Thanks..

---

### Post by makko on 2008-03-31
Nothing happened when I hit alt-f2..

What could cause something like this to happen.

---

### Post by Het Irv on 2008-03-31
I think this is what happend:
When you install updates, Ubuntu will delete the old file and then replace it with the new version, when the computer crashed and then restarted there was a file missing that was needed to run the computer.  If alt-f2 is not working, then your problem goes deeper that just the Ubuntu-Desktop.  Someone eles may know few lines of code that could help you, but your best bet would be to reinstall Ubuntu.

---

### Post by forrestcupp on 2008-03-31
If alt-F2 doesn't work, just boot to your recovery console.  It should be the 2nd option in your GRUB menu.  It will boot to the command line as a root user, so you won't need 'sudo'.  Just be careful.  Then type
```
apt-get install ubuntu-desktop
exit
```

If it still doesn't work, boot to recovery again and try reconfiguring X
```
dpkg-reconfigure xserver-xorg
```
And just to be safe, you can choose the Vesa video driver, then when you get to your desktop, you can get the proper video drivers working.

---

### Post by billgoldberg on 2008-03-31
Just reinstall ubuntu.

It will take about 30 minutes, i'll bet you can't find a solution that quickly.

---

### Post by Het Irv on 2008-03-31
> **forrestcupp said:**
> If alt-F2 doesn't work, just boot to your recovery console.  It should be the 2nd option in your GRUB menu.  It will boot to the command line as a root user, so you won't need 'sudo'.  Just be careful.  Then type
```
apt-get install ubuntu-desktop
exit
```

If it still doesn't work, boot to recovery again and try reconfiguring X
```
dpkg-reconfigure xserver-xorg
```
And just to be safe, you can choose the Vesa video driver, then when you get to your desktop, you can get the proper video drivers working.

Yeah that should work because updates don't affect the Recovery console correct?

---

### Post by makko on 2008-03-31
It is fixed now..

So here's what I did..

boot into recovery console.
sudo apt-get install ubuntu-desktop
*Message:dpkg was interrupted. Use dpkg --configure -a to fix
I then typed the above command. It went throught lots of setups.
I just typed exit then and restarted..

Perfect.

Thanks for all your help people.

Now all I need is a kernel patch to enable support for my JMicron chip..:(

---

### Post by forrestcupp on 2008-04-01
> **makko said:**
> 
*Message:dpkg was interrupted. Use dpkg --configure -a to fix
I then typed the above command. It went throught lots of setups.
I just typed exit then and restarted..

Nice!  Good for you.  You don't know how many people don't take the time to just read the output and try doing what it says to do.

---

