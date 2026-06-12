---
title: "Terminal Aliaas?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-22
Okay herd that there are like alias for terminals for like certian programs like music and stuff. I have only seen a couple not alot and i dont really understand what they are for. If anyone can tell me what they ar for and what they can be used for and what not

---

### Post by p_quarles on 2008-01-22
They're kind of like miniature scripts. It makes it easier to run long commands that you use frequently. For instance, if you had an rsync command that you run on a regular basis, you could make an alias for for it by adding a line like this to ~/.bashrc:
```
alias syncdocs='rsync -vrtplze ssh --progress --stats --delete /home/uersname/Documents/ username@othermachine:/mnt/backup'
```
Now, you would be able to run that long command automatically simply by typing "syncdocs" in the terminal.

---

### Post by wolfen69 on 2008-01-22
here you go. [http://www.ubuntuhacker.com/index.php/2007/06/18/adding-terminal-aliases-to-ubuntu/](http://www.ubuntuhacker.com/index.php/2007/06/18/adding-terminal-aliases-to-ubuntu/)

---

### Post by fedex1993 on 2008-01-22
Okay so i could like make and ssh one?

---

### Post by p_quarles on 2008-01-22
> **fedex1993 said:**
> Okay so i could like make and ssh one?
You can make an alias for any command that you have installed.

---

### Post by fedex1993 on 2008-01-22
Thats pretty awesome i like also cant you like change the colors of the terminal to?

---

### Post by bump_ on 2008-01-22
> Okay so i could like make and ssh one?

Easily. The syntax is
```
alias someName=ssh user@host
```

You can replace someName with whatever name you wish. Typing this in the terminal will only last for that session though. To make it permanant, you have to add the command to ~/.bashrc

Also, in case you didn't know, if you just type "alias" in the terminal, it will show you all of your current aliases

---

### Post by gvartser on 2008-01-22
> **fedex1993 said:**
> Thats pretty awesome i like also cant you like change the colors of the terminal to?
He he you are funny.. Like it.. ;)

---

### Post by fedex1993 on 2008-01-22
and what i meant by colors is i rember you could just change like the user names to stay one color and everything else stays one color  like something@wha3s and something would be red and then wa3s would be white i rember reading a guide about it but havnt seen it anywhere in a while

---

### Post by fedex1993 on 2008-01-22
> **bump_ said:**
> Easily. The syntax is
```
alias someName=ssh user@host
```

You can replace someName with whatever name you wish. Typing this in the terminal will only last for that session though. To make it permanant, you have to add the command to ~/.bashrc

Also, in case you didn't know, if you just type "alias" in the terminal, it will show you all of your current aliases
how do i add it to my bashrc like where at on it

---

### Post by bump_ on 2008-01-22
I'm not sure, but I think anywhere in the file will suffice. To be on the safe side, look toward the end of it, you will see a part titles "Alias Definitions". In there is fine.

---

### Post by tojge on 2008-01-22
Yeah, anywhere in the file is okay, that is, it works, but it's always nice to be organized, so, put them somewhere towards the end, and keep all of your aliases together, it will make your life a bit less complicated :-)

Also, I like to have them logically grouped according to purpose, with a little comment (lines beginning with the **#**, which are ignored) before each group.

This screenshot should illustrate the point, though on the machine I'm currently working from, there really aren't that many aliases defined to begin with. Still...

[IMG]http://xs223.xs.to/xs223/08042/snapshot47474.png[/IMG]

---

### Post by bodhi.zazen on 2008-01-22
like this ?

[img]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_xterm.png[/img]

You need to add color information to .bashrc :

> # Colors
BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'              # No Color


Then you can :

play :

> PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$' #Green

echo -ne "${CYAN}";uptime
echo -e "${LIGHTGREEN}"; display-dhammapada; echo ""
echo -ne "${LIGHTBLUE}""Peace be with you $USER"

and on ...

---

### Post by fedex1993 on 2008-01-22
> **bodhi.zazen said:**
> like this ?

[img]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_xterm.png[/img]

You need to add color information to .bashrc :



Then you can :

play :



and on ...

yes thanks bodhi zazen

---

