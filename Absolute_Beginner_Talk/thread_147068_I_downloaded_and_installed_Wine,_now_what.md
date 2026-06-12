---
title: "I downloaded and installed Wine, now what?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
I used get-apt to get wine... it downloaded and installed.... Now how to I find it to access it?  Its not in any menu I can find...

---

### Post by taurus on 2006-03-19
You need to config it first before you use it.  Open a terminal, Applications -> System Tools -> Terminal, and type
```

wincfg

```

---

### Post by bluevoodoo1 on 2006-03-19
[QUOTE=taurus]You need to config it first before you use it.  Open a terminal, Applications -> System Tools -> Terminal, and type
```

wincfg

```[/QUOTE]

winecfg

might work better for you :)

---

### Post by noswal on 2006-03-19
then type winefile - opens an explorer type of  window

---

### Post by Kersus on 2006-03-19
Then it says 

bash: winefile: command not found

---

### Post by markmark on 2006-03-19
Just say you've downloaded installer.exe which is a windows program you want to try to install. On the command line just do:

wine installer.exe

And with a bit of luck you'll be away. If the installer succeeds you might end up with the windows program in your ubuntu menus. If not you can launch it from the command line. You need to know where it was installed to, in general it will be somewhere like "/home/your_user_name/.wine/drive_c/Program Files/"
So to launch it you'll run something like this from the command line:

wine "~/.wine/drive_c/Program Files/my_new_prog/new_prog.exe"

And again, with a little luck your windows program will launch.
To save your self all that typing you can now add it to a menu, again remembering that you can just  point the launch to new_prog.exe you need to have the wine at the start.

---

