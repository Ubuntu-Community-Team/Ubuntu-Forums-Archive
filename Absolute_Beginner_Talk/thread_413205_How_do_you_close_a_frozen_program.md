---
title: "How do you close a frozen program?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-18
I installed Aria a download manager but it keeps freezing on me and won't close. What's the Linux equivalent of Ctrll/Alt/Delete? Thanks.

---

### Post by BarfBag on 2007-04-18
Ctrl - Alt - Esc

The mouse pointer should turn into a scull.  Then, click on the window.

At least, that's how it is in Arch.  (Waiting for Feisty.)

---

### Post by freebird54 on 2007-04-18
Lots of ways!  here's an assortment of others..

[http://www.geocities.com/lunatech3007/how-to/html/howto_18.html](http://www.geocities.com/lunatech3007/how-to/html/howto_18.html)

---

### Post by pjones0404 on 2007-04-18
there is a system monitor under administration. here there is a processes teb where u could kill the process. 

there is even a way to create a keyboard shortcut to make it pull up when u press Ctrll/Alt/Delete. 

 How to enable Ctrl+Alt+Del to open System Monitor in GNOME

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

---

### Post by ramjet_1953 on 2007-04-18
The easiest way is to add the [COLOR="Blue"]'Force Quit"[/COLOR] applet to either your top or bottom panel.

To do this, right click on the panel of your choice and then select [COLOR="Blue"]"Add to Panel"[/COLOR]

A window will then open.

Scroll down to the [COLOR="Blue"]"Desktop and Windows"[/COLOR] section and choose [COLOR="Blue"]"Force Quit"[/COLOR]

Close the window.

You will now have the "Force Quit" applet on you panel and if you have an  application that won't close, just click on the "Force Quit" applet and drag it to the window of the recalcitrant application.

ps you may want to try wxDownload Fast as a download manager. It works great! It is in Synaptic under [COLOR="Red"]wxdfast[/COLOR]

Regards,
Roger 8)

---

### Post by crimesaucer on 2007-04-18
In terminal write:

```
xkill
```

then your mouse will turn into a "x" and then you just move your "x" mouse over the frozen program and then "left click" it.

That's the way I do it.

---

### Post by jacatone on 2007-04-19
I'd always thought Windows was the only OS with this problem. Surprised to see Linux has it as well.

---

### Post by PartisanEntity on 2007-04-19
> **jacatone said:**
> I'd always thought Windows was the only OS with this problem. Surprised to see Linux has it as well.

Why would Linux not have this? Linux is made by human beings and human beings make mistakes. In the software world these mistakes are called 'bugs'. Why should Linux or applications made for Linux not have bugs?

---

### Post by crimesaucer on 2007-04-19
Well, sometimes certain things like right before Flash was updated, there was a Flash beta available on the wiki page that worked with most sites, but froze other sites that hadn't updated their code to work with the newer Flash.

And sometimes the force quit option couldn't be clicked when those pages would freeze. So xkill would close Firefox's frozen Flash sites. One site that did this was Surfline.com. They hadn't updated their page so it would freeze every time I clicked onto their site when using the newest Flash Beta. Even the Finalized Flash version froze for a few days before they updated their code. 

Another time that Linux apps freeze are when they aren't really that good of an app, I had an app, I think it was "x-paint" and it caused a freeze up that needed the "xkill" command to shut it down. I also had a problem with the program called Mixxx. It freezes everything.

The difference between xubuntu Linux and Windows, is that in Windows Xp when something freezes, you have to use ctrl-alt-delete to get the network manager to appear, then you have to force a program to shut down and sometimes that takes like ten times to close it, and sometimes it will close all the programs you have running instead of just the "not responding" one, and then Windows will feel slow and buggy after all of that, and you might end up having the same problem happen a few minutes later. 

If I remember it correctly, each time you click on the app that says, "not responding" on the list of programs that you have running in Windows Xp, then you get a gray dialog box that says close now and lose all data, or you can wait for it to close by it's self, and that takes for ever and usually doesn't work until the third or fourth try of closing it. Plus it's always trying to connect you to Microsoft to file a report and that's a waste of time.

Now in Linux xubuntu, all it takes is one command:

```
xkill
```

then the frozen program is gone. If there is a second program that froze with it, then while your terminal is still open, you just press the "up arrow" once and it will repeat the last terminal command you typed, so then you just press enter and you can "xkill" another app.

It's a simple as opening up terminal, typing one 5 letter command "xkill" and then moving the mouse "x" over the frozen app and left clicking on it.

Compared to Windows, that is so much easier and better.

---

