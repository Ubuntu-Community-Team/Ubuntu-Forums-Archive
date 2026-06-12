---
title: "Two questions about using xubuntu/ubuntu"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-13
Two questions:

1.) I was wondering how you can end a program that freezes like Firefox when it gets stuck and the window is unable to close?

On Windows Xp if the computer froze or got stuck, I could use ctrl/alt/delete and then choose the running programs that weren't responding and close them manually from there with "End Program".

Is there a terminal command that could close frozen programs. Also, is there a hot key that will make terminal appear?

2.) Do I need to perform a "disk cleanup" or any sort of maintenance like I did in Windows Xp with "disk cleanup" and "defragment"? 

Do I need to maintain my file systems like I used to maintain the registry in Windows? Would that be basically like sudo apt-get autoremove?

---

### Post by argie on 2006-11-13
What I usually do to close programs is something like this.

1. Press Ctrl+Alt+F1 (tty1)
2. ```
killall firefox
``` replacing firefox with whatever I want to kill.

---

### Post by Sef on 2006-11-13
> 1.) I was wondering how you can end a program that freezes like Firefox when it gets stuck and the window is unable to close?

On Windows Xp if the computer froze or got stuck, I could use ctrl/alt/delete and then choose the running programs that weren't responding and close them manually from there with "End Program".

Is there a terminal command that could close frozen programs. Also, is there a hot key that will make terminal appear?

Usually clicking the x button on the app will case a force quit box to appear.  Via terminal - killall app name

Terminal to appear > needs to be set via System > Preferences > Keyboard Shortcuts > Desktop > Terminal

> 2.) Do I need to perform a "disk cleanup" or any sort of maintenance like I did in Windows Xp with "disk cleanup" and "defragment"?

Do I need to maintain my file systems like I used to maintain the registry in Windows? Would that be basically like sudo apt-get autoremove

If you use ext3 then it automatically defrags every 30 boot ups.

To install use - sudo aptitude install app - to remove - sudo aptitude remove app - 

By using aptitude rather than apt-get, all the files that installed with the package will be uninstalled.

---

### Post by ajgreeny on 2006-11-13
Don't know about *xubuntu* but in Ubuntu start *gnome system monitor*, and in the processes tab highlight *firefox-bin* and then click on "End process"

If you use KDE, (Kubuntu), you can do Ctrl+Alt+Esc, and then click the mouse when the cursor, now a skull & crossbones, is in the offending window.  That will close it.

Of course if the mouse and keyboard are frozen, then a reset with the button may be all you can do.

---

### Post by an.echte.trilingue on 2006-11-13
1.  I find the best way to do this is xkill.  To use it, open up a terminal and type xkill.  Your cursor will change to a little X and the next window you click on will die a fast death.  You can make a launcher for this by right clicking on your desktop and selecting the create launcher option, using xkill as the command.  You can also add it to your menu with the menu editor.

2.  No you don't need to do this.

---

### Post by crimesaucer on 2006-11-13
Thanks for the info, though, I have never seen the force quit option when certain programs have frozen. 

I have only had my system freeze when trying to run the Flash 9 update with surfline.com (won't work with their site) and when I tried to add the Radio.Blog 3.0 (tester version) to my google personalized homepage.

I also have had rythmbox freeze bad on me and Mixxx 1.4.2 because I am new to the programs and did something wrong. Both times I was unable to close them off of my workspace and had to turn the computer off and reboot so they would be closed and gone.

Also, when using "Press Ctrl+Alt+F1 (tty1)", how do I get tty1 to go back to a GUI desktop rather than doing a sudo shutdown -r now?

Thanks for the info on xkill and killall app name.

Now about aptitude rather than apt-get, on the wiki, everything to install is done in apt-get, should I have been using sudo aptitude install?

---

### Post by an.echte.trilingue on 2006-11-13
> **crimesaucer said:**
> 
Also, when using "Press Ctrl+Alt+F1 (tty1)", how do I get tty1 to go back to a GUI desktop rather than doing a sudo shutdown -r now?

Now about aptitude rather than apt-get, on the wiki, everything to install is done in apt-get, should I have been using sudo aptitude install?

1.  Your GUI is on CTRL+ALT+F7.  You really do not need to switch though if you are not comfortable with that, for almost everything you can do on tty1 thru 6 you can just open a terminal window in your existing session under applications-->accessoires-->terminal

2.  Aptitude is a front end for apt that tracks your packages in a slightly different way but has the same input, output, and result.  You can simply interchange apt-get and aptitude in commands as you desire.

Take care,
mat

---

### Post by crimesaucer on 2006-11-13
Could you explain the tty1 a little bit more for me, I have had to go to ctrl/alt/F1 a lot when messing around with the 6.10 edgy betas during upgrades, and also with the final release during upgrades for various problems like the xserver error. When I worked in tty1 (mostly just remove purging the xinit, xorg, xserver-xorg, and x11-common and then reinstalling and dist-upgarde installing with -f installs and --configs, I basically thought it was the terminal without the GUI, but you just said there are tty1 thru tty7? What are the functions for them. 


The reason I asked about opening the terminal from a hot key was because I was on a page that froze my Firefox and the top panel of xubuntu and my mouse turned into this weird right angel x (close) thing, so I couldn't click on my app menu with the weird icon and I could not close the Firefox page or browser or even switch tabs, also it seems like if there is a hot key, it would be faster than clicking on the menu with the mouse since my fingers would already be typing for sudo commands.

Thanks for the info. 

Also, I liked doing dist-upgrades in tty1, it seemed faster, is xubuntu/ubuntu faster when working without the GUI, and is there a page to learn all of the things needed to learn to be able to work/fix xubuntu/ubuntu from the tty1? And I also read somewhere to do the upgrade dist-upgrade in aptitude and I tried it and everytime I used aptitude instead of apt-get, I ran into problems with either avahi-daemon failing (my desktop was blank except for wall paper) or the xserver error which I fixed in tty1, but maybe those were just the common edgy problems because I ran into the same problems with apt-get also.

---

### Post by an.echte.trilingue on 2006-11-13
Linux is derived from unix, and unix is an old mainframe OS that used to have several terminals connected to one mainframe.  As things have evolved, the actual terminals turned into virtual terminals that are usually on F1 thru F7, with F7 being the one that the GUI is usually on.  There is no reason to limit it to seven, in fact, when you use the change user function in ubuntu you are actually starting a new X session on tty8, 9, and so on..  You can log in as two, three, four users and switch between them with the CTRL+ALT+F<whatever> keys.  The reason for 7 is, I think, a guess by developers to accomodate for future changes that could possibly have a use for them but right now they are just kind of hanging around.

On some linux distros, you will see that all the boot stuff happens on tty1 and if you want to use another virtual terminal you have to go to tty2. 

And yes, it is faster to work in a text environment because the computer does not have to take the processing power to draw all those lines and shadows on the screen. 

I am stumped as to why aptitude should cause those problems.  To make a hotkey for xkill, use the keybindings tool under desktop-->preferences.

Take care,

-mat

---

### Post by LLRNR on 2006-11-13
-- WHOOPS !! Sorry for the incomplete post, I was editing it earlier and it seems that by lack of attention I cut off half of it... I'm terribly sorry, crimesaucer !! --

Hi crimesaucer, I don't know if this helps you a lot but here are my "versions" on killing un-responsive applications (you can do it from either the terminal or from tty1...tty6, whichever you like best).

**Solution #1:**
```
top
```and you'll get a list of currently running processes. (You can exit this by typing '**q**'.) 

When you press '**k**', which as you guessed stands for "kill", you'll get at the prompt a message displaying "Pid to kill: " and here you have to type in a number - the PID you see in the "table" that top displays, corresponding to the application that's causing you troubles. PID stands for **P**rocess **ID** and it's an identifier associated to a process.

Then you'll be asked which signal you want to send to the process you designated by that PID you typed in earlier. The default signal is no.15 and that's the SIGTERM signal. If you wanna be really sure you're going to  kill the mis-behaving process, yiu can use SIGKILL and this has no.9 associated. So you can just type "9".

When you're finished you can type '**q**' to exit (quit) top.

**Solution #2:**

You can also type ```
ps -e | more
``` and get a list of running processes, then fetch the desired PID and do one of the following:

```
kill -**number** PID
``` or ```
kill **ABCD** PID
```. The two commands have the same effect but the syntax differs, it's up to you which you like best.

The **number** above designates a number associated to a certain signal. You can see all the signals that your system knows by issuing ```
kill -l
``` where " -l " is lowercase "L"; this will display a list of all signals available; the most common are SIGKILL, SIGTERM and so on.

For example, if the mis-behaving app has PID 1234, then you can either type "kill -9 1234" or "kill KILL 1234". (Don't forget to put a "-" i.e. a minus sign if front of the signal's associated number) 

The **ABCD** above is a suffix made out of 4 uppercase letters representing the suffix of a certain signal (all signals have the form SIGABCD), and you can see this, as I said, with "kill -l".

-----------------

Or you might as well use <Ctrl>+<Esc> and do it a lot easier if you prefer the GUI (for myself, I like the CLI better :D), but it might come in handy to know this stuff if your mouse gets stuck i.e. you can't use <Ctrl>+<Esc>, nor **xkill** (which is faster, by the way).

HTH,

LLRNR

---

### Post by crimesaucer on 2006-11-13
Thank you very much for the detailed info, and the aptitude problem happened when I was doing and upgrade from 6.0.6 to 6.10 and it might have just been one of those many upgrade issues that was happening.

Thanks again for taking the time to help a beginner learn xubuntu/ubuntu.

---

### Post by LLRNR on 2006-11-13
I'm terribly sorry for my last post, after I wrote it I wanted to add something, I edited it and when I hit the save button I didn't realise that I had cut off half of my message by mistake... I'm very sorry if I somehow confused you or misled you, crimesaucer, but I think now the post is ok :P

LLRNR

---

### Post by crimesaucer on 2006-11-14
Thanks, and if anyone has a link to a page with a good ubuntu tutorial for tty1, please post it.

---

### Post by LLRNR on 2006-11-14
It's not just about tty1, but it's rather useful for learning lost of stuff about the command line, about scripting and so on: [http://www.linuxcommand.org](http://www.linuxcommand.org).

HTH,

LLRNR

---

### Post by crimesaucer on 2006-11-14
Cool, I'll read through that, thanks.

---

