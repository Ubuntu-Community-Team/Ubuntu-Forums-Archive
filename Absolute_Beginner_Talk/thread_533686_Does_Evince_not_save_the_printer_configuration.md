---
title: "Does Evince not save the printer configuration?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by stefangachter on 2007-08-24
I have basic question about printer configuration in ubuntu. I already asked a similar question beforehand, but did not get an answer.

I am using evince, but each time I make a print out I have to choose afresh my preferred settings. Evince seems not to remember the settings of the last time. Ubuntu provides a printer manager in the menu System -> Administration -> Printing. However, the settings done there are not considered in evince. Evince is always using the default configuration.

Is there a possibility to chance the defautl printer configuration in evince? Why are the settings of the printer manager not considered by evince, or other programs? 

Maybe I missunderstand something, but under Windows this was never a problem, in general the user defined settings were considered by each program.

Thanks for any hint, Stefan

---

### Post by cmnorton on 2007-08-25
You might want to start here.
[http://live.gnome.org/Evince](http://live.gnome.org/Evince)

---

### Post by stefangachter on 2007-08-28
Thanks for the hint, but I couldn't get the information i need from there. Actually, it is not a particular problem of evidence, it seems to be a general trait of ubunutu. Maybe it should be like that, but don't understand why it should be like that.

Again, it is possible to configure the printer settings in System -> Administration -> Printing. For example, let's take the generic pdf-cups printer. It is possible to set the paper size to A4 as default. However, it I print a test page from the same menu, then the paper size is US Letter and the print out is not centered (see file below). But why the configured settings are not considered? I get the same result when doing a test print on a real printer.

As I can observe, always the default printer settings of each printer are used but not the one pre-configured by the user. If I am correct, then why providing a configuration menu? 

Maybe I misunderstand something, but simply i want to know, if i am not the only one who is confused. Does somebody have the same "problems"? Somebody a hint?

Thanks, Stefan

---

### Post by stefangachter on 2007-08-28
Just to be more specific... The settings of the CUPS manager at [http://localhost:631/](http://localhost:631/) are NOT the same as for the genome printer manager (see attached screenshot). And I would like to know why? In my opinion, the CUPS configuration and the genome printer manager configuration should be the same!.

Apparently, people out there seem not to have these problems...

---

### Post by stefangachter on 2007-08-28
The configuration in the CUPS web interface works perfectly (see attached file)t! So, why does the Genome CUPS manager not work properly?

---

### Post by stefangachter on 2007-08-28
(the printout...)

---

### Post by stefangachter on 2007-08-29
This problem is now reported here:

[http://bugzilla.gnome.org/show_bug.cgi?id=393293](http://bugzilla.gnome.org/show_bug.cgi?id=393293)

Still, either this problem is not common at all or people simple ignore it. Anybody else has the same problem out there?

---

### Post by stefangachter on 2007-08-29
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=393293](http://bugzilla.gnome.org/show_bug.cgi?id=393293)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				...

---

