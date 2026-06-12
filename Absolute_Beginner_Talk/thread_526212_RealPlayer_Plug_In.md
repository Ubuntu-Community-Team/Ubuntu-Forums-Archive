---
title: "RealPlayer Plug In"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by nrpgeek on 2007-08-15
I need the RealPlayer plugin for firefox to watch/listen to the BBC streamed content.

How do I install it?

I tried to add if from firefox:
1) Tools -> AddOns
2) Select 'Plugins' from the left hand menu
3) Scroll down to RealPlayer and click the 'Linux' link
4) Click the Download button.

All this did was place a file on my desktop: RealPlayer10GOLD.bin

Now What?

---

### Post by HereInOz on 2007-08-15
You need to run that file to install RealPlayer.

Open a terminal and run it as fakeroot (sudo) and it ought to install RealPlayer.

---

### Post by ukripper on 2007-08-15
use automatix2 and install swiftfox and its plugins. Real player comes within swiftfox plugins

---

### Post by mali2297 on 2007-08-15
To install realplayer, type in the terminal:
```

cd Desktop
sudo ./RealPlayer10GOLD.bin

```
... and answer the questions given to you. 

Hopefully you will then get the plugin in firefox automatically if you just restart the browser.

---

### Post by nrpgeek on 2007-08-15
> dave@dave-server:~$ sudo RealPlayer10GOLD.bin
Password:
sudo: RealPlayer10GOLD.bin: command not found

How do I do that - sorry - the transition from Window$ is sometime puzzling!

---

### Post by nrpgeek on 2007-08-15
> dave@dave-server:~/Desktop$ sudo ./RealPlayer10GOLD.bin
sudo: ./RealPlayer10GOLD.bin: command not found

Nope!

Have I lost the plot? Or am I doing something really stupid?

---

### Post by Ainab on 2007-08-15
do following steps to install realplayer in ubuntu.
1. open terminal.
2. type sudo su to be administrator, and type your password
3. go to folder that realplayer.bin is
4. make the file excutable by using this command chmod +x  Realplayer.bin
5. type ./Realplayer to excute the programm
6 then follow instructions.

I hope that helps you.

---

### Post by mali2297 on 2007-08-15
Where do you got the RealPlayer10GOLD.bin file?

Type in the terminal
```

locate RealPlayer10GOLD.bin

```
to find out.

---

### Post by ukripper on 2007-08-15
Try this guide -
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)

---

### Post by ThrobbingBrain66 on 2007-08-15
<post deleted>

I'm slow on the draw today :)

---

### Post by ukripper on 2007-08-15
i wish I could win million £ today :)

---

### Post by nrpgeek on 2007-08-15
I did change directory to the desktop first. Some knowledge of the old days of DOS is transferable to linux, but some isn't. The hard bit is knowing which. I've used computers for nearly 25 years - but completely new to linux I'm afraid Mali.

Many thanks.

---

### Post by mali2297 on 2007-08-15
Oh sorry, I forgot that you need to make the file executable. Follow the instructions the others gave you.

That is,
```

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```

---

### Post by ugm6hr on 2007-08-15
If you haven't got that working yet - this is a LOT easier (in Feisty / Edgy):
[http://ubuntuforums.org/showpost.php?p=2720883&postcount=4](http://ubuntuforums.org/showpost.php?p=2720883&postcount=4)

Basically - download, double-click - done.

---

### Post by nrpgeek on 2007-08-15
Getting there, used a version of Ainab's instructions and it's working!

What does this mean...

> Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ....Y.
enter the prefix for symbolic links [/usr]: ..........................

What the hell are "system-wide symbolic links"?

(Linux sure isn't boring!)

---

### Post by nrpgeek on 2007-08-15
Should I have hit 'n' instead of 'Y'?

(I have a sneaking feeling...)

---

### Post by mali2297 on 2007-08-15
> **nrpgeek said:**
> Getting there, used a version of Ainab's instructions and it's working!

What does this mean...



What the hell are "system-wide symbolic links"?

(Linux sure isn't boring!)

Just choose the defaults and you'll be fine (capital letter). You can look for a tutorial on symbolic links later.

---

### Post by nrpgeek on 2007-08-15
Thanks mali and everyone else - finally got it sorted - I'm listening to radio 4 quite happily now.:)

---

