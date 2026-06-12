---
title: "Arch vs Ubuntu"
date: 2017-08-14
forum: Arch and derivatives
---

### Post by ClickXT on 2017-08-14
I am thinking about giving Arch a serious look after some things that I have been reading.

For people that use Arch and Ubuntu -- any advice or words of caution? 
I use my Dell XPS13 (i7, 16GB RAM, SSD) for home office use but also to learn Linux while I am at home. (IT, System Admin - in 95% Windows environment otherwise)

Is Arch more "serious business" as I have seen it worded somewhere else or is that just elitist speak?

I realize that the typical answer is "try it for yourself and see if it's for you." But any information or input from those who are using or have I'd love to hear it from your perspectives.

Thanks-
CXT

---

### Post by TheFu on 2017-08-14
Arch is not business friendly. It is for people who want the latest and broken stuff ASAP.  Serious businesses need computers that work EVERY DAY.  I ran Arch for about a month. The install felt like Slackware from 1995 - too many questions.  Then it broke 2 times because some core libraries were updated and some dependent projects took a few days to recompile and catch up.  If that is acceptable to you, great!

IMHO, Arch is for bleeding edge developers and nobody else.
If you want complete control, either build your own distro or use gentoo.
If you want great stability with good patch management, use Debian-Stable, Ubuntu LTS or CentOS/RHEL.
If you want bleeding edge, use Fedora or Arch or Debian testing/unstable.  Expect occasional problems - probably 4x a year.

IMHO.

I used to be bleeding edge when younger. That was in the mid-1990s.  Had to compile everything manually and manually handle all the dependencies. It was a hassle - huge hassle.  

But you really should put it into a VM and see if you like it?  What is the risk?  20G of storage for a week?  Not really a big deal.

---

### Post by ajgreeny on 2017-08-14
I have heard of users simply getting fed up with the need to keep working on their OS rather than just doing their work when using the OS, Arch.

With Ubuntu the hard work of OS maintenance is largely done by all the devs who create .deb packages for installation, and the general ease of using the system, which makes life so simple for us, ie, we Ubuntu users, who seldom if ever need to mess around compiling source code and installing that way.

If you want a bleeding edge OS that uses the Arch packages and its general system but is also made a lot easier for users, have a good look at Antergos.  I am running it as a "look-see" in VBox and it is a lot easier to use than I understand Arch to be, though I admit I have never tried Arch proper, and doubt I ever will.

Without knowing your Linux competence it is impossible for us to tell you which will be best for you; for me and my uses it is definitely Ubuntu, well, Xubuntu actually, and it would take a lot to move me away from that.

---

### Post by ClickXT on 2017-08-14
I appreciate the feedback you two. I think I am going to just stick with Ubuntu/Xubuntu. Thanks.

---

### Post by TheFu on 2017-08-14
> **clickxt said:**
> I appreciate the feedback you two. I think I am going to just stick with Ubuntu/Xubuntu. Thanks.

Hopefully, you've posted the same question on the Arch forums to get their views as well.  Clearly, by posting here, you are getting biased responses. ;)

---

### Post by ClickXT on 2017-08-14
> **TheFu said:**
> Hopefully, you've posted the same question on the Arch forums to get their views as well.  Clearly, by posting here, you are getting biased responses. ;)

Fair enough. I'll do that.

---

### Post by Cope57 on 2017-08-15
I would suggest an Arch based distribution such as Manjaro.

---

### Post by ClickXT on 2017-08-15
> **Cope57 said:**
> I would suggest an Arch based distribution such as Manjaro.

Interesting. I'll check it out. Thanks for the tip.

---

### Post by ajgreeny on 2017-08-15
> **Cope57 said:**
> I would suggest an Arch based distribution such as Manjaro.
Exactly my point when I suggested you look at Antergos, another Arch based distro.

---

### Post by vasa1 on 2017-08-15
> **ajgreeny said:**
> ..., have a good look at Antergos.  I am running it as a "look-see" in VBox ...
Which option have you gone with?> The installer boots into a GNOME desktop, but during installation gives the options to choose between GNOME 3, Cinnamon, Mate, KDE Plasma 5, Xfce and Openbox desktop environments.

---

### Post by ajgreeny on 2017-08-15
I installed the xfce version which is always my DE of choice.

---

### Post by Dennis N on 2017-08-15
I have had Manjaro XFCE on this computer since Oct. 2015 and use it as the default startup OS. I multiboot my other OSes through its grub menu.  Manjaro has a good (and active) forum where it seems many of the distro maintainers are actively participating. So for an Arch based system I can recommend it.

---

### Post by 1clue on 2017-08-15
IMO arch would be difficult for a business or a must-always-work desktop. However all expert distros have a certain rhythm to maintenance. Once you become familiar you can keep the system up more easily.

I would recommend that you run both.  Set up virtualbox or kvm and build an arch box. Use it for something real, get to know what you're doing.

I maintain a bunch of Linux boxes. Most of them are Ubuntu Server, but I choose the distro most appropriate for whatever task is at hand. I don't currently use Arch on a regular basis but I have it installed on a vm. I also use Gentoo, which is a source-based distro, and several others like RHEL, CentOS, Suse and a couple others.

Brand loyalty is always huge. Ubuntu people tend to recommend Ubuntu variants to everyone, and many truly believe it to be superior. Same with Gentoo, RedHat, whatever. People best understand what they have, and familiarity tends to breed comfortable enthusiasm.

That said, Canonical gets no extra cash for each image installed, and the same can be said for every other distro. There's no prize for a user to only use one distro. There's no top score to keep. It benefits users to be familiar with several distros and to frequently dip a toe into many others, because it teaches us what's different about each distro, and the benefits and faults of each approach. There's a lot of common ground between all distros, and a little bit that's significantly different. The biggest visible difference for an end user is, in my opinion, the package management system.

Good luck and have fun.

---

### Post by ClickXT on 2017-08-15
Fantastic post and great insight. Thank you.

> **1clue said:**
> IMO arch would be difficult for a business or a must-always-work desktop. However all expert distros have a certain rhythm to maintenance. Once you become familiar you can keep the system up more easily.

I would recommend that you run both.  Set up virtualbox or kvm and build an arch box. Use it for something real, get to know what you're doing.

I maintain a bunch of Linux boxes. Most of them are Ubuntu Server, but I choose the distro most appropriate for whatever task is at hand. I don't currently use Arch on a regular basis but I have it installed on a vm. I also use Gentoo, which is a source-based distro, and several others like RHEL, CentOS, Suse and a couple others.

Brand loyalty is always huge. Ubuntu people tend to recommend Ubuntu variants to everyone, and many truly believe it to be superior. Same with Gentoo, RedHat, whatever. People best understand what they have, and familiarity tends to breed comfortable enthusiasm.

That said, Canonical gets no extra cash for each image installed, and the same can be said for every other distro. There's no prize for a user to only use one distro. There's no top score to keep. It benefits users to be familiar with several distros and to frequently dip a toe into many others, because it teaches us what's different about each distro, and the benefits and faults of each approach. There's a lot of common ground between all distros, and a little bit that's significantly different. The biggest visible difference for an end user is, in my opinion, the package management system.

Good luck and have fun.

---

### Post by 1clue on 2017-08-15
You're welcome.

Some distros are just plain better at one or two things. Back in the early days, Debian had better driver support than anything else, so they became the go-to distro for people with weird hardware. Ubuntu is a commercially supported distro based on Debian, and has both customer support and a dedicated, paid testing staff.  They also don't put any roadblocks in using commercial software on their platform.  All that is important to me.

Some commercial software runs best (or only) on one particular distro. If you want Oracle database, you'll use Oracle Linux. You used to use CentOS or RHEL for Oracle, but they've rebranded their own now based on RHEL.

If you want something very specific that isn't easily achieved by some other distro, then I use Gentoo. Gentoo lets you control fine details, like whether or not a feature is present all across your system. If you do or do not want "foo" feature support, you can compile every package on your box that has some sort of "foo" support to either have or not have that support. You can/must choose which init system to use, what logger, and so on. While not the most frequently used distro in my flock, it's my second most common and also my first favorite, but it does take more work than *buntu and it sometimes is less stable due to its rolling releases. It also tends to be a pain in the rear to get commercial software working because it's running newer versions of everything.

---

### Post by ClickXT on 2017-09-13
> **Dennis N said:**
> I have had Manjaro XFCE on this computer since Oct. 2015 and use it as the default startup OS. I multiboot my other OSes through its grub menu.  Manjaro has a good (and active) forum where it seems many of the distro maintainers are actively participating. So for an Arch based system I can recommend it.

Thanks for the advice. I have actually fully switched to Manjaro XFCE. 
--I believe it does Xfce better than Xubuntu. But that's just my opinion. From the AUR to the Theme/Appearance Options. 

Thanks for the advice all.

---

### Post by yoshii on 2017-09-29
> **1clue said:**
> It benefits users to be familiar with several distros and to frequently dip a toe into many others, because it teaches us what's different about each distro, and the benefits and faults of each approach. There's a lot of common ground between all distros, and a little bit that's significantly different. 

I agree with this very much.  
I enjoy trying out different distros just for fun and to stay educated.  
Some might call it distro-hopping, but I'm learning a lot along the way.  
It's really just a matter of computer literacy experience of different flavors of Linux.  
I do the same with Windows and MacOS versions every couple of years too.  Nobody calls that "Windows-hopping".  
The whole "distro-hopping" label is kind of derogatory.  I'm glad to be able to learn.  

I recently installed the low-latency kernel into Xubuntu and built a nice system exteremly similar to Ubuntu Studio.  
I could've installed Ubuntu Studio instead and it would've been quicker, but I did it because I wanted to know how and if it could be done.  
Now I know from experience the advantages (less bloatware and fonts; can manually install more up to date programs) and disadvantages (time consuming to install extras).  

Lately I've been reading about rolling-release distros such as Manjaro and I don't know yet if I prefer that to the LTS release schedule of Ubuntu's, but I'm going to try it out.  It seems like a nice venture.  I've tried a lot of different Linuxes over the years and I enjoy discovering how sophisticated each one is.  

Overall, I'd say try it out on a LiveDVD or flash drive or whatnot and then if it works out ok, carefully do a dual boot install (after reading about the caveats and issues of dual booting Manjaro).  Then if you like it better or not, you still have a pathway backwards or forwards.

---

### Post by 1clue on 2017-10-03
It's only "hopping" if you switch distros. If you have multiple distros  installed and they're persistent, especially if they're running  simultaneously, then it's not hopping.

Some of us forum users  have only one system, and that's OK. Some of those people use VMs or  dual/triple/n boot capabilities, and that's OK.

Others of us own multiple physical systems running mostly one distro, and that's also OK.

I run lots of systems *(both mine and for my work)*, and choose the distro for each based on my assessment of what is needed and which distro best focuses their efforts in the direction I prefer for that application. This is what I think people should do, because one size definitely does not fit all.

Nobody gets a prize for only using one distro. No money changes hands, no awards won, no glamor in being the winner.

The prize comes from familiarity with multiple distributions and their quirks.

---

### Post by Cavsfan on 2017-11-26
I have been using Arch Linux for about 2 years or so and it does not break randomly; it is very, very stable in my experience. 

It is what it is meaning there are no pre-installed packages, the only packages that are installed are what you choose to install. It uses the bleeding edge packages but, I've had zero problems on this  9 year old desktop. I have a wallpaper that has the Arch Linux logo and the saying "Arch Linux, it doesn't do a g******ed thing unless I tell it." And that pretty much is true. Nothing is installed automatically, You have to open up a terminal, enter commands to install packages and update your system. There is a way to ignore a package or packages, if you do not want to update them. Also a way to downgrade a package, like a kernel if you absolutely need to. I've done that without problems. 

I was told to install the Arch Wiki app on my phone, download the latest ISO and go from there. You have to read from the wiki how to install the system and once that is done, you decide what DE you will use, then you chose a web browser, etc. Nothing is there unless you install it. I chose Xfce which is much like Xubuntu.

It is not for the faint hearted and some people cannot install it. I tried for nearly a week and almost gave up. I let it go for a few days to clear my head, got back to it and it installed properly.
Once installed Arch is very hard to break. There were many times I thought "Oh no I'm going to have to re-install it." But, that was never needed. I was able to sort the problem out. Arch is probably one of the best maintained Linux distributions out there. There is a wiki for everything on Arch and if you open up a thread on their forum without doing your research and reading the wikis, you will be "harassed" let's just say for not doing so before hand.

I've read about Gentoo and would try that but, I'm not interested in compiling every single package on my machine from scratch, I'll take Arch Linux any day.

Everything works like the Fusion Icon and many of the Compiz packages that no other distribution maintains any more, works beautifully on Arch Linux. The Fish Tank, etc. There is the Arch kernel, which is bleeding edge, but thoroughly tested currently at 4.13.12-1 and there is a fallback kernel should you have an issue with the regular kernel. Also, you can install an LTS kernel, which is currently at 4.9.65-1. The LTS kernel also has a fallback kernel. These are constantly updated, after thorough testing. The LTS kernel is very stable and can be used if the regular kernel cannot. But, an update usually comes along and the regular kernel is fixed. I haven't encountered that, just saying there is an LTS kernel to use just in case.

Not, meaning to put anyone using Antergos down but, Antergos Linux is considered the easy way to install Arch Linux. It comes with a GUI and pre-installs a lot of software that you may or may not want/need, while Arch Linux has no GUI. You can see what I mean from this thread on Reddit: [Antergos vs Arch : archlinux - Reddit]("https://www.reddit.com/r/archlinux/comments/2chcc5/antergos_vs_arch/")

I do not even have a DM, I just boot into TTY1, enter my userid and password and it starts X and Xfce. I do not need things that take up room for no reason.
Arch never needs to have a clean install of an upgrade or anything as it is a rolling release and just keeps updating itself.

Arch Linux is the best OS I've seen yet. I've been with Ubuntu the longest and have a few installations on this box. But, I've tried Mint, Debian and a few others.
But, Arch is hands down the best I've used to date.

Addition: I'm just saying Arch is a beast and while installing it I learned quite a bit that I would not have using a GUI.

That's my 2 cents

---

### Post by jpberes on 2018-02-08
Or you can, like I currently do, install multiple Linux Distros in Virtual Box and play now and then with them. I have Ubuntu Mate 17.10 now as my main production machine and have Fedora (with Gnome), Antergos, Opensuse, Elementary, Ubuntu Budgie, Linux Mint 18.3 Cinnamon, Peppermint and Linux Lite on Virtual Machines, so I can test most of the Linux variant, being based on Red Hat, Arch, Debian and Slackware and test most of the Desktop environments being Gnome3, KDE Plasma, Pantheon, Budgie, Cinnamon and XFCE ...

---

### Post by Cavsfan on 2018-02-11
Apparently some people give Arch Linux less credit than it is due. It does not break all the time, 4 times a year, or whatever...

I've been using it since 2015 and never have I had one problem that kept me from using it for whatever I need.

It is my main Linux distro now and it is indeed on the cutting edge. The kernel is at **4.15.2-2-ARCH** already.

It is not necessary but, if one wants an LTS kernel, one can be installed. It is currently at **4.14.18-1-lts**.
It does not come installed, the same as any other optional package but, must be explicitly installed.

There is also a fallback kernel for both the regular and the LTS kernel.

My friend, the conky weather programmer, uses Arch Linux exclusively without the LTS kernel. He has never had a problem that he could not get by.

I have Windows 10, Arch Linux, Xenial 16.04 LTS, Artful Aardvark and the current Xubuntu developmental version Bionic 18.04 on my one and only 9 year old PC.

If I get a laptop, I would format the hard drive and install Arch Linux.

You have the choice of updating your system or waiting until you need to as there is no automatic updating on Arch. 
Many things like Compiz, the Fusion Icon, etc. are on the AUR (Arch User Repository) and can be left for as long as you want before updating.

There is also a couple of websites to look at before updating to see if there is anything to prepare for, one is [https://www.archlinux.org](https://www.archlinux.org)

So, ye of little faith, there is not one reason that Arch Linux can be used exclusively, of course you need to know what you are doing but, it's not as bad as some would have you believe.

I just prefer having some different operating systems to boot into is the reason I don't use Arch Linux exclusively.

---

### Post by Cavsfan on 2018-02-15
> **ClickXT said:**
> I am thinking about giving Arch a serious look after some things that I have been reading.

For people that use Arch and Ubuntu -- any advice or words of caution? 
I use my Dell XPS13 (i7, 16GB RAM, SSD) for home office use but also to learn Linux while I am at home. (IT, System Admin - in 95% Windows environment otherwise)

Is Arch more "serious business" as I have seen it worded somewhere else or is that just elitist speak?

I realize that the typical answer is "try it for yourself and see if it's for you." But any information or input from those who are using or have I'd love to hear it from your perspectives.

Thanks-
CXT

Did you ever try Arch? If you did, you want to have Arch control your Grub because there is no way to disable it. If it ever updates, the Grub will be on Arch.
But, for Ubuntu and any other Debian distro you can just install that Grub to the PBR like this [[COLOR=blue]_here_[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#If_you_multiboot_mutiple_Linux_installs_and_want_one_Grub_to_control_all_of_your_OSs").

---

### Post by QIII on 2018-02-15
All the foregoing notwithstanding, Arch has arguably the best documentation out there.  Thorough instructions with detailed explanations.

---

### Post by malspa on 2018-02-15
I've been running Arch for a little over four years. I've also used some Arch derivatives, and I currently have an Antergos installation, along with Arch and my other Linux installations. 

Arch is surprisingly stable. I check the news ([https://www.archlinux.org/news/](https://www.archlinux.org/news/)) before I do updates, and I try not to go too long between updates. I haven't encountered any serious breakage with Arch, or with any of the Arch derivatives I've tried. The updates can be kinda massive compared to anything in the Debian world but I run stuff like Xfce, LXDE, and Openbox in Arch so I don't have as much in the way of package updates as I'd have if I were running KDE or GNOME. 

Antergos is good; I basically run it just like I run Arch. I haven't tried Manjaro. I'd like to take a look at ArchLabs sometime, maybe. But in the end, I prefer Arch over any of its derivatives because I end up with a better, lighter, cleaner system with "straight" Arch. My two favorite distros right now are Debian Stable and Arch.

---

### Post by Cavsfan on 2018-02-17
I went a couple of days between updates. (From VinDSL's conky thread, Paramvir has conky checking pacman for updates every 3 hours) but, mine wasn't working. I looked at an error log and seen some ^M characters.

So, I edited that file with VIM and there was a Windows line feed (^M) on every line. I got rid of those and conky showed I had 45 updates. But, a kernel is only ~60MB and an Nvidia driver is >10MB. Every time a kernel comes out there is a corresponding Nvidia driver to go with it.

I use Xfce exclusively and boot to terminal, if it's TTY1, it will login and it starts X and Xfce; no DM at all. Many of the things that used to work on other distros like Ubuntu, the Fusion Icon for example, work perfectly in Arch Linux. I can right click on the Icon in the top panel and switch WM from Compiz to Xfwm4 or Metacity and switch back when needed. It also has a lot of the old Compiz stuff like the fishtank and several other cool things. There are 2 versions of Compiz too. Like QIII said, everything for Arch is well documented.

Regular updates are not bad but, some updates from the AUR can take a long time as it compiles right before your eyes. I use Vivaldi most of the time now and I installed it from a tar.xz file but, it get's updated via the AUR. It doesn't take long but vivaldi-ffmpeg-codecs, which is an optional dependency takes quite a while.

But, Arch Linux is a beast! I've tried Mint, Debian and can't think of others right now but, I've never tried any version of Arch except Arch Linux.

---

### Post by Clickster on 2018-02-23
'ClickXT' was my old account (I wish I could've gotten them merged?) but anyway - yes I used Manjaro and Arch Linux for a good while. 
Although I found both to be overall positive experiences I ended up coming back to Ubuntu. 

I did enjoy the AUR but Ubuntu's availability when it comes to *official* proprietary software/third party software is what I end up missing the most.

I enjoy having **OPTIONS** (especially as a SysAdmin) and for me Ubuntu provides that and stability while _enjoying_ Linux more than any other distro I have used for any considerable length of time. (Arch, Manjaro, Fedora, OpenSUSE)

Having said that - I will be giving Solus a spin next.

---

### Post by litlesam on 2018-02-23
I'm been using Manjaro along side of all the others. Must say Manjaro is fantastic but out of the box, it's ugly to look at.
Glad it can be customized easily.
Never tried Antergos yet, guess that will give me something to do next week.

---

