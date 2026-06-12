---
title: "what do i do next?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by mental_noise on 2006-01-26
hi, newbie here.

i was able to do a minimal install [(see here)]("http://ubuntuforums.org/showthread.php?t=118448") a few days ago and i was able to install the packages i needed to run ubuntu on fluxbox as indicated [[here]]("https://wiki.ubuntu.com/Installation/LowMemorySystems").

as excited as i was, i entered [FONT="Courier New"]**startx**[/FONT] from the terminal and i was greeted by a dialog box that said something like [FONT="Courier New"]**"cannot find /home/username/.xsession ... there are no window managers installed ... no display managers installed ... blah ... blah ..."**[/FONT] (i apologize but i forgot to note the exact error :rolleyes: ).

anyway, i know i already have [FONT="Courier New"]**fluxbox**[/FONT], [FONT="Courier New"]**x-window-system-core**[/FONT], [FONT="Courier New"]**xdm**[/FONT], [FONT="Courier New"]**dillo**[/FONT] and [FONT="Courier New"]**synaptic**[/FONT] installed so what gives?

i have exhaustively been searching the internet (and also this forum) for some enlightenment but to my dismay i have not quite found the correct documentation to help me out.  i found sites that said to change the [FONT="Courier New"]**.xinitrc**[/FONT] or the [FONT="Courier New"]**.xsession**[/FONT] but i don't know where to find these.

i would really appreciate anybody's help! thanks! :)

---

### Post by adwait on 2006-01-27
those files are in your home directory:
/home/<you username>/<filename>

---

### Post by mental_noise on 2006-01-27
[QUOTE=adwait]those files are in your home directory:
/home/<you username>/<filename>[/QUOTE]
thanks for the reply. do i need to change both [FONT="Courier New"]**.xsession**[/FONT] and [FONT="Courier New"]**.xinitrc**[/FONT] and put [FONT="Courier New"]**exec fluxbox**[/FONT] in both of them?

---

### Post by adwait on 2006-01-27
I have no experience with fluxbox, so you'll have to rely on the HOWTO that you are reffering to on that :)

---

### Post by twisted_steel on 2006-01-27
[quote=mental_noise]thanks for the reply. do i need to change both [FONT=Courier New]**.xsession**[/FONT] and [FONT=Courier New]**.xinitrc**[/FONT] and put [FONT=Courier New]**exec fluxbox**[/FONT] in both of them?[/quote]

I believe just in **.xinitrc**.

---

