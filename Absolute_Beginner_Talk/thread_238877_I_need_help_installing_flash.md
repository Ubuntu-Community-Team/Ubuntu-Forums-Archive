---
title: "I need help installing flash"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by alexandermimix on 2006-08-18
We were unable to detect the correct version of flash on your computer. 

The latest version of the Flash player can be downloaded free from Macromedia.

---

### Post by telegramsam on 2006-08-18
[www.getautomatix.com](www.getautomatix.com)

You can get that from here.  That will get your internet movies rolling...

---

### Post by meng on 2006-08-18
Yep, that must be THE reason. To think it was staring me in the face all this time and I never realized it. How stupid am I?

---

### Post by Dinerty on 2006-08-18
**Originally created by **Artificial Intelligance**

Manually:

Download Flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman 

```


cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer


```

When you see this:
Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: /usr/lib/mozilla-firefox

Done.

Now you need install the fonts that flash needs:

```


sudo apt-get install gsfonts-x11
sudo fc-cache -f -v


```

Done

---

### Post by zxee on 2006-08-18
If you want to install flash read the last two posts here: [http://www.ubuntuforums.org/showthread.php?t=225152&highlight=flash+player](http://www.ubuntuforums.org/showthread.php?t=225152&highlight=flash+player)

---

### Post by alexandermimix on 2006-08-18
> **meng said:**
> Yep, that must be THE reason. To think it was staring me in the face all this time and I never realized it. How stupid am I?

pretty damn stupid? Obviously what I was saying was 'lack of support for commonly used formats'.

---

### Post by bulldog on 2006-08-18
> **meng said:**
> Yep, that must be THE reason. To think it was staring me in the face all this time and I never realized it. How stupid am I?

LOL,is a good one.

To TS,

There are people who give up without even trying!

Fortunately there are people who won't give up and running Linux day by day,and they are happy with it.

And yes Linux isn't for everybody.
You have to learn a whole new OS and maybe you won't do that.

But your statement could be right,on the other hand,I too think that Linux won't take over the desktop market soon, but I can live with that, because I run Linux every day with flash and java and listen to MP3 and much more..........

pretty damn stupid? Obviously what I was saying was 'lack of support for commonly used formats'.

Take a shot at Macromedia and not Linux.
And you have a funny way to say things.

---

### Post by meng on 2006-08-18
> **alexandermimix said:**
> pretty damn stupid? Obviously what I was saying was 'lack of support for commonly used formats'.
Ah well then, don't you know you have to pitch your message to the lower common denominator? i.e. idiots like me! Now I understand what you're saying.
Except that I don't agree with it. Sure, it's a pain to get Flash8 working on Linux, but then it's also silly for a website designer to use Flash8 and exclude everyone else (including older Windows boxes) which only have Flash7. Any other common formats you can think of that can't be supported in Linux?

---

### Post by alexandermimix on 2006-08-18
> **meng said:**
> Ah well then, don't you know you have to pitch your message to the lower common denominator? i.e. idiots like me! Now I understand what you're saying.
Except that I don't agree with it. Sure, it's a pain to get Flash8 working on Linux, but then it's also silly for a website designer to use Flash8 and exclude everyone else (including older Windows boxes) which only have Flash7. Any other common formats you can think of that can't be supported in Linux?

thats like saying websites should only use html because older browsers cant display newer content.

---

### Post by syedn on 2006-08-18
I wouldn't say its exactly like that..

---

### Post by Tomosaur on 2006-08-18
The problem is not with linux, it's with the people who develop flash. If they got around to actually releasing Flash 9 for linux, then everyone would be happy. You can't blame linux for not having support for closed source, propietary formats, when the actual developers of this format are so damn slow releasing updates for the linux version.

FYI: Flash 9 for linux should be coming along soon.

---

### Post by MetalMusicAddict on 2006-08-18
> **alexandermimix said:**
> pretty damn stupid? Obviously what I was saying was 'lack of support for commonly used formats'.

Its ignorance really. Its not the fault of linux that theres no Flash 8 support. Its Adobe. Rumor has it that we will get Flash 9.

Please man. Dont make inflammatory thread titles like this just to get attention to your problem. Search the forum and you will see your not the only one with this problem.

Also, if you believe that linux will "take over the desktop market any time soon" you bought into someones hype. If its ready for *your* desktop thats great. Use what works for you.

---

### Post by aysiu on 2006-08-18
Can a moderator retitle this to a less sensationalist and more appropriate title like--"I need help installing Flash"?

This is just ridiculous. To the OP--stop with the theatrics. If you want help, ask for it. If you want to talk about the desktop market, read [my essay on it](http://www.psychocats.net/essays/linuxdesktopmyth) first.

---

### Post by telegramsam on 2006-08-18
> **alexandermimix said:**
> We were unable to detect the correct version of flash on your computer. 

The latest version of the Flash player can be downloaded free from Macromedia.


Hey--I'm new to this too.  In some ways, I can understand your frustrations.  I've had my battles in trying to do what I perceive to be fairly simple things.  

If you want to PAY through the nose for an OS, you'll likely get out of the box interoptibility with everything.  If you want a FREE OS, it's kinda demanding to expect it to just do everything like Windows tries to do.  

Believe me, I've seen at LEAST as many of those dialog boxes saying things like that while running Win as I have with Linux. 

So take a breath and follow the advice of all of these people who do a DAMN FINE job of helping.  They're patient and knowledgeable, and you won't find better FREE support.  But you gotta be cool.

---

### Post by MetalMusicAddict on 2006-08-18
Thanx aysiu. I was looking for your article.

---

### Post by cstudent on 2006-08-18
Zzzzzzzzzzzzzzzzzzzzzzzzzzzz =; 


This crap is getting old.

---

### Post by meng on 2006-08-18
> **alexandermimix said:**
> thats like saying websites should only use html because older browsers cant display newer content.
No actually it's more like saying that websites should be compatible with IE5 as well as IE6.

---

### Post by Perfect Storm on 2006-08-18
> **aysiu said:**
> Can a moderator retitle this to a less sensationalist and more appropriate title like--"I need help installing Flash"?

This is just ridiculous. To the OP--stop with the theatrics. If you want help, ask for it. If you want to talk about the desktop market, read [my essay on it](http://www.psychocats.net/essays/linuxdesktopmyth) first.

Done. But I more likely want to throw into the backyard with the rest of "not ready" threads.

I'm keeping an eye on this one.

---

### Post by aysiu on 2006-08-18
> **Artificial Intelligence said:**
> Done. But I more likely want to throw into the backyard with the rest of "not ready" threads.

I'm keeping an eye on this one. Thanks, Artificial Intelligence.

I would think of it as a "not ready" thread except that those have more explanation and a lot more ranting. This honestly feels more like a support thread with a bad attitude. I can see where the distinction can get blurry, though.

---

### Post by meng on 2006-08-18
> **aysiu said:**
> This honestly feels more like a support thread with a bad attitude.
That's funny, my impression was entirely different. However, since others did offer suggestions to fix the problem, there are obviously members who agree with your interpretation aysiu!

---

### Post by Perfect Storm on 2006-08-18
Agreed.
There's no need to making a thread which such title if you want help. But I doubt it the person wants help after reading the thread twice, that's why a backyard can be an option, but I'll give it a chance.

---

### Post by randlieb on 2006-08-18
i see mention of flash player 8 but when i go to adobe to download, all that's available for linux is version 7. is there a way to install version 8 on ubuntu. i have a site that i want to see but is viewable only with version 8. (and i run ubuntu exclusively now for the past year, and totally love it!!!)

---

### Post by aysiu on 2006-08-18
> **randlieb said:**
> i see mention of flash player 8 but when i go to adobe to download, all that's available for linux is version 7. is there a way to install version 8 on ubuntu. i have a site that i want to see but is viewable only with version 8. (and i run ubuntu exclusively now for the past year, and totally love it!!!)
You'll need to install the Windows version of Firefox using Wine and then install Flash 8 through there.

There are also some hacks to fool sites into thinking you're using Flash 8 if you're really using Flash 7.

---

