---
title: "Shell Function"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-08-15
I am trying to learn Bash scripting. Right now, I am stuck with shell functions.

Say that we have a shell function as the following:
# filename: my_function
my_cp()
{
  if test ! -s "$2"
  then cp "$1" "$2"
  else echo "mycp: cannot copy $1: $2 exists"
  fi
}

What do I need to do so that I can call the function from prompt? For example, 
$ my_cp file1 file2

Thanks.


Buhi

---

### Post by Cone on 2006-08-16
I'm not really much for shell scripting yet, but as there's no responses yet I'll add what I can.

I believe if you hit enter with all the function things typed in you should be able to call it?

For a good place to learn more and helpfully solve your problem check out [this link]("http://www.tldp.org/LDP/abs/html/").

Hope this helps,
~Cone

[EDIT: Wrong link, whoops.]

---

### Post by LadyDoor on 2006-08-18
What you need to do is make it execuble and put it in your $PATH (the $PATH is where BASH looks for runnable programs...if you left the file in your home dir, for example, you could run it with ./my_cp (or whatever you called the file)). First, let's create ~/bin--a safe place to keep anything you write.

```
$ mkdir ~/bin
```

Now, let's find out if that's in your path.

```
$ echo $PATH|grep ~/bin
```

If there is any output from that command, then ~/bin is in your $PATH. If not, make a backup of your .bashrc and then open up .bashrc with your favorite editor, then enter the following lines:

```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"

```

Then, move the file to ~/bin and do 

```
$ chmod +x name_of_file
```

Now, all you need to run it is to type whatever you ended up naming it into a terminal.

I hope that helped!

--Door

P.S.:  Is this a bash script? If so, don't forget to add
```
#!/bin/bash
```

---

