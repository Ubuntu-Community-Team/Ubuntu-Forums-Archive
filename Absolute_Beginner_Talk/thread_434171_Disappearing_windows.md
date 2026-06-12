---
title: "Disappearing windows"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2007-05-05
Today I logged in and I was taking a look at the different themes, and the frames for my windows disappeared.
Along with the icons for close, maximize and minimize
How can I reset my windows?

I already switched my theme to the ubuntu default theme.

---

### Post by 67GTA on 2007-05-05
Try running "metacity --replace" in a terminal window. If you are using compiz or beryl they sometimes cause this problem. Do a google search for solutions for them.

---

### Post by dunklegend on 2007-05-05
Thanks man, that line did it.

Can you tell me what did I just did?

I want to learn the command line but I don't know what the commands do.

Thanks in advance :)

---

### Post by 67GTA on 2007-05-05
Metacity is the default window manager and the --replace command tells the OS to replace it with what you specify. Sometimes there are bugs like that and that command will basically reset the metacity window manager. Sometimes you can reboot and fix that also. The way I learned the command line was to create a file and copy and paste every command someone told me to use, or that I ran across on the forums and paste it in that file with a brief explanation of each. That way I could open the file when I needed a command and copy and paste them until they were comitted to memory.

---

### Post by walsworth on 2008-01-14
> **67GTA said:**
> Try running "metacity --replace" in a terminal window. If you are using compiz or beryl they sometimes cause this problem. Do a google search for solutions for them.
That solution worked for me, too. Thanks! Only problem is, now I'd like to go back to my desktop cube [4 screen version] and it's not seeming to work as it did before [being able to see the cube, rotate it, etc. Is that the price I pay, or is there a way to make both work?

---

### Post by bumanie on 2008-01-14
Are you using an nvidia graphics card?

---

### Post by Faud on 2008-01-14
Did you go to system-->preferences-->appearance and turn your visual effects back on ? and do you have CCSM installed ?

---

### Post by mobileking on 2008-01-14
i too had the same problem !

---

### Post by walsworth on 2008-01-14
Figured it out... thanks!

---

### Post by seventhc on 2008-01-14
> **67GTA said:**
>  The way I learned the command line was to create a file and copy and paste every command someone told me to use, or that I ran across on the forums and paste it in that file with a brief explanation of each. That way I could open the file when I needed a command and copy and paste them until they were comitted to memory.
Good idea, I basically do the same thing, but I use my .bash_history for the file. I think it's the same thing though.
Once a week, I back up my .bash_history file to usb and it is commented, so whenever i run a previous command, the comment also shows so I can see why the heck I'm doing it in the first place.

edit..note...I set my bash history to something like 10,000 though by default i think it only saves 500

---

