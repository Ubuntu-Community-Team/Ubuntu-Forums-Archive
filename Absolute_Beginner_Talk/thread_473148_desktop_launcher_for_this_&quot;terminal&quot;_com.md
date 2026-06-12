---
title: "desktop launcher for this &quot;terminal&quot; command"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-06-13
Is it possible to make a desktop launcher for this command sequence that I normally issue in the terminal, so I do not have to go to the terminal and type this every time I want to check the status of my FAH ?

[B]cd foldingathome
cd CPU1
./qd[/B]

Thanks.

---

### Post by Ek0nomik on 2007-06-13
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

If you made a launcher and had the command set as:  foldingathome/CPU1/./qd

wouldn't that work?

---

### Post by cantormath on 2007-06-13
What kind of script is qd?
you should be able to execute it with an abolute path name.....ie) put /home/wpsshooter/foldingathorne/CPU1/qd into the launcher.

You could also make a hardlink from /home/wpshooter/foldingathome/CPU1/qd to /sbin/qd
```
:~$ sudo ln /home/wpshooter/foldingathome/CPU1/qd  /sbin/qd
```or if it does not require sudo
```
:~$ sudo ln /home/wpshooter/foldingathome/CPU1/qd  /bin/qd
```then you can just run qd from the command line......so, you could then put qd as a command in the launcher, or sudo qd if sudo is required.

---

### Post by punx45 on 2007-06-13
it appears qd is a program or script, so couldnt you just execute it with an absolute path name rather than moving into the directory and ./ ing it?

e.g.

<starting at root>/foldingathome/CPU1/qd

and therefore just place that absolute path in a launcher?

---

### Post by wpshooter on 2007-06-13
> **Ek0nomik said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

If you made a launcher and had the command set as:  foldingathome/CPU1/./qd

wouldn't that work?

NO.  When I do that and make it a "Application in terminal" launcher and then click on it from the desktop it just flashes up a blank terminal (as far as I can tell) and then automatically closes it.

Thanks.

---

### Post by psyopper on 2007-06-13
A sh or bash script would probably do it just fine. The script should contain the commands just as you have them. Drop the script into /usr/bin then create a shortcut that points to the script.

Are you the "learn how to do it myself" type? I hope so (you did install Linux!)
Look here for more on bash scripting: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by punx45 on 2007-06-14
> **wpshooter said:**
> NO.  When I do that and make it a "Application in terminal" launcher and then click on it from the desktop it just flashes up a blank terminal (as far as I can tell) and then automatically closes it.

Thanks.

thats because throwing the "." into the mix makes it an invalid pathname.  

"." is a shortcut that refers to the current directory. e.g. if you did 
```
pwd
cd . 
pwd

```
the result of pwd would be the same both times.

you could just write a script to execute that script, but using a script to execute a script or program is somewhat redundant.

---

