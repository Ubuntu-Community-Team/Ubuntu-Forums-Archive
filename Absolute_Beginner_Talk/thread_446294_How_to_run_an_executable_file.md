---
title: "How to run an executable file?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-16
Ok, I downloaded a small arcade game by the name of 'N'. It came in a compressed file, so I unpacked it, and in the folder were several readme files and one file called 'n_v14', I checked under properties, and all it says is executable for file type, and I'm confused as how to install/run it. 

Help would be appreciated, thanks.

---

### Post by chamberlain2006 on 2007-05-16
It should just be a matter of making it executable just to make sure, by doing
```
sudo chmod +x filename
```
and then
```
./filename
```
to rrun it.

---

### Post by lopagof on 2007-05-16
if it was designed for windows then you will need WINE windows emulator.

---

### Post by Hobo Joe on 2007-05-16
This is what I got when I tried to run it:

```

./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

It says no such file or directory, but I can see it, it's sitting right no my desktop!

> **lopagof said:**
> if it was designed for windows then you will need WINE windows emulator.

It's not, I downloaded the Linux version. I tried using WINE with the Windows version, but it had REALLY bad performance.

---

### Post by chamberlain2006 on 2007-05-16
It means that it cannot find the shared library it needs, not the executable.  Is it a Windows program? I didn't think about that...

---

### Post by Hobo Joe on 2007-05-16
> **lopagof said:**
> if it was designed for windows then you will need WINE windows emulator.

> **chamberlain2006 said:**
> It means that it cannot find the shared library it needs, not the executable.  Is it a Windows program? I didn't think about that...

It's not a Windows file. If you download a Windows executable they have .exe on the end, this one doesn't.

How can I get it to find the shared library it needs?

---

### Post by chamberlain2006 on 2007-05-16
By the way, the package you need to install is libstdc++2.10-glibc2.2.  Do
```
sudo apt-get install libstdc++2.10-glibc2.2
```

---

### Post by Hobo Joe on 2007-05-16
It worked!

But the problem of really bad performance seems to be cross-platform. Wine had bad performace, and so does this... :(
Oh well. 

Thanks for all your help though!

---

### Post by chamberlain2006 on 2007-05-16
No problem.  Seems like a bad program, unfortunately.  One a happier note, this will mean that you won't get that error with any other programs!

---

### Post by Gen2ly on 2007-05-16
Post the weblink, Id like to try it.

---

### Post by noerrorsfound on 2007-05-16
> **lopagof said:**
> if it was designed for windows then you will need WINE windows emulator.
How do people manage to make the mistake of calling Wine a Windows emulator? The name stands for "Wine is not an emulator" so how does this happen?

Does it really make sense to say "you will need the 'Wine is not an emulator' Windows emulator"?

---

### Post by chamberlain2006 on 2007-05-16
Some people really get mad at that kind of stuff.  Personally, I think it's a common, easy to make mistake.  I don't think it's that big of a deal, really.

---

### Post by Hobo Joe on 2007-05-16
> **Dirk.R.Gently said:**
> Post the weblink, Id like to try it.

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

Sorry for a slow response, I was eating dinner.

---

### Post by chamberlain2006 on 2007-05-16
I agree, not a good game at all.  Probably cause it's in flash...

---

### Post by Hobo Joe on 2007-05-16
> **chamberlain2006 said:**
> I agree, not a good game at all.  Probably cause it's in flash...

I figured it out.

For some CRAZY reason, if you start some music before you open the game, it runs perfectly fine. I have absolutely NO idea why though. It's the wierdest thing I've ever heard of.

The game is awesome though. I used to play it in Windows all the time.

---

