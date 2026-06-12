---
title: "[SOLVED] /dev/null question"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-03-09
I read this about /dev/null, but considering the amount of jokes on the site, I'm not exactly sure whether to take it seriously:

> 17.4. Where does data written to /dev/null go?

It goes into a special data sink in the CPU where it is converted to heat which is vented through the heatsink / fan assembly. This is why CPU cooling is increasingly important; as people get used to faster processors, they become careless with their data and more and more of it ends up in /dev/null, overheating their CPUs. If you delete /dev/null (which effectively disables the CPU data sink) your CPU may run cooler but your system will quickly become constipated with all that excess data and start to behave erratically. If you have a fast network connection you can cool down your CPU by reading data out of /dev/random and sending it off somewhere; however you run the risk of overheating your network connection and / or angering your ISP, as most of the data will end up getting converted to heat by their equipment, but they generally have good cooling, so if you do not overdo it you should be OK.



If this is true, then couldn't you basically send unwanted data of any kind to /dev/null, to completely remove it from a machine?

For instance, on Windows (the bad old days), I used a program called "CCleaner", that was supposed to effectively remove all unwanted data from a machine. There came another option later, whether on that program, or another one I used, to remove data completely, without leaving ANY trace of it, that was supposed to be up to "CIA standards of file removal." Basically, making it impossible for the data to ever be retrieved again.

So yeah, couldn't you use /dev/null to completely remove data/files, leaving no trace at all?

---

### Post by Rocket2DMn on 2008-03-09
/dev/null is a file that ignores all input to it, it is like a black hole.  I don't know what that post is, but people come up with goofy and often hilarious explanations to this fun and convenient little tool.

edit: more here: [http://en.wikipedia.org/wiki//dev/null](http://en.wikipedia.org/wiki//dev/null)

---

### Post by Nerdriot on 2008-03-09
I noticed a flaw in the wikipedia explanation, too...

They said that you couldn't use "mv" to move files to /dev/null, since it's a file...

But, I've done it. :P

That's another reason why I was wondering about being able to remove files, leaving no trace of them, by sending them to /dev/null. I made a file called "test", and echoed some gibberish in it, then "sudo mv test /dev/null", and it's gone.

But then again, I'm sure there's something on this machine (aside from bash history) that shows that the file existed at some point.

Oh well. I was thinking of making a more effective version of a program like CCleaner, which is why I asked, heh...

---

### Post by HermanAB on 2008-03-09
Think of all poor bits dying horrible deaths when you do this:
$ cat /dev/urandom > /dev/null

Horrible, just horrible...

---

### Post by Rocket2DMn on 2008-03-09
The "rm" command is, of course, the best way to delete files.  When these filesystems were designed, they made it very tough to recover deleted files, so when you rm something, it's basically gone for good.  It's like 10x harder to recover than doing it in windows I think.

---

### Post by Feivel on 2008-03-09
dev/null is a black hole that doesn't have any associated Hawking radiation. If it gets outside of the confines of it's linux cage...the universe will disappear but there is some that think whatever is lost in dev/null eventually appears on a windows machine thus accounting for it's bloat.

---

### Post by Feivel on 2008-03-09
> **HermanAB said:**
> Think of all poor bits dying horrible deaths when you do this:
$ cat /dev/urandom > /dev/null

Horrible, just horrible...

Tidal forces turn them into spaghetti.

---

### Post by Nerdriot on 2008-03-09
> **HermanAB said:**
> Think of all poor bits dying horrible deaths when you do this:
$ cat /dev/urandom > /dev/null

Horrible, just horrible...

LOL... 

Almost sad enough to make you want to write a poem about the poor little guys.

"Ode to a Dead Bit"

---

### Post by Rocket2DMn on 2008-03-09
/dev/null = 42 !!!
..........
Awww, doesn't work.  The search continues.

---

### Post by Nerdriot on 2008-03-09
cat /dev/urandom > /dev/null = nullocaust :(

---

### Post by The Cog on 2008-03-09
> **Nerdriot said:**
> I noticed a flaw in the wikipedia explanation, too...

They said that you couldn't use "mv" to move files to /dev/null, since it's a file...

But, I've done it. :P

That's another reason why I was wondering about being able to remove files, leaving no trace of them, by sending them to /dev/null. I made a file called "test", and echoed some gibberish in it, then "sudo mv test /dev/null", and it's gone.

But then again, I'm sure there's something on this machine (aside from bash history) that shows that the file existed at some point.

Oh well. I was thinking of making a more effective version of a program like CCleaner, which is why I asked, heh...
You may have just overwritten the special file /dev/null with a standard data file. Please can you post the output of this command so we can see if things are still normal:
**ls -l /dev/null**
This is the output I get, indicating that /dev/null is a character device:
```
crw-rw-rw- 1 root root 1, 3 2008-02-22 09:08 /dev/null
```

You can look upon /dev/null as a device driver (like a disk or a serial port perhaps) that discards any data sent to it. As far as I know, its main use is for discarding the redirected output of programs that would otherwise print unwanted output to the console.

That quote from section 17.4 (wherever you ot that from) was intended to be funny.

---

### Post by Rocket2DMn on 2008-03-09
> **Nerdriot said:**
> cat /dev/urandom > /dev/null = nullocaust :(

Yeah, I heard they demagnetized millions of bits!  I believe the initial command was something like
```
killall bits
or
kill -9 bits
```
Such a tragedy...

---

### Post by Nerdriot on 2008-03-09
> **The Cog said:**
> You may have just overwritten the special file /dev/null with a standard data file. Please can you post the output of this command so we can see if things are still normal:
**ls -l /dev/null**
This is the output I get, indicating that /dev/null is a character device:
```
crw-rw-rw- 1 root root 1, 3 2008-02-22 09:08 /dev/null
```

You can look upon /dev/null as a device driver (like a disk or a serial port perhaps) that discards any data sent to it. As far as I know, its main use is for discarding the redirected output of programs that would otherwise print unwanted output to the console.

That quote from section 17.4 (wherever you ot that from) was intended to be funny.

Mine gives me this:

```
-rw-r--r-- 1 ben ben 22 2008-03-09 18:17 /dev/null
```

As a test, again, I created a file called "test", and used "sudo mv test /dev/null", then used "cat /dev/null" and "ls -l /dev/null". Got nothing for either...

/dev/null has eaten my file, heh.

---

### Post by Nerdriot on 2008-03-09
> **Rocket2DMn said:**
> Yeah, I heard they demagnetized millions of bits!  I believe the initial command was something like
```
killall bits
or
kill -9 bits
```
Such a tragedy...

LOL! A part of me wants to give you a "Thanks" for the laughing I've been doing.

---

### Post by Rocket2DMn on 2008-03-09
> **Nerdriot said:**
> LOL! A part of me wants to give you a "Thanks" for the laughing I've been doing.

=D
You're a *riot*, too.

Oh how the horrible puns slay me.
:lolflag:

---

### Post by Nerdriot on 2008-03-09
Now I'm DEFINITELY giving you thanks.

It's a must.

;)

---

### Post by The Cog on 2008-03-10
Unfortunately, you have overwritten your /dev/null device with a regular file. Look at the **ls -l** output - it should start with a "c", denoting that it is a character device.

This should fix it:
```
sudo rm /dev/null
sudo mknod /dev/null c 1 3
sudo chmod 666 /dev/null
```

---

### Post by Nerdriot on 2008-03-10
Ahh, you were right. Apparently, something else tried to send output to /dev/null. And it did. Just a moment ago, I checked /dev/null, and got this random output...

What you instructed worked perfectly! Thank you very much. :)

I will no longer send a file to /dev/null, hah... I'm still a noob. I just switched over in January, and I'm still getting the hang of things, like bash scripting, python, all the term commands, etc..

Thanks again!

---

### Post by bodhi.zazen on 2008-03-10
Nice catch The Cog !!!

---

