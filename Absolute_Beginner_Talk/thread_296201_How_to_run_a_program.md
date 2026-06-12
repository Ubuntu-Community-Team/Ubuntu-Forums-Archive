---
title: "How to run a program"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-09
Hi there.
I've downloaded TextStat2, which si a proram for information retrieval,
I's a source zip file; I've extracted it, but now I don't know hot to run it.
All the files have the py extension (python) apart form one which has pyw.

Any hint?:confused: 

Thanks

---

### Post by haxer on 2006-11-09
Hmm... unpack it and cd to it then do ./configure then make then sudo make install? :-k

---

### Post by Ben Sprinkle on 2006-11-09
```

sudo ./file.py

```
Not sure which is the main executable, try each one.

---

### Post by helphope on 2006-11-09
Thanks for answering

> **haxer said:**
> Hmm... unpack it and cd to it then do ./configure then make then sudo make install? :-k

I've extracted it: is that different form unpacking?
What do you mean with cd to it? Maybe that I have to use a cd? In any case I've got an internet connection.
:confused:

---

### Post by taurus on 2006-11-09
cd in this case means change directory...  If you want to move to another directory, you use the cd command, not the CD media thing!

```
cd Desktop
```

---

### Post by ner0tic on 2006-11-09
> **helphope said:**
> Thanks for answering



I've extracted it: is that different form unpacking?
What do you mean with cd to it? Maybe that I have to use a cd? In any case I've got an internet connection.
:confused:

cd as in ChangeDirectory

if the files were extracted to the directory named 'pythonMess' then you would type > cd pythonMess

---

### Post by Ben Sprinkle on 2006-11-09
If it's a bunch of py files do what I said, ubuntu has the python interpreter installed so just do:
```

cd <<dir>>
sudo ./file.py

```

---

### Post by helphope on 2006-11-09
OK
I've tried it; went on the directory wehre I've extracted the files and the sudo ./xxx.py (pyw) command, but I got a "command not found.

:confused:

---

### Post by bsussman on 2006-11-09
Generally python packages do not get built the way compile-only-language packages do.

The mainline is the pyw file so:

```
python xxxxx.pyw
```

---

### Post by zekopeko on 2006-11-09
why don't you do this so that we may have a look at what you have:

cd to the directory
then do this: ls -al
and then just copy & paste everything that shows after that command here in a post

---

### Post by bsussman on 2006-11-09
> **Goat Spirit said:**
> If it's a bunch of py files do what I said, ubuntu has the python interpreter installed so just do:
```

cd <<dir>>
sudo ./file.py

```

No - you use sudo when you need root privs.  Using it on an otherwise unknown program is not very clever.

---

### Post by helphope on 2006-11-09
Thanks for your patience

:~/Intenet/Textstat2/TextSTAT2-source.zip_FILES$ ls -al
total 180
drwxr-xr-x 3 ab ab  4096 2006-11-09 13:48 .
drwxr-xr-x 3 ab ab  4096 2006-11-09 13:48 ..
-rw-rw-rw- 1 ab ab  1783 2005-10-10 20:52 ConvertText.py
-rw-rw-rw- 1 ab ab  8943 2005-10-10 21:35 History.txt
drwxr-xr-x 2 ab ab  4096 2006-11-09 13:48 Images
-rw-rw-rw- 1 ab ab 14729 2005-10-10 20:52 Korpus.py
-rw-rw-rw- 1 ab ab 29052 2005-10-10 21:35 LangOpt.py
-rw-rw-rw- 1 ab ab  1178 2004-08-17 19:24 License.txt
-rw-rw-rw- 1 ab ab 11684 2004-05-05 11:19 MultiListBox.py
-rw-rw-rw- 1 ab ab  2128 2003-09-01 18:20 News2Korpus.py
-rw-rw-rw- 1 ab ab  3689 2003-09-23 12:49 ProgressBar.py
-rw-rw-rw- 1 ab ab  1009 2003-09-23 12:52 StatusBar.py
-rw-rw-rw- 1 ab ab  4560 2004-06-25 09:50 TabPage.py
-rw-rw-rw- 1 ab ab 49768 2005-10-10 20:52 TextSTAT.pyw
-rw-rw-rw- 1 ab ab  2598 2003-09-01 11:36 ToolBar.py
-rw-rw-rw- 1 ab ab  4317 2005-08-02 21:26 Web2Korpus.py

---

### Post by helphope on 2006-11-09
OK. I've got it.
Thanks again:D

---

### Post by Ben Sprinkle on 2006-11-09
> **bsussman said:**
> No - you use sudo when you need root privs.  Using it on an otherwise unknown program is not very clever.

It is obviously known if **he downloaded it!**.

---

### Post by bsussman on 2006-11-09
> **Goat Spirit said:**
> It is obviously known if **he downloaded it!**.

Excuse me, he has not yet ever run it on his system otherwise he would not be here  :)

How about a more basic principle:  Never run a program using higher privs than necessary.

---

### Post by Ben Sprinkle on 2006-11-09
Why?

---

### Post by bsussman on 2006-11-09
> **Goat Spirit said:**
> Why?
Because the less privs you have at any given point, the less chance you will accidentally do something inappropriate.

Also, since most things do not require high privs, if you run into a situation where you think you need higher privs that expected, it is a good signal that you may have done something incorrectly.

Thes are some of the principles of prudent system management.

They (among others) led the designers to segregate admin privs a little more thoroughly in ubuntu distributions.

---

### Post by Ben Sprinkle on 2006-11-09
That was sarcasim. I know why.
I am in a bad mood so sorry.

---

### Post by bsussman on 2006-11-09
> **Goat Spirit said:**
> That was sarcasim. I know why.
I am in a bad mood so sorry.

:KS - I would have triple the number of posts except I erase 2/3 of them instead of clicking the Submit button...

---

### Post by Ben Sprinkle on 2006-11-09
What's that have to do with anything?

---

### Post by Blutack on 2006-11-09
He means the frustrated posts that you read through just before posting and then think hmm...maybe not.

---

### Post by bsussman on 2006-11-09
> **Blutack said:**
> He means the frustrated posts that you read through just before posting and then think hmm...maybe not.

It is very hard to read tween the lines in a forum - it is one of the issues with communication in written form only.  I used to think that smilies were stoopid - I don't any longer, since they are the only way I know to soften posts sufficiently in many cases.

Since intent and attitude are so hard to read, I have learned to attempt to be totally without them in the words, and if attitude is needed, to attempt it only with little colored doofuses :-D

This usually works.

---

### Post by Ben Sprinkle on 2006-11-10
I don't get you, you need glasses or something to read between the lines on this forum?

---

