---
title: "Beginning with Cron"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-05-21
Hi!
I'm starting to lear Cron, but just after I started I ran into a problem.
I'm using [this howto]("http://wiki.ubuntu.com/CronHowto").
My crontab is the following:
[QUOTE=Klaidas's crontab]*/1 * * * * echo "This is a test. It will annoy you every 1 minute! :)"
[/QUOTE]
However, nothing is echoed. I don't get any message.
What am I doing wrong? :-?

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=Klaidas]Hi!
I'm starting to lear Cron, but just after I started I ran into a problem.
I'm using [this howto]("http://wiki.ubuntu.com/CronHowto").
My crontab is the following:

However, nothing is echoed. I don't get any message.
What am I doing wrong? :-?[/QUOTE]


I think this is the format

Min(0-59)  Hr (0-23)  Day(1-31)  Month(1-12 or Jan-Dec)  Day(0-6)  

     *            *               *                    *                        *

---

### Post by skippy81 on 2006-05-21
I would imagine its because it doesnt know where to echo it too.  Try piping the echo into a file like this:

> */1 * * * * echo "This is a test. It will annoy you every 1 minute! " >> /tmp/crontest

That will help you see if it is working.  Since you will be in your gui you could try doing this : 

> */1 * * * * xmessage  "This is a test. It will annoy you every 1 minute!" 

That should be very annoying, it will open a pop up on your desktop every minute.  Kinda like using Windows XP :p

---

### Post by DSn0wMan on 2006-05-21
I tried the echo, and it didnt work, but if I direct the echo to a file then it shows up.

```
***** echo "testing testing" > /home/test.txt
```

---

### Post by Klaidas on 2006-05-21
I have changed it to ```
*/1 * * * * echo "This is a test. It will annoy you every 1 minute! :)" >> /home/klaidas/Desktop/cron_test

```
It seems to work. I guess the problem was that [QUOTE=skippy81]its because it doesnt know where to echo it[/QUOTE]
Thanks :)

Is there a way to send this message to an active terminal window?

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=Klaidas]

Is there a way to send this message to an active terminal window?[/QUOTE]

I think you have to direct the echo to stdout or &1 (shorthand for standard out)

So far I can't get it to work for me.

* * * * * echo "testing" > &1

maybe directing output to stdout requires a special technique.

---

### Post by 5-HT on 2006-05-21
[quote=Klaidas]I have changed it to ```
*/1 * * * * echo "This is a test. It will annoy you every 1 minute! :)" >> /home/klaidas/Desktop/cron_test

``` It seems to work. I guess the problem was that 
Thanks :)

Is there a way to send this message to an active terminal window?[/quote] 
If you want to sent it to the terminal of a particular user (I'm using klaidas here, but substitute appropriately), something like this should work:

```
*/1 * * * * echo "This is a test. It will annoy you every 1 minute! :)" | write klaidas 
``` 
If you want to send it to all users: ```
*/1 * * * * echo "This is a test. It will annoy you every 1 minute! :)" | wall 
``` 
Hope that helps.

---

### Post by DSn0wMan on 2006-05-21
Very cool. I had forgotten about wall.

---

### Post by 5-HT on 2006-05-21
[quote=DSn0wMan]Very cool. I had forgotten about wall.[/quote] 
Along with write, wall's a nice utility!
It can be hard at times to resist annoying users with them on a network though... :)

---

### Post by Klaidas on 2006-05-22
Thanks for the > write and > wall commands. It now works! :)

---

