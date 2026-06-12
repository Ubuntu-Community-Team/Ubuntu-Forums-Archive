---
title: "Bash scrtipt"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Ziggy72 on 2006-09-29
I would like to write a simple bash script to open a terminal in a  nominated directory (say /usr/share/doc/pythoncard-doc/samples/) and then do ls -a to show the files and folders in the terminal. Among many things I've tried:

```


#!/bin/bash
cd /usr/share/doc/pythoncard-doc/samples/
gnome-terminal
ls -a


```

This will open a folder and change to the required directory but it will not show any ls -a output. 

Where can I get good, simple information about bash scripting?
Help appreciated...

---

### Post by K.Mandla on 2006-09-30
I've looked at this one more than once.

[http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html](http://www.linux.org/docs/ldp/howto/Bash-Prog-Intro-HOWTO.html)

I don't know that it's the best one, but it's not bad.

---

### Post by Ziggy72 on 2006-09-30
Thanks, but I seem to need even more basic help. For example, if I type:

```

#!/bin/bash          
echo Hello World 

```

and save it as a script, when I run it the terminal flashes on to the screen and then disappears. How do I get the terminal to stay there so I can see the output?

---

### Post by morphodone on 2006-09-30
try something like this...

```
#!/bin/bash
ls -a /etc/X11 > /home/kyle/output.txt
gedit /home/kyle/output.txt

```

---

### Post by Ziggy72 on 2006-09-30
Yes, thank you. That works just fine and I can see the output I need. However, I would really like to see the output in a terminal window. Surely that must be easily achieved?...

---

### Post by David_T on 2006-09-30
This works fine for what you want to do, but it's kind of clumsy.  Anyone know how to avoid using the temp file?


#!/bin/bash

echo "cd /usr/share/doc/pythoncard-doc/samples; ls -a" > /var/tmp/myrandomtempfile
infile=/var/tmp/myrandomtempfile

gnome-terminal -e "bash --init-file ${infile}"

---

### Post by curtisf14 on 2006-09-30
Hmm, I'm not sure what the issue is, but I did the following and it worked for me:

I made a file called "testfile" in my home directory, and put the following in it:

```

#!/bin/bash
echo Hello World

```Then, in my terminal, I put:

```

chmod +x testfile

```Then, I did "./testfile", and it printed "Hello World" in the terminal.  See if this works.  If it doesn't, then maybe something is strangely wrong...

---

### Post by David_T on 2006-09-30
I think the idea is he doesn't want to have to run the script from the terminal, he wants to run it from the desktop or wherever and have it open up a new terminal window.

---

### Post by David_T on 2006-09-30
OK, this is cleaner, but it only works in xterm for some reason,
it doesn't work in my xfce4-terminal:

First, this goes in your ~/.bashrc file:
```

if [ $START_DIR ]
    then if [ -d $START_DIR ]
        then cd $START_DIR; ls -a
        else echo "Bad starting directory."
    fi
fi

```

And then your script would just look like:
```

#!/bin/bash
export START_DIR=/usr/share/doc/pythoncard-doc/samples
xterm

```

---

### Post by norco on 2006-09-30
```
gnome-terminal -x bash -c "cd /somedir; ls -a; bash"
```
but the ls colouring doesn't work ](*,)

---

### Post by Ziggy72 on 2006-09-30
> **David_T said:**
> This works fine for what you want to do, but it's kind of clumsy.  Anyone know how to avoid using the temp file?


#!/bin/bash

echo "cd /usr/share/doc/pythoncard-doc/samples; ls -a" > /var/tmp/myrandomtempfile
infile=/var/tmp/myrandomtempfile

gnome-terminal -e "bash --init-file ${infile}"

Very many thanks for the replies. Yes, my question was about how to use a desktop or launcher script to start a terminal, do some actions within the terminal and then show the results within the same terminal window. I began the task thinking that this would be an easy thing to do, but I see now that something like that is difficult in linux.

Special thanks to David_T. If you do find a solution which doesn't involve the use of the temp file, please let me know.

---

### Post by m83 on 2006-09-30
Hello, Ziggy72. This is what I could come up:
```
#!/bin/sh
cd /usr/share/doc/
gnome-terminal -e 'bash -c "ls -a; exec bash"'
```

I open the gnome-terminal which executes a ls in a bash shell then I replace the shell which ran the ls with another shell so you can type commands. I did it like this because I found out that running only [FONT="Courier New"]gnome-terminal -e 'ls -a'[/FONT] closed the terminal real quick and I couldn't see the result of the ls -a.

If you don't want to have a shell into which to type commands after you run ls, but still want to see the output of the ls command you can do it like this: [FONT="Courier New"]gnome-terminal -e 'bash -c "ls -a; read"'[/FONT] (you have to press Enter to close the terminal).

Your solution norco, opens another bash shell into the shell that ran the ls. If you do a pstree you'll see that you have something like this: bash--bash--pstree.

If you want color, you have to make the shell that runs ls an interactive shell, like this (add the -i option): [FONT="Courier New"]gnome-terminal -e 'bash **-i** -c "ls -a; exec bash"'[/FONT].

---

### Post by David_T on 2006-09-30
OK, I got it work in xfce4-terminal, so it should work in gnome-terminal.  You still have to make the change to ~/.bashrc, but then this script works, complete with ls colors:

```

#!/bin/bash
gnome-terminal -x bash -c "export START_DIR=/etc; bash"

```

---

### Post by Ziggy72 on 2006-09-30
Thank you all for your marvellous solutions.

May I suggest that one of you write a detailed "HOWTO Use a desktop Script to Start a Terminal, Execute Commands and View the Results within the Terminal".

That's a bit long-winded, but what you've suggested today deserves to be more widely known because I'm sure these techniques would be very useful to a lot of people.

David_T - the only thing wrong I see with your method is that the terminal command(s) have to be embedded within the ~/.bashrc file. Can the commands somehow be incorporated into the script?

Anyway, thanks once again to everybody - you're all very clever....:) :)

---

