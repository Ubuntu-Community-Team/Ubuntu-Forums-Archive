---
title: "network file sharing - what have I missed?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-01-23
Hi,

I'm tearing my hair out trying to get a Ubuntu-XP network going.  Here's the problem:

1.  The XP machine sees the shared folders on the Ubuntu machine, and will let me read, write and delete their contents.  So far so good.

2.  The Ubuntu machine can SEE the shared folders on the XP machine... BUT, when I click on them to get at the contents, I get the message: "THE FOLDER CONTENTS COULD NOT BE DISPLAYED.  Sorry, couldn't display all the contents of 'folder-name'"

In other words, XP does a great job of accessing the Ubuntu machine, but it's not working the other way round.

It's frustrating not to be able to read/write to the XP folders - I feel like I'm halfway there, but must have missed part of the process.  I've googled this and found other people with the same problem, but no solutions.  Any advice will be very gratefully received!

---

### Post by TheWizzard on 2007-01-23
> **whitefort said:**
> 
In other words, XP does a great job of accessing the Ubuntu machine, but it's not working the other way round.
in other words, ubuntu does a great job of sharing folders, but it's not working the other way round.

please give us more details, so we can help you. how exactly do you try to acces the xp machine from ubuntu? what are the settings on the xp machine?

---

### Post by Ba66e77 on 2007-01-23
Newb myself here, but I had a similar problem that was resolved when I installed smbfs. 

sudo apt-get install samba smbfs

---

### Post by whitefort on 2007-01-23
> **TheWizzard said:**
> 
please give us more details, so we can help you. how exactly do you try to acces the xp machine from ubuntu? what are the settings on the xp machine?

Thanks.

To access the XP machine from Ubuntu, from the menu I click 'network servers'.  This brings up a window with a little icon called 'Windows network'  I click that, and I get an icon called 'ashtree' (the name of my workgroup).  I click that, and I get icons for both computers.  I click the XP computer, and icons appear for all the shared files on that machine.

And when I click one of those, I get the message that the contents can't be displayed.

As far as settings on the XP machine are concerned, all I've done was to set the folders up for sharing on the network.  This was enough for other windows machines, but it seems I need to do something more for it to work in Ubuntu, and I don't know what.


When I use the xp machine to access the Ubuntu machine, I have to type in my Ubuntu name and password - I've been wondering if I have to do something similar to get into the XP machine from Ubuntu, but ubuntu never asks me for any password, and in any case, I don't have any passwords set up on the XP machine.

I'll be really grateful for any help.

---

### Post by whitefort on 2007-01-23
Thanks, BA66e77.  According to Synaptic, I do have smbfs installed.  Should it work automatically, or do I have to do something to turn it on?

Don't apologise for being a newb!  I think what I need most is help from a newb who's got it working, and hasn't forgotten how difficult this all is for newbs!!

Thanks.

---

### Post by teitunge on 2007-01-23
I have the exact same problem, but I found a temporary solution for it.
When you browse the network, refresh the window until the icon appear. This is first to access that certain workgroup, and then to access the windows computer.

I do not know if this made any sense, but I will be watching this thread if it didnt work :)

---

### Post by whitefort on 2007-01-23
> **teitunge said:**
> 
When you browse the network, refresh the window until the icon appear. This is first to access that certain workgroup, and then to access the windows computer.:)

Sorry, I don't quite understand...  I already get the icons for the windows network, the workgroup, and the two computers in the workgroup.  When I click the icon for the windows machine, I get all the icons for the shared folders - but when I click on those I get the message that the contents can't be displayed.  if I keep hitting reload to refresh the window, I just keep getting the same message, that they can't be displayed.

Have I misunderstood you, or is it just that we have different problems?  Thanks for trying to help!

---

### Post by teitunge on 2007-01-23
Ah, no, you actually got me quite right, and I am suprised since my english could be very confusing ;)

Then your problem is quite weird and I have no more ideas. Sorry :/

---

### Post by Buck2348 on 2007-01-23
I know the problem teitunge was addressing, and I don't believe it's the same problem you have.  But I'll post the fix for it here anyway--maybe it will help someone else.  This is for Edgy 6.10.  Is that the version you're using?  Edit the file smb-module.conf
```
gksudo gedit /etc/gnome-vfs-2.0/modules/smb-module.conf
```
change the line

Code:  smb: [daemon] libsmb     [COLOR="Blue"]to[/COLOR]
Code:  smb: libsmb

Source:  [http://www.ubuntuforums.org/showthread.php?p=2004713#post2004713](http://www.ubuntuforums.org/showthread.php?p=2004713#post2004713)

This fixes a problem which was peculiar to Edgy.  Sorry, Whitefort, that I can't come up with an easy fix for you, but either someone else will or you'll find the answer somewhere in the forums.  I'm going to try to find something more now.

Buck

---

### Post by chipmonk010 on 2007-01-23
try this

goto system > administration > networking >general tab

make sure the domain is the same as your windows machines workgroup

also make sure that your xp shares have the "allow others to change my files" box checked

---

### Post by Buck2348 on 2007-01-23
What about the Windows firewall?  That has been my problem more than once when trying to open a network share.  Do you know how to configure it?
Also, can you ping the windows machine from ubuntu?

Buck

---

### Post by whitefort on 2007-01-24
Thanks, everyone - I continue to be ***very ***grateful for every suggestion, but as yet I still can't get Ubuntu to open the folders on the Windows machine.

**Chipmunk010**, no, everything seems OK in those settings. The Domain is the same as the windows workgroup, and the files are set for complete sharing - in fact, other windows machines can access them without problems.

**Buck 2348,**  Yes I can ping the windows machine, and Ubuntu can actually find and see the shared folders - it just refuses to display their contents.  As for the firewall, I'm using ZoneAlarm, not the windows firewall, but that doesn't seem to be the problem, because I've even tried turning the firewall off altogether, and it doesn't help.

I was hoping I'd just missed something obvious and stupidly simple, but it's beginning to look a lot worse than that.  I'm getting a sinking feeling that this is something I'm never going to be able to fix, which will mean going back to Windows... I'm depressed!  :(

---

### Post by freebeer on 2007-01-24
Some thoughts on the issues (but with no definitive answer) :(

Are you using WinXP Home Edition?  It's designed to not play nice with networking.  I know, for instance, that you cannot get Home Edition to join a domain.  This might be a contributing factor.

ZoneAlarm has been known to remain persistent even when you disable it.  Its rules/blocking can remain in effect even when uninstalled.  

Some motherboards have a built-in firewall in the BIOS.  You might want to check yours and disable it, if it exists.

---

### Post by whitefort on 2007-01-24
hi, Freebeer.

Yes I'm using XP Home on the Windows machine, but Ubuntu *is* reading it as part of the domain.  Ubuntu can see the domain, see the XP machine as part of it, and can see the indivudual shared folders on the XP machine - it just won't let me into them!

From the other side, XP sees the Ubuntu shared folders and gives me complete access to them. The network is 100% fine with other windows machines - it's just that Ubuntu can't get into the windows folders.

If you're saying that an Ubuntu/XP Home link will never work, that will be a REAL bummer, and will mean for sure that I have to switch back to Windows.  I'm hoping I misunderstood you!

---

### Post by tbraun on 2007-01-24
Hello!

> **whitefort said:**
> If you're saying that an Ubuntu/XP Home link will never work, that will be a REAL bummer, and will mean for sure that I have to switch back to Windows.  I'm hoping I misunderstood you!

Oh dear, no! Everything else, just not switching back to Windows! :) 

For whatever it's worth: I had no problem at all accessing, creating and modifying files in a shared Windows folder from my Ubuntu machine. Just like in your case, I simply declared a folder in Windows as 'shared', and Ubuntu recognized the Windows network, and found the folder ... and that's all there is to it. So, it IS possible. Unfortunately, I also don't know what could be wrong in your particular case. And it is XP Pro. However, I can't imagine that Home or Pro should be the problem, since you said that other Windows machines could access it all easily.

One question: Is it possible for you to create new files in that Windows folder from your Ubuntu box?

Tom

---

### Post by whitefort on 2007-01-24
> **tbraun said:**
> Hello!
One question: Is it possible for you to create new files in that Windows folder from your Ubuntu box?
Tom

Hi, Tbrawn, and thanks.  I hadn't thought of trying that - it didn't work.  I get the message 'ERROR CREATING NEW FOLDER:  Error "operation not permitted" when creating new folder.'

If I actually click into one of the windows shares and try to create the folder there, I get an 'invalid parameter' message.

As a really annoying and unwieldy workaround for all this, I can transfer files from Ubuntu to Windows by first putting them in a shared folder on my Ubuntu desktop, then walking to the other room and using Windows to take them out of the Ubuntu desktop folder - but it's a bit of a pain to do it that way.

Also, I've not been able to get the windows printer to print from the Ubuntu machine, and I suspect that it's the same thing causing the problem - I'm hoping that if I can sort out the fileshare problem, it will solve the printer problem too.

It's kinda as if Ubuntu thinks I don't have the full permission to get at those windows folders, isn't it?  I'm wondering if that's the problem in some way, but I don't know enough to test the theory.

---

### Post by Buck2348 on 2007-01-24
whitefort, I wish I knew enough to help.  I'm going to dig a little more with google.  One thing that makes my access to Windows boxes faster and more reliable:  I've set a static ip through System -> Administration -> Networking, Connections -> (select your connection) Properties.  I doubt this relates to your problem but it wouldn't hurt to try.  Also have you considered trying to mount the Windows shares in the filesystem?  Again, that shouldn't help if you can't access them, but who knows?

Don't give up--we just need one of the experts to find your thread and provide the solution.

Buck

---

### Post by whitefort on 2007-01-24
Thanks Buck.

I've been googling for the past week (and again for the past few hours)  I keep finding people using various linux distros who have the same problem, but I haven't yet found any solutions - admittedly this might be because I don't know enough PC/Linux terminology to really understand some of the discussions.

*I've set a static ip through System -> Administration -> Networking, Connections -> (select your connection) Properties.*

I've already done this, giving an ip to the Ubuntu machine, and adding the windows ip as the 'gateway' (which I hope was the right thing to do!)

I did try mounting them at one stage, working through instructions I found on a webpage - but the mounted files just gave the same error messages. 

I've also come across threads about a bug in gnome which causes a very similar problem, where the workaround was to type the address into nautilus instead of clicking - but that didn't work either.

I've just been looking at one suggested solution which involves going into the Windows registry and turning off some sort of security settings.  I might try that, but I'm nervous about it for several reasons.

---

### Post by Buck2348 on 2007-01-24
Do you use a router?  My router's ip address is the 'gateway'.  I don't think giving the Windows machine's address would be right, unless that is the one machine on the network connected directly to the Internet.  Don't really know--I've never really understood these things, just tinker till they work.  Also have you tried Places -> Connect to Server instead of -> Network Servers?

---

### Post by TheWizzard on 2007-01-24
try mounting the shared folder from the command line. something like this: 
```
sudo mount -t cifs -o credentials=/home/username/.smbpasswd,noperm //xpmachine/home /mnt/xpmachine
```
you can set a name for the remote pc in /etc/hosts

---

### Post by Buck2348 on 2007-01-24
I think he's using samba/smbfs rather than cifs.

---

### Post by Buck2348 on 2007-01-24
I'm dubious anything this simple will fix the problem but it won't hurt to try.  The quotee is telling how he got into Windows shares:
> Here is what I finally found:
- right click on your Computer folder on desktop, choose Browse Folder.
- or click on Browse File system in the gnome menu
- you are going to have to click on Go at the top and go to Computer, if
you right clicked on Computer on your desktop you will already be there.
- you will now see a traditional nautilus window that you can actually
type your location into.
- double click on Network
- double click on your Windows Network
- double click on your work group
- you should now see the available computer shares
- if you double click on the computer you want you will get the error
that you mentioned in this e-mail.
- in location type smb://computer name/share folder name/
- you should get the password dialogue box now.  I got it.
- I think there is a bug in nautilus where you can only access a share
if you type in the full path of the share folder you need access to.

If you don't have a location bar to type into in the Nautilus window, click on the pad&pencil icon at the left end of the location button bar immediately above the space with folder/file icons.

For some reason I don't have "Network Servers" in "Computer" so I just used the icon on the desktop.

---

### Post by chipmonk010 on 2007-01-24
whitefort:

is the username and password on your xp machine the same or different from your username on ubuntu?

I have found that sometimes if they ARE the same things work easier(im not suggesting you do this) but perhap it has something to do with windows not recagnizing the ubuntu machine as a trusted host

im gonna go run some tests and see if i can reproduce something, the only other thing i can think of is a bug perhaps your install got corrupted options:

reinstall samba and nautilus
reinstall ubuntu

oh! try booting to the live cd and see if it works!

---

### Post by whitefort on 2007-01-25
I just wanted to say another quick "Thank You" to you guys for not giving up on me yet.

I'm starting to get all sorts of 'I told you so' crap from my windows friends, and it's hard not to feel that they have a point.  If I took Linux off this machine and reinstalled Windows, I could have file and printer sharing working again in a few minutes.  Surely it really shouldn't be this hard to get something so basic to work?  I thought I was just an isolated case, but googling has shown me that this is seems to be quite a common problem.

Anyway, enough complaining.  Today I'm going to work through your most recent suggestions,  and even (dammit!) try a complete reinstall of Ubuntu if all else fails - I've messed with so many config files etc in the past week that it's possible I've screwed something up and not put it back the way it was.

Just a thought on that subject.  If/when I reinstall, should I switch to Edgy? - I'm on Dapper at present.

Also, I read something about how it makes future upgrades easier if you put your home directory in a separate partition.  Is this something I should do, or should I leave it WELL alone until I understand more about this stuff...  My instinct is telling me to do the latter!

Thanks again.

---

### Post by Palmstroem on 2007-01-25
Hi Buck,

your solution is great! Thanks a lot! It actually makes life **much** easier for those who really need a working connection to Windoze computers.

Could you eventually forward your conf modification to the distro people for the next upgrade?

---

### Post by erlyrisa on 2007-01-25
I had similar difficulties.... and still do to this day (after a year of Ubuntu)

-thing is I don't really care as long as Ubuntu can access the windows shares I was happy - in the end I thought - geez I'm not really roaming network folders on XP anyway what's 1 linux machone out of the loop - at least no-one else can get to it.

-shame ur problem is the other way around.


Some things I have learnt though...

Konqueror is somewhat better then Nautilus(gnome fbrowser) at attempting to locate network folders - dunno why its just my experience - it's slower but more reliable (or it could be that when I look via nautilus and it didn't work I give up and start konq and by then the computer being polled has woken from standby)

Install the smbfs and bring all your documents and such into one location. -you'll be able to work on the share like a mounted harddrive - much neater.

Don't stuff around with IP addresses - it's easier to leave it dynamic, you'll find that the computer that you mount an smbfs will probably always have the same IP anyway. -but if you can have some computers permanent and still talking to your router and still have Windows networking working tha'ts great too - but you need tobe a bit savy with networking and such to get it going - I still don't understand networking -and I got five comps on one router/switch.

Look at your Microsoft computers settings - sometimes U may have played around with them too.

Funny how opposite problems attract - maybe you could pass on your settings , and I pass on mine to yours then we'd have a network where both oses workied in concert!:D

---

### Post by chipmonk010 on 2007-01-25
just an update:

I messed around with xp home and ubuntu but could not reproduce the errors you are getting. having the same usernames does not matter for me nor should they matter for you. 

Im using edgy but have had no problems with hoary breezy or dapper

im starting to think its possible that its a driver problem?

for reference perposes would everyone whose having this type of issue post the output of 

lspci

perhaps there is a common NIC or NIC chipset involved?

again i think best thing to do next is boot form the livecd and or try a fresh install

as for edgy? down load it and run the edgy livecd too see if it works

then even try installing it, maybe your dapper cd was corrupted or something(never know)


hopefully we'll get some results, sry for your troubles

---

### Post by whitefort on 2007-01-25
Thanks again everyone.

As requested, here's what I get when I type in lspci:
-------------------------------------------------------------------------
john@BIGROOM:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)
0000:02:09.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:02:0b.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
0000:02:0d.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
----------------------------------------------------------------------------------------------

It's been a nightmare day with this problem - following some other 'how to' pages on the net brought me to a situation where I lost even the half-way connection I already had (and screwed up the windows machine to a point where I had to do a system restore to get things working again).

Anyway, now I'm back (I think) to where I was before the nightmare.  My next step will be to try running from the CD.

One quick question - my situation is complicated now because my wife has a million emails and addresses on the Ubuntu machine. Is there any way to save all her Thunderbird contents and settings, so I can replace them after a clean install?  I've done some browsing around, but I can't see the thunderbird files anywhere.

I'm going to keep slogging away at this tonight, but I'm not doing any more 3AM bedtimes! There have been two of those already this week, and it's a really bad idea!

---

### Post by chipmonk010 on 2007-01-25
just goto <wifes username>'s home folder in the file manager press Ctrl h and copy .thunderbird to a disk or thumb drive etc. 

after reinstalling thunderbird simply copy and paste the old .thunderbird folder in and overwrite the existing one

---

### Post by whitefort on 2007-01-25
The latest news...

Running the live CD doesn't fix the problem.  I can see the windows shares, but when I try to get into them I get the same old message that the contents can't be displayed.

This makes me disinclined to do a complete reinstall, as I don't think that would fix things either.  I'm starting to feel that the problem is at the Windows end, but I can't see how, as things would work perfectly if this machine was running windows instead of Ubuntu.

I just don't know what else to try - I'm starting to think that I'm never going to solve this one.  I HATE the thought of going back to Windows, so I guess it's time to make some decisions.

I can still transfer files back and forward by doing it from the XP machine, since it sees the Linux shares with no problem.  It's a nuisance, but it's workable.

It's a bigger nuisance not being able to use the network printer - at present I have to save stuff to a disk or email it to myself, then print it on the XP machine.  This one is more of a hassle, but I *suppose* I could buy a cheap printer and put it on the Ubuntu machine....

It's all a bit unsatisfactory, and to be honest I'm a lot less enthusiastic about Linux than I was a week ago, but I'd still like to try to stick with it.

Would it be fair to say that Linux is an OS for people who like to get under the hood and tinker around, more so than for people who just want a working PC so they can use the apps?  I'm definitely getting that impression.

Oh well...  Thanks again everyone.  I'm sure I'll have lots more questions before long!

---

### Post by chipmonk010 on 2007-01-25
whitefort:

ill search around and see if a cant find a new/better driver for you to try for your NIC and if i do ill post some instructions on how to install it. u got me hooked on this one! i dont want to let ubuntu fail for the average user! As you have basically stated you are to the point where theirs not point in persuing it, i agree, but i'd like to see if i can find something so ill keep you posted

---

### Post by crispingatiesa on 2007-01-25
Did you try this?

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by Buck2348 on 2007-01-25
Whitefort:

I admire your patience and am really sorry you're having so much trouble.  I'm going to keep looking around too.

Are you using a router?  We talked about the static ip a day or two ago.  I assume you've also tried automatic configuration (DHCP)?

Buck

---

### Post by Buck2348 on 2007-01-25
> **Palmstroem said:**
> your solution is great! Thanks a lot! It actually makes life **much** easier for those who really need a working connection to Windoze computers.

Could you eventually forward your conf modification to the distro people for the next upgrade?
This is a confirmed bug that was fixed for Gnome and Nautilus, and for Edgy the status is "fix committed."  It also prevented streaming audio from Windows.  [https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277](https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277)

 I don't know where to send the simple fix I posted to try to get it incorporated . . .?

Buck

---

### Post by freebeer on 2007-01-25
Maybe I'm jumping in here a little late, but I'm almost certain that it's an XP Home issue that you're experiencing.  A little rundown on my system here:

1 Linux box, running Samba.  1 dual-boot Windows2000 with ubuntu.  (both ubuntu versions are 6.06).  1 WinXP Home.

I've shared a folder on each machine.  The linux box can see the Linux share and the Win2k share no problem.  Full browse, full read/write.  But it cannot see the XP home share.

The Win2k machine can see the Linux share, but not the XPHome share.

The XPHome machine can see both the Linux and Win2k share.  

(by "see" I mean can locate the share and browse the directory in the GUI)

I can create a document in WinXP Home, save it on the Linux box, have Linux or Win2k open, edit, and save the file and WinXP can read back that file, edit and save it again.  All is good on that front.  I open the file in Linux and save (or copy) it to the share on the Win2k box.  Neither Win2k nor Linux can do that to the XP Home share.

The pattern I see is that WinXP is just being brain-dead (deliberately, I'm told) when it comes to playing nice on networks.  It just does not want to (at least) broadcast its presence on the network.

I don't have a copy of XP Pro otherwise I'd install it on a machine and complete the test to prove that it's an XP **Home Edition** issue.

---

### Post by Buck2348 on 2007-01-25
This all seems strange--I have one Ubuntu/WinXP Home dual boot, and two WinXP Home only boxes, and they are all working on the network with an older D-Link wireless router hooked to the DSL modem and the Ubuntu box.  I've installed Ubuntu four times on this machine and as far as I can recall it could access the Windows shares right out of the box--I had to work a little to make it go the other way.  I hope you folks can sort this out--I'd like to know what's going on.

Buck

---

### Post by whitefort on 2007-01-26
Guys, I know I keep saying this, but thanks for your continuing efforts to help. It's appreciated, and I'm amazed how generous you are with your time.  I just hope I can eventually learn enough about Ubuntu to be able to return the favour to other newbies...

A quick summary...  Ubuntu can still find the Windows workgroup, the XP computer, and the shared XP folders, but any attempt to get into them produces the message: ***THE FOLDER CONTENTS COULD NOT BE DISPLAYED. Sorry, couldn't display all the contents of "SharedDocs".***

From the other side, Windows XP ***can*** see all the shared folders on the Ubuntu machine, and has full access to them.

The problem isn't unique to Ubuntu - a Google on the error message shows that it's common across a wide range of Linux types (distros?).  I've tried just about every fix I can find, including those suggested above, but with no success.

I suspect the problem IS at the Windows end, and have confirmed that when it comes to networking, XP Home *is* different from XP pro.  A few of the 'fixes' I found suggested turning off 'simple file sharing' in XP as part of the procedure.  This can be done in XP Pro, but NOT in XP home - that's official, from Microsoft. It's one of the features they charge extra for.

It's still a puzzle. I know that if I removed Ubuntu and put Windows back on this machine, I WOULD have a working network and would be able to use the remote printer.  Also, Ubuntu<--->XP Home does work for some people, doesn't it?

Oh well...  I'm sticking to my aim of ***eventual*** liberation from Windows. I'm certainly never going to pay for another MS operating system.  But in the meantime I'm going to still need one hi-spec windows machine, as there's no viable Linux equivalent for some of the essential windows apps I use on a daily basis.  Otherwise I would seriously consider dumping windows on ***both*** machines and seeing if I could get a proper Ubuntu network running.  

I've given up on trying to fix this particular problem - or at least, I've given up spending all my waking hours on it!  I'll still be paying attention to all 'network' threads in case someone finds a fix, and if anyone else has anything to suggest here, I'll certainly give it a shot!

Thanks again!

---

### Post by TheWizzard on 2007-01-26
> **freebeer said:**
> Maybe I'm jumping in here a little late, but I'm almost certain that it's an XP Home issue that you're experiencing.  A little rundown on my system here:

1 Linux box, running Samba.  1 dual-boot Windows2000 with ubuntu.  (both ubuntu versions are 6.06).  1 WinXP Home.

I've shared a folder on each machine.  The linux box can see the Linux share and the Win2k share no problem.  Full browse, full read/write.  But it cannot see the XP home share.

The Win2k machine can see the Linux share, but not the XPHome share.

The XPHome machine can see both the Linux and Win2k share.  

(by "see" I mean can locate the share and browse the directory in the GUI)

I can create a document in WinXP Home, save it on the Linux box, have Linux or Win2k open, edit, and save the file and WinXP can read back that file, edit and save it again.  All is good on that front.  I open the file in Linux and save (or copy) it to the share on the Win2k box.  Neither Win2k nor Linux can do that to the XP Home share.

The pattern I see is that WinXP is just being brain-dead (deliberately, I'm told) when it comes to playing nice on networks.  It just does not want to (at least) broadcast its presence on the network.

I don't have a copy of XP Pro otherwise I'd install it on a machine and complete the test to prove that it's an XP **Home Edition** issue.

that's what i said from the beginning. using less words though. 
for some reasons lots of people star blaming linux by default. in my experience miscommunications between linux and windows are virtually always windows issues. 
linux was designed for networking; windows was designed for stand-alone.

---

### Post by HereInOz on 2007-01-26
Just a simple one, and it may have been covered previously and I missed it, but do you actually have a password set up on your Windows XP machine?  I know that XP is quite happy to exist without a password, but I am not sure about Ubuntu accessing Windows shares without a password.

Also, be aware that you are not able to write to an NTFS share.  You can copy from it and copy to it, but at this stage, unless you install some fairly experimental software, whose name eludes me, you cannot write to NTFS from Ubuntu.

---

### Post by TheWizzard on 2007-01-26
> **HereInOz said:**
> Also, be aware that you are not able to write to an NTFS share.  You can copy from it and copy to it, but at this stage, unless you install some fairly experimental software, whose name eludes me, you cannot write to NTFS from Ubuntu.
ntfs write is beta, but it is pretty good/save as far as i know. i mean, half of the open source stuff is in beta ...

check
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Buck2348 on 2007-01-26
> **HereInOz said:**
> Just a simple one, and it may have been covered previously and I missed it, but do you actually have a password set up on your Windows XP machine?  I know that XP is quite happy to exist without a password, but I am not sure about Ubuntu accessing Windows shares without a password.

Also, be aware that you are not able to write to an NTFS share.  You can copy from it and copy to it, but at this stage, unless you install some fairly experimental software, whose name eludes me, you cannot write to NTFS from Ubuntu.
I don't believe the ntfs file system problem applies here.  ntfs-3g is the software I use to write to ntfs partitions.  In /etc/fstab I use ntfs-3g as the file system type.  But for the Windows shares it's smbfs, not ntfs.  It must be samba that does the direct writing to the shares.  At any rate, the problem here is the shares cannot be read OR written to.

I access shares on Windows machines which have no password set up.  I had to make an adjustment to /etc/samba/smb.conf to be able to go the other way without a password.

Buck

---

### Post by tanman on 2007-01-26
I have been watching this thread with much interest also. I am fairly new to Linux also, but have not had this problem. I have a desktop with Edgy, laptop with win home, and a desktop with Media Center home all on the same network. It really does seem to come down to a permission thing on the Windows computer. Though it is strange that another Windows computer can access the same file. Since I am fairly new to Linux I probably can not be a lot of help especially since I never had any problems with my networking. I do hope you can solve it though for the more I use Ubuntu the more I realize how great of a operating system
it is. I will try to play with my network a bit on the weekend and see if I can get that error message.

---

### Post by chipmonk010 on 2007-01-26
well drivers are not the issue. The card you have is one of the most well supported NICs under linux.

I agree with others who think this is an XP problem not an ubuntu problem. Ive heard stories of xp home and xp pro not playing well togather hell xp and xp sometimes dont play well together! but im not experiencing any problems here with ubuntu dapper and edgy and xp pro and home. 

things to try tho im sure u probably have already:

make sure xp is up to date

disable all firewalls virus including windows firewall protection EVERYTHING and try it

create a folder on you desktop and share it allowing others to change your files
(sometimes creating a new one works while the old one wont....this is windows after all)

sry for your troubles whitefort, hopefully some one will find something

couple Qs:

how many xp machines? just one or more experiencing the same problem?

was xp installed by you or did it come from factory installed?

who makes the machines aka dell compaq etc?


sry for your troubles whitefort, hopefully some one will find something!

*************************************************************************************************************************

heres a run down of things we have ruled out for reference: (input welcome ill probly miss something)

ubuntu software: ruled out
problem persists with nautilus, konquer, and linneighborhood

config samba seems to be configured correctly workgroups etc
*whitefort perhaps you should post your config file just incase*
gedit /etc/samba/smb.conf

ubuntu hardware:
one of most supported cards out there seems to work fine

windows machine:
shares are correctly shared and can be viewed by other xp computers just fine

---

### Post by tanman on 2007-01-26
I have re-read some of the posts is this thread and have to agree that the problem could be Zone Alarm. I realize you said you turned it off, but like someone stated this is sometimes not enough for Zone Alarm does not want to be turned off. I do realize you can access the files from another XP computer, but the fact that you are trying to access it from a non windows computer could be it. It has been my experience that ALL security suites are the root of all evil and do nothing but add problems to a already unstable OS.  As suggested before I would uninstall Zone Alarm and then go in and try to clean out any traces of it. Either unistall from the disk or see if Zone Alarm has a uninstaller on the site. I found using the Windows Add/Remove can be useless when trying to get rid of such a program. This is why I am going away from windows for to protect it you have to add programs that hinder the performance of 
the OS. This is just a suggestion that hopefully will help.

---

### Post by salvo on 2007-01-26
> **whitefort said:**
> It's kinda as if Ubuntu thinks I don't have the full permission to get at those windows folders, isn't it?  I'm wondering if that's the problem in some way, but I don't know enough to test the theory.

What is the Share Permissions of your shared windows folder, whitefort?

---

### Post by PaulFXH on 2007-01-26
Hi whitefort

We have two computers:
1. Dell Dimension E521 with OS Windows XP (MCE)
2. Dell Dimension 4550, multiboot, current OS Ubuntu 6.10

When the multiboot machine was running WinXP (Home), we set up a Windows-to-Windows home network which worked fine.
When this box switched to Ubuntu, I used this guide to set  up Samba [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

While this worked perfectly sharing Ubuntu files over to the WinXP machine, and allowing the Windows box to print on the Ubuntu machine's printer,  I had very much the same problems as you do when trying to view shared Window folders in Ubuntu (Folder cannot be displayed........etc.).

Then I followed the points (to the letter) in this very short guide [http://jason.379.com/node/32](http://jason.379.com/node/32) and this rectified everything.

Worth a try
Paul

---

### Post by brimondyl on 2007-01-26
> **whitefort said:**
> Hi,

I'm tearing my hair out trying to get a Ubuntu-XP network going.  Here's the problem:

1.  The XP machine sees the shared folders on the Ubuntu machine, and will let me read, write and delete their contents.  So far so good.

2.  The Ubuntu machine can SEE the shared folders on the XP machine... BUT, when I click on them to get at the contents, I get the message: "THE FOLDER CONTENTS COULD NOT BE DISPLAYED.  Sorry, couldn't display all the contents of 'folder-name'"

In other words, XP does a great job of accessing the Ubuntu machine, but it's not working the other way round.

It's frustrating not to be able to read/write to the XP folders - I feel like I'm halfway there, but must have missed part of the process.  I've googled this and found other people with the same problem, but no solutions.  Any advice will be very gratefully received!

I believe with xp if you use your xp name and password, it will let you
did awhile ago with to UBUNTU machines and one xp (if I remember correctly it was that easy

---

### Post by MouseClick on 2007-04-04
Follow this link [https://launchpad.net/bugs/34594](https://launchpad.net/bugs/34594). You may need to copy these folders to local drive(for example desk top) to be able to access them

---

