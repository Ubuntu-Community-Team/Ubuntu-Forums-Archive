---
title: "How to end a program running in terminal?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-03-27
When I run something like "tail -f filename", how do I get back to the command line when I am ready to end tail? Obviously I don't want to use killall or something like that. In top, I can just type "q". But that doesn't work in tail. And how do I know what works in other apps? Thanks.

---

### Post by codeslicer on 2008-03-27
Control+C cancels/terminates it...

---

### Post by whycantihavemyusername on 2008-03-27
Out of interest how would you continue the process running and still be able to use the session ie when using SSH i often open multiple connections..

---

### Post by Helgiks on 2008-03-27
> **whycantihavemyusername said:**
> Out of interest how would you continue the process running and still be able to use the session ie when using SSH i often open multiple connections..

If I understand you correctly, you can put it to sleep with ctrl+z and revive it with bg.

Also put "&" at the end of the command.

---

### Post by MountainX on 2008-03-27
I tried 
```
top &
```
as an experiment and now I can't seem to get it back

Is the command to bring it back to foreground
```
bg
```
or 
```
bg top
```
or something else?

---

### Post by smartboyathome on 2008-03-27
Use:
```
sudo killall top
```
to kill it.

---

### Post by MountainX on 2008-03-27
I still see top & listed when I type bg after doing killall - see output below

sudo killall top
[1]+  Stopped                 top
:~/.local/share/applications$ bg
[1]+ top &

---

### Post by which_chick on 2008-03-27
Once you've revived a sleeping top via bg, you have to type fg (to get it to the screen again) and then type q to quit it.

---

### Post by Whiffle on 2008-03-27
Also relevant to this is the "screen" program.  It lets you start a session, disconnect it, and then reconnect it.  Very handy for ssh, and other things like rtorrent.

---

### Post by MountainX on 2008-03-27
> **which_chick said:**
> Once you've revived a sleeping top via bg, you have to type fg (to get it to the screen again) and then type q to quit it.

Now I understand. And this works. Thanks

---

### Post by MountainX on 2008-03-27
> **Whiffle said:**
> Also relevant to this is the "screen" program.  It lets you start a session, disconnect it, and then reconnect it.  Very handy for ssh, and other things like rtorrent.

I found some info on "screen" here:
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

Do you know of other resource for how to use it?

---

### Post by Whiffle on 2008-03-27
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by MountainX on 2008-03-27
I'm just reading that gnome terminal (the one we have in Ubuntu) already does a lot of what screen does - it has tabs, for example. Will gnome terminal also allow you to disconnect from a running session and reconnect later?

---

