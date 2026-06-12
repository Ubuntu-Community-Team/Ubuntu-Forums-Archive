---
title: "could someone tell me how to make a custom script run on startup?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-08
SOLVED

ok.  i'm a TOTAL noob when it comes to linux.  i've just installed a program and have to start it JUST A CERTAIN WAY.  here's the way i'm talking about.

```

cd /home/link/.cairo-dock
./cairo-dock --no-glitz

```

it HAS to be executed JUST like that.  could someone tell me STEP BY STEP how to do this?  THANKS.  (i like emphasis. [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/giggle.gif[/IMG] )

---

### Post by earobinson on 2007-05-08
go to system -> preferences -> sessions and you should be able to add as many programs as you want to start up.

you should just put that code into a file named <your choice>.sh and run that at start up.

---

### Post by locke.dragon on 2007-05-08
don't i have to give it executable permissions first?  how can i do this?  

when i try to run the .sh file i just made in terminal i get this 
```

link@aperturescience:~$ /home/link/.cairo-dock/launch.sh
bash: /home/link/.cairo-dock/launch.sh: Permission denied

```

---

### Post by earobinson on 2007-05-08
oops your right.

chmod +x <file name>

or you can run ```
sh <filename>
```

---

### Post by Skrynesaver on 2007-05-08
One little thing, in order to run a file as a program you have to make it executable and you have to call the command interpreter.  It's also a good idea to make a bin directory in your home directory where you store your scripts, thus
```

mkdir $HOME/bin
echo "#! /bin/sh[FONT=monospace]
[/FONT]$HOME/.cairo-dock/cairo-dock --no-glitz" >$HOME/bin/cairo_startup.sh
chmod 755 $HOME/bin/cairo_startup.sh

```now go to system>Preferences>Sessions
and under the startup programs tab add /home/link/bin/cairo_startup.sh

---

### Post by earobinson on 2007-05-08
> **Skrynesaver said:**
> One little thing, in order to run a file as a program you have to make it executable and you have to call the command interpreter.  It's also a good idea to make a bin directory in your home directory where you store your scripts, thus
```

mkdir $HOME/bin
echo "#! /bin/sh[FONT=monospace]
[/FONT]$HOME/.cairo-dock/cairo-dock --no-glitz" >$HOME/bin/cairo_startup.sh
chmod 755 $HOME/bin/cairo_startup.sh

```now go to system>Preferences>Sessions
and under the startup programs tab add /home/link/bin/cairo_startup.sh
that works also. ```
man chmod
``` for more info

---

### Post by locke.dragon on 2007-05-08
hey thanks guys!  works like a charm.  [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/clap.gif[/IMG]

---

### Post by earobinson on 2007-05-08
np

---

### Post by klep on 2007-05-10
hello,

i've just come to the forum to ask this exact question. Annoyingly though I'm already doing what is being suggested and it wont work..

I have a script called initwireless.sh:

```
#!/bin/sh

modprobe ndiswrapper

```


and in the sessions section i have added a new entry and have set the command to: /usr/local/bin/initwireless.sh 

But it doesnt work. If i run that script from the commandline (with sudo permissions) my wireless starts working fine but my wireless does not work fine when the pc boots up so i assume the script is not running on start up... That or it does not have permission to run bit I would assume it would run the script with root privilege rather than user privilege?


Anyone any ideas?

---

### Post by klep on 2007-05-10
boy is my face red. I didnt realise running "sudo ndiswrapper -m" once would add to to the list of modules loaded by the kernal at startup anyway.


Still, I found out that /etc/rc.local will be executed as one of the last things before a full boot up and anything in it is run with root privileges so hope that helps someone.

---

### Post by Skrynesaver on 2007-05-10
If you call the script in /etc/rc.local it will run on boot

---

### Post by locke.dragon on 2007-05-10
i just recently found out the solution to this.  if you want a script like that to run at startup, you have to give it the priveledges it needs.  just do this...

 Give a .sh file executable priveledges
```

chmod +x <file name>

```

hope that helps!  :D

---

### Post by frogitts on 2007-05-11
I know that running sudo ndiwrapper -m will add it to startup, but that doesn't help me. Here's my script:

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Which I type in manually every time I start my computer.

So far I have:
Made a $HOME/bin director where the file ("rewrap.sh") resides
Put in the following commands (I tried one first, then the other) in System->Preferences->Sessions:
'home/myname/bin/rewrap.sh'
sh '/home/myname/bin/rewrap.sh'
typing "echo "#! /bin/sh" into the terminal, which results in a prompt that looks like this: >
and does nothing. Even though nothing happens, I typed in: 
```
> $HOME/bin/rewrap.sh
> chmod 755 $HOME/bin/rewrap.sh
```

and got nothing.


I'm about to try putting it in /etc/init.d and running "sudo update-rc.d name_of_script defaults" which I got from here: [http://ubuntuforums.org/archive/index.php/t-36505.html%3c/t-178682.html](http://ubuntuforums.org/archive/index.php/t-36505.html%3c/t-178682.html)

Unfortunately, for that last thing, I need to know how to make a file 'executable', and I don't know how. It'd be nice to know what I'm doing wrong so that this happens automatically.

On the plus side, all I have to do now is run sh '/home/alex/bin/rewrap.sh in the terminal instead of typing three lines of code every time I start my computer, so thanks for that :)

---

### Post by kangol69 on 2007-05-11
Also instead of using rmmod you can blacklist the bcm43xx module from starting by editing your /etc/modprobe.d/blacklist and adding the following to the bottom of it. 
```
blacklist bcm43xx
```
That will take care of the rmmod and to have ndiswrapper load add "ndiswrapper" to /etc/wrapper

That should take care of what you're doing but It's a different route.

---

### Post by klep on 2007-05-11
and if not like that (which is nicer) , as i mentioned earlier you could add those 3 lines to /etc/rc.local and have them all executed on start up.

---

### Post by frogitts on 2007-05-11
Thanks! That worked perfectly!

---

### Post by locke.dragon on 2007-05-11
> **frogitts said:**
> I know that running sudo ndiwrapper -m will add it to startup, but that doesn't help me. Here's my script:

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Which I type in manually every time I start my computer.

So far I have:
Made a $HOME/bin director where the file ("rewrap.sh") resides
Put in the following commands (I tried one first, then the other) in System->Preferences->Sessions:
'home/myname/bin/rewrap.sh'
sh '/home/myname/bin/rewrap.sh'
typing "echo "#! /bin/sh" into the terminal, which results in a prompt that looks like this: >
and does nothing. Even though nothing happens, I typed in: 
```
> $HOME/bin/rewrap.sh
> chmod 755 $HOME/bin/rewrap.sh
```

and got nothing.


I'm about to try putting it in /etc/init.d and running "sudo update-rc.d name_of_script defaults" which I got from here: [http://ubuntuforums.org/archive/index.php/t-36505.html%3c/t-178682.html](http://ubuntuforums.org/archive/index.php/t-36505.html%3c/t-178682.html)

Unfortunately, for that last thing, I need to know how to make a file 'executable', and I don't know how. It'd be nice to know what I'm doing wrong so that this happens automatically.

On the plus side, all I have to do now is run sh '/home/alex/bin/rewrap.sh in the terminal instead of typing three lines of code every time I start my computer, so thanks for that :)

you have to type in 
```

chmod +x

```

you left out the +x part.  let me know if that works.

---

