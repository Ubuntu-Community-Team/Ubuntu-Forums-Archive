---
title: "Switch to Windows7"
date: 2012-04-26
forum: Any Other OS
---

### Post by t.rei on 2012-04-26
Hi,

I'm a linux user. My first one was installed via a collection of floppy discs and I was impressed by a working command prompt after a couple of days of installing and configuring. I used fvwm, twm, kde1, gnome, enlightenment, ... up to unity and gnome-shell. I grew older using linux. For several years now, I'm with ubuntu. I don't agree on everything done, I liked 'stuff' better the way it was, I do like more of the improvements, though.

Now I've recently gotten the strange idea while working on my text: With all the comments about how bad it is for a user to switch to linux and what could be done to improve the transition: Has anyone actually taken a look at what it is like to **Switch from Linux to Windows**?

I accepted that I won't have any solution for multiple virtual desktops that comes close to gnome-shell or cinnamon. I accepted that there won't be something as simple as update-manager or software-center. I accepted not-knowing any usefull commandline tools or even havin a fallback like tty1... and that my browser was the way to get software. And that any software had it's own updater. And that there probably aren't as many tools to pick from. Hence I was going to focus on something simple: Get a working latex environment that works comparatively well. Something many a student or teacher at a university would need sooner or later.

**Getting things running**
It was rather easy to get windows running on a dual boot machine (it destroyed my bootmanager, but that was easily fixed using an ubuntu live cd and a step by step guide from the forums).

It was just a matter of 2 hours (*sigh*) to patch it to the current version.

Installing up-to-date-drivers for the graphics card took me an hour (laptop card... nv_disp.inf editing... finding out what the freck I needed to write in there... no information on any official board regarding this...). The others were slowly downloaded from the manufacturer website and required a couple of reboots. Nothing scary, just annoying. But really not difficult.

Then libreoffice, thunderbird, firefox, pidgin, skype... easy. Download, install... 

Now I'm trying find the solution to the equivalent of:
[FONT="Courier New"]sudo apt-get install gedit-plugins texlive-base texlive-bibtex-extra rubber make cvs bzr build-essential [/FONT]
... and the corresponding dependencies. Just a working environment for something as basic as latex-document-writing. And I'm already stuck for some hours trying to figure out what is actually available and how to install and get it. WOW. Is this the way that the oldschool windows users actually LIKE getting things going?

I'm still on it, but honestly - I've already spend quite a lot of hours on this, and I do NOT have a working environment to 'just get things done'. I'm growing incredibly frustrated by the experience of running windows. 

**Conclusion so far**
Switching to Windows is _a lot_ more painful than expected. I'm curious about what and if there will be notable differences in working on a windows environment compared to a linux one (unity/gnome-shell/cinnamon/...).

The task is rather simple: just basic everyday university work. It can't be THAT difficult to get it working? 

I wonder - is there even a gain to this? Will anything work BETTER or easier? WHAT IS IT, that makes anyone put up with this instead of just working?

**I am missing obviously easy stuff?**
I'd appreciate any pointers to good sites/quides/howtos/boards where I can find information on how to get a basic windows working environment for university work going.

---

### Post by Erik1984 on 2012-04-26
I know what you mean, I missed Linux very quickly after a switch to Windows. 

Some serious tips though:
Latex -> MikTEX for the Latex packages also comes with an editor. NotePad++ (GPL) also does syntax highlighting for Latex.
Shell -> Powershell or you could try CygWin.

---

### Post by t.rei on 2012-04-26
Thanks for that - I got the basic latex working now, just not bibtex *gnah*

Man, we linux (ubuntu) users are a spoiled bunch.

---

### Post by forrestcupp on 2012-04-26
It's just a totally different mentality. People who have only used Windows live in that mentality and that's how they think. Because of that, they can get things done quickly because they're already thinking the Windows way.

There are a couple of things that you'll have to get used to. Windows is a graphical OS, and almost everything you would ever do is done in the GUI. There are no repos; all the software is scattered all over the place instead of in one central location. You usually don't have to worry about any dependencies. Either the software depends on things that are already built into Windows, or it just includes all of the dependencies as dll files in the installation. Also, the filesystem is handled much differently.

If you can learn to completely change your mentality of how things work, it will become much easier for you.

---

### Post by Dragonbite on 2012-04-26
Since you're experienced with different distributions and desktops, think of Windows as a new distribution and desktop since everybody does something differently!

At least Windows 7 almost gives you a semi-Linux-like experience (hey, it almost is as easy to install as Linux! ... (then the updates start) ... almost.)

There was something about a 3rd party app that gave Windows a virtual-desktop like setup.  I think it was for Windows XP and chances are it's been ported to Windows 7.

If you've used KDE 4 (the more recent ones) I think you'll find it less of a stretch look-and-feel-wise.

---

### Post by grahammechanical on 2012-04-26
You are missing the point from Microsoft's point of view. :)

Don't upgrade Windows buy a new machine!

The Word Processor cannot keep up with your typing? Get a new Windows PC.

Don't mention that it is a Microsoft OS and program that is being used, just advertise - buy the latest Windows PC to solve all your problems.

Regards.

---

### Post by stalkingwolf on 2012-04-26
in recent months i have had two experiences with installing windows.
about 4 months ago i had an HP laptop i was selling.  I installed winxp, did the service pak update and all that.  had someone come look at it.  It wouldnt play a dvd.  WTF i knew it had when i had ubuntu installed.  A little searching found that it required a special "decoder pak" to play dvd's.
Interestingly enough the person that finally bought it wanted Ubuntu on it.

A few weeks ago I purchased a Dell M6300 for a family member.  He had an old (running win98) computer that had a program and files he wanted transfered to the new lap top. ok no problem.

First with his permission i dual booted the laptop with Zorin, the same os that is on the computer his partner bought from me. nothing i could find would read his files . they transfered fine . just couldnt read them.

I got a brilliant idea.  why not clone the drive.  it was a whopping 6gb with only 1.7 being used.so off i go, wipe her HDD clone his drive to it then reinstall zorin.    bobs your uncle. Her computer boots into 98 runs everything fine.
After fixing a memory issue with my bench computer works there also.
On to the laptop which has Vista on it and is accompanied by the Dell reinstall disk.
clone his drive, reinstall vista (just to make his brother happy.  brother is a linux doesnt have software, is to hard etc etc fan)  then zorin.  first discovery, 
vista has no option to format, vista only recognizes NTFS.
second discovery no 98 partition in boot loader.  3rd the reinstall disk has no lan driver, has wireless but nothing for wired.
After 3 days and 15 Dell certified drivers still no wired connection.   works fine in zorin (  broadcom wireless doesnt).

Fast forward to Monday last. we have the discussion you know the one that goes it is your computer it should do what you ant it to, not what your brother thinks it should, not what i think it should. With Vista you cant boot into 98.

Bottom line wiped the hard drive and reformatted, recloned the 98 drive and reinstalled zorin.  now all i need to do is see if i can get the wireless working,
if not i have another solution that i have used since 7.10 a usb wireless adapter.

---

### Post by SemiExpert on 2012-04-26
> **grahammechanical said:**
> You are missing the point from Microsoft's point of view. :)

Don't upgrade Windows buy a new machine!

The Word Processor cannot keep up with your typing? Get a new Windows PC.

Don't mention that it is a Microsoft OS and program that is being used, just advertise - buy the latest Windows PC to solve all your problems.

Regards.

 I'm sure that Microsoft would like to sell large numbers of upgrade copies of Windows with each product cycle.  There was even a time when Windows user would camp outside stores to buy boxed retail copies of the new Windows release - although that was back in the 1990s.  The fact that consumers are buying Windows preloaded on new hardware and rarely upgrade to a new version has more to do with how consumers perceive Windows PCs as being cheap and disposable than any planning on the part of Microsoft.  Apple can convince consumers upgrade OS X on a biannual, and perhaps even an annual basis, but Microsoft users are willing to recycle the PC before they'll shell out for an upgrade.  It all comes down to the increasingly negative perception of generic Windows PCs and the operating system itself.  The average consumer regards a Windows license as something that comes with a Windows PC.  There are real costs associated with an OEM license, but to the consumer, a Windows license is something without any meaningful value.  It just comes with the PC.

---

### Post by Mathor on 2012-04-26
> **forrestcupp said:**
>  You usually don't have to worry about any dependencies. Either the software depends on things that are already built into Windows, or it just includes all of the dependencies as dll files in the installation. Also, the filesystem is handled much differently.

If you can learn to completely change your mentality of how things work, it will become much easier for you.

The registry is all based on depencies. The problem is, there is no clear way to fix broken depencies. No Synaptic (Hence, if you delete a program without "uninstalling" it, you're basically OUT OF LUCK at that point, because finding all the various scattered registry files in the various folders and with various names for that program is near to impossible). You basically keep installing and deleting things, filling up your registry, until your system becomes very slow. Driver management is abysmal. This thread is relieving, as I forgot about a world in which computing was so much more difficult.

The windows mentality is as such: "My system is running slow. I must have a virus

EDIT:

Also, although I'm probably gonna take some crap for this: Mac's Unix filesystem works a LOT better than that damn registry.  All depencies are all tied to the individual program. All of the config files, etc, leave your system entirely when you delete that program.  Although it's no linux, Unix is certainly a better alternative to an unusable command line and unusable file system.

---

### Post by Tombgeek on 2012-04-26
I don't find Windows 7 that difficult to use. If you are talking about pre-Windows 7, I can understand your problem -- they were awful. But Microsoft has gotten their act together (although seems to be losing it with Windows 8 :( ). 
It's not that Windows or Linux is better, they're both just different. You can't go into Windows with a Linux mentality, because you're surely to be disappointed. While I like Ubuntu and Linux, I use Windows 7 as my primary operating system.

About as far as I know, about your LaTex problem, just download the install from the LaTex site and install a program like Lyx. Is there any particular piece of software you prefer or something?

---

### Post by Dragonbite on 2012-04-26
> **Tombgeek said:**
> I don't find Windows 7 that difficult to use. If you are talking about pre-Windows 7, I can understand your problem -- they were awful. But Microsoft has gotten their act together (although seems to be losing it with Windows 8 :( ).

They're not "losing it", they are following their well-established pattern...

Windows 3.11 = good
Windows 95 = bad
Windows 98 = good
Windows Me = bad
Windows XP = good
Windows Vista = bad
Windows 7 = good
Windows 8 = guess!;)

---

### Post by Mathor on 2012-04-26
> **Dragonbite said:**
> They're not "losing it", they are following their well-established pattern...

Windows 3.11 = good
Windows 95 = bad
Windows 98 = good
Windows Me = bad
Windows XP = good
Windows Vista = bad
Windows 7 = good
Windows 8 = guess!;)

Windows 3.11, 98, and 7 are the only ones on this list that are at all usable imho.  Windows 8 looks kind of cool, but the alienating all-touch, no c++, all webapps and html5 apps (not far off from a chromebook or the xbox360's OS or the windows phone) is going to turn off regular desktop users. I think you will find a lot of people flocking to Linux and Mac in large numbers.

---

### Post by forrestcupp on 2012-04-26
> **stalkingwolf said:**
> i
about 4 months ago i had an HP laptop i was selling.  I installed winxp, did the service pak update and all that.  had someone come look at it.  It wouldnt play a dvd.  WTF i knew it had when i had ubuntu installed.  A little searching found that it required a special "decoder pak" to play dvd's.Either that, or VLC. ;)
XP didn't come with the ability to play DVDs out of the box. I think Win7 does, though.

> **Mathor said:**
> The registry is all based on depencies. The problem is, there is no clear way to fix broken depencies. No Synaptic (Hence, if you delete a program without "uninstalling" it, you're basically OUT OF LUCK at that point, because finding all the various scattered registry files in the various folders and with various names for that program is near to impossible). You basically keep installing and deleting things, filling up your registry, until your system becomes very slow. Driver management is abysmal. This thread is relieving, as I forgot about a world in which computing was so much more difficult.If you're a simple user, you're not going to delete anything. If you have any awareness of needing to remove anything, you'll just use the "Uninstall a program" feature in the Control Panel. If you're advanced enough to know how to manually delete things, then you should know better. Nevertheless, I've done it before. :)

But CCleaner does a pretty good job at cleaning up registry messes. I agree that the registry is a mess. I liked things a lot more when programs used .ini files in their local folders, rather than the registry.

> **Dragonbite said:**
> They're not "losing it", they are following their well-established pattern...

Windows 3.11 = good
Windows 95 = bad
Windows 98 = good
Windows Me = bad
Windows XP = good
Windows Vista = bad
Windows 7 = good
Windows 8 = guess!;)
Lol. I agree with most of that, but not Win95. Windows 95 was revolutionary. That was the first 32-bit Windows OS for mainstream computing. It was also the first OS to popularize the modern paradigm in desktops, where you have a menu button on a panel with a task switcher and notification area. There have been a heck of a lot of desktop environments that have copied the layout that Windows 95 began, and it's only just now starting to change after almost 20 years.

---

### Post by Mathor on 2012-04-26
> **forrestcupp said:**
> Either that, or VLC. ;)
If you're a simple user, you're not going to delete anything. If you have any awareness of needing to remove anything, you'll just use the "Uninstall a program" feature in the Control Panel. 

That's like seven clicks! I'd hate to see what a Unity hater would have to say about that. However, in Windows you actually have the freedom to put a shortcut to a feature like that on your desktop rather simply. :)

---

### Post by CharlesA on 2012-04-26
> **forrestcupp said:**
> Either that, or VLC. ;)
XP didn't come with the ability to play DVDs out of the box. I think Win7 does, though.

Win7 can play dvds out of the box in both Windows Media Center or Media Player (I prefer Player tbh).

I haven't used XP for media in ages so I don't know if it came with the codecs needed for dvd playback or not.

---

### Post by Dragonbite on 2012-04-26
> **CharlesA said:**
> Win7 can play dvds out of the box in both Windows Media Center or Media Player (I prefer Player tbh).

I haven't used XP for media in ages so I don't know if it came with the codecs needed for dvd playback or not.

Installing XP was a royal pain with no drivers (even NIC) and minimal codecs.

That's why I say Windows 7 is the closest thing to Linux... it works an providing these things almost (but not qutie) as good as Ubuntu.

---

### Post by Herpythebrony on 2012-04-26
I remember my first clunker bit the dust and I had to use my dads laptop and he does not wanna learn linux so I had to use winblows for a couple of months, I so missed linux during. Glad I have my new cpu with Lubuntu on it! :D

---

### Post by forrestcupp on 2012-04-26
> **CharlesA said:**
> 
I haven't used XP for media in ages so I don't know if it came with the codecs needed for dvd playback or not.

I think you had to buy the Media Center version to get DVD codecs. Most XP computers came with codecs and DVD players preinstalled, like CyberLink PowerDVD. But I think if you installed XP from scratch, you didn't get DVD playback at all.

---

### Post by TheMTtakeover on 2012-04-26
> **Dragonbite said:**
> They're not "losing it", they are following their well-established pattern...
 
Windows 3.11 = good
Windows 95 = bad
Windows 98 = good
Windows Me = bad
Windows XP = good
Windows Vista = bad
Windows 7 = good
Windows 8 = guess!;)
 
I switched from the 12.04 beta to the Win 8 beta and I have to say that I haven't had any problems with it, I was very surprised considering it is in the Beta stage. I really don't think its a bad OS and the install was just as easy as any Ubuntu install.

---

### Post by inspiredbylasers on 2012-04-27
It seems that Windows 8 will be integrated in many work environments, I am curious how a triple-boot will work with 12.04 LTS and Lion OSX.

---

### Post by mamamia88 on 2012-04-27
I had switched to windows 7 for a few months after a upgrade to the precise beta killed my working wifi and I was lazy and had a flash drive with windows 7 laying around so i put that on there.      Windows 7 is actually a very good os.    I just prefer linux because I want my netbook to run as smooth as possible with the least amount of effort on my part.    I would always get paranoid in windows that I would get a virus or something even though I never would.

---

### Post by wolfen69 on 2012-04-27
> **forrestcupp said:**
> dependencies

I can't remember the last time I had a dependency issue. In the 90's?

---

### Post by wolfen69 on 2012-04-27
> **mamamia88 said:**
> I had switched to windows 7 for a few months after a upgrade to the precise beta killed my working wifi and I was lazy and had a flash drive with windows 7 laying around so i put that on there.      Windows 7 is actually a very good os.    I just prefer linux because I want my netbook to run as smooth as possible with the least amount of effort on my part.    I would always get paranoid in windows that I would get a virus or something even though I never would.

You're always so eloquent with your wording.  Ha ha yeah.

---

### Post by mamamia88 on 2012-04-27
> **wolfen69 said:**
> You're always so eloquent with your wording.  Ha ha yeah. lol talk about run on sentences.  my bad typed it up in kind of a hurry.

---

### Post by Tombgeek on 2012-04-27
> **Dragonbite said:**
> They're not "losing it", they are following their well-established pattern...

Windows 3.11 = good
Windows 95 = bad
Windows 98 = good
Windows Me = bad
Windows XP = good
Windows Vista = bad
Windows 7 = good
Windows 8 = guess!;)

Vista was not all that bad. After Service Pack 2, Vista is actually a very good OS, on par with a clean install of Windows 7 and better that Windows XP SP3. Windows 7 is the only Windows OS I can recall that was actually stable with a clean install without updates. Then again, I'm only 18 so I can't really talk about anything before Windows 2000.

I don't think that Windows 8 as an OS will be bad (it is just Windows 7 with a different interface). I just personally hate the interface. You can probably fix it with a third-party program. But either way, I'll stick with Windows 7 and Ubuntu for a while.

---

### Post by t.rei on 2012-04-27
Thanks for all the replies. I am gave up on the bibtex for now and put it on the "need to get working" list. 

You guys are aware, that in my case "dependencies" was used as a good thing? Like installing nautilus-sendto and not having to mention nautilus, because it's going to get installed anyways. Smart and sane use of dependencies and virtual packages makes installing collections of software really easy. "ubuntu-restricted-extras" anyone? Yey for post-install-scripts.

I don't think installing in windows is difficult. Just annoying!
Download -> go to folder -> doubleclick -> agree to mod system -> click install -> click ok -> enter path (sometimes) -> click ok -> click ok -> go back -> deselect explorer bar XYZ (sometimes) -> select "agree to licence" -> click ok -> wait. done. Not difficult, but not what I'm used to.
And thats not just the 3rd party stuff, thats with the official ms stuff as well, just usually there's a 'reboot system popup' afterwards.

But lets assume I'd never have to google for the solution to my bibtex-non-workiness (apparantly it SHOULD work) and that this is the system that I'd be able to work with. Most things are working.

Now to look at what I'm with:
The explorer is an ugly old bitch: nasty looking like konqueror in it's early days as a filemanager ( [http://wap-pool.math.uni-bayreuth.de/pictures/rz_pool/konqueror_home.png](http://wap-pool.math.uni-bayreuth.de/pictures/rz_pool/konqueror_home.png) ) and it's working pretty much like it, too. It's like going back 10 years. :D 
Adobe reader makes me cry a little. It's working, but only if i manually kill the darn update-thing... disabled it... it's back after reboot... I am actually having to mess with system-settings to get the pdf viewer to not interrupt my work! ARGH!
Have you guys ever noticed how much one can muss compiz-scale / gnome-shell overview for application switching and keeping control of what applications are running? Going back to a "dock" only is strange.
The bar however is impressive: a nice mix of a panel and the unity launcher bar. Very much like a nicely tuned kde4 panel.
The applications that do run, run smoothly and fast and I have to admit, the eyecandy is nice. I like glass-with-blurr. Nothing fancy but something lost with gtk3. 

Well, you know what I have to do now? Reboot. Something apparently was updated. *sigh*

---

### Post by wolfen69 on 2012-04-27
> **Tombgeek said:**
> Vista was not all that bad. After Service Pack 2, Vista is actually a very good OS, on par with a clean install of Windows 7 and better that Windows XP SP3. Windows 7 is the only Windows OS I can recall that was actually stable with a clean install without updates. Then again, I'm only 18 so I can't really talk about anything before Windows 2000.

I don't think that Windows 8 as an OS will be bad (it is just Windows 7 with a different interface). I just personally hate the interface. You can probably fix it with a third-party program. But either way, I'll stick with Windows 7 and Ubuntu for a while.

Stop the excuses. Either you like windows, linux, or mac. You don't need to make excuses why you like *any* of them. Who cares? It's not going to change *my* life, or yours. Chill.

---

### Post by Tombgeek on 2012-04-27
> **wolfen69 said:**
> Stop the excuses. Either you like windows, linux, or mac. You don't need to make excuses why you like *any* of them. Who cares? It's not going to change *my* life, or yours. Chill.

Sorry, I didn't mean to make it seem as I'm making excuses or being fanboyish. :oops: 

> **t.rei said:**
> 
Adobe reader makes me cry a little. It's working, but only if i manually  kill the darn update-thing... disabled it... it's back after reboot... I  am actually having to mess with system-settings to get the pdf viewer  to not interrupt my work! ARGH!

Do you require the advanced features of Adobe Reader? If not, I  recommend SumatraPDF. It's very limited, but it's fast and works really  well as a basic PDF viewer. Otherwise, there is always Foxit Reader.

---

### Post by forrestcupp on 2012-04-27
> **wolfen69 said:**
> I can't remember the last time I had a dependency issue. In the 90's?

Yeah, unless you compile a lot of stuff or download random debs from around the web, you're probably not going to have any problems. The nice thing about Ubuntu is that everything has a special package made for it. But you're still aware that there *are* dependencies. In the Windows world, people don't even know or care about dependencies because they don't ever need to, unless they're a developer.

---

### Post by Dragonbite on 2012-04-27
> **TheMTtakeover said:**
> I switched from the 12.04 beta to the Win 8 beta and I have to say that I haven't had any problems with it, I was very surprised considering it is in the Beta stage. I really don't think its a bad OS and the install was just as easy as any Ubuntu install.

Yeah, Windows 7 is the most Linux-like and Windows 8 is building on that (just like Windows 7 built on the larger changes Vista brought over XP).  It seems like, now that they are having to compete again, Microsoft is starting to get a clue.

Starting... but still a ways to go. Obviously they didn't pay close attention to the arguments and uprising KDE 4 or Gnome3/Unity brought on before deciding to jump right into Windows 8.


> **forrestcupp said:**
> Yeah, unless you compile a lot of stuff or download random debs from around the web, you're probably not going to have any problems. The nice thing about Ubuntu is that everything has a special package made for it. But you're still aware that there *are* dependencies. In the Windows world, people don't even know or care about dependencies because they don't ever need to, unless they're a developer.

Linux repositories have made installing and upgrading such a breeze. No wonder these "App Stores" are basically Linux repositories-like systems with just a different name.

---

### Post by MisterGaribaldi on 2012-04-27
I wonder how many more howls of outrage there would have been here in this thread if the title had instead read: "Switch to Macintosh".

---

### Post by CharlesA on 2012-04-27
> **MisterGaribaldi said:**
> I wonder how many more howls of outrage there would have been here in this thread if the title had instead read: "Switch to Macintosh".
That can be arranged...

:twisted:

---

### Post by szymon_g on 2012-04-27
Well... my "cool story": after years of using Linux (I've started with Red Hat 7.2; than Mandrake 9; than few years without a computer, than ubuntu 6.06 and debian, arch, opensuse, fedora etc)- and I've run windows 7 (it was a RTM version). I liked it; so I bought (in pre-sale) its Ultimate version (i've paid peanuts money for it)- and it's really nice, stable. Runs all programs I need, using newer/older versions is much easier than on, let say, Ubuntu or Fedora.
Lack of virtual desktops? [http://www.makeuseof.com/tag/2-cool-virtual-desktop-managers-for-windows/](http://www.makeuseof.com/tag/2-cool-virtual-desktop-managers-for-windows/) dexpot and virtualwin (this one is open source) works fine. Lack of command line (because, its not a mystery, cmd.exe isn't perfect)- sure, PowerShell is nice. Ok, it's a bit different- but well, it's a different system after all.
Webcam works, soundcard works (although it requires manually installed drivers), everything else (including suspending- I was unable to /succesfully/ use it on linux) works after updating.
So- in short: no, i do not miss linux.

---

### Post by t.rei on 2012-04-27
The virtual desktop tool is ok, but for me it messed with my dual-screen setup. Thanks for the hint, tho.

I guess it depends on what programs one needs when deciding to use windows. Once they run, they run - no matter the system. 

On my laptop installing windows was rather cumbersome compared to ubuntu, mostly due to missing drivers and TONS of updates (university version of win7 ultimate). 

When running I really hardly miss anything, except the "scale effect" and a better way to keep track of 25+ apps and windows open at the same time. And of course the totally awesome multi-monitor-support I get with gnome-shell. But those are things I could easily get used to. 

Oh - one thing that drove me totally nuts - and continues to do so are really only habbits:
Move windows using alt+click
Resize windows using alt+middleclick
And my custom keybindings, that date back to eagle-typing (two fingers circular motion strike down)

If you ask me: gnome-shell wins right now. **for me**!
I'll give it some more time, to be fair. Right now it looks like it works just fine, just a lot less features. Couldn't spot any actual GAIN so far.

---

### Post by Bandit on 2012-04-27
> **forrestcupp said:**
> It's just a totally different mentality. People who have only used Windows live in that mentality and that's how they think. Because of that, they can get things done quickly because they're already thinking the Windows way...........

Not sure I 100% agree with that. Setting up a LAMP & WinAMP server for example. Last year finishing up college I watched my instructer who ONLY uses Windows take an hour to install just the OS and drivers, then the next two class days (about 2 more hours) just to get Apache, MySQL and PHP installed. Yet thats not even configured yet, that part took another whole week or 3 class days. Basicly a whole work day for setting up a server.. 

I can install Ubuntu Server LAMP in less then 30 mins and within a hour have it ready for testing. And I dont do this but maybe once every year or two.

Windows just makes things difficult having to jump around to setup screen dialog after dialog hunting for settings. In linux just edit a few well placed text configuration files. Ready to rock..

---

### Post by forrestcupp on 2012-04-27
> **szymon_g said:**
> Well... my "cool story": after years of using Linux (I've started with Red Hat 7.2; than Mandrake 9; than few years without a computerHow can a Linux geek go a few years without a computer? :shock:

> **Bandit said:**
> Not sure I 100% agree with that. Setting up a LAMP & WinAMP server for example. Last year finishing up college I watched my instructer who ONLY uses Windows take an hour to install just the OS and drivers, then the next two class days (about 2 more hours) just to get Apache, MySQL and PHP installed. Yet thats not even configured yet, that part took another whole week or 3 class days. Basicly a whole work day for setting up a server.. 

I can install Ubuntu Server LAMP in less then 30 mins and within a hour have it ready for testing. And I dont do this but maybe once every year or two.

Windows just makes things difficult having to jump around to setup screen dialog after dialog hunting for settings. In linux just edit a few well placed text configuration files. Ready to rock..It's all the in the mentality. I have experience setting up a WAMP server, but no experience at all setting up a LAMP server. So I could probably set up a WAMP in Windows much faster than I could set up a LAMP in Linux. I can't help it if your instructor is a slow poke. :)

---

### Post by szymon_g on 2012-04-27
> **forrestcupp said:**
> How can a Linux geek go a few years without a computer? :shock:

I wasn't geeky than (or now if that matters). And I had no computer because I had no cash for it :/

---

### Post by sffvba[e0rt on 2012-04-27
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by t.rei on 2012-05-06
Well, I'm back to linux. Ubuntu. Using gnome-shell.

And the bottom line is, that this is simply better (for me).

I had to google way too often for solutions of minor issues and not being able to alt+drag or mark+middleclick drove me insane. 

I guess details like these are equally confusing when someone is doing the switch the other way round.

---

### Post by Dragonbite on 2012-05-07
> **Bandit said:**
> Not sure I 100% agree with that. Setting up a LAMP & WinAMP server for example. Last year finishing up college I watched my instructer who ONLY uses Windows take an hour to install just the OS and drivers, then the next two class days (about 2 more hours) just to get Apache, MySQL and PHP installed. Yet thats not even configured yet, that part took another whole week or 3 class days. Basicly a whole work day for setting up a server.. 

I had a project (auction registration program for our church's annual auction) that runs a LAMP server plus connects to the internet via a wireless signal in the building and connects to another router via wire for everybody working on the program to use and I had it up and running very easily in Ubuntu (I used 10.04 because of errors mentioned elsewhere and time).

Installing Ubuntu (Wubi) probably took the greatest amount of time (45min+), then install Xampp (and secure everything) for the server, Dropbox for the source code files and change the ethernet port to shared connection. Done.

Yes, I could (theoretically) do the same things in Windows (7) except all reference I see about sharing the connection this way involves more steps and complexity.  Most sharing documentation I have found goes from a wired internet to broadcasting wi-fi for others to connect.  I'm running things opposite.

Although I did prefer using Notepad++ for editing files, rather than gEdit.

---

### Post by synaptix on 2012-05-07
Use whatever works best for you.

---

