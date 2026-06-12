---
title: "Switch workspace from script"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by joddbeem on 2007-10-17
Hi guys

Is there a command in bash that I can use to switch to one of the workspaces(I got 4), just plain gnome, no Beryl etc.

I would like to make a little script, that could switch back to workspace1 each ten minutes or so.

---

I am having some troubles with VMWare, suddenly when switching to full-screen mode, it freezes and I am not able to get back to gnome/linux. I am stuck there, if radio or music is played, I can hear Ubuntu running just fine in the background, I just can't get there somehow, as all keystrokes or mouse input is not working. The only thing left is to turn of computer.

If I was forced back to Workspace1 each ten minutes, I could do some research on whats going on when it happens again,.

---

### Post by kidders on 2007-10-18
Hi there,

I wouldn't be posting this if your thread wasn't over a day old (because it doesn't really answer your question), but KDE can do what you describe. I have no doubt that Gnome can be *made* to do it, but KDE's "dcop" infrastructure makes this sort of interaction with the graphical environment trivial, out of the box.

Since you'd have to switch to KDE to make any use of that suggestion (!!), I've spent a moment considering your problem in more detail. Do you suppose it would be possible to identify vmware's unresponsiveness somehow?

I'm thinking along the lines of "watchdog" services, that try to monitor systems for lock-ups & automatically reboot them. If, for instance, your vmware problems were associated with some sort of unusual activity, it should be possible to have your system kill it. For example:
[LIST]
[*]Perhaps vmware eats up 99.9% of your CPU when it goes funny. You could write a script to kill the process, if it stays like that for more than 15 or 20 seconds.
[*]Maybe it gets locked in an I/O loop. Applications that spend a lot of time reading & writing very large amounts of data to your hard disks can make Linux appear unresponsive. Something like this could also be detected & stopped.
[*]Could it be that your vmware problems trigger certain error messages in your system logs?
[/LIST]

As one final suggestion, assuming you don't have more than one computer, you could have a friend SSH into your box to investigate your problem, the next time it arises. I realise this is reaching a bit (to say the least), but I'm trying my best to offer you something more than "Switch to KDE". I figured a one-liner like that would be rather mean hehe!

---

### Post by jimbren on 2007-10-18
Along the lines of kidders' final recommendation, have you tried switching to a console when VMware locks up the system?  If you could use CTRL+ALT+F1 to get to a prompt, you might be able to find something in the logs or by taking a look at the running processes. 

Just a thought.  Might be a little simpler than switching to KDE.  Although it is far superior to gnome.  :)

jimbo.

---

### Post by kidders on 2007-10-18
> **jimbren said:**
> Might be a little simpler than switching to KDE.  Although it is far superior to gnome.  :)Uh oh... I smell a religious war lol!

I was making the (possibly invalid) assumption that your vmware is intercepting keystrokes like CTRL+ALT+F1, or that your system simply becomes too unstable for them to work properly. Since Jimbren disagrees with me on that one (and may well be right), it might be worth suggesting CTRL+ALT+Backspace as an alternative to turning off your PC ... it's at least worth a try, since it would keep your native environment (but not the virtualised one) safe from corruption.

---

### Post by joddbeem on 2007-10-18
Hi there, thx for response.

My computer is not responding when it happens, so no shortcuts can do it.

I considered a timing kill of vmware, but since that both are quite drastic and I didn't know how in the first place, I took my chance asking :D.

I doubt however that it occupies the CPU since music plays without trouble in the background.

I guess I can figure out a script, but then...

I just updated ubuntu, then I discovered that I had the "old" vmware, 1.0.3, so I of course did an update to the .4 . I have not any idea if this is now fixed, I just have to play around not working seriously for a while I guess, to see if it still happens. 

To gnome or not to gnome, vmware gives me an excelent testing ground, so I guess I can check the Kubuntu as well - still a newbie so theres no really bounds. If me likes, me switch :D

---And yes, next time I check if updated first :(

---

### Post by mali2297 on 2007-10-18
> **joddbeem said:**
> 
Is there a command in bash that I can use to switch to one of the workspaces(I got 4), just plain gnome, no Beryl etc.


For this, you can use **wmctrl**. Install it from the repositories (with apt-get or Synaptic). Then you can switch desktop with the command
```

wmctrl -s <DESK>

```
where <DESK> should be the desktop number 0,1,2 or 3.

---

