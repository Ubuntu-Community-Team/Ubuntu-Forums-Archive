---
title: "Simple shell script, cant seem to figure"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-23
I have an executable in a directory:

/builds/FlightGear/source/src/Main/fgfs

I want to launch the executable 'fgfs' in a terminal with some command line options:

fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,183.91.37.29,5000 --callsign=GWIZZ

If I navigate in a terminal to the above directory, then manually execute that command line, it runs fine.

But I can't get it to launch from a shell script file.. what am I doing wrong?

Permissions seem ok, I think;

---

### Post by raja on 2007-06-23
Can you paste your script here. You are giving the full path in the script, I hope.

---

### Post by taurus on 2007-06-23
Can you post that script you want to run it?

---

### Post by ecs_pf5 on 2007-06-23
Don't laugh :lol: just call me Windows-boy:

I called my script 'fgfsgo.sh' and gave it executable permission

```

cd /builds/FlightGear/source/src/Main
fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ

```

I tried making a launcher too on the desktop, but that didn't work either. I used the command:

```

/builds/FlightGear/source/src/Main/fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ

```

in it.

---

### Post by yabbadabbadont on 2007-06-23
Edit: Never mind, posted too late.

---

### Post by scxtt on 2007-06-23
looks like you're missing what shell to use:

add:
#!/bin/bash

as the 1st line and try executing it again ...

---

### Post by ecs_pf5 on 2007-06-23
Weird, no joy.. it does flash up a terminal but it's gone again in the blink of an eye, and the fgfs program (FlightGear flightsim) doesn't launch.

But if I type the same commands into a manually-opened terminal, happy days..

---

### Post by scxtt on 2007-06-23
post the entire script

---

### Post by po0f on 2007-06-23
ecs_pf5,

Try this modified version of your script:

```
#!/bin/bash

cd /builds/FlightGear/source/src/Main
./fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ
```

---

### Post by ecs_pf5 on 2007-06-23
heh.. scxtt... that *is* the entire script ;)

I'm just trying to launch the game with it's command line options loaded, from some kind of one-click scenario. Perhaps I shouldn't be trying to use a shell script at all?

po0f.. thanks, gave it a shot, but no joy

---

### Post by ryanVickers on 2007-06-23
Yeah, if you know the options, and the terminal works, I wouldn't bother with a script.  The usefulness reminds me of not much higher than a script I made that you enter a path and it does 'cat' on the file :p

---

### Post by po0f on 2007-06-23
ecs_pf5,

Please post the output of:

```
$ ls -l /builds/FlightGear/source/src/Main/fgfs
```

---

### Post by ecs_pf5 on 2007-06-23
```

user@ubuntu:~$ $ ls -l /builds/FlightGear/source/src/Main/fgfs
bash: $: command not found
user@ubuntu:~$

```:shock:

erm.. don't understand! it's there allright.. and it runs manually.. odd

oh hanggggo on I'm being dim, back in a sec

```

user@ubuntu:~$ ls -l /builds/FlightGear/source/src/Main/fgfs
-rwxr-xr-x 1 user user 58571636 2007-06-22 19:39 /builds/FlightGear/source/src/Main/fgfs
user@ubuntu:~$ 

```

---

### Post by ryanVickers on 2007-06-23
Yeah, try removing the $ :lolflag:!

---

### Post by ecs_pf5 on 2007-06-23
^ soz :p

---

### Post by po0f on 2007-06-23
ecs_pf5,

Ok, this is really odd.  Try using the script that sort of worked (flashed a terminal on the screen) and try changing the command to:

```
./fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ >~/fgfs.log
```

then post the contents of ~/fgfs.log (if any).  Maybe there is an error somewhere you're not catching.

---

### Post by jfinkels on 2007-06-23
> **po0f said:**
> ecs_pf5,

Ok, this is really odd.  Try using the script that sort of worked (flashed a terminal on the screen) and try changing the command to:

```
./fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ >~/fgfs.log
```

then post the contents of ~/fgfs.log (if any).  Maybe there is an error somewhere you're not catching.

Yes.

Or just try launching the script from the terminal and see if there's any output (will accomplish the same thing as above).

---

### Post by yabbadabbadont on 2007-06-23
I wonder if it is complaining about not being able to attach to the X display?  You know how that can happen when you use sudo to try to launch a graphical app instead of gksudo.  Maybe something like that is going on.

---

### Post by ecs_pf5 on 2007-06-23
With the logfile method, I kept getting an empty, 0-byte log.

From the terminal (script was on the Desktop and called 'gofg.sh'):

```

user@ubuntu:~$ cd Desktop
user@ubuntu:~/Desktop$ gofg.sh
bash: gofg.sh: command not found
user@ubuntu:~/Desktop$ ls
AptNav200701XP810.zip  gofg.sh                    mozilla-thunderbird.desktop
Computer.desktop       gofg.sh~                   new file
dmesg.txt              g.sh~                      new file~
fg.desktop             keyrepeat_badmouse_fixes   Root Filemanager.desktop
firefox.desktop        keyrepeat_badmouse_fixes~  sound
gofg~                  Link to log                sound~
user@ubuntu:~/Desktop$ gofg.sh
bash: gofg.sh: command not found
user@ubuntu:~/Desktop$ sudo su
Password:
root@ubuntu:/home/user/Desktop# gofg.sh
bash: gofg.sh: command not found
root@ubuntu:/home/user/Desktop# ls -l gofg.sh
-rwxrwxrwx 1 user user 90 2007-06-24 00:36 gofg.sh
root@ubuntu:/home/user/Desktop# 

```

---

### Post by scxtt on 2007-06-23
> root@ubuntu:/home/user/Desktop# gofg.sh
bash: gofg.sh: command not found
to execute a script - if your CWD isn't in your path - do it like so:

./gofg.sh

---

### Post by bigboy_pdb on 2007-06-23
If you enter 'echo $PATH' within the terminal, you will see the directories that are being checked when you go to run an executable file. In windows, the current directory is automatically included as being one of the directories that is checked (although I don't think it is listed in the PATH variable). In Linux, the current directory is not checked. So if you are trying to run a program from the terminal and it is not in your path then you have to use './program_name' where program_name is the name of the program. Without the './' at the beginning Linux doesn't know to check in the current directory.

In order to make a script executable you have to change the permissions so that it is executable. I can see that you've done this but for anyone else who does not know how to do this you can use 'chmod 755 script_name'. If it is a bash script, you must have '#!/bin/bash' as the first line (without the single quotes). Once you do this you can run the script from the command line using './script_name'. Another way that you can run the script (if you don't have '#!/bin/bash' as the first line) is using 'sh script_name'.

ecs_pf5, your problem is that you're trying to execute your script, but Linux doesn't know to check in the current directory so it's saying that it's not found. To execute it use './gofg.sh' but before this will work you must have '#!/bin/bash' as the first line of your script. You can also use 'sh gofg.sh' to execute the script (but you must be in the directory that gofg.sh is located in to use this method).

---

### Post by ecs_pf5 on 2007-06-23
```

user@ubuntu:~$ cd Desktop
user@ubuntu:~/Desktop$ ./gofg.sh
Warning: detected OpenGL error 'invalid enumerant' after RenderBin::draw(,)
freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.
user@ubuntu:~/Desktop$ 

```Don't worry about the OpenGL / freeglut warnings and errors - they're another issue.

Won't run from a double click on gofg.sh or a launcher pointed at gofg.sh though.

If I try specifying ./gofg.sh in a launcher on the Desktop, it says 'no such file or directory'.

tried also 

./home/user/Desktop/gogf.sh
./home/user/Desktop/./gogf.sh
~/Desktop/gogf.sh
~/Desktop/./gogf.sh
sh /home/user/Desktop/gogf.sh
sh gogf.sh
sh ~/Desktop/gogf.sh
sh ./gogf.sh

in launchers.. no joy so far

Perhaps I should sit down for a day or two with a shell scripting manual.

---

### Post by bigboy_pdb on 2007-06-23
If all you're trying to do is run your program with certain command line options then perhaps you should try creating a launcher on your desktop. To be honest I haven't done this before because I use a terminal for most things but I should think that the following would work. If somebody notices that I'm wrong then please correct me.

Create a new Launcher on the desktop by right clicking and selecting 'Create Launcher...'. For Type select 'Application in Terminal' and for Command use '/builds/FlightGear/source/src/Main/fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ'. Hopefully that will work.

---

### Post by ecs_pf5 on 2007-06-23
This is it.. for some reason, that doesn't work.

Clicking the launcher results in.. nothing. No error message, just nothing at all.

Right now this minute, I have a launcher on the Desktop pointed at:

```

sh /builds/FlightGear/source/src/Main/gogf.sh

```with the script placed as per the path noted. This does the same - the launcher just makes like a lemon and does absolutely nothing in response to a click or double click.

If I change the command to

```

/builds/FlightGear/source/src/Main/gogf.sh

```then it does complain that it can't find the path. which makes me think, in the first example, it's finding it okay, then dying.

admittedly I've been getting mixed up somewhat between gofg and gogf in the posts above :lol: but I've just been through it again to check up, nope, no joy.

---

### Post by ecs_pf5 on 2007-06-23
[quote="yabbadabbadont"]
I wonder if it is complaining about not being able to attach to the X display? You know how that can happen when you use sudo to try to launch a graphical app instead of gksudo. Maybe something like that is going on.
[/quote]Could that be the case & if so.. could I fix it?

---

### Post by bigboy_pdb on 2007-06-23
That sounds peculiar. Perhaps you should try making an alias. In the command line type the following:
alias gogf='/builds/FlightGear/source/src/Main/fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ'

Now when you type 'gogf' it should execute the command. You'll still need to open a terminal but you could always just create a shortcut to the terminal by clicking and holding your mouse on the Terminal shortcut in 'Applications' -> 'Accessories' and dragging it to the panel or desktop. To recreate the alias automatically after you restart your computer you'll have to add it to the file '.bashrc' in your home folder.

---

### Post by ecs_pf5 on 2007-06-23
How cool is that 8)

Works like a charm.

(so I would just add a line alias = etcetcetc in .bashrc ?)

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

export PATH=${PATH}:/usr/local/share/OpenSceneGraph/bin
export OSG_FILE_PATH=/builds/OSG2/OpenSceneGraph-Data
export LD_LIBRARY_PATH=/usr/local/lib64

alias multifg='/builds/FlightGear/source/src/Main/fgfs --fg-root=/builds/FlightGear/data --multiplay=out,10,mpserver04.flightgear.org,5000 --multiplay=in,10,192.168.0.5,5000 --callsign=GWIZZ'

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after ea

```

I'll give it a reboot & see..

---

### Post by bigboy_pdb on 2007-06-23
Yes. In fact it tells you where to add the line in one of the comments. You might want to try restarting your computer after doing it to check that it works. Also, your terminal has a history of commands that you can scroll through by pushing the up and down arrow keys. I think the history remains even after you restart the computer, meaning you could just push up once or a few times (depending on what you've recently done in your last terminal session) to get the command instead of re-entering it every time that you want to run the program.

EDIT: You might want to try re-creating that Launcher on the desktop using the new alias command so that you don't even have to open the terminal

---

### Post by ecs_pf5 on 2007-06-23
Yeah it works admirably. & the up and down arrow thing is a good tip too Thx :p

---

### Post by bigboy_pdb on 2007-06-23
You're welcome

---

### Post by ecs_pf5 on 2007-06-23
I'm beginning to think I have a pet bug on this system, with the launcher. Although the alias works fine as described above, using it in a launcher fails in the same manner as the other flightgear commands. There's just.. nothing, when you click on it.

I've created launchers before and they've worked. Just this second I tried typing 'mozilla' in a terminal & I got a firefox open up; then I entered 'mozilla' in a launcher, clicked on it, &.. firefox came up. No probs at all.

So the problem seems to boil down to; launchers don't like my builds of flightgear. Oh well :(

Happy enough with the way the alias works in a terminal though.

---

### Post by po0f on 2007-06-23
ecs_pf5,

What happens if you move the script into /usr/local/bin (as root) and try to set a launcher to execute the script from there?

---

### Post by ecs_pf5 on 2007-06-24
Same thing. 

I created the script in /usr/local/bin/ via a root terminal;

It runs fine when called from a terminal:

```

user@ubuntu:/usr/local/bin$ gofg.sh
Warning: detected OpenGL error 'invalid enumerant' after RenderBin::draw(,)
freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.
user@ubuntu:/usr/local/bin$ sudo su
Password:
root@ubuntu:/usr/local/bin# gofg.sh
fgfs: error while loading shared libraries: libosgViewer.so.11: cannot open shared object file: No such file or directory
root@ubuntu:/usr/local/bin# 

```(the errors only serve to indicate that it did run.. plus the program's splash screen came up. the niggling program errors I can deal with seperately)

(note that no 'dot' 'slash' seemed to be required - /usr/local/bin/ is in the path anyway, is that the reason?)

(note 3 - interestingly, *running* it as root caused it to lose sight of an OSG library.. hmm)

..but if I try to invoke it from a Desktop launcher, there is no response to clicks at all, like always.

I wonder if that OSG library problem that showed up under root-invocation is significant of anything.

I built the whole install of flightgear from sources, and I'm a n00b, so maybe I have something 'twisted' inside flightgear.

Like, maybe I did something whilst building one of the dependency packages as root, when I should have been user, or vice versa.

---

### Post by bigboy_pdb on 2007-06-24
Sorry ecs_pf5. I made a mistake.

The '.bashrc' file is only for the bash shell (which is used by your terminal) meaning any aliases that you specify won't work in a Launcher. Also, the '.bashrc' file is read whenever you open a terminal, meaning you never had to restart your computer (you only had to open a new Terminal).

I understand that the problem of not being able to use a Launcher is a little irritating and I was trying to figure out why it wasn't working for you, unfortunately I can't think of a reason why the other methods didn't work.

Hopefully someone else can come up with a reason and fix for the Launcher problem. If I find a solution in the future, I'll try to post here again because you and others could benefit from the knowledge.

---

### Post by po0f on 2007-06-24
ecs_pf5,

Well, at least now that the script is in PATH, you can just open a `run` dialog with alt-F2 and execute it from there.

---

### Post by ecs_pf5 on 2007-06-24
Alt-f2.. that's a good one :)

Cheers guys for all your help. I get the feeling the launcher is trying to fire it up, then FG is throwing a spanner in the works. 

With the target program, at the end of the day you've got a newbie here using compilation tools he's never met before, on a fairly complex set of source files pulled from a bleeding edge non-stable development branch.

If that isn't a recipe for disaster I don't know what is :lol:

---

### Post by bigdude808 on 2007-07-10
I think I know what your problem is.

When you enter the commands manually, does it ask you for any sort of input? Y/N, yes, whatever?

If it does, that may be what's causing the flickering.  You need to set up the script to prompt the user for the ecorrect value.

I ran into the same problem, and I haven't figured out what to do yet

---

