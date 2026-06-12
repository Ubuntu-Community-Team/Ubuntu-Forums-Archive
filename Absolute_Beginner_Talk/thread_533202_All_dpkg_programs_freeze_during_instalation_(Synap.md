---
title: "All dpkg programs freeze during instalation (Synaptic, Add/Remove, apt-get)"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by shongzah on 2007-08-23
I may be having a related problem, maybe not. When I try to use Add/Remove, Synaptic, or Apt-Get my system freezes completely. With the two graphic apps, I can browse, select, deselect just fine. The problem comes when I click [apply]. With apt-get I can do a few things but, again, when i ask it to install it freezes. 

I am a moderately adept newbie. If the directions are clear, i can follow them.

---

### Post by aysiu on 2007-08-23
> **shongzah said:**
> I may be having a related problem, maybe not. When I try to use Add/Remove, Synaptic, or Apt-Get my system freezes completely. With the two graphic apps, I can browse, select, deselect just fine. The problem comes when I click [apply]. With apt-get I can do a few things but, again, when i ask it to install it freezes. 

I am a moderately adept newbie. If the directions are clear, i can follow them.
How much RAM do you have?

Can you launch ```
gksudo synaptic
``` from the terminal and post back any error messages that appear when the program freezes?

Is it *just* the program that's in use that freezes, or does your entire screen freeze?

---

### Post by shongzah on 2007-08-23
>How much RAM do you have?
I have 512 mb

>Can you launch
>Code:
>gksudo synaptic
>from the terminal and post back any error messages that appear when the program freezes?

I entered :gksudo synaptic and it launched Synaptic. From there I made another attempt. 

I did a clean install of 6.10 this morning and was trying to install the apps that I use that do not come with the default install. So in synaptic, I searched for Inkscape, selected it for install, and then clicked apply. I got a pop up telling me about the changes to be made, the files that would be installed, and asking me to approve them. I clicked apply again. I got a pop up showing me the progress (Downloading files...) and, just like before with Add/Remove, Synaptic, and Apt-Get, it freezes mid-progress. The entire system locks. The seconds stop ticking on the clock, the cursor won't move, and the keyboard is unresponsive. 

I have to do a hard shutdown (hold down the power button) and reboot.

---

### Post by aysiu on 2007-08-23
So, no error message when you launch Synaptic from the terminal?

The other thing to try: create a new user (make sure the new user is an administrator), log in as that user and see if the new user experiences the same freeze-up.

If the new user does, then it's a system-wide issue (which it probably is, but this is the best way to test). If the new user doesn't, it's a user-specific issue, in which case, you may have to use a new user and copy over some of your settings and files from the old account.

---

### Post by shongzah on 2007-08-23
No errors. It launched without a hitch.

I had to go to work, but I will do as you suggest tomorrow and report the results.

---

### Post by shongzah on 2007-08-25
Okay. I created another user and installed Avahi Browser and Inkscape using Add/Remove with no trouble. So I switched users. With my normal login, I used Add/Remove to install Acrobat Reader. Then I used Synaptic to install Fontforge and Fontforge-doc and upgrade Kdelibs-data and Kdelibs4c2a. I then installed Scribus using Apt-get. Up to that point, I had no problems. The next day, I was trying to get PDF/X-3 working in Scribus and to do that I needed to have Color Management installed. In my last Ubuntu installation I used LittleCMS to accomplish this. I couldn't find LittleCMS in the repositories so I downloaded the source from the maintainers to compile on my own. My first run at compiling suggested that I needed a C compiler. I tried to use apt-get to download a c compiler, build-essential (i think). During the process it froze. *shrug* What the hell, man? Maybe my computer just doesn't like install stuff late in the evening (the time it has frozen most).

---

