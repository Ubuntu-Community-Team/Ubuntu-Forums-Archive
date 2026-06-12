---
title: "LAME building help"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by jiub on 2006-03-24
I'm a complete noob to linux and i've never had to compile a program before so this is a first. This computer will eventually double as my main computer/myth tv box and i'm trying to get the latter set up right now.

I've been using this guide: [http://mythtv.org/docs/mythtv-HOWTO-5.html#ss5.1](http://mythtv.org/docs/mythtv-HOWTO-5.html#ss5.1) , at 5.1: building LAME

"$ tar -xzf lame-3.96.1.tar.gz
$ cd lame-3.96.1
$ ./configure"

Up to here things go fine.

But when I try "$ make" it says command not found.

---

### Post by PhilOSparta on 2006-03-24
You need the various development tools.

sudo apt-get install build-essential

That will get you the compiler and make programs.

---

### Post by jiub on 2006-03-24
Thanks, that helped a lot. One more question:

Now I'm at the lines:

$ su
# make install

After "$ su" (which I assume is granting me superuser privileges?) I get

"su: Authentication failure
Sorry."

Also, what is the "#" in the last line?

---

### Post by PhilOSparta on 2006-03-24
Use sudo instead of su

Re: 
"su: Authentication failure
Sorry."

I just tried that myself and got the same thing.  It is caused because in Ubuntu the "powers that be" don't really think that you should be root without going through a few hoops.

Use of sudo will allow you to enter the command you want, but it will request your passwd and give you about 15 minutes to get your terminal session completed.  When your 15 minutes are up, it will ask you for the passwd again.

The # indicates that you are root.  At least that's the usual meaning.

---

