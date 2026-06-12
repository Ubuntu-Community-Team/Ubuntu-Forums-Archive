---
title: "sudo gedit does not work in KDE"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by tadashi on 2006-02-20
For some reason sudo gedit does not work in KDE terminal but if I just use gedit it works.  I am assuming this has something to do with paths.  How do I fix this?

---

### Post by codejunkie on 2006-02-20
[QUOTE=tadashi]For some reason sudo gedit does not work in KDE terminal but if I just use gedit it works.  I am assuming this has something to do with paths.  How do I fix this?[/QUOTE]
how are you running the command in the terminal or by pressing alt+f2?

---

### Post by Sutekh on 2006-02-20
You need to use ```
kdesu gedit
``` rather than```
sudo gedit
```

kdesu - KDE superuser (If I'm not off the mark)

---

### Post by Madpilot on 2006-02-20
Isn't the default text editor in KDE called "kate"? 

Assuming I'm right, just use "sudo kate" whenever an instruction calls for "sudo gedit".

There's nothing special about gedit, it just happens to be Gnome's default text editor.

---

### Post by Sutekh on 2006-02-20
True, gedit is the default GNOME editor.  

[QUOTE=tadashi]but if I just use gedit it works[/QUOTE]
If gedit works without the sudo then I assume that it's been isntalled along with KDE.

Still you'd have to use ```
kdesu kate
```

---

### Post by codejunkie on 2006-02-20
[QUOTE=Sutekh]You need to use ```
kdesu gedit
``` rather than```
sudo gedit
```

kdesu - KDE superuser (If I'm not off the mark)[/QUOTE]
```
sudo gedit
```should work in kde as long as it is run through a terminal you only need to add the kdesu prefix to a command if your using the command through the run dialog or a command launcher.

---

### Post by Sutekh on 2006-02-20
I just tried that and it wouldn't work.

---

### Post by codejunkie on 2006-02-20
[QUOTE=Sutekh]I just tried that and it wouldn't work.[/QUOTE]
that's weird, it's always worked for me using that as long as i run it in a terminal, i only have to use the kdesu prefix for desktop launchers and the run command because it won't display the password prompt unless i add it.

---

### Post by manicka on 2006-02-20
in KDE use sudo kate and forget about gedit

---

### Post by Sutekh on 2006-02-20
[QUOTE=codejunkie]that's weird, it's always worked for me using that as long as i run it in a terminal, i only have to use the kdesu prefix for desktop launchers and the run command because it won't display the password prompt unless i add it.[/QUOTE]
My apologies, the user I tried this with was messed up.  I tried it again with a different user and no problems.

I was sure that sudo didn't work in kubuntu and that kdesu was used instead.  
8-[

---

### Post by cotcot on 2006-02-20
In KDE you can also use "sudo kwrite"

---

### Post by aysiu on 2006-02-20
I've never found ```
sudo kate
``` to actually work. Can someone come forward and say, "I've used the exact command *sudo kate* and had no problems"?

In the meantime, I do know that ```
sudo kwrite
``` works just fine in KDE.

```
sudo gedit
``` doesn't work in KDE because *gedit* doesn't exist in KDE.

---

### Post by dvarsam on 2006-02-20
[QUOTE=aysiu]I've never found ```
sudo kate
``` to actually work. Can someone come forward and say, "I've used the exact command *sudo kate* and had no problems"?

In the meantime, I do know that ```
sudo kwrite
``` works just fine in KDE.

```
sudo gedit
``` doesn't work in KDE because *gedit* doesn't exist in KDE.[/QUOTE]

I use the Ubuntu 5.10:

"gedit *name_of_file*" does NOT work with me either...

So, I use "nano *name_of_file*".

But I do NOT know if it is going to work in your case.

---

