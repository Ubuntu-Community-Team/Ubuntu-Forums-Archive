---
title: "New linux/kubuntu user needs help"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by mudogg on 2007-03-07
I'm definetly a new user to linux and kubuntu, but i'm having trouble changing my xorg.conf file, or any file for that matter. When i open or create a file, when i try and save that file, i get  permission errors saying I don't have the proper permissions to save this file. I believe that my user account is as an administrator but i'm not really sure what the problem is.

Thanks in advance.

---

### Post by taurus on 2007-03-07
You need to use either sudo or kdesu when you want to edit anything outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aktiwers on 2007-03-07
you need to open the program with a 
```
gksudo
```

Like typing this in terminal:
```
gksudo konqueror
```

Should open your file manager, where you can navigate o the file you need to change.

Or simply type in:
```
[SIZE=-1]**sudo gedit** /etc/X11/**xorg**.conf
```

to edit your xorg.conf file. 
[/SIZE]

---

### Post by taurus on 2007-03-07
> **aktiwers said:**
> you need to open the program with a 
```
gksudo
```

Like typing this in terminal:
```
gksudo konqueror
```

Should open your file manager, where you can navigate o the file you need to change.

Should be

```
kdesu konqueror
```
since he uses Kubuntu.

> Or simply type in:
```
[SIZE=-1]**sudo gedit** /etc/X11/**xorg**.conf
```

to edit your xorg.conf file. 
[/SIZE]
Should never run gedit with sudo or bad things can happen and will happen.  Instead, use either "gksudo gedit" (for Gnome) or "kdesu kate" (for KDE).

```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by mudogg on 2007-03-07
AHHHH!! Thanks very much!! I'm sure there will be more questions to come!


Thanks again.:)

---

### Post by aktiwers on 2007-03-07
upss.. my bad.. thanks for the corrections taurus  :)

---

### Post by taurus on 2007-03-07
> **aktiwers said:**
> upss.. my bad.. thanks for the corrections taurus  :)

No problem, mate.  Hope you don't mind.  ;)

---

### Post by JAPrufrock on 2007-03-07
> **taurus said:**
> Should be

Should never run gedit with sudo or bad things can happen and will happen.  Instead, use either "gksudo gedit" (for Gnome) or "kdesu kate" (for KDE).

Whoa.. that's news to me.  I can't count how many howtos I've read and used that open the text editor with "sudo gedit".   What are the bad things that can happen?

---

### Post by Nythain on 2007-03-07
sudo is more for running terminal commands... while kdesu and gksudo are designed more for launching DE apps... im not sure about anything MAJOR happening... but i have encounterd minor random problems i cant remember at the moment as its been a while now

---

