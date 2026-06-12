---
title: "GTK problem with KDe"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-07-09
Hi,
As you see from my signature I am using Kubuntu Fiesty Fawn. Now, whenever I use any prgrams that were created for GNOME using GTK, I get blank dialog boxes or sometimes they dont even work. Examples include gorphan, azureus, gksu etc.

What happens is that there the dialog box is black in color and blank. Except for the space where I need to enter anything and the OK and CANCEL buttons. 

Any idea how I can fix this?

Thanks.

---

### Post by KIAaze on 2007-07-09
This is not normal.
Did you install the programs using a package manager?
They should have installed the necessary dependencies normally.

Make sure that you have at least libgtk2.0-common and libgtk1.2-common installed.

---

### Post by linuxnovice on 2007-07-09
Yes I installed the packages using Adept. And I checked that I have libgtk2.0-common. I didnt have libgtk1.2-common installed. I installed it and tried opening gorphan and it is same as before. The window is blank and I cant read what is being asked.

The weird thing is sometimes if I select the words on a hunch on where they will be they get highlighted as if you are looking at something with the same background and same font.

Any other suggestions?

---

### Post by RomeReactor on 2007-07-09
Hi. I don't have KDE installed right now, so I can't be specific about this; however, go to the control panel (or system preferences, can't remember the name, it's the application that let's you change the **appearance** of KDE). There has to be a left panel and in it an option to choose a GTK engine for programs running it; try changing the engine to "Clearlooks" and see if you still have trouble. Also, do you have Beryl or Compiz enabled?

---

### Post by KIAaze on 2007-07-09
If it's the fonts/themes as you suggest, you might want to try changing them.
Could you try running GTK apps in other KDE distros to see if it's hardware related or not? (or theme related)

Otherwise I would suggest asking on one of the GTK mailing lists: [http://www.gtk.org/mailinglists.html]("http://www.gtk.org/mailinglists.html")
[email]gtk-list@gnome.org[/email] might be the best at first.

Or report it as a bug on the Ubuntu, Gnome or GTK buglist. I don't know which is best.

---

### Post by linuxnovice on 2007-07-09
Thanks everybody. Romereactor's suggestion solved it. I dont know how exactly it is solved :) but everything seems to be ok now. Ofcourse, if I encounter the problem again i will have to ressurect this thread

---

