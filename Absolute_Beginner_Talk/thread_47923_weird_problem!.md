---
title: "weird problem!"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-10
i'm facing a very weird problem
after a while, my ubuntu is freezing up for no reason, donno why!
first time, it froze when I was entering Gaim
and next time it froze when I entered this forum

I have 256MB ram and GForce2 64MB

what's wrong?

---

### Post by Snitz on 2005-07-10
[QUOTE=Snitz]i'm facing a very weird problem
after a while, my ubuntu is freezing up for no reason, donno why!
first time, it froze when I was entering Gaim
and next time it froze when I entered this forum

I have 256MB ram and GForce2 64MB

what's wrong?[/QUOTE]
 this is getting very annoying
this is the third time my pc freezs up
I donno what's causing it!!!!!!!!!!

---

### Post by Snitz on 2005-07-10
this is driving me insane
ubuntu just keeps on freezing damn it
256MB ram aren't enough?
should I upgrade?
if this is not the prob then what is it?

---

### Post by Knome_fan on 2005-07-10
Hi, adding more ram will not solve your problem.

Of course it's very hard to guess what is happening here, but a lot of people were having problems with the nvidia drivers that are in hoary. I think most of them had RenderAccel enabled in their xorg.conf and disableing it solved the problem.

Also, does the entire computer freeze, or are you still able to change to a console using ctrl+alt+F[1-6]?

---

### Post by Snitz on 2005-07-10
> Of course it's very hard to guess what is happening here, but a lot of people were having problems with the nvidia drivers that are in hoary. I think most of them had RenderAccel enabled in their xorg.conf and disableing it solved the problem.
I didn't quiet understand, how will I be able to fix this prob?

> Also, does the entire computer freeze, or are you still able to change to a console using ctrl+alt+F[1-6]?
everything freezes up, I still can move my cursor but can't click anything..
and sorry it's the first time I know about: ctrk+alt+F[1-6], so I wouldn't know if that's working or not!

---

### Post by cwaldbieser on 2005-07-10
Pressing CTRL+ALT+F1 will take you to virtual console 1.
Pressing CTRL+ALT+F2 will take you to virtual console 2.
Pressing CTRL+ALT+F3 will take you to virtual console 3.
etc...

The virtual consoles are like the MS-DOS window in Windows.  If your desktop keeps freezing, it may be that just the Window manager or GUI is "getting stuck", but the rest of the computer is still running fine.  In this case, you can usually switch to another virtual console to get the desktop to diagnose problems, start a new desktop, etc.

I am not completely familiar with the configuration Knome_fan mentioned, as I do not have an NVidia card, but I have heard there is a program called "nvidia-settings" that you run that lets you configure your NVidia card settings.  In those settings, there is presumably something like the RenderAccel setting previously mentioned, and you could try turning that off.

Of course, this is mostly conjecture on my part, and I may be totally wrong.

---

### Post by Snitz on 2005-07-10
what if I switched to another desktop and it also froze?
and kept switching desktop and all of them froze?
what then?

> you could try turning that off
turn what off?

and where can I find this program on synaptic?

---

### Post by Knome_fan on 2005-07-10
About the nvidia problem:
Many people added the option RenderAccel "true" to their xorg.conf and that caused problems. As you don't know about this option, I don't think this is your problem.

About ctrl+alt+[F1-6]:
Though you don't see it, there is also a text console running while you are in the graphical environment and you can access these console, or rather consoles by pressing ctrl+alt+F1 to F6. (You can change back to the graphical environment by pressing ctrl+alt+F7).
Now if you can still change to a console that would mean that it's not really your computer that is freezing, but the graphical environment, that's why I asked.

Oh, and changing the subject of your post might be a good idea, weird issue doesn't really tell people what kind of problem you are having and someone knowing a solution might overlook your threat.

---

### Post by Snitz on 2005-07-10
[QUOTE=Knome_fan]About the nvidia problem:
Many people added the option RenderAccel "true" to their xorg.conf and that caused problems. As you don't know about this option, I don't think this is your problem.

About ctrl+alt+[F1-6]:
Though you don't see it, there is also a text console running while you are in the graphical environment and you can access these console, or rather consoles by pressing ctrl+alt+F1 to F6. (You can change back to the graphical environment by pressing ctrl+alt+F7).
Now if you can still change to a console that would mean that it's not really your computer that is freezing, but the graphical environment, that's why I asked.

Oh, and changing the subject of your post might be a good idea, weird issue doesn't really tell people what kind of problem you are having and someone knowing a solution might overlook your threat.[/QUOTE]
 let's see:

the problem isnt from the RenderAccel (xorg.conf) becoz I had no idea what this was so it's set to the default

if the problem is from the graphical envirment, then how could I fix it?

and I can't change the title of my post :confused:

---

### Post by Knome_fan on 2005-07-10
[QUOTE=Snitz]let's see:

the problem isnt from the RenderAccel (xorg.conf) becoz I had no idea what this was so it's set to the default
[/quote]
Yep, that's what I wanted to say.

[QUOTE=Snitz]
if the problem is from the graphical envirment, then how could I fix it?[/QUOTE]
Well first you'll have to find out if it realy is such a problem and if it is you can try to find out what the offending program is, or what triggers the problem.

For example you could try to log in and then issue killall nautilus.

---

### Post by Snitz on 2005-07-10
> Well first you'll have to find out if it realy is such a problem and if it is you can try to find out what the offending program is, or what triggers the problem.
sorry, but im a newbie, how could I know what program is triggering the problem?
in winxp, you can simply click Ctrl+Alt+Del and u'll see what prog is consumming the cpu usage and u'll kill it
but what should I do in ubuntu?

> For example you could try to log in and then issue killall nautilus.
killall?
so all my progs will be killed?
u mean when I first login to ubuntu, I issue this command and everything works?

sudo killall nautilus?

---

### Post by Snitz on 2005-07-10
[QUOTE=Snitz]sorry, but im a newbie, how could I know what program is triggering the problem?
in winxp, you can simply click Ctrl+Alt+Del and u'll see what prog is consumming the cpu usage and u'll kill it
but what should I do in ubuntu?


killall?
so all my progs will be killed?
u mean when I first login to ubuntu, I issue this command and everything works?

sudo killall nautilus?[/QUOTE]
 I just switched to ubuntu, opened synaptic and the pc just froze
I was able to move only mouse (usb)
tried to press: ctrl+ alt+f1,2,3.... but nothing happened
so reset my pc and came back to winxp

any suggestions?

---

### Post by cwaldbieser on 2005-07-10
If I search for "nvidia" in synaptic, I see a program called "nvidia-settings".  To run it, you can open up a terminal (a program similar to WinXP cmd.exe) and type "nvidia-settings" and it should run.

---

### Post by cwaldbieser on 2005-07-10
When you first log on, instead of logging into the graphical screen, try doing the CTRL-ALT-F1 then.  When you are in the virtual console, you should be able to just type some commands without locking up.

Try entering this command:

```
$ top
```

It will show you a table that is updated in real time just like the "processes" tab in WinXP task manager.  See if some process is eating up all of your CPU.  Press "q" to quit.

In Ubuntu, there are programs similar to WinXP TaskManager, but from the terminal, the command to stop a runaway program is called "kill".  There is another command called "killall" that is like kill, but it takes the name of the process instead of its process ID.  So if I want to shut down a xine because it has become a runaway process, I could just do:

```
$ sudo killall xine
```

and all instances of the xine process would be stopped.


Hopefully, you will be able to monitor what the problem is so you can correct it.

You say that this was a recent phenomenon, and that Ubuntu had been working fine before.  Did you install any new software or change hardware?  I had a friend whose PC exhibited similar symptoms in WinXP, and after a while, he figured out the heat sink had just come loose from his CPU, so when it got hot, the computer froze up.

---

### Post by Knome_fan on 2005-07-11
Just a thought, but could it be that you only get this problem when you try to access the net?

From what you wrote you had this problem when using gaim, a browser and now synaptic.

So, how do you access the net?

---

### Post by Snitz on 2005-07-11
I went to the ubuntu lookalike taskmanager and I couldn't find anything that's eating up my cpu usage
everything looks fine to me.
so I don't think this is the prob, donno maybe it is, im so lost and confused

I connected to the internet using a broadband connection. and it connects automatically when the pc is on

yesterday late night, I couldn't stay more then 3mins using ubuntu, it just kept freezing so fast
now it's a new day and shutdown my pc yesterday to make it rest, and now im on ubuntu and it's not freezing fastly like it did yesterday
could it be my ram or anything like that?

now what about the "nvidia-settings", could this be the solution?

---

### Post by Knome_fan on 2005-07-11
Just found a pretty good writeup about things you could try:
[http://ubuntuforums.org/showpost.php?p=213121&postcount=31](http://ubuntuforums.org/showpost.php?p=213121&postcount=31)

Maybe one of the suggestions works for you.

Also your problem start to sound like your computer might be overheating. I'm sorry, I don't have any experience with this kind of problem, but you might want to search the forum or google for this issue.

Good luck!  :grin:

---

### Post by Snitz on 2005-07-11
[QUOTE=Knome_fan]Just found a pretty good writeup about things you could try:
[http://ubuntuforums.org/showpost.php?p=213121&postcount=31](http://ubuntuforums.org/showpost.php?p=213121&postcount=31)

Maybe one of the suggestions works for you.

Also your problem start to sound like your computer might be overheating. I'm sorry, I don't have any experience with this kind of problem, but you might want to search the forum or google for this issue.

Good luck!  :grin:[/QUOTE]
 thank you for the suggestion

but smething weird is happening
I woke up this morning, logged on to ubuntu, and opened synaptic for the update... and I left it downloading the packages for hours, I got home few mins ago to find that ubuntu didn't freeze
so, the overheating options is out of the question, no?

---

### Post by Knome_fan on 2005-07-11
[QUOTE=Snitz]thank you for the suggestion

but smething weird is happening
I woke up this morning, logged on to ubuntu, and opened synaptic for the update... and I left it downloading the packages for hours, I got home few mins ago to find that ubuntu didn't freeze
so, the overheating options is out of the question, no?[/QUOTE]

Hm, I think that depends on wether downloading stuff with synaptic really puts that much pressure on the cpu that it would lead to the cpu overheating. I don't think it does, but I don't really know.

As I said unfortunately I don't really know much about overheating issues, but I think the best way would be to just keep an eye on when exactly the problem occurs. If it only occurs after you have used your computer heavily for some time this might be an indication that it's indeed an overheating problem.

---

### Post by Snitz on 2005-07-11
> As I said unfortunately I don't really know much about overheating issues, but I think the best way would be to just keep an eye on when exactly the problem occurs. If it only occurs after you have used your computer heavily for some time this might be an indication that it's indeed an overheating problem.
I left my pc for almost 2 hours with touching, and nothing happened
I came 2 mins ago and started using the pc and opening progs and stuff and after 15mins it froze
this is really werid

---

### Post by Snitz on 2005-07-11
I went to the url u have me
but I couldn't get anything to work
the noapic and nolapic didn't work at the grub, becoz I kept pressing esc and nothing happend

I went to /ect/X11/xorg.conf to add these 2 words at the end, but the files is read only!

:(

---

