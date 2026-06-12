---
title: "Uninstalling a broken package"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by The Minder on 2006-05-22
Greetings... btw, sooo noob it isn't funny however I once did some C programming when Jesus was a boy.

Anyway, just installed Ubuntu (after trying unsuccessfully with Debian) and must say I'm pretty impressed.   However, for newbies Ubuntu doesn't offer a "fix what I just did" option... pipe dream huh.   My prob is I tried to install a package for a Brother MFC8500 laser all in one and half way through the install (apt-get install yadda yadda) I got some errors.   "No probs" thinks I... I'll just forget about the damn printer.   And there's the catch... now, when I go into synaptic I get this message:

[I]E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/I]

So I blow past the error message and continue with synaptic and low and behold it refuses to list any packages... nada, just empty dialog box.  It appears I can't go forward (with the printer installation; not that I really want to anymore) and I can't back out the partial installation to get synaptic back to being responsive.

Naturally I'm looking for a one line fix to the prob (dreaming) but will settle for anything except a full reinstall of Ubuntu as I have just spent the past 2 weeks learning and setting this thing up to be usable on a network.

Suggestions greatly appreciated.

Wayne

---

### Post by S{yndrom}e on 2006-05-22
try this??

sudo dpkg --configure -a

---

### Post by S{yndrom}e on 2006-05-22
i also think you can reinstall synaptic if it gets to that instead of reinstalling ubuntu

---

### Post by The Minder on 2006-05-22
Thank for the quick reponse S{yndrom}e

I tried "sudo dpkg --configure -a" and got:

dpkg: status database area is locked by another process

Oh yeah, the install proc for the printer was dpkg.

---

### Post by christhemonkey on 2006-05-22
You need to make sure you close synaptic.

Did you install the file from outside the repositories, i mean like from a terminal typing:
```
sudo dpkg -i whatever.deb
```
?

---

### Post by S{yndrom}e on 2006-05-22
type ps -e in the terminal

look for any synaptic/download process

kill the processes with 

kill -9 *numberofprocess*

then run sudo dpkg --configure -a

---

### Post by The Minder on 2006-05-22
[QUOTE=christhemonkey]You need to make sure you close synaptic.

Did you install the file from outside the repositories, i mean like from a terminal typing:
```
sudo dpkg -i whatever.deb
```
?[/QUOTE]

Good one chris... I did have synaptic running when I tried sudo dpkg --configure -a... closed synaptic and the command executed without errors... however, when I opened synaptic again I get the same probs as before.

Second, yes, the printer install was done with sudo dpkg -i yadda yadda

---

### Post by S{yndrom}e on 2006-05-22
do 

sudo dpkg -r *debfilewithoutextension*

---

### Post by christhemonkey on 2006-05-22
Then you need (i think) to do a;
```
sudo dpkg -r Nameofpackageyouinstalled 
```

---

### Post by The Minder on 2006-05-22
[QUOTE=S{yndrom}e]do 

sudo dpkg -r *debfilewithoutextension*[/QUOTE]

Ok... tried that and got:
"dpkg - warning: ignoring request to remove mfc8500lpr-1.1.2-1.i386 which isn't installed."

---

### Post by christhemonkey on 2006-05-22
Try reinstalling it then.
```
sudo dpkg -i /wherever/whatever.deb
```


After that, try removing it again!

---

### Post by S{yndrom}e on 2006-05-22
any make sure any sudo apt-get/aptitude's arn't running and so is synaptic

---

### Post by The Minder on 2006-05-22
[QUOTE=christhemonkey]Try reinstalling it then.
```
sudo dpkg -i /wherever/whatever.deb
```


After that, try removing it again![/QUOTE]

Ok... went through the reinstall again and got the same errors as b4 (btw, this time I made sure there were no apt-gets synaptic running)... basicaaly the errors are along the lines of:
[I]Unpacking replacement mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory[/I]

Also tried to uninstall the package and got:
*dpkg - warning: ignoring request to remove mfc8500lpr-1.1.2-1.i386 which isn't installed.*

---

### Post by christhemonkey on 2006-05-22
Sounds like your package depends on lpr, although it may be a little difficult to install if your dpkg is broke.
```
sudo apt-get install lpr
```

Its in the universe repository so mke sure you have it enabled.

---

### Post by The Minder on 2006-05-22
[QUOTE=christhemonkey]Sounds like your package depends on lpr, although it may be a little difficult to install if your dpkg is broke.
```
sudo apt-get install lpr
```

Its in the universe repository so mke sure you have it enabled.[/QUOTE]

Not sure how to ensure the universe is enabled... only place I ever saw that was in synaptic which is now not behaving itself... anyway, executed the command and got:
michelle@ubuntu:~$ sudo apt-get install lpr
Reading package lists... Done
Building dependency tree... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.

Frustration levels rising.

---

### Post by S{yndrom}e on 2006-05-22
search in synaptic for that file

---

### Post by The Minder on 2006-05-23
[QUOTE=S{yndrom}e]search in synaptic for that file[/QUOTE]

No can do... synaptic doesn't show anything... it's as if it's empty even after telling it to it to do a reload which it seems to do just fine... but the display is empty.

---

### Post by The Minder on 2006-05-23
Problem fixed!!!!!!!!!

Searching on this forum I found several other instances of broken packages where users couldn't go forward (synaptic was not filling with data) and couldn't go backwards (package woulkd not uninstall) becasue 'something was missing'.   Then I came across a thread that indicated synaptic got it's information from a file called 'sources' and that that file indicated the status of a package.   It seams if the sources file indicated a package had a problem then synaptic would have a brain fart and refuse to play the game.

A user suggested doing the following:
[INDENT]cd /var/lib/dpkg/
sudo cp status status_bkup
sudo gedit status[/INDENT]
and then changing the status of the offending package from:
[INDENT]deinstall reinstreq half-installed[/INDENT]
to
[INDENT]deinstall hold half-installed[/INDENT]

I did this and when I ran synaptic, voila!!   All packages were listed including the broken mfc8500lpr (which was listed under the 'broken' group).   Damn brilliant!   Unfortunately, when I tried to use synaptic to remove the broken package I got the same old run-around again about not being able to find certain files... sheeeesh!

Then I thinks to meself, "meself!... if I can force a change in synaptic just by editing the sources file, why not just delete the mfc8500lpr entry from it alltogether and see what happens when I run synaptic?"   So I do that and praise be to the great pumkin, synaptic loads, displays all my packages and doesn't show or hang up on the mfc8500lpr issue.   Everything now appears normal.

Sure, I bet there are some mfc8500lpr files laying around looking for a home, but I don't give a ratz ***, they can damn well stay there.   My system is up, it's stable and I'm gonna find another printer (maybe).

To all who helped, my sincere thanks.   Through this forum I might just get to like Linux.

---

### Post by haddog on 2006-05-27
Thnx "The Minder". I followed your instructions and removed the reference of my offending package from status using gedit and all is good!

---

### Post by nolan- on 2006-05-29
Nice one Minder,
I had a tiny file broken that was hanging my adept. At least things are working again even if theres a couple of k crap in there :D

---

