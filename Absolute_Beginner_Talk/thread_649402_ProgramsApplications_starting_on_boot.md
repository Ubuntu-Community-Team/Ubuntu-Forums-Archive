---
title: "Programs/Applications starting on boot?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-24
Hey,

Is there any way (I'm sure there is) to make programs start when the computer starts?

I'd like KNotes and Pidgin to open up when it boots (Kubuntu Gutsy with GNome Desktop Package installed).

I've googled it and found a few different ways, one involving messing with the boot kernel, one adding configuration scripts, blah blah blah.

Easiest way would be preferable.  I'm NOT looking to go around changing important files so that it won't boot or some crap :-\.

Thanks in advance.

---

### Post by wormser on 2007-12-24
System> Preferences> Session> Add.

---

### Post by PmDematagoda on 2007-12-24
So what DE are you using? Is it GNOME or KDE?

In the instance of GNOME:-
Go to System>Preferences>Sessions then add the required programs you need to the Startup Programs tab.

In the instance of KDE:-
I never found a real(Technological) way, but I just leave the programs(open or minimised) that I need to startup automatically when I shutdown the PC and the next time I start up KDE, I find them running automatically.

---

### Post by xeth_delta on 2007-12-24
There is a directory called **/home/user_name/.kde/Autostart**. If I am not mistaken, placing a soft link in there to the program you want to run might do the trick. Otherwise, you could do what I do and write a really short script (2 lines) to run your program at startup:

```
cd .kde/Autostart
nano script_name
```

The script will contain
```
#!/bin/bash
program_to_run
```

Save the script (Control-O in nano) and make the script executable:
```
chmod +x script_name
```

There might be an easier way to do it, but I don't know of it.

Xeth

---

### Post by Syndacate on 2007-12-24
I'm using Kubuntu with Ubuntu Desktop Enviornment installed.

Yeah, I remember with KDE it would just leave open whatever you shut down - that was cool - no way to do that with Ubuntu?

As far as system >> preferences >> sessions goes - how do I find where the programs are located?

(I was always a windows user so I'm looking for an executable or something...obviously those don't exist in linux so ??)

Add the name, then browse to what dir?

ie.  Pidgin, KNotes.

There any way to get it to react like KDE does where it opens whatever was open before it was shut down?

---

### Post by mynogan on 2007-12-24
Isn't there an option to remember the applications currently running when you log out of Ubuntu --- under system >> preferences >> sessions?

---

### Post by PmDematagoda on 2007-12-25
You can just enter the commands to run the application instead of browsing for the executables. Or you can enable "Saved Sessions" for GNOME which would make it work like KDE does.

To find the commands for the applications, just go to Main Menu in System>Preferences>Main Menu, then just double click on an entry to bring up the Launcher Properties for it, you can then see the command required to run it, then it is just a simple matter of Copy & Paste:).

---

### Post by Syndacate on 2007-12-25
> **PmDematagoda said:**
> You can just enter the commands to run the application instead of browsing for the executables. Or you can enable "Saved Sessions" for GNOME which would make it work like KDE does.

To find the commands for the applications, just go to Main Menu in System>Preferences>Main Menu, then just double click on an entry to bring up the Launcher Properties for it, you can then see the command required to run it, then it is just a simple matter of Copy & Paste:).

Worked perfectly, thanks a lot.

---

### Post by PmDematagoda on 2007-12-25
Glad I was able to help:).

Merry Christmas:).

---

