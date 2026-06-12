---
title: "&quot;too many open files&quot;  WTH?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Boondock5 on 2007-10-27
I was copying mp3 files to a flash drive,(w/only minimal trouble out of that damn windows based flash drive crap thing) after about 30 song transfers, I get the "Too many open files" thing and everything as far as apps went into slow motion.

So now, forward to today, everything running slightly slower than usual, (This thing screams with Ubuntu on it) and it doesn't want to play music( it will, but the video effects thing doesnt work from Movie player(Totem.)

I've been reading everywhere about this "too many open files" thing and no one seems to have a fix for it in Ubuntu. Am I just missing something?

---

### Post by Martje_001 on 2007-10-27
How much free space do you've got on you hard drive?

---

### Post by Boondock5 on 2007-10-27
> **Martje_001 said:**
> How much free space do you've got on you hard drive?

51.8 gigs, plenty if someone were to ask me, but what do I know?

---

### Post by Boondock5 on 2007-10-27
And how do I edit this;    ulimit -n
1024
Thats the number that hat needs to be changed to some ungodly high amount, along with the Maximum quantity number

---

### Post by CaptainInsaneO on 2007-10-27
This is caused by a single app, do you happen to know which one it is?

Edit: Sorry, didn't see your previous post. You can edit that by doing this:

Set your root pass in a terminal session, then type su.

Now type ulimit -n 64000 or some crazy high number like that.

---

### Post by Boondock5 on 2007-10-27
> **CaptainInsaneO said:**
> This is caused by a single app, do you happen to know which one it is?

I think it was  "Totem" or "Movie player"

---

### Post by Boondock5 on 2007-10-27
I feel like such an Idiot, I can't get the command thing to work

check this out,
boondock5@boondock5:~$ my /etc/init.d,
bash: my: command not found
boondock5@boondock5:~$ file-max
bash: file-max: command not found
boondock5@boondock5:~$ /etc/security/limits.conf 
bash: /etc/security/limits.conf: Permission denied
boondock5@boondock5:~$ ulimit -n
1024
boondock5@boondock5:~$ sudo /etc/security/limits.conf 
[sudo] password for boondock5:
sudo: /etc/security/limits.conf: command not found
boondock5@boondock5:~$ su ulimit -n 1000000
su: invalid option -- n
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

boondock5@boondock5:~$ sudo ulimit -c 1000000
[sudo] password for boondock5:
sudo: ulimit: command not found
boondock5@boondock5:~$ sudo ulimit -n 100000
sudo: ulimit: command not found

---

### Post by CaptainInsaneO on 2007-10-27
Ok, I apologize. My instructions were actually a little vague, do this exactly in this order in terminal:

```
sudo passwd
```

Then, type in your pass for sudo, and then type in a password for your root account. It will ask twice. Do NOT forget this password - ever.

Now type
```
su
```
to switch to your root account, use the new password if it asks.

Then, type the following:
```
ulimit -n 20048
```

Everything should be golden now. To see if it stuck, type
```
ulimit -a
```

and look for "Open Files" on the left side.

Hope this helps!

---

### Post by Boondock5 on 2007-10-27
here is what happened

boondock5@boondock5:~$ sudo passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
boondock5@boondock5:~$ su
Password: 
root@boondock5:/home/boondock5# ulimit -n 20048
root@boondock5:/home/boondock5# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 8191
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 20048
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 8191
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited




I saw the "open files thing matched, so right on! thank you so much. I know what it's like dealing with people who hav'nt a clue... I train new Aircraft Electricians. Thanks again!

---

### Post by CaptainInsaneO on 2007-10-27
My sympathies, for sure. lol My girl's dad is an aircraft mechanic. He HATES new people.

Post back here if you have any more problems, but I'm pretty sure this should take care of it.

---

### Post by hanzomon4 on 2007-10-27
> **CaptainInsaneO said:**
> Ok, I apologize. My instructions were actually a little vague, do this exactly in this order in terminal:

```
sudo passwd
```

Then, type in your pass for sudo, and then type in a password for your root account. It will ask twice. Do NOT forget this password - ever.

Now type
```
su
```
to switch to your root account, use the new password if it asks.

Then, type the following:
```
ulimit -n 20048
```

Everything should be golden now. To see if it stuck, type
```
ulimit -a
```

and look for "Open Files" on the left side.

Hope this helps!

Thanks, I was getting the "too many files open" thing as well. However you don't have to enable the root account to get this to work. Just do ```
sudo -i
```

---

### Post by CaptainInsaneO on 2007-10-27
> **hanzomon4 said:**
> Thanks, I was getting the "too many files open" thing as well. However you don't have to enable the root account to get this to work. Just do ```
sudo -i
```

I didn't know you could do that, thanks for the tip!

---

