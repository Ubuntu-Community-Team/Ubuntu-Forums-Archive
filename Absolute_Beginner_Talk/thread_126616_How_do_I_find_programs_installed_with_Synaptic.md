---
title: "How do I find programs installed with Synaptic?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by JeffV on 2006-02-07
Most programs I've installed with Synaptic Package Manager I've noticed get conveniently added to the menus automatically.  However, there are a couple I just installed that didn't.  One of them was Putty, which I was able to run simply by typing putty at the command prompt.  So there's no issue there.  However, the other program I installed was the openAFS client and I have no idea how to find it and run it.

---

### Post by paulmilliken on 2006-02-07
The apropos command might be useful here - it's like doing a keyword search for programs installed on your computer.  Type, for example, "apropos afs" or "apropos openAFS" to see a list of commands with that keyword.  I'm not sure what openAFS does but you can probably think of your own keywords to track it down.

Alternatively have a look in the /bin , /usr/bin and /usr/local/bin directories as the program was probably installed in one of these directories.

Paul

---

### Post by JeffV on 2006-02-07
Ah!....I just read this page:
[https://wiki.ubuntu.com/OpenAFSSupport?highlight=%28openafs%29](https://wiki.ubuntu.com/OpenAFSSupport?highlight=%28openafs%29)

I didn't realize openAFS had complications in setting it up and using it.  I guess that's why it doesn't just appear in the menu.

---

### Post by JeffV on 2006-02-07
[QUOTE=paulmilliken]The apropos command might be useful here - it's like doing a keyword search for programs installed on your computer.  Type, for example, "apropos afs" or "apropos openAFS" to see a list of commands with that keyword.  I'm not sure what openAFS does but you can probably think of your own keywords to track it down.

Alternatively have a look in the /bin , /usr/bin and /usr/local/bin directories as the program was probably installed in one of these directories.

Paul[/QUOTE]

Thanks!  I'll remember that for the future.  I did end up finding it in the /etc directory.

---

### Post by Lanrond on 2006-02-07
If you can run a program simply by typing in the command line, typing **which *<command>*** will tell you where the executable is.

Otherwise use **apropos *<program>*** to find the command(s) related to the program an re-try with **which**.

---

### Post by Madpilot on 2006-02-07
Have a look at [https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands), which includes:

> 
If you aren't sure which command or application you need to use, you can try searching the man files. 

 * man -k foo will search the man files for foo. Try "man -k nautilus" to see how this works. 
        * Note that this is the same as the apropos command. 
 * man -f foo searches only the titles of your system's man files. Try "man -f gnome", for example. 
        * This is the same as the whatis command.


---

### Post by BoyOfDestiny on 2006-02-07
in synpatic right click the app name, choose properties, then choose the installed files tab. =)

---

