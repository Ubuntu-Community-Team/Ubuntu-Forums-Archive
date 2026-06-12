---
title: "Simple Command help please :)"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-01-16
So, theres a file in usr/games I want to exec (./)
When I try cd /usr/games | ./run 
it says no such file (file is called run)
When I just do cd /usr/games | run 
it works but it doesnt call to another program specified in the run file, so it opens "run" but not the program I need. How can I accomplish all this without having to:
cd /usr/games -  then
./run
 I know this seems lazy on my part, but I use this file alot, plus it would be fun to figure this out 8)

---

### Post by 23meg on 2007-01-16
./ will make the shell look for the app in the current working directory. When you want to access something with an absolute path, just type the path itself, in this case it's /usr/games/run .

---

### Post by meng on 2007-01-16
cd /usr/games && ./run

OR

/usr/games/run

---

### Post by Daergeth on 2007-01-16
The "&&" worked, thanks! What exactly does && do if I might ask? (for my future reference)

---

### Post by meng on 2007-01-16
Think of && as "and then"
command 1 && command 2
means do command 1 and then do command 2

whereas the pipe symbol |
command 1 | command 2
means do command 1, get the output of that command and pass it onto command 2 as an argument

---

### Post by 23meg on 2007-01-16
[QUOTE=meng]
command 1 && command 2
means do command 1 and then do command 2
[/QUOTE]
It means "execute the command after this only if the command before it has completed successfully".[QUOTE=meng]
command 1 | command 2
means do command 1, get the output of that command and pass it onto command 2 as an argument[/QUOTE]More precisely, it directs the standard output of command one to the standard input of command 2.

---

### Post by Daergeth on 2007-01-16
Awsome, thank you so much. I was under the impression that the pipe command was used for that. Another side question, if this program (run) runs in term how could I get it to start up automatically when I start Linux. Could I just go to System<Pref<Sessions<Startup Progs and put that in it?

---

### Post by meng on 2007-01-16
Well, I'd put in
/usr/games/run
if you're going to enter it into sessions.
/usr/games/run is the more logical solution.

---

### Post by Daergeth on 2007-01-16
Well, for some reason when I do /usr/games/run it doesnt recognize the file that run pulls in. (its also an executable file and has to be ./) So it just says, file cannot be loaded. Sorry for being so difficult. :(

---

### Post by 23meg on 2007-01-16
> the file that run pulls inDo you mean the file referred to in this script? What exactly is the path to it? Try providing an absolute path to it as well.

---

### Post by kerry_s on 2007-01-16
Since it term based, try putting this in the startup->

```
xterm -T "Run" -e /usr/games/run
```

---

### Post by Daergeth on 2007-01-16
Yep, thats exactly what I meant.
The script is run
the program is tt++ (in /usr/games as well)

Run only has 1 line in it

./tt++ run.tin (run.tin is another script)

---

### Post by meng on 2007-01-16
Change the script to read.
/usr/games/tt++ run.tin

---

### Post by 23meg on 2007-01-16
Why are you passing another script as an argument to the app? Are you sure this is needed? If it is, provide an absolute path to both the game executable and that other script.

---

### Post by Daergeth on 2007-01-16
Alrighty, Ill give that a try, I created these scripts because the website for the program told me to :D. I figured they would know best. Heh.

---

### Post by 23meg on 2007-01-16
Why not give us a link to the instructions?

---

### Post by kerry_s on 2007-01-16
> **Daergeth said:**
> Alrighty, Ill give that a try, I created these scripts because the website for the program told me to :D. I figured they would know best. Heh.

How about a link to the website so we can see what your working with?

---

### Post by Daergeth on 2007-01-16
Ah, sorry about that. Guess its hard to help when the person in need isnt giving much in return.

[http://tintin.sourceforge.net/starting.php](http://tintin.sourceforge.net/starting.php)

Btw, thanks to all of you, this is why Ubuntu is so awsome :)

---

### Post by kerry_s on 2007-01-16
Okay, let me look this over and get back to you. so far just got this->

---

### Post by Daergeth on 2007-01-16
Just to show you my problem, the first attachment is what I get when I just /usr/games/run

The second is when I do it the longer route (Which works). All this going from file to file is confusing as hell to me ](*,)

---

### Post by kerry_s on 2007-01-16
Yeah, i took the lazy route i just grabbed the precompiled version, then just extracted it and ran it with "./tt++". But i have no idea what this is suppose to do. But i did create a launcher that launches it with just a click. i have mine in a tmp folder in my user accoumt, so i used this for the launcher-> 
```
xfce4-terminal -T "Run tt++" -e /home/user/tmp/tt++
```

Yours would start with "gnome-terminal" for the terminal, so from what i seen it would look like this for you->

```
gnome-terminal -T "Run tt++" -e /usr/games/tt++
```

You can press alt + F2 and put that command in there, if it works you can make a launcher.

---

