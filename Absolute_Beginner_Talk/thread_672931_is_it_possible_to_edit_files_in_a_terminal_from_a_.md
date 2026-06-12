---
title: "is it possible to edit files in a terminal from a script?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by seregaShishkilov on 2008-01-20
Hello everyone, I have installed ubuntu 7.10 a few days ago (and love it).

Some of my friends after seeing what ubuntu can do, really want it as well, however they want all the software (like compiz fusion, wine...) pre installed, the best I could offer them was script that installs the software, they agreed. However in the script I need to edit a file, I can not use *sed* or *perl* as I do not know what their file configuration is, what I am looking for is to somehow tell the terminal that the *controll* or *delete* key is pressed. (in other words I need a way to use *nano* from a script) or is there another way?

Please help a semi-nub

---

### Post by tukuyomi on 2008-01-20
Seems a little confuse, but if I understand well, are you trying to alter the sources.list to add more repositories?

---

### Post by frup on 2008-01-20
All this is non-repo software?

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) is an advanced bash scripting guide you might find useful. 

This is how you write to files
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

You want to learn piping, awk and grep

[http://tldp.org/LDP/abs/html/awk.html](http://tldp.org/LDP/abs/html/awk.html)
[http://www.hmug.org/man/1/awk.php](http://www.hmug.org/man/1/awk.php)
[http://www.ss64.com/bash/grep.html](http://www.ss64.com/bash/grep.html)

---

### Post by seregaShishkilov on 2008-01-20
> **tukuyomi said:**
> Seems a little confuse, but if I understand well, are you trying to alter the sources.list to add more repositories?

Precisely, but thats not the only thing I want to do, I want to pretty much replace their sources.list with my one, as it has a lot of repos they might need later on.

@ frup: your second link seems to be what I need, i will try and get my head around it as I am not too familiar with it. And some of this is non repo, some is, but my friends wanted what they saw, and nothing more, saying it would be enough and whe I tried telling them how to install things like compiz fusion, they looked confused when I said "Open terminal and type sudo"

EDIT: command < input-file > output-file

This would mean that I put MY sources.list in place of the "output file" and THEIR sources.list in place of the < input file > correct?

---

### Post by tukuyomi on 2008-01-20
Oh OK
Then, first, you should back-up their actual source.list. Run as root (or use sudo instead)
```
# mv /etc/apt/sources.list /etc/apt/sources.list.backup
```
_The following is an example_
Then, to REPLACE (the old source.list -hence the back-up ;)-will be erased with the first following command) you can (in a script or on a terminal) *look closely to the `>` and `>>`*

```

echo '#- STABLE BRANCH -' > /etc/apt/sources.list
echo 'deb http://ftp.us.debian.org/debian/ stable main contrib non-free' >> /etc/apt/sources.list
echo 'deb http://security.debian.org/ stable/updates main contrib non-free' >> /etc/apt/sources.list
echo '# Add more comments and repositories with >>' >> /etc/apt/sources.list

```

---

### Post by frup on 2008-01-20
if you just wan't to replace the sources.list and initiate a set of apt-gets you can create a bash script 

mv  /etc/apt/sources.list  /etc/apt/sources.list_old
mv -f $/Desktop/sources.list /etc/apt/sources.list
sudo apt-get install program1 program 2 etc.

This presumes that the desired sources.list is on the desktop... eg dragged from disc

---

### Post by seregaShishkilov on 2008-01-20
Thanks a lot people replacing makes it a whole lot easier.

Why did I never think of replacing the actual file? For some strange reason I thought the only way would be to edit the file in a terminal and save it...

---

### Post by tukuyomi on 2008-01-20
LoL simpler solutions are often the best, you're welcome =)

---

### Post by zipperback on 2008-01-20
It would be best if you walked your friends through the install and then taught them how to manage their packages and install software for themselves.

- zipperback
:popcorn:

---

### Post by frup on 2008-01-20
Yeah I spent and hour today showing my grandma xorg.conf and what I was editing in it for her laptop :D. Then we opened gconf-editor and made some key bindings to toggle on and off her laptops touch pad :) She was thrilled to half understand it and thought Ubuntu was such a clever system that we could do something like that :)

---

### Post by DasCrushinator on 2008-03-04
> **tukuyomi said:**
> Oh OK
Then, first, you should back-up their actual source.list. Run as root (or use sudo instead)
```
# mv /etc/apt/sources.list /etc/apt/sources.list.backup
```
_The following is an example_
Then, to REPLACE (the old source.list -hence the back-up ;)-will be erased with the first following command) you can (in a script or on a terminal) *look closely to the `>` and `>>`*

```

echo '#- STABLE BRANCH -' > /etc/apt/sources.list
echo 'deb http://ftp.us.debian.org/debian/ stable main contrib non-free' >> /etc/apt/sources.list
echo 'deb http://security.debian.org/ stable/updates main contrib non-free' >> /etc/apt/sources.list
echo '# Add more comments and repositories with >>' >> /etc/apt/sources.list

```

I tried (and would prefer) this method, but kept getting an error:

> 
matthew@matthew-laptop:~$ sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
[sudo] password for matthew:
matthew@matthew-laptop:~$ sudo echo 'deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras' >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
matthew@matthew-laptop:~$ sudo echo 'deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras' >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
matthew@matthew-laptop:~$ 


---

### Post by tukuyomi on 2008-03-06
```
sudo "echo 'deb http://apt.wicd.net feisty extras' >> /etc/apt/sources.list"
```
Does this work? (added the double quotes!)

---

### Post by DasCrushinator on 2008-03-06
> **tukuyomi said:**
> ```
sudo "echo 'deb http://apt.wicd.net feisty extras' >> /etc/apt/sources.list"
```
Does this work? (added the double quotes!)

No, but I did get this to work:

> sudo su -c 'echo deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras >> /etc/apt/sources.list'

---

### Post by tukuyomi on 2008-03-06
A most direct path would be to use ```
$ sudo -s
or
$ sudo -i
``` but don't forget to ```
# exit
``` after that!

---

### Post by DasCrushinator on 2008-03-06
> **tukuyomi said:**
> A most direct path would be to use ```
$ sudo -s
or
$ sudo -i
``` but don't forget to ```
# exit
``` after that!

Hmm?  I just found that command (sans what the echo said) so I am not sure what you are telling me.

---

