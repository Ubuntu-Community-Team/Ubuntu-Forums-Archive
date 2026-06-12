---
title: "Remaster arch Linux into a Newbie Friendly Distro"
date: 2008-01-31
forum: Arch and derivatives
---

### Post by jseiser on 2008-01-31
I love arch and the speed of it.  I enjoy reading configuration files and editing them and all around screwing with my install.  Yet, most people i know who use computers, see them as a necessary evil, one they have to deal with.  I have over the course of the past 2 months, had to set up a few friends and relatives with Linux, either their windows was becoming a pain to manage, they kept using a computer naively and were installing virus and spyware, or they just received some old hardware and wanted to set up a computer for the first time since they were in school.  That is awesome for Linux, and i enjoy showing people things and knowing i helped out.  Yet, each time, i had to spend way to much time installing, icewm or openbox, then setting up their menu, setting wallpapers, and forgetting about pdf files etc and having to go back, because i wasn't confident that some of them could handle the CLI and things of that nature.  So i want to remaster arch, with a WM, Applications, custom menu, folders already pre-fabbed.   I just wanted to know if anyone else see's this not as a problem, but maybe an opportunity to fill a niche, that could really get some use.  Here is what i have so far in the planning department.  

Window Manager - Openbox.
- A light weight, pre configured, desktop, that is fast, but still resembles windows enough to be easy to use from a converted windows users perspective. 

I plan to create this look by having tint pre-installed with a config file already present, one set up for light  backgrounds, others for dark, telling openbox to give me 15 pixels of free space at the top.  This will allow the user a small transparent panel, while allowing them to right click to open the menu.  So we take a 'different' look, and make it somewhat friendly with the pseudo panel.

Menu - I would like an installed menu, that only contains single nested entries.  (example)
Openbox
Sound - app1
           -app2
Web    -app1
          -app2
Admin -app1
          -app2

This allows for easy navigation, but also serves the purpose of making editing it with obmenu a breeze, a new user can easily see 'audio', drop that menu open, and add a new item to it.  Its a minor thing, but could really make the menu easier to edit with obmenu for the newbie.  I would also want to edit obmenus code, or maybe i can create a script that actually launches obmenu, that backs up the menu file before its edited, that way a newbie can revert back an old config

I would like to program a feh frontend, one that just shows you all the images in a directory (~/.wall) and allows to to select an image, and a style (scaled, tiled etc) and hit apply and will launch a feh --bg-scaled(tiled) /path/to/image

This will overcome the problem a newbie gets when he wants to change the background.

The next thing iwanted to tackle was File Manager.  To me, something like gentoo, or emelfm, works best.  I might want to waste some resources here, for teh sake of the persons adjustment.  First Dual pane isnt popular in windows.  Second, i want to easily set up automounting of drives.  So i was thinking of using Thunar as a the Filemanager, and have the volume plugin installed from the get go.

Another problem i see is with music.  I want this distro to be as light as possible, so i want a command line music player.  I see mpd + ncmpc as a very useable lightweight option.  The only problem i see is that mpd needs to be set up, so i need to make the mpd file know the name of the proper user and home folder.  If this isnt possible to set up, i will have to install cplay from source, as it doesnt need set up.

Web browsing will be with kazehakase, using the script from their wiki to delete history at launch.  Mplayer +plugin will allow watching movies in the browser, VLC will handle movies outside of the browser.

xarchive and xpdf will  need to be set up already.  As will mirage with images.  pidgin will be the default IM software, with Xchat installed as well.
P2P is a big deal with users now, so i would want to install nicotine, DC++ and frostwire.  Frostwire has java problems, so the correct java will need to be preinstalled.  I want the  home directory to already be set up with the following folders.

/.wall - for the feh frontend to look for the wallpapers in.
/.torrents so rtorrent knows what folder to watch
/music so mpd or cplay knows where to look for music at
/images for images :)
/documents for typed files
/files for all other downloads

Email will be handled with Sylpheed.  File editing with be with the Open Office suite and Leafpad.Burning is the biggest problem, k3b is by far the best, yet its kde and slow.  If i use Hal/Dbus and then use an alternative file manager, maybe i can get bashburn pre setup.  Another front end i would like to be able to set up, would do nothing more than edit the gtkrc.mine file, it would be nice to just tell this program, where the icon set is installed, say /home/justin/.icons. selecting that path in the program will edit the line in the gtkrc file to match the one we just selected.  That way we are still editing the file for configuration, but the users hand is held somewhat in that they have a GUI to do this task for them.

Can anyone give me more ideas, and maybe want to help out?  I know some basic coding, but i don't really know how to turn arch, into a pre configured distro that someone can install.  I know their are some other distros out there with openbox etc, but the arch base allows for speed.  It also allows this newb distro to be turned into a full fledged distro once that user is more comfortable in linux.

---

### Post by mips on 2008-01-31
I like arch the way it is personally.

Have a look at:
[http://archie.dotsrc.org/?q=node&from=10&PHPSESSID=4b0e6db2e4c57a8ca487b8973487ab87](http://archie.dotsrc.org/?q=node&from=10&PHPSESSID=4b0e6db2e4c57a8ca487b8973487ab87)
[http://bbs.archlinux.org/viewtopic.php?id=14500](http://bbs.archlinux.org/viewtopic.php?id=14500)

You might learn something from the above, Archie has a openbox version from what I can tell.

---

### Post by SunnyRabbiera on 2008-01-31
I never had any real issues installing or using arch, the only big gripe I have against it is its package manager.

---

### Post by jseiser on 2008-01-31
the problem isnt mine, its the people i have to install it for.  Arch itself is awesome, i love everything about it.  but when my cousin gets a old old HP PC, and wants it set up, installing arch, then the DE, then the FM, then trying to show them how to change their background etc becomes a problem.  Making everything pre set up, would be an awesome intro to linux.  Because my cousins or family doesnt care that its windows, or its linux, or that their was even a choice, but when i get them set up, i want them to notice wow, this is fast, and simple, and o its linux, then maybe they will become interested enough to hit the CLI, install their own arch, and config it etc.

---

### Post by mips on 2008-01-31
I would not give arch to a beginner though. More something like Mint.

---

### Post by jseiser on 2008-01-31
Ubuntu based systems are slow.  Also, arch is very newb friendly, you install and just pacman -Sy gnome you would have a full gnome desktop and it would run great and everything.  Something like mint isnt free, and is bloated.  I just want to take the awesome arch linux openbox setup, and put it to a cd that will install it to other computers.  I found larch on the arch forums, and i think this will make doing this very easy.

also mips i looked at archie and its dead :(  the openbox version doesnt seem to have even got off the ground.

---

### Post by fwojciec on 2008-01-31
> **jseiser said:**
> Ubuntu based systems are slow.  Also, arch is very newb friendly, you install and just pacman -Sy gnome you would have a full gnome desktop and it would run great and everything.  Something like mint isnt free, and is bloated.  I just want to take the awesome arch linux openbox setup, and put it to a cd that will install it to other computers.  I found larch on the arch forums, and i think this will make doing this very easy.

also mips i looked at archie and its dead :(  the openbox version doesnt seem to have even got off the ground.

Arch is not newbie friendly, it's not supposed to be and it will never be (without changing beyond recognition).  If a person who uses Arch doesn't know anything about computers and is not willing to learn every system update becomes a potential disaster -- not because Arch is buggy, but because there might be (and there will be -- it's just a matter of time) an upstream change of some sort that the user is expected to inform him/herself about in order to be able to respond to intelligently to it by changing configs for example or whatever is necessary (vide last xorg update and synaptic touchpad issues for many users).

The alternative, of course, is not to upgrade at all, but this will quickly introduce security issues, so it's not a good idea either.

Arch is not a good distro choice for someone who wants the computer to just work.  I understand that you like Arch, and I like Arch too, but if you're setting up linux based computers for others it's best to try and choose a distro that matches their skill level and passion for computers, IMO.

---

### Post by chris4585 on 2008-01-31
> **jseiser said:**
> Ubuntu based systems are slow.  Also, arch is very newb friendly, you install and just pacman -Sy gnome you would have a full gnome desktop and it would run great and everything.  Something like mint isnt free, and is bloated.  I just want to take the awesome arch linux openbox setup, and put it to a cd that will install it to other computers.  I found larch on the arch forums, and i think this will make doing this very easy.

also mips i looked at archie and its dead :(  the openbox version doesnt seem to have even got off the ground.

umm.. i could of swore mint was free, i have downloaded just about every iso they offer for no cost?

---

### Post by eljoeb on 2008-01-31
> **chris4585 said:**
> umm.. i could of swore mint was free, i have downloaded just about every iso they offer for no cost?

Includes proprietary software/codecs.  I guess by that count Ubuntu would have some issues as well.  Of course, this isn't important to everyone.

---

### Post by DJiNN on 2008-01-31
> **SunnyRabbiera said:**
> I never had any real issues installing or using arch, the only big gripe I have against it is its package manager.

Isn't the package manager supposed to be one of the highlights of Arch?  

Arch is excellent and sooo fast, but it can be a pain to install, especially for noobs. Jseiser - i think it's a great idea...... Archie could have been great, and there is already a live CD of Arch (March Linux) which may be worth looking at for some ideas or hints etc. :)

---

### Post by santaslittlehelper on 2008-01-31
If you did do it I would say go with either gnome or kde as default DE makes more sense to me in terms of friendly anyway.

The problem as I see it is that no matter what they would at least have to deal with the output of pacman -Syu which can be a challenge if you have no interest in reading it whatsoever. 
In the couple of months I have run arch I have lost the GUI twice to updates (with only [core]  [extra]  [community] enabled, once to .xinitrc and once to xorg, I think, don't really remember) both times might have been my own fault, but that's not really the point.  

So why not just give them Ubuntu much less chance of anything bad happing IMHO and much less work for you. :)

Just to echo I enjoy the arch way too. :)

---

### Post by Warren Watts on 2008-01-31
I use Arch on my personal system on my home network.  All of the other computers on the network are running Ubuntu, because Ubuntu "Just Works" and I don't have to spend hours maintaining the Ubuntu systems.

I use Arch on my personal system because it's faster, and not "weighed down" with a zillion extra packages at install.  Over the course of the last six months, I have added packages to my Arch box as needed, and I like it that way.

I have never experienced any problems with the system being "borked" by a Pacman upgrade.  Every time there is a kernel or xorg upgrade I always wince, expecting terrible things to happen, but nothing ever has.

My personal recommendation for a default WM would be Xfce, with Thunar as the File Manager.  Its got lots of features, it's intuitive, and not nearly as resource hungry as KDE or Gnome.  I personally find both Fluxbox and Openbox to be a bit spartan for me, and I think a former windows user would find it kind of dull and uninspiring.

But that's just my two cents.  Therein lies the beauty of Arch;  you can build it to be anything you want it to be, to suit your own tastes.

---

### Post by Rumor on 2008-02-01
You might want to look at FaunOS which is trying to do similarly to what the OP is thinking to design: [http://www.faunos.com/index.html](http://www.faunos.com/index.html)

I've not tried FaunOS, but it has received some pretty favorable press. It is Arch based and uses the Arch repositories.

---

### Post by DJiNN on 2008-02-01
Hey Rumor - Thanks for the info & link to FaunOS. Looks really interesting & i'm downloading the USB image right now. It looks like it uses KDE which is cool (only because Konqueror is so fantastic!) but i'd be interested to know how easy (or difficult) it would be to change to XFCE/Gnome/Fluxbox/Openbox etc......

Looking forward to giving it a go though! :)

---

### Post by kelvin spratt on 2008-02-01
Faunos Is superb and there is a new version out soon. The speed is amazing but needs a lot of ram as its a full distro and runs in ram. on my system its like lighting to use. and very stable as you can't break it, Changes are handled by overlays so you can go back to the previous overlay in simply terms.

---

### Post by DJiNN on 2008-02-01
> **kelvin spratt said:**
> Faunos Is superb and there is a new version out soon. The speed is amazing but needs a lot of ram as its a full distro and runs in ram. on my system its like lighting to use. and very stable as you can't break it, Changes are handled by overlays so you can go back to the previous overlay in simply terms.

It sounds great, and in a few hours i'll put it onto a USB stick & give it a go. I didn't know that it runs in ram though.... that's interesting.  I've bookmarked the forums because i'm sure to have a few questions. :)

Have you tried March Linux as well? That's quite an interesting (Arch based) project, but at the moment it's a Live CD only, with (AFAIK) no intention of having a HD install added. Worth having a look at though.

I'd never heard of Larch before either (Until i had a quick look into the FaunOS forums just now) and that looks interesting also, as a way to create Arch based CD's/Distros etc.... So much to look at, it's going to be a busy weekend! :)

---

### Post by jseiser on 2008-02-01
yeah i got a full plate this  morning.  Tryingto figure these larch scripts out and their forums arent to active, think im going to wipe  the main desktop, and se tit up how i want the livecd set up.  Then go from their, i was hoping k mandla would just do this project for me :) I have yet to have a problem with an arch update, and thats with testing running.  My major problem now with larch is I dont understand how it works.  So ill have to wrap my head around that this weekend.  I would love to throw ubuntu on a computer and walk away and let some person use it, but i keep getting people who have PC's that are pretty old, have windows XP on them, and just crawl around.  I dont want to give them ubuntu and say, its really pretty BUT, its going to be as slow as windows, if not slower.  So consider this not a ubuntu diss, but a way to enable old  hardware to perform and grow.  This is going to be my DSL linux type project.  I think the main thing that could  help this be worth using is avoiding gnome or KDE libraries like the plague.

---

### Post by santaslittlehelper on 2008-02-01
If you put it out there ill be happy to dust of my Pentium III and give it a spin. :tongue: j/k
More seriously though, sounds like a good project. But still I have doubt to how newbie friendly it would be, when I think newbie frindly I think about the eee pc for instead. 
How about big icons and lock down?

---

### Post by aeto on 2008-02-02
No biggie. This will just be another Sabayon, except based on Arch. Thought of doing so, but gave up on the idea; there is already FaunOS.

A note to the undertaker:

**Have your own community**

Why? Well, Arch will not support countless newbies who are not "competent" users, eg. rtfm first, then approach for help, know your stuff, or atleast know some stuff. Furthermore, with a remastered platform, comes a different platform. Issues faced may not be parallel to Arch issues. Gentoo has experience of this in terms of Sabayon. In short, prepare to make it an entirely new distro like Sabayon.

---

### Post by DJiNN on 2008-02-02
> **aeto said:**
> Thought of doing so, but gave up on the idea; there is already FaunOS. 

Downloaded FaunOS last night, put it on a 2gb flash drive, it started to boot then just hung there..... couldn't get into it at all??  I was thinking of perhaps downloading the DVD version because i don't seem to have a lot of luck with USB distros..... Maybe it's just early days, but it's definitely the way to go. :)

Have you tried the DVD version? Is it the same as the USB version but just comes on a DVD instead? 

I love the idea of FaunOS so i'm keen to see it running. 

> ** Have your own community**

Totally agree....

---

### Post by DJiNN on 2008-02-02
> **jseiser said:**
>  I would love to throw ubuntu on a computer and walk away and let some person use it, but i keep getting people who have PC's that are pretty old, have windows XP on them, and just crawl around.  I dont want to give them ubuntu and say, its really pretty BUT, its going to be as slow as windows, if not slower.  So consider this not a ubuntu diss, but a way to enable old  hardware to perform and grow.  This is going to be my DSL linux type project.  I think the main thing that could  help this be worth using is avoiding gnome or KDE libraries like the plague.

Yep, i know what you mean. Ubuntu (et al) is a great distro, and works well on most computers, but not so well on older (PII's & PIII's etc) machines. It can work well if it's set up properly, but of course that's what you're setting out to achieve OOTB as it were, but with Arch. 

As for the KDe libs etc, maybe even stick with one or the other, or just go the GTK way & have nothing to do with Gnome or KDE...... but you'll as likely have a few probs with network browsing, as many low end distros do. Those that use Thunar (Xubuntu for instance) often have the speed & light foorprint, but at the expense of some other things. 

I have loaded several lightweight distros onto older PC's that i have here, only to find out that setting up Network browsing is such a pain, it's easier to just grab the KDE base libs (including Konqueror - Which is fabulous) and that takes care of so many things. :)

It's quite surprising at just how fast an older machine can be though, even with the KDE base libs etc.... it can still perform well, providing it has enough RAM......

But whatever you do & however you do it, i wish you luck, and i think that it's totally achievable with a modern Linux. Hard work though!

---

### Post by jseiser on 2008-02-03
ive got it set up, its not perfect, but once i get mklarch to make this a livecd :) it will cut off 90% of my config time when setting up anew machine.  Install, add user, set up ALSA and DHCP.  both are easy.  dhcp is just editing one line in rc.conf. Alsa is just adding the new user to the audio group.  With everything running, its .7% of my processor, and using 24mb's of ram.  I would say thats pretty good.  Considering im surfing the web, on irc, and listening to music.  Just to see how people like this, i want to list the programs that are being used. Programs ain ('s are also installed.

Web Browser - Kazehakase (elinks)
Chat - irssi (pidgin, xchat)
ssh/ftp - Gftp
images - mirage
movies - vlc (mplayer + mplayer-plugin for movie sin browser)
audio - mpd/ncmpc
volume - Alsa mixer in the OB menu
terminal - urxvt
P2P - rtorrent ( gtk gnutella)
File Manager - mc-utf8 (emelfm2)
Tools - Htop, Pyburn, xarchive
Editors - epdfview, leafpad
ob menu - obmenu
gtk themes - gtk-chtheme
obconf - openbox themes
wallpaper - nitrogen

I wish i could make nitrogen only load images in a certain directoy though.  I would much rather have a front end for feh. :/

Any other ideas that im missing, that people do on their computer?  This comes ready to surf the net, download music, look at pictures, pdf files. etc.  I was thinking abou tinstalling openoffice.  But if someone wants that, it wouldnt be hard to just install and add it to the menu.  I also removed the panel.  The idea of a panel fitting in with any theme isnt going to work.  It also just wastes resources and isnt needed.  So for the sake of size, and speed, middle clicking on the mouse or alt/tab will havbe to be your panel for now :) This is all easy to change though.

---

### Post by DJiNN on 2008-02-03
That sounds great....!!  Nice selection of programs as well. I hope you're going to make an iso available for download? :)

Regarding Nitrogen, it may be worth you taking a look at TinyMe, as that uses Nitrogen with OpenBox and works really well. You can set the wallpaper dir that you want, and then that will load in whatever pics are in the dir..... 

I'd also think about perhaps adding Audacious or xmms for music. I know they're not as light as mpd etc, but they're not too heavy, look great, they're written to work well even on modest/old machines and they've very expandable. (just a thought) :)

If i can think of anything else i'll let you know, but it sounds like you have it fairly well covered. Are you going to try an install on someones machine soon? I'd be interested to hear how it goes. :)

---

### Post by K.Mandla on 2008-02-05
> **jseiser said:**
> I wish i could make nitrogen only load images in a certain directoy though.  I would much rather have a front end for feh. :/
feh is a front end for feh. Check this out:

[http://kmandla.wordpress.com/2007/04/28/browse-and-set-wallpaper-in-openbox-with-feh/](http://kmandla.wordpress.com/2007/04/28/browse-and-set-wallpaper-in-openbox-with-feh/)

By the way, if you get this into a manageable shape, I'd love to give it a try. :D

---

### Post by Tenken on 2008-02-06
Thanks for info, nice and simple and works great.

---

### Post by jseiser on 2008-02-06
I have the enviroment set up, created my live cd, and ended up with a iso about 100mb to large for a cd.  Something smells wierd though, since the prgorams i have installed should not be that large.  Im going to have to go through and figure out what im doing to make this so large.  Kmandla, i was waiting for you to see this thread and offer some help :) i only know of arch from your blog.

wow, feh -g 640x480 -d -S filename /home/kmandla/wallpaper/, that will so replace nitrogen.  Thanks for that :)

---

### Post by mips on 2008-02-06
Arent things usually compresed on a livecd?

---

### Post by K.Mandla on 2008-02-06
> **DJiNN said:**
> I'd also think about perhaps adding Audacious or xmms for music. I know they're not as light as mpd etc, but they're not too heavy, look great, they're written to work well even on modest/old machines and they've very expandable. (just a thought) :)
+1 to Audacious; I use it on machines as slow as 550Mhz on a daily basis, and it's not a drag at all. 

If you want something even lighter than that though, [Alsaplayer]("http://www.archlinux.org/packages/search/?q=alsaplayer") is in Extra, and is a great little audio machine that's strictly GTK2. And don't forget that mplayer can play audio files from the command line ... but that's uncivilized. :D

---

### Post by jseiser on 2008-02-07
didnt have time to work on it last night, or tonight , most likely the weekend is going to be when i get this done.  I think my problem with size, was the pacman cache.  Im going to wipe everything, start the install again, and just set up a root desktop.  So you log in and then create your user.  everything will get moved over to the new user and be good to go.  I am removing nitrogen and mirage.  No need for them since i can use feh for both of these.  I think im going to keep mpd, if i could get it to instal and work, i would use cplay.  it is lighter, and has a easy to use layout.  The main goal for this project now, besides getting it useable, is to port over the scripts from absolute linux, Paul, the creator, has already created adduser python programs and different things like that, one programs lets you choose your dameons etc.  This will also help with setting up and running the machine.

ive never actually created a root desktop though.  i will have to figure out where the root account sets up their files.  Like the xinitrc file, and their default openbox menu.  Since normal users things go in their folder. Im wondering if i just stick the .xinitrc right inside the / folder.  I would then stick the openbox folders in /.config/openbox.  If this gives me problems, ill just set up a normal guest account as well and just skip setting up the root account.  it just sucks their wil lbe a user 'guest' that the normal user will probably delete anyways.  Would rather not even include it.

---

### Post by Changturkey on 2008-03-02
Is this dead?

---

### Post by jseiser on 2008-03-06
im still trying to get it working, Havent been able to get the mklarch scripts to work for me.  Just got a new pc, so i might be able to set something up, everything was done and working, except for handling the users properly, so i tried to re-do it, and now mklarch wont install.. its something im doing, but Im trying to get it going.  Ended up cutting out most of the GUI apps all together, since they arent as good as the CLI ones.

---

### Post by DJiNN on 2008-04-02
How's it going with the Arch project?  I've just beem playing around with Arch some more, and while i love the flexibility of Arch, it's still quite a steep learning curve. 

Also, i've just downloaded the new Arch iso's and am contemplating having a go at the 64bit version..... I'm not 100% sure that it's worth all the effort though, especially as the 64bit version of Xubuntu (Hardy Beta - Upgrade) works fine, with the caveat of a few nigglies that needs sorting. :)

Anyway, hope the project's coming along, and when you get 5 mins post the latest here if you can.

---

