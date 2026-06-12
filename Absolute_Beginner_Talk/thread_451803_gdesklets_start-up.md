---
title: "gdesklets start-up"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-22
O.k I got gdesklets to start-up when I log-on but does that box that shows all available desklets have to pop-up every time my desklets start-up?](*,)
Is there a way to stop it from starting up ?[-o<
Thanks
smoaky

---

### Post by diatribe on 2007-05-22
instead of starting the gdesklets manager or whatever, just start the daemon; it will start the desklets with it if I remember correctly

---

### Post by smoaky on 2007-05-23
Thanks I,m running Edgy. How do I do that? (start the daemon)

---

### Post by Viskovitz on 2007-05-23
Type this in a console:
```
gdesklets&
```

Works?

---

### Post by smoaky on 2007-05-23
OK
Maybe I was not clear enough in my explanation. My apologies. I have two desklets that I have set to start-up when I log-on CPU load and Ram useage.  The only annoying thing is that a box pops up(have no idea what it is called) that gives me a list of all available desklets **everytime** my two preferred desklets start-up. How do I stop that box from appearing all the time? Is there a workaround or do I have to view and  manually close this box upon every log-on?

---

### Post by Viskovitz on 2007-05-23
Sorry smoaky, it was me not being clear :) I understood your problem, although I don't remember having that box when I used gdesklets. Once your desklets appear, kill them:
```
killall gdesklets
``` 
and then launch the daemon manually:
```
gdesklets&
```
Like this you'll know if that misterious box appears with the base daemon (maybe it's an option that you have to disable somewhere in a config file) or if the command that you run in the startup is not the correct one (maybe a manager like diatribe said).

---

### Post by smoaky on 2007-05-23
Did that in terminal. It says no process killed
I will disable desklets from start-up and launch daemon using the code and get right back to you
with my results.

---

### Post by smoaky on 2007-05-23
Launched daemon and desklets appeared with NO pop-up box ...great =D
Problem is do I have to launch daemon manually upon every log-on the get my desklets to run?
Tried entering" daemon" as a command for start-up but that didn't work

---

### Post by Viskovitz on 2007-05-23
Of course you don't have to launch it manually... which command did you have before in the list of startup programs? Just that, "gdesklets"? That's supposed to work... 

C&P from [here]("http://ubuntuforums.org/showthread.php?t=203093"):

> Finally you will want gDesklets to load at the login. To do this open System->Preferences->Sessions, choose the tab Program Start and there add "gdesklets".

Try and see if it keeps opening the pop-up.

"daemon" is just a kind of program that runs in the background, doing its task from time to time. So there are many daemons of many applications running at the same time, and each has a different name. Your system cannot execute "daemon", it means nothing :)

---

### Post by smoaky on 2007-05-23
yes I have gdesklets as the command for start-up. And yes the pop-up box continues to appear.
That is the reason for my initial post. 
As with most things in Linux nothing is simple

---

### Post by smoaky on 2007-05-23
My apologies[-o< Bill Gates was tugging at my dark side again :redface:
Linux rulz. I just have to become more open source savvy
Thanks for all you that take the time to help me =D>

---

### Post by Viskovitz on 2007-05-23
Yep, some things that should be plain easy turn to be just tricky. You may try this:

1. instead of adding "gdesklets" add "gdesklets&", although I'm not sure it helps...

2. Otherwise you can also add it in a config file, like here:
[http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

3. or maybe use .xinitrc:
[http://www.cyberciti.biz/tips/linux-desktop-auto-start-or-launch-programs.html](http://www.cyberciti.biz/tips/linux-desktop-auto-start-or-launch-programs.html)

Good luck!

---

### Post by smoaky on 2007-05-23
Thank you
Turns out I had "gdesklets shell" entered as the command for start-up. That caused the pop up box to appear. Once I correct the command to "gdesklets" no pop up appeared. YAY!!

---

### Post by Viskovitz on 2007-05-23
I'm so glad to hear that :D

<joke>Now go to the corner and copy a thousand times: "I will never ever say that Linux is difficult again"</joke>

Enjoy your desklets, thank you too!

---

### Post by smoaky on 2007-05-23
As I bow my head with shame and embarrassment, my deepest regrets.
I will look for my chalkboard and proceed to start writing. 
BTW I have sporatic problems with my mouse freezing up. Thought it was the kernal used in Feisty so I switched to Edgy,still freezes. Tried OpenSUSE same thing. Must not be the Kernal, or Linux.
I have Edgy on an external HDD with XP and Vista on my primary  internal HDD 
Using a Logitech wireless USB mouse plugged directly into my NEW pc. Tried switching to a wired mouse still the same snafu. Switched USB ports. Any clues?

---

### Post by Viskovitz on 2007-05-23
Can't help you there, but you should do 2 things:

1. Start a new thread with your new problem
2. Change the title of this post to add "[solved]" (don't know how, though)

Cheers

---

