---
title: "gutsy and Sunbird 0.7 running?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-10-31
Hi all,

Anyone have Gutsy and Sunbird 0.7 running together? If so, how did you do it? I tried paralleling the 0.5 Sunbird install and it doesn't execute. I was able to get the 0.7pre version running but not 0.7. Any ideas or suggestion much appreciated!

Thanks,
Jim M

---

### Post by jamere on 2007-11-01
gratuitous bump

---

### Post by haldean on 2007-11-01
what do you mean by paralleling?
i haven't done it myself but it looks like if you go to the webpage you can download [http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.7/linux-i686/en-US/sunbird-0.7.en-US.linux-i686.tar.gz](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.7/linux-i686/en-US/sunbird-0.7.en-US.linux-i686.tar.gz) that and install from source to get 0.7 or use ```
sudo apt-get install sunbird
```although the one in the repository currently is 0.5

---

### Post by jamere on 2007-11-01
haldean, thanks for the reply. I installed Sunbird 0.5 months ago using a "How To" procedure and it worked fine. I then installed 0.7pre and it worked fine also for several months. I downloaded newest 0.7 from mozilla following the 0.5 How To procedure. Everything installed ok but Sunbird won't execute. I suspect I have some sort of permission problem or the 0.7 version is faulty.

That's why I asked if anyone had successfully installed 0.7 on Gutsy and how they did it. Apparently not many on Gutsy AND Sunbird 0.7 yet. I know just enough about Linux installs to be dangerous! 

As a side note, I know some of the guys developed Ubutuzilla scripts to install the latest Firefox and Thunderbird versions (Thanks guys for the great work). Would be nice to add other standard apps such as Sunbird to Ubuntuzilla for those wanting or needing the latest app versions before they show up in the repos.

---

### Post by nanotube on 2007-11-01
> **jamere said:**
> 
As a side note, I know some of the guys developed Ubutuzilla scripts to install the latest Firefox and Thunderbird versions (Thanks guys for the great work). Would be nice to add other standard apps such as Sunbird to Ubuntuzilla for those wanting or needing the latest app versions before they show up in the repos.

i'll think about it - and hopefully get around to it fairly soon :) 
could you please submit a feature request on the ubuntuzilla sf.net project site, just so i don't forget?

---

### Post by jamere on 2007-11-01
Be glad to submit a request nanotube, and THANKS! Will be great to get the latest standard apps installed via Ubuntuzilla.

Thanks much,
Jim M

---

### Post by haldean on 2007-11-01
It works fine for me. I downloaded, extracted, double-clicked "sunbird", pressed "Run", and all was good, even with 0.5 still installed! I'm running Gutsy, fully upgraded.

What exactly isn't working for you?

---

### Post by KOld Iron on 2007-11-01
jamere,

I did the same thing as haldean. I had Sunbird 0.5 installed through Gutsy. Yesterday I downloaded Sunbird 0.7 directly from its web site, unzipped it and just started "sunbird" (actually I redirected my quick launch starter to the new file), even though I never removed the 0.5 version. Worked just fine, as a matter of fact, it even picked up the holiday.ics I had added to the 0.5, so I guess the new version is using the profile from the old version (being new with Ubuntu I am guessing here a little).

Heinrich

---

### Post by jamere on 2007-11-01
haldean and Kold Iron, thanks for the replies. I downloaded the tar file to my Desktop and extracted it there. I then moved the Sunbird directory to /opt and am trying to execute Sunbird from there. I double-click on the executable and nothing happens which leads me to believe there's a permission problem or something else.

Where are your extracted files located? I may be over-complicating this thing. I may be mistaken but I think my previous Sunbird installs were in /opt.

I may try to re-install and leave the extracted files on the Desktop and try to execute from there.

Anyone have any idea where Sunbird executables should be properly installed?

Thanks again guys,..
Jim

---

### Post by Maestro23 on 2007-11-01
> **jamere said:**
> haldean and Kold Iron, thanks for the replies. I downloaded the tar file to my Desktop and extracted it there. I then moved the Sunbird directory to /opt and am trying to execute Sunbird from there. I double-click on the executable and nothing happens which leads me to believe there's a permission problem or something else.

Where are your extracted files located? I may be over-complicating this thing. I may be mistaken but I think my previous Sunbird installs were in /opt.

I may try to re-install and leave the extracted files on the Desktop and try to execute from there.

Anyone have any idea where Sunbird executables should be properly installed?

Thanks again guys,..
Jim

/opt is owned by root.  You need root permission to do anything in there.  For GUI root thru Nautilus, Open a terminal:

> gksudo nautilus

Command line:

> sudo 

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by haldean on 2007-11-02
Well you don't really have to "install" it anywhere - you just run it from the folder. For me, I untarred it to my Desktop and just double clicked it there, and it worked fine. Make sure you're double-clicking on sunbird, and not sunbird-bin as well, otherwise it won't work.

---

### Post by jamere on 2007-11-02
haldean,
I've installed and used several versions of Sunbird with no problems in the past. I re-downloaded and installed to desktop as you did. For some reason Sunbird will not start on my system. I also tried with the newest 0.8 and got the same result. I'm beginning to suspect that the extraction process is not working correctly in that no Sunbird profile is generated and no hidden files of anykind. I'll re-post if I can figure out what's going on.

Thanks for your interest,
Jim

---

### Post by jamere on 2007-11-03
Finally a solution...

See thread by "bonejob" here

[http://ubuntuforums.org/showthread.php?p=3697601#post3697601]("http://ubuntuforums.org/showthread.php?p=3697601#post3697601")

or search on "sunbird 0.7"

---

### Post by KOld Iron on 2007-11-04
I guess I should have mentioned it right the first time, but I just made a folder called "apps" in my home directory and there I have the files put into a sub-directory called "sunbird". Which would agree with your suspicions about the permissions, because in my home directory I would have the needed permissions, of course. I did this mainly because it was a parallel install and also because I am not yet so familiar with the directory structure being a newbie on Linux. So far no problems with this setup.

Edit: I just followed your link on the other thread with respect to the dependency on Java. I guess I never realized that in my case, because I believe I had Java installed as part of Azureus, if I remember correctly (before I tinkered with Sunbird). So that never was an issue for me, but very good to know, indeed.

---

### Post by jamere on 2007-11-04
Kold Iron,

Looks like you've found a way that works for you for installing apps. I was quite surprised to find that my problem was that my Java was out-of date! I had absolutely no indication of errors even on syslog. All I knew was that Sunbird wouldn't launch, leading me to believe that I had a permission problem of some kind. If I hadn't stumbled onto "bonejob"s posts, I'd still be looking for a solution. :)

Which brings me to another point...why can't the LATEST  "mainstream apps like Firefox, Thunderbird and Sunbird find their way into the repos much sooner? Once there, newbies like us could use Synaptic to "properly" install them. I know just enough to be dangrous with installs! Thanks for your input on the thread.

Jim

---

### Post by KOld Iron on 2007-11-04
Hi Jim,

I fully agree with you. But I believe one of the really big advantages of Ubuntu is this forum! I did a few searches on some problems myself and always found an answer (most of them positive). It's a great community, which helps a lot, particularly during the beginning. I guess this is part of the experience using Ubuntu, at least that's the way I see it.

Your point on providing the LATEST releases is not new, and at least for Firefox and Thunderbird there is a solution called Ubuntuzilla (Sunbird may be supported as well in the future). I have not tried this yet myself, but will look into this probably once Firefox 3 comes around, if that upgrade is not covered by Ubuntu in time (there are also good reasons, why Ubuntu does take the slower approach, e.g. focus on stability).

Anyway, here is the link to Ubuntuzilla: [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Heinrich

---

### Post by jamere on 2007-11-04
Hi Heinrich,

> I fully agree with you. But I believe one of the really big advantages of Ubuntu is this forum! I did a few searches on some problems myself and always found an answer (most of them positive). It's a great community, which helps a lot, particularly during the beginning. I guess this is part of the experience using Ubuntu, at least that's the way I see it.

I wholeheartedly agree...the forums are a great resource! Ubuntuzilla is another great resource provided by Nanotube. I installed the latest Thunderbird from his site fairly recently and it worked without a hitch. In general, I'm really happy with Ubuntu Linux. My pc stays up 24-7 (since 2004) and I've never had a kernel failure. Pretty good testimonial for Linux reliability! Now if we could just get the  latest versions in the repos sooner, I'd be a happy camper! :)

Jim

---

