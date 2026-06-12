---
title: "[SOLVED] Using Wine to run installed programmes"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-09-04
I've managed to install a program using Wine, but now I can't figure out how to get it to run. A short cut was made in Applications -> Wine -> Programs -> Macromedia but this doesn't do anything when clicked. I've also tried navigating the virtual c drive to double click the .exe file, but it comes up with an error

> Cannot open /home/ps/.wine/drive_c/Progr...reworks MX 2004/Fireworks.exe: No application suitable for automatic installation is available for handling this kind of file.

Does anyone have any clues as to what is going on? Am I going about this all the wrong way?

---

### Post by hyper_ch on 2007-09-04
well, problem is you have spaces in the path -->  Fireworks MX 2004  hence the path actually stops after "Fireworks".

So try to enclose the whole path with double quotes

```

wine "home/ps/.wine/drive_c/Program Files/Fireworks MX 2004/Fireworks.exe"

```

well, correct the path above there to your actual one :)

---

### Post by shearn89 on 2007-09-04
Or you can press alt-f2 and type "winefile", then use that to navigate to and run the program.

---

### Post by NovaAesa on 2007-09-04
When I type the wine "<application path>" into the console, nothing happens, it just starts a new line.

Also, when using winefile, when I double click on the .exe file, nothing happens.

Is there any special configuration that I need to do? (I haven't tried to configure anything yet).

---

### Post by hyper_ch on 2007-09-04
did you run first winecfg?

---

### Post by NovaAesa on 2007-09-05
Ok, I figured out what is going wrong. The version of Fireworks I'm trying to run doesn't work with Wine. (lol I feel silly for not thinking to check that)

Looks like I'll have to upgrade to Fireworks 8.

Thanks to everyone that's helped!

---

