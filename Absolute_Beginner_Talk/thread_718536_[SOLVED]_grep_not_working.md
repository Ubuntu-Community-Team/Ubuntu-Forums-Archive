---
title: "[SOLVED] grep not working"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Riffer on 2008-03-08
[SIZE="2"]Whenever I try and use grep, nothing happens.  According to synpatic I have it installed.  For instance, if I use the command 
> lspci -grep audio

I get the lspci help list of proper triggers.

Any ideas?
[/SIZE]

---

### Post by Daveth on 2008-03-08
you need to pipe your commands into grep, using those triggers to refine it. So try

lspci |grep audio

this throws out my Creative card for my system.I'm sure this can be more properly explained by hard core linux users!!

---

### Post by prshah on 2008-03-08
Enable "PnP Operating System" or "Plug-n-Play" or "Plug and Play OS" or similar options in your BIOS. If you cannot find such a setting, look for something like a list of IRQ numbers (1-15), and if any of them are set to "manual", change it to "auto"

Cheers,
PRShah

---

### Post by Riffer on 2008-03-08
[SIZE="2"]Tried the pipe trigger and nothing happens, even change audio to video, nothing happens.

My bios is set to PnP.

This weird as I have a pretty standard install.  Do I need the "build essintials"  and all that?[/SIZE]

---

### Post by Keith Hedger on 2008-03-08
try ```
lspci |grep -i audio
```
The -i switch to grep makes it ignore case

---

### Post by Riffer on 2008-03-08
nope that didn't work either.

---

### Post by mikeyphi on 2008-03-08
> **Riffer said:**
> nope that didn't work either.

The previously posted code should work - suggest you copy/paste it into the terminal to eliminate typos.

---

### Post by Hospadar on 2008-03-08
what happens when you pipe it? do you still get the list of triggers? do you get the full output of lspci? 

I you get nothing at all, probably just none of the lines in lspci have "audio" in them.

---

### Post by Riffer on 2008-03-08
[SIZE="2"]All commands that were posted in this thread I cut n pasted right into the terminal.

What is meant by "pipeline" I'm unsure what you mean, but I did cut n paste in your commands.  So I'm at a loss.[/SIZE]

---

### Post by Riffer on 2008-03-08
> **Hospadar said:**
> what happens when you pipe it? do you still get the list of triggers? do you get the full output of lspci? 

I you get nothing at all, probably just none of the lines in lspci have "audio" in them.

[SIZE="2"]AHHH there it is, you're right there is no "audio" in lspci or "video".  I tried "lspci |grep VGA" and up popped my nVidia card.  

Thanks I'm mark it solved.[/SIZE]

---

