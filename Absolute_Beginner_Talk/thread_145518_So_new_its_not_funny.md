---
title: "So new its not funny"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by bronco59 on 2006-03-16
Hey there im sure this is a dumb question but i am having trouble getting anysort of graphic interface to work  

im stuck at   root@bronco59:#    


can do some things with linux but want a graphical desktop instead of text   can you help me please

---

### Post by Brunellus on 2006-03-16
you're going to have to tell us what you did to get to that point.  ubuntu doesn't enable the root account by default (it uses sudo), so you must have been changing stuff.

---

### Post by bronco59 on 2006-03-16
never got it up and running i guess     haven changed anything just basicaly been able to check man man and i installed automatix  and updated it    


this is the first day i ever used ubuntu on my computer


i was told this is the easiest and most stable version so i installed it   obviously im online with it cause i downloaded automatix   but i did it in text and i want to get a graphic interface going

---

### Post by taurus on 2006-03-16
How did you install Ubuntu?  At the prompt, did you just hit the return key to install it or did you type in "server" at the prompt?

---

### Post by mlind on 2006-03-16
that looks like runlevel 1

---

### Post by bronco59 on 2006-03-16
installed it from cd      now i have duel boot  setup

---

### Post by Teroedni on 2006-03-16
What is your videocard

Ati?


Brand and modelnumber please:)

---

### Post by bronco59 on 2006-03-16
ati all in wonder 9600

---

### Post by Teroedni on 2006-03-16
Okey


Ati often have problems working properly because of bad drivers.

I will need to see your xorg.conf file.  Since you have to manually type it , i will not ask for the whole;)


[COLOR="Red"]Okay here are the Instructions:[/COLOR]

in your console(white text and black background) type

```
sudo nano /etc/X11/xorg.conf
```

You get a text file open . scroll down until you find this section

[COLOR="Red"]Demo!!![/COLOR]
Section "Device"
	Identifier	"?"
	Driver		"?"
	BusID		"?"
EndSection
[COLOR="Red"]Demo[/COLOR]

IN your text file whats stand in there?

[COLOR="DarkOrange"]***[I]Edit:I had written the command wrong.Sorry for that:/*[/I]**[/COLOR]

---

### Post by mlind on 2006-03-16
I honestly think he's somehow screwed the installation and ended somewhere
else than runlevel 5, otherwise terminal wouldn't give root permissions.

X isn't probably even installed?

---

### Post by bronco59 on 2006-03-16
ok i got the GNU nano  1. 3. 8     going but there is nothing in this 


at the botton is has like  get help write out read file previous page cut text cur pos exit justify where is  next page uncut txt to spell


thats it    

wonder why this is in root instead of sudo

---

### Post by Teroedni on 2006-03-16
Ohh i dident get your run root. Stupid me sorry:/

Try without sudo please just

```
 nano /etc/X11/xorg.conf

```


and the X11 part need to be with an Big X, Its case sensitive.

---

### Post by bronco59 on 2006-03-16
yeah same thing  asthe last time   



by the way thanks for the help its really appritiated   





its blank

---

### Post by engla on 2006-03-16
It looks like you don't have a complete install. I'd try this:

apt-get update
apt-get install ubuntu-desktop
apt-get dist-upgrade

That should install all packages that come with a complete ubuntu install; it should work both off- and online

---

### Post by cjazz on 2006-03-16
[QUOTE=mlind]I honestly think he's somehow screwed the installation and ended somewhere
else than runlevel 5, otherwise terminal wouldn't give root permissions.[/QUOTE]

I'm wondering if he selected expert install.

---

### Post by bronco59 on 2006-03-16
sorry aboit waiting so long  but i totally reinstalled it and am trying it again

---

