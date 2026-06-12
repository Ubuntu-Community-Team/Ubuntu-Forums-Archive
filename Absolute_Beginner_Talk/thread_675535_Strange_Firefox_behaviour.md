---
title: "Strange Firefox behaviour"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by MockY on 2008-01-22
Firefox in Linux is quite a thing of it's own. I have a couple of questions I would like to get some answers to.

First of is the behavior where drop-down menus goes under any Flash commercial or banner. This is constant and has been an issue ever since 6.06 and it does not seem to change. Why is this? It makes FF unusable on some sites. Here is an example.

[IMG]http://www.sotd.se/ffflash.png[/IMG]

The next issue is only present on my main computer. I have no problems on any other computer what so ever and have never encountered this on any of hundred installs of any version of Ubuntu. This includes both Ubuntu and Xubuntu. It does not matter if I do a fresh install or not, the problem is still present. It has to do with character coding. I run a couple of Vibe Streamer servers and some folders have the letters Ö, Ä and Å, as well as characters such as ' and é. FF can't display these what so ever, making the folder impossible to open. I have changed the Charset to ISO-8859 and it still does not work. I do this with all the installs I do with every computer I touch, and it works just fine. BUT not on my main machine. I have tried reinstalling it so many time it's not funny anymore. So for this specific task, I have to use Opera. Anyone have a clue?

I have some more issues but mention them later.

---

### Post by sports fan Matt on 2008-01-22
1.  Happens to me too, but I fear its a fix for possibly adobe (which is flaky at best, we just may need to wait it out, I know, pain)

2.  I am not sure

---

### Post by MockY on 2008-01-22
> **sox fan Matt said:**
>  Happens to me too, but I fear its a fix for possibly adobe (which is flaky at best, we just may need to wait it out, I know, pain)

This has been an issue for years and nothing have changed. I have no idea why this is not fixed by now.

Another thing that bugs me

Firefox in Linux renders websites differently than from Firefox in Windows. Why the heck is that? It's the same browser. I have to develop all my websites for not just IE6, IE7 and Opera, I have to develop two versions for the same browser. Does not make any sense what so ever.

---

### Post by scizzo on 2008-01-22
what rendering are you refering to is different......?

since they are both using Gecko that is the engine.....but the font usage is...well different...

---

### Post by MockY on 2008-01-22
> **scizzo said:**
> what rendering are you refering to is different......?

since they are both using Gecko that is the engine.....but the font usage is...well different...

A simple thing as this:

Lets say I have a <div> where the width of 500px, and inside I have two text fields of the same width. The result of that is different in the windows version of it. If I make the text fields as wide as possible so that they still fit within that layer right next to each other, opening the same page in another OS but with FF, it looks different. It could be not as wide or it could spill over so the other text field are pushed to a second row. This is when fonts are not even used. However, this is not as annoying as the differences between the engines, but in my mind, gecko should display the page exactly the same.

Overall, this is not a huge deal, but something that bugs the living poo out of me sometimes.

---

### Post by cartisdm on 2008-01-22
unfortunately it happens t me too:/  Happens when I play jetman on Facebook:D

---

### Post by MockY on 2008-01-25
I ended up installing Flock. A visually pleasing browser that fixed at least on of my problems - The charset bug. But the drop-down behind a flash banner still remains.

---

### Post by mcduck on 2008-01-25
> **MockY said:**
> Firefox in Linux is quite a thing of it's own. I have a couple of questions I would like to get some answers to.

First of is the behavior where drop-down menus goes under any Flash commercial or banner. This is constant and has been an issue ever since 6.06 and it does not seem to change. Why is this? It makes FF unusable on some sites. Here is an example.

[IMG]http://www.sotd.se/ffflash.png[/IMG]
That is a bug in Adobe's Flash player for Linux. When Macromedia owned Flash they promised to fix it, and nothing happened, and now that Adobe owns Flash they have also promised to fix it and still nothing has happened. The bug causes Flash to always play on top of everything, and as the Flash player is closed source and proprietary sofware nobody else can do anyhting about it..

Send e-mail to Adobe and ask them to fix their program. If enough people do that they may some day actually fix it..

---

### Post by mcduck on 2008-01-25
> **MockY said:**
> A simple thing as this:

Lets say I have a <div> where the width of 500px, and inside I have two text fields of the same width. The result of that is different in the windows version of it. If I make the text fields as wide as possible so that they still fit within that layer right next to each other, opening the same page in another OS but with FF, it looks different. It could be not as wide or it could spill over so the other text field are pushed to a second row. This is when fonts are not even used. However, this is not as annoying as the differences between the engines, but in my mind, gecko should display the page exactly the same.

Overall, this is not a huge deal, but something that bugs the living poo out of me sometimes.
That is usually because of different fonts. Have you tried configuring your browser to use same default fonts on both operating systems?

Of course web designer has to acknowledge the fact that different operating systems have different fonts, so any web page you make should be designed to work correctly even if the font changes.

There are also some differences in font rendering between different systems, but these are not usually big enough to cause any major changes in web page layouts.

I also recommend zeroing out margins, paddings and borders in your CSS to make sure you'll get the same looking page even on different platforms, as different browsers have different default settings. You can do that easily with the following code:
```
* { margin: 0; padding: 0; border: 0;}
```

---

### Post by Anicka on 2008-01-25
I haven't tried this, but I think it might work. In FF you could install an add-on called "NoScript". It blocks all flash, java and such things from appearing. Most of the time the flash-animations are from an other server than the webpage itself, so if you allow e.g. bbc.co.uk, the ads are still blocked.

As I said, I haven't tried it for this particular problem, but it might work.

---

