---
title: "Various questions..."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by karni on 2007-04-29
ok, there's probably something I've already done inherently wrong here, but bear with me...

Basically, I've created a new user called 'guy' by doing
```
sudo groupadd guy
sudo useradd -g guy guy
```

Now doing this doesn't actually create a home directory for guy (ie /home/guy) so I've tried doing it with my login (the one set up originally). So essentially I've cd'd to /home. Using mkdir guy doesn't work, cos it says I don't have permission. Using sudo mkdir guy doesn't tell me there's anything wrong, but it doesn't create the directory either. (Also it doesn't actually ask for my password.)

What am I doing wrong?



Next question:
Should I later wish to make guy an admin (ie allow him to use sudo) is it simply a case of
```
sudo usermod -G admin guy
```
?



Final question:
I am going to be using SFTP to access the /var/www directory a lot. I generally use WinSCP for this. How do I tell WinSCP to tell my server that I'm an admin? At the moment I am being told 'access denied' for anywhere other than my home directory. Do I need to change the group that /var/www belongs to or something?


Anyway, thanks for helping, I've recently moved from running Apache on WinXP to Ubuntu, and am a bit intimidated by it all!


Edit: got one more, now I think about it! I've installed Ubuntu 7.04 Server Edition - does this by default only have a command line interface? Is it possible to install a GUI on it? Just it would be a little more user friendly (also responsibility for this system gets passed on to a new person once a year, and it's quite possible that next year's person will never have used linux or unix before, and will thus be completely bewildered by the command line!)

Thank you again

---

### Post by starcraft.man on 2007-04-29
Just a question, but you do know that there is a very well done gui for groups and users right?

System >Administration > Users and Groups.

Very easy to manager users there. To answer your second question in that, you can simply select a user from the gui and go to properties and limits its privileges (or grant them). 

As to the first question, I don't know the exact command you need to make that folder but I believe the gui would take care of it if you did it that way.

If btw you want this user to have a seperate partition for their folder, you'll need to use gparted to do that then set their folder in it.

EDIT: Wuups, just noticed you said at bottom you were running server... ignore what I say, I am no master of the server just a normal desktop person. >.<

---

### Post by starcraft.man on 2007-04-29
You might want to post [here]("http://ubuntuforums.org/forumdisplay.php?f=7") .

This section is mostly for desktop issues I believe, I'm sure some server admin on that subsection can help you, best of luck.

---

### Post by octoberdan on 2007-04-29
Use adduser over useradd (more on this: [http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/))

and sudo usermod -G admin <user> will make the user a sudoer

```

daniel@octobertop:/$ su joe
Password:
$ sudo ls
joe is not in the sudoers file.  This incident will be reported.
$ exit
daniel@octobertop:/$ sudo usermod -G admin joe
daniel@octobertop:/$ su joe
Password:
$ sudo ls
bin    dev   initrd      lib32       media  proc  share  tmp  vmlinuz
boot   etc   initrd.img  lib64       mnt    root  srv    usr
cdrom  home  lib         lost+found  opt    sbin  sys    var

```

---

### Post by CodeNosher on 2007-05-01
Help!!

I added myself to the dialout group and lost all my other groups!

I did this:

[INDENT][/INDENT]sudo usermod -G dialout jason

since that time I have not been able to sudo anything!  

When I ran id it looked fine.  Now that several minutes have passed when I run id I get this:

uid=1000(jason) gid=1000(jason) groups=20(dialout),1000(jason)

I seem to have lost everything!  I'm the only user.  How do I grant myself admin rights?!?

-Jason

---

