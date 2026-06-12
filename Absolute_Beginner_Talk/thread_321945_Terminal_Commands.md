---
title: "Terminal Commands"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-12-19
In trying to edit my ?etc/X11/org.conf file I opened a monitor and typed and got this response:
steve@steve-laptop:~$ gksudo gedit ?etc/X11/xorg.conf
(gedit:5162): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


but the gedit app opened and i am able to edit it. what exactly does this message mean?

---

### Post by jvc26 on 2006-12-19
Not exactly sure am afraid just ran the same command through my terminal to check and it spat out a very similar error - doesnt have an effect on your ability to edit the file though.
Il

---

### Post by bodhi.zazen on 2006-12-19
LOL second time this has been asked today.

It is a warning often seen just prior to total system failure.

Just kidding ;)

It is a known bug and is otherwise meaningless :p

---

### Post by jvc26 on 2006-12-19
Must've missed the first time lol. I'd dismissed it as meaningless after the 500th time it popped up at me to no effect :) nice to know its just a forerunner to oblivion to my kernel ;)
Il

---

### Post by Stephen47 on 2006-12-20
also how come sometimes I type in a sudo command and after I enter my password the terminal just returns to the prompt with nothing having happened?

---

### Post by riven0 on 2006-12-20
> **Stephen47 said:**
> also how come sometimes I type in a sudo command and after I enter my password the terminal just returns to the prompt with nothing having happened?

Well, what commands are you running? Sometimes if you do a sudo apt-get clean, sudo dpkg --configure -a and others, it will not return anything. Happens to me all the time.

---

### Post by bodhi.zazen on 2006-12-20
> **Stephen47 said:**
> also how come sometimes I type in a sudo command and after I enter my password the terminal just returns to the prompt with nothing having happened?

In Linux the default behavior is no output to a terminal unless there are errors.

---

### Post by Stephen47 on 2006-12-22
So when I back up a file and it returns to the prompt I can assume it was succesful? How come then when I tried to use a backed up file I got a message that the file didn't exist? I ran this command: "sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf"

---

### Post by yabbadabbadont on 2006-12-22
You can check the errorcode that was returned by the command by immediately running "echo $?" right after the command.  It should be zero if there were no error.

---

### Post by Bachstelze on 2006-12-22
> **Stephen47 said:**
> So when I back up a file and it returns to the prompt I can assume it was succesful? How come then when I tried to use a backed up file I got a message that the file didn't exist? I ran this command: "sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf"

Yes. And if you got an error saying the file doesn't exist, you should check if the file exists ;)

---

