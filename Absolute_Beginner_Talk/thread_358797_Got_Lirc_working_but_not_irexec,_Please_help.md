---
title: "Got Lirc working but not irexec, Please help"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2007-02-11
Hello

    I finally got Lirc working. My remote works in mplayer as setup in my lircrc . But I aslo put a command in the lircrc file to start mplayer with irexec. But it doesn't work. I've also tried another commands to start another programs. That I've found on the forum. But none work. What I'm I doing wrong. (and yes I started irexec in terminal)

Here's my Lircrc

# MPLAYER ======================================|
begin mplayer
begin 
    prog = irexec
    button = TIVO
    mode = mplayer
    config = /usr/bin/mplayer
end
begin
    prog = mplayer
    button = PLAY
    config = pause
end
begin
    prog = mplayer
    button = REWIND
    config = seek -10
end
begin
	prog = mplayer
	button = FORWARD
	config = seek 10
	repeat = 1
end
begin
	prog = mplayer
	button = WINDOW
	config = vo_fullscreen
end
begin
	prog = mplayer
	button = CHAN_UP
	config = volume 1
	repeat = 1
end
begin
	prog = mplayer
	button = CHAN_DOWN
	config = volume -1
	repeat = 1
end
begin
    button = TIVO
    prog = mplayer
    config = esc
end

begin
    button = THUMB_DOWN
    prog = mplayer
    config = pt_step -1
    repeat = 1
end
begin
    button = THUMB_UP
    prog = mplayer
    config = pt_step 1
    repeat = 1
end
end mplayer

---

### Post by energiya on 2007-02-11
irexec must be running. The best way to start it is to put it in an initialization script or write yourself
```

irexec &

OR

[B]better use:
irexec -d
[/B]

```
in a terminal window (nasty thing to do)

---

### Post by Shawn Dineley on 2007-02-11
Ya I started it before I tried it. But nothing happens???

---

### Post by Dubstar_04 on 2007-02-25
Did you solve this problem as I am finding them same problems starting myth front end.

---

### Post by eagle63 on 2007-03-04
Yep, same problem here.  I too am running Mythfrontend on Edgy, and while I have Lirc working great, irexec doesn't work at all.  I've started it from a terminal by typing "irexec -d" .  Typing ps -e | grep irexec shows that it is indeed running.

In my lircrc configuration file, I've got the following:
begin
  prog = irexec
  button = Power
  config =  /home/mythfrontend/scripts/doSomething.sh
end


I know the doSomething.sh script works fine, as I can run it manually.  And the path to the script is correct.  

So what's going on!??

---

### Post by superm1 on 2007-03-04
> **eagle63 said:**
> Yep, same problem here.  I too am running Mythfrontend on Edgy, and while I have Lirc working great, irexec doesn't work at all.  I've started it from a terminal by typing "irexec -d" .  Typing ps -e | grep irexec shows that it is indeed running.

In my lircrc configuration file, I've got the following:
begin
  prog = irexec
  button = Power
  config =  /home/mythfrontend/scripts/doSomething.sh
end


I know the doSomething.sh script works fine, as I can run it manually.  And the path to the script is correct.  

So what's going on!??
Have you heard of ircat?

ircat is used to diagnose .lircrc file parsing errors. Take a look at it.

Also, did you make sure that script of yours is marked executable.

---

### Post by eagle63 on 2007-03-05
> **superm1 said:**
> Have you heard of ircat?

ircat is used to diagnose .lircrc file parsing errors. Take a look at it.

Also, did you make sure that script of yours is marked executable.

Yes, it's executable - again I can run the script manually just fine.  

I haven't herad of ircat, but I don't think it's possible that I have a parsing error in my lircrc file.  MythTV is currently using it, and it works fine with the exception of when I change one of the button configurations to use irexec.

---

