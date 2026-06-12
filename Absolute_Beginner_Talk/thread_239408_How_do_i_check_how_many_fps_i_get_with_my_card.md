---
title: "How do i check how many fps i get with my card?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by p.i.m.p on 2006-08-19
i tried running glxgears but there doesnt seem to be an option for reporting the fps :-s i also searched on google but no luck :( somebody? thanks

---

### Post by Klaidas on 2006-08-19
If you run glxgears in terminal, don't you get output like> 2563 frames in 5.0 seconds = 508.627 FPS?

---

### Post by p.i.m.p on 2006-08-19
nope :-s left it running for about a minute but no output

---

### Post by tappad on 2006-08-19
I know i don't.. (been wondering the same in silence)

---

### Post by Indras on 2006-08-19
> **Klaidas said:**
> If you run glxgears in terminal, don't you get output like?

```
2563 frames in 5.0 seconds = 508.627 FPS
```

Actually, when I run glxgears, I get an output like this:

```
35766 frames in 5.0 seconds = 7153.113 FPS
42127 frames in 5.0 seconds = 8425.299 FPS
42381 frames in 5.0 seconds = 8476.069 FPS
42391 frames in 5.0 seconds = 8478.174 FPS
42315 frames in 5.0 seconds = 8462.866 FPS
```

:D :D :D 8)

---

### Post by tappad on 2006-08-19
```
$ glxgears
X connection to :0.0 broken (explicit kill or server shutdown).

```

Thats all that i get..  "X connection to :0.0 broken (explicit kill or server shutdown)" when i get tired of waiting and shut it down..

---

### Post by xpod on 2006-08-19
Excuse my ignorance....I do that glxgears in the terminal and i get.....
glxgears?
Ive gathered it`s some fps test BUT i too would like to know how to adjust this setting if possible because i recall one of the games telling me i needed to turn the FPS up but i did`nt know how.Cant recall actual name of game.

EDIT:I get your terminal message if i close it

[ATTACH]14542[/ATTACH]

---

### Post by Lord Illidan on 2006-08-19
```
glxgears -printfps
``` should output the fps in the terminal. It could be this too.```
glxgears --printfps
``` I am not sure which as I am on a windows machine.

---

### Post by p.i.m.p on 2006-08-19
hey thanks man.. works :-D

---

### Post by tappad on 2006-08-19
> **Lord Illidan said:**
> ```
glxgears -printfps
``` should output the fps in the terminal. It could be this too.```
glxgears --printfps
``` I am not sure which as I am on a windows machine.

You solved it! :)

```
$ glxgears -printfps
73147 frames in 5.0 seconds = 14629.395 FPS
77370 frames in 5.0 seconds = 15473.994 FPS
77391 frames in 5.0 seconds = 15478.030 FPS
77283 frames in 5.0 seconds = 15456.562 FPS

```

---

### Post by ash211 on 2006-08-19
try running ```
glxgears --help
```  It might give you an option to display the fps.  Try the -printfps and -iacknowledgethatthistoolisnotabenchmark flags.  Those used to work on my machine, but I think an upgrade to glxgears made it print the fps by default.    Don't forget to let it run for 5-10 seconds or so to be able to come up with those statistics too!

---

### Post by xpod on 2006-08-19
GOOD STUFF .....BUT is there any way to adjust the fps?????

EDIT:..it aint having that help command but you`se have gave me the inclination now to go find out how to mess around with it.

---

### Post by ash211 on 2006-08-19
You can't just adjust the fps of glxgears, I'm pretty sure it displays at the best framerate possible.  You're limited to the abilities of your hardware.

EDIT: Those are some pretty solid numbers you're getting there, though.  Check [http://www.ubuntuforums.org/showthread.php?t=39349&page=8](http://www.ubuntuforums.org/showthread.php?t=39349&page=8) to get a feel for what other people are getting.

---

### Post by TooDamFast on 2006-08-19
wow, thanks!  its the first time ive seen the "-printfps"  now mine works!

---

### Post by Frank Golden on 2006-08-19
> **TooDamFast said:**
> wow, thanks!  its the first time ive seen the "-printfps"  now mine works!


Try this command "fgl_glxgears" without the quotes of course.
You will get glxgears in a rotating 3-D cube and it will output FPS.

Read this

 [http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

Don't get too obsessed with glxgears it is not very reliable
measure of performance. See the other commands at bottom of
web page verification that you are in hardware acceleration.
As far as I know you don't have much fine control in Ubuntu.

---

### Post by jrjr on 2006-08-19
.

---

### Post by tappad on 2006-08-19
> **ash211 said:**
> You can't just adjust the fps of glxgears, I'm pretty sure it displays at the best framerate possible.  You're limited to the abilities of your hardware.

EDIT: Those are some pretty solid numbers you're getting there, though.  Check [http://www.ubuntuforums.org/showthread.php?t=39349&page=8](http://www.ubuntuforums.org/showthread.php?t=39349&page=8) to get a feel for what other people are getting.

Assuming you mean me.. And what if i could make use of SLI in ubuntu? :P

---

### Post by jrjr on 2006-08-21
.

---

