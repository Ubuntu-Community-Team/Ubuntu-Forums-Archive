---
title: "Making Kubuntu/Ubuntu look like OS X"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Tixer on 2006-08-20
Basically, I recently installed Kubuntu as a virtual PC, since it was having problems installing as a dual boot, and I really wanted to get a feel for Linux since I got some friends to convert, so they'll be coming to me for tech support, ugh!

Anyways, so I installed Kubuntu, since my brother really likes Konqueror, and I want to make it look like OSX. So I look for some  guides, and they all phail.

I found something called Baghira, which, although it looks promising in that I can get it 100% Perfect, I couldn't follow since some things died and some commands listed wouldn't work, so I gave up on that.

Then, I installed GNOME, since I saw this,[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php), which looks really easy and I wanted to do it, but, all my bars are black, preventing me from seeing the text, and windows keep closing on me randomly, causing me to abandon that route. 

Can anyone show me how to apply a simple mac style to KDE?

---

### Post by aysiu on 2006-08-20
Easy way to apply a Mac style in KDE. Follow these two steps:

1. [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) to get extra repositories.

2. Paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install kwin-baghira
``` Now Baghira should show up in your window decoration and styles settings.

---

### Post by Tixer on 2006-08-20
I've already tried that, and I found that some of the commands went nowhere, I couldn't find certain menu items, and I couldn't get the bar at the top working. Is there some really easy way, like just a simple program or something really simple and detailed? I can follow directions just fine, and I feel good in konsole, since I used to use DOS alot, but nothing pisses me off more than seeing something tell me to go to "LooknFeel", which doesn't exist. I managed to find it, but this was but 1 little thing.

---

### Post by aysiu on 2006-08-20
"Some of the commands went nowhere"? Not sure what you mean by that.

What told you to go to "LooknFeel"?

Once you have Baghira installed, press Alt-F2 and type ```
kcontrol
``` Then, select Baghira in Style and Window Decorations. In the menu bar behavior section, select the Mac OS behavior.

---

### Post by Tixer on 2006-08-20
[http://baghira.sourceforge.net/OS_Clone-en.php](http://baghira.sourceforge.net/OS_Clone-en.php).

Don't worry about getting me to roll back it, already done.

Also, how do I generate a space out of nowhere? I know this sounds pretty retarded, but, this keyboard doesn't have a space bar since it broke, and I've been Ctrl-V"ing" this message. In 'Windwoes' I use Alt-32, then copy and paste it, but on Linux, how do I generate one?

---

### Post by aysiu on 2006-08-20
I'm not sure what you mean by a space out of nowhere... maybe you can change your keyboard layout and map another (less used) key to be your spacebar? I'm not sure how to do this, but I think it can be done.

---

### Post by Tixer on 2006-08-20
I've currently been copying a space from somewhere, but there are times, for example, in the terminal, where that doesn't always work. Thats actually the best idea yet, to map a space to something like F15 (Mac keyboard)

---

### Post by aysiu on 2006-08-20
[I have no idea what this means](http://ubuntuforums.org/showthread.php?t=79251), but it seemed to help the person who asked a similar question.

---

### Post by Tixer on 2006-08-20
W00t, that'll work. KDE probably has an option in kcontrol. Anyways, any good tutorials that can give me the look of the Bagira thing without that blasted tutorial, since that completely confused me. Furthermore, is there some way to, write a script to do all that for me?

---

### Post by aysiu on 2006-08-20
Instead of using that tutorial, just follow the instructions in the 2nd and 4th posts of this very thread.

---

### Post by Tixer on 2006-08-20
I managed to get it skinned a bit, using instructions similar to that, but I couldn't get the top bar going more than looking like shit, etc.

---

