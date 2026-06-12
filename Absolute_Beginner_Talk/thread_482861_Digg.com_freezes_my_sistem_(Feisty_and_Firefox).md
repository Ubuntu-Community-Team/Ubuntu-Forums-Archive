---
title: "Digg.com freezes my sistem (Feisty and Firefox)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-24
Hello mates.
So, I don't know if everybody is having my problem. But, when I go to digg.com with Firefox on my Feisty, everything goes slow... even my mouse!!! Then I have to close the digg tab to recover my normal speed...

Somebody else is having this strange problem?

---

### Post by Lord Illidan on 2007-06-24
Digg is a pretty large site, but it works fine here. What are your machine specifications?

---

### Post by Kosimo on 2007-06-24
> **Lord Illidan said:**
> Digg is a pretty large site, but it works fine here. What are your machine specifications?

Quite enough for that site I guess.   

[LIST=1]
[*]Pentium M 1.5GHz 2MB L2
[*]1,2 GB RAM 
[*]Ati Radeon 9200 32 MB
[*]80 GB 4.200rpm
[/LIST]

I'm not having any problem when in Win

---

### Post by Kosimo on 2007-06-24
Somebody else can try it plz?

---

### Post by Kosimo on 2007-06-24
Help!!  	:frown:

---

### Post by joep on 2007-06-24
I don't have any problems just came off there. I use swiftfox try that.

---

### Post by Kosimo on 2007-06-24
> **joep said:**
> I don't have any problems just came off there. I use swiftfox try that.

It looks like I'm the only one having this problem...
What a f``!!!!!!!!!!   Swiftfox is the same as well....  :(

---

### Post by bashveank on 2007-06-27
I'm having a similar problem -- whenever I visit Digg FF will periodically freeze, and then unfreeze after a few seconds.

---

### Post by Earthwormzim on 2007-09-11
I just started having the same problem.  I've never had this problem before today (Sept 11, 2007), and now, when I visit Digg, everything goes slower than beans.  When I right click a link (to select open in new tab), I have to shake the window (grab the top, and move it around) for the menu to show, and when I left-click a link, it pops up in a new window instead of running in the same window.  But, all of this at unbearably slow speeds!

So, I open Konqueror, and...boom!  No problem.  But, I like FireFox...I don't wanna have to use Konqueror.  Help, anyone!  Please!!!!

---

### Post by Tsen on 2007-09-11
It's Digg's fault.  Their layout includes a LOT of inefficient and just plain bulky code that tend to freeze up Firefox.  It does the same thing to me in Windows and Linux.  I don't know if there's a fix, but you could see if there's some GreaseMonkey scripts for a slimmed-down version of Digg, or you could just use Reddit.

(BTW, posting "Please help!" repeatedly without adding information isn't liable to get you help faster.  It's actually just kind of annoying.)

---

### Post by cusa on 2007-09-11
I have the  same problem but Konqueror works fine.:confused:

---

### Post by Earthwormzim on 2007-09-11
Here's some additional information:  when I open the System Monitor, firefox-bin stays hovering around 70% to 90% CPU usage...but only when on Digg.  When I go to other websites, after the page loads, firefox-bin sleeps.  

I wonder...what on Digg requires a constant usage of the CPU?  When I view Digg in Konqueror, after the page finishes loading, it goes to back down to 0% CPU usage and goes to sleep, just like it should.  So, I guess the question is:  What is the deal with Firefox?

---

### Post by derjames on 2007-09-11
Ok folks... That behaviour in DIgg.com also happens here... I am using a laptop with a Core2 duo T5600 1GB RAM,  Ubuntu Feisty and GNOME.

What I found is that the Adblock addon lists some annoying add servers even when digg is not displaying any adds. So I blacklisted the servers and firefox returned to normal and the CPU usage drops accordingly...

cheers

---

### Post by deltronik on 2007-09-11
This just started happening on my ubuntu feisty install with firefox on digg yesterday.
Firefox will eat up so much cpu time that my cpu fan will actually start spinning faster.
Firefox gets so slow while digg is open that it is almost unusable.
This sucks.  Doesn't happen in windows xp firefox at all.

Edit:
just reread previous post:  I am not using any extensions or add-ons (just reinstalled firefox because of this issue) and am using gnome

---

### Post by derjames on 2007-09-11
> **deltronik said:**
>  ... I am not using any extensions or add-ons (just reinstalled firefox because of this issue) and am using gnome

Try installing Adblock and while on digg.com go to tools->adblock->show all blockable elements

Then inspect the list on the window that appears and block all the add-servers...

hope this helps.

---

### Post by philinux on 2007-09-11
In adblock use 
*adtech* and
*doubleclick* these filters get most

---

### Post by cwgannon on 2007-09-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/81858](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/81858) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, Digg's code is bloated and inefficient, much moreso than any site that I frequent.

I've experienced the above described problem on all three of my Feisty machines, but I have been able to find a workaround:

From [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/81858](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/81858), courtesy of Matt Jamison:

[LIST=1]
[*]Open a terminal
[*]Enter "sudo gedit /etc/X11/xorg.conf" (replace gedit with your text editor of choice)
[*]In your xorg file that has just opened, scroll to the "Device" section
[*]In this section, add, in a new line: "Option," hit <Tab>, ""XaaNoOffscreenPixmaps""
[*]Make sure you left one set of quotes around "XaaNoOffscreenPixmaps"
[*]Save your xorg file by exiting the text editor
[*]Restart X
[/LIST]

This workaround has worked for most of those who have reported on the bug page (and please add your results there so that this can get fixed).  If it doesn't work for you, I suggest installing the NoScript extension in Firefox and using it to disable Javascript on digg.com, which though it will limit the site's functionality will as well give it a swift kick in the pants.

Anyway, I hope that helps.

---

### Post by deltronik on 2007-09-11
thanks james and phil, it seems to be working fine after following your direction.
Too bad it needs a workaround to work normally.
not that I mind having the ads blocked.

---

### Post by RancidLM on 2007-09-11
ya same.. digg just freezes up my browser. the xorg.conf fix didn't work though.

---

### Post by nmayotte on 2007-09-11
The adblock suggestion worked for me, I just added *adblock* and *doubleclick* and firefox is back to normal cpu usage even when digg is open.  Digg must have changed something like yesterday, thats when it seems mine and others problems started.

---

### Post by FuturePilot on 2007-09-11
Hmmm. Everything is fine here.

---

### Post by n3tfury on 2007-09-11
> **Kosimo said:**
> Hello mates.
So, I don't know if everybody is having my problem. But, when I go to digg.com with Firefox on my Feisty, everything goes slow... even my mouse!!! Then I have to close the digg tab to recover my normal speed...

Somebody else is having this strange problem?

are you using compiz/beryl or compiz-fusion by chance?

---

### Post by Acglaphotis on 2007-09-11
My firefox freezes when i go to digg too.

---

### Post by cusa on 2007-09-12
Adblock works for me :)

---

### Post by misfitpierce on 2007-09-12
It was a ad thing slowing mine down. Does not seem to be doing it anymore. Ad Block Plus avail from extensions on firefox website can block out those ad's and more. :)

---

### Post by Arbiterxero on 2007-09-26
It's the FLASH ads that are causing it.

I turned on only flashblock and it all worked great.

New animated ads on the site are slowing it all down.

---

