---
title: "Next Ubuntu Release"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-19
Does anyone know the name of the next UBUNTU release and when it is scheduled to be released. If memory serves me correctly I believe I heard October:ish???

Also, Will multimedia be addressed? I mean can I now watch live video and video streams over the Internet just like I can in a windows environment?

Peace Y

---

### Post by sunexplodes on 2007-09-19
October 22, I think.

And I've never had a problem watching multimedia streams at all. You've probably just missed a codec or two.

---

### Post by Pumalite on 2007-09-19
Name is Gutsy 7.10. Release Oct. 18 I think. I'm running Tribe 5 and looks and works great. Multimedia?. Codecs have to be installed.

---

### Post by jamesford on 2007-09-19
[https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)

---

### Post by ruibernardo on 2007-09-19
To install multimedia in Feisty: [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413626")

I think that multimedia installation will be easier on Gutsy, it has been every time more easy to install it on each Ubuntu release.

---

### Post by lentomies on 2007-09-19
But shouldn't life be easier? I mean why install anything when it all can be done during the original install?

At the very least, after install is completed a multi-media install could be completed which enables the user to install restricted "packages" etc... but after this EVERYTHING would work PERFECTLY!

Right now for me at least I have "issues". I installed all the codecs etc.. and eveything worked. But now when I for example want to watch a multi media stream and have full screen the audio runs faster then video. But if I minimize my screen it goes back to normal. Before it didn't do this.

For me it appears there are "bugs" and "kinks" that need to be worked out....

Hey... come on... If Microsoft can do it couldn't the Linux community as well?

---

### Post by ddrichardson on 2007-09-19
> **lentomies said:**
> Hey... come on... If Microsoft can do it couldn't the Linux community as well?

Not unless you wish to start paying for the cost of the MP3 licences. That's the advantage Windows has. The DMCA and the UK & European equivalents are the problem here.

Perhaps a better explanation and an option after basic installation offering support.

---

### Post by sstusick on 2007-09-19
It would be nice if a window would popup upon first bootup after installation, which would say something like "Would you like to install audio codecs? They are necessary to play audio files..blah blah" and then click "yes" and it would give you a list of codecs available and then you just check them off and install them. Though that might be annoying to some users, why not place an icon on the desktop "Install audio codecs" or something. This would make it much easier for newer users.

---

### Post by lentomies on 2007-09-19
Ah... there we go! Thank You "ddrichardson" An  "OPTION"!!!! Now all we got to do is define what this option is? What it looks like? and then run with the ball and make it happen!!!!

I might be standing alone here but people do watch and listen to multi media and in all formats and in all languages!

Boy-o-boy if this were perfected in Ubuntu WHAT WOULD THE WORLD LOOK LIKE THEN???

Imagine.................

Come on.... Who wants to leave her/his mark?

---

### Post by aninaiian on 2007-09-19
Your problem (slow video) could be unaccelerated video playback.  There are lots of ways to go about this one being using the Xv video output module (however, it does some funky stuff with compiz/beryl/compiz-fusion though opengl playback is arguably weirder).  Another would be to allow your video player to drop late frames or skip frames.  Also what video driver are you using, does it support direct rendering with your card?

As for streaming media the default totem and vlc do pretty well with streaming in my experience.

---

### Post by lentomies on 2007-09-19
sstusick Your post came in between but you indeed gave a good picture of what is possible! I like your idea!!!!

Maybe we could even have a "preliminary" scan done that would identify what is possible with the present PC config that such an install would see? then the install would really be custom tailored!

Ha! beat that Microsoft!

By the way...... Are the "Powers-to be", I mean those that can make things HAPPEN with new Ubuntu releases monitoring these chats?

If so, Maybe they too can add insight as to the challenges the community faces? I would be interested to hear.......

---

### Post by sstusick on 2007-09-19
I like the idea, too, but it is unlikely that something like that will ever happen, unfortunately. But we can hope :)

---

### Post by ruibernardo on 2007-09-19
Sorry to *disappoint* you both, but this is already working in Feisty. Just boot from a Desktop CD, and try to watch a movie in your disk. Totem will ask you exactly that... If you add medibuntu repos on the liveCD, I bet you can watch the movie without any problem.

---

### Post by ddrichardson on 2007-09-19
> **lentomies said:**
> Ah... there we go! Thank You "ddrichardson" An  "OPTION"!!!! Now all we got to do is define what this option is? What it looks like? and then run with the ball and make it happen!!!!

I might be standing alone here but people do watch and listen to multi media and in all formats and in all languages!

Boy-o-boy if this were perfected in Ubuntu WHAT WOULD THE WORLD LOOK LIKE THEN???

Imagine.................

Come on.... Who wants to leave her/his mark?

Its not quite that simple. A decision like that would be made by the council. IANAL but would imagine that it could be construed as more of an approval by Ubuntu to supporting non-free licensed technology.

I also doubt Canonical would be keen to see a lawsuit heading their way. Remember Microsoft [lost a similar case]("http://arstechnica.com/news.ars/post/20070222-8910.html").

---

### Post by ddrichardson on 2007-09-19
> **epimeteo said:**
> Sorry to *disappoint* you both, but this is already working in Feisty. Just boot from a Desktop CD, and try to watch a movie in your disk. Totem will ask you exactly that... If you add medibuntu repos on the liveCD, I bet you can watch the movie without any problem.

I am running Fiesty and that's slightly incorrect - Totem asks you if you want to and then can fetch the codecs for you.

That's not the same thing as defaulting to install codec support in the initial install.

---

### Post by lentomies on 2007-09-19
epimeteo..... This is nice to know but things shouldn't have to go to such a length to work... even if temporarily......

Many suggestions, such as yours have been offered to me and otheres as well..... BUT.... if it is as simple as you say, then I should be  able to right click on a "LINK" and be able to choose "OPEN WITH" to see if certain players can give me the multi media experience I seek.....

Currently, this is impossible......

---

### Post by lentomies on 2007-09-19
ddrichardson---- Seems to me we are on the same page.....???

Now all we need is the option to "choose" that multi-media player that gives us the experience we seek. Then when a similar multi media stream is choosen/clicked upon the correct player will launch....

Does this make sense although I'm a novice in all this terminology?

---

### Post by ddrichardson on 2007-09-19
> **lentomies said:**
> ddrichardson---- Seems to me we are on the same page.....???

Now all we need is the option to "choose" that multi-media player that gives us the experience we seek. Then when a similar multi media stream is choosen/clicked upon the correct player will launch....

Does this make sense although I'm a novice in all this terminology?

I don't think we are ;-)

From fiesty onwards, when a stream is launched, totem checks for the codec required and prompts to download automatically after explaining the legal issue.

I personally don't think there is anything wrong with this approach and find it an improvement from previous releases.

---

### Post by lentomies on 2007-09-19
ddrichardson-- Then I don't have the same experience as you. Maybe this is because of "system configuration" and a host of other varibles? BUT I've never had TOTEM pop up and ask me anything.  Most of the time it's mPlayer that does the taliking and playing.

My comment of being on the same page was in reference to your statement "
That's not the same thing as defaulting to install codec support in the initial install."

Here I was referring to what can be done on an intial install and what in comparison can be done via live CD.

Are we on the same page now?

---

### Post by ruibernardo on 2007-09-19
> **lentomies said:**
> epimeteo..... This is nice to know but things shouldn't have to go to such a length to work... even if temporarily......


Like ddrichardson said on post #7, it is legal issue. Mayby not for many people, but it is in the United States. Ubuntu can't put those codecs on their official repositories because automatically, if users in the United States installed those codecs, they would be in an illegal situation. So, who want to use those codecs, just add the medibuntu repository (it's not hard. System, Administration, Software Sources, and add the medibuntu repo). This is boring, but makes Ubuntu a legal distro.

> **lentomies said:**
>  Many suggestions, such as yours have been offered to me and otheres as well..... BUT.... if it is as simple as you say, then I should be  able to right click on a "LINK" and be able to choose "OPEN WITH" to see if certain players can give me the multi media experience I seek.....

Currently, this is impossible......

Well that's your opinion. I've done the [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413626") and I don't have any problem. All works without problem at all (except maybe with TV streams on the Internet, but I use VLC for those, so it isn't a real problem). 

Still, a total noob on a fresh install or a LiveCD will be asked for the "codec search question" when he tries to listen a MP3 file or play a movie. If he is on Firefox, probably he will write "ubuntu codecs" on the Google toolbar and get some answers about it.

Again, codec problems were a real issue on pre-Feisty releases. Feisty has made it easy and I bet 20 euros that Gutsy will be even easier!

---

### Post by ruibernardo on 2007-09-19
And don't tell me that Windowz Media Player can play all the multimedia files on a fresh install without any question to the user and without any downloads.

---

### Post by Snoopyowns on 2007-09-19
That's correct. For Windows XP at least, you have to go search codec sites. Typically people will go with those all in one codec packs to make it easier that have 95% of the codecs you can possibly need.

I'm not familiar enough with Vista to know if that's handled the same way, but due to legal reasons, I'm assuming it'd require the same steps.

Maybe it's just me, but Ubuntu seems to support more codecs out of the box than Windows XP does. Also, it's easier to get multimedia going using the walkthrough on the forums than in Windows, due to the fact that all the information you need is in that one post. With Windows, you have to google it and browse various links.

---

### Post by lentomies on 2007-09-19
Hey epimeteo cool down... This is suppose to be a friendly environment to communicate and exchange information. But more importantly to LEARN!

I would like to, however, take you up on your 20 EURO challenge. Would it be okay with you if we got say 5-10 different machines and do a 7.04 installs on each and see the results. As you suggest it should be same result across the board "No issues whats so ever".

How do you suggest we move on this challenge? Who will be the judges etc... Should I come to you or You to me. How you want to arrange this?

I Like Linux Ubuntu 7.04 and have an open mind. I have used XP since 2004 and have never ever had to download codecs to make certian media streams work. Everything just worked. Now maybe what Snoopyowns is talking about occurs during a Windows update but with that said I've never had to got out of my way and search for Windows XP codecs....

---

### Post by Snoopyowns on 2007-09-19
I don't think Windows Update really has any codecs, I haven't checked recently, maybe for Vista it does considering driver support with Windows Update in Vista is pretty nice. 

The main problem I see is that you are under the assumption that Windows XP "just works". In my 6 years of having Windows XP, beta through SP2, I have only had 1 BSOD, among having gone through about 3 computers during that time. And that one BSOD was faulty RAM. Is that always the case? No of course not. What works for 1 computer doesn't necessarily work for another. Thats how it's been always for every computer ever made.

Also, the media streams you are using are most likely different than what others use. So without knowing more specifics about the media stream, we can't say for sure that the media stream works for others, but not you. 

Although a few ideas you've given on a "Getting Started Wizard" would seem to be useful, more of like an offline version of some of these great How-To's that are on the forums would be helpful, especially if your network card isn't configured right :P I'm not sure if there is a suggestions forum, but layout a good plan and post it in there.

---

### Post by ruibernardo on 2007-09-19
Well, don't bet, you would loose. 

Try it if you want. Boot the LiveCD (Ubuntu Desktop), add the medibuntu repos, install the packages "libdvdcss2" and "w32codecs" and open a movie on your hard disk. Totem will ask you to search the codecs and will install them. With those 2 packages installed, all the rest is installed by asking "search to find a suitable codec". You can even watch a DVD.

About Windowz, you must be forgotten. Install a fresh Windowz XP and go to YouTube or Googlevideo, or try to watch a Xvid video, or another codec that isn't on Windows by default. Windows have to install them. Maybe you installed them with another software (another media player or NERO or something like that), which usually is the case.

---

### Post by Pumalite on 2007-09-19
In XP you HAVE to install FDDShow or some such before you can process audio or video. It's been a long, long time, but I remember.

---

### Post by lentomies on 2007-09-19
Hi Snoopyowns... Seems to me that you suggest that making bets is a dump idea.....

Can we now move forward on helping others?

I think most people will agree with me that ALL are willing to contribute information that will lead to an Out-of-the box solution that will work.

Can you imagine if one day a novice user could connect to Ubuntu and have their present PC configuration scanned and then a proper image downloaded that when burned to a CD/DVD and then installed would give them a EXPERIENCE they never before imagined?

Today it kinda exists... You just can't be technical challenged.... But if the bigger picture is to convert the world.... Well then my friend who would be talking then?

---

### Post by Snoopyowns on 2007-09-19
> Can you imagine if one day a novice user could connect to Ubuntu and have their present PC configuration scanned and then a proper image downloaded that when burned to a CD/DVD and then installed would give them a EXPERIENCE they never before imagined?


Would be a nice thought, until your PC changes and you have to redownload. Also keep in mind, there would need to be about 1 million different ISO images hosted to support all the possible hardware configurations.

Although, you may be able to have the setup scan for codecs, common software, etc, and after the install of Ubuntu, a program takes that list and gives you the options you have that are comparable to each category. 

The only other option is to bloat Ubuntu with anything and everything :P And that wouldn't really appeal much when you have to have a 5 DVD OS install.

---

### Post by lentomies on 2007-09-19
epimeteo my friend!!! I thought I gave you a suggestion for the challenge you suggested! Did you disapprove?

How come you don't want to suggest how it takes place?

Also, Why are you talking about DVD playback? I want to play media streams from links I finds on various news services websires etc.... That's all I've been taking about. Nothing else.

Tell me, can you go to beelinetv.com  or russiantvonline.com/ or even [http://www.mtv3.fi/](http://www.mtv3.fi/) and play a multi media stream out of the box? I doubt it! So as I said before how can I take you up on your challenge? Your the one that made it and I want to take you up on your offer.

---

### Post by justin whitaker on 2007-09-19
On a stock XP or Vista install, you can only use WMA, MP3, and AVI (maybe-I don't recall). You need to go and get KLite, Codec Pack, or some other third party software to play everything else, including DVDs. PowerDVD is bundled with alot of PCs for just that reason-without it, you can't use that DVD drive you paid for.

Now, with Ubuntu, you only get OGG, Theora, and other open source codecs available out of the box...there is a good reason for that: you can't distribute the rest of them in the US and other DRM friendly countries. Most of these, however, are available via the Restricted-Extras pack, and the rest are in the repositories as well.

My point is, either way, you are not going to be able to run just any file because you need to install codecs, and yes, that includes streaming media.

---

### Post by Pumalite on 2007-09-19
After you install Ubuntu; all you need to do is this:

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install vlc

And you are all set.

---

### Post by rand0m on 2007-09-20
A clean basic XP install doesn't play everything out of the box or else I wouldn't have to make custom installation CDs with slipstreamed codecs among other things.

As for: beelinetv.com, russiantvonline.com, mtv3.fi

Do you mean play the streams out of the box on a ubuntu machine? With the codecs from the medibuntu repo I can play from all of them w/ smplayer (mplayer) & vlc except russiantvonline which shows me a commercial/ad before it asks me to login. Maybe it's a Totem problem? I don't really know, since I've never been a fan of totem. SMplayer w/ mplayer mozilla plugin for the win!

---

### Post by ruibernardo on 2007-09-20
Sorry lentomies, you lost.

On a "almost" fresh Windows XP install: the link [http://www.mtv3.fi/](http://www.mtv3.fi/) didn't work on Windows (didn't see any movie even when I clicked on the Flash player windows),  and the russiantvonline.com gave me the following error (please login to view the image):

[IMG]http://img512.imageshack.us/my.php?image=russiantvqb7.png%5D%5BIMG%5Dhttp://img512.imageshack.us/img512/3867/russiantvqb7.th.png[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=43889&d=1190263371[/IMG]
[IMG]http://img512.imageshack.us/my.php?image=russiantvqb7.png%5D%5BIMG%5Dhttp://img512.imageshack.us/img512/3867/russiantvqb7.th.png[/IMG]
EDIT: It's a RealPlayer file and Windows didn't recognize it.

So, were is the out-of-the-box O.S.? 8-[

Let's finnish this. Propriety software just sucks. It's them that give you issues and problems, not Ubuntu. I still say that the next Ubuntu release (Gutsy) will be easier than Feisty to install all those codecs and other things, and definitely easier than Windowz...

---

### Post by sstusick on 2007-09-20
I'd say Ubuntu works more out of the box than Windows. On Windows you have to load your nic card drivers, video card drivers, sound card drivers, wireless card drivers, card reader driver, etc. etc.  I didn't even have to load the bloatware driver for my HP Printer, I plugged it in and 30 seconds later I was printing with it. Can you do *that* with Windows?

On Ubuntu, I didn't have to load any of these. They were taken care of during the initial install of the OS. And they say Windows is easier? I think it is more aggravating having to load driver after driver and then installing an anti-virus and anti-spyware software to combat the infestations.

---

### Post by irish_flu on 2007-09-20
OK it seems the original poster is talking about streaming internet video.

A whole lot of your common streaming internet video is one of three things: Flash, WMV (Windows Media Video) and Quicktime.

**Flash:** Owned by Adobe, does not ship with Windows, Mac OS, or Ubuntu.  In Internet Explorer, Firefox, Safari, or any browser in any OS, this must be installed before you can view them.  Everybody has to download the Flash Plugin for their browser to use Flash, no matter which OS they use.

**WMV (Windows Media Video):** Owned by Microsoft.  Can be played automatically on a Windows box, not so on a Linux or Mac OS box.  The reason why, I'm sure, is obvious.

**QuickTime:** Owned by Apple.  Need a software download to be played in any OS besides Mac OS.  Again, I'm sure the reason why is obvious.

Flash is, I believe, the most common currently and is used on popular sites like Youtube, Myspace, photobucket, and their imitators/competitors.

Many of the news sites use Windows Media.

---

