---
title: "Ridiculous question: how to use WINE to run Internet Explorer"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-03-24
Cut to the chase: Can I use WINE to run Internet Explorer???

Much as it galls me I have a machine set up at work running Ubuntu. The machine is for my student employees to access the web and their email, etc.

Unfortunately the students have to use this horrible web-based timesheet manager called Kronos Timekeeper to print out their timesheets. And this wretched application will only run in Internet Explorer. 

(As an aside, I really think that developers of web-based applications should design programs that can run on any browser. Why is it that they DON'T???)

Anyway, is there some way that I can run Internet Explorer in Ubuntu? I know this appalling and almost sacreligious but I am, as they say, stuck. 

And, as a further unrelated note, I think this forum is fabulous. The reason why is this: beginners are treated nicely and questions are almost always answered. This allows non-geek users to give it a try.

I am thrilled with Ubuntu and although there is a bit of a learning curve it is not impossible. All of you great people are helping to make Linux more viable because we need more users so that hardware and software developers will  eventually start designing products that are LINUX-compatible. Forums like this help create that momentum.

Sorry for the rant!

---

### Post by aysiu on 2006-03-24
I recommend [IEs4Linux.](http://www.tatanka.com.br/ies4linux/)

---

### Post by Sef on 2006-03-24
> Anyway, is there some way that I can run Internet Explorer in Ubuntu?

It is possible to run I.E. under Ubuntu if you use wine.

[http://appdb.winehq.org/appview.php?appId=25]("http://appdb.winehq.org/appview.php?appId=25")

---

### Post by Mustard on 2006-03-24
Winetools does a good job of installing IE in wine.  The issue is usually whether the current version of winetools will work with the latest version of wine you have installed.  I had to wait some time for the 'moon and stars' to align so I could get a working copy of winetools that went with my wine install and then installation was pretty easy.  Since that time I have rarely played with my wine setup, so I have little idea what the current state of affairs is.  Wine is a bit of a science unto itself, so you would be well advised to read all you can about the various tools that work with wine.

-edit-

I just had a peak at aysiu's link above.  It looks like a good way to proceed. :)

---

### Post by PhilOSparta on 2006-03-24
[QUOTE=gigi1234] And this wretched application will only run in Internet Explorer. 
[/QUOTE]

I'm not familiar with that web based application, but the Opera browser has a setting that allows the user to make Opera look like Internet Explorer to the web.  It could be worth a try, given that wine has a reputation as being problematic.

Good luck!

---

### Post by aysiu on 2006-03-24
[QUOTE=PhilOSparta]I'm not familiar with that web based application, but the Opera browser has a setting that allows the user to make Opera look like Internet Explorer to the web.  It could be worth a try, given that wine has a reputation as being problematic.

Good luck![/QUOTE] Firefox has an extension for this, too, called **User Agent Switcher**. Unfortunately, I don't think these solutions or Internet Explorer in Wine will work.

Apparently, according to [this document](http://kvc.kronos.com/WindowsXP_SP2.pdf), the Centra Client Software uses ActiveX, which is Windows-specific.

---

### Post by az on 2006-03-24
If it is not something about the custom javascript that IE uses, but simply the identity check, you can use the useragent switcher for firefox.  Just click on the extensions option in the firefox help menu and search for useragent switcher.

---

### Post by gigi1234 on 2006-03-24
So...I get the impression that even if I used Wine to run IE, the application (Kronos) I want to use still will not operate because it is dependent on ActiveX or some other proprietary garbage?

I am not sure I know for certain what the application requires. I know it needs Java Runtime Environment but beyond that I am stumped. 

I am not too much of an expert on these kinds of matters. 

Thanks everyone!

---

### Post by gigi1234 on 2006-03-24
Okay I tried installing the user agent switcher extension, but when I try to access the website I want to use I get a message saying that the Java plugin failed to initialize.

Am I dead in the water?

---

### Post by az on 2006-03-24
[QUOTE=gigi1234]Okay I tried installing the user agent switcher extension, but when I try to access the website I want to use I get a message saying that the Java plugin failed to initialize.

Am I dead in the water?[/QUOTE]
No.  Do you have java installed?

See here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by trent dillman on 2006-03-24
As a last ditch effort, try plunking down some cash for Crossover Office. It auto installs IE for you in a GUI.

---

### Post by gigi1234 on 2006-03-24
Yes, I believe the latest version of JRE is installed. At least that is what seems to be the case when I use Sun's test page.

---

### Post by ncappel1 on 2006-03-24
[QUOTE=gigi1234]Okay I tried installing the user agent switcher extension, but when I try to access the website I want to use I get a message saying that the Java plugin failed to initialize.
[/QUOTE]

I have this exact same problem. My college uses an internet java program to handle course registration, but it won't work with linux nomatter how hard I try. I asked the guys at the tech office here and they told me it was probably because it is not a pure java applet, it is some windows code that only uses java as a base, but for some reason is not programmed towards linux. For a long time I thought that java was installed improperly on my computer, but it isn't, I still havn't figured out the problem! woe are us! Maybe your internet java plugin error is similar to mine. they told me to use a windows emulator. ugg

---

### Post by gigi1234 on 2006-03-27
At least I am not the only one then!

If I ever find a solution to this I'll post it. 

Meanwhile, happy trails!

---

### Post by BobSongs on 2006-03-27
Two things, **gigi1234**:
[LIST=1]
[*]Did you ever get Internet Explorer going? On the odd occasion there has been the occasional site that requires IE. Just curious if the advice has been helpful;
[*]I truly enjoyed how you worded your question. You took the bull by the horns and off you went. Not because of anti-MS wording. I was expecting a whining newbie asking for help to install a "favorite" browser. 8)
[/LIST]

---

### Post by gigi1234 on 2006-03-28
Dear Bobsongs,

I haven't found the solution quite yet. I still haven't tried using Wine to run IE, mostly because I got the impression that it probably would not work. It seems to have something to do with the Java scripting as far as I can tell.

If I ever figure it out I will post the solution on this thread. 

I am glad I don't seem like a whiner. I am really very excited about using Ubuntu and Linux in general. At home I have completely switched to Ubuntu because I can easily do the things I want to do which is surf, email, burn cds, etc.

But at work there are these specialized applications that make it hard to shake Windows. 

Anyway, thanks for the hints! Take care.

---

### Post by RedKnight on 2006-03-28
On topic, can someone recommend a version of wine and a version of wine tool's that works well together?

I've had issues with both the latest version of wine and the current version of wine tools so I would happily download and install 2 old versions :)

Cheers
Stuart.

---

### Post by RedKnight on 2006-03-28
Second note: I previously used the most uptodate version of wine and the most recent version of winetools which installed IE6 SP2 fine :)

---

### Post by gigi1234 on 2006-03-30
I think I am at the end of the line here. I tried the ies4linux and also installing IE using Crossover Office. Neither one solves the program. I give up!

---

### Post by Princey on 2006-03-30
[QUOTE=gigi1234]I think I am at the end of the line here. I tried the ies4linux and also installing IE using Crossover Office. Neither one solves the program. I give up![/QUOTE]

I've had a similar issue running a web based application used in one of my online courses. I too fiddled with wine and the trial version of crossover office. Neither seemed to work as the css embeded sheet somehow detected I wasn't using Windows. I either had to install vmware or dual boot until I read somewhere about a Windows emulator that runs a lot of Windows programmes natively. It's called Win4lin. I downloaded the trial program and it did work fine for me. Before giving up, I'd suggest you try the trial versions of both, see which works for you.

---

### Post by gigi1234 on 2006-03-31
Okay, great! I will give a try. Thanks for the hint.

;)

---

### Post by Princey on 2006-03-31
[QUOTE=gigi1234]Okay, great! I will give a try. Thanks for the hint.

;)[/QUOTE]

You're welcome. Would be nice to update us as to your findings.

---

### Post by gigi1234 on 2006-04-01
Will do. I went to check out the win4lin website and requested a trial version but I haven't heard from them yet. Maybe by Monday.

---

### Post by YokoZar on 2006-04-01
[QUOTE=Sef]It is possible to run I.E. under Ubuntu if you use wine.

[http://appdb.winehq.org/appview.php?appId=25]("http://appdb.winehq.org/appview.php?appId=25")[/QUOTE]

This is the best way to do it.  Forget stuff like win4lin - just follow the instructions in the green box at the link here - you'll need to scroll down.  [http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

You'll need to download dcom98.exe and ie6setup.exe from Microsoft's downloads website to get them working.  These require a Windows 98 license to be legal, but you almost certainly have one.

Then to run IE, navigate to ~/.wine/drive_c/Program\ Files/Internet\ Explorer/
and run wine IEXPLORE.EXE

---

### Post by dj-toonz on 2006-04-02
i had the same problem what a lot of people in here are having, look's to me that a lot of the software or website's dont realise that not everyone uses M$ rubbish  so i downloaded the trial of crossover office myself and after the trial ran out , got meself the pro version & work's a treat , i use IE for just 1 website lol , tried it in Firefox (it opens but nothing works) , In IE it opens & work's to a degree (but the ruddy return key does'nt work) i have to press send on the screen , work's under M$ lol (i can learn to deal with that if i remember to press the send button & not use the return key on me k/board lol, i did try using wine myself like a lot of people was saying but couldnt unstand how to use the commands so crossover office here we came , i'm even using IE 6 to type this up in

---

### Post by gigi1234 on 2006-04-05
Yeah ummm the win4lin thing seems a little over-done to me now that I have checked it out. I don't want to run Windows in Linux. I love Linux and hate Windows!!! I feel dirty even thinking about running Windows in Linux...


I was able to get IE running using both Wine and Crossover, but I still could not successfully use the web-based application that I need to use. Every now and then you just can't prevail.

---

### Post by bogyit on 2006-04-09
[QUOTE=aysiu]I recommend [IEs4Linux.](http://www.tatanka.com.br/ies4linux/)[/QUOTE]

It's a perfect solution, I ran it and now I have IE 5.* and 6
Great!

---

### Post by BobSongs on 2006-04-15
**gigi1234**, are you still a) monitoring this thread and, b) having difficulty installing Internet Explorer through Wine in Ubuntu?

Cuz, if so you may wish to check out **[this thread]("http://www.ubuntuforums.org/showthread.php?t=149585")**. I've got Internet Explorer working right now on my box. Hope it works for you. (I've got the Google page all loaded up and lookin' pretty.)

---

### Post by gigi1234 on 2006-04-23
Okay thanks I'll check out that link.

I pretty much decided that I was wasting too much time on this particular project and at some point you just have to move on. 

But I will give it another go at some point!

Thanks to everyone who responded!

---

### Post by OrganicPanda on 2006-05-20
[QUOTE=aysiu]I recommend [IEs4Linux.](http://www.tatanka.com.br/ies4linux/)[/QUOTE]

excellent! i have been looking for exactly that for so long , thank you very much good sir

---

### Post by gmcle454 on 2006-05-20
I've had good luck with codeweavers' CrossOver Office. it doesn't have the bloat of win4lin, but it does create a sandbox environment without any emulation (which translates into light and fast). Unfortunatley it is a commercial project ($39), but it the only one I've ever purchased for Linux. I do a lot of web development and need to see how different engines render my sites. Unfortunalty most of the world's population use IE, so I have to check to see how microsoft's disregard for w3c standards affect my sites.

---

