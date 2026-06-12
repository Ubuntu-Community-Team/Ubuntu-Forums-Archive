---
title: "AntiVirus- safe to install as root?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-06-25
After reading many posts on whether or not AntiVirus software is necessary, and understanding that it may have its place, I decided to install KlamAV (Running XUBUNTU Feisty).

As part of the installation it warned me that I was ¨about to install software that can´t be authenticated¨  and that ¨doing this might allow a malicious individual to take control...¨

Of course, I´m new and paranoid, but it seemed to be from Ubuntu, so I continued, with trepidation.   Then, when I tried to run it, it says I don´t have virus definitions.  OK.  But instructs me to install them as ¨root¨.  

Is this safe?  It seems like I might be in over my head.

Ultimately, I am trying to scan the files on an external hard drive given to me by a windows user with the warning that it was removed from an infected old computer.   I want to recover some photos/personal files from it.  

I´ve been reading these forums and stuff like 
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

and still learning how much I don´t know...

---

### Post by p_quarles on 2007-06-25
The safest way to make sure you virus definition files are up to date is to open a terminal and type ```
sudo freshclam
```

You don't really have to worry about the authentication message, though. If the external HDD has Windows viruses on it, they still won't be able to do anything to the Linux file system. Just don't e-mail those files to anyone until you're sure they're clean.

---

### Post by zmike1 on 2007-06-25
Thank you. 
What does the switch -v do?  The program suggested running freshclam -v as root.

---

### Post by p_quarles on 2007-06-25
That would run it in "verbose" mode, which means it would report what it's doing while it's doing it. Go ahead and do that -- it won't hurt anyting. 

FYI, you can get information on command line options by typing ```
man {command}
```
That will bring up the manual for most commands.

---

### Post by zmike1 on 2007-06-25
Thanks again.
 tried sudo freshclam -v and it typed some stuff and ended with a comment that my version was not the latest.  

Then I tried sudo apt-get install clamav and (apparently) got the latest version. (?)
Then back to sudo freshclam - v   and I get the warning that I don´t have the latest version.

Ignoring all of this text, when I try to run clamav anyway,  Applications --> virus scanner, 
I get the error: You do not appear to have virus definitions!
Running "freshclam -v" as root may fix the problem.

It seems to be stuck.  or at least I am...

---

### Post by p_quarles on 2007-06-25
It will say "out of date" at the beginning of the process. After that it should say: ```
main.cvd is up to date (version: 43, sigs: 104500, f-level: 14, builder: sven)
daily.inc is up to date (version: 3523, sigs: 25782, f-level: 16, builder: sven)
```

If those messages came up, your definitions files should be up to date.

---

### Post by zmike1 on 2007-06-25
Cool.  It did that.  Perhaps the definitions are up to date but the version is old.  It says 0.92 vs. the current of 0.93.  Might that be causing the problem?  I´m assuming I don´t need to reboot.  Is that correct?

BTW, how do you get those ¨screenshots¨ copied and pasted to the forum?

---

### Post by cogadh on 2007-06-25
> **zmike1 said:**
> BTW, how do you get those ¨screenshots¨ copied and pasted to the forum?
If you mean the "Code:" stuff, he's using the CODE forum function. Just do this when typing your post:
{code}blah blah blah{/code}
Except change the "{ }" brackets to "[ ]".

---

### Post by p_quarles on 2007-06-25
> **zmike1 said:**
> Cool.  It did that.  Perhaps the definitions are up to date but the version is old.  It says 0.92 vs. the current of 0.93.  Might that be causing the problem?  I´m assuming I don´t need to reboot.  Is that correct?

BTW, how do you get those ¨screenshots¨ copied and pasted to the forum?
No, it's just telling you (at the beginning) that your previous definitions were out out of date. The last two lines are confirming that it has downloaded the current definitions.

---

### Post by zmike1 on 2007-06-25
Thank you.
When I run ClamAV, I get errors such as ¨unable to view clamAV information file...¨  and  ¨it appears virus definition files are out of date¨

Sorry for being so dense on this.  Perhaps it doesn´t work right on Xubuntu??

---

