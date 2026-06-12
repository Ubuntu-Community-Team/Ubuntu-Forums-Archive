---
title: "Monitor Crashes Randomly Requiring Poweroff to Reset"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2006-03-27
I've been having this intermittent problem where my monitor goes blank, shows a small blue box with (often strange) refresh rates, and then shuts off. The computer is still running and I can do CTRL-ALT-DEL However, when I reboot in that way, the computer reboots and the monitor stays shutoff no matter what I do. The only solution has been to physically turn the machine off and restart.

At first I thought the problem was GDM related, but now I don't use GDM or have it installed. I checked my BIOS settings and disabled all power features that I could. I thought it was GNOME related, but now I don't use GNOME, I use fluxbox. Then I checked my /etc/X11/xorg.conf file and noticed that it was missing my refresh rates--why I don't know. So I fixed that hoping that it was the cause of the problem. It wasn't :(  The problem still occurs.  These are the situations where I've seen it happen:

exiting window manager
switching virtual consoles
occaisonally when exiting xmame (I rarely use xmame)

Monitor: ViewSonic A90f+
Video Card: SiS  I'm using the winischhofer driver

I've attached my xorg.conf file

Any help is greatly appreciated.

---

### Post by Thirsteh on 2006-03-27
First, sorry if I'm stating the obvious, but.. Have you tried turning off any power saving features inside Linux? Any screensaver, standby timer, anything..?

---

### Post by Pragmatist on 2006-03-27
> Originally Posted by: **Thirsteh**
First, sorry if I'm stating the obvious, but.. Have you tried turning off any power saving features inside Linux? Any screensaver, standby timer, anything..?

I'm pretty sure.  Where/how would I check to be certain?

My monitor does go blank and when I hit a key it goes away.  The mouse doesn't awaken it, though.  It annoys me as I would like to turn off any powersaving/screensaving mechanism.  Could it be that there is powersaving built into the monitor itself?  I looked through the on-screen menu for my monitor and didn't see anything that seemed relevant.

---

### Post by jeremiebergeron on 2006-03-30
I'm not sure if this will help but I have managed to turn off my power saving features by running the following:

xscreensaver-demo

And go to advanced and see if power management is enabled there. Another command that may help is:

xset s off

This one should disable the screen blanking. Just type xset to see the parameters for the command.

---

### Post by Pragmatist on 2006-03-30
Thank you for the advice. It turns out that the problem doesn't appear to be X related. This morning the monitor crashed again. It went down when I logged out. To try and figure out what is going on I used SSH to remotely administer via another computer.

USING SSH:
X was not running on the system, so that means it was able to exit from X. Nothing seemed unusual while I was administering the system via SSH.  However, the ONLY way I could get my monitor working again was to use the shutdown command via SSH and then physically turn the machine back on. Reboot didn't work. The machine reboots, but the monitor stays shutoff. physically unplugging the monitor doesn't help either. FYI, the keyboard does work.

I'm not sure if the DISPLAY variable is supposed to be set even when in a virtual console. If so, then there was nothing in the DISPLAY variable when I checked via SSH. Maybe the display variable gets wiped out while exiting X ??? :-k
I did manually set the DISPLAY variable by typing: DISPLAY=:0.0  The variable stayed set, but this didn't change anything.
Help! :confused:

---

### Post by klytu on 2006-03-31
Have you tried to rule out faulty hardware? If you have another working monitor, extra good RAM, and/or another working box you could try different combinations and attempt to isolate a bad component.

---

### Post by Mustard on 2006-03-31
Does anything come up in your /var/log/Xorg.0.log? Or even the Xorg.0.log.old if there has been a reset since the monitor went down.

Maybe this will bring up some errors from that log..

```
cat /var/log/Xorg.0.log | grep EE
```


My first thoughts are hardware failure.  I wonder whether its the monitor failing or the graphics card, or a faulty connection between the monitor and the graphics card.  The fact that you see the 'blue thing' on the screen makes me think that the monitor is not seeing the graphics card anymore.  Is this the type of 'blue thing' you are talking about?  If its a graphics card and not onboard graphics, then I would even wonder whether its a power supply failure coming on.

---

### Post by Pragmatist on 2006-03-31
Thank you for all of your input.

I really doubt that it is a hardware failure.  The reason is that the problem **only** occurs when moving between X and the console (exiting the window manager, changing VTs). If it were a hardware failure of the monitor, for instance, then the problem would present itself in a variety of ways. Also, moving between X and the console isn't especially intensive for the monitor, while watching DVDs, for example, is. I watch DVDs for hours every day and never have a problem.

The main hinderance to solving this problem is the fact that it is not consistently reproducible. This makes testing different theories very difficult.

Update: Yesterday, when I exited the window manager, **not only did the monitor crash, but the keyboard did too.** This almost certainly indicates a **problem with X**.

Does anybody see anything wrong with my xorg.conf file?  Any suggestions on how to troubleshoot my X configuration?

Meanwhile, I will read more about X and see if I can figure something out.  If not, I will try upgrading/reinstalling X

---

### Post by cliff0108 on 2006-03-31
I've had this too and have yet to isolate why it happens. In my case the screen becomes jumbled with coloured lines. A reboot cures it - so I suspect it is application related. I have dual boot and I know the hardware to be good.

---

### Post by homersbrain on 2006-08-11
I also have this problem. First the screen blanks and then goes into standby. It happens randomly and only a reboot brings it back up. No problem with the hardware because it never happens in windows. I reinstalled dapper again to see if XGL screwed something, but it's still the same. Sometimes I can run ubuntu for an hour, other times less than 10 mins. My vid card is a radeon 9000. Is it the ati driver, X or even the kernel?

---

