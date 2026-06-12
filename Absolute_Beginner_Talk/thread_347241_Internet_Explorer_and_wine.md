---
title: "Internet Explorer and wine"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2007-01-26
I posted this in another area of the forum, but it pretty much died and I am in a kind of a rush.

In wine will IE be able to play a streaming video feed from an mpeg Network camera. [[link]("http://www.cnet.com.au/wireless/accessories/0,239028911,240055564,00.htm")] (I get an error using ff in any OS talking about mpeg-4)

I think I'll need dx because in XP it had to update mine.

Thanks

ps- I need it so i can watch a horse being born over the internet! (soon) Problem is I have linux mainly :P

---

### Post by HereInOz on 2007-01-27
Not sure, particularly as you had to upgrade your directX in XP, but check out this site:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

It may give you some of the information you need.  Sorry I can't be of more assistance though.

---

### Post by acorn22 on 2007-01-28
Sorry, It was active x or something

---

### Post by AirRaven on 2007-01-28
Have you installed Internet Explorer onto your computer yet? 

If not, [Grab the Linux Installation Script here](http://www.tatanka.com.br/ies4linux/page/Main_Page). It automatically configures a Wine install for IE usage. 

Try it with that first, and then get back to us.

---

### Post by LKRaider on 2007-01-28
You can watch or download the stream with mplayer or wget:

example:
```
mplayer http://user:passwd@192.168.1.115/img/video.asf
wget --http-user=user --http-passwd=pass http://192.168.1.115/img/video.asf
```
[source link]("http://www.linuxhjælp.dk/index.php?title=WVC54G")

Another link, in english and more info:
[http://www.linuxslate.org/LinksysWVC11B.html](http://www.linuxslate.org/LinksysWVC11B.html)

---

### Post by acorn22 on 2007-01-28
I don't have IE on my linux yet. I've had to use windows for the past few days. 

Thanks for all the replies. I checked out ies4linux and I think they said how to add activeX on there.

Also, It's funny that LKRaider should use .115 for an example ip because on thier local network that is the ip :P

edit: .115 wasn't a conesidence. I am just dumb. lol

---

### Post by acorn22 on 2007-01-31
UPDATE: I got the video working through mplayer (ty LKraider) and IE installed, but I couldn't get activeX installed. I couldn't find any info, rather.

But now it's working and I'm happy!

---

### Post by capran on 2007-02-10
I'm interested in using my Ubuntu box as a HTPC, and I'd like to be able to use Netflix's new Watch Now feature. But it requires Windows and Internet Explorer.

So I tried IEs4linux, and I can browse to Netflix, but Watch Now claims "Your operating system is not compatible with this feature. Try again from a computer with Windows XP Service Pack 2."

I'm thinking it must be the user agent string. But how do I change that?

I've googled for changing IE's user agent string, but what I've come up with requires regediting some keys..which I can't find in IEs4linux's winereg/*.reg files.

Specifically, they want me to change

**[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\5.0\User Agent]**

But I can't find that string specifically.

This will show you your current user agent:** javascript:alert(navigator.userAgent)**

And in IE it tells me **Mozilla/4.0 (compatible; MSIE 6.0; Windows 98 )**

I thought **winecfg** would allow me to change the Windows 98 thing, so I set it to XP, but IE still says 98.

Ideas?

EDIT:

I found this method to change it to read Windows NT 5.1 (XP)

WINEPREFIX=~/.ies4linux/ie6 winecfg

then change to Windows XP in the drop down

Now my user agent reports it, but Netflix's Watch Now site reports the same message as before. Damn!

---

### Post by acorn22 on 2007-02-10
Is VMWare an option?

---

### Post by capran on 2007-02-11
I just tried VMware Player with WinXP, and while the Watch Now plug-in installs, I can't watch any movies. It brings up a message about your DRM codecs or whatever need to be updated, then after that a another window shows up but it's all black, then later it goes white with "Bad Request" in the box.

Shrug.

Plus the resolution was all screwed up when I go to full screen. My screen is 1024x768, and it'd be larger than that, so part of it was off screen. I tried changing res, and it goes to 1024x768, but the left side of the display starts about 2" from the left side of the monitor, and I can move my pointer into the blank area! Screwey.

Begining to think Ubuntu/Linux is just not right for what I want to do with this box, as much as I like hacking/futzing with it. Too bad I can't legally run OS X on this box, and it's even more hackish than Linux to get working on a PC. So that leaves Windows, and the only legal copy of that I own is Vista Home Premium OEM I just set up for my gaming box (yeah, long story, and it was only $10 more than XP MCE), so that means I'd have to resort to less than legal means and WGA work arounds, etc. GAH. I hated doing that.

---

### Post by LKRaider on 2007-02-11
Do you pay for Netflix (whatever that is) ? If so, complain it doesn't work and you want your money back.

It is afterall their fault. I would search for another service.

---

