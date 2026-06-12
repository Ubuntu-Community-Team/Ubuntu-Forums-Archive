---
title: "Dual Install with Win 2000"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Spankmaster79 on 2006-09-14
Hi Community,

I want to install Xubuntu on an old Toshiba Tecra 8000 I have. I already downloaded the .iso and testet it and it looks fine. 

On install it asks me if want to delete the partition that is on dev/hda0 or if I want to manually edit the partition table. Now my problem is that I don't want to destroy my Windows 2000 partition.

Actually I'm used to Suse's automatic install and Grub. Which worked fine for me all the time. But now I need a little help, since I didn't see a dialog in the graphical installer.

I need to keep the Win 2000 because I don't know if Cisco VPN is working, or even any VPN connection which I need at times.

So can someone guide me? Couldn't find a HOW-TO on dual boot install with Grub... :rolleyes: 

thx in advance
Spanky

---

### Post by Najand on 2006-09-14
Do you have any other partitions on your hard disk?

---

### Post by petri on 2006-09-14
You´ll find an excellent guide at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

or if you want a separate /home follow this [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
I prefer a separate /home partition, in that way I don't have to worry about my files in case of a new installation/clean uppgrade.

Do not forget to defragment windows before starting Xubuntu installation!

---

### Post by Spankmaster79 on 2006-09-14
First of all, *WOW* your fast!!!! That's what I love in Unix/Linux Forum.Always quick answers :KS 

> **Najand said:**
> Do you have any other partitions on your hard disk?

No, there are no other partitions on the laptop. The harddisk is only 6GB.

thx for the links, I'll read them and try to follow.

[QUOTE=petri]Do not forget to defragment windows before starting Xubuntu installation![/QUOTE]
What for? Space?


By the way, will I need the Altenate CD? Because than I'll start downloading it already.

---

### Post by petri on 2006-09-14
Yes with xubuntu you will need an alternate CD. If you have a FAT32 partition then follow this guide
[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

Another great site before, during and after installation is [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

EDIT: Defragmenting yes, because of space. Windows spreads fragments of files all over your harddisk, when you resize it during xubuntu installation something may be left behind under the Linux partition and then your windows behaves a little bit sick :D If it starts.

---

### Post by Najand on 2006-09-14
Why using the alternate CD And why not the original Live+Installation CD?

---

### Post by Spankmaster79 on 2006-09-14
I think not the live+installation CD because you can't install in text-mode.

Or is it able to do partitioning in the graphical installer and install GRUB?:-k

---

### Post by petri on 2006-09-14
Yes it is able :D

But if your comp specs are 366MHz/128MB RAM like [here]("http://www.lapworld.de/model/Toshiba_Tecra_8000_mP_II_366_Mhz_-_128_MB_-_DVD.php") then you really do need xubuntu instead of a regular ubuntu. In ubuntu live you need 256 MB RAM to play with.

---

### Post by Najand on 2006-09-14
Hmm, and what is the neccessity of using a text-base installation when installation using a GUI-base installation is much easier?

---

### Post by Spankmaster79 on 2006-09-14
> **petri said:**
> Yes it is able :D
So you mean I better don't take the risk. I have 256MB RAM (extended it) but you're right, I chose Xubuntu because of the limited hardware resources.

And the alternate.iso is there already so I'll install with that and the great tutorial you've provided.

thx to all helping \\:D/

---

### Post by petri on 2006-09-14
xubuntu is for the older pc's with very low RAM like 128 MB. 

I have an 200MHz/96MB RAM and the processor works really hard from time to time and swap slows down the machine little bit too often. 

It takes about 3 minutes to boot :( so my kids still use win98. Without the internet of course.

---

### Post by petri on 2006-09-14
You're welcome. :)

Don't forget you can install ubuntu desktop with the psychocats -link. After that when you log in you can choose which desktop to use. Ubuntus gnome desktop will use more of your RAM so...

An alternate CD is also good with computers with naughty ATI graphics, not all ATI are naughty but some. :-?

---

### Post by Najand on 2006-09-14
How can you use XFCE in such situation? Ubuntu wiithout X can work similarlty then.

---

### Post by petri on 2006-09-14
> **Najand said:**
> How can you use XFCE in such situation? Ubuntu wiithout X can work similarlty then.

If you mean my 200/96 so we are not using it. I just tested... :)

---

### Post by Najand on 2006-09-14
I see... Sorry for questioning alot.. I was just curious...

---

### Post by petri on 2006-09-14
That's perfectly ok, 
There are no stupid questions but there are stupid answers.
If you don't ask, you don't know.
and so on... :D

---

### Post by xpod on 2006-09-14
> Hmm, and what is the neccessity of using a text-base installation when installation using a GUI-base installation is much easier?

Older pc`s can have a lot of problems with gui installers because of the extra resources they require.
I could`nt install any of the main cd`s on a similar pc and HAD to use the text based installer...........Which FLEW along

---

### Post by Najand on 2006-09-14
LOL, I am sure there were no stupid answers too... 
When I first installed linux I had a 286 processor, 
8 Mb or Ram and 128 Mb Hard-disk. No Graphical
Environment was supported and installation was very 
difficult. I kept installing with floppy disks and
getting error, then start it over again.  It took me
3 days and I was sitting in front of the computer
with red eyes, but I could finally made it. i don't 
use that computer now, but using that computer with
just using text-base terminal was the best experience
I achieved about linux. The story is about many years 
ago, but that experience is still being used. To be 
honest I have missed my Debian 1.1 &#8211; buzz.... That is
why I was curious...

---

### Post by petri on 2006-09-14
I envy you, you can so much more than I do about comps and Linux. 

When I started my Linux era about 11 months ago I had no clue what hda1, hdb etc means so I formatted my hd which contained all my mp3's :rolleyes: 

My w2k did work flawlessly and still does, never had a virus or spyware. At least what I know 8-[ 

I simply like Ubuntu and the philosphy behind it, humanity to others.

If I had known about psychocats site my emigration would have been painless :D

---

### Post by Spankmaster79 on 2006-09-14
> When I first installed linux I had a 286 processor,
8 Mb or Ram and 128 Mb Hard-disk. No Graphical
Environment was supported and installation was very
difficult. I kept installing with floppy disks and
getting error, then start it over again. It took me
3 days and I was sitting in front of the computer
with red eyes, but I could finally made it.
I'll just have to say *RESPECT*!! That's really not much of system-power you had back then. 

I'll have to say I like graphical installers, if they work:rolleyes:. I'm pretty new to Linux (started with Suse 7.3) and just like having the option of using a system that is not so resource-hungry. But the time you spend sometimes configuring it, is what get's you frustrated. 

Also working in a Windows world makes you automatically get used to the Software and all sourroundings.

So, what was I about to say... :confused: 
Oh ok, the text-installer of the Alternate CD is also "easy-to-use" as far as my opinion as a "not-so-often-Linux-user" goes.

---

### Post by xpod on 2006-09-14
> and I was sitting in front of the computer
with red eyes

Im sure theres even an app in linux that`ll even fix THAT for you....lol

Ive only been using pc`s for 6 or 7 months.Used m.e and xp with I.E & O.E for two weeks before i realised FF and TB were the way to go but then i only used windows for another 4 months or so before i realised enough to get those ISO`s burned,tried and installed\\:D/ ....Killed them both recently and ended up just giving ubunto the whole pc untill i told my other half that is

Xp only now exists due to my lovely wife who dont even use the pc`s but just likes to see me squirm....So back on it went!!
I reckon i could have got away with changing a few colour schemes and just telling her the ubunto was in fact the latest new update from MS..

She`d never have known.....:twisted: 

Have fun....

---

### Post by Spankmaster79 on 2006-09-14
> **xpod said:**
> 
I reckon i could have got away with changing a few colour schemes and just telling her the ubunto was in fact the latest new update from MS..

She`d never have known.....:twisted: 

Have fun....

:D :D *puahhhhh* :D :D
that one was good. REALLY good.

I could've done the same to my girlfriend, but since she used XP at work she's getting confused in Ubuntu because everything is somewhere else.

When she want's to turn to Vista I'll just get [http://www.xpde.com/index.php]("http://www.xpde.com/index.php") Window Manager and tell her it is that! Maybe that'll do it \\:D/ \\:D/

---

