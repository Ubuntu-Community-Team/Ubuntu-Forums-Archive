---
title: "gnome transparencies"
date: 2005-01-18
forum: Art &amp; Design
---

### Post by lizardking on 2005-01-18
Somebody knows how to set  **transparencies** under Gnome 2.8 ?  :?: 

thnx

---

### Post by Johan on 2005-01-18
Assuming that you have configured your x.org correctly you can use the xcompmgr and transset commands to set transparencies. They can be installed by apt-get install xcompmgr transset. This, however, assumes that you are using Hoary.

---

### Post by lizardking on 2005-01-18
[QUOTE=Johan] assumes that you are using Hoary.[/QUOTE]
and if I am with warty i can't?

---

### Post by DoubleDangerClub on 2005-01-18
No.  XF86 does not support transparency.

---

### Post by eNiNjA on 2005-01-22
[QUOTE=lizardking]Somebody knows how to set  **transparencies** under Gnome 2.8 ?  :?: 
 
 thnx[/QUOTE]
 
 Hehe, excuse me for this one...
 
 Why do we buy faster computers, only to get em fat, and slow them down?
 
 *is guilty too

---

### Post by WakkiTabakki on 2005-02-10
>  Why do we buy faster computers, only to get em fat, and slow them down? 

This applies to girlfriends as well...

---

### Post by vassalle on 2005-03-07
[QUOTE=Johan]Assuming that you have configured your x.org correctly you can use the xcompmgr and transset commands to set transparencies. They can be installed by apt-get install xcompmgr transset. This, however, assumes that you are using Hoary.[/QUOTE]
 hi.. how do i set all this option ? is it buggy or laggy in anyway ? iM using hoary btw.. thanks in advance!

---

### Post by bored2k on 2005-03-07
[QUOTE=WakkiTabakki]This applies to girlfriends as well...[/QUOTE]
 rofl

---

### Post by invitro on 2005-03-08
[QUOTE=eNiNjA]Hehe, excuse me for this one...
 
 Why do we buy faster computers, only to get em fat, and slow them down?
 
 *is guilty too[/QUOTE]

Hehe. The thing is that with a reasonably recent graphics card from Nvidia, it's not slowing it down. At least not noticable. That means we can have eye candy porn for free!

Can't wait until Metacity integrates XComposite support and has options for window shadows!

---

### Post by HungSquirrel on 2005-03-08
> is it buggy or laggy in anyway ?
Yes and yes.  It's good for pretty screenshots and that is it.

---

### Post by invitro on 2005-03-08
[QUOTE=HungSquirrel]Yes and yes.  It's good for pretty screenshots and that is it.[/QUOTE]

Buggy - yes
Laggy - depends

I didn't have any speed problems with Nvidia drivers and HWAccel (or whatever it's called) turned on.

---

### Post by vassalle on 2005-03-09
[QUOTE=invitro]Buggy - yes
Laggy - depends

I didn't have any speed problems with Nvidia drivers and HWAccel (or whatever it's called) turned on.[/QUOTE]
 HWAccel ? what is that?

---

### Post by TravisNewman on 2005-03-09
RenderAccel? That's the only thing I can think of.

---

### Post by LongTooth on 2005-03-09
How does one use this option? How to set it?

I just did a sudo apt-cache search xcompmgr transset. No return on this query. Where can I get it? Would I have to add a repository? 

And last but not least, once I get it, how do I use it? Thanks.

---

### Post by invitro on 2005-03-09
[QUOTE=panickedthumb]RenderAccel? That's the only thing I can think of.[/QUOTE]

Of course I meant RenderAccel (blame the early hour)!

It's an option available only to those with Nvidia cards and the proprietary nvidia driver. Google it and you will find how to use it!

---

### Post by LongTooth on 2005-03-15
I've done some searching but still can't fine how to enable this feature. Can anyone give us a few pointers. According to the some post, it buggy and slows down your machine. I'd still like to give it a shot. So along with instructions on how to use it, don't forget the instructions on how to turn it off. Thannks.

---

### Post by Gary Powers on 2005-03-15
It has not worked for me yet  [-o< , but I was told to enter "transset" at the command line and then click on the desired window.  If you find the correct way, let us know.

Gary

---

### Post by LongTooth on 2005-03-15
Well, I did the same thing and I do get the '+' but when I click on a window...nothing. I would have expected to configure my system to have this on when I open an app, be that the the browser or what ever. I'd like some comments from someone who's used it. Thanks.

---

### Post by vik on 2005-03-15
Are you sure you're running "transset <transparency_value>" ?  Usually doing transset 0.7 gives me a nice transparent window.  Before I run trannsset, I run xcompmgr -c to start up the composite manager.

Make sure you have this somewhere in your xorg.conf:

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Also, if you are using the nvidia binary chipset driver, add these lines in your Section "Device":

Option  "AllowGLXWithComposite" "true"
Option     "RenderAccel" "true"

It goes extremely slow on my ati card since the fglrx driver disables DRI if composite is enabled :(

---

### Post by telmo on 2005-03-15
I just find it too damn buggy!
(using ATI driver 3D enabled)

---

### Post by LongTooth on 2005-03-16
Well, with these last two post, I think I'll stay away from this. If it affects the preformance of my system to this extent I don't want it. I like eye candy as much as the next guy but not at the expense of my PC. Maybe later when these issues get ironed out.

---

### Post by Gary Powers on 2005-03-16
Thanks, Vik!

Gary

---

