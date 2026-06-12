---
title: "housekeeping questions"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by dross on 2006-10-06
Hello,

I've got a few minor admin questions that I can't seem to locate an answer to. Can anyone help?

1.  When I put Ubuntu into hibernate, I can't get it out again...I've tried every keyboard combination I can think of...I'm using Ubuntu 6.10 and a Dell Dimension XPS T450...could this be some quikiness with my hardware?

2.  Just curious, is there a terminal command to find what version of the OS you're running?

3.  I installed the OS to boot up with the gui, and would now prefer to boot up in command line...anyone know how to keep the gui installed, but keep the OS from booting to it by default.  Also, is there a way to close the gui, and move to command line version once the computer is on, without restarting??

Thanks a lot!

---

### Post by tribaal on 2006-10-06
I dont' know for the first 2, but number 3 is easy: To switch between GUI and command line, just push ctrl-alt-F1 to go to command line, and Ctrl-Alt-F7 to go back to GUI.

F2-F6 also work, they are your different command line "desktops" :)

There is an option on the graphical login manager to boot into command line mode, and you can make this a default option, as far as I know.

Alternatively, you can "sudo /etc/init.d/gdm stop" and "sudo /etc/init.d/gdm start" to turn the GUI on and off.

Enjoy the power of linux :)

- trib'

---

### Post by podunk on 2006-10-06
For the hibernate thing - it's not like Windows, use the power button instead of a keyboard combo.

---

### Post by dross on 2006-10-06
Great!  Thanks for the help.

---

