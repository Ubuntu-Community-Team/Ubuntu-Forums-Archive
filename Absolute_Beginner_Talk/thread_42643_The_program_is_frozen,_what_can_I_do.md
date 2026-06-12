---
title: "The program is frozen, what can I do?"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by leohart on 2005-06-18
Hi guys,

In Windows, if a software/process is frozen, I would Ctrl-Alt-Del and hope that the process manager is still responding so that I can force kill/force quit/shut down/end task (whatever) that stupid process is.

I was having some problem playing Nexuiz today. For some reason, the program lost focus (in window mode) so I want to force kill it. I click click and click (try all the combination I can think of including Apple-Q  :-P j/k I am on x86_64).

My question is: if a process is frozen, what are my options?

Thanks in advance guys.

---

### Post by Xian on 2005-06-18
[QUOTE=leohart]My question is: if a process is frozen, what are my options?
[/QUOTE]
Run the Gnome System Monitor as user (or sudo if the program has admin auth).
Open a terminal and input the following command(s).

Click on the "Process Listing" tab.
Find your application then right-click and choose 'Kill Process'.

```
$ gnome-system monitor
```
or
```
$ sudo gnome-system-monitor
```

---

### Post by Declan on 2005-06-18
There's a thread on this here, with many options outlined.  The title is "task manager".  Have a read of that.

---

### Post by poofyhairguy on 2005-06-18
[QUOTE=leohart]
My question is: if a process is frozen, what are my options?[/QUOTE]

I have a great answer for that. My Java programs crash and hang a lot.

My favorite option is force quit. To get that, right click on your top panel, select "add to panel" and then click on the one that says "force quit." 

To use it:

Click the force quit icon. You will get some crosshairs, use those to click on the program that is hagging. Be sure NOT to click on a minimized program in the bottom bar because the bottom bar is its own program (that shows what other programs are running) and clicking on it will kill your panels!!! So just click the maximized crashing window instead.

If that doesn't work (always has for me), or if you need to kill something that is minimized and won't maximize then run this command:

> killall appthatcrashed

---

