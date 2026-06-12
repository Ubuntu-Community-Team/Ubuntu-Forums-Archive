---
title: "[SOLVED] Urgent!How to install IE in Ubuntu .."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-09-17
Plz tell me how to install Internet Explorer in Ubunu.. I installed both Opera and FF but my sis work cannot be done in this .. The calender field is not opening in any of em so how can I install Ie plz help urgent :(:mad:
Regards

---

### Post by zach12 on 2007-09-17
first you need to install wine then just download IE 
and open it with wine

---

### Post by kebes on 2007-09-17
> **Dark Star said:**
> Plz tell me how to install Internet Explorer in Ubunu.. I installed both Opera and FF but my sis work cannot be done in this .. The calender field is not opening in any of em so how can I install Ie plz help urgent :(:mad:
Regards

You will of course have to use Wine to run Windows software on Linux. So first thing to do is install Wine:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

There is a project called "IEs4Linux" that says it makes installing Internet Explorer easy:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

This how-to gives a step-by-step for installing IEs4Linux:
[http://www.howtoforge.com/ubuntu_internet_explorer](http://www.howtoforge.com/ubuntu_internet_explorer)
(Note: I have not used it, but it looks reasonable.)

---

### Post by Dark Star on 2007-09-17
What do I nedd Wine for Ie 4 :?

---

### Post by Skidpad on 2007-09-17
> **Dark Star said:**
> What do I nedd Wine for Ie 4 :?
Because IE is for Windows and isn't compatible with Linux.  Wine allows you to run many (but not all) Windows programs in Linux.  If you want to run IE, you'll need Wine.

See the links posted by kebes - good info there on how to get it going.

---

### Post by Simon G Best on 2007-09-17
> **Dark Star said:**
> What do I nedd Wine for Ie 4 :?

You need Wine for the following reasons:-

1.  Microsoft haven't provided a version of IE that runs on Linux.  (This could be considered an example of Microsoft's anticompetitive behaviour reducing your choice in the market place.)

2.  Wine provides programs, such as IE, with a Windows-like environment in which to operate.  That gets round the problem of there not being a version of IE that runs on Linux.

:)

---

### Post by Dark Star on 2007-09-17
But site says this
> 
IEs4Linux is the simpler way to have Microsoft Internet Explorer running on Linux (or any OS running Wine).

No clicks needed. **No boring setup processes. No Wine complications.** Just one easy script and you'll get three IE versions to test your Sites. And it's free and open source.

---

### Post by silent1643 on 2007-09-17
> **Dark Star said:**
> Plz tell me how to install Internet Explorer in Ubunu.. I installed both Opera and FF but my sis work cannot be done in this .. The calender field is not opening in any of em so how can I install Ie plz help urgent :(:mad:
Regards

all hope is lost

---

### Post by Skidpad on 2007-09-17
> **Dark Star said:**
> But site says this
...keep reading. No Wine *complications* - not that you don't *need* Wine.  No complications because the commands are already there for you.

---

### Post by philinux on 2007-09-17
IEs4linux says that the browsers are only for testing sites. Not for browsing?

---

### Post by slira on 2007-09-17
I have the exact same problem: my work web site only accepts IE :(  some of the tag's and so-called CSS only work with that "thing"...
i simply refuse to have it in my machine, so i do not access, except when i'm there... :guitar:
and when things are not done in time, so sorry... please use decent software.
slira

---

### Post by CaptainInsaneO on 2007-09-17
> **silent1643 said:**
> all hope is lost

I :lolflag:'d, mostly because I thought the same thing.

---

### Post by w4ett on 2007-09-17
Abandon hope all ye who enter this thread.

---

### Post by reckless2k2 on 2007-09-17
yeah dark star, depending on what needs to be done and especially if it's activex driven which it sounds, you're going to need to go back to windows.

---

### Post by Kilz on 2007-09-17
> **philinux said:**
> IEs4linux says that the browsers are only for testing sites. Not for browsing?

That is correct IE is a security problem waiting to happen. Secondly Wine is a bug for bug copy of windows. Its prone to the same problems Windows is. IE is ok to check and see if the page you created looks good on IE, or for one or 2 sites that may not run on Firefox that you really need to run (like if you need to access your employers site to get paid).
But do not surf with IE under wine. While someone is bound to say it can only mess up your user account. How many users would be ok with wiping out the home folder and all their files in it to get rid of a bug IE installed?


But there is an alternitive some people dont know about [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") is a Firefox extension that can tell a website you are using IE. Some sites that block you will work with this simple trick.

---

### Post by Calash on 2007-09-17
Just as a note, my work also requires IE for some of it's web based functions.  IE4Linux did not work for me, I had to setup a virtual PC (VMWare or Virtualbox) and load windows that way.

The problem was when it tried to download and install the ActiveX component that created a VPN link to my company.  It was not happy doing that :).

---

### Post by dark_harmonics on 2007-09-17
Calash's solution is the one i would reccomend although the user agent switcher is very interesting and im going to play with how well that works for some of my apps. 

Look for work purposes there are some things that just have to be done on software that runs only in windows (yea i check for wine support because i like my ubuntu so much better). So running a virtual machine is really no problem for my super-low overhead ubuntu. It runs windows like it was the only OS on there and even fools my boss. I switch to the cube side that has xp on it when he walks in the room!.

---

### Post by philinux on 2007-09-17
Just installed ies4linux. No errors and it works a treat. I will prob only use it for that "odd" site. I like firefox too much now.

---

### Post by DouglasAWh on 2007-10-10
> **kebes said:**
> 
This how-to gives a step-by-step for installing IEs4Linux:
[http://www.howtoforge.com/ubuntu_internet_explorer](http://www.howtoforge.com/ubuntu_internet_explorer)
(Note: I have not used it, but it looks reasonable.)

These instructions are now out of date.  Change edgy to fiesty or maybe it just to work correctly because I already had WINE installed.  Anyway, I skipped some of the initial steps and got it working.  Thanks!!!!  People that force IE usage should be drug into the street and shot.  *shudders*

---

### Post by DouglasAWh on 2007-10-10
Ok, first problem...PandoraFM does not appear to work.  Neither does Pandora, but they stop working at a different point.  I actually have problems with Pandora in Firefox in WINE also.  WINE doesn't seem to access the sound card.  Anybody know of a way to solve this?

---

### Post by n3tfury on 2007-10-12
user agent switching works awesome, thanks Kilz

---

