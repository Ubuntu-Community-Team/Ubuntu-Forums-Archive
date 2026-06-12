---
title: "How to start a program with a low priority process  ?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-20
How to start a program with a low priority process  ?
  or to make a process in the background
  
Thank you !
  
Patrick

---

### Post by patrick295767 on 2006-05-20
I recall now !!  I used it in slack 3.1
Nice !! is the key program... 
  
> Nice can be used with an integer from 0-19 if you are a normal user, and -20 to 19 if you are the superuser. Strangely, positive numbers decrease the application&#8217;s priority and negative numbers increase it. Hence why only the superuser (root) can elevate a processes&#8217; priority via negative nice numbers.

The basic syntax of the nice command is:

nice process/application [nice number] [options]

    nice foo &#8211;15 &

This command will start application foo at an elevated priority of -15 and push it to the background (&). If you don&#8217;t specify a nice number, the default of 10 is used.


  
[http://www.die.net/doc/linux/man/man3/nice.3.html](http://www.die.net/doc/linux/man/man3/nice.3.html)

---

### Post by patrick295767 on 2006-05-20
If you niced once, then : 
  
You have to renice it !
> You can change the default priority that an application runs with by starting it with the nice command, but if you want to change the priority of a process that is already running, the command to use is renice.

Renice can be used to change the priority of a single process, or of all the processes owned by a specified user. As with the nice command, the priority values range from -20 to +19 and negative numbers raise the priority of a task while positive numbers lower it. Only the superuser can specify negative numbers (thus raising the priority of a process).

    renice 5 some_process

This command will change the priority of some_process to 5.

    renice -5 -u jon

will change the priority of all processes owned by user jon to -5.

    renice -5 -u jon -p 588
  
[http://www.die.net/doc/linux/man/man8/renice.8.html](http://www.die.net/doc/linux/man/man8/renice.8.html)
  
Greetings !!

---

### Post by patrick295767 on 2006-05-20
Thread Solved !

---

### Post by Harleen on 2006-05-20
Edit: man, I'm getting slow

To start a program in the background, append a & on the command call:

> program &

If the program is already running and you want to send it into background, you can suspend it by pressing <CTRL>+Z and then type "bg" to send it into the background. Type "fg" to get it back in the foreground.

If the program shall keep running in the background, after you have logged out, start it with
> nohup program

To set the process priority, start the program with "nice":
> nice 19 program
will run your program with idle priority. The default nice level is 10. 
You can change the priority of a program aleady running with "renice".
Note that you can only lower the priority. Only root can increase it. (where lower priority means higher nice-numbers and vice verse)

---

