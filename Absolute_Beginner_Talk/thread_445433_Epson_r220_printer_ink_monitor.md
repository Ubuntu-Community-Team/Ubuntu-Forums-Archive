---
title: "Epson r220 printer ink monitor?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-15
Printing works well, or it did... Now I have the "ink" monitor light blinking on the printer, & I can't print from a web page, etc. Is there a driver/software to monitor ink levels, i.e. tell me which cart. needs to be replaced, as the standard driver does in windows?

Thanks, discmaster :)

EDIT: - I did find [this]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R220") - is it what I need?

---

### Post by discmaster on 2007-05-16
I did find [this]("http://ubuntuforums.org/showthread.php?t=193863") thread, & it works in the terminal.

However, if possible, it would be nice to have a GUI pgm. that would show a graph of remaining levels; I know there are some out there; anyone recommend one that works great?

:)

---

### Post by discmaster on 2007-05-16
Does anyone here have any experience with these type of ink status monitors?

I found several, one I am looking at is [Inkblot]("http://www.gnomefiles.org/app.php/Inkblot") I see I have to install  libinklevel & GTK + version 2.2.x.

Being a newbie to linux I am concerned about installing things that might "break" something else. Should I go for it?

Thanks, discmaster :)

---

### Post by technotika on 2008-03-05
hi mate

Did you have any luck with that ink monitoring thing? Inkblot...

After finally getting up and running with ubuntu  - printing DVD's with gimp etc  - the only thing left
is to monitor ink levels  - would be greatly appreciated if you could let me know  - or perhaps some other method you found?

Thanks alot!!

Jerry

[email]wheelscene@gmail.com[/email]

---

### Post by discmaster on 2008-03-11
This is what I did to get it working;
> There is a program "escputil" available to download via Synaptic.
It is a Command Line Interface (CLI) program. Run it in a terminal.
I used this command to see if the program would work. It timed out so I powered off then on the printer and it worked.
~>sudo escputil -d -r /dev/usblp0
EPSON Stylus CX3800

This command generated the ink levels.
~>sudo escputil -i -r /dev/usblp0
Ink color Percent remaining
Cyan 76
Yellow 77
Magenta 77
Photo Black 0
~>
Check out the man page for all the commands.

---

### Post by maineman2 on 2008-03-11
I use mtink it was created for epson printers. It works great. It is in the synaptics package manager. Dan

---

### Post by coleyman on 2008-07-21
Has anyone been able to print on the CDs with the Epson R220 using Linux? I can't find any software for that either.

---

### Post by coleyman on 2008-07-22
Never mind my other post. I figured it out, configuring the settings for CD media in Guttenprint.

---

