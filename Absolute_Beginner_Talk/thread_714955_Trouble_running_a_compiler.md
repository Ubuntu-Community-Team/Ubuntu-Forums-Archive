---
title: "Trouble running a compiler"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by holdie on 2008-03-04
Hey everybody, so I'm trying to get the NXT - Lego Mindstorms programs to work with my linux and I'm running into a bit of a problem

when I downloaded the tar file from their website and extracted it, I found that the NBC program (the compiler) is there but it doesn't have any extension on it.  Linux reads it as an "executable" although wine still can't open it...I was wondering whether or not this is a bad file or if i need to be modifying it in some way.

Thanks

---

### Post by Oldsoldier2003 on 2008-03-04
> **holdie said:**
> Hey everybody, so I'm trying to get the NXT - Lego Mindstorms programs to work with my linux and I'm running into a bit of a problem

when I downloaded the tar file from their website and extracted it, I found that the NBC program (the compiler) is there but it doesn't have any extension on it.  Linux reads it as an "executable" although wine still can't open it...I was wondering whether or not this is a bad file or if i need to be modifying it in some way.

Thanks
is it mean to run under wine or be compiled as a linux app? take a look at the readme files and get back with us maybe we can help sort it out

---

### Post by holdie on 2008-03-04
it's supposed to be a linux app...I tried it under wine and nothing happened.

as for the readme, unfortunately there isn't much as far as installation goes, it only details the language for the program and such...I got instructions from a book that gave me the link to the site and such, and apart from that it only specified that I needed to run the program to compile the code...

---

### Post by dstew on 2008-03-04
To run the file, navigate to the directory that contains it and enter:```
./nbc
```

---

### Post by Peacepunk on 2008-06-16
As of now, best ressource is here:
[forums.nxtasy.org]("http://forums.nxtasy.org/index.php?showtopic=2143")

Or at least, that's how I had it up an running, if you do a bit more research.

*nix softwares you ought to have:
**nbc     **            //that's your cli compiler
**nexttool **           //that's your interface to the NXT
**n2t    **             //that's a quicker, leaner interface

They are all CLI (aka, work in a terminal). They are all trustable (tested by many people or issued by knowledgeable people). They are all easy to install and they all provide you with all options with name-of-soft -help

&& you'll need your favourite text editor at hand.

Following the steps mentionned in the nxtasy forum, I was up and running in one evening. OK, a long one.

Time to start writing some code now...
:)

*For the record, I didn't get LiNXT, nxt_python and brickcc-with-wine working. Wine stumbled upon the usb/bt comm, as usual. I am still trying nxtfs and libnxtusb but it doesn't look promising.*

---

