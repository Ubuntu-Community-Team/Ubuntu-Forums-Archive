---
title: "[SOLVED] several small questions"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-14
Hi
A few questions.
1. How do i turn off the computer using only the keyboard?
2. Does ubuntu have a task manager similar to the XP one where you can turn off non-response programs or if nothing else works?
3. If you hit control, and F6 i tihnk it is it takes you to a large whole screen version of the terminal i think, how do i exit that?
4. How do i open rar files? I have 7zip in ubuntu, but the option to start the program dosen't appear in my applicaitons menu, neither does write clicking on the file, then clicking 'extract here' work. I have tried right cliking, and choose the application 7z to open the file with, but this does nothing on my computer.
Thanks for the help

---

### Post by 1/0 on 2007-11-14
1. By editing /etc/X11/xorg.conf
2. There are no windows. GNU/Linux. The various desktop managers usually have a process manager refer to the user manual, wiki and faq on the homepage for the desktop you are using (Fluxbox, XFCE, Enlightenment, KDE, WM, Gnome, CDE, Ice, etc...) in order to find where exactly they are located.
3. Depends on your xorg settings but usually by alt + F7.
4. If you mean how to decompress them its possible in many ways. Using unrar it would be "unrar e path/file"

---

### Post by KhaaL on 2007-11-14
> **Falc7 said:**
> Hi
A few questions.
1. How do i turn off the computer using only the keyboard?
2. Does windows have a task manager similar to the XP one where you can turn off non-response programs or if nothing else works?
3. If you hit control, and F6 i tihnk it is it takes you to a large whole screen version of the terminal i think, how do i exit that?
4. How do i open rar files? I have 7zip in ubuntu, but the option to start the program dosen't appear in my applicaitons menu, neither does write clicking on the file, then clicking 'extract here' work. I have tried right cliking, and choose the application 7z to open the file with, but this does nothing on my computer.
Thanks for the help


I can answer some of your questions... for non-responsive programs, yes there is a task manager. I don't know what it's called in ubuntu (gnome desktop) but in kde it's ksysguard. you can also have a task manager in the console by simply typing "top". from there you can kill unresponsive windows.

alternatively, you can type in the console:

ps -e|grep nameoftheunresponsiveapp

the first colum will return a number, you can now stop it by typing:

kill 888 (replace 888 with the tasknumber you got by ps -e command).


The console you got to can be reached by Ctrl+alt+F1-F6. you go back to the GUI by Ctrl+alt+F7.

---

### Post by Falc7 on 2007-11-14
okay thanks
What should i do in xorg.conf to turn off the computer using only the keyboard?

---

### Post by Rhubarb on 2007-11-14
1.  To turn off your pc from the terminal type this in:
```
sudo shutdown -P now
```
DO NOT CONFIGURE YOUR xorg.conf, as this has nothing to do with powering your computer down (it controls your video, keyboard and mice settings).

2.  System --> Administration --> System Monitor
You can also kill any app that is not reponding on your screen by pressing Alt + F2, then type in: "xkill" (without the quotation marks), your mouse cursor turns into an X, click on the application that is not responding to kill it.

3.  Control + Alt + F7

4.  I'm not 100% sure, I can get back to you on this later some time.
(There are some rar utilities you can download in Synaptic Package Manager)

---

### Post by KhaaL on 2007-11-14
Rhubarb, if I understood the OP post correctly I think he wants to shut down the computer through a hotkey on his keyboard... How can he bind the command "shutdown -P now" to a single keystroke?

---

### Post by Rhubarb on 2007-11-14
You can press: Ctrl + Alt + Delete, press tab until you get to the shutdown button, press space bar.
I'm sure there are other ways to instantly turn your computer off by binding a bash script (or similar) to a key somehow.
You can change the keybindings to "Log out" in System --> Preferences --> Keyboard Shortcuts

---

### Post by Falc7 on 2007-11-14
thanks guys for the help
One last thing, its strange now, for some reason, archive manager can handle rar format, even though it couldn't before. I think it was because i installed somethign through the terminal.
Anyway, i want to choose the default to be that rar files are opened with archive manager, at the moment they are opening with 7z, which does nothing, how do i make the rar files automatically open with archive manager?

EDIT: Nevermind, just worked it out

---

### Post by Absorbed on 2007-11-14
> **Falc7 said:**
> thanks guys for the help
One last thing, its strange now, for some reason, archive manager can handle rar format, even though it couldn't before. I think it was because i installed somethign through the terminal.

"unrar" is what I use for rar files. It's in one of the ubuntu repositories. Maybe you installed that.

---

### Post by RedSquirrel on 2007-11-14
> **KhaaL said:**
> ... alternatively, you can type in the console:

ps -e|grep nameoftheunresponsiveapp

the first colum will return a number, you can now stop it by typing:

kill 888 (replace 888 with the tasknumber you got by ps -e command).

**pidof** and **killall** are also quite helpful. :)

man pidof
man killall

---

