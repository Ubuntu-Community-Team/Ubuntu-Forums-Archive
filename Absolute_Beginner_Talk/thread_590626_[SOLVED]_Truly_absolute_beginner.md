---
title: "[SOLVED] Truly absolute beginner"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by spookyone on 2007-10-24
I am a complete newbie to Linux, but not computer illiterate as I am a sys admin in Windows.  I want to move my laptop to Linux and Ubuntu seems like the perfect distro for me.  I have dabbled with live CD distros and used them to repair Windows boxes when Windows either wouldn't boot or I didn't want it to load for one reason or another.  Gnoppix and Puppy.   I am hoping to get some reassurance about my few remaining concerns.  Like drivers.  Can I be sure I can get support for all my hardware for Ubuntu?  Can I do all the things I need to do?  I don't game, so that's no problem.  How can I know Linux is for me?

---

### Post by JKyleOKC on 2007-10-24
Use a Ubuntu live CD for a while to find the answers to your questions. I used Knoppix live CDs to troubleshoot and rescue Windows systems but never liked it as a general desktop package. Within a week after trying the Xubuntu live CD, I installed it on all four of my Win98 boxes in dual-boot configuration. While I still have to run Windows on two of them to support my customers (I do data recovery on Btrieve-based packages) the other two run Fiesty 24/7. One of them is the print server for my LAN and it works much better than it did using Windows. The other is an experimental machine that sometimes runs Win2K in VMWare, where I can try out ideas.

I've installed Samba on all four boxes so that I can exchange data with the Windows machines; so far I've not encountered anything I cannot do with Xubuntu so I may be able to get rid of the dual boot setups and simply run the various flavors of Windows in VMWare, on all of them. The main thing holding me back is that my Email (on one box) and my Delphi setups (on the other) are both highly customized and I want to avoid having to redo that...

---

### Post by avik on 2007-10-24
> **spookyone said:**
> Can I do all the things I need to do?  I don't game, so that's no problem.  How can I know Linux is for me?

The best way to find out is to use LiveCDs, which you already know how to do.  Try the Ubuntu LiveCD if your computer can handle it.

And what are your specs?  Post them so we can tell how compatible your hard ware is.

---

### Post by jimrz on 2007-10-24
> **spookyone said:**
> I am a complete newbie to Linux, but not computer illiterate as I am a sys admin in Windows.  I want to move my laptop to Linux and Ubuntu seems like the perfect distro for me.  I have dabbled with live CD distros and used them to repair Windows boxes when Windows either wouldn't boot or I didn't want it to load for one reason or another.  Gnoppix and Puppy.   I am hoping to get some reassurance about my few remaining concerns.  Like drivers.  Can I be sure I can get support for all my hardware for Ubuntu?  Can I do all the things I need to do?  I don't game, so that's no problem.  How can I know Linux is for me?

1 - d/l and burn the live cd ... pop it in ... see how your equipment works with it. if it's ok with the live cd, it should do fine. 

2 - might also want to search these forums, by make/model #/chipset for things like your vid card, wifi, printer and mp3 player, etc, to see what experience others have had correcting problems, if any, on the same equipment.

3 - post specific questions here

Welcome

---

### Post by HermanAB on 2007-10-24
Most laptops work OK - 99% of trouble are with getting the WiFi adaptor to work and you can use ndiswrapper with a Windows driver for that.

If you are a Windoze admin, then I'm not sure that Ubuntu is for you.  You may find the wizards lacking and the command line frustrating.  Mandriva Linux has wizards for everything and may be more to your liking: [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

However, if you *want* to get your hands dirty, then Ubuntu is the right one.

Cheers,

Herman

---

### Post by mdpalow on 2007-10-25
Hello,

Download 7.10 and burn it to disk (iso). Have your computer boot up with the disk in and let it run Live CD on your computer. It won't put anything on your HD permanently and it allows you to evaluate it pretty well. I was even able to setup a few programs to run (e-mail / Evolution) while in Live CD mode. Once I saw my video card (VC), wireless, and sound card working, I knew I was good. When I installed it on my desktop, the first install option didn't work, so I had to reboot and select the 2nd option. That was however do to my video card I'm sure 'cause I had the same problem with my VC using XP. Second option allowed me to see the screen and then 7.10 came up and told me I needed to select an option for my VC that it had detected. It then installed the right drivers and I'm golden. 7.10 also recognized my Linksys Wireless PCI card, sound, on board LAN, web cam, and USBs. No problem with anything working so far. Tested my CD ROMs and they work as well.

I too am a Windows user, but this Ubuntu is exciting. I've had Unbuntu on my two computers now for a total of six days and I haven't even gone into Windows once since then. I know I may have to at some point for something, but as of now - I haven't had reason to boot up in Window$. :)

20 minutes to install, 15 minutes to configure (moving icons, setting up e-mail, adjusting main menu, etc.), and ONLY 9 updates to download... Wow! Very nice compared to that other OS.

The only thing I haven't been able to get working is Lightscribe for burning labels to CD.

Good luck...

---

### Post by PointyWombat on 2007-10-25
Although the Live CD is a good quick option for a quick glance into Ubuntu, there are some limitations to it. I suggest trying Wubi ( [http://wubi-installer.org/](http://wubi-installer.org/) ), which will install an alternative boot environment painlesly and allow you to boot into Ubuntu without disrupting your Windows installation. Read the Wubi FAQ for a quick run down. I've used it and suggested it for new folks quite a few times in the past and all have had success with it.

Good luck.

---

### Post by mmmfottrell on 2007-10-25
As a recent XP convert,  I can say that overall the process was painless. Many laptop users have reported the process as painless. Your best bet is to install while directly connected using ethernet, and you should be able to install all the drivers you need.

Some troubleshooting is necessary, but these forums are incredibly helpful, and the troubleshooting isn't anymore than one might have with a reformat/reinstall of Windows.

---

### Post by magicman5421 on 2007-10-25
> **HermanAB said:**
> Most laptops work OK - 99% of trouble are with getting the WiFi adaptor to work and you can use ndiswrapper with a Windows driver for that.


btw, gutsy is much better about wifi drivers than feisty was. Almost all of the reports I have heard about wifi cards have been good. You may have to "get your hands dirty" with the drivers if say your sound doesn't work but hey, that's what linux is all about.
(almost everything works, that's the beauty of linux)

---

### Post by dem0 on 2007-10-25
While I am not an absolute beginner when it comes to *nix, I have been an avid Windows user as long as I've owned a computer. I was MCSE certified on win2000, but I didn't renew after I joined the USAF. Over the past couple of years I've tried SUSE and Gentoo, both of which impressed me, but I had too many Windows ties to commit 100%. On Monday I finally got so fed up with Windows Vista that I was on the verge of going back to XP or 2000. This is a brand new computer, bought for me as a bonus from a business partner. Unfortunately, he doesn't know anything about computers and this one only came with 512mb RAM...barely enough to even run Vista (which it also came with, amazingly). 

Then I read a news article about Gutsy Gibbon's release and decided to give it a try. I have a dual boot setup with Vista, just because this is a work computer, but I have yet to boot Vista since Monday night, when I was testing out the live cd. 

I haven't had so much fun playing around with an OS since beta testing Whistler, which of course became XP. The best part is it only has what I want or need, none of the extra garbage taking up memory or disk space. I don't even have to get another 512mb of RAM to feel like I'm on a decently quick computer now, although I may throw it in there anyway.

I'm a web applications developer (mostly PHP, MySQL, XML, XSLT) and it was actually faster to set up everything I needed to work on Ubuntu than it was on Windows. The performance is great and it is nice to have an OS that I feel like can be exactly as much or as little as I want it to be. Try Ubuntu, in 3 days it beat more than 14 years of Windows experience. You can even install the Windows fonts and make the adjustment a little easier. I know I didn't answer any of your questions, but I just felt like advocating my new favorite OS with a fellow avid Win user.

---

### Post by herbster on 2007-10-25
> **spookyone said:**
> How can I know Linux is for me?

Try it :)

---

### Post by spookyone on 2007-10-25
> **avik said:**
> The best way to find out is to use LiveCDs, which you already know how to do.  Try the Ubuntu LiveCD if your computer can handle it.

And what are your specs?  Post them so we can tell how compatible your hard ware is.

The box I want to experiment on is not my main machine (obviously).  It's a cheap Compaq notebook with a 1.46G Celeron M, 512M RAM, 40G HD, I bought to play around with last winter when XP boxes were cheap in anticipation of Vista.  I bought two XP boxes at that time and am amused that XP boxes are reappearing in the stores now that Vista has proved not all that, after all.  The other is a nice Media Center I plan to keep on XP MCE.  But I digress.  (I do that often.  If it bothers anyone, say so, but I like to get to know people at forums.  So I share.)  The notebook claims to be Vista "capable" (and I'm SURE they mean absolute minimum spec for Vista Home Basic) and I guess I assumed that anything that could run Vista could handle Ubuntu.  I guess I really don't know what the minimum specs for Ubuntu are.  Can my little notebook handle it?  (It's really not that little--it's only impressive spec is that the 15.4" wide screen display is **really** beautiful.)

Probably my biggest reason for wanting to rid this box of Windows is that between the XP install and Compaq's "restore partition" the OS takes up more than half the little tiny HD!  I'm betting Ubuntu takes up less space. LOL

Do you need any other info?

Thanks to everyone for your input.  It's been a long time since I was a newbie, and it's a little scary.

---

### Post by Orbital75 on 2007-10-25
I honestly wouldn't worry to much about it, I have Xubuntu installed on my Laptop and
it does everything I want it to ( I'm not a Gamer either ).  I really like it much more so
than windows. I told myself after XP that I was going to really try an alternative and
Ubuntu is the one.  Honestly, the high system requirements mixed with the Microsoft
Genuine Disadvantage, and Product Activation did it for me. Also this whole advanced
DRM scheme made me dislike Microsoft even more.  Ubuntu is the right choice.

---

### Post by spookyone on 2007-10-25
> **HermanAB said:**
> Most laptops work OK - 99% of trouble are with getting the WiFi adaptor to work and you can use ndiswrapper with a Windows driver for that.

If you are a Windoze admin, then I'm not sure that Ubuntu is for you.  You may find the wizards lacking and the command line frustrating.  Mandriva Linux has wizards for everything and may be more to your liking: [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

However, if you *want* to get your hands dirty, then Ubuntu is the right one.

Cheers,

Herman

Now I'm a little hurt.  Do you think Windows Admins use wizards?  Seriously?  I use the command line frequently--there are still some things you can't do in Windows without the command prompt, (I don't know that this is true of Vista as I have deliberately avoided knowing ANYTHING technical about it.  My company is staying with XP until Vista is AT LEAST SP2) and I have also used Gnoppix and Puppy on live CD to remove Windows files that you can't remove from within Windows.  Most notably files from Norton or McAfee that refuse to stop running when Windows launches.  I'm a newbie, but I've had dirty hands before--in Windows and Linux.  In fact, I used Puppy first because I was in a hurry and it was the first one I was sure could read and write to NTFS.  I tried Gnoppix later, but still prefer Puppy in a pinch.

My impression was that Ubuntu was the most intuitive distro for Windows users.  Certainly it has that reputation in Windows circles.  In the end, I'd kinda like this notebook to be very friendly to Windows users as I have many friends who take up most of my free time removing spyware from their Windows boxes.  If I could move them all to Ubuntu I could save myself some real time.  If they could use this notebook and see how easy it can be to switch...

I'm not very socially adept, and I am responding as if you meant this seriously but I suspect you may be making fun of me.  If you are, well, I also heard Ubuntu had the friendliest people.  I hope that part is true.

---

### Post by spookyone on 2007-10-25
dem0, 

thanks.  I'm not even sure what my questions are yet, so not answering them is not a problem.  And I'm not sure I'd call myself an avid Windows user, I just fell into it as I was given a box running 3.11 back in 1998.  My first computer was a TRASH80 (LOL, I'm old) and I learned FORTRAN, COBOL, BASIC and IBM360-65 Assembly in college.  So those who suggested above that I haven't got my hands dirty are just plain uninformed.  Just because I admin a Windows office doesn't mean I can't code if I need to.  I grew up before realtime and GUI's.  I was good at Windows, no certification--self taught--I just got it.  So I ended up with a part time job as sysadmin for my brother's small (15 workstations/1 server) office.  I have a full-time job as well (doing paperwork for export of goods to Japan and China) and of course fixing endless friends and family Windows boxes.  Eventually, I'd like to get all friends and family on a *nix, so spware won't take up all my free time.  Ubuntu seemed a good choice.

Anyway, good to meet you, glad you like Ubuntu.  It confirms my feeling that Ubuntu will be a good fit for my current needs.  And maybe the forum is a good place to make friends, too.  Better yet, friends on whose computers I don't have to run Spybot S&D, Adaware, AVG and Hijack This!  LMAO

---

### Post by JKyleOKC on 2007-10-26
No need to be concerned about the capabilities of your laptop. I'm running Xubuntu on one ancient HP Pavilion (from 1999 or so) that has only 256 MB of RAM and a 30-GB disk, and the Xubuntu partition is only 6 GB. Less than 55% of that space is taken up by the o/s and programs -- and that box is the print server for my LAN. Another installation, on an only slightly newer Gateway with the same amount of resources, has even more free space in its Xubuntu partition, and it's also running Win2K in a VMWare server. In general, Xubuntu has about the same resource requirements as Win 3.11 but more capability than WinXP Pro.

The differences between Ubuntu, Kubuntu, and Xubuntu are primarily in the window manager used (Gnome, KDE, and XFCE4 respectively). The first two will take more resources than the last, but all three have similar capabilities.

---

### Post by candtalan on 2007-10-26
> **spookyone said:**
> Now I'm a little hurt.  Do you think Windows Admins use wizards?  Seriously?  I use the command line frequently--there are still some thin[...snip]

My impression was that Ubuntu was the most intuitive distro for Windows users.  Certainly it has that reputation in Windows circles.  In the end, I'd kinda like this notebook to be very friendly to Windows users as I have many friends who take up most of my free time removing spyware from their Windows boxes.  If I could move them all to Ubuntu I could save myself some real time.  If they could use this notebook and see how easy it can be to switch...

I'm not very socially adept, and I am responding as if you meant this seriously but I suspect you may be making fun of me.  If you are, well, I also heard Ubuntu had the friendliest people.  I hope that part is true.

(age comment: I started work in a factory manufacturing thermionic valves - vacuum tubes - remember them?


Hi and Welcome!
I read the wizards comment with a smile and thought it may have been written with slightly tongue in cheek. It can though have some serious truth because the more windows experience one has then the more initial difficulty is often found because the culture shock is so large. I was an enthusiast and serious pc user, recycling stuff (windows) for others and most of my experience was very specific to windows, as I found out. No worries, things I learned with linux are enduring and also general.

Intuitive:
Ubuntu is the distro I would recommend to you. It is easy to use, has immediate practical conveniences, but you still find you are close to the code. the community, (wizards aside), is the best, friendly and technical depth too.

FWIW I generally use Kubuntu, it initially looked more like windows, and the feature set is a bit richer than in ubuntu - both helped reduce the culture shock. And I have mostly avoided command line stuff. You might be ok with ubuntu of course. My family and friends generally get given kubuntu for this reason. However, ubuntu can also be loaded and chosen at log on time - (session) so you can have it all anyway.

You will certainly free up your spare time after moving friends to ubuntu - I have now stopped supporting anything but (k)ubuntu.

best wishes

---

### Post by spookyone on 2007-10-30
> **candtalan said:**
> (age comment: I started work in a factory manufacturing thermionic valves - vacuum tubes - remember them?


Hi and Welcome!
I read the wizards comment with a smile and thought it may have been written with slightly tongue in cheek. It can though have some serious truth because the more windows experience one has then the more initial difficulty is often found because the culture shock is so large. I was an enthusiast and serious pc user, recycling stuff (windows) for others and most of my experience was very specific to windows, as I found out. No worries, things I learned with linux are enduring and also general.

Intuitive:
Ubuntu is the distro I would recommend to you. It is easy to use, has immediate practical conveniences, but you still find you are close to the code. the community, (wizards aside), is the best, friendly and technical depth too.

FWIW I generally use Kubuntu, it initially looked more like windows, and the feature set is a bit richer than in ubuntu - both helped reduce the culture shock. And I have mostly avoided command line stuff. You might be ok with ubuntu of course. My family and friends generally get given kubuntu for this reason. However, ubuntu can also be loaded and chosen at log on time - (session) so you can have it all anyway.

You will certainly free up your spare time after moving friends to ubuntu - I have now stopped supporting anything but (k)ubuntu.

best wishes

Thank you, and I do indeed remember vacuum tubes! I took FORTRAN, COBOL, BASIC and IBM 360-65 Assembly in college. (You haven't lived if you haven't tried to put your 1000+ card Assembly program back in order after someone bumps you in the hall and you drop it!  It's also fun to put your page advance *inside* the DO loop and instead of 80 lines on one page you get 80 pages with one line each.)  I owned a TRASH80. I'm old.  Probably the comment was tongue-in-cheek, and I just get a little sensitive because, if you ask me, considering Windows' security and stability issues, administering a Windows network a huge skill set!  The fact that the OS itself is kind of a joke makes it very hard to keep such a system up-to-snuff.  Whatever people say about XP, Win2003 Server (I avoid Vista like the plague)  and the NT kernel in general being so stable, you still can't keep a Windows box up very long.  Don't get me started on malware.  I've personally seen Linux servers that have been up for years without rebooting.

Glad to hear someone has changed some friends and family over to a system that doesn't require constant spyware removal.  Quite frankly I spent most of my free time this week installing the (insert cuss word of your choice here) patch for Adobe Reader! (Dozens of times.)  I can now install Adobe Reader in my sleep, though, including removing the previous versions AND browser support for both IE and Firefox.  Not that it left me time for sleep.

Anyway, I downloaded Gutsy and tried the live CD.  I am looking at it with thoughts of putting friends and family who don't know command line exists on it.  It appears that it would work for this if you can get past the driver issues.  Everything worked with a little tweaking except I could not, for love nor money, get the dang thing online.  I have a Broadcom wireless card, and it appears that is a common problem.  But I also couldn't get online connecting directly to my cable modem via ethernet.  I just can't make it see the nic.  I have tried several things I found on the forum and have not been able to get online.  Anybody have ideas?

It was also deadly slow.  Is this also true of the installed or a symptom of running from the CD?  I have used Puppy liveCD , as well as Gnoppix, although I preferred Puppy so I used Gnoppix only once.  I use Puppy occasionally for rescuing Windows, and it runs wicked fast; although I'd expect it to as it runs completely in RAM.

Again, glad to find people my age here!

---

### Post by spookyone on 2007-10-31
I am proud and pleased to report that I am online using my Broadcom 802.11b/g Wifi card, on Gutsy Gibbon liveCD!  Other than using Puppy (and Gnoppix once) for Windows rescue This is my first foray into Linux!  Certainly I never tried to go online using it.  I am thrilled to report that, as someone in this thread pointed out, 'almost everything works.'  Well, after a little messing around with restricted drivers, Everything works!  Thanks for each and every post.  I feel like I've joined a community, and made new friends.

Thanks especially for the posts that reminded me that not all geeks are 20+ years younger than I am.

---

