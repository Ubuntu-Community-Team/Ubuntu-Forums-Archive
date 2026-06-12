---
title: "Ubuntu vs Kubuntu"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by timdh on 2006-04-20
I hope this is the right place to ask this. I have only used Xandros so I guess I am a beginner. :) 

Anyway, I am thinking about switching from Xandros to either Ubuntu or Kubuntu but would like a little more information on a couple items. 

1. I am not sure which version of Ubuntu to use - Ubuntu or Kubuntu. Xandros uses KDE so that is the only thing I know but I have heard that some people prefer Gnome. How about some advantages/disadvantages of the 2 versions of Ubuntu. I am mainly looking for something that looks sleek and is easy to configure. I found some interesting information about Compiz on the forums here and I would like to be able to run something like that.

2. Not sure how to ask this one. Does Ubuntu break easily if I compile software that is not built specifically for Ubuntu? What I am trying to get to is this...Xandros is pretty and easy to use but if you venture outside of thier official software packages then there is a real risk of breaking the system. I know because I screwed up my installation several times after trying to compile something that was not on their "approved" list. I want something that I can play with a little more without worrying about breaking it. 

Thanks!

Tim

---

### Post by pbaehr on 2006-04-20
As for the first question, I would suggest installing Kubuntu if you're already comfortable with KDE. If you feel adventurous and want to try Gnome it's very easy to install alongside KDE (sudo apt-get install ubuntu-desktop). Down the road if you develop a strong preference you can safely remove the one you don't want any more. But why not start with KDE since you're already familiar with it?

Can't help you with the second question but someone with more experience in that field will probably come along and answer it for you.

---

### Post by mjm115 on 2006-04-20
[QUOTE=timdh]I hope this is the right place to ask this. I have only used Xandros so I guess I am a beginner. :) 

Anyway, I am thinking about switching from Xandros to either Ubuntu or Kubuntu but would like a little more information on a couple items. 

1. I am not sure which version of Ubuntu to use - Ubuntu or Kubuntu. Xandros uses KDE so that is the only thing I know but I have heard that some people prefer Gnome. How about some advantages/disadvantages of the 2 versions of Ubuntu. I am mainly looking for something that looks sleek and is easy to configure. I found some interesting information about Compiz on the forums here and I would like to be able to run something like that.
[/QUOTE]

First off, welcome!

Honestly, the underlying systems of Ubuntu and Kubuntu are exactly the same.  The only difference is the user interface- if you prefer GNOME (Ubuntu) or KDE (Kubuntu).  You can actually try both if you want.  Using the package manager in Ubuntu, you can add the 'kde-desktop" meta package or 'ubuntu-desktop' in Kubuntu, and then you can try both Gnome and KDE.  I personally prefer KDE and am therefore a Kubuntu user.

[QUOTE=timdh]
2. Not sure how to ask this one. Does Ubuntu break easily if I compile software that is not built specifically for Ubuntu? What I am trying to get to is this...Xandros is pretty and easy to use but if you venture outside of thier official software packages then there is a real risk of breaking the system. I know because I screwed up my installation several times after trying to compile something that was not on their "approved" list. I want something that I can play with a little more without worrying about breaking it. 

Thanks!

Tim[/QUOTE]

For this one, it is really hit or miss.  As with all distros, you would like to stay with it's own packages, but I have installed packages, not in the repositories with success.  So the only thing I can say is, it may work, it may not.  I have used Xandros before and what I CAN tell you is that the system will not break nowhere NEAR as bad as it would Xandros.  You can try going to [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) and creating a better sources.list than the one that comes with the system.  The added repositories should give you most of the packages specific to Ubuntu (Kubuntu) that you may need or are looking for.

Let us know if you have any more questions.

---

### Post by hw-tph on 2006-04-20
1. KDE or Gnome? It's up to you. Don't swear by one until you have tried the other. And to make matters more easy - Ubuntu and Kubuntu is actually the same distribution, only Kubuntu installs a KDE based desktop and Ubuntu installs a Gnome desktop. You can install one or the other by installing the ubuntu-desktop or kubuntu-desktop meta packages. You are not tied to either of these though - I prefer Gnome (GTK) applications but I think Gnome is a tad slow for my computer, so I generally use use lighter setups. [OpenBox and pypanel/fbpanel](http://hakan.prinsig.se/files/screenshots/ss_devon_2005-09-09-1804.png) has been a favourite of mine for some time now.

2. I use a lot of locally built applications. No problem here. I usually install to the default /usr/local prefix and have no problems with that.

Håkan

---

### Post by hw-tph on 2006-04-20
Oh, three of us responding at the same time. That's community response for ya. :)


Håkan

---

### Post by aysiu on 2006-04-20
[QUOTE=pbaehr]If you feel adventurous and want to try Gnome it's very easy to install alongside KDE (sudo apt-get install ubuntu-desktop). Down the road if you develop a strong preference you can safely remove the one you don't want any more.[/QUOTE] While *apt-get* will easily install Gnome alongside KDE, it will not make Gnome so easy to remove if you don't want it any more. ```
sudo apt-get remove ubuntu-desktop
``` removes virtually nothing (just the pointer to all the packages *ubuntu-desktop* installs--the actual packages themselves will not be removed).

If you want to try Gnome, do this instead ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
``` When/if you want to remove Gnome later, do ```
sudo aptitude remove ubuntu-desktop
```

---

### Post by pbaehr on 2006-04-20
Good call. I was slightly miffed to find that out the hard way when I tried installing kubuntu-desktop and ended up having to use a command which spanned 10 or 11 lines.

Either way, the point remains that it is easy to install. Just not my way. ; )

---

### Post by aysiu on 2006-04-20
[QUOTE=pbaehr]Good call. I was slightly miffed to find that out the hard way when I tried installing kubuntu-desktop and ended up having to use a command which spanned 10 or 11 lines.

Either way, the point remains that it is easy to install. Just not my way. ; )[/QUOTE] Hey, I learned the hard way, too!

---

### Post by NeoGreen on 2006-04-20
What if you are using GNOME and you want to give KDE a try? :D

---

### Post by Jagot on 2006-04-20
[QUOTE=NeoGreen]What if you are using GNOME and you want to give KDE a try? :D[/QUOTE]

sudo aptitude update && sudo aptitude install kubuntu-desktop

---

### Post by Charax on 2006-04-20
What's with the aptitude stuff? I just used Synaptic to add KDE to Ubuntu.

---

### Post by aysiu on 2006-04-20
[QUOTE=Charax]What's with the aptitude stuff? I just used Synaptic to add KDE to Ubuntu.[/QUOTE] What happens when you try to uninstall KDE with Synaptic? That's why people recommend *aptitude* instead.

---

### Post by catlett on 2006-04-20
Aptitude is another way to install packages. It is installing the same things as Synaptic. All their programs come from the same repository list. It's just that Aptitude deals with dependency issues better and it appears uninstalling desktops as well. If you have the Debian Menu you can enter it graphically by Debian<Apps<System<Aptitude.

---

### Post by aysiu on 2006-04-20
[QUOTE=catlett]But take my word for it if the advice comes from Aysui, you can go take it to the bank.[/QUOTE] I hardly think that's true at all. I try my best, but I'm still a new user (coming up on my first year Ubuntu anniversary in a couple of weeks).

So, to make sure I'm not just talking out of my behind, I did a little test. Installed *kword* using Synaptic. It also installed *libwv2-1c2* and *kspread*. Then, I uninstalled *kword*--only *kword* was uninstalled. I had written down the names of those two other packages, so I was able to manually mark them for removal in Synaptic, but they otherwise would have stayed.

Then I tried *aptitude*. Here's what happened: ```
user@ubuntu:~$ sudo aptitude install kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  kspread libwv2-1c2
The following NEW packages will be installed:
  kspread kword libwv2-1c2
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7707kB of archives. After unpacking 19.6MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package kspread.
(Reading database ... 79081 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.4.2-3ubuntu11_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.4.2-3ubuntu11_i386.deb) ...
Setting up kspread (1.4.2-3ubuntu11) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword (1.4.2-3ubuntu11) ...

user@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  kspread libwv2-1c2
The following packages will be REMOVED:
  kword
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 19.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 79863 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing libwv2-1c2 ...
user@ubuntu:~$ 
```

---

### Post by beewer on 2006-04-21
Hi.

I have Kubuntu 5.10 box. If I install gnome-desktop will I be able to start multiple sessions with different window managers (is this right term?)?

Usually me and my wife are both logged on this computer and we jump back and forth between sessions using ctrl+alt+7 and ctrl+alt+8.

If she logs onto computer first and starts kde session, will I be able to start gnome session? And other way round? And can we still jump between sessions using same keys as before?

-b

---

### Post by catlett on 2006-04-21
You choose the session at the login screen. When you're at the login in screen look over and you'll see "sessions". This opens a list of options. From there you will be able to pick KDE or Gnome desktop. This is one of tye nice things about Linux. The log on/off is quick and versatile. You can have KDE and Gnome and choose what you want to use each time you log in.

---

### Post by gingermark on 2006-04-21
[QUOTE=timdh]2. Not sure how to ask this one. Does Ubuntu break easily if I compile software that is not built specifically for Ubuntu? What I am trying to get to is this...Xandros is pretty and easy to use but if you venture outside of thier official software packages then there is a real risk of breaking the system. I know because I screwed up my installation several times after trying to compile something that was not on their "approved" list. I want something that I can play with a little more without worrying about breaking it. [/QUOTE]
I compile a fair few apps for my own system and they all run fine. Have a look at checkinstall ([https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)) for a program that will create a .deb file for you when you compile from source so that any manually compiled software can be removed easily.

---

### Post by timdh on 2006-04-21
Thanks for all the input! I may try to install both KDE and Gnome at a later date but I think I will start with Gnome. I am already familiar with KDE so I want to see how Gnome compares. Knowing that I can change/add/delete in the future makes this a pretty easy decision. 

Also, thanks to those who responded regarding compiling apps on Ubuntu. I love to play with, and learn, new software, which is something I did not get to do much with Xandros because it is rather easy to break it.

Tim

---

### Post by Sarisar on 2006-05-12
```
sudo aptitude update && sudo aptitude install kubuntu-desktop

Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
```
I won't list them but it's about 25 in total!  Also looking at doing it through the synapyic manager it wanted to install... well ubuntu it looked like!

I'm fairly happy with gnome (although to be honest I despise the brown) but thought if it was this simple I would try out KDE.  Now the question is, have I broken something (a dependancy uninstalled somehow) and that is why the commands aren't working?

---

### Post by aysiu on 2006-05-12
When you get that kind of dependency warning, it usually means you have conflicting repository sources.

Get a fresh list here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by sabredog on 2006-05-12
As an aside, just how big is the KDE package once installed?

cheers and thanks

---

### Post by aysiu on 2006-05-12
[QUOTE=sabredog]As an aside, just how big is the KDE package once installed?

cheers and thanks[/QUOTE] I think it's several hundred MB--maybe about 300? Try ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` It'll tell you all the packages it wants to install and how much room it'll take up in MB. If it seems like too much room, just say "no." If you want to proceed, say "yes." You can always remove KDE later with ```
sudo aptitude remove kubuntu-desktop
```

---

### Post by sabredog on 2006-05-12
Hmmm, I have around 4.4Gb left on the partition, might install it to have a play :)

---

### Post by sabredog on 2006-05-13
Well that was easy. I noticed that the trash icon is back on the Gnome desktop. How can I remove that safely?

cheers and thanks

---

### Post by aysiu on 2006-05-13
[QUOTE=sabredog]Well that was easy. I noticed that the trash icon is back on the Gnome desktop. How can I remove that safely?

cheers and thanks[/QUOTE] As long as you have the trash applet in the KDE taskbar, it's safe to delete the one that magically appears on the Gnome desktop.

I *think* it'll keep regenerating, though, every time you log out of KDE and log back into Gnome again. I'm not 100% sure on that.

---

### Post by sourdough on 2006-05-13
[QUOTE=timdh]I hope this is the right place to ask this. I have only used Xandros so I guess I am a beginner. :) 

Anyway, I am thinking about switching from Xandros to either Ubuntu or Kubuntu but would like a little more information on a couple items. 

1. I am not sure which version of Ubuntu to use - Ubuntu or Kubuntu. Xandros uses KDE so that is the only thing I know but I have heard that some people prefer Gnome. How about some advantages/disadvantages of the 2 versions of Ubuntu. I am mainly looking for something that looks sleek and is easy to configure. I found some interesting information about Compiz on the forums here and I would like to be able to run something like that.

2. Not sure how to ask this one. Does Ubuntu break easily if I compile software that is not built specifically for Ubuntu? What I am trying to get to is this...Xandros is pretty and easy to use but if you venture outside of thier official software packages then there is a real risk of breaking the system. I know because I screwed up my installation several times after trying to compile something that was not on their "approved" list. I want something that I can play with a little more without worrying about breaking it. 

Thanks!

Tim[/QUOTE]

To address your second question, any debian based source "should" operate corectly if compiled error free.  The other option is Synaptic, if the binaries are available it's quite an easy solution.

---

### Post by stansz on 2006-05-13
ya thats wat im doing now...im a little bored/have extra time on my hands so im gonna re-try kde.....i briefly tried it once..but im gonna try again....ill keep u all updated ..lol

---

### Post by sabredog on 2006-05-13
Well my wife seems to like KDE better than Gnome :)

---

### Post by stansz on 2006-05-13
mmm it looks nice..but it just doesnt feel as good as gnome

my personal opinions : 

KDE: 
good: Nice looks, smooth, the mouse over bubbles are a nice touch, more "windows" like with the "start" menu on the lower left hand corner...good look and feel...the katapult is neat idea

bad: just doesnt feel right, maybe caues i used gnome alot more, but i dont find the menu to be as intuitive as the gnome menus....the "desktops" are sorta redunant...as the bottom thing still show the progams even in different desktops....a liiiitttle bit slower...not really noticeable..

im gonna unstill kubuntu now..lol it was a nice run while it lasted..but really jsut doesnt feel as comfortable as gnome

---

### Post by sabredog on 2006-05-14
Installed KDE on Friday and when I run an application the CPU use went through the ceiling.

So KDE is pretty and looks functional, my lovely wife likes it but I think Gnome will remain the default desktop because it seems to work faster and no CPU issues.

---

### Post by Tortanick on 2006-05-14
Whats the aptitude command for Xfce?

---

### Post by gingermark on 2006-05-14
If you want Xubuntu:
```
sudo aptitude install xubuntu-desktop
```
If you want Xfce:
```
sudo aptitude install xfce4
```

(same difference as ubuntu's desktop compared with default GNOME, or Kubuntu's desktop compared with default KDE).

---

### Post by Tortanick on 2006-05-14
Thank you :)

---

### Post by Sarisar on 2006-05-14
aysiu: thanks for that - it appears that I had grabbed the repository list from another OLD website and was trying to use an older verison or something.  Ooops!

---

