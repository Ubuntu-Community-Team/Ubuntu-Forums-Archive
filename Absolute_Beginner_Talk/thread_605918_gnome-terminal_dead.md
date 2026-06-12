---
title: "gnome-terminal dead?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-11-07
i cant seem to use my terminal anymore, i tried to reinstall to no avail
how do i fix this?
am posting screenshot as attatchment

EDIT: i found the problem: the box "run custom shell" box under the preferences was checked, un-checking it fixed the problem;)
i will post a link to the one im talking about shortly...

EDIT NO2: aand, heres the link [http://99bluefoxx.deviantart.com/art/ubuntu-fourms-no3-71848261](http://99bluefoxx.deviantart.com/art/ubuntu-fourms-no3-71848261)

---

### Post by taurus on 2007-11-07
Install another terminal like rxvt using synaptic and see if the new one works or not.

---

### Post by 99bluefoxx on 2007-11-07
is that one similar to the one that just died?

---

### Post by 99bluefoxx on 2007-11-07
ok, so i have KDE installed and the konsole for that works. in addition shell scripts like luanch-wow.sh and hello_world.sh will work. but only premade commands
i cant do anything other than that, no sudo aptitude install, no lsmod, sudo aptitude purge, nothing like that works at all
should i purge and reinstall it
ps, i was following a tutorial that told me to create a file called ".bash_profile"if it didnt allready exist, after i made this is when it stoped working
wont be able to respond for a while as im at school, not on my computer at the moment[windows sux]

---

### Post by taurus on 2007-11-07
What did you put in ~/.bash_profile?  Otherwise, just remove it.

---

### Post by 99bluefoxx on 2007-11-07
a few variations of ```
[FONT=Courier New]export PATH=$PATH=(directory)[/FONT]
```[FONT=Courier New] to automate the addition of directories to search for executables[/FONT]
[FONT=Courier New]and i allready removed it, it still didnt work[/FONT]
 
[FONT=Courier New]im gonna try and remake .bash_profile with [/FONT]```

[FONT=Courier New]if [ -f ~/.bashrc ]; then[/FONT]
[FONT=Courier New]   . ~/.bashrc[/FONT]
[FONT=Courier New]fi[/FONT]

```[FONT=Courier New] in it instead, hopefully that will work[/FONT]

---

### Post by taurus on 2007-11-07
PATH should be in your ~/.bashrc and the syntax that you have in your ~/.bash_profile is not even right.

```
export PATH=$PATH:/first/path:/second_path
```

---

### Post by 99bluefoxx on 2007-11-07
ok, so i tried the rewrite that i mentioned and it still doesnt work
apart from a complete reinstall what might i do to keep gnome-terminal?
can i manually delete all the configuration files and reinstall terminal from scratch?
if so, how can i remove all files for gnome-terminal?
or maby i could copy my user account and all non configuration files, reseting ecerything else

---

### Post by taurus on 2007-11-07
I don't even have ~/.bash_profile because all my settings are in ~/.bashrc.  Delete ~/.bash_profile and log out and back in again and see if gnome-terminal is running now.

---

### Post by 99bluefoxx on 2007-11-07
tried and still failed
so am i totally screwed or is there some comand line i can use for Konsole to purge all gnome-terminal settings from my computer?

---

### Post by taurus on 2007-11-07
What else did you edit besides ~/.bash_profile?

---

### Post by 99bluefoxx on 2007-11-07
nothing, that was the only one.
i can post my .bash_history, _logout and rc, if that will help

---

### Post by 99bluefoxx on 2007-11-07
if anyone has anymore ideas, would be appreciated.

---

### Post by talktechnow on 2007-11-07
Can you run programs directly, ie /usr/bin/... ?

---

### Post by 99bluefoxx on 2007-11-07
tried, still failed, however luanch-wow.sh, and other shell scripts work, as does ALT+F2 and sudo gnome-terminal +"run in terminal"
but for normal comand lines, its useless, and i dont know how to configure other terminal programs to look like my current one

---

### Post by talktechnow on 2007-11-07
How about 'Ctrl + Alt + F1', login and test commands there?
You can return to the GUI using 'Ctrl + Alt +F7'

---

### Post by 99bluefoxx on 2007-11-07
nope, repeate an message saying  ```
 [ ????.??????] PCI_SET_POWER_STATE(): 0000:00:00.0: STATE=3, CURRENT STATE=5
```, whear the ????.?????? are varieing numbers, i am assuming that they must be memory addresses
Ctrl + Alt f2 to 6 and f8+ are the same
if it hasnt been pressed before it says my distro version, and host name@login, then continues scrolling the previously mentioned message

---

### Post by taurus on 2007-11-07
> **99bluefoxx said:**
> tried, still failed, however luanch-wow.sh, and other shell scripts work, as does ALT+F2 and sudo gnome-terminal +"run in terminal"
but for normal comand lines, its useless, and i dont know how to configure other terminal programs to look like my current one

What do you mean by "i dont know how to configure other terminal programs to look like my current one"?

What does your gnome-terminal look like before it went kaput?

---

### Post by 99bluefoxx on 2007-11-07
i mean in terms of how it looks, eg transparent background, color schemes, and difference in those type things[fonts, spacings, ect]

---

### Post by taurus on 2007-11-07
You can do all that with rxvt-unicode terminal emulator.

---

### Post by 99bluefoxx on 2007-11-07
ok, ill try that now, thanks

---

### Post by 99bluefoxx on 2007-11-07
ok, i installed it, but how do i configure it, like the font background and crap
also, is there a easy way to luanch it[other than alt+f2]

---

### Post by taurus on 2007-11-07
You can create a short cut in the upper panel so you run it by clicking it.

If you want to know all the options for it, just run it with

```
rxvt-unicode --help
```

---

### Post by 99bluefoxx on 2007-11-07
ok thank you

---

