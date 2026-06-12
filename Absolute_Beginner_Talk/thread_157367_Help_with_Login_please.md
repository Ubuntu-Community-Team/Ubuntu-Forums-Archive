---
title: "Help with Login please"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by beef_thing on 2006-04-09
I just installed Ubunto 5.10. However, when it took me to the login screen, "Ubunto 5.10 "Breezy Badger" ubunto tty1", I entered the correct username, pressed "enter", then when I try to enter the password, not a single character is registered. Thus always results in login failure. Need help desperately! Thx!

---

### Post by 5-HT on 2006-04-09
Your password keystrokes are not reflected by asterisks as a security feature.
The password is getting entered though, just type it in (case sensitive) and press enter.

HTH

---

### Post by beef_thing on 2006-04-09
Thx 5-HT! However, now I have another problem...after login, a bunch of text appeared, and the end command line is kefan@ubunto:~$(kefan is my username), and apparently it's expecting me to enter something, what should I do?

---

### Post by krusbjorn on 2006-04-09
Looks like your graphical environment (X) didnt startup as expected. Type "startx" and see what happens. If it doesnt work, there probably is an issue with your graphics card. What card do you have? Nvidia/ATI? Model?

---

### Post by taurus on 2006-04-09
That thing is called a prompt.  It's waiting for you to type something, just like the old DOS prompt!  Just curious.  How did you install Ubuntu?  Did you just hit an enter at the prompt or did you type in server at the prompt?

---

### Post by beef_thing on 2006-04-09
hmm, I typed in "startx", however, it returned "bash: startx: command not found" to me. My card is integrated, neither Nvidia nor ATI I think...does this mean that I will not be able to load Ubunto?

---

### Post by 5-HT on 2006-04-09
[quote= beef thing]hmm, I typed in "startx", however, it returned "bash: startx: command not found" to me. My card is integrated, neither Nvidia nor ATI I think...does this mean that I will not be able to load Ubunto? [/quote]

Looks like X isn't installed (maybe you did an expert install)?
Do you want the default Ubuntu install?
If so type this in: ```
 sudo apt-get install unbuntu-desktop 
``` and enter your password.

This will download and install the all the packages in the stardard Ubuntu install.

---

### Post by beef_thing on 2006-04-09
To taurus, when I was installing Ubunto, I did type in server and then installed it.

---

### Post by beef_thing on 2006-04-09
Ok, let me try to run the LiveCD first then, and then see if the graphic environment would load, oh ya, and also, during the installation, when I typed in "default", apparently it did not let me, saying that default is not recognized...so I installed in server mode

---

### Post by taurus on 2006-04-09
Just hit the enter at the prompt and that would be good for you...  No need to type anything in!

---

### Post by krusbjorn on 2006-04-09
[QUOTE=beef_thing]Ok, let me try to run the LiveCD first then, and then see if the graphic environment would load, oh ya, and also, during the installation, when I typed in "default", apparently it did not let me, saying that default is not recognized...so I installed in server mode[/QUOTE]

When you typed "default", you should just have pressed enter. If you are not in a hurry, you could just reinstall, and press enter when it asks you which type of installation you want. Then everything should work.

---

### Post by 5-HT on 2006-04-09
[quote=beef_thing]Ok, let me try to run the LiveCD first then, and then see if the graphic environment would load, oh ya, and also, during the installation, when I typed in "default", apparently it did not let me, saying that default is not recognized...so I installed in server mode[/quote] 
Try the Live CD to see if everything works.
If it does, boot back into Ubuntu and follow my previous advice in post #7 (sudo apt-get install ubuntu-desktop) to get a nice, working, and full Ubuntu installation which will boot into a graphic environment.

The server install you did is a bare-bones version.

Hope this helps.

*wow, nice to see such a quick reaction with everyone here!

---

### Post by beef_thing on 2006-04-09
[QUOTE=5-HT]
*wow, nice to see such a quick reaction with everyone here![/QUOTE]

Haha, oh ya! Thx a lot for all of your help =] I am still trying it out right now, system is a bit slow. Hopefully it'll work

---

### Post by 5-HT on 2006-04-09
[quote=beef_thing]Haha, oh ya! Thx a lot for all of your help =] I am still trying it out right now, system is a bit slow. Hopefully it'll work[/quote]

If the Live CD works, you can either reinstall or try to update. I'm not sure if you network connection would be automatically set up with the server install, but you can always update by putting the install CD in and doing the command.

---

### Post by beef_thing on 2006-04-09
[QUOTE=5-HT]If the Live CD works, you can either reinstall or try to update. I'm not sure if you network connection would be automatically set up with the server install, but you can always update by putting the install CD in and doing the command.[/QUOTE]

Ya, the Live CD works, I guess then I have to reinstall it in default mode, well, at least I figured that it's not the graphic card's problem.  thx a LOT for your help, greatly appreciated =]

---

### Post by 5-HT on 2006-04-09
[quote=beef_thing]Ya, the Live CD works, I guess then I have to reinstall it in default mode, well, at least I figured that it's not the graphic card's problem. I'll do a reinstall now, thx a LOT for your help, greatly appreciated =][/quote]

No prob, it's great that everything was detected properly. This means you should hopefully have no issues when it comes to the installer configuring your hardware.

---

### Post by beef_thing on 2006-04-09
Also, thx Taurus and krunsbjorn for your help also! Right now I am reinstalling Ubunto like how you guys told me to, lol I never noticed that I didn't need to type in anything...

---

