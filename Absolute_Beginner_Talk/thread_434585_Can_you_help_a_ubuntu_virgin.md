---
title: "Can you help a ubuntu virgin?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by belair14486 on 2007-05-06
Hi all
Here's the thing iv been using windows as long as i can remember using a computer so im totally used to it. But after getting so many problem with windows over the years im pretty much fed up now.
So i was looking at the linux OS's since iv been hearing about how much better than windows its meant to be. I know it can be somewhat harder to operate than windows for some things but iv no problem with trying to learn it. But before i jump in heads on theres just a couple of questions i wanted to ask and hoped that the community out there could help me with, even if its just giving me a link to a guide or telling me. My questions are pretty easy or so i think.

My first question is, im a gamer i love my pc games espically world of warcraft and command and conquer3 what i would like to know if it would still be possible to play these on Ubuntu?

The other thing is i have a zboard and Zboard Fang, iv had alot of problems with trying to install these onto windows because my windows wont install the drivers.

Also if i was to change over to Ubuntu or something similar how would i go about it? would i need to get rid of windows completely or wipe my HDD? and would installing ubuntu like installing windows?

Guys i would be very gratefull for any info you could pass onto me cause i really intrested in switching to Ubuntu or a similar software. An will appreciate any help.

thanks Steve.

P.S. Dont know if this matters but thought i would leave the info of my computer incase that helps.

CPU: AMD 3.4ghz 64bit
Memory: 2.00gb
HDD: 200gb (180gbwith windows installed for some reason)
Motherboard: ASUS KV8
Video Card: Radeon 9600SE 128mb
Current OS: Windows XP Pro 32bit edition + SP2

Thanks again in advance.

---

### Post by Najand on 2007-05-06
> **belair14486 said:**
> Hi all
Here's the thing iv been using windows as long as i can remember using a computer so im totally used to it. But after getting so many problem with windows over the years im pretty much fed up now.
So i was looking at the linux OS's since iv been hearing about how much better than windows its meant to be. I know it can be somewhat harder to operate than windows for some things but iv no problem with trying to learn it. But before i jump in heads on theres just a couple of questions i wanted to ask and hoped that the community out there could help me with, even if its just giving me a link to a guide or telling me. My questions are pretty easy or so i think.

My first question is, im a gamer i love my pc games espically world of warcraft and command and conquer3 what i would like to know if it would still be possible to play these on Ubuntu?

The other thing is i have a zboard and Zboard Fang, iv had alot of problems with trying to install these onto windows because my windows wont install the drivers.

Also if i was to change over to Ubuntu or something similar how would i go about it? would i need to get rid of windows completely or wipe my HDD? and would installing ubuntu like installing windows?

Guys i would be very gratefull for any info you could pass onto me cause i really intrested in switching to Ubuntu or a similar software. An will appreciate any help.

thanks Steve.

P.S. Dont know if this matters but thought i would leave the info of my computer incase that helps.

CPU: AMD 3.4ghz 64bit
Memory: 2.00gb
HDD: 200gb (180gbwith windows installed for some reason)
Motherboard: ASUS KV8
Video Card: Radeon 9600SE 128mb
Current OS: Windows XP Pro 32bit edition + SP2

Thanks again in advance.

Please try to write shorter messages. 
1. Yes, you can use a package called "wine" to use windows applications on linux. However they are not linux native softwares and there are limitations with using wine. So there won't be any guarantee for that.

2. As far as I know those guys in IDEAZON[TM] have only windows drivers... However they have been working on developing drivers for other Operating Systems like linux.

3. You don't need to wipe your current windows... Just defrag it and make an open room for ubuntu... Then use Ubuntu Live CD to resize windows . Make a new partition for linux and another one for the swap. Then install it on it.

---

### Post by Cappy on 2007-05-06
Wow works. Command and Conquer 3 is newer and has the bug that it won't work on the internet/network.

ZBoard support: It doesn't look like it is supported but you can set it up yourself:
[http://gentoo-wiki.com/HOWTO_Zboard](http://gentoo-wiki.com/HOWTO_Zboard)
Probably not the first thing you'll want to do when you start using linux but you can learn at your own pace if you still have Windows installed.

If you use linux you should keep your windows partition so that you can dual boot to play Command and Conquer or other games that may not work on linux atm. You would need to resize your windows partition using the Ubuntu Live CD and then devote the new space you created to Ubuntu. This will let you choose if you want to use Windows or Linux when you boot your computer.

---

### Post by belair14486 on 2007-05-06
Thanks guys im glad to get such quick replies with good info. Sounds like linux is definetly the way to go then. sorry bout length of post, you guys are talking bout resizing windows with the linux cd does that come with downloading it from ubuntu? where i would just burn it to disk. would i need to set it up manually or will it do it pretty much auto? i tried my zboard the keyboard and it worked but the Fang gamepad still doesnt not to bothered anymore to tell ya the truth guess just need to keep looking for a solution

---

### Post by Cappy on 2007-05-06
You'll have to resize Windows manually. The only options Ubuntu has is to wipe the disk and install or use free space on a disk (which you would setup). You do it with the Ubuntu CD.
Alternatively, you can try:
[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
It doesn't require partitioning to run Linux + Windows XP side by side.

---

### Post by sailor2001 on 2007-05-06
download the pc image (iso) for your archetecture (32/64) then burn as an iso image disk at a slow speed (4x is good) Now you have a live disk to experiment with and know if everything is working for you.......or you can order 7.04 disks from SHIPIT, although that takes a few weeks, but it is free...

---

### Post by belair14486 on 2007-05-06
So Cappy u think id be better using Wubi for now till i learn more bout linux? im ok with working partitons etc. but can u guys recommend a size for the partiton or should i just split my HDD in half half for windows an half for linux? or just partition 1 part for Windows OS and 1part for Linux an the extra as an overflow for software? cause if i went with the last option then would definetly need sizes. Actually sailor made me think of something there i have a 64bit cpu but have a 32bit windowsOS could linux be run 64 or would it need to be the same as the windowsOS?

---

### Post by Cappy on 2007-05-06
If you decide to change your partitions around I would probably allocate 5GB + Whatever space you might be using for games on linux in the future. It's pretty easy to move something to another partition if you need to so don't worry too much about it. 
I would probably try Wubi in your situation. If for some reason it doesn't work, you can just try partitioning.

---

### Post by belair14486 on 2007-05-06
thanks cappy think ill probably start off with wubi to get my feel around linux/ubuntu to start with. from what iv seen and read about it am i right in thinking its similar to use as windows as an interface. to me it seems that way cant think why people say its harder to use.

---

### Post by Cappy on 2007-05-06
you can run 64-bit OR 32-bit. 64-bit is more difficult but if you use the program Automatix it will install all the stuff you need (flash, java, etc) in a few clicks. You can use 64-bit if you don't mind spending a little more time for a little more speed.

---

### Post by belair14486 on 2007-05-06
if i will give me more speed at the end of the day ill spend the time. is there certain place i should go to read about setting up a x64 version? btw iam really gratefull for you spending the time helping me here guys

---

### Post by Cappy on 2007-05-06
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by belair14486 on 2007-05-06
Thanks again Cappy for all the great info and help well looks like i got some reading to do so better go to it. well until next im off. if i get anymore problems or questions ill post em here. thanks again.

*Steve has left the building* cya guys.

---

### Post by belair14486 on 2007-05-06
ok back been reading that info gave to me before now i have 2 new questions.
Iv definetly decided on going with the x64 versions of ubuntu but what i cant figure out is what the diffrence is between Dapper, edgy or fiesty fawn? also this is probably really basic and iv missed the info about how,what,where why we have to use Repositories? Also just thought what is gnome?

as always any ifo would be greatly appreciated

---

### Post by stalkingwolf on 2007-05-06
> **belair14486 said:**
> ok back been reading that info gave to me before now i have 2 new questions.
Iv definetly decided on going with the x64 versions of ubuntu but what i cant figure out is what the diffrence is between Dapper, edgy or fiesty fawn? also this is probably really basic and iv missed the info about how,what,where why we have to use Repositories? Also just thought what is gnome?

as always any ifo would be greatly appreciated

as I recall, Dapper ver. 6.06, edgy ver 6.10 , and fiesty is 7.04 ( current ver.).  Make sure when you download
your version not to use the alternate cd, it doesnt have the LIVE part on it. it only installs. (my experience)

instead of searching all over the internet for programs and applications we want to install like winblows
we have repositories that have them all in one place.

Gnome is one of the "  popular desktop managers" .

In answer to one of your previous questions, No ubuntu does not install like winblows.  Ubuntu is much easier
and faster, about 20 - 40 min..  And usually when the install is finished your done.  In my experience ( which is limited.) about the only thing I need to do to be online and running is configure and activate my WIFI
(2-4 min.)

sorry for the simple answers but Im new also.
please feel free to correct me if Im wrong.

---

### Post by GSF1200S on 2007-05-07
> **Cappy said:**
> you can run 64-bit OR 32-bit. 64-bit is more difficult but if you use the program Automatix it will install all the stuff you need (flash, java, etc) in a few clicks. You can use 64-bit if you don't mind spending a little more time for a little more speed.

Ive actually thought about trying Gentoo in a 64 bit platform (in a virtual machine- lol im not that advanced with Linux yet).. Heres my question.. Doesnt a 64bit OS need 64 bit applications? If so, than im guessing you would be vastly limited with application support.

Hell, thinking about it, would it even be possible to run a 64 bit OS in a virtual machine?

---

### Post by seshomaru samma on 2007-05-07
> **belair14486 said:**
> ok back been reading that info gave to me before now i have 2 new questions.
Iv definetly decided on going with the x64 versions of ubuntu but what i cant figure out is what the diffrence is between Dapper, edgy or fiesty fawn? also this is probably really basic and iv missed the info about how,what,where why we have to use Repositories? Also just thought what is gnome?

as always any ifo would be greatly appreciated

I would not recommend using the 64 bit as your first installation , it's possible that many things will not work. 

Dapper is the stable version - I would recommend it
Feisty is the latest version - it might be a little buggy
forget about Edgy -there is no reason to use it as it is not stable nor recent.

about repositories read [this]("https://help.ubuntu.com/community/Repositories/Ubuntu")

gnome is a desktop manager , read [this comparison ]("http://www.psychocats.net/ubuntu/kdegnome")between the most popular managers :KDE and gnome . It will give you some idea.
[URL="http://www.psychocats.net/ubuntu/index.php"]
this[/URL] website has plenty of good info
and[ this]("http://monkeyblog.org/ubuntu/installing/") is useful as well

---

### Post by belair14486 on 2007-05-07
Thank very much seshomaru samma thats some good info you gave me. im still debating with myself about the 64bit thing but we'll see what happens. Its true not alot of software is written for 64bit processors, but alot of software can be run on 64bit which is meant for 32bit processors. On the other hand the lack of software at the moment makes me consider using a 32bit processor software.

---

### Post by Cappy on 2007-05-07
All software runs on 64-bit (32-bit runs when there is no 64-bit alternative). 32-bit Ubuntu is still easier because if you want to install a 32-bit program (manually) on 64-bit you may have to download some i386 (32-bit) files manually and move them to ubuntu's lib32 folder. Almost every open source application is already compiled for 64-bit though.
The rumor of "vastly limited with application support" is completely false now. That was true several years ago and it seems to have spread around.

You might as well go with 32-bit since it IS easier, like Seshomaru said.

---

