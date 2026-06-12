---
title: "Simple Scripting Question"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by zds on 2006-11-08
I'm having some trouble with what I believe to be a simple scripting issue. I want to use a script to start a program, allow it to run for a period of time, and then force it to quit.

In more detail, I'm trying to use mplayer to rip a media stream that's 3 hours long. I can start mplayer no problem, but the program doesn't have a built in runtime option. I think this is a candidate for a cron-triggered script that invokes the program in a child process, but I can't figure out the timing.

I've been trying to assign "date +%s" (the date in seconds) as a variable and then add time to that to get my quit time, but Bash is uncooperative (insisting that the variable is actually the command, not the resulting integer). I haven't yet addressed how to control the child process.

Can anyone help? Thanks!

---

### Post by bsussman on 2006-11-08
> **zds said:**
> I've been trying to assign "date +%s" (the date in seconds) as a variable 

```
bos@Dillon:~$ a=`date +%s`
bos@Dillon:~$ echo $a
1163021396
bos@Dillon:~$
```If this is for your homework, I am entitled to part of your grade but I prolly wouldnt want it :)

As far as the bigger question, it is sloppy but:

```
> command whatever with parameters&
> sleep 10800
> killall command
```There are waay better ways to do this...

Not that I really need to know, but why do you need to kill it?

---

### Post by zds on 2006-11-08
no, no homework. Just trying to get this stream.

I've used your suggestion. The problem is that I can't add to it (the variable is the date command, no the resulting integer).

Thanks.

---

### Post by bsussman on 2006-11-08
```
bos@Dillon:~$ a=`date +%s`
bos@Dillon:~$ echo $a
1163022113
bos@Dillon:~$ a=$((a+10800))
bos@Dillon:~$ echo $a
1163032913
bos@Dillon:~$ 
```

is this not what you are asking for?

---

### Post by zds on 2006-11-08
Yes, exactly! Thanks!

I told you this was really basic...

Can you point me to a good resource to learn this stuff on my own?

Thanks again.

---

### Post by bsussman on 2006-11-08
I know this sounds cold, but google 'bash tutorial' is really about the best start :)

I refreshed my memory of arithmetic using google 'bash arithmetic'

:)

---

### Post by zds on 2006-11-08
ok. thanks again!

---

