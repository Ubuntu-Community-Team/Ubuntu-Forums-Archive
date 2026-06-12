---
title: "wine &lt;application.exe&gt; not working"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by kinson on 2006-11-21
Hi Guys,

I've just installed wine following these instructions:
[https://help.ubuntu.com/community/WineForAMD64?highlight=%28wine%29#head-aa2244ea3332a3e6c4aea59069ae827a2fed3469](https://help.ubuntu.com/community/WineForAMD64?highlight=%28wine%29#head-aa2244ea3332a3e6c4aea59069ae827a2fed3469)

I used the script provided on that link, and it installed successfully.

So I copied a simple program(winamp, in this case) to my Ubuntu desktop, and tried to install it.

```
wine winamp.exe
```

but it returned:

```
kinson@ubuntu:~/Desktop$ wine winamp.exe
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
kinson@ubuntu:~/Desktop$
```

The exe is on the desktop btw(just in case :p )
```
kinson@ubuntu:~/Desktop$ ls
IMG_0147.JPG  klite.exe  room.exe  winamp.exe
```

I tried with a few other apps with the same results ](*,)  Any idea?

I'm hoping to be able to get wine running, so that I can install WoW, and hopefully quicky move over from windoze :p

Cheer and thanks in advance,
Kinson

---

### Post by LLRNR on 2006-11-21
First of all... Wine IS running, but you should follow a nice HowTo. I'd suggest Bodhi.zazen's [HowTo](http://doc.gwos.org/index.php/HowToWine), it's a very nice one. Also when you want to install something through Wine, better check in their Applications DataBase ([AppDB](appdb.winehq.com)) and see detailed install instructions there - there are the most official instructions, anyway. Also try to keep in mind that usually you launch the app with "wine app" from the same directory as "app" is in. (See Bodhi.zazen's HowTo for further reference.)

Second... I don't know about the other apps you want to run, but instead of Winamp I'd suggest you try out [Beep Media Player](https://help.ubuntu.com/community/BeepMediaPlayer), it's a great player (IMO) and you can have Winamp Classic skins on it too...

HTH,

LLRNR

---

### Post by kinson on 2006-11-21
I selected Winamp only to test it, cause it was small and nothing major :p no to mention that I saw that it was supported at the AppDB.

I was reading another thread, and I think the error is cause I haven't installed my graphic card or something. Cause I tried glxgears:
```

kinson@ubuntu:~/Desktop$ glxgears
Error: couldn't get an RGB, Double-buffered visual
```


I know its probably there, and I'm probably blind, but I looked here and didn't see any instructions:
[http://appdb.winehq.org/appview.php?iVersionId=2883&showAll=Show+All+Tests](http://appdb.winehq.org/appview.php?iVersionId=2883&showAll=Show+All+Tests)

Anyways, thanks for the tip :) I'll try to install my graphics card tomorrow, and hopefully it'll work.

Cheers,
Kinson

PS: The main thing I wanna run is Word of Warcraft :)

---

### Post by kinson on 2006-11-22
I've got it working now ! :D

It was because I hadn't installed my graphics card drivers, heh. Noob :p

Installed them, got the setup started, but I didn't try installing it yet, but the initial problem is solved :)

Cheers all,
Kinson :)

---

