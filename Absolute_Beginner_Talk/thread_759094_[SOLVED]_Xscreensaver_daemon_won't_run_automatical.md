---
title: "[SOLVED] Xscreensaver daemon won't run automatically"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Raazka on 2008-04-18
I installed xscreensaver to replace my gnome-screensaver, but the xscreensaver daemon won't start when I boot the computer. To start the daemon, I have to open xscreensaver-demo, which shows me a notification that the daemon isn't currently running and offers me the option to start it. 

I'm running Gutsy, and I've already tried adding an entry to my System>Preferences>Sessions>Startup Programs list. I'm using the command "xscreensaver -nosplash", but the daemon still won't start automatically. 

Thanks,
Raazka

---

### Post by quirks on 2008-04-18
1. Have you tried starting it while Gnome is already running (i.e., not during login as an autostart program)?
2. Have you tried launching it without the -no-splash option? Again, maybe it works when Gnome is already running.
3. Are you sure that gnome-screensaver is not running anymore (the two might conflict with one another)?
4. After you put the command in the startup programs list, didn't the process come up at all or was it visible in the System Monitor?

quirks

---

### Post by Raazka on 2008-04-18
I'm not fully sure what you mean by answer #1. I'm very new to Linux :). I would guess that I've never ran xscreensaver without Gnome, but I don't know how to tell. I also don't know how to start the daemon without autostart, other than by manually turning it on with the option xscreensaver-demo gives me.

I tried #2 and restarted, but nothing happened. I didn't see a splash screen at the startup, either.

For #3, I can't find the gnome-screensaver on my System Monitor.

The process xscreensaver-nosplash was visible in my System Monitor, but only after I manually started the daemon with xscreensaver-demo.

---

### Post by quirks on 2008-04-19
This is what I meant by question #1:

1. Login to your computer and wait until everything has finished loading.
2. Open a terminal: go to Applications -> Accessories -> Terminal
3. In the terminal type
```
xscreensaver -no-splash
```
4. Check if the deamon starts successfully (you should be able to lock your screen). If it doesn't, paste any output produced by the command here.

I just had a look at my Xubuntu installation (which uses xscreensaver, too), and the xscreensaver -no-splash command seems to be correct.

quirks

---

### Post by Raazka on 2008-04-19
The daemon did start when I entered "xscreensaver -no-splash" in the terminal. Maybe it's just the command -nosplash that was wrong; I'll try editing the command in my startup programs and logging in again.

Thanks for helping me out!

---

### Post by Raazka on 2008-04-19
I logged out and logged in again, but when I did, the daemon again didn't start on its own, even though I edited the code in the startup menu.

---

### Post by quirks on 2008-04-19
Looks like **during **logon, xscreensaver cannot start for some reason which is not given **after **you have logged on.

Try the following:

1. Create a text file named **xscreensaver.sh** on your Desktop and write the following into it:
```
#!/bin/bash
/usr/bin/xscreensaver -no-splash > /home/*your_username*/Desktop/xscreensaver_output.txt 2>&1
```
Make sure to replace *your_username* with your Ubuntu username.

2. Right-click the file and select **Properties**. Switch to the **Permissions** tab and check **Allow executing file as program**. Close the window.

3. Test the little script: open a terminal and enter this command:
```
~/Desktop/xscreensaver.sh
```
xscreensaver should start now. Also, you should see a new text file named **xscreensaver_output.txt** on your Desktop. If neither of the two is true, then make sure you performed the previous steps correctly, or ask me for help.

4. Delete the file **xscreensaver_output.txt** from your Desktop.

5. Add the following program to your startup programs list (System>Preferences>Sessions>Startup Programs):
> /home/*your_username*/Desktop/xscreensaver.sh
Again replace *your_username* with your username.

6. Log out and log in again.

7. On your Desktop should be a file called **xscreensaver_output.txt** now. If it isn't, the command for starting xscreensaver was never invoked during logon. If there is a file, open it and paste the content in this thread. It possibly contains some valuable error information.

quirks

---

### Post by Raazka on 2008-04-19
Yay! the daemon started when I logged in!

The file "xscreensaver_output.txt' says this: 
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  348
  Current serial number in output stream:  378
checkbox "nogui" on
radio "out9"
radio "X11"
xscreensaver: 12:36:36: 0: child pid 6946 (xaos) exited abnormally (code 1).
xscreensaver: 12:37:11: WARNING: 1 failed attempt to unlock the screen.
xscreensaver: 12:37:13: 0: unrecognised ClientMessage "_NET_CLOSE_WINDOW" received
xscreensaver: 12:37:13: 0: for window 0x1600021 (gnome-terminal / Gnome-terminal)
xscreensaver: 12:37:22: 0: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 12:37:22: 0: for window 0x1600239 (gecko / Firefox-bin)
xscreensaver: 12:37:36: 0: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 12:37:36: 0: for window 0x160013a (gecko / Firefox-bin)
xscreensaver: 12:37:44: 0: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 12:37:44: 0: for window 0x3400081 (gedit / Gedit)
xscreensaver: 12:37:47: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:37:47: 0: for window 0x160013a (gecko / Firefox-bin)
xscreensaver: 12:38:26: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:26: 0: for window 0x3400081 (gedit / Gedit)
xscreensaver: 12:38:37: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:37: 0: for window 0x1600239 (gecko / Firefox-bin)
xscreensaver: 12:38:38: 0: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 12:38:38: 0: for window 0x1600239 (gecko / Firefox-bin)
xscreensaver: 12:38:39: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:39: 0: for window 0x160013a (gecko / Firefox-bin)
xscreensaver: 12:38:45: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:45: 0: for window 0x3400081 (gedit / Gedit)
xscreensaver: 12:38:46: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:46: 0: for window 0x1600239 (gecko / Firefox-bin)
xscreensaver: 12:38:48: 0: unrecognised ClientMessage "WM_CHANGE_STATE" received
xscreensaver: 12:38:48: 0: for window 0x1600239 (gecko / Firefox-bin)
xscreensaver: 12:38:48: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:38:48: 0: for window 0x160013a (gecko / Firefox-bin)
xscreensaver: 12:39:34: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 12:39:34: 0: for window 0x3400081 (gedit / Gedit)
```

This file's contents also keep changing every few seconds.

Thanks for the help!

---

### Post by quirks on 2008-04-19
I'm glad to hear that! :)

There could be two reasons, why your first attempts didn't work:
1. You have to reference the program to be started by the full path in the startup programs list. So instead of **xscreensaver -no-splash** it should say **/usr/bin/xscreensaver -no-splash**. I would try this out first, because it is easier to correct. So go to your startup programs list and test the change.

If the first solution didn't work, this could be the other reason:
2. You cannot put programs with a command line option (such as **-no-splash**) into the startup programs list ... which is a bit weird, because I could swear, I've already done that.

Nevertheless, this is pretty easy to fix:

1. First of all, kill the xscreensaver process, delete the **xscreensaver.sh** file on your Desktop and the **xscreensaver_output.txt** file as well. We don't need them anymore.

2. Open a text editor as root. In a terminal enter:
```
gksu gedit
```

3. Paste this code into the file:
```
#!/bin/bash
/usr/bin/xscreensaver -no-splash
```

4. Save the file to **/usr/local/bin/xscreensaver.sh**. If the directory does not exist, create it.

5. Run this command in a terminal:
```
sudo chmod 755 /usr/local/bin/xscreensaver.sh
```

6. Make sure, the file works:
```
/usr/local/bin/xscreensaver.sh
```
This should launch xscreensaver. If it doesn't, something went wrong.

7. Add this entry to the startup programs list:
```
/usr/local/bin/xscreensaver.sh
```
You can remove the old command.

8. Log out and log in. Check if it works.

quirks

---

### Post by Raazka on 2008-04-19
Method #1 worked fine, and knowing what is and isn't acceptable in the startup programs list will save me trouble later on. Thanks again for all the help!

---

