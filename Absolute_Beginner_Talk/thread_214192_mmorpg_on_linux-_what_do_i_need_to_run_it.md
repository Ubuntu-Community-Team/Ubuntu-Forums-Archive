---
title: "mmorpg on linux- what do i need to run it?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-07-12
Hello, so far this has been the only negetive expirience ive had with ubuntu, I can't get my favorite mmorpg to run on linux, runescape.

I run opera and I installed the java sdk (since i want to learn to program) in my /usr/local/  and it still wont work! Is there enything else I must install or do I have my java software in the wrong location?

Its only a game and im willing to give it up for linux but it is still something I dont want to lose

Thank you

---

### Post by Sonic Alpha on 2006-07-12
I know in Windows, Opera and Java don't get on very well.  Try using a different browser (FireFox for example), and see if that cures the problem :)

---

### Post by Miguel on 2006-07-12
Hi drosophyllum,

Let's go step by step.[list=1][*] Did you install Opera via Synaptic*? Is it working
[*] How did you install Java? Is it working?
[/list]

Anyway, I'll be reallistic. While we will proably be able to get your Opera and Java working, the mmorpg one will be more difficult. Especially as it depends on the program. As an example, I'll tell you that I can play Baldur's Gate 2 in Linux, but haven't had any luck with Links LS (Golf) or The Longest Journey.

---

### Post by Sonic Alpha on 2006-07-12
> **Miguel said:**
> Hi drosophyllum,

Let's go step by step.[list=1][*] Did you install Opera via Synaptic*? Is it working
[*] How did you install Java? Is it working?
[*] What mmorpg are you trying to play?
[/list]

Anyway, I'll be reallistic. While we will proably be able to get your Opera and Java working, the mmorpg one will be more difficult. Especially as it depends on the program. As an example, I'll tell you that I can play Baldur's Gate 2 in Linux, but haven't had any luck with Links LS (Golf) or The Longest Journey.

Look at the post, drosophyllum stated that he/she is trying to run "runescape."

More info on it can be found [here]("http://www.runescape.com/"), but basically it is linux compatible (it works through the web browser, I believe).

---

### Post by drosophyllum on 2006-07-12
I tried it and it still wont work. I dont see what im doing wrong.... Ive tryied plenty of times intalling it. Are there any web browsers with java preinstalled?

---

### Post by Sonic Alpha on 2006-07-12
Java may have been installed incorrectly.

Have you tried [this]("http://easyubuntu.freecontrib.org/index.html")?

---

### Post by drosophyllum on 2006-07-12
Oh and no, I installed opera manually. But java wont work even in my synaptic installed browsers.

---

### Post by drosophyllum on 2006-07-12
Thank you, easy ubuntu installed the java and my mmorpg is up and running!

:-D

---

### Post by _simon_ on 2006-07-12
I just tried it and it seems to be working correctly.

I have Java Version 5.0 Update 7 - [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp) - choose "Linux (self-extracting file)"

Once installed, go to Opera

Tools -> Preferences -> Advanced -> Content -> Java Options

If Java installed to the default path (which it should have) then you need to enter: /usr/lib/j2re1.5-sun/lib/i386

If you press Validate Path it should confirm.

Press OK and tick ENABLE JAVA.

Now try runescape again.

EDIT: I see I was too late!

---

### Post by user1397 on 2006-07-12
is opera even in synaptic?

i dont see it in mine.  can anyone else confirm this?

---

### Post by Miguel on 2006-07-12
Hi erik,

To see java (search by name and description) you must have enabled both "universe" and "multiverse" repositories. Opera has, at least, Ubuntu debs ready to download. If you don't have a clue how to do it or what it means, don't doubt to drop us a line.

---

### Post by The Noble on 2006-07-12
There are some commercial repos that you can add that are being implimented by the devs. They only have 2 things in it right now, opera and something else. I'm on windows right now, so I don't have access to my sources.list, but try searching and it may turn up.

---

### Post by Tao-Tao on 2006-07-12
> **erik1397 said:**
> is opera even in synaptic?

i dont see it in mine.  can anyone else confirm this?


Yes it is.  But I think it still is some 8.* version.  You can get the 9.0 straight from Opera's [website]("http://www.opera.com/download/?platform=linux").

Choose 'Ubuntu' from the drop down list and choose the right version ( leave the " ...TAR.GZ" box unchecked ), download it and install it by writing in terminal:

```
sudo dpkg -i thepackagename.deb
```

---

### Post by Sonic Alpha on 2006-07-12
> **drosophyllum said:**
> Thank you, easy ubuntu installed the java and my mmorpg is up and running!

:-D

Any time, I was glad I could help :)

---

