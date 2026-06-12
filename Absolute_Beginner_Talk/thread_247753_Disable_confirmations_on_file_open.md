---
title: "Disable confirmations on file open"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by XaeroDegreaz on 2006-08-31
Hi, I just have a question regarding the confirmation dialogue that opens every time I click an application. I mean, it gets really annoying that everytime I click a .txt file I get a dialogue box. I would rather it just open up in gedit everytime!

There are countless other files that I would rather just perform a default operation, without having to do the damn dialogue box everytime. For instance, when I doble click a .exe file, I would just like it to try and open it with WinE :)

I have found it before, quite by mistake, and I disregarded it. I had first started up Ubuntu and I was just playing with everything to get a hang of it.

TIA!

---

### Post by shinythings on 2006-08-31
Well, for text files the solution is quite easy. The reason it asks you whether to run the file is because the 'execute' bit is set in the permissions.

To change this, right-click on the file and go to the 'permissions' tab and untick the 'execute' boxes. Voila.

Alternatively you can do it in the console:

```
chmod -x filename
```

OR if it's a system file

```
sudo chmod -x filename
```

Careful with the second one!

---

### Post by Frank Golden on 2006-08-31
> **XaeroDegreaz said:**
> Hi, I just have a question regarding the confirmation dialogue that opens every time I click an application. I mean, it gets really annoying that everytime I click a .txt file I get a dialogue box. I would rather it just open up in gedit everytime!

There are countless other files that I would rather just perform a default operation, without having to do the damn dialogue box everytime. For instance, when I doble click a .exe file, I would just like it to try and open it with WinE :)

I have found it before, quite by mistake, and I disregarded it. I had first started up Ubuntu and I was just playing with everything to get a hang of it.

TIA!
Hi XaeroDagreaz,
  Can I call you X?:p I think what you are looking for is here.
Open a file browser window (Nautilis) and go to edit>Preferences>Behavior 
and click either "run executable text..." or "view executable text file..."
this will stop the "disagreeable" behavior. You can also change your mouse from double click to single.
And create a right click option to delete a file instead of sending to 
Trash.

These should remain in effect across the board un less you change them.
You also on the view tab have the option to view hidden files.
There are bunches of hidden files in your /home folder for instance.
Have fun.

---

### Post by XaeroDegreaz on 2006-08-31
Hey thanks to both of you, esp the last one, it was exactly what I was looking for.

So this works on any text files, ie, php files as well? I would just have to set the "Open With" bit so it wouldnt always open in gedit when I want it to open with Zend Studio.

And yes, you can call me X lol.

---

### Post by Frank Golden on 2006-08-31
> **XaeroDegreaz said:**
> Hey thanks to both of you, esp the last one, it was exactly what I was looking for.

So this works on any text files, ie, php files as well? I would just have to set the "Open With" bit so it wouldnt always open in gedit when I want it to open with Zend Studio.

And yes, you can call me X lol.
I think so. Try it.

---

