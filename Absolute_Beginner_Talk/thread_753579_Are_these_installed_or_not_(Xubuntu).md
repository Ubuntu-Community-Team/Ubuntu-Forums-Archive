---
title: "Are these installed or not? (Xubuntu)"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Mutant Corn on 2008-04-12
There's two programs on my computer -Zinf and Sound Converter- that show up in the Multimedia menu, but when I click on them nothing happens. I've only recently installed them, and this has happened since I put them in. I'm trying to get something that will play WMA...

Did they install wrong or something? Or did it miss a package somehow?

---

### Post by smartboyathome on 2008-04-12
Try running them from the terminal. I don't know the commands for them, but you could run "whois zinf", for example, and see the command. The terminal will give you the output, which you can post here to tell us why it won't start.

---

### Post by JoshuaRL on 2008-04-12
Do you have the Ubuntu Restricted Extras package installed?

And if you ever have a question about why a program doesn't load or has problems, try running it from the terminal.  An easy way to find the command to run the application is to go to the terminal and try:
```

apt-cache search guess-name-of-package

```
and see if you can find it.  Another way is to do it is to put the following into the terminal:
```

alacarte

```
and search through the menu until you find the right application.  If you either double click or click Edit to find the command to run the application.  Remove any % you see, and that should be the way to run the program in the terminal.

Any errors or output you get can lead you to a solution, or at very least give us more information.

---

### Post by JoshuaRL on 2008-04-12
> **smartboyathome said:**
> Try running them from the terminal. I don't know the commands for them, but you could run "whois zinf", for example, and see the command. The terminal will give you the output, which you can post here to tell us why it won't start.

Man, I forgot the "whois" command.  Thanks dude.

---

### Post by qamelian on 2008-04-12
> **JoshuaRL said:**
> 
```

sudo apt-cache search guess-name-of-package

```and see if you can find it.  Another way is to do it is to put the following 
You don't need sudo to search with apt-cache.

---

### Post by JoshuaRL on 2008-04-12
Thanks, I guess APT triggered my sudo.  Fixed.

---

### Post by niteshifter on 2008-04-12
Hi,

> but you could run "whois zinf"

Ah, no. whois is for networking, as in finding a domain name, IP address, etc. A whois on a system command gets nothing:
```
foo@bar:~$ whois bash
No whois server is known for this kind of object.
```

I think what you mean is the whatis command, which displays the one-liner descriptive text from a man page:
```
foo@bar:~$ whatis bash
bash (1)             - GNU Bourne-Again SHell
```

What's really handy about whatis is it's ability to take wildcards:
```
foo@bar:~$ whatis -w "pdf*"
```
will return one-liners for all the commands (in the man database) that begin with "pdf".

---

### Post by Mutant Corn on 2008-04-12
the whatis command yields "nothing appropriate" for both

"apt-cache search" yields descriptions, and descriptions of the packages as well for ZINF

alacarte picks them up, but there's no option to edit...

add/remove doesn't seem to detect them

---

### Post by JoshuaRL on 2008-04-12
I may have had the Edit tag wrong.  You want to double click them and look for the field for the command that clicking them does.

You can also look for them through Synaptic.

So you found the name of -zinf?  If you find the name, that's the command to run it.  Really simple.

---

### Post by Mutant Corn on 2008-04-13
:( Both gave errors

---

### Post by JoshuaRL on 2008-04-13
Okay, for the first one try:
```

sudo apt-get install decodebin

```
If it says its missing something, try to install it.

I'm not sure about the other error, I'll have to look at it more.  But it may just be that you have the default depth to the wrong thing for that program.  That looks like the error it's sending out.  Maybe someone could enlighten me though.

---

