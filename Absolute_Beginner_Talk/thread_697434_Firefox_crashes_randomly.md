---
title: "Firefox crashes randomly"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2008-02-15
Firefox keeps crashes unexpectedly.  It either Freezes and needs to be forced to quit or It just shuts down randomly. Any ideas/
I'm using 7.10

---

### Post by gvartser on 2008-02-15
1) make sure that Firefox isn't running.

2) Open up a shell, (using terminal or other similar app)

3) Go to your home directory.
```
cd 
```

4) Rename your ".mozilla"  directory. (The directory where all the Firefox personal config & addons are saved)
```
mv .mozilla .mozilla.backup
```

5) Start Firefox again. (hopefully your problems are now gone.)

/g

---

### Post by Joeb454 on 2008-02-15
If the above does not work (it moves your profile and Firefox configurations into a different file, you can recover them :))

please open a terminal and simply type ```
firefox
```
This will give feedback when Firefox crashes, if you could post the output when it does crash, it might help solve your problem :)

---

### Post by pfwd.tech on 2008-02-15
Ok will give it ago thanks

---

### Post by pfwd.tech on 2008-02-15
This has worked but I have lost my profile, Is there any way of getting it back?
If i rename the folder back to what it was surely it will start crashing again?

---

### Post by Joeb454 on 2008-02-15
You have lost your profile because that's what post #2 said - it copies your profile to a different place. It seems your profile is the cause of the crashes.

But if you want it back anyway, open up a terminal and type ```
cd
```
followed by
```
mv .mozilla.backup .mozilla
```

---

### Post by pfwd.tech on 2008-02-15
Its just crashed again (with default profile) what output is needed?

---

### Post by pfwd.tech on 2008-02-15
Sorry - I should of said, No output was given when it crashed.  It just shut down. When I loaded it back up there was no output of any errors.

---

### Post by pfwd.tech on 2008-02-15
I found the out put after another crash 
Segmentation fault (core dumped)
This was in the terminal

---

### Post by Joeb454 on 2008-02-15
Your best option - in my opinion - is to follow the instructions in post #2 again, and start over...you *should* still have your bookmarks with a new profile...I'm not sure.

Even so, it shouldn't take that long to get them again, if you export them somewhere etc.

---

### Post by megahead13 on 2008-02-15
I have the problem here too. Haven't tried yet with the default profile. I am up2date, so I am with the latest firefox 2.0.0.12 Well, normaly I use konqueror (I use kubuntu), but because of a problem described [here]("http://ubuntuforums.org/showthread.php?t=688770") (by the way if you have any idea about it, I will be thankful), the last days I am with firefox...

---

### Post by ejs7597 on 2008-02-17
I am having this same problem.  It seems to do it most often, when there is mouse activity. Thunderbird is also doing it once in a while, but not as often as Firefox.

---

### Post by argraff on 2008-02-17
Yup, I'm seeing this too. I read somewhere (can't find it now) that installing it from firefox's site and NOT from the repos will fix it. Something about the repos not having the latest version. Can anyone confirm that idea?

In the meantime, I'm trying out Opera. Not bad. Speed dial is kinda cool.

---

### Post by zhanglini on 2008-05-26
Mine crashes all the time too, FF3b5, Hardy.

---

### Post by pfwd.tech on 2008-05-26
Mines settled down after the upgrade to firefox 3.5 beta and hardy

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **pfwd.tech said:**
> Firefox keeps crashes unexpectedly.  It either Freezes and needs to be forced to quit or It just shuts down randomly. Any ideas/
I'm using 7.10

u should mention ur system specifications such as RAM in order to help us attend to ur problem. Also, u didn't mention if u hv installed any add-ons for Firefox( many add-ons can affect the stability of ur system, and cause it to hang, like mine does.

Why don't u consider switching over to OPERA?

---

### Post by pfwd.tech on 2008-05-26
I'm a web developer and we test our applications in the major browsers such as Opera/IE/FF and Safari but we develop the applications FF as it has so many useful add-ons not to mention compliance of web standards over other browsers.

The systems spec is a dual core, 2GB 3200 ram, 32bit Ubuntu Feisty. 
I recently upgraded to hardy and Firefox 3.5 and it seems more stable. I now use a virtual machine to use other browsers such as IE6 -8, Opera, Safari, AOL,Flock, and earlier versions of FF.

The strange thing was my home machine never got the problem of crashing out of FF regardless of its version.  But then again it is a 64bit 4GB rig.

---

### Post by thecheat on 2008-05-27
Are these crashes happening at any particular time?

My FF3b5 crashes randomly ONLY when Flash is on the page. Therfore anytime I browse around YouTube.com I get crashes as do I with any other Flash heavy site. This might narrow down your "symptoms" so that you can better find a solution.

---

### Post by dopple on 2008-05-27
try googling "firefox 3 linux" There is a known problem with some process being called that brings firefox to it's knees. Linux is not curretnly supported for FF3. There's a massive row going on. Anyway, lots of the toolbars are not working so I would suggest using ff2 until the kinks are worked out.

---

