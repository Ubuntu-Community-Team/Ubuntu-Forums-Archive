---
title: "how to defrag ram?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Strannik on 2005-12-20
Hello all, could you help me with one question that started to interest me?
This may be a stupid question, so bare with me... I am using my computer for many hours a day..and I start to see that its just gets a little slow after a couple hours (for example firefox that just eats up all of my memory) I have only 256 and i'm only dreaming for an upgrade.. i know in windows i had some software that I could just use to defrag my ram and i would just flush all of the stuff that I had in my ram like the cache for firefox...

how would I be able to do this in ubuntu? 
btw. i'm using breezy

any help would be most helpful...

---

### Post by earobinson on 2005-12-20
there is a command to flush the memmory but I cant seem to think of it right now. You dont need to defrag the memmory, This is most likely caused by a memmory leak.

Do a apprapos memmory free to see if you can find the command, Im on windows right now so I cant

---

### Post by Rinzwind on 2005-12-20
earo: how about

**sync; sync; sync**

?

---

### Post by earobinson on 2005-12-20
[QUOTE=Rinzwind]earo: how about

**sync; sync; sync**

?[/QUOTE]
Im sorry I have no clue what you mean by that

---

### Post by Rinzwind on 2005-12-20
[QUOTE=earobinson]Im sorry I have no clue what you mean by that[/QUOTE]

To flush the memory ;)
But maybe it flushed your memory too :D :D

At least 3x sync normally (in Unix) flushes the memory. So I was asking you if this command rings a bell and was what works in Ubuntu too.
(since I'm not at my Ubuntu install too :( )

---

### Post by earobinson on 2005-12-20
no its not that, it was like a memfree or something. I read it on a blog some place DAM :mad:

look what I found, not what I was looking for but this should help the op lots [http://www.ubuntuforums.org/showthread.php?t=104179](http://www.ubuntuforums.org/showthread.php?t=104179)

---

### Post by bscbrit on 2005-12-20
To identify whether you need to 'defrag' your RAM (you can't but lets ignore that, I think I know what you mean) simply reboot the computer.  If it is a RAM problem the computer will have started again and your programs will be running at normal speed.  If it is a disk  I/O bottleneck, (i.e. the computer cannot write to and read from the disk fast enough to meet your requirements) then the computer will continue to operate at a slow speed.  But in linux there is no 'Disk Defrag' - it is not required.  My guess is that it is a memory problem or limitation.  
Memory leakage, in simple terms, is when a program asks for a block of memory, the memory is allocated to it by the kernel, but it never hands some or all of it back when it has finished.  Eventually, the kernel runs out of memory that it can use.  A memory hog is a program that simply uses huge amounts of RAM in order to run.   A third possibility is that your computer has insufficient memory for the number of  tasks you are trying to run - it will end up swapping data between memory and RAM - which is very time consuming in computer terms!  The first two are a fault of a particular application/program and there is not much that you can do to solve the problem other than 1.  Report it as a bug, with as much supporting information as possible so that it can be fixed, 2. be aware that a specific program has a problem and either reboot, restart as user as often as is necessary.  The last cause is because you are asking too much of the computer.  Either ask less of it, give it more memory, or live with it.

---

### Post by Strannik on 2005-12-20
I usually have the following programmes running all the time:
xmms, firefox, thunderbird, konsole, xine. Sometimes, I use abiword and gnumeric, or have apt-get downloading in the backround.
for example, The slowness starts after I look through some galery of wallpapers or just a lot of web pages. The whole computer just starts to respond slowwww... After reboot, everything is just great..
I was wondering is there any command that would just flush out the memory and cache that firefox-bin uses or something like that...

---

### Post by Perfect Storm on 2005-12-20
Sounds like a firefox problem. You could try with epiphany and see if it helps with your web-browsing

```
sudo apt-get install epiphany epiphany-extensions
```

Or try firefox 1.5 : [http://ubuntuforums.org/showthread.php?t=79283](http://ubuntuforums.org/showthread.php?t=79283)

---

### Post by Strannik on 2005-12-20
Its probably a firefox problem, and I already have firefox 1.5. Unfortunately, using epiphany will not work for me since I need all the extensions that I have with my firefox (thats why i love it so much)... So I am looking for some way to just *clear* out the memory that firefox uses in the swap and in my ram...how could i do that?

---

### Post by bscbrit on 2005-12-20
Ok, a really easy way to identify the cause of the problem is to start the System Monitor.  (Applications -> System Tools -> System Monitor).  Then you should be able to see whether the bottleneck is CPU or swap related.  You can also check that the computer is not processing other major tasks in the background which you might have overlooked.

EDIT:  I agree with Artificial Intelligence - Firefox is a known resource hog.  And, like you, I now want certain extensions so much that I cannot/will not change to another browser.  Once you have the System Monitor running and you see the problem again, kill firefox and watch the resources that it frees up.   Its a superb browser but not without its problems.

EDIT2:  There is no way of freeing the resources that Firefox is using without killing firefox - or, at least, I am not aware of any!

---

### Post by Strannik on 2005-12-20
Just looked in system monitor and firefox is eating about 130mb of virtual memory. 
bscbrit, I have the same situation. I need the extensions that I have so much that I just can't change to another browser, because it will just take a lot of time to find the alternatives (if there are any in other browsers) that i'm just stuck with it....just want to find out is there something i can do like flush all the stuff from my ram that firefox put in there every hour or so

---

### Post by tlc on 2005-12-20
Firefox eats ram. Not much you can do about that until they fix it, except use a different browser. Opera is excellent, and now free. There's also Galeon, Konqueror (actually very fast, but you'll probably have to install half of KDE too) and numerous others.

Can you not stump up $20 or whatever for another stick of ram off ebay?

Alternatively, close Firefox down every hour or so and then fire it up again.

---

### Post by Strannik on 2005-12-20
I use ubuntu at work, so nobody will get me more than 256 mb. another things is that i don't live in the states. Next: neither Galeon, nor Konqueror have the extensions that firefox has and i need a lot of them because they really help with my work. I like Opera too and i have it installed (and konqueror with kubuntu desktop and xubuntu desktop also).

---

### Post by cstudent on 2005-12-20
You might also try removing an extension an see what happens. If no change try another. It may be an extension causing a problem and not so much Firefox itself.

---

### Post by bscbrit on 2005-12-20
There are lots of useful tips regarding firefox being given - and I am grateful - but for me it is simply a case of firefox meets my requirements but it has a flaw.  I am running computers with as much as 750Mb of RAM, and firefox still eats great chunks of it for no apparent reason.  I know that I and others have reported this bug but it is either very difficult to pin down, or too low down on the priority list that it is not being addressed.  I mention this to counter the suggestion that the problem might be solved by buying more RAM - it won't be, but thanks for the thought.  I am  resigned to closing it down and restarting it periodically.

---

### Post by jastonas on 2008-05-30
I have emesene and at some point probably because of a memory leak (?) it gets tos 1.8gb of memory as seen in system monitor.. and i need to endthe process which takes me a couple minutes and is very frustrating. Can i limit the amount of memory a program can use?

---

### Post by lavinog on 2008-05-30
You should start a new thread, this one is quite old.
you could use a script to kill it and restart it when the memory reaches a certain point. Generally i keep the system monitor gnome-panel applet up...if the swap starts getting used i know there might be an issue and close out programs i don't use. (this happens alot with the gimp and super large images)
you may also want to file a bug report for the memory leak or see if there is an update to that program.

---

### Post by Sealbhach on 2008-05-31
There's a Firefox tweak you might want to try. Makes a difference, apparently.

[http://ubuntuforums.org/showthread.php?t=202838](http://ubuntuforums.org/showthread.php?t=202838)


.

---

