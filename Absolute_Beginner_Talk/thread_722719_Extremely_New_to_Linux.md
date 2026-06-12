---
title: "Extremely New to Linux"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Zubatron on 2008-03-12
So I finally did it I made the move to Linux. I completely reformatted my hard drive and got rid of windows (mainly because I was sick of all the malware/viruses/spyware. I was orignally just gonna reload Windows XP but I decided to try something different)

So I got Ubuntu. Basically I have a few questions, hopefully relatively easy to anwser.

1. I partitioned part of my hard drive cause it had important files I wanted to keep. Mainly photos, videos word documents etc...The partitioned drive shows up on my desktop and I was wondering if there was a way to have that hidden or anything like that.

2. When I was avidly using Windows XP on this machine. Oh by the way this is a laptop. The specs off the top of my head is: 1GB of ram, dual processor (dont know speed) and can't remember the rest exactly. But as I was saying, when I was running Win XP even with general use I noticed my laptop getting warm then sometimes extremely hot. Though I've only been running Ubuntu for about a day now I've noticed my laptop hasn't been warming up as usual. It gets warm but not very hot like it used to. Is this normal? Or something I should be worried about?

3. Will creating another user on Ubuntu slow down the system? As I'm only really used to Win XP I always noticed that when creating multiple users it slowed the OS down. Does this hold true for Ubuntu?

4. This may sound stupid but I cannot find it for the life of me, how do you change the home page on Firefox? I know it was under Tools on the Windows version of Firefox but I cannot find it on this version i'm using version 1.5.0.13 if that helps.

Well that's about it. Thanks for the help and I hope to be more active on here!

---

### Post by gpilkay on 2008-03-12
You can probably un-mount the partition (just right-click, then hit 'unmount volume' and see if ti works.  You can re-mount it by finding it in the places menu, under 'computer' in mine.

Not sure about the heat.  Sometimes Ubuntu has trouble with the fans, which makes it WORSE, but it could just be that you are not taxing the hardware as heavily.  Linux doesn't use as many resources.

Usually another user does nothing bad to it, as Linux was intended to BE a multi-user system from the ground up.  Hence the whole 'sudo' thing, when you use it you are actually functioning as a 'super user' who can modify the system.  Normal users (your usual log-in) can't do tha and as such, in theory have a harder tiem messing things up.  In rality, of course, people tend to  enter their sudo password for everything, btu that's human error, you can't fix that.


That's...a VERY old version of Firefox.  What Ubuntu version are you using?  The most recent has the recent Firefox as well, 2.0.0.12.

---

### Post by InfinityCircuit on 2008-03-12
1. The storage drive is on your desktop because you have your computer set up to mount it.  This makes it easy for you to access your documents.  You will notice that the drive is also present in the Places menu at the top of your screen.  It probably isn't worth hte trouble to remove it.

2. Your laptop doesn't warm up because the powernow daemon is doing an efficient job of throttling your cpu speed.  This is nothing to worry about.

3. You can add users and nothing will slow down, although logging in as multiple users at once will cause speed decreases.

4. Go to Edit -> Preferences.  I have no idea why it is different in the Linux and Windows versions but this is a known issue.  If you want to change this you can install the "Menu Editor" firefox extension.

---

### Post by Nepherte on 2008-03-12
1. If you want to hide your volumes on your desktop, press alt+F2 and run gconf-editor. Navigate to apps > nautilus > desktop and uncheck "volumes_visible". Your hard disk partitions will still be accessible through nautilus (a file explorer similar to windows explorer).

3. Creating new users should definitely not slow down your Ubuntu.

4. I work with Firefox 2.0.12 but if I recall correctly it should be more or less the same: in Firefox go to edit > preferences and choose the "general" tab. There's a field called start page or something. Fill in the site you want.

---

### Post by Zubatron on 2008-03-12
oh whoops didn't mention that. I'm currently using Ubuntu 6.06. I saw 7.04 is out. Should I upgrade it?

---

### Post by Nepherte on 2008-03-12
7.10 is already out and soon 8.04 will be (april).

---

### Post by Zubatron on 2008-03-12
Yea I just saw that, as I type this I am downloading 7.10 right now. By the way I love having 4 desktops at once.

---

### Post by Daveski on 2008-03-12
> **Zubatron said:**
> 
2. When I was avidly using Windows XP on this machine. Oh by the way this is a laptop. The specs off the top of my head is: 1GB of ram, dual processor (dont know speed) and can't remember the rest exactly. But as I was saying, when I was running Win XP even with general use I noticed my laptop getting warm then sometimes extremely hot. Though I've only been running Ubuntu for about a day now I've noticed my laptop hasn't been warming up as usual. It gets warm but not very hot like it used to. Is this normal? Or something I should be worried about?

With a Linux machine there is virtually no background tasks running that aren't important, and they are all well written to be 'nice' to the rest of the system. The upshot of this is that when you are not doing much on your machine it is pretty idle and so the power cosumed, and therefore heat dissipated by the CPU, is minimal.

I have found that most Windows machines have loads of background stuff running which ramps up the CPU usage (and so heat). For example, Quicktime, RealPlayer, Acrobat Reader etc all seem to load 'background tasks' presumably to do things such as look for updates etc. Digital camera or scanner software always seem to run tasks that constantly check newly inserted media for pictures etc. Then there will be your antivirus and antimalware programs that are running all the time, and if you *are* infected with malware, spyware etc. that too will be running stuff on the machine. This is why I think Windows starts to slow down the longer it is installed so that most machines after a year or so of use are trudging along like a donkey with a fully ladened back bulging with unnecessary tasks. A quick reinstall (or OS switch) will breath life into an old Windows machine - but be warned, with Windows it will start to 'fur up' again.

---

