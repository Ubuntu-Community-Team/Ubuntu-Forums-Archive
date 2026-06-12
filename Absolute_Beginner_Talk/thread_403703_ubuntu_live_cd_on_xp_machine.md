---
title: "ubuntu live cd on xp machine"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by pgheric on 2007-04-07
Hi all, 

Just you typical problem. Can't seem to get the ubunto live cd to run on my xp machine. anyone help.....................please!0000000

---

### Post by HokkaidoHillbilly on 2007-04-07
Did you partition your hard drive so that Ubuntu has an unallocated partition to install to?

---

### Post by xpod on 2007-04-07
You dont need to do anything to try the live cd out other than make sure it`s burned correctly and make sure your bios is set to "boot from cd-rom" first.

It should boot up to the start menu regardless of any pre-partitioning if you`ve done the above correctly.
Of course if you want to install it then pre-partitioning is one way to do things but you should be trying Ubuntu out from the live cd first for a while just to make sure it`s really for you.....and of course your hardware.:)

---

### Post by Strelz on 2007-04-07
I'm having the same problem.  Can't install from the disk over my Windows XP.  I have an inspiron 1150 notebook.  I tried safe graphics mode.  I checked that the disk is ok.  Is it necessary to first partition, and if so, could you please explain more detail on how to do this?  

I get a drop down that says install.  I click on it, and within a few minutes, there is no appearance of any activity, the clock stops, and the mouse is dead.

---

### Post by houstonbofh on 2007-04-07
To both people with issues, Please...  We need more information.

pgheric - What do you mean?  Does it boot?  Does it try to boot and fail?  If so, where?  What kind of system?  What Video card, and how much memory?

Strelz - How much memory in the 1150?  What version of Ubuntu?  There is a odd problem in the 1150 with Video and Edgy.  I installed Dapper on mine with no issues.  The Upgrade to Edgy went fine.  You may want to try that.  Also, if you have less than 512 meg of ram, you may want to use the alt install method.  256 meg or less makes for difficult installs.

---

### Post by xpod on 2007-04-07
This place will explain many of the basics for you`se.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Strelz on 2007-04-07
I have 256 meg memory and the graphics is the Intel 82852 which I'm guessing is some built in graphics chip set.  I have the 6.10 disk.  I don't have a disk of the previous release.

When I tried safe mode, it got futher than in normal mode.  I clicked on Install, and saw a drop down with "Install" on it.  Later, a  window came up that had "Install" on the title bar.  Eventually that window went away and the screen became dark.  Then all activity appeared to cease after about a half hour of grinding away with the screen dark.  When activity ceased, the CD lite stopped flickering and I could not hear the hard drive doing anything.  Perhaps I am too impatient and did not wait long enough?

I don't know what you mean by "alt install".

---

### Post by confused57 on 2007-04-07
> **Strelz said:**
> I have 256 meg memory and the graphics is the Intel 82852 which I'm guessing is some built in graphics chip set.  I have the 6.10 disk.  I don't have a disk of the previous release.

When I tried safe mode, it got futher than in normal mode.  I clicked on Install, and saw a drop down with "Install" on it.  Later, a  window came up that had "Install" on the title bar.  Eventually that window went away and the screen became dark.  Then all activity appeared to cease after about a half hour of grinding away with the screen dark.  When activity ceased, the CD lite stopped flickering and I could not hear the hard drive doing anything.  Perhaps I am too impatient and did not wait long enough?

I don't know what you mean by "alt install".
I believe they're referring to the alternate install cd:
[http://ubuntu.cs.utah.edu/releases/6.10/](http://ubuntu.cs.utah.edu/releases/6.10/)

You'd need to download & burn it to cd, here's how burn an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Maybe this will help with the live cd:
[http://ubuntuforums.org/showthread.php?t=313406](http://ubuntuforums.org/showthread.php?t=313406)

---

### Post by Strelz on 2007-04-07
Thanks very much for your answer Confused.  And I appreciate the other replies as well.

Basically what I'm after is one of two things.  I bought ($5) a CD with the expectation that I could use it to install Ubuntu on my Inspiron and that 256 Meg memory would be enough.

If anyone can help me, I would like to resolve this is in one of two ways, neither of which involve any fiddling or downloading something else:

1)  There is a way to do the installation.  I don't care what I have to do if someone can tell whatever that might be.  But I'd like to find out if there is indeed a way to do it with the disk I bought.
2)   There is no way to do it and I wasted my $5 (not such a big deal) but at least now I know not to waste any more time.  Maybe there was even  a notice on the Ubuntu web page that I missed.

---

### Post by houstonbofh on 2007-04-08
There is a odd bug in graphics on the Inspiron 1150.  The easiest way to do it is to burn the dapper version of the alt install cd.  There may be other ways with the CD you have, which you still have not identified.  However, it sounds like you may just not want to go to the effort.  This is fine, as Ubuntu may not be the best solution for you.  If you want to try, we are here as long as you are willing.

First, what version do you have?  Does it boot into a desktop at all?  If so, we can do this, but it will not be the normal method...

---

### Post by Strelz on 2007-04-08
Houston,

I very much appreciate your reply.  I'll tell you everything I can, and I would like to try with the disk I have.

I think there is a small principle here.  I very much hope that Ubuntu can be for me and indeed everyone.  If this is to be so, then it must be possible to obtain a disk and install with one click, or see from a list on the web site that ones computer is not supported and don't even try. 
But  if this is not possible with an Inspiron yet, so be it, it's just a small problem that I'm sure will be overcome in time.

Having said that, I would like to go into hacker mode and try to get this to run.  So now let me tell everything I can.  I will follow any advice you give.  You can AIM me ( Strelz) if you think that would help.

The disk is 6.10 i386.  I got it two days ago.

When I boot it, I get the Ubuntu screen.  I can open device manager and see that it seems to see everything.  For example, it lists the graphics chips, it sees the usb ports, the mouse, etc.  I have no floppy.  My Ethernet port is also seen.  So, looking at the device manager list, I think to myself that all should be ok.  The clock in the upper right hand corner is running.  The mouse moves ok, but is jerky.  

I see an icon of a disk in the upper left hand corner that says "Install"  

When I click on the Install icon, a drop down appears.  The system then freezes, but I can hear activity for a while.  When I boot in safe mode and try this, it goes much further.  In safe mode, a window comes up with the title bar "Install" on it.  But then it dies after grinding away for about a half hour.

On boot up there are error messages on the screen that fly by too fast for me to read them.

I did not partition my disk or attempt to do anything to windows.  I am willing to do anything to the machine before booting that you might suggest.  I don't care if I have to delete any files before booting again.  If you want me to partition the disk in some way, please tell me how to do this as I don't know.

I did follow the links that Confuse gave me and I downloaded that other version of Ubuntu 6.10.  I downloaded the burner he suggested, but when I burned the CD, I must have done it wrong.  I checked "boot disk" and when I booted up the disk that resulted, it came up in DOS with instructions in German (I am not making this up).  Now fortunately, I can read German, so I was able to read the instructions.  None of them seemed to tell me how to continue with a Ubuntu boot.  By this time I knew that I had wandered pretty far into this strange land where perhaps I didn't belong.  

Thanks very much for your help Houston, I am here in orbit awaiting further instructions.

---

### Post by Strelz on 2007-04-08
Ok, I ginally got Ubuntu installed on my Inspiron and it works fine.  Let me give the exact steps I used in case anyone else has the same problem.

1) Follow the link supplied by Confused:

Download this .iso file::
[http://ubuntu.cs.utah.edu/releases/6.10/](http://ubuntu.cs.utah.edu/releases/6.10/)

2) Get the recommended burner software at:
[www.cdburnerpro.com/](www.cdburnerpro.com/)

Install this.  You can't burn a CD with Windows because it treats an iso file as data and wouldn't make a proper bootable disk.  Don't get any other software, there is no need to verify as the boot process includes a disk checker.

3) Open cdburnerpro and click on "Create a new Data-CD/....".  Then click on file -> Write disk from iso file.  This opens a dialog box.  At the very top of it is a button that you use to browse to where you stored your downloaded .iso file.  The only other setting you can chose is "final". Don't change any other setting.  Click on "Write Disc".

A mistake I made (among many) was using other options with this tool that created the wrong kind of disc.

4) Create a 3 GByte partition on your Inspiron.  Go to disk manager and use help if you need to figure out how to do this.

5) Insert the newly burned CD into the Inspiron and restart it.  Click f12 as it starts up.  When you get a Ubuntu menu, accept the first option, "start in text mode".  Then all you need to do is answer all the questions as they come up.  Windows and all your files will be completely erased.

The Ubuntu installation with this CD goes very smoothly and takes less than a half hour.  The performance of Ubuntu on an Inspiron is quite good.  The installation found my network connection, and when Ubuntu came up, I could click on Firefox and get right to the internet.

I would suggest to the Ubuntu team that it would be helpful to direct owners of such machines as mine directly to this alternative install disc as I found it very easy to use after I finally mastered CDBurnerPro (also a really good package despite all my dumb mistakes with it).

I would also suggest as friendly as possible that you do something about the help for those like me that feel stuck.  I wrote to what I thought was an install help team only to get the somewhat unfriendly reply as follows:

"Your mail to 'ubuntu-users' with the subject
    Can 't install Ubuntu
Is being held until the list moderator can review it for approval.
The reason it is being held:
 Post by non-member to a members-only list
Either the message will get posted to the list, or you will receive notification of the moderator's decision."

I had no intention of causing so much trouble!

This closes off my posting on this thread.  Thanks again to Confused and Houston, and I am sorry for the somewhat petulant tone of my previous posts which reflected an unjustified frustration.

---

### Post by houstonbofh on 2007-04-08
I am glad you have the patients to let us help you.  For the record, I **hate** the way the images have been "reorganized" and can not believe they missed the trouble this would cause!

> **Strelz said:**
> I think there is a small principle here.  I very much hope that Ubuntu can be for me and indeed everyone.

**Nothing** is for everyone! :lolflag: I am a big Ubuntu fan, and have it on all my systems but one.  Because on that one, it is not the right tool for the job.  This is not a religion for me.  I am just a craftsman who likes this tool quite a lot.

First, lets get you a better version.  Go to [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) and find a close mirror.  (That is what the other guy did, but he is in Germany...)  I am in the US, and close to easynews, so I wen to [http://mirrors.easynews.com/linux/ubuntu-releases/](http://mirrors.easynews.com/linux/ubuntu-releases/)  This is all the released versions, and the current dev version.  6.06 is Dapper, the older version under long term support.  61.0 is Edgy the current version.  7.04 is Feisty, the version that will be current on April 19th.  It is also listed under name at that mirror.  Let's look at Dapper...  Clicking on 6.01, 0.16.1, or Dapper takes you to the same page, a list of all the versions of Dapper.  The First one is the Live CD.  It is a simple install (if everything goes right) and a nice rescue disk.  I have one of these for each version.  Next is a Mac version.  The 64 bit version only runs on 64 bit CPUs.  However, some things only run on 32 bit OSs, so installing the 32 bit version is often better.  You have a 32 bit CPU.  The Sparc version is for Sun systems.  Next is the 3 server versions, then we get the 3 Alternate Install versions.  These are the command line install CDs.  I also have one of these for each version I have.  (For the record, I have currently running systems with Dapper, Dapper Server, Edgy and Feisty.  That is 7 CD's I keep around.  I only have the Alt-install cd for Dapper Server.)

Now, if you search the forums for "Inspiron 1150," you we see some issues with Video.  You can fix them, but I found Dapper not to have them...  However, the Alt-install CD will get you installed to a point we can work.  If you feel lucky, grab the Feisty Beta alt-install.  If you want to be safe, the Dapper Alt-install.  If you want to try to skip a step upgrading, the Edgy alt-install.  I am running Feisty, but we have already established that I am crazy. :)  Here is the link to an englisg Edgy Alternate Install at easy news in the US. [http://mirrors.easynews.com/linux/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://mirrors.easynews.com/linux/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)

Now before you start, if you want to keep XP, clean it up.  (Grab a copy of "crap cleaner" to find a lot of junk)  Make some space, and defrag the HD.  Make sure that after compressing the partition, you will still have at least %25 free.  You can do more, but it gets **slow** if you try.
Now boot one of the Live CDs that you have.  Run "Gparted" In the System --> Administration section.  This will allow you to shrink the XP partition graphically.  You can also get the latest Gparted on a Live CD of it's own, which may be quicker.  It is also handy for other things, however.

Once you have a nice sized chunk of unpartitioned space, boot the Alt-install CD.  Follow the prompts.  The Partitioning step is the only one to pay attention to.  After you get it all on, it will reboot.  If graphics come up, post back for tweaks.  If they do not, post back for solutions.  As I said, I have one myself, so I **will** get you going.

Good luck.  I will chat again when my family drives me to the calm regions of the computer. :)

---

### Post by pgheric on 2007-04-08
> **houstonbofh said:**
> To both people with issues, Please...  We need more information.

pgheric - What do you mean?  Does it boot?  Does it try to boot and fail?  If so, where?  What kind of system?  What Video card, and how much memory?

Strelz - How much memory in the 1150?  What version of Ubuntu?  There is a odd problem in the 1150 with Video and Edgy.  I installed Dapper on mine with no issues.  The Upgrade to Edgy went fine.  You may want to try that.  Also, if you have less than 512 meg of ram, you may want to use the alt install method.  256 meg or less makes for difficult installs.

:) Hey,

 thanks formthe info but i am booting fro a live cd on a hp machine with a gig og mem and all it does is comemup and show install etc then goes back to my staart up and back to xp, any suggestions will be of great help

thanksd in advance eric

---

### Post by houstonbofh on 2007-04-09
> **pgheric said:**
> :) Hey,

 thanks formthe info but i am booting fro a live cd on a hp machine with a gig og mem and all it does is comemup and show install etc then goes back to my staart up and back to xp, any suggestions will be of great help

thanksd in advance eric
This is unclear.  Do you see the Ubuntu boot menu?  Have you heard the Ubuntu startup music?  Have you seen the Ubuntu Desktop on the live CD?  Can you go into the examples directory and "play stuff?"

---

### Post by pgheric on 2007-08-15
:confused:Hi gang,

Sorry it has taken me so long to post again but i am still having problems running the live cd on this xp machine. Nothing seems to work. I know it's burned correctly, it came from the original source! i set bios to boot from cd and that didn't make any difference. it won't load. Any othe suggestions i am totally frustrated but am not about to give up and of course ms is no help at all, lol, go figure.
HELP!!!!!!!!!!!!!!!!!
eric
:lolflag:

---

### Post by houstonbofh on 2007-08-17
Pop the cd in your system while XP is up.  Now look at the files and tell me what you see.  And since a lot of time has passed, what version are your trying to boot?

---

### Post by flint_ on 2007-10-02
I am also trying to install Dapper Drake 6.06 LTS on a Dell Insprion 1150.

The CD I am using is a known good CD.  The Machine boot to X and the installation process gets as far as the timezone screen and locks.

At the timezone screen the machine thrashes the CD.  This can go on for a half hour but stops.  The machine is frozen.

Can installation take place in character mode?

New info, I seem to be getting it done.  Fingers Crossed....

Regards,

Flint

---

### Post by flint_ on 2007-10-02
Damn,

No sooner than I edit the post, I freeze loading gparted.  CD is thrashing, Mouse frozen, Keyboard unresponsive, No Capslock light, No num lock light.

Power clear is my only option.

Regards,

Flint

---

### Post by houstonbofh on 2007-10-02
Sound like a low memory issue.  How much ram have you got?  And can you try the alt-install?

---

### Post by flint_ on 2007-10-05
Greeting List Lurkers...

The TADA on installation of Ubuntu installation on the dreaded Dell Inspiron 1150 is to use a known good 7.04 Fiesty Faun version of Ubuntu.  This was the secret that allowed it to work and not hang during the installation.

Once over this hump the beastie worked fine.  Note that this installed on a gpartd partition of about 5 G and the machine had a blazing 256M of ram.

Enjoy!

Flint

---

