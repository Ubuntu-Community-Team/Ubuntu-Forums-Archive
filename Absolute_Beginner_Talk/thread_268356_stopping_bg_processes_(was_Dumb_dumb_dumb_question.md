---
title: "stopping bg processes (was: Dumb dumb dumb question)"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by jeepescu on 2006-09-30
How do you stop a background process in linux ? 

I am running vpnc to connect to work, and it works very well. 
I am getting a message like this: 
[FONT="Fixedsys"]
root@imladris:/home/elrond# vpnc /etc/vpnc/vpnc.conf
Enter password for glorfindel@24.201.243.21:
VPNC started in background (pid: 32414)...[/FONT]

My questionis, once I am done< I would like to close this process.
The only way I found is by using kill 32414 

Is there another , more elegant way to do this? 

Thanks in advance,
BN

---

### Post by LookTJ on 2006-09-30
System -> Administration -> System Monitor

:)

---

### Post by jeepescu on 2006-09-30
Thank you for your reply. 
I forgot to mention I am looking for a command. 
BN

---

### Post by jr.gotti on 2006-09-30
The only dumb question is the unanswered one...(wow...there goes my cliche quota...)

Anyway...heres a quick command line tutorial (everythings quicker with the command line...you'll come to learn that)

By entering "ps -aux" in the terminal, you will list all processes running on your box. However, you probably don't want to read through that whole list...so we'll pipe it through grep, which is like a search result filter, if you will.

Say your trying to find process xyz. we would enter

"ps -aux | grep xyz"

If "xyz" was indeed running, the output will be like the following:

jason    24468  1.7  2.1  55872 16288 ?        SLl  00:33   0:58 xyz

See the number after my username? Thats the process number. We can close the process using that number. Enter the following in the terminal.

"kill -19 24468" (or whatever your process number is)

Blam! Renegade process is dead!

So you'll probably want to enter something like this...

"ps -aux | grep vpnc"

Find the process number, and kill -19 it, and you're good to go.

Hope I helped!

EDIT: DOH!! I TOTALLY didn't read your whole post before replying...you already do the kill thing...oh well...I'll keep this up for others to read...

As far as elegance, IMO, who cares? Does it work? Yup. Is it fast and efficient? Yup. Go for it. :D

---

### Post by jordanmthomas on 2006-09-30
I'm not sure if this will work, but if your program is running as a daemon / service,
```
sudo /etc/init.d/*appname* stop
```
will stop lots of things.  Otherwise, *kill PID* is the way to go.

---

### Post by jeepescu on 2006-09-30
Thanks to all who replied.

Pixelpoet: I tried something simpler that appears to be working too:

ps -C vpnc

It only returns one line with the pid of the process.
Next on my list, putting this (and the kill) in a script that will do it "fully automatic". Another fun linux challenge. 

jordanThomas: It doesn't work, I tried it. 

Ubuntu rocks !!!

---

### Post by jr.gotti on 2006-09-30
hmm, wow! thanks for the ps -C tip! never knew about that...I'm so stuck in my old methods...I use grep for EVERYTHING...

learn something knew everyday...

---

### Post by olejorgen on 2007-02-05
uh, I think (at least now) it's connect and disconnect scripts you can run. vpnc-connect and vpnc-disconnect

---

### Post by Brunellus on 2007-02-05
thread title changed to reflect nature of question.  Please use the thread title to summarize your problem/question--do NOT use it to flog yourself about how dumb you are.  Your self-flagellation is not likely to result in good technical advice.

We're here to help.  Tell us how we can.

---

