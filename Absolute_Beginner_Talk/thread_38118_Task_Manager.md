---
title: "Task Manager"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by wirjo on 2005-05-30
Hi,

I'm a complete n00b at Ubuntu and Linux in general. It has been crashing quite a lot lately, sometimes because of XMMS and going to [http://del.icio.us/](http://del.icio.us/) also crashes it somehow. Is there a way I can open up Task Manager to kill processes like in Windows (by Ctrl+Alt+Del) or something? 

Thanks.

---

### Post by benplaut on 2005-05-30
[QUOTE=wirjo]Hi,

I'm a complete n00b at Ubuntu and Linux in general. It has been crashing quite a lot lately, sometimes because of XMMS and going to [http://del.icio.us/](http://del.icio.us/) also crashes it somehow. Is there a way I can open up Task Manager to kill processes like in Windows (by Ctrl+Alt+Del) or something? 

Thanks.[/QUOTE]

in the terminal, type:

gnome-system-moniter

and make an icon link to it, if you want  ;-)

---

### Post by ltmon on 2005-05-30
I find a good way is to run the command 'xkill' from a terminal, and then clicking on the window of the process you wish to kill.

L.

---

### Post by Declan on 2005-05-30
Another idea could be to go to one of your panels, above or below, right click (or whatever it is) and pick add applet: "system monitor".  This applet will monitor your cpu, memory, swap space, network etc. use.  You can choose which of these you are interested in monitoring. 
Anyway, once you have that applet showing, you can go and click on the monitor at any time and up will pop your "task manager".  In Gnome it's called System Monitor, and it has two views - "Resources" and "Processes".  It is the "Processes" view that you are interested in.  It tells you all the processes that are running, and their process id numbers.  You can stop any process from there.

Or, and this is what I do, you can go to a terminal, type "top" (= table of processes) and it tells you what's going on.  If the misbehaving process is firefox (that's the one that misbehaves for me), you press the letter "k" (= kill) and the number beside firefox.  

Or, as has been suggested, xkill.  In order to summon up xkill, I press ALT + F2, which gives me a little window from which I can launch a program by name.  Then I type "xkill" and the cursor changes into a funny kind of x.  With the mouse you bring that to the window of the program you want to kill and click.

In all of these cases the result is highly satisfying.  Whatever you want to stop is instantly stopped.  No hesitation.  I never figured out how to do that with Windows.  I would open the task manager, press "stop" or "end" or whatever.  But the thing (usually Outlook) would refuse to stop.  Or it would take ages.

In linux the thing is instantaneous.  It still brings a smile.

---

### Post by Whistler on 2005-05-30
or use command line:

open a console and type:
$ su
Password: <type password>
# ps -A
... will list all the programs running, and then:
# kill <pid number>

---

### Post by op3studios on 2005-05-31
I've got the problem with xmms...it just keeps going and going.....

tried all of the above can't get it to stop.  The program window goes away but the song plays on.   Can't reboot at the moment.

I guess when I do I'll be looking for another media player.  I miss my winamp ](*,) 
But as soon as I get this canon i550 printer working or get another printer, I'll be on this side of the hard drive for sure.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=op3studios]I've got the problem with xmms...it just keeps going and going.....

tried all of the above can't get it to stop.  The program window goes away but the song plays on.   Can't reboot at the moment.

I guess when I do I'll be looking for another media player.  I miss my winamp ](*,) 
But as soon as I get this canon i550 printer working or get another printer, I'll be on this side of the hard drive for sure.[/QUOTE]

Also try adding the "force quit" applet to your Gnome panel. I use it a lot for Firefox (when it gets crashy) and Java apps.

---

### Post by jdong on 2005-05-31
try a **killall -9 xmms** , which is a violent way of destroying XMMS, equivalent to NT's End Process option.

---

