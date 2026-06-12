---
title: "force quit"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by bmenge on 2007-02-08
I tried to open an email attachment in open office and as I opened the file it gave me a list of filters to open with?  Anyway I chose the file extension that the file was saved as(wps) and went on to open the file.  After waiting and waiting I chose to force quit the operation.  Now as a result I can not run Open Office.  Is there something I have to do to get it to open after a force quit or has something out of the ordinary happened here. Thanks for any help or advice that might be out there.

---

### Post by annda on 2007-02-08
have you tried logging out or even rebooting? this is the easiest way to kill all your running processes and applications (you can use top from the terminal or the system monitor as well).

if you still can't run OO after reboot, try typing openoffice in the terminal and see what errors it shows.

---

### Post by K.Mandla on 2007-02-08
I believe under System > Administration there's a System Monitor tool. You can check there to see if there's an OpenOffice process still hanging there, and kill it out if you want.

Does that help? If not, it might require a reboot, although I always feel guilty suggesting it. :oops:

---

### Post by Greykrrr on 2007-02-08
I'm not at home right now, so I can't check it, but if feel like venturing into the terminal you try and type (I believe this is correct):

ps - ax

and see if Open Office is listed. If it is, type

sudo killall <proces name>

that ought to do it.

Oh, and if you want to always have a termnal handy I suggest Tilda. It is small and lightweight and can drop down at the press of a button :)

---

### Post by mojoman on 2007-02-08
When I want to kill something i always make sure I got the right tool for the job. The sharpest blade in Linux is the terminal

```
ps aux | grep [o]pen
```

This will give you a list of openoffice programs that you're running. Note the number (four digits) of that process, say, 8796. Ok, and now...

```
kill 8796
```

Now, it may be the exact same thing that the GUI alternative does, I don't know because I always use this, but let's face it, it's more fun to order your computer to actually kill something.

Oh, no, that's right, I keep forgetting, it's humanity towards other or something, eh, well, it works anyway... 
;)


edit: damn, a little to slow on the trigger...

---

### Post by bmenge on 2007-02-09
Ok thanks for all the help, there is a lot of traffic on this board.  I got oo to run after a reboot but that even took two times before I tried to reboot I started with typing openoffice in the terminal and that hung up as well and did not really respond.  Then I went to the system monitor and there were about 10 oo processes sleeping, I tried to kill those and the system froze all to gether.  This is when I tried to reboot.  I got an error saying could not kill pid when the system rebooted, I hit the power buton and all was fine...I think in the future I will use the suggested 

ps aux | grep comand I played with that once I got going again and it seems nice.  

thanks again for all the help

---

