---
title: "Problems Booting"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-02
During the boot procedure I received an error stating that the X Server could not be started due to it not being setup correctly... it also states that the X Server will be disabled, and that I should restart GDM when it is configured correctly. 
It then gives me a command prompt to login and I think I'm using the terminal. I can login an see the documents in my desktop and such but there is no GUI. I just see the terminal.

What to Do, Oh! What to Do.1?1

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Mustard on 2006-01-02
type this command in terminal...

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the default options for any questions it ask that you don't know the answers to.  When you have finished, press ctrl+alt+backspace to restart X.  Or alternatively, via the command line, restart X with the command..

```
sudo /etc/init.d/gdm start
```

---

### Post by Jaygo333 on 2006-01-02
will try, give sec to restart computer and input in terminal.
In windows(bleH)  right now.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Jaygo333 on 2006-01-02
[QUOTE=Mustard]type this command in terminal...

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the default options for any questions it ask that you don't know the answers to.  When you have finished, press ctrl+alt+backspace to restart X.  Or alternatively, via the command line, restart X with the command..

```
sudo /etc/init.d/gdm start
```[/QUOTE]

Thanks for the advice. It worked. Now writing this in ubuntu. Thanks a lot.

Just one question. When booting, at GRUB. I get an error taht when starting system, the system doesn't exist but whn choosen the error again, the system boots. I have to choose a system twice to boot into it. Is there also a wa to have only two options at startup. There are too many in my opinion. Also, is there any GRUB GUI, so that I could only have ubuntu and windows as the options.

Thanks a lot for the other advice. Worked very well.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

