---
title: "Strange error when using apt-get or add/remove"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-09-19
Today I was trying to install opera so I went to the terminal and typed the command (in bold) and got an error (last line).

> 
**fatsheep@fatsheep:~$ sudo apt-get install opera**
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.


Just now I went to Add/Remove and tried to install a game and then I got this:

> E: The package jedit needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have no idea what has gone wrong.  Help? :confused:

---

### Post by Brunellus on 2006-09-19
try 

sudo apt-get -f install

to see what happens.

---

### Post by aktiwers on 2006-09-19
I had the same problem, and got a pretty long thread about it. There is a lot of suggestions on how to fix this.

[http://www.ubuntuforums.org/showthread.php?t=252762](http://www.ubuntuforums.org/showthread.php?t=252762)

Strange enough, my problem solved it self, or maybe my typing some of all the commands suggested.. donno but take a look. 

Also I dont mention that I often did the "sudo aptitude" and tryid to remove the broken pages from there. But try out all the suggestions, and with a little luck, you will end up like me. With a problem solved (without knowing how :D)

---

### Post by fatsheep on 2006-09-19
> **Brunellus said:**
> try 

sudo apt-get -f install

to see what happens.


> **fatsheep@fatsheep:~$ sudo apt-get -f install**
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

> **aktiwers said:**
> I had the same problem, and got a pretty long threat about it. There is a lot of suggestions on how to fix this.

[http://www.ubuntuforums.org/showthread.php?t=252762](http://www.ubuntuforums.org/showthread.php?t=252762)

Strange enough, my problem solved it self, or maybe my typing some of all the commands suggested.. donno but take a look. 

Also I dont mention that I often did the "sudo aptitude" and tryid to remove the broken pages from there. But try out all the suggestions, and with a little luck, you will end up like me. With a problem solved (without knowing how :D)

Thanks I'm checking it out now

---

### Post by Brunellus on 2006-09-19
> **fatsheep said:**
> Thanks I'm checking it out now
synaptic and/or the update manager is still running somewhere.

---

### Post by fatsheep on 2006-09-19
Sorry that was careless of me.  Here's the output with no synaptic running:

> fatsheep@fatsheep:~$ **sudo apt-get -f install**
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.


---

### Post by fatsheep on 2006-09-19
Well still no luck, any ideas?

---

### Post by Brunellus on 2006-09-19
all repos in order and up to date?

---

### Post by jrobinson5 on 2006-09-19
Unfortunately for me, I've got the same problem. Tried the command you gave, got the same thing as him. This seems to be a pretty common problem.

---

### Post by fatsheep on 2006-09-19
> **Brunellus said:**
> all repos in order and up to date?

I'm not sure how I would tell but I've done the command

> sudo apt-get update dozens of times...

> Unfortunately for me, I've got the same problem. Tried the command you gave, got the same thing as him. This seems to be a pretty common problem.

If you find a solution then please do pm me?  I will do the same for you.

---

### Post by Brunellus on 2006-09-19
please post solutions to the thread if any are found.  

PMs aren't searchable (obviously).  The idea behind an open support forum is that people should be able to find the answer to their question--since someone else has probably asked it and answered it before.  solutions in pms only mean more questions here

---

### Post by jrobinson5 on 2006-09-19
> **fatsheep said:**
> I'm not sure how I would tell but I've done the command

 dozens of times...



If you find a solution then please do pm me?  I will do the same for you.

EUREKA! I found it!

Look here:
[http://www.ubuntuforums.org/showpost.php?p=1427262&postcount=18]("http://www.ubuntuforums.org/showpost.php?p=1427262&postcount=18")

I found out that my sources.list was completely empty:shock:. So I generated one on Source-O-Matic. Wierd.

It looks like the person who wrote the instructions added the SF site that hosts Jedit to their sources.list file; I just downloaded it.

I only had to do from where it says "# cd /var/lib/dpkg" onwards, but you may have to do the whole thing. Make sure you check your sources.list file and comment out [precede with #] any lines that mention sf.net.

Glad to help

---

### Post by fatsheep on 2006-09-19
That topic fixed my problem as well.  However, the only step I needed to follow was this:

> 
# cd /var/lib/dpkg

open the file status and delete any related lines to the packages jedit


I just opened up status and deleted the jedit paragraph and all was solved. :D

---

### Post by jrobinson5 on 2006-09-19
Yeah, this ought to be either stickied or put in the FAQ.

Sheep: That's a pretty cool looking sheep you got as your avatar.

---

### Post by fatsheep on 2006-09-20
What's strange is after I fixed the jedit problem my computer updated and I get a grub boot error 22 at bootup.  Basically this means the coordinates to my partition were changed so I had to bootup in the LiveCD and change them back.  This worked fine until another update came in and changed my partition's coordinates AGAIN.  So I went in and changed it back again and I'm wondering is this going to happen with every update?

---

