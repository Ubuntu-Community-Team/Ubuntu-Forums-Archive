---
title: "gxine streamin vids online"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by 068139 on 2008-04-13
**SOLVED**

2 problems.

1- i start the app gxine and i see a splash screen that does not dissapear, how do i quit or  close the app or make the splash go away?
2- how would i go about using gxine or any other media player to be able to see the content available at allsp.com or familyguyx.net, it uses dailymotion.com to play the videos. Thanks for all the help guys!

---

### Post by 068139 on 2008-04-13
bump

---

### Post by starcannon on 2008-04-13
Try Mplayer, you can get it using synaptic package manager, also be sure to get the mplayer firefox plugiin, also available using synaptic package manager.

While your in synaptic grab all the gstreamer plugins, good, bad, ugly, the whole nine yards, don't bother with the dev ones or the docs unless your going to be messing with them in some low level way.

Thats how I do things, your mileage may vary.

---

### Post by 068139 on 2008-04-13
I've got mPlayer, thanks. I'll try looking for the firefox plugin now...well I'll remove gxine first and then do this..

Thanks for the help, I'm relatively new to linux so..I appreciate how all you guys don't patronise and just give clear constructive advise. I like the community. Thanks again. I'll let you know how I get on. ;)

---

### Post by starcannon on 2008-04-13
Oh yeah, almost forgot, you may need some non-free codecs and things so go here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
follow those directions and then in Synaptic Package Manager get:
w32codecs
dvdcss
lame

and anything else you think you may need :) I always grab the msttcorefonts as well.

---

### Post by 068139 on 2008-04-13
linux is a pain in the backside if you don't know what you're doing. =[

okay, to install the mplayer firefox plugin (i googled it)...basically it does not come as a debian (or ubuntu) file it comes as .rpm...so i downloaded 'alien' to try to convert the file into a suitable .tar.gz2 format or something similar that i could use.

so i typed the following command into terminal:
```

jamie@jamie-desktop:~/Desktop/alien$ sudo ./alien.pl -d mplayerplug-in-3.50-fc6.i386.rpm
[sudo] password for jamie:

```

and it gave me this response:
```

sh: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{NAME} mplayerplug-in-3.50-fc6.i386.rpm":  at Alien/Package.pm line 482.
jamie@jamie-desktop:~/Desktop/alien$

```

Can anybody help me? :( Thanks

---

### Post by starcannon on 2008-04-13
Okay first things first :) take a deep breath.

Sorry for not being more specific, the package your looking for in Synaptic is named mozilla-mplayer that should get you up and running.

Again sorry for not being more specific :(

---

### Post by 068139 on 2008-04-13
I guess what's scary is the fact this is already installed...do i need to configure it to work with firefox or anything? I'm having trouble viewing allsp.com, familyguyx.net and even youtube videos! thanks for the help

---

### Post by starcannon on 2008-04-13
For youtube videos you need the flash plugin, you should get an option to install it from within firefox, likely an alert notice at the top of the page will inform you that you need it.

I'm going to try those other 2 links you posted and see if I have any issues with them.

allsp.com requires the flash plugin as well...checking the other link next
the familyguyx one also requires flash plugin.

So.... get the flash plugin :) in synaptic the plugin is called flashplugin-nonfree, oh and grab ubuntu-restricted-extras while your in there, that'll get a bunch of the good stuff for you, including the flash plugin, sorry if i'm flaky atm, tired, and still have a load of trig to do (returning to college at 39, ugh, do it while your younger, its easier when your brains expiration date is still valid)

---

### Post by 068139 on 2008-04-13
I visitted some page somewhere for the mplayer firefox plugin that gave me the yellow security notice, it said firefox has blocked this install, I clicked options but no drop down menu or nothing appeared, it just remained the same when I clicked it...which sucks :(

**EDIT**
here's the page i visitted where I got the yellow bar to install the plugin that didn't work and still doesn't:
```
http://sourceforge.net/project/downloading.php?groupname=mplayerplug-in&filename=mplayerplug-in-0.4.xpi&use_mirror=mesh
```

---

### Post by starcannon on 2008-04-13
Get that plugin from synaptic reread my last post I edited it. As for those sites that you are interested in, mplayer isnt the issue, the flash plugin is the issue, get the medibuntu repositories, linked them in one of the previous posts, then grab the ubuntu-restricted-extras package it will take care of a lot of media issues (isn't drm loverly)

---

### Post by 068139 on 2008-04-13
Okay, I managed to edit the options, allow installations from sourceforge.net and install the plugin successfully but for some reason allsp.com and familyguyx.net won't work, is there anything else that i need to do? it's not the websites that aren't working, I know that because they're practically online 24/7 for the past...6 months? =[

---

### Post by starcannon on 2008-04-13
Yeah I know they work I could watch them here on my end, Ubuntu Gutsy 7.10 on an Asus Eee 8g. If this little machine can do it, just about any can (with exception of pii era hardware thats pushing it)

---

### Post by 068139 on 2008-04-13
this is really frustrating...I have an AMD processor (1.6ghz 2800+), perhaps I chose some i386 settings instead by accident?

---

### Post by starcannon on 2008-04-13
Some of this is my fault I should have gone and visited those links straight away, for some reason you didn't get a dialogue box asking if you wanted to install the flash plugins. 

You need to go back through the posts, I edited a few of them with directions on how to get your solution.

One post links you to Medibuntu (extra repositories of packages that are non-free)

Another tells you to install ubuntu-restricted-extras after you have enabled Medibuntu, that will get the flash plugin installed for you, and *knock on wood* should get your media issue fixed.

Again sorry for not being more thorough in the beginning, don't let this get to you to much, the nice thing is, once you get Ubuntu set up the way you like it, you rarely have to ever fuss with it (unless like me you just like to).

Anyway give that a shot, I'll keep checking back in.

---

### Post by 068139 on 2008-04-13
It's fine, I'm just happy that you're helping me..

unfortunately here's some bad news.."flashplugin-nonfree" and "ubuntu_restricted_extras" were already installed..this is really becoming painful.

---

### Post by 068139 on 2008-04-13
good news and bad, i manually downloaded flash player 9 from adobe.com for linux x86, installed it from terminal and I have made some progress...now it shows the streaming video but the content does not load...instead it crashes the web browser.

here's a screenshot of what happens:
[img]http://img294.imageshack.us/img294/1544/screenshotgb0.png[/img]

---

### Post by 068139 on 2008-04-13
perhaps this is occuring because i have a sound card enabled and the drivers are not set up? I will try it again with on board sound plugged in...

---

### Post by starcannon on 2008-04-13
Yeah, I've been trying to get you to use synaptic package manager, it removes alot of head aches, /sigh

If your on broadband and can get your ip address to me I'd be willing to vnc in and see if we can fix it, but its starting to snowball into a mess the way were going at it now.

If vnc sounds like something you'd like to do, then turn it on using:
System-->Preferences-->Remote Desktop enable everything in there and set a random password, then send the password to me using private messaging feature here at the forums, when were done turn off Remote desktop until you need it again.

Holler back if this sounds like something that will work for you or not.

---

### Post by 068139 on 2008-04-13
okay, I've just tried it with on-board sound and this is the result...still crashing but this screen appears:
[img]http://img120.imageshack.us/img120/9992/screenshotwq7.png[/img]

---

### Post by 068139 on 2008-04-13
[B]SOLVED[/B

Thanks for all the help, starcannon

---

### Post by starcannon on 2008-04-13
Anytime, was fun.

Be safe, off to do trig now :(

---

