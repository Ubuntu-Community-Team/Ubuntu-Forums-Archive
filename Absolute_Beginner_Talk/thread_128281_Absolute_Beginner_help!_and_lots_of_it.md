---
title: "Absolute Beginner: help! and lots of it"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by Discretion on 2006-02-11
Hi guys
i have now install Unbuntu and love the feel!.......it is my first ever look at any flaviour   
of linux.....i now need lots of help...i think i have worked out some of the consepts and just need some help using them....i cant seem to get to run "ROOT" i have installed terminal but dont know what to do with it. i tryed to use an FTP manager with no success. in the debug screen it says must be run as ROOT.
I HAVE DONE:
1 installed an FTP SERVER
2 Installed a GUI FTP Manager
3 changed my user groupe to root in "USERS & GROUPS"
3 tryed to run the terminal ...ERROR MESSAGE:cry:  = " Failed to execute child process "Terminal" (No such file or directory)

:( so like i say i think i need lots of help, so perhaps if someone could first off help me with the command line....how do i get it to work..step by step would be nice

---

### Post by bartbes on 2006-02-11
you can get root access with sudo and if you want a root terminal (a terminal with root access) use the command ```
sudo -i
```

---

### Post by Discretion on 2006-02-11
:D Thanks for the help....i did read that somwhere ....but my terminal wont open see error message in firts post!

---

### Post by bartbes on 2006-02-11
where do you put in terminal then?

EDIT: I mean where you put in the command terminal

---

### Post by Discretion on 2006-02-11
applications-----system tools------run as different user


i installed "Terminal" from add new applications

---

### Post by bartbes on 2006-02-11
I'm not working in GNOME right now, but I thought there was somthing in the system tools menu as terminal or console. I'm sure there is a link for it..

you can also access a linux terminal with ALT+CTRL+F1 - F6 (F1 till F6). So if you really can't find it logon there ans type:```
sudo apt-get install konsole
``` and back in gnome (ALT+CTRL+F7) do ALT+F2 and type in there konsole.. then you get a console and under Session you can choose root terminal. Put in your password and you are root. BUT remember **sudo is more secure then a root terminal**

---

### Post by Discretion on 2006-02-11
Thanks very much..... i will now play a while:twisted: ....i will try not to break it!!!

---

### Post by Discretion on 2006-02-11
perhaps someone may know of a good site for the "Absolute Beginner"

---

### Post by wjp.reg on 2006-02-11
[QUOTE=Discretion]perhaps someone may know of a good site for the "Absolute Beginner"[/QUOTE]

I found this to be quite helpful 

[http://www.ubuntuforums.org/showthread.php?t=13042]("http://www.ubuntuforums.org/showthread.php?t=13042")

as is the ubuntu wiki

Cheers!
Wolf

---

