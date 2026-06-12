---
title: "How to  mkdir"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Ariam on 2006-04-03
Please help to create a directory as follows. 

  /user/local/src/       (user substituted  with my ID)

This what I did. 

Applications - Accessories - Terminal at command promt.  

mkdir /user/local/src/ 

reponse cannote create dir. 

Ariam

---

### Post by taurus on 2006-04-03
You need to be root to create, write, remove, or modify system files.  So, try this
```

sudo mkdir /usr/local/src

```

p.s.  There is no such thing as /user unless you want to create one!!!

---

### Post by Princey on 2006-04-03
[QUOTE=Ariam]Please help to create a directory as follows. 

  /user/local/src/       (user substituted  with my ID)

This what I did. 

Applications - Accessories - Terminal at command promt.  

mkdir /user/local/src/ 

reponse cannote create dir. 

Ariam[/QUOTE]


Type this: 
> sudomkdir /user/local/src/  and press enter when done. You will be asked for your password. Type it in. Note, you won't see any **** showing, don't mind that. Just type and press enter. If you return back to the prompt with no error, it means it was created.

---

### Post by Ariam on 2006-04-03
Pricey, Taures 
both commands did not work. Pl note I am brand new to Linux world so be patient. 

What I need is to install  flash and real player and may be other software. 
Pl let me know how to go about doing this or point me to a place if you can on this topic. Thanks ariam.

point me if there is a th

---

### Post by taurus on 2006-04-03
If you want to install flash and realplayer, you can do that with Automatix, [http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix).  Personally, I did it the old fashion way but if you don't want to get into all that, see if you can install those two apps with Automatic...

---

### Post by Cephyr on 2006-04-03
Are you *sure* it didn't work?

Make sure you've capitalized and spelled everything correctly, the Linux command line is case-sensitive and will not work if you don't spell everything correct.

The correct command to use here is most definently 

```
sudo mkdir
```

---

### Post by Sweet on 2006-04-03
Dont forget to substitute user for your username, if thats what you are trying to do.

A dir in your home folder?

```
 sudo mkdir ~/local/src 
```

Or

seeing as you put a "/" at the beginning you might also be talking about "/usr" directory?

```
 sudo mkdir /usr/local/src 
```

Which directory is it? Because for the first one, you wouldn't normally need root :S

---

### Post by taurus on 2006-04-03
[QUOTE=Sweet]
```
 sudo mkdir /usr/local/src 
```
[/QUOTE]
BUT that is exactly what I had above!!!  :rolleyes:

---

### Post by Sweet on 2006-04-03
[QUOTE=taurus]BUT that is exactly what I had above!!!  :rolleyes:[/QUOTE]


haha, yeah I know, im just asking if he means /usr or his home directory (user directory).

---

### Post by az on 2006-04-03
[QUOTE=Ariam]
What I need is to install  flash and real player and may be other software. 
Pl let me know how to go about doing this or point me to a place if you can on this topic. Thanks ariam.
h[/QUOTE]
Open your file browser and right click on the window and create a new folder.

---

### Post by Ariam on 2006-04-03
Thanks All. I will go with Automatix for now. till I get more comfortable with comand line.

---

