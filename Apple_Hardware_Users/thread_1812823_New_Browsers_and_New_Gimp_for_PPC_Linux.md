---
title: "New Browsers and New Gimp for PPC Linux"
date: 2011-07-26
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2011-07-26
Hello,

I wanted to ask and see if anyone knows, since Mozilla has abandoned PPC for Firefox, there is now TenFourFox for Mac OS X PowerPC on the Mac side.

What is a good new browser to use if any to replace Firefox for PPC Ubuntu?

Also, Gimp. Seems that this hasn't been updated in quite awhile. And compared to Photoshop I find it somewhat difficult to use. But I love to use the layers, channels, and filters of Photoshop. Does anyone have any suggestions please?

Thank you. :-)
MacPenguin

:popcorn:

---

### Post by Tylerjd on 2011-07-26
For a replacement Firefox:
[LIST]
[*]Compile Firefox Yourself
[*]Look at Seamonkey (You may have to Compile it Yourself)
[*]Maybe chrome (if not available for PPC you will need to compile Chromium then)
[/LIST]
That is it for replacement for Firefoxes off the top of my head. I only own intel Macs and don't play around with PPC anymore.

For GIMP, Try compiling the source yourself.

Sorry thats all I have, but the PPC platform is starting to disappear. :(

---

### Post by MacPenguin1972 on 2011-07-26
> **Tylerjd said:**
> For a replacement Firefox:
[LIST]
[*]Compile Firefox Yourself
[*]Look at Seamonkey (You may have to Compile it Yourself)
[*]Maybe chrome (if not available for PPC you will need to compile Chromium then)
[/LIST]
That is it for replacement for Firefoxes off the top of my head. I only own intel Macs and don't play around with PPC anymore.

For GIMP, Try compiling the source yourself.

Sorry thats all I have, but the PPC platform is starting to disappear. :(

Compiling would be a problem. I'm not a programmer. 

PPC won't disappear if the people who use it keep it alive.

---

### Post by Tylerjd on 2011-07-26
> **MacPenguin1972 said:**
> Compiling would be a problem. I'm not a programmer. 

PPC won't disappear if the people who use it keep it alive.

You do have a point in that last sentence. 

You don't need to be a programmer to compile a program. 

Generally speaking you need to know four commands that you would run in the terminal. (this could be used as a great learning experience)

The first thing you need to do is to get the source, which is usually in a tar.gz format. Let us take Seamonkey as an example (as Firefox seems to be all pre-configured for specific architectures. The source would be found [here]("http://www.seamonkey-project.org/releases/#source").
It comes packaged as a .tar.bz2, which is like a tar.gz. Download it into your downloads folder.

When it is finished, goto the area that you downloaded it and double click to extract it.  It should be extracted into a seamonkey-2.2 folder. Then open terminal.

In terminal, use the command cd to goto the folder, so your command would be something along the lines of (replace the seamonkey-2.2 to whatever the you extracted the tar.bz2 to)
```
cd Downloads/seamonkey-2.2/
``` 

Which brings you into the directory where the seamonkey source is located. 

These next commands may seem scary at first, but only the last one does anything that may be hard to undo to your system- that being installing seamoney. You'll see what I mean.

Time to compile the code. _Make sure to reread this a few times before you do anything in order to have an understanding of what you are doing_

First, you will need to make sure you have all of your tools. As it seems like you have never compiled anything before, you will need to install the developer tools required to install.

In the following code boxes, don't type anything in the parentheses. Those are comments telling you what the command is doing. 
```
sudo apt-get install build-essential (Installs the developer tools. You will need to enter the password associated with your account)
(Wait for that to finish, make take some time depending on internet connection)

./configure (Makes sure you have all of the required dependancies to build seamonkey. If it says that it fails, google the step that it failed on, see if there is a package that you can install that will resolve it, then run the command again)
(It will look like a lot of scary code, but it is nothing to worry about.)

make (yes, a very simple command, and that is all of the hard work, which is compiling the actual program. Your CPU will be used a lot, and it may take some time to finish the process, so go grab a coffee.)(if this step fails, then post back here)


sudo make install 
(this last command (make install) installs the program, and you will need to enter your password again)
```

And that is all that is to it. Seamonkey should show up under applications, and if not just run the command "seamonkey &" in terminal

---

### Post by SoFl W on 2011-07-26
From what I understand [GIMP]("http://www.gimp.org/") is going through a massive re-write for version 2.8.  The website is regularly updated.  
Here is a website with [GIMP tutorials]("http://www.tuxradar.com/gimp").

---

### Post by scott092707 on 2011-07-26
Re: GIMP

I think/thought that the next version released was going to be 3.0.
Has anything changed to make them put out another 2.x first?

Also, I have seen GIMP tutorials/demos on YouTube (example, I saw one on Layers), so check there, too.

-Scott

---

### Post by rsavage on 2011-07-27
The replacement for firefox is firefox.  Version 5.0 for Power PC is ready to go in Natty.  For installing natty see the last few pages of the power pc sticky thread.

---

### Post by SoFl W on 2011-07-27
> **scott092707 said:**
> Re: GIMP
I think/thought that the next version released was going to be 3.0.
Has anything changed to make them put out another 2.x first?


From the [GIMP website]("http://www.gimp.org/").
> [SIZE=2]**GIMP 2.7.2 Released** ------------   **11-04-15 **[/SIZE]We  are pleased to announce availability of a new development version that  brings us closer to GIMP 2.8. This version is packed with important new  features and improvements. For a complete list of changes since 2.7.1  please refer to [NEWS]("http://developer.gimp.org/NEWS") page, while the [release notes]("http://www.gimp.org/release-notes/gimp-2.7.html") summarize changes in the whole 2.7.x series.  Please note that the whole 2.7.x series of versions is considered  unstable and is not recommended for use in production even though it  might just work for you. Our intention is to make development versions  available for passionate users who can provide useful feedback to help  us fix bugs and streamline implementation of some of the new features.  The upcoming v2.8 also introduces a huge amount of API deprecations and  additions that have the potential to break existing 3rd party scripts  and plug-ins. Please file bugs for all plug-ins and scripts that do work  in v2.6, but don't work in 2.7.2. A migration guide for developers will  be provided when v2.8 is out.
  There is still a lot of work to do on v2.8. Please refer to [this]("http://tasktaste.com/projects/Enselic/gimp-2-8")  page to find out what the current estimation of v2.8 release is, and  what bugs you can help us fixing to make the new stable version happen  sooner.

---

### Post by pauljwells on 2011-07-27
I'm running Natty on a G5 powermac. It has some 'quirks' but it runs generally very well. I have Firefox 5 (with the all-important sync feature) Thunderbird 3.1 and python 2,7.

It will only run unity-2d, but this is getting better every day.

---

### Post by MacPenguin1972 on 2011-07-28
First, I want to thank everyone who replied to this. And let me answer your replies. :-)

I am addressing each reply per poster, but I welcome comments from anyone. (sorry, I'm still quite new to all this and still very much the "learner". thank you for your patience in advance.)

**@ Tylerjd** -- Is that all there is to it? And would that work to make any program work under Ubuntu PPc?   I've been under the impression that if it's written for Intel, it will not work at all on PPC because we have two different chip architectures. But I would be shocked if porting programs was really as simple as putting some commands like that.  I wonder if that will work for Firefox and Adobe Flash? 

Also like I said, call me the nostaligc type, but I am a firm believer that Power PC, though it will eventually die I suppose - as long as people like to use them and the die-hard fans in the community continues to buck the trends, it will be around for awhile. The PPC G5 series is still a very powerful series. Funny because I heard one of the newer game systems is going to use a PPC chip set. But I forget which one. 

If I knew how to use Linux better and program I might try to do things to help keep it alive. But yeah, it will die if PPC fans let it die.

I figure it is inevitable I will have to switch to Intel- and then I'm trying to find out how to build a Hackintosh instead of buying a Mac, just to spite Apple for their BS in recent years (lol!) but yeah, for now.... I'm not giving up on PPC. 

I'm just saying this to encourage other PPC users because I'm one of them.

**@ SoFl W. scott092707**, Right now I am still using Tiger (10.4.11) on the Mac OS X side, and Ubuntu 10.4 on the Linux side. But the latest PPC versions I have seen are 2.6.11 - seems like it's been at that version for the last 2 years or so but I could be wrong. Just *seems* that way to me.  But yeah, I hope to see som newer versions.

Also can you recommend any other good programs like that which are Photoshop-like programs and open source/GNU for either Ubuntu or Mac OS X Tiger? (I plan to create a partition for Leopard for my G5 also to begin porting myself to Intel eventually.... but for now...)   I know there was GimpShop for the Mac which was a hack for Gimp that made it look/feel more like Photoshop but I could never quite get it to work on Mac OS X. I have not tried the Linux version, if there is one.


**@ rsavage  **How is that possible on the PPC platform? The reason I ask is because Mozilla made it quite clear that FF 4 will not work on Power PC anymore. so if they have written their code that only works on Intel, how can a PPC user still use it, either on the Mac OS X side or the Ubuntu side?  (Sorry, I'm a bit confused). Or is it a simple matter of using the commands like Tylerjd suggested for SeaMonkey? 

On the Mac OS X side it's no problem. There is still Camino (based on Firefox) and now TennfourFox (based on FireFox 4) But I was assuming since Firefox would no longer be supported for PPC on the Mac OS side, that the Ubuntu PPC side would follow suit, which is my reason for this posting.

But thank you- I will just see what you and the others have to say. I apologize, I'm just trying to learn more about this. Thx. :-)


**@ pauljwells  **What is the sync feature? Thx. Also thanks, I will check out those other browsers too and add them to my programs. I just want to make sure I have browsers that will do the job.


Again, thanks everyone for replying. And I will wait and see what the answers are to questions I have posed.

Peace! God bless! :-)
The Penguin

---

