---
title: "First Ubuntu Install 64bit or 32bit?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by obesus_puer on 2007-10-16
So I have just received my new laptop today. I bought it for the purpose of learning linux. I have decided that I will install Gutsy Gibbon. However... I cannot decide between 64bit and 32bit. From what I can find it seems that 64bit no longer has issues with Flashplayer but I'm worried about other issues that may arise. My question is if anyone out there is using Gutsy 64bit and if so what issues (if any) have you had to deal with. Also is there really that much of a performance increase?

---

### Post by overdrank on 2007-10-16
> **obesus_puer said:**
> So I have just received my new laptop today. I bought it for the purpose of learning linux. I have decided that I will install Gutsy Gibbon. However... I cannot decide between 64bit and 32bit. From what I can find it seems that 64bit no longer has issues with Flashplayer but I'm worried about other issues that may arise. My question is if anyone out there is using Gutsy 64bit and if so what issues (if any) have you had to deal with. Also is there really that much of a performance increase?

Hi and I must say as a personal opinion I would install  Feisty. I was super fast on my system and I thoroughly enjoy it. I am always hesitant on a new OS and I have installed Gutsy on a system although not 64 bit. But I am sure you will be impress as I was with Feisty! Good luck! :KS

---

### Post by PmDematagoda on 2007-10-16
64 bit is great for PC's with RAM greater than 4Gb and also for memory intensive tasks such as encoding, etc.

Though it is a little more difficult to find software for the 64 bit version it is still useful to know how to use it as more and more emphasis is being put on 64 bit which is going to be the new standard of OSes over the older 32 bit ones.

---

### Post by Seisen on 2007-10-16
I installed Gutsy on a 64-bit laptop and the only problem i  had was with Java but that could of been because I was using Iceweasel instead of Firefox. Personally I didn't notice a difference between 64-bit Ubuntu and 32-bit Ubuntu except for a little tweaking to get Flash and Java installed.

---

### Post by obesus_puer on 2007-10-16
Well this laptop will have a gig of ram. So I'm guessing I won't see a noticeable difference between the two?

---

### Post by PmDematagoda on 2007-10-16
There won't be much of a difference, but if you are doing some memory intensive tasks then you may notice a significant difference.

---

### Post by phidia on 2007-10-16
Hi I encourage you to try 64 bit because it is the way things will be soon (it's hard if not impossiible to even find new 32 bit systems for instance) You also should check out the 64 bit forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134") as there are a lot of myths about 32 vs 64 bit mostly those myths are promoted by the lesser informed. 
We need more people to use 64 bit linux IMO. 
And finally for things like video ripping, burning and editing 64 bit beats 32 bit hands down. While I haven't done any scientific measurements video burning alone is at least 30% faster.

---

### Post by obesus_puer on 2007-10-16
> **phidia said:**
> Hi I encourage you to try 64 bit because it is the way things will be soon (it's hard if not impossiible to even find new 32 bit systems for instance) You also should check out the 64 bit forum here as there are a lot of myths about 32 vs 64 bit mostly those myths are promoted by the lesser informed. 
We need more people to use 64 bit linux IMO. 
And finally for things like video ripping, burning and editing 64 bit beats 32 bit hands down. While I haven't done any scientific measurements video burning alone is at least 30% faster.

I'll take a look at the 64bit forums. I didn't even know there was one >.<

---

### Post by overdrank on 2007-10-16
> **phidia said:**
> Hi I encourage you to try 64 bit because it is the way things will be soon (it's hard if not impossiible to even find new 32 bit systems for instance) You also should check out the 64 bit forum here as there are a lot of myths about 32 vs 64 bit mostly those myths are promoted by the lesser informed. 
We need more people to use 64 bit linux IMO. 
And finally for things like video ripping, burning and editing 64 bit beats 32 bit hands down. While I haven't done any scientific measurements video burning alone is at least 30% faster.

Hi I would agree and I did notice quite a difference on my system with 1gig of ram. Good luck in whatever you choose! :popcorn:

---

### Post by PsycoGeek on 2007-10-16
I'm also in the same position (kind of).  I am building three new desktop machines with 64bit processors.  If I go with 64bit Gutsy, will I still be able to run 32bit apps?

---

### Post by fluffman86 on 2007-10-16
If you have a 64 bit processor, you should definitely get the 64 bit version of *buntu.  I'm not having any problems with 64bit programs anymore, and I don't think people even make 32bit processors now.  

64bit is future proof.

PS - there are few 32bit ONLY programs (like picasa), so you do have to manually install those with
```
sudo dpkg -i --force-architecture program.deb
```

---

### Post by phidia on 2007-10-16
> **PsycoGeek said:**
> I'm also in the same position (kind of).  I am building three new desktop machines with 64bit processors.  If I go with 64bit Gutsy, will I still be able to run 32bit apps?

Yes all the apps will work under 64 bit-unless you are using/needing something unusual.
It really is a good idea, though, to check or ask this question at the 64 bit thread (linked above in my previous post). It would be great for ubuntu and all it's variants if people would consider using the 64 bit version.

---

### Post by Kilz on 2007-10-16
> **PsycoGeek said:**
> I'm also in the same position (kind of).  I am building three new desktop machines with 64bit processors.  If I go with 64bit Gutsy, will I still be able to run 32bit apps?

Sure you can install 32bit applications. But the real question is you should ask is, will you need to. The answer is no. There are 64bit versions of all common applications in the repositories. But if you have some ancient old application that no one uses anymore, yes you can install a 32bit version.

---

### Post by Z_Cee on 2007-10-16
Congratulations on your new laptop. 

I don't want to put a damper on your install, but if your system came with Windows installed and is a 'brand new computer' as opposed to being a used computer, but still new to you I would wait a couple of weeks before attempting installing a new operating system. 

You may have a short period you can return the computer if there is something wrong, but if you install another operating system within the 'grace period' you may lose the chance to return it if there is a problem. I've returned a new computer because of problems after 3 days and actually had a 2 week period to return it.

See how your new laptop works with Windows so that you will have a reference point when you install Ubuntu.

In that time do your research with what version of Ubuntu you want to install. Whatever version you install will most assuredly be better than Vista. Of course you already knew that...:)

---

### Post by obesus_puer on 2007-10-16
> **Z_Cee said:**
> Congratulations on your new laptop. 

I don't want to put a damper on your install, but if your system came with Windows installed and is a 'brand new computer' as opposed to being a used computer, but still new to you I would wait a couple of weeks before attempting installing a new operating system. 

You may have a short period you can return the computer if there is something wrong, but if you install another operating system within the 'grace period' you may lose the chance to return it if there is a problem. I've returned a new computer because of problems after 3 days and actually had a 2 week period to return it.

See how your new laptop works with Windows so that you will have a reference point when you install Ubuntu.

In that time do your research with what version of Ubuntu you want to install. Whatever version you install will most assuredly be better than Vista. Of course you already knew that...:)

Well I played around with Fedora back in the day. As for warrantys I kinda like voiding them. DD-WRT on brand new router for example. Plus the guy I bought it from on ebay will only accept returns for DOA.

---

### Post by obesus_puer on 2007-10-16
One of my main concerns is actually VLC media player. Its my favorite player (in windows) and I'm hoping it will run well in Gutsy 64

---

### Post by rsambuca on 2007-10-16
VLC works perfectly in 64bit Ubuntu.

---

### Post by obesus_puer on 2007-10-16
> **rsambuca said:**
> VLC works perfectly in 64bit Ubuntu.

excellent thanks. are there any commonly used programs that need to be installed in 32bit?

---

### Post by haden9 on 2007-10-16
Could you clarify something for me please? I read through the entire thread and didn't find listed what kind of CPU your laptop came with. Also if it has a 32-bit cpu sadly you will only be able to use the 32-bit version of Ubuntu be it gutsy or feisty.

Thanks!

---

### Post by obesus_puer on 2007-10-16
> **haden9 said:**
> Could you clarify something for me please? I read through the entire thread and didn't find listed what kind of CPU your laptop came with. Also if it has a 32-bit cpu sadly you will only be able to use the 32-bit version of Ubuntu be it gutsy or feisty.

Thanks!

Core 2 Duo, im not that dumb =) I consider myself fairly knowledgable when it comes to hardware/networks and *cough* windows hopefully I can add linux to that list one day.

---

### Post by fluffman86 on 2007-10-16
> **obesus_puer said:**
> excellent thanks. are there any commonly used programs that need to be installed in 32bit?

Yes.  I mentioned Google Picasa and Google Earth earlier.  If you need them, they will need to be run as 32-bit programs.  To install, download the .deb from [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html) and save it to your **_desktop_**.  If you try to install, you will get an error saying "wrong architecture."  To fix this, open a terminal and type:

```

cd ~/Desktop
sudo dpkg -i --force-architecture picasa*

```

That should do it.  


PS - I just checked the google earth page and I don't think you'll need to do this for that program, just Picasa.

---

### Post by haden9 on 2007-10-16
> **obesus_puer said:**
> Core 2 Duo, im not that dumb =) I consider myself fairly knowledgable when it comes to hardware/networks and *cough* windows hopefully I can add linux to that list one day.

I didnt mean to offend ya :) I just wanted to make sure and that it would support the 64-bit version. Perhaps if my system had more memory I would try out 64 bit version, but it only has 1GB so I use 32-bit one and so far am not dissapointed neither by the linux experience or by the 32-bit OS architecture, so my vote if your starting with ubuntu is to go with 32-bit for a while then move up to 64-bit. Hope this can be of help to you :D

Good luck with your Ubuntu install!!!

---

### Post by rsambuca on 2007-10-16
> **haden9 said:**
> I didnt mean to offend ya :) I just wanted to make sure and that it would support the 64-bit version. Perhaps if my system had more memory I would try out 64 bit version, but it only has 1GB so I use 32-bit one and so far am not dissapointed neither by the linux experience or by the 32-bit OS architecture, so my vote if your starting with ubuntu is to go with 32-bit for a while then move up to 64-bit. Hope this can be of help to you :D

Good luck with your Ubuntu install!!!

1GB of RAM is plenty for running 64bit Ubuntu, so please don't make that an excuse or an issue.

---

### Post by obesus_puer on 2007-10-16
> **haden9 said:**
> I didnt mean to offend ya :) I just wanted to make sure and that it would support the 64-bit version. Perhaps if my system had more memory I would try out 64 bit version, but it only has 1GB so I use 32-bit one and so far am not dissapointed neither by the linux experience or by the 32-bit OS architecture, so my vote if your starting with ubuntu is to go with 32-bit for a while then move up to 64-bit. Hope this can be of help to you :D

Good luck with your Ubuntu install!!!

Thanks! I think what I will do is install 64 bit first and if I fail miserably I will just go 32. One final question though I've seen a few people say that if I install the beta of Gutsy now and let it update in 2 days it will be the same as if I had waited. Is this true?

---

### Post by phidia on 2007-10-16
> **obesus_puer said:**
> Thanks! I think what I will do is install 64 bit first and if I fail miserably I will just go 32. One final question though I've seen a few people say that if I install the beta of Gutsy now and let it update in 2 days it will be the same as if I had waited. Is this true?

Actually the release candidate is out now. That means it's out of beta-although there still could be bugs/issues. And yes you can always upgrade to the latest release. Re-read your question: Using update manager will update the system to current state-hope that answers that :)
It would be good to let others reading this know how your install worked when you get to it.

---

### Post by obesus_puer on 2007-10-16
> **phidia said:**
> Actually the release candidate is out now. That means it's out of beta-although there still could be bugs/issues. And yes you can always upgrade to the latest release. Re-read your question: Using update manager will update the system to current state-hope that answers that :)
It would be good to let others reading this know how your install worked when you get to it.

Thanks I will probably install tonight then. I'll let you all know how it turns out. Thanks everyone for your input! I'm sure I'll have many more questions in the future!

---

### Post by Eriksmits596 on 2007-10-16
Good luck:)

---

### Post by Myglaren on 2007-10-16
I tried 64 bit Dapper on this machine (Athlon 64 3200+) and while the OS was fine it was a bind to get some things to work, most notably Firefox and Flash.
Reinstalled the 32-bit and all was well.

There have been a couple of problems with Feisty 32 - all but the primary desktop have a habit of nothing being there when I switch to them - like diving into a black hole.  Also the Desktp Effects only worked for a couple of minutes and there was only ever one desktop anyway.

In preparation for Gutsy I installed the 64 bit version of Feisty a few days ago and all seemed to go reasonably well with the exception of, while the desktop effects now work well, I'm still more often than not plunged into limbo if I step from one desktop to where another should be.

Firefox and Flash are both fine except some of the icons are missing from Firefox and the controls missing from the YouTube screen.

It does seem faster and smoother though.

---

### Post by EnigmaX on 2007-10-16
I'm currently using Fiesty 64 but plan on going to 7.10.  I gave up on FF & Flash and installed Swiftfox 2.0 instead (headache solved).

---

### Post by obesus_puer on 2007-10-16
> **EnigmaX said:**
> I'm currently using Fiesty 64 but plan on going to 7.10.  I gave up on FF & Flash and installed Swiftfox 2.0 instead (headache solved).

I found a script somewhere on the forums that is supposed to fix it. I'll give it a shot once i have everything installed. Oh why must I be stuck at work! stupid users... always calling me...

---

### Post by haden9 on 2007-10-16
> **rsambuca said:**
> 1GB of RAM is plenty for running 64bit Ubuntu, so please don't make that an excuse or an issue.

My bad, I didn't mean for it to sound that way but sadly it did (and no my intension was not to make it an excuse or an issue for him)... Anyways it seems you made your decision so good luck with your install again :)

---

### Post by obesus_puer on 2007-10-16
Downloading Gutsy now 14min to go.
As a side note... this Laptop came with Vista and after 20minutes of playing with it I HATE it.

---

### Post by obesus_puer on 2007-10-16
Booting Gutsy 64 disk now! here goes nothing!:)

---

### Post by obesus_puer on 2007-10-16
I have successfully booted into Ubuntu. I am actually posting this from within it. Wireless is working! Time to click install =)

---

### Post by obesus_puer on 2007-10-16
Ubuntu installed great... unfortuanately my sound does not work. It played a tune after installing. but now it seems it is permanently muted. :confused:

---

### Post by barkej on 2007-10-16
Hmmm...Maybe it's time for me to give 64 bit a try again, I have not tried 64bit Ubuntu since Dapper.

---

### Post by barkej on 2007-10-16
Well. Everything seems to be working on the 64bit install of Feisty. I have to say that I am pretty impressed with the speed increase i am seeing.

---

### Post by obesus_puer on 2007-10-17
> **barkej said:**
> Well. Everything seems to be working on the 64bit install of Feisty. I have to say that I am pretty impressed with the speed increase i am seeing.

Congrats. I'm pretty impressed to. I managed to get the sound working by installing updated alsa drivers. But I kinda winged it. After restarting it stopped working.

---

### Post by phidia on 2007-10-17
> **obesus_puer said:**
> Congrats. I'm pretty impressed to. I managed to get the sound working by installing updated alsa drivers. But I kinda winged it. After restarting it stopped working.

With sound probs it could easily be something simple.
Rather than re-invent the wheel though it's easier to use the audio troubleshooting guides already [available]("http://ubuntuforums.org/showthread.php?t=565925&highlight=no+sound").

Note: there is a sound troubleshooting thread in the thread i linked (it should be a sticky IMO)
Hope that helps.

---

### Post by Officer Dibble on 2007-10-17
This thread has been very useful... I'll be rereading this tomorrow when I'm 64bit

---

### Post by obesus_puer on 2007-10-17
> **phidia said:**
> With sound probs it could easily be something simple.
Rather than re-invent the wheel though it's easier to use the audio troubleshooting guides already [available]("http://ubuntuforums.org/showthread.php?t=565925&highlight=no+sound").

Note: there is a sound troubleshooting thread in the thread i linked (it should be a sticky IMO)
Hope that helps.

Sound is now working. I followed a guide this time to compile and install the drivers. The only thing that I know of that isnt working at this point is Desktop Effects.

---

### Post by phidia on 2007-10-18
> **obesus_puer said:**
> Sound is now working. I followed a guide this time to compile and install the drivers. The only thing that I know of that isnt working at this point is Desktop Effects.

Congrats 2 U!!!!!!!!

I hope everyone interested in 64bit checks out the 64bit section [here]("http://ubuntuforums.org/forumdisplay.php?f=134").

I'm sure someone has some ideas about desktop effects there.

---

### Post by lmlypfan on 2007-10-18
I tried 64bit feisty, and it didn't work out very well.  Flash was my main problem
Currently running Gutsy 64bit and love it.  
Much faster then 32bit IMO, and I'm only running 2 gigs of ram

---

### Post by obesus_puer on 2007-10-18
> **sasquatch74 said:**
> My apologies if you have already seen this, but [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61") post on ThinkWiki got my Desktop Effects working.  I have a r61 with the same chipset, but I have the 32 bit version installed, not the 64 bit.  I don't know if it makes a difference in this case, I hope it works for you!

This solved my enabling Desktop Effects problem. Hope it can help someone in the future.

---

