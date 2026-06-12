---
title: "Batch Scripting i can do in Unbuntu?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by truth on 2006-06-08
Hi All =)   I was just wondering, is there some kind of Batch Scripting i can do in Unbuntu? 

The closest thing ive found to  .bat files and scripts in Unix is   Make or MakeFile 

but Ubuntu Seems to be missing it. . . why is that? 

Is ubuntu using a Different Shell?  

Ive only used Bash under Slackware and FreeBSD and both i belive had MakeFile? 

Also if i wanted to add new tools to my Shell,  lets say such as Nmap all i would need to do is download it from the  Nmap website or what. . .? is there some kind of    List of Compatible Programs or Apps for Ubuntu Only, becuase i know Ubuntu is based on Debian so ofcourse i woulndt be able to use something such as Ports from FreeBSD?  Where is our Port List?   

Thx

---

### Post by mostwanted on 2006-06-08
The shell in most Linux distros is called BASH or SH. Batch is, basically, the crap Windows imitation of a real Linux shell. Open up a terminal and you have BASH which has many of the features of a real programming language, unlike Batch. May want to visit this site:

[http://linuxcommand.org](http://linuxcommand.org)

Makefiles are used for making the compile and install process automatic for source packages, not really anything to do with shell scripting.

When you install a program in Ubuntu, most likely the program executable or a link to exectable is gonna be put in /usr/bin which means it's accessible as a command in the shell.

nmap can be installed through APT, you don't have to put anything anywhere. Take a look at this guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by IYY on 2006-06-08
Making a script file is very simple. Just create a plain text file (ascii) with the commands you want to execute. For example, let's create a file called myscript with the following text in it:

```
echo hello world
touch mynewfile.txt
ls -l mynewfile.txt
rm mynewfile.txt
```

These are just regular shell commands you can use in the command line: the first one prints "hello world" on the screen, the second creates a file, the third prints out the information about the file, and the last removes that file.

To make the script executable, do the following:
```

chmod +x myscript
```

and then to run it:

```
./myscript

```

If you want to specify which shell should run the script, add it as a comment on the first line of the script file. For example, if we want to run our command in the sh shell:

```

#!/bin/sh
echo hello world
touch mynewfile.txt
ls -l mynewfile.txt
rm mynewfile.txt
```

The most common shells are bash and sh. In the shell script, you can have execute any programs and commands you wish, create variables, use loops and much more.

---

### Post by matthew on 2006-06-08
My friend, you are in luck. Scripting is common and easy with Linux. You will have to do a little homework to get started, but you are in for a treat. Here's a place to look for information: [http://www.tldp.org/LDP/abs/html/]("http://www.tldp.org/LDP/abs/html/")
[QUOTE=Advanced Bash Scripting Guide, intro page]This tutorial assumes no previous knowledge of 	scripting or programming, but progresses rapidly toward an 	intermediate/advanced level of instruction *. . . all 	the while sneaking in little snippets of UNIX® wisdom and lore*. It 	serves as a textbook, a manual for self-study, and a reference and 	source of knowledge on shell scripting techniques. The exercises 	and heavily-commented examples invite active reader participation, 	under the premise that **the only way to really learn 	scripting is to write scripts**.[/QUOTE]

---

### Post by siminone on 2006-06-08
[QUOTE=mostwanted] Batch is, basically, the crap Windows imitation of a real Linux shell. ][/QUOTE]

The window Terminal is the legacy of MS-DOS and was about 10 years before Linux was a sparkle in Linus Torvalds eye. 

Before there is any flame, the terminal was never meant to be as sophisticated as bash and has been acknowledged by MS as they are putting a shell scripting terminal in vista.

---

### Post by truth on 2006-06-08
wow. . . Awesome Awesome Feedback you guys!! your the best!!  (using my bash emulator on Windows) I tried a small script using    echo "hello world"    ran it with ./  works good so i will try some more stuff . . .  

i orginally wanted to shell script so i may have a shortcut to installing certain things like my ATI Drivers. . . 

Im at work now but when i get home ill give it a go. . .should be Fun Thx guys. . .

p.s.  with such a good community as this i serously Doubt Ubuntu will stray from being #1  =)  its great to be apart of this Thx Again

---

### Post by angkor on 2006-06-08
[QUOTE=siminone]The window Terminal is the legacy of MS-DOS and was about 10 years before Linux was a sparkle in Linus Torvalds eye. 
[/QUOTE]

Yet the Bourne shell wasn't.

[http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell)

---

