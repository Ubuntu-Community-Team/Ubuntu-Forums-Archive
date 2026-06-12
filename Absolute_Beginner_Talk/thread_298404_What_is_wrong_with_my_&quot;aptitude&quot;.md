---
title: "What is wrong with my &quot;aptitude&quot; ?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-12
Hi folks !

I started with Ubuntu Dapper, a while ago I tried out kubuntu-desktop (er... I even switched to KDM, I like it a lot) and now I'd want to test XFCE as well (my computer is kind of slow, so I thought I'd give it a shot, to have XFCE there just in case).

So now I'm trying to istall xubuntu-desktop through aptitude, just as described in many guides I read, because it's a lot easier afterwards to do "aptitude remove" 1 package instead of many many others through "apt-get".

When I enter ```
sudo aptitude install xubuntu-desktop
``` in a shell, or even when I issue aptitude install for anything else, I get a long message displaying more than 100 packages to be removed in order for the new ones to be installed... and they seem important packages too (packages like adept, ark, kate, k3b etc).

This doesn't occure when I use **apt-get** instead, but still it bothers me and I wonder what's wrong.

Could anyone please give me a clue on what's going on?

Thanks in advance,

LLRNR

---

### Post by K.Mandla on 2006-11-12
I've seen that too. It has something to do with the way aptitude manages dependencies, I think.

Usually when I'm moving to something big (like xubuntu-desktop, as you are) I use apt-get for that reason. I don't know that there's anything to be done about it. It doesn't strike me as a bug, although it is a little disconcerting.

---

### Post by LLRNR on 2006-11-12
Thanks for your reply! I had no idea this can happen and it doesn't mind me that much, but I hope it's not a main disadvantage. 

I mean, I hope I won't be obliged at a certain moment to use **aptitude** instead of **apt-get** and not be able to do that, right ? :-k 

LLRNR

---

### Post by K.Mandla on 2006-11-13
No, don't worry about it. The two commands are 99 percent interchangeable.

Some people prefer using aptitude because when you remove something with it, it takes away all the dependencies too.

When you *apt-get remove* something, it leaves all the dependent files on your system.

There's a good explanation of it [here]("http://www.psychocats.net/ubuntu/aptitude").

---

