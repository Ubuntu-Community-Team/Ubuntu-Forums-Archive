---
title: "Copy entire folder and contents"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by SZorg on 2006-12-08
I installed Unreal Tournament 2004 -- I love the game.

I want to patch it and install the ECE bonus pack. I have both downloaded and they sit as folders on my desktop. I can't directly copy and paste (don't have permission) them to the /usr/local/games/ut2004 folder so I tried to use terminal.

```

zorg@zorg-desktop:~$ cp /home/zorg/Desktop/ut1 /usr/local/games/ut2004
cp: omitting directory `/home/zorg/Desktop/ut1'

```

First, what am I doing wrong in the copy process? Second, can I change the folder owner as well as the owner of it's contents? I sudo'd the installer, which I'm not sure was necessary in retrospect. Help would be appreciated. :]

---

### Post by scrooge_74 on 2006-12-08
much easier open terminal write sudo nautilus so you have a GUI and are root and can do as you please at the click of a button

---

### Post by SZorg on 2006-12-08
That.. solved nearly eveything. The problem at hand is gone, so thank you very much.

Is there a way, though, to change permissions/owner of a folder and all of it's contents?

---

### Post by loell on 2006-12-08
on nautilus right click the folder -->properties--> permission

---

### Post by scrooge_74 on 2006-12-08
> **SZorg said:**
> That.. solved nearly eveything. The problem at hand is gone, so thank you very much.

Is there a way, though, to change permissions/owner of a folder and all of it's contents?

You may feel like you are using MS....... LOL

---

### Post by SZorg on 2006-12-08
The permissions under Nautilus didn't change the contained contents.


Well, it's not a big deal. Don't go to any lengths to solve it, as this workaround will do anytime.

---

### Post by scrooge_74 on 2006-12-08
> **SZorg said:**
> The permissions under Nautilus didn't change the contained contents.


Well, it's not a big deal. Don't go to any lengths to solve it, as this workaround will do anytime.

you can change permissions to folders by using chown

in termina type man chown so you can get an idea of what to do

---

### Post by aysiu on 2006-12-08
What you're missing in both cases is the *-R* option. If you had done ```
sudo cp -R /home/zorg/Desktop/ut1 /usr/local/games/ut2004
``` that would have copied everything.

If you want to do recursive permission changes you would do ```
sudo chmod -R 755 /usr/local/games/ut2004
``` I just put *755* as an example, but you can change the permissions to whatever you want, of course.

Same principle applies to *chown* (for changing ownership of the folder): ```
sudo chown -R *username:username* /usr/local/games/ut2004
```

---

### Post by drr422 on 2006-12-08
This will give you an more indepth explation and examples of using chown and permissions in general.  I have been learning alot from this web site [http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php]("http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php")

---

### Post by SZorg on 2006-12-09
Another million points for Ubuntu over M$, the people here are infinitely friendlier.

---

### Post by DUNC4N on 2006-12-09
Is there a step by step for installing ut2004. Its the only game I have that will probably work in linux.

Thanks.

---

### Post by aysiu on 2006-12-09
> **DUNC4N said:**
> Is there a step by step for installing ut2004. Its the only game I have that will probably work in linux.

Thanks.
Maybe [this thread](http://ubuntuforums.org/showthread.php?t=8140) might help?

---

