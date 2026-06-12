---
title: "Ubuntu killing application"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by laginimaineb on 2007-06-22
Hello, I am very new to Ubuntu and have recently encountered a problem. As a Java programmer, I supposed my applications will be able to run on Ubuntu easily. Anyway, I started an application of mine, and just as the main window started appearing I got the message "Killed" and the application terminated. I'm guessing this is the equivalent to Window's "End Task", but if so, why did Ubuntu automatically kill my application? 

P.S - If it helps, the application uses a library called "LWJGL" (Lightweight Java Game Library) which uses native Linux libraries (.so). However, I do know people have managed running LWJGL based applications on some Linux distributions.

---

### Post by Happy_Man on 2007-06-22
What's the app?

---

### Post by phr0ze on 2007-06-22
Have you gone through the log viewer to see if any problems are noted there?

---

### Post by laginimaineb on 2007-06-22
Hi again. The application I tried running is a Java game I wrote, using the game library LWJGL (which, as noted above, uses native Linux libraries). Anyway, I don't know which log you're talking about and what I should do with it (I'm a total beginner).

With Thanks,
laginimaineb.

---

### Post by tillo on 2007-06-22
Bash sends a "Killed" message when the process being spawned is killed by some kind of forced signal, like SIGKILL (man kill for more information).

Check the "ulimit -a" command to see if it's due to some process limit setting or check that your program or some of his library doesn't send an auto-kill signal. It probably means some code error anyway.

---

### Post by laginimaineb on 2007-06-22
Hey, I typed "ulimit -a" and it just showed me a list containing information about memory etc. Anyway, could the problem be the fact that I have very little memory? Otherways, what do you suggest I do next?

*Edit - I just edited the code to run in a Windowed mode, which enabled me to see a single frame of the game, followed by the "Killed" message. I have disabled mouse grabbing, to no effect.
Thanks much in advance,
laginimaineb.

---

### Post by laginimaineb on 2007-06-24
I tried running Ubuntu in Safe Terminal Mode, and then running my application. This time I managed to get 3 seconds of game-play, closely followed by the "Killed' message. I don't know if this is related to my post, but when I ran glxgears, I also got 3 seconds of fluent animation, followed by very very laggy performance (but no "Killed" message). Hope this helps.

With Thanks,
Laginimaineb.

---

### Post by laginimaineb on 2007-07-02
Sorry for BUMPing this post, however, I was wondering whether someone has found a fix yet? This problem is quite annoying and I have a really strong feeling it's caused by the very poor graphics card,processor and RAM, could it be?

With Thanks,
laginimaineb.

---

### Post by mysticrider92 on 2007-07-02
What method are you using to run the game? Maybe try starting it from a terimal with gij or install either the Blackdown or Sun Java. That may have an affect. Also, you could try compiling it with gcj. A simple way to do this is gcj -C *.java in a terminal (you may be familiar with using javac from a Windows command prompt, this is basically the same thing).

---

### Post by laginimaineb on 2007-07-10
Hello again, I just wanted to say I'm pretty confident the application was terminated because it required too much from a not-so-good computer. I ran the application on a better machine and it worked fine,
(By the way, I know how to run a java application :P)

Thanks for all the help,
laginimaineb.

---

