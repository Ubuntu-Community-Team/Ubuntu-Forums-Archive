---
title: "ctrl + alt + del equivalent?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by mollyhardin on 2007-12-18
Hi there,

I have a couple of random windows that keep poping up and blocking my apps...I suspect it is part of a bug that somehow still remained on my laptop after I switched from Windows to Ubuntu - and installed Wine.

How can I see what apps and what processes are running?

Cheers,

M

---

### Post by beow on 2007-12-18
Install the System Monitor applet. "Open System Monitor" will give you a list of processes.

---

### Post by x-to-tha-t on 2007-12-18
if you open a terminal and use the command
```
top
```
it will show you every process running on the system.

---

### Post by daimaru on 2007-12-18
system->admin->system monitor
or
```
top
ps aux
```

and as to your heading ctrl+alt+backspace

---

### Post by SegaFan on 2007-12-18
Edit, already been answered, I was too slow.

---

### Post by stchman on 2007-12-18
> **mollyhardin said:**
> Hi there,

I have a couple of random windows that keep poping up and blocking my apps...I suspect it is part of a bug that somehow still remained on my laptop after I switched from Windows to Ubuntu - and installed Wine.

How can I see what apps and what processes are running?

Cheers,

M

I believe it is System--->Administration--->System Monitor

From there you can see what is running and you can end the process.

---

### Post by Majorix on 2007-12-18
System Monitor does NOT show all the running processes, I don't know whose idea it was. I use htop instead, found in the repos.

---

### Post by exactopposite on 2007-12-18
> **Majorix said:**
> System Monitor does NOT show all the running processes, I don't know whose idea it was. I use htop instead, found in the repos.

in system monitor click view, and check off "all processes"

---

### Post by Niniel on 2007-12-18
System monitor is great.
I put that in my lower taskbar, so not only does it look nice, I can also just click on it. Couldn't be easier. :)

---

### Post by Joeb454 on 2007-12-18
Whoever said Ctrl+Alt+Backspace is kind of right, but that restarts X (the display manager)

While this helps if all else fails, it's not good if you just want to force quit something

---

### Post by XFocus on 2007-12-18
I still have yet to find an ALT+CTRL+DEL equivalent.  All of these suggestions are assuming that the GUI is responsive.  There are instances when clicking on the System Monitor icon does nothing, and the Force Quit icon does the same.  In windows, regardless of your opinion of it, 99% of the time ALT+CTRL+DEL will get you to the task manager and you'll be able to take care of stuff from there.  

I've been seeing in Ubuntu that there are instances when even ALT+F2 won't respond.  There has to be a more elegant solution.  I've read so much about Linux trumping Windows when it comes to stability but I have yet to find a way to control my rogue programs, leading me to reboot 10x as much as I used to in Windows.  Usually I'm forced to ALT+CTRL+Backspace or even ALT+SysRq+REISUB.  

Am I missing something?

---

### Post by petteriIII on 2007-12-19
The 'equivalent' for CTRL-ALT-DEL is ALT-SysRg-b; but it is rather harsh. Actually you ought use six combinations, one after another:
ALT-SysRg-r
ALT-SysRg-s
ALT-SysRg-e
ALT-SysRg-i
ALT-SysRg-u
ALT-SysRg-b

---

### Post by XFocus on 2007-12-19
No no no no....ALT+SysRq+RSEIUB/REISUB only restarts the computer and that's not what I want at all.  You hardly (if ever) need to reboot your PC in windows.  Usually you can ALT+CTRL+DEL and end task to maintain state and not lose your work.

ALT+SysRq+RSEIUB/REISUB, while safely rebooting your PC, will lose all of your work.  This is unacceptable for me coming from a PC where I rarely, if ever, lost my work to a reboot.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
> **XFocus said:**
> I still have yet to find an ALT+CTRL+DEL equivalent.  All of these suggestions are assuming that the GUI is responsive.  There are instances when clicking on the System Monitor icon does nothing, and the Force Quit icon does the same.  In windows, regardless of your opinion of it, 99% of the time ALT+CTRL+DEL will get you to the task manager and you'll be able to take care of stuff from there.  

I've been seeing in Ubuntu that there are instances when even ALT+F2 won't respond.  There has to be a more elegant solution.  I've read so much about Linux trumping Windows when it comes to stability but I have yet to find a way to control my rogue programs, leading me to reboot 10x as much as I used to in Windows.  Usually I'm forced to ALT+CTRL+Backspace or even ALT+SysRq+REISUB.  

Am I missing something?

To XFocus

skip down to ******* for solution if you dont wanna hear my convincing storry
you know how you said in windows you could 99% of the time kill the program with ctrl-alt-del
well right now your in the .001% of the time linux screws up and it's not really its falt any way
if the computer hangs like that there is something wrong with your install or it may not like all of your hardware
The only time I have ever had the problem you discribed was when i upgraded from 6.06 to 7.04
on my desktop 
see in 6.06 my wireless card was not reconized my computer egnored it i didn't care i have ethernet port everything ran fine 
then i upgraded 
system reconizes my wireless card installed falty driver woppsies and randomly hangs system lockup complytly just like you discribed
when i upgraded to 7.10 i happend to reinstall the card just to see and well works flawlessly

***************************************
next time this happens i would like you do this
first note the time it happend at important for later
second reboot safly
ALT-SysRg-r
ALT-SysRg-s
ALT-SysRg-e
ALT-SysRg-i
ALT-SysRg-u
ALT-SysRg-b

after ubuntu boots all the way back up

goto 
System > Administration > System log
there are a few logs in here but i think its in the System log we would like to look 
maybe i will find my thread from before to link you to it if i can find it
at the bodom of the log there should be crap about system startup
scroll up to the time were the system crashed 
now there shoud be wired messages that just dont look right google them and see whats up 
also post the log here and we will have a look at it
Linux is more stable with out a dout just not when stuff you put in it is not

---

### Post by Majorix on 2007-12-19
> **exactopposite said:**
> in system monitor click view, and check off "all processes"

Whoa I didn't know about that. Thanks a lot for pointing it out :)

---

### Post by weblordpepe on 2007-12-19
Ladies & gentlemen, the magic command you are looking for is **xkill**. It turns your mouse pointer to a skull & crossbones and will kill the first application you click with the left button. Right-button cancells.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
> **weblordpepe said:**
> Ladies & gentlemen, the magic command you are looking for is **xkill**. It turns your mouse pointer to a skull & crossbones and will kill the first application you click with the left button. Right-button cancells.

ya but what do you do when mousy not working
oh and the keybord will not respond
and system wide freez up 
that was the problem i was haveing when i ran 7.04 with my wireless card in there

---

### Post by XFocus on 2007-12-19
@ <<joe>>

I <3 U

Thanks for taking the time to explain it.  I'm going on vacation but I'll post my logs as soon as my pc crashes again.

---

### Post by weblordpepe on 2007-12-20
> **<<joe>> said:**
> ya but what do you do when mousy not working
oh and the keybord will not respond
and system wide freez up 
that was the problem i was haveing when i ran 7.04 with my wireless card in thereIf the keyboard won't respond, then no key combination will work.

Same thing in Windows, - if the keyboard locks up (and it does) then ctrl-alt-delete does nothing. I don't think you're going to find an answer to your question beyond the ones you've already gotten.

---

### Post by natehall on 2007-12-20
Don't know why but I had a start up that froze up so bad it even ignored the off button. Of course this happened when I was showing off Ubuntu to someone. It hasn't happen since, ( It was a laptop so I had to yank out the battery!)

---

### Post by GSF1200S on 2007-12-20
> **Majorix said:**
> System Monitor does NOT show all the running processes, I don't know whose idea it was. I use htop instead, found in the repos.

+1 for htop.

sudo apt-get install htop

then just open a terminal and type 

htop

and youll have an idea of every process. You can sort by memory, cpu usage, etc..

---

### Post by exactopposite on 2007-12-20
> **Majorix said:**
> Whoa I didn't know about that. Thanks a lot for pointing it out :)

glad u could help

---

### Post by tech9 on 2007-12-20
> **stchman said:**
> I believe it is System--->Administration--->System Monitor

From there you can see what is running and you can end the process.

+1

---

### Post by TheLions on 2007-12-20
> **weblordpepe said:**
> Ladies & gentlemen, the magic command you are looking for is **xkill**. It turns your mouse pointer to a skull & crossbones and will kill the first application you click with the left button. Right-button cancells.

awesome!!! 10x!

---

