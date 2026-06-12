---
title: "[SOLVED] running foxfire/mozilla in terminal"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Snoreis on 2008-02-01
Hi, so I screwed up my laptop, and can only run it in terminal mode. 

What is the command to run Foxfire/mozilla from the terminal.

I need a browser to copy and pase some information from the xorg.conf file.

Thanks

---

### Post by jaytek13 on 2008-02-01
```
./firefox
```

---

### Post by Whiffle on 2008-02-01
Can't, they don't have a terminal mode as far as I'm aware.  But lynx or links2 work under terminal, not sure about copy paste though.

---

### Post by sports fan Matt on 2008-02-01
can you try a sudo apt-get install firefox?

---

### Post by Snoreis on 2008-02-01
>  "can't, they don't have a terminal mode as far as I'm aware. But lynx or links2 work under terminal, not sure about copy paste though."


Well its the terminal failsafe mode that you can select at login.

Right now its the only thing that works

---

### Post by PinkFloyd102489 on 2008-02-01
Lynx is for terminal. Rather basic but you can do normal text-based stuff.

---

### Post by Snoreis on 2008-02-01
Ok, so I'm dyslexic, I was typing foxfire, and not firefox  

Whoops, 

Thanks guys

---

### Post by Nythain on 2008-02-01
links2 is pretty groovy command line web browser, and i think elinks or links2 even supports images if you have the right supporting apps installed...

they are all UGLY and a bit tricky to get used to, but when you dont have a choice, they can be real lifesavers

---

### Post by seanc7 on 2008-02-01
Do you need a text editor or a web browser?

If you need a text editor, you can use "nano" It should have been part of the default Ubuntu install. The interface isn't like Notepad or anything but it will get the job done.

---

### Post by Snoreis on 2008-02-01
Well I needed a webbrowser.  I can open files In a text editor.


Is there anyway to open more than one terminal so I can run a browser and a text editor at the same time?

---

### Post by weaverryan on 2008-02-01
If you're still running normally, the terminal has multiple tab options.

I'm assuming, since your messing with xorg, that you're far from "running normally"

In that case, ctrl+alt+f# will do it for you. The f#'s act as "tabs" if you will - allowing you to have a whole bunch of different terminals at the same time.

For example, once you're at the terminal, hit ctrl+alt+f3 - all of a sudden you'll see a new terminal. Your original terminal is f4, I think, so you might have to hit a couple to get back to where you started.

---

### Post by Snoreis on 2008-02-01
Very interesting,

Thanks

---

### Post by Dr Small on 2008-02-01
There is also screen:
```
screen
```

---

