---
title: "[SOLVED] just downloaded the FF3.5 beta"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-04-02
Anyway, on my other computer I have been having a terrible time with my browsers lately and so I wanted to do this right the first time. I would like to install the new version of FF but it is not in the repositories so I downloaded it directly to my desktop. I extracted the archive and now  I have a neat little folder that says "Firefox" on it,  but when I click on it there is no obvious "click here to install me" icon.

If I double click on a file just called "Firefox" a little warning comes up telling me that that is an executable text file. I then click "run" and lo and behold Firefox 3.5 starts up. The problem is that as things now stand that is the only way to get FF3.5 to run. So, my question becomes, have I installed FF 3.5 as it is or do I need to do something more? Secondly, if it is now installed how do I set it up to run 3.5 when I click on a firefox icon? Right now simply clicking on the Firefox icon runs Firefox 2.

---

### Post by The Cog on 2008-04-02
You have installed it.

Personally, I would put the directory somewhere else - it's a bit in the way there. I put mine in /opt where all users can use it. This command does it:
```
sudo cp -r ~/Desktop/firefox /opt/firefox3b5
```
Now you need to make the new firefox the one that get launched. Putting a symlink in /usr/local/bin (which is in your path before the other firelfox links) will do the trick:
```
sudo ln -s /opt/firefox3b5 /usr/local/bin/firefox
```
Delete the link and the directory in /opt to ununstall again.

---

### Post by boriquajake on 2008-04-02
> You have installed it.

Personally, I would put the directory somewhere else - it's a bit in the way there. I put mine in /opt where all users can use it. This command does it:
Code:

sudo cp -r ~/Desktop/firefox /opt/firefox3b5

Now you need to make the new firefox the one that get launched. Putting a symlink in /usr/local/bin (which is in your path before the other firelfox links) will do the trick:
Code:

sudo ln -s /opt/firefox3b5 /usr/local/bin/firefox

Delete the link and the directory in /opt to ununstall again.


Holy crap, you are a freaking genius!!

---

### Post by The Cog on 2008-04-03
No I'm not. I got that wrong. The symlink needs to link to the new firefox executable, not justs the directory it's in. So if you already created the symlink, delete it with
```
sudo rm /usr/local/bin/firefox
```
and make the proper one with
```
sudo ln -s /opt/firefox3b5/firefox /usr/local/bin/firefox
```

---

