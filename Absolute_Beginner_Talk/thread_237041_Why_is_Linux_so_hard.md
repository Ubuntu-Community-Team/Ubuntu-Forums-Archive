---
title: "Why is Linux so hard??"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Homer_jay on 2006-08-15
I set aside a computer just to learn Ubuntu. I desparately want to get away from windoze but why is so hard to do even the most simple things?

I need to be able to see streaming media (WMV, Quicktime etc) in Firefox. I cant do it. There appears to be no SIMPLE way to install a plugin. Why cant I just download a file and just launch it to install a plugin? Instead I have open the terminal, download a bunch of files, then do this, do that, type in a few lines of code etc - in short, stuff that I don't understand. Am I missing something here?

I also want to be be able to have a better screen resolution that 1024 X 768 as I have a 24" Dell monitor. Why do I have to edit some file to get the extra resolution instead of choosing it in system-->screen resolution?

I'm sorry to sound so pissed but I've been really trying hard to understand but nothing seems to be simple apart the installation which was sooo smooth & simple!!

I'm on the verge of giving up and putting it down to another failed good idea.
Please help if possible.

Homer_J

---

### Post by Klaidas on 2006-08-15
Linux is different.
Please take time to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) - it answers all the questions, it helped me to understand Linux difference too ;)

---

### Post by sharperguy on 2006-08-15
Also for things like streaming video try automatix

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by cstudent on 2006-08-15
I don't know how long you've been at Ubuntu, but you're not going to learn a new OS in a day or two. Once you have learned some of the basics then you'll start to think that it is just as easy to do most things as it is in Windows. 

You can take a look at my website for starters. Maybe you'll find some helpful info there to help you on your journey into Ubuntu.

[Cstudent's Help Desk]("http://wjkirby.googlepages.com/")



Good luck,
cstudent

---

### Post by nero2150 on 2006-08-15
3 month ago I was just like you. ](*,) 
Im still a newbie in Linux but what make ubuntu to use is the 
easy installing of software. ;) 
I cannot count how many time i formatted the drive for a fresh install after a mess up.
[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)
This should help a lot forget about your terminal for complex codes install this to install most needed apps. :D 
Once youre getting use to it will come easy to do simple task

---

### Post by Perfect Storm on 2006-08-15
Hehehe...When I was a newbie once I blew up Corel-linux more than I can count. That was fun :mrgreen: ...but rich of learning.


> I set aside a computer just to learn Ubuntu. I desparately want to get away from windoze but why is so hard to do even the most simple things?
It's all about habit/what you are use to do contra a new way to do things.

---

### Post by agurk on 2006-08-15
I totally understand you being pissed, you are not an idiot. You may even be considered a computer pro by your friends. For example, I know it can be frustrating when you have this supposedly fantastic terminal window in front of you, but no idea what to write. All I can say is, give yourself time to learn.

I **know** it's easier said than done, here's what I posted a couple of minutes ago before spotting this thread... I think you'll see what I mean... [http://ubuntuforums.org/showthread.php?t=236612](http://ubuntuforums.org/showthread.php?t=236612)

edit: oh, and welcome!

---

### Post by bluntu on 2006-08-15
Linux is not hard if you are organized. The thing here is that you don't have to remember anything and you need to do it only ONCE. What you should do is keep a note (text file) and everytime you're reinstalling Linux just open up that text file and follow it. Here's an example of my TODO.TXT:

```

**# Faster scroll for FireFox**
Address: about:config
mousewheel.withnokey.action = 0
mousewheel.withnokey.numlines = 8 [number to scroll by]
mousewheel.withnokey.sysnumlines = false

**# Installing Quicktime/WMV**
$ sudo apt-get install mozilla-mplayer

**# Fixing Flashplugin crashes**
$ sudo apt-get install  alsa-oss
$ sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

**# Installing XCHM (to view *.chm files):**
$ sudo apt-get install xchm

**# Installing Java:**
http://java.com/en/download/manual.jsp

1: Look for Linux (self-extracting file which is a .BIN) download it and  make it "Executeable". Let's called java5.bin
2: sudo mkdir /usr/java
3: sudo cp java5.bin /usr/java/java5.bin
4: cd /usr/java
5: sudo ./java5.bin

```

You need to struggle only once, not twice so stay organized and LINUX will be easy to use. Trust me...

When you're following a tutorial to set up something and it works make NOTE of it and write down the steps like I did with my TODO.TXT.

---

### Post by Tom Brokaw on 2006-08-15
I too completely feel your pain.  The resolution thing drove me nuts, I ended up breaking the GUI, etc.  I think you're doing the right thing by setting aside a separate computer, as you can avoid the stress of "I just lost everything."  Give it some time, remember why you want to make the switch, and take a break if you have to.  It'll come.

---

### Post by xpod on 2006-08-15
AAARRHHH.......Exactly what i told myself to do ....BUT did`nt..

Only been ten-ish days or so and ive got everything working great BUT boy i wish i could remember some of the stuff i did.That taking notes is a real good idea but sadly one i neglected...till NOW

Then again.....sudo apt-get OR aptitude(i know..lol) is about ALL ive had to really use.

Got some line of code off automatix arnie to fix sound after getting automatix for easy java & flash installation....APART from that..

OH not to forget editing a couple of fstabs and mounting my xp

Apart from THAT......everything else is slowly but surely slipping into place

As i said to someone else....The MORE experience you have had and the longer you have used windows probably makes it seem all the more difficult than what i found it having only been using xp and pc`s full stop for a few months.....You`se are mabey quite SET in your (win)ways which i reckon is causing SOME people real trouble.

Sudo aptitude install automatix........THEN click what you need...DONE


Stick at it.......trust me,you wont look back(another one OFF the numbers bill).....we hope

---

### Post by John.Michael.Kane on 2006-08-15
Homer_jay now that we kow some of the issues your having. can you atleast list your system spec's? for use to help you with resolution issues this is needed. 

For the most part you should be able to get most of these issues solved provided your willing you do some CL work if needed.

Also posting while angry does not help get your point accross any better then had you been calm. relax breath step back from computer for a sec.

---

### Post by Ribs on 2006-08-15
If you stick at it long enough, you may end up having my problem...

I've not used Windows at home in a long time (we are talking years here). When I was forced to boot into Windows to install some language software which wouldn't work in Linux, I was lost. I kept getting frustrated at how the control panel was laid out, and annoying "help" bubble after help bubble, after... well, you get the idea. The system was slow and frustrating, and every piece of software I installed had a different look and feel to it, and it seems everyone in the Windows world wants more of your cash. My computer was suddenly slower, and performance was not consistant, sometimes the machine ran okay, other times it was drastically slower for no apprant reason. And Windows would simply not leave me alone until I rebooted to install some updates, dispite me saying I would "reboot later", it kept asking me again every five minutes until I relented.

When I rebooted back into Ubuntu, I felt at home again, safe and sound that I knew the system inside out. Everything was fast again, open, and secure. I was so nice to "be home". I wouldn't trade Linux for Windows ever again.

So basically, I actually find Windows a lot harder to use than Linux.

I, like yourself, found Linux fairly difficult when I started out. Stick with it, you may learn to love it in the long run, like I did.

---

### Post by xpod on 2006-08-15
AAARRHHH.......Exactly what i told myself to do ....BUT did`nt..

Only been ten-ish days or so and ive got everything working great BUT boy i wish i could remember some of the stuff i did.That taking notes is a real good idea but sadly one i neglected...till NOW

Then again.....sudo apt-get OR aptitude(i know..lol) is about ALL ive had to really use.

Got some line of code off automatix arnie to fix sound after getting automatix for easy java & flash installation....APART from that..
Ive asked many daft questions still though

OH not to forget editing a couple of fstabs and mounting my xp

Apart from THAT......everything else is slowly but surely slipping into place

As i said to someone else....The MORE experience you have had and the longer you have used windows probably makes it seem all the more difficult than what i found it having only been using xp and pc`s full stop for a few months.....You`se are mabey quite SET in your (win)ways which i reckon is causing SOME people real trouble.

Sudo aptitude install automatix........THEN click what you need...DONE


Stick at it.......trust me,you wont look back(another one OFF the numbers bill).....we hope

---

### Post by aysiu on 2006-08-15
Linux isn't so hard.

For philosophical and legal reasons, Ubuntu doesn't come with the non-free codecs you want. If you had installed PCLinuxOS, Blag, or Linspire (all Linux distributions), you wouldn't have that "problem."

Windows is just as likely not to recognize screen resolution as any Linux distribution is. Ubuntu detected mine just fine on my new monitor. On my old monitor, it didn't, so I added two lines to my /etc/X11/xorg.conf file. No big deal.

Install Windows on a computer it doesn't detect the screen resolution for, then try tracking down that driver. It's not pretty, and it'll make you want to join a Windows forum and start a thread entitled "Why is Windows so hard?"

Ask for help, and you'll get it. Complain, and you'll get responses like mine intermingled with help.

---

### Post by NewWithoutClue on 2006-08-15
Just think.. if you started using a computer that had Linux on it before you started using one with Windows on it.. you'd be complaining about Windows.

---

### Post by kaens on 2006-08-15
I too, had a really hard time installing linux the first time around. The first distro I tried to install was Debian stable, about a year and a half ago. 

I never got X to work.

But yes, if you are willing to learn a bit, and willing to poke around a bit, you can lose that "lost newb" feeling pretty fast.

I found [RUTE](http://rute.2038bug.com/index.html.gz) to be really helpful when I was learning my way around linux.

And hey, I've only been using *nix for approximately a year and a half now, and I'm learning how to write device drivers as we speak!

As a note, I can't get out of 640x480 4bit resolution under windows on one of my machines - and it is incredibly annoying; Ubuntu gets the resolution correct.

Also, keeping notes is important. It gives you something to reference, and helps you remember, period.

---

### Post by MyBigToe on 2006-08-15
I started with linux about a week ago, i set up the OS to work how i use windows (took a few evenings), and now I boot into linux instead of windows.. If theres something i need to do that i could do in windows, but dont know how to do in ubuntu, I have a quick search and if i find nothing, i just ask for help.
Most of the time people are very willing to help

---

### Post by The Waco Kidd on 2006-08-15
In the short term giving up might be a good idea. I had my first serious attempt to adopt Linux as my primary OS with Kubuntu 5.10 last autumn, it lasted about two weeks before the frustration of it all sent me packing.

When I tried again this spring I set up a dual boot with XP and promised myself when things got too hard, rather than spend endless days trying to get things working, I would let myself give up and boot into XP before the stress got too much. Happy to say, I'm having to resort to that less and less now, about two months in.

It does get easier.

---

### Post by ComplexNumber on 2006-08-15
> **Homer_jay said:**
> I set aside a computer just to learn Ubuntu. I desparately want to get away from windoze but why is so hard to do even the most simple things?

I need to be able to see streaming media (WMV, Quicktime etc) in Firefox. I cant do it. There appears to be no SIMPLE way to install a plugin. Why cant I just download a file and just launch it to install a plugin? Instead I have open the terminal, download a bunch of files, then do this, do that, type in a few lines of code etc - in short, stuff that I don't understand. Am I missing something here?

I also want to be be able to have a better screen resolution that 1024 X 768 as I have a 24" Dell monitor. Why do I have to edit some file to get the extra resolution instead of choosing it in system-->screen resolution?

I'm sorry to sound so pissed but I've been really trying hard to understand but nothing seems to be simple apart the installation which was sooo smooth & simple!!

I'm on the verge of giving up and putting it down to another failed good idea.
Please help if possible.

Homer_J
the "difficulty" isn't in learning linux/ubuntu. your difficulties arise from having to unlearn windows :).

---

### Post by meng on 2006-08-15
"Hard" is relative. Years ago when I was experimenting with Mandrake 7 and Redhat (forgot which version), and driver support was extremely thin on the ground, now that was hard! These days many systems' components work "out of the box" and for those that require minor tweaking, help is nearby with forums and chatrooms.

If you want help, then ask. Your original post is not asking, it's whining, and if you're looking for advice on tweaking your system, you're approaching it the wrong way.

Try starting a thread detailing one of the problems you are having (note the word 'detail') then you will find out just how "hard" Linux is to set up.

---

### Post by anasofiapaixao on 2006-08-15
I was going to tell my story but in awe I saw that everyone's journey is the same: You try a pair os distros and you run off back to windows, then you try "the one" and stay. You get frustrated. You think of getting back. You don't. You blow up your system more times than you can count. You eventually get used to it. If you don't game/don't have really apps that can't be replaced in Linux/are tight on disk space you just blow away your windows partition.

Let me tell you: I have Dapper since June (I did try SuSE when I was... uh, 14/15? - the only thing I used it was to play Beneath a Steel Sky; I couldn't configure internet or install software or ANYHTING - and Fedora Core 3 where I learned to...use yum and configure repos. That was all) and yesterday at my course's computer room I was just so uneasy...

When I have kids I would love that, when I'd put a windows computer in their hands, I'd hear "Mooooom! Where's the terminal??"

---

### Post by wpshooter on 2006-08-15
> **Homer_jay said:**
> I set aside a computer just to learn Ubuntu. I desparately want to get away from windoze but why is so hard to do even the most simple things?

I need to be able to see streaming media (WMV, Quicktime etc) in Firefox. I cant do it. There appears to be no SIMPLE way to install a plugin. Why cant I just download a file and just launch it to install a plugin? Instead I have open the terminal, download a bunch of files, then do this, do that, type in a few lines of code etc - in short, stuff that I don't understand. Am I missing something here?

I also want to be be able to have a better screen resolution that 1024 X 768 as I have a 24" Dell monitor. Why do I have to edit some file to get the extra resolution instead of choosing it in system-->screen resolution?

I'm sorry to sound so pissed but I've been really trying hard to understand but nothing seems to be simple apart the installation which was sooo smooth & simple!!

I'm on the verge of giving up and putting it down to another failed good idea.
Please help if possible.

Homer_J

Homer:

My advise is to do what you can and wait for this O/S to **mature** by giving the developers/programmers time to convert all of these functions, etc. that are bound to the terminal to a GUI interface so that you will not have to keep a notebook on in order to remember how to accomplish simple tasks that are already automated in M/S windows O/Ss.  I'm guessing about 2 to 3 years.  If you try to learn all of the commands and syntax of linux, about time you have them all down pretty good, the developers will have come up with GUI alternatives.

Good luck.

---

### Post by Ambimom on 2006-08-15
Try this:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I couldn't figure out why I couldn't get anything to play either and then someone gave me this link to install codecs.  I did and now just about everything works!  I'd also install Videolan (VLC) player if I were you.  It plays just about anything and everything.

The Real Media Player 10 works, but not like it does in Windows, but this link will explain.  

I agree that the "tweaking" gets a bit frustrating...but hang in...it does start to make sense.  

Good luck.

---

### Post by PenguinMan on 2006-08-15
[COLOR=Purple]Why is Linux so hard? Answer: Because it is Linux. :shock:

There is no unified GUI so you will always have fun trying to learn different programs. Also, compared to Mac OS X, there are no easy iApps for you to use.
[/COLOR]

---

### Post by AzureCrystal on 2006-08-15
> **Homer_jay said:**
> I set aside a computer just to learn Ubuntu. I desparately want to get away from windoze but why is so hard to do even the most simple things?

I need to be able to see streaming media (WMV, Quicktime etc) in Firefox. I cant do it. There appears to be no SIMPLE way to install a plugin. Why cant I just download a file and just launch it to install a plugin? Instead I have open the terminal, download a bunch of files, then do this, do that, type in a few lines of code etc - in short, stuff that I don't understand. Am I missing something here?

I also want to be be able to have a better screen resolution that 1024 X 768 as I have a 24" Dell monitor. Why do I have to edit some file to get the extra resolution instead of choosing it in system-->screen resolution?

I'm sorry to sound so pissed but I've been really trying hard to understand but nothing seems to be simple apart the installation which was sooo smooth & simple!!

I'm on the verge of giving up and putting it down to another failed good idea.
Please help if possible.

Oh no, don't despair, it just takes a while to get used to Ubuntu, remember most of the software out there is FREE for the taking, it will take you a solid month of sleeping and breathing Ubuntu until you get the hang of it, just think of how many years you have used Windows, it's a hard change, it's like learning sanscript !!

I made my nest as a VB/Delphi developer in Windoze for 20+ years, now I totally moved to PHP/MySQL dev tools, and Linux machines and I ADORE IT !!!  I still have a Windows machine running with software that does not yet exist in Linux, but here is a great story:

I JUST bought a Dell E310 PC, sweet deal, $449 with 17 lcd monitor and printer, the idea was to use partition magic to run a dual boot system with both Ubuntu Linux and WinXP, but after struggling with the sneaky partitions Dell uses, I just took a GIANT leap of faith and erased WinXP altogether from that machine, it is now a Ubuntu Virgin !!!  I NEVER thought I would trust Linux to that extent, and yes, sometimes there are streaming things, and windows media files that wont run, but most of it is because I have been lazy not to find all the FireFox plugins and various drivers I need...

Linux is SUPER WINDOWS, it's free, it's more secure, it is better and faster, and it is contantly evolving, probably why Gates has hesitated for so long to release Vista, he knows the Linux community will just roll over laughing at the bloat monster....

We can do this together, I am starting myself with this although I have used and taught myself Linux over the years, I just wished I converted sooner !!!

:rolleyes: :rolleyes: :rolleyes:

---

### Post by jason.b.c on 2006-08-15
> **bluntu said:**
> 



```
**# Fixing Flashplugin crashes**
$ sudo apt-get install  alsa-oss
$ sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"
```



Well that one don't work..!

> jason@Hp-Vectra-VL:~$ sudo apt-get install  alsa-oss
Password:
Reading package lists... Done
Building dependency tree... Done
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package alsa-oss has no installation candidate
jason@Hp-Vectra-VL:~$


:confused:

---

### Post by Drakkor on 2006-08-15
ARRRRR !!! LOL, Me be on thee Ubunutu vessel nigh about 2 months,and she never once ran asunder, and has guided mee well !! AAARRRRRR,MATEY ! :mrgreen:

---

### Post by niallabrown on 2006-08-15
I found taht the easyest way to get linx up and running was to install EASY UBUNTU.  You just put: ```
wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in
```  Into your terminal (Applications>Termininal) hit enter and put in your pass.  It takes you to a window that installs all your video, flash, skype, video dirvers and alot more just by ticking the boxes.


This is the webpage: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by Drakkor on 2006-08-16
It's available in Synaptic,if all you sources are up to date,including universe and multiuniverse.

---

### Post by 3rdalbum on 2006-08-16
> **NewWithoutClue said:**
> Just think.. if you started using a computer that had Linux on it before you started using one with Windows on it.. you'd be complaining about Windows.

I did, and I do! Windows is the frustrating operating system; having to restart after every new piece of software and every update, having to find and download binary installers that you just KNOW contain libraries that are already present on your system, having your interface drawing SOO SLOOOOWWWLLLLYYYYY after quitting a full-screen program, having to defrag before digitising a videotape, the system asking you what to do every time you insert a disc or USB device, etc.

Linux will get easier, but then I lead a charmed life...

---

### Post by Homer_jay on 2006-08-16
Wow,
Thanks guys. I'm a little overwhelmed!

I'm sorry that I sounded a little pissed but I initially bought a little Nokia 770 (internet tablet) because I wanted to do some 'couch surfing' and I wanted to learn about Linux. I love this thing but I quickly realised that if I fiddled with it, i was going to break it so I set aside a dedicated machine. I have not been trying long but I was frustrated when I just couldn't get anywhere.
You are all right about the 'being used to windows' thing. In the old days I used to program dbase & foxpro applications in DOS so I just assumed that I'd take to it like a duck to water, but that's not been the case. At least not yet.
I think I need to go back and 'unlearn' all the windows stuff and just start again!
I'm just going thru all the URL's in this thread and reading them so once again, many thanks.
Is Ubuntu a good distro to learn on ? - I only picked it because it's a Debian variant and Maemo (runs on the Nokia) is a Debian variant apparently.
I tried the easyubuntu thing - it seemed to work but then came up with an error that said something like 'fix broken packages first' or something like that so I'm still fumbling around in the dark a little!!

Once again many, many thanks!

H:D

---

### Post by Ptero-4 on 2006-08-16
Homer. Ubuntu is actually quite easy once you spend some time with it. I came here as an early adopter (4.10 preview edition) and I can tell you, I don't know my way around Windoze anymore. To my it's windoze the one that's hard.

---

### Post by bonjun on 2006-08-16
as they say take down notes,,, i got a notebook and wrote everything that i find on specific problem that i encounter plus copying everything in doc or txt file then attaching it to my email and **subscribing to the thread** which i think is beneficial to me,,, 
after a year of ubuntu, i still ask a lot of question or seaching the forums of what i need,, whoa man, i tell you, **this forums rocks!!!**

---

### Post by rck_hitokiri on 2006-08-16
its just your start and i too was once frustrated and pissed, well im still learning things right now and im gladly enjoying the frustrations, i mean when you really get a hang of it and even read some stuffs to learn things or two youll find out that it was wortg\h the trouble of having these troubles. check this site out and see if it helps you though.



[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) (for sound problems)


if you have anymore questions jus post it up here or youcan search forums or google it out. cheers

---

### Post by aysiu on 2007-01-21
Someone (who is not the OP) revived this thread from five months ago. I've moved the subsequent posts to [this thread](http://ubuntuforums.org/showthread.php?p=2045009#post2045009). Please continue your discussion there unless the OP comes back asking for help. Thanks!

**Edit**: Apparently, people keep trying to revive this *old* thread, so I'm closing it. If the OP has a new issue, she or he can start a new thread. *This thread is five months old!*

---

