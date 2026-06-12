---
title: "Copying and pasting"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by 1337sithlord on 2006-03-03
Ubuntu remembers what ive copied and pasted for less than 5 minutes.  Its not like it takes up much space, its just a URL.  Is there any control for the duration of this memory?  Thx

---

### Post by Pragmatist on 2006-03-03
What exactly happens?  Are you using right-click and selecting cut and then do the same for paste?  Are you highlighting and then using the middle mouse-button?  What are you doing in between pasting the first time and trying to paste more than 5 minutes later?  Is this cutting and pasting problem independent of whatever application you are running?

---

### Post by aysiu on 2006-03-03
If you copy, close the application, and then try to paste it, your "copy" will be gone.

Copied text is kept on the clipboard only as long as the application it's copied from is open.

---

### Post by rfruth on 2006-03-03
aysiu hit the nail on the head, so the work a round is to leave the app you copied from running (it can be minimised) :rolleyes:

---

### Post by Pragmatist on 2006-03-03
clipboard!  That is what its called.  Thanks aysiu!  Check out: **xclipboard** If you use that program, I don't think you have to worry about switching between applications. **man xclipboard** will explain more.

---

### Post by 1337sithlord on 2006-03-03
Oh thanks, thats it.  I was opening firefox, copying whats in the address bar (i tried all methods) and pasting it to my friends in gaim.

---

### Post by towsonu2003 on 2006-03-04
i've xclipboard installed (never installed it myself, so i guess it was pre-installed w OS) but it doesn't help (same problem). I tried running it with ```
xclipboard
``` but it says it is already running. ps aux does not list xclipboard. any ideas?

---

### Post by Pragmatist on 2006-03-04
Thats weird.  I can just type ```
xclipboard
``` and I get a small window that lets me type text in it.  Then I can just right click and paste in an application.

I would try ```
ps -ef | grep xclipboard
``` and then kill the process and restart by typing xclipboard in a terminal.  If that didn't work, I would install and reinstall it in synaptic.

---

### Post by towsonu2003 on 2006-03-06
I'll try this and report back...

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=Pragmatist]If that didn't work, I would install and reinstall it in synaptic.[/QUOTE]
removing it uninstalls a bunch of important stuff... dpkg-reconfigure didn't help. time for a bug report? i should post a new thread first (after waiting for other ideas here).

---

### Post by Pragmatist on 2006-03-06
For the moment, just a couple of details.  What happens if you run xclipboard as root?  What is the output of ```
echo $DISPLAY
```

Why do you need to run xclipboard?  Are you having the same problem as the OP:
> Ubuntu remembers what ive copied and pasted for less than 5 minutes.  In that case, can you give us a test case.  For example, "I'm running firefox and I copy a url and want to paste it into oowriter and it holds what I've cut for 6 minutes and then what I've cut is no longer there." etc...

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=Pragmatist]For the moment, just a couple of details.  What happens if you run xclipboard as root?  What is the output of ```
echo $DISPLAY
```
[/quote]
output is :0.0 
running as root gives the same error (xclipboard is already running).
[quote=Pragmatist]
Why do you need to run xclipboard?  Are you having the same problem as the OP
  In that case, can you give us a test case.[/QUOTE]
My test case would be simple. open up terminal, type uname -r, copy output, close terminal, try pasting to firefox. it won't (in my system). I think xclipboard's function is this: copy clipboard to ram until limit is reached or user clears the saved info, regardless of the open/close status of the application one just copied the text from.

---

### Post by Pragmatist on 2006-03-06
> open up terminal, type uname -r, copy output, close terminal
I just tried this and I also couldn't paste.  xclipboard is however running.  Have you tried opening a terminal, typing uname -r, copying the output, leave the terminal open, and then paste into firefox??

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=Pragmatist]I just tried this and I also couldn't paste.  xclipboard is however running.  Have you tried opening a terminal, typing uname -r, copying the output, leave the terminal open, and then paste into firefox??[/QUOTE]
That should already work without xclipboard? not sure but man page says:
[quote=man page]
 The  xclipboard  program is used to collect and display text selections that are sent to the CLIPBOARD by other clients.  It is typically  used to  save  CLIPBOARD selections for **later** use.[/quote] (emphasis mine)

---

### Post by Pragmatist on 2006-03-06
Now I'm confusing myself! :???: 
Your right, the key problem here is to be able to cut from one application, close that application and paste to another.  A persistent cut/paste buffer.  Just to see, I ran xclipboard in one terminal and then tried it simultaneously in the other.  The exact error message I get is: 
> Error: another clipboard is already running


One serious troubleshooting attempt, just to see if xclipboard works, is this:
1. switch virtual terminals, for example ```
CTRL-ALT-F3
```
2. stop gdm and X ```
/etc/init.d/gdm stop
```
3. switch back to vt3 if necessary ```
CTRL-ALT-F3
```
3. start x with this command: ```
X &
```
4. you'll see a grey hatched background switch VTs ```
CTRL-ALT-F5
```
NOTE: Make sure you make this VT different than the one where you started X
5. run xclipboard: ```
xclipboard -display :0.0
```
6. See if it worked by switching to vt7: ```
CTRL-ALT-F7
```
7. To return to where  you started: 
A. to switch to where you started xclipboard ```
CTRL-ALT-F5
```
B. to kill xclipboard ```
CTRL-C
```
C. to switch to where you started X ```
CTRL-ALT-F3
``` 
D. to kill X ```
CTRL-C
``` 
E. to start gdm and get your login screen ```
/etc/init.d/gdm start
``` 
Instead of using CTRL-C you can go to a different VT and use ps and kill or killall to kill the specific xclipboard and X processes.  In any of these cases you can go back to the VTs and logout of them.  In all of these login as a regular user.

Good luck!  It sounds worse than it is and it really should take more than a few minutes.

---

