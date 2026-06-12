---
title: "This script wont run in a terminal window - why?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by ceejay on 2007-12-24
Hello 

Heres a little script that is driving me nuts.  It was a lot longer and did actually do something, but I've reduced it to the basics to show the problem.  What I want to be able to do is run this script in a window of its own: I can do that either by setting up a launcher, or double-clicking in the file browser and selecting "run in terminal".

```

# !/bin/sh
function conv()
{
	echo Message One
}

echo Message Two
sleep 5
conv Parameter
echo finished
sleep 5

```

My problem is that if I do that, a window flashes very quickly and immediately disappears, so I can't see what error it is presumeably reporting. You'll note there is a "sleep" so it really should be waiting a while...

The odd thing is that if I run the same script from a command line within an existing window it runs fine.

The REALLY odd thing is that if I comment out the lines that declare the function (and change the function call to an echo so it doesn't barf on that error), it runs fine either way.

So what is different about the environment between running from a command line and running in a fresh terminal? What could this possibly have to do with a function declaration?

Please help... !!

I'm on Ubuntu 7.10

---

### Post by ceejay on 2007-12-24
OK, I got it.

The extra space in the first line between the # and the ! means that the forcing of shell type isn't working.

Just as well, because the function syntax isn't valid in /bin/sh

If I force properly to /bin/sh then it fails both times.

If I force it properly to /bin/bash then it works both times.

The default shell when opening a new window must be /bin/sh.

I do wonder what the right function syntax might be in /bin/sh, but life's too short to worry too much !

---

### Post by nick_h on 2007-12-24
> I do wonder what the right function syntax might be in /bin/sh
Just remove the keyword "function".
```
conv()
{
	echo Message One
}

```
You can always look up the syntax in the manual page.
```
man sh
```

---

### Post by Josh1 on 2007-12-24
Isn't it conventional to use " " after echo's?
Such as
```
echo "Hello World!"
```
I don't know, I have only been doing BASH for a couple of weeks, but have been doing PHP forever.. So I guess I'm just use to it, lol.

---

### Post by nick_h on 2007-12-24
> Isn't it conventional to use " " after echo's?
It is safer.  The quotes will prevent pathname expansion which you probably don't want.
Try:
```
echo *
```
It won't print a single * character if there are files in the working directory.

---

### Post by Martje_001 on 2007-12-24
Go to a terminal and do:
```
./script
```
or
```
bash script
```

---

