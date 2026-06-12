---
title: "This fawn is too feisty."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ibexslam on 2007-05-09
I know next to nothing about linux, but I don't like the way my xp computer has been treating me, so I'm checking out ubuntu.

So I got my hands on a Feisty Fawn live CD, which seemed to have some promise.  Without the ability to save settings or anything else, however, it's a little frustrating after about ten minutes.  

I read about the possibility of using a usb flash drive to save settings and files.  That seemed interesting, so I bought a 4 gig drive so I could see if I could make that happen.

Then I started looking for a "how-to" on this page:
[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)
Hey, wait a minute..."Doesn't work with 7.04 'Feisty Fawn'"!  Where does that leave me?  

I'll tell you what I think: it's a little TOO feisty, if you ask me.  It certainly doesn't "just work."  I can't experiment any further with it because I'm too nervous about fiddling with the hard drive on my "mission critical" computer.  I keep getting weird junk showing up on web pages when I use ubuntu's Firefox, which doesn't happen when I use Firefox on that other operating system.  

I'm wondering if I showed up a little too early for the party -- maybe I should wait a few years for zesty zebra?

---

### Post by jfinkels on 2007-05-09
> **ibexslam said:**
> I know next to nothing about linux, but I don't like the way my xp computer has been treating me, so I'm checking out ubuntu.

So I got my hands on a Feisty Fawn live CD, which seemed to have some promise.  Without the ability to save settings or anything else, however, it's a little frustrating after about ten minutes.  

I read about the possibility of using a usb flash drive to save settings and files.  That seemed interesting, so I bought a 4 gig drive so I could see if I could make that happen.

Then I started looking for a "how-to" on this page:
[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)
Hey, wait a minute..."Doesn't work with 7.04 'Feisty Fawn'"!  Where does that leave me?  

I'll tell you what I think: it's a little TOO feisty, if you ask me.  It certainly doesn't "just work."  I can't experiment any further with it because I'm too nervous about fiddling with the hard drive on my "mission critical" computer.  I keep getting weird junk showing up on web pages when I use ubuntu's Firefox, which doesn't happen when I use Firefox on that other operating system.  

I'm wondering if I showed up a little too early for the party -- maybe I should wait a few years for zesty zebra?

If you have any specific problems that you would like fixed, we can give you a hand; just make a new thread.

Ubuntu will probably work better if you install it to disk. If you don't want to remove Windows (mission critical, eh?) you can resize your Windows partition, and dual boot, switching between operating systems whenever you feel like it.

Feisty Fawn is a stable release, but as with any Linux release, some hardware combinations won't "play nice", as they say.

But we can fix most any problem :D

---

### Post by Pigsflew on 2007-05-09
Well here's my two cents: If you want to wait for perfect software, you'll wait forever, from any source. I honestly feel like Feisty is to the point where I will recommend it to people who are less tech-savvy. The only difficult thing which sometimes arises is certain hardware, but people tend to be very willing to help with that :)

Feisty is extremely good, but the LiveCD wasn't really meant to be used as a person's actual desktop. It's just a sample. If you'd like a persistant Ubuntu test setup, Edgy is actually also solid; I'm still using it on my desktop. It has a somewhat out-of-date version of Firefox and Thunderbird, but it should work fairly well to get you used to how Ubuntu works.

---

### Post by Kevanx on 2007-05-09
I was getting really weird errors too, as well as a really really long boot time when I was trying out the live CD. I think the main point of the live CD is to introduce you to Ubuntu's GUI, learn what the Synaptec package manager is all about, and of course, the lovely terminal. Because linux relies heavily on a swap partition to process various activities (not to mention Firefox needing to write cache files and cookies to disk all the time), it's not surprising that you're having a less-than-satisfactory experience.
I can't really help you out with saving settings on an external drive.

If you want to wait, it wouldn't hurt, but I do know that countless problems that I had encountered with XP quite simply vanished when I switched to Ubuntu, and then when I upgraded from Edgy Eft to Feisty Fawn, a lot of other little details (the occasional firefox crash, wireless network issues) ironed themselves out.

I think what a lot of Linux users don't push as much is the community support. I can safely say, given how no-name my graphics card (Trident ALi Cyberblade - what?) is, that whatever problems you might face during installation and setup, someone else has already had them, or if not, there will be at least ten well-informed experts chomping at the bit to help you with your problem. I haven't had a problem with any hardware, network, or peripherals issues that I couldn't solve with ten minutes effort, and a search through these forums. That's the beauty of Ubuntu, not the OS itself, but the community. Although I don't think you'll find many complaints about the OS.

I was super nervous when I jumped on board, too, but nothing is irreversible, so back up your data, and give it a try. Otherwise, see you at Zebra!

---

### Post by mckryptyk on 2007-05-09
The problems you see when going to certain webpages are because of those webpages using rendering tricks to display correctly in Internet Explorer.

Some websites will even tell you that you need to "upgrade" to the latest Internet Explorer if you are using Firefox.

You can thank lazy and clueless webpage designers and webadmins for that.
To get around it you should use a "user-agent string modifier".

In Firefox, go under Tools ..> Add-ons ..> Click on "Get Extensions"
In the top right search bar: Search for "user agent".
Go to "User Agent Switcher" (by Chris Pederick).
Install.

To use:
Go to Tools ..> User Agent Switcher ..> select "Internet Explorer on Windows XP"
You will have to do this each time unless you modify the default "user-agent string"
If you need to do that, break out the Googlefu and you shall find :)

Cheers.

---

### Post by poppers1957 on 2007-05-09
> **ibexslam said:**
> 
I'll tell you what I think: it's a little TOO feisty, if you ask me.  It certainly doesn't "just work."  I can't experiment any further with it because I'm too nervous about fiddling with the hard drive on my "mission critical" computer. 

Hi ibexiam,  I am curious about you mission critical OS.  Unless you are a gamer, there is NOTHING you can't do as good as, (in most cases better than) In Linux.  Again as has been said, NO live cd will do any OS justice. Just what is it that makes your current OS mission critical?  I repair computers, and have to be involved with M$ systems, but all of our computers at home have Linux on them.  I absolutely love the freedom, not to mention, lack of crashes, blue screens, error messages, viruses, spy ware, and defrag maintenance and such.   Side by side, my children learned Linux faster, and more comprehensively than Window$.  But I do suggest you back up your data, and fully install Ubuntu 7.04.  The support you will get is awesome, and mature.  Please join us and feel it for yourself.  You will be glad you did.  You can always keep the old one and go back and visit if you get to missing it, but I bet you won't after a short time with Linux.

---

### Post by aimran on 2007-05-09
Too feisty? Well maybe yes if you want to do fancy stuff like Beryl. (damn you ATI xpress and beryl :( )

But at the basic level Feisty is one of the most refined Ubuntu releases so far. With networking support working better just to name an example.

For me it took about one month to get adjusted to Linux. If you are afraid to take the plunge and instead want to run the LiveCD to get used then be prepared for one month of slow loading off the CD :)
[B]
My suggestion? Take the plunge. Backup all your Windows data in case you want to switch back. [/B]

But if you can't afford to waste time on the learning curve while losing work productivity to learning Linux then I suggest you may as well get a sacrificial computer and fiddle with Linux on it. While not working just play with it. Then when you're ready, you know you're ready.

Just IMHO.

---

### Post by ibexslam on 2007-05-10
> Well here's my two cents: If you want to wait for perfect software, you'll wait forever, from any source.

It's not so much about achieving perfection. It's more about "satisficing." Software tends to naturally reach a level of maturity after enough bug tracking and user feedback cycles.  My offhand impression is that ubuntu is more of a wobbly colt and less of a fierce stallion at this point. 

> The problems you see when going to certain webpages are because of those webpages using rendering tricks to display correctly in Internet Explorer.

> Some websites will even tell you that you need to "upgrade" to the latest Internet Explorer if you are using Firefox.

> You can thank lazy and clueless webpage designers and webadmins for that.
To get around it you should use a "user-agent string modifier".

The funny thing is, I've seen these inappropriately displayed graphic clusters on THIS forum page as well as pages that I've created myself that, believe you me, weren't optimized for Explorer.  NY Times front page as well...just about everywhere.  The other flavor (xp) of Firefox on the same hardware renders the same pages correctly.

> Hi ibexiam, I am curious about you mission critical OS. Unless you are a gamer, there is NOTHING you can't do as good as, (in most cases better than) In Linux.

It's not so much the OS per se that's critical; it's what's hooked into it. If you're a graphic designer, you MUST use Quark and Photoshop on a Mac.  If you're an architect, you MUST use AutoCAD on a Windows machine.  For other things like word processing, web browsing, spreadsheets, etc., I'm inclined to agree with you: open source is the way to go. 

> But if you can't afford to waste time on the learning curve while losing work productivity to learning Linux then I suggest you may as well get a sacrificial computer and fiddle with Linux on it.

I'm not up for dealing with more hardware and cables right now. I'll probably just sit this one out and wait for glorious gerbil (or whatever it's called) and, if that one works, try the saved-settings-on-the-usb-drive trick.  If there is (at that time in the future) an E-Z way to slip the whole OS (not just the settings) onto the usb drive, that might be even better.

---

### Post by sandeep108 on 2007-05-10
I too have a "mission critical" PC and I simply cannot afford any downtime. But I do realise that with M$ road ahead, I will always be poorer. 

Here is what I am doing: Bought a second HDD (easily affordable) and installed it as a secondary master. To avoid any remote possibility of borking my XP stuff/data/setup, I simply disable the XP HDD through bios and enable the ubuntu one. I am now spending a little time over weekends getting everything to work and guys here (and at the OpenOffice forums) are helping - very promptly I might add. I also realise that some stuff like syncing with my symbian smartphone, etc. will be tough to accomplish, but maybe I will continue using XP for such stuff and all my other PCs switch to Ubuntu.

I was quite pleasantly surprised at the relative ease of ubuntu and not having even bothered to read up, still could get many things working straight off.

If more and more of us switch to open source, the hardware manufacturers will write software/drivers for us - Nokia - are you listening?

---

### Post by misfitpierce on 2007-05-10
> **aimran said:**
> Too feisty? Well maybe yes if you want to do fancy stuff like Beryl. (damn you ATI xpress and beryl :( )


Got mine working on ATI Xpress 200M :)  :KS  :popcorn:

---

### Post by ibexslam on 2007-05-18
Regarding the usb drive "persistence" that "Doesn't work with 7.04 'Feisty Fawn'": should I look for a patch for this someplace...or do I just have to wait 6 months for a new release?

---

### Post by Nekiruhs on 2007-05-18
> **ibexslam said:**
> 
 If there is (at that time in the future) an E-Z way to slip the whole OS (not just the settings) onto the usb drive, that might be even better.
There is just Google Bootable Ubuntu Flash Drive, it basically involves extracting the live CD to a flash drive. And that does work with Feisty

---

### Post by Spinelli on 2007-05-18
If all you want is a live CD I would recommend DSL, Slax, or Knoppix.
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")
[http://www.slax.org/]("http://www.slax.org/")
[http://www.knoppix.org/]("http://www.knoppix.org/")

I think Slax is my favorite.

---

### Post by mikewhatever on 2007-05-18
Anyone sees bad graphics? 
Since your first impression's based on is ten minutes of experience with a Live CD, I'd say you are very impatient and Ubuntu is probably not for you.

---

### Post by tompickles on 2007-05-18
also, if you are so keen to keep M$, why not go and dowload a virtual machine ([VMWare Server ]("http://www.vmware.com/products/server/")would easily do the trick for free) and go and install Fiesty on a virtual machine. Ok you will loose performance, and the chances are the Desktop Effects (Windows on a Cube and Wobbly Windows) won't work. This way, you can save all your settings in Ubuntu, as well as save any documents you create  al whilst keeping XP intact without even repartitioning your hard drive which always has some risk involved.

---

### Post by EricWiz on 2007-05-18
Just to throw in my 2 cents I am fairly new to Linux myself. I love it though and I was a hard core M$ fanboy for a long time. 

I downloaded Ubuntu mostly to look into a cheap DVR solution. Well, I never built the DVR but I use Feisty 99% of the time now. I have 2 PCs, 1 my kid uses to play games (XP) and one I use to serve music files, print serving, file serving etc.. That's the Ubuntu box and it's all I really use unless I need to remote into work. Then I have to switch to XP for now because I have not gotten an IPSEC client working yet.

My other kid only uses the ubuntu box as well. She just likes it better. Is is more responsive, doesn't crash etc etc.

I think if you make the move you'll find that it is just plain better and there is very little you can't do in Linux that you can in Windoze. 

Either way good luck!

---

### Post by tompickles on 2007-05-18
just a bit of an aside - EricWiz: I am also only starting to discover the power Linux can actually wield, and wondered just how easy it was to set up the music/print/file server on your LAN?

---

### Post by brennydoogles on 2007-05-18
Dual booting is the way to go..... until you're ready to ditch windows ;O)

---

### Post by ageilers on 2007-05-18
Try the Kubuntu Live CD. I started out on Ubuntu. I liked it, but I decided to try all the flavors. Kubuntu really satisfied me. I had to install Firefox, but that was easier than a warm knife through butter. I think the browsers on my linux PCs smoke the browsers on the XP partitions, Firefox and IE. If you do decide to repartition and install, you should definately backup. Well, Feisty or not, you should always have a backup anyway. It's not if the hard drive will fail, it's when it will fail. I see it every day. Backup, Backup, Backup (chant the mantra).

---

### Post by animusFL on 2007-05-18
> **ibexslam said:**
> 

So I got my hands on a Feisty Fawn live CD, which seemed to have some promise.  Without the ability to save settings or anything else, however, it's a little frustrating after about ten minutes.  ...

I'm wondering if I showed up a little too early for the party -- maybe I should wait a few years for zesty zebra?

 The Live CD willl just let you get a taste, but if you want to really try it without hosing your
mission critical stuff just install VMWare on XP , you can find it here...
[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)
 Then install ubuntu on a virtual drive inside that program. Works great, network functions,
sound works etc. you can install software & save files etc. Don't forget to install 
vmware tools into the guest OS, makes it work muuuuuch smoother.
 Hope that helps 
 animus

---

### Post by louieb on 2007-05-18
> **Spinelli said:**
> If all you want is a live CD I would recommend DSL, Slax, or Knoppix.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.slax.org/](http://www.slax.org/)
[http://www.knoppix.org/](http://www.knoppix.org/)

I think Slax is my favorite.
I've tried all the above and their good. **WOOF **my favorite is: [Puppy Linux ]("http://www.puppylinux.org/user/viewpage.php?page_id=1")

---

### Post by ibexslam on 2007-05-18
> Bootable Ubuntu Flash Drive
That sounds perfect.  I like the idea of a "computer on a stick" that can just plug into a machine and go.  I'll check that out.

> I think Slax is my favorite.
It's a nice name, that's for sure.  The panoply of flavors of linux is truly overwhelming.  I'm not saying it's a bad thing.  

> Anyone sees bad graphics?
I don't get it all the time, which is weird.  Or normal, maybe.  I don't know.  Today the errant graphic-block things seemed to relate to the viewing/not viewing of my bookmarks toolbar.  

> Since your first impression's based on is ten minutes of experience with a Live CD, I'd say you are very impatient and Ubuntu is probably not for you.

The thing is, I'm running a business.  I'm not so much impatient as pressed for time.  I've spent several days testing the CD, though, mostly for web browsing, and that's been working really well.  I haven't really had to do any fiddling.  You know what I mean.

> also, if you are so keen to keep M$
Believe me, I'm not.  It's all about the software.  Maybe that will change someday.

> Try the Kubuntu Live CD.
I did.  In fact, I tried that one first.  It seemed a little surly to me.  I liked the other better.

> just install VMWare on XP ... Then install ubuntu on a virtual drive inside that program
That sounds interesting.  I'm going to look into that.

Thanks for all the assistance!

---

### Post by mikewhatever on 2007-05-19
> The thing is, I'm running a business. I'm not so much impatient as pressed for time. I've spent several days testing the CD, though, mostly for web browsing, and that's been working really well. I haven't really had to do any fiddling. You know what I mean.
It looks like you are looking for a free Windows version which Ubuntu is not. Expecting it to fit your business needs right away is silly.
> I keep getting weird junk showing up on web pages when I use ubuntu's Firefox, which doesn't happen when I use Firefox on that other operating system.
Now you're saying that web browsing worked well, but I thought that was exactly the part that didn't work. :confused:

I think switching from Windows to Ubuntu is like learning a foreign language. All languages are similar in the sense that they have nouns and verbs, and words are grouped into sentences. That obviously does not mean one can master a foreign language in 10 minutes or two weeks.
Do not expect too much from Ubuntu, in fact, do not expect anything. Keep learning it in your spare time, and eventually, you'll find out if it suits your need or not.

Good luck.

---

### Post by ibexslam on 2007-05-19
> It looks like you are looking for a free Windows version which Ubuntu is not.
I already have Windows.  I don't like it, for the usual reasons.  

> Expecting it to fit your business needs right away is silly.
I don't expect it to fit my business.  For example, UPS doesn't make a version of WorldShip for linux.  If things keep moving toward web-based applications, though, as they seem to be, the choice of OS won't really matter that much.

>Now you're saying that web browsing worked well, but I thought that was exactly the part that didn't work.

It didn't require any messing around to make it work.  That's lovely.  Sometimes there's junk on a page.  It doesn't slow me down.

When I spend time in front of a computer, is that time productive?  That's the key.  

> I think switching from Windows to Ubuntu is like learning a foreign language.
A foreign language and a foreign culture.  In Japan, people have different ways of doing things than they do in Spain, but many things are pretty much the same in every culture.  

I was kind of surprised how similar ubuntu is to windows, interface-wise.  The desktop metaphor is pretty much the same.  

> Do not expect too much from Ubuntu, in fact, do not expect anything.
Zen tech support.  How refreshing!

Regarding that Bootable Ubuntu Flash Drive idea, I checked into that, and it looks awfully darned complicated.  I want to see a screen that pops up with "Install operating system to usb drive?"  I click on "yes" and it happens.

---

### Post by EricWiz on 2007-06-08
> **tompickles said:**
> just a bit of an aside - EricWiz: I am also only starting to discover the power Linux can actually wield, and wondered just how easy it was to set up the music/print/file server on your LAN?

Tom: Sorry to be so late in answering your question. I lost track of the thread. 

I found it very easy to setup the server. I should state that I started with ubuntu desktop, not the server version, because I use it as a desktop as well but it's primary use is to store files, music and the printer.

There is a great How-To on Samba that you can follow. It took me maybe an hour to get the initial setup and a few more hours here and there tweaking the setup but I started on a saturday morning and by the afternoon I was copying all my docs and MP3s. Everyone in the house has a login with their own /Home as you would expect and they have access to the /Music and /Docs directories as well.

The printer worked right away as well once samba was setup but I noticed a long interval between selecting print in an app on, say, my brother-in-law's pc and the printer actually starting to print. What I found was that I needed to add "Use Client Driver" in the samba.conf file and that was fixed.

So.. I am still ruinning the box and haven't needed to reboot since my original post in this thread either :)

The last thing I need to do now is get IPSec running on the ubuntu box so I can RDC into my machine at work. At that point I will have no need for windows at all anymore.

As an aside, I had this discussion with the marketing guy at work about a month ago. Now he's going through the same process! He said to me a couple days ago that he also prefers ubuntu now over windows and has setup his own server too! 

He uses a upnp server on it as well to serve up his music to his upnp devices. This was a BIG win for him because he was using windows before and, as he said, the device didn't pass the "wife" test because he would have to restart the upnp server on the windoze box every other day or so. He's been running it on ubuntu now for 2 weeks with no issues whatsoever!

so, tompickles, I hope that answers you question. Good luck with your setup!

Eric

---

### Post by sandeep108 on 2007-06-09
Can you please post the link to the samba how-to? I can see my windows workgroup network boxes from the ubuntu box but nothing further works. I suspect I have to set up user names/passwords in the samba config.

---

### Post by EricWiz on 2007-06-11
Sure,

Here you go. 

[Samba How to]("https://help.ubuntu.com/community/SettingUpSamba")

Eric

---

