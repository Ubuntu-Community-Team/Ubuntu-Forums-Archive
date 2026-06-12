---
title: "What is the . (dot) used for?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-17
In a lot of scripts, I see a dot space used..e.g. 

if [ -e $HOME/.alias ]; then
  [ -n "$PS1" ] && . $HOME/.alias
fi


What does the dot space before the $HOME do?

---

### Post by meatpan on 2007-12-17
Good question.  In the context above, the '.' is actually a built-in shell command.  

A quick snippet from the built-in command docs:
> 

. filename [arguments]
Read and execute commands from filename in the current shell environment and return the exit status of the last command executed from filename.


This is useful for running a text file that contains a bunch of commands.

---

### Post by santiagoward2000 on 2007-12-17
Hi there!
Really, the dot at the beginning of a file's name means that that file is hidden. For example, if you want to hide the file called **file**, all you have to do is rename it to **.file**

---

### Post by movrshakr on 2007-12-17
Wow, powerful little dot.

So, (I'm just learning bash scripting), I had decided that the
[ -n "$PS1" ] && . $HOME/.alias
line generated a prompt, followed by the command to be executed ($HOME/.alias).
So why would the dot be needed?  Or why would the prompt be needed, e.g., why not:
. $HOME/.alias or
exec $HOME/.alias or just
$HOME/.alias

??

---

### Post by bodhi.zazen on 2007-12-17
Depends . and .. can be used in the path as well

. also means current directory One uses this to start applications not in $PATH. Example, say you have a script in $HOME/bin 

cd ~/bin
sh ./application

ls ..

.. = parent directory

To list hidden files :

ls -a

To list hidden files with out seeing . or ..

ls -A

---

### Post by movrshakr on 2007-12-17
bodhi.zazen, actually this topic was about (dot) (space) not the (dot)(name) that denotes hidden file.

---

### Post by bodhi.zazen on 2007-12-17
.(space) = current directory

.(file) = hidden file

---

### Post by movrshakr on 2007-12-17
> .(space) = current directory

Others earlier contradict this, saying the .(space) is a command to execute the filename which follows.

This is getting confusing.

---

### Post by meatpan on 2007-12-17
Since '.' can mean many things in a shell, and can be difficult to distinguish by eye, consider using 'source' instead of '.' to execute the commands in a file.

---

### Post by movrshakr on 2007-12-17
I did a  "man source" and it isn't there.

---

### Post by LaRoza on 2007-12-17
> **movrshakr said:**
> > .(space) = current directory

Others earlier contradict this, saying the .(space) is a command to execute the filename which follows.

This is getting confusing.

Exampes to clear up the confusion. In the shell, there is a variable named $PATH, it is where the shell looks for programs.

If you had a program named "abc" in your home directory (for example), you could not run it by typing its name. The shell would look in the $PATH, and that is not where "abc" is.

You have to specify where the program is, so you could use:

```

/home/laroza/abc

```

Long, a bit shorter:

```

~/abc

```

(~ means /home/<username>)

or:

```

./abc

```

The last one says "in this folder".

The "." is often used to specify the current directory when trying to run scripts and programs.

---

### Post by psusi on 2007-12-17
The [ -n part is a test for a non zero string ( see man test, which [ is a symlink to for shorthand ), so it is checking to see if the PS1 variable has been set to anything.  Only if PS1 has been set to something, it opens the file ".alias" in your home directory, and interprets the commands there before returning.  

exec replaces the current shell with the specified executable program.  The script wants to keep running, and .alias is not executable so it would not work.  $HOME/.alias would return to the calling script, but again, .alias is not executable.

---

### Post by Junglizer on 2007-12-17
I'd like to add that since .(space) = current working directory, you can use this, as well as ..(space) as handy shortcuts in the terminal. 

```
cd ../home
```

---

### Post by psusi on 2007-12-17
> **Junglizer said:**
> I'd like to add that since .(space) = current working directory, you can use this, as well as ..(space) as handy shortcuts in the terminal. 

```
cd ../home
```

A dot as part of a path name means the current working directory, a dot used as a command ( as it is in this guy's question ) causes the specified file to be read and its contents interpreted.

---

### Post by movrshakr on 2007-12-17
Yes, this kind of got off track on the use of the dot and dotdot as directory reference.  I am quite familiar with that.  It was its use as a command that completely threw me.

Am I to understand that 'source x' is the same thing as ' . x'?  (dot x)

I tried 
sudo source x 
on something and it failed, but source x worked.  Weird.

Also weird that source has no man page.

---

### Post by bodhi.zazen on 2007-12-17
> **psusi said:**
> A dot as part of a path name means the current working directory, a dot used as a command ( as it is in this guy's question ) causes the specified file to be read and its contents interpreted.

Depends on the location of the dot, no ?

./file =! /.file

---

### Post by movrshakr on 2007-12-17
bohdi.zazen, we aren't talking about .file or ./file

We are talking about dot as a COMMAND...

dot (space) something

REPEATING:
Am I to understand that 'source x' is the same thing as ' . x'? (dot x)

I tried
sudo source x
on something and it failed, but source x worked. Weird.

Also weird that source has no man page.

---

### Post by tgalati4 on 2007-12-17
If you are not completely confused yet, go into your Desktop directory:

>cd

>cd Desktop

>cp ../../../etc/hosts . 

Now you will have a copy of your hosts file on your desktop.

Of course you could have just done:

>cp /etc/hosts .

But that doesn't have as many dots, and we are talking about dots.

---

### Post by movrshakr on 2007-12-17
I give up.

We were trying to talk about the dot as a command, and everybody keeps going back to using it as a directory reference.

---

### Post by bodhi.zazen on 2007-12-17
.

is not a command

@movrshakr


Which of these commands do you want explained ?

> # Current directory = $HOME/bin


# Show contents of $HOME/bin/echo
bodhi@VirtualUbuntu:~/bin$ cat echo                          
#! /bin/bash
echo "it works"

# run echo
bodhi@VirtualUbuntu:~/bin$ echo                               

##Run $HOME/bin/echo
bodhi@VirtualUbuntu:~/bin$ ./echo                             
it works

###Variations
bodhi@VirtualUbuntu:~/bin$ /.echo                             
zsh: no such file or directory: /.echo

#### . is not a command
bodhi@VirtualUbuntu:~/bin$ . echo                            
/bin/echo:3: parse error near `)'

bodhi@VirtualUbuntu:~/bin$ .                                  
.: not enough arguments

---

### Post by movrshakr on 2007-12-17
bohdi.zazen, you obviously missed the post above by meatpan:

[B]Good question. In the context above, the '.' is actually a built-in shell command.

A quick snippet from the built-in command docs:
Quote:

.  filename [arguments]
_*Read and execute commands from filename in the current shell environment and return the exit status of the last command executed from filename.*_
This is useful for running a text file that contains a bunch of commands.[/B]

Yes, there are times it is indeed a command, and that is what I was trying to sort out/understand.  Go back and read the very first posts.  Then people started talking about the use as directory or as designator for hidden files, which was not the question at all...

which, by the way is now answered as shown in the bold type above.

---

### Post by bodhi.zazen on 2007-12-17
oic , thanks for your patience

---

### Post by HermanAB on 2007-12-17
Some dots are more dotty than others...

I avoid using dats and doshes wherever possible, since it makes scripts hard to read.

Cheers,

Herman

---

### Post by meatpan on 2007-12-18
> **movrshakr said:**
> I did a  "man source" and it isn't there.

I'm not sure why 'man source' isn't working.  This command on RHEL 9 (distro I use at work) returned the bash built-in command manual, but I couldn't find anything on a ubuntu or debian system.

If you want to see documentation for source, and any other bash built-in commands, you can open up the bash manual and then scroll all the way down to view the built-in command list.

---

### Post by spec-chum on 2007-12-18
From the shell builtins section of the bash manpage (man bash for details)

        .  filename [arguments]
       source filename [arguments]
              Read  and  execute  commands  from filename in the current shell environment and return the exit
              status of the last command executed from filename.  If filename does not contain a  slash,  file
              names in PATH are used to find the directory containing filename.  The file searched for in PATH
              need not be executable.  When bash is not in posix mode, the current directory is searched if no
              file is found in PATH.  If the sourcepath option to the shopt builtin command is turned off, the
              PATH is not searched.  If any arguments are supplied, they become the positional parameters when
              filename  is executed.  Otherwise the positional parameters are unchanged.  The return status is
              the status of the last command exited within the script (0 if no  commands  are  executed),  and
              false if filename is not found or cannot be read.

so yes, . x and source x are interchangeable.

---

### Post by psusi on 2007-12-18
> **movrshakr said:**
> Yes, this kind of got off track on the use of the dot and dotdot as directory reference.  I am quite familiar with that.  It was its use as a command that completely threw me.

Am I to understand that 'source x' is the same thing as ' . x'?  (dot x)

I tried 
sudo source x 
on something and it failed, but source x worked.  Weird.

Also weird that source has no man page.

That fails because sudo can't find a program named source, as it is a shell  builtin command.  If you really want to interpret script x as root, do sudo bash x.

---

