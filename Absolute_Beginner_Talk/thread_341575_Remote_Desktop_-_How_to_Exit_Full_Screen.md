---
title: "Remote Desktop - How to Exit Full Screen?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-01-18
I'm using Dapper and a remote desktop session to a Windows server from my laptop. I successfully used the -f (fullscreen) option but once I'm done with my remote session, how do I cancel, switch, and/or return to my Ubuntu desktop? When they say full screen, they really mean full screen... 

btw - for anyone trying rdesktop for this first time, it was simple and the performance is extremely good! Better even than my old Windows-to-WIndows session on the same network.

---

### Post by x64Jimbo on 2007-01-18
Use the following arguments.
```
rdesktop -D -K -g <width>x<height> -z -a <bitdepth in multiples of 8> -u <username> <ip/DNS name>
```
Set your geometry to be the same as your native screen resolution, then start the program while you are on a different viewport, then use Ctrl+Alt+Left/Right to change viewports.

---

### Post by linux_believer on 2007-02-03
The easiest method is to press F8 and you will get options and one is to exit.

---

### Post by mikerhodes on 2008-03-13
You can use Ctrl-Alt-Enter to switch between full screen and windowed mode for the remote desktop :)

Edit: I just read that there can be problems with a composited desktop and using Ctrl-Alt-Enter to switch modes. If this happens you need to change back to metacity (set System -> Preferences -> Appearance -> Desktop Effects to "None")

---

### Post by gyorgy5635 on 2008-04-03
The System->Preferences->Appearance->Visual Effect->None solved my problem. Thanks mikerhodes.

---

### Post by nota9 on 2008-04-24
On Hardy's Remote Desktop Viewer 0.5.1 [F11] switches between full screen and windowed mode.

---

### Post by sudomp on 2008-05-01
I also had the same problem & I didn't want to lose out on cool compiz effects but still wanted to connect to my office machine on rdesktop. Doing this helped me keep both.

[http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/](http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/)

---

### Post by Vazovsky on 2008-05-01
I had same problem with exiting full screen mode in rdesktop. Solution given by sudomp works great for me. Tnx!

---

### Post by boywithcar on 2008-05-01
> **Vazovsky said:**
> I had same problem with exiting full screen mode in rdesktop. Solution given by sudomp works great for me. Tnx!

FYI
I am using Hardy Heron and connecting to remote desktop of Windows Xp.
If you set both "Attach to console" and "Enable window manager's key bindings" in the "Performance" tap, "Ctrl + Alt + Enter" could help you change the mode of the "Terminal Server Client". Although it still has the focus after applying "Ctrl + Alt + Enter", you could either use "Ctrl + Alt + Left/Right" to switch the workspace or use "Alt + Space" to pop down a menu of "Terminal Server Client", where you could choose "Minimize".

If you need to completely exit "Remote Desktop", you could "Start"->"LogOff" (in Windows).

---

### Post by linfidel on 2008-07-20
> **sudomp said:**
> I also had the same problem & I didn't want to lose out on cool compiz effects but still wanted to connect to my office machine on rdesktop. Doing this helped me keep both.

[http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/](http://adminian.com/2008/03/18/fix-rdesktop-exit-fullscreen-issue-in-ubuntu/)
Thanks, that solved the problem for me.  I'd thank you officially, but there's not thanks button for archived posts. :(

---

