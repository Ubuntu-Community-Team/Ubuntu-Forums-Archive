---
title: "[SOLVED] Strg+Alt+F1... what then, Session lasts less than 10 sec..."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by excogitation on 2008-03-09
So when I'm in a console window - I only see a blinking cursor (top left) -
and what then? I can't enter anything. (don't laugh too hard)

Also I seem to have a problem with my xserver? or gnome? because
when I login it says sth. like my session only lasted 10 sec.
(xsession-errors attached)

One last thing how do I get compiz to autostart at startup/login?

---

### Post by dsauxier on 2008-03-09
Problem 1:
If you can't do anything int he console window, try going to another one : 
<CTRL><ALT><F1> or <CTRL><ALT><F2>
Then sign in.
My guess is that your in console 7 which has failed to load X for your userid and is stuck in limbo.
Alternatively, you can boot in recovery mode : 
When the system boots, press <ESC> to get to the grub menu, then select Recovery Mode (or something like that)

Problem 2: session lasted less than 10 seconds : 
I've had this problem a couple of times myself, but it's been a while.
In all code snippets below, replace "someuser" with your own username.

Look for a file in your home directory /home/someuser/.ICEauthority
```
ls -la /home/someuser/.ICEauthority
```
When I had this problem, that file was owned by root, so when I logged in I was unable to write to it.

If you booted in recovery mode, you're already root, so you won't need the "sudo" part of the command below.

```
sudo chown someuser:someuser /home/someuser/.ICEauthority
```

NOTE : I vaguely remember that the /home/someuser/.Xauthority file may have had the same problem, so check that one too.
```
ls -la /home/someuser/.Xauthority
sudo chown someuser:someuser /home/someuser/.Xauthority
```

Problem 3: Hopefully someone else will answer that - I'm not using it so I hate to provide an answer that I can't test.

---

### Post by excogitation on 2008-03-09
Thanks for your reply,

> try going to another one :
<CTRL><ALT><F1> or <CTRL><ALT><F2>
Then sign in.
My guess is that your in console 7 which has failed to load X for your userid and is stuck in limbo.

I only get a "_" in all consoles. I can't login because it doesn't ask me to (and I can't enter antything).

I temporarily got "everything" to run just fine, then I accidentially clicked on the today's xorg-driver-fglxr update and now the UI is broken again, but I'm quite confident I can get it to work again :)

Anyhow I can always use "Failsafe GNOME" (don't know from the login window or Recovery Mode as you stated.

---

### Post by excogitation on 2008-03-18
Due to multiple major problems (unsolvable with my linux knowledge)
I decided to reinstall Ubuntu and now this problem doesn't exist anymore.

Now the console asks me to login - like it's supposed to.
I have no idea what went wrong beforehand or how it can be fixed if it happens.

Also now I can use the fglrx drivers supplied by Ati without the 10sec. problem.

---

