---
title: "opening .run files"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Zopiac on 2008-04-18
ok im getting angry....im a whiz at windows, but i have no idea where to start for the linux extensions!:confused: i have several games, unreal tournament (ut-install-436) and americas army, both in .run formats, and they try to open in gedit, with errors:

Could not open the file /home/zopiac/Desktop/ut-install-436.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Im running 7.1 64bit currently...

any help welcome, thanks in advance!!!:)

---

### Post by Bachstelze on 2008-04-18
In a terminal :

```
sudo sh /home/zopiac/Desktop/ut-install-436.run
```

---

### Post by y-lee on 2008-04-18
> ok im getting angry....im a whiz at windows

First of all [linux is not windows]("http://linux.oneandoneis2.org/LNW.htm") things are a bit different. SO there really is no reason to be angry it is simply a learning experience if you wish to learn to use Ubuntu.

Now for your question I think the below should work:

make sure you are in the directory containing the files then

```

chmod 755 filename.run
./filename.run

```

---

### Post by Shazaam on 2008-04-18
Do you have build-essential installed? It has multiple tools that you need. You can install it with Synaptic (System>Administration>Synaptic Package Manager).

---

### Post by Bachstelze on 2008-04-18
> **Shazaam said:**
> Do you have build-essential installed? It has multiple tools that you need.

No, it doesn't.

---

### Post by Can+~ on 2008-04-18
> **Shazaam said:**
> Do you have build-essential installed? It has multiple tools that you need. You can install it with Synaptic (System>Administration>Synaptic Package Manager).

[Build-essential](http://packages.ubuntu.com/feisty/devel/build-essential) contains elements for developers. C, C++ compilers, dpkg-dev, make and other things.

---

### Post by Bachstelze on 2008-04-18
> **Can+~ said:**
> [Build-essential](http://packages.ubuntu.com/feisty/devel/build-essential) contains elements for developers. C, C++ compilers, dpkg-dev, make and other things.

Exactly. Ant the OP doesn't need any of that.

---

### Post by Shazaam on 2008-04-18
> **HymnToLife said:**
> No, it doesn't.

*hangs head in shame*
You are correct. I read the description in Synaptic and I stand corrected.:oops:

---

### Post by dynamethod on 2008-04-18
chmod u+x ut-install-436.run

then

./ut-install-436.run

---

### Post by Zopiac on 2008-04-19
ok, i did this in a terminal: 

sudo sh /home/zopiac/Desktop/ut-install-436.run

and came up with this:

[sudo] password for zopiac:

what? i cant type anything in...and if i press enter, it wait a few seconds, then says:

Sorry, try again.
[sudo] password for zopiac:

---

### Post by PmDematagoda on 2008-04-19
> **Zopiac said:**
> ok, i did this in a terminal: 

sudo sh /home/zopiac/Desktop/ut-install-436.run

and came up with this:

[sudo] password for zopiac:

what? i cant type anything in...and if i press enter, it wait a few seconds, then says:

Sorry, try again.
[sudo] password for zopiac:

The terminal does not show the characters you type in, just type the password(your password) as normal and then press enter.

---

### Post by Zopiac on 2008-04-19
ok, understandable, but then all i get is this:

sh: Can't open /home/zopiac/Desktop/ut-install-436.run

---

### Post by Can+~ on 2008-04-19
```
gksudo chmod u+x /home/zopiac/Desktop/ut-install-436.run  && sh /home/zopiac/Desktop/ut-install-436.run
```

That will do both things, plus a graphical interface for the password.

---

### Post by PmDematagoda on 2008-04-19
> **Zopiac said:**
> ok, understandable, but then all i get is this:

sh: Can't open /home/zopiac/Desktop/ut-install-436.run

Did you try the commands provided by dynamethod?

---

### Post by Zopiac on 2008-04-19
> **PmDematagoda said:**
> Did you try the commands provided by dynamethod?

> **dynamethod said:**
> chmod u+x ut-install-436.run

then

./ut-install-436.run


i didnt get it

---

### Post by Can+~ on 2008-04-19
> **Zopiac said:**
> i didnt get it

I posted a quicker command above, basically it runs both in the same sentence (&& operator):

> gksudo chmod u+x /home/zopiac/Desktop/ut-install-436.run  && sh /home/zopiac/Desktop/ut-install-436.run

Basically, why are you doing this?

(gk)sudo - prompts for root power, meaning that you have access to all files and permitions.
chmod - linux uses a permission system, each user has rights to Read (R), Write (W) and Execute (X). Files you download come with the execution disabled for your protection, you must enable it using this command, or via the graphical interface (right click, properties, permissions, allow execution)
sh - execute a Bash file, this case.

---

### Post by Zopiac on 2008-04-19
...?

---

### Post by Bachstelze on 2008-04-19
This should do, then.

```
cd /home/zopiac/Desktop
chmod +x ut-install-436.run
sudo ./ut-install-436.run
```

---

### Post by Vadi on 2008-04-19
... and that's why a graphical installer or a .deb is needed. Poor guy, I feel for you :(

---

### Post by Zopiac on 2008-04-19
zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
zopiac@zopiac:~/Desktop$ sudo ./ut-install-436.run
sudo: ./ut-install-436.run: command not found
zopiac@zopiac:~/Desktop$ 


????im totally lost, just blindly putting in variables from you guys now :/

---

### Post by PmDematagoda on 2008-04-19
> **Vadi said:**
> ... and that's why a graphical installer or a .deb is needed. Poor guy, I feel for you :(

Atleast he isn't compiling the program:).

---

### Post by Vadi on 2008-04-19
> **Zopiac said:**
> zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
chmod: cannot access `ut-install-436.run': **No such file or directory**
zopiac@zopiac:~/Desktop$ sudo ./ut-install-436.run
sudo: ./ut-install-436.run: command not found
zopiac@zopiac:~/Desktop$ 


????im totally lost, just blindly putting in variables from you guys now :/

Are you sure a file named "ut-install-436.run" is on your desktop?

---

### Post by ad_267 on 2008-04-19
Are you sure the file is on your desktop and is called ut-install-436.run? Also commands are case sensitive.

Can you post the output of:
```
cd ~/Desktop
ls
```

---

### Post by PmDematagoda on 2008-04-19
> **Zopiac said:**
> zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
zopiac@zopiac:~/Desktop$ sudo ./ut-install-436.run
sudo: ./ut-install-436.run: command not found
zopiac@zopiac:~/Desktop$ 


????im totally lost, just blindly putting in variables from you guys now :/

Post the output of:-
```
ls ~/Desktop
```

---

### Post by Can+~ on 2008-04-19
> **Zopiac said:**
> zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
zopiac@zopiac:~/Desktop$ sudo ./ut-install-436.run
sudo: ./ut-install-436.run: command not found
zopiac@zopiac:~/Desktop$ 


????im totally lost, just blindly putting in variables from you guys now :/

"No such file or directory" The file is not there?

some basic terminal usage:

cd *foldername* = enter a folder
ls = List content inside a folder.

If you click the up arrow, it will put the commands previously used.

---

### Post by Zopiac on 2008-04-19
> **Vadi said:**
> Are you sure a file named "ut-install-436.run" is on your desktop?

holy crud! i must have moved it!!!!!!!

hold on...

---

### Post by Zopiac on 2008-04-19
zopiac@zopiac:~$ chmod +x ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
zopiac@zopiac:~$ cd /home/zopiac/Desktop
zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
zopiac@zopiac:~/Desktop$ sudo ./ut-install-436.run
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Unreal Tournament version 436 Linux installtrap: 154: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap
zopiac@zopiac:~/Desktop$

---

### Post by Vadi on 2008-04-19
Now, that's a broken installer, nothing we can do there afaik.

Try using this one: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) it's nice and graphical too. Just right-click, select properties, permissions, and enable 'allow execution as program' after you downloaded it. Then just double-click and enjoy.

---

### Post by Can+~ on 2008-04-19
I found this HOWTO:

[http://ubuntuforums.org/showthread.php?t=153181](http://ubuntuforums.org/showthread.php?t=153181)

---

### Post by Bachstelze on 2008-04-19
Do this instead :

```
sudo bash ./ut-install-436.run
```

---

### Post by Vadi on 2008-04-19
(liflg installer is still easier)

---

### Post by Zopiac on 2008-04-19
huzzah! its workin on downloading, of course, but i have little doubt it wont work......just a hunch.

but though that doesnt answer my questions about .run files, it solved one problem. further help is appreciated, though not required.

---

### Post by Zopiac on 2008-04-19
> **HymnToLife said:**
> Do this instead :

```
sudo bash ./ut-install-436.run
```

zopiac@zopiac:~/Desktop$ cd /home/zopiac/Desktop
zopiac@zopiac:~/Desktop$ chmod +x ut-install-436.run
zopiac@zopiac:~/Desktop$ sudo bash ./ut-install-436.run
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
tail: Warning: "+number" syntax is deprecated, please use "-n +number"
.......................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
The program returned an error code (1)
zopiac@zopiac:~/Desktop$

---

### Post by Vadi on 2008-04-19
Generally, when a .run or a .bin or a file with no extension doesn't open when you double-click, first thing you do is check if it's set to be executable. Right-click, properties, permissions, and enable the checkbox.

If that doesn't do it (willl in 98% of the cases though), then there is some other problem - run the program in the terminal to find out why.

---

### Post by Bachstelze on 2008-04-19
Well, with a RUN file, you're supposed to do just that : run it. In Linux, running an executable is done by just typing it's path at the command line but before, you need to make the file executable, thus the usual steps :

```
cd /path/to/where/my/file/is
chmod +x myfile.run
./myfile.run
```

*EDIT : and that file you have seems to be quite old and broken. You'll have to find a newer one*

---

### Post by Zopiac on 2008-04-19
> **Vadi said:**
> Now, that's a broken installer, nothing we can do there afaik.

Try using this one: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) it's nice and graphical too. Just right-click, select properties, permissions, and enable 'allow execution as program' after you downloaded it. Then just double-click and enjoy.

Could not open the file /home/zopiac/unreal.tour…36-multilanguage.goty.run.
Could not open the file /home/zopiac/unreal.tour…36-multilanguage.goty.run using the Unicode (UTF-8) character coding.

---

### Post by Zopiac on 2008-04-19
> **HymnToLife said:**
> Well, with a RUN file, you're supposed to do just that : run it. In Linux, running an executable is done by just typing it's path at the command line but before, you need to make the file executable, thus the usual steps :

```
cd /path/to/where/my/file/is
chmod +x myfile.run
./myfile.run
```

*EDIT : and that file you have seems to be quite old and broken. You'll have to find a newer one*

thx, ill try to use this on the americasarmy one now :P wish me luck

---

### Post by Vadi on 2008-04-19
I don't know what the goty one is for, I was looking at the normal one

---

### Post by Can+~ on 2008-04-19
```
sudo ./ut-install-436 --keep
```

I Insist on the [HOWTO](http://ubuntuforums.org/showthread.php?t=153181), found another [Howto for AA](http://ubuntuforums.org/showthread.php?t=101929).

> **Vadi said:**
> I don't know what the goty one is for, I was looking at the normal one

GOTY is the Game Of The Year, the only UT that was awarded with it was the UT99. And damn it was good for that time, still remember CTF-Face = headshot fun.

---

### Post by Zopiac on 2008-04-19
> **Vadi said:**
> I don't know what the goty one is for, I was looking at the normal one

goty=game of the year (edition), if thats what ur looking for

---

### Post by Zopiac on 2008-04-19
> **Can+~ said:**
> ```
sudo ./ut-install-436 --keep
```

I Insist on the [HOWTO](http://ubuntuforums.org/showthread.php?t=153181)



GOTY is the Game Of The Year, the only UT that was awarded with it was the UT99. And damn it was good for that time, still remember CTF-Face = headshot fun.

very very very very much headshot fun. :P (tempted to run windows and play :)  )

---

### Post by Zopiac on 2008-04-19
so far i have:

zopiac@zopiac:~$ cd /home/zopiac/Desktop
zopiac@zopiac:~/Desktop$ chmod +x armyops250linux.run
zopiac@zopiac:~/Desktop$ ./armyops250linux.run
Verifying archive integrity... All good.
Uncompressing America's Army for GNU/Linux 2.5.0....Signal caught, cleaning up
zopiac@zopiac:~/Desktop$ 



looking good, i think :)


wait, what now? :confused:

---

### Post by ad_267 on 2008-04-19
If you go to Applications -> Games can you see it in the list?

---

### Post by Can+~ on 2008-04-19
> **Zopiac said:**
> so far i have:

zopiac@zopiac:~$ cd /home/zopiac/Desktop
zopiac@zopiac:~/Desktop$ chmod +x armyops250linux.run
zopiac@zopiac:~/Desktop$ ./armyops250linux.run
Verifying archive integrity... All good.
Uncompressing America's Army for GNU/Linux 2.5.0....Signal caught, cleaning up
zopiac@zopiac:~/Desktop$ 



looking good, i think :)


wait, what now? :confused:

> **sudo** ./armyops250linux.run

It will probably need root power to install it's goodies.


I hope the lack of response means that it's working.

---

### Post by Zopiac on 2008-04-19
> **Can+~ said:**
> It will probably need root power to install it's goodies.


I hope the lack of response means that it's working.

lol i think so...it shows a graphical interface and in prompting me for something. aside from that, i was also getting more skins :P

edit:it says its installing the base install, but keeps going from 0 to 100 to 0 to 100 again and again...i hope that means its installing differant files... :/

---

### Post by Can+~ on 2008-04-19
> Ingnore the warning,
hit exit at the license agreement,
say yes to the license agreement,
say ok at the directory scree,
say no to the symbloic links,
say yes to base install,
say yes to startup entries.

(took it from [here]("http://ubuntuforums.org/showthread.php?t=101929"))

---

### Post by Zopiac on 2008-04-19
> **Can+~ said:**
> (took it from [here]("http://ubuntuforums.org/showthread.php?t=101929"))

just checked; installation complete anyways

---

### Post by 1/0 on 2008-05-11
> **Zopiac said:**
> edit:it says its installing the base install, but keeps going from 0 to 100 to 0 to 100 again and again...i hope that means its installing differant files... :/

Same same for me. If I stop the installation, by pressing "ctrl" + "c", it deletes all the installed files and folders...

---

