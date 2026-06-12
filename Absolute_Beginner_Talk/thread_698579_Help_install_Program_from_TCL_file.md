---
title: "Help install Program from TCL file"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by BrendaninBrazil on 2008-02-16
I have just installed Fluxbuntu on an old Pentium 2 300mHz Compaq for my mother in law. I am trying to ease the transition for her from windows(because XP runs like a dog on this machine). She only does simple things like web browsing, email & using Skype. My problem is that she is addicted to Windows freecell! I have installed it using wine but she tells me it only has 100 random games instead of the million or so in Windows(I don't understand why but OK). I have found another version that I think to her will be almost identical but don't know how to install it. It is a tcl file which I got from [http://www.talvo.com/tcl-code.php]("http://www.talvo.com/tcl-code.php"). I have made sure that tcl is installed via Synaptic but when I try to open the file I just get nano with all of the script on the screen. Can someone please help with a basic step by step on what I need to do with this file

---

### Post by jan quark on 2008-02-16
try this

run the following install codes in terminal


```
sudo apt-get update
```

```

sudo apt-get install libsnack2 tcl8.5 tcl8.5-dev tcllib tile tk8.5 tk8.5-dev
```

navigate to the folder

```
cd /path/to/folder
```


then compile the application with
one command at a time
```

./configure
```
```
make
```
```
sudo make install
```

---

### Post by BrendaninBrazil on 2008-02-16
Hi Jan,
Thanks for the quick response. I don't know if you looked at the site I linked to but I don't have a folder to ./configure in. All I have is a single file called "freecell-1.1.tcl". I have made sure through synaptic that tcl(I think it&#347; actually 8.4) is installed & OK.

---

### Post by stevescripts on 2008-02-16
You sure the tcl install is working?

From a terminal:

```

which tclsh

```

That should give you the path to the tcl executable.

If you file is just a tcl file (which it appears to be...) then
(from a terminal again);
```

chmod +x freecell-1.1.tcl
./freecell-1.1.tcl

```

If you still have problems, post back.

Hope this helps.

Steve

---

### Post by BrendaninBrazil on 2008-02-16
Hi Steve,
I think that you're right & I do just have a file.

When I did the which tclsh command I got

/usr/bin/tclsh

I then tried the next 2 commands you gave. The first one seemed to work without a problem. When I do the ./freecell-1.1.tcl command I get the following error:

bash: ./freecell-1.1.tcl: /bin/sh^M: bad interpreter: No such file or directory

The tcl file is really small so I have attached it if anyone is able to look at it & let me know how to use it.

Thanks

---

### Post by stevescripts on 2008-02-17
You need to make sure that you are in the same directory as the tcl file when you
execute ./freecell-1.1.tcl.

I dont see the attachment here?

Steve
(sorry for the delay in getting back to you)

---

### Post by stevescripts on 2008-02-17
I found the file - it needs to be executed with wish, rather than tclsh.

So from a terminal:
```

wish freecell-1.1.tcl

```

Again, make sure your shell is in the same directory as the *.tcl file.

Hope this helps.

Steve
(*IF* you cant make this work, feel free to e-mail me directly)

---

