---
title: "windows manager question."
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2006-08-17
i am pretty new to linux overall and have a few questions about how things work. 

i would like to know if i can install as many windows managers as i want? right now i have installed the default gnome desktop and have added the xubuntu xfce WM as well.  i can just add them through aptitude or apt get right? if i dont like them i can just remove them and all is back to normal? are there any ill effecs of adding too many or anything that i should be aware of before i start adding everyone i can find.

any recommendations for a lightweight WM? i am running this on a machine w/ 866 mhz & 256 mb of ram. i am really looking to run a file server here in the house and maybe a webserver too.

---

### Post by meng on 2006-08-17
Yes, as many as you like. If you're thinking of removing later, aptitude is probably better so that you aren't left with lots of orphaned dependencies.

I've been playing around with XFCE and fluxbox of late. Both seem okay (I guess XFCE is more polished).

---

### Post by zxee on 2006-08-17
You shouldn't have any problems beyond some system bloat. And since your only using one DE at a time it no big deal IMO.
For a lightweight Desktop Environment you might want to check out fluxbox. 
Homepage here: [http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/) and available through apt/synaptic.

---

### Post by 23meg on 2006-08-17
For some detailed info about window managers see [this site]("http://xwinman.org/").

---

### Post by pjones0404 on 2006-08-17
thanks for the help guys. :D 

just to make sure that i understand. all i have to do is "aptitude install fluxbox" or whatever one i want and it will install it? does it only install the dependencies that fluxbox uses and adds them to the system files? it knows automatically what dependencies you already have and only gets what it needs right? 

when you say system bloat you are only referring to the amount of storage that the install is taking up right? it is not like in a windows where you can have all these apps running at the same time and it slows everything else down. 

just so you know i have also installed automatix so i think all that my repositories are set up already. 

thanks again. :smile:

---

### Post by 23meg on 2006-08-17
> 
just to make sure that i understand. all i have to do is "aptitude install fluxbox" or whatever one i want and it will install it? does it only install the dependencies that fluxbox uses and adds them to the system files? it knows automatically what dependencies you already have and only gets what it needs right?That's right.
> 
when you say system bloat you are only referring to the amount of storage that the install is taking up right? it is not like in a windows where you can have all these apps running at the same time and it slows everything else down.That's right for window managers. If you mix and match desktop environments and, say, use KDE apps in GNOME, you'll have some extra system load as well.

---

### Post by pjones0404 on 2006-08-18
> **23meg said:**
> That's right.
That's right for window managers. If you mix and match desktop environments and, say, use KDE apps in GNOME, you'll have some extra system load as well.

i really appreciate the help. these are thing that i know should be easy to understand but i just dont get it. :confused:  i have a bunch more questions. thanks for taking the time. 

when i want to run kde apps in gnome do i need to have the entire KDE installed or can i only choose the apps that i want? 

after the app i need is installed via aptitude will it automatically show up in the gui? 

does kde and gnome run on entirely different dependencies/libraries? does it create any types of problems running apps in a non native enviroment? how does this defer from running a windows manager? :-k is the DE a more full featured enviroment where the WM u have to add the different apps to do different things?

i know it is hard to answer all these questions but if u could generalize or point me to a resource that talkes about these types of questions. 

:D

---

### Post by meng on 2006-08-18
If you install KDE apps to run in GNOME, only the required KDE libraries will be installed for that app. Most apps will automatically show in the menu, but many require you to edit the menu. GNOME and KDE have different dependencies; DEs are more integrated than WMs.

---

### Post by 23meg on 2006-08-18
> after the app i need is installed via aptitude will it automatically show up in the gui? You mean window managers? Yes, most will automatically add an entry to your display manager so you can easily choose them.
> 
does kde and gnome run on entirely different dependencies/libraries? Almost entirely. > does it create any types of problems running apps in a non native enviroment? 
Typically no, except the extra memory taken up by the extra libraries loaded. Menu clutter because of extra apps installed by additional desktop environments is a common complaint but you can just edit the menus manually in the worst case.
> how does this defer from running a windows manager?  is the DE a more full featured enviroment where the WM u have to add the different apps to do different things?Window managers do just what the name says: they manage windows. Desktop environments have their own widget toolkits (QT for KDE, GTK+ for GNOME and XFCE), their own window manager (Kwin in KDE, Metacity in GNOME) and their own suites of applications.

[This thread]("http://www.ubuntuforums.org/showthread.php?t=87276") may clarify things further for you.

---

