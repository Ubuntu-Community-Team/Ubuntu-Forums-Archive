---
title: "Keyboard Shortcuts Doesn't Work Properly"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by guguma on 2007-08-07
I want to assign a hotkey to Run a Terminal. I used System -> Preferences -> Keyboard Shortcuts for that but it does not apply my shortcut for a weird reason I have not yet found. 

I assigned ctrl + H for the home folder and it works fine. I assigned ctrl + H to terminal and it does not work???

So what is going on?

---

### Post by forestpixie on 2007-08-07
Are you trying to use the same hotkeys for two different things?

---

### Post by guguma on 2007-08-07
No I am not. I am sorry it looks that way from my posting isn't it. I assigned ctrl +H to home to test if I was doing something wrong. Then I disabled the shortcut to home and assigned ctrl + H to Terminal and it did not work.

---

### Post by forestpixie on 2007-08-07
does it not work with any shortcuts at all?

---

### Post by nichipet on 2007-08-07
When I get home I'll try it on mine if you haven't found a solution yet.

---

### Post by guguma on 2007-08-07
Forestpixie, only the terminal shortcut does not work. When I assign a hotkey to my home folder it works. But it does not work when I assign something for the terminal whether it be ctrl+t ctrl+alt+shift+n and etc. I tried many combinations but none of them works for the terminal.

Thanks

---

### Post by forestpixie on 2007-08-07
There's probably an easy mewthod - but I can't think of it :( the only thing I've found which might help is this 

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

### Post by guguma on 2007-08-09
I have bad news. It does not work too. It is very weird indeed. I also have nauilus-open-terminal I thought maybe it is causing a problem but I do not think so.

---

### Post by nichipet on 2007-08-09
Well, it worked on mine. I guess that's unfortunate in that I can't replicate your problem.

---

### Post by ELCouz on 2007-08-22
me to i have exactly the same problem ,,, found this topic while searching on google ... tryed the metacity method also.

---

### Post by ELCouz on 2007-08-27
Are you running compiz or beryl ???

---

### Post by guguma on 2007-08-28
I am running compiz-fusion

---

### Post by mali2297 on 2007-08-28
> **guguma said:**
> I am running compiz-fusion

You should then set the shortcut in the Compiz configuration settings manager.
See under General->General options->Commands.

---

### Post by guguma on 2007-09-02
I suggested as you said but it does not work. It changes the open terminal tab shortcut. But if there are no terminals already open then it does not open a terminal window.

---

### Post by mali2297 on 2007-09-02
> **guguma said:**
> I suggested as you said but it does not work. It changes the open terminal tab shortcut. But if there are no terminals already open then it does not open a terminal window.

Strange. :? 

Instead of making a shortcut to *Open terminal*, try to make a custom command (in menu *Commands*) to run *gnome-terminal* and make a shortcut to it (in *Key bindings*).

---

### Post by ELCouz on 2007-09-04
this is a bug under compiz-fusion because me too i have the same problem ,,, when running gnome without compiz the terminal launch shortcut work #1 !

try updating to the lastest version ... thats the only thing i can say or bind a script that open it.

---

### Post by TiMBuS on 2007-09-06
My compiz hotkeys were being overridden by gnome's native hotkeys. I suggest that you first unbind any hotkey you had for 'open terminal' and try setting it in just compiz itself. Under 'General Options->Commands tab->Run Terminal Command' you simply put 'gnome-terminal' as the command and set your hotkey to whatever you want it to be. Should work.

---

### Post by necrologist on 2007-09-12
Hi!

Not sure this will help, but it should work under ubuntu too (i'm usin openSuSE now):

open gconftool-2 or kconfigeditor go to gnome->apps->compiz->general->allscreens->options
you wil find a lot hotkeys there and there are a lot which is disabled by default.

Hope you will find there what you need (i haven't tried it yet but hopefully enabling one of them will solve the prob)

---

