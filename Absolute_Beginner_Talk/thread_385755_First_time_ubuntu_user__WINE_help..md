---
title: "First time ubuntu user / WINE help."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-03-16
Hello Ubuntu World!

As a veteran Ubuntu user for just over 4 days :)   I am experiencing issues which are occurring because of my complete lack of knowledge of linux based systems, however rest assured…..I am trying to learn !

My switch to ubuntu had been anticipated months before I actually downloaded the live cd, complete FEAR had kept me away from linux before this, fear that various apps that I NEED are not linux compatible….and also the average perception that linux isn’t user friendly, and that I have to learn months of source code before I can make it work like I NEED it to work……FOOL!

Having installed ubuntu (dual booting for the mo),  and first seeing the desktop ping to action, complete with correct resolution, working Bluetooth keyboard, and working internet connection (which took me the best part of an hour to set up in XP) I realised that I had finally arrived home! I am more than happy with Ubuntu (Edgy), and have already made a solid vow never to return to the realms of Windows (aside from whilst at work of course, not much of a choice when your working for the enemy &#61514; )

However! I really really need IE 6 for cross browser testing (I work in webdesign), and could also use photoshop CS (although gimp IS a good program, and a complete bargin to boot, photoshop IS the industry standard, and should I ever venture to another company to work, rusty photoshop skills WILL be frowned upon)……I digress….. IE would be advantageous, photoshop also, and…this may be a big one, ppmate……ppmate is a p2p digi tv connection to asian TV, in this little console I have the world of football at my finger tips, including English football (f**k paying for SKYTV)….

Ok so after being proactive I located WINE via google, followed the instructions and installed the ubuntu WINE package from Synaptic, opened a terminal sess, tapped in winecfg pointed it to a freshly downloaded ppmate (downloaded from [http://www.download.com/PPMate/3000-2017_4-10603770.html](http://www.download.com/PPMate/3000-2017_4-10603770.html) ) and off the install went………I kicked back in my chair and thought……this is f**kin tip top stuff……until an error occurred (windows style…I think!) stating that the file is not in a compatible format…

Now my limited knowledge of all aforementioned steps means that I am unable to identify if the error occurs because ppmate is a win app, and wine isn’t set up accordingly, or more the likely, that I have simply gone about the install the wrong way…….

My Qs:

What is the correct procedure for installing an app via wine, now theres plenty of stuff online, both via Wine and other resources, however all help guide seem to skip over the tentative first steps……how to get a file onto your ubuntu desktop…..is it simply a task of pointing WINE towards a cd drive with the app CD inserted, or obviously to an iso alternative (via some form of VCD mount), or should the full file be transferred from win, and placed into a folder within ubuntu, which is later referred to via WINE. ???? (did that make any sense? &#61514; )

If PPmate is simply not supported by linux (via WINE), is there a linux alternative, ive noticed that there is a linux TV from some guy in Germany, however any info ref a p2p alternative would be greatly appreciated.

Although iam able to launch winecfg via the terminal, would be nice to have a user friendly clickable icon, any way to do this in ubuntu?

I know theres a lot of new user questions on this forum, which is why I am gonna thank everyone a thousand times right now 1, for reading all this, 2, for any answers which you are able to supply.

Cheers

Dale

---

### Post by eljalill on 2007-03-16
You install programs with wine through the following:
download the windows setup file (.exe or so),
navigate with the terminal to where that file is ("cd" and so on)
type 
```
wine SetupForYourProgram.exe 
```
and wait while it installs /go through the install menu.

You can find a list of programs that are supported together with what you need to know additionally about the installaion here:
[http://frankscorner.org/index.php?p=office](http://frankscorner.org/index.php?p=office)

Wine does not make a handy icon.. but you can make yourself one: make a .sh file (Custom command, if you look for it, you'll find it, otherwise ask again) .

I have no clue as to the other question... sorry. But have you searched sysnaptic for the functions you are looking for?

Hope this helps!

---

### Post by Kay The Bantu on 2007-03-16
hi turner congrats on taking the plunge (YAY) now I'm a bit of a noob myself but I'll try help.

to install ms software with wine, first go to the console and *winecfg* then add your application install file, chose the settings apply and your good to go, secondly(ok almost good to go) now on the gui double click on the app to install and it should install. you should note how wine labels your file stucture, so that you can access your installed app.

as for the desktop shortcut ...........................let me mule over that a bit

hope this helps

---

### Post by hyper_ch on 2007-03-16
Depending on your hardware (and until you get the stuff to run in wine fine) you could consider installing a virtual machine software which allows you to run Windows within Ubuntu... but that requires quite a bit of cpu power and ram...

---

### Post by cub on 2007-03-16
> **hyper_ch said:**
> Depending on your hardware (and until you get the stuff to run in wine fine) you could consider installing a virtual machine software which allows you to run Windows within Ubuntu... but that requires quite a bit of cpu power and ram...
Like hyper wrote I have used VMware for some Windows application I can't get to work with wine. It's takes some power of your pc but I'll have to learn to live with that until I find another solution.

---

### Post by TURNER on 2007-03-16
Hi all, 

Thanks for your quick feedback…

Point one: the code provided; wine ppmate.exe for example ?? and this would start a windows type install wiuard I take it?

I actually attempted via wine gui (config), i.e locate file (I think is the option), which launched the install wizard before supply an error that the file isn’t in the correct format…….does this sound like wine was somehow left out of the equation? 

The process I followed above seems to be the same as Kay has listed……perhaps some of my settings in wine are incorrect, I’ll have to do some more reading to find out.

As for a Vpc option…not feasible….iam seriously lacking the ram to host a vpc, and to be honest id rather dual boot than create a vpc……although iam currently trying not to use win for anything whatsoever….i think in a worst case scenario, id simply forget about win apps, and use linux alternatives, just a bit of a shame that id be missing tv for example, and of course photoshop…

I have checked synaptic, does anyone know of any way in which to receive peer to peer tv via linux?

Thanks again for feedback..

One more q, I originally installed dapper, and upgraded to edgy a day later, the upgrade was performed via the package installer, and everything seems to go ok, aside from an error which I saved in order to forward onto the ubuntu dev team, any ideas how I can submit this doc to the dev team??

thanks

---

### Post by eljalill on 2007-03-16
Point one: that's essentially how it works.
However, the program you want might just not go together with wine, which is also why you would get an error message when you use the GUI... I just don't know about that sorry. You could try it in the terminal an look at the error message. Sometimes googling the whole text of the error also bring new insights..

As for photoshop though: is there aynthing photoshop does that the Gimp can't do?
(that would be the linux program..)

---

### Post by Jussi01 on 2007-03-16
Hei, a couple of things in responce to your questions. 

Firstly your ppmate question, I assume you want this program for watching football/sports etc. There is a linux alternative for this, it is called sopcast - you may have heard of it before. You can find the files for it here: 

[http://dengpeng.name/blog/2006/12/07/gsopcast/](http://dengpeng.name/blog/2006/12/07/gsopcast/)

Secondly, I suggest you have a look at gimpshop ( [http://plasticbugs.com/?page_id=294](http://plasticbugs.com/?page_id=294) )- it is gimp with an almost photoshop front end - so it will look and feel like photoshop - you can follow many photoshop tutorials in it. However if that isnt good enough, you should definately have a look at crossover office. although it costs ($40) it supports photoshop, office, and IE6 - it makes installation a breeze. have a look at 

[http://www.codeweavers.com/](http://www.codeweavers.com/)

 I hope this helps


Jussi

---

### Post by Jussi01 on 2007-03-16
Oh, and for your problem, to report a problem to the devs, use [https://launchpad.net/](https://launchpad.net/)

---

### Post by TURNER on 2007-03-16
To be 100% honest…….I dont know.

I have heard great things about gimp, having visited graphic design forums and webdesign blogs it seems that gimp can cope with about 80% of what photoshop can do… my worry is that as the 2 tools work differently (iam guessing), that I will lack photoshop skills and be stuck should I ever need to use photoshop for a job…..in a production environment..

I’ll give gimp a spin and see what she can do..:) 

Has anyone any ideas about p2p tv, or an alternative for linux, where one can watch some sport :KS

---

### Post by Jussi01 on 2007-03-16
> **TURNER said:**
> 
Has anyone any ideas about p2p tv, or an alternative for linux, where one can watch some sport :KS

2 posts up mate...

---

### Post by TURNER on 2007-03-16
During the excitement of replying to this post I missed your response Jussi…

In all honesty I could kiss you! :) 

Firstly, watching footie and designing websites are my computers primary mission :) 

Having read about gimps capabilities iam happy that it can handle everything I would like to throw at it, as metioned in my previous posts the only worry is that I become rusty with photoshop, potentially creating issues down the road…..if there s a gui of photoshop, with gimp sitting behind, then problem solved.

Thanks all for responses, iam gonna get sopcast fired up before the rugby kicks off tomorrow &#61514;

Heres a little something to put a smile on yer face …

At a recent computer expo (COMDEX), Bill Gates reportedly compared the computer industry with the auto industry and stated, "'If GM had kept up with technology like the computer industry has, we would all be driving $25.00 cars that got 1,000 miles to the gallon.' 

In response to Bill's comments, General Motors issued a press release stating:

If GM had developed technology like Microsoft, we would all be driving cars with the following characteristics.

1. For no reason whatsoever, your car would crash........ Twice a day. 

2. Every time they repainted the lines in the road, you would have to buy a new car. 

3. Occasionally your car would die on the freeway for no reason. You would have to pull to the side of the road, close all of the windows, shut off the car, restart it, and 
reopen the windows before you could continue. For some reason you would simply 
accept this. 

4. Occasionally, executing a manoeuvre such as a left turn would cause your car to shut 
down and refuse to restart, in which case you would have to reinstall the engine. 

5. Macintosh would make a car that was powered by the sun, was reliable, five times 
as fast and twice as easy to drive - but would run on only five percent of the roads. 

6. The oil, water temperature, and alternator warning lights would all be replaced by 
a single 'This Car Has Performed An Illegal Operation' warning light. 

7. The airbag system would ask 'Are you sure?' before deploying. 

8. Occasionally, for no reason whatsoever, your car would lock you out and refuse to 
let you in until you simultaneously lifted the door handle, turned the key and grabbed hold of the radio antenna. 

9. Every time a new car was introduced car buyers would have to learn how to drive all 
over again because none of the controls would operate in the same manner as the old car. 

10. You'd have to press the 'Start' button to turn the engine OFF.

---

### Post by Jussi01 on 2007-03-16
great to hear you are doing well with it. any probs you come across just ask.

---

### Post by Absolom on 2007-03-16
An easy solution for web developers to test pages in IE while running  Ubuntu  is to get IEs4Linux  this installs IE version 5,5.5 & 6 either all or any one of them...  

Here is an URL on how to install in Ubuntu

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Hope this helps..

---

### Post by TURNER on 2007-03-19
Absolom, thanks very much for the link, iam certain this will come in use.

Ive actually decided NOT to mount win applications via WINE, instead iam attempting to use linux alternatives, GIMP is a pretty cool tool, and iam sure with a little playing around I should be able to make it do what I need it to....

I downloaded and installed sopcast, posed a few "issues" but armed with google and this forum ive managed to install...plenty of premiership football been running over my ubuntu ever since :) 

Thanks to everyone for taking the time to read and reply! The level of support in this forum is second to none!

---

### Post by hyper_ch on 2007-03-20
btw, it is easier to install MSIE 6.0 in Linux than it is in Vista ;)

---

