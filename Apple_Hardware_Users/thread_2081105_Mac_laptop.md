---
title: "Mac laptop"
date: 2012-11-05
forum: Apple Hardware Users
---

### Post by offgridguy on 2012-11-05
Hello Apple users; I am considering a new laptop and would like to try a mac.I have no experience with apple but the reputation is good,  I realize they are not cheap,  size is not critical, as
it's not going to be taken anywhere very often.   Besides the basics, I use a computer for photo editing and management.  I have
been told apple is the best for programs with lots of graphics.
Any suggestions on model, etc.?:)

---

### Post by 2F4U on 2012-11-06
Should it be a laptop or a desktop? Technically, there is not much difference, because Apple desktops (aside from the PowerMac) uses notebook technology. But you get a large screen with the iMacs.

---

### Post by offgridguy on 2012-11-06
> **2F4U said:**
> Should it be a laptop or a desktop? Technically, there is not much difference, because Apple desktops (aside from the PowerMac) uses notebook technology. But you get a large screen with the iMacs.

I would_ love_ to have a desktop, with a large high resolution screen, remote keyboard  along with the tons of memory and ram.
    However I am in a unique situation,  as my username suggests  we live off-grid
and power our home entirely on solar power.  Hence power consumption is
always a concern, especially in the winter season when days are short, sky's are
cloudy or snowy, and  electrical usage increases with more lights, etc.
       During the summer months we have abundance of energy and could easily
use a desktop computer, but we couldn't use it year round, so we get by with
laptops, because when can use one year round due to the lesser power
requirements.
    I have considered a remote monitor, connected to the laptop for the summer months, actually about 8-9 months are no worry, only Nov.,Dec.,Jan.
    Monitors of course being the major power consumer of a computer system.
A rather long reply to your question ,I know, but thanks for asking. :)

---

### Post by Lars Noodén on 2012-11-06
The older notebooks based on PPC draw a lot less power, about half according to the adapter specs. (If I read them right)  They'll run Lubuntu just fine.  However, they are getting to be quite old at this point.  

I had a lot of luck running 10.10 on a Macbook pro, but more recent versions are not recommendable at all until some bugs are fixed with the track pad, heating and (possibly) battery cycling.  So if you go with a newer (Intel) MBP you are looking at running a version of Ubuntu  prior to 11.04

---

### Post by offgridguy on 2012-11-06
Thank you Lars, I appreciate the input.

---

### Post by 2F4U on 2012-11-06
If power consumption is an issue, at least during winter, a MacBook Air would probably the best solution. You can get that with 11" and 13" screen size and they come with Intel processor and graphics, but would still have enough resources for the intended usage patterns.
The MacBook Pro's are obviously more powerful, but due to their graphics cards and bigger high resolution screens draw a lot more power.

---

### Post by offgridguy on 2012-11-06
> **2F4U said:**
> If power consumption is an issue, at least during winter, a MacBook Air would probably the best solution. You can get that with 11" and 13" screen size and they come with Intel processor and graphics, but would still have enough resources for the intended usage patterns.
The MacBook Pro's are obviously more powerful, but due to their graphics cards and bigger high resolution screens draw a lot more power.

The mac book pro may be okay, the computer I use now is not a real power miser
and it is possible to curtail the computer use for a day or two if necessary  :(
     Do you know if it has SSD?

---

### Post by Lars Noodén on 2012-11-06
The Macbook pro can come with an SSD.  Check their online store for details.  The Macbook air only comes with an SSD.  The quality seems to have come down in recent years.  Also, the way OS X has been heading has not been favorable for user freedoms.  On the plus side, it now uses PF for a packet filter even if an old one.  If you run Linux inside a VM on OS X, the VM will use a lot of power.  No clue how or if you can use an external monitor with them on Linux, there is no longer a dedicated monitor port.

---

### Post by offgridguy on 2012-11-06
Very interesting Lars,  Thank you.  By the way do you have an idea what the 
battery life might be ?
    Right now with my acer aspire 5735Z ,  I average from 2 to 2 1/2 years,  the
folks at battery world tell me this is very good.

---

### Post by Lars Noodén on 2012-11-07
The claim on the web site is about 7 hours, but that's for OS X and without running peripherals like a 3G dongle.  With a 3G dongle, I've gotten about 3 hours.  But that's also with Lion, which is supposed to be worse than Snow Leopard.

With 10.04 or (defunct) 10.10 you might get 3 hours or so also, I can't recall.  With 12.10, it appeared to be sometimes discharging the battery even while connected to the mains, that's a dangerous and intolerable situation.  I'll wait a week or so and try again with the development version of 13.04.

---

### Post by offgridguy on 2012-11-07
That looks comparable to most pc's, the manufacturer claims are usually higher
than reality.
    I am wondering about dual boot issues with apple, but maybe I should start a new thread for that ?

---

### Post by the8thstar on 2012-11-07
Hello Offgridguy,

My personal experience with iMac and MacBook Pro have been very good. The computers are pricy but it's worth the buy, trust me. Apple support has been steadfast and helpful, so I would also recommend buying their products because of this.

In your situation, if you limit yourself to mostly photo and video editing, I believe a new MacBook Air would do just fine. The MacBook Pro I had was overkill for everyday work, so I sold it. The resolution is 1440x900 if I recall correctly. And it comes with SSD by default, which is nice.

On a side note, you might be interested in one of the Retina MacBook Pros (13 or 15") because of the crisp resolution they provide.

Hope you find my 2 cents helpful.

---

### Post by Lars Noodén on 2012-11-07
Dual boot works ok.  I use rEFIt for that, though maybe something newer and better has since come along.  You have to install OS X first and leave a partition for Linux plus maybe a data partition.  Linux supports HFS+ filesystems but not journaling yet.  So you can use HFS+ to share a partition between OS X and Linux if you first turn off journalling.

---

### Post by the8thstar on 2012-11-07
Dual boot is hit and miss at best. I personally was never able to set up a proper Ubuntu system with rEFIT or BootCamp on my rigs. 

Eventually, I chose to use VirtualBox and it proved to be a good idea, for two reasons :

1. Direct access to files for both Linux and OS X simultaneously
2. No problems with wifi, sound and graphics drivers, thanks to emulation

---

### Post by Lars Noodén on 2012-11-07
the8thstar, what did you set in Virtualbox to be able to copy and paste between the VM and OS X?  That's something I have somehow missed.  Another drawback to running a VM is the increased power consumption which also shortens the time available on battery.

---

### Post by the8thstar on 2012-11-07
> **Lars Noodén said:**
> the8thstar, what did you set in Virtualbox to be able to copy and paste between the VM and OS X?  That's something I have somehow missed.  Another drawback to running a VM is the increased power consumption which also shortens the time available on battery.

1. I activated the "shared folders" option in the host. 
2. I installed the guest addtions in the guest.
3. And if I recall correctly (since I'm not using VBox right now) I had to fiddle with the command line to add myself (home user) to the virtualbox usergroup in the guest machine.

Does this help you?

---

### Post by the8thstar on 2012-11-07
Ok, this is the command line to use :

> sudo adduser *username* vboxusers

...where *username* is your home folder name of course.

---

### Post by offgridguy on 2012-11-07
> **the8thstar said:**
> Hello Offgridguy,

My personal experience with iMac and MacBook Pro have been very good. The computers are pricy but it's worth the buy, trust me. Apple support has been steadfast and helpful, so I would also recommend buying their products because of this.

In your situation, if you limit yourself to mostly photo and video editing, I believe a new MacBook Air would do just fine. The MacBook Pro I had was overkill for everyday work, so I sold it. The resolution is 1440x900 if I recall correctly. And it comes with SSD by default, which is nice.

On a side note, you might be interested in one of the Retina MacBook Pros (13 or 15") because of the crisp resolution they provide.

Hope you find my 2 cents helpful.

Thank you for the input.

---

### Post by offgridguy on 2012-11-07
> **the8thstar said:**
> Dual boot is hit and miss at best. I personally was never able to set up a proper Ubuntu system with rEFIT or BootCamp on my rigs. 

Eventually, I chose to use VirtualBox and it proved to be a good idea, for two reasons :

1. Direct access to files for both Linux and OS X simultaneously
2. No problems with wifi, sound and graphics drivers, thanks to emulation

I appreciate the advice, before I lay down a lot of $$$ for a new 
computer i like to hear the pro's and con's,  and what things to avoid.  Thanks again.

---

### Post by the8thstar on 2012-11-08
Sure thing, I'm glad to help. 

One more thing to remember : Ubuntu is not yet optimized for the Retina display. I'm not sure that Windows 7 or 8 are either.

That means that on one hand you'll get a super high resolution in Ubuntu or Windows, with lots of real estate. On the other hand, everything will look extremely small ! So be warned.

To further this up: 
1. [http://www.anandtech.com/show/6008/windows-8-on-the-retina-display-macbook-pro]("http://www.anandtech.com/show/6008/windows-8-on-the-retina-display-macbook-pro")
2. [http://www.omgubuntu.co.uk/2012/06/what-does-ubuntu-look-like-on-a-retina-display-bad]("http://www.omgubuntu.co.uk/2012/06/what-does-ubuntu-look-like-on-a-retina-display-bad")

---

### Post by offgridguy on 2012-11-08
Thanks again , the8thstar,  I'm glad to know this beforehand.

---

### Post by pschyska on 2012-12-25
About native dual-booting: I'm dual booting OSX 10.8.2 and Ubuntu 12.10 currently, until my pc laptop arrives :-)
It works quite well, the touchpad behves a bit differently like in OSX (worse in Ubuntu, but still OK), and I didn't have any sort of driver issues. Battery life isn't that great though (about 75% of OSX's, ~3h on my 2012 MBP 13" with 2.9ghz i5).
I had to use re**find** as re**fit** bugged out. Refind is a fork of the unmaintained refit.

As far as virtualization goes, I made good experiences with VMware player, which is free (not OSS), and gives me better performance. Virtualbox should work as well, though.

---

### Post by offgridguy on 2012-12-26
Thanks for the input pschyska,  As to the mac laptop, i'm thinking i probably
wouldn't dual boot as i have another laptop already dedicated to linux.
   I am hoping that the mac can replace the photo editing functions that i use 
windows for.   I don't use ubuntu for photo editing at all as i don't care for any of the current open source photo management software.

---

### Post by pschyska on 2012-12-27
> **offgridguy said:**
> Thanks for the input pschyska,  As to the mac laptop, i'm thinking i probably
wouldn't dual boot as i have another laptop already dedicated to linux.
   I am hoping that the mac can replace the photo editing functions that i use 
windows for.   I don't use ubuntu for photo editing at all as i don't care for any of the current open source photo management software.

I kanged my other thread with my view on macs: [http://ubuntuforums.org/showpost.php?p=12423868&postcount=14](http://ubuntuforums.org/showpost.php?p=12423868&postcount=14)

If you need Photoshop, there isn't really another option than Mac OSX. Don't use Windows, life is too short for that **** :-)

---

### Post by offgridguy on 2012-12-28
> **pschyska said:**
> I kanged my other thread with my view on macs: [http://ubuntuforums.org/showpost.php?p=12423868&postcount=14](http://ubuntuforums.org/showpost.php?p=12423868&postcount=14)

If you need Photoshop, there isn't really another option than Mac OSX. Don't use Windows, life is too short for that **** :-)
Thank's for the link :)

---

### Post by fulopattila122 on 2012-12-29
> **pschyska said:**
> About native dual-booting: I'm dual booting OSX 10.8.2 and Ubuntu 12.10 currently, until my pc laptop arrives :-)
It works quite well, the touchpad behves a bit differently like in OSX (worse in Ubuntu, but still OK), and I didn't have any sort of driver issues. Battery life isn't that great though (about 75% of OSX's, ~3h on my 2012 MBP 13" with 2.9ghz i5).
I had to use re**find** as re**fit** bugged out. Refind is a fork of the unmaintained refit.

As far as virtualization goes, I made good experiences with VMware player, which is free (not OSS), and gives me better performance. Virtualbox should work as well, though.
I'm also using dual boot OSX/Ubuntu on a Mac with refit, and keep having issues. Can I update refit to refind without destroying existing installations?

---

### Post by powerpcliberation on 2012-12-29
> **fulopattila122 said:**
> I'm also using dual boot OSX/Ubuntu on a Mac with refit, and keep having issues. Can I update refit to refind without destroying existing installations?

In my experiences there are generally always issues when OS X and Linux share a drive.  When possible you should dedicate a drive to each.  This is tricky when you have a laptop but you could always boot the lesser used one from a high speed thumb drive.

---

### Post by offgridguy on 2012-12-30
As mentioned earlier in this thread, you can dual boot using virtual box.
Something i personally have no experience with.

---

### Post by pschyska on 2013-01-08
> **fulopattila122 said:**
> I'm also using dual boot OSX/Ubuntu on a Mac with refit, and keep having issues. Can I update refit to refind without destroying existing installations?

I guess you can simply install refind over refit. It's an EFI boot loader so it replaces refit on the (normally hidden) EFI partition on the disk (it's a fat volume in case you wanna mount it, there are howtos on the internet to make it visible).
The only downside I noticed it that there is a about 30s delay for me before showing me the boot options (osx and linux in my case). As I use hybrid standy mostly this doesn't matter much for me.

Do a backup just in case :-)

---

