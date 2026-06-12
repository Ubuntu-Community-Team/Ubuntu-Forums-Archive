---
title: "Can't extract plugins to protected folders"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2006-07-08
For a while now I've been trying to figure out how to install plugins and skins I have for aMSN into /usr/share/amsn/plugins but when I try I get a "You don't have permision" error :cry: 

To be more specific I attached a screeny.

Is there a way I could tell ubuntu that I'm root for just a second or something? I'm kind of suprised that Archive Manager doesn't ask me for sudo like everything else.

Thanks for the reply _(._.)_

---

### Post by taurus on 2006-07-08
If you plan to write to /usr/share/amsn/plugins, you need to be root so open a terminal by Applications -> Accessories -> Terminal and type
```

sudo cp <wherever the plugins are> /usr/share/amsn/plugins/

```

---

### Post by Nexusx6 on 2006-07-08
I really should more bash commands, answer was right there lol.

Still running into trouble though, terminal looks like this:

> fox@fox-desktop:~$ sudo cp /home/fox/Desktop/amsnplus /usr/share/amsn/plugins
cp: omitting directory `/home/fox/Desktop/amsnplus'


---

### Post by taurus on 2006-07-08
If you want to copy stuff from /home/fox/Desktop/amsnplus/ to /usr/share/amsn/plugins, then you need to do
```

sudo cp /home/fox/Desktop/amsnplus/* /usr/share/amsn/plugins

```

---

### Post by ramcosca on 2006-09-08
What if I wanted to move a folder called "Ubuntu (Human)" with all it's contents? It says that "(" is an invalid token...

---

### Post by bodhi.zazen on 2006-09-08
> **ramcosca said:**
> What if I wanted to move a folder called "Ubuntu (Human)" with all it's contents? It says that "(" is an invalid token...

He he he... Why do you think they call em protected files. :mrgreen:

You can likely save them in a hidden folder in your /home/user_name.

For example, I keep skins in /home/bodhi/.xmms/Skins 8-[

Second, the command line has options, no

Try man cp

The command you seek, however, is

```
sudo cp -r .../Ubuntu /etc/destination
```
:wink:

---

### Post by jordanmthomas on 2006-09-08
> **ramcosca said:**
> What if I wanted to move a folder called "Ubuntu (Human)" with all it's contents? It says that "(" is an invalid token...

Put a \ before anything you want to "escape"
so it would be like this:
```

mv Ubuntu\ \(Human\) *wherever*

```
or, you can put Ubuntu (Human) in quotation marks

---

### Post by ramcosca on 2006-09-08
> **bodhi.zazen said:**
> He he he... Why do you think they call em protected files. :mrgreen:

You can likely save them in a hidden folder in your /home/user_name.

For example, I keep skins in /home/bodhi/.xmms/Skins 8-[

Second, the command line has options, no

Try man cp

The command you seek, however, is

```
sudo cp -r .../Ubuntu /etc/destination
```
:wink:> **jordanmthomas said:**
> Put a \ before anything you want to "escape"
so it would be like this:
```

mv Ubuntu\ \(Human\) *wherever*

```
or, you can put Ubuntu (Human) in quotation marks
Thanks to both, exactly what I meant. Now, another question I think you'll answer fast...
The folder has other folders inside it. When I do... ```
sudo cp /where/it/is/* /where/i/want/it
```... it says...```
cp: ommiting directory `/where/it/is/FolderItDoesNotWantToMove'
```How can I solve this mysterious problem? I tried cp'ing each folder's contents but it's exhausting! :-k


[Edit] Nevermind! I should've read better. ](*,)  Thanks! :KS

---

