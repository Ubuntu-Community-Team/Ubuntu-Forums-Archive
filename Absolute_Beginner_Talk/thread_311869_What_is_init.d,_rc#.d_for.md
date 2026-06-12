---
title: "What is init.d, rc#.d for?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by gejr on 2006-12-03
Can anyone please explain me in a human understandable way the difference between init.d and the different rc#.d's ? It's been nagging me for a while. Apparantly it allows me to run things during boot, but I don't see the reason why I would need so many of these:) I have rc0,1,2,3,4,5,6 and rcS.d + that init.d-directory.

I just read somewhere that I should put some symbolic links in rc2.d to make lampp run on startup. It worked perfectly, but I don't quite understand why...what would happen if I put the links in rc1.d or init.d++ ?
:)

---

### Post by dbott67 on 2006-12-03
This article may help.

[http://www.linux.com/article.pl?sid=06/01/03/1728227](http://www.linux.com/article.pl?sid=06/01/03/1728227)

-Dave

---

### Post by Shatrat on 2006-12-03
I can partially answer your question.  The numbers stand for different runlevels.  0 is off and 6 is restart.  3 is command line only, but multi user with networking.  5 is graphical environment, multi user, networking, basically the normal state for ubuntu.

As for where the appropriate places to put the links is, I'm not so clear on what is appropriate.  For most user applications that you want to run on startup you can just simply add them to the startup of your gnome session in System -> Prefs -> Sessions.  If it's some kind of server or something then it might be better after all to put it in rc2

---

### Post by johnnymac on 2006-12-03
Okay - explain in human...hmmm I'll try :)

So init.d and the rc(X).d files are initialization scripts.  There are several different initialization levels (hence the rc2.d, rc3.d, etc).  So, depending on when you want a specific script or service (daemon) to run during initialization you throw that entry into the respective init script.  

From the man pages of init.d

```

     /etc/init.d is a  directory  containing  initialization  and
     termination scripts for changing init states.  These scripts
     are linked when appropriate to files  in  the  rc?.d  direc-
     tories, where `?' is a single character corresponding to the
     init state.  See init(1M) for definitions of the states.

     File  names  in  rc?.d   directories   are   of   the   form
     [SK]nn<init.d  filename>,  where  S  means start this job, K
     means kill this job, and nn is the relative sequence  number
     for killing or starting the job.

     When entering  a  state  (init  S,0,2,3,etc.)  the  rc[S0-6]
     script  executes  those  scripts in /etc/rc[S0-6].d that are
     prefixed with K followed by those scripts prefixed  with  S.
     When  executing  each  script  in  one  of the /etc/rc[S0-6]
     directories, the /sbin/rc[S0-6] script passes a single argu-
     ment.   It  passes  the argument 'stop' for scripts prefixed
     with K and the argument 'start' for scripts prefixed with S.
     There  is  no  harm  in applying the same sequence number to
     multiple scripts.  In this case the order  of  execution  is
     deterministic but unspecified.

     Guidelines for selecting sequence numbers  are  provided  in
     README  files  located in the directory associated with that
     target state. For example,  /etc/rc[S0-6].d/README.  Absence
     of a README file indicates that there are currently no esta-
     blished guidelines.

     ...

     Assume the file /etc/init.d/netdaemon is a script that  will
     initiate networking daemons when given the argument 'start',
     and will terminate the daemons if given the argument 'stop'.
     It    is   linked   to   /etc/rc2.d/S68netdaemon,   and   to
     /etc/rc0.d/K67netdaemon.   The   file   is    executed    by
     /etc/rc2.d/S68netdaemon  start  when init state 2 is entered
     and by /etc/rc0.d/K67netdaemon stop when shutting the system
     down.

```

Hope this helps your understanding some.

---

### Post by gejr on 2006-12-03
Thank you very much for your explanations..helped me a lot! :KS

---

