---
title: "Not the owner? [Resolved]"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by svmseric on 2007-04-28
Why is it that I cannot edit files, move files, or pretty much a lot of admin things. It says im not the owner whereas I am the owner and it says im the admin. and example of what is happing to me is this. I was trying to move a file into the /usr/lib/mozilla/plugins, and it would not let me move it into the folder. Can someone please help me with this problem. I started using ubuntu last night. And im already an addict. I have been a windows user for years now, and i think that this is better and also free. Though Vista is alright. :lolflag:

---

### Post by taurus on 2007-04-28
You need to be root to write anything outside of your $HOME directory.  You can use sudo if you wish or if you want to do the drag 'n drop, run

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tomosaur on 2007-04-28
On Linux, users only have access to their home directory.

Since you are the administrator, you can **gain** access to things outside of your home directory, but you need to input your password to do it. This prevents people doing nasty stuff when you're not at the computer, and also for general security. In the unlikely event that you get a virus, for example (there are very, very few viruses known to be available for Linux, and none 'in the wild' which pose much of a threat), it will not be able to install itself just anywhere, and can't damage anything outside of a small area (your home dir, if that).

To gain temporary root priveleges, you need to use either sudo (for command line stuff) or gksudo (for graphical stuff). To run a command using gksudo, hit alt+f2, then type 'gksudo <command>'. For example, to run gedit (the default text editor) with root priveleges, so that you can edit files outside of your home directory, hit alt+f2, then type 'gksudo gedit'.

If you want to run a command line application with root priveleges, you do the same thing, but in a terminal, and use 'sudo' instead of gksudo. For example, to run nano (a command line text editor) with root privs, you'd type 'sudo nano <filename>'.  When you run either sudo or gksudo, you will be prompted for a password. You need to enter the same password you use to log on to the system. When entering your password with 'sudo', you will not see the password being typed. This is a security measure, to prevent malicious programs hijacking the terminal to read your password.

You can alter file permissions using the 'chmod' command - but you should never alter file permissions for files outside of your home directory, unless they already have the wrong permissions. Doing so is a recipe for disaster.

---

### Post by svmseric on 2007-04-28
Thank you for the info guys, this should really help me out, and im sure I will be using this section of the forums many times to come :-P

---

