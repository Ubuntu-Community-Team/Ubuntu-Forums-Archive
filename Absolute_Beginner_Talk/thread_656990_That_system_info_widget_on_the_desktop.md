---
title: "That system info widget on the desktop?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Locutux on 2008-01-03
I'd like to have a system info on my desktop as well/anyone else. :) But the thing is, I don't know where to get it, or how to set it up. 

I'd appreciate your help. Thank you.

---

### Post by NilsE on 2008-01-03
One option is gkrelm which is in the repositories.

---

### Post by jan quark on 2008-01-03
Do you mean the system monitor? Applications > System > System Monitor.

or another application?

some more info please:)

---

### Post by Locutux on 2008-01-03
@NilsE, I think it's not in the repositories. It says "Couldn't find the package gkrelm".

@jan quark, I don't have that there.

---

### Post by Locutux on 2008-01-03
Ok, I found the System Monitor, but how do I put it on the desktop?

---

### Post by metalpancake on 2008-01-03
You can try gDesklets available in the repos. 

It basically allows you to put widgets onto your desktop, many of which can display system information:)

---

### Post by NilsE on 2008-01-03
> **Locutux said:**
> @NilsE, I think it's not in the repositories. It says "Couldn't find the package gkrelm".

@jan quark, I don't have that there.

Sorry, it's 2 l's    gkrellm

It will provide more info than the system monitor applet.

---

### Post by argie on 2008-01-03
I've tried Gkrellm and it's very good, nice and useful. 

There's also another program worth trying: conky. [Here's a nice thread full of some nice conky settings]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

---

### Post by Locutux on 2008-01-03
Thanks everyone.

gkrellm works great, but showed this warining:

```
(gkrellm:11757): Gtk-WARNING **: Unable to locate theme engine in module_path: "           murrine",
```

It works anyway. Also, can I embed it in the desktop, without gkrellm tab in my down panel?

---

### Post by Locutux on 2008-01-03
Also, I cannot open it without tying it in the shell. And of course, when I close the shell, gkrellm closes as well. How can I add it in the Applications menu?

---

### Post by Locutux on 2008-01-03
Sorry for double posting, but when I try to start gDesklets via Applications menu, it stucks at gDesklets shell.

Also, when I try to run it via the Konsole, it says this:

Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the proble

---

### Post by argie on 2008-01-03
> **Locutux said:**
> Also, I cannot open it without tying it in the shell. And of course, when I close the shell, gkrellm closes as well. How can I add it in the Applications menu?

One simple solution to that is to Hit Alt-F2 and type gkrellm. 

If you really want a launcher, right click on the Application menu and choose Edit Menu. Then choose the appropriate category from the left bar and hit the New Item button on the right. Then enter the following:

Type: Application
Name: GKrellM (Or whatever you want for the name)
Command: gkrellm
Comment: Type what you want here. It's the tooltip to remind you what the program does.

Now hit Ok.

---

### Post by NilsE on 2008-01-03
> **Locutux said:**
> Also, I cannot open it without tying it in the shell. And of course, when I close the shell, gkrellm closes as well. How can I add it in the Applications menu?
You can start it automatically by going into

System > Preferences > Sessions and do an add on the Startup Programs tab

Name it whatever you like and the command line is just gkrellm. I don't think you need sudo in front of it.

Also: I think you can change the gkrellm theme in it's properties.

---

### Post by Locutux on 2008-01-03
Thanks everybody. Again. :)
argie's advice worked.

Now, can anyone help me with this:

> **Locutux said:**
> When I try to start gDesklets via Applications menu, it stucks at gDesklets shell.

Also, when I try to run it via the Konsole, it says this:

Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the proble

---

