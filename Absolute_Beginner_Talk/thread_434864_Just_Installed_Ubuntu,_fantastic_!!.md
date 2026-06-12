---
title: "Just Installed Ubuntu, fantastic !!"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Julian Lewis on 2007-05-06
This is great, apart from a few small problems ...

1) Real Player isn't working correctly. From what I read here I am not alone.
2) Flash player insists on using the speakers and wont talk to my USB audio, even though I set the sound preferences to use USB. 
3) The add printer function crashes when I try to declare a LPD network printer, but I did manage to do it accross the CUPS daemon web interface on localhost:631
4) Networks are a bit clunky when changing locations or when switching between wireless and wired. It seems that I have to turn off "wired" before wireless will work correctly, even though I have a wireless link established.
5) Remotley hosted files are not accessed in all cases by all programs, for example picasa2 needs the pictures to be on the local drive. This seems to be a general problem.
6) As a result of point 5, I now have 37Gigs on MP3s on my hard drive, and another 10Gigs of photos that I had to copy. Can any one tell me if there is a way of compressing the data.
7) Firefow has difficulties with some web sites [www.meteosuisse.ch](www.meteosuisse.ch) crashes, but its ok on firefox under XP

All in all, moving to Ubuntu has been a huge amount of fun, I will never go back to windows.
I guess most people were like me, using windows because they were affraid to try.
This forum has been a huge help. Thanks:)

---

### Post by crispy_420 on 2007-05-06
1. I'm not having realplayer issues, but then again I hardly use it,
2. Had the same issue when I had mobo and soundblaster turned on, disabled on board audio and problem solved.
3. Try installing and setting up swat to handle printers.
4. Depending on wireless card, it may be slow. A good example: atheros chipset is slow to connect but flawless once connected.
5. Never tried so no comment.
6. Again no comment.
7. Tried it worked for me on dapper.

---

### Post by rfs1970 on 2007-05-06
Hi There,

1) Did you try to install Helix Player (its a open source version of Real Player).
6) I believe you will not get any compression from your mp3 files, cause they are already compressed. 

r.

---

### Post by Julian Lewis on 2007-05-06
Hmm just tried it, no joy. Basicly RealPlayeied is horrible I hate it, too invasive.  The BBC site has only RealPlayer or Media player as a choice for how to watch their videos. As both of these are %^&$%# then I guess the BBC is simply not interersted in providing Microsoft free ways of looking at their web pages. They will either change their policy, or realplayer will get its act together, or more and more people will  stop looking at their web pages. When I used windows I was very hesitant to install RealPlayer, it always seemed to be taking over my entire computer, like AOL. Anyway MPLAYER seems to work, sort of, Horibl;y slow and keeps stopping, but gets there in the end.... 
Now that DELL is backing Ubuntu, people will change their tunes in the near future, I will just wait till then
Cheers, thanks for the help in any case.

---

### Post by MoxJet on 2007-05-06
You can't compress mp3 and images without losing data. Mp3 is already as compressed as possible for its bitrate.

(ok ok, the files may get a few percent smaller with vorbis instead, but that's another issue)

SSH gives you a great way of mounting remote directories, should you ever need it in any of your running applications. You can find a nice howto here:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

Good luck!

---

### Post by Brian Levy on 2007-05-06
Funny about Dell moving finally to support Linux.  More years ago than I'd care to remember I was a Tandy 16 Xenix user when Tandy discontinued the line and I decided to move to SCO on Intel.  After trying to install it on several commercially available IBM clones, I called SCO and asked them what they used there as their standard machine and they gave me this telephone number to call.  I called and some guy named Michael Dell answered the phone. It seemed SCO was one of his corporate accounts and he was selling them 286 machines that worked on SCO.  I never heard of the company nor the guy.  At the time he was the order taker, builder, QC person and shipper.  At the time the 386 was just coming out but I wanted exactly what SCO had so went with the 286.  When it arrived, the case said 386 and when I queried him he told me he had run out of 296 labeled covers and used a 386 cover.  SCO still would not run but then I found out that SCO was adding a RAM board to the Dells.  Michael was unaware they were putting them in to get Xenix to run when I called about it and he sent me 1 to install.  I spent a fortune loading it with chips to fill it to capacity (3 megabytes) at a time when most machines were still 640 megs and only the hotshots were going to 1 meg.  My 4 meg machine was as hot as they came.  I had the 40 meg hard drive and later got a SCSI board and added the 4 Tandy harddrives fromt he 16 with the firm data, with each being the size of the computer.  On Xenix, with 5 Wyse terminals the unit ran 24/7 with never a reboot for almost 5 years.  My brother meanwhile in his firm was using IBM machines with multi-dos and a hub lan and was rebooting at least 3-4 times per 8 hour days and it never did run right.  It is great to hear Dell is going back to its roots.

---

### Post by Julian Lewis on 2007-05-07
Nice to hear your story, some of us old f*rts have been playing with Unix a long long time. I hope that Dell has severed all connections with SCO. The behaviour of SCO towards the open source Linux comunity will be their downfall. The IBM SCO case has been going on for a long time in the courts, I have been following the case on slashdot for years and it seems their attempts to destroy the GPL and claim ownership of GPL sources is about to collaps. I will be very pleased to see the back of them. We had now better get ready for the next attack comming from Microsoft. Lucily outside the US they don't stand a chance, we shall see.
PS in my day twenty or so proggrammer were all able to develope code at the same time on a 32K PDP11 with glass teletypes under RSX11, I started coding on a PDP 8 with 12K a real ASR32 teletype, and the storage device was a paper tape reader on the ASR, it ran with 110 baud connection!! I bet there arn't many out there who can beat that.

---

### Post by motin on 2007-05-07
2) I know I had to change some sort of text-file to change Flash's output from oss to alsa - guess it isn't connected with the central sound settings. Make a separate post on this and I believe you'll get replies. 
5,6) You can mount remote file systems in folders in your system - so that programs thinks they are local. Search on terms like FUSE, smbfs, sshfs and the likes. 

> **Julian Lewis said:**
> I guess most people were like me, using windows because they were affraid to try.This forum has been a huge help. Thanks:)

Agrees whole-heartedly. 

Good luck with finding solutions mate!

---

