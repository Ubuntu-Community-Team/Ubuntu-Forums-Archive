---
title: "how do i become root?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Daniel Z on 2007-07-11
hello :)

well as the title says how do i become root or "super-user"?
ive downloaded a file that is supposed to update my drivers but when i run the program in terminal it says i need to become super user :(
can some nice guy help me? :)

---

### Post by Seisen on 2007-07-11
You can just type in **"sudo"** before the command and it will give you temporary superuser rights. If its a graphical application use** "gksudo"**. Also don't worry when you type in your password and it doesn't show up on the screen. Its still being entered.

---

### Post by Daniel Z on 2007-07-11
well when i open the file it says "run in terminal" "show" "cancel" "run"
when i click on run i cant enter my password anywhere,
when i click on run in terminal i cant type sudo anywhere before it shutsdown due to im not super-user. i tried opening another terminal and typing sudo then clicking on run in terminal but the dont seem to respond to eachother and justs shutsdown like before
do i have to first type sudo then open the file by terminal? if i do i dont know what to type :(

well if i tell you where the file is located you guys can tell me what to type :)
 /home/daniel/Desktop thats where it is
and the file name is ati-driver-installer-8.38.6-x86.x86_64.run

well i hope i can get it running soon :)

---

### Post by Seisen on 2007-07-11
```
cd /home/daniel/Desktop
```
```
sudo  sh ./ati-driver-installer-8.38.6-x86.x86_64.run
```

---

### Post by jw5801 on 2007-07-11
You need to run the file from the terminal. So the command entered would depend on the file. If you want to try it graphically then you can open a file browser as root and then run it, but that can be dangerous if you accidently wipe something important. Type ```
sudo nautilus
``` then try running it.

Otherwise the safer option, since it sounds like this file is a script of some kind would be to type this:
```
cd ~/Desktop
sudo sh ati-driver-installer-8.38.6-x86.x86_64.run

```
The cd is "Change Directory" (~ represents /home/daniel), sudo means execute as root and the sh denotes a shell script (which is what you're trying to run).

EDIT: got beaten to it :p

---

### Post by Eddy Van Halen on 2007-07-11
wrong thread.

---

### Post by testube_babies on 2007-07-11
> **jw5801 said:**
> You need to run the file from the terminal. So the command entered would depend on the file. If you want to try it graphically then you can open a file browser as root and then run it, but that can be dangerous if you accidently wipe something important. Type ```
sudo nautilus
``` then try running it.

..That can also be dangerous because it can change permissions on your user account and make you unable to log in.  Never use sudo for graphical applications; use **gksudo** as previously mentioned:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jw5801 on 2007-07-11
Cheers for that, I tend to do most things that require root permissions using terminal commands so I'm not all that familiar with graphical applications as root. I know the command line can be intimidating to some people though.

---

