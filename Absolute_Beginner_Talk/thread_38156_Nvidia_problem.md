---
title: "Nvidia problem"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by served on 2005-05-30
I installed nvidia drivers but now when i start up my gnome then there is no gnome.
Only thing what apares is nvidia picture and thats all.
How to fix it?
Add: I dont know how to get in the terminal to dsiable that screen, i ve got commands but how and where should i write it when i dont know how to open terminal.

Actually i only need to know a way how to open terminal and write there theses commands. I only have install cd and live cd.

---

### Post by served on 2005-05-30
up

---

### Post by nocturn on 2005-05-30
Pressing CTRL-ALT-F1 will get you a console.

You can login from there.

---

### Post by served on 2005-05-30
but i recive a warning that i cant open display setings.
Shoul i disable it first and then edit it?

---

### Post by nocturn on 2005-05-30
[QUOTE=served]but i recive a warning that i cant open display setings.
Shoul i disable it first and then edit it?[/QUOTE]

What warning did you get?
Did it occur when you pressed the sequence I gave?

You can also kill the X-server (at the Nvidia logo) by pressing:
CTRL-ALT-BACKSPACE

---

### Post by served on 2005-05-30
warning - canot open display

ill try that killing operation.

i want to do that- sudo gedit /etc/x11/xorg.conf

---

### Post by served on 2005-05-30
sad.
Not helping.
I tried that backspace thing it just turned it on for a second and then it was back on.
It was litlle my shit too bcs i didnt disable it in the firstplace but i diddnt know :neutral:

But maybe some one knows what i should do?

---

### Post by crane on 2005-05-30
So if you are looking at the nvidia screen and you hit[color=blue] ctrl>alt>f1 [/color]you should drop ti console.
Then Log in and type [color=blue]sudo vi etc/X11/xorg.conf[/color]
that will open a text editor where you can edit the file.
When your done hit [color=blue]shift ZZ[/color] to close and save.

now you can type [color=blue]alt>f7[/color] to return to you normal desktop.
Or hit [color=blue]ctrl>alt>backspace[/color] to restart the xserver.

I would look at your driver in the xorg.conf maybe change it back to nv from nvidia and see if it startes up!

---

### Post by served on 2005-05-30
now im really mad bcs my keyboard is not responding when that vidia f***k gomes on  ](*,) 
DAMN
I guess i have to start using windows again bcs this is so .....
But if some one knows where i can get a disk and boot from that then let me know.

---

### Post by served on 2005-05-31
i found a solution :)  i wont install it bcs when i disable that nvidia screen then it wont start either.

---

