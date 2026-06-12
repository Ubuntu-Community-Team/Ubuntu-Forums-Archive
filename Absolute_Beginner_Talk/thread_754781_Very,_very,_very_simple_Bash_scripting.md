---
title: "Very, very, very simple Bash scripting"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-04-14
Okay, I'm just playing around at very low level bash scripting and here's my awesome script prog1:

> #!/bin/bash
This is a test!

After I've saved this to my /home/Mark directory I ran:

> sudo chmod 700 ./prog1

However when I try to run it I get:

> bash: prog1: command not found

Now I've checked the directory and bash is in the bin directory, so what am I doing wrong? Admittedly if I'm getting this wrong then I guess my future as a programmer is looking pretty bleak!

Any advice welcome.


Mark

---

### Post by dje on 2008-04-14
Try this:
```
./prog1
```
You need the ./ if the script isn't in /usr (like Trail says below your PATH variable)

EDIT: Also this won't do anything:
```
#!/bin/bash
This is a test!
```

You need:
```
#!/bin/bash
echo "This is a test!"
```

hope that helps,
dje

---

### Post by Trail on 2008-04-14
If you try to run it as
```

prog1

```
then this assumes that "prog1" is found on your PATH variable (like, usr/bin/prog1). Try running it as 
```

./prog1
or
sh prog1
or
. prog1

```

Those ways dictate that the file to be executed resides on your current directory instead of $PATH.
(provided you are in the same directory of course)

---

### Post by mister_pink on 2008-04-14
If its in your home dir you shouldn't need sudo to chmod it. Also you probably want 755 not 700 really. Finially like he said, to run executables in the current directory do ./scriptName
If you want it to display that on the screen then you want to echo it:
echo "This is a test!"

---

### Post by hyper_ch on 2008-04-14
to start bach scripting have a look here:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by NeonSamurai on 2008-04-14
Ahh...

Thanks guys. 

I wondered how bash would recognise something in a different directory without prompting. 

Much obliged.

---

