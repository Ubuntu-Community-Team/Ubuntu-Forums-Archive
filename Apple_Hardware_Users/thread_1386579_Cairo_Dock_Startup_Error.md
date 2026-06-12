---
title: "Cairo Dock Startup Error"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by bhj6268 on 2010-01-20
When Cairo Dock launches at startup it comes up with a Error Box that says this:

[I]OpenGL allows you to use the hardware acceleration, reducing the CPU load to the minimum.  It allows some pretty visual effects to Compiz.

However some cards and/or their drivers don't fully support it, which may prevent the dock from running correctly.

Do you want to activate OpenGL?
(To not show this dialog, launch dock from the Application menu, or with the -o option to force OpenGL and -c to force cairo.)[/I]  It then asks YES or NO!

What can I do to get rid of this text box?

---

### Post by linuxopjemac on 2010-01-21
in "Startup applications" under System -> Preferences you can add an entry for cairo-dock. As command I use
```
cairo-dock -c -o
```

The otion -c is to force him I guess without asking.

---

### Post by fabounet on 2010-01-21
as it is said in the dialog box (this is not an error box)
> (To not show this dialog, launch dock from the Application menu, or with the -o option to force OpenGL and -c to force cairo.)

so add either the option -o (opengl) **OR **the option -c (cairo) to the startup command.

The easiest way is, if you didn't add it to startup yet, to just right-click on the dock, ad select "launch on startup"

---

### Post by linuxopjemac on 2010-01-21
I now tried only with the -o option, and it works just the same. I guess fabounet is right, as the -o option was after the -c opton and therefore I got openGL.

---

### Post by bhj6268 on 2010-01-21
Hey guys thanks so much.  The -o option worked perfectly!  I'm very new to Linux but love what I'm seeing so far.  For all the people I know that has a PC I'm going to suggest Linux as a Windows Alternative!

---

### Post by linuxopjemac on 2010-01-21
People are seeing the light only after they found out themselves, like you, in my honest opinion.

---

