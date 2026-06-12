---
title: "Uninstall Picasa"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by muddler on 2007-03-26
I installed Picasa and ended up with hundreds, if not thousands, of images. I don't want my disk cluttered up with images I don't want and can't use. I think I need to uninstall and reinstall without the unwanted images. Does anyone have a suggestion?
Thanks.

---

### Post by ajgreeny on 2007-03-26
Where did the images come from?  I tried Picasa some time ago and didn't think it was as good as digikam on my machine, it ran very slowly and didn't seem worth the bother.  However, I do not remember getting lots of images with it.

---

### Post by ajgreeny on 2007-03-26
Where did the images come from?  I tried Picasa some time ago and didn't think it was as good as digikam on my machine, it ran very slowly and didn't seem worth the bother.  However, I do not remember getting lots of images with it.

It was supplied as a deb file so you should be able to uninstall with the usual right click, and then chose uninstall from the context menu.

Sorry this is nearly a duplicate post.  I tried to stop the saving of my first post with the stop button in firefox, but obviously it does not work as I expected.

---

### Post by muddler on 2007-04-23
I don't know where the images originated. They just appeared. I uninstalled and reinstalled Picasa and everything seemed normal and Picasa is working.

---

### Post by rich.bradshaw on 2007-04-23
Those must have been on your disk already - Picasa doesn't come with any sample images or any stock photos...

---

### Post by Sweet Spot on 2007-05-08
Erm, how DO you uninstall it though ?

---

### Post by Sweet Spot on 2007-05-09
Nevermind. > sudo dpkg -r picasa
  That did it. But when I start up Ubuntu I get an error message saying something to the effect of can't find ***** Picasa, or something.

---

### Post by paintandswim09 on 2007-10-28
I couldn't get Picasa to uninstall from Apps>Add/Remove Programs... It would freeze my system when I tried to run it, and  then I couldn't find it in add/remove programs for some reason. I was about to try the sudo dpkg deal mentioned but then I though to try it from Synaptic (don't know why the thought didn't occur to me before...) worked just fine. i can live without Picasa

---

### Post by Astrikor on 2007-10-31
Hi,

I have been having a Picasa problem too - very slow - so I thought I would uninstall it.

Tried synaptic, but Picasa isn't listed.  

Then tried sudo dkpg -r picasa in the terminal and got message :

dkpg - warning ignoring request to remove picasa which isn't installed

I originally installed Picasa using wine.

What am I doing wrong???

Thanks

Astrikor

---

### Post by rents1977 on 2007-11-20
I have Picasa showing under my Applications/Graphics/ menu.

I installed it on a whim, but much prefer F-Spot.

I'd like to uninstall it, however there is no remove option in Synaptic, when I click the icon it asks me to agree to the user agreement, then from memory it will try to index all my photos.

Is there anyway to uninstall it without going through the indexing stage?

```
sudo dpkg -r picasa
```

Results in the message that it isn't installed. It seems to be half and half, and unless I accept the user agreement and wait for it to index I won't be able to remove it.

This is a pain, as I have have some 10,000 images on my drives.

---

### Post by rents1977 on 2007-11-20
```
sudo aptitude remove picasa

```

Seemed to work.

---

