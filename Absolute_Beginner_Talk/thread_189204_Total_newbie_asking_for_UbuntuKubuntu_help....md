---
title: "Total newbie asking for Ubuntu/Kubuntu help..."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-04
Hey guys,

Wow where do I begin? I’ve been a “Microsoft boy” since Windows 3.1 but it was with Windows 98 that I had my first bad experience. I’ll never forget calling tech support with an issue and getting chastised for installing the operating system on two PC’s in my home. Since then things have gone from bad to worse with their restrictive policies like “product activation” and “genuine validation”. So while many of my collegaes at work are getting excited about the impending release of Windows Vista, I’m left wondering, “How are they going to screw me over this time”? Combine that with the fact that they are big bankrollers for organizations like the BSA and you realize just how greedy corporations are changing the landscape of computing for the worse. I’m just to the point where I don’t want Microsoft to have any more of my money because I’m scared to think of how they’ll use it to attack me in the future! I just can’t live that world any longer and I’m dying for a viable alternative.

I’ve dabbled with a few Linux distributions in the past (Red Hat, SuSE, & Mandriva) but so far I have yet to make a successful transition to Linux on any of the three hand-built computers in my home. With the success of FireFox and the buzz around Ubuntu, it’s only natural that I’d give Linux another look. I’ve downloaded both Kubuntu v6.06 and Ubuntu v6.06 and installed both on one of my NForce 4 boxes. While both are more polished than any Linux Distro I’ve ever seen, I’m still having a lot of trouble getting them properly configured. Now I’m not bashing the OS I’m just hoping someone else out there has hardware like mine and is currently using Ubuntu (or Kubuntu) for the same applications I plan to use it for. My eventual goal is a setup with two workstations and a server. For now, here is what I want to use the workstations for: 

[LIST]
[*]Web Surfing (FireFox)
[*]Image Editing (Gimp works here)
[*]Web Design/Development (No idea what to use here)
[*]Media playback (MP3’s AVI’s, MPEG’s)
[/LIST]

Hardware specs for each workstation is:
[LIST]
[*]CPU - AMD 3200+ ATHLON 64 (Socket 939) 
[*]Motherboard - DFI LANPARTY UT nF4 SLI-DR
[*]RAM - 2GB CORSAIR PC3200 DDR
[*]Video - XFX GeForce 6800GT
[*]Sound - Soundblaster AUDIGY 2 ZS
[*]Storage - Dual Maxtor 300 GB Hard Drives (SATA 150)
[/LIST]

I read Aysiu's post on "Is Ubuntu For You?” and I know the Linux community tends to frown on people who ask a million questions rather than research the issues for themselves. However, please understand that I live in a part of Louisiana that is not big on technology. Also I am the only technical person in my immediate circle of friends and I feel like I have nowhere to turn for quick answers when I get frustrated. The only way I’m ever going to get this thing set up properly is with some help from the community, and believe me I *WANT* to make this work so badly. I really respect and admire the ideology behind the open source movement and want to embrace it wholeheartedly. However I have to face the fact that Windows has ruined me in a lot of ways. To loosely quote Yoda I must “unlearn, what I have learned”. In order to do that I’m afraid I’ll need someone to “hold my hand” initially. Is there anyone out there up to the task?

---

### Post by aysiu on 2006-06-04
[QUOTE=ZeusABJ]
Web Design/Development (No idea what to use here)[/quote] I would recommend Quanta, Nvu, Bluefish, or just a plain, old text editor. > Media playback (MP3’s AVI’s, MPEG’s)
 For MP3s, I would recommend Banshee or AmaroK. For movies and such, MPlayer.

> I read Aysiu's post on "Is Ubuntu For You?” and I know the Linux community tends to frown on people who ask a million questions rather than research the issues for themselves. Maybe "the Linux community" does, but the Ubuntu community certainly doesn't. Ubuntu means "humanity toward others," and people around these forums tend to practice that (with few exceptions).

Since you build computers yourself, you're in good company. Many users (myself excluded) here build computers from scratch and can recommend good Ubuntu-friendly hardware. That way, when Vista comes out, you can build yourself a nice, Ubuntu-compatible box with all the bells and whistles.

---

### Post by ZeusABJ on 2006-06-04
Thanks for the advice/words of comfort Aysiu. I guess I'm just a little frustrated by how steep the learning curve really is. I spent most of the weekend just trying to install the video drivers from NVIDIA’s website and a web development application that seemed similar to Dreamweaver. Now I'm not even sure I ever needed those NVIDIA drivers in the first place and I can’t seem to get all the additional required components installed that I need to make that Dreamweaver clone work. Being able to just "double-click" an installer to load an application or driver under Windows really spoils you sometimes. Also (as your article indicated) I am having a great deal of difficulty adapting to using the command line so much. 

Even more frustrating is the fact that I'm a big "hot key" guy and a lot of the hotkeys I typically use under Windows either don't work or do something totally different in Ubuntu (and Kubuntu). It’s looking more and more like I may have to try and make Kubuntu work before going with Ubuntu. KDE just seems a bit friendlier to people trying to transition over from Windows. Hopefully someone else with similar application needs and hardware specs will see my thread and share how they were able to overcome some of their frustrations. I’m just going to back off a bit for now and try to come back to it later with a cooler head.

---

### Post by aysiu on 2006-06-04
I can totally relate to your experience.

When I first started using Ubuntu, I tried to install the NVidia driver (because I have an NVidia graphics card), but I later realized... there's no noticeable difference in performance between that and no NVidia. Likewise, I tried installing the K7 (AMD) kernel instead of the default i386 kernel. Also realized there was no noticeable difference in performance.

As far as installing software, these two links should have you covered:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And if you still find Ubuntu too command-line-heavy, consider Mepis. It has proprietary codecs immediately available. You can install NVidia drivers with the click of the mouse (one click, not several clicks). It was my first distro, and I couldn't have imagined using Ubuntu at the time (Ubuntu scared me off). Ubuntu is, however, a great second distro.

---

### Post by nalmeth on 2006-06-05
> Thanks for the advice/words of comfort Aysiu. I guess I'm just a little frustrated by how steep the learning curve really is. I spent most of the weekend just trying to install the video drivers from NVIDIA&#8217;s website and a web development application that seemed similar to Dreamweaver. Now I'm not even sure I ever needed those NVIDIA drivers in the first place and I can&#8217;t seem to get all the additional required components installed that I need to make that Dreamweaver clone work. Being able to just "double-click" an installer to load an application or driver under Windows really spoils you sometimes. Also (as your article indicated) I am having a great deal of difficulty adapting to using the command line so much. 

Even more frustrating is the fact that I'm a big "hot key" guy and a lot of the hotkeys I typically use under Windows either don't work or do something totally different in Ubuntu (and Kubuntu). It&#8217;s looking more and more like I may have to try and make Kubuntu work before going with Ubuntu. KDE just seems a bit friendlier to people trying to transition over from Windows. Hopefully someone else with similar application needs and hardware specs will see my thread and share how they were able to overcome some of their frustrations. I&#8217;m just going to back off a bit for now and try to come back to it later with a cooler head. 
Yeah, it's frustrating at first, but hang in. Look at this, [my first ever thread]("http://www.ubuntuforums.org/showthread.php?t=89979"). I was quite thick-headed, trying to make ATI and NVIDIA driver's work for my intel card, when I never realized it was setup out of the box on the 386 kernel.

When you mention mulitmedia, do you mean getting codec's installed? There are many way's of going about this, each varying in difficulty from manual, to automated. Click Almighty Automatix in my signature for automation, or visit this site for an explanation and install instruction's.

[http://wiki.ubuntu/RestrictedFormats]("http://wiki.ubuntu/RestrictedFormats")

So is your NVIDIA setup? I tend to [link to this site]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation") for installing their proprietary driver. 

Using gnome? To edit the hotkey's go to SYSTEM - PREFERENCES - KEYBOARD SHURTCUTS
On my keyboard, they weren't enabled by default, but they all work (volume, wake sleep, power, I have 16 extra mod-key's).

There *are* actually double-click installation files, if you download a .deb file (for ubuntu), you can double-click it and install the package with gdebui.

Use the forums. Don't hesitate to ask many questions. These people are wandering around here and spending time anyway, ask away.

---

### Post by ZeusABJ on 2006-06-05
So let me get this straight Nalmeth, you can actually create your own Hotkeys under Gnome?! Wow that’s pretty tight! I'm just so used to Microsoft's mentality of "we're going to tell you how to compute" that I guess I've lost some of my ability to "think outside the box" like that. So about those .deb files, is there some sort of "repository site" where I can download those? I was under the impression that Linux used package manager to list software for download and installation. Anything beyond those you had to use a lengthy series of commands to get something running.

Thanks again for your advice Aysiu, I'm at work right now, but when I get home I'll give those links a look. Maybe I'm making this harder than it has to be. However one thing I'm still confused on, do I just not need to download and install the NVIDIA drivers? Are you saying they come in the Kernal? And if so do any of you know why my system seemed to "stutter" a bit when I draw a box around multiple objects on my desktop. I assumed this little performance hit was because I needed to install a video or chipset diver. I have similar issues with Windows XP after a clean install. Installing the drivers (chipset and video) from NVIDIA’s site is always required to fix it.

---

### Post by aysiu on 2006-06-05
[QUOTE=ZeusABJ]So let me get this straight Nalmeth, you can actually create your own Hotkeys under Gnome?! Wow that’s pretty tight![/QUOTE] You can do this in Gnome, KDE, and XFCE. Linux is all about customization. > So about those .deb files, is there some sort of "repository site" where I can download those? I was under the impression that Linux used package manager to list software for download and installation. Anything beyond those you had to use a lengthy series of commands to get something running. Well, the .deb installation usually doesn't check for dependencies. I'm not sure if GDebi is a bit more sophisticated than that and actually integrates with the package manager. Maybe Nalmeth can confirm or deny that.

> Maybe I'm making this harder than it has to be. I always advise caution over haste. It's better to realize, "Oh, I made such a big deal over that for nothing" than "Oh, s**t. What the hell did I just do?" > However one thing I'm still confused on, do I just not need to download and install the NVIDIA drivers? You may. You may not. I don't know your system. I'm just saying on my system, they didn't make a noticeable difference. > Are you saying they come in the Kernal? No. NVidia is proprietary. Ubuntu uses the Nv driver, which is an open source approximation of the NVidia driver. If you want the genuine NVidia (i.e., if it *does* make a noticeable difference), then you need to install that separately. > And if so do any of you know why my system seemed to "stutter" a bit when I draw a box around multiple objects on my desktop. I assumed this little performance hit was because I needed to install a video or chipset diver. So you may need it after all. I'm just saying that a lot of times when people offer you tweaks, they may not be necessary.

---

### Post by sweeper on 2006-06-05
I am 4 days into my first experience with any Linux and I would advise you stick with it, I have spent hours banging my head against the wall trying to install certain things so I know how frustrating it can be, but there is a nice sense of satisfaction when I do learn a little of what I am doing (I am still stuck on certain things but I don't need them sorting out immediately).

I had to install my ATI drivers, I don't know about Nvidia but I could see by the screensavers things were going slow.

Also I would recommend installing the 32 bit Ubuntu for a noobs like myself :)

Stick with it, Micrr$oft can go *&$£"%$ :)

---

### Post by joshrobinson on 2006-06-05
have you played around with synaptic package manager under ubuntu/gnome?
its a very good program, its under system, administration, synaptic package manager

you can search for files that you want, such as a html editor, music/movie player
and it installs all dependencies for you :-D so there isnt a problem tracking down deb's of everything else it needs.. sometimes tho  you will have to download a .deb if you cant find it in synaptic.. or you can compile from source, but you have to have the build-essential package in synaptic

synaptic and aptitude work on internet repositories, so you just tell it where the deb is and you can get it from the repo's.. say you want to install xmms, you can either use synaptic and search for it or use terminal and t ype this command

```
 sudo apt-get install xmms
```
and it will grab all the needed files from the repo's

---

### Post by ZeusABJ on 2006-06-05
Heh, thanks so much Aysiu for breaking down all my questions and answering them so well. I really appreciate that. I'm thinking I still have some sort of performance issue relating to drivers or my current configuration. Does anyone else out there have hardware specs like mine? If so what steps did you take to optimize performance? Also to answer Josh Robinson, I did play with Synaptic and was very impressed, but (if memory serves) it was lacking some of the applications I needed (like a Dreamweaver clone). I think Kubuntu used a different package manager called "Adept". It had an application listed as a web development platform (can't remember its name) but when I installed it I kept getting this error message that some dependency was not installed. I'll try some of those terminal commands and see if I have better luck.

Oh and Sweeper, I already discovered that 32-Bit was the route for me the hard way after TRYING to work with 64-Bit Ubuntu!!! Don't worry, I'm not throwing in the towel just yet!

---

### Post by aysiu on 2006-06-05
If you're having dependency issues, you may have conflicting repositories.

I'd get a fresh list from here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try ```
sudo aptitude update
sudo aptitude install quanta nvu bluefish
``` and try out Quanta, NVu, and Bluefish--see which one you like best.

---

### Post by urbanmyth on 2006-06-05
hi,  sounds like this link might be of use:  [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) 8)

---

### Post by ZeusABJ on 2006-06-05
[QUOTE=urbanmyth]hi,  sounds like this link might be of use:  [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) 8)[/QUOTE]

Now that looks VERY nice! 

:KS 

Thanks for showing me that link Urbanmyth! Also thanks to everyone who stepped up to help me in my hour of need. I'm going to do a little reading and try some of the things you all suggested. If I get hung up again I'll post here.

Thanks again!!!

---

### Post by ZeusABJ on 2006-06-05
[QUOTE=aysiu]If you're having dependency issues, you may have conflicting repositories.

I'd get a fresh list from here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try ```
sudo aptitude update
sudo aptitude install quanta nvu bluefish
``` and try out Quanta, NVu, and Bluefish--see which one you like best.[/QUOTE]

 Thats it! It was Quanta that I had all the trouble with. I'll give one of those other ones a go instead.

---

### Post by Ptero-4 on 2006-06-05
And don't forget to enable the universe and multiverse repositories. They have a lot of nice software for ubuntu.

---

### Post by ZeusABJ on 2006-06-05
[QUOTE=Ptero-4]And don't forget to enable the universe and multiverse repositories. They have a lot of nice software for ubuntu.[/QUOTE]

Okay I installed practically everything in that pack, but other than the Java and Flash plugins, I'm not really seing a difference. Where do I got to view those repositories? Also how can I tell if that NVIDIA driver got installed?

---

### Post by ZeusABJ on 2006-06-05
Oh and BTW; Aysiu These links TOTALLY rocked:

[QUOTE=aysiu]
As far as installing software, these two links should have you covered:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[/QUOTE]

Thanks again!

---

### Post by nalmeth on 2006-06-06
I've not been logged off for long, and naturally things pace on quite quickly.

[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation")

You must have just missed this in my previous post, it's probably a little more info than you need but there it is. 

RE: the GDebUI dependency thing

The program *will* tell you if you have missing dependencies, but I don't know if it will fetch them for you. The reason? I never had it tell me I was missing dependencies. Kinda useless information, I know. I quickly tired of using that on my slow laptop, and went right back to the terminal. Just my preference.

EDIT:
> Where do I got to view those repositories? A previous user recommended synaptic if you want to view the available packages. You can use it for enabling the extra repos and viewing all their packages.
ALT-F2
gksudo synaptic

want a couple more great ubuntu links?

_[[U]Ubuntu Document Storage Facility_]("http://doc.gwos.org/index.php/Main_Page")
[wiki.ubuntu - User Documentation]("https://wiki.ubuntu.com/UserDocumentation")

HAVE FUN!
[/U]

---

### Post by ZeusABJ on 2006-06-06
Thanks a lot guys. I'm definitely doing a lot better now (maybe I just needed a pep talk). My Ubuntu machine is up and running, and while there are still a few glitches to iron out I'm much less frustrated than I was before. I'll keep playing with it but hopefully the worst of my issues are almost over.

---

### Post by ZeusABJ on 2006-06-07
Okay there's still one thing I'm not clear on. How do repositories work? I followed some instructions on "installing" some recommended repositories. Once I do that do they just appear in Synaptic? There was a lot in there already so I’m having a hard time telling if anything changed…. Also if I’m using Kubuntu and install these repositories, do they appear in Adept?

---

### Post by dbw on 2006-06-09
The repos are all stored in /etc/apt/sources.list.  Any apt-get based software finds its sources there (ie synaptic, &c. ).  You should be able to see your new repos in the sources (or whatever it is called) dialog in synaptic.  Additionally, you could simply 
```
cat /etc/apt/sources.list
```
remember, lines that start with # are commented out (inactive)!

WRT the nvidea drivers, they are certainly neccessary to take full advantage of your video card - I noticed an immediate difference in the speed with which my box rendered the open-gl screensavers,  and a general decrease in cpu & memory usage when doing graphically heavy stuff.  You might not notice this, as you have 4-16 times more RAM than I (desktop and laptop respectively).  You should get some sort of nvidea settings app when the drivers are installed.  I am rusty on kde and gnome, but I think that this will just appear somewhere in your menus.

thanks for your questions  - this is a great thread for all newbies and former newbies!!!  (I think that covers everyone)

---

