---
title: "Installing downloaded content/printer"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-07-11
Two questions :

1- When I donwload something like the .tar.gz file for Opera 9 online what do I do afterwards in order to install it (i assume the procedure works for every other downloaded package)?When doens't it show up in Synaptic?



2-I have a printer (hpdeskjet 940c) and altho it has been recognized and I can print things they print at a very very slow rate and also I can't edit things like if I want balck and white only or draft on OpenOffice's word processor...Why is that?

---

### Post by Kilz on 2006-07-11
> **Endow said:**
> Two questions :

1- When I donwload something like the .tar.gz file for Opera 9 online what do I do afterwards in order to install it (i assume the procedure works for every other downloaded package)?When doens't it show up in Synaptic?
[Look here for info]("http://www.monkeyblog.org/ubuntu/installing/") on how to install things.



> 2-I have a printer (hpdeskjet 940c) and altho it has been recognized and I can print things they print at a very very slow rate and also I can't edit things like if I want balck and white only or draft on OpenOffice's word processor...Why is that?
Click System > Adminstration > Printers, Find your printer, right click on it, choose Properties, Click on Advanced tab. You can select some things on how jobs are printed out there.

---

### Post by Endow on 2006-07-11
1- I don't understand something...it says I should type "sudo make install" 
but what is the argument here?Isn't it the path of my extracted folder?


2- I found the properties and all but I still get very slow printing rate...as in VERY slow...

---

### Post by Kilz on 2006-07-11
> **Endow said:**
> 1- I don't understand something...it says I should type "sudo make install" 
but what is the argument here?Isn't it the path of my extracted folder?
You may find compiling a program from source is difficult. You may want to read the instructions for using Synaptic on the page I linked to last post. The package manager has a lot of programs already compiled.
If you find that you must compile a program you may want to spend some time reading the instructions [Here]("http://www.monkeyblog.org/ubuntu/installing/#source") and [here]("http://www.monkeyblog.org/ubuntu/installing/#navigating_the_terminal") as compiling a program is a little more advanced.

---

### Post by Endow on 2006-07-11
Why don't they just code an installer?It would make things alot easier...


*goes Muttley*

---

### Post by Kilz on 2006-07-11
> **Endow said:**
> Why don't they just code an installer?It would make things alot easier...


*goes Muttley*
Because the source code method makes it avaiable to a lot more systems. Since it can be compiled it will work on a variety of distro's. But compiling isnt easy for beginers sometimes(sometimes its not even easy for experenced people).
If the package is a common one most of the time someone has packaged it up already and its in the repositories. You use Synaptic to search through the repositories and install those packages.

---

### Post by Endow on 2006-07-11
Opera is pretty popular...atlho 9.0 is recent...anyways thanks for the help.Tomorrow I'll try the "hard way" :p

---

### Post by slimdog360 on 2006-07-11
You can download the .deb file which is the way Id recommend if you want some practice at doing thigs. But if you must there is an commercial thingy that you can add into synaptic. It has opera in it, thus it will also automatically update opera for you.
If you want to do it this way you can follow this.

open a terminal
```
sudo cp /etc/apt/sources.lst /etc/apt/sources.lst_backup
sudo gedit /etc/apt/sources.lst
```

then add this into the file that opens up at the **bottom**(minus the quotes).

"deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main"
save the file then type into the terminal
```
sudo apt-get update
```
once that is done opera and a few other things should be in synaptic.

But its probably best if you get some more experience installing from source and other things. You can install it from source or as a deb file then use the instructions that I gave you and opera can update its self.

---

### Post by Endow on 2006-07-12
Hmmm.Ok, thanks.Anyone got some thoughts on why my printer is butt slow?

---

### Post by slimdog360 on 2006-07-12
can you tell us what driver you used to install it.
was it any of these do you know
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_940C]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_940C")

---

### Post by Endow on 2006-07-12
I dind't download anything and I used the "recommended" (that's what Ubuntu itslef says on "driver") hpijs.

---

### Post by slimdog360 on 2006-07-12
Well I can tell you thats its going to be a driver problem.My suggestion is to use the drivers on that page I just gave you [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_940C")
The first one is probably the same as in Dapper, but it might be a little different so still give it a try. 
It took me a lot of different drivers to get mine working and mine isnt even officially supported by anything in linux. There is like 6 different drivers on that page, one is bound to work for you. If you need any help installing them just message back.

---

