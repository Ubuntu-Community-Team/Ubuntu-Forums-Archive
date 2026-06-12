---
title: "want dual boot ubuntu/xp but already installed ubuntu first."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by topjohn on 2007-10-10
hello all!  hope someone here can help me.  i currently have ubuntu feisty on my dell.  i would like to install xp so that i can dual boot.  can someone give me a step by step on how to do this?  everyone seems to indicate that i should've installed xp first then ubuntu.  i finally got my ubuntu customized the way i want it, and don't want to half to go through re-install again.  any and all help would be greatly appreciated.  long live the might ubuntu.

---

### Post by perixx on 2007-10-10
Hi topjohn!


I remember I was doing this before and used the XP bootmanager for booting the Ubuntu grub loader with pointing it to some kind of partition table file...
If I'm not mistaken, though, you got to have XP on the primary partition (hda0) - but I might be wrong there. If you got Ubuntu on hda0, then it's MBR will surely be overwritten by XP - even if you install it to another partition. 

So where is your Ubuntu installed to - or will you install XP on another HD?

Anyways, if you like, I can dig a little in my personal hint-box and look for the corresponding procedure... I think there should be a solution for you, depending what your configuration shall look like. ;-]


perixx

---

### Post by jd65pl on 2007-10-10
See this for recovering grub after installing windows
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by topjohn on 2007-10-10
wow, fast response!  i'm have one drive.  my intention is to have both os' on the same drive.  to give you some background...

shark@tvtime:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  83  Linux
/dev/sda2              13         282     2168775   82  Linux swap / Solaris
/dev/sda3             283       10974    85883490    5  Extended
/dev/sda5             283        1498     9767488+  83  Linux
/dev/sda6            1499        8677    57665286   83  Linux
/dev/sda7            8678        9314     5116671   83  Linux
shark@tvtime:~$ 

i have seperate partitions for:

/boot
/home
/
/storage
linuxswap

i hope that information helps

when i look at gparted, it looks like i can't make anymore primary partitions.  am i screwed?  if so, is there another way to accomplish this?  as in, a simple backup of ubuntu, then wipe drive, then install xp, and finally restore ubuntu.

thanks for the advice.

---

### Post by perixx on 2007-10-10
Phew - beats me :)


Not sure where you want to make free space on that HD?! Well, I had the same problem with gparted and could accomplish 4 primary partitions with 'ranish' on the 'system rescue cd'... but I would assume that your MBR will be overwritten by such actions, rendering all your other partitions unusable.

Maybe it was better to buy a cheap second HD for your purpose, with the advantage of having space on the first HD for Windows' virtual memory file.... (although you'd have to have a fat16/32 partition for this)?

perixx

---

### Post by SpiritIsReality on 2007-10-10
howdy

[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+reinstall+grub+mbr&meta=&btnG=Google+Search](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+reinstall+grub+mbr&meta=&btnG=Google+Search)
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

tx 
buds

---

### Post by topjohn on 2007-10-10
well, i'm on a dell 6400 laptop, so second hd is not possible... i think.  i guess it didn't show in the fdisk, but i have unparitioned space in the amount of 19gigs.  also wierd is that the 19 gigs is split into 13gigs and 7gigs.  i can't seem to get those two unpartitioned segments to show as one unpartitioned space of 19gigs.  is my paritition table whacked out?

---

### Post by perixx on 2007-10-10
Hmm... counting clusters and things alike is not one of my favourites, I'm better off with MB's ;)

Well, if you hadn't got those empty partitions in an extended tree, you do the following: delete them and creating a new one with qparted - should give you a new primary partition. But unfortunately that's not an option...

I don't know what's on your primary Linux and extended Linux partition... can you somehow 'shovel', say, transfer your data from the first partition into an extended partition and install XP into the first one (no idea, how big it is)?  


Update:

another choice might be using 'ranish', deleting the extended empty partitions and creating a fourth primary for XP -- but I STRONGLY would urge you to back up all of your data!!!

or you give up, do a new dualboot install and prepare for future updates with a separate /home partition as I read about in another thread a few minutes ago: 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 

perixx

---

### Post by Neobuntu on 2007-10-10
Disclaimer: For simplicities sake, put XP first. It's dumb that way. I just now got tired of this. Read on.

Most all open OSs, Ubuntu, Kubuntu, Linux Mint, MEPIS, PCLINUXOS, Debian, etc..., are fast  to install (and build up) . This is far different from Windows.

First one might ask, Why would we now bother with keeping up two separate systems? First, so we don't forget that XP is NOT overall more user friendly. Windows wastes more time with maintainence and still, it's not nearly as secure. Second, to compare hardware performance. Third, to run apps in their native environments. Forth, if you get peeved at "Linux" you can go back to XP until you puke and come back and see it may not be perfect but "Linux" (GNU/Linux) is the best overall. It's improving faster to so don't blink.

Yet if you really want simplicity(and more time back), use Linux only. There's nothing it can't do.

Anyway, XP took WAY too much time to get "updated" and set using the apps I choose. Still, it's been sitting in my faster (how much, can we tell?)  and first spot (partition just after the MBR). 

Years ago I tried this and decided it wasn't worth fighting. Today, it works.

In prep you will want to go into Windows and remove everything you don't need. Make it as small as possible. You may want to check the drive too. You have a current backup, right?

MY SOLUTION: I used a Gparted CD to COPY my NTFS XP (hda1) to a spot (hda3) AFTER my (now) old Kubuntu spot (hda2). BTW, my Linux swap space spot is hda5 and hda4 is an extended holder partition. I set the flag for hda3 as the boot partition (was this absolutely necessary with "MAKEACTIVE"?).

I rebooted and used the "c" command in GRUB (GRUB gfxboot actually; after the "Esc"' key) to test the windows title, setting it for hda3, AKA  (hd0,2) in GRUB parlance (GRUB needed a universal nomenclature). Windows came up and actually un-hibernated. It saw it's self as "C:", cool. Note this is still the first windows partition, even at hda3 and it is a "primary" partition.

So I took the plunge and erased the old hda1, NTFS, XP partition (Have your backups kiddies). I then (in my case) did a fresh install of "Linux"at hda1; leaving my current Kubuntu at hda2. Kubuntu also still worked. FYI, I did a Debian Etch install into hda1 with zero selected package "tasks" and installed kde-core and built on it. I have recently done a gnome-core and a separate icewm build on two other computers. Both sweet. You could just as well install Linux Mint 3.1 or whatever you like (as position numero uno!)

This might be a good place to point out, never erase you current; best install but instead, install a new test partition and use it a while, before you decide to make it your fav (and work OS). This way you always do recommended clean installs and you can fall back to what you got all fluffed up; in a hurry.

TIP: I suggest that your main system should not be a new, so called  "stable" or out of "RC" release but a few months after that (in the wild) and with good reports and upgrades available. Be patient. No one will force you to be patient with open software. Do test everything you can. Just not as your MAIN system. Balance Grasshopper.

Obviously, one has to work with GRUB (or your preference) and one way to do it is, have the GRUB "/boot" directory reside and "setup (hd0)" to your new main chosen, installed partition. Your other Linux partitions (if any) might best be called by the generic /vmlinuz (and rd) links, so if they upgrade, it will boot the new kernels automatically. This way your main GRUB dynamically changes with your main systems kernel upgrades but the "other" "Linux" partition get a static call (once set to the correct partition)  to those kernel links in their / directory. So in my case (for example) my Kubuntu hda2 gets called from the hda1 GRUB install and it's "menu.lst".

As I said, I also like GFXboot cause it's perdy. The count down is a sweet tweak.  I notice no speed slowdown there. I like the Tux vs. MSN gfxboot theme.

DON'T FORGET TO HAVE FUN!

---

### Post by R.Bucky on 2007-10-10
In summary, you would have to conduct a clean Windows install first, and then use a linux live cd to partition the remaining space in the ntfs partition. I had an hp ze5170 with a 40 GB drive where I installed XP on the entire drive and then used a partition editor to allot 20GB to ubuntu. Windows has to be installed first and it is best to just install it without adding any additional programs. Trust me. It is better for the mind and the soul!

---

### Post by topjohn on 2007-10-10
based on what i've read here, i'm now looking for other options.  my main dilema is i have some wmv's for computer based training, that i can't see in ubuntu.  i've installed all codecs mentioned in the forum and that has worked for some wmv's, but not these.  i get audio but no video.  i assumed that i wouldn't be able to view without having windows.  any suggestions?  vmware player or server?  thanks for everybody's help.  i will try the ranish parition editor and see if i can get a primary parition together for xp install.  worse comes to worse i'll just look up how to do backup restore of my ubuntu and install xp first.  thank you to everyone foryour awesome support.  lastly, what's the deal with the different amounts of "ubuntu beans"?  is that somekind of credit system for helping?  if so, how do i award folks?  thanks again!

---

### Post by Neobuntu on 2007-10-10
No, I've had all video formats working and it's easier than installing, emulating or messing with Windows; which by the way doesn't come playing all these formats.

Video playing is not a Windows (or Mac) exclusive. In fact, an open system is your best bet of playing them all.

The real question is why are there so many non-free formats (and why do they keep changing them)? That is, why is there not more of  standard and the answer is, it's up to you (and the people producing them) to recognize lock-in technologies.  

This has less to do with "Linux" compatibility than it does with corruption and monopoly. 

In the end, it all works but you have to follow the many who have already blazed this trail.

Once you try installing the many codecs for (Firefox?) plug-ins, realize that VLC has it's own set. Most other front ends use Xine or Mplayer on the back end. So there are three to try, and with so many differing formats and differing versions, then on top of that, perhaps one of these three will play and play in the manner you like to see it.

I had a star trek ".wmv" that only worked to my liking in the VLC player. It ALSO depends on the horse power you've got. Old computers need very carefully selected (light) programs.

In addition, you may need to right click (mplayer) in a plug-in and set the video "engine" to match the best choice for you video card. (xv,gl,ect..)

Now, one question (for some) is plug-in or simulated plug-in. If a plug-in doesn't work (in the browser on some format and version) then you could run the player separately and made to work, as if it is embedded.  Firefox has a media extension for this. This may get you your 100% compatibility with all things and types (that Windows doesn't even have). Ironically, this is what you best have to setup in Windows too.

Overall, if you look at it pessimistically, computers stink. Open software stinks less.

Summary: If I understand your goal. You are barking up the wrong tree (Windows install) just to get a video to work.

My advice is to be patient and select your instruction carefully. Check for Ubuntu, current, and short (automatic) methods.

As time goes by and more people adopt open software, open formats will be all that is tolerated. Right now the glass is 99% full. They work anyway. Blame the monopolist and sheep for your extra work. It's definitely not the norm from open developers.

---

### Post by Martje_001 on 2007-10-10
I should do:
1. Install WinXP
2. Boot up live-cd
3. Go to terminal and type:
```
sudo grub
> find /boot/grub/stage1
> root (hdx,x)
> setup (hdx)
```
4. Add WinXp to menu.lst

---

### Post by sd.chen on 2007-10-10
> **topjohn said:**
> 
i have seperate partitions for:

/boot
/home
/
/storage
linuxswap

i hope that information helps

when i look at gparted, it looks like i can't make anymore primary partitions.  am i screwed?  if so, is there another way to accomplish this?  as in, a simple backup of ubuntu, then wipe drive, then install xp, and finally restore ubuntu.

thanks for the advice.

You can make as many *logical* partitions as you want. I used logical partitions to subdivide an *extended* partition to get my machine (single HD) to dual boot while keeping / and /home on separate partitions.

Edit: From what I understand, you need to boot from a primary partition, so maybe move one of your existing (non-booting) primary partitions into the extended partition and install Windows in the newly freed primary partition.

---

### Post by s.victor on 2007-10-10
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Here is the step-by-step tutorial you need.

---

### Post by Neobuntu on 2007-10-10
Short answer, try VLC for your (Windows monopoly format) video files.

I'm sorry if I have given extra info but that is for everyone.

Of note are (some) reasons why one may or may not also want to use Windows.

If one does want to also use Windows, yes, if you have not already installed your open system. It is easier to install Windows First but don't sweat it. If Windows XP is installed second, just know how to do the quick GRUB reinstall.

Note that what I did was different. I (backed up and) copied XP to spot 3, clean installed "Linux" in spot 1 (leaving  my main work install in spot 2) and that adjusted GRUB for me. 

Note "spot" 4 is an extended one that holds the Linux swap spot #5 (hda5). This if I ever want more than 4 partitions by resizing but leaving the installed, with their same partition spot/name. Even swap would stay "hda5". Currently I do have a large hda6 partition (5 and 6 are inside of 4) for testing as well, FYI. 

Normally I keep it simple but this is a large drive that begs for testing. :)

Newbies need only to indicate that they want the installer(s) to take the whole drive. Done. A dual boot around XP (first) is easy too. It will give you the choice upon starting.

I used to favor both but now I really think newbies are better if they can skip Windows altogether. Just don't forget the down sides to Windows when you have a glitch. If you expect perfection, you'll be disappointed with open software and more so with anything else.

Some people are too scared and leaving XP installed, is there no-risk (soft sell) option. This and it's free. Yet, we would perhaps be better off getting over it (and perhaps retiring some useless devices too) . It's the "buyers" remorse thing. "Oh poo! What have I done!".  When one has XP to run back to, they can then see how XP stinks more. Oh how we forget. So the bottom line is, the weak at heart need both. Yeah, I said it. :) Not that anyone can't have both for testing(I do). I'm not being elitist here. Windows simply wastes my time(more). if you're a good decision maker, just do it.

---

### Post by jlambeth1 on 2007-10-10
I used to dual boot but I decided to experiment with installing XP as a virtual machine using virtualbox.  After finding a good guide on how to install virtualbox, I was able to get XP installed as a virtual machine just fine.  I was skeptical when I read other people's posts claimiing that XP ran just as fast this way but it is true.  My virtual XP machine flys right along.  If you want to give this a shot, go to [http://www.howtoadvice.com/UbuntuVirtualBox/](http://www.howtoadvice.com/UbuntuVirtualBox/) for a good and easy tutorial on getting virtualbox installed.  Now I can have XP open in one workspace for my wife and Ubuntu on the other one for me!

---

### Post by Neobuntu on 2007-10-10
That's some good advice. Last time I tried a win4lin with XP it ran dog slow (required fees technically) and was largely a win98 (Ack) thing unless you had the double harse pawr (CPU/RAM). 

Still, it is not the same a a native OS. Yet, if it is enough, fine. It beats rebooting. One could say, why not dual boot AND use Virtualbox (or something). 

Well now we have Three things to keep up with. 

If you just want to use a computer, XP (Vista known as worse) is not the answer. An open install such as Kubuntu is. Or Linux Mint 3.1>, or the other way, the kinda newbie friendly, Debian.  That depends on what you want to wide up with tomorrow. PCLINUXOS might be your best; easy to install and use now system but I would not plan on having it forever. It may be considered difficult to update.

*(K)ubuntu is one of the best balances of newbie ready, human friendly but not so much that is can't be upgraded and settled down with for a year or so. 

Debian (fast to install), while requiring (some) more of an education; well, I've come to see is a good thing. Even if you don't want to know stuff about Linux. Debian can be run as the most stable (server or desktop), most flexible, more programs to choose, upgradeable system of anything.  It's just perhaps isn't granny's best first drive (sorry granny). Unless a loving geek builds it up like *ubuntu or Linux Mint. This all depend on the current release status of Debian though.  Right now, Etch is hot. Once Debian is  old though, you may be back porting just about everything from Debian "testing". While that stability will most likely trounce Windows Anything, it may not Ubuntu; at that point in time. This is how and why ubuntu came together IMHO. Two things about this: One, you'll best do a clean install of *ubuntu once it's this "old". Two, Debian is historically better at dist-upgrading, than Ubuntu (but you'd probably be better clean installing anything, anyway) . Three, (clean) installing a Debian release just before it is official is usually a somewhat desirable thing (over backports) unlike with ubuntu where you'd best wait a while after it has been out, before making it your production system.    

Remember folks, Ubuntu is Debian Sid (and friends) somewhat stabilized (and recompiled). There are pros and cons to it all. While it's reasonable to expect variability is such complex and newly changing (progressive) systems sets, one would hope to depend on stable stability. Yep, I said a stable level of stability. Ubuntu gets better at this and so does Debian. The idea is they help each other. Not just better at stability, but better at a more stable stability over time. It's about smoothing out the curves, for the masses. Testing (while imperative) is secondary!

I am well aware that Debian users tend to use a mixed system for their desktops. Yet,  I am playing with Debian stable for the desktop. I value a more known base; when trouble arises. Currently I am not missing any newer stuff (this changes from time to time). I find adding non-free "stuff" and the like to Debian little more complex (the same)  than "correctly" doing the same with Ubuntu. So far I've only have to "backport" Flash from "testing" (for it to work 100%). I found the nvidia(legacy) install preferable. I now have an easy plan (upgrading Nvida 3D) for when Kernel upgrades come through.

Anyway, so much for the Debian boost. 

UPDATE: I chunked it all for Ubuntu Gusty. I just don't have the time for Debian.

Ubuntu has many advantages. Happy (open) computing. Ain't choice grand.

---

### Post by topjohn on 2007-10-10
i've looked into the codecs and am now able to to get mplayer to play the wmv's... however the video is stretched out.  imagine writing on a rubber band and then stretching it out.  looks like it's clear and playing fine, except it's squished and elongated.  also, i looked at my partitions again. one of the unpartitioned areas appears under the extended area and the other looks to be eligble to be made a primary.  so i made it primary and will try to install xp tonight.  there is soo much to learn!  it's also really amazing that all this help is available from other users.  ubumtu can be somewhat frustrating, but always interesting.  i will look into virtual box as well.  maybe that will be my answer.  how does virtual box compare to vmplayer.  the only thing i keep xp around for at this point is games(but rarely if ever), wmv's(because i can't figure a way around it), and sometimes itunes, cause shows never get catagorized correctly when i use gtkpod!

---

### Post by Neobuntu on 2007-10-10
The biggest point here is: Newbies simply do not believe that Windows is not necessary. You may have a need there but it is nothing that can't be left behind and that is, for all our best interest.

"Linux" is COMPATIBLE! (dear newbies)

I suggest that you forget your old Windows closed monopoly programs and move along to better choices. Do not download them from their development web sites when they are already there and ready to plug-in, using your better "package manager" (synaptic).

---

### Post by Neobuntu on 2007-10-10
That's great news. It sounds like you simply need to tick off the correct matching screen aspect and you are there (zero Windows needed). You might still see if you like VLC for some coded formats. I think mplayer is my fav.

XP for Games is a winner. There are more and you can use name brand titles(but at what cost per game). Yet, it is nice to play the many games on an open system that require no CD, only the Internet and for free. See TORCS, Open Arena, etc..(after you have a setup 3D video card). Many good non-3D games are available too. Some "open" games work on Windows too. I mean how much time does one have to play all these games? I'd say every category is well covered. What kind of game does one wish?

---

### Post by zekica on 2007-10-10
@topjohn: I have never resized/moved partitions with gparted, so this is only a guess what you should do.

You can have maximum of four Primary partitions on your hard drive (this is a problem with MBR partition table, which exists since DOS), and that includes that one 'Extended' partition you have. You have total of three partitions on your HDD:

1-12 - linux /boot = 98 MB
13-282 - linux swap = 2221 MB
283-10974 - Extended = 87944 MB
Extended: 293-9314 - Three Linux Logical Drives = 74200 MB
Extended: 9315-10974 - Free Space *inside* Extended partition = 13645 MB
10975-11978 - Free Space = 8250 MB free

Total Free Space = 21935 MB

You will have to resize this Extended Partition from gParted, and it should be quick operation, and then create windows (NTFS) partition.

1. You have to use Ubuntu LiveCD or gparted LiveCD.
2. Resize this Extended Partiton (shring it's end, so that it end on Cylinder 9314.
3. Create NTFS partiton from all free space that is now outside of this extended partition.

Then you should install windows onto that partition (I think you can do that).

Then you can get GRUB back by using Ubuntu LiveCD and entering in terminal:

[B]sudo grub
root (hd0,0)
setup (hd0)
quit [/B]
Reboot, and hopefully it will reinstall GRUB and you will be able to boot Ubuntu.

After that you have to edit **/boot/grub/menu.lst** to boot Windows - add this at the end of file:
[B]title           Microsoft Windows XP
root            (hd0,3)
savedefault
makeactive
chainloader     +1
[/B]

That should be everything you need to do.

---

### Post by Neobuntu on 2007-10-10
BEWARE: (Manual) GRUB warning!

When using the "setup" after setting "root" you probably NEVER want to see more than one digit... "setup (hd0)"... so that you ONLY write to your (separate) MBR an not OVER the important bootable; first part of any numbered partition/OS install. You'll never restore it from where it was if you do(without a separate backup) . It will best be a reinstall.

Hey, what do you think we'd have to do to get the GRUB team to throw up a simple text warning before trashing newbies installs?

---

### Post by topjohn on 2007-10-10
> **zekica said:**
> @topjohn: I have never resized/moved partitions with gparted, so this is only a guess what you should do.

You can have maximum of four Primary partitions on your hard drive (this is a problem with MBR partition table, which exists since DOS), and that includes that one 'Extended' partition you have. You have total of three partitions on your HDD:

1-12 - linux /boot = 98 MB
13-282 - linux swap = 2221 MB
283-10974 - Extended = 87944 MB
Extended: 293-9314 - Three Linux Logical Drives = 74200 MB
Extended: 9315-10974 - Free Space *inside* Extended partition = 13645 MB
10975-11978 - Free Space = 8250 MB free

Total Free Space = 21935 MB

You will have to resize this Extended Partition from gParted, and it should be quick operation, and then create windows (NTFS) partition.

2. Resize this Extended Partiton (shring it's end, so that it end on Cylinder 9314.



is there anymore light you can shed on how to do number two so that i can "shrink" it to cylinder 9314.  i'm a bit nervous about parititioning at that level.

---

### Post by jlambeth1 on 2007-10-10
I agree completely that Linux is compatible and that Windows is not necessary.  Unfortunately my wife is very much against change and that is the reason I keep XP around.  I hope over the next couple of years I can ween her off of Microsoft and can be free of their garbage forever!

---

### Post by topjohn on 2007-10-11
after the tip from  zekica, i went back to gparted and resized the extended partition to the specs he mentioned.  that gave me back a full 20gig unpartitioned space, which i was able to make a primary parition.  i was able to re-install xp, and then use the grub advice given to correctly boot into both ubuntu and xp.  thanks to everyone for helping on this!  i've learned alot!  cheers all and happy ubuntu'ing!

---

### Post by JackLhasa on 2007-10-24
when trying to set this up on my pc, the windows xp installer disk says that my hard drive partitions are "unknown device."  It will not let me select any of them for the installation.  I just want XP back so I can play games again.  Ubuntu does everything else better than XP.

-Jack.

---

### Post by perixx on 2007-11-07
JackLHasa, you could maybe use your XP install-CD, boot into the recovery console (R - partition select, but DO NOT make a "repair installation"!) and enter "fixboot" and "fixmbr" (if you can access your partition from there...


perixx

---

