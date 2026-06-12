---
title: "Pretty frustrated.  Thinking about giving up on linux"
date: 2011-07-02
forum: Any Other OS
---

### Post by profozone on 2011-07-02
So I love the idea of linux and I do appreciate all of the support in the forums.  It looks like linux has come a long way for people who use GUI's but it also seems like I can't even finish setting things up and it's 100% frustration.

After loading it on, I was working to create the look I wanted.  I'm using Ultimate Edition 2.6.1 based on Ubuntu 10.04.  I hate the animated cursor that comes with it, so I go to "cursors."  Right.  That does nothing.  Don't even know why it's there.  Eventually I find "appearance" and I'm pleasantly surprised that I can change a lot of stuff about how it looks and it came out awesome.  But I noticed that none of the special effects worked.  It was because I did not have an nVidia driver for my card.  No problem.  I go online, eventually find one and then about 10 different ways of loading it.  So I try like 5 different ways, never knowing if I'm messing something up.  The final one being to take a lot of scary steps for a linux newb, but voila!  It loaded.  The effects were there and looked pretty cool.  However, the appearance I had set up was changed.  No problem, I'll change it back.  So I go into appearance and start putting things back, only now the cursor will only change when it's over a program.  When it's moved over the operating system windows and stuff it stays this stupid spinning arrow.  The window frame around each window wouldn't change at all and it's so dark I can't see the controls.

The internet runs very slow, but when I boot into Windows, there's no problem.  So I go online again.  Someone said to unplug the computer and hold down the start button to bleed of any extra charge, wait about 10 minutes and come back.  I did this and it seemed to make a lot of things snappier.  But the very next time I booted.  Same thing.  The internet actually works and sometimes it's fine, but most of the time it's nearly unusable.  I do not witness this in Windows.

I have a book that tells me how to get software.  Go into "Ubuntu software center," or Use "Synaptic."  It conveniently leaves out what to do when the package isn't there or the name has some cryptic identifier tacked on the end.

When I first started this endeavor a few weeks ago, I loaded Windows, then I loaded Linux.  No problem.  I put them on two separate drives, so I didn't have to worry about partitions.  I set everything up and started tackling one thing at a time.  I was told to allow the updates.  But when I did (not the kernel update), it broke the internet connection permanently.  Long searches didn't help at all.  So I reinstalled Linux and broke Grub.  It gave no options for Windows at all.  More long searches and I fixed grub and there was a window option, but it wouldn't boot into it.  Finally I fixed the windows bootloader and it works again.  So I ask.  Do allow updates again?  I don't want to do all of these searches and learn how to set up all of this stuff and get it working again, only to break it with one click of the update button.

Ok, so I've been venting for a while now.  It would be nice to have some kind of life preserver here.  Am I doing something wrong?  Should I use some kind of friendlier version of Linux?  Is linux just for guru's who know every little detail about all of the parts that make it work?  I don't want to go back to Windows, but I have to at least be able to surf the web.  That's 90% of my computer usage.  I couldn't even type this in Linux.  I had to go into Windows to get a connection that actually worked.

---

### Post by Matt__ on 2011-07-02
Linux is new to you, its a learning process and you should expect bumps in the road to learning :)

Look back on your experiences with windows when it was new to you, and if you've had no problems then you either have the most charmed life ever, or never did anything with it.

The great thing about linux is choice, there are many variants out there, if one causes you problems, then try another. download and give ubuntu 11.04 a try, or mint or pclinux.
As for breaking stuff, thats part of the learning process surely?
I know I have screwed ubuntu to death quite a few times and come out knowing more.
And apart from win7 and my own personal cutdown version of winxp pro, ubuntu is much faster and easier to install. so messing up isnt a problem, if you cant fix it spend the 30 minutes and reinstall.


As for your slow internet, open a new thread with that as the title and explain in detail the problem, adding the terminal output of lspci and iwconfig.

---

### Post by Topsiho on 2011-07-02
Sorry for your frustration. I do sympathize with you.

But ...

Why don't you try and explore a ***regular*** Ubuntu, instead of playing with an Ubuntu version that was tampered with by a third party? And then complain that things don't work?

Please get hold of a regular Ubuntu, and I advise to download Ubuntu 10.04.2, as that is the latest version of the LTS (Long Term Service, and thus of the "enterprise quality") of Ubuntu.

If that one doesn't work as you would like it to do, THEN you're quite right if you complain here :)

I wish you a lot of JOY, and not frustration, even if not everything works as you would like.

If there is something that you don't like, you can send a bug report. I experienced once a real program change within a few days, after some consultation by it's author with me. You try that in Windows ...

Greetings,

Topsiho

---

### Post by grahammechanical on 2011-07-02
+1 to Topsiho's post. Here is a link to the Ultimate Edition forum

[http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)

I am not trying to get rid of you but as I am not familiar with how things are done in Ultimate edition I cannot begin to work out what issues you are having or how to fix them.

I keep in mind that if a package/program is not in the Ubuntu Software Centre then there is good reason for its absence. It may not be packaged for the Debian version of Linux that is the base of Ubuntu. It may not be of sufficient quality to be worth including. I have also noticed that if I download the package file from a website such as sourceforge and it has the .deb extension then I can open it with the Software Centre and all the tricky bits will be taken care of.

I cannot speak of Ultimate Edition or any of these types of projects but I am of the opinion that they may need the user to have more skill than I presently have. So, I am content with standard Ubuntu. It works fine for me and lets me get on with what I want to do on a computer.

Regards.

---

### Post by howefield on 2011-07-02
Thread moved to "*Other OS/Distro Talk*"

---

### Post by in-dust-rial on 2011-07-02
:)
hi,

first of all I like the above post.

but I would like to add some considerations.

1)
WHY or TO WHAT END LINUX/UNIX?

clearly, answering this question might determine future steps.

a) idiology
if you want to use a open-source operating system, because of ideology - keep on using linux.
but put your /HOME directory in a seperate partition.
so you can easily reinstall linux without any change on personal data. also search for ways to use aptitude to remember all installed packages - so you can install them all again after clean install of ubuntu/debian. so if something is messed up - just install again. after 1 hour everything is new again, but with the old configurations. (dont use kde3 and kde4 on the same home parition)

b) innovation
so clearly computers are your hobby. get a working station with a reliable operating system for everyday activity. and test **** on a second box. spend some money on your hobby :D. go crazy
... try dragonfly-bsd

c) insights into unix
get a reliable operating system on your box and install virtualbox. 
ontop you may install debian stable or even gentoo or maybe even build a whole linux from scratch. try some bsd and fucka round. learn more than just how much you hate following bad ubuntu-advice/how-tos.

d)you dont know.
then - as matt said - linux comes with a lot of choices... if you dont know what you want you will be inconsistent with your choices and mess up the systems every now and then.
so use the /home trick from above and also the aptitude trick. do it in virtual machines before you do it in a real install. and create a ghost image of your windows install .... AND because you will encounter trouble through your inconsistency, use backups ... and think twice before playing around with MBR or associated tools.


i certainly started somewhere in group d) because i did not realize i am in group c) ...

hope this helps somehow :D,
at least to spend more time away from your box!

---

### Post by handy on 2011-07-02
Install LinuxMint, life will be much easier; it will do a whole lot of things for you automatically on install that you had to struggle to do with your current distro, & also would with Ubuntu.

If Mint is still too tough, then I'd go back to Windows for a while & give a popular distro another try in a year or so, as they generally keep improving.

---

### Post by Anaphylaxis on 2011-07-02
I second what you are saying.

I have been using various distros since starting with ubuntu back in 2005, having accidentally screwed up my XP installation. It's been an uphill battle. At first, I relied massively on the ubuntuforums. Then, I relied massively on the Arch linux forums. Then, wikis. Then, I started knowing my way around enough to google answers to problems more specifically, and my forum posting frequency declined. 

Still, I keep banging my head against the wall with linux. I spend hours fixing printers. I spent the majority of yesterday, having my htpc work with nvidia ion and flash. I can't get my new asus u36j work with hdmi monitors/tvs, because hybrid graphics support for linux is plain crap. I had to buy an external usb soundcard/box for my microphones, as firewire support is crap on linux, at least when I bought my gear. The interfaces for the synth, recording software, and rosegarden, is plain crap. Way too complicated to learn. Compare this to cubase... no, please don't.

I don't think linux is any good at all. Problem is, windows isn't any good either, and apple is plain evil. Android, even though you have to know java to program for it, seems to get it's scheisse together, so it is agonizing to see how crappy hardware and software on linux is getting along. 

Yeah, sure, canonical is offering a pretty pimped-up, and from a user-interface perspective, functional debian, but it still ain't good enough. Proof of point: this was written from my windows 7 partition, because I am watching live coverage from tour de france on a silverlight page, and my moonlight plugin kept crashing in firefox5. 

Linux sucks, and people should stop praising it. Obviously, the free part doesn't work. Better to keep things proprietary, and just steal.

---

### Post by handy on 2011-07-02
> **Anaphylaxis said:**
> 
Linux sucks, and people should stop praising it. Obviously, the free part doesn't work. Better to keep things proprietary, and just steal.

Even though you sound like a troll I'll reply:

No, that wasn't what I was saying.

Linux doesn't suck. It can be harder for some people than others, due to a variety of variables, such as:

They aren't naturally technically inclined.

They have hardware that for whatever reason isn't supported or not well supported. (Even though Linux supports with its drivers more hardware than any other OS on the planet.)

The user has specialised needs that aren't well supported at this time by software &/or hardware.

---

### Post by Topsiho on 2011-07-02
And sometimes expectations are unrealistically high.
If everything is crap, then what?

By the way, handy (nearly) exactly says (in his second post) what I was planning to do, and logged in for.

Topsiho

---

### Post by in-dust-rial on 2011-07-02
today I just argued, why linux seems to be no option to the mainstream user ( [http://ubuntuforums.org/showpost.php?p=11004852&postcount=23](http://ubuntuforums.org/showpost.php?p=11004852&postcount=23) )

...
however, if one closely looks at the development there is a trend towards server-client architectures (terminals, clouds, web-services) and away from DOS like setups in desktop applications. (I heared that windows 7 has implemented quite some unix like infrastructure, but i do not really know about windows...)

unix(linux) was developing towards the DOS idea and tried to catch up with desktop environments. but it is clear that unix based software seems to have quite a history in the server direction. 

most of the time the unix approach was associated with reliability and customization - which are the backbone of productive systems.
while windows bugged me always with error massages without clear hints to a solution ... I had with most open-source software a change to solve the problem by myself -due to open source code.

furthermore open source means also, that the solutions - which are in the favor of the user are developed and pushed. 
(since they are coming from users)
not the solutions which sell most or are convenient to management.

together with the driving force behind unix:  geeks and science-labs 
it is relatively clear, that unix based solutions will always stay the SOLID choice for productive work.


well, when it comes to unix and it features towards DOS like desktops ...

today still the big money beats the better developing/development. 
but as soon as open-source distributions make use of GIT and a social approach to package sharing between friends there wont be much place for commercial products in desktops anymore.
(the marked will shift into server based services - where I expect unix to be ahead and waiting for the others to catch up (very soon))


sorry for the abundance :D

---

### Post by krapp on 2011-07-02
Have you given Ubuntu a shot, profozone?

---

### Post by profozone on 2011-07-02
Wow!  I expected nothing but flames, for essentially complaining, but I  got pretty much what I asked for.  Lot's of good insight, suggestions, a  bit of sympathy and pretty much everything in between.  Thank you.

To answer some questions and to ask a few more, let me start by saying  that I wish to use Linux for four reasons.  One, I like the philosophy.   Two, I like the security.  Three, I like the customizability.  Four,  I'm just as frustrated with Windows, especially in the spam, virus,  identity theft, bloatware, malware area.  (I think Apple is evil too.)

I don't want to anger people who love this system, but if I make stuff, I  like to make stuff very intuitive to the user, especially if it's for  home use.  It is my opinion that, if you are trying to appeal to the  mainstream  that you shouldn't have to be technically savvy.  If Ubuntu is not  trying to appeal to the mainstream, then why even have a GUI at all.  Even when I know what I'm typing in a command line environment, I tend  to make typos so it's not my preferred method for working.  If it means  doing some studying, I'm fine with that too, but my computer is also a  tool.  I use if for many many things (aside from the obvious email, I do  research on doing car stuff, which is my real hobby, video editing,  writing, home accounting, gaming, music editing/recording, website  updating, etc.) so there is a limit to how long I am willing to devote  to researching these issues.  Plus I get fatigued by doing so,  especially if I get the dreaded "hey buddy, do a search" comment.

The reason I chose Ultimate Edition, was because I read an article that  said it was the best distro to use for someone that was used to  Windows.  From what I understand it is basically Ubuntu with a bunch of  software already loaded on.  For me that was good, because it limited  the number of software packages I had to seek out and install even if it  meant a few I wasn't going to use.  Plus it has a bunch of eye candy (I  know it's about usability, but I'm a sucker for the eye candy too).  I  really liked the fact that I could customize the window frame, cursors,  background colors, etc. and really make a custom look.  Windows STILL  doesn't seem to offer that (unless I missed it somewhere).  Is this  something that is Ultimate Edition related or does Ubuntu allow you to  do that?  How about LinuxMint?  In fact, I've had suggestions for these  two versions.  Can anyone detail, just very briefly the differences?   Someone asked why I was using a third party version and then  complaining.  Well, it's because I didn't know I was using a third party  version.  I just saw that there was Fedora, Ubuntu, Red Hat, the list  seemed to go on forever.  How is a newb supposed to know which one to  use.  I knew Ubuntu was popular and usually I prefer the road less  traveled, but not when it comes to computers.

I did briefly try the CD version of Ubuntu a while ago, but I didn't like the fact that I couldn't save any of the changes.

I also did/do visit the Ultimate Edition forums, but they were down the  last time I tried, so I came over here to post since I knew it was based  on Ubuntu.

Again, thanks for the comments.  I will consider carefully my next course of action.

---

### Post by wolfen69 on 2011-07-02
> **Anaphylaxis said:**
>  

Linux sucks, and people should stop praising it. Obviously, the free part doesn't work. Better to keep things proprietary, and just steal.

You're not serious, are you? If you are, I'm just going to unsubscribe from this thread and not even bother. 

Good luck to the OP, and I hope you consider giving linux another try when you get a compatible computer. 

Linux has been nothing less than spectacular for me. In the 20 years or so I've been using computers, linux has by far been the best computing experience I've ever had. But then again, I care enough to actually take the time to learn, and buy only 100% compatible hardware. 

Most people I know that has tried linux absolutely love it. From grandfathers to young geeks. Peace.

edit: btw, LinuxMint is pretty good and worth a try. It has all codecs and flash preinstalled. Try out a few live cd's and see how it goes.

---

### Post by el_koraco on 2011-07-03
Dunno about Ultimate Edition, but it should have the Additional Driver utility that Ubuntu has. That probably would have been a much easier way of installing the driver for your GPU. As for the wireless thing, I suggest you open another thread, and give as much details as possible. What programs are you trying to install that you can't find in the Software Center?

---

### Post by Psyco430404 on 2011-07-03
What i would do personally is forgo the "ultimate edition" all it is is the default Ubuntu with a hellacious amount of extra software packages and bloat that dont do anything. As far as the eye-candy effects, there present in every single distro that uses compiz, for a default Ubuntu installation, all it is is a simple tick of a radio button and you have them. It will automatically detect if you have the drivers installed and if not it'll give you a gui to install them that simple. For the borders and every thing, thats again completely customizable in EVERY distro period. For instance, my openbox set up has everything tweaked, just as my gnome set up did. That's all in what you want, and its all easy to get. In the end compilations like the "ultimate edition" take something that is rock solid and stable, like ubuntu, and turn it into crappy bloat ware.

(sorry for rant)

What i would do is either install linux Mint or a Vanilla ubuntu install. Then make it your own and learn a lil bit about your system on the way to your final desktop.

---

### Post by imiT on 2011-07-03
I am in pretty much the same situation - I love the idea of Linux-am trying Linux basically for the first time.I did load Red hat about 8 years ago but it did not have the software I wanted so went back to windows.

2 days ago downloaded Ubuntu Studio. The  installation appeared to go fine but when I boot in it the mouse cursor is invisible. So I spend 3 hours on the net - dozens of the same complaint going back years- but not one solution except "google it" or "reinstall" or some temp. workaround which "may or may not work for you" (they did not). Surely this is such a basic feature that if it does not work, the distro should not be released. I have spent at least 10 hours without a solution. As a professional that means the "free" os has cost me $600 t0 $800 in time spent without a solution.

 I would love to hear that it is me - that there is a solution which I have been too dumb to find.

---

### Post by Psyco430404 on 2011-07-03
[http://ubuntuforums.org/showthread.php?t=1335416&page=2](http://ubuntuforums.org/showthread.php?t=1335416&page=2)

the second page of this thread should help you.

---

### Post by in-dust-rial on 2011-07-03
yes go for mint!

(and i would suggest KDE as dekstop manager too ...)

good luck

p.s.:
it strikes me that you are not clearly following a goal and that you can still learn a lot about the up-side of linux.
i strongly suggest to you my post from page one: 
-distinct /home partition 
-aptitude backup 

(no more subscribed to threat)

---

### Post by BigSilly on 2011-07-03
The top post reminds me of when I first started using Linux. Pfft, who am I kidding, it reminds me of when I first started using XP! :D

I can relate to it. It can be frustrating and seem complicated at times. But if you want to continue you will find that over time the things that seemed obtuse and difficult at first become easy to deal with and much less troublesome. A bit like when you started using Windows. If you have the time to learn a new way then continue, but if not I would recommend to stick with what you know.

You may have just been unlucky with (Ultimate) Ubuntu. I'm the same if it's any consolation, and cannot use Ubuntu as it doesn't work for me any more. Try other distros if you feel confident enough. Though Ubuntu is the biggest Linux name, it won't be so sparkling for everyone. Perhaps look into Mint or PCLinuxOS. I personally am using the latter and triple booting with OpenSUSE 11.4 and Windows 7. I'm very happy with my set up. :)

Good luck with what you choose. Though I will add that you sound like you'll be back. :) ;)

---

### Post by ShagzModo on 2011-07-03
start with using a clean distro... without too many tweaks... I was on ubuntu for 6 years, but now switched to Fedora Lovelock 15 this because i don't like the Unity desktop at all, and Gnome 3 is sweet. Everything just works!

---

### Post by wolfen69 on 2011-07-03
> **BigSilly said:**
> A bit like when you started using Windows.

Speaking of that, you should have seen me when I first tried windows. I was hopelessly lost, and broke it left and right. It took me a good month before I felt comfortable with it. As you can see, it's not just new linux users who feel lost.

---

### Post by mo66 on 2011-08-29
Hello, I use Ultimate edition. I love it. almost everything comes pre set up.    personally change themes as I do not like them.    

1. in the top right corner right click on (blue box  compiz fusion icon) and change the window decorator from Emrald to GTK window decorator.  

This allow you to change themes from the top left menu on desktop>system>apperance>themes   

After viewing themes tab you can customize it and there you can change mouse pointer

---

### Post by BlacqWolf on 2011-08-29
> **wolfen69 said:**
> 
Linux has been nothing less than spectacular for me. In the 20 years or so I've been using computers, linux has by far been the best computing experience I've ever had. But then again, I care enough to actually take the time to learn, and buy only 100% compatible hardware. 

Most people I know that has tried linux absolutely love it. From grandfathers to young geeks. Peace.

edit: btw, LinuxMint is pretty good and worth a try. It has all codecs and flash preinstalled. Try out a few live cd's and see how it goes.

You're absolutely right. I tried Ubuntu back when I was 11 or so, 9.04 was the latest stable release, and I was tired of Windows, and I needed something lightweight that was more up-to-date that I was going to put on a 16 year old PC I was keeping just for fun. Well, a college friend of mine suggest Ubuntu, and I loved it. Even the then-latest edition worked quite well on the outdated hardware, and I decided to also try it on my other desktop that I primarily use. Despite the learning curve, the failed installation because then I was naive and burned the installation disk at too high of a speed and it corrupted, and then the WLAN card I had didn't work, I stuck to it. After Ubuntu 10.04, the hardware worked flawlessly out-of-the-box on both the desktops (by then I had received a new laptop anyways). Now, since Ubuntu and Linux have matured a bit more and expanded hardware support, and now that I have a different computer which has hardware which is more compatible, I use it all the time. Everything worked out-of-the-box, except for best performance I had to use a proprietary video driver instead the open-source one. But that's it, quick fix and everything works. I love Ubuntu, and I love Linux. Enough that I've permanently ditched Windows and Mac OS (Mac OS I never liked to begin with).


 I've loved Linux and Ubuntu since I first used it, despite the compatibility issues at first, but now that's resolved. And, in terms of hardware support, Ubuntu, or Linux in general, is actually much better than Windows. Windows has little to no hardware support in most cases, just that things work better for it because it's the big guy, it's where all the marketshare is at and so it's where all the money is at. Therefore, the hardware manufacturers make the official drivers for Windows, and half the time Mac OS, while Linux isn't much of a big guy and so they won't bring in much money compared to Windows or Mac OS. And since Linux doesn't bring in as much money since it's not the big guy of the market, very few tend to make official drivers for it, while 99% of the time they provide functional drivers for Windows. So the problem with hardware support isn't really Ubuntu's fault or Linux's fault. It's because Ubuntu, or Linux in general, isn't the big guy of the OS market, so the #1 driver producer for Linux is the Linux community, not the official hardware manufacturer. Now that I have a computer that's just as well supported on Ubuntu as it it Windows, I dual booted them for some time to see how things went performance wise. In Linux, everything worked better. All except the video card worked at full speed out-of-the-box, which was resolved with a driver from nVidia. While in Windows, In had to get a driver for the sound card, wireless card, and video card. And since I had full support in both OSes, I saw how things were doing performance-wise. Using either KDE, Unity or GNOME, CPU and memory usage was always lower in Ubuntu. And certain applications that were available on Windows and Ubuntu worked faster in Ubuntu than they did in Windows. So at this, I removed Windows from my system. So, at this, it should be obvious why me and others in similar situations stick with Linux and love it so much. Compared to Windows, Linux feels more snappy, and I enjoy using it. It's customizable, fast, and reliable. This is why I stick with Ubuntu.

Ok, I'm done ranting. Carry on. :lolflag:

---

### Post by craig10x on 2011-08-29
As some others suggested...try Linux Mint...it's not as bloated as ultimate edition, and it looks great...also has just one panel on the bottom (like you are used to on windows) and a unique and very nice "mint menu"...

Also, all the multimedia codecs, flash, java, etc...are pre-installed (be sure to download the dvd not the cd version so you get everything in the initial download)...and like the Ubuntu forums, it has an excellent community...:)

Grab the "Main Edition" (Gnome)...it is based on the current ubuntu...At least run the live dvd and take a look at it...i think you will like it a lot!

---

### Post by BrokenKingpin on 2011-08-29
> **Topsiho said:**
> 
Why don't you try and explore a ***regular*** Ubuntu, instead of playing with an Ubuntu version that was tampered with by a third party? And then complain that things don't work?

++

I am running Xubuntu myself and haven't run into any of these issues. Just be patient and try working through the issues. You will always have a few issues learning a completely new system, but it gets easier.

When I was first learning Linux (almost 10 years ago) things were a lot harder than they are now, but I stuck with it. Now I wouldn't consider using anything else.

---

### Post by christopher.wortman on 2011-08-30
> **profozone said:**
> So I love the idea of linux and I do appreciate all of the support in the forums.  It looks like linux has come a long way for people who use GUI's but it also seems like I can't even finish setting things up and it's 100% frustration.

After loading it on, I was working to create the look I wanted.  I'm using Ultimate Edition 2.6.1 based on Ubuntu 10.04.  I hate the animated cursor that comes with it, so I go to "cursors."  Right.  That does nothing.  Don't even know why it's there.  Eventually I find "appearance" and I'm pleasantly surprised that I can change a lot of stuff about how it looks and it came out awesome.  But I noticed that none of the special effects worked.  It was because I did not have an nVidia driver for my card.  No problem.  I go online, eventually find one and then about 10 different ways of loading it.  So I try like 5 different ways, never knowing if I'm messing something up.  The final one being to take a lot of scary steps for a linux newb, but voila!  It loaded.  The effects were there and looked pretty cool.  However, the appearance I had set up was changed.  No problem, I'll change it back.  So I go into appearance and start putting things back, only now the cursor will only change when it's over a program.  When it's moved over the operating system windows and stuff it stays this stupid spinning arrow.  The window frame around each window wouldn't change at all and it's so dark I can't see the controls.

The internet runs very slow, but when I boot into Windows, there's no problem.  So I go online again.  Someone said to unplug the computer and hold down the start button to bleed of any extra charge, wait about 10 minutes and come back.  I did this and it seemed to make a lot of things snappier.  But the very next time I booted.  Same thing.  The internet actually works and sometimes it's fine, but most of the time it's nearly unusable.  I do not witness this in Windows.

I have a book that tells me how to get software.  Go into "Ubuntu software center," or Use "Synaptic."  It conveniently leaves out what to do when the package isn't there or the name has some cryptic identifier tacked on the end.

When I first started this endeavor a few weeks ago, I loaded Windows, then I loaded Linux.  No problem.  I put them on two separate drives, so I didn't have to worry about partitions.  I set everything up and started tackling one thing at a time.  I was told to allow the updates.  But when I did (not the kernel update), it broke the internet connection permanently.  Long searches didn't help at all.  So I reinstalled Linux and broke Grub.  It gave no options for Windows at all.  More long searches and I fixed grub and there was a window option, but it wouldn't boot into it.  Finally I fixed the windows bootloader and it works again.  So I ask.  Do allow updates again?  I don't want to do all of these searches and learn how to set up all of this stuff and get it working again, only to break it with one click of the update button.

Ok, so I've been venting for a while now.  It would be nice to have some kind of life preserver here.  Am I doing something wrong?  Should I use some kind of friendlier version of Linux?  Is linux just for guru's who know every little detail about all of the parts that make it work?  I don't want to go back to Windows, but I have to at least be able to surf the web.  That's 90% of my computer usage.  I couldn't even type this in Linux.  I had to go into Windows to get a connection that actually worked.

For the love of all that is holy, try Kubuntu 11.04. Friends don't let friends use Gnome. lol Gnome and other DEs are all underdone and under achievers. KDE is the only sane choice.

---

### Post by drawkcab on 2011-08-31
If you're new to Ubuntu and Linux more generally, working through the ubuntu guide is key: 

[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

---

### Post by Topsiho on 2011-08-31
> **christopher.wortman said:**
> For the love of all that is holy, try Kubuntu 11.04. Friends don't let friends use Gnome. lol Gnome and other DEs are all underdone and under achievers. KDE is the only sane choice.

I am glad you like Kubuntu so much. Really good for you.
I was using Kubuntu with much satisfaction too, until KDE4 came around, which for me didn't work as I was accustomed to. Many things did not work, and too many bugs shattered my user satisfaction.

After that I used Ubuntu. It's much simpler, such as an OS ideally should be (one should not notice what OS one is using, one should only need to concentrate on what problem one tries to solve using the computer). I learned to love it.

Now Gnome is being replaced with either Gnome3 or Unity. The situation now is the same as when KDE4 was started: many things don't work as one is accustomed to, many things don't work at all. After a new install one has to twiddle with the graphics card as 3D acceleration is needed, but the open source graphics driver doesn't deliver 3D acceleration (out of the box).

This need to twiddle before things work is very frustrating for a new
user, and is contra the squashing of bug #1, which is to wipe Windows from the desktop (if I remember correctly).

Now I am trying Kubuntu (11.04) again, and it works far better now, though I have the impression that my computer is much slower using Kubuntu, then before. But I like experimenting with it, in order to be prepared to return to Kubuntu if Ubuntu 10.10 is not far better then 10.04.

I really like the simplicity of Gnome2. With a number of applets in the upper panel, and a rather clean bottom panel.

Topsiho

---

### Post by BrokenKingpin on 2011-08-31
> **christopher.wortman said:**
> For the love of all that is holy, try Kubuntu 11.04. Friends don't let friends use Gnome. lol Gnome and other DEs are all underdone and under achievers. KDE is the only sane choice.
This is the most ridiculous thing I have read on here in a while. Gnome (2) is far more stable than KDE every has been, and probably ever will. It has all the required options to configure your environment. KDE has a some really cool design concepts, but it is extremely buggy and the configuration is a bloody mess. People have been using Gnome for years without issues.

---

### Post by ilovelinux33467 on 2011-08-31
> **BrokenKingpin said:**
> This is the most ridiculous thing I have read on here in a while. Gnome (2) is far more stable than KDE every has been, and probably ever will. It has all the required options to configure your environment. KDE has a some really cool design concepts, but it is extremely buggy and the configuration is a bloody mess. People have been using Gnome for years without issues.

KDE 4 may have been buggy in earlier versions (4.0 to 4.3) however in the newer versions (4.4 - 4.7) in my experience I haven't experienced any buggyness. Also the configuration IMO is one of KDE's best features.

---

### Post by tukmont on 2011-08-31
Just my 2 cents... Ubuntu has been nothing short of spectacular for me. A few small frustrations, but I chalk that up to my inexperience. There was one issue that I think I resolved that has been a problem for some folks I have noticed.
 
I put 10.10 on an HP netbook and had no wireless. I tried a number of things, but finally upgraded to 11.04 and that did the trick. Wireless active and all seemed good, until it started dropping the connection every 5 min or so. What I did then was to disable the "connect automatically" in the network manager (I think). That fixed that... I'm online, no dropping and the connection seems quite a bit faster.
 
I'm really quite a noob, but I hope others can benefit from the fruits of my frustration!
 
Cheers

---

