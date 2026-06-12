---
title: "ibook g4 ubuntu?"
date: 2012-03-25
forum: Apple Hardware Users
---

### Post by Clessy on 2012-03-25
Hola, Im thinking of getting a ibook g4 ppc just because I think they're nice and they're relatively cheap now.

I'll be getting the 12" model with the 1.3ghz ppc. Having 1.5gb of ram and adding a 160GB 7200 rpm pata drive.

What im really curious about is just the general performance I should expect out of the machine running the last ubuntu. 

Is this is the best linux distro for this job?

Also how well will wine be able to run some older games on the hardware. Thinking around Unreal Tournament 1 level old.

---

### Post by guidop on 2012-03-27
Disclaimer:  I have not made a serious effort in working with GNU/Linux on PowerPC for about a year.  Maybe some things are better than my last experience.

1) The Apple iBook uses a PowerPC processor. This is NOT Intel x86 architecture.

I suggest you start reading here for general ppc info:
[**https://wiki.ubuntu.com/PowerPCFAQ**]("https://wiki.ubuntu.com/PowerPCFAQ")

This link is found in the top sticky post:
[**Where to download Ubuntu for PowerPC and other frequently asked questions**]("http://ubuntuforums.org/showthread.php?t=427714")


2) WINE does not and never will work on PowerPC.

3) There is no Flash support. There are alternatives, but they don't always work. See the FAQ. I had the best playback on PowerPC with minitube, but it's only for YouTube, and HD video was still too much processor load, at least when I tried it on my 1.7 GHz upgraded G4 Cube.  HTML5 video also seemed to load the system too much for good HD.

4) Ubuntu or Debian with a lightweight desktop environment is probably a good way to get a decent system up and running.  Try installing a command-line system, then X and LXDE (and wireless support).

5) I think PowerPC machines are cheap now, because Apple and most third-party software have abandoned software support. You will have to work harder to make it work well, compared to an x86 machine.  If this is your first time trying GNU/Linux, you would probably be better off getting an Intel based machine.  In my opinion, used Lenovo laptops seem like a good choice.

---

### Post by MisterGaribaldi on 2012-03-27
If you really want to use Apple hardware to run Linux, go get a MacBook, a MacBook Pro, or a MacBook Air.

---

### Post by ChupacabraMama on 2012-03-31
Hi!

I'm new here, and was looking around for answers to the same question Clessy asked.

"you're better off with a _____" is not a solution for me at this time, due to finances.  I actually trashpicked the laptop out of an e-dumpster, and with spare parts shared from friends and bits of advice I figured out how to get OSX 10.4.11 to run from an external HD (firewire.)  Other than the previous owner stripping the internal screw heads, so I can't get to the internal HD, it works completely.  Fantastically.  Just fine.

Except for the last six months, it seems like everything has slowed down, and much of what I do has slowed down and/or is no longer supported.  I was under the impression that you couldn't load another OS onto an iBook, but apparently I was wrong.  :)  

If I had 48 hours to go fetal, I could probably figure something out from the notes and other FAQ suggestions.  Guys, this is a great collection of information.

My limitations:

I am a farmer/rancher.  There is no way I can guarantee any amount of time to sit down and do something.
Farms have emergencies.  They are unpredictable.  
Children live here.  See above.
Goats live here.  See above.
All spare cash goes into making sure the next economic crash doesn't touch us.  :)

I'm trying to set cash aside, I'm hoping in the next six months to pull together enough to grab a cheap Android or something laptop or tablet.  So why do this?  Because I hate like heck to have one machine that depends on one OS I have little control over.  I'm not a geek, but with decently simple instructions I can fake it well enough. 

What do I need in a laptop?

1. Firefox.  I'm mostly using Google and its stuff, I've got an Android phone, I already read that Chrome is not likely to work.  Fine, it doesn't work for me anyway as things are now.  :)
2. A text editor that handles lots of formats.  That's OpenOffice, right?  I remember using that the last time I got SuSe running on a long-gone Lifebook.  2004, 2005, that long ago.
3. VLC or whatever else works best.  Music, and watching DVDs.
4. I've already read that Flash is no longer an option?  There seem to be substitutions or work-arounds, I couldn't tell if any of those are things that Just Work or need lots of fiddling with.  That's about where I was hitting Information Overload in my brain.
5. PDF handling, mostly reading and writing.  No fancy chart or graphics stuff needed.

What I have:

* A G4 iBook, circa 2005.
* An external hard drive, roughly 250 or 300GB.  I don't remember what's free on it, but quite a lot as I'm from the days when 40MB was OMGWHOA!  I just don't do much bloaty stuff, nor do I have as much time as I'd like for music and movie watching.  It's Firewire of course.
* An extra hard drive, I've played with it a little.  Plus a case for it.  It's not huge, but I'm pretty sure it's some two digit multiple of _GB.

* A spotty, occasionally good wireless connection.  Fortunately the weather where I'm most likely to be stuck inside is the weather that most supports a decent wireless signal.

What I'd like to do:

Spend the next few weeks little by little putting what I need to boot on the spare hard drive.  I'm terrified of screwing up what I already have.  Lots of the vocabulary in the FAQ and step by step directions is a language I don't speak.  I'll have to spend time looking up words I don't understand on Wikipedia, mostly.  Not going onto a step until I know just what it will do, and what I have to do if it breaks something.

Once I have what I need on the spare hard drive, seeing if it works.  HOPING it works the first time.

Now tell me, am I crazy or looking at unrealistic expectations for my needs and goals?

---

### Post by MisterGaribaldi on 2012-03-31
**ChupacabraMama**:

Ok. *You're crazy*. There, feel better now? :p

Seriously, you and Clessy have the same basic problem, and that's this: PowerPC (PPC) is essentially a deprecated architecture. That's a fancy way of saying that, some specialized hardware exceptions notwithstanding, the mainstream of computerdom no longer uses PPC in any way, shape, or form. Intel-compatible CPUs (so-called "x86" CPUs) are mainstream, and so the best support to be found at this point for any current OS is on x86.

You will enjoy far better support for your hardware by using Apple's Mac OS X, in your case 10.5.x (Leopard) because you will have full support for your graphics card, for your multimedia components, for wireless, and so on. Linux, from those distributions (or distros) which even port and compile a PPC version, really treat PPC as a red-headed stepchild.

I totally understand your financial situation. Believe me, I know exactly what it's like to be just a few short paychecks from total financial oblivion. Unfortunately, even though you can get Linux for PPC, it's just not your best choice for use as a desktop OS. Now, if you said "Hey, I have a PPC-based Mac and I want to use it as a file server!" then that's a whole different story, and I wouldn't hesitate to recommend putting Linux on that sucker.

Adobe, which is already rapidly withdrawing Flash from everywhere, has NEVER made a PPC version of their player, except for Mac OS X. The next-best runner up is called Gnash, and while it works, it's not 100%. Besides, and this is the truth even with Flash in Mac OS X, it runs like crap on PPC. And, that's largely due to two reasons: 1. It has always been optimized for x86; 2. What development resources could have been put into improving it for PPC stopped a few years ago, and all they've been doing is putting out "something" for PPC Mac users.

Now, it's also true that some sites like YouTube are slowly going Flash-free or Flash-independent (that is, they maintain two separate sets of code to build a web page based on if you have Flash installed or not) but it's going to take a while for everyone to transition away from Flash.

Besides, you will have better (perfect, that is to say) support for your on-board graphics, for all your iBook's multimedia capabilities, for wireless functionality, and so forth, under Mac OS X. Under Linux, it's largely (from what I understand) a crap-shoot.

Now... *if* you stick with Mac OS X, you will need to get Leopard (or, perhaps I should say you will be strongly motivated to get Leopard) simply because it's turned into the minimum system requirement for an awful lot of software, including anything approaching even somewhat dated versions of Firefox (and possibly Thunderbird).

---

### Post by ChupacabraMama on 2012-04-01
Dissenting viewpoints if any are welcome!    Thank you!

I got a PM reply suggesting MintPPC, anyone care to weigh in on their experiences with it?  I have AppleUspecific questions for you mistergaribaldi, but I'm taking those to a PM as they're apple apecific not Linux.  I have a tremendous amount of gratitude for the detailed quality of your response. 

(Next: look up what a file server is, so next time someone uses the phrase I know what it means.)

---

### Post by dpny on 2012-04-01
As someone with older, Apple PPC hardware and newer, Apple x86 hardware, I agree with the above: given that PPC is an obsolete platform, and that Ubuntu PPC is no longer officially supported (and that PPC Linux, is, in general, a relative backwater) your best bet for having an easy-to-use and maintain OS on that machine is to use OS X 10.5.8.

I have it on my G5, and it's still fine for everyday computing. Additionally, you will get Flash (although not the latest-and-greatest, as Adobe, too, has stopped PPC development). And while Apple no longer officially supports 10.5, they're still updating software for it: I fired up my G5 yesterday and found the latest iTunes waiting for me to download. Plus, there's a version of UT for OS X.

I have some experience with Mint PPC: I tried to install it on my G5, but ran into a problem which had nothing to do with Mint, namely that the Mac ATi X800XT is completely unsupported under any PPC Linux distro. That aside, I found the community to be very committed and helpful. If you're interested, there's a forum on the MintPPC forums specifically to list which machines its been successfully installed on. It will be more work than installing OS X, and the install, in particular, will require attention and a good internet connection.

If you really want to run Linux for not much money, your best bet is cheap x86 hardware. For PPC hardware, OS X is the best choice.

---

### Post by MisterGaribaldi on 2012-04-02
ChupacabraMama:

Sorry, I didn't check here in this thread before getting your PM.

A file server is a computer specifically set up to share files on a network. A print server shares a printer on a network, and so on.

My own home file server is a G4 Mac mini running Debian (another Linux distro and the one that Ubuntu is based on) and it is headless (that is, it's just the computer itself sitting on a shelf, with no monitor or keyboard attached). It's very reliable, and I can't begin to praise it enough.

---

### Post by Lars Noodén on 2012-04-02
Th G4 is a good processor so if you can get one cheaply then by all means go for it.  However, it is a bit older so you might want a leaner distro.  [Lubuntu](http://lubuntu.net/) runs very nicely on the old machines.  If you want to get a preview of 12.04 you can find the Beta2 version here:

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14349/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14349/downloads)

[http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14368/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/210/builds/14368/downloads)

---

### Post by rsavage on 2012-04-02
The advice given by MisterGaribaldi and dpny is actually quite bad. The version of flash available for Mac OS X is dated and therefore has security flaws. That is why TenFourFox actually stops you installing it.
 
Html5 has been around for well over a year now and most major websites are now setup to take advantage of it. I don't have flash installed and I don't find it a major inconvenience. I assume the thousands of iPad users feel the same. However, I would recommend you install FlashVideoReplacer (an extension for firefox) to get good video playback on sites like YouTube and Vimeo if you use these sites. The author of FlashVideoReplacer is a Ubuntu user and a member of this forum. 
 
The iBook 2005 is now 7 years old. This is your biggest obstacle, rather than the PowerPC architecture. Video cards and processor speed have moved on in that time and you should install a distro that reflects your computers capabilities. Lars Nooden makes a good shout with Lubuntu, but Ubuntu 10.04 works well too on a G4 ibook. You can have all the 3D effects working and your wireless cards work (not sure what MisterGaribaldi is on about since Airport classic and Airport Extreme both work fine).
 
I would like to address the "Ubuntu PPC is no longer officially supported" statement by dpny. It is something that often gets thrown by the Ubuntu PPC bashers. Well Lubuntu and Xubuntu are both community supported - just like Ubuntu PPC - yet nobody ever says you shouldn't install them because of this. Besides, you weren't planning on paying Canonical for support were you?
 
Ubuntu/Lubuntu/Xubuntu/Kubuntu PPC offers a choice of stable distros to fit your needs. Using a live CD you can try them out before installing or have them installed in 20 minutes. The Ubuntu PPC documentation is also the most complete of any of the linux distros available to you. Don't go following the dubious advice on forums. 
 
If you wish to install linux on your ibook then I recommend you choose one of the *ubuntu distros.

---

### Post by MisterGaribaldi on 2012-04-02
rsavage:

Excuse me, but what is so bad about giving advice based on the limitations of her system's capabilities?

She cannot run a newer version of Flash, no matter what she does, on that hardware. Telling her how to at least make use of what she can -- as opposed to just saying "Oh well, sucks to be you, buy a new box" -- is hardly defective advice.

Most people "out in the wild" make use of Flash simply and only because there is some Flash content on some page they intend to view. What exactly would you have had me say? "Oh, well, Gnash isn't so bad…" ? That's crap and you know it. Moreover, I did tell her that in any event Flash performance on that system is going to be pretty bad. I assume she is intelligent enough to have worked out on her own that this is going to be a stop-gap measure until some future point where she can obtain better hardware.

And yes, you're right, there is community support for Ubuntu on PowerPC. But it carries no backing or official support from Canonical (which is not a criticism, it's a fact) and there's really no getting around that. Besides, best case, "desktop" Linux for PPC is at this point more an OS for enthusiasts and hobbyists, and not someone who really would like to realize the full benefit of the hardware that they *are* -- not that they *could be* -- running. ChupacabraMama is running the hardware she's got, not some other hardware that she doesn't have. If you think she should be running newer, better versions of OS, plug-ins, and other software, why don't you buy her a new laptop and ship it to her?

Moreover, if you think advice on forums is "dubious" then why in the world are you here in the first place? Either you're taking dubious advice, or you're giving it. Now kindly quit casting aspersions on other people's factually correct, actually relevant, volunteer best efforts.

Thanks!

---

### Post by dpny on 2012-04-02
Ditto the above.

PPC Linux is a backwater, official support or not. I started running PPC Linux with Ubuntu 6.06. Even back then, before Apple stopped PPC support, running PPC Linux required more work than on an x86 system for simple things like hardware sensors and Flash. Now, 6 years later, PPC Linux is a hobbyist system. As I noted above, there isn't even support for the Mac version of the ATi X800 XT in any PPC Linux, despite it being the arguably most powerful GPU Apple ever put in the G5. If you want something as powerful you will have to run a 7800 GT, but then you won't be able to put your machine to sleep, as suspend is disabled in the kernel with nVidia GPUs. . .

And you get my point. Simple things, like suspend and hibernation, won't necessarily work. This is not a judgement. It's just a fact. Due to its relatively small user base versus x86 Linux, PPC Linux never had the same level of support. Now things are that much worse.

So, if you want to run an old PPC Mac and not have to spend a lot of time tweaking and googling, run OS X. If you have the time to spend making the system work, go crazy.

---

### Post by rsavage on 2012-04-04
ChupacabraMama listed their simple requirements.  Ubuntu/lubuntu/xubuntu etc fills their needs perfectly.

I wrote most of the PowerPC FAQ.  Along with Lars I am testing 12.04.  I own an iBook G4.  I think i am well qualified to say what works and what doesn't on an iBook.

It is irrelevant to ChupacabraMama whether the X800XT may or may not work.  Similarly, it is irrelevant if nvidia cards suspend or not (actually I think it would be possible to get them to using old framebuffers, but I don't have a machine to test).  You focus on the few things that don't work to drive your argument against PPC linux.  You could of said how much the 3D support on nvidia cards has improved over the last year, but of course, that wouldn't support your negative attitude.

Personally, I am always amazed at what does work (btw, suspend works on an iBook G4).

Again, I have to point out that needless negative statements like "it carries no backing or official support from Canonical" are just scaremongering.  You should be focusing on how fortunate we are that Canonical is still compiling PPC packages.  To maintain the necessary infrastructure and staff time must cost them.  This is the position as outlined by the FAQ:

"Canonical and the wider community still fix PowerPC bugs when they are reported and when they find them. However, releases will not be delayed due to problems which are specific to PowerPC. This means there is occasionally the need for some PowerPC specific workarounds which are detailed below and on the PowerPC Known Issues page"

This is an entirely sensible approach given the numbers of PowerPC users.  The focus of the 12.04 development testing and bug reporting has been to minimise the need for these workarounds.  I myself have reported several bugs and I think somebody from Canonical has responded on nearly every one.  

The PowerPC ISOs undertake the same testing as the other architectures to ensure their quality.  So as it happens there is a problem with nautilus and gedit at the moment in 12.04 because of a problem with the glib package under PowerPC.  If this is not fixed before the release date then I am very reluctant to release the Ubuntu ISO, even though the workaround would be relatively simple.  Directing people to the Lubuntu ISO would probably be more useful to them anyway.

The usefulness of a computer does not begin and end with the ability to run Adobe flash. As I have already said, I am happy to run entirely flash free, but if I  was bothered about things like YouTube then I would install the  FlashVideoReplacer extension.  Please remember when answering questions that others may not use a computer like you do.  For example, not everybody is 12 years old wanting to play facebook games or whatever.  Your recommendation to use an old browser and an old version of adobe flash goes against every security advice you will find.

MisterGaribaldi and dpny, I am sorry that you both seem upset that I have corrected you.  I do find it slightly odd that you don't like being criticised, yet seem very eager to criticise PPC linux.  I can assure you, people have volunteered a lot more time to PPC linux than you have to a forum post.

---

### Post by ChupacabraMama on 2012-04-08
Dear All,

Apologies for the delay in response - I also have some PMs to respond to, I'll get to those today I hope.  

The quick solution is to upgrade to OS X 10.5.  A disk is on the way, and the Nice Lady At Apple said that was probably the best solution.   Of course aside from suggesting I drop buckwads on a reconditioned whatever, that is.  :)  (And no, I didn't drop some blatantly ridiculous multiple of Franklins on it, the friend who sent me the Tiger disks didn't know Leopard would work on PPC.  He's fascinated with me keeping this running.)

Should we end up with a week's worth of appropriate weather that doesn't involve me having to crawl under the house or on the roof or wire the fences back together, I'll start building a load on my spare HD for Just In Case.  I don't expect Leopard to be functional forever, and I consider having the alternate OS in the wings just plain common sense.  Plus a learning experience - I've done it before, I just haven't retained the knowledge because I'm not into tinkering beyond what I need when it comes to computers.  Cooking, yes.  Software, much less so.  

(Frankly, what I can't see working scares the heck out of me.  I'm not a luddite or terribly lazy, just nervous about it since the time I first brought down an internationally operating mainframe because I was encouraged to "mess around, you won't break anything, you can't, our programmers wouldn't let that happen.")  

I appreciate the differences of opinion, truly I do.  And how civilized you all are about it.  Thank you, I'll keep reading and asking questions when needed.

...that lady with the goats

---

