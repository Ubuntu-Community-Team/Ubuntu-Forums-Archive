---
title: "Removing Compiz Breaks Gnome GUTSY"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by nutbastard on 2008-01-28
After breaking my window manager many times by messing around trying to get Compiz and Desktop Effects working, (The old, "Desktop effects could not be enabled, then very wonky when i did once get it 'working')  I did yet another fresh install, this time swearing to forego the eye candy and remove the related packages right off the bat.

So, a fresh 7.10 I did install, and after doing my normal run of fresh-install tweaks (disable system beep, annoying startup sounds, enable graphical root login) I jumped into synaptic, did a search for 'compiz' and proceeded to remove all installed packages that contain the string 'compiz'.

Upon exiting Synaptic, I found that again, I had broken Gnome and I no longer had any window borders, title bars etc, alt-tab did not work and I had only one (graphical) desktop where there was once four. The option to change the number of desktops disappeared from the associated preferences window. Control-alt-right did not manifest a new desktop.

I know leaving it installed doesn't really hurt, but it's the principle of it; It's NOT stable, it doesn't "just work" and I'm honestly annoyed that it's included by default in 7.10. There is no end to the reports of users somehow junking their system because of compiz.

BUT what REALLY gets me (onto the apple website calculating payments) is that removing those 3RD PARTY packages breaks vanilla ubuntu. It's not right, Ubuntu 6.06 ran fine without compiz.

If i'm mistaken and there are not dependancies that i'm screwing up by removing compiz, then some config file is not being altered to a functional state, the way it should be when a package is removed. The whole idea of Synaptic is negated the instant i've got to go in and edit some config file by hand. Removing Compiz should not break the friggin desktop. Period.

So, the question:

I've read that the bug is fixable by doing:

metacity --replace

sudo apt-get autoremove compiz*

Which I haven't tried yet for fear of what will be my 6th install.

Nothing of importance is on my computer yet - easier to reinstall than start messing around with the CLI, THAT i'll do when i have something to preserve.

Does this work for this bug? Anyone else hating compiz installed by default with no straightforward GUI removal?


Dell Inspiron 8600
1.5 ghz Pentium M
nvidia geforce fx GO5200 64mb
2 x 256mb DDR Total: 512mb
Intel PRO/Wireless 2915 A/B/G

---

### Post by Kilz on 2008-01-28
> **nutbastard said:**
> After breaking my window manager many times by messing around trying to get Compiz and Desktop Effects working, (The old, "Desktop effects could not be enabled, then very wonky when i did once get it 'working')  I did yet another fresh install, this time swearing to forego the eye candy and remove the related packages right off the bat.

So, a fresh 7.10 I did install, and after doing my normal run of fresh-install tweaks (disable system beep, annoying startup sounds, enable graphical root login) I jumped into synaptic, did a search for 'compiz' and proceeded to remove all installed packages that contain the string 'compiz'.

Upon exiting Synaptic, I found that again, I had broken Gnome and I no longer had any window borders, title bars etc, alt-tab did not work and I had only one (graphical) desktop where there was once four. The option to change the number of desktops disappeared from the associated preferences window. Control-alt-right did not manifest a new desktop.

I know leaving it installed doesn't really hurt, but it's the principle of it; It's NOT stable, it doesn't "just work" and I'm honestly annoyed that it's included by default in 7.10. There is no end to the reports of users somehow junking their system because of compiz.

BUT what REALLY gets me (onto the apple website calculating payments) is that removing those 3RD PARTY packages breaks vanilla ubuntu. It's not right, Ubuntu 6.06 ran fine without compiz.

If i'm mistaken and there are not dependancies that i'm screwing up by removing compiz, then some config file is not being altered to a functional state, the way it should be when a package is removed. The whole idea of Synaptic is negated the instant i've got to go in and edit some config file by hand. Removing Compiz should not break the friggin desktop. Period.

So, the question:

I've read that the bug is fixable by doing:

metacity --replace

sudo apt-get autoremove compiz*

Which I haven't tried yet for fear of what will be my 6th install.

Nothing of importance is on my computer yet - easier to reinstall than start messing around with the CLI, THAT i'll do when i have something to preserve.

Does this work for this bug? Anyone else hating compiz installed by default with no straightforward GUI removal?


Dell Inspiron 8600
1.5 ghz Pentium M
nvidia geforce fx GO5200 64mb
2 x 256mb DDR Total: 512mb
Intel PRO/Wireless 2915 A/B/G

Sometimes packages tied to the ubuntu-desktop package can break gnome when removed. Evolution used to do it in Dapper. Just reinstall the desktop with ```
sudo apt-get  -f install ubuntu-desktop
``` then disable compiz rather than uninstalling it. I think there is a place to do that in System > Preferences, or right click on the desktop.

---

### Post by nutbastard on 2008-01-28
That's all well and good - if you have internet access at the time. Wait, can i run that command with the Live CD in the drive successfully? No internet at home. Closest hotspot: 20 miles.

---

### Post by Zars on 2008-01-28
I will install a fresh install of Ubuntu on VB and give the command a go for you. I understand your reasoning for wanting to remove Compiz-Fusion. Will take me a while to get VB installed and Ubuntu set up :) Will get back to you tomorrow.

Zars

---

### Post by nutbastard on 2008-01-28
Cool beans. I appreciate it man.

---

### Post by emarkd on 2008-01-28
I may not have understood your post above, but did you or did you not run:

```
metacity --replace
```

That should get your windows borders, etc going again.

---

### Post by Zars on 2008-01-28
Right,

I ran 'metacity --replace' using sudo, just to be sure. I ran it in terminal, but when I closed the terminal the windows flickered. So, I ran it in terminal again, then opened another. I ran 'sudo apt-get autoremove compiz* ', which took a while, closed all windows and restarted.

Loading o Ubuntu seemed normal, no obvious problems. Windows work just right. However the Visual Effects tab is still on the Appearences window, but if I try and enable the effects it says it cannot load compiz.

So, if my experiment is correct, you may run this and live to tell the tail :D

Zars

---

### Post by nutbastard on 2008-01-28
no i did not run it - i was unaware of it at the time, it's something i ran across today.

I'm actually going to try this in a bit.

Scary, man, im sitting in my car on a friend-who's-not-home's wifi, really really don't want to break it now that i've run update and customized firefox, again. but if you think it'll work, okey doke, i'll try it later. thanks!



oh and if anyone else can confirm this, the more the merrier.

---

### Post by UltraMathMan on 2008-01-28
As far as pulling the packages from the CD, just modify you sources to [use just the CD]("http://www.psychocats.net/ubuntu/sources") and then run ```
sudo apt-get update && sudo apt-get install -f install ubuntu-desktop
```

-Hope this helps :)

---

### Post by nutbastard on 2008-01-28
NO!!!! It broke again.

Ok, so i did

sudo apt-get autoremove compiz*

Then

sudo metacity --replace

BUT ALL IT DOES is give me a title bar for the terminal, which doesn't do me a lot of good. It also messed up how my keyboard input works - i had to log in as root to even get here!

ctrl-alt-f7 worked, as did the login screen, but i couldn't type in terminal, firefox, nothing!

I've also lost application tabs in the "taskbar"

SOMEONE owes me an explaination!!

: )

seriously, im dying here!!!

---

### Post by nutbastard on 2008-01-28
also i've lost my workspaces, alt-tab no longer functions, no titlebars, and user account can't use keyboard for text input. I tried using onboard, but being unable to move the indow out of the way, it was useless.

im REALLY glad I enabled graphical login for root.

the other strange thing that happens every time i remove compiz is the text in the login window becomes larger, and the "dots" that appear when i type my password are large enough that the bottom fifth is cut off by the text field.

GRRRR!

---

### Post by nutbastard on 2008-01-28
ok, ctrl-alt-backspace ing and logging back in as user level, the keyboard is working again.

by not closing the terminal window, my borders came back, so i know i'm close here.

it seems replace --metacity is something that needs to be run, and should continue to run, upon startup. I do not know how to do that. Some startup script or something? this works for now, but i don't revel having to have a terminal open running metacity --replace all the time. It's an ugly kluge, not a fix...

---

### Post by nutbastard on 2008-01-28
ok i can close the terminal and everything stays kosher. workspaces are back, all that jazz, but i have to run 

metacity --replace 

every time i log in.

I let it run in the tray for a second or two, then i can close it.

I CAN HAZ BOONTOO WERK RITE?

I know startup script stuff can do this for me... im off to see if i can figure it out, i'll check back, if i find the solution i'll post it, but contributions to this thread would be greatly appreciated!

---

### Post by nutbastard on 2008-01-28
battery dying - CAR battery, that is : )
*turns on car*

ok much better.

still lost as to how to get metacity to run on startup. I need it to run automatically, for ALL users.

I hate compiz when it's here, I hate it when it's gone.

Compiz is like a girlfriend you cant stand so you kick her out, then you come home and see that she took some of your stuff, and you don't want her back just for that stuff, but then you go looking around and realize some of those things are very difficult to replace, and you have to go on a forum to find em.

---

### Post by nutbastard on 2008-01-28
crap - car just spewed collant for no good reason - new radiator. i have bigger issues than title bars now. will check back tomorrow. night all

---

### Post by Zars on 2008-01-29
> I ran 'metacity --replace' using sudo, just to be sure. I ran it in terminal, but when I closed the terminal the windows flickered. So, I ran it in terminal again, then opened another. I ran 'sudo apt-get autoremove compiz* ', which took a while, closed all windows and restarted.


When I did it, I ran 'metacity --replace' first. You need to replace compiz before you remove it. 

As far as start-up scripts go, you can add an entry into the Sessions window. Just click add, enter a name and the command.

And I hope you can sort out your car :(

Zars

---

### Post by nutbastard on 2008-01-29
Spring style hose-clamp ate into one of the hoses. Was an easy fix, but hard to find which hose was doing it, as it only leaked when the car was on for 10 minutes. I should have followed murphys law and just assumed that the absolutely most difficult, hard to get-at hose was the offending agent, as it turned out murphy was right.

Sometimes, though, I'd rather fix a car than a computer; I can see what im doing to the car. too often fixing a computer makes me feel like i'm handing cryptic messages on 3 x 5 cards to a guy behind a curtain who assumes i know what im handing him and does it without consult.

OK SO - I did it backwards.

removed compiz first, then did 

metacity --replace

whats the real difference though? i imagine many people remove compiz without knowing that they have to put in the above before doing so. How do i make it as if i had done it correctly or does it even matter, as long as i get it running?

---

### Post by Zars on 2008-01-30
Ok, if typing 'metacity --replace' into the terminal everytime does the trick, you could make add this command to the startup of the session. To do this, go to Ssystem > Preferences > Sessions, click the '+ Add' button, then enter a name (e.g. metacity), command 'metacity --replace', then a comment if you want. Restart and it should run the command automatically.

Alternatively, you could set your software sources to install from the CD-ROM then enter:

```
sudo apt-get update && sudo apt-get  -f install ubuntu-desktop
```

This should reinstall compiz and all the extra's, and return your desktop to normal. You may well have to live with compiz installed.

The virtual Ubuntu install I have on my laptop is still running perfectly, with no problems.

Zars

---

### Post by nutbastard on 2008-02-01
i tried putting that in as a command:

metacity --replace

did not work.

i've seen other forum posts where this did not work for other people.

i may reinstall the desktop environment.

---

### Post by latchkeyed on 2008-02-01
I just fixed the same issue on my machine and you should be able to do it without adding anything to the startup list. 

What I did was:
[LIST]
[*]Log in to gnome
[*]open a terminal and run the "metacity --replace" command
[*]open another terminal and run "sudo apt-get install --reinstall ubuntu-desktop ubuntu-standard" just to be safe
[*]when that is complete, run "sudo apt-get install compiz"
[*]log out of gnome
[/LIST]

I think the --reinstall of ubuntu-desktop and ubuntu-standard is likely unnecessary for two reasons: 1) Reinstalling ubuntu-desktop by itself had previously failed to resolve the problem and 2) neither package asked to reinstall compiz as a dependency. 

Hopefully those steps will work for you as well. I initially had a different problem, enabling compiz gave me a white screen of death effect that I couldn't get around to disable compiz again. So I used Crtl+Alt+F1 to log in to the console and removed the packages, which worked fine, except that the window borders and Alt+Tab functionality were broken when I got back to the desktop. 

I just wish I knew where that "turn on compiz" setting was stored so I could change it from the terminal, or some other desktop environment.

---

### Post by nutbastard on 2008-02-04
well im actually up and running fine, except i have to terminal metacity --replace every boot up. i've been trying to find a good way to get this to run automatically, which i figured would be a trivial task, but it never works.

---

### Post by emarkd on 2008-02-04
Did you add it to your Session?  System > Preferences > Sessions

---

