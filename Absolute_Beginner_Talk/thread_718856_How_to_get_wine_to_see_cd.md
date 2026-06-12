---
title: "How to get wine to see cd"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-08
For games using wine. How do you get wine to recognize the game cd? Games won't work without the game cd inserted?

---

### Post by glennric on 2008-03-08
Open Applications->Wine->Configure Wine
and go to the Drives tab.
Click on Autodetect then click on Ok.
This should find the cd drives and set them up for wine.

---

### Post by linuxjerk on 2008-03-08
I'm doing like you said but the game still does not find the cd.

There must be more to it than that.

I'm doing this and it does find all the drives. I click ok. Then exit and start the game.
Keeps asking for the cd???

IOpen Applications->Wine->Configure Wine
and go to the Drives tab.
Click on Autodetect then click on Ok.
This should find the cd drives and set them up for wine.

---

### Post by linuxjerk on 2008-03-11
I still can get my game to find it's cd in wine. Anyone with ideas?

---

### Post by linuxjerk on 2008-03-12
So I should give up?

---

### Post by ptn107 on 2008-03-12
Pop open a terminal and try this...

CD to the wine drives folder
```
cd  ./wine/dosdevices/
```

add a symbolic link to your cdrom
```
ln -s /media/cdrom d:
```
(if d: is taken go to the next letter, e: etc...)

post your results

---

### Post by linuxjerk on 2008-03-12
ok thanks, I will try this now and let you know what happens.

---

### Post by linuxjerk on 2008-03-12
ok now I think I broke my gnome. I got some kind of gnome error saying some things might not work. Guess what? they don't

Whenever I try to minimize things they just disapear. Doesn't matter what they are as soon as I press the minize button they're gone for good.

Anyone know how to fix this? Can I reinstall gnome? Am I screwed and have to reinstall ubuntu?

Now I tried to reboot and I don't even get the top panel buttons. There isn't even a shutdown button.

I'm getting constant hard drive activity. Is there a scan disk like thing in ubuntu??

I'm back to my windows machine because ubuntu is screwed.

Unless someone can tell me how to find out what the error was I guess I'll have to reinstall.

Help!!!

---

### Post by forrestcupp on 2008-03-12
About the CD thing.  A lot of games that work in wine detect the CD ok.  But there are certain games that don't work right and the suggested solution is to find some kind of no CD patch that allows the game to run without a CD.  For those games, there is pretty much nothing else you can do.  A good place to find solutions is [the Wine app database](http://appdb.winehq.org/).  You can do a search for your specific game there and people tell how or if they got it to work.

---

### Post by linuxjerk on 2008-03-12
Well I'm not going to be able to do anything unless I can get gnome going again.

Can I just reinstall Gnome?????

Or do I have to start all over and reinstall utuntu?

Help

---

### Post by linuxjerk on 2008-03-13
ptn107 I tried your fix and when I do this "cd  ./wine/dosdevices/" I get no such directory error.

The wine configuration thing is all screwed up. I set things and apply and come back and there back to where they were.

What's the difference between /media/cdrom d: and /media/cdrom 0 ?

Anyway I can't figure out the wine drive configurations and I'm pretty sure that's why
I'm having so much trouble getting the game to see the cd.

---

### Post by linuxjerk on 2008-03-13
forrestcupp I did find a nocd patch mentioned in WIneAppDB  for half-life1 but I could not find a download link for it.

---

### Post by linuxjerk on 2008-03-13
Well never got my half-life game to find the cd. But got it working with a nocd crack.

So I guess it's solved for now.

[http://www.freeinfosociety.com/site.php?postnum=1079](http://www.freeinfosociety.com/site.php?postnum=1079)

---

### Post by linuxjerk on 2008-03-14
Well this morning the half-life game is back to "insert cd"

Yesterday the crack worked first try.

Played the game for an hour with no problems.

Noticed the game did not exit properly. But didn't think any thing of it.

Tried playing the game today and back to the no cd problem.

Uninstalled the game and deleted all related files.

Reinstalled the game fresh and ran the crack as described.

No go.

This is crazy. Any ideas as to why the crack would only work once?

---

