---
title: "avi to dvd"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-01-16
so I have to show a short film for a class I am teaching and it is in avi format and the dvd players.

so, the question is how to I get avi to DVD?

Yes, this is all new to me and I do not know the technical terms so I may not be phrasing this correctly... sorry..

also, digging round here I noticed several ppl talking about GUI and Command line... Does this mean that it is possible to do video edting at the command line? that sounds cool


thanks for the help


Robi

---

### Post by bumanie on 2008-01-16
If the dvd player/s you have available are able to play mpeg 4 or dvix or xvid (this is usually noted somewhere on the machine or in the manual), you will not have any problems because these formats are the same as the avi format. If this is not the case the first thing that comes to mind is the dvdrip program (as it is not a large file). I have found it is fairly slow (I only have low end system), but its output is good. Dvdrip will convert avi to mpeg. Another possibility is the program devede, this encodes much quicker than dvdrip and also provides good qualtiy output. The only problem with this program is that it had  poor sound in some ubuntu distributions due to a problem with mplayer. There is a fix for the sound at [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) (bottom of the page). You may have to install this. You can get a prepackaged devede 3.6 at getdeb, which is a simple install (ensure you have the medibuntu repository enabled). As long as you are confident in fixing the sound issue, I would go with devede. Devede outputs an iso file that is easy to burn in the ubuntu cd/dvd creator - just right click on the iso, click burn and a few minutes later you will have a dvd.
Hope this makes sense and is of help to you.

---

### Post by balaknair on 2008-01-16
@beanco
Yes I too would recommend DeVeDe, it's easy and much faster than dvdrip.
The sound is the only drawback with DeVeDe, but you can fix it by installing Mplayer 1.0 RC2 from Gutsy backports.

---

### Post by beanco on 2008-01-16
the sound is pretty bad on the original and it is in Japanese, the subtitles in English and I actually need just this, the kids have to compare the audio with the subtitles ....

so, devede is what I should get?

Robi

---

### Post by bumanie on 2008-01-16
Yeah, devede is very easy to use. If you are using 7.10, do what balaknair suggested re the backports. If you are using feisty go to the ratersoft website to get the fix.

---

### Post by beanco on 2008-01-16
so devede and then onto ratersoft since I am on feisty...

what about the command line way of doing things?

robi

---

### Post by evil316 on 2008-01-16
I like tovid/todisc apps.

---

### Post by bumanie on 2008-01-16
Sorry beanco, am at work, had to disappear for a while. 
As you on feisty, the easiest thing is to go to [http://www.getdeb.net/search.php?keywords=devede](http://www.getdeb.net/search.php?keywords=devede) download the deb. file, double click and it should install
Then go to rastersoft as in my earlier post to get the sound fix.

---

### Post by Motorhead Kaze on 2008-01-22
Hi folks,

I hate to be all negative, but I had a terrible time with DeVeDe and .avi files when I was on Feisty.  It was sweet for other formats, but with .avi the conversions came out with green lines on the screen, and a harsh, loud, white noise.  I went to the DeVeDe site and got the Mencoder and Mplayer  fixes, but then I got an error message that says "This file not recognized as video."  I stopped trying after 3 attempts.

So, if you are recommending this program, is it actually working for you now?  I hear it worked with Edgy, but with Feisty it was crap (for me).

Anyone using DeVeDe with .avis on Gutsy successfully?

---

### Post by evil316 on 2008-01-22
> **Motorhead Kaze said:**
> Hi folks,

I hate to be all negative, but I had a terrible time with DeVeDe and .avi files when I was on Feisty.  It was sweet for other formats, but with .avi the conversions came out with green lines on the screen, and a harsh, loud, white noise.  I went to the DeVeDe site and got the Mencoder and Mplayer  fixes, but then I got an error message that says "This file not recognized as video."  I stopped trying after 3 attempts.

So, if you are recommending this program, is it actually working for you now?  I hear it worked with Edgy, but with Feisty it was crap (for me).

Anyone using DeVeDe with .avis on Gutsy successfully?

Yeah, I switched from using Tovid/Todisc to using Devede on gutsy and it works perfectly for me.

---

### Post by bumanie on 2008-01-22
I use devede successfully on feisty, once downgrading mplayer etc.
The sound is fine the video output quality is fine. So far I have not found any file type it will not convert. From memeory, have done wmv, raw analogue (old video camera), avi, rmvb. I personally find it to be a stable and easy to use program.

---

### Post by beanco on 2008-01-22
installed devede, easy as pie, but when I tried to convert I could not find the file... if I go to places/home it is there but when I go through devede I cannot see it.

robi

---

### Post by beanco on 2008-01-22
> **evil316 said:**
> I like tovid/todisc apps.

looking into this I like the idea but it is kind of confusing.

so could you give me a quick quide to it?

Robi

---

### Post by stchman on 2008-01-22
> **beanco said:**
> so I have to show a short film for a class I am teaching and it is in avi format and the dvd players.

so, the question is how to I get avi to DVD?

Yes, this is all new to me and I do not know the technical terms so I may not be phrasing this correctly... sorry..

also, digging round here I noticed several ppl talking about GUI and Command line... Does this mean that it is possible to do video edting at the command line? that sounds cool


thanks for the help


Robi

Use DeVeDe from [www.getdeb.net](www.getdeb.net).

The Mencoder is buggy with Ubuntu so you will have to enable the backports and upgrade to the 1.0rc2 Mencoder.

---

### Post by beanco on 2008-01-22
as I posted above I have devede and it is not working ... nothing to do with sound.... I  could not find the file!!!

robi

---

### Post by stchman on 2008-01-22
> **beanco said:**
> as I posted above I have devede and it is not working ... nothing to do with sound.... I  could not find the file!!!

robi
Do you have the proper extension on the file?

.avi, .mpg, .wmv, etc.

---

### Post by bumanie on 2008-01-22
> **beanco said:**
> installed devede, easy as pie, but when I tried to convert I could not find the file... if I go to places/home it is there but when I go through devede I cannot see it.

robi

I'm at work at present and can't see my ubuntu machine (obvious), but from memory you just need to open up devede, click on dvd or avi or whatever output you want. At the next screen, put a title if you wish by clicking on properties under the title box. Next, under the files box, click add and you should be able to navigate to where your video is. Double click the video file and it should migrate to the files box.

---

### Post by bumanie on 2008-01-22
> **stchman said:**
> Use DeVeDe from [www.getdeb.net](www.getdeb.net).

The Mencoder is buggy with Ubuntu so you will have to enable the backports and upgrade to the 1.0rc2 Mencoder.

that is true for gutsy, but beanco is using feisty.

---

### Post by beanco on 2008-01-22
> **bumanie said:**
> that is true for gutsy, but beanco is using feisty.


yeap, fesity and when I open devede i get a window that says

choose the disc to create

video dvd

video cd

Super video Cd

cvd

divx/mpg 4

i choose video dvd and the prgm opens, I choose file/open and look for the file I want but it is not shown....

there is nowhere for me to choose the type of file I want to open, etc.

need a good devede tutorial...

robi

---

### Post by bumanie on 2008-01-22
> **beanco said:**
> yeap, fesity and when I open devede i get a window that says

choose the disc to create

video dvd

video cd

Super video Cd

cvd

divx/mpg 4

i choose video dvd and the prgm opens, I choose file/open and look for the file I want but it is not shown....

there is nowhere for me to choose the type of file I want to open, etc.

need a good devede tutorial...

robi

You need to click the **add** button under the file window. That should open up a window that allows you to search through your home folder etc.
Try this tutorial [http://lildeadstar.altervista.org/devede/](http://lildeadstar.altervista.org/devede/)

---

### Post by beanco on 2008-01-22
Thanks!

robi

---

### Post by popie on 2008-01-22
> **balaknair said:**
> @beanco
Yes I too would recommend DeVeDe, it's easy and much faster than dvdrip.
The sound is the only drawback with DeVeDe, but you can fix it by installing Mplayer 1.0 RC2 from Gutsy backports.
Is there any downside to enabling the backports repository? 

Can I enable it, install mplayer, then disable backports, or will that cause problems?

---

### Post by beanco on 2008-01-25
ok, so i have an iso file sitting on my desktop but acording to properties it is 5.9 gigs... how can I get it down to 4.7 to fit on a single dvd, or break it in two ??

Also, when I was first trying to make the iso file i did sg and ended up with an .mpg file ... .how I do that? I swear I did the same thing on both files, the first resulted in the mpg, the second in the iso.


thanks

robi

---

### Post by ubuntu27 on 2008-01-25
In order to create a DVD, you will need a mpeg file, iso file,  or a  [VOB, IFO, and BUP files].

If you don't have any of those files. (You don't have it. You have avi). 
Then you will need to convert it to mpeg, and then burn it to the DVD.

The method to convert avi to mpeg is a little complicated if you do it with the terminal. 
Here is some guide on converting avi to mpeg or other DVD compatible files:

[Converting to DVD]("http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD")

[Avidemux Documentation]("http://www.pcbypaul.com/absolute/programs/avidemux/")

[Burning Video DVDs on Linux]("http://www.katspace.org/Computers/LinuxBurnDVD")

> **beanco said:**
> ok, so i have an iso file sitting on my desktop but acording to properties it is 5.9 gigs... how can I get it down to 4.7 to fit on a single dvd, or break it in two ??

Also, when I was first trying to make the iso file i did sg and ended up with an .mpg file .

thanks

robi

So you have an mpg file now? Now you can use [KDE DVD Authoring Wizard ]("http://dvdauthorwizard.sourceforge.net")or other software to make it DVD compatible :)

```
sudo apt-get install dvdauthorwizard
```

---

### Post by beanco on 2008-01-25
Ubuntu27,

thanks for the info.

I was under the impression based on earlier posts to this thread that I need an .iso file, I have that, now.... but how to make it a dvd file?

robi

---

### Post by ubuntu27 on 2008-01-25
> **beanco said:**
> Ubuntu27,

thanks for the info.

I was under the impression based on earlier posts to this thread that I need an .iso file, I have that, now.... but how to make it a dvd file?

robi

I don't know which gtk or gnome application will be suitable to burn DVDs. 
I am a KDE user. I use K3B for all my burning needs.

If you don't mind having some qt libraries (that are used in KDE) in your Ubuntu system, then install [k3b]("http://www.k3b.org/")

```
sudo apt-get install k3b libk3b3 dvd+rw-tools cdrao transcode sox
```

It is an easy to use program, its interface is really intuitive. You can burn DVD iso, and DVD files with this program. :)

One more thing: Yes, you can use iso also. I forgot to mention that in my previous post. So, you can burn the iso file that you got with k3b. The only problem will be the size...

---

### Post by bumanie on 2008-01-25
Hi beanco, I see you are still having difficulties. I assume the dvd you are trying to copy may be a double layer dvd, is that correct? If so you will have to put it through a program such as k9copy to shrink it to a single layer prior to converting it in devede. I found devede actually compresses its output somewhat, therefore having 5.9g, must mean it is a double layer disc you are dealing with.
I suggest putting the disc through k9copy and then put the output of k9copy through devede. A bit of mucking around, but I think that should work. I have to go out now, so I will check in later and see how you are going.

---

### Post by beanco on 2008-01-26
I have K3b installed already, never actually used it though.

as for what I need to copy,... It is sg I downloaded, not a disc I have on hand, but that should not matter, right?

I have to show this to a class on wed. so I need to get it up and running as soon as possible.

I have the original downlad in .avi format.

somehow I ended up with it in .mpg and .iso as well. this was done with devede.

how can I get this .avi, or the .mpg, or the .iso on to a single DVD/or onto two DVDs in a format that a table top DVD player will play?

Thanks everybody for the help

robi

---

### Post by bumanie on 2008-01-26
Forgot the original disc was avi format. How large is the avi file?

---

### Post by beanco on 2008-01-26
it's 700.9 mb!

robi

---

### Post by beanco on 2008-01-26
ok, the .iso file is too big, it will not fit on the dvd...

so how can i make it smaller?

robi

---

### Post by beanco on 2008-01-28
i was able to burn one of the .iso files but when I played the movie it stopped at 18 min 50 sec.


the whol movie is well over an hour.

what could cause this?

robi

---

### Post by ubuntu27 on 2008-01-28
Try using dvdauthorwizard to convert your mpeg to DVD files.

Also, in the  mean time, create another thread and ask how to shrink a video. I don't have experience with that.

---

### Post by bumanie on 2008-01-28
I've been wondering how you went. Not too well by the look of things. Wish I was there to help you. Sometimes trying to do everything via forum posts just isn't enough.
How large was the iso you burnt? What program did you use to make the iso? Was it dvd ripper? I am running out of ideas, but if I were you, I would get the mpeg file you have and see how big it is. If it fits on a dvd, with a bit of extra room for the authoring, we'll look for a program to author the dvd from the mpeg.
By the way although dvd's say they fit 4.7g on them, they effectively have only 4.3g of storage.

---

### Post by billgoldberg on 2008-01-28
Don't feel like reading 4 pages but have you tried mandvd?

I believe you can find it on getdeb.net.

I've used it without any problems.

---

### Post by bumanie on 2008-01-28
I've been at work all night, I need to sleep. I'll check in later and see where things are up to. I was in fact thinking of putting the mpeg through mandvd - I gave it a bit of a test run earlier in the week and it seemed to do OK. If the mpeg is a bit big, mandvd also allows you to reduce the bitrate. Don't worry beanco, you'll eventually get there (even if you resort to buying a double layer dvd).

---

### Post by beanco on 2008-01-28
dvdauthorwizard and mandvd.. two new programs... well I cna give them a try. but I need sleep now. that means I will have a few hours tomorrow night after work to get this all done because I need the movie on Wed for the class I have to show it to.

Geting a dual layer DVd will help with the first problem, the one about the larger file...

I used devede to make the make the .iso!

what about the other quesiton regarding the film only playin 19 minutes of th e1.5 hour movie?

robi

---

### Post by bumanie on 2008-01-28
Have no idea why it only played 18-19 minutes of 1.5 hours. 
If you need to have the dvd ready by Wednesday, with the luck you've been having, I think you better get a double layer disc as a back up/last resort option. Would still like to clear this up somehow. In linux\ubuntu there are multiple burning and authoring tools etc. I have used devede the most. There is also dvd author - yet it is part of the devede program and there are more, but I have never tried most of them.

---

### Post by beanco on 2008-01-29
thanks for the support.

Teh movie I ahve to show this week is not the dual layer one. it is the other one.  

I have the one for this week as both .avi (which I converted to .iso  and .mpg. The .avi did not copy, that is the one that ended up only playing 18-19 minutes.

I canot figure out how to get the .mp onto a dvd, well I tried but got an error that devede could not make a file tree or sg like that... says maybe out of space.. but I have around 50 gigs of space free.

robi

---

### Post by bumanie on 2008-01-29
The mpeg won't play in a dvd player unless it has been authored and has the appropriate coding for the dvd player to read. What is the exact size of it?

---

### Post by beanco on 2008-01-29
I am not at home right now so I cannot check the size, but I have no idea what authoring means... and how do I find out what coding it needs?

robi

---

### Post by bumanie on 2008-01-29
Authoring and coding is what devede (and other programs such as mandvd, dvd author etc) does (as well as convert from one video format to another). You don't need to know the codes - the program knows how to do it without user specific input. That is why the raw mpeg you burnt would not play in a dvd player - it had not been 'authored' so dvd player could not read the disc. If you put the same the same disc in a computer and opened up something like vlc player (which natively plays almost any type of video file), it would probably be able to play the disc contents, but not all media players would be able to.

---

### Post by beanco on 2008-03-01
Hi,

one of the films I had to play only half burned... I deleted the .iso back then for some reason...

now I have tried 2 times to make a new .iso but keep getting .mpg using devede.

AT this very moment I am trying a third time... hope it works.

I have one of the mpg files still. How can I author that? I am getting tired of this but I have to show these clips and short films for the rest of the year... hopefully I will get better at this and be able to  do it all with no hitches...


robi

---

