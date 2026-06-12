---
title: "Services"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by jfh1993 on 2007-01-16
Hello,

I purchased an old computer on Craigslist (500 mhz, 128 RAM - Ubuntu already installed. $40) ... faster than a 1000 mhz, 512 RAM windows box. Happy so far, though I just used OpenOffice Writer, and it took 1 minute to get to a blank doc!

First thing I was told to do was Add User - Adv tab, change profile from Desktop to Administrator ...

I've added/removed a few programs using that user name password, and am generally happy with my box so far (some pages need Flash 9 instead of 7).

But I was reading some about security, and one suggestion that has me intrigued is "Get rid of services that you don't need" ... so I went to system/administration/services, typed in my password, and saw that 2 computer activities loggers and 3 actions scheuler services were active,and a couple others ... which made me, a very inexperienced computer person, wonder whether the seller can permanently log my computer activities ... would he have had the opportunity to install certain things before delivering the box, and be able to remotely "read" my computer files, or whatever? Especially if, through emails, he was able to discern my ip address ... could he then ssh or whatever, and remotely control my box?

Paranoid and ignorant ...jfh

---

### Post by IusedTObeSOMEONEelse on 2007-01-16
Just a suggestion, you mention faster than a windows box, of course:)  but I would get a Xubuntu cd and install it. Even better performance out of an older machine:p  Sally                                                                                                                                         Edit: then you could tweak it to your liking and your security issues(personal) would be solved as well

---

### Post by eXisor on 2007-01-16
Firstly, I second the suggestion to use xubuntu for this particular box. You'll notice the speed improvement.

Secondly, I'd reformat the drive and start clean with the xubuntu install. This is not paranoia, just being prudent.

---

### Post by jfh1993 on 2007-01-16
Thanks for the xubuntu suggestion (would that work best for the 1000 mhz, 512 RAM boxes as well?) ... wonder where/how to get that cd, because I don't have a cd burner ... are these types of cd's sometimes found inside a Linux Tech magazine? Any ideas on how to quickly get my hands on an xubuntu cd, besides asking a friend? any rate, does xubuntu 6.1 have firefox 2.0, flash9, and all that surfing stuff in the add/remove program interface, or already installed? 

I didn't get a clear answer on whether the seller COULD be actually logging info from my box or not? Is it possible? I sort of trust him, though I don't know him from adam ...

Also how difficult and necessary would it be to install and use firestarter (though I do have a router that serves as a firewall (a D-Link DI-624)? 

The reason I had someone else install the os was because I avoid dealing with wierd h/w issues ... AND a lot of time is saved with install, updates, etc (another thing I noticed in my time using ubuntu 6.0.6 was that the loading of program/installing was quite slow - and of course OpenOffice was way slow (that won't change w/ a new os obviously). 

So what is diff about xubuntu anyway - is the gui more clunky than gnome? What makes it faster? Thanks.

---

### Post by ardchoille42 on 2007-01-16
> **eXisor said:**
> Firstly, I second the suggestion to use xubuntu for this particular box. You'll notice the speed improvement.

Secondly, I'd reformat the drive and start clean with the xubuntu install. This is not paranoia, just being prudent.

I totally agree with both of eXisor's suggestions. Good ideas.

---

### Post by steve.horsley on 2007-01-16
The GUI is more lightweight - less bloat and widgets I believe. I'm not sure "klunky" is the rihgt word, but I admit I haven't seen Xubuntu. 

Theoretically he could have planted things on there that you would probably never find. You can see what network ports are open with the command **netstat -lntu**, and looking for local addresses that are not 127.0.0.1. Even if nothing is listening at the moment though, it doesn't mean there's nothing that calls home occasionally. How much do you trust him? Reinstalling is fairly easy, but getting the network working again may take some effort.

---

### Post by Delkster on 2007-01-16
> **jfh1993 said:**
> so I went to system/administration/services, typed in my password, and saw that 2 computer activities loggers and 3 actions scheuler services were active,and a couple others ... which made me, a very inexperienced computer person, wonder whether the seller can permanently log my computer activities

If you don't trust the person who installed the computer, well, it's of course possible that he would have installed something that could monitor the computer. In fact, since he installed it and had adminitrator privileges, he could have installed anything.

I assume that the logging services you found are klogd and sysklogd, and that the schedulers are anacron and atd. Right now I can't think of a third one that would fit the description, except cron, but I don't think it's shown in the services administration list. You needn't be worried about the four services I mentioned, as they're standard in a fresh Ubuntu install.

But again, it completely depends on whether you trust the person who installed it. Would you trust him to install a Windows system for you?

If you end up installing Xubuntu, remember that its graphical user interface is probably a little more ascetic than the Gnome desktop that comes with the traditional Ubuntu. If the system currently works fine with your hardware and the person who installed it didn't do any particular magic tricks, it'll very likely just work with a fresh Xubuntu install as well. It was probably a good idea to have someone else do the recon first, though. ;-)

---

### Post by zerhacke on 2007-01-16
> **jfh1993 said:**
> Thanks for the xubuntu suggestion (would that work best for the 1000 mhz, 512 RAM boxes as well?) ... wonder where/how to get that cd, because I don't have a cd burner ... are these types of cd's sometimes found inside a Linux Tech magazine? Any ideas on how to quickly get my hands on an xubuntu cd, besides asking a friend? any rate, does xubuntu 6.1 have firefox 2.0, flash9, and all that surfing stuff in the add/remove program interface, or already installed? 
Most all computer companies, little local shop to big chain, will download and burn an ISO image for you for a nominal fee.  I live in a very small town of less than 10,00 people and there's three shops here that will burn a disc for you.  I'm sure you could find something.  Barring that, it shouldn't be too hard to find someone on the forum who could send you a copy.  What I'd do is make a new thread asking for someone to send you a CD if you cannot find a mom and pop computer shop willing to make five bucks to create the CD for you.

> I didn't get a clear answer on whether the seller COULD be actually logging info from my box or not? Is it possible? I sort of trust him, though I don't know him from adam ...
Oh yes, it's quite possible they could be logging your actions.  I have a friend who used to thumb his nose at Linux security buffs by installing a kernel module he created.  This kernel module just records every keystroke and at regular intervals dumps the log to a file and emails it out to himself.

Thing is, it's not likely.  One would have to have a pretty good knowledge of programming to create that kind of a module.  Then they'd have to know how to insert the module on boot every time - which, yes, is easier than creating the module in the first place.  If this guy knows enough to sell Linux based systems it's possible but I wouldn't call it likely.  After all, how much does he stand to gain by logging your Hotmail password and looking at your junk mail? (yes, this is an oversimplification but you get the point)  The average end user who is just now getting into Linux isn't going to be doing anything interesting enough to want to log.  Maybe if he were a control freak...

If it worries you enough, just reinstall the OS.  It's pretty easy to install anymore, asks very few questions, and if you would reinstall you would be sure that there's no spy software running.

> Also how difficult and necessary would it be to install and use firestarter (though I do have a router that serves as a firewall (a D-Link DI-624)? 
Firestarter is in the repositories, and I'm pretty sure it's in one of the ones turned on by default.  No mucking around with repository lists, you'd be able to get it without any work.  Just use synaptic or apt-get and you're set.

> The reason I had someone else install the os was because I avoid dealing with wierd h/w issues ... AND a lot of time is saved with install, updates, etc (another thing I noticed in my time using ubuntu 6.0.6 was that the loading of program/installing was quite slow - and of course OpenOffice was way slow (that won't change w/ a new os obviously). 
I'd be willing to bet you money that 6.06 would detect any hardware you have other than printers and a wireless network card out of the box.  Even then many printers and wireless cards are detected.  If worst comes to worst and your wireless network card didn't work, you could connect to your D-Link router with a hard wire, get on the net, and ask us how to use your wireless . . . assuming you have one.

> So what is diff about xubuntu anyway - is the gui more clunky than gnome? What makes it faster? Thanks.
Xubuntu is exactly like Ubuntu, except that instead of using Gnome and the gnome libraries it uses XFCE as a window manager.  I think Xubuntu still does load some gnome libraries but it's not the whole full blown Gnome install.

Some people like Xubuntu better than Ubuntu or Kubuntu because the window manager is lighter on resources and somewhat faster to respond than (K)Ubuntu.

---

### Post by Delkster on 2007-01-16
> **jfh1993 said:**
> Thanks for the xubuntu suggestion (would that work best for the 1000 mhz, 512 RAM boxes as well?)
I've set up Ubuntu (with Gnome) on a box with Duron 1000 MHz and 512 MiB RAM (not my own, though) and it runs decently. I've also used Ubuntu on a laptop with a P3 1000 MHz and 256 MiB RAM and it ran okay considering the amount of RAM and that I was using it for somewhat memory intensive things.

> (another thing I noticed in my time using ubuntu 6.0.6 was that the loading of program/installing was quite slow - and of course OpenOffice was way slow (that won't change w/ a new os obviously).
If, by "loading of program/installing" you mean Add/Remove Applications (a.k.a. gnome-app-install), I think it's a bit faster to load in 6.10, although it still wouldn't win a race.

> So what is diff about xubuntu anyway - is the gui more clunky than gnome? What makes it faster? Thanks.
I don't know what makes it faster because, frankly, I haven't put any time into that (I tried Xfce once on Debian a couple of years ago), but my educated guess is that the base operation is about as simple in Xfce as it is in Gnome but there are probably fewer graphical tools for things so you may end up on the command line more often.

---

### Post by jfh1993 on 2007-01-16
The easiest thing is for me to keep all as is, and count on this guy being decent ... said he helps friends move all their data from old to new machines - in return he resells the boxes, with linux os, to people curious, and wanting to learn linux ... he works on mainframes for a living, and is familiar with unix/linux ... seems ethical, and is fair and straightforward when it comes to answering tech questions. But of course I know nothing about him, so it's all a leap of faith. 

I don't think he has the time to care what I do on the computer, but I'm clearly inexperienced and he could take advantage of that by getting access to my online banking passwords, forms I fill out that include ss#'s, etc ... access to files ... and I'm sure looking into what services are going is not the best way for me to figure out what might be happening (btw, services are anacron, atd, cron, klogd, sysklog, gdm, cupsys ... harmless I gather from one of the responses to my lonnngggg posts ..).

So, I could simply avoid doing that kind of work on this computer, and continue to gain experience slowly but surely (I did application/accessories/terminal, and followed a great tutorial to install the acroreader plugin: ([http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox.html)) That's the kind of experience I need to get comfortable with linux ....

Would that be prudent? Leave this box as is, and try to install the most stable (i.e. 6.0.6, NOT 6.1) ubuntu onto the 1000 mhz, 512 machine, while keeping all my bookmarks and tutorials on the original ubuntu box (i'm thinking that xubuntu may not have enough friendly graphical stuff for me .... true?)

---

### Post by eXisor on 2007-01-17
I'd install from edgy (6.10) rather than dapper (6.06) since the supported hardware/compatibility/recognition is better. It's been stable on all my boxes.

Xubuntu is fully functional and has equivalent apps to your ubuntu install. You'll have everything you'll need. The xubuntu apps are just chosen/optimised for low memory systems. Also, the xubuntu interfaces/menus are straight forward and you won't find it more difficult than the ubuntu he loaded for you. (One notably absent function is the file search option for the xubuntu file manager - thunar, but there is a script - available on these forums - you can attach to thunar which gives you search functionality).

I agree the risk is low that the guy sabotaged your system, but since I'm an untrusting sod I'd do a reformat and clean install anyway. If he got everything working that proves there are no hardware incompatibilities, so you'll probably get it going without too much effort. Help is always just a post away. 

If you do decide to stick with his install, at the very least install firestarter from the repos and check the many firestarter threads to get an idea of what you should see for a standard ubuntu install.

But my advise is... dive in, reformat,  and back yourself to get it all going from scratch. You'll learn some very important lessons and be that much closer to independence in linuxland. Besides, you're inevitably going to bork you're install sometime and have to start from scratch, so rather do this willingly than with your back to a wall.

Welcome and the best of luck for the steep learning curve ahead.

---

