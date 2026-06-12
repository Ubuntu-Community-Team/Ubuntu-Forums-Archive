---
title: "Compiz-Fusion Magic Lamp"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-10-21
How do I get that Genie/Magic Lamp affect to work in Compiz-fusion?

What about 3-D Windows?

And how about the Window "Peaking"? When a window is minimized, I like to be able to grab the corner and peak behind it like turning a page in a book. Now in Compiz-fusion, it "unsnaps" the window and it's no longer minimized?

---

### Post by sammydee on 2007-10-22
You will need to install the compiz settings manager if you havent already. Open a terminal and type:

> sudo aptitude install compizconfig-settings-manager

Once you have done that, an option will apper in system/preferences that says "Advanced Desktop Effects Settings".

All the settings you need are in there. If you need further help how to activate/adjust a particular plugin, try reading the help files or documentation. It should be pretty easy to find everything.

And next time you ask for help, a please wouldn't go amiss :guitar:

---

### Post by Baby Boy on 2007-10-22
Well, actually, enabling the Magic Lamp effect isn't *that* easy. I for example already had Compiz Settings Manager installed and I knew where to look but whenever I tried to enable it, I was too lazy to find out how. But this time I got it to work :).

So once you have the Compiz Setting Manager installed, do the following:

1.) *System->Preferences->Advanced Desktop Effects Settings *
2.) Once in *ADES*, click on *Animations* under the *Effects* category.
3.) Let's say you want the Magic Lamp effect for the Minimize action. Choose the *Minimize Action* tab and click on the *Add* button below the *Animation Selection* box.
4.) In the *Edit* window, choose the *Magic Lamp* effect from the dropdown menu. Set the duration to 400.
5.) Paste this
> (type=Normal | Dialog | ModalDialog | Utility | Unknown)
to the *Window Match* input box in the *Edit* window and click OK.
6.) Click the Up button with Magic Lamp effect selected in the Animation Selection box to make it the default effect instead of Zoom.

You're all set.

---

### Post by Baby Boy on 2007-10-22
EDIT: Double post, sorry. Please delete.

---

### Post by homerj742 on 2007-10-22
Thank you very much for that information guys. I will try it as soon as I get home.

---

### Post by Het Irv on 2007-10-22
Just a warning:
If you enable the cube be sure to also enable rotate cube or its worthless.

---

### Post by ronmarley1 on 2007-10-22
> **homerj742 said:**
> How do I get that Genie/Magic Lamp affect to work in Compiz-fusion?

What about 3-D Windows?

And how about the Window "Peaking"? When a window is minimized, I like to be able to grab the corner and peak behind it like turning a page in a book. Now in Compiz-fusion, it "unsnaps" the window and it's no longer minimized?

I had issues with the "peel back" not working when I upgraded to to Gutsy from Feisty.  I think it's due to the fact that GTK was the default window decorator.  I changed back to Emerald and the "peel back" functionality returned.  3D windows has been removed.

---

### Post by TadH on 2007-10-22
So there is no 3d windoows effect on gutsy ?

---

### Post by akiratheoni on 2007-10-22
> **TadH said:**
> So there is no 3d windoows effect on gutsy ?

Nope; if I recall correctly, 3D Windows didn't work on Feisty either (I tried), and I heard that it was too buggy anyway.

---

### Post by nchase on 2007-10-22
the 3d windows effect plugin is being rewritten to be better.

---

### Post by Presto123 on 2007-10-22
I got the 3D Windows to work...but it was in Beryl. It's nowhere near as fancy as the Compiz version, but still cool.

---

### Post by ronmarley1 on 2007-10-23
> **akiratheoni said:**
> Nope; if I recall correctly, 3D Windows didn't work on Feisty either (I tried), and I heard that it was too buggy anyway.

I had 3D Windows working in Feisty with Beryl and then Compiz-Fusion.  Then, after a few Compiz-Fusion updates, it sorta got broke and didn't work for me.  When I upgraded to Gutsy, it was gone.  I did not know it was being rewritten.  Thanks for the info.

---

### Post by warbird on 2008-02-20
Sorry for resurrecting this thread, but was googling around about the subject and found this thread and [this]("http://www.suseforums.net/index.php?showtopic=45699&pid=228436&mode=threaded&show=&st=&") guide on how to get OSX-like magic lamp effects (removing the "waves"). Hopefully useful for someone.

---

### Post by Sceiron on 2008-02-20
lol
can someone paste a picture/file of this lamp
I'm curious !

---

### Post by jordanmthomas on 2008-02-20
It looks just like the one in OS X.
This video's a little blurry and it's slowed down, but this is what it'll look like in compiz if you follow the steps linked.
[http://youtube.com/watch?v=i3IPRdT07hc](http://youtube.com/watch?v=i3IPRdT07hc)

I used to do this right after they took the option out of beryl because of fear Apple would sue.  :)
I don't build compiz from git myself any more, so I don't bother with it.

**edit**
Just read the link.  That's a new way, I just edited the source back in the day.  The option's right there in plain sight.
I suppose this way works too though.

---

### Post by jimv on 2008-03-05
To keep windows from "unsnapping" when you pull down the title bar, go into the CompizConfig Settings Manager, and go to the settings for "Move Window".  Uncheck "Snapoff Maximized Windows".

---

