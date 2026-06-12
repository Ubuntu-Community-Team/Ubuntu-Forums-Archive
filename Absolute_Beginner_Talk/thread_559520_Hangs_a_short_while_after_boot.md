---
title: "Hangs a short while after boot"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Wingcommander on 2007-09-25
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/13964](https://answers.launchpad.net/ubuntu/+question/13964) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/13964](https://answers.launchpad.net/ubuntu/+question/13964) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
just installed Ubuntu, and after appearing to go well it just hangs a few seconds into a fresh boot up. Here's what happens ...

1. Boot into gui.
I can enter my username and password - although it's worth noting that the letters appear lagged behind my typing - but then the screen shows only the Ubuntu logo in the centre and a grey box in the top left quadrant of the screen. Nothing happens at all then.

2. Switch to command prompt.
If I ctl-alt-f2 I can log in again (still with typing lag), and I can enter some commands (ls, cd, etc) although still with the typing lag. Then, a few seconds (maybe 30 odd) later I'm able to type but I only get what I've typed repeated back to me. Nothing actually works.

3. Switch to ctl-alt-f8
This seems to have halted on starting cupsd (there's no [OK] at the end and nothing ever prints on this screen again).

4. Repair mode.
This boots fine. No lag and no functionality :)

I've searched the forums but cannot find anything quite like this. Maybe I'm just bad at searching, but any help gratefully received.

One more thing - the Live cd that I installed from seemed to work fine. I could navigate around ok.

Another thing I almost forgot - if I press the power button on the pc, Ubuntu seems to detect this and shuts everything down properly. So it's sort of still running.

WC.

---

### Post by Wingcommander on 2007-09-25
I've found out what it is.

I forgot i had a USB Wifi dongle in (DWL-G122) - it was round the back of the PC so I just forgot it was there. Pulling this out allows it to boot just fine, GNOME runs and everything.

Now just got to find out how to install network stuff without a network to install from...

---

