---
title: "I would like a guide on how to install software"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by GILBERTO15 on 2007-01-14
I would like a guide on how to install software, i have xubuntu 6.10 on a ibook. I downloaded the snes9x-1.5-linux-x86.tar.gzip, i then eextracted to my desktop and i dont know what to do next.

---

### Post by Arisna on 2007-01-14
Good news--you don't need to download software from different websites often anymore.  Ubuntu uses a package manager called Synaptic, which you can find under your Applications > System menu, that will let you use a one-stop graphical interface to install most software that you would want.

---

### Post by Abu Imak on 2007-01-14
Synaptic is the single most wonderful thing about using ubuntu that I can imagine.  If you want a guide on how to install software, I would look for a guide on how to use synaptic. Also, if you wanted a SNES emulator, you already have one you just dont know it. Go to Synaptic and click on search and type Gsnes9x. Or just type snes and it should find a few for you to use.

---

### Post by mikewhatever on 2007-01-14
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

hope it helps.

---

### Post by mykalreborn on 2007-01-14
if you stil want to know how to install software in ubuntu you can use good ol' google to find out:[http://www.google.ro/search?q=install+everything+in+ubuntu&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.ro/search?q=install+everything+in+ubuntu&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)
try the first find, because it's one of the best and easier tutorials there are.

---

### Post by Wartooth on 2007-01-14
Three things, from my attempts in recent days, that I haven't found answers to by searching:

1.  When I'm untarring something, how do I know where to put it or know that the GUI is putting it in the right spot?  Sounds stupid, but...
2.  Have been trying to access Monkeyblog as it is so widely recommended, but the site is either down or my ISP is having DNS issues or...?
3.  I THOUGHT I installed Wine a few nights ago, but I have no clue as to where it went, how to find it, or what on Earth happened.

I know I very well could have skipped over something somewhere, but I'm still pretty lost with all of this.

---

### Post by mykalreborn on 2007-01-14
> **Wartooth said:**
> Three things, from my attempts in recent days, that I haven't found answers to by searching:

1.  When I'm untarring something, how do I know where to put it or know that the GUI is putting it in the right spot?  Sounds stupid, but...
2.  Have been trying to access Monkeyblog as it is so widely recommended, but the site is either down or my ISP is having DNS issues or...?
3.  I THOUGHT I installed Wine a few nights ago, but I have no clue as to where it went, how to find it, or what on Earth happened.

I know I very well could have skipped over something somewhere, but I'm still pretty lost with all of this.

1. when you have an archive you can right-click it and select "extract here". ;)
2. i've tried it today, too. it must be their server's problem, but i guess it should work again soon. :-k 
3. well.. wine is pretty hard to set up, at least that's what i think. but everytime you don't know something about a program you can learn a little about it by typing in a terminal
```
man *software* #if you know the exact name of the program
or
man -k *software* #if you don't know the exact name of a program and get a list of the search results.

```
you can check out wine realted issues here: [http://www.winehq.com/](http://www.winehq.com/) ;)
but maybe there is a linux alternative for why you are using wine, so tell us what you need, and maybe we can help you

---

### Post by kliljedahl on 2007-01-14
I'm a super newbie also. I read a thread about Automatix and installed it. It will add almost everything you need to be up and running efficiently in no time. You can pick and choose what you want to install. Good luck, the people here are very patient and considerate.

---

### Post by moshuptrail on 2007-01-14
I came across this:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by old_geekster on 2007-01-14
> **GILBERTO15 said:**
> I would like a guide on how to install software, i have xubuntu 6.10 on a ibook. I downloaded the snes9x-1.5-linux-x86.tar.gzip, i then eextracted to my desktop and i dont know what to do next.
Here is a link to the best guide that I have found:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I just this minute installed "Google Earth" using it and it was very easy.  In fact, I simply copied the command given and pasted it into the terminal.

Good luck!

---

### Post by GILBERTO15 on 2007-01-14
i got gsnes9x to work, but i can never get sound to work on my ibook

---

### Post by Catsworth on 2007-01-16
> **Wartooth said:**
> [...]3.  I THOUGHT I installed Wine a few nights ago, but I have no clue as to where it went, how to find it, or what on Earth happened.[...]

I can relate to this, I think the problem is that I'm used to Windows where newly installed programs either have a desktop icon or an entry in one of the Start menus.

With Ubuntu installed programs just dissapear.....  I know that they're there somewhere though, I just don't know where.

Can someone tell me please how I add a program to one of the menus?

Thanks.

---

### Post by Wartooth on 2007-01-16
> **mykalreborn said:**
> 1. when you have an archive you can right-click it and select "extract here". ;)
2. i've tried it today, too. it must be their server's problem, but i guess it should work again soon. :-k 
3. well.. wine is pretty hard to set up, at least that's what i think. but everytime you don't know something about a program you can learn a little about it by typing in a terminal
```
man *software* #if you know the exact name of the program
or
man -k *software* #if you don't know the exact name of a program and get a list of the search results.

```
you can check out wine realted issues here: [http://www.winehq.com/](http://www.winehq.com/) ;)
but maybe there is a linux alternative for why you are using wine, so tell us what you need, and maybe we can help you

Thank you for your reply, and your help.  I've been busy and not feeling well, so I have been away...

So, when extracting, it *just knows* where to put the file?  The right directory and all?  Interesting. 

Monkeyblog still appears to be down for the count :(

I'm wanting/needing to see if I can install AutoCAD 2000 and use Wine as has been claimed elsewhere.  I'll have to be able to use AutoCAD on a Linux machine if I'm ever to convince my husband to make the switch.  And, the way MS keeps looking, I'm thinking that's going to be necessary someday, although not necessarily soon.  

Now, to see if I can flippin' find WIne...:-k :p 

Catsworth:  Have you used the Alacarte Menu Editor?  Applications > Accessories > Alacarte Menu Editor  I've used it to add a couple of things, but, well, it can't find/doesn't show Wine. ](*,)

---

### Post by jd4x4 on 2007-01-17
YES! Help on editing/finding menus is a great idea. I'm in need of an XUbuntu version.

One thing I've noticed is that while the forums are a SUPER good source of info, the HOW TO's don't take into account the different distros & what they come with. It would help greatly if there was some sort of cross reference to the differences between Ubuntu/KUbuntu/XUbuntu/EdUbuntu .. like file structure (tree) and what's kept where, editors,  etc. While I'm sure that eventually people will figure out things like XUbuntu doesn't have a "gedit" so there is another alternative, it's tough for a newbie to try to follow a how-to and guess at the differences as well.

XUbuntu has the Xfce4-MenuEditor, but no help text & I'm still trying to figure out where the stuff that populates the menus come from. I'll check the Kfce web site next, but it would be nice if someone could tie these differences together here in the forums/docs/someplace.

---

### Post by deadgobby on 2007-01-17
> **moshuptrail said:**
> I came across this:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Monkey has been down for a week now. May be updating???

Gobby

---

