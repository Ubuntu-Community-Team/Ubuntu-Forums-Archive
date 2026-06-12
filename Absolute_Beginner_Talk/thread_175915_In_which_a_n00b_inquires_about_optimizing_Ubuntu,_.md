---
title: "In which a n00b inquires about optimizing Ubuntu, upgrading to 5.10, and more!"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Elim on 2006-05-14
Short backstory: I did install Ubuntu once before, about 9 months ago, but shortly thereafter my sister took that desktop to college, and I left (to a different college) with my laptop (which steadfastly refused to cooperate with Linux).  So, although I regged at this forum 9 months ago, my only real experience with Ubuntu/Linux comes from installing Ubuntu yesterday.  (And what wwould a n00b thread be without the obligatory "Impressive!" comment?  So far I am happy with how things are going, although daunted by the learning curve.)

So I did some searching and I couldn't find much relating to my questions; hopefully I'm not duplicating something that's been asking many times before.

1.) I'm running Ubunut on a very old desktop--128 MB of RAM, 600 MHz processor, <5 GB hdd.  On another forum I frequent (admittedly one not dedicated to Linux), some knowledgable people told me that I could run Ubuntu with that.  Well, they're certainly correct, but it's a bit slow, and I'd like to ease up the pressure on my comp just a bit.  Obviously getting some RAM will help, and I'll do that ASAP, but I am a poor student.  In the meantime, what can I do to use less system resources?
--A friend told me that Xfce is more lightweight than GNOME.  So I'll use Xfce.
--Is there a browser that's better memory-wise than Firefox?  I'm willing to forego some of the extensions and stuff, for now.  FF is a known memory hog, and I've got but 128...
--For that matter, does anyone know of a list of lightweight alternatives to popular apps (e.g. office suites, browsers, media players)?
--Typing "top" into the terminal reveals 72 running "tasks"; a lot more than the ~35 "processes" running on my Win XP laptop.  Is this many normal?  Are there things I can trim down?

2.) I installed 5.04 since that was the install CD that I had lying about from when I did this before.  Should I go ahead and upgrade to 5.10?  Is there anything I need to be aware of that is not covered [here]("https://wiki.ubuntu.com/BreezyUpgrade")?

3.) I think I need to increase my swap.  Currently it's 204 MB.  According to [this article]("https://wiki.ubuntu.com/SwapFaq"), it's not necessary to re-install the OS and expand the swap partition.  Could someone tell me what type of file that article is creating?  How does it differ from a swap partition?  If there's little/no difference, why have a swap partition at all?  Also, should I increase my swap before or after upgrading to 5.10?

4.) Lastly: Synaptic.  Yes, the dreaded package manager!  As a long-time Windows users, I'm having a bit of trouble wrapping my head around this one; does anyone have a link to a nice tasty Beginner's Guide / FAQ that I could use?  Thanks!

Thanks in advance to anyone that can help with any of these questions. :)

---

### Post by aysiu on 2006-05-14
[QUOTE=Elim]
--A friend told me that Xfce is more lightweight than GNOME.  So I'll use Xfce.[/quote] Your friend is correct. [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) > --Is there a browser that's better memory-wise than Firefox?  I'm willing to forego some of the extensions and stuff, for now.  FF is a known memory hog, and I've got but 128... Epiphany. > --For that matter, does anyone know of a list of lightweight alternatives to popular apps (e.g. office suites, browsers, media players)? AbiWord and Gnumeric instead of OpenOffice. JuK is a pretty lightweight music player. > 2.) I installed 5.04 since that was the install CD that I had lying about from when I did this before.  Should I go ahead and upgrade to 5.10? Yes. Or wait three weeks and install Dapper. > 4.) Lastly: Synaptic.  Yes, the dreaded package manager!  As a long-time Windows users, I'm having a bit of trouble wrapping my head around this one; does anyone have a link to a nice tasty Beginner's Guide / FAQ that I could use?  Thanks! [http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

---

### Post by jdusablon on 2006-05-14
aysiu, you forum hog!:)

Regarding XFCE, yes it's lighter. You have a few choices:

1. There's a distro built specifically with XFCE as the window manager called Xubuntu. You may want to try that if you want to start off with a trim system to begin with.

2. You can find out how to install XFCE (not too hard) and rip Gnome out (not so easy)

3. As the most difficult (learning-curve-wise) maneuvre, you can start with a server install of ubuntu and apt-get everything manually and set everything up (like X.) This is the lease fun, but you're guaranteed a trim and snappy install!

If you can, go for #1. It's clean and fast.

---

### Post by RAV TUX on 2006-05-14
[QUOTE=Elim]
--For that matter, does anyone know of a list of lightweight alternatives to popular apps (e.g. ...media players)?
-[/QUOTE]

Quark is also a nice lightweight media(music) player.
:mrgreen:

---

### Post by Elim on 2006-05-14
[QUOTE=aysiu]
Epiphany.[/QUOTE]
I downloadeded Epiphany (at first I thought you were just being smarmy about my remark that FF uses a lot of memory!).  However, it didn't seem to be that much lighter--it used 86 MB VM compared to FF's 116 (and FF had four tabs loaded).

Some research yielded Dillo and Skipstone, although I've yet to install them.  And how does Opera compare to FF?

[QUOTE=aysiu]
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)[/QUOTE]
Thanks, the background there helped a bit.  From the tutorials, I more or less understood how to use it (it's not hard), but I didn't understand the concepts behind it.

When I used it to install Epiphany I did run into a problem, though.  There was one dependency (iso-codes) that installed with Epiphany, but when I uninstalled Epiphany I had to specifically tell Synaptic to uninstall the dependency--it didn't do it automatically.  Is there a way to make Synaptic uninstall a program's dependencies when it uninstalls that program?  (Assuming, of course, that the dependency is not needed for anything else...)


[QUOTE=jdusablon]
Regarding XFCE, yes it's lighter. You have a few choices:

1. There's a distro built specifically with XFCE as the window manager called Xubuntu. You may want to try that if you want to start off with a trim system to begin with.

2. You can find out how to install XFCE (not too hard) and rip Gnome out (not so easy)

3. As the most difficult (learning-curve-wise) maneuvre, you can start with a server install of ubuntu and apt-get everything manually and set everything up (like X.) This is the lease fun, but you're guaranteed a trim and snappy install!

If you can, go for #1. It's clean and fast.[/QUOTE]
I'm sorry, I suppose I should have made myself more clear.  I'm actually already using XFCE--after I installed Ubuntu I downloaded it.  I do have a question that springs from your remarks, though.  What's the benefit of installing Xubuntu rather than Ubuntu with XFCE?  And, I'm sorry, but what's the difference between Xubuntu (1) and the server install with XFCE (3)?


One last question, if you'll permit me.  In XFCE, how do I change the desktop background?  I know how to do it (Settings > Desktop), but nothing changes when I change the image.  Thoughts?  Advice?

Thanks again for your help.

EDIT to add: Ooops, forgot something.  How do I open Synaptic in XFCE?  Right now the only way I can access it is via the terminal...

Oh, also: When I installed Epiphany it didn't add itself to the "Xfce Menu" (equivalent to the applications and system menus in the top left of GNOME).  So the only way I could access it was via the terminal.  How can I add programs to the "Start" menu, and ensure that when Synaptic installs them a link gets put there?  Thanks.

---

### Post by nalmeth on 2006-05-14
wow alot to remark on

the only difference between xubuntu and ubuntu with xfce is that you're getting pre-selected packages, or a custom default package set with xubuntu, whereas with ubuntu + xfce you get the xfce developers packages set. Make sense?

Galeon is supposed to be pretty light webbrowser. Opera is supposedly faster than firefox, and I happen to like Opera, but funnily never use it.. YOu have to manually link your firefox plugins to get multimedia + flash to work.
Swiftfox is supposed to be faster that firefox, but it didn't bedazzle me. I happen to be fine with firefox's speed and memory usage. I know it's a little bloated + big, but it works so well.
You won't like dillo for an everyday webbrowser, unless all you want to view is text and pictures. It is the fastest GUI browser I know of though.
of course xmms is the great light music player. Totem is light enough for my on my slow laptop. I recommend abiword for wordproccessing. Any other's you need?

You may consider installing dapper (6.06) early. It is quite stable in my opinion, and with the newer kernel is faster too.

You can prelink apps to make them load faster, it makes a noticeable difference for me. There is a guide for doing this on these forums.

YOu can create a launcher on your panel for synaptic, but the command has to be:
gksudo synaptic
so that you're prompted for the password.

I never use synaptic, as I love the terminal for apt-get

searching for packages easy as
apt-cache search package_name

I don't know what is up with your desktop wallpaper.. It's supposed to be instantaneous.

About epiphany/xfce menu I don't have this problem, but restarting xfce might do it.
Do you know about xfce-appfinder?
It's included with xfce, it is sweet.

I recommend installing the xubuntu rather than xfce, it might sort out these minor problems.

EDIT: seeing that you only have 5 gigs, not alot, I would rip out gnome as suggested. You won't want to rip it out completely though, as you might lose totem and a lot of other packages. Tread carefully. I would honestly go for a bigger HD than more RAM. 128 isn't that small. I have 96 and am pretty comfortable.
Any other questions? Any thing we missed?

---

### Post by aysiu on 2006-05-14
[QUOTE=Elim]I downloadeded Epiphany (at first I thought you were just being smarmy about my remark that FF uses a lot of memory!).  However, it didn't seem to be that much lighter--it used 86 MB VM compared to FF's 116 (and FF had four tabs loaded).[/quote] It's not the amount of memory--it's the speed. But, yeah, Firefox runs pretty quickly for me, so I don't really see a need for Epiphany. For others, Firefox has been kind of sluggish.

> 
Some research yielded Dillo and Skipstone, although I've yet to install them. Dillo is super-fast, but it's kind of lacking in features. > And how does Opera compare to FF? Slow to load, fast to browse.

> 
When I used it to install Epiphany I did run into a problem, though.  There was one dependency (iso-codes) that installed with Epiphany, but when I uninstalled Epiphany I had to specifically tell Synaptic to uninstall the dependency--it didn't do it automatically.  Is there a way to make Synaptic uninstall a program's dependencies when it uninstalls that program?  (Assuming, of course, that the dependency is not needed for anything else...) Synaptic, Adept, and apt-get will not remember what dependencies came along with an application, so you should use *aptitude* instead. ```
sudo aptitude update
sudo aptitude install epiphany-browser
``` Then, ```
sudo aptitude remove epiphany-browser
``` would also remove *iso-codes*.

> 
One last question, if you'll permit me.  In XFCE, how do I change the desktop background?  I know how to do it (Settings > Desktop), but nothing changes when I change the image.  Thoughts?  Advice? If you've run Nautilus, it takes over XFCE's desktop. You need to run the XFCE desktop command to get it back. I forget what the command is. Open a terminal, type *xf* and press Tab twice.

---

### Post by catlett on 2006-05-14
Dillo and lynx are super light. But what do you want? If you want full rendering they will not do. If you just want speed, low resource usage and text only dillo is good as a launching browser.[http://www.dillo.org/](http://www.dillo.org/) Lynx runs in the terminal.[http://lynx.browser.org/](http://lynx.browser.org/) They should both be in Synaptic(I think)
This might help with the xfce questions [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

