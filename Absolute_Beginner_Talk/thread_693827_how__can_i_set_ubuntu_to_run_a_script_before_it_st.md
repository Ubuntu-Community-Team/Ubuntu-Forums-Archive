---
title: "how  can i set ubuntu to run a script before it starts?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by ntrgc89 on 2008-02-11
After splitting my head open trying to set-up the external monitor on my laptop I finally got it to work, and even have compiz running on it.

My problem is that the settings I have active right now have to be redone everytime I reboot ubuntu. Not a big deal, as it's just a few lines in the terminal, but I'd rather it be done automatically, is that possible?

Here's how it launches:
Display active on the laptop internal LCD at 1024x768 and on external monitor at 1280x1024. The display of the internal LCD is cloned onto the external.

Here's what I do to set it up:
xrandr --output VGA-0 --off (Turn off external)
Manually activate compiz through System ->preferences ->appearance (although I suppose typing compiz in the terminal would also work)
xrandr --output VGA-0 --auto (turn external back on, note that the internal has been on throughout)
xrandr --output LVDS --off (turn off internal)

So is there any way to get the system to do this right as the Xserver is starting? Thanks in advance.

---

### Post by gerscht on 2008-02-11
Have you tried adding it in
"System => Preferences => Session"
?

---

### Post by mbhardwaj on 2008-02-11
I had a similar issue ,
used the following script available here,

> [http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

you could try something on this line,

I am new to ubuntu as well so am not sure if this is what you wanted...
tc..

---

### Post by amvella on 2008-02-11
> **gerscht said:**
> Have you tried adding it in
"System => Preferences => Session"
?
Yea this should work. just make a script and add it to the start up manager.:guitar:

---

### Post by ntrgc89 on 2008-02-11
tried adding the following in system -> preferences -> sessions

Name: xrandr
Command: --output VGA-0 --off
Comment: Step 1: Turn off the external monitor

I restarted the X-server and everything booted up the way it normally does, adding the command seems to have changed nothing.

mbhardwaj: I'm running an ATI mobility radeon 7500 so that script doesn't work for me, but I am looking for something in that vein.

Also, instead of manually starting compiz from the appearances menu, I tried to start it from terminal, but it produces funky results (read: the title bar of applications is no longer there so I can't move them and the only way to close or minimize is to right click them on taskbar)

In any case, thanks for your quick replies, any more ideas?

---

### Post by ntrgc89 on 2008-02-11
also, forgot to mention, after typing compiz in the terminal, it started and kept running, so the only way to get to the next step is to press control+c, which, of course, stops compiz. I worked around that by launching another terminal, but how would I do something like that in the script?

Compiz must be activated while the external monitor is off, otherwise it won't work

gerscht and amvella: could you please be a little more specific in terms of exactly how one would go about creating a script? Thanks.

---

### Post by bump_ on 2008-02-11
It would probably be better to put them all in a script to run through Sessions rather than each command individually. Just open up gedit and put your 4 commands like this

Note: I replaced the second command with the command i think you need:

```
xrandr --output VGA-0 --off
compiz --replace &
xrandr --output VGA-0 --auto
xrandr --output LVDS --off

```

Save it with any name and make it executable like this:
```
sudo chmod 766 nameOfScript
```

Then you can add this script to Sessions.

---

### Post by Ptero-4 on 2008-02-11
I think that after the "compiz --replace &" he might need a "gtk-window-decorator --replace &" or "emerald --replace &" instruction followed by the last two "xrandr" instructions from the script.

---

### Post by fmartinez on 2008-02-11
you can also create a script and put in the /etc/rc.d directory and run the update-rc.d command to add that script the the start up files.... dont quote me on the command i cant verify then now.... you can view the man page for rc.d those are the startup in Linux....

---

### Post by ntrgc89 on 2008-02-11
OK, so I created the script like bump_ suggested, and it worked but it didn't work.

The monitor sequence was flawless, but it couldn't activate Compiz, I'm guessing it just didn't have enough time to. Also, when I tried going backwards and then forwards again to activate compiz, the title bars disappeared again.

Would adding "gtk-window-decorator --replace &" to the script fix this? What is that line supposed to do?

Again, thanks for the lovely responses!

---

### Post by ntrgc89 on 2008-02-11
A little more detail gained through these forays:

The last line of the output of compiz --replace & is 'Starting gtk-window-decorator'

After that the terminal just hangs. Compiz is working, as I tested it out by moving the terminal window around and there was the expected wobble effect, but the title bar was inactive, even after I tried clicking on it.

One more discovery, the internal LCD MUST be on when turning the external back on, otherwise the monitor displays an error message: "Not optimal mode [even though the command is auto] Recommended..blahblahblah"

Also, I'm a little concerned for my monitors, all this turning on and off, is that bad for them? If so, how bad?

---

### Post by bump_ on 2008-02-11
Try addding

> gtk-window-decorator --replace &

to the script right after compiz --replace and before the last 2 commands. I'm not sure if compiz will start the window decorator on its own and by the sounds of it, it doesn't. This line shoudl ensure you get your title bar and such

---

### Post by ntrgc89 on 2008-02-11
tried that; it got the title bars back but still no compiz. it may sound silly, all this effort to get compiz to run but I feel like that's one of ubuntu's main features when compared to windows and it really shouldn't be this hard.

Maybe we should try another command to launch compiz?

By the way, as I mentioned in an earlier post, the last line of the compiz output (when performing these operations manually) is "starting gtk-windows decorator"

---

