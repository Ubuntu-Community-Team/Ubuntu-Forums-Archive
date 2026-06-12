---
title: "KDE Autostart problem"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Lexyboy on 2007-01-19
Hi All,

I'm having a problem getting programs to start on booting into KDE.  I've tried both putting softlinks to the programs in my autostart directory, and using a script to invoke them, both to no effect.  Anyone have any ideas?  I've checked the path in kcontrol is the right one, and the files start the programs when clicked in Konqueror, so don't know what to do... ](*,) 

Any ideas appreciated!

Alex

---

### Post by TheWizzard on 2007-01-19
can you elaborate a bit?
- what is the exact folder you're using?
- what kind of programs do you want to start? 
- post the scripts you use to start them
- etc

---

### Post by kebes on 2007-01-19
When you say "autostart directory", you mean:

/home/username/.kde/Autostart

right? If you put a symlink to a program/script in there, it should work. (It does on my system.) Try testing the Autostart directory using a very simple script like:

```

#!/bin/bash
kwrite &

```

(Don't forget to "chmod +x" the script.) And see if a copy of "kwrite" opens everytime you log-in. This will hopefully help determine what the source of the problem is.


Note also that programs launched from a terminal setting are killed when the terminal closes. In the example above I wrote "kwrite &" because the "&" starts the program in the background, so it's still running after the terminal closes. If your script is just running a few commands, you don't need it... but if you're expecting your script to open a program and leave it open, you may need to add that.


Also, you say you can run the scripts on the commandline, but do they need to be run as root or something like that? I don't think the Autostart directory runs things as root.


Hope that helps.

---

### Post by x64Jimbo on 2007-01-19
No, Autostart does not run as root - it runs as the logged-in user. If you want a program to run as root on startup, you'll want to add it in an init script.

---

### Post by Lexyboy on 2007-01-19
Thanks for the quick replies!

Correct, the directory is /home/ajw/.kde/Autostart

I'm trying to launch kopete, thunderbird and knotes - the first two are links and knotes is a script:

#!/bin/bash
knotes

Guess I may need the &, but I don't understand why the linked files don't load.  When I said they work when logged in, I meant that if I click the icons the programs all run fine, so I don't think it's a problem with the contents of the folder - they just don't seem to get executed.

---

### Post by x64Jimbo on 2007-01-20
I implement all of my KDE startup items in one script. 
#!/bin/bash
command1 &
command2 &
command3 &

ALSO, as was previously mentioned, be SURE that you set the executable bit on the script with chmod +x <scriptname>
I'm fairly certain that links to programs don't work in the Autostart directory.

---

### Post by Lexyboy on 2007-01-22
According to [this wiki]("http://gentoo-wiki.com/HOWTO_Autostart_Programs#KDE") you can start programs with a link.  In any case, scripts (yes, made executable with chmod) don't do anything either.  Is there a setting somewhere else in KDE which might be the problem?

---

### Post by TheWizzard on 2007-01-23
> **Lexyboy said:**
> According to [this wiki]("http://gentoo-wiki.com/HOWTO_Autostart_Programs#KDE") you can start programs with a link.  In any case, scripts (yes, made executable with chmod) don't do anything either.  Is there a setting somewhere else in KDE which might be the problem?

there is no setting in kde that i know of. 
one question: in the (small) script you made to start your program, does it end with an empty line?
and did you test the script?

---

### Post by Lexyboy on 2007-01-24
It does end with an empty line (don't know why).  I tested it by clicking the icon in Konqueror and typing its path into the Alt+F2 prompt - both launch the program (knotes in this case).  Am a bit baffled - I might just save a session with the programs I want and set KDE to start with that session...

---

### Post by Lexyboy on 2007-01-24
OK, have just tried with the script with the full path for the program (ie /usr/bin/knotes rather than just knotes) and no empty ending line.  Still nothing :roll:

---

### Post by Ramses on 2007-01-24
Is the script file executable?

---

### Post by x64Jimbo on 2007-01-24
> **Lexyboy said:**
> It does end with an empty line (don't know why).  I tested it by clicking the icon in Konqueror and typing its path into the Alt+F2 prompt - both launch the program (knotes in this case).  Am a bit baffled - I might just save a session with the programs I want and set KDE to start with that session...
That's what I've always done, and it works pretty well.

---

### Post by TheWizzard on 2007-01-24
> **Lexyboy said:**
> OK, have just tried with the script with the full path for the program (ie /usr/bin/knotes rather than just knotes) and no empty ending line.  Still nothing :roll:

you didn't forget the "&" sign? 
```
#!/bin/bash
knotes &
```

and does the script run from the command line?

---

### Post by Lexyboy on 2007-01-25
Nope, the & is there, and the script is executable at the command line, so it's definitely not a problem with the contents of the Autostart directory, it's just not getting run!  Think I'll have to give up on this one and use sessions instead...

---

### Post by TheWizzard on 2007-01-25
> **Lexyboy said:**
> Nope, the & is there, and the script is executable at the command line, so it's definitely not a problem with the contents of the Autostart directory, it's just not getting run!  Think I'll have to give up on this one and use sessions instead...

i really don't understand. sorry i can't help you :confused:

---

### Post by Lexyboy on 2007-01-26
Oh well, thanks for the suggestions everybody - now I just restore the previous session, seems to work OK (though thunderbird doesn't start for some reason).

---

### Post by Lexyboy on 2007-05-23
OK, found a solution (sort of): apparently the Autostart directory is not ```
~/.kde/Autostart
``` but rather ```
~/.kde/share/autostart
```
(According to: [kde.org]("http://l10n.kde.org/docs/admin/autostart-and-runonce.html")).  So, I just put my foo.desktop files there and they start up!  Woo-hoo!

Still in the dark as to the function of ~/.kde/Autostart, since its contents are clearly not executed at any point... oh well, never mind!

---

### Post by TheWizzard on 2007-05-26
strange ~/.kde/Autostart works for me. 

mmm, how did you install kde? did you install the kubuntu meta package or did you do it differently?

---

### Post by jorj on 2007-06-26
hello, in my case, I just dragged the application from the desktop to ~./kde/Autostart/ and then clicked on move here. rebooted and skype starts for me at the beginning of each session automatically. 

annoyingly though, it doesn't start minimized and that can be quite frustrating.  :p

---

