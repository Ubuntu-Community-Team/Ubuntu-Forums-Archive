---
title: "Automatix2 Destruction...."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by rabideau on 2007-06-15
[FONT=Helvetica, Arial, sans-serif]Can anyone help me out?  I installed (actually failed at installing) Automatix2 on feisty using the line by line method. Now synatpic and my auto install (Add/Remove) do not work.  I get the following errors and have no idea how to fix things.  

_**Add/Remove Error:**_
*This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. *[I tried this and it didn't work]

_**Synaptic Error:**_
[I]E: Type '“deb' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

Can you help me out???
[/FONT]

---

### Post by Azakus on 2007-06-15
Looks like automatix2 was broken. Run this command.
```
sudo apt-get check
```
It will attempt to fix what the automatix2 install broke, then you can install automatix2 again.
If that doesn't work, do this
```
sudo aptitude purge automatix2
```
then try installing automatix again.

---

### Post by rabideau on 2007-06-15
Thank you...

So here's what ended up fixing things:

I went to  /etc/apt/sources.list (backed th file up)
I then edited sources.list to remove two "deb" strings
I finally reinstalled automatrix2 using the *.deb download.  All is now in good repair.

---

### Post by diatribe on 2007-06-15
you should really consider other routes than automatix, it does not do anything that you can not do yourself with a little more effort and saves you from problems like this

---

### Post by rabideau on 2007-06-15
I am sure you are right... my problem is I keep looking for nice gui items to save me from typing in terminal mode.  I'm getting over it though.;)

---

### Post by zero244 on 2007-06-15
I would go to the Automatix web site and download the Deb file and install that way. Thats how Ive always installed it and have had no problems.

---

### Post by arnieboy on 2007-06-15
> **rabideau said:**
> [FONT=Helvetica, Arial, sans-serif]Can anyone help me out?  I installed (actually failed at installing) Automatix2 on feisty using the line by line method. Now synatpic and my auto install (Add/Remove) do not work.  I get the following errors and have no idea how to fix things.  

_**Add/Remove Error:**_
*This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. *[I tried this and it didn't work]

_**Synaptic Error:**_
[I]E: Type '&#8220;deb' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

Can you help me out???
[/FONT]
Before you think about automatix "destroying" anything, you need to learn how to copy and paste commands in terminal (if you cant copy and paste correctly, linux will frustrate you).
As a small exercise. post the results of the following:
```
cat /etc/apt/sources.list
```

---

### Post by rabideau on 2007-06-15
Just as an aside... there was nothing in my post indicating that your software caused the failure.  I took responsibility for the error.

Demeaning comments like yours should be avoided in polite company.

---

### Post by arnieboy on 2007-06-15
> **rabideau said:**
> Just as an aside... there was nothing in my post indicating that your software caused the failure.  I took responsibility for the error.

Demeaning comments like yours should be avoided in polite company.

hmm.. wasnt trying to be demeaning.. you pasted one command wrongly leading to your sources.list getting broken (one repo has double quotes).
do you still need help fixing your sources.list? if you do.. you might want to post the results of the command I posted.

---

### Post by rabideau on 2007-06-15
Thanks ... as I have noticed with Linux it turns out there are more ways to fix a problem than I am used to (I'm a 25+ years Windoze user).  I have everything repaired and in good working order.

I just love this Linux thing...;)

---

### Post by carusoswi on 2007-06-16
> **rabideau said:**
> Just as an aside... there was nothing in my post indicating that your software caused the failure.  I took responsibility for the error.

Demeaning comments like yours should be avoided in polite company.

Just an aside - your choice of topic titles led to the "demeaning comment."

. . . but, it's ok, we're all friends here.

Caruso

---

