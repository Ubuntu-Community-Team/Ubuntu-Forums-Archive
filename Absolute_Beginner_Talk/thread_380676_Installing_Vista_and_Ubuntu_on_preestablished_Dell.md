---
title: "Installing Vista and Ubuntu on preestablished Dell"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Stevo0687 on 2007-03-09
Hey all,
   I've been working, mostly asking questions about installing Vista and Ubuntu on my Dell laptop that already has XP on it.  I want to keep XP and add the other 2 with a 4th shared partition for data.  
  My problem has been dealing with the Dell partitions that were already created and keeping XP.  Here is my last post, it got off topic of the title so I started a new post hoping to get more help.  [http://www.ubuntuforums.org/showthread.php?t=378012](http://www.ubuntuforums.org/showthread.php?t=378012)
Here is a little more background from an even earlier post if anyone cares.  [http://www.ubuntuforums.org/showthread.php?t=313899](http://www.ubuntuforums.org/showthread.php?t=313899)
  Well, I deleted the Fat 16 (utility with diagnostics for hardware) and the Fat 32 PC restore partition.  I didn't think either of these should affect my operation of XP.  Well, now XP will not boot.  I found this site: [http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm)  about the hidden partitions that I just deleted.  It even looks like I can get a copy of the utility if I want to replace it.  I'm just not sure why Windows won't boot now?  Can anyone help me.  If I absolutely have to I can reinstall XP and start over but I'd REALLY prefer not to.  For one thing, I don't have an XP install CD right now.  I can get one next week through school, but I'd rather not lose what I have on my current XP.  Its nothing I can't replace, it would just be a pain. 
  Please help me out.   I have not OS right now. lol I'm on the family computer right now.  Thanks in advance.

---

### Post by zubrug on 2007-03-09
install ubuntu in the appropriate partition and grub should find windows for you.

---

### Post by Stevo0687 on 2007-03-09
Alright, thank you.  Should I install Vista and do my other partitioning too and then install Ubuntu and hope it works?  

Also, when I deleted the other partitions it leaves me with unallocated space infront of the ntfs XP partions and some after.  I'm using Gparted.  I can't figure out how to combine them and make XP the first partition.  Thought I think its only 47 MiB, should I just leave it unallocated?  Thanks again.

---

### Post by Stevo0687 on 2007-03-09
Alright, I'm ignoring the 47 MiB for now. Correct me if I shouldn't.  I've created 20 GB for Vista and 40 for a shared ext3 partition for date.  That leaves me with 17 or so for Ubuntu, is that ok?  I want to do a /home partition, the main one, and a 2 GB swap.  How big to I make the home partition?  Will Ubuntu walk me through setting up these partitions when I install it or do I need to set them up in Gparted ahead of time?  Please let me know thanks.

---

### Post by zubrug on 2007-03-09
that is plenty, swap does not need to be that big, unless you have low ram
install will run gparted for you in the process
good luck

---

### Post by Stevo0687 on 2007-03-09
Well, I screwed up!! I thought I was renaming the partition and I erased everything!! I feel like an idiot. I guess I'll have to start all over.  Can I install Vista and Ubuntu now and XP later or should I wait until I get a copy of XP to install?  I'm sorry to everyone who was helping me work this out w/o starting all over.  I screwed this one up.  I have most of my files on DVD so its not that big of a deal, but I feel like an idiot.  Any sugguestions or comments would be great.  Thanks.

Zubrug, I guess I'll make my swap 1 GB?  I have 1 GB memory and I heard 2 times the memory size.  But I also heard that isn't always necessary.

---

### Post by Stevo0687 on 2007-03-09
Alright, one last post for the night.  Hopefully I can work most of this out tomorrow.  

I guess I'm looking for suggestions as to the best way to set all this up from scratch now.  I'd like to do it correctly, but I have no OS on my laptop now so the sooner the better. lol

I want to stick with XP, Vista, and Ubuntu. With a 4th partition of shared data and files. I don't want to go with just Vista because I believe there will be some bugs and compatibility issues.  Like I said, I can get XP (my school has an agreement with MS so I can get if for free) but I'll have to wait until Monday at the earliest.  

Any and all suggestions are very welcome.  I may even try to install Ubuntu tonight just for the heck of it and then start over again tomorrow.  But that way I can play around with it.  We'll see, its late.  Thanks in advance.  I hope to work this all out.  I'm guessing I'm not the first to do this. lol

---

### Post by Stevo0687 on 2007-03-10
Alright, I have Ubuntu 6.06.1 LTS running on my laptop here now.  Its running better than I expected.  I have internet, obviously.  Anyway.  I was wondering if I can set up the partitions in order on my hard drive?  Is that as good as installing them in order?  Can I set up the XP partition then Vista then the shared and then Ubuntu in that order on my hard drive but install Vista and Ubuntu today.  While typing this I talked to a buddy who didn't know how the Windows bootloaders would like Linux and seemed to think I have to wait until I have XP and Vista installed to install Ubuntu again.  Is that correct?  

Thanks in advance for your help.  I hope you can help me with these questions.  Thanks.

---

### Post by mac.ryan on 2007-03-10
Hi Stevo,

for the sake of the knowledge: the reason for which deleting the FAT16 didn't make you load XP anymore is that on the first partition of the HD there is the boot loader (like LILO or GRUB for linux). So, as somebody already pointed out to you, installing ubuntu (who installs GRUB as well) would have recovered for you the possibility to boot your XP.

The same principle is valid for the order of installation now (XP - VISTA - UBUNTU). I have no clue for Vista, but XP likes to be the only one on the machine, so it will **not** install a boot loader to keep ubuntu as an option.

As you already installed ubuntu, I see three options (to be tried progressively from one to three) here:[LIST=1]
[*]Installing XP and then Vista, hoping that Vista comes shipped with a boot loader. (XP will make ubuntu "invisible", but Vista might bring it back).
[*]Installing XP and then Vista, and trying to install GRUB again from the ubuntu LIVE CD. I have no direct experience in doing that but I think is feasible.
[*]Installing XP, then Vista, and then reinstalling ubuntu, that will reinstall GRUB too.[/LIST]As for the partition with data, you can make it whenever you wish, as it will not need to be in the boot loader, and it will be each OS to recognise it and mount it automatically.

My only recommendation - in order to keep the HD performant - is to make the data partition close to the partition where you will be installing the OS you will use the most to manipulate those data. (This way you will limit the time in which the HD will have to move its reading heads across the disk).

Best luck!

---

### Post by Stevo0687 on 2007-03-10
Thanks Mac.  Sounds like the best thing for me to do is run Ubuntu for now until I get a copy of XP and then clear the HD and start over by installing XP, then Vista, then Ubuntu.  I'm planning on making it on the harddrive in this order.

| XP ntfs | Vista ntfs | shard data ext 3 | Ubuntu (with /home and swap) ext 3 | 

That is the plan.  I really don't know which OS I will be using the most.  Hopefully, Vista and Ubuntu that is why I have it set up like that.  Is that what you mean by close to each other?  Does that sound good?

---

### Post by packeteer on 2007-03-10
WOW it appears nobody here has had ANY Vista experience!!!!  from a RC1 disk this OS will force you into complete rewriting of your drive partitions and not share ANYTHING!! 
But, there is, from microsoft (FREE!) a beautiful little tool called virtual PC. 

just load ANY operating system into this little jewel and walla mulitiple opearting systems inside vista !! 

I connect to wireless networks print to network printers and so on.

Vista also has a disk utility that lets you repartition you hard drives, shrink and expand partitions WHILE RUNNING VISTA!!! a cute little GUI drive editor taken right from the Open Source community!!

With limited hardware support because the OS is so new Vista is quite a challenge but it has grown on me quickly and recovered from what would have been complete reinstall crashes with EASE!!! (with the other OSes intact!!!)

Now I can install multiple Open Source OSes without all the typical headaches.

That said, take a shot at a Vista first install and add MS vitualPC then load all your OSes

---

### Post by Stevo0687 on 2007-03-10
Sounds like a good idea!  Anyone else have experience with this?  I might go for it.  Can I get Virtual PC online?  I know that is another program I can get from college.  Will this mean I boot to Vista everytime and then go from there and run XP or Ubuntu?  Or will this allow me to pick which to boot to?  Will I always be "running" Vista with the other OS's inside??  I like the idea of picking the OS from the boot.  How does this work.  I'd be willing to try it out, but a little more info ro comments would be nice.  Thanks very much.

---

### Post by packeteer on 2007-03-10
with this method You will always be working inside Vista, BUT adding vista to a third party bootloader makes it VERY ustable (you will hate Vista!!) the other OSes seem to like it though. 
Vista first is very stable but might not give you full functionality to all you hardware:( 

Somethings you will need to wiegh??  

I started with a brandy new Vista loaded laptop and had a steep learning curve.

Good luck!!:)

---

### Post by Stevo0687 on 2007-03-10
So install Vista and then Virtual PC?  And then Ubuntu and XP through Virtual PC?  Will I still be able to have a shared partition for data?

---

### Post by konungursvia on 2007-03-10
Well I would install Xp first, on only one partition, then add a second and third partition when installing the dual boot ubuntu. Oh, and screw Vista.

---

### Post by Stevo0687 on 2007-03-10
> **konungursvia said:**
> Well I would install Xp first, on only one partition, then add a second and third partition when installing the dual boot ubuntu. Oh, and screw Vista.

Nahh, I want to play around with Vista.  And I want to play around with Ubuntu. And I want XP for my stable OS that I'm used to.  But thanks.

---

### Post by Mr. Joe on 2007-03-10
> **packeteer said:**
> WOW it appears nobody here has had ANY Vista experience!!!!  from a RC1 disk this OS will force you into complete rewriting of your drive partitions and not share ANYTHING!! 
But, there is, from microsoft (FREE!) a beautiful little tool called virtual PC. 

just load ANY operating system into this little jewel and walla mulitiple opearting systems inside vista !! 



correct me if i'm wrong, but you mean using an operating system WHILE your running vista? so it would be like running it in a window?

if so (and keep in mind i'm just assuming thats correct, not that it is) then there are 2 problems that could happen:

1) a fatal problem with vista and you lose all your info on the other os's

2) if it acts like an emulator or something its going to run slower than if it just had its own partition. i'm imagining something like wine which is slower than a program running natively on windows. It all just seems really limiting =/

then again, idk for sure what you mean so I can of course be wrong ^_^

---

### Post by puccaso on 2007-03-10
mmm
my tv card doesnt work with vista
so i need kaffine to watch tv
and its too slow in vmware or vitual pc.


but i heard that if i install grub over the mbr, 
vista crashes??
because it needs to have control of everything

---

### Post by packeteer on 2007-03-10
you WILL have shared partitions, ALL of your partitions are accessible through all the virtualPC OSes, another little disk utility available in Vista along with full partition editing. Most people have NO CLUE about the Vista OS (as you've seen) and are OS eliteists, poopooing anything they aren't familiar with, YOU are the exception to the rule as am I. each new OS invites new challenges. KEEP it up you (and I) are a dieing breed.
try what you are used to first, do LOTS of research, keeping an open mind and try what YOU have decided sounds best!

I know I am going against the grain in this "ubuntu elites" thread but that is my nature, stirring things up gets lots of response.
Thanks for a GREAT question!!

---

### Post by packeteer on 2007-03-10
To answer Mr. Joe, VirtualPC creates virtual partitions within itself OR you can create a physical partition with Vista's partition manager, My XP runs faster on VirtualPC than on my old laptop!! might be the dual core processor.

I HAVE had my Vista build to an unbootable crash (me messing with the MBR) and all I had to do was boot with the OS install cd and it asks what the problem was, gave me 10+ options for recovery and rebooted within three minutes flwlessly with no effect on any OS loaded in VirtualPC!!  
 quite amazing for any MS build, seems they have learned alot from the Open Source community!

---

### Post by Stevo0687 on 2007-03-10
I'm kind of wondering what Mr. Joe said.  Will I be running the other OSs in a window?  Will it slow things up.  Since I'd be running the others inside Vista I'm not so keen on the idea.  What I'm thinking right now is that I'll try them with their own partitions first (the way I was planning) and see if it goes well.  If not I'm definately willing to try Virtual PC, I just don't know enough about it yet, I'll have to research more.

---

### Post by Mr. Joe on 2007-03-10
> **Stevo0687 said:**
> I'm kind of wondering what Mr. Joe said.  Will I be running the other OSs in a window?  Will it slow things up.  Since I'd be running the others inside Vista I'm not so keen on the idea.  What I'm thinking right now is that I'll try them with their own partitions first (the way I was planning) and see if it goes well.  If not I'm definately willing to try Virtual PC, I just don't know enough about it yet, I'll have to research more.

well can I just say that, since your hard drive is kinda wiped as it is and there really isnt any important info on it yet mess around with partitions and actually dual-boot (or triple booting lol) first to see if it works for you. you have a clean slate, see what works. I personaly would install ubuntu first (but then again i haven't used vista) but its your choice.


Whats the worst that could happen? it dosen't work and you reformat the hardrive and do a clean install of vista and do what that other guy said.

But if you do what he said FIRST and you wind up not liking it later you probably will have info on there that you won't want to get rid of, making it harder to just start from scratch.

so just take this opportunity to mess around when you have nothing importent to lose before you lock yourself in.

regards, 
Joe

---

### Post by mac.ryan on 2007-03-10
> **packeteer said:**
> stirring things up gets lots of response.

Yes, it is called [trolling]("http://en.wikipedia.org/wiki/Troll_%28internet%29").

---

### Post by mac.ryan on 2007-03-10
Hi Stevo,

as specified in my previous post, I am not a Vista user. However I was curious to check the issue about the impossibility to make a dual-boot installation.

Indeed it seems it is not impossible at all! :)
I found this article that has an how-to explanation:
[http://articles.techrepublic.com.com/5100-10877_11-6157570.html](http://articles.techrepublic.com.com/5100-10877_11-6157570.html)

The teaser of the article seems in line with what you want to do: "Are you really excited about the prospect of experimenting with the new features in the Windows Vista operating system, but are not yet ready to give up your existing Windows XP installation? Greg Shultz walks you step by step through the entire dual boot configuration procedure."
 
From what is written, it is a straight-forward procedure (just click on the "advanced" options when installing).

Have fun!

---

### Post by puccaso on 2007-03-10
OK
THIS IS HOW U INSTALL UBUNTU
ON PRE-INSTALLED VISTA SYSTEM.

you have to first re-size the drivers in vista - easyest option here.
so if ur harddrive is 200g, make ur vista 100g, (these figures are just examples)
now with the 100g u have left over:

when you install SELECT F6 - so that you go in expert mode.
more about this later:


now... 
MAKE A SEPERATE BOOT PARTITION... as apposed to ur home/root/swap.
select your BOOT parition to be bootable.


reference to f6::: 
there will come an option after you isntall base system about the GRUB 

rememebr pressing f6 before hand... this allows you to CHOOSE WHETHER TO INSTALL GRUB TO MBR OR NOT.
 YOU SELECT NO
 AND YOU TYPE IN THE YOUR BOOT PARTITION
 IN GRUB LANGUAGE 
 
 SO /dev/sda2 would be (hd0,1) etc.. (work that out for urself - it explains anyway)
 
now when you boot
you should see ur grub
with vista lodare
and i just did it
and it works :)

---

### Post by Stevo0687 on 2007-03-11
Thanks for the article Mac!!!! I read it and it sounds good.  I found another article on how to do all three and it had the user installing Ubuntu first.  I think I'll probably try it the way the article tells and then try to install Ubuntu afterwards. 

Puccaso, 
I don't understand your directions completely. I don't know if I should ask questions now or worry about that later.  Atleast it sounds like it'll work.  And like Mr. Joe said, I don't really have anything to lose.  Except that I as long as I'm switching around I can't save files and such that I want to keep, but I've got a 1 GB flash drive I can use for now I guess.

So I think I'll get XP one day this week and hopefully install the and then Vista.  I may even talk to my profesor (head of Computer Science department) for his suggestions.  I don't know how much he has messed with it yet though.  Thanks for the advice all.  Hopefully it will go well.  I'll definatly be checking back in soon enough.  Especially when I go to install Ubuntu.  Thanks again all.

---

### Post by Stevo0687 on 2007-03-11
Well, I was just fooling around this evening and installed Vista w/o activating it online so that I can reinstall it again.  It looks pretty cool but I didn't do a lot with it.  BUT I then installed Ubuntu.  Ubuntu worked fine, but I could no longer access Vista.  I went into GParted and switched Vista to the boot drive and still it loaded to Ubuntu.  I hit escape at the loading and went into Grub and saw some info on Ubuntu, but nothing about Vista.

Like I said, I was just fooling around.  I didn't follow any directions online so I could've done plenty wrong.  I should get XP tomorrow and I'll try to install all 3 this week following directions posted online.  Just thought I'd post my results from just fooling around.  Hopefully when I follow the directions that others have suggested, it will go better. lol  It was an experience though.

---

### Post by Stevo0687 on 2007-03-13
Well, I've got XP and Vista dual-booting so far.  And it seems to be going great.  We'll see what issues I have as I explore more, but so far I LOVE Vista!  Though that may be partly because I have XP Professional now instad of Media Center.  Its just not the same.  But Vista looks awesome.  Hopefully I'll be able to tackle adding Ubuntu tomorrow.  I talked to a guy in my networking class at school and he said he had done a triple boot with Linux, XP, and Vista.  It wasn't with Ubuntu, but I think it should work alright.  I guess we'll see.  So far so good...

---

### Post by mac.ryan on 2007-03-13
I hope you will love ubuntu at least as much as vista! ;)

Out of any joke, I hope you will dedicate time to explore ubuntu too... It is probably less user friendly and eye-candy than vista, but - for the very core feature of being free, and therefore requiring you to use your freedom in choosing how to tweak and configure your system - it gives much more satisfactions... or at least this is my experience! ;)

Good luck!

---

### Post by Stevo0687 on 2007-03-13
Yes, you are correct.  It isn't as user friendly and doesn't look as nice, Vista looks awesome! lol  But I still want to try Ubuntu. (Though I'm thinking about dropping XP, because I don't like the Professional like I liked my Media Center Edition and I haven't had any problems with Vista...yet) I like to challenge myself and so I'd like to explore Ubuntu and learn more about it.  I don't think I've mentioned it, but I'm a Computer Science major at York College of Pennsylvania, so it would benefit me to know how to use Ubuntu, just in that it teaches a lot more than the user friendly Windows does, I believe(obviously, I'm a very new C.S. student, a freshman, I don't know a ton yet, but I'm learning fast).  So I definitely still want to try it.  And like you said, its free and I'm beginning to love freeware more and more!   I also lost Powerpoint and Excel which I need for college and don't want to buy so hope to use Open Office instead.  

Thanks for the encouragement Mac.  I hope to attempt to install Ubuntu this week sometime.  I don't want to wait too long and have Vista established and all my files and then mess something up in the install.  I was up until 2:00 am last night so I don't think I'll install Ubuntu tonight but hopefully some day this week or over the weekend at the latest.

---

