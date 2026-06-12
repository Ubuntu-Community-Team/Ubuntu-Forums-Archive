---
title: "Error: No Suitable Application"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-08-14
I have Windows XP and Ubuntu 7.04 working well on my hard drive.

I installed wine (off synaptic package manager) and then i tried running xfire (an IM service for gamers) and i get an error. the same error occurs to any program i try to run that's on my windows partition. when i run for example halo or anything i get the same error. I tried restarting. still got the error. Tried removing wine completly, then restarting, then installing, then restarting. Nothing Happens, I still get the error.

[IMG]http://img527.imageshack.us/img527/571/error00nn2.png[/IMG]

Then i tried opening a terminal, typing in 
> nick@nick-desktop:~$ wine /media/disk-2/Program Files/Xfire/xfire.exe 



but I get
> wine: cannot find '/media/disk-2/Program'


Please Help!

---

### Post by MenZa on 2007-08-14
The error you're getting when attempting to run it from a terminal, is that it sees two different targets; /media/disk-2/Program and ./Files/Xfire/xfire.exe. To resolve this, type:

```
wine "/media/disk-2/Program Files/Xfire/xfire.exe"
```

However, there is another issue; you should never run applications in wine from a Windows partition(!). It'll be missing the required registry keys in many, many cases.

---

### Post by WebSiteGuru on 2007-08-14
```
wine "path/to/your/file/xfire.exe"
```

not

>  wine /media/disk-2/Program Files/Xfire/xfire.exe

---

### Post by Alterax on 2007-08-14
It's because of the space in program files.  Add a backslash at the end of program\  and then a space before files.  This is an escape character to let the shell know that the next part is a continuation of the path.

---

### Post by Hospadar on 2007-08-14
If you can, try installing it with wine and then running it from there, generally things work a lot better that way.

---

### Post by RomeReactor on 2007-08-14
Hi. Just as **Alterax** said, try running it like this:
```
wine /media/disk-2/Program\ Files/Xfire/xfire.exe
```

---

### Post by BatsotO on 2007-08-14
nice thing about command line :
type /me(press tab) = /media/
the rest of the line follow the same drill.

as far as i know there are some programs in windows that can run fairly well just by copying the whole program folder,  but same require direct installation. you can try copying the program folder from your windows partition to your home folder, but be aware with the license.

---

