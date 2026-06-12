---
title: "Make sources.list ready:  what does this mean?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-02
So I decided to follow the custimization guide there is a link to in one of the sticky posts in this forum. i read it severl atimes, then opened the terminal, typed in the first command, and got this message back:

> 
chili@chili-laptop:~$ gksudo gedit /etc/apt/sources.list
(gedit:5817): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

A gedit window opened, with a lot of information about the repository, and the terminal went unresponsive after that. I typed in "sudo aptitude update && sudo aptitude upgrade" more to see if the terminal was asleep or not, than anything else,and it let me type, and then nothing happened. I have a theory I wasn't supposed to type that in there...

I'm curious about that the GnomeUI-Warning means though. It looks to me as if a file or two that the system wants aren't there, but other than that I have no idea.

/Mimsy

---

### Post by bulldog on 2006-09-02
You can savely ignore the warning,it's a little bug and totally harmless.

You did the right thing to use gksudo to open an app. with a graphical interface,and sometimes,mostly with gedit you get this warning.

The terminal will be responsive again when you close gedit.
That's normal behavior when you open an application with the terminal,it will not respond till you close the app.

You could open a new terminal if you need to though.

---

### Post by taurus on 2006-09-02
Then use nano to edit your /etc/apt/sources.list...

```
sudo nano /etc/apt/sources.list
```

---

### Post by aysiu on 2006-09-02
Everything that bulldog says is true. When you launch an application from the terminal, the terminal will remain unresponsive until you close that application.

And you should use *gksudo* for graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Mimsy on 2006-09-02
> **bulldog said:**
> You can savely ignore the warning,it's a little bug and totally harmless.

You did the right thing to use gksudo to open an app. with a graphical interface,and sometimes,mostly with gedit you get this warning.

The terminal will be responsive again when you close gedit.
That's normal behavior when you open an application with the terminal,it will not respond till you close the app.

You could open a new terminal if you need to though.

I was informed in another thread that using sudo to open anything with a graphical interface is very bad. I don't quite understand why, but I trust this other forum member to know what he or she is talking about. So gksudo it is. :) 

If I understand you right, I wait for gedit to open that file, then close it and type in the aptitude upgrade and update command in the terminal. Then it's all good and it updates. Did I get that right?

/Mimsy

---

### Post by taurus on 2006-09-02
> **Mimsy said:**
> 
If I understand you right, I wait for gedit to open that file, then close it and type in the aptitude upgrade and update command in the terminal. Then it's all good and it updates. Did I get that right?

/Mimsy
Yes.  You've got it.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Mimsy on 2006-09-02
Awesome. Thanks! :)

/Mimsy

---

### Post by aysiu on 2006-09-02
> **Mimsy said:**
> I was informed in another thread that using sudo to open anything with a graphical interface is very bad. I don't quite understand why, but I trust this other forum member to know what he or she is talking about. So gksudo it is. :) Read the link I posted earlier.

---

### Post by Mimsy on 2006-09-02
I completely missed your post earlier. I apologise. And feel rather stupid for not noticing it. Thanks for the link, I'll check it out. :)

EDIT: I have checked it out, and consider myself a bit more educated. Thanks for the information. I'll remember to never use sudo for graphical interface applications from now on. Better safe than very sorry.

/Mimsy

---

