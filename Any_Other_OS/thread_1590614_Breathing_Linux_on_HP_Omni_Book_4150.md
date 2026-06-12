---
title: "Breathing Linux on HP Omni Book 4150"
date: 2010-10-08
forum: Any Other OS
---

### Post by amjjawad on 2010-10-08
Hi guys,

One of my relatives has a very old HP laptop. It's PII with 64MB RAM and not sure what's the capacity of the HDD. They installed Windows XP SP2 on it (which I disagree with them about that choice because the laptop needs 5-7 mins to boot up with XP) and I was wondering if there's a very light version of Linux that can be installed on it?

I have Slax, Linux Mint LXDE, Fedora LXDE and  Xubuntu. I guess (not sure) I have Win98 or WinMe but I don't want to install Windows, I want Linux.

What do you recommend? I tried Fedora LXDE and Xubuntu but didn't try Mint and Slax yet.

Any idea? :)

Thanks!

_**Edit**_:
[COLOR=Red]*To skip the whole thread and read the final result and how did I fix it, please click*[/COLOR] [here]("http://ubuntuforums.org/showpost.php?p=10183383&postcount=105") and [here]("http://ubuntuforums.org/showpost.php?p=10199668&postcount=108")

---

### Post by sikander3786 on 2010-10-08
Damn Small Linux or Puppy Linux or someother but definitely not Ubuntu.

It won't be able to run any variant/derivative of Ubuntu with 64 MB RAM. Not even the minimal or text only version.

---

### Post by Scunizi on 2010-10-08
xubuntu maybe.. lubuntu which is lxde better, crunchbang is a possible.. but you really don't have much ram so you might have to look at DSL (damn small linux)... or just turn it into a server and live on the cli.. mutt for email. elinks for web browsing, file server, web server etc.... explore :)

---

### Post by TNT1 on 2010-10-08
I have an old dell, PII, 64MB ram, I run antiX on it quite successfully. Try puppy as well. or dsl.

---

### Post by Khakilang on 2010-10-08
I have try Lubuntu and Xubuntu and both of them works great and fast. I came across a few light weight Distro like Tiny Core, Puppy Linux,  SliTaz and Damn Small Linux. Maybe you can look into them as well. But I will go for Xubuntu.

---

### Post by sikander3786 on 2010-10-08
> But I will go for Xubuntu.

From the Xubuntu homepage,

> You need 192 MB RAM to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 192 (or even just 128 ) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by Khakilang on 2010-10-08
> **sikander3786 said:**
> From the Xubuntu homepage,

Now I remember I got 384MB RAM on my Pentium 3 computer and overlook his computer spec. Sorry! Than I guess Tiny Core linux is the answer.

---

### Post by nerdopolis on 2010-10-08
How about Lubuntu? [http://lubuntu.net/](http://lubuntu.net/)

you might be a bit cramped as far as RAM goes, [http://lubuntu.net/tags/requirements](http://lubuntu.net/tags/requirements)

---

### Post by amjjawad on 2010-10-08
Thanks guys :)
So, most of you recommended Puppy and DSL. I see, I tried DSL but I didn't like it much.

Any one has tried Slax or Fedora LXDE before? or maybe any other light OS?

The laptop currently has WinXP and I know that XP needs 128MB RAM as minimum but it works with 64MB RAM.

I need to know if someone has tried any light OS him/her self :)

Thanks again ;)

---

### Post by Dragonbite on 2010-10-08
[[COLOR="Blue"]_TinyMe_[/COLOR]]("http://tinymelinux.com/doku.php")? Or [[COLOR="Blue"]_ArchBang_[/COLOR]]("http://distrowatch.com/table.php?distribution=archbang")?

---

### Post by Sporkman on 2010-10-08
People need to stop recommending Damn Small Linux - that distribution hasn't had a release in 2 years...

---

### Post by TNT1 on 2010-10-08
> **amjjawad said:**
> 

I need to know if someone has tried any light OS him/her self :)

  

antiX dude! Try it...

I am running it on a PII Dell Latitude with 64MB RAM. I put a bigger HD in, and gave it 10GB swap, but even without any swap it ran fine.

And anticapitalista and the guys on the antiX forum will gladly assist in getting you set up...

---

### Post by Dragonbite on 2010-10-08
I used DSL, TinyMe and Suse 9.1 on a Pentium I (w/MMX) laptop running at 133MHz and with 64 MB of Ram.

DSL was the most responsive, but as mentioned it hasn't been developed in some time.

Suse 9.1 worked, but was very, very slow.  Not so slow it was unusable, but slow enough.

TinyMe was probably my best experience with it. It uses Opera for browsing AND email, and was overall not too bad speed-wise.

---

### Post by amjjawad on 2010-10-08
> **TNT1 said:**
> antiX dude! Try it...

I am running it on a PII Dell Latitude with 64MB RAM. I put a bigger HD in, and gave it 10GB swap, but even without any swap it ran fine.

And anticapitalista and the guys on the antiX forum will gladly assist in getting you set up...

Ok, if you have tried it, then I'll add this to my list :)
If it's lighter than XP then it will work for that laptop for sure.
Still not sure about the HDD's capacity for that laptop but I assume it's bigger than 2GB.

---

### Post by amjjawad on 2010-10-08
> **Dragonbite said:**
> I used DSL, TinyMe and Suse 9.1 on a Pentium I (w/MMX) laptop running at 133MHz and with 64 MB of Ram.

DSL was the most responsive, but as mentioned it hasn't been developed in some time.

Suse 9.1 worked, but was very, very slow.  Not so slow it was unusable, but slow enough.

TinyMe was probably my best experience with it. It uses Opera for browsing AND email, and was overall not too bad speed-wise.

I'm happy to know that PI is still alive :)

Hmmm, is TinyMe like DSL or it's different? honestly, I didn't like the interface of DSL :(

---

### Post by Dragonbite on 2010-10-08
> **amjjawad said:**
> I'm happy to know that PI is still alive :)

Hmmm, is TinyMe like DSL or it's different? honestly, I didn't like the interface of DSL :(

TinyMe uses Openbox but the way the PCLinuxOS guys make TinyMe, it looks more like an early version of LXDE.

Mind you, this a quite a while ago I tried these so things may have changed since then.

Also, sometimes it is better to go with an older version of the OS as it will have been developed using older (closer to the PII's) technology and systems with low specs.  I think I almost got the PI working with Ubuntu 5.?? or 4.??, but the graphics didn't work very well (and this was before desktop effects)

---

### Post by ubunterooster on 2010-10-08
> **Sporkman said:**
> People need to stop recommending Damn Small Linux - that distribution hasn't had a release in 2 years...
This is true

Puppy is nice, I might end up using it on my new 3.62 GHz hexacore for real speed. I did that on one of my old desktops for a while and it worked fine

---

### Post by amjjawad on 2010-10-08
I don't mind to use an old version/release of any OS, guys :)
All what I really want to know is what's the best OS that will run smoothly (or maybe I should use not TOO slow) on an old laptop with 64MB RAM and PII CPU :)

After all, that laptop is not mine but I feel bad when I see a laptop or a PC abandoned :D
It's better to use it than through it. At least, for checking emails, browsing, listening to Music, etc.

Hmmm, I'm worry about two things:
1- Sound Card might not be recognized by one of the OS's you guys recommended.
2- Same goes for the Wireless Card. I even forgot what's the name of that card. PCM ...somehting :(

---

### Post by Dragonbite on 2010-10-08
I ended up my PI with installing Ubuntu Server on it and running as a web server. Haven't used it in a long time, should dust it off and take a look at it again... :popcorn:

---

### Post by Dustin2128 on 2010-10-08
SliTaz- it's just as light as DSL, but it is actually in development. Uses openbox for the DE.

---

### Post by ubunterooster on 2010-10-08
I've had problems with Slitaz and my Atheros wireless card but the speed is nice

---

### Post by amjjawad on 2010-10-09
Thank you everyone, looks like I got a nice list of Operating Systems. Let's hope my relative will be convinced and give me his very old laptop :P

---

### Post by soldier1st on 2010-10-19
well there won't be many linux alternatives that will run on that ammount of ram decently, DSL and puppy linux and lubuntu are very lightweight but don't even think of putting xp back on it as it will be slow as you have seen so MS oses are out of the question but couldn't you upgrade the ram?ram is cheap and it works but if you can't you of course do have a few options.

---

### Post by amjjawad on 2010-10-19
> **soldier1st said:**
> but couldn't you upgrade the ram?ram is cheap and it works but if you can't you of course do have a few options.

The laptop is not mine, it's for my relatives and I was thinking to take it from them and use it but now, I guess it doesn't worth it. I don't have time to spend on that *super fast* laptop :D

---

### Post by sikander3786 on 2010-10-19
> I don't have time to spend on that super fast laptop

Now you'll have to free up some of your time for that as we did give your thread a bit of our precious time. :lolflag:

Not fair if you've started thinking the other way....

---

### Post by amjjawad on 2010-10-19
> **sikander3786 said:**
> Now you'll have to free up some of your time for that as we did give your thread a bit of our precious time. :lolflag:

Not fair if you've started thinking the other way....

Sir yes sir :D
LOL :D

P.S.
No worries, I might ask them tomorrow and hopefully they'll give it to me :)

---

### Post by amjjawad on 2010-10-19
Oh, by the way, antiX has two kernels (686 and 486 kernel).
Which one is the best for PII ???

---

### Post by Yavatar on 2010-10-19
I am just wondering how an ubuntu based installation would run on something below 1ghz. I have an old thinkpad A21m running W2K. It is about 800mhz and is maxed out out at 512mb RAM. I use less than 200mb at startup turning off the majority of the services and using Avira Antivirus.

It runs fairly well especially since it has dedicated ATi Rage graphics chip although it struggles with the higher-def youtube videos and intensive flash sites. The wife uses it but I maintain it. ;) I know ubuntu is a little more efficient but on the flip side it seems oriented to more recent machines.

I'm thinking Mint XFCE might be a good choice but I was thinking of letting her try out Edbuntu (she's a preschool teacher) IF it would run reasonably well. Some people say Ub runs fine with 512mb on older machines. I'd rather not be playing with different distros as it IS the wife's notebook and she gets cranky if she can't use it. ;) Plus there is only about a 9-10gb hard drive.

I figure I could probably get XP on there with only a little more memory use since there be more native support and less reliance on 3rd party programs (such as the wireless). (I recently fresh-installed on an older Inspiron and I was sitting about 256mb with Avast on it after all the updates including drivers.) I just don't want to waste the license I have to try it out. ;)


If it was just a spare system it wouldn't be a big deal but wife will probably clobber me with the Thinkpad (and the laptop would probably win, those things are fairly solid) if I screw up the system.


Yav

---

### Post by Yavatar on 2010-10-20
Reading and reading and reading ... I think I might give Lubuntu with LXDE a shot. The thing that is bugging me right now with Mint is their websites are horribly slow right now for whatever reason.

---

### Post by Yavatar on 2010-10-20
Interestingly as I was looking about for info about running it on an old Thinkpad A21m (800mhz, 512mb RAM maxed), I came across a link to psychocats Ubuntu Linux Resources which had a link to a Linux 'Quiz' at: [http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)  . I tried answering it like it was my wife doing the quiz and the top  suggestion, which surprised me, was openSUSE which I had not seen  previously mentioned. Anybody have any experience with Suse?


After doing quite a bit of reading Lubuntu seems like a nice choice just edging out Linux Mint with Xfce, even if its not 'official' yet... but, hey, it's Linux. Anybody with a beat-up pickup and a rusty pair of pliers can do whatever they want and just maybe he's got the next great distro. ;)

---

### Post by amjjawad on 2010-10-20
> **Yavatar said:**
> Anybody have any experience with Suse?


Yes, I guess it's mentioned on my first post :)
When I installed it, it could not detect my Wireless Adapter so I removed it.
I know what you'll say but connecting to the internet via LAN is not possible at the moment for some reasons I prefer to not discuss it here :)

You know? the best place to read more about Distribution is: [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by anticapitalista on 2010-10-20
For PII use the 686 version. (the 486 version will also work ok)

---

### Post by Yavatar on 2010-10-20
> **amjjawad said:**
> Yes, I guess it's mentioned on my first post :)
When I installed it, it could not detect my Wireless Adapter so I removed it.
[/]("http://distrowatch.com/")

Forgot that. Was looking at a number of posts and a number of pages and Suse didn't catch my eye originally. ;) Just out of curiousity, do you think it was just Suse itself wasn't quite suited for it or was it lack of RAM as I've seen a number of discussions on that topic?

Obviously if you modify the default install packages you can get some of these flavors to work on the older rigs, but at this point I'm looking for more of something out of the box so to speak. (I suppose if I had a CD shipped to me then it would be out of the box?)

And just for kicks, what's the bottom end anyone has pushed it to? Maybe not particularly useful at that point, but just out of pure morbid curiosity? =)

Will let you all know how it goes when I get a chance to get Lubuntu on the Thinkpad.

Yav

---

### Post by amjjawad on 2010-10-21
Ok, I have good news and bad news :)

Good news is: I got that latptop. Its name is OMNIBOOK 4150.
Bad news is: the CD-Drive doesn't work.

I'm not sure if one of the distributions you guys mentioned can be installed form a live USB or not but for example, antiX doesn't seem to be installed from Live USB. Didn't check the other distributions yet.

I still can't understand how come it works while XP is installed :) I thought it would take ages for a right-click to take effect but it's really impressive. It's not that slow :)

---

### Post by Dragonbite on 2010-10-21
> **amjjawad said:**
> Ok, I have good news and bad news :)

Good news is: I got that latptop. Its name is OMNIBOOK 4150.
Bad news is: the CD-Drive doesn't work.

I'm not sure if one of the distributions you guys mentioned can be installed form a live USB or not but for example, antiX doesn't seem to be installed from Live USB. Didn't check the other distributions yet.

I still can't understand how come it works while XP is installed :) I thought it would take ages for a right-click to take effect but it's really impressive. It's not that slow :)

Most ISO files can be placed on a USB either by using something like UNetBootin, or teh dd command. When using the dd command, make DARN SURE you point it to the right device!  It can cause irrepriable damage to your system! ```
dd if=/path/to/linux.iso of=/dev/sdb bs=4M;sync

```(the last part is optional).  You may want to format the usb stick and make sure it is set to be bootable first.

---

### Post by Yavatar on 2010-10-21
> **amjjawad said:**
> Ok, I have good news and bad news :)

Good news is: I got that latptop. Its name is OMNIBOOK 4150.
Bad news is: the CD-Drive doesn't work.

I looked up your notebook. Probably about the same age as my wife's Thinkpad A21m. I saw the Omnibook was a business notebook which was a good sign since they typically use 'modules' which you can swap out. Just go on eBay and search "Omnibook 4150 CD (or CD-ROM)" and you should be able to pick up a replacement relatively cheap. All you have to do is power down, pop out the old one and swap in the new one and you are all set. No worries about trying to boot off a USB stick.

Its really nice and you don't have to worry unscrewing anything. I replaced the CD-ROM on the Thinkpad for about $10 if that (depends if you want used or new... new may run a little more). Don't be surprised if multiple models are listed for the CD-ROM compatibility. Usually there a few series models that use the same parts.

Here's the manual for your notebook: [http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf)

You want pages 62 onward (64 shows how to pop it out).

Hope that helps,

Yav

---

### Post by amjjawad on 2010-10-21
> **Dragonbite said:**
> Most ISO files can be placed on a USB either by using something like UNetBootin, or teh dd command. 


Does  **System > Administration > Startup Disk Creator** apply to all other distribution too? because I didn't find anything mentioned about Live USB in their websites just like antiX. If yes, then that would be really great. I could create LiveUSB and use it to boot up the new system.

> 
When using the dd command, make DARN SURE you point it to the right device!  It can cause irrepriable damage to your system! ```
dd if=/path/to/linux.iso of=/dev/sdb bs=4M;sync

```(the last part is optional).  You may want to format the usb stick and make sure it is set to be bootable first.
I'm still so beginner about CLI so I won't do it for now :)
As long as there's GUI applications, I'd use it for now.


Thanks a lot :)

---

### Post by amjjawad on 2010-10-21
> **Yavatar said:**
> I looked up your notebook. Probably about the same age as my wife's Thinkpad A21m. I saw the Omnibook was a business notebook which was a good sign since they typically use 'modules' which you can swap out. Just go on eBay and search "Omnibook 4150 CD (or CD-ROM)" and you should be able to pick up a replacement relatively cheap. All you have to do is power down, pop out the old one and swap in the new one and you are all set. No worries about trying to boot off a USB stick.

Its really nice and you don't have to worry unscrewing anything. I replaced the CD-ROM on the Thinkpad for about $10 if that (depends if you want used or new... new may run a little more). Don't be surprised if multiple models are listed for the CD-ROM compatibility. Usually there a few series models that use the same parts.

Here's the manual for your notebook: [http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf)

You want pages 62 onward (64 shows how to pop it out).

Hope that helps,

Yav


Thanks a lot, Yav :) that's so nice of you.

Truth is, it's not my laptop so I won't even bother to buy anything for it :)
The real reason behind starting this thread is:
[B]To know which Linux Distribution that could work on 64MB of RAM.
[/B]Why I want to use that laptop? because sometimes I really miss using old slow machines :)

By the way, I did some search today and I came to know that most LXDE Distributions need minimum 128MB of RAM. I remember you started a thread asking about which OS is most suitable for 512MB of RAM.

---

### Post by anticapitalista on 2010-10-21
antiX has a simple antiX2usb script that you can use in the antiX control centre under Disks.
However, it is likely that you have usb1.1 ports so booting and installing will be slow. (if it works)

---

### Post by Yavatar on 2010-10-21
[]("http://ubuntuforums.org/member.php?u=941822")Actually, I was more concerned about the processor. I think 512mb would  actually be fairly decent for ubuntu. Of course if you start loading up  things it is going to run out. But considering a lot of people have a  decent processor but not the memory the laptop is doing pretty good in  that area.

Unless you are just crunched for money, $10 for a replacement CD-ROM is  not a bad amount at all to save a lot of headaches. That's what, a  couple of Happy Meals you go without? Hey, there we go. We'll include  ubnuntu CDs with McDonald's desktop themes and games with purchase of a  Happy Meal... ;)

Actually last night I was trying to find out a way to boot off a floppy and load USB driver (kind of like booting a DOS disk and MSCDEX). Oddly enough, it's actually more difficult to do this on Linux apparently. The only thing I found last night was mention of using a boot floppy disk image from Puppy Linux from a post 3 years ago. The link is incorrect, but if you just yank out the filename, the directory structure is still good and you see the file.

---

### Post by amjjawad on 2010-10-23
> **anticapitalista said:**
> antiX has a simple antiX2usb script that you can use **in the antiX control centre under Disks**.
However, it is likely that you have usb1.1 ports so booting and installing will be slow. (if it works)

I didn't install it yet and I can't install it unless I create a LiveUSB because the CD-Drive doesn't work :)

---

### Post by amjjawad on 2010-10-23
**In Summary:** for those who posted here and for anyone who will read this ... I did some search the other day and I came to know that most common LXDE Distribution needs _**minimum**_ 128MB of RAM. Xfce require a little more if I'm not wrong.

So far, we have:

[B]DSL
antiX
Slitaz
Slax [/B](no one recommended yet - not sure why?)
**Archbang**
crunchbanglinux
Puppy
TinyMe
TinyCore

Hope  I didn't miss anything from the whole thread.

The above Distributions in bold, I have them all. I just need to create a LiveUSB so I need to search if that's possible. I guess it's possible even though it doesn't mention in their websites (most of them).

I guess there are more very light OS's that works with 64MB RAM.
Don't forget that Laptop has XP already and it's not very much slow but yeah, with Linux, it should be faster, I suppose.

So, that's the summary of all this thread :)

P.S.
[URL="http://distrowatch.com/search.php?category=Old+Computers"]Linux Distributions for Old Computers
[/URL]Honestly, I didn't noticed that in DistroWatch. It's such a great website indeed.
I was just wondering (yet again :D) if someone has used one of these Distribution mentioned in the above link beside what we already discussed here.
That list sounds promising but as usual I need to know if someone has tried it him/her self :)

---

### Post by amjjawad on 2010-10-23
Well, after all, this old laptop doesn't have an option to boot from USB :(
I tried my best but it doesn't even exist.
As mentioned before, the CD-Drive is dead so can't even boot from there.
Not to mention it has no LAN adapter.

Thanks everyone for everything and I'm sorry for wasting your time.
I think someone else might find some useful stuff here.

**I think this thread is suitable for those who have 64MB RAM and 128MB RAM.**

---

### Post by sikander3786 on 2010-10-23
You might find something interesting here.

[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

---

### Post by amjjawad on 2010-10-25
> **sikander3786 said:**
> You might find something interesting here.

[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

WOW, seriously, there's nothing impossible in this world :)
Thanks a lot :)

However, there's a bit of a problem (don't hate me guys :P). That laptop has no Floppy Drive and as mentioned before, the CD-Drive is not working. Having that said, the only option to install that program and boot from is the HDD. I'm planning to wipe the HDD and install Linux. In that case, I'm afraid that program will work no more.

---

### Post by amjjawad on 2010-10-25
By the way, anyone heard about this:
[http://www.thinkgos.com/gos/download.html](http://www.thinkgos.com/gos/download.html)

Looks very nice indeed and it requires almost the same system specifications that laptop has.

In general, it's light and looks nice.
Was wondering if someone heard about it or tried it?!

---

### Post by Dragonbite on 2010-10-25
> **amjjawad said:**
> By the way, anyone heard about this:
[http://www.thinkgos.com/gos/download.html](http://www.thinkgos.com/gos/download.html)

Looks very nice indeed and it requires almost the same system specifications that laptop has.

In general, it's light and looks nice.
Was wondering if someone heard about it or tried it?!

Is that even still being developed?

---

### Post by Moozillaaa on 2010-10-26
> **sikander3786 said:**
> Damn Small Linux or Puppy Linux or someother but definitely not Ubuntu.

It won't be able to run any variant/derivative of Ubuntu with 64 MB RAM. Not even the minimal or text only version.


You mean there's a machine that will run Windows, and won't run Ubuntu?

I venture that that is wrong...

---

### Post by amjjawad on 2010-10-26
> **Dragonbite said:**
> Is that even still being developed?

> Since our debut in 2007, gOS has been praised for  being the most beautiful and easiest to use Linux operating system on  the market. Now with our third and best version of gOS, we have carried  on our effort to create a Linux for the rest of us.

[http://www.thinkgos.com/gos/index.html](http://www.thinkgos.com/gos/index.html)

I guess it's not.

---

### Post by amjjawad on 2010-10-26
> **Moozillaaa said:**
> You mean there's a machine that will run Windows, and won't run Ubuntu?

I venture that that is wrong...

He was talking about "Ubuntu" not ALL Linux Distributions.
The lightest version of Ubuntu is Lubuntu and it needs minimum 128MB or 192MB, can't remember correctly. :)

---

### Post by amjjawad on 2010-10-28
> **Dragonbite said:**
> Is that even still being developed?

You know what? I tried to install gOS (I tried it from the LiveCD and it was good) and it got stuck on step 4 - Partitioning Step. I posted on their forum. First of all, the forum is not official and second thing is no one replied yet.

It looks good but if it got stuck in the first few steps so I don't really need that hassle :)

Just thought to share this with you in case someone will try to install it so he/she would be aware of this issue. Some other users got the same issue by the way. It was mentioned on that forum.

[http://gosforums.org/](http://gosforums.org/)

---

### Post by m4tic on 2010-10-28
Man... Not even Android will run on this

---

### Post by amjjawad on 2010-10-28
> **m4tic said:**
> Man... Not even Android will run on this

Sorry, I'm afraid I didn't understand what you mean?

---

### Post by ubunterooster on 2010-10-28
Android OS uses more resources than a stripped down Lubuntu

---

### Post by amjjawad on 2010-10-28
> **ubunterooster said:**
> Android OS uses more resources than a stripped down Lubuntu
But it has nothing to do with gOS unless he forgot to QUOTE the right post :)

---

### Post by ubunterooster on 2010-10-28
> **amjjawad said:**
> But it has nothing to do with gOS unless he forgot to QUOTE the right post :)
Likely.

---

### Post by amjjawad on 2010-10-31
> **sikander3786 said:**
> You might find something interesting here.

[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

Hi again :)

Okay, neither I want to give up nor that very old laptop. I'm trying for the 20th times to boot the LiveCD of perhaps 10 Distributions until now but NONE is working. I installed Plop. The whole idea is amazing and I've never thought there's something like that. Now, problem is, I can't boot the LiveCD.

I got the list to choose which device to boot from. I choose USB, I got the first menu of UNetbootin and whatever choice I take, nothing happens after that, it got stuck or shows error message.

1- Is there something wrong with Plop?
2- Something wrong with UNetbootin? is there any better tool to create LiveUSB?
3- What's going on? I don't really know what's wrong?

I'm just concerned that the 64MB of RAM is not enough but the fact is, almost all the distributions I'm trying are built for 64MB of RAM. 
Now, I'm going to try one last time. If nothing will change, I think I'm wasting my time with this old laptop UNLESS someone has another suggestions.

I know this thread became so long but I don't want to give up that easily. Windows XP is working and everyone knows WinXP is so slow on 64MB of RAM so NO WAY Linux can't operate on the same machine.

Thank you!

---

### Post by amjjawad on 2010-10-31
That's all what I got. Either a white/light gray screen with password box which I have no idea what is that (I tried to enter guest, root, live ...nothing worked) or the other one with Kernel_Thread something.

I don't know what's wrong?!

---

### Post by Dragonbite on 2010-10-31
Could look up video options, that caused me problems with my PI (and I don't remember what I had to do, but I had to do it for every distribution).

What about Gentoo, has it been suggested? 

The downside is you do a lot more of things yourself, the good side is that when it is installed, it drops you into a working CLI installation.

Oh, and don't give up!  This will, if nothing else, be a great learning experience that a lot of people just don't get!

---

### Post by amjjawad on 2010-10-31
> **Dragonbite said:**
> Could look up video options, that caused me problems with my PI (and I don't remember what I had to do, but I had to do it for every distribution).

What about Gentoo, has it been suggested? 

The downside is you do a lot more of things yourself, the good side is that when it is installed, it drops you into a working CLI installation.

Oh, and don't give up!  This will, if nothing else, be a great learning experience that a lot of people just don't get!

Yes, I thought about the same (could be the Video Card) after I posted here but I was so tired so I took a nap.

Gentoo? hmmm, I don't think it's suitable for 64MB RAM. I tired many distributions:

antiX
Archbang
PapugLinux
gOS
Slitaz
Slax
And can't remember wha else.

I'm just concerned about UNetbootin, I just hope there's nothing wrong with it. By the way, is there a better software than UNetbootin?

"Never Give Up Nor Surrender" is my motto :)


Edit: [http://www.gentoo.org/doc/en/mips-requirements.xml](http://www.gentoo.org/doc/en/mips-requirements.xml)
I guess it might work with that Laptop :)

I'm just tired of downloading :)
My connection is very slow, 30kbps is the max download speed. 700MB takes 6-7hours. Yeah, I know, it's very slow.

---

### Post by sikander3786 on 2010-10-31
> I'm just concerned about UNetbootin, I just hope there's nothing wrong with it. By the way, is there a better software than UNetbootin?

Unetbootin always worked for me just fine. Still there are other options like pendrivelinux and universal USB creator. Many others also I believe. Google!

Plop should be able to boot the USB device. **IT SHOULD BOOT** ragardless of the over ageness of the laptop.

---

### Post by amjjawad on 2010-10-31
> **sikander3786 said:**
> Unetbootin always worked for me just fine. Still there are other options like pendrivelinux and universal USB creator. Many others also I believe. Google!

Plop should be able to boot the USB device. **IT SHOULD BOOT** ragardless of the over ageness of the laptop.

The best thing ever that I learned from here is **Plop**. It's such an amazing software.
I guess it did but I was just thinking loudly :) I'm trying to find out what could the real problem be?
Perhaps as Dragonbite said, it might be the graphics card.

Yes, I found some other tools but I wanted to know about your suggestions :)

So, any idea what's the next step?

---

### Post by sikander3786 on 2010-10-31
What exactly happens when you boot your USB device?

I have read all your previous posts but couldn't get to the exact problem :-)

What I understand is that PLOP lists your USB drive as a bootable device but after that nothing happens when you choose the boot options from Unetbootin interface and it returns you back to the Unetbooting default page?

Am I right?

Did you try adding some boot parameters to the kernel from Unetbootin by editing the entry?

---

### Post by amjjawad on 2010-10-31
> **sikander3786 said:**
> What exactly happens when you boot your USB device?

6 Post #**[[B]58**]("http://ubuntuforums.org/showpost.php?p=10052012&postcount=58")[/B]

> 
I have read all your previous posts but couldn't get to the exact problem :-)

1- I turned the laptop on
2- Got a small menu with 4 options to boot from (I guess): HDD, Floppy, CD and USB
3- When I choose to boot from USB, it started to boot from the USB Flash Drive/Pen Drive and I got UNetbootin menu (that's what the title of that menu said). Sometimes, that menu was totally blank (check post **[[B]58**]("http://ubuntuforums.org/showpost.php?p=10052012&postcount=58")) [/B]and when I press any key, I got **yS** (not sure what's that) and Password to enter. I don't think it has anything to do with that distribution (it happened with me with Slitaz or Slax, antiX and Archbang). Then, I got stuck with the password and can't move forward
4- With some other distribution, I got that black screen with lots of instructions or commands that I don't really understand. I attached the screen shots in post **[[B]58**]("http://ubuntuforums.org/showpost.php?p=10052012&postcount=58").
[/B]Same goes here, I got stuck and can't move forward.

> 
Did you try adding some boot parameters to the kernel from Unetbootin by editing the entry?
I'm afraid I don't know what are you talking about :(
I did nothing, I just created the LiveUSB.

---

### Post by amjjawad on 2010-11-01
ATI RAGE Mobility
P/M AGP 2x (A21/2) << that's what Windows XP shows in Settings.
Memory 4MB

That's the AGP Card that laptop has.
I'm trying Gentoo now. I downloaded the minimal iso file (111MB) and it took 1 hour and 15 mins to download it.

---

### Post by Dragonbite on 2010-11-01
> **amjjawad said:**
> ATI RAGE Mobility
P/M AGP 2x (A21/2) << that's what Windows XP shows in Settings.
Memory 4MB

That's the AGP Card that laptop has.
I'm trying Gentoo now. I downloaded the minimal iso file (111MB) and it took 1 hour and 15 mins to download it.

I was lucky, I got a Gentoo CD (downloaded at work), but for actually installing things I was stuck with dial-up.  Believe me, you do NOT want to download and install KDE over dial-up! ;)

---

### Post by amjjawad on 2010-11-01
> **Dragonbite said:**
> I was lucky, I got a Gentoo CD (downloaded at work), but for actually installing things I was stuck with dial-up.  Believe me, you do NOT want to download and install KDE over dial-up! ;)

Well, I'm stuck for many years now with 30KB/s which is killing me but thank God, at least I can connect to the Internet.

By the way, during the installation of Gentoo (I downloaded the minimal iso - 111MB), it asked me for a user name and password and yet again, I couldn't move forward. However, this time, it's different and not like the other password I was talking about previously (screen shots posted in post 58). I got lots of stuff (CLI no GUI) and then it stopped and said:
**(none) login**:
When I enter anything, it said **Password** and then I'm stuck. I got "incorrect password) and showed (none) login again up to 5 tries.

I don't know what's the password nor the user name. If it's asking about what username and password I want, then it should accept whatever I enter but that did not happen. I tried to search for that in Gentoo Installation Guide but found nothing.

I'm not giving up though :D

---

### Post by mips on 2010-11-01
[http://www.slitaz.org/en/artwork/screenshots.html](http://www.slitaz.org/en/artwork/screenshots.html)

---

### Post by amjjawad on 2010-11-01
> **mips said:**
> [http://www.slitaz.org/en/artwork/screenshots.html](http://www.slitaz.org/en/artwork/screenshots.html)

Hello mips,

Not sure if you read the whole thread or not but I've tried it already and it didn't work as explained previously.

Thanks anyway :)

---

### Post by sikander3786 on 2010-11-03
Hi. Sorry mate I am a bit late on this.

Were you able to find the Gentoo password?

Actually I have a whole new idea. Can you get a USB CD-ROM somewhere, boot your distro using PLOP and install?

---

### Post by amjjawad on 2010-11-03
> **sikander3786 said:**
> Hi. Sorry mate I am a bit late on this.

Hello mate,
Never mind, don't worry about it :)

> 
Were you able to find the Gentoo password?
 Not really. I didn't have much time to search for that. I searched the other day but found nothing.

 > 
Actually I have a whole new idea. Can you get a USB CD-ROM somewhere, boot your distro using PLOP and install?

LOL, I had the same idea since day 1 but would have used it if I have it :(
I don't want to buy new one, it's too much money for a very old laptop. I'll try to borrow one from a friend except I have no idea who has one? looks like it's time to update my status on facebook :P

I was about to use Lubuntu and create LiveUSB using UNetbootin but the minimum requirement for Lubuntu is 128MB and I don't think it will work as other distribution which require less RAM didn't work.

---

### Post by sikander3786 on 2010-11-03
There is also a SATA/IDE to USB switch if you could find it somewhere and use your existing CD-ROM to serve the purpose.

Regarding you previous posts about Unetbootin USB not able to boot, I have no idea. It asks for some passwords, doesn't show the options etc, I actually never encountered/heard about that. I feel like PLOP has something to do with those errors.

Boot parameters are explained here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by amjjawad on 2010-11-03
> **sikander3786 said:**
> There is also a SATA/IDE to USB switch if you could find it somewhere and use your existing CD-ROM to serve the purpose.

I need to travel to another city to find such stuff. There are very limited option in my city.
I guess I'll update my facebook status and ask my people if they have an USB CD-ROM :)

 > 
Regarding you previous posts about Unetbootin USB not able to boot, I have no idea. It asks for some passwords, doesn't show the options etc, I actually never encountered/heard about that. I feel like PLOP has something to do with those errors.
 
I suspect that too as I mentioned earlier. I have a password on UNetbootin and another during Gentoo Setup. Menu doesn't show any thing except yS as mentioned in post 58 and weird stuff.
Anyway, I won't give up, I'll do all what I can to give new life to that ancient laptop :)

> 
Boot parameters are explained here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Thanks for the link, mate :)
Although it's for Ubuntu but I'll read it for general knowledge :)

Tomorrow, I should be free and I might try one more time.

---

### Post by sikander3786 on 2010-11-03
> I need to travel to another city to find such stuff. There are very limited option in my city.

Where are you exactly? I think they should be available eveywhere :-)

---

### Post by amjjawad on 2010-11-03
> **sikander3786 said:**
> Where are you exactly? I think they should be available eveywhere :-)

Not here, believe me :)

---

### Post by amjjawad on 2010-11-04
Again, good news and bad news :)

Good news is, I finally found a Linux Distribution that potentially will work on that laptop. It's [Vector Linux Light]("http://vectorlinux.osuosl.org/docs/vl60/manuals/vl6_installation_guide_en.html#requirements")

Bad news is, after 10-15 mins of waiting, I got a black desktop with the main task bar but for some reason, once I right click on the desktop, the task bar will fade away and all what I got is the mouse pointer :(
Vector Linux Light was able to detect my VGA Card (ATI) and it gives me 5 options (I guess), one of them is to choose AUTO Configuration with Zero Question.
Now, I need to figure out how to avoid the totally black screen and how to install VL on that laptop.

I think the other distributions couldn't detect the VGA Card. None of the other previously mentioned distributions worked except for VL.

---

### Post by amjjawad on 2010-11-04
Guys, hope someone has more experience with VectorLinux and these stuff.
I found some topics but it's different from my case and doesn't make sense to me.

See the attached screen shot. Whatever I choose from this list except the last option, I got the desktop with a black background (after 5-10 mins). After few seconds, the screen goes to black and nothing happens except I can move the mouse. After 3-5 mins, I got the desktop with black background again. After 1-2 mins, same happened again. I can't get out from that loop.

With the last option, nothing happened, I just got black screen with the mouse course (black cross pointer) and it doesn't even move.

I checked the [installation guide]("http://vectorlinux.osuosl.org/docs/vl60/manuals/vl6_installation_guide_en.html#installation") but couldn't find something that could fix my issue.
I can't get to the text-mode installation whatsoever.
All what I got after many lines of executable commands (I don't need to do anything) is the attached screen shot.

I guess the best thing to do at this point is to test the RAM to make sure it's not faulty. I can't think about another solution at the moment.

---

### Post by sikander3786 on 2010-11-04
It will be better to check the RAM for defects as you already got to the point :-) I have no experience with Vector Linux so can't help there. Just bumping the thread as I am also interested to see you get that Laptop up and running.

Hope you get there.

---

### Post by amjjawad on 2010-11-04
> **sikander3786 said:**
> It will be better to check the RAM for defects as you already got to the point :-) I have no experience with Vector Linux so can't help there. Just bumping the thread as I am also interested to see you get that Laptop up and running.

Hope you get there.

I'm checking it now but I didn't know it takes forever :(
More than 3 hours now and it's still running the test. I wonder how long it will take if I'll run that test on my 2GB RAM?

Thank you my friend, never mind. I'm not giving up, I'm more interested to run Linux on that laptop. I'll do whatever it takes to do that :)

---

### Post by amjjawad on 2010-11-05
RAM test was running for 4.5 hours and no errors were found.

ALL what I managed to do so far is to get DSL booting up and working (didn't install it) but of course it couldn't detect my Wireless Card and that laptop has no LAN port.
Not to mention that I don't like DSL interface at all.

Yesterday, I tried to use the laptop while booting into Windows XP (it's already installed) but I ended up cursing Windows. I wasted lots of time just to do few things. I hate the guy who installed XP on that laptop. What was he thinking?

If I just could manage to get it up and running with Linux but it's getting harder especially with very limited options.
I don't think it will work even if I'll find an external CD-ROM.

Sorry guys, I know this became a very long story but I thought we could manage to get it up and running.
Not giving up completely but have no more options to try.

---

### Post by amjjawad on 2010-11-08
Okay, I'm so much frustrated because I've been (as you might know) searching and trying over and over again to get that laptop up and running with Linux instead of Windows XP SP2  but:
**Either** I'm doing something wrong
**Or **this laptop is really really very old and there's no hope with it
**Or** Linux DOES NOT work on such low hardware specifications

I took that as a challenge from day one but it became too much hassle for me as I'm spending many hours days and nights to get it up and running with no hope/light at the end of the tunnel.
The challenge became even more interested when I couldn't run the simplest distributions on that laptop. Another challenge has been added which is:
[B]Windows XP is up and running on that laptop so Linux MUST be up and running too.
[/B]Sad but true, it did not except for DSL and I'm telling you, I prefer to use XP rather than DSL.

The other thing that drove me crazy is the lack of OFFICIAL documentations for most of the distributions I've tried. The simplest information is not available. I downloaded 10 or even more based on some other articles which recommended that this distribution will work on RAM 64MB and stuff like that. This is not right IMHO. If they really want their projects to be well-known, they should spend more time on Documentation than building/developing Operating Systems. I've learned in University that documentation is very important.
How would you feel when you can't find the minimum requirements of the OS that you're trying to install? or you can't find the installation guide or whatever you're looking for?

So, it might be the end of this journey :(
This laptop has Windows XP and it's up and running BUT it can NOT be up and running using Linux.
They should STOP saying that this Distribution work on low hardware specifications. First, I thought I'm doing something wrong but when you try over 20 distributions and NONE of them is working, this left you with one idea that _**these distributions are not made for such low hardwares**_.

I wanted to beat XP and prove to myself and my friends that Linux is capable of that but ... too bad it couldn't :(

Again, DSL does not simply meet my needs nor expectations.
Oh and guess what? even puppy could not work. It got stuck in the first few steps.

NO, there's nothing wrong with the RAM nor the HDD. I checked both.
Again, XP is up and running except it's slow but it's up and running.

I really hope someone could prove me wrong.

That was anyhow a good experience and also good to know what OS one could use with such old machines.

Thank you!

Some references:
[http://www.goodbyemicrosoft.net/e107_plugins/links_page/links.php?cat.3](http://www.goodbyemicrosoft.net/e107_plugins/links_page/links.php?cat.3)
[http://en.kioskea.net/faq/8584-running-linux-on-small-configurations](http://en.kioskea.net/faq/8584-running-linux-on-small-configurations)

---

### Post by sikander3786 on 2010-11-08
Sad!

I can't figure out where you got it wrong :-) Some distro, at least any one of them should have worked. I am surprised DSL neither Puppy worked for you.

---

### Post by amjjawad on 2010-11-08
> **sikander3786 said:**
> Sad!

I can't figure out where you got it wrong :-) Some distro, at least any one of them should have worked. I am surprised DSL neither Puppy worked for you.


[LIST=1]
[*]Absolute Linux 
[*]Puppy 
[*]&#65279;&#65279;&#65279;&#65279;&#65279;ConnochaetOS 
[*]Debian 
[*]VectorLinux 
[*]Lubuntu 
[*]Xubuntu 
[*]SliTaz 
[*]Slax 
[*]LinuxMint LXDE 
[*]DSL 
[*]PCLinuxOS-ZEN-Mini 
[*]Papuglinux 
[*]Gentoo 
[*]gOS 
[*]Archbang 
[*]antiX
[/LIST]

I have tried all these or maybe more but can't remember what else?
I have tried more than 3-5 times with each distributions so you could tell how many times I've tired and how many hours I spent doing that.

I know some of the above listed distributions will never work (like Xubuntu) but I was just trying to compare between Windows XP and Linux. Apparently, XP has achieved what Linux can not. Sad but true.

DSL was the only OS that worked but without internet connection of course (couldn't detect my Wireless Adapter and that laptop has no LAN port). Beside, DSL is the last thing that I want to end up with. I prefer XP over DSL.

I've tried most of maybe ALL the distributions that you guys have recommended but NONE worked for me.

Thank you anyway :)

---

### Post by amjjawad on 2010-11-08
I know this post could upset those who LOVE Linux but Microsoft knows what they're talking about.

[http://support.microsoft.com/kb/314865](http://support.microsoft.com/kb/314865)

I was trying to prove otherwise but unfortunately, Windows XP beats Linux when it comes to very low RAM.

It's not XP vs Linux anymore, it's XP vs DSL. Sad but true.

I love a quote from a movie (Training Day) so I'm going to use it:

> It's not what you know, it's what you can prove


Please don't be offended, I don't mean anything bad, guys :) I appreciate the time and everything that you provided but I'm just sad that most of the listed distributions above (previous post) have very very very few documentations not to mention some have NONE. Yes, when I click on "Installation Guide" link for example, I got error message like this link has been removed, etc.

I still adore Ubuntu because everywhere I go, I find tons of documentations, guide, etc.
Imagine (for example) that one of the distributions (gOS) has NO official forum and when I posted on their forum, they replied "sorry, we can't answer your questions because we don't know".

The other thing I'm sad about is obviously Linux runs smoothly on most of the machines because these are modern and not +10 years old. On the other hand, Windows is up and running on old machines. 

By the way, I guess someone would say: You could take the HDD out, put it on another machine and install from there then get it back where you took it from. Well, that's not an option. Why would I do that while I could simply either keep the current OS (XP) or install Windows 98 for example?

Anyway, I'll keep looking because this has become way beyond a challenge of installing Linux on an old machine. It's become a challenge to prove whether Linux is made for old machines or not?
I'll keep digging until I could either prove Linux doesn't work on old machines (except for VERY few distributions) or it could work.

When I say old I mean OLD (64MB RAM or less).

Thank you guys :)
That's been very very interested project :)

---

### Post by Dragonbite on 2010-11-08
Is your issue with Gentoo still just the password?  And I can't remember if this system has an optical disk or not (CD-Rom).

I ran across this tutorial on installation, which doesn't have any password but does have some helpful information : [http://gentoo-install.com/install]("http://gentoo-install.com/install")
A lof of this you probably already know, but it doesn't hurt to read through and see if there is anything "missing" ;)  That's part of the journey *(can't tell you the number of times I have beat my head against the wall only to find out the documentation I've been finding and reading misses one command or one parameter that makes it work)*

Windows XP came out about 8 years ago so machines from just previous to that era were still "in the mainstream" and didn't even consider 3D acceleration and always-on networking and whiz-bang effects we take for granted today.  Maybe should look for old versions of Linux that would have been available at that time and work your way up!

I think on my old (PI) system I tried Ubuntu 4.10 and it ran, not really well but it ran.

Don't give up, it's the journey that is worth its weight! ;)

---

### Post by Dragonbite on 2010-11-08
Just ran across [Webconverger]("http://webconverger.org/"), which is a Web Kiosk distro.   Since it tries to do nothing else other than offer web access they may have tried trimming down it's requirements enough.

> Webconverger works with almost any standard x86 hardware that meets Firefox’s minimum requirements.

Since Firefox is no lightweight, this may still pose a problem.

---

### Post by amjjawad on 2010-11-08
> **Dragonbite said:**
> Is your issue with Gentoo still just the password?  

Yes, it's. I tried it again last night and got the same issue.

> 
And I can't remember if this system has an optical disk or not (CD-Rom).

It has but it's faulty and does not work (dead).

> 
I ran across this tutorial on installation, which doesn't have any password but does have some helpful information : [http://gentoo-install.com/install](http://gentoo-install.com/install)
A lof of this you probably already know, but it doesn't hurt to read through and see if there is anything "missing" ;)  That's part of the journey [I](can't tell you the number of times I have beat my head against the wall only to find out the documentation I've been finding and reading misses one command or one parameter that makes it work)
[/I]
I'll read it. I just read the first part and it seems not the right one for this machine (it's talking about 10GB HDD). However, I'll read it :)

> 
Windows XP came out about 8 years ago so machines from just previous to that era were still "in the mainstream" and didn't even consider 3D acceleration and always-on networking and whiz-bang effects we take for granted today.  **Maybe should look for old versions of Linux that would have been available at that time and work your way up!**

That's exactly what I was thinking about. I'm a bit disappointed that I couldn't install any Linux (except DSL) Distribution yet but I guess you're right, the old versions might work.

> 
I think on my old (PI) system I tried Ubuntu 4.10 and it ran, not really well but it ran.

I don't think Ubuntu 4.10 will work for that machine but I'll try older versions of other distributions.

> 
Don't give up, it's the journey that is worth its weight! ;)
Actually it's all your fault :D hahahaha. You're the one who's motivating me :)
I thought to quit for a while but that motivated me even more to carry on. I don't quit so easily :D

Thank you, buddy :)

---

### Post by amjjawad on 2010-11-08
> **Dragonbite said:**
> Just ran across [Webconverger]("http://webconverger.org/"), which is a Web Kiosk distro.   Since it tries to do nothing else other than offer web access they may have tried trimming down it's requirements enough.

Since Firefox is no lightweight, this may still pose a problem.

> 
[http://www.mozilla.com/en-US/firefox/system-requirements.html](http://www.mozilla.com/en-US/firefox/system-requirements.html)**Minimum Hardware**   
[LIST]
[*]Pentium 233 MHz (*Recommended:* Pentium 500 MHz or greater)
[*]64 MB RAM (*Recommended:* 128 MB RAM or greater)
[*]52 MB hard drive space
[/LIST]
I guess it's a problem :(
ALL the distributions I've tried which say the same about requirements, have never worked. Always stuck and couldn't even reach the point where I could see the desktop or the installation process.

---

### Post by amjjawad on 2010-11-18
> **Yavatar said:**
> Here's the manual for your notebook: [http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/bpi03931/bpi03931.pdf)

You want pages 62 onward (64 shows how to pop it out).

Hope that helps,

Yav

Yav, thanks a lot :) I thought I'll never need that manual but guess I was wrong. I was looking actually for page 79. 

I just bought a Mobile Hard Disk Enclosure (almost 5.5 USD - I thought I won't pay anything but that's impossible with the condition of that laptop - it's half dead). I'm going to do the FINAL try with that laptop. If it failed, then I don't want to try more.

---

### Post by amjjawad on 2010-11-18
By the way, I got a 2nd PC from a friend of mine (check my signature for PC-Specifications) and as usual, I installed 5 OS's, one of them is Slitaz.
It's really worth to mention that Slitaz is amazing :) out of all the other distributions I have tried, Slitaz take ONLY 47MB of the RAM after HD Installation and with nothing opened. It's really nice. I know DSL might take way less but I don't like DSL.

I just need sometime to spend with Slitaz and the best thing to do is trying to install Slitaz on the HD of that ancient laptop :D

---

### Post by sikander3786 on 2010-11-18
> I just need sometime to spend with Slitaz and the best thing to do is trying to install Slitaz on the HD of that ancient laptop

You found yet another one :-)

Good Luck once again.

---

### Post by amjjawad on 2010-11-18
I'm about to lose my mind :)
it seems that HD or that laptop is designed and made for one purpose which is NOT to work with Linux :(

I successfully installed Slitaz, Vector and Absolute Linux (can't remember what else) but I always get the same error message after rebooting:

** Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (8,1)**

CAPS and Scroll lock lights are flashing and can't do anything except hard reset.

I unplugged my main HDDs so that the external HDD (the laptop's HDD) would be sda but that did not help. I don't know what else shall I do? I traveled 150Km to buy that Mobile HD enclosure thought that would make me finally install Linux but ... nothing happened.

Oh yes, the best news is I formatted so there's nothing on that HD anymore :) what a lovely achievement!

---

### Post by amjjawad on 2010-11-19
> **amjjawad said:**
> I'm about to lose my mind :)
it seems that HD or that laptop is designed and made for one purpose which is NOT to work with Linux :(

I successfully installed Slitaz, Vector and Absolute Linux (can't remember what else) but I always get the same error message after rebooting:

** Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (8,1)**

CAPS and Scroll lock lights are flashing and can't do anything except hard reset.

I unplugged my main HDDs so that the external HDD (the laptop's HDD) would be sda but that did not help. I don't know what else shall I do? I traveled 150Km to buy that Mobile HD enclosure thought that would make me finally install Linux but ... nothing happened.

Oh yes, the best news is I formatted so there's nothing on that HD anymore :) what a lovely achievement!

I connected the HDD to my other PC. It's P4 with 512MB RAM. I have two PCs now, one is P4 with 2GB RAM (the one I used first to install Linux on the laptop's hard drive) and another one which is also P4 but 512MB RAM.

Just for the record and before I explain further, I'm using a Mobile Hard Disc Enclosure. It has USB cable with 3 ends, one to be plugged in the HDD's case and other two ends to be plugged in to the PC. It has no external power, that's why there are two USB sockets to be connected to the PC.
I'm using that because (as explained before) that laptop has NO optical devices, nothing to install Linux from except an USB port. I've tried for maybe 10 days to install via that USB port using Plop but as explained before too, I couldn't.
As suggested here and in other forum, it's better to take out the HDD from the laptop and connected to another PC and install from there.

I'm using GParted to format the HDD. I created only 2 Partitions, one is root (ext3) and the other is Swap. The total capacity of that HDD is 4.5GB. 520MB for SWAP and the remaining for the root which is almost 4GB.

During installation of any OS, I have NO PROBLEMS whatsoever. The problems start immediately after the first reboot when installation finished and I have to restart/reboot.

With my 1st PC, I got that **Kernel-Panic** error message with Command Line Interface (CLI). Today, after I tried to install from my 2nd PC, I got 

```
grub>

```

That's all.

As suggested, I tried to LABEL sda1 but now I have another kind of errors.

Yes, I unplugged ALL the internal HDDs in my first PC and now with the 2nd one as well. Yes, both PCs are able to boot from USB. Yes, I have tried before to Install Ubuntu to an USB-External HDD and it worked without any issues. Yes, I checked the HDD and it's error-free.

I'm ... okay, I'll keep trying but it doesn't make sense to try and more errors will come up. There must be something NOT right.

---

### Post by amjjawad on 2010-11-19
A) Ubuntu 10.04 was successfully installed on that ancient HDD and it was up and running. I did that to test and make sure the HDD is fine and it's fine. I had to rebooted 3-4 times though until Ubuntu became up and running.
Had to remove Ubuntu because it will never work on 64MB of RAM.

B) I finally managed to install antiX on that HDD while it's connected to my 2nd PC. I rebooted and got "Error 2" after "grub stage 1.5".
I gave up and didn't want to try more. I put the HDD back to the laptop and when I turned it on, I got this:

```
Warning: bootdevice may be renamed. Try root=/dev/hda1

*some instructions*

dev/sda1 does not exist.

/bin/sh: can't access tty: job control turned off
(initramfs)
```

Honestly, I can't try more. If someone knows how to fix that, I'll be very glad to follow his/her instructions, otherwise I can't do anything more than that. I mean, I can't install/format more than that. But, I'm open to a reasonable suggestions :)

I already posted on antiX's forum but it's not active as this one.

The whole thing was for fun but it's now a pain, a real pain :)

---

### Post by sikander3786 on 2010-11-19
> The whole thing was for fun but it's now a pain, a real pain 

I feel sorry. Your attempts didn't bear any fruit :-)

And I can't help you on antiX thing. That seems to go over my head :-)

Might be some other member comes up with a suggestion.

I know you won't like it, still I want to say Good Luck to You! :lolflag:

---

### Post by amjjawad on 2010-11-20
> **sikander3786 said:**
> I feel sorry. Your attempts didn't bear any fruit :-)

And I can't help you on antiX thing. That seems to go over my head :-)

Might be some other member comes up with a suggestion.

I know you won't like it, still I want to say Good Luck to You! :lolflag:

Never mind, it's already over my head and I don't feel like trying anymore.

Hahaha, I'm trying to say "Good luck" to myself as well to be motivated but it doesn't work anymore :D

---

### Post by Linux_junkie on 2010-11-20
> **amjjawad said:**
> Hi guys,

One of my relatives has a very old HP laptop. It's PII with 64MB RAM and not sure what's the capacity of the HDD. They installed Windows XP SP2 on it (which I disagree with them about that choice because the laptop needs 5-7 mins to boot up with XP) and I was wondering if there's a very light version of Linux that can be installed on it?

I have Slax, Linux Mint LXDE, Fedora LXDE and  Xubuntu. I guess (not sure) I have Win98 or WinMe but I don't want to install Windows, I want Linux.

What do you recommend? I tried Fedora LXDE and Xubuntu but didn't try Mint and Slax yet.

Any idea? :)

Thanks!

Instead of going down the Linux route why not try freeDOS! it's website is [http://www.freedos.org/](http://www.freedos.org/)

---

### Post by amjjawad on 2010-11-23
> **Linux_junkie said:**
> Instead of going down the Linux route why not try freeDOS! it's website is [http://www.freedos.org/](http://www.freedos.org/)

I love hard and tough challenges ;)
I just don't feel comfortable with easy solutions :)

Every time I try to throw that laptop away, the desire of making it up and running grow stronger :)

---

### Post by amjjawad on 2010-11-23
Well, not a great achievement for sure but after days and night of struggling, that ancient laptop has antiX up and running BUT with CLI not GUI. I'm still working side by side with antiX's guys to make it up and running with GUI. They're very helpful indeed and know what they're talking about :)

And I thought it's hopeless :D
Really, nothing is impossible!

---

### Post by Dragonbite on 2010-11-23
So did you try Tiny Core? I see it on your list, but I don't know if that means you tried it or not.

The only reason is because this caught my eye (I don't remember how much RAM you have, but it looks like they are talking about running the whole thing in RAM (OS & Apps), so installation may be better.> Unusually Fast. Unlike most operating systems, the Tiny Core can run completely from RAM. Individuals with RAM to spare can even use Tiny Core to load and run their programs from RAM (you didn't know your computer could run Open Office and Firefox so quick). Experienced users can still install Tiny Core to disk, but Tiny Core can run out of 48 megabytes of RAM ... or less.

Also, can the system PXE boot? You could take a more powerful system and set up an LTSP (thin client) situation where this one boots up to the LTSP server which does all of the work.?

OR what about RYO Linux... "Roll Your Own"?

---

### Post by amjjawad on 2010-11-23
> **Dragonbite said:**
> So did you try Tiny Core? I see it on your list, but I don't know if that means you tried it or not.

Yes, I put it on my list to make it easier for me and everyone else to summarize the whole thread in one post. However, I'm not sure why I haven't tried it yet. 

I just checked its website and it says:

> [I][B]It is not a complete desktop nor is all hardware completely supported.  It represents only the core needed to boot into a very minimal X desktop  typically with wired internet access.
[/B][/I]
Perhaps that's the reason why I didn't try it.

> The only reason is because this caught my eye (I don't remember how much RAM you have, but it looks like they are talking about running the whole thing in RAM (OS & Apps), so installation may be better.

The laptop comes with 64MB RAM and it has now 512MB as SWAP Partition. I formatted the whole drive so XP is no longer exist.

Also, Installation is not a problem now. I passed that stage now :)
I'm trying to get rid of CLI and get into GUI. It has antiX and I installed it after connecting the HDD of that laptop to one of my PCs.

>  Also, can the system PXE boot? You could take a more powerful system and set up an LTSP (thin client) situation where this one boots up to the LTSP server which does all of the work.?

It doesn't boot from a CD so I guess it will blow up if I'll do that :D
Actually it has no such option. There's no LAN port anyway.

>  OR what about RYO Linux... "Roll Your Own"?

[http://it.toolbox.com/blogs/locutus/roll-your-own-linux-11746](http://it.toolbox.com/blogs/locutus/roll-your-own-linux-11746)

Am I right?

---

### Post by Dragonbite on 2010-11-23
Yeah, the Roll Your Own Linux is also called LinuxFromScratch or DIYLinux I think.

---

### Post by amjjawad on 2010-11-23
> **Dragonbite said:**
> Yeah, the Roll Your Own Linux is also called LinuxFromScratch or DIYLinux I think.

WOW, this is very interesting my friend but it's a bit early for me at this point :)
I'd LOVE to build my own distribution. I'm not a programmer/developer but hope I don't have to be one.
Sooner or later, that would be my next move but first of all, I must learn more about Linux and that will be done by learning more about Ubuntu first :)

Thanks a lot for that tip. Will work hard from now to achieve that goal.

---

### Post by amjjawad on 2010-11-26
[B]To every beginning, there must be an end.
[/B]
For more than a month, I've been trying my very best to install one of Linux Distributions on a very old laptop (1999). For more than a month, I have tried many things. The last two weeks, I've tried days and nights. However, the title of this post is louder than my words.

> [FONT=Book Antiqua][COLOR=Navy][SIZE=4]**I did not fail, I found 10,000 ways that did not work**[/SIZE][/COLOR][/FONT]This is the **"unsuccessful"** end of this long thread. 

BIG THANK to everyone for everything, here in this forum and other forums that I had to register and start new threads there.

Until my next adventure, please be safe and hope to see you soon ;)

---

### Post by amjjawad on 2010-11-30
[B]                       When POSSIBLE beats impossible
When YES beats no
When LIGHT beats dark
When WIN beats fail
WHEN I SAY "I CAN DO IT" IT MEANS I CAN DO IT :D[/B]


I don't believe it. I don't believe I have such spirit. Every time I throw it away and say "move on, that piece of junk is worthless", the motivation in me becomes stronger and stronger. You know I've been trying to do that for a month or more.
Guess what? it happened, finally :D HOOO HAAA :D

Yes, that's Mint 9 LXDE and YES, I know it's so slow but you need to know that I've tried 10,000 ways that did not work and the 10,001 did work. So, give me a break, I just posted on Linux Mint's forum and hope someone could tell me how do I install another desktop manager and remove LXDE if possible. How to tweak it to make it faster.

The HDD was dead. I found bad block. However, it's fixed now.

No more talk ... the picture worths 1,000,000 words :D

---

### Post by Dragonbite on 2010-11-30
Woo Hoo!  Congratz!  Knew you could do it!

Hmm... now I'm wondering about my own little PI machine...

---

### Post by amjjawad on 2010-12-01
> **Dragonbite said:**
> Woo Hoo!  Congratz!  Knew you could do it!

Hmm... now I'm wondering about my own little PI machine...

Hahahah, thanks buddy I appreciate that :D

WOW, another old machine? PLEASE, SEND IT TO ME :P hahahahah

---

### Post by amjjawad on 2010-12-04
I forgot to mention what happened. I was so excited when I posted before few days :)

There you go. I posted that on antiX's forum:

> Okay I'm here to tell you a very good news and a bit of bad news.

Good  news: I managed to fix the problem on the HDD. Apparently, it had bad  blocks or at least this is what Linux CLI commands showed. I did my best  to find a tool to fix that so I found this:

[http://hddguru.com/](http://hddguru.com/)

It's Windows application. I used it to fix the HDD and it's working perfectly now.
I  installed Linux Mint 9 LXDE just for the sake of testing, nothing more.  It was so much slow (obviously) and I couldn't do anything so I removed  it and installed WattOS which is also slow. I guess I'll install either  Windows 98/ME, DOS or FreeDOS.

The bad news is: neither AntiX  nor any other distribution with GRUB Legacy was able to be installed.  THIS IS what I came to find out after billion times of installation. As  you already know, immediately after installing antiX or any OS with GRUB  Legacy, once I reboot, I got an error message. It never ever happened  with me whenever I use an OS with GRUB2. I guess it's because I'm  installing while the laptop's hard drive is connected to my PC through **USB Connection**. 

This is a bit of a problem. Every OS with GRUB2 needs minimum 128MB-192MB if not 265MB.
I perhaps need to tweak WattOS or other OS by installing lighter WM like Fluxbox, Openbox, etc.

**Honestly, I've done what I was looking for. It's working with Linux even though it's so slow [IMG]http://antix.freeforums.org/images/smilies/icon_smile.gif[/IMG]**

I made 700MB SWAP Partition but that did nothing, it's slow.

Just thought I have to let you know [IMG]http://antix.freeforums.org/images/smilies/icon_smile.gif[/IMG]

If anyone who is looking for a lightweight OS for his/her machine (64MB of RAM), there are many distributions listed in this thread. However, note that (this is from my own experience) some take more than 64MB. For example: antiX takes 99-100MB of RAM without running anything.
Archbang takes 90-100MB of RAM without running anything.

Also, I'd like to highlight a very important point:
First thing first, when we talk about "OLD" machines, then we need to define what do we mean by "old". In my case, I'm talking about +11 years old machine. That's really old :)
Second thing is, if you need to install a Linux OS or any other OS on similar machine, you need to ask yourself one simple question: How old is that OS I'm trying to install?
IMHO, it could be bad idea to install a recent OS (say 2009) on a very old and antique machine. Either install an old version or find an OS which is designed for such machines.
Unfortunately, in my case and as explained above, I couldn't install any OS with GRUB Legacy. Couple of distributions work for 64MB of RAM but they use GRUB Legacy not GRUB2.
Why didn't I buy an adapter (2.5 to 3.5) and use it instead of that mobile HDD enclosure with USB Connection? that's another story.

Anyway, that's all what I want to say :)

Sharing this amazing experience with everyone :)

---

### Post by lightnin on 2010-12-09
Thinking about the password issues you were having, I found this on the slackware FAQ

> Q: 	 What's the password for root on the install disk?

There isn't one. If you're asked for one, it usually means that you don't have enough memory to install.

To help work around this, look in your CMOS settings and make sure you don't have any ROM shadowing enabled. ROM shadowing wastes memory and won't improve the performance of Linux. Also, make sure you're using the smallest bootdisk you can. For example, you don't need to use "scsinet" if you're not installing to a SCSI drive via NFS. Use something small -- the "bare" disk if you can get away with it. Some people mistakenly think they need to use a bootdisk with network drivers if they plan to use networking after installation. Not so! The drivers on the bootdisk have no impact on what you can use *after* installation -- in almost all cases you won't be running the same kernel on your installed system as you used 

---

### Post by amjjawad on 2010-12-09
> **lightnin said:**
> Thinking about the password issues you were having, I found this on the slackware FAQ

What? I didn't understand anything :)

Anyway, I accomplished what I wanted from the beginning. I don't know what do you mean by your post but if you check my last few posts, you'll understand that I'm way beyond that stage.

Thanks ;)

---

### Post by Dragonbite on 2010-12-10
> **amjjawad said:**
> What? I didn't understand anything :)

Anyway, I accomplished what I wanted from the beginning. I don't know what do you mean by your post but if you check my last few posts, you'll understand that I'm way beyond that stage.

Thanks ;)
I think the gist of the post was when you don't have enough memory, you are asked for a password which may be what happened to you with Gentoo.

The rest is the techno-babble of how to work around this (I don't quite understand it either). :D

---

### Post by amjjawad on 2010-12-10
> **Dragonbite said:**
> I think the gist of the post was when you don't have enough memory, you are asked for a password which may be what happened to you with Gentoo.

The rest is the techno-babble of how to work around this (I don't quite understand it either). :D

So I'm not alone :D

That was long time ago. The laptop has WattOS.
Unfortunately, WattOS Forum is VERY inactive :( I posted there 6 or 7 days ago and nothing until now. Only 30 or less had read the post anyway.

I was thinking to install FreeDOS with a GUI but I don't want to waste "more" time with that laptop. I did what I wanted and I have nothing more to prove unless I want to go further and beyond that :D

---

### Post by Dragonbite on 2010-12-10
> **amjjawad said:**
> I did what I wanted and I have nothing more to prove unless I want to go further and beyond that :D

That will last about, 4.. 3.. 2..              :popcorn:

---

### Post by amjjawad on 2010-12-10
> **Dragonbite said:**
> That will last about, 4.. 3.. 2..              :popcorn:

ROFL, now, you start to read my mind, buddy :D hahaha

---

### Post by amjjawad on 2010-12-10
> **Dragonbite said:**
> That will last about, 4.. 3.. 2..              :popcorn:

ROFL, now, you start to read my mind, buddy :D hahaha

---

### Post by amjjawad on 2010-12-10
> **Dragonbite said:**
> That will last about, 4.. 3.. 2..              :popcorn:

ROFL, now, you start reading my mind, buddy :D hahaha

I'm sorry ... my internet connection is acting crazy lately so 3 posts were made instead of one :S

> The connection was reset

The connection to the server was reset while the page was loading.

---

### Post by Spice Weasel on 2010-12-10
Tiny Core if you have internets, DSL if you don't.

---

### Post by amjjawad on 2010-12-10
> **Spice Weasel said:**
> Tiny Core if you have internets, DSL if you don't.

Hmmm, I guess you didn't read the whole thread :)

---

### Post by Spice Weasel on 2010-12-10
> **amjjawad said:**
> Hmmm, I guess you didn't read the whole thread :)

I scanned a couple of pages. :P

Maybe I should go back..

e: WHATTHEHELLLINUXMINTON64MB

My 60MB laptop barely managed to run DSL...

---

### Post by amjjawad on 2010-12-10
> **Spice Weasel said:**
> I scanned a couple of pages. :P

Maybe I should go back..

Long story short: [http://ubuntuforums.org/showpost.php?p=10199668&postcount=108](http://ubuntuforums.org/showpost.php?p=10199668&postcount=108)

 :)

---

### Post by lightnin on 2010-12-10
Just the 1st two lines . Might be some of the problems you had earlier on.  It might be of some help to others reading this thread.  The rest of the quote might make sense to someone :-)

I am just trying a few installs on my 11 yr old Acer laptop.  Celeron 600. To see which will run suitably fast.

---

### Post by amjjawad on 2010-12-12
> **lightnin said:**
> Just the 1st two lines . Might be some of the problems you had earlier on.  It might be of some help to others reading this thread.  The rest of the quote might make sense to someone :-)

I am just trying a few installs on my 11 yr old Acer laptop.  Celeron 600. To see which will run suitably fast.

Just forget about that as it's history now ;)

What happened with you? did you install anything on your antique? :)

---

### Post by lightnin on 2010-12-13
I am still trying different disros.

I am a bit better off than you, because I have 192Mb ram installed
Xubuntu alternate install works but is a bit slow.

That is the only one that has self installed so far.

Others dont detect one thing or another (network / graphics etc ) and I dont have time to go tweaking at the moment.

Lubuntu hangs
Puppy and SliTaz doesnt see the network

also, I have run out of blank CD's to burn new ISO's too. I found a CDRW that boots OK, so I can still try one at a time. I will see if I can get the USB install to work, but the BIOS doesn't have that option.

That is where I am at at so far

Rich

---

### Post by amjjawad on 2010-12-13
> **lightnin said:**
> I am a bit better off than you, because I have 192Mb ram installed

Unquestionably, my friend :)
Oh, and don't forget my CD-Drive is dead so better square :P


> Xubuntu alternate install works but is a bit slow.

Have you tried Fedora LXDE?

> Others dont detect one thing or another (network / graphics etc ) and I dont have time to go tweaking at the moment.
Lubuntu hangs
Puppy and SliTaz doesnt see the network

Yeah, I know what you mean.

> I will see if I can get the USB install to work, but the BIOS doesn't have that option.

I'm still thankful to one of my friends who told me about this:
[http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)

---

### Post by lightnin on 2010-12-13
I haven't tried fedora, no. I'll add it to my list.

I've just got some more CD-R's, and I'll have a look at plop - that looks interesting !

Thanks

I'll post in this thread from time to time, with my results, if that is ok with you - as the thread starter ?

For now though, I need to fix my day to day PC - ubuntu packet manager is corrupted :-(  .... but that is another thread !

---

### Post by swiftlinuxcreator on 2010-12-13
I recently started a new antiX-derived lightweight distro called Swift Linux.  It has the UNIQUE combination of: 
1. Lightweight operation: If your computer can run Windows 98 or Puppy Linux, it can run Swift Linux. 
2.  Superior repository: Debian compatible 
3.  User-friendliness  Swift Linux is at [http://www.swiftlinux.org](http://www.swiftlinux.org) .

---

### Post by amjjawad on 2010-12-13
> **lightnin said:**
> I haven't tried fedora, no. I'll add it to my list.

I think on page6 of this thread or ... not really sure what page ... you'll find a list of all the distributions that other users have recommended and another post with a link about some others.
Try to have a look.
Again, 192MB is MUCH better than 64MB with a dead CD-Drive :)

> I've just got some more CD-R's, and I'll have a look at plop - that looks interesting !

Thanks
You welcome :)


> I'll post in this thread from time to time, with my results, if that is ok with you - as the thread starter ?
I don't mind at all but I prefer to post results and if you're facing any problem especially with another distribution rather than Ubuntu, I recommend to sign up on their forum. I have an account with Fedora, WattOS, OpenSUSE, antiX, Debian and can't remember what else.
Have to say that antiX forum was THE BEST forum ever. ALL of the posters are so much polite and helpful. antiX is a good option as well. 
On the other hand, users in Debian forum are so much rude. I'll never login again on their forum and not really interested to try or use Debian. I thought I could install it on my laptop but it didn't work.

Let's us know what will happen :)

> For now though, I need to fix my day to day PC - ubuntu packet manager is corrupted :sad:  .... but that is another thread.
Yes :)
Don't post here though, try Absolute Beginner talk :)

---

### Post by amjjawad on 2010-12-13
> **swiftlinuxcreator said:**
> I recently started a new antiX-derived lightweight distro called Swift Linux.  It has the UNIQUE combination of: 
1. Lightweight operation: If your computer can run Windows 98 or Puppy Linux, it can run Swift Linux. 
2.  Superior repository: Debian compatible 
3.  User-friendliness  Swift Linux is at [http://www.swiftlinux.org](http://www.swiftlinux.org) .

You mean you start using it?

It's not listed yet in [distrowatch]("http://distrowatch.com/").

---

### Post by asifnaz on 2010-12-14
> **soldier1st said:**
> well there won't be many linux alternatives that will run on that ammount of ram decently, DSL and puppy linux and lubuntu are very lightweight but don't even think of putting xp back on it as it will be slow as you have seen so MS oses are out of the question but couldn't you upgrade the ram?ram is cheap and it works but if you can't you of course do have a few options.

I dont mind giving credit to Microsoft Oses . Windows 95 can run on 486 with 8 mb ram and even 4 mb ram .

Windows 98 can run on PI with 16 mb ram .

I am not assuming I actully worked on such PCs

---

### Post by amjjawad on 2010-12-14
> **asifnaz said:**
> I dont mind giving credit to Microsoft Oses . Windows 95 can run on 486 with 8 mb ram and even 4 mb ram .

Windows 98 can run on PI with 16 mb ram .

I am not assuming I actully worked on such PCs

No one could deny that. Even XP, you [still can run it on 64MB RAM]("http://www.microsoft.com/windowsxp/sysreqs/pro.mspx") but definitely, the machine will be so slow.
However, the challenge in my case was to install a new OS on a very old machine.

XP is 9 years old. The OS I installed on that machine is less than 1 year old. That's the challenge I'm talking about.
As for Microsoft, can I install Vista or Windows 7? undeniably no one can.

Reminder:
My machine is:
HP Omni book 4150
CPU: PII 366MHz
RAM: 64MB PC100
HDD: 4.5GB
CD-Drive: Dead
Floppy: N/A
LAN: N/A
USB: USB 1.0 x1 port.

---

### Post by asifnaz on 2010-12-14
> **amjjawad said:**
> No one could deny that. Even XP, you [still can run it on 64MB RAM]("http://www.microsoft.com/windowsxp/sysreqs/pro.mspx") but definitely, the machine will be so slow.
However, the challenge in my case was to install a new OS on a very old machine.

XP is 9 years old. The OS I installed on that machine is less than 1 year old. That's the challenge I'm talking about.
As for Microsoft, can I install Vista or Windows 7? undeniably no one can.

Reminder:
My machine is:
HP Omni book 4150
CPU: PII 366MHz
RAM: 64MB PC100
HDD: 4.5GB
CD-Drive: Dead
Floppy: N/A
LAN: N/A
USB: USB 1.0 x1 port.

In such case go for Slitaz . I have installed it on PI with 32 MB ram . It works fine . It is my hobby to buy very old laptops at junk price and try to make them work .

---

### Post by amjjawad on 2010-12-14
> **asifnaz said:**
> In such case go for Slitaz . I have installed it on PI with 32 MB ram . It works fine . It is my hobby to buy very old laptops at junk price and try to make them work .

In that case I suggest to read the whole thread ;)

---

### Post by asifnaz on 2010-12-14
[I]CD-Drive: Dead
Floppy: N/A
LAN: N/A
USB: USB 1.0 x1 port.

[/I]You need external CD drive in oredr to install any distro . I havent read full thread by the way :D

---

### Post by amjjawad on 2010-12-14
> **asifnaz said:**
> [I]CD-Drive: Dead
Floppy: N/A
LAN: N/A
USB: USB 1.0 x1 port.

[/I]You need external CD drive in oredr to install any distro . I havent read full thread by the way :D

When you'll read the whole thread, you'll understand that your last two posts are invalid :)

---

### Post by asifnaz on 2010-12-14
> **amjjawad said:**
> When you'll read the whole thread, you'll understand that your last two posts are invalid :)

I think you will keep wondering .

---

### Post by CharlesA on 2010-12-14
Good luck. The only way I can think of getting some form of Linux of that machine is to throw the drive in another machine and see what you can install.

Having a dead cd drive and no LAN makes it quite hard, unless you find something that'll work with yer wireless card.

---

### Post by amjjawad on 2010-12-14
> **CharlesA said:**
> Good luck. The only way I can think of getting some form of Linux of that machine is to throw the drive in another machine and see what you can install.

Having a dead cd drive and no LAN makes it quite hard, unless you find something that'll work with yer wireless card.

Thank you, CharlesA :)

That was the fun part of this challenge. Can't deny I had tough time but I enjoyed a lot. If you're interested to know, please check Post [105 ]("http://ubuntuforums.org/showpost.php?p=10183383&postcount=105")and post [108 ]("http://ubuntuforums.org/showpost.php?p=10199668&postcount=108"):)

---

### Post by CharlesA on 2010-12-14
> **amjjawad said:**
> Thank you, CharlesA :)

That was the fun part of this challenge. Can't deny I had tough time but I enjoyed a lot. If you're interested to know, please check Post [105 ]("http://ubuntuforums.org/showpost.php?p=10183383&postcount=105")and post [108 ]("http://ubuntuforums.org/showpost.php?p=10199668&postcount=108"):)
Awesome. Nice job. :)

---

### Post by amjjawad on 2010-12-14
> **CharlesA said:**
> Awesome. Nice job. :)

Appreciate that :)

---

### Post by amjjawad on 2010-12-20
I have installed Linux Mint Fluxbox on that laptop. It's much lighter but whenever I connect to the interent, it starts to be so slow.

Anyway, as I already mentioned before, I did what I want and there's nothing more to prove :P Linux Rules, period.

I'm looking now for more old machines. I need to start calling some friends :)

---

### Post by lightnin on 2010-12-23
> **amjjawad said:**
> 
I'm looking now for more old machines. I need to start calling some friends :)

Where are you based ?  I have a few, if you are in the UK :D

---

### Post by amjjawad on 2010-12-23
> **lightnin said:**
> Where are you based ?  I have a few, if you are in the UK :D

So nice of you mate but I'm very far from you :)

---

### Post by amjjawad on 2011-10-27
I just don't believe that... before few months, the laptop fell down and the lid plus some other parts are BROKEN ... however, it does WORK :D

I'm too busy with Lubuntu stuff at the moment (I have joined Lubuntu Team in August, 2011) but I guess I'll go wild again with another adventure :D

P.S.
We have HP Pavilion dv6 [Core i5, 4GB RAM, Win7 64bit] and it takes LONGER time to get a working desktop than this broken P2 Laptop :D

---

### Post by s.fox on 2011-12-21
Thread moved to [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401") and renamed at OP request.

---

### Post by amjjawad on 2011-12-21
> **s.fox said:**
> Thread moved to [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401") and renamed at OP request.

Thanks a lot, s.fox :)
I appreciate that!

---

### Post by amjjawad on 2011-12-21
I think the attached screenshot speaks louder than 1000 words :)

I have decided to use it and ... oh boy, it works and doing great :D

If you see it, you would never believe it works ... it's broken from the outside and some keys are missing but the inside works prefectlly :)

Edit:
If anyone is interested, let me know and I'll help you to breath new life into your old machine instead of keeping it with dust :)

---

### Post by JC Cheloven on 2011-12-26
Really amazes me. The most I succeded in a similar specs pc was puppy (4.1 I think). I also like to bring back to life old computers.

I guess setting up the swap before anything else has been a keypoint?
Oh... is that midori what I see in the bottom?
Just curious: Is the system nearly usable for web browsing ?

Congrats in any case :)

JC

---

### Post by amjjawad on 2011-12-29
> **JC Cheloven said:**
> I guess setting up the swap before anything else has been a keypoint?
Preciously :)
If you check the Community Documents, you'll see that too. I mean I think it's mentioned there.

> Oh... is that midori what I see in the bottom?

Yes. Other browsers are not usable.

> Just curious: Is the system nearly usable for web browsing ?

It depends on what website are you visiting?! for example, Ubuntu Forum Website was ok but with Gmail, it was NOT.

>  Congrats in any case :)
Thanks a lot :)

I have done all that as a challenge to myself whether I can do it or not (specially the laptop is actually broken) ad also to prove that Linux is very much capable of that. It had WinXP before I take it from its owner. With XP, I had to wait for many mins to do one simple thing. Now, I don't have to.

Linux ROCKS :D

---

### Post by leclerc65 on 2011-12-30
I tried Puppy then abandoned it because it's not very newbie friendly.
Then I came back and tried Lucid Puppy 5.28, very impressed !

---

### Post by JC Cheloven on 2012-01-02
> **leclerc65 said:**
> I tried Puppy then abandoned it because it's not very newbie friendly.
Then I came back and tried Lucid Puppy 5.28, very impressed !

Yep. Puppy has been amazing over the time. I enjoyed it many times, specially when an old machine was at hand.

---

### Post by amjjawad on 2012-01-12
Had to go back few pages to find **[this]("http://ubuntuforums.org/showpost.php?p=10088152&postcount=83")**. I'm sure I have tried more at that time. Anything with GRUB Legacy did NOT work whatsoever and I still don't know why? the only system that worked on that laptop was Linux Mint LXDE 9.
I thought I could try to install Lubuntu but taking the hard drive out yet again while the laptop is broken is not good idea ... I'm afraid I'll break it. The Physical Damage from the outside is bad and I like that old machine and not ready to let it go :) I spent the best month in my life with it and I have learned a lot from it so I want to keep it the way it is :)

Puppy was not helpful at all for my case.

---

### Post by amjjawad on 2012-04-10
I can't sit still, I must do something and I guess I did it again :)

I'm not going to write much, pictures will do the talk on my behalf :)

**I did get rid of Linux Mint 9 and replace it with [COLOR="Navy"]Lubuntu 11.10[/COLOR] and [COLOR="Red"]OH YES[/COLOR], the machine is more responsive now and ... [COLOR="red"]OH YES, it is Kernel 3.0.0.17[/COLOR] :D**

---

### Post by Dragonbite on 2012-04-10
> **amjjawad said:**
> I can't sit still, I must do something and I guess I did it again :)

I'm not going to write much, pictures will do the talk on my behalf :)

**I did get rid of Linux Mint 9 and replace it with [COLOR="Navy"]Lubuntu 11.10[/COLOR] and [COLOR="Red"]OH YES[/COLOR], the machine is more responsive now and ... [COLOR="red"]OH YES, it is Kernel 3.0.0.17[/COLOR] :D**

Awesome to hear!  Your machine looks like it's had better days.  Should cover it with duck tape to hold it together and give it that "shiny" Apple look! :lolflag:

---

### Post by Herpythebrony on 2012-04-10
> **amjjawad said:**
> I can't sit still, I must do something and I guess I did it again :)

I'm not going to write much, pictures will do the talk on my behalf :)

**I did get rid of Linux Mint 9 and replace it with [COLOR=Navy]Lubuntu 11.10[/COLOR] and [COLOR=Red]OH YES[/COLOR], the machine is more responsive now and ... [COLOR=red]OH YES, it is Kernel 3.0.0.17[/COLOR] :D**
Lubuntu, saving your old computers from the trash since 2009.

---

### Post by amjjawad on 2012-04-25
> **Herpythebrony said:**
> Lubuntu, saving your old computers from the trash since 2009.

Actually at that time when I got that laptop from someone and tried to play with Linux on it, Lubuntu 10.04 at that time didn't work for some reason. Funny that 11.10 did :D
So, Lubuntu on that laptop is just recently installed :)

After all, it's not for daily use because it's VERY old.

---

### Post by Herpythebrony on 2012-04-26
> **amjjawad said:**
> Actually at that time when I got that laptop from someone and tried to play with Linux on it, Lubuntu 10.04 at that time didn't work for some reason. Funny that 11.10 did :D
So, Lubuntu on that laptop is just recently installed :)

After all, it's not for daily use because it's VERY old.
The early releases where kinda buggy but Lubuntu has come leaps and bounds. And major improvement when it finally got parenting from the big guns and Canonical. Color me dazzled! XD

---

