---
title: "How To: Interesting Terminal"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-26
Since I'm a noob myself and don't know much about the inner workings of the terminal, I won't shed any light on that subject.  But, I would like to share some interesting and useful terminal code I've found.  This code was only tested on Ubuntu Feisty Fawn, but it will also work on most Mac OSX computers and should work on all Ubuntu releases.

I plan on updating when I find something new.

If you have any others, please post them!  :D

**_ Entertainment _**

Watch Star Wars 
```
 
telnet towel.blinkenlights.nl 

``` 

Chat with a bot 
```
 
telnet the-funk.net 7000 

``` 

Custom ascii text
```

banner

```

See how long your machine has been running
```

uptime

```

To see the arbitrary precision calculator (7^500 is interesting!  That's 7 to the 500th power)
```

bc

```

**Must enter below code to use the next few**
```

sudo apt-get install cowsay

```

See your fortune
```

fortune

```

Use cowsay (replace &#8220;message&#8221; with your own text in single quotes)
```

cowsay 'message'

```

Cowsay your Amarok lyrics
```

dcop amarok player lyrics | cowsay

```

**Must enter below code to use the next few**
```

sudo apt-get emacs21

```

--------------------------------------------------

To play 'snake'
```

emacs21

```
Once emacs21 opens, hit...
> 
Esc>>&#8221;X&#8221;
 
Type in...
```

snake

```

--------------------------------------------------

To play 'tetris'
```

emacs21

```
Once emacs21 opens, hit...
> 
Esc>>&#8221;X&#8221;
 
Type in...
```

tetris

```

--------------------------------------------------

**_ Useful _**

Show some computer stats
```

lspci

```

Access a dictionary through terminal (must have a working internet connection)
**Note**: Replace 'word' with whatever you'd like to search for (without quotes)
```

curl dict://dict.org/d:word

```

Check system temperature and battery charge 
```
 
acpi -t 

``` 

See a list of all running processes
```

ps aux

```

View the current time, date, and year
```

date

```

Show a simple calendar
```

cal

```

See what programs are running with the path names
```

ps -aux

```

See your current IP address
```

ifconfig -a

```

See what your system is doing at startup
```

dmesg

```

Show information about the computer users
```

finger -l

```

Show current Ubuntu version
```

cat /etc/issue

```

**_ System Recovery _**

Backup xorg.conf 
```
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 

``` 

Replace current xorg.conf with a previously made backup 
```
 
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 

``` 

Delete auto xorg.conf backups 
```
 
sudo rm /etc/X11/xorg.conf.2007* 

``` 

Use nano to edit xorg.conf (works in &#8220;terminal-only&#8221; mode) 
```
 
sudo nano /etc/X11/xorg.conf 

``` 

_**Keyboard Shortcuts**_

Terminal keyboard shortcut for paste
> 
Ctrl>>Shift>>Alt>>&#8221;V&#8221;

Or...
> 
Shift>>Insert


**_Advanced Users Only_**
Open up a file browser with all privileges
```

gksudo nautilus

```

Edit color options (advanced users only)
```

gedit .gtkrc-2.0

```

Give a .sh file executable priveledges
```

chmod +x <file name>

```

---

### Post by dev_person on 2007-04-26
Those are some useful tips. Thanks for posting them.

---

### Post by Iarwain ben-adar on 2007-04-26
Keyboard Shortcuts

Terminal keyboard shortcut for paste
> Shift-Insert

That's the one i always use :D


Iarwain

---

### Post by locke.dragon on 2007-04-26
thanks!  i'll put that one in!  :D

---

### Post by Iarwain ben-adar on 2007-04-26
**Entertainment**

Fortune
> fortune

Cowsay (need to apt-get it ;) )
> cowsay 'message'

Cowsay your amarok lyrics
> dcop amarok player lyrics | cowsay 

Banner
> banner

Hope to help ;)


Iarwain

---

### Post by nhandler on 2007-04-26
Those are pretty cool. Especially the Start Wars thing. I never new about these things.

---

### Post by ubuntu27 on 2007-04-26
This is not for the terminal perse but:

If you use Ubuntu (if you use GNOME)

Alt+F2 in your keyboard

and then type "free the fish"


2) SUPER COW POWERS:

```
aptitude -h 
```    [Comments: Read the last line]

```
apt-get moo 
```


```
aptitude moo
```

```
aptitude -v moo
```

```
aptitude -v -v moo
```

```
aptitude -v -v -v moo
```

```
aptitude -v -v -v -v moo
```

```
aptitude -v -v -v -v -v moo
```

```
apt-get moo
```


3) Debian's Top Secret List of planned Release Names:

```
zcat /usr/share/doc/linux-image-`uname -r`/changelog.Debian.gz | egrep -e "Release"
```

```
zgrep "The.*Release" /usr/share/doc/dpkg/changelog.Debian.gz
```

---

### Post by locke.dragon on 2007-04-26
bump

---

### Post by Seidojohn on 2007-04-26
I love it! Especially the ASCII Star Wars. Thanks locke.dragon!

---

### Post by Iarwain ben-adar on 2007-04-27
Locke,
it's ALT-F2 instead of ALT-F4 for the 'free the fish' thing ;)

Nice list, gets big!


Iarwain

---

### Post by jaywee on 2007-04-27
great list!!
esp. ctrl+insert.really convient and save time a lot!:lolflag: :lolflag:

---

### Post by locke.dragon on 2007-04-27
hey!  you're welcome guys!  :D

---

### Post by plainjane on 2007-04-27
Fish swimming is very cute.  Now, how do we turn it off???!!!???

---

### Post by foffen on 2007-04-27
> **plainjane said:**
> Fish swimming is very cute.  Now, how do we turn it off???!!!???

you got to catch it ;)

Or type  sudo killall gnome-panel in terminal to terminally hurt it ;)

---

### Post by lepz on 2007-04-27
>  The "Bully's Special Prize" Release.

Smashing, super, great :lolflag:

---

### Post by RedSquirrel on 2007-04-27
With regard to using nano, I believe it's safer to run it with *line wrapping* off, like this:

```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by mckryptyk on 2007-04-28
You should take a look at [This]("http://eeggs.com/"). It has lots of easter eggs :)

---

### Post by pixelbeat on 2007-05-23
A terminal screensaver
 ```
tr -cd '[[:print:]]' < /dev/urandom
```
Ok that sucks. A better one:
  ```
cmatrix
```

More command line tips here:
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

### Post by locke.dragon on 2007-05-29
bump...  again!!!  :p

---

### Post by esavato on 2007-06-06
To clear all of the past commands you have run in the terminal history type:
```
history -c
```

---

### Post by derred on 2007-06-08
Thanks for all the fish :)
and Star Wars 2

---

### Post by derred on 2007-06-08
I found another gnome easter egg:
Alt+F2: gegls from outer space
A galaxian like game with fish and cows?

---

### Post by SOULRiDER on 2007-09-24
I loved Star wars int he terminal, it was brilliant! :P

---

### Post by nebu on 2007-12-20
coll... the starrwars thing is damn cool

---

### Post by jan quark on 2007-12-20
thanks and want more

---

### Post by Josh1 on 2007-12-20
Awesome, I posted this on my blog.
[http://joshuataylor.info/useful-and-fun-things-to-do-with-the-ubuntu-terminal/](http://joshuataylor.info/useful-and-fun-things-to-do-with-the-ubuntu-terminal/)

---

### Post by Fabioamd87 on 2008-03-09
> **locke.dragon said:**
> Since I'm a noob myself and don't know much about 

**Must enter below code to use the next few**
```

sudo apt-get emacs21

```


you shold put install after apt-get :)

---

