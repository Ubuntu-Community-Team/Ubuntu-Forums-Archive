---
title: "Regaining Control of Hung System?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-08-07
Hi,

What are the basics for attempting to recover a system that has frozen itself up?  In Windows there is the task manager.....

My kid's 6.06 system locked up yesterday.  She had Firefox open, using Pandora, and when she accidently started up Tux Typing, while looking for a different game, the screen resolution reduced and the GUI froze up.  Most of the icons from the menu bar and the status bar disappeared, as well.

The system would respond to keystrokes but not to the mouse.  Because Firefox was minimized, I could tab to the terminal icon on the desktop and run it by pressing the enter key.  I tried to shut the system down from the terminal, switching to root, but I am not yet familiar enough with the syntax for the shutdown command and could not get it to run.  I was not helped by the fact that most of the terminal window was outside of the screen display area.

My next attempt was pushing the power button, rather than the reset switch, which would have forced an ungraceful reboot.  The power switch brought up the shut-down/log-off/change-user menu.  I could see enough of the menu to tab through it to the restart icon and gracefully reboot the system.

Does anyone have any pointers for dealing with this sort of stuff?

---

### Post by davebgimp on 2006-08-07
Well, if you can get at the terminal you can kill the processes causing the problems.

**killall firefox**

or 

**ps -A|grep firefox**
and note the number associated with the process (there may be more than one depending on the program) and then
**kill 'process number'**

Repeat either method for other suspect processes until you have control back.

---

### Post by colo on 2006-08-07
There are several ways corresponding to several levels ov severity of the lockup. The easiest way to regain control about you X-Server and GUI-subsystem is to hit Ctrl+Alt+F1 (or F2, F3, ..., F6), login on the virtual text terminal with your user, and use programs like top, ps, kill and killall to terminate the blocking application.

If X itself hangs and refuses to give you control of the keyboard, so you can't switch to a VT (as described above), there's a neat little thing built into recent kernels, called the "Magic SysRequest Key". (usually the "PrintScreen"-key on your keyboard). Notes on how to operate it are to be found here: [http://snafu.freedom.org/linux2.2/docs/sysrq.txt](http://snafu.freedom.org/linux2.2/docs/sysrq.txt)

If all else fails, you can still try to remotely connect to your box via ssh, and see if you're able to log in, and kill whatever is bothering you.

Last resort is hard power off. But please at least TRY Alt+SysRq+S to sync your disks.

Hth.

---

### Post by harisund on 2006-08-07
Generally it is an X application that crashes and not the Linux kernel itself. In most cases, you could Ctrl+Alt+Backspace, and *AT THE COST OF LOSING UNSAVED DATA* restart your X server and be back on track.

Otherwise colo's suggestion here is practically the best. Make sure you have SSH server installed and running in order to remotely access it.

---

### Post by houseisland on 2006-08-07
Thank you all.  Most informative.  Most helpful.

5 :KS / 5 :KS 

:cool:

---

