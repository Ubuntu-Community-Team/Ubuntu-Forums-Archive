---
title: "Why Compile?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by PhillD on 2007-03-21
I understand why files are compiled in windows - to compile the code to form an executable which allows the code to run.  This also keeps the code safe in a non open source environment.  But often in Linux, when a file is not available in a software repository, 9/10 you have to download source code and compile it before you can use it.  Why is it not possible to download an equivalent to an exe file and install it from that?  I understand RPM's exist but these don't always work in ubuntu.  Is it because each version (or flavor) of Linux is a little different and a compiled program for SuSe won't necessarily run on Ubuntu?

Phill

---

### Post by Tomosaur on 2007-03-21
> **PhillD said:**
> I understand why files are compiled in windows - to compile the code to form an executable which allows the code to run.  This also keeps the code safe in a non open source environment.  But often in Linux, when a file is not available in a software repository, 9/10 you have to download source code and compile it before you can use it.  Why is it not possible to download an equivalent to an exe file and install it from that?  I understand RPM's exist but these don't always work in ubuntu.  Is it because each version (or flavor) of Linux is a little different and a compiled program for SuSe won't necessarily run on Ubuntu?

Phill

I think you answered your own question:
> 
I understand why files are compiled in windows - to compile the code to form an executable which allows the code to run. 


If you don't compile code, you can't run it, to put it simply.

The reasons why there are so many programs on linux which you need to compile for yourself:
[LIST]
[*]Security - If you have access to the code, you can look through it to see whether there's anything malicious.
[*]Freedom - You can change and modify the source code (with most programs anyway, others have restrictions which don't allow you to do this). All GPL licenced software can be modified to your hearts content. You can then redistribute your version of the program, or sell it if you wish.
[*]Dependencies - Sometimes a program depends on something else. When you download a package like a .deb or a .rpm, these dependencies are normally satisfied automatically. The same thing happens with a setup.exe on Windows. The reason many people shy away from them and simply give you the source code is that you will invariablu end up with lots of files on your machine which all do the same thing. This is a waste. On Linux, developers try to re-use code as much as possible, so they will say -"here are the libraries you need to run this program." rather than just rewriting all of the libraries themselves (which is what frequently happens on Windows programs). Package management systems like aptitude help to satisfy these dependencies efficiently, so that lots of different programs all use the same libraries, alleviating the stress you would otherwise have to encounter. Think of it as a sacrifice to ensure efficiency. Developers on Linux want to reuse code as much as possible, but this means they can't rely on the end-user having these dependencies on their system. It is much more efficient than the use of setup.exe on Windows, although it doesn't seem like it from the end-user perspective.
[/LIST]

There are, of course, other reasons, but that should give you some idea :)

---

### Post by mac.ryan on 2007-03-21
> **PhillD said:**
> Is it because each version (or flavor) of Linux is a little different and a compiled program for SuSe won't necessarily run on Ubuntu?

Also. But other reasons include the fact that when you compile you can give a number of options, in order to optimize the software for your environment, or you might be to use different libraries, or...

Anyhow, because ubuntu is based on debian, often you can use debian binaries (.deb) without having to recompile the software on your own...

---

### Post by yabbadabbadont on 2007-03-21
If you ever need to warm up a cold computer room, just compile glibc from source.  That will do it nicely.  :D

---

### Post by dracomordag on 2007-03-21
i, too, find it a little annoying to compile a lot of programs from source

but once you've done it once or twice, its really not much of an issue. you get used to it.

---

### Post by mahy on 2007-03-21
I don't understand your probs, guys. A normal Ubuntu user never needs to compile anything at all!

---

### Post by dracomordag on 2007-03-21
for example, i needed to compile gnomad2 with libmtp so that i could get my Creative mp3 player running.

---

### Post by PhillD on 2007-03-21
I guess the only time I find it annoying is when the compile doesn't work, otherwise the extra few steps vs. windows doesn't bother me.  What annoys me more is when a program won't compile for unknown reasons e.g. No acceptable C compiler found - when i have a c compiler.... or a very long list of errors which really don't explain what’s wrong.

---

### Post by yabbadabbadont on 2007-03-21
> **mahy said:**
> I don't understand your probs, guys. A normal Ubuntu user never needs to compile anything at all!

They do if they want to use the gtk-smooth-themes that are included in the repositories.  They need both the gtk2-engines-smooth and gtk-engines-smooth in order to function properly.  However, there isn't any gtk-engines-smooth in the Edgy repos.  It is missing for some reason.  The only option is to build it from source.  There are other examples, but that is the first that comes to mind.

---

### Post by macogw on 2007-03-21
> **dracomordag said:**
> for example, i needed to compile gnomad2 with libmtp so that i could get my Creative mp3 player running.

And as you've probably noticed (I have) the ones in the repos DON'T WORK!

---

### Post by PhillD on 2007-03-21
I am setting the machine up for use in a business environment.  I have to have the following setup and working:

1. Touch screen monitor (gunze)
2. Wireless capability for trendnet wireless card
3. Attached printer

A lot of people say that the average user does not need to compile but this message board would suggest otherwise.  I guess it depends on what the average user is considered to be, depends on whether they need to compile: Refer to my other post, and comments in if ubuntu is viable for the average user.

[http://www.ubuntuforums.org/showthread.php?t=389269&page=2&highlight=viable+for+average+user](http://www.ubuntuforums.org/showthread.php?t=389269&page=2&highlight=viable+for+average+user)

---

### Post by euler_fan on 2007-03-21
At the risk of being redundant, I compile a few things from source to get the latest and greatest or something not available via the repos. The latest ClamAV comes to mind :( (or at least it does thinking about the last time I looked for it in the repos).

In the end, the more you want something that is cutting edge or esoteric (not necessarily different things), the more I find you will end up compiling from source. There is just way too much software available in this world for all of it to be in the repos, no matter how comprehensive they are.

In the end, you do it a few times and it gets to be a no big deal, and actually not a major issue either. Just bookmark the link to the developer's page and check it periodically for an updated version.

---

### Post by dracomordag on 2007-03-21
i think people to often think of the basic user as the average user. The basic user will only listen to a couple of songs, browse the net, check email, do some basic word processing.

the average user, however, needs quite a bit more than that.

---

### Post by mahy on 2007-03-21
> **PhillD said:**
> I am setting the machine up for use in a business environment.  I have to have the following setup and working:

1. Touch screen monitor (gunze)
2. Wireless capability for trendnet wireless card
3. Attached printer

A lot of people say that the average user does not need to compile but this message board would suggest otherwise.  I guess it depends on what the average user is considered to be, depends on whether they need to compile: Refer to my other post, and comments in if ubuntu is viable for the average user.

Ubuntu is as viable as it gets with virtually no support from big business and hardware manufacturers. I, too, did some compilations (ALSA...), but i don't count myself among the average users... ;)

---

### Post by mahy on 2007-03-21
But i do agree it's bad if some Free sw vendors (e.g. GNU) only release their products in source code. Wine developers on the other hand release packages for a plethora of distros.

---

### Post by PhillD on 2007-03-21
I'm not sure if this is along the right lines but I guess it's fair to think of things like this.  Vista now comes in 6? different flavors, each offering different (or progressive) functionality aimed at a different types of user groups.  When I heard this I thought it was a bad idea (but this is beside the point).  Would it be fair to think of the different versions of Windows in a similar manner to the different distributions (and flavors) of Linux, each offering something a little different for a general user group.  However, a program written for vista, is a program written for all versions of vista.  Do you think _certain parts _ of Linux should be more standardized to make it easier for software installation?  Would this help Linux become more popular and successful?

---

### Post by dracomordag on 2007-03-21
yes, the differing distros of Linux have always been, shall we say, "distracting" Linux from gathering more and more support and awareness. Ubuntu, however, has been the leading distro for a while now, so it's pretty hard to find something for linux thats NOT supported by it in some way.

---

