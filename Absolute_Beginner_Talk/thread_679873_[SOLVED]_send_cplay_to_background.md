---
title: "[SOLVED] send cplay to background"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2008-01-27
Hey folks,

I would like to launch cplay, start playing a file, then send cplay to background so I can continue with the same bash session while music is running.  Is this possible?

Thnx

---

### Post by emarkd on 2008-01-27
Try ending the command with an &.  If you still need to get back to the program later, you may want to check out screen

---

### Post by il-luzhin on 2008-01-27
Sorry I got it.

Type ! to get shell sesion. Then & to send to background and ignore the error message

---

### Post by il-luzhin on 2008-01-27
> Type ! to get shell sesion. Then & to send to background and ignore the error message

It seems I spoke too soon.

When I do this the file playing will  complete but the playlist will not continue so the current tune ends and that's all you get.  Any suggestions?  What I'm aiming for here is to play music without launching x-server.  For example, in a Ctrl + Alt + F1 session.

```

luzhin@kerenin:~$ cplay

--: 1: Syntax error: "&" unexpected
Traceback (most recent call last):
  File "/usr/bin/cplay", line 1643, in main
    app.run()
  File "/usr/bin/cplay", line 1466, in run
    self.keymapstack.process(c)
  File "/usr/bin/cplay", line 95, in process
    if keymap and keymap.process(code):
  File "/usr/bin/cplay", line 117, in process
    apply(method, args)
  File "/usr/bin/cplay", line 1586, in stop_input
    apply(self.stop_input_hook, args)
  File "/usr/bin/cplay", line 690, in stop_shell
    pid, r = os.waitpid(pid, 0)
OSError: [Errno 10] No child processes

```


thnx for the advice emarkd, but i need to open cplay to start the song playing before i '&' it

---

### Post by emarkd on 2008-01-27
If you need to interact with the program and then get back to a prompt without killing it, try installing screen:

```
sudo apt-get install screen
```

Then, you can start your software with screen
```

screen cplay
```

and when you're done interacting with it, you do <ctrl>A, D to detach.  Run screen -list and it'll show all of your screen sessions and you can reattach to one by running

```
screen -r <id>
```

Screen is really handy command line software

---

### Post by il-luzhin on 2008-01-27
Good Lord that's useful software!

thnx emarkd

---

### Post by emarkd on 2008-01-27
You're welcome.  I love screen and find uses for it all the time.  One more useful screen tip - when you start a screen session, you can give it a name.  Like this:

```
screen -S cplay cplay
```

The first cplay (the parameter to the -S flag) names the session and the second cplay starts cplay.  Then you can reattach by doing screen -r cplay instead of having to look up the session number.

There are lots of good feature to screen.  I'm sure you'll find all sorts of uses for it.

---

### Post by il-luzhin on 2008-01-28
well now that's slick!

---

