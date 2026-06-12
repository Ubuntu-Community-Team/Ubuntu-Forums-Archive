---
title: "Is there a way to execute a job in the background from ssh and then logout?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by ioannis on 2006-12-03
This might sound like asking for too much, but maybe it can be done:
Sometimes I need to execute a very long running program in my computer at work from home. I ssh from my laptop at home to my computer running edgy at work and submit the job in the background using &. Obviously, I have to leave the laptop on and the ssh session running for the process not to be interrupted. Is there any other way to submit a job to my computer through ssh that would allow me to then close my ssh session but keeps the program running? This might sound ridiculous, but I figured at least I'd ask. Thanks!

---

### Post by apjone on 2006-12-03
yeah , you can use the nohup command

---

### Post by Bachstelze on 2006-12-03
Screen is what you need :)

```
sudo apt-get install screen
```

---

### Post by TerryHowe on 2006-12-03
To use the nohup command, you probably want to toss an & at the end of the command like to run it in the background or ctrl-z if you forget.

---

### Post by steve.horsley on 2006-12-03
**nohup myprog > myprog.out &**
should do the trick.

---

### Post by ioannis on 2006-12-03
Thanks for the answers! I have been wondering how to do this for a while. I looked up both nohup and screen, and screen seems to be more powerful because you can re-attach the session after logging out, does nohup have an option to retake control of the process? I don't mean to start a nohup vs screen thread, but if somebody could say what the advantages/disadvantages of both are, that would be great. Thanks a lot again.
In my opinion this forum is one of the major reasons why Ubuntu is great.

---

### Post by steve.horsley on 2006-12-03
I hadn't heard of screen until HymnToLife said about it. I looked at the web page and it looks really powerful but needs some effort to learn. nohup on the other hand is simple. nohup does not have any option for reconnecting to the process.

So for fire-and-forget such as launching a backup job or a daemon that you control through a socket, nohup is the way to go. 

For a process you want to return to, screen must be the way to go. I need to think about it for a while - I didn't know anything like it was possible - there must be good uses for such a facility.

---

### Post by speedman on 2006-12-03
screen doesn't take much effort to learn.

screen <command_you_want_to_run>

<ctrl> <a> <d> to detach from the screen session.

The next time you log in you can reattach to the screen session with:

screen -r

If you have multiple screen sessions running you will be presented with their details and can connect to them like this:

screen -r 1234.pts-1.hostname

... where 1234.pts-1.hostname is one of the returned values from the output from screen -r.


Regards,

SM

---

### Post by steve.horsley on 2006-12-03
Hmm. That much, I can handle. That much is simple and useful. 

I don't think I'll bother trying to remember the other reams and reams of man page. There's so much man page you can't tell from there if screen is actually useful or not. It would have been nice if it gave a menu or something like that (like the commands in minicom).

---

### Post by DaveBorealis on 2006-12-03
Hello,

A 'screen -h' will give a menu that might be of use.  Take a peek.

Dave

---

