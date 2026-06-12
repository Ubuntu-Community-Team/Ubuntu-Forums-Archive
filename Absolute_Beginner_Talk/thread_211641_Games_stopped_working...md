---
title: "Games stopped working..?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-07-08
Hey there, peeps.. I got another problem.

 I just went to start Metal Blob Solid, and it ain't working. I opened the terminal to try opening blobwars in there, since the error said it couldn't start the child process 'blobwars' but it said command not found. I hopped into Synaptic to check if it had been uninstalled or something, and it hasn't. I clicked 'reinstall' anyhow, just in case something had maybe messed the code up, and tried again. Still not working, it can't find blobwars... So I thought 'double-you tee eff?' and tried another game, Chromium, also not working, and then Neverball, still not working. Gnometris works, as does Nvu and some of my other random programs. It seems to only be non-default games that are messed up.

 Anyone know what the hell is going on? The only thing I can think of is that my recent installation of Enlightenment (e17) could have inserted something long, cold and metal up my system's rear entrance without using lube...

 ...What the hell is wrong, and how can I fix it, short of giving my system an enema? o.O

PS: The only things I have installed since I last used blobwars, are e17, and Easy Ubuntu. I used EU to install flash and java and fonts and midi capability (It's sad to admit, but I'm very keen on some of my ancient games' midi music. xD) and er, something else I don't recall...

---

### Post by Raavea on 2006-07-08
Update:

 I decided to do a little poking around. I found usr/games and that had a thing called blobwars in it. Which I double-clicked. Which opened blobwars just fine.

 Perhaps something has been changed that points all commands to their correct places...?

 If so, where is it, what is it, how do I fix it?

---

### Post by Raavea on 2006-07-09
They still won't work from the menu like they used to... o.O

---

### Post by lamego on 2006-07-09
From a terminal window type:
```
whereis blobwars
```
If it doesn't find the program its because you have changed something which trashed the PATH variable that would be needed to find the games.
You can check it with:
```
echo $PATH
```
It should return:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by RaZer0r on 2006-07-09
it has to do with the links to the programs that are corrupt/missing, i found a way to get them back automaticly but i cant remember it atm, i'll search right away

---

### Post by Raavea on 2006-07-12
> **lamego said:**
> From a terminal window type:
```
whereis blobwars
```
If it doesn't find the program its because you have changed something which trashed the PATH variable that would be needed to find the games.
You can check it with:
```
echo $PATH
```
It should return:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

Thanks. I see what the problem is, but dunnoh how to fix it! D:

 ```
raavea@bernard:~$ whereis blobwars
blobwars: /usr/games/blobwars
raavea@bernard:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin

```

---

