---
title: "Is an AMD processor compatible?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by tchase on 2007-05-10
Here are my system specs, is my processor compatible?:

AMD Turion 64 X2 Mobile Technology TL-50 1.60 GHz

1 GB RAM

100 GB Hard Drive

---

### Post by Medieval_Creations on 2007-05-10
I have an AMD Athalon 64 3000+ with 1 GB RAM.

And it works perfectly fine with both the 32bit and 64bit versions.  You shouldn't have any problems with the CPU.

---

### Post by Zzl1xndd on 2007-05-10
agreed Im using an old 2200+ here and never had any problems.

---

### Post by lakersforce on 2007-05-10
If you really want to know, you should compile your own kernel.

---

### Post by Bachstelze on 2007-05-10
And why is that ?

---

### Post by David Corrales on 2007-05-10
> **lakersforce said:**
> If you really want to know, you should compile your own kernel.

Ignore this. Go ahead with AMD, it's all good.

---

### Post by Martin on 2007-05-10
> **David Corrales said:**
> Ignore this. Go ahead with AMD, it's all good.
I agree - you will very rarely need to ever compile a new kernel and AMD is just as compatible as Intel

---

### Post by Medieval_Creations on 2007-05-10
> **lakersforce said:**
> If you really want to know, you should compile your own kernel.

I agree that this option would produce the best performance for a specific rig, but it probably isn't the easiest.  I've done it quite a few times in the last few years, playing with different configurations and for the life of me there are still sections in the config of the kernel that I don't fully understand.

*EDIT*

tchase:
You won't need to compile a kernel. Ubuntu does a good job of trying to keep bloat in check while still supporting as much hardware as it can.

---

### Post by Bachstelze on 2007-05-10
I'm pretty aware of that, thanks, I was compiling kernels perhaps before you even touched a Linux at all and it it absolutely not required for a system to work, especially Ubuntu.

---

### Post by Medieval_Creations on 2007-05-10
> **HymnToLife said:**
> I'm pretty aware of that, thanks, I was compiling kernels perhaps before you even touched a Linux at all and it it absolutely not required for a system to work, especially Ubuntu.

That was my fault.  I miss interpreted the post.  Sorry about that.
You probably were. :)

---

### Post by Bachstelze on 2007-05-10
Sorry for the rudeness too, I tend to get out of my nerves quite often these days...

---

### Post by Medieval_Creations on 2007-05-10
No Blood, No Foul. :cool:

---

### Post by mb01915 on 2007-05-10
That was really helpful especially in a beginner's forum.

---

### Post by Drooling Iguana on 2007-05-10
> **tchase said:**
> Here are my system specs, is my processor compatible?:

AMD Turion 64 X2 Mobile Technology TL-50 1.60 GHz

1 GB RAM

100 GB Hard DriveIf you're wondering if any given hardware setup will work with Ubuntu, burn the LiveCD and try booting from it. If everything works on the LiveCD, everything'll work when you install it to your HD. If the LiveCD doesn't work, it still might work when you install it (my P5B-based system couldn't boot the 7.04 LiveCD but could install without a problem from the alternative install CD) but you might have to do a bit more research.

---

### Post by lakersforce on 2007-05-10
Ignore me? Ignore you!

The question was if her processor was supported. I dont know if it is supported, but I do know that her Ubuntu partition would most proberly run out-of-box (if not with 7.04 then with 6.10 or 6.06).

If she really wants to find out if her specific processor is surported at the kernel level, the best way to find out would be to compile the kernel herself. That way she would be able to go over the kernel options and see if it is supported.

Kernel compiling is a great learning experience and the best way you can get to know your os. And there is plenty of help to find in these and other forums.


I am no techie, but I succesfully compiled my first kernel less than one week into linux.

---

### Post by stmiller on 2007-05-10
> **lakersforce said:**
> Ignore me? Ignore you!

The question was if her processor was supported. I dont know if it is supported, but I do know that her Ubuntu partition would most proberly run out-of-box (if not with 7.04 then with 6.10 or 6.06).

If she really wants to find out if her specific processor is surported at the kernel level, the best way to find out would be to compile the kernel herself. That way she would be able to go over the kernel options and see if it is supported.

Kernel compiling is a great learning experience and the best way you can get to know your os. And there is plenty of help to find in these and other forums.


I am no techie, but I succesfully compiled my first kernel less than one week into linux.

Wow lakersforce. Out to make enemies?

Giving the advice to 'compile your own kernel' on a forum titled 'Absolute Beginner Talk' is quite out of place. That would not solve any problems, nor does it answer the person's questions. You said you didn't even know anything about AMD64 support....

There is NO NEED to 'compile a kernel for AMD64 support.' In fact, ubuntu provides these kernels for you:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amd64&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amd64&searchon=names&subword=1&version=feisty&release=all)

So if you run 64bit ubuntu, you can use the 64bit kernels provided. 

Or running a standard x86 install will work just fine on this cpu also.

See the AMD64 section on the discussion board for lots of info.

---

### Post by David Corrales on 2007-05-10
> **stmiller said:**
> Wow lakersforce. Out to make enemies?

Giving the advice to 'compile your own kernel' on a forum titled 'Absolute Beginner Talk' is quite out of place. That would not solve any problems, nor does it answer the person's questions. You said you didn't even know anything about AMD64 support....

There is NO NEED to 'compile a kernel for AMD64 support.' In fact, ubuntu provides these kernels for you:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amd64&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amd64&searchon=names&subword=1&version=feisty&release=all)

So if you run 64bit ubuntu, you can use the 64bit kernels provided. 

Or running a standard x86 install will work just fine on this cpu also.

See the AMD64 section on the discussion board for lots of info.

Exactly why I wrote about ignoring that post. It's pointless in a new user forum, and no, compiling a kernel isn't the best way to "learn about an os".

---

### Post by spur on 2007-05-10
I am also running a 64bit system. I installed from a live cd. No probs. I would say try it. You will find it works. You have plenty of ram as well so if you have any probs it may be your other hardware not your cpu. A common problem with installs of a new os is the graphics card. This is with all oses, even windows of all varieties. But ATI and Nvidia are well supported so no problems should arise.
Should be absolutely no reason to compile your own kernel unless your cpu was manufactured on Mars, I believe their technology is way ahead of ours anyway![img]http://www.democraticunderground.com/discuss/images/sarcasm.gif[/img]

---

