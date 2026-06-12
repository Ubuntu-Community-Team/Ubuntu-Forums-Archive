---
title: "[SOLVED] I fail at iso burning"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by thenewgirl on 2008-02-27
Well, I downloaded Ubuntu 7.10 alternate and ran md5sums. So far so good. Then I burned the CD using InfraRecorder. I set the boot to the CD drive and restarted my computer. I was able to get the menu screen (yay) but when I chose the CD integrity check I got the following: 

> [ 44.654512] PCI:Cannot allocate resource region 1 of device 0000.00.14.0

Pretty sure that is bad :(.

Any suggestions?

PS I tried to burn it as slowly as possible, but InfraRecorder had a slowest speed of 16x.

---

### Post by thenewgirl on 2008-02-27
And I am leaving work soon, but I will check back with you good people a little later when I can get to a computer. 

Many thanks.

---

### Post by matherians2 on 2008-02-27
If you are trying to burn with windows, then try this:
[http://www.terabyteunlimited.com/downloads-free-software.htm](http://www.terabyteunlimited.com/downloads-free-software.htm)

---

### Post by thenewgirl on 2008-02-28
Ok, I've used the program from terabyte to burn a new image at 4x. 

Now my question is, is it possible to completely screw up my work computer in any way if I try to check the cd here? I mean, is there any way that if the cd is not proper it will damage my computer?

---

### Post by taurus on 2008-02-28
No chance to screw up the computer if you just run the Check CD for Defects.  In fact, you should run that option to make sure the CD is good before you attend to boot or install from it.

---

### Post by thenewgirl on 2008-02-28
I figured so, but I didn't want to take any chances at work. Thanks!

---

### Post by thenewgirl on 2008-02-28
I got the same message this time only with a different number in the [ ]. Man this is frustrating! What am I doing wrong? :confused:

---

### Post by thenewgirl on 2008-02-28
I know it's only been an hour since my last post. Just doing the *bump* to see if anyone knows specifically what the message I got means?? 

I figure if I know why it's not working I can avoid making the same mistakes again -- hopefully!

Thank you for helping me out! I really want to understand what I'm doing and learn more about computers/linux. I have skated on what little I know in Windows, but I've never tried to intall any OS before.

---

### Post by Duck2006 on 2008-02-28
Here are some tips that may help.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by thenewgirl on 2008-02-28
Thanks. I'll try again.

---

### Post by thenewgirl on 2008-02-28
Nevermind...tried it again and it worked...

---

### Post by thenewgirl on 2008-02-28
Ok, I've gotten to the point where I am ready to burn the ISO to a disk. But in InfraRecorder it is not giving me the option to slow the speed of the burn. That section is greyed out. Any input?

---

### Post by drunkardivan on 2008-02-28
I haven't had any difference burning at faster speeds, and I've been downloading Linux distros a lot lately, trying to find one that "just works" on my wife's laptop.

You should be fine burning at a faster speed, I think the "burn at 4x" is just an engineer's conservatism.

---

### Post by Oldsoldier2003 on 2008-02-28
> **thenewgirl said:**
> Thanks. I'll try again.
I hope you're having better luck. Best advice I can give is burn on a good quality CD at a slow speed. run your checks to make sure it burned clean... and oh yes make sure its not one ot the old 640mb cd's hiding in the bacck of the closet lol!

---

### Post by akiratheoni on 2008-02-28
> **drunkardivan said:**
> You should be fine burning at a faster speed, I think the "burn at 4x" is just an engineer's conservatism.

This is true. I've burn at 8x and all of my CDs have been fine. I think at one point I may have even done 12x.

---

### Post by thenewgirl on 2008-02-28
I know that the drive has a max speed of 48x though and in InfraRecorder it is set to record at max speed without the option to change that. Wouldn't that be taking it too fast??

---

### Post by p_quarles on 2008-02-28
InfraRecorder is a full-featured burner, but you don't really need all those features for this task. If the next try doesn't yield better results, maybe see if you have luck with another application:
[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by xeth_delta on 2008-02-28
Give the following writing programs a try:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
[http://burncdcc.en.softonic.com/](http://burncdcc.en.softonic.com/)

---

### Post by thenewgirl on 2008-02-28
I'll take a look at those. Thank you. I believe that burncdcc is the one mentioned by another poster which I already downloaded and tried once. I was just trying to use InfraRecorder in order to follow the tutorial to the letter :redface:.

---

### Post by sneeks on 2008-02-28
hi,i found that image burn is almost foolproof for iso's,give it a go and im sure all will be fine but do try and burn at a slow speed as has been said before.
if still a problem,try d/l the iso file again just in case it is corrupted.

---

### Post by thenewgirl on 2008-02-28
Thanks. I am going to try Image Burn since it's the only one I haven't tired yet!

Also, is it possible the dl is corrupted even if checksums came out fine? I thought that meant everything was a-ok??

---

### Post by sneeks on 2008-02-28
i have d/l some other versions of ubuntu before that were a prob,but that was a while ago,a lot of peeps here say to try the torrent d/l,but i have always done it straight from site.
mind you saying that,have a version here that worked on my sons pc but not a newer laptop,got the kerrnel alert thing so d/l another,and it seemed ok,mind you that was an edubuntu disc for nursery's.
i think once you have a stable file,all will be ok,just burn slow......
then boot from live cd,you will love it..

---

### Post by thenewgirl on 2008-02-28
Alright I got Image Burn and I am just about to start it. On the right hand side in the write section it says my drive has supported write speeds of 16x, 24x, 40x and 48x. So does that mean I should do it at 16x because my drive itself won't write it slower?? 

Man, I never knew I was *this dumb* about computers!

---

### Post by sneeks on 2008-02-28
on the speed box there should be an arrow to burn slower,just scroll down to the speed you want..:KS

---

### Post by thenewgirl on 2008-02-28
Oh, yeah, I saw that but then when I saw the part about my drive only **supporting** those speeds I thought it might mess it up to do it at another speed.

What I don't know could fill a 500 gig hard drive...:-({|=

---

### Post by thenewgirl on 2008-02-28
This is the third time I've tried burning the cd, the third burning utility I have used to do so, the third time I've consulted a tutorial every step of the way and the third time I want to pull all my hair out in frustration. Can it really be this difficult just to get a working cd???

I get this message yet again when I run the cd integrity check:

> [ 34.645488] PCI: Cannot allocate resource region 1 of device 0000:00:14.0

I am feeling pretty foolish for even trying this at this point. Am I just totally missing the mark here??

Anyway, if there are any other ideas I would still like to get this working. So frustrated :(.

What does the message I got mean???

---

### Post by p_quarles on 2008-02-28
Have you tried just running the live desktop, and skipping the integrity check?

---

### Post by thenewgirl on 2008-02-28
No because I downloaded and burned the alternate cd on the suggestion of a forum member since I was planning to just wipe out Windows rather than dual boot. Guess I could try doing the LiveCD and then run the live desktop?? Would that help somehow?

---

### Post by p_quarles on 2008-02-28
> **thenewgirl said:**
> No because I downloaded and burned the alternate cd on the suggestion of a forum member since I was planning to just wipe out Windows rather than dual boot. Guess I could try doing the LiveCD and then run the live desktop?? Would that help somehow?
Basically, I'm thinking that something could be preventing the computer from running the integrity check, and that this has nothing to do with the actual integrity of the disk.

It doesn't matter which disk you're using, and I don't think you need to make more coasters. Just skip the integrity check, and see if it works. Nothing bad will happen if it doesn't.

---

### Post by thenewgirl on 2008-02-28
> **p_quarles said:**
> Basically, I'm thinking that something could be preventing the computer from running the integrity check, and that this has nothing to do with the actual integrity of the disk.

It doesn't matter which disk you're using, and I don't think you need to make more coasters. Just skip the integrity check, and see if it works. Nothing bad will happen if it doesn't.

I was wondering that as well about it being related to the computer itself. You know what I've been trying to check the disks on my work computer. I will try to run the integrity check on my laptop (the one I am actually trying to get Ubuntu on). And whether it checks it or not try the install. As long as I am not able to render my computer unusable I am fine with trying.

PS I really appreciate the help!

---

### Post by sneeks on 2008-02-28
if i was close i would bring you the disc!!!!!
but hey this is the wild web.
can you post any results?

---

### Post by thenewgirl on 2008-02-29
Well, I took the advice of p_quarles. Actually I did run the integrity check on my laptop at home and it said the cd was valid!! So I went ahead with the install. Everything seems to be perfect but it went by really quickly so I have a couple of additional questions:

1) Right at boot there was a message about bug #81 something BIOS. It went by so fast that I wasn't able to catch it all and write it down. So if that sounds like something I should be worried about please do let me know!

2) I did the Guided - use entire disk option and it created an ext3 partition and a swap partition. I get what a partition is, but I have read on here that there should be a /home partition as well. Did I mess up?

3) It was unable to set up the network (DHCP or something?). Yeah, sorry I didn't get good info there to get advice on. But I was given the option to set it up manually or not set it up. I chose not. I am hoping if necessary I can do that after the fact. 

Sound seems to be working. As I said before I don't have internet connection right now so I haven't been able to test that. Don't know if it would have given me some kind of error if it couldn't detect my wireless?

I booted up and logged in with the user name and password I set up at install...that is a user right, I am not running as admin (or root right)?

My friend was over at my house and was so impressed with the look and how easy it was she said she might try it. So I gave her a cd seeing as how I had made so many! 

Couldn't believe how fast it runs without all that antivirus and crap running in the background! When I went to shut my computer down it went off *quick*. Windows usually took minutes to shut down. 

Well, I've gone on long enough!! Hopefully one of you can help me out with the 3 "issues" above. If those things are worrisome, I could always install it fresh. I am pretty proud of myself and glad I stuck with it. It may not seem like such a huge accomplishment, but it feels like it to me. :cool:

---

### Post by Oldsoldier2003 on 2008-02-29
> **thenewgirl said:**
> Well, I took the advice of p_quarles. Actually I did run the integrity check on my laptop at home and it said the cd was valid!! So I went ahead with the install. Everything seems to be perfect but it went by really quickly so I have a couple of additional questions:

1) Right at boot there was a message about bug #81 something BIOS. It went by so fast that I wasn't able to catch it all and write it down. So if that sounds like something I should be worried about please do let me know!

[COLOR="Red"]2) I did the Guided - use entire disk option and it created an ext3 partition and a swap partition. I get what a partition is, but I have read on here that there should be a /home partition as well. Did I mess up?[/COLOR]

[COLOR="Red"]3) It was unable to set up the network (DHCP or something?). Yeah, sorry I didn't get good info there to get advice on. But I was given the option to set it up manually or not set it up. I chose not. I am hoping if necessary I can do that after the fact.[/COLOR] 

Sound seems to be working. As I said before I don't have internet connection right now so I haven't been able to test that. Don't know if it would have given me some kind of error if it couldn't detect my wireless?

[COLOR="Red"]I booted up and logged in with the user name and password I set up at install...that is a user right, I am not running as admin (or root right)?[/COLOR]

My friend was over at my house and was so impressed with the look and how easy it was she said she might try it. So I gave her a cd seeing as how I had made so many! 

Couldn't believe how fast it runs without all that antivirus and crap running in the background! When I went to shut my computer down it went off *quick*. Windows usually took minutes to shut down. 

Well, I've gone on long enough!! Hopefully one of you can help me out with the 3 "issues" above. If those things are worrisome, I could always install it fresh. I am pretty proud of myself and glad I stuck with it. It may not seem like such a huge accomplishment, but it feels like it to me. :cool:

Not setting up a /home partition won't "kill" you. its recommended for several reasons one of which is that having a separate partition for data is always a good idea.

You can set up networking later, not a problem

If you logged in as the user you created on setup you are not "Root". The first user of the system is part of the "admin" group so you can use sudo to access root functions.

I'm glad to see that you got sorted out and hope you enjoy your Ubuntu experience! As always there are tons of helpful people here to help you if you need a hand.

---

### Post by thenewgirl on 2008-02-29
I am really excited to get into this and check out everything there is to my new OS.

Thanks for your quick answers, Oldsoldier! 

As for a separate /home partition, can I still set one up now using gParted or something without disrupting anything??

---

### Post by p_quarles on 2008-02-29
> **thenewgirl said:**
> I am really excited to get into this and check out everything there is to my new OS.

Thanks for your quick answers, Oldsoldier! 

As for a separate /home partition, can I still set one up now using gParted or something without disrupting anything??
Yes. Read this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by thenewgirl on 2008-02-29
Wow, that looks daunting, but I believe I can do it. And anyway there isn't anything I've saved on there yet, so I could always start over. 

Now I need to burn a LiveCd #-o

I am pretty sure I will have questions so watch out...

---

### Post by forrestcupp on 2008-02-29
If your install is working ok, I don't think you really have to worry about the BIOS error.  There is really no reason to download and burn a Live CD if you already have it installed.  You've already been through enough of burning CD's.

If you could find out what kind of wireless you have, people might be able to help you out with that, too.

---

### Post by thenewgirl on 2008-02-29
> **forrestcupp said:**
> If you could find out what kind of wireless you have, people might be able to help you out with that, too.

Is there a command to do that? :) 

Hehehe, yeah I don't know much, but I am willing to learn...

---

### Post by xc3RnbFO8P on 2008-02-29
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138305]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138305")

Found this on the www:

> Try adding hpet=disable to your kernel options (F6 on the live CD)

Try to set Bios to default:

[http://ubuntuforums.org/showthread.php?t=641354]("http://ubuntuforums.org/showthread.php?t=641354")

Or maybe you have to flash your Bios:

[http://www.cyberwalker.com/article/30]("http://www.cyberwalker.com/article/30")
[http://www.cyberwalker.com/article/671]("http://www.cyberwalker.com/article/671")

---

### Post by forrestcupp on 2008-02-29
Your best bet is to go to the laptop's manufacturer's web site and look up the specs on your laptop.  Hopefully it will show the wireless model/chipset.

But you should go to System->Administration->Restricted Drivers Manager and see if it automatically lists your wireless card.  If so, just install the drivers through that.

---

