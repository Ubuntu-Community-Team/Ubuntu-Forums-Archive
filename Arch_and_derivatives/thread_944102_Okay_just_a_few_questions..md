---
title: "Okay just a few questions."
date: 2008-10-11
forum: Arch and derivatives
---

### Post by Jordan777 on 2008-10-11
So i've decided I'm going to try and install ArchLinux but I have a few questions.  It says the only two options available are x86-64bit and i686.  Well I know I run on the x86 architecture (AMD 5200+) but I don't know about 64 bit.  Does it make any difference?  I really want to try Arch but I don't want to download it for no reason.  I know this is a newb question but I really want to try Arch and I'm willing to go through the time to get a system set up that's truly mine.  Also I noticed they have The Core and FTP versions of ISO/USB.  I'm wondering which one I should try.  I know the difference between USB and ISO but I'm not sure about Core and FTP.  Also I have a 4GB sandisk usb drive should I just use that or should I stick with the ISO (cd) installation?

Again I'm sorry that I'm so newbish but what else are these forums for? :lolflag:

---

### Post by noerrorsfound on 2008-10-11
That's a 64-bit processor. Get x86-64.

---

### Post by SkonesMickLoud on 2008-10-11
Core is the install disk with packages that'll give you a base install without the need for an internet connection.  Depending on when the .iso you downloaded was shot the packages might be a bit outdated.

If you have broadband or a connection that's simple to set up, the FTP disc will get you the same packages as Core, but they'll be more up to date as you'll download them before installing.

Unless you know for sure that you'll be able to set up your connection, it's best to get the core disc.

---

### Post by Jordan777 on 2008-10-11
Wow you guys answered quick!  So if I use core I can still update the packages and stuff to their current states?  I should most likely use core just so I can get the base system set up and then work on wireless.  god knows if I could get my realtek 8187 to work other wise.

---

### Post by SkonesMickLoud on 2008-10-11
> **Jordan777 said:**
> So if I use core I can still update the packages and stuff to their current states?

Yeah.  When you get all booted after the install and get your network up, just:

```

su -
pacman -Syu
```

And you'll have a fully up to date system.

---

### Post by SomeGuyDude on 2008-10-11
Just for what it's worth, I had issues with the 64-bit (running Intel C2D, so yes it's the right proc). No flash was one, there were a lot of other hiccups as well. Currently just rolling with the i686 version and it's smooth as silk.

---

### Post by crimesaucer on 2008-10-11
> **SomeGuyDude said:**
> Just for what it's worth, I had issues with the 64-bit (running Intel C2D, so yes it's the right proc). No flash was one, there were a lot of other hiccups as well. Currently just rolling with the i686 version and it's smooth as silk.


64bit Flash plugin was super easy with this guide: [http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64](http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64)


For 64bit Java plugin use Openjdk "icedtea": [http://www.archlinux.org/packages/extra/x86_64/openjdk6/](http://www.archlinux.org/packages/extra/x86_64/openjdk6/) 


My 64bit Arch has always worked good.



Also some more Arch64 info: 

[http://wiki.archlinux.org/index.php/Category:Arch64_(English](http://wiki.archlinux.org/index.php/Category:Arch64_(English))
[http://wiki.archlinux.org/index.php/Arch64_FAQ](http://wiki.archlinux.org/index.php/Arch64_FAQ)

---

### Post by crimesaucer on 2008-10-11
> **Jordan777 said:**
> So i've decided I'm going to try and install ArchLinux but I have a few questions.  It says the only two options available are x86-64bit and i686.  Well I know I run on the x86 architecture (AMD 5200+) but I don't know about 64 bit.  Does it make any difference?  I really want to try Arch but I don't want to download it for no reason.  I know this is a newb question but I really want to try Arch and I'm willing to go through the time to get a system set up that's truly mine.  Also I noticed they have The Core and FTP versions of ISO/USB.  I'm wondering which one I should try.  I know the difference between USB and ISO but I'm not sure about Core and FTP.  Also I have a 4GB sandisk usb drive should I just use that or should I stick with the ISO (cd) installation?

Again I'm sorry that I'm so newbish but what else are these forums for? :lolflag:



If your eth0 Internet connection works good with ubuntu, then you should try the FTP install.


There is even an FTP option on the regular CD.


FTP will start your install with detecting your Ethernet connection, then it will ask you if you want to use DHCP, you say yes, then it will ask you what mirror to use.... you pick one close to your location.... then it will go into a regular install just like the CD..... except it's already configured your DHCP for your rc.conf.


If you want a VERY OLD look at what to expect, check this VERY OLD guide out because it still has some very good info: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)


.....read and look at all of the pictures from all 10 PAGES to see what you are about to get into.


With the FTP install you don't have to do a full system upgrade after installing like you do from the version on the disk.... because it installs the newest version of every package just like if it were doing a regular pacman -Syu (full system upgrade). When you install the CORE packages from the CD you have to finish with a "pacman -Syu" to catch up to the version that the rolling release is on.

Like this part in that old guide: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7)

---

### Post by handy on 2008-10-11
You probably already know this, but I'll just put it here to make sure, because it is SO important.

Use this [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") & follow it to the letter, if you are unsure of the meaning of something, ask here &/or on the Arch forums, search the Arch wiki it is really well made.

Good luck, I think you will enjoy the trip. :-)

P.S. I use 64bit too, no problems here either.

---

### Post by Jordan777 on 2008-10-11
Okay so I think I just have two last questions before I start this thing up.  I need to know how I can partition my hdd.  I only have one internal and I'm gonna dual-boot arch (hopefully) and Windows XP.  Right now Windows XP is up and running and I'd like to keep it that way.  I'm wondering, when I install Arch can I bypass the \var partition?  On ubuntu I only had a \, \home, and swap partition.  Or can i make one of them extended so I don't end up going over the primary partition limit of 4?

Also I noticed there is a lot of little tweaking that needs to be done from that guide with the pictures.  Is there any way, other than having another computer, to have the manual while I'm doing all this?  I thought I read somewhere that you can just switch to a different terminal and type in some command to bring up the installation guide in nano or vi(m)?

---

### Post by SkonesMickLoud on 2008-10-11
> **Jordan777 said:**
> Okay so I think I just have two last questions before I start this thing up.  I need to know how I can partition my hdd.  I only have one internal and I'm gonna dual-boot arch (hopefully) and Windows XP.  Right now Windows XP is up and running and I'd like to keep it that way.  I'm wondering, when I install Arch can I bypass the \var partition?  On ubuntu I only had a \, \home, and swap partition.  Or can i make one of them extended so I don't end up going over the primary partition limit of 4?

Also I noticed there is a lot of little tweaking that needs to be done from that guide with the pictures.  Is there any way, other than having another computer, to have the manual while I'm doing all this?  I thought I read somewhere that you can just switch to a different terminal and type in some command to bring up the installation guide in nano or vi(m)?

/var doesn't *need* it's own partition.

For the beginers guide during the install:

```

Ctrl+Alt+F2
more /arch/beginnersguide.txt

```

---

### Post by Jordan777 on 2008-10-11
Thanks a lot!  You guys have been very helpful and I really appreciate it!  Hopefully some other people see this thread and get just as much help as I did.  I'll be back if I have more questions which I inevitably will. :lolflag:

---

### Post by crimesaucer on 2008-10-11
> **Jordan777 said:**
> Okay so I think I just have two last questions before I start this thing up.  I need to know how I can partition my hdd.  I only have one internal and I'm gonna dual-boot arch (hopefully) and Windows XP.  Right now Windows XP is up and running and I'd like to keep it that way.  I'm wondering, when I install Arch can I bypass the \var partition?  On ubuntu I only had a \, \home, and swap partition.  Or can i make one of them extended so I don't end up going over the primary partition limit of 4?

Also I noticed there is a lot of little tweaking that needs to be done from that guide with the pictures.  Is there any way, other than having another computer, to have the manual while I'm doing all this?  I thought I read somewhere that you can just switch to a different terminal and type in some command to bring up the installation guide in nano or vi(m)?


Use nano, it's easier for beginners.... 

ctrl + o, then enter for same file name, then yes = a saved file

ctrl + x will exit with out changing the file


thats all you need to know about nano for the install.


> ".....Is there any way, other than having another computer, to have the manual while I'm doing all this....."

On the live CD they include the beginners guide in text like SkonesMickLoud said.


> ".....I only have one internal and I'm gonna dual-boot arch (hopefully) and Windows XP....."

Leave your Windows Xp on sda1. Don't touch it.


Delete everything else.


Then create a partition for boot on sda2. Toggle it for boot (you have to un-toggle windows boot).


The create a SWAP on sda3


Then finish with your root / (linux uses slashs this way / for root) on sda4.


Now you have your 4 primary partitions.... with a dual boot:

sda 1 = Xp
sda 2 = /boot
sda 3 = SWAP
sda 4 = /root


Don't worry about mounting Windows until after the install. Just mount sda2, sda3, and sda4.


..... Unless you have windows on 2 partitions, or need a separate /data partition, there should be no need for a extended/logical partition.

---

### Post by Jordan777 on 2008-10-11
So I need a /boot partition?  Mkay so do I just do like what I did with Ubuntu?

With Ubuntu I had:
sda2 - /*root*(~10Gb)
sda3 - SWAP (1024 MB)
Sda4 - /home (remainder hdd space)

But with Arch it would be:
sda2 - /boot (~10GB)
sda3 - SWAP (1024MB)
sda4 - /*root*(remainder hdd space)

Is that how I set it up?  I'm just unclear as to how much space the /boot partition needs and I guess /*root* now acts as what was my /home partition for Ubuntu?

---

### Post by Rumor on 2008-10-11
> **Jordan777 said:**
> So I need a /boot partition?  Mkay so do I just do like what I did with Ubuntu?

With Ubuntu I had:
sda2 - /*root*(~10Gb)
sda3 - SWAP (1024 MB)
Sda4 - /home (remainder hdd space)

But with Arch it would be:
sda2 - /boot (~10GB)
sda3 - SWAP (1024MB)
sda4 - /*root*(remainder hdd space)

Is that how I set it up?  I'm just unclear as to how much space the /boot partition needs and I guess /*root* now acts as what was my /home partition for Ubuntu?

A separate boot is not necessary, but it can be helpful. It does not need to be any larger than 50 megabytes as only the kernel image will reside there. 10GB is way too much real estate to give to /boot.

Your Ubuntu layout would work fine for Arch too.

---

### Post by crimesaucer on 2008-10-11
> **Jordan777 said:**
> So I need a /boot partition?  Mkay so do I just do like what I did with Ubuntu?

With Ubuntu I had:
sda2 - /*root*(~10Gb)
sda3 - SWAP (1024 MB)
Sda4 - /home (remainder hdd space)

But with Arch it would be:
sda2 - /boot (~10GB)
sda3 - SWAP (1024MB)
sda4 - /*root*(remainder hdd space)

Is that how I set it up?  I'm just unclear as to how much space the /boot partition needs and I guess /*root* now acts as what was my /home partition for Ubuntu?

/boot should only be about 50MB.....

other than that, it would be good.


Root ( "/" ) is your entire system.... it includes /home, /etc, /usr, /lib...... and the rest of your system.

---

### Post by handy on 2008-10-11
If you have a gig or more of RAM, I wouldn't bother creating a SWAP partition, unless you are heavily into editing video, CAD, recording multi-track audio & the like.  You will already know if you are one of the few that needs huge amounts of RAM.  

I have an iMac that runs Arch with 1Gb of RAM & another machine that runs Arch with 2GB of RAM, & neither of them have a SWAP partition/file & neither of them ever get anywhere near needing one.

---

### Post by SomeGuyDude on 2008-10-12
> **handy said:**
> If you have a gig or more of RAM, I wouldn't bother creating a SWAP partition, unless you are heavily into editing video, CAD, recording multi-track audio & the like.  You will already know if you are one of the few that needs huge amounts of RAM.  

I have an iMac that runs Arch with 1Gb of RAM & another machine that runs Arch with 2GB of RAM, & neither of them have a SWAP partition/file & neither of them ever get anywhere near needing one.

Don't you need a swap partition if you use suspend-to-RAM? The guide says aim for a swap of around 110% of your RAM and that's what I've been doin' thus far.

---

### Post by handy on 2008-10-12
> **SomeGuyDude said:**
> Don't you need a swap partition if you use suspend-to-RAM? The guide says aim for a swap of around 110% of your RAM and that's what I've been doin' thus far.

I don't use notebooks, so I guess if the OP is using one (though probably not with a 64bit 5200+), or likes to use suspend to RAM on his/her desktop, then a swap partition IS needed.

Thanks for pulling me up on that one. :-)

---

### Post by Jordan777 on 2008-10-12
No, I'm just on my desktop.  I'm having some interesting problems though.  At first I tried to install Arch and I got an error where it wouldn't load or something like that.  So I went back and just redid it because it wouldn't hurt to just repartition the drives.  Every time after that I kept getting a grub 15 error at boot.  So I redid it a couple of times again.  Now I've gotten it to the point where grub will load and arch will load but here seems to be the problem.  Arch loads but I'm just at a console basically just as if I was installing it again.  Also in the grub boot menu my Windows XP isn't even shown.  Just Arch Linux and Arch Linux Fallback.  I'm gonna continue to read on to see if I have to enable the GUI for Arch but if I'm unsuccessful I'm gonna have to uninstall it for now just so I can continue using my computer.

I ended up just using two partitions for Arch.
sda1 Windows XP
sda2 / (12GB)
sda3 /home (remainder)

Before I tried setting up a /boot partition and I kept getting the grub 15 error so I don't know what that was about. 

Also since I'm very new I basically don't change anything in the configuration files.  That may be against the Arch way but just getting this distro up and running would be a great leap for me right now.  I'm not super concerned with editing out that one function that doesn't really need to be there.  Also since I use dhcp there's nothing except for one line in defining eth0="dhcp" that needs to be changed.

Maybe you guys can give me help or maybe not.  I'm still hoping for the best.  I'm off to read the Arch guide now to see if the console is normal or if I messed up yet again.  :-k

---

### Post by myboosnme on 2008-10-12
EXCELLENT CASH INCOME 
I started out with $6. Now, I am making thousands.
I found this on a bulletin board and decided to try it. A little
while back, I was browsing through newsgroups, just like you are now,
and came across an article similar to this tha said you could make
thousands of dollars within weeks with only an initial investment of
$6.00! So I thought, "Yeah right, this must be a scam", but
like most of us, I was curious, so I kept reading. Anyway, it said
that you send $1.00 to each of the 6 names and addresses stated in the
article. You then place your own name and address in the bottom of
the list at #6, and post the article in at least 200 newsgroups.
(There are thousands) No catch, that was it. So after thinking it
over, and talking to a few people first, I thought about trying it. I
figured: "what have I got to lose except 6 stamps and $6.00,
right?" Then I invested the measly $6.00. Well GUESS WHAT!?...
within 7 days, I started getting money in the mail! I was shocked! I
figured it would end soon, but the money just kept coming in. In my
first week, I made about $25.00. By the end of the second week I had
made a total of over $1,000.00! In the third week I had over
$10,000.00 and it's still growing. This is now my fourth week and I
have made a total of just over $42,000.00 and it's still coming in
rapidly. It's certainly worth $6.00, and 6 stamps, I have spent more
than that on the lottery!! Let me tell you how this works and most
importantly, WHY it works... Also, make sure you print a copy of this
article NOW, so you can get the information off of it as you need it.
I promise you that if you follow the directions exactly, that you
will start making more money than you thought possible by doing
something so easy!
Suggestion: Read this entire message carefully! (print it out or
download it.) Follow the simple directions and watch the money come
in!
It's easy. It's legal. And your investment is only $6.00 (Plus
postage)
IMPORTANT: This is not a rip-off; it is not indecent; it is not
illegal; and it is 99% no risk - it really works!
If all of the following instructions are adhered to, you will receive
extraordinary dividends.
PLEASE NOTE:
Follow these directions EXACTLY, and $50,000.00 or more can be
yours in 20 to 60 days. This program remains successful because of
the honesty and integrity of the participants. Please continue its
success by carefully adhering to the instructions.
You will now become part of the Mail Order business. In this business
your product is not solid and tangible, it's a service. You are in
the business of developing Mailing Lists. Many large corporations are
happy to pay big bucks for quality lists. However, the money made
from the mailing lists is secondary to the income which is made from
people like you and me asking to be included in that list.
Here are the 4 easy steps to success:
STEP 1:
Get 6 separate pieces of paper and write down your name and address
followed by the words "PLEASE ADD ME TO YOUR MAILING LIST" on each
of them. Now get 6 US $1.00 bills and place ONE inside EACH of the
6 pieces of paper so the bill will not be visible through the envelope
(to prevent thievery). Next, place one paper in each of the 6 envelopes
and seal them. You should now have 6 sealed envelopes, each with a piece of
paper stating the above phrase, your name and address, and a $1.00
bill. What you are doing is creating a service. THIS IS ABSOLUTELY
LEGAL! You are requesting a legitimate service and you are paying for
it! Like most of us I was a little skeptical and a little worried
about the legal aspects of it all. So I checked it out with the U.S.
Post Office (1-800-725-2161) and they confirmed that it is indeed
legal. Mail the 6 envelopes to the following addresses:
1) C. Warren
721 W. 1500 S.
Provo, UT 84601
2) justin s
12 bense ct
Washington, NJ 07882
3) Rueben Hernandez
709 3rd ave apt B
Bradley Beach, NJ 07720
4)Gregory Avanesov 777 Foster av apt.4a Brooklyn NY 11230
5) Carmen Limon Fabian
San bonifacio 400 1028 res.chap.
Guadalajara, jalisco 44500
Mexico
 6)Angela Myers
   211c w 151 st 4d
   New York, NY 10039

STEP 2:
Now take the #1 name off the list that you see above, move
the other names up (6 becomes 5, 5 becomes 4, etc...) and add YOUR
Name as number 6 on the list.
STEP 3:
Change anything you need to, but try to keep this article as
close to original as possible. Now, post your amended article to at
least 200 newsgroups. (I think there are close to 24,000 groups) All
you need is 200, but remember, the more you post, the more money you
make! You won't get very much unless you post like crazy.
This is perfectly legal! If you have any doubts, refer to Title 18
Sec. 1302 & 1341 of the Postal lottery laws.
Keep a copy of these steps for yourself and, whenever you need money,
you can use it again, and again.
PLEASE REMEMBER that this program remains successful because of the
honesty and integrity of the participants and by their carefully
adhering to the directions. Look at it this way. If you are of
integrity, the program will continue and the money that so many
others have received will come your way.
NOTE: You may want to retain every name and address sent to you,
either on a computer or hard copy and keep the notes people send you.
This VERIFIES that you are truly providing a service. (Also, it might
be a good idea to wrap the $1 bill in dark paper to reduce the risk
of mail theft.)
So, as each post is downloaded and the directions carefully followed,
six members will be reimbursed for their participation as a List
Developer with one dollar each. Your name will move up the list
geometrically so that when your name reaches the #1 position you will
be receiving thousands of dollars in CASH!!! What an opportunity for
only $6.00 ($1.00 for each of the first six people listed above) Send
it now, add your own name to the list and you're in business!
---DIRECTIONS ----- FOR HOW TO POST TO NEWSGROUPS------------
Step 1) You do not need to re-type this entire letter to do your own
posting. Simply put your cursor at the beginning of this letter and
drag your cursor to the bottom of this document, and select 'copy'
from the edit menu. This will copy the entire letter into the
computer's memory.
Step 2) Open a blank 'notepad' file and place your cursor at the top
of the blank page. From the 'edit' menu select 'paste'. This will
paste a copy of the letter into notepad so that you can add your name
to the list.
Step 3) Save your new notepad file as a .txt file. If
you want to do your postings in different settings, you'll always
have this file to go back to.
Step 4) Use Netscape or Internet explorer and try searching for
various newsgroups (on-line forums, message boards, chat sites,
discussions.)
Step 5) Visit these message boards and post this article as a new
message by highlighting the text of this letter and selecting paste
from the edit menu. Fill in the Subject, this will be the header that
everyone sees as they scroll through the list of postings in a
particular group, click the post message button. You're done with
your first one! Congratulations...THAT'S IT! All you have to do is
jump to different newsgroups and post away, after you get the hang of
it, it will take about 30 seconds for each newsgroup!
**REMEMBER, THE MORE NEWSGROUPS YOU POST IN, THE MORE MONEY YOU WILL MAKE! 
BUT 
:
YOU HAVE TO POST A MINIMUM OF 200**
That's it! You will begin receiving money from around the world within days! You may eventually want to
rent a P.O.Box due to the large amount of mail you will receive. If
you wish to stay anonymous, you can invent a name to use, as long as
the postman will deliver it.
**JUST MAKE SURE ALL THE ADDRESSES ARE CORRECT.**
Now,
each of the 5 persons who just sent me $1.00 make the MINIMUM 200
postings, each with my name at #5 and only 5 persons respond to each
of the original 5, that is another $25.00 for me, now those 25 each
make 200 MINIMUM posts with my name at #4 and only 5 replies each, I
will bring in an additional $125.00! Now, those 125 persons turn
around and post the MINIMUM 200 with my name at #3 and only receive 5
replies each, I will make an additional $625.00! OK, now here is the
fun part, each of those 625 persons post a MINIMUM 200 letters with
my name at #2 and they each only receive 5 replies, that just made me
$3,125.00!!! Those 3,125 persons will all deliver this message to 200
newsgroups with my name at #1 and if still 5 persons per 200
newsgroups react I will receive $15,625,00! With an original
investment of only $6.00! AMAZING! When your name is no longer on the
list, you just take the latest posting in the newsgroups, and send
out another $6.00 to names on the list, putting your name at number 6
again. And start posting again. The thing to remember is: do you
realize that thousands of people all over the world are joining the
internet and reading these articles everyday?, JUST LIKE YOU are
now!! So, can you afford $6.00 and see if it really works?? I think
so... People have said, "what if the plan is played out and no
one sends you the money? So what! What are the chances of that
happening when there are tons of new honest users and new honest
people who are joining the internet and newsgroups everyday and are
willing to give it a try? Estimates are at 20,000 to 50,000 new
users, every day, with thousands of those joining the actual
internet. Remember, play FAIRLY and HONESTLY and this will really
work!
ALSO REMEMBER*** : : SEND YOUR $1 OUT
TO EVERYONE ON THE LIST, : : EVEN
IF THEY ARE NOT FROM THE U.S. : :

---

### Post by crimesaucer on 2008-10-12
> **Jordan777 said:**
> No, I'm just on my desktop.  I'm having some interesting problems though.  At first I tried to install Arch and I got an error where it wouldn't load or something like that.  So I went back and just redid it because it wouldn't hurt to just repartition the drives.  Every time after that I kept getting a grub 15 error at boot.  So I redid it a couple of times again.  Now I've gotten it to the point where grub will load and arch will load but here seems to be the problem.  Arch loads but I'm just at a console basically just as if I was installing it again.  Also in the grub boot menu my Windows XP isn't even shown.  Just Arch Linux and Arch Linux Fallback.  I'm gonna continue to read on to see if I have to enable the GUI for Arch but if I'm unsuccessful I'm gonna have to uninstall it for now just so I can continue using my computer.

I ended up just using two partitions for Arch.
sda1 Windows XP
sda2 / (12GB)
sda3 /home (remainder)

Before I tried setting up a /boot partition and I kept getting the grub 15 error so I don't know what that was about. 

Also since I'm very new I basically don't change anything in the configuration files.  That may be against the Arch way but just getting this distro up and running would be a great leap for me right now.  I'm not super concerned with editing out that one function that doesn't really need to be there.  Also since I use dhcp there's nothing except for one line in defining eth0="dhcp" that needs to be changed.

Maybe you guys can give me help or maybe not.  I'm still hoping for the best.  I'm off to read the Arch guide now to see if the console is normal or if I messed up yet again.  :-k

If you read that OLD GUIDE that I linked you to, you are only half-way through your install....


I assume, that you finished your install to the point where it told you to remove the install CD and reboot, then you did that, logged in through GRUB, and then was greeted with a console screen.


As for your windows not showing in GRUB, you need to remove the comments ( "#" ) from in front of your windows list (to look like the Arch parts).... you'll find that in /boot/grub/menu.lst and you need to edit that as root. (you can use nano)


log in as root, then:
```
nano /boot/grub/menu.lst
```

.... and make the bottom windows part look like the Arch part above, like this:

```

# (4) Windows
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

```


As for where you might be: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7)


read from there to create a user, install xorg, detect your hardware, install gnome, and then start from a bare-bones install.

---

### Post by Jordan777 on 2008-10-12
Ah so it seems like I still have configuring to do but other wise I have been successful so far.  I believe.  My problem though is that I have a realtek 8187 integrated card (ASUSM2N-32 Sli mobo) and I need to now figure out how to get this installed so I can continue.  Otherwise I might just be out of luck.  Also if anyone has a way for me to be able to see windows xp from grub that would be cool.  I can get to the config file using an Ubuntu Live CD but I can't edit it because I'm not root and I don't know if I can set myself up as root on the Live CD.  :-s

I know I'm having a lot of problems and maybe this wasn't the right distro for me but I really want to finish what I started.  You guys have been awesome and I really appreciate all the help you've given me thus far.  But if you're all tired and want to get on with your lives no one could blame ya. :lolflag:

---

### Post by crimesaucer on 2008-10-12
> **Jordan777 said:**
> Ah so it seems like I still have configuring to do but other wise I have been successful so far.  I believe.  My problem though is that I have a realtek 8187 integrated card (ASUSM2N-32 Sli mobo) and I need to now figure out how to get this installed so I can continue.  Otherwise I might just be out of luck.  Also if anyone has a way for me to be able to see windows xp from grub that would be cool.  I can get to the config file using an Ubuntu Live CD but I can't edit it because I'm not root and I don't know if I can set myself up as root on the Live CD.  :-s

I know I'm having a lot of problems and maybe this wasn't the right distro for me but I really want to finish what I started.  You guys have been awesome and I really appreciate all the help you've given me thus far.  But if you're all tired and want to get on with your lives no one could blame ya. :lolflag:


You have been successful so far, you just need to create your username and password, and then install an actual Desktop Environment and X.


As for the rtl 8187, it is already in your Arch kernel and should be easily detected: 

[http://wiki.archlinux.org/index.php/Wireless#rtl8187](http://wiki.archlinux.org/index.php/Wireless#rtl8187)
[http://wiki.archlinux.org/index.php/Rtl8187_wireless](http://wiki.archlinux.org/index.php/Rtl8187_wireless)

---

### Post by SomeGuyDude on 2008-10-12
My man, it's gotten to the point where I put Arch on my machine every weekend, use it for two days, go back to Ubuntu, and repeat. I'm always asking for help and that's the beautiful thing about Linux: the community.

---

### Post by crimesaucer on 2008-10-12
> **Jordan777 said:**
> "..... Also if anyone has a way for me to be able to see windows xp from grub that would be cool.  I can get to the config file using an Ubuntu Live CD but I can't edit it because I'm not root and I don't know if I can set myself up as root on the Live CD.  :-s....."

Just log in as root on that console screen:

```
root
```


Then enter your password that you created during the install CD.


then run this command:

```
nano /boot/grub/menu.lst
```


make it look like this:

```

# (0) Windows
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

```


then save it like this:

```
ctrl + o
```

then YES or Y to rewrite /boot/grub/menu.lst

then press:

```
ctrl + x
```

to exit nano..... now your Xp should be able to be booted into, even if you haven't finished installing xorg, gnome, or your Arch user name.

---

### Post by Rumor on 2008-10-12
> **Jordan777 said:**
> So I redid it a couple of times again.  Now I've gotten it to the point where grub will load and arch will load but here seems to be the problem.  Arch loads but I'm just at a console basically just as if I was installing it again.  Also in the grub boot menu my Windows XP isn't even shown.  Just Arch Linux and Arch Linux Fallback.  I'm gonna continue to read on to see if I have to enable the GUI for Arch but if I'm unsuccessful I'm gonna have to uninstall it for now just so I can continue using my computer.

[COLOR="Cyan"]<snip>[/COLOR]

I'm off to read the Arch guide now to see if the console is normal or if I messed up yet again.  :-k

Nope, the command prompt login is normal, as I am sure you are aware by now. 

Arch has no default GUI. You'll have to install whatever desktop environment or window manager you want to use.

Where you are at it sounds like you need to 
[LIST]
[*]login as root
[*]pacman -Syu to bring your system up to date
[*]pacman -S xorg (insert favorite DE or WM)
[*]create your user
[*]configure your X
[*]start X and login as your user and begin configuring things the way you like them.
[/LIST]

You're almost there, don't give up now!

---

### Post by crimesaucer on 2008-10-12
> **Rumor said:**
> Nope, the command prompt login is normal, as I am sure you are aware by now. 

Arch has no default GUI. You'll have to install whatever desktop environment or window manager you want to use.

Where you are at it sounds like you need to 
[LIST]
[*]login as root
[*]pacman -Syu to bring your system up to date
[*]pacman -S xorg (insert favorite DE or WM)
[*]create your user
[*]configure your X
[*]start X and login as your user and begin configuring things the way you like them.
[/LIST]

You're almost there, don't give up now!

Yes, you are here: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7)


ignore this part:

# cd /etc/pacman.d
#pwd
/etc/pacman.d
#ls
community current extra release unstable


because pacman uses "1" mirrorlist instead of "5" different mirror files like it did last year (this is one of the OLD parts to this guide).

just:

```
nano /etc/pacman.d/mirrorlist
```


and un-comment (remove the # signs) from the ftp mirror locations that you want to use.


Also, what is you graphics card..... because if it's nvidia, I have different instructions for you..... otherwise just continue with the rest of the guide because everything else is basically the same..... gdm..... all of that.

---

### Post by Jordan777 on 2008-10-12
Okay I got my grub redone this morning.  I still need to continue with Arch I just need to do it hopefully somewhat quickly as I have a lot of homework to finish by the end of today.  I have an Nvidia 8800GTS 320MB.

---

### Post by crimesaucer on 2008-10-12
> **Jordan777 said:**
> Okay I got my grub redone this morning.  I still need to continue with Arch I just need to do it hopefully somewhat quickly as I have a lot of homework to finish by the end of today.  I have an Nvidia 8800GTS 320MB.

Since you have Nvidia, and it is supported: [ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/README/appendix-a.html)

..... you are going to want to install xorg like this:

1.) create your user account like the guide
2.) un-comment your mirrorlist like I said above
3.) do a full upgrade with this command:

```
pacman -Syu
```


then do this differently for Nvidia:

1.) install xorg and xterm:

```
pacman  -S  xorg  xterm
```

2.) install nvidia and nvidia-utils:

```
pacman  -S  nvidia nvidia-utils
```

now what I do is I use nvidia-xconfig instead of Xorg -configure

look at this wiki: [http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)

now create your XF86Conf instead of a xorg.conf:

```
nvidia-xconfig
```


or if you plan to use compiz-fusion:

```
nvidia-xconfig --composite
```


..... these 2 commands above should detect your harware, create a XF86Conf which is just like a xorg.conf, and it will create the file in the proper directory of /etc/X11/XF86Conf (just incase you need to edit it).


now run this command to see if your Xwindows system works:

```
startx
```


if your NVIDIA splash screen appears and then three terminal of xorg, then it worked..... just run this command in one of your terminals:

```
reboot -n
```


Now, login as root again, and then install gnome or xfce4, don't forget to add gdm and configure it with your ~/.xintrc file.


..... just read the beginners guide and the OLD GUIDE I linked you to.

---

### Post by Jordan777 on 2008-10-15
Mkay so everything went well so far but now I can't seem to get pacman -Syu to do anything.  I added a new user (myself) and got my wireless connected.  When I enter ```
pacman -Syu
``` I just get a Transient Resolver failure and a failure to synchronize database errors.  Anyone have any suggestions?  Oh and I already unchecked all of the mirrors on the mirrorlist.  It just goes through all of them giving the same error.  

Also I saw in one of the guides that after running ```
pacman -Syu
``` they go on to set up sudo and alsa is this recommended or should I just continue on with what you said?

---

### Post by SkonesMickLoud on 2008-10-15
> **Jordan777 said:**
> Mkay so everything went well so far but now I can't seem to get pacman -Syu to do anything.  I added a new user (myself) and got my wireless connected.  When I enter ```
pacman -Syu
``` I just get a Transient Resolver failure and a failure to synchronize database errors.  Anyone have any suggestions?  Oh and I already unchecked all of the mirrors on the mirrorlist.  It just goes through all of them giving the same error.  

Also I saw in one of the guides that after running ```
pacman -Syu
``` they go on to set up sudo and alsa is this recommended or should I just continue on with what you said?

Are you running *pacman -Syu* as root?

Sudo is entirely optional, as is setting up ALSA.  I personally find it easy, as I just set it up to not ask fo a password and set it within a bunch of aliases.  Both can be setup later if you need/want them.

---

### Post by Jordan777 on 2008-10-15
Yeah I'm running as root.  I wonder if it's my wireless connection?  I sure hope not cause it says it's connected.  At least ```
iwconfig wlan0
```tells me it is after I connected to my network.


EDIT****

Whoops!  I forgot to run ```
dhcpcd wlan0
```

It's updating now.  Man... I'm missing the debates doing this but it sounds like they are both saying the same things.  But that's just because they are asking the same questions.

---

### Post by SomeGuyDude on 2008-10-15
You missed McCain taking constant potshots on Obama about ACORN and taxes, that's about it. Schieffer was a great mod, but it was really annoying watching McCain interrupt Obama constantly. He looked like a child.

Got your Arch set up, then? If you need a wireless client, Wicd is tops.

---

### Post by Jordan777 on 2008-10-15
That's all he's been doing really.  I can't believe so many people are supporting him out of ignorance.  It's really frightening.  They don't have to vote for Obama if they really dislike his policies (most of them just don't want to vote for him because they are ignorant) but voting for McCain is just going to kill the country.

So anyways, I'm still getting the same problem.  This is really strange.  I'm gonna see if enabling all of the US mirrors will do something.  Most likely not though.  I tried to ping google.  It worked the first time but then when I ran pacman it wouldn't work so I had to reboot.  Now I still get my ip address using dhcpcd but this time when I pinged google I got a bad packet message.  Grr.  This really sucks.

---

### Post by Jordan777 on 2008-10-15
Okay.  I just enabled all of the mirrors on the list.  Now everything is going just fine.  I skipped the alsa and sudo options.  I can configure those later I'm sure.  Now I'm just working on running ```
pacman -S xorg xterm
```this might take a while to download...

Edit*

Okay so I followed these steps

```
pacman -syu
```

```
pacman -S xorg xterm
```

```
pacman -S nvidia nvidia-utils
```

Now after this last command I get the following output and I don't know what to do from here.

error:failed to prepare transaction (could not satisfy dependencies) ::ndiswrapper:requires kernel26<2.6.26

---

### Post by handy on 2008-10-16
I've been having similar trouble with Arch & the internet also. On the iMac, the one that works! :lolflag:

Costing me a lot of time to go nowhere, its been a tough couple of days with Arch for me.

A new kernel came into the Arch repo's today, it may or may not be causing problems...

Time will tell.

---

### Post by crimesaucer on 2008-10-16
> **handy said:**
> I've been having similar trouble with Arch & the internet also. On the iMac, the one that works! :lolflag:

Costing me a lot of time to go nowhere, its been a tough couple of days with Arch for me.

A new kernel came into the Arch repo's today, it may or may not be causing problems...

Time will tell.

There seem to be a bunch of issues with the 2.6.27 kernel..... I just went through a bunch of other stuff myself..... I screwed up my X server with a compiz ccsm plugin that made my screen really slow and choppy..... the graphics turned to crap.


So, I thought to myself, "Hmm, why not try the new xorg in testing?"...... next thing I know, I have a totally botched upgrade with all the testing packages..... so then I try to downgrade as many packages back to the normal release versions while removing my testing packages..... the only problem is that I use pacbuilder to build all my packages from source, so now I have no idea how many testing packages I installed, and I can't just go back to /var/cache/pacman/pkg to pacman -U them back into use....


Well, I had a list of about half of them written down, so I at least got my computer back to a working level..... but it was still slow with that compiz/X bug..... I sort of figured out it was the blur effect, I fixed it, but it still kept resurfacing.....


I also kept getting a strange error for my network.... it seems they upgraded something with either dhcp or dhcpcd or something else that conflicts now with the -R argument for dhcpcd..... anyway, when I was messing around with that, I errased something important, I ruined my eth0 Internet connection, and was unable to re-connect to fix it.....


So, I just decided to save my important files, and then start over with a fresh install.


This is how much time an Arch install took me when rebuilt from source:


- regular FTP install was less than one hour, with the basic packages and a few settings configured.

- pacbuilder recompiling 411 packages (probably only 300 of them successfully) from source = 24 hours (with a sleep break)

- additional compiz-fusion and other things like firefox-optimized built from source using pacbuilder was another few hours (also patched xfce4-panel and other customizations)

..... and my system is almost back to the way it was when I was happy with it. I probably have another day of building packages and configuring everything the way I had it.


Anyway, if you followed this guide here like I did: [http://wiki.archlinux.org/index.php/Post_Installation_Tips#Configure_dnsmasq](http://wiki.archlinux.org/index.php/Post_Installation_Tips#Configure_dnsmasq)

and had this:

```
 DHCPCD_ARGS="-t 30 -h $HOSTNAME -R"

```

I just took away the -R argument to get an Internet connection.


As for the 2.6.27 kernel, mine boots up and works decently except for when I take the AC adapter out, then it won't boot up or shutdown..... so I went back to my 2.6.26 zen2 kernel.

---

### Post by Jordan777 on 2008-10-16
Even though I ran ```
pacman xorg xterm
```  I wonder if I can just follow [this]("http://wiki.archlinux.org/index.php/NVIDIA#How_to_install_Nvidia_Driver_with_pacman") guide from here on?  Or does anybody know how I can continue on with installing my video card drivers without breaking anything?

---

### Post by handy on 2008-10-16
> **crimesaucer said:**
> 
There seem to be a bunch of issues with the 2.6.27 kernel..... I just went through a bunch of other stuff myself..... I screwed up my X server with a compiz ccsm plugin that made my screen really slow and choppy..... the graphics turned to crap. 

I'm very much caught up in this problem at the moment, with two machines, one that's done its initial installation upgrade & lost the internet & the other which I just happened to do an -Syu & also catch the new kernel & its problems.  It is times like these I am glad that I have Leopard, as I hardly use it, don't really like it, don't mess with it, so it doesn't break on me. :lolflag:

> **crimesaucer said:**
> 
So, I thought to myself, "Hmm, why not try the new xorg in testing?"...... next thing I know, I have a totally botched upgrade with all the testing packages..... so then I try to downgrade as many packages back to the normal release versions while removing my testing packages..... the only problem is that I use pacbuilder to build all my packages from source, so now I have no idea how many testing packages I installed, and I can't just go back to /var/cache/pacman/pkg to pacman -U them back into use.... 

Ow!  I'm glad I could just look at the pacman.log & use pacman -U to downgrade, even though it didn't help me! :confused:

> **crimesaucer said:**
> 
I also kept getting a strange error for my network.... it seems they upgraded something with either dhcp or dhcpcd or something else that conflicts now with the -R argument for dhcpcd..... anyway, when I was messing around with that, I errased something important, I ruined my eth0 Internet connection, and was unable to re-connect to fix it.....


You are lucky that the removal of the -R worked for you, it doesn't for most, from what I have read on the Arch forums.

From what you have written about your installation, you seem to have turned a binary Arch install into a compiled one like Gentoo... :lolflag:

---

### Post by crimesaucer on 2008-10-16
> **Jordan777 said:**
> Even though I ran ```
pacman xorg xterm
```  I wonder if I can just follow [this]("http://wiki.archlinux.org/index.php/NVIDIA#How_to_install_Nvidia_Driver_with_pacman") guide from here on?  Or does anybody know how I can continue on with installing my video card drivers without breaking anything?

You can type this all at once like this:

```
pacman -Sy xorg xterm nvidia nvidia-utils
```


You can then configure your xorg.conf:

```
nvidia-xconfig --composite
```


then check to see if it worked:

```
startx
```


- If it works it will show the "nvidia splash", then 3 terminal boxes (blueish/greenish window decorations), type in the terminal with the blinking cursor: "reboot -n"


- If it didn't work (no "nvidia-splash", no xorg xterms), then you might need help with detecting your hardware.


If it worked then it reboots back to the Grub login (you choose it), then it boots to "console login": you type Root, then password,


next install gnome with:


```
pacman -Sy gnome  gnome-extra gnome-system-tools  xscreensaver aspell-en
```


then edit your DAEMONS line of your /etc/rc.conf:


```
DAEMONS=(syslog-ng network netfs crond portmap fam dbus hal !avahi-daemon)
```


then edit your /etc/inittab from this:


```

id:3:initdefault:

```

to 

```

id:5:initdefault:

```


and then this section from this:


```

x:5:respawn:/usr/bin/xdm -nodaemon

```

to this

```

x:5:respawn:/usr/sbin/gdm -nodaemon

```


..... then exit the Root console:

```
exit
```


now login to the "USER" console (your user name):

then type this:

```
nano .xinitrc
```


and add this on the blank page:

```
exec gnome-session
```

save with ctrl + o, enter, ctrl + x


then exit:


```
exit
```


now press ctrl + alt + delete to reboot and go to GDM then gnome login.



All of this is covered here: [http://www.raiden.net/?cat=2&aid=276&pid=9](http://www.raiden.net/?cat=2&aid=276&pid=9)

---

### Post by crimesaucer on 2008-10-16
> **handy said:**
> "..... I am glad that I have Leopard, as I hardly use it, don't really like it, don't mess with it, so it doesn't break on me. :lolflag:..."

I have a Vista partition for the same reason, I keep a backup of all my important Archlinux files on that partition so I can easily re-install my old configurations and custom kernels/scripts/wallpapers/themes....



> ".....Ow!  I'm glad I could just look at the pacman.log & use pacman -U to downgrade, even though it didn't help me! :confused:...."

The pacbuilder app downloads all PKGBUILDS from either ABS or AUR, into a /tmp/pacbuilder/build/"package_name" directory, where it runs the PKGBUILD and other patches and install files from that /tmp folder, then, when it builds the package, it installs it and then erases the /tmp folder..... so I have no backup packages after it get's installed..... so no old version to fall back to..... I should try to see if I can change the build location or make it not erase the "package_nam.tar.gz".



> "..... You are lucky that the removal of the -R worked for you, it doesn't for most, from what I have read on the Arch forums...."


I still get an error during boot about a "write file", but at least the Internet connection works..... maybe it's because I used the FTP install where it did an automatic DHCP connection of my Internet.


> "..... From what you have written about your installation, you seem to have turned a binary Arch install into a compiled one like Gentoo... :lolflag:....."


Yes, that is what I was going for. I'm really liking the performance of it. It's a lot of work to lose on bad update and some of my own user errors.... but when it's working good (like right now) it's nice to use.

---

### Post by handy on 2008-10-16
***@crimesaucer:***  I just very carefuly did another downgrade on the iMac, rebooted & I now look to have fully functioning internet.

I must have been brain addled yesterday when I downgraded, missing something.  Probably due to the big day before dealing with the problem on a fresh Arch install.

Anyway, now I will have a look at the machine that is stuck pre X install with my new found knowledge & see if I can copy my .../pacman/pkg contents onto a DVD & salvage the situation that way.

When problems strike is when I learn the most. :lolflag:  Tough that I need a problem to motivate me.

---

### Post by crimesaucer on 2008-10-17
> **handy said:**
> ***@crimesaucer:***  I just very carefuly did another downgrade on the iMac, rebooted & I now look to have fully functioning internet.

Cool.

> ".....I must have been brain addled yesterday when I downgraded, missing something.  Probably due to the big day before dealing with the problem on a fresh Arch install....."

Or they fixed something important in the last Oct.15/16 updates.


> ".....When problems strike is when I learn the most. :lolflag:...."

I learn through my mistakes too, I try to learn without causing breakages, but sometimes a broke computer can make you have to learn new things about Linux..... this last mistake of mine made me learn that I like the -Os customization more than the -O2 setting.


These C[XX]FLAGS that I tried on this new install are feeling much better. I also, lightened my compiz-effects to avoid that bug I had, and I tried using the default nvidia settings (other than the highest quality setting)..... and everything is feeling better than my last install.

---

### Post by Jordan777 on 2008-10-17
Thanks crimesauce.  I'm gonna try all that when I get some free time this weekend.  I'll update with a story of success or questions that I have later on should I fail or run into problems.

---

### Post by handy on 2008-10-17
> **crimesaucer said:**
> 
Or they fixed something important in the last Oct.15/16 updates. 

No, they haven't fixed anything yet.  

I don't know whether the solution will come from upstream as a patched kernel, or whether a patch will become available in the Arch repo's?

> **crimesaucer said:**
> 
I learn through my mistakes too, I try to learn without causing breakages, but sometimes a broke computer can make you have to learn new things about Linux..... 

The mistake that made me do most of the work was not mine this time (unusually :lolflag:)  Though I did have to repeat some stuff due to having missed something in the downgrade process.

It was the kernel problem that caused all my troubles on both machines, I have verified that by downgrading the kernel & the few dependent files on both.  This is good.  I'll wait until there is a fix before I continue with the install on my 2nd box.  I don't want anything out of place when I install X, it is the most dangerous part of the install from my experience.  Though I have put the xorg.conf from the previous install on my install disk, & emailed to myself as well.  It took me a good 20 hours to sort out my graphic card from hell the first time I installed Arch on that machine.  Due to the GPU being designed for PCI-X & the makers engineering it into an AGP card, I eventually found that I had to turn off AGP in the xorg.conf to get the card to accept the nVidia drivers & function properly.

This is my theory as to why I had to turn AGP off, I may of course be dead wrong. :lolflag:

---

### Post by MisfitI38 on 2008-10-17
> **handy said:**
> 
I don't know whether the solution will come from upstream as a patched kernel, or whether a patch will become available in the Arch repo's?

No, I don't think Arch will patch a kernel. The bug report needs to be filed upstream, to the kernel monkeys.
handy, if you find a link to an existing bug report, link me up; I have been swamped with work and will not have a chance to find one until after the weekend..
My gut feeling is that a fix is in the works from upstream and will arrive in the [core] repo as 2.6.27-x
Though, I could also be dead wrong; there's always a chance that you and I are among a minuscule minority, among whom no one has filed a bug report.. ;)

---

### Post by crimesaucer on 2008-10-17
Yeah, I downgraded to my 2.6.26 zen2 kernel until they make some fixes for the ACPI issues I've had.....


I found that the updated dhcpcd has changed in an unfavorable way also. I'm also waiting for a fix for that so it doesn't erase my /etc/resolv.conf that had my dnsmasq lo address and my OpenDNS nameservers. (the -R command no longer works..... having no dnsmasq and no OpenDNS servers make my Internet much slower)


> ".....The mistake that made me do most of the work was not mine this time....."

Yes, the Arch forums (kernel issues and pacman upgrade sections) are full of posts about this recent upgrade..... I didn't make any threads because I was at fault for my own problems..... which I kept ruining by trying to fix them with out asking for any help..... but as for the 2.6.27 kernel, I've been messing around with the 2.6.27 rc1-rc7 zen kernels for the last couple of months, and I've had the same ACPI issues with all of them..... including this new -ARCH stock kernel.


I had originally thought that I had built/compiled the zen patched 2.6.27 rc1 - rc7 kernels wrong..... because all of them would not boot/shutdown without the AC adapter plugged in..... but then I had the same issue with the Arch stock kernel that I installed as a regular binary..... so it must be something else that makes the new 2.6.27 kernels not boot/shutdown with my battery power on my HP Pavilion dv9920us. (works good as long as the AC adapter is plugged in)

---

### Post by MisfitI38 on 2008-10-17
> **crimesaucer said:**
> 
I found that the updated dhcpcd has changed in an unfavorable way also. I'm also waiting for a fix for that so it doesn't erase my /etc/resolv.conf that had my dnsmasq lo address and my OpenDNS nameservers. (the -R command no longer works..... having no dnsmasq and no OpenDNS servers make my Internet much slower)

Try ```
DHCPCD_ARGS="-t 30 -h $HOSTNAME -C resolv.conf"
```

---

### Post by crimesaucer on 2008-10-17
> **MisfitI38 said:**
> Try ```
DHCPCD_ARGS="-t 30 -h $HOSTNAME -C resolv.conf"
```

Thanks, I'll give it a try.

---

### Post by crimesaucer on 2008-10-17
> **crimesaucer said:**
> Thanks, I'll give it a try.

It didn't work for me. Thanks anyway.

---

### Post by cardinals_fan on 2008-10-17
> **crimesaucer said:**
> 
I found that the updated dhcpcd has changed in an unfavorable way also. I'm also waiting for a fix for that so it doesn't erase my /etc/resolv.conf that had my dnsmasq lo address and my OpenDNS nameservers. (the -R command no longer works..... having no dnsmasq and no OpenDNS servers make my Internet much slower)

I actually have an answer for this one!  Save the resolv.conf file the way you like it somewhere (in /root, say) and add a line in /etc/rc.local to copy it to /etc.

---

### Post by crimesaucer on 2008-10-17
> **crimesaucer said:**
> It didn't work for me. Thanks anyway.


Oops.... My bad.... I had it written like this:

```
DHCPCD_ARGS="-q -L -t 30 -h $HOSTNAME -C resolv.conf"
```

when it needs to be:

```
DHCPCD_ARGS="-t 30 -h $HOSTNAME -C resolv.conf"
```


See, the new way it is written in the /etc/conf.d/dhcpcd before editing is like this:

```
DHCPCD_ARGS="-q -L -t 30 -h $HOSTNAME"
```

.... so I figured all I had to do was add the -C resolv.conf to the end of it.... I was wrong. Thanks for the tip.

Also, thanks cardinals_fan for the backup tip.

---

### Post by Jordan777 on 2008-10-19
So.  I just reinstalled Arch because I got stuck and figured I'd just start from scratch.  Now I have a weird problem.  I find myself entering ```
iwconfig wlan0 essid (my network) key (my key)
``` but then I get an error saying that bash doesn't recognize iwconfig...  What!?  What does it mean it doesn't recognize the command that's supposed to work?  :)  I'm just stumped now.

---

### Post by SomeGuyDude on 2008-10-19
> **crimesaucer said:**
> 64bit Flash plugin was super easy with this guide: [http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64](http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64)


For 64bit Java plugin use Openjdk "icedtea": [http://www.archlinux.org/packages/extra/x86_64/openjdk6/](http://www.archlinux.org/packages/extra/x86_64/openjdk6/) 


My 64bit Arch has always worked good.



Also some more Arch64 info: 

[http://wiki.archlinux.org/index.php/Category:Arch64_(English](http://wiki.archlinux.org/index.php/Category:Arch64_(English))
[http://wiki.archlinux.org/index.php/Arch64_FAQ](http://wiki.archlinux.org/index.php/Arch64_FAQ)

Update. Arch64: rolling along just fine. Extra RAM usage that I don't particularly like, but apparently that's just a part of using the 64-bit system. I'm unsure about how I like that, and if it's affecting battery life (it seems that it doesn't last QUITE as long...), but otherwise no issues. Thanks for the nudge!

---

### Post by handy on 2008-10-19
> **crimesaucer said:**
> 64bit Flash plugin was super easy with this guide: [http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64](http://wiki.archlinux.org/index.php/Install_Flash_on_Arch64)


For 64bit Java plugin use Openjdk "icedtea": [http://www.archlinux.org/packages/extra/x86_64/openjdk6/](http://www.archlinux.org/packages/extra/x86_64/openjdk6/) 


My 64bit Arch has always worked good.



Also some more Arch64 info: 

[http://wiki.archlinux.org/index.php/Category:Arch64_(English](http://wiki.archlinux.org/index.php/Category:Arch64_(English))
[http://wiki.archlinux.org/index.php/Arch64_FAQ](http://wiki.archlinux.org/index.php/Arch64_FAQ)

Having recovered my iMac from my recent Arch troubles I have got my new xfce4 set up pretty much done.  

So when I saw SomeGuyDude's previous post, I decided it's about time I got Flash (in particular) & Java working on my 64bit install.

So I went through the two how-to's that crimesaucer provided links for without any problems, but I still can't watch a google or u-tube video.


Apart from installing windows Firefox under Wine. :twisted:
Does anyone have any wisdom to impart on the subject?

[I]**[Edit:]**

I saw this code:

**nspluginwrapper -v -a -i**

happening at the end of the install, so I thought that it was ok, any way it obviously wasn't ok, because after I ran it manually I got flash working.  8-)[/I]

---

### Post by doorknob60 on 2008-10-19
I used Arch64, and all was working good, then something happened and some of my 32 bit OpenGL using apps broke (Java and Wine), although it's weird because FoF Alarian Mod x86 binary and Googe Earth still worked fine. Java couldn't load OpenGL, making Runescape HD unplayable, and it didn't fix itself with a reinstall. I honestly have no clue what happened, because they just suddenly stopped working, but I'm on Arch 32 right now. Anyways, give 64 a shot first.

---

### Post by Jordan777 on 2008-10-19
Okay well does anybody have an answer to my previous question?  It's kinda necessary for me to even begin downloading packages and continuing with my installation.  I enter iwconfig esside my network key my network key but bash just returns an error saying iwconfig isn't a recognized command.  Can anyone explain that to me?

---

### Post by handy on 2008-10-19
> **doorknob60 said:**
> I used Arch64, and all was working good, then something happened and some of my 32 bit OpenGL using apps broke (Java and Wine), although it's weird because FoF Alarian Mod x86 binary and Googe Earth still worked fine. Java couldn't load OpenGL, making Runescape HD unplayable, and it didn't fix itself with a reinstall. I honestly have no clue what happened, because they just suddenly stopped working, but I'm on Arch 32 right now. Anyways, give 64 a shot first.

Mysterious breakages are the hardest to fix eh!?

I've been using 64bit Arch on both machines since early in the year, I usually use 64bit of whatever distro' I install, especially since being able to play Guild Wars & Oblivion on 64bit became easy. :)

> **Jordan777 said:**
> Okay well does anybody have an answer to my previous question?  It's kinda necessary for me to even begin downloading packages and continuing with my installation.  I enter iwconfig esside my network key my network key but bash just returns an error saying iwconfig isn't a recognized command.  Can anyone explain that to me?

Sorry, I can't help you I avoid wireless like the plague.

---

### Post by crimesaucer on 2008-10-19
> **Jordan777 said:**
> Okay well does anybody have an answer to my previous question?  It's kinda necessary for me to even begin downloading packages and continuing with my installation.  I enter iwconfig esside my network key my network key but bash just returns an error saying iwconfig isn't a recognized command.  Can anyone explain that to me?

Make sure you have the wireless_tools package installed: [http://www.archlinux.org/packages/core/x86_64/wireless_tools/](http://www.archlinux.org/packages/core/x86_64/wireless_tools/)

You can check if you have it installed with:

```
pacman -Q wireless_tools
```

if you don't have it installed, then install it with:

```
pacman -Sy wireless_tools
```


then iwconfig and iwlist should work..... During and install, they offer the wireless_tools in the development section, along with ntfs-3g and ndiswrapper and other tools people might need to get there install working correctly.

More info on wireless_tools: [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html)

---

### Post by Jordan777 on 2008-10-19
Thanks crimesaucer!  Do you know if I can just install the wireless tools from my arch install cd without redoing my install from scratch?  Aw, never mind.  It only takes a few minutes to go through the whole cd anyways.  Thanks again crimesaucer.

Edit*

So this is just ridiculous.  I got my wireless connection up but now when I attempt to update I get the old transient resolver error.  *sigh*  I fix one thing and then another problem just springs up.  I have no idea what to do anymore.  It seems as if the forces of nature and technology wish for me to never use ArchLinux.

---

### Post by crimesaucer on 2008-10-19
> **Jordan777 said:**
> Thanks crimesaucer!  Do you know if I can just install the wireless tools from my arch install cd without redoing my install from scratch?  Aw, never mind.  It only takes a few minutes to go through the whole cd anyways.  Thanks again crimesaucer.


Only if you have a working Internet connection, which I'm assuming that you don't. If you have a eth0 wired connect to use, then you could use pacman to install anything from a console screen.....


When you get to the part about installing the core packages, and you toggle it with a "*", then the next question is if you want to install any dev packages, click yes "*", and then look for wireless_tools on the list and toggle it with a "*".


If your wireless card is easily recognized, you could use the Arch FTP install (an option on the live CD), and it would configure your wireless network for you automatically at the very beginning of the install. Then you will have a working Internet connection, and if it doesn't work then just log out and use the other HTTP install option.

---

### Post by Jordan777 on 2008-10-19
I don't know what the problem is exactly.  I can connect to my network and get an IP address in order to connect to the web.  But I've only ever gotten the mirrors to work once and I had to reinstall because something went wrong.  Now I try to update and I just get a transient something error.  Basically it's trying to find the servers but it can't.  This is just stupid.  I really wish I had wired internet.  Wireless seems to be so much trouble sometimes.

---

### Post by crimesaucer on 2008-10-19
> **Jordan777 said:**
> I don't know what the problem is exactly.  I can connect to my network and get an IP address in order to connect to the web.  But I've only ever gotten the mirrors to work once and I had to reinstall because something went wrong.  Now I try to update and I just get a transient something error.  Basically it's trying to find the servers but it can't.  This is just stupid.  I really wish I had wired internet.  Wireless seems to be so much trouble sometimes.

Did you use the "dhcpcd wlan0" command like the last time you got it to connect, before your upgrade with "pacman -Syu"? 


And like I said before, if you use the FTP install, it will do an automatic configuration of your Internet (wired or wireless), then it will save the settings, and you can use the Internet the way it was configured from the FTP install.

---

### Post by Jordan777 on 2008-10-19
Yup I did dhcpcd wlan0.  It's just giving me errors from trying to update.  It's not the configuration of my wireless.  That's easy enough to do.  It's just getting the connection to the servers through.  I don't know.  Maybe that does mean that it's not being connected properly but I've done it before and it's worked.

---

### Post by handy on 2008-10-20
Jordan, what kernel version are you running, have you done a pacman -Syu in the last few days?

If so you just may be suffering from what I'm calling the kernel bug, that comes with the latest kernel.  It interferes with internet connection in a variety of ways.

This thread on the Arch forum will give you an idea of how this bug is affecting some of us:

***_[http://bbs.archlinux.org/viewtopic.php?id=57102](http://bbs.archlinux.org/viewtopic.php?id=57102) _***

---

### Post by Sorivenul on 2008-10-20
Also, have you actually set up your mirrorlist (/etc/pacman.d/mirrorlist)?  I've never been able to set a mirror during the actual install and this is always my first step.  I got your "transient resolver failure" or whatever that you are experiencing before I uncommented the mirrors I wished to use.  Good luck!

---

### Post by handy on 2008-10-20
I think the mirrorlist is created when you first run pacman, which is a bit strange to my mind, as I do a core install off the CD, & doing it that way your initial upgrade is done at a 50k limited speed from the Arch server.  Then after you have done that you can sort out your mirrorlist.

That's my understanding of it.  If I installed Arch often enough I think I would find a way around that speed limiting problem.

---

### Post by crimesaucer on 2008-10-20
> **handy said:**
> I think the mirrorlist is created when you first run pacman, which is a bit strange to my mind, as I do a core install of the CD, & doing it that way your initial upgrade is done at a 50k limited speed from the Arch server.  Then after you have done that you can sort out your mirrorlist.

That's my understanding of it.  If I installed Arch often enough I think I would find a way around that speed limiting problem.

If you use the FTP install, it let's you pick a mirror (other than the default Arch one that is slow), then after the install, you need to edit the /etc/pacman.d/mirrorlist and remove all of the comments in front of your preferred mirrors.... I just choose the U.S and Canada ones. (and I leave the Arch one commented out)

---

### Post by crimesaucer on 2008-10-20
> **handy said:**
> If I installed Arch often enough I think I would find a way around that speed limiting problem.

FTP install with a good mirror is almost like doing a pacman -Syu..... super fast, and then you don't have to update after the install becasue you already get the newest version of every app.

---

### Post by handy on 2008-10-20
> **crimesaucer said:**
> FTP install with a good mirror is almost like doing a pacman -Syu..... super fast, and then you don't have to update after the install becasue you already get the newest version of every app.

It sounds like the quickest way to go.

---

### Post by mips on 2008-10-20
> **crimesaucer said:**
> FTP install with a good mirror is almost like doing a pacman -Syu..... super fast, and then you don't have to update after the install becasue you already get the newest version of every app.

That's relative to you internet connection speed. For me it takes way longer than using the cd. I do however use the FTP install though.

Simple reason being I'm going to have to do a update anyway so I might as well install via FTP.

Generally I would not recommed FTP install to new users using wireless internet access.

---

### Post by Rumor on 2008-10-20
It's usually a pretty good idea to run rankmirrors after an install, then edit your mirror list to use only those to which you have a good connection.
```
rankmirrors -t /etc/pacman.d/mirrorlist
```

It doesn't hurt to ping the new mirrorlist too (/etc/pacman.d/mirrorlist.pacnew)

---

### Post by crimesaucer on 2008-10-20
> **mips said:**
> Generally I would not recommed FTP install to new users using wireless internet access.

True, but for a Ethernet connection to a T1 cable account, it's nice and fast.


I also think it's as easy to install with as the regular CD install..... the only difference is the very beginning, detecting the eth0 or wlan0 and selecting a close mirror. After that it's the same, plus you don't have to do another upgrade like you said. 


..... And it does one nice thing, it detects your connection and configures it for you if your hardware is easily recognized..... so for someone having the problems like Jordan777 is having, it might be a nice way of taking care of the wireless connection first, before doing anything else...... I think I remember that he has the rtl8187 module so it should be recognized.

---

### Post by Jordan777 on 2008-10-20
Woah, sorry guys.  Didn't see all this.  Well yeah I've edited my mirror list.  I've done it with all the US servers but that takes forever for it to go through all of them just to not work.  I've done it with just a couple from the US list...  It's really strange that it just doesn't work.  I don't really know what an FTP install would do for me other than what I've already done.  I'm using the latest Arch iso that's out as I only downloaded it like three weeks ago.  I go through the steps to connect my wireless card to my network.  It's just really strange that it gives me that error for every single server.  And I don't believe it's my NIC because I've actually gotten it to work before and I haven't done anything different.  I just had to repartition because something went wrong.  I think it started giving me the server error again so I thought maybe I'd done something wrong or something like that.

---

### Post by crimesaucer on 2008-10-21
> **Jordan777 said:**
> "..... I don't really know what an FTP install would do for me other than what I've already done....."  


This is what a FTP install would do differently for you:


1.) The VERY first thing a FTP install does is connect you to the Internet.... it scans your hardware, and if it recognizes your "rtl8187" wlan0 as being able to connect to your router, it will.


----- if it can't connect, it will tell you that it did not connect, then you have the choice to either try and configure it, or modprobe the correct modules. If you have no luck with that, then stop the install since it would be useless without a working Internet connection.



2.) If it was successful on detecting your card and loading your module, and connecting to your router/network, it will save your network configuration. 



3.) Then it will give you a choice of one FTP mirror to use for the download. Choose a close one.



4.) Then proceed with your install as usual..... the difference being:


That you already know that your Internet is connected, and will be able to download packages necessary for installing Arch (like gnome).


>  I go through the steps to connect my wireless card to my network.


If you try the FTP option (already on the iso CD), it will attempt to connect your wireless before doing anything else.... just try it, nothing else is working for you. This might be the best solution for now.

---

### Post by cardinals_fan on 2008-10-21
> **Jordan777 said:**
> I don't know what the problem is exactly.  I can connect to my network and get an IP address in order to connect to the web.  But I've only ever gotten the mirrors to work once and I had to reinstall because something went wrong.  Now I try to update and I just get a transient something error.  Basically it's trying to find the servers but it can't.  This is just stupid.  I really wish I had wired internet.  Wireless seems to be so much trouble sometimes.
What happens when you enter dhcpcd wlan0?  Do you get any errors?

---

### Post by Jordan777 on 2008-10-21
Nope no errors when I do dhcpcd wlan0.  Well maybe when I get some time I'll try the FTP install.  Probably this weekend as I just don't have several hours to blow during the week.

---

### Post by crimesaucer on 2008-10-21
> **Jordan777 said:**
> Nope no errors when I do dhcpcd wlan0.  Well maybe when I get some time I'll try the FTP install.  Probably this weekend as I just don't have several hours to blow during the week.

Seriously, the FTP install takes me about 40 minutes to 1 hour.... that's a full install with a desktop environment like xfce4, and a browser like Firefox.


If it doesn't work for you, you will know within the first 2 minutes.


Good luck.

---

### Post by Jordan777 on 2008-10-21
Ah in that case maybe I'll try it tomorrow or Wednesday.  Thanks crimesaucer.  I really really appreciate your help.

---

### Post by crimesaucer on 2008-10-21
> **Jordan777 said:**
> Ah in that case maybe I'll try it tomorrow or Wednesday.  Thanks crimesaucer.  I really really appreciate your help.

Cool, I hope it works out, I hope I didn't pressure you too much about the FTP install, I just don't know how else to help..... another way might be for you to use a friends Ethernet connection (as DHCP), and the FTP install just to get it on your computer, and from there you can figure out your wireless network.

---

### Post by Jordan777 on 2008-10-25
So I tried the FTP install...  It didn't really do anything for me.  I couldn't even finish because it wouldn't install the packages.  Also it can detect my cards and it says it connects to the network.  My only problem with that is, my network requires a WEP key and it doesn't take that in to account.  Also when I think about it, and FTP install is not really any better than a normal install.  I just redid the normal install and I'm getting the same transient resolver error.  I want to know what the heck is going on.  I'm not angry if I seem that way :P.  I'm just confused and frustrated.  I can connect to my network and I get assigned a IP address through dhcpcd wlan0 but then I can't ping google and I get this server error.  What's up with that?  My network isn't messed up.  I've done nothing special to it.  All it has is a WEP key.  That's it.  This shouldn't be this big of a deal.  :(

---

### Post by crimesaucer on 2008-10-26
> **Jordan777 said:**
> So I tried the FTP install...  It didn't really do anything for me.  I couldn't even finish because it wouldn't install the packages.  Also it can detect my cards and it says it connects to the network.  My only problem with that is, my network requires a WEP key and it doesn't take that in to account.  Also when I think about it, and FTP install is not really any better than a normal install.  I just redid the normal install and I'm getting the same transient resolver error.  I want to know what the heck is going on.  I'm not angry if I seem that way :P.  I'm just confused and frustrated.  I can connect to my network and I get assigned a IP address through dhcpcd wlan0 but then I can't ping google and I get this server error.  What's up with that?  My network isn't messed up.  I've done nothing special to it.  All it has is a WEP key.  That's it.  This shouldn't be this big of a deal.  :(


Well, my point was that it would either work, or it would fail, and if it failed then you wouldn't have had to spend all of the time that a regular install takes..... just to get to the same "transient resolver" error.


You got to the point where normally you would install the core packages..... and it failed..... just like if you had installed regularly and done your first "pacman -Syu".


When you say that it recognized your wifi card, and connected it successfully..... that seems strange that it still didn't work.


I can't suggest any other solution, sorry.

---

### Post by Jordan777 on 2008-10-26
Oh well...  That's alright.  I'll just get intrepid when it's out.  I'll come back to Arch at some point.

---

### Post by Portmanteaufu on 2008-10-28
Sorry, I'm joining the saga a bit late.

This might seem like a stupid question, but after dhcpcd-ing, have you tried getting to the internet in general? Either by pinging (ping google.com) or with lynx (lynx google.com)?

I may have missed it in the 8 or so pages of the thread, but I wasn't clear on whether you had general net access and the mirrors were failing or if you couldn't get to anything beyond your router at all. Of course, if you're just sick of the whole ordeal and want to wait for Ibex instead of continuing, that's understandable.

---

### Post by Jordan777 on 2008-10-29
Well I already installed Ibex but I see internet troubles have followed me there as well...  Anyway, yes, I had tried pinging google but that didn't work.  It worked at one point in the past but then never again.  And I had been able to connect to the servers at one point and then it just stopped after doing part of the updates.  It was really strange.  I'm thinking that my wireless card rtl8187, it's part of my ASUSM2N 32 sli deluxe board, just doesn't seem to want to play nice with ubuntu or arch.  In windows it does just fine though...

---

