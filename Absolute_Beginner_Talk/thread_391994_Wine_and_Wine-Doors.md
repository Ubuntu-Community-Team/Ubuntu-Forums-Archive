---
title: "Wine and Wine-Doors"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-03-23
mark@Lexington:~/src$ python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory

I installed Wine with A/X. It has since updated Wine. I then installed Wine-Doors and when invoked, it gave the above. Anybody know what to do next?

---

### Post by TheRingmaster on 2007-03-24
This doesn't make sense to me. Wine doesn't have anything to do with a python program. What are you trying to do with this file? Please give us more insight on your problem.

FYI: After you install wine make sure to do "winecfg" in a terminal. This will make a fake ":C/" directory. Also, Just try to do "python whereeveritis"

---

### Post by bodhi.zazen on 2007-03-24
You need to give the path to setup.py

It looks like setup.py is not in your current directory (src)

---

### Post by Mark_in_Hollywood on 2007-03-24
Sorry for the lack of "know-how" but I don't know where (what directory or directories) or how to add a path statement. However, I did find this:

mark@Lexington:~/src/wine-doors/wine-doors/trunk/src$ ls

application.py
installed.packlist.xml
utils.py
winedoors.py
cedega.svg
log.py
wine-doors.128.png
wine.py
const.py
packlist.py
winedoors.glade
wtparser.py
create-packs.sh
preferences.py
winedoors.gladep
crossover.svg
queue.py
winedoors-header.png
ctile.py
ui.py
wine-doors.png

---

### Post by TheRingmaster on 2007-03-24
Is there a question to this thread???

---

### Post by bodhi.zazen on 2007-03-26
LOL

Last time I looked you should have a directory : ~/src/wine-doors

You should then :

```
cd ~/src/wine-doors
sudo python setup.py install
```

---

### Post by Mark_in_Hollywood on 2007-03-27
Nope, Bodhi, same as before and following you by 'cut & paste' I rcv'd:

mark@Lexington:~$ cd ~/src/wine-doors
mark@Lexington:~/src/wine-doors$ sudo python setup.py install
Password:
python: can't open file 'setup.py': [Errno 2] No such file or directory
mark@Lexington:~/src/wine-doors$

What now, Zen Master?

---

### Post by bodhi.zazen on 2007-03-28
Bah, zen master indeed :lolflag:



Alrighty then ...

```

mkdir ~/src
cd ~/src
svn co http://www.wine-doors.org/svn wine-doors
cd ~/src/wine-doors/wine-doors/trunk
sudo python setup.py install
sudo chown user_name:user_name /home/user_name/.wine-doors
wine-doors
```

_Note_: user_name = you log in name.

At this pint you will get a lot of output to the terminal ending with an error message :

IGNORE IT !!

Close wine-doors Ctrl-c or close the terminal

Open a new terminal and enter :

```
wine-doors
```

Enjoy :)

---

### Post by Mark_in_Hollywood on 2007-03-31
mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo python setup.py install
Password:
. . . [much removed to conserve space & time[

webdings-1/pack.xml
  ** Base Repo
  ** Global Repo
Symlinking resources
Creating initial preferences
mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo chmod mark:mark /home/mark/.wine-doors
chmod: invalid mode: `mark:mark'
Try `chmod --help' for more information.

mark@Lexington:~/src/wine-doors/wine-doors/trunk$ ls
debian  dtd      LICENSE  README  setup.py
dist    INSTALL  pixmaps  repos   src

mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo chmod user_name:user_name /home/mark/.wine-doors
chmod: invalid mode: `user_name:user_name'
Try `chmod --help' for more information.

Oh! Zen Master, how I have failed you, I'm not worthy!!!

---

### Post by bodhi.zazen on 2007-03-31
> **Mark_in_Hollywood said:**
> mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo python setup.py install
Password:
. . . [much removed to conserve space & time[

webdings-1/pack.xml
  ** Base Repo
  ** Global Repo
Symlinking resources
Creating initial preferences
mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo chmod mark:mark /home/mark/.wine-doors
chmod: invalid mode: `mark:mark'
Try `chmod --help' for more information.

mark@Lexington:~/src/wine-doors/wine-doors/trunk$ ls
debian  dtd      LICENSE  README  setup.py
dist    INSTALL  pixmaps  repos   src

mark@Lexington:~/src/wine-doors/wine-doors/trunk$ sudo chmod user_name:user_name /home/mark/.wine-doors
chmod: invalid mode: `user_name:user_name'
Try `chmod --help' for more information.

Oh! Zen Master, how I have failed you, I'm not worthy!!!

LOL

My mistake actually :( Sorry (I will edit my previous post to avoid misleading others).

Open a terminal

```
sudo **chown** mark:mark .wine-doors
wine-doors
```

---

### Post by Mark_in_Hollywood on 2007-04-01
OooooK, but look what happened:

mark@Lexington:~/src$ sudo chown mark:mark .wine-doors
chown: cannot access `.wine-doors': No such file or directory
mark@Lexington:~/src$ sudo chown mark:mark wine-doors [I removed the . ]
mark@Lexington:~/src$ wine-doors
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in ?
    import ui
  File "/usr/share/wine-doors/src/ui.py", line 7, in ?
    from ctile import Tile
  File "/usr/share/wine-doors/src/ctile.py", line 1, in ?
    import cairo, rsvg, math
ImportError: No module named rsvg
mark@Lexington:~/src$

I can't find a "hidden" or .wine-doors anywhere in /home/mark [my first name]

---

### Post by zvacet on 2007-04-01
i know this will not solve wine-doors problem but will help you to configure wine.I give to you wine tools.Similar program with same porpose.

---

### Post by Mark_in_Hollywood on 2007-04-01
Thanks, but not for me. I tried it before and it didn't play nicely with everything else.

Bodhi Zazen-ski : Can you come out and play?

---

### Post by bodhi.zazen on 2007-04-01
LOL

You are in the wrong directory (looks like you are in ~/src)

Open a new terminal

cd to your home directory ```
cd
```

Now, to list your hidden files :```
ls -la
```

Do you see .wine-doors ? If so, who owns it ?

If it is owned by you, good to go

If it is owned by root : ```
sudo chown -R mark:mark .wine-doors
```

Then, again in a terminal,

wine-doors

---

### Post by david_kt on 2007-04-02
> **Mark_in_Hollywood said:**
> Thanks, but not for me. I tried it before and it didn't play nicely with everything else.

Bodhi Zazen-ski : Can you come out and play?

Mark in Hollywood,

I think we should wait until wine-door at least announce a pre-release. Now there is not even pre-release, so, I dont know what stage wine door is.

I suggest, instead of trying to run a program (wine-doors) that will help you run another program (windows program), why don't you tell us what windows program you wanted to run and you could not run it with wine? I think that is much better approach.

DK

---

### Post by Mark_in_Hollywood on 2007-04-02
> **bodhi.zazen said:**
> 

cd to your home directory ```
cd
```

Now, to list your hidden files :```
ls -la
```

drwxr-xr-x  4 mark mark     4096 2007-04-02 11:30 .wine


Do you see .wine-doors ? If so, who owns it ?

Looks like I do own it.

If it is owned by you, good to go

If it is owned by root : ```
sudo chown -R mark:mark .wine-doors
```

Then, again in a terminal,

wine-doors
 Returns:

mark@Lexington:~$ wine-doors
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in ?
    import ui
  File "/usr/share/wine-doors/src/ui.py", line 7, in ?
    from ctile import Tile
  File "/usr/share/wine-doors/src/ctile.py", line 1, in ?
    import cairo, rsvg, math
ImportError: No module named rsvg
mark@Lexington:~$

---

### Post by bodhi.zazen on 2007-04-02
Looks like you are out of luck as far as wine-doors ...

You can try running as root ```
sudo wine-doors
```

However, wine-doors may have set up wine ...

What program are you trying to run with wine ?

Try installing the program and then ... wine /path/to/program.exe

---

### Post by Mark_in_Hollywood on 2007-04-04
Bodhi.Zazen,

Dude, you've spent more than your fair share of time on me and this. I'll work it out elsewhere. Many Tux-Thanks!! You're the best.

---

### Post by TheRingmaster on 2007-04-04
what apps do you want to install with these programs. I am sure that there are some excellent native linux replacements for it.

---

### Post by Mark_in_Hollywood on 2007-04-04
. . . Since you asked:

My public library has a service from Rosetta Stone, the language company. I have to use Internet Explorer because the online service requires Shockwave. And there ain't no shockwave for linux in any flavor. But, thanks for asking.

---

