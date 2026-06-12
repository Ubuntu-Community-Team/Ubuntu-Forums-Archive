---
title: "Programs Won't Run Anymore"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by nhandler on 2006-11-10
I have edgy installed on my laptop. I wanted to add files to my video ipod, so I installed gtkpod. That program ran fine. Then, a few days ago, it crashed. Now, it won't launch. I've tried uninstalling it and reinstalling it through synaptic and the terminal. Neither have worked. Then, I moved on to try Amarok. That program ran fine as well. Then, it crashed. And now, it won't launch. I've tried uninstalling and installing it as well. I've also tried restarting/shutting down my computer. Could someone please explain why these programs won't start? I really don't want to mess up any more. Also, could someone help me get these programs running again? 

Thanks.

---

### Post by taurus on 2006-11-10
Open a terminal and run it from a prompt to see what the error message is...

```
amarok
```

---

### Post by nhandler on 2006-11-10
There isn't an error message. It just shows the blinking cursor on the next line. It just keeps blinking until I exit the terminal or hit ctrl+c.

When I type 'gtkpod', I get this error message:
> Segmentation fault (core dumped)


---

### Post by ajm2005 on 2006-11-23
the way to solve the "segmentation fault" issue seems to be to revert to the previous version of gtkpod (0.88.1-1). Uninstall the current version (0.90.x I think) of gtkpod or gtkpod-aac via synaptic. Then go here:

[http://packages.debian.org/stable/sound/gtkpod](http://packages.debian.org/stable/sound/gtkpod)

and download the appropriate .deb file for your machine. (Probably the i386 version). Put it in your home directory, click on it, with a bit of luck a program will open to install the program for you.

See this thread:
[http://ubuntuforums.org/showthread.php?t=248428](http://ubuntuforums.org/showthread.php?t=248428)

It worked for me. :)

As for amarok problems, I can't help you there. I hope you get it working, tho, as amarok is a great program.

---

