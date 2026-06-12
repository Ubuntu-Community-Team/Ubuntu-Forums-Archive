---
title: "Help - Managed to screw up the system - AGAIN!!!"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-15
For the second time i managed to screw up xubuntu. This time I don't even have an ideia of what I did wrong.

The last time I shutdown the computer, everything seemed ok, altough the computer took an unsual long long time shutting down. 
Today starting up xubuntu the usual way, made the login, but then when xfce starts I have no menu bars. I don't have the applications menu, dont have the logout/reboot/shutdown menu, dont have the upper bar with the shortcuts, and even don't have the lower bar (panel). I entered with FVWM-crystal but XCFE seems "broken". The problem is I want to use the XCFE and not the windows managers.

How do I fix this problem? Must I re-install xubuntu? I can backup my files to a pen using this windows manager. 


Any help will be wellcome!

---

### Post by Ateo on 2007-05-15
What? You want to use XFCE and not the window managers? That makes no sense. In order to have a desktop environment, you need a window manager. Do you mean you just don't want to use FWWM in favor of XFCE?

Without knowing what you did, helping you fix your issues might be difficult.

---

### Post by Ganda_Melga on 2007-05-15
> **Ateo said:**
> What? You want to use XFCE and not the window managers? That makes no sense. In order to have a desktop environment, you need a window manager. Do you mean you just don't want to use FWWM in favor of XFCE?

Without knowing what you did, helping you fix your issues might be difficult.


Well, xubuntu comes with XFCE by default. After a while I installed FVWM and FVWM-crystal, However I found them too difficult to configure and decided to stick with XCFE, wich has it's own windows manager, I suppose.

Can't really figure out what happened. The only unusual thing was the very long shutdown time last night. Also the Pc was running a little bit slow in the past few days.

Ah... another thing. Now every time I enter with xfce i can't log out, so I have to restart the computer. Well, it doesn't restart. I have to press the power button for a few seconds to shutdown, and after that press it again to boot again.


Perharps I should backup my files and re-install Xubtuntu again. Or maybe try an even lighter linux such as Fluxbuntu.

---

### Post by crimesaucer on 2007-05-15
Well, your xubuntu window manager should be called xfwm4

Your panels, in xfce, should be able to be put back on your desktop using this code in - alt + F2:

```
xfce-panel &

```

Try that, and I guess you could also try this for the default xubuntu window manager:

```
xfwm4

```

I could be wrong though...

...also, did you make any startup scripts to use that other window manager, or add it to the start up programs in Autostarted Applications?

---

### Post by Ganda_Melga on 2007-05-15
> **crimesaucer said:**
> Well, your xubuntu window manager should be called xfwm4

Your panels, in xfce, should be able to be put back on your desktop using this code in - alt + F2:

```
xfce-panel &

```

Try that, and I guess you could also try this for the default xubuntu window manager:

```
xfwm4

```

I could be wrong though...

...**also, did you make any startup scripts to use that other window manager, or add it to start up programs**?

Negative. Don't even even know how to make scripts. That probably why I can't configure the FVWM.

I will try your suggestions. Thanks

---

### Post by Ganda_Melga on 2007-05-15
This might be important, so I'll put it here. I tried to boot in XFCE with my daughter's login name and password. It booted fine! Seems the problem only affects my user name. Did I broke my user definitions or something?

---

### Post by Ganda_Melga on 2007-05-15
> **crimesaucer said:**
> Well, your xubuntu window manager should be called xfwm4

Your panels, in xfce, should be able to be put back on your desktop using this code in - alt + F2:

```
xfce-panel &

```

Try that, and I guess you could also try this for the default xubuntu window manager:

```
xfwm4

```

I could be wrong though...

...also, did you make any startup scripts to use that other window manager, or add it to the start up programs in Autostarted Applications?


I tried those two commands. Nothing happened

---

### Post by crimesaucer on 2007-05-15
I would guess that you installed the FWWM in your name using sudo or in Synaptic, so it only affected your names xubuntu. Did you try un-installing FWWM either in Synaptic or in Terminal using "sudo aptitude remove --purge "FWWM" ( I don't know the exact thing to say, whether it's FWWM or fwwn, or something else)

You should get some other help from someone that has more knowledge in this matter.

---

### Post by totalnub on 2007-05-15
did you change icon themes?
i had a similar problem when i accidentally selected a cursor theme for regular icons.....gnome didn't like that. i'll see if i can find the link that helped me.

---

### Post by totalnub on 2007-05-15
see if this link works. it did the trick for me :) gl.
[http://ubuntuforums.org/showthread.php?t=409155](http://ubuntuforums.org/showthread.php?t=409155)

---

### Post by Ganda_Melga on 2007-05-15
> **crimesaucer said:**
> I would guess that you installed the FWWM in your name using sudo or in Synaptic, so it only affected your names xubuntu. Did you try un-installing FWWM either in Synaptic or in Terminal using "sudo aptitude remove --purge "FWWM" ( I don't know the exact thing to say, whether it's FWWM or fwwn, or something else)

You should get some other help from someone that has more knowledge in this matter.


Thanks a lot anyway! :guitar:

---

### Post by Ganda_Melga on 2007-05-15
> **totalnub said:**
> did you change icon themes?
i had a similar problem when i accidentally selected a cursor theme for regular icons.....gnome didn't like that. i'll see if i can find the link that helped me.

I changed themes 2 weeks ago, but I choose one of those who came inbuilt in xubuntu. Dit not installed any new themes.

---

### Post by Ganda_Melga on 2007-05-15
> **totalnub said:**
> see if this link works. it did the trick for me :) gl.
[http://ubuntuforums.org/showthread.php?t=409155](http://ubuntuforums.org/showthread.php?t=409155)


I thank you for your help, mas it didn't worked out.


I suppose I will enter with my daughter login for the rest of this week, and in the weekend will re-install Xubuntu. Or maybe I'll try Fluxbuntu.


Also tried to re-install the xfce4 with "sudo apt-get install xfce4". Nothing changed, however.

---

### Post by crimesaucer on 2007-05-15
> **Ganda_Melga said:**
> I thank you for your help, mas it didn't worked out.


I suppose I will enter with my daughter login for the rest of this week, and in the weekend will re-install Xubuntu. Or maybe I'll try Fluxbuntu.


Also tried to re-install the xfce4 with "sudo apt-get install xfce4". Nothing changed, however.

Did you remove --purge the FWWM that you didn't want to use anymore?

---

### Post by Ganda_Melga on 2007-05-15
> **crimesaucer said:**
> Did you remove --purge the FWWM that you didn't want to use anymore?

Yes, I did follow your advice. Typed in the terminal:

"sudo aptitude remove --purge fvwm-crystal"

fvwm-crystal was removed

Then typed:

"sudo aptitude remove --purge fvwm"

fvwm was removed

On the login screen they no longer appear. However XFCE continues without the panels. Managed to put some shortcuts in the desktop, that was the best i could do. Also on the Settings Manager clicking on the icon "panel" produces no effect. It's just as the panels do not exist. Very strange.

Anyway, you tried very hard to help, and I thank you for that! :popcorn:

---

### Post by crimesaucer on 2007-05-15
Now try this:

```
killall xfce-panel
```

then after that, try this one again:

```
xfce-panel &
```

It can't hurt to try.

---

### Post by Ganda_Melga on 2007-05-16
> **crimesaucer said:**
> Now try this:

```
killall xfce-panel
```

then after that, try this one again:

```
xfce-panel &
```

It can't hurt to try.


The terminal produced this answer:

melga@melga-desktop:~$ killall xfce-panel
xfce-panel: nenhum processo abortado (no process was aborted)
[2]+  Exit 127                xfce-panel


melga@melga-desktop:~$ xfce-panel &
[1] 4585
melga@melga-desktop:~$ bash: xfce-panel: command not found

---

### Post by Ganda_Melga on 2007-05-18
Anybody has any other ideias? Please? :(

---

### Post by Najand on 2007-05-18
What is the output of your "date" command. Panels don't load when time of the system is wrong.

---

### Post by Ganda_Melga on 2007-05-18
> **Najand said:**
> What is the output of your "date" command. Panels don't load when time of the system is wrong.


Date gives the current date. No errors there.

---

