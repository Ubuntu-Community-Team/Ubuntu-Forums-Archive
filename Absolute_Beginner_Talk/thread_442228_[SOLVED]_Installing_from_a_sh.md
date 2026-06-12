---
title: "[SOLVED] Installing from a sh?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-13
I've downloaded a .tgz to my desktop and extracted it to the desktop

inside the folder is a file extension sh using the instructions in [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) the install appears to run and the application starts


I assume that's not right as I need to do the same in Terminal to get it to run

How do I actually install the application into the system

Thanks

And a thank you after having installed Ubuntu oveer the last week - it has been most informative just reading and absorbing information from the threads - it's made everything seem much more user friendly than i had imagined

---

### Post by Dr Small on 2007-05-13
to run a shell, open the terminal, cd to the directory where it is located, and type:
```

sh filename.sh
```
That should run the shell file.

Dr Small

---

### Post by taurus on 2007-05-13
What are you trying to install anyway?  Is it a source file?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by Wiebelhaus on 2007-05-13
"sudo sh /yadda/yadda/yadda/filename.sh"

---

### Post by forestpixie on 2007-05-13
Trying to install atunes

I've got the shell to run to run in terminal, which opens and runs atunes

Do i have to run the sh in terminal each time I want to run atunes?

---

### Post by Wiebelhaus on 2007-05-13
na , locate the launcher like /opt/picasa and create a launcher from the desktop tied to that file.

---

### Post by Wiebelhaus on 2007-05-13
also , sounds like that program is modular , pretty cool.

does it have radio stations , download info from last.fm and stuff to?

---

### Post by forestpixie on 2007-05-13
okay ran it in terminal as sudo this time - 

still seems to mean i have to run the shell from terminal each time though?

if that's the case i'll not bother - just casting about for mp3 players really - using amarok at the moment

So I guess last question would be - to run this app will I need it run it from terminal each and every time?

---

### Post by Dr Small on 2007-05-13
Basically, yes. Or you can create a desktop launcher that runs that command, so you don't have to type it every time.

Dr Small

---

### Post by forestpixie on 2007-05-13
where would the file i can tie to the launcher be?

looked in /usr/bin not there

still trying to find my way round the directory structure - been used to win for a long time 

I find references to primers and the like in threads - keep reading and then the next one and forget to bookmark them!

anyway still not sure where to look

AND i keep missing replies before i post - got two 7 year olds whining at me

---

### Post by Wiebelhaus on 2007-05-13
> **sx66gns said:**
> na , locate the launcher like /opt/picasa and create a launcher from the desktop tied to that file.

check /opt


.....kids

as do i bud.

---

### Post by forestpixie on 2007-05-13
no just got open office in there !

---

### Post by forestpixie on 2007-05-13
just noticed a bunch of stuff in terminal (twas hidden behind everything else) further up in the terminal screen 

errors and WOAR frame size errors and corrupt jpeg data

not at all sure about this now

---

