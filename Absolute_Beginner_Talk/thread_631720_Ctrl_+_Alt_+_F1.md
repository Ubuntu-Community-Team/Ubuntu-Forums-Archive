---
title: "Ctrl + Alt + F1"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by GodsDead on 2007-12-04
hey there, im getting used to ubuntu here and their now =]
and today i installed a counter strike server Yippie! i havent had time to test it yet, as im about to go off to bed, work in the morning =[ its like 12!

i have a couple of questions, the first is; i am using the desktop version of ubuntu, so therefore its GUI.. this obviously takes up loads more resources..
I accedently found CTRL + ALT + F1 somewhere, and this brings me to the command line.. like in a terminal?
i was wondering, if i run my server like this, will my resources go down and give better performance?
or is the desktop environment running in the background?



Also, can someone link me to a good place on how to install vent onto the server too?
I will be installing HLStatsX Tomorrow.. aswell.. so i can kill two birds with one stone! and maybe get some CS:S gaming on!


Thanks!
:guitar:

---

### Post by PeterJS on 2007-12-04
> **GodsDead said:**
> 
i have a couple of questions, the first is; i am using the desktop version of ubuntu, so therefore its GUI.. this obviously takes up loads more resources..
I accedently found CTRL + ALT + F1 somewhere, and this brings me to the command line.. like in a terminal?

That is actually the first physical terminal, of which the desktop terminals are just an emulation of.
F1-F6 are the physical terminals you can login on.
F7 & F8 have system information on them from booting up.
F9 has the desktop on it.
F10-F12 don't have anything on them on Ubuntu. On some systems F12 contains system messages.
> 
i was wondering, if i run my server like this, will my resources go down and give better performance?
Yes, running the server from the physical terminal will get you slightly better performance as you won't have the mem usage from the desktop environment.  BUT! see below.
> 
or is the desktop environment running in the background?
Just switching to the physical terminal won't kill your desktop session. To do that you will have to first stop the display manager (GDM) with:
```

sudo killall gdm

```and then press ctrl+alt+backspace to end your desktop session. Note if you do this you won't be able to log back in to a graphical desktop with out restarting gdm as follows:
```

sudo /etc/init.d/gdm start

```and then switching back to terminal 9 and log in again.

EDIT:

X is still on vt7? I could have sworn it was moved to vt9. I'd check but my system is dead, I can't wait to escape this win box :(.

---

### Post by finer recliner on 2007-12-04
ctrl + alt + f1 is called tty1 and is pretty much just a terminal as you guessed. this terminal is always running. theres one for each f# key that you may use.

f7 is reserved for the GUI. so yes, when you accidentally switched to tty1, your GUI was still running the background

---

### Post by The Cog on 2007-12-04
Like the others say, Ctrl-Alt-F1 to Ctrl-Alt-F6 give you 6 text mode terminals. Ctrl-Alt-F7 gives you the GUI again (if you switch users in the GUI, the second GUI goes on Ctrl-Alt-F9).
The GUI remains using memory resources while you switch to the text consoles. You can always kill the GUI off with this command:
**sudo /etc/init.d/gdm stop**
and restart it later when needed with:
**sudo /etc/init.d/gdm start**

Killing the GUI will kill any programs that were running in it in a very ungraceful way, so it is best to log out of the GUI first.

Incidentally, you can start the GUI from the console with the command **startx** if you like, rather than launching gdm (the gnome desktop manager). You can launch a second GUI from a second console with 
**startx -- :1**
but I recommend not launching as the same user id in case they fight over locks and configuration.

---

### Post by ekravche on 2007-12-09
> **The Cog said:**
> Like the others say, Ctrl-Alt-F1 to Ctrl-Alt-F6 give you 6 text mode terminals. Ctrl-Alt-F7 gives you the GUI again (if you switch users in the GUI, the second GUI goes on Ctrl-Alt-F9).
The GUI remains using memory resources while you switch to the text consoles. You can always kill the GUI off with this command:
**sudo /etc/init.d/gdm stop**
and restart it later when needed with:
**sudo /etc/init.d/gdm start**

Killing the GUI will kill any programs that were running in it in a very ungraceful way, so it is best to log out of the GUI first.

Incidentally, you can start the GUI from the console with the command **startx** if you like, rather than launching gdm (the gnome desktop manager). You can launch a second GUI from a second console with 
**startx -- :1**
but I recommend not launching as the same user id in case they fight over locks and configuration.

I'll give this a try
**startx -- :1**

---

### Post by kvorion on 2007-12-09
I noticed that the Ctrl Alt Fx does not work on my Vmware Xubuntu virtual machine. I dont know why that is. Is there some constraint because its a virtual machine?

---

### Post by PeterJS on 2007-12-10
> **PeterJS said:**
> 
X is still on vt7? I could have sworn it was moved to vt9. I'd check but my system is dead, I can't wait to escape this win box :(.

So I did just check, I've got physical terminals on 1-6, dmesg on 7, init messages on 8, and X on 9.

See, I knew I wasn't crazy.

---

### Post by v.alari on 2007-12-10
sure you are Peter, you madder than the hatter:)

---

### Post by GodsDead on 2007-12-13
WOW, cheers so much guys =]
Ausom!
will this run, say at the same speed, as if i installed the server package of ubuntu? or am i totally in teh wrong league LOL

i like haveing the security of a GUI at the end of the day =p!

there was another question i was goign to ask, but i forgot =[ it'll come back 

cheers =]

---

