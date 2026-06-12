---
title: "New installed programs not showing up in the menu"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by bete on 2005-10-26
When i install a new program with apt-get or synaptic, they often do not show up in the applications menu.
Anyone know why and how i can fix it?

Also, i tried downloading opera from their homepage, chose ubuntu , and i got a .deb file.. what do i do with it?:P

---

### Post by corstar on 2005-10-26
with a .deb file you have to install it at the terminal
The process for doing that is :
1. change to the directory where the file is 
2.type su (enables superuser) then your password when asked
3.type "dpkg -i **whatever**the**package**name**is**"
4. if the dependencies are met, it will install with no drama's

---

### Post by Jenda on 2005-10-26
> When i install a new program with apt-get or synaptic, they often do not show up in the applications menu.
Anyone know why and how i can fix it?
Some programs just don't do that. If you really want the program to have an entry, open up SMEG (Applications>System Tools>Application Menu Editor) in Breezy (If you use Hoary you'll have to install SMEG first), select the desired category, click "new entry" and add a name and command. If you don't know the command, just ask here. Someone will tell you. Maybe there is even an easy way to find out directly, but I don't know about that. What I always did was open "package properties" in Synaptic and check the "files installed" tab. The name of the file in /bin or /usr/bin is the command.

> Also, i tried downloading opera from their homepage, chose ubuntu , and i got a .deb file.. what do i do with it?:P
```
sudo dpkg -i /full/path/of/your/package.deb
```

---

### Post by Jenda on 2005-10-26
or ```
cd /the/directory/where/the/file/is/
sudo dpkg -i name-of-package.deb
```
better than using "su"

---

### Post by bete on 2005-10-26
Thanks, i got opera working with a minor plugin error at the start..

Anyways, bit off-topic.

I remember seeing someone writing a small command and the got up a small window showing their FPS with the graphics card.

How can i do that? because i want to see if my graphics card really is installed.

---

### Post by Jenda on 2005-10-26
Well, in hoary you would type glxgears to test that. It would tell you the FPS every 5 seconds. The command still works in Breezy, but it doesn't show the fps.
What graphics card do you have?

Ah found it! type:
```
glxgears -printfps
```

---

### Post by bete on 2005-10-26
[QUOTE=Jenda]Well, in hoary you would type glxgears to test that. It would tell you the FPS every 5 seconds. The command still works in Breezy, but it doesn't show the fps.
What graphics card do you have?

Ah found it! type:
```
glxgears -printfps
```[/QUOTE]

> 468 frames in 5.7 seconds = 82.696 FPS
360 frames in 5.3 seconds = 68.224 FPS
360 frames in 5.0 seconds = 71.633 FPS
360 frames in 5.0 seconds = 71.535 FPS
360 frames in 5.0 seconds = 71.632 FPS
360 frames in 5.3 seconds = 67.784 FPS
360 frames in 5.7 seconds = 62.828 FPS
360 frames in 5.0 seconds = 71.504 FPS


I got a ATI Rage XL AGP x2.

It is a old graphics card.
But is the FPS supposed to be THAT low on that little graph it is trying to show?
On my screen it almost doesnt go around.

---

### Post by Jenda on 2005-10-26
hmm... I don't know. I usually get above 500 FPS. I have 1600 MHz, 768 Mb RAM and a 64-meg nVIDIA GeForce 2/MX. What CPU do you have?
BTW ATI cards aren't supposed to work too well, but this looks a little too weak. Maybe someone who actually knows what they're talking about should tell you...

---

