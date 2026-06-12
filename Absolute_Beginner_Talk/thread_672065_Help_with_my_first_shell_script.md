---
title: "Help with my first shell script"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by acl123 on 2008-01-19
Hi, I wrote a little script to enhance the well known Linux Source Code Screen Saver ([http://micrux.net/?p=66](http://micrux.net/?p=66)). The script that guy wrote selects a random file from the linux code and outputs it's contents. My script starts at a random line number so you don't always just get the header of the file.

My script is this:
```
TotalLineCount=$(wc -l < $1)
sed -n $[ $RANDOM % $TotalLineCount],$[$TotalLineCount]p $1
```

I've saved this in a file called /home/myusername/scripts/sed-from-random-line.sh and given the file u+x permissions.

Now I can happily run this in the shell, like this:
```
/home/myusername/scripts/sed-from-random-line.sh `find /usr/src/linux-source/ -name '*.txt' | argshuf`
```

However, when I add this as the "Text Program" setting in the Phosphor screensaver, or other text outputting screen saver, I get the error:
```
sed: -e expression #1, char 2 unknown command : `['
```

Can anyone help me work out what is going wrong?

---

### Post by cmnorton on 2008-01-19
What about

find /usr/src/linux-source/ -name '*.txt'  -exec  /home/myusername/scripts/sed-from-random-line.sh {} \;

---

### Post by acl123 on 2008-01-20
Hi thanks, that's useful to know. I also need to pipe *find*'s output through the argshuf program though.

I was thinking I could add argshuf into my own sed-from-random-line script. How can I place the output of a command into a variable?

---

