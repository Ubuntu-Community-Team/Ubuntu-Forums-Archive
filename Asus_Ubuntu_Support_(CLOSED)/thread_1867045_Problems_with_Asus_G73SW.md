---
title: "Problems with Asus G73SW"
date: 2011-10-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Karl1982 on 2011-10-22
On my Asus G73SW, this morning I upgraded my scantly-used 11.04 to  11.10.  Scantly used in part because my keyboard backlight won't work in  Ubuntu, nor do most of the function keys.

After the upgrade, I'm having the following problems:

[LIST=1]
[*]The touchpad is malfunctioning
[*]Hangs during suspend/hibernate
[*]Keyboard backlight/function keys don't work
[/LIST]
What I'd really like to look at is the touchpad because... the bottom line is, if my touchpad doesn't work, Ubuntu doesn't work.

I  see there are a lot of threads about this, but my symptoms seem to be a  little different, so let me describe the problem in detail.  It works  fine for brief periods, but then it's like the finger detection goes  haywire.  It will either lock up and not move (although I can still  click with the buttons sometimes), or it will go berserk, dragging  windows all over the screen in a very erratic manner.  Then it stops and  returns to normal for a moment.

It also frequently brings up the  drag handles on windows when it has these episodes which leads me to  believe it's a problem in the driver.  The reason being, I have no  middle mouse button, but I can middle-click or middle-drag with three  fingers placed laterally.  This works in between the touchpad's  seizures.  It seems to think I've got fingers all over it.

If I don't touch the touchpad, it has no incidents...  just sits idle.  A USB mouse has no issues so long as I leave the  touchpad alone.  The touchpad works perfectly in Windows 7.  It also  worked fine in Ubuntu 11.04, although the Synaptic software for Ubuntu  is very feature-limited compared to the software for Windows.

On  my previous laptop, I didn't have problems like this.  Once I got the wlan driver loaded, it was smooth sailing.  I used Ubuntu as  my main OS, but I haven't on this one primarily because of the broken features.  Now with the touchpad driver  broken, it's completely useless without an external mouse, which just  won't cut it for me.  I would very much like to get the other problems  fixed as well, but the touchpad is a deal-breaker.

---

### Post by Karl1982 on 2011-10-25
Still has problems when booted from live cd, although it's a little different.  It won't let me do the three-finger window drag in the live cd, which seems to be the most common place for it to get stuck.  The window handles appear, and then I know I'm in trouble.  It sits there for a moment, like it's staring at me, then jerks my window all over the screen, sometimes maximizes it, etc.

This is so irritating.  Is there nothing that can be done about it?

---

### Post by fuzzylogicx on 2011-10-26
I had problems with the touchpad as well after doing the upgrade.  What I had to do in the end is wipe the existing ubuntu partition and do a fresh install.  However I have noticed that the back lit keyboard and hibernate hacks that applied to 11.04 do not seems to work in  Ocelot.  I would assume that no kernel modifications should need to be done now that those changes were merged in but that does not seems to be the case.

After a fresh install of Ocelot:

--Back lit keyboard does not work
--All function keys except F3 work however F4  does not actually do anything accept show that you are increasing the back lit keyboard brightness (however the backlit keyboard is not on so it does not matter) If you try to add the hack to /etc/rc.d it has no effect there is still no back lit keyboard.

--To Enable brightness control you still need to modify the nvidia settings for the default

--Suspending does not work after adding the recommended script for 11.04 it does not actually hibernate any longer it just sends you back to your login screen.

I was hoping with the new release that all of these things would be in the release but it is looking like I will need to downgrade to get it to work again :(

---

### Post by Karl1982 on 2011-11-04
I've been following bug#868400 for the touchpad problems, although no one seems to be finding a solution.  [https://bugs.launchpad.net/bugs/868400](https://bugs.launchpad.net/bugs/868400)

I haven't worked on my function keys yet because of the touchpad issue.  There's really no point.  I have to use Windows 7 exclusively until this is fixed.

I've been on board with Ubuntu since 8.10, and not once have I EVER had an upgrade go smoothly.  I'm starting to think I should just stick to LTS releases.

---

