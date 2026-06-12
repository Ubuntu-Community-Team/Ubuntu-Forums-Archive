---
title: "mythtv chapter 9999999"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-02-05
I think this thing is close. Apparently the database is finally connecting and most other things seem to be working. The latest is this message --->

MythgTV is already using all available inputs for the channel you selected. 
If you want to watch an in-progress recording, select one from the playback menu. If you want to watch live TV, cancel one of the in-progress recordings from the delete menu

There is nothing to delete that I can find. There are no recorded programs. I havent selected a channel that I know of. 

I'm almost afraid to touch anything for fear of screwing up what may be a very near success.

Anybody that has any suggestions I am listening. 

Thanks. (Especially to fenian who got me this far)

---

### Post by kpatz on 2007-02-05
That message means mythtv is currently using all available tuners to record programs, thus watching "live TV" is unavailable.  If you want to watch the show being recorded, go into recorded programs and select the currently-recording program.

---

### Post by squrl on 2007-02-05
I understand what the message means.. The problem is there are no programs being recorded and none to select from to watch. There is only one tuner and it shows no indication of being used.

---

### Post by dannyboy79 on 2007-02-05
> **kpatz said:**
> That message means mythtv is currently using all available tuners to record programs, thus watching "live TV" is unavailable.  If you want to watch the show being recorded, go into recorded programs and select the currently-recording program.

i am also curious about this error. kpatz, you haven't really helped us here. he has explained that he didn't previsouly pick a channel, he didn't chose to record anything and he can't find any recording to delete. so could you please be more specifc as to how to solve this issue. thank you very much.

---

### Post by chris.olsen on 2007-02-18
I am having the exact same problem.  When I run the mythfilldatabase command it seems to work fine, but when I try to watch something I get the exact same message.

---

### Post by scottishnarn on 2007-02-19
Have you updated your kernel since you installed your card's drivers. I get this error when I haven't updated my TV card's drivers (IVTV, see the ubuntu wiki for details) after the kernel has been updated.

---

### Post by johndavid400 on 2008-02-18
I had the exact same problem...

The solution for me was that mythTV lost my tuner info and couldn't find an available input (b/c it deleted them).

You have to close myth frontend, go to your start menu> Settings> MythTV Setup

Then go to the TV Tuner option... re-add your TV tuner (or if you haven't done this step yet, thats why it wasn't working), scan for channels.

Now it should work

---

