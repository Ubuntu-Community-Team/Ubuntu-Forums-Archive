---
title: "Does ubuntu ever suffer from &quot;DLL Hell&quot;?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Derek Tomes on 2006-11-22
I'm used to Win32 where applications spray files all over the HDD and overwrite system and OS files. Do apps in GNU/Linux (and in this case - more importantly in ubuntu) suffer from this behaviour???

Could I, for example, just select all the applications in Applications > Add/Remove... and install them without fear of trashing my system???

I'm not planning to, I'm just wondering...:rolleyes:

---

### Post by CatKiller on 2006-11-22
If you **only** use the package management system - Synaptic / Add/Remove / Aptitude / apt-get - then you won't suffer at all. All the dependencies get sorted out for you.

If you add in other repositories, then all bets are off, and if you compile from source or download a .deb or what-have-you then you need to sort out the dependencies yourself.

---

### Post by Ocxic on 2006-11-22
what catkiller said is correct, and to answer your question, no you don't have to worry about trashing your system by doing that. It's the one great thing i love about ubuntu, when you un-install something it really get completely un-installed, no stupid little folers/shortcuts, and best of all no registry to get messed up. YAY!

---

### Post by loell on 2006-11-22
dll hell is possible in ubuntu, if you install wine.
there is however "dependency hell" usually it only happens when you install a debian package not specifically built for ubuntu.

---

### Post by kinson on 2006-11-23
> **CatKiller said:**
> If you **only** use the package management system - Synaptic / Add/Remove / Aptitude / apt-get - then you won't suffer at all. All the dependencies get sorted out for you.


A dream I never thought possible, a misconception that probably came from using too much Windows :p

I'll be a happy little user when I get to install whatever I wanna try, and uninstall it without worry(thats what you mean right? :p )

Cheers,
Kinson

---

### Post by aysiu on 2006-11-23
> **loell said:**
> dll hell is possible in ubuntu, if you install wine.
there is however "dependency hell" usually it only happens when you install a debian package not specifically built for ubuntu.
Or if you try to install GnomeSword in Edgy Eft.

---

### Post by livinginx on 2006-11-23
The closest to DLL Hell would be a dependency issue or using an older version library file.

Usually, pretty easy to fix.  Just put the new lib in its place and you are done.  Your main libraries only exist in one place (if I am not mistaken, only been using Ubuntu for a couple of weeks and very limited linux use prior.)

---

### Post by cantormath on 2006-11-23
> **Derek Tomes said:**
> I'm used to Win32 where applications spray files all over the HDD and overwrite system and OS files. Do apps in GNU/Linux (and in this case - more importantly in ubuntu) suffer from this behaviour???

Could I, for example, just select all the applications in Applications > Add/Remove... and install them without fear of trashing my system???

I'm not planning to, I'm just wondering...:rolleyes:

I think with any os, trashing it is always an option.  However, in linux there is not DLL hell.  The hell that exist for new people is in the installation.  What I mean is alot of folks have trouble getting everything working right with there hardware.  

I would rather use a broken linux box then a working windows box anyday of the week.`:KS

---

### Post by livinginx on 2006-11-23
In my first week of Linux, I would just throw whatever I could at it.  If it broke, I would look for a solution to return it to its previous state.

Broke it so bad a couple of times in the first week, I had to reinstall.  Well, I probably didn't have to, but it seemed easier, and more fun :-D

One thing I really thought was cool about my switch over is that the computer I use in the bedroom has a GeForce 6200 AGP 128MB card in it.  Problem, anytime I tried to do anything with the NVidia driver, the computer would lock up.  I would still be able to use my mouse, but I couldn't switch to tty1-6 or anything.

Well, I did some research, tried a few options from other people (some of which broke my install), and then I would modify what they did until it works.

My vid card isn't running to 100%, but that is a solution that is either going to have to come from NVidia or somebody working on the drivers, way above my head.

Break it and fix it to learn it :-D

---

### Post by PrinceArithon on 2006-11-23
LOL I Love this question.  Yes there is something similar it's called lib hell, the thing is, it's not as bad as dll hell.  Lib hell doesn't happen nearly as often, and there are ways of cleaning it all out through your synaptic manager.

---

### Post by aysiu on 2006-11-23
As far as I know, *dependency hell* doesn't allow you to install an application and *dll hell* doesn't allow you to run an application.

---

### Post by leech on 2006-11-27
Though with Dependency Hell, you can still force the package, but it's generally not a good idea to do so.  RPM handles this a bit better, where it looks for both the package name and the library file itself.  

Leech

---

### Post by David Marrs on 2006-11-27
The trouble with that is when you want to dist-upgrade. The same applies to using external repos, package builders, easyubuntu etc. These days, if I want to install something not in the repos, I compile it from source and keep it unmanaged. That's usually pretty easy to do as any dependancies are almost always packaged and can be installed through synaptic.

---

### Post by OttifantSir on 2006-11-27
> **livinginx said:**
> Break it and fix it to learn it :-D

Unless you started with radio-tubes like in the ENIAC, or went to a month-long course to learn, that`s the only way.

Have tried to say this to so many people. You won`t learn computers without playing with it. Sometimes, you do something bad. Then, you ask for help or read the manual or the output and try to understand it. Then you look for ways to fix it. Only way I have ever learned anything on the computer.

---

### Post by kinson on 2006-11-27
> **OttifantSir said:**
> 
Have tried to say this to so many people. You won`t learn computers without playing with it. Sometimes, you do something bad. Then, you ask for help or read the manual or the output and try to understand it. Then you look for ways to fix it. Only way I have ever learned anything on the computer.

Yeah, I totally agree with this. I remember when I first started out, I kept screwing up my windows box and didn't know how to format a pc(lol !). I kept having to bring it back to the shop. And some of them stole some of my hardware(I didn't know until I was wondering why my drivers wouldnt install :evil: ). All in all, everthing's a lesson :)

Cheers,
Kinson

---

