---
title: "how to make a shortcut ?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by medya on 2006-06-09
hey guys
i have installed Free Tennis Game on my ubuntu...it is really nice game.

to run the game I do this :
cd /home/fred/freetennis-0.4.8/
./freetennis -newbie

how I can make a short cut to it on desktop , to run the game with One Click ?
I DID try to creat a Aplication Luncher , I put this command in the application luncher's command :
/home/fred/freetennis-0.4.8/./freetennis -newbie


but it runs the program with error here is the error :
> 
fred@fred-desktop:~$ /home/fred/freetennis-0.4.8/./freetennis -newbie
open /dev/sequencer: No such file or directory
Fatal error: exception Sdlmixer.SDLmixer_exception("Mix_LoadWAV_RW with NULL src")


---

### Post by RRS on 2006-06-09
Right click an open area of the desktop and select "create launcher"

---

### Post by r3st on 2006-06-09
i was wondering the same thing

---

### Post by aysiu on 2006-06-09
```
sudo ln -s /home/fred/freetennis-0.4.8/freetennis /usr/bin/freetennis
``` Then right-click on the desktop and select "create launcher" and make the launcher command ```
freetennis -newbie
```

---

### Post by medya on 2006-06-10
assiu i did what u said ....  it doenst run anything when I click on it

---

### Post by medya on 2006-06-10
ayslu 
I tried it in Terminal it gaves me the same Error ... 
> fred@fred-desktop:~$ freetennis -newbie
open /dev/sequencer: No such file or directory
Fatal error: exception Sdlmixer.SDLmixer_exception("Mix_LoadWAV_RW with NULL src")

but it doenst give me any error when I run it in its own directory.

---

### Post by dvarsam on 2006-06-10
Hello!

I have already answered this...

Visit:

[http://ubuntuforums.org/showthread.php?t=193238](http://ubuntuforums.org/showthread.php?t=193238)

Good Luck!

---

### Post by medya on 2006-06-10
dvarsam I dont see anything new in your post.... all u had said is "create a luncher"  enter the command...
I already did it ! it doenst wokr look at my previous posts.

---

