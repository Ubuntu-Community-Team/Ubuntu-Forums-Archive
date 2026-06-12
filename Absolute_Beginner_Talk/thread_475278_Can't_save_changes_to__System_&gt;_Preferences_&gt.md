---
title: "Can't save changes to | System &gt; Preferences &gt;Sessions!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-15
For some reason, whenever I go to system >> preferences >> sessions 

and try to add a startup program like this

```
Name = Beryl

Command= beryl-manager
```

and hit OK then Close, it removes it ( I know because I went back into it, and, no Beryl) 

I also tried adding a Avant Window Navigator Entry, and that didn't work either. I am assuming logging into root would only change the settings for the root account, right? 

It's very annoying, as I am now very used to and comfortable with Beryl. 

How can I change this? Please Post an idea or link to another thread where this same issue has been solved. Also, my Ubuntu Version is Feisty (if it makes a difference:-k). 

-ts51

---

### Post by merlyn on 2007-06-15
Open the session manager applet again & go to the third tab "Session Options".

There is a button to "remember currently running applications", click this to save your session settings.

Cheers.

---

### Post by ts51 on 2007-06-15
If I reboot, everything running currently in the background (beryl, pidgin, network) will automatically load? Right? Or have I misunderstood....

---

### Post by ts51 on 2007-06-15
Going to attempt a reboot, post my results shortly.

---

### Post by ts51 on 2007-06-15
It didn't work! And now, when I start up, I don't have any tool bars, and my tasks don't display in my bottom panel. Also, my workspaces don't work! What can I do to resolve this? This is extremely annoying, and I hate going into to the terminal every time just to type in 

```
 beryl-manager 
```

---

### Post by merlyn on 2007-06-15
Hmmm, you've done everything that I did, & Beryl starts for me.

Did, saving the session, keep the entry for Beryl in the Startup Programs?

Also, [this]("http://ubuntuforums.org/showthread.php?t=357501&highlight=beryl+latest") thread may help, as it's the one that got me started with Beryl, it's for Nvidia cards however, so if you have an ATI card I cannot help.

Cheers.

---

### Post by ts51 on 2007-06-15
First question: No

I'll check out that thread, but on my linux/xp system (the one I can't get Beryl on) I have an intel card.

---

### Post by merlyn on 2007-06-15
> **ts51 said:**
> First question: No

I'll check out that thread, but on my linux/xp system (the one I can't get Beryl on) I have an intel card.

Gosh, it didn't save. I'm stumped on that one sorry.

Hopefully you'll have better luck in your search.

---

### Post by ts51 on 2007-06-15
I just went to this directory: 

```
/etc/init.d 
```

Which I think has the startup files, but it's missing Beryl. Could someone go to that directory and upload their beryl script, or would that just make a huge ubuntu mess?

---

### Post by merlyn on 2007-06-16
I don't have any beryl entries in /etc/init.d. It would seem that it isn't required.

How did you install beryl?

---

### Post by ts51 on 2007-06-16
I'm pretty sure I just installed using this guide: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by ts51 on 2007-06-16
Is there something in the guide above that I missed, that says how to get it to run on startup?

---

### Post by merlyn on 2007-06-16
That guide seems overly complicated, and is possibly outdated.

Search the Ubuntu forums for Beryl, and particularly [this]("http://ubuntuforums.org/forumdisplay.php?f=223") sub forum, as it deals specifically, with desktop effects and customisation.

Cheers & good luck.

---

### Post by ts51 on 2007-06-16
Ok, I got it to work. I just logged out, went to select session, and clicked XGL. Then, when I entered my username and password, it asked me if I wanted to make XGL my default session. So, for now at least, it is default. 

-ts51

---

### Post by thecure on 2007-06-17
I have four computers running feisty and on one it wont save anything to the start up sessions... I wonder if logging out and to the xgl session will work for me also... I'll try when I get back home.

---

### Post by peterbakker on 2007-06-18
I have the same problem, both 'save current session' and manually ad programs on startup list System>Preferences>Sessions don't work. The startup list in Session is back to standard when ik open it after adding one or two programs, so it 'forgets'

---

### Post by Faust942 on 2007-06-19
Same here. 

I have so many programs I'd like to start when I log in! 

I want to add this cool calendar program (rainlendar) to my Sessions list. I add everything correctly, but when I start up the computer back it doesn't start up with it. How do I actually add it to the start-up? 

I've clicked Save and selected the Automaticly Save Sessions box, but still doesn't work.

Help! :(

---

### Post by jasonwert on 2007-06-22
I was having this same problem and this [entry fixed it]("http://ubuntuforums.org/showthread.php?t=286883"). It was caused by the ~/.config/autostart folder having root owner permissions. Fix this and Sessions works fine.

---

### Post by Pat123 on 2007-06-25
Thanks a lot jason !! That helped me :)

---

### Post by Faust942 on 2007-06-26
Thanks to RSX311 and Jason for the help.

I added Gmail Notify and Rainlendar2 to my startup session. :p

---

