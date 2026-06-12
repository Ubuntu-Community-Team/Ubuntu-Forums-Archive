---
title: "installed skype deb package but now cant  see it anywhere"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by retep57 on 2006-09-19
hi i d/l  skype and it said it was installed but i cant see it anywhere,  hmm  am struggling a bit with this o/s.. it was  a deb package so it just installed itself  , so it said  but where,   i am lost  ... again  please help cheers

---

### Post by jd65pl on 2006-09-19
Try typing 

```
skype
```

In the terminal to see if it starts

Try

```
Whereis skype
```

To locate instances of "skype"

---

### Post by macdo on 2006-09-19
Three solutions: 
[LIST=1]
[*]the K menu
On Kubuntu, Skype should add a shortcut under 'Internet'; I can't remember the equivalent menu with Gnome, but it should be there somewhere! However, I''m guessing that you've already looked around in the menus, so here's a quick fix...
[*]Run Application
Press Alt+F2. A box appears. Type the word skype into the box. Skype starts. This has to be the easiest way!
But I imagine that you'd like the graphic goodness, so I suggest that you install the Debian Menu...
[*]The Debian menu
At the command line: 
```
sudo apt-get install menu
```You'll find it under 'Applications', and it will contain Skype (and all the other progs as well). 
[/LIST]
Have fun!

---

### Post by retep57 on 2006-09-19
> **jd65pl said:**
> Try typing 

```
skype
```

In the terminal to see if it starts

Try

```
Whereis skype
```

To locate instances of "skype"
 cool,  too easy, ha there it is, next too configure sound , hmm  making progress, this forum is  great, get help  real fast, thanx,

---

### Post by 3rdalbum on 2006-09-19
A little tip: You don't need to know where a program has installed itself. Any program that hasn't asked you where to install to, can be started simply by typing its name into the terminal.

If the program's name differs from the name of the package you installed, you can go into Synaptic, get the Properties of the package, and click the "Installed Files" tab. Any file with "/bin" in its path is a program.

---

### Post by Brunellus on 2006-09-19
> **3rdalbum said:**
> A little tip: You don't need to know where a program has installed itself. Any program that hasn't asked you where to install to, can be started simply by typing its name into the terminal.

If the program's name differs from the name of the package you installed, you can go into Synaptic, get the Properties of the package, and click the "Installed Files" tab. Any file with "/bin" in its path is a program.
it's also a fair bet that anything in /usr  or /opt is a program.

---

### Post by retep57 on 2006-09-20
hey macdo, thanx   that alt F2 works a treat!!!
  my  sound not work with linux skyppe but at least i found it  and  making progress, thanx

---

### Post by retep57 on 2006-09-23
killall esd
 at terminal did the trick, now the sound works fine yay, happy now , good progress
  also i got java working after   going to  the other repositories, univers etc,,   cool  did the download of the java  and worked easy, no need for the command line  trickery for newbies like me

---

