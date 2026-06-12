---
title: "Xfce Xubuntu Mac"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by oneouncebrick on 2008-03-29
Hi. i run an old ibm thinkpad with 500kb of ram. and 13.7 gb of available memory. 

it has an intel processor, and used to have windows 2000

i recently installed xubuntu and think its great!, however. i was wondering ... if i could put a mac icon dock on my commputer, that wouldnt slow it down or mess with any settings... nothing else, no other themes... Just the doc :)

---

### Post by Triggerhapp on 2008-03-29
I have one like (I think?) Mac's dock, I use it alot.
```
sudo apt-get install avant-window-manager
```
then run it ```
avant-window-manager &
```
if you dont know how to set it up to run every time, hit me back :P

---

### Post by oneouncebrick on 2008-03-29
ok thanks =] the sudo apt codes are the kinds i like! =p now.. one mmore question after i install it wats the "run" codemean? does that mean i just type it into my terminal after i install it.. and what do u mean "set it up to run every time" lol =p thanks

---

### Post by Triggerhapp on 2008-03-29
The latter command you type into a terminal OR press alt-f2 and type it there without the following "&"

By "every time" I mean that the dock will not stay if you reset or log out... you put it into "Autostarted applications" to have it run at startup :)

Play with the settings in AWN before discarding it, if you want my advise, I find it should be suitable after a few options are chosen to your liking :)

---

### Post by oneouncebrick on 2008-03-29
also....i typed in the code sudo apt-get install avant-window-manager and it said command not found?

---

### Post by oneouncebrick on 2008-03-29
ooh okay sounds great exept for my previous post.. and im terribly sorry but could you tell me how to set it and put it into auto start applications? in lamens terms =p i dont mean to be a bother but im really new to ubuntu

---

### Post by Triggerhapp on 2008-03-29
OOPS! Its 2:40am, forgive me...
```
avant-window-navigator
```
That one infact, not manager

---

### Post by oneouncebrick on 2008-03-29
oh no problemo! =P so now all i need to know is how to d o the run code thing and put it in autostart applications in lamens terms .. if posible

---

### Post by Triggerhapp on 2008-03-29
> **oneouncebrick said:**
> i dont mean to be a bother
You're not. We were all new once.

I've forgotten a bit about how the XFCE normal settings menu works...so forgive some errors...

Menu->Settings->Autostarted Applications
Press "Add" button
Give it a name that you will know, best to just type "Avant" and then in the "Command" section type in ```
avant-window-navigator
``` and that should be that.

I would, ofcourse, advise making sure you want this before you set it up as automatic ;)

---

### Post by oneouncebrick on 2008-03-29
hmmmm navigator didnot work either? are their any build tools or settings i have to install/change first?

---

### Post by oneouncebrick on 2008-03-29
oh kk lol sory frgot to refresh, thanks ill try that and keep you posted
so, umm still comand not found though i googled this and got some people on xubuntu with the same problem installing awn

---

### Post by Triggerhapp on 2008-03-29
Erg, you might need to add a Repository source to your list... Let me find out

---

### Post by Sockerdrickan on 2008-03-29
> **oneouncebrick said:**
> Hi. i run an old ibm thinkpad with 500kb of ram. 

Holy crap

---

### Post by oneouncebrick on 2008-03-29
lol suprized its not exploding on me? mee too ! :)

---

### Post by Triggerhapp on 2008-03-29
Try this for me a moment...
Paste what it says if you can :P
```
sudo apt-get install avant-window-navigator*
```

---

### Post by oneouncebrick on 2008-03-29
u want me to put that in my terminal ? =[] lol or search it on google

---

### Post by Triggerhapp on 2008-03-29
Lol... I misclicked while pasting and didnt realise for a moment XD

---

### Post by Triggerhapp on 2008-03-29
On another note, Im really happy you just asked that...
Shows you have the right mindset for Linux, in my opinion :P

---

### Post by oneouncebrick on 2008-03-29
the asterix diddnt work either

---

### Post by Triggerhapp on 2008-03-29
Did it say no packages found? heres what I get, for example...
```
Note, selecting avant-window-navigator for regex ‘avant-window-navigator*’
Note, selecting avant-window-navigator-bzr for regex ‘avant-window-navigator*’
Note, selecting avant-window-navigator-svn for regex ‘avant-window-navigator*’
Some packages could not be installed.
```

---

### Post by Triggerhapp on 2008-03-29
[http://www.tectonic.co.za/wordpress/?p=1881](http://www.tectonic.co.za/wordpress/?p=1881)
> Step 1: Edit your apt sources list ( sudo gedit /etc/apt/sources.list ) and add the following two lines to the bottom of that file:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

If you’re using Feisty then change “gutsy” to “feisty in both lines.

Step 2: Update apt with sudo apt-get update

Step 3: Before you can install AWN you need to add the appropriate apt key. To do this execute the following three lines at a command line, one at a time:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc

Step 4: Finally, download AWN and the AWN applets:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr


There ya go, that one should set you up. As I said, play with the settings afterwards, its very configurable

---

### Post by oneouncebrick on 2008-03-29
nope, this is what i get when i type sudo apt-get install avant-window-navigator "command not found" it doesnt even start installing.. it tries to but then stops itself and i get that:

---

### Post by oneouncebrick on 2008-03-29
none of those comands were found i am on a gutsy and this confuses me O.o i typed: sudo gedit /etc/apt/sources.list

---

### Post by Triggerhapp on 2008-03-29
I'm on Gutsy too... are you getting "command not found" for every command?

---

### Post by oneouncebrick on 2008-03-29
i then took out the "g" on edit lol and got :Warning: unknown mime-type for "/etc/apt/sources.list" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

---

### Post by JoshuaRL on 2008-03-29
Technically the correct command is:
```

gksu gedit /etc/apt/sources.list

```

---

### Post by oneouncebrick on 2008-03-29
ok thanks that one took me right to another terminal type in command $... so i did that then copy and pasted the 2 lines he told me to and they both didnt work, is it because they were links?

---

### Post by Triggerhapp on 2008-03-29
Sudo is command line based, gksu is the same program with a GTK+ frontend. I dont see the need to load a seperate frontend to do the exact same one line of password that I can do on the terminal.

And yes, im the kind of person who would sometimes rather log into the terminal and then startx

---

### Post by Triggerhapp on 2008-03-29
the 2 lines starting with "deb"? They are data to tell the update/install program where it should look... What terminal are you using?

---

### Post by oneouncebrick on 2008-03-29
OH i am usin the terminal that ocmes with xubuntu 7.10 gutsy gibon, $terminal

---

### Post by oneouncebrick on 2008-03-29
okay.......

i typed his avant code it diddnt work
i tried to folow your instructions and c=kindof coulldnt O.o
what next =p ? O.o

---

### Post by Triggerhapp on 2008-03-29
> **JoshuaRL said:**
> ```

gksu gedit /etc/apt/sources.list

```
What happens when you type this in? What should happen is it runs a text editor program with a file filled with deb/deb-src lines....

---

### Post by oneouncebrick on 2008-03-29
this:it brings up the regular terminal command.. it virtually does nothin, just opens the next lineO.o

---

### Post by oneouncebrick on 2008-03-29
sodo u guys think its tim to not install AWN yet =D ? ='} ='{

---

### Post by Triggerhapp on 2008-03-29
ok I really am out of my depth here...
```
which gksu
which gedit
```
Paste the terminal output after each one of these

---

### Post by Triggerhapp on 2008-03-29
XD I have no idea whats wrong but it sounds interesting...

---

### Post by oneouncebrick on 2008-03-29
first one gksu: /usr/bin/gksu

second one: gedit:michael@Mike-laptop:~$ 

^--another terminal line

---

### Post by oneouncebrick on 2008-03-29
lool, okay. ill just give up lookin like maclol. i dont care if this is wat its gunna put me through! XD lol

Good night, lol! we all need sleep @_@ 
;)
mabey ill figur somthing out

---

### Post by Triggerhapp on 2008-03-29
Close all your terminals... Alt-f2 and type "xterm" then enter, then try this instead ```
sudo mousepad /etc/apt/sources.list
```

---

### Post by oneouncebrick on 2008-03-29
i have no idea what just happend! lol i did that it brought up a mini terminal i typed it in and it brought up a white box saying "warning you are using the root account you may harm your system.....?!!!!!

this looks illiegal lol jk

---

### Post by Triggerhapp on 2008-03-29
gksu means you move to "root" or administrator, to perform a command.
Here you are editing your sources list, which tells your installer program (apt-get in this case) what websites, cd's etc, it is allowed to install from.
You will be adding 2 more sources from tuxfamily.org which host Avant-window-navigator

---

### Post by Triggerhapp on 2008-03-29
> Step 1: Edit your apt sources list ( sudo gedit /etc/apt/sources.list ) and add the following two lines to the bottom of that file:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

If you&#8217;re using Feisty then change &#8220;gutsy&#8221; to &#8220;feisty in both lines.

Step 2: Update apt with sudo apt-get update

Step 3: Before you can install AWN you need to add the appropriate apt key. To do this execute the following three lines at a command line, one at a time:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc

Step 4: Finally, download AWN and the AWN applets:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Here we go, this, but using mousepad (like windows notepad) instead of gedit...
For future reference, always use mousepad where anyone else instructs you to use gedit. gedit is for gnome, generally

---

### Post by Zippo_from_hell on 2008-03-30
Hi i'm following this discussion since the beginning and i have the exact same problems. Don't know what is going on and i tried the last thing that Triggerhapp suggested  and i got 

W: GPG error: [http://download.tuxfamily.og](http://download.tuxfamily.og) gutsy release: the following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

I just tried everything lol nothing seems to work^^'

---

### Post by Triggerhapp on 2008-03-30
> **Zippo_from_hell said:**
> Hi i'm following this discussion since the beginning and i have the exact same problems. Don't know what is going on and i tried the last thing that Triggerhapp suggested  and i got 

W: GPG error: [http://download.tuxfamily.og](http://download.tuxfamily.og) gutsy release: the following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

I just tried everything lol nothing seems to work^^'

Did you do the...```
sudo apt-get update
```?
What did it say about adding the GPG key?
Try each command in a row and give me errors/warnings :)

---

### Post by Zippo_from_hell on 2008-03-31
ok first step done
Second step failed. It tells me the two comments go to a 404 not found site
Step tree failed miserably:
-first step -  404 not found
-second step - no such file or directory
-third step - no such file or direcory
T_T where do y failed? i did the update too

---

### Post by Triggerhapp on 2008-03-31
> Step 1: Edit your apt sources list ( sudo gedit /etc/apt/sources.list ) and add the following two lines to the bottom of that file:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy main
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy main


try this edited command, then follow the others... Sorry about this XD

---

### Post by Zippo_from_hell on 2008-03-31
he's telling me he failled to fetch the filles. Again 404 not found. I'm sorry to be such a noob. One more detail who could help: i'm runing eeexubuntu for my eeepc so maybee this version doesn't have the packages needed.

---

