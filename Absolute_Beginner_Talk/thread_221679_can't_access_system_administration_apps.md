---
title: "can't access system administration apps"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by navy_doc on 2006-07-23
I just installed Ubuntu, and it seems to be working fine, however I cannot access any of the applications under system>adminstration...  

I am the only user ever set up, so my password should give me administrator privelages I believe?? in the etc/group file, I am indeed shown as an adminstrator, but when I click any of the adminstrator apps, I get the 'spinning dial' for a few seconds, and 'starting administrative application' on the bottom bar, which then dissapears after a few seconds, with no application starting, and no messages of any kind...

Any suggestions would be welcome. (I have never used anything other than windoze and dos, so please be gentle... :-)

---

### Post by RJARRRPCGP on 2006-07-23
This is a bug. It randomly fails to give a password prompt, hangs then disappears.

Now that reminds me of Windows when it's having a bad day! :(

---

### Post by Iandefor on 2006-07-23
> **navy_doc said:**
> I have never used anything other than windoze and dos, so please be gentle... :-) It's a rare Linux user that didn't come from somewhere else :).

RJARRRPCGP's probably correct when he says it's a bug.

RJARRRPCGP: Is it filed in Launchpad? I can't find it.

---

### Post by navy_doc on 2006-07-23
OK, is there a solution/patch/work-around? It has now done it 12 times in a row! And yes, I have loged-out and in again, restarted, including a shut-down and wait, all with the same symptom on restart...](*,)

---

### Post by Iandefor on 2006-07-23
> **navy_doc said:**
> OK, is there a solution/patch/work-around? It has now done it 12 times in a row! And yes, I have loged-out and in again, restarted, including a shut-down and wait, all with the same symptom on restart...](*,) Might be a problem with sudo. Run > sudo ls in a terminal and see what it does.

---

### Post by navy_doc on 2006-07-23
rob@:~$ sudo ls
sudo: unable to lookup  via gethostbyname()
rob@:~$

---

### Post by ubuntu-geek on 2006-07-23
Give this thread a read it should help you to resolve the issue.

[http://ubuntuforums.org/showthread.php?t=78324](http://ubuntuforums.org/showthread.php?t=78324)

---

### Post by Iandefor on 2006-07-23
It looks like you have no hostname. That in itself is a problem.
What's the output of ```
cat /etc/hostname
```

EDIT: Ubuntu-Geek got there first, and it looks like his will help.

---

### Post by navy_doc on 2006-07-23
rob@:~$ cat /etc/hostname
-HOME-
rob@:~$

So my hostname appears to be OK....

---

### Post by navy_doc on 2006-07-23
OK, you just gave the monkey a torque wrench! I am A Windows user, this stuff means very little to me. Type an enquiry into the terminal and report the output I can do, follow a string of linux/unix type command-line parameters and network configuration settings eh, no...

---

### Post by shongzah on 2006-08-09
I'm having the same problem.  I was fooling around with the Networking settings (trying to see if my neighbors wireless was secured).  Afterwards my stuff doesn't work.

sudo ls returns the same error

cat/etc/hostname returns No such file or directory

My terminal prompt is laptop@(none):~$.  I do not remember what it was before but not that.  Like laptop@home maybe.

like navy_doc, I am a linux rookie (from OS X) and have very little familiarity with the commandline stuff.  I can do it, but good step-by-step instructions would be awesome.

---

### Post by don_m on 2006-08-26
So what the solution? 

This happened on my desktop machine the first time it was installed and ended up reinstalling Ubuntu 6.06.

This has now happened to my laptop installation?

When I switch to another network access on my laptop (ethernet, wireless, or modem), I end up having to delete some of the DNS pickups and other info for a new connection to work.

I'm glad the modem will work on my IBM T23 laptop, but stuff like the problem of this post topic is why Linux will not make inroads to the average desktop user.

So, why does this happen, and what can be done to fix it?

---

### Post by don_m on 2006-09-06
Okay, here is what worked for me. I used this thread 
[http://ubuntuforums.org/showthread.php?p=1470515#post1470515](http://ubuntuforums.org/showthread.php?p=1470515#post1470515)
as what had helped me originally.

I tried to add more detail:

1. Choose recovery mode when booting.
2. Should indicated root at the command line. At command line, type "vi /etc/hosts"
3. Press Insert on keyboard, and enter "127.0.0.1 IBMT23" (substitute your hostname for IBMT23)
4. Press escape.
5. Vi editor works with a ":" command, so type ":wq".
6. File should be saved 'w' and quit 'q' vi. Type exit to login.
7. You should now be able to access "Network Adminstration" as well as the avoiding the sudo gethostbyname error.:-D 

[http://www.eng.hawaii.edu/Tutor/vi.h](http://www.eng.hawaii.edu/Tutor/vi.h)

---

### Post by eschreib on 2006-09-08
I'm having the same issue, and even if I go into the recovery consul as 'su' I can not copy into the etc/ directory.
vi will not let me save there either.
Any ideas?

---

