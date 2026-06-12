---
title: "Simple BASH script problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-05-06
Hi all,

I'm having a small problem making a bash script. If you dont know what a bash script is you probably can't help me.

I'm making the file to run a program under wine. I need one because I have to use some options when I run the program with wine and don't want to type them out everytime I use them and I want the shell script file so it will be more platform-independent.

In a nut shell I'm having trouble with making a variable value with whitespace in it. I read the man page for bash and found a tutorial website: [http://www.gentoo.org/doc/en/articles/bash-by-example-p1.xml?style=printable](http://www.gentoo.org/doc/en/articles/bash-by-example-p1.xml?style=printable)
which tells me that if I use single or double quotes i can put whitespace in the variable's value.

so I have:

```
MYVAR='/home/catfish/some directory with spaces/directory'
or
MYVAR="/home/catfish/some directory with spaces/directory"
```

to set the value of $MYVAR in my script, but when I call:
```
cd $MYVAR
```
in my script it outputs:

> cd: 16: can't cd to /home/catfish/some

Anyone know why? It's probably really easy and I haven't read the docs enough.

---

### Post by Famicommie on 2007-05-06
From my understanind, bash can understand spaces in file names if you format them with a back slash preceeding the space, like so:
/home/user/lol\ here\ is\ some\ white\ space

where the directory is named "lol here is some white space"

---

### Post by igknighted on 2007-05-06
> **Catfish81 said:**
> Hi all,

I'm having a small problem making a bash script. If you dont know what a bash script is you probably can't help me.

I'm making the file to run a program under wine. I need one because I have to use some options when I run the program with wine and don't want to type them out everytime I use them and I want the shell script file so it will be more platform-independent.

In a nut shell I'm having trouble with making a variable value with whitespace in it. I read the man page for bash and found a tutorial website: [http://www.gentoo.org/doc/en/articles/bash-by-example-p1.xml?style=printable](http://www.gentoo.org/doc/en/articles/bash-by-example-p1.xml?style=printable)
which tells me that if I use single or double quotes i can put whitespace in the variable's value.

so I have:

```
MYVAR='/home/catfish/some directory with spaces/directory'
or
MYVAR="/home/catfish/some directory with spaces/directory"
```

to set the value of $MYVAR in my script, but when I call:
```
cd $MYVAR
```
in my script it outputs:



Anyone know why? It's probably really easy and I haven't read the docs enough.

Because there are spaces in the path.  Try making it like this:

```
MYVAR=/home/catfish/some\ directory\ with\ spaces/directory
```

---

### Post by Catfish81 on 2007-05-06
doing this yields the same output as the original post.

---

### Post by Catfish81 on 2007-05-06
ok i've debugged a little and have found that the value is being SET correctly, but when I do: 
```
cd $MYVAR
```
it is not interpreting the value correctly and terminates the value at the first whitespace. is there a special way of calling the variable inside of a bash script to get it working right?

---

### Post by hyper_ch on 2007-05-06
well, this

```

#!/bin/bash
VAR="/path/to/some of my files/in/the/directory"

echo $VAR

```

echoes this:

```

hyper@xubi:~$ sh test.sh
/path/to/some of my files/in/the/directory

```

Have you set on top what shell shall be used? (e.g. bash)?

---

### Post by Catfish81 on 2007-05-06
yeah i have that.

I worked out how to make it work, but don't know the reasons why.

```

MYVAR="/home/catfish/some dir with spaces/directory"
# echo works fine...
echo $MYVAR
# cd needs double quotes...
cd "$MYVAR"
# otherwise the value is interpreted as: /home/catfish/some

```

there would be some reason for this but i just need it to work at the present time so Im not going to look for an answer to it.

---

### Post by hyper_ch on 2007-05-06
well, it works :)

---

### Post by Tundro Walker on 2007-05-06
I was screwing around with this too, and I think there's some limitation in the "cd" command accepting input from variables.  For instance, this works...

```
cd "My Folder"
```

...and so does this...

```
cd 'My Folder'
```I tested to see if maybe the variable was just truncating, but...

```
MYFOLDER="My Folder"
echo $MYFOLDER
```...returns "My Folder" echo'ed ok.

```
MYFOLDER="My Folder"
cd $MYFOLDER
```...however, returns "cd: 4: can't cd to My".  So, it's truncating the varaible's contents for some reason.  I thought maybe I had to explicitly create some quotes for it to use, so I tried this...

```
MYFOLDER="'My Folder'"
echo $MYFOLDER
cd $MYFOLDER
```...but while it echo'ed "'My Folder'" ok, the cd returned "cd: 8: can't cd to 'My".

I've got a Linux book (a large "Linux for Dummies" book, which is "8 books in 1", one of which talks about scripting), and the writer coded some script with variables that had a # comment saying "no embedded spaces".  He doesn't elaborate on that, though.  I guess spaces are allowed when echo'ing, but not allowed in variables when using other commands, like "cd".

I tried ad-hoc'ing my way around this, but didn't get any where.

---

### Post by Catfish81 on 2007-05-06
Yes, one of these little things that is buried somewhere in thousands of pages of documentation and takes you a week to read and find. Anyhow, buggering with the code has worked for me and I'm not too keen to find out why it works one way rather than the other.

---

### Post by hartz on 2007-05-06
I will try to explain it this way.

When you do a chdir (cd) command, the shell (bash) will pass each argument, deliminated by blanks, to the program.  This "splitting up of the string into separate argument words is done by the shell BEFORE the command is executed.

The entire command line is split up into "words" by the shell.  The first word is the name of the program to run (there are exceptions, but that is not relevant here; "cd" also technically is not a command, but rather a so-called shell builtin).  The other "words", other than the command name, are the arguments.

Example
```
cd [COLOR="Red"]/mydir[/COLOR]
```

In my example the "command" is "cd" and the argument is /mydir.

Another example, this time with two arguments:

```
cp /path/to/my/file /path/to/target
```

Now here is a trick question:  How many arguments does the following command have:

```
echo *
```

To find out the answer to this, We can write a short one-line script, like this
```
#!/bin/sh
echo Found $# arguments on the command-line.

```

(May be a two-line script, but the first line is not a command in the script)

Note: The bit that shows $# will automatically evaluate to the number of arguments passed to the script.

Put those lines into a small file, eg /tmp/argtest.  Then make it executable using this command:
```
chmod +rx /tmp/argtest
```

Now lets run some tests.

```
hartz@linwarg:/tmp$ /tmp/testargs
Found 0 arguments on the command-line.
hartz@linwarg:/tmp$ /tmp/testargs X X X
Found 3 arguments on the command-line.
hartz@linwarg:/tmp$ /tmp/testargs X
Found 1 arguments on the command-line.

```

So far so good - all is as expected.

Now lets test it with a variable.
Set a variable and pass it to the script:
```
MYVAR="This-is-a-string-with-no-spaces"
hartz@linwarg:/tmp$ /tmp/testargs $MYVAR
Found 1 arguments on the command-line.
```

Nothing strange here.   Lets now put spaces into the variable:
```
MYVAR="This is a String with spaces"
hartz@linwarg:/tmp$ /tmp/testargs $MYVAR
Found 6 arguments on the command-line.
```

And one final run, without modifying the value of MYVAR, but passing it in quotes:
```
hartz@linwarg:/tmp$ /tmp/testargs "$MYVAR"
Found 1 arguments on the command-line.

```

And to answer the question at the top:
```
hartz@linwarg:/tmp$ /tmp/testargs *
Found 27 arguments on the command-line.

```

Where does those 27 (in my case) arguments come from?

This little trick will reveal much:
Re-run the test, but first enter the command set -x to print debugging info:
```
hartz@linwarg:/tmp$ [COLOR="Red"]set -x[/COLOR]
++ echo -ne '\033]0;hartz@linwarg: /tmp\007'
hartz@linwarg:/tmp$ /tmp/testargs *
+ /tmp/testargs assemblymanual.pdf atop.d comtest com-test.zip flashgot.gfrhr9eh.default gconfd-hartz gconfd-root gnome-system-monitor.hartz.3159815534 hsperfdata_hartz hsperfdata_root kde-hartz keyring-8C42cd ksocket-hartz libgksu-h96MSM libgksu-YXvfAx mapping-hartz orbit-hartz orbit-root plugtmp plugtmp-1 scrollkeeper-hartz ssh-eLmEG12773 ssh-fLmEG12773 testargs tzdata-2007b tzdata_2007b.orig.tar virtual-hartz.TJ5qAU
Found 27 arguments on the command-line.
++ echo -ne '\033]0;hartz@linwarg: /tmp\007'
hartz@linwarg:/tmp$ [COLOR="Red"]set +x[/COLOR]
+ set +x
```

Note that "set -x" will cause debugging info, each debugging line printed with a leading +, be displayed before each command is executed.  The set +x is used to end the debugging session.

If you've followed this far you will have learned a few things:
1) To set a variable to a value containing spaces, the whole value must be quoted.
2) To dereference a variable containing spaces into a single argument, the variable needs to be quoted with double-quotes.
3) Stating a variable on the command-line as an argument to a command without quotes allows the shell to break it up into separate words to be passed to various variables.

There is one other aspect to "quoting" in the Unix shell.  This is the single-quote, sometimes called hard-quoting.

Hard-quoting can be used to prevent the shell from interpreting the "$" in the argument as a special symbol which, in this case means that the word following it is to be treated as a variable name which must be expanded.

Therfore using debugging again:
```
hartz@linwarg:/tmp$ set -x
++ echo -ne '\033]0;hartz@linwarg: /tmp\007'
hartz@linwarg:/tmp$ /tmp/testargs '$MYVAR'
+ /tmp/testargs [COLOR="Red"]'$MYVAR'[/COLOR]
Found 1 arguments on the command-line.
++ echo -ne '\033]0;hartz@linwarg: /tmp\007'
hartz@linwarg:/tmp$ /tmp/testargs "$MYVAR"
+ /tmp/testargs [COLOR="Red"]'This is a string with spaces'[/COLOR]
Found 1 arguments on the command-line.
++ echo -ne '\033]0;hartz@linwarg: /tmp\007'
hartz@linwarg:/tmp$ set +x
+ set +x
```

Note that a single back-slash, i.e. \ is used to "hard-quote" a single character.  Therefore
echo '$MYVAR'
is the same as 
echo \$MYVAR

Lastly in case it is not quite clear, after the shell has done variable expansion, it removes all quotes that are not themselves quoted, before passing the arguments to the program.

Hopefully this makes variable expansion a little more understandable.

Ask away if you have more questions :-)

---

### Post by Catfish81 on 2007-05-10
Seeings as i'm here and still bash scripting, do you know how to take a full path and filename string (eg: /home/catfish/directory/filename.ext) and split the filename off the end of it to leave just the path and vice versa? (pop the path off to just leave the filename)

I saw this done in a tutorial 3 days ago, but I can't find that website again for the life of me. And my browser history is only kept for 2 days!  They were using single functions to do it. Like (what I vaguely remember it to be like):

$FULLNAME = "/path/to/filename.ext"
$PATHNAME = topath($FULLNAME)

it was similar to this. what i'm saying is, that they didn't get $FULLNAME and find the number of chars in it and then seek to an offset in the string and then remove x amount of characters from there to remove the filename. it was just one simple function to do it.

---

### Post by hartz on 2007-05-10
There is a very clever way to do this:

Example:
```
FULLNAME=/long/path/to/file
echo Full=$FULLNAME

NAME=${FULLNAME##*/}
PATHPART=${FULLNAME%%$NAME}

echo Name=$NAME
echo Path=$PATHPART
```

How does that work?

The trick lies in ${ ## } and ${ % }

The ## operator will remove a leading portion from the value and return it.
The % operator will remove a trailing portion.
In this case I remove the largest portion ending in a / - that will leave me with only the file name part.
Then I use the file name part to remove the file name part from the original variable, leaving only the "full path" to the file to be returned.

WARNING:  I used variables "FULLNAME", "NAME", and "PATHPART" ... one might be tempted to use "PATH" but it has got special meaning to the shell - it tells the scripts where to find programs, so don't change it unintentionally.

---

### Post by Catfish81 on 2007-05-17
PATHTO=${ABSOLUTE%/*}					 	# Get *path* only to ABSOLUTE filename

I found this on a website. It will strip the filename and (I think) trailing / from an absolute path and return only the path name. As you said, do not be tempted to use vriable name PATH.

---

### Post by pacific35 on 2007-06-14
you can use the basename and dirname utilities to write either the path prefix or suffix to standard output;

```
$ basename /home/catfish/directory/filename.ext
filename.ext
$ dirname /home/catfish/directory/filename.ext
/home/catfish/directory
```

I hope this helps

---

