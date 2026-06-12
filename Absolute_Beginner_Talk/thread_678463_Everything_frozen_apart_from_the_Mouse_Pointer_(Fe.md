---
title: "Everything frozen apart from the Mouse Pointer (Feisty)"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by RostokMcSpoons on 2008-01-25
Hi.

my tales of woe continue... I'm in the middle of downloading 250mb of Automatic Updates, and everything on my desktop has become unresponsive except the mouse pointer still moves.   The wifi dongle still has a flickering light so I *think* the download is continuing.

Are there any magic buttons I can press, so I can close down non-essential processes and don't lose what's downloaded (rather slowly)?, or should I just wait for the package to download (light to stop on the wifi) and hope it worked?, or am I just SOL?


This Ubuntu thing is kicking me to hell and back. I'm losing the will to live :(

---

### Post by prshah on 2008-01-25
OK a few points below:

1) I had this problem when I installed Kubuntu over Ubuntu using "sudo apt-get install kubuntu-desktop", especially when the screensavers kicked in.

2) You can try Ctrl+Alt+BkSpace to restart the X server (screen will flicker and login screen will appear after a few seconds, if sucessful).

3) You can try to switch to a different terminal by pressing Ctrl+Alt+F9 or F10 (login screen will appear if successful)

4) You can try to switch to a ordinary (character, non-gui interface) by using Ctrl+Alt+F1 / F2 / F3

5) As a last resort, you can try Ctrl+Alt+Shift+SysRq+B (=instant reboot) or E (=Terminate running processes, should drop you at ordinary interface if successful)

If none of the above seem to work (no change in display) then your machine is locked / frozen, use the reset switch to reboot it.

I personally found that I cannot get Kubuntu and Ubuntu to exist and play together, so I had to switch back to Ubuntu. 

Another thing you can check is if certain screensavers or power modes (System-> Preferences-> Screensavers) are causing the freeze.

Cheers,
PRShah

---

### Post by RostokMcSpoons on 2008-01-26
Thanks - it was a clean install.
I left it running til the wifi light stopped flickering, rebooted, and found Update Manager informing me I could download 188mb of updates, which was the final straw

It may have been a screensaver / power issue.
 I don't know for sure now, cos I've blown it away to try openSUSE.


(which sucks too*)





* for a noob like me

---

