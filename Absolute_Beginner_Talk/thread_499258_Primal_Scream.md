---
title: "Primal Scream"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by wooxy on 2007-07-12
Greetings.

I guess I'm a Linux newbie, although I did spend 10 or 20 years in the paleolithic era programming in UNIX environments, so I'm not a UNIX newbie.  I'm just kind of frustrated trying to install Feisty Fawn onto my HP Pavillion 6125 laptop.  I mostly just need to vent --- at the end of the post I shall review my current  plan and ask for a sanity check ...

I live out in the boondocks, where I am lucky to have a phone line at all.  Don't even talk broadband or DSL: my copper twisted pair has never yeilded a connection speed greater than 28k baud.  I can get to a library marginal wireless available 6 miles away, or 25 miles to a coffeehouse with good stuff.

Thus far, I have determined that my Feisty distribution disk does not support:

my Conexant modem
my Dell style wireless adapter
my nvidia display

Okay, fine, I have found explanations of how to get and install solutions for these things.  However, the combination of problems is very frustrating --- this frustration is exacerbated by the fact that: 

When running the "Install" in safe graphics mode, the aspect ratio of my wide-screen causes the "next" buttons to be unavailable, as they are displayed off the screen.  There is no way to resize the Install window smaller so I can slide the window up to see these buttons.  The "return" key works to get past the first screen, but once I choose my time zone, I cannot proceed with the installation because there is no available "next" button to click.

Great, so I go to "change desktop" to resize the screen.  Nope, it needs to connect to the internet to get my nvidia graphice driver, and it will not resize the screen in safe graphics mode.  And of course, without my modem or wireless drivers working, it cannot go get the graphics driver which I need to click through the screens of the install program.

Very frustrated.  My plan, then, seems to be:  Using Windows, I go get the Linuxant and  nvidia package I need, then boot Feisty from the Live-CD.  I guess I can "install" the graphics driver into the temporary disk area of my Live-CD setup, so I can see the "next" buttons on the installer.  Then after I install, I will have to install the graphics drriver again, since it won't remember about when I installed it in the "Live CD" session

Then install the linuxant driver for my modem, after which perhaps I can get a PPP connection and be able to ask apt to go get the support for my wireless.

Thanks for listening.  This would be a lot less complicated for me if the "install" program screens were designed so that the buttons were available on widescreen-aspect displays running in "safe" mode.

AIYYYYYYYYYYYYYYYYYEEEEEEEEEEE!   Thanks, I feel better now.

wooxy

---

### Post by Outrunner on 2007-07-12
Hold ALT+ click and drag the window to see the next button. That's all I can help with, sorry.

---

