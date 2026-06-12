---
title: "How do I run a program from the terminal?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-08-07
Say for example I wanted to start up Firefox from the terminal, how would I go about doing that?

---

### Post by echo $USER on 2006-08-07
> **Scintillement said:**
> Say for example I wanted to start up Firefox from the terminal, how would I go about doing that?

just type in > firefox or > firefox & to run it in the background of the terminal.

---

### Post by arjun.shankar on 2006-08-07
'firefox' on the prompt will be just fine.

---

### Post by arjun.shankar on 2006-08-07
Okey! I'm getting into the bad habit of replying simultaneously with someone else.
Doesn't hurt though!

---

### Post by louis_nichols on 2006-08-07
the only thing is, with the last option, firefox will close if you close the terminal. it's a gnome thing, I think. there is a way around that, but I don't remember which one.

cool thing is autocomplete. just write first few letters and press tab.

the command line is a pretty cool thing. comming from windows, it's hard to believe that there are things MUCH easier done in terminal window, with a few commands, than with any GUI. it's true, though.

---

### Post by kingbilly on 2006-08-07
For firefox you can just type firefox.  For some programs, you need to know where the executable for them is located.
```
 /usr/games/tuxracer
```

Other programs may have an entry in /usr/bin and then you can just type the name in the terminal. Firefox is one of them.
```
 gaim 
```

---

### Post by davebgimp on 2006-08-07
> **louis_nichols said:**
> the only thing is, with the last option, firefox will close if you close the terminal. it's a gnome thing, I think.

It happens regardless of Gnome.

---

### Post by louis_nichols on 2006-08-07
> **davebgimp said:**
> It happens regardless of Gnome.

actually... no. The same thing doesn't happen in KGE's konsole and probably others.

---

### Post by Scintillement on 2006-08-07
Either way when I close the terminal Firefox stays open.

Um what is the difference when running it in the background? What does that mean?

---

### Post by davebgimp on 2006-08-07
> **louis_nichols said:**
> actually... no. The same thing doesn't happen in KGE's konsole and probably others.

You mean KDE, I assume and yes it certainly does happen as I only use Kubuntu and can vouch for it. Konsole and Gnome's terminal application just lets you run a terminal session from within the GUI. You close the application, the terminal session is ended, thus killing any programs running in the forefront of that session, hence a lot of people prefer to use the '&' to avoid accidentally closing a program unintentionally.

---

### Post by kingbilly on 2006-08-07
> **Scintillement said:**
> 
Um what is the difference when running it in the background? What does that mean?

It leaves your terminal free to run other commands.  You can actually bring them back to the forground if you wanted, but you probably would not need to if the program you are running has a gui.  

Also as davebgimp pointed out, if you run it in the background you can avoid having the program close when you close the terminal that launched it.

---

### Post by kebes on 2006-08-07
You can also use Alt+F2 to bring up a "Run..." box that you can then run a single command from. If you start Firefox (or whatever) from this box, you don't have to worry about it closing when you close a terminal or whatever.

---

### Post by Scintillement on 2006-08-07
When I run Firefox through a terminal I opened by going to Applications>Accessories>Terminal and then typing in Firefox it opens Firefox.

Now if I close that terminal it does not close Firefox, Is that normal?

---

### Post by Scintillement on 2006-08-07
Hmmm nevermind, it does close it.

If I had another Firefox window opened via it's icon first, and I then run it from the terminal (giving me a second firefox window) neither closes when the terminal is closed though.

---

### Post by flash47 on 2008-06-07
How do i open "sessions" from terminal?

---

### Post by mgmiller on 2008-06-08
Just hit alt/F2 and either pick the command from the list or type "firefox" (without the quotes) in the box at the top.

---

