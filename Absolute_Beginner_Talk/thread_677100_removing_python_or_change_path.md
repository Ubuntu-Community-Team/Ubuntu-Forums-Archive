---
title: "removing python or change path"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by seventhc on 2008-01-24
I was having a problem running an older program so I installed python-1.5.2...now when I start up python from the terminal it is starting the 1.5 instead of 2.5.
I couldn't find it in synaptic, and sudo apt-get remove python-1.5.2, didn't work either, so how would I go about removing it or if I keep it, what do I do to reset the path back to python-2.5.1??
I think I can do something in my ~/.bashrc but I don't see anything in there referencing the PYTHONPATH and if I do need to add it, what exactly should I put in.
thanks in advance.

---

### Post by emarkd on 2008-01-24
try this
```

sudo update-alternatives --list python
```

not sure, but maybe that'll be what you're looking for

---

### Post by seventhc on 2008-01-24
> **emarkd said:**
> try this
```

sudo update-alternatives --list python
```not sure, but maybe that'll be what you're looking for
Thanks for the quick reply, I ran the command you suggested and the output was this.
No alternatives for python. :confused: I would think there should be though since i have 1.5, 2.4, and 2.5 installed.

---

### Post by emarkd on 2008-01-24
update-alternatives only tracks some packages.  You'll have to update the symbolic link yourself.  If you cd to /usr/bin and do
```

ls -al | grep python
```

You'll probably find that python is a symbolic link to some other binary, like Python1.4 (or whatever).  You'll have to remove that link and create a new symbolic link to python2.5.  Like this:

```
sudo ln -s python2.5 python
```

Hope that helps.

---

### Post by seventhc on 2008-01-24
I did that, I didn't see anything listing python1.5, I ran the second command anyway, but it's still points to 1.5

---

### Post by emarkd on 2008-01-24
I'm sorry if my post was confusing.  I meant the python1.5 as a generic example.  When I run

```
sudo ls -l | grep python
```

from my /usr/bin directory, I see this as part of my output:

lrwxrwxrwx  1 root   root                 9 2008-01-24 14:33 python -> python2.5
-rwxr-xr-x    1 root   root     1026796 2007-10-04 18:03 python2.4
-rwxr-xr-x    1 root   root     1158452 2007-10-05 10:17 python2.5

I can see from this that the file python actually points to python2.5.  We call that a symbolic link.  Notice that python2.5 is also listed there as a binary.  That means that when I run "python", linux actually runs python2.5.  I could remove (or rename) "python" to something else and then run

```
sudo ln -s python2.4 python
```

and after that python will point to python2.4 instead and anytime I type python, linux will actually run python2.4.

To apply this to your situation, make sure you've got a file there called python2.5, then remove (or rename) your file called "python", then you can do:
```

sudo ln -s python2.5 python
```

to point a file called python to the binary python2.5.

Maybe that makes sense...

---

### Post by seventhc on 2008-01-24
> **emarkd said:**
> I'm sorry if my post was confusing.  I meant the python1.5 as a generic example.  When I run

```
sudo ls -l | grep python
```from my /usr/bin directory, I see this as part of my output:

lrwxrwxrwx  1 root   root                 9 2008-01-24 14:33 python -> python2.5
-rwxr-xr-x    1 root   root     1026796 2007-10-04 18:03 python2.4
-rwxr-xr-x    1 root   root     1158452 2007-10-05 10:17 python2.5

I can see from this that the file python actually points to python2.5.  We call that a symbolic link.  Notice that python2.5 is also listed there as a binary.  That means that when I run "python", linux actually runs python2.5.  I could remove (or rename) "python" to something else and then run

```
sudo ln -s python2.4 python
```and after that python will point to python2.4 instead and anytime I type python, linux will actually run python2.4.

To apply this to your situation, make sure you've got a file there called python2.5, then remove (or rename) your file called "python", then you can do:
```

sudo ln -s python2.5 python
```to point a file called python to the binary python2.5.

Maybe that makes sense...\
It shows as if it is pointing correctly.
```
lrwxrwxrwx  1 root root      9 2007-01-24 15:17 python -> python2.5
```
or do I remove that and recreate the symbolic link since it isn't working?

---

### Post by seventhc on 2008-01-24
I am at a loss, if I go to /usr/bin 'python' has an arrow on it and in properties it says (Type:  link to executable)
( Link target: /usr/bin/python2.5)
I don't even see python 1.5 in there, but it still starts up if I try to start it from the terminal. The only place I see a python1.5 is in /usr/local/lib
can I just delete that folder???


(that doesn't work either...I put it back :D)

---

### Post by seventhc on 2008-01-24
*bump*

---

### Post by emarkd on 2008-01-24
two things to try:

1.  See what you're actually running when you type 'python' by running

```
which python
```


2.  See if you can run python2.5 from the shell by running

```
python2.5
```

---

### Post by seventhc on 2008-01-24
if I type python at the terminal I get Python 1.5.2

I can run it from the shell if I type python2.5 but if I just type python it runs the older version. I use vim and have it set up so the <F2> key runs the program, but now it's going to run it in python1.5 instead (causing errors most likely)

From the terminal I can run 2.4 and 2.5 by adding the number but I'd really like 2.5 to be the default version.

---

### Post by emarkd on 2008-01-24
So did you run

```
which python
```

so that we can see what the full path is to whatever is executing when you type 'python'.  That'll give us a direction to go since you say that /usr/bin/python points to /usr/bin/python2.5 already.

---

### Post by seventhc on 2008-01-24
> **emarkd said:**
> So did you run

```
which python
```so that we can see what the full path is to whatever is executing when you type 'python'.  That'll give us a direction to go since you say that /usr/bin/python points to /usr/bin/python2.5 already.
oh I think I read it wrong..sorry

the full path that shows is
/usr/local/bin/python

---

### Post by emarkd on 2008-01-24
So lets cd into /usr/local/bin and do an

```
ls -l | grep python
```

to see where that points.  I bet it's a symbolic link to some python1.4 or something somewhere else.  If it is, you can just remove (or rename) it and recreate it using

```
sudo ln -s /usr/bin/python2.5 python
```

---

### Post by seventhc on 2008-01-24
I get this output
-rwxr-xr-x 2 root root 1755671 2007-01-24 11:18 python
-rwxr-xr-x 2 root root 1755671 2007-01-24 11:18 python1.5
 do I have to remove it first? If so, how so?


---

### Post by emarkd on 2008-01-24
If python is not a symbolic link, I'd take the safe route and just rename it so that you could restore it if something goes wrong:

```
sudo mv python python.bak
```

or something like that.  'mv' stands for move, but that's how you rename things in Linux.  

That may be enough for Linux to start finding the other link that is under /usr/bin/python.  Try it and see.  If it still doesn't work, you can create a new symbolic link in this directory using

```
sudo ln -s /usr/bin/python2.5 python
```

---

### Post by seventhc on 2008-01-24
I tried that, but then when I ran python it said 
bash: /usr/bin/python: No such file or directory
I then renamed it from python.bak to python, then back to same situation.
can i just move the python executable from /usr/local/bin to /usr/bin???
And maybe delete the python1.5?

---

### Post by emarkd on 2008-01-24
Did you enter the last set of commands I gave you in /usr/bin or /usr/local/bin?  I was intending for you to rename /usr/local/bin/python to /usr/local/bin/python.bak so that linux would then hopefully find /usr/bin/python which is a symbolic link to /usr/bin/python2.5.  If that is indeed what you did, did you at some point remove /usr/bin/python?  I thought you had it earlier.

---

### Post by seventhc on 2008-01-24
I did as you said, I think I may have messed something up earlier before when I was messing with it before i posted back here. I'll try again tomorrow, going to sleep now.
Thanks so much for your help, I hope your here tomorrow :D
I'm considering removing python all together then just reinstalling the gnome-desktop..not sure if thats so good to do though or if it would even work.

---

### Post by emarkd on 2008-01-24
I'll be around and I'll be sure to check this thread.  I think we're really close to solving this one :)  Don't get too hasty and start randomly removing packages, especially not your gnome-desktop.  I'm pretty sure python doesn't require that one, so it would not help at all and would probably leave you with a bunch of other problems.

---

### Post by seventhc on 2008-01-24
I got it back..so now I run 'which python' i get /usr/bin/python
the file in /usr/local/bin is renamed to python.bak
I created the symbolic link
but still giving me python1.5...
just an update before i go to sleep. :)
Thanks again.

---

### Post by seventhc on 2008-01-25
I tried setting this in my ~/.bashrc
```
set PYTHONPATH=/usr/bin/python2.5
```
but no luck.
Now when I do 
```
ls - | grep python
```
i get this
```
lrwxrwxrwx 1 root    root      9 2008-01-24 18:30 exec_python2.5 -> python2.5
lrwxrwxrwx 1 root    root     18 2008-01-24 21:26 python -> /usr/bin/python2.5
lrwxrwxrwx 1 root    root      9 2007-01-24 15:55 python.bak -> python2.5
```
that first line was something I tried. earlier.

---

