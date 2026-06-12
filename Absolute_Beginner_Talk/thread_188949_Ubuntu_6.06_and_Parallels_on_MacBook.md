---
title: "Ubuntu 6.06 and Parallels on MacBook"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by insha on 2006-06-04
Hi all,

My curiosity finally got the best of me and I downloaded Ubuntu 6.06 in hopes of installing it on my MacBook as a guest OS using Parallels Desktop (RC2). The installation went smoothly; but the only thing that is not working is the networking and I can't seem to change the resolution from 1024x768 to anything else.

The following is the screen cap of the configuration screen for the Parallels Desktop:
[IMG]http://coldstorage.macbonsai.com/public/ubuntu-config-pd.png[/IMG]

Any help will be greatly appreciated.

Cheers.

---

### Post by joshrobinson on 2006-06-04
it should work since its briged networking.. have you went to system > administration > networking and enabled and configured your network adapter in there?

you can also try this im terminal

```
sudo dhclient
```

then try a website or whatever to see if it works

for the resolution you might have to edit your xorg.conf and add the resolution you want

```
sudo gedit /etc/X11/xorg.conf
```

when you get to the section that says 24bit depth and the other resolutions, try to add yours in there.. like "1024x768" ahead of the others in the list

---

### Post by insha on 2006-06-04
[QUOTE=joshrobinson]it should work since its briged networking.. have you went to system > administration > networking and enabled and configured your network adapter in there?

you can also try this im terminal

```
sudo dhclient
```

then try a website or whatever to see if it works[/QUOTE]

I should have mentioned that I am a total n00b when it comes to Linux.

That aside, I did check the system>administration>networking and it was enabled; but I'm not sure what you mean by "configured you network adapter in there".

The following is the screen cap of the Network Settings from ubuntu:
[IMG]http://coldstorage.macbonsai.com/public/ubuntu-network.png[/IMG]
[IMG]http://coldstorage.macbonsai.com/public/ubuntu-network-properties.png[/IMG]

And the following is the output from running the ```
sudo dhclient
```
[IMG]http://coldstorage.macbonsai.com/public/ubuntu-dhclient.png[/IMG]

As for the resolution; thank you very much. That did the trick.

Cheers.

---

### Post by joshrobinson on 2006-06-04
everything looks fine in your network settings.. thats what i meant by saying configure it.. is to make sure its active, and dhcp is set

on the bottom of the network settings window there is a "Default gateway" option, did you try selecting your network card in that drop down list? select eth0

if it still doesnt work it has to be something on your mac parallel's end.. ive never really used a mac, so i cant really help to much there

is there any other settings for the internet besides bridged connection?
or maybe you have to set a static IP number on ubuntu because parallel isnt giving it an ip via dhcp

and your welcome on the resolution part :-D at least you got that working so far

---

### Post by spaceballl on 2006-06-06
My HD is full, but I will be doing a parallels install as soon as my new HD comes!

---

### Post by Tu13erhead on 2006-06-06
I'm having the same issue with networking.  Anyone found out how to fix it?

---

### Post by dadzilla on 2006-06-07
I am having precisely the same problem. Parallels provides these virtual ethernet adapter settings:
Type: Realtek 8029(AS)
MAC Address: 008E94FABDBB

---

### Post by youbuntoo on 2006-06-08
every time I've had a Parallels issue I've been able to solve it using the Parallels Forum at [http://forum.parallels.com](http://forum.parallels.com)   Check it out, numerous Parallels users giving support there.

---

### Post by mostwanted on 2006-06-08
Hi there. You need to set the default device to eth0, right now it's not set to anything:

[IMG]http://coldstorage.macbonsai.com/public/ubuntu-network.png[/IMG]

Take a look at this screenshot. Can you see the empty pulldown box? Choose eth0.

---

### Post by kevinkobecross on 2006-06-09
I solved the Parallels networking issue 2 ways:
- Use the ethernet port instead of the airport wireless (not optimal, but works), or
- Set the Ubuntu ethernet interface to use a static IP

Apparently the current version of Parallels Desktop doesn't play well with the airport wireless.

---

### Post by ttrygve on 2006-06-09
The odd thing about this, that leads me to checking the Ubuntu forums, is that the bridging my MacBook Pro's wireless connection to the Dapper virtual machine works just fine on my home network (open network), but has yet to ever work on my work wireless network (also an open network), or my school's network (PEAP authenticated network).  Additionally, my winXP virtual machine is able to get online just fine from everywhere.

So the sometimes works and sometimes doesn't nature of the problem, along with another OS working fine under the same circumstances, lead me to suspect the Ubuntu forums may have found something unique to Ubuntu that affects it.

Incidentally, I also experienced the same problem with my Breezy virtual machine, so I doubt it's Dapper specific, and I've also tried creating a new virtual machine from scratch and doing a completely fresh default install of Dapper while at work (thinking it may have somehow picked up a setting that was only working for my home network because that's where I installed it), but even the fresh default install on a fresh virtual machine also experienced the same issue.

---

### Post by youbuntoo on 2006-06-09
you get it figured out?

---

### Post by ttrygve on 2006-06-09
[QUOTE=youbuntoo]you get it figured out?[/QUOTE]

I'm not sure if you were asking me or not, but I certainly didn't.  That's why I came in here, because I was hunting around UbuntuForums hoping somebody else had found out something useful.

Until then, the Ubuntu vm on my macbook is only useful at home, where I already have another Ubuntu machine anyway.  =(

---

### Post by youbuntoo on 2006-06-12
yup, I' was asking you...so I assume you check the parallels forum @ [http://forum.parallels.com](http://forum.parallels.com) ???

---

### Post by ttrygve on 2006-06-12
Oh of course, I've been searching both Ubuntu & Parallels forums for pointers.  I did just find a suggestion to set the virtual machine type to "Debian" instead of "Other Linux kernel 2.6", but I'm not somewhere I can test that right now.  I'll reply again after I've tried that.

---

### Post by ttrygve on 2006-06-13
[QUOTE=ttrygve]I'll reply again after I've tried that.[/QUOTE]

That suggestion had no apparent effect either.  I've not yet found anything else helpful on this problem in either the Ubuntu or Parallels forums, sadly.  =(

---

### Post by youbuntoo on 2006-06-15
[QUOTE=ttrygve]That suggestion had no apparent effect either.  I've not yet found anything else helpful on this problem in either the Ubuntu or Parallels forums, sadly.  =([/QUOTE]

What version of Parallels Desktop are you using?

---

### Post by ttrygve on 2006-06-15
[QUOTE=youbuntoo]What version of Parallels Desktop are you using?[/QUOTE]

Woohoo, I hadn't realized there was a new release earlier this week.  I was on "Build 1842.7 Release Candidate 2 (May 28, 2006)".

I've typically upgraded each time I heard about a new version, hoping this would get resolved, I just hadn't seen this one yet.

I've just now upgraded to "Build 1848 (June 12, 2006)", and appears to have solved the problem.

For me, at least, there's also no obvious difference between telling Parallels that the guest OS is "Other linux kernel 2.6" versus "Debian", as some posters had suggested in the Parallels forums.

Thanks for suggesting the obvious, though.  I hadn't yet noticed the new version that I'd been waiting for.  =)

---

### Post by youbuntoo on 2006-06-16
so you just downloaded the GA release and it fixed the problem just like that?  nice.  I'm using it as well and it's lightning fast for me.

---

### Post by youbuntoo on 2006-06-19
has anyone else been using the GA with any luck?

---

### Post by jamarks1 on 2006-11-20
I'm still having trouble gaining my Macbooks full screen real estate using Ubuntu 6.1 edgy with Parallels build 1970. It defaults to 1024 by 768 in full screen mode. 
First, I stated a custom resolution of 1200 by 800 within the Parallels configuration file.
Next, I edited /etc/X11/xorg.conf to accept this resolution.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
        Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	
My changes are the ModeLine and "1200 by 800" in the Modes for each depth listed.

Next, I restarted X and lo and behold... still no 1200 by 800 resolution.

I tried installing the 915resolution package but that was a dead end.

lspci

00:02.0 VGA compatible controller: Unknown device aaaa:1121

Almost Completely new to Linux. 

Any idea?

James

---

