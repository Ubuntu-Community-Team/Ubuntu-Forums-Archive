---
title: "How On Earth Do I Download Programs On Ubuntu"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
HELLO PEOPLE
I am a total novice user of the ubuntu os so i need some help please.
I have installed the os with ease , but i try to download programs like avg etc through firefox and i try to open it and i tells me it dosent recognise the program or similar to this.
Also when i ticked the box for the updates they downloaded but when the computer rebooted the screen was in a very low pixel rating.
Any help would be wonderful to get away from the bill gates treatment.
Cheers

---

### Post by slimdog360 on 2007-08-18
Ubuntu, or any linux, can not run any file which ends with .exe     take a look at the file name of that avg file you just downloaded, it will end in .exe

If you do download any programs its best if they have a .deb extension. For now though while you are still learning its best to use the "add/remove programs" feature built into Ubuntu.

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
So once i have downloaded the file in firefox i go to add remove programs.
What do i do next.
Thank you

---

### Post by infoseeker on 2007-08-18
Don't download anything with Firefox (except flash, etc).  Use Synaptic Package Manager (Gnome) or Adept (KDE) to install software.

---

### Post by scrooge_74 on 2007-08-18
Forget about downloading stuff, all you need is in Add/Remove programas or use Synaptic

Linux has what it is call a package manager which takes care of dependencies between programs.  Everything you need to download comes from what is call repositories.  There everything is store.  You need somthing you can find there in the official repositories in 99 % of the time.  At the most you have the enable some of the repositories that are not mantained by Ubuntu.  

The system is base on Debian and the Debian package manager (synaptic) has like 20,000 different programs to download.

And yes if you want to install something that you want to download using Firefox it has to be a linux version which needs to end in .deb

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
So do i download files in firefox or with synaptic or through add remove programs
How do i add programs in the add remove program feature.
Sorry to sound like a cabbage but this is all new to me.

---

### Post by slimdog360 on 2007-08-18
to avoid confusion Id suggest just using what is called add/remove programs. In the upper left of the screen you will see the 'applications' menu. Click on this. At the bottom of the menu there is something called 'add/remove programs', click on that. 

The way ubnutu works is by having one big place where heaps of programs are all stored, you can download them via this 'add/remove programs'. This way you do not need to search the internet for programs to download, plus you know that these programs from here do not conain any viruses or anything. You should search the net to find out more.

Add/remove programs is different from the one in windows. You can not install programs which you have personally downloaded from firefox with it. You do not need to anyway as pretty much all of what you need is in add/remove programs.

---

### Post by scrooge_74 on 2007-08-18
Yes you can search the internet for things you need, but most likely they will already be in Synaptic (or use the add/remove feature). 

In the long run you will get the hang of it. [This]("http://www.psychocats.net/ubuntu/installingsoftware") should explain things a little further.

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
i have had a look on this already and i didnt know which of the programs were firewalls or anti virus programs
Could you recommended a very good anti virus and firewall i could use to get me started on the linux road.
Cheers Mate

---

### Post by original_jamingrit on 2007-08-18
Actually, he means that most programs are *downloaded through* the Add/Remove Programs.  If you download an exe file, it will not work (maybe unless you have wine installed).  Files that are .exe are usually the windows version of the program.  You probably want files that you either get through Add/Remove or if it's not there, Synaptic Package Manager(System->Administration->Synaptic).

When you're feeling a bit more experienced, you could download a .deb file and just double-click on that, and follow the instructions.  Downloading source tarballs aren't hard either, just enter```
tar -xvzf TARBALLNAME.tar.bz2
```or```
tar -xvzf TARBALLNAME.tar.gz
``` and read the README instructions to see how to compile it.

Just be careful to download stuff from a reliable source.  Downloading viruses does nothing, but making them executable will.


As for the low pixel rating, try going to System->Preferences->ScreenResolution

---

### Post by original_jamingrit on 2007-08-18
> **FOBBEDOFFWITHCRAP said:**
> i have had a look on this already and i didnt know which of the programs were firewalls or anti virus programs
Could you recommended a very good anti virus and firewall i could use to get me started on the linux road.
Cheers Mate

You really don't need antivirus or firewall for Ubuntu, but if you really want to manage your firewall do a search for "firestarter" in Synaptic.

---

### Post by bapoumba on 2007-08-18
Moved to "Absolute Beginner Talk" support forum.

May be this can also be of some help:
[https://help.ubuntu.com/7.04/add-applications/C/index.html]("https://help.ubuntu.com/7.04/add-applications/C/index.html")

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
Sorry but i dont know how to enter codes or a command (im new and i want to make the change for good)
My screen resolution is maxed out at 800 by 600 and in the linux version of device manager it looks like it dosen't recognise my graphics card as it say unknown.
Cheers people

---

### Post by punong_bisyonaryo on 2007-08-18
I think we shouldn't confuse him with tarballs for now, but I'm sure he'll learn about that in due time.

You don't need anti-virus, this is the world of Linux.:) Don't worry too much about the firewall for now, as it is, try out your Ubuntu "fresh", I know that sort of thing is a no-no with Windows, but this is Linux.

Just go find programs you like and take it out for a spin.

As for your video card, is it an Nvidia, ATI, or Intel?

---

### Post by scrooge_74 on 2007-08-18
> **FOBBEDOFFWITHCRAP said:**
> Sorry but i dont know how to enter codes or a command (im new and i want to make the change for good)
My screen resolution is maxed out at 800 by 600 and in the linux version of device manager it looks like it dosen't recognise my graphics card as it say unknown.
Cheers people

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I recommend you read some before going any further to avoid future problems.

As for your video card you should post what type of card you have so we can help

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
Sorry i suppose i have been used to windows for so long / it just seems the thing i would automattically do  when i would install an operating system
I have been playing with ubuntu on and off for a while now and i like it very much indeed.
My graphics card is a radeon 9200
Cheers

---

### Post by scrooge_74 on 2007-08-18
> **FOBBEDOFFWITHCRAP said:**
> Sorry i suppose i have been used to windows for so long / it just seems the thing i would automattically do  when i would install an operating system
I have been playing with ubuntu on and off for a while now and i like it very much indeed.
My graphics card is a radeon 9200
Cheers

Good luck with your video card, maybe [this]("https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI") will help  from the community documents.

---

### Post by Cphood on 2007-08-18
There is an additional graphic interface for installation/removal and configuration of
the most popular add-on programs for debian based linux of which Ubuntu
7.04 is.  It is very simple, you just download it, respond to the screen
prompts,  and it installs into the "Applications" menu of Ubuntu.  From
there you can select from a broad range of programs such as browsers,
email clients, utilities, drivers, players, burners, codecs etc.  You
must have an Internet connection for the selected program to download,
but installation is point and click.  The program is "Automatix" and
their Internet address is: [http://www.getautomatix.com](http://www.getautomatix.com).  This program
combined with the "Add/Remove" and "Synaptic Package Manager"
repositories give the non-tech person a menu, prompt driven, point and
click installation environment that does not require any command line
knowledge or skills for installation or removal of any programs that
they may need.  The only difficulty is knowing what to select.

---

### Post by Myglaren on 2007-08-18
Welcome to Ubuntu **FOBBEDOFFWITHCRAP**!

It's not easy but try and forget Windows methods and learning Linux ways will become all that much easier for you.  Be prepared to do a fair amount of reading on these forums as the problems you face have already been faced and overcome by many.

Try not to do too much and get in too deep all at once, do a few simple things and become familiar with them then move on to something a bit more advanced.

None of it is difficult but you do have to learn it mostly from scratch.
  Keep telling yourself *It Isn't Windows*.  It's like learning a new language, in the beginning it is semngly impossible but then something clicks and you have an "AHA" moment.  It progresses in stages.

The advice offered above is all good.  You will probably find the Psychocats site linkd to above an invaluable resource for your first steps, I know I did and still visit there regularly.

For your graphics card look for/ search for advice on installing ATI graphics cards here on the forum.
Can't offer any better advice than that I'm afraid as I use Nvidia graphics.

Anyway, welcome again and I hope your experiences are pleasant ones.

---

### Post by Myglaren on 2007-08-18
Can I just say as a rider to **CPhood**'s post - he was quicker on the keyboard than I am - that Automatix is certainly an excellent suggestion BUT I tried it a few times and it trashed my filesystem beyond repair which meant reinstalling Ubuntu from scratch.  No big deal admittedly but not something you want to do every day.
Maybe it is just me or perhaps an idiosynchracy of this particular machine but Automatix and I are incompatible, it seems.

---

### Post by punong_bisyonaryo on 2007-08-18
At the risk of some people who might disagree, I recommend [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). What it does is it automatically downloads and installs your video card driver. I'll also link the .deb file here for your convenience. Click [here]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb") and download and start it by clicking on it (similar to windows-installers-method, so you should have no problem I suppose).

I've read some problems about Automatix, such like it doesn't follow Ubuntu package standards, etc.If it works for you, It'll make your life easier. But the opposite can also be true.

---

### Post by FOBBEDOFFWITHCRAP on 2007-08-18
HELLO EVERYBODY
Thank you for all of your comments and suggestions.
At present i am on a windows pc and i am about to run ubuntu on one of my other pcs and  use your advise as a starting block for my linux learning.
Many Thanks everybody
I will keep you posted how i get on and maybe share with everybody methods that i have used.
Cheers
Dave

---

### Post by hyper_ch on 2007-08-18
first of all:

Forget about downloading through firefox, about .deb, about .tar.gz, about automatix, about envy...

Start off reading thsi here:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Many questions will be solved..

---

### Post by tyggna1 on 2007-08-18
I've been using Ubuntu for almost a month and just found out how to really utilize my graphics card today.

I do tech support for windows--professionally--but I still have to ask myself "how to I copy a restricted file in Linux?"  on occassion (sudo cp /path/of/file/fileyouwantto.copy /path/of/copy/nameofcopied.file, FYI).   Let me share some things that I found useful during my first few weeks.

Windows is fundamentally different than Linux.  Windows has a kernel that commands everything your computer does--and so does linux but the similarities seem to end there.  
Command:
In Windows:  the kernel will check on the harddrive for various "drivers" that will tell it how to use the hardware on your computer.
In Linux:  the ability to use your hardware is programmed straight into the kernel--there aren't any "drivers," for the most part.  It does have one exception, called "restricted drivers," which (anyone may correct me if this isn't right) is there for legal reasons primarily.  All the "drivers" built into the kernel are open source--meaning anyone can change them.  The restricted drivers are there for non-open source drivers.

Software:
In Windows: All programs are self-sustaining.  Meaning that they can run in and of themselves as soon as the programmer compiles it.  They might not run *well* if you don't have the drivers that supports them, or some files that the program uses are corrupt or missing--but they will still attempt to run.

The difference here is kinda like a lego car vs. a solid plastic toy car.

In Linux:  Programs are dependent on packages.  To run a program--you need all the base building blocks in place--which Linux calls packages.  If a package is missing, then the program won't even try to run--much like forgetting to put the wheels on your lego car.  Fortunately--Ubuntu will often tell you what peice it's missing.

Security
In Windows:  The security is something like:  You have it until I say you don't.
In Linux:   The security says:  You don't have it until I say you do.

Let me elaborate:  Windows will let anything install on it.  It does this to be more accessible to a new user, or someone who isn't familiar with how a computer works.  Linux won't install anything without your express permission and root password to verify that you want to change something.  Occassionaly, Ubuntu will ask for your permission to install _additional_ software/packages (they really are the same thing), in order to satisfy dependencies.  

Because of this security policy-- a virus would be a pointless peice of software in linux--as you would have manually change the "permissions" on it so it could run, and then run it yourself, and then punch in your password to give the virus clearance to change something crucial or important on your computer--even if it did download itself.  Hence the previous suggestion to not get software from "shady repositories"

Novice users:
In windows:  You paid us to make it work, so we'll make it work at whatever the cost!  Our "cost" includes:  The money you pay us,  an inability to change crucial aspects, being well known,  making a number of enemies who resent us, find our weaknesses, and then exploit them.
In Linux:  Welcome to the club!  Hope we can help, but you really do need to learn a lot.  You can change anything you want, and we won't stop you--afterall, what would we ever really learn if there weren't mistakes?

Installing:
In Windows:  It's download, point and click, and click, and click, and "I agree" and wait, and click, occasionally reboot and you're done.

In Ubuntu:  It's select or add a repository (or an online database that contains various peices of software or links to that peice of software, and also "packages" that item of software in such a way that all the dependent packages are installed with the software),  and then select either the packages you want to download (Synaptic package manager) or select the software you want and let the add/remove programs select all the packages you need.

Maintenance:

In Windows:  Defragment, chkdsk, virus scans, firewall, pop-up blocker, spyware scans, disk cleaner--and sometimes using msconfig to change the way you boot up.
In Linux:  Maintenance is not required.  You just need more time to set it up so it works the way you want it to.


I hope this has been helpful.  It's some of the basics I've picked up along the way. I wish I would've read this my very first week of using Ubuntu--it would've made my experience with it much more bearable and enjoyable. [ Windows is not Linux]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by scrooge_74 on 2007-08-18
I like the lego car vs plastic car, it says a lot on the differences.  I really like to  use different colors when making my car, is more fun in the long run. :D

---

