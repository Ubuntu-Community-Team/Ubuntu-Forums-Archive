---
title: "I'm concidering switching BUT....."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-05-20
Hi, I saw this video on the nice effects on Ubuntu such as the cube and water effects and I am concidering switching, but I have a few questions

1) how hassle free is switching from XP to Ubuntu

2) the video had windows XP and Mac running ontop of Ubuntu how easy is this (I need to be able to run microsoft office and games)

3)Will this run it:

Intel core duo, Ram: 1GB, GFX: 128mb intergrated

4) how hassle free is it to get the XP OS back.

As you can see I am not quite ready to completely let go of XP, this is mainly becuase I have heard that Ubuntu won't run certain PC related programs I use.

any help apreciated.

---

### Post by tompickles on 2007-05-20
why not consider dual booting with both OS's on your box? there is plenty of [info around on setting this up]("https://help.ubuntu.com/community/WindowsDualBoot"). basically you just resize your xp partition and install Ubuntu on the space.

---

### Post by overdrank on 2007-05-20
> **Ludford said:**
> Hi, I saw this video on the nice effects on Ubuntu such as the cube and water effects and I am concidering switching, but I have a few questions

1) how hassle free is switching from XP to Ubuntu

2) the video had windows XP and Mac running ontop of Ubuntu how easy is this (I need to be able to run microsoft office and games)

3)Will this run it:

Intel core duo, Ram: 1GB, GFX: 128mb intergrated

4) how hassle free is it to get the XP OS back.

As you can see I am not quite ready to completely let go of XP, this is mainly becuase I have heard that Ubuntu won't run certain PC related programs I use.

any help apreciated.

Hi to answer some of your questions
1.Well you dont have to totally switch you can still dual boot. That way if you have trouble in ubuntu you can still get some work done until you get use to ubuntu.
2. As you can see it can be done, I have not tried that option yet so.
3. If you could give more info on the video card everything else should be ok.
4. Like I said in answer one you dont have to loose xp.
There are some programs that ubuntu can run in wine that are windows programs but there are a lot of linux programs that are equivalent to windows. So you can feel safe to give it a try but it is a new experience. Good luck!

---

### Post by JerryAtrik on 2007-05-20
I have had Ubuntu alongside XP for about a month . If you follow the instructions properly you will have no problems. It is far easier to install than Windows XP .Don`t rush it check everything as you go .I was worried when I looked in on these threads but remember the ones with problems are a minute section of all those that have Ubuntu  installed .I have no regrets , it is a voyage of discovery

---

### Post by Ludford on 2007-05-20
My card is an Intel 128mb Intergrated, Would this run the nice 3d effects?

---

### Post by ArieT on 2007-05-20
Probably.

---

### Post by abhishek456 on 2007-05-20
> (I need to be able to run microsoft office and games

remember you can manage your office documents through openoffice which is a good set of office tools and you can also play ur windows games in linux through Cedega (They may not be that great as played in windows)

[http://www.transgaming.com/]("http://www.transgaming.com/")

you can run windows programs through wine emulator [http://www.winehq.com/]("http://www.winehq.com/")

---

### Post by Ludford on 2007-05-20
is the myth that linux and WINE are bitches to set up true?

---

### Post by Campingman on 2007-05-20
> **Ludford said:**
> is the myth that linux and WINE are bitches to set up true?

Wine is a doddle to set up on Linux, it is just that not all windows programs are supported, for more info:
[http://frankscorner.org/index.php](http://frankscorner.org/index.php)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Take the plunge and give it a go with dual boot, you only have a bit of hair to lose!!

---

### Post by Ludford on 2007-05-20
I'd switch completly if Cedega was free, but I guess I'll just run duel boot for now.

---

### Post by cmost on 2007-05-20
Intel graphics cards are very well supported by open source drivers so Compiz (or Beryl's) visual effects should work right out of the box as long as you install Ubuntu 7.04 (or Linux Mint 3.0 Beta 2.).  As for that video you mentioned, please don't be dazzled too much.  First, let me mention that it is illegal to run Mac OS-X on any hardware other than a Macintosh.  There are hacked copies of OS-X that will run on ordinary Intel hardware but these are not sanctioned by Apple.  Don't waste your time.  As for Windows, if you have a legal copy then you should have no trouble dual booting, or, running your Windows installation from within Ubuntu using the free VMware Server (or QEMU, VirtualDOS box, or KVM.)  VMware has a utility on their website that will create a virtual OS image from your existing copy of Windows.  Then, when you use VMware in Ubuntu you'll be accessing your XP installation as it was (rather than a fresh install.)  Running Windows this way is faster because it doesn't require a reboot.  Finally, IEs4Linux will allow you to run a copy of Internet Explorer 6.0 in Ubuntu, natively.  This is useful for the few websites that don't display in Firefox properly.  You can also utilize Crossover Office (or WINE all by itself) to run your copy of Microsoft Office natively in Ubuntu (no Windows emulator required.)  I recommend you give OpenOffice a try first.  Version 2.2 is very good and looks and feels just like MS-Office.  Good luck.

---

### Post by Ludford on 2007-05-20
Theres one more question I need to ask before doing it. Will I notice any "Slow down" of either OS than if I had the PC all one OS?

---

### Post by Swab on 2007-05-20
> **Ludford said:**
> Theres one more question I need to ask before doing it. Will I notice any "Slow down" of either OS than if I had the PC all one OS?

No.

---

### Post by nalmeth on 2007-05-20
Defrag your windows partition before shrinking it. At least once.

And I fully recommend backing up any important files you have. This is good safe practice even if you're just using XP. 
You will probably be OK, but as a general rule, data loss sucks :(

---

### Post by Ozeuss on 2007-05-20
> **Ludford said:**
> Hi, I saw this video on the nice effects on Ubuntu such as the cube and water effects and I am concidering switching, but I have a few questions

1) how hassle free is switching from XP to Ubuntu

2) the video had windows XP and Mac running ontop of Ubuntu how easy is this (I need to be able to run microsoft office and games)

3)Will this run it:

Intel core duo, Ram: 1GB, GFX: 128mb intergrated

4) how hassle free is it to get the XP OS back.

As you can see I am not quite ready to completely let go of XP, this is mainly becuase I have heard that Ubuntu won't run certain PC related programs I use.

any help apreciated.

1) it depends what you consider hassle. Ubuntu and Linux and just different in some things. for the better, IMHO, for sure.
2) that virtualization. pretty easy, there are very specific howtos.
your specs are enough to run virtualization, although know that you will have to allocate some RAM for it, so games in VM are no good.
if you want to play games, Dual Boot. for routine and common programs, u can use wine. for pretty much anything else, u can use VM.

---

### Post by Ludford on 2007-05-20
Wait, Do I need 2 Hard drives?

---

### Post by nalmeth on 2007-05-20
> Wait, Do I need 2 Hard drives?
No, you can use one hard drive for both OS's

---

### Post by meatus on 2007-05-20
You should look into [wubi](http://www.google.co.uk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.cutlersoftware.com%2Fubuntusetup%2Fwubi%2Fen-US%2Findex.html&ei=f85QRu6NEJWGQdLh1eQH&usg=AFrqEze1qcwkM42C33oSFRxniXlOiVmzSA&sig2=o-VspquNSe9dlvecoJQkow)

---

### Post by Ludford on 2007-05-21
Right, I have actually just deleted my OS, (mis-understod a part and changed the intire memory to SWAP)

Maybe this is an excuse to do a total install?

I can always get xp back with my system restore right?

---

### Post by Happy_Man on 2007-05-21
Do you have a recovery partition? If so, it may be possible, if not, well.... :( 

Of course, now you can just stick Ubuntu on there, no hassle!

---

### Post by Ludford on 2007-05-21
No idea I havn't heard of a partition untill today, Lol

If I install Ubuntu, I could always switch back to XP with my XP disk that came with the Laptop right?

---

### Post by Kobalt on 2007-05-21
Yes and you can even keep your XP while having Ubuntu aside, it's called a dual boot. Check [it]("http://psychocats.net/ubuntu/partitioning") out.

---

### Post by Ludford on 2007-05-21
I'm guessing you didn't read the first pages, I was trying to duel boot but ended up deleting my entire OS, lol.

Never mind, as long as I can get XP back whenever I want (should I want to, depends how good linux is) I'll do a full install.

My laptop is only used for Writting notes, listening to music, browsing the internet and looking cool. If linux can do all that I'm set.

---

### Post by lazyart on 2007-05-21
Well, you've lost your data.

IF you want to dual boot you must first install windows then ubuntu.

---

### Post by Ludford on 2007-05-21
I'm not really asking that, I don't mind that I lost my data, I do not want it back.

I want to know if I make linux my only OS, if I can get XP back (minus all the data of course) with the Xp disk.

---

### Post by Kobalt on 2007-05-21
oOops, sorry Ludford, I think I'm a bit too tired...
I advice you to install your XP first and then Ubuntu, this way it won't be messing up Grub.

---

### Post by Ludford on 2007-05-21
Cool, cheers :)

Although with my PC idiocy I may end up doing the same again. Like I said if linux can, write, play music, browse internet and most importantly look cool. That'd be all I needed.

---

### Post by Kobalt on 2007-05-21
Cheerio !

---

### Post by Dustdevil on 2007-05-21
Hey all this is my 1st posting, so forgive....

As far as the Dual boot. Go for it, I loaded Ubuntu on my Dell D610 about 3 days ago. It automatically gave me a dual (actually 4 choices on the boot screen) choice. 
At anytime I can chose XP of Ubuntu. I was told to play around with it and explore it. I somehow found Kubuntu , which is really neat. I could ramble for a while with how happy I am. I'v never used anything other than Windows before 3 days ago, and I relay like Ubuntu. 

Your gonna love the way it updates itself too. I was lucky and had a friend who knows Ubuntu very well ( he claims to be dumb, hahah) but he's day by day explaining stuff to me. 

As to running Office or Games. Don't worry. Open office seems to have that under control. All my Office 2003 stuff was easy to import over. I just had to click it. Bam ! it opened up. Very nice experience. 
I would recommend install Ubuntu now, and start enjoying it. I bet your gonna wonder why you did not try it sooner (I am wondering that now my self....)

BTW, before I installed Ubunto... I did format my machine, installed XP, did all the updates,(2 days process), did all the utilities software I like, -Ghosted the Drive- Installed Ubunto.

So regardless of what COULD/MAY/ or POSSIBLY COULD happen, I wont lose anything. Windows is recoverable. And Ubuntu is also.

Cheers~

---

### Post by Ludford on 2007-05-21
Cheers for the info

hmmm, I can't lay my hands on my XP disk today.

I may full install. But the answer I really want to know is....

If I full install now. and I don't like linux for whatever reason, can I pop my xp disk in (when I get it). and restore my PC to what it was at the factory (running xp)

---

### Post by Kobalt on 2007-05-21
Yes you can remove Ubuntu just as easily as you can remove XP.

---

### Post by Ludford on 2007-05-21
What by poking around in it and changing random things like I did, lol

I am now going to install it full, I don't know why I want to get XP back but I somehow need to know I can.... a 17 year teather is hard to break.

one more question, Does linux auto detect and run flash drives like xp?

Now all I need is something like linux for dummies.

---

### Post by Happy_Man on 2007-05-21
Yes it does....

And Linux for Dummies... you're looking at it. The UbuntuForums is the place to be for Linux and Ubuntu help.

---

### Post by Ludford on 2007-05-21
Well I've full installed, and posted a topic about my happyness

---

### Post by Happy_Man on 2007-05-21
Congrats, and Welcome To Ubuntu!

---

### Post by Ludford on 2007-05-21
Wow it wobbles, (How shallow am I)

---

### Post by Nekiruhs on 2007-05-21
Meh, its been about 6 months and I'm still in awe at beryl, especially my desktop decahedron (ten sides, eight desktops).

---

### Post by Kobalt on 2007-05-21
Welcome :)

---

### Post by Happy_Man on 2007-05-21
Dude.. I cannot live w/o Beryl. It is what keeps me sane.....

---

