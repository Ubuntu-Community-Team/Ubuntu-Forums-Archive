---
title: "Ripping CD's"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-05
I need another program to rip CD's because I screwed up Sound Juicer and no one can figure out how I did it.  What would you recommend?

---

### Post by htinn on 2006-05-05
If you don't mind having to pay for it, there's also Nero:

[http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)

---

### Post by Sef on 2006-05-05
> I need another program to rip CD's because I screwed up Sound Juicer and no one can figure out how I did it. What would you recommend?

Try to fix it this way.

Applications > Accessories > Terminal

sudo apt-get remove --purge sound-juicer

that will totally remove sound juicer including the configuration files.

Now to reinstall it.

sudo apt-get install sound-juicer

---

### Post by Guns90 on 2006-05-05
I appreciate the tip Sef, but I still get an error window that says

Cannot launch entry

Details: Failed to execute child process "/home/gary/Billy" (Permission denied)

---

### Post by Sef on 2006-05-05
That sounds like a Permission problem.  Not sure how to take care of it offhand.  If I find something, I will post it here.  

> /home/gary/Billy

That seems odd.  Could you post what it says in your Terminal.  Just open the terminal and copy and paste everything before the $, including the $.

---

### Post by Guns90 on 2006-05-05
gary@GARY:~$

Yeah, I know.  I shouldn't have used Gary twice.

---

### Post by Sef on 2006-05-05
For future reference: Make your box gary1, so as to differenciate it from your user name.

---

