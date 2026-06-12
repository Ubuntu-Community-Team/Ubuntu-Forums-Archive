---
title: "Almost like I have two user accounts which randomly load!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Jofaba on 2007-08-10
I started my computer and all the work I did last night is gone! 

I did a lot of setup last night on a new install. But this morning when I started up, everything was gone. This happened once while I was having a problem installing nVidia drivers but it wasn't that big of a deal at the time because I didn't have any customization yet.I thought my general user settings had just been reset because I rebuilt my xorg.conf through:

sudo dpkg-reconfigure -phigh xserver-xorg

The odd thing is, the stuff that loaded up this morning are actually THOSE Lost settings. All of my customization from last night after losing those and starting over, including Firefox bookmarks, are gone. The bookmarks from when I was looking up Ubuntu help are all back, my Kmenu is back to what it looked like at that time, and all my customization, such as wallpaper, are back to the defaults (or what I had from that first loss). 

What causes this to happen? And how do I get back to what I had last night? 

I'm running Kubuntu 7.04 with Nvidia and Compiz Fusion. There were some errors that occured when I shut down last night but I was tired and don't remember what they were. 

Any help on this perplexing problem would be extremely appreciated!

---

### Post by Jofaba on 2007-08-10
Well, KDE is really pissing me off. While I prefer the KDE programs, the community support just isn't there. What I mean, is that the further programs and support don't exist. Almost all code help is in gnome and you have to try to translate it, plus; kde just sort of sucks. It's not stable. Everytime I change something it crashes. 

That said, I hate gnome. It may rock as far as "working" but the programs suck. They lack very basic things for a person coming from Windows. And i hate Windows. 

I'll be doing a new system with Gnome only, and trying to find programs that I like and can replace the kde programs I enjoy. KDE is out for me though. I actually don't want help with this problem because I'll be going back to gnome and seeing what I can do. 

I hope none of this sounds angry or off. I'm just explaining why I'll be going back to gnome. I sorta wish I had an ATI pcie card to work with. I"m actually thinking of going back to my agp system for my next setup because I have an agp videocard. Crazy!!

---

### Post by vexorian on 2007-08-10
> hey lack very basic things for a person coming from Windows like what?

Your issue is very strange actually.

BTW the only significant differences between most howtos from ubuntu into kubuntu would be:
- replace gedit with kate
- replace synaptic with adept
- replace terminal with Konsole
- replace gksu with kdesu
- replace nautilus with konqueror

...
If you really like KDE apps (and I do like a couple of them) but can't extand KDE itself, then I think you should try installing the apps in gnome, the only issue would be looks, I think I can get to configure a qt theme in gnome, let me do research...

---

### Post by Jofaba on 2007-08-11
I think a lot of my problem is that I'm trying to jump straight into linux without learning the ins and outs first. I need to research which environment works best for my needs, then figure out how best to apply the settings. What I'm looking for in the end is:

Customizable appearance. Theming ala "Windows Blinds"
Stability (except for when Compiz is enabled obviously)
Photo galleries with thumbnails that are sortable by various means and viewed in order of sortation. 
Video galleries with the same abilities (including thumbnails)
The ability to access the NTFS partition on my drive. Have read/write capabilities. (One thing that's annoying about Kubuntu is that Konquorer doesn't automatically open in Root mode).

As far as this particular problem (the one I created this thread over) it certainly is strange. As the saying seems to go, if your linux is screwed up, you probably made a mistake. I still equate Root with Administrator rights. I'm not used to making changes that can literally kill your OS, or at least temporarily cripple it until you can research a fix. 

I hate Windows and hope my drunken rant last night didn't make me sound like your average "why can't linux be like Windows!" rant. I have a dual core SLi gaming computer that rated around 10k in 3dMark06, but Windows has aggrivated me enough to basically toss all that in favor of Ubuntu. 

I love Ubuntu. I talk about it all the time at work and am always reading up on new stuff. I am computer savvy. It's just aggrivating that small seemingly easy-to-impliment stuff is still not quite there. 

I now see that nVidia is a pain in the butt to deal with. If I can get my old agp gear to handle Compiz and peform well enough then I'll switch back to ATI for a while and try to sell my nVidia and watercooling gear. I'm not giving up on Ubuntu at all. 

Thanks for your reply to my otherwise childish rant =)

---

### Post by macdo on 2007-08-11
> Photo galleries with thumbnails that are sortable by various means and viewed in order of sortation.

You could try digiKam (K->Graphics->DigiKam). Or Picasa works just fine on (K)ubuntu ([http://picasa.google.com](http://picasa.google.com)). Konqueror even integrates a tool to make html galleries, if that rock's your boat. (Tools-> Create Image Gallery)

> The ability to access the NTFS partition on my drive. Have read/write capabilities. (One thing that's annoying about Kubuntu is that Konquorer doesn't automatically open in Root mode).
You need to install ntfs-3g. 
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

You can start konqueror as root; I'm just not sure why you'd want to on a regular basis. Use alt+F2, then ```
kdesu konqueror 
```

There is definitely a learning curve associated with linux. And I totally grok your frustration!

macdo

---

### Post by Jofaba on 2007-08-11
As "odd" as this problem may be, it's actually happened again. I'm, for the first time, having a very difficult time installing compiz fusion. And I just noticed that all my firefox settings, including bookmarks and quicklinks are gone, just like I had with kubuntu.

---

### Post by Jofaba on 2007-08-12
For NTFS I went to that link and replaced "edgy" with "feisty" in the repository adds, but came out with this

> Err [http://flomertens.keo.in](http://flomertens.keo.in) feisty/main Packages                              
  404 Not Found
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) feisty/main Packages           
  404 Not Found
Ign [http://flomertens.free.fr](http://flomertens.free.fr) feisty/main Packages                   
Err [http://flomertens.keo.in](http://flomertens.keo.in) feisty/main-all Packages                
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) feisty/main-all Packages              
  404 Not Found
Ign [http://flomertens.free.fr](http://flomertens.free.fr) feisty/main-all Packages                      
Err [http://flomertens.free.fr](http://flomertens.free.fr) feisty/main Packages    
  404 Not Found
Err [http://flomertens.free.fr](http://flomertens.free.fr) feisty/main-all Packages
  404 Not Found
Fetched 4B in 1s (2B/s)
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.free.fr/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://flomertens.free.fr/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.free.fr/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz](http://flomertens.free.fr/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'll look for an updated version of how to add that

EDIT: I checked add/remove and indeed there is an ntfs configuration tool. I'm going to try that. I'm looking at cleaning up the Windows XP folders and files so that just the media and files I want to keep are there, then I'm going to start experimenting with wine to see which games I can get running (if any).

---

### Post by Jofaba on 2007-08-12
Okay this problem occurs everytime I restart my computer. None of my stuff is saved! It all goes back to the first setup I had before losing it. Can anyone help me here? How do I save my settings so that when I reboot my computer they're exactly as they were the last time I left?

I keep losing all my bookmarks! I keep losing everything!

EDIT: Even my compiz settings reset back to the default. But Wine is still installed, and the changes I made to my ntfs drive are still there. But absolutely all customization in firefox and ubuntu revert back to defaults. It's really getting annoying because I keep losing important bookmarks, plus who want's to customize their computer and lose it everytime they reboot?

---

### Post by Jofaba on 2007-08-12
Apparently it also resets all my program settings. I just went to go listen to a cd and had to remap my music location. I really hope someone has a fix for me. This is so frustrating.

---

### Post by p_quarles on 2007-08-12
As someone pointed out above, this is indeed a strange problem. I've never encountered it (or even heard of it) before, so I don't know how much I can help.

That said, here's what I would do: make a minor edit to a configuration file, like adding a comment line. For example:
```
kate /home/username/.config/menus/applications.menu
```
Then, add the following somewhere in that file:
```
# test
```
Save it, reboot the computer, and reopen the file. Is the added line still there? 

I don't know how much good this will do, but if the file reverts, that could point us in the right direction. 

Other tips:
1) Make sure that you run the text editor from the terminal, and watch the terminal for any error messages, especially when you save the file.
2) I'm using Gnome, so I'm not sure my example file will exist in KDE. Just find an equivalent.

---

### Post by Jofaba on 2007-08-12
Actually I'm on a new install and using Gnome now. I won't be going back to KDE. Sure, the programs are nice, but the rest of it's a headache. 

It very much feels like there's multiple user accounts. Like, lets say I had 3 accounts. Depending on how I logged in, I'd be brought to those settings. It's not even so much that "all my settings are being reset". I'm being brought back to a previous environment. I've got the bookmarks from when I was installing nvidia drivers. 

I've found other people with similar problems but no fix. The threads just lose activity. 

The only thing I can possibly think of is that I'm usually running Compiz when I do all my settings. Could it be that running in Compiz doesn't save the settings to gnome? 

Unfortunately I'm in Compiz right now as well, but I will try making some changes in both environments and seeing which, if any, settings stick.

---

### Post by Jofaba on 2007-08-12
One thing I do notice, is that there are errors when I shut down. X fails on "restart" and "shutdown" as well as "logout". I can get back in with "startx" and can turn the computer off (i forget which command works, reboot, restart, shut off, etc) but yeah, there are errors.

---

### Post by annda on 2007-08-12
> **Jofaba said:**
> One thing I do notice, is that there are errors when I shut down. X fails on "restart" and "shutdown" as well as "logout". I can get back in with "startx" and can turn the computer off (i forget which command works, reboot, restart, shut off, etc) but yeah, there are errors.

this may be a compiz problem but i don't think disappearing configurations are. but have you tried disabling it anyway, rebooting, making some changes to the system and/or disk and rebooting again?

are you (temporarily) losing only configuration changes, or other things as well? i mean created/downloaded files etc. also, does it happen after every reboot or only occasionally?

as to multiple users hypothesis, i suppose you have checked that neither in /home or in system>administration>users and groups there any pseudo duplicates...

---

### Post by Jofaba on 2007-08-12
There's only one user. I checked as soon as I got the feeling something like that may have happened. 

I just restarted and nothing's lost from what I was doing, so it's not always happening. But it's happened a few times now and I in no way feel confident that it's magically fixed. 

I'm now about to start all over and set up ubuntu and compiz the way I want to. I'll update as soon as everything's lost again =(

---

### Post by p_quarles on 2007-08-12
When you say it's like having multiple users, do you mean that sometimes the settings would reappear? Or, did they just disappear for good? 

I think it's entirely possible that Compiz is involved here. If it's causing X to fail on shutdown, and then this is leading to problems with the shutdown sequence, I can imagine that this would cause settings to be lost. The only way to rule it out would be to try to get this problem to replicate itself while Compiz is out of the picture. If that happens, at least you'll know Compiz isn't the problem.

---

### Post by Jofaba on 2007-08-12
Lately, the error on closedown hasn't repeated itself. But I'll run without compiz for a day or two to see what happens. I finally got Steam working, so I'll be playing around with Wine gaming for the next couple of days anyway, and have no need to run compiz (it'd probably get screwed up anyway). 

Thank you for your help and please check back in a couple of days to see how I'm doing =)

---

### Post by Jofaba on 2007-08-15
So far so good the past couple of days. Ever since the error problem that occured at shutdown stopped, so did the resetting of my personal settings. It's still scary that some conflicting software could completely reset my computer though. That seems a hell of a lot more dangerous than anything Windows has thrown my way. 

I know that Compiz is beta and considered "use at your own risk" but I just figured that meant my computer could crash at any moment. I figured if I had to do important work I could just type in "metacity --replace" and go back to a stable linux environment. Am I wrong in that assumption? Can Compiz also attack the rest of my linux install and make the entire OS unstable?

---

### Post by p_quarles on 2007-08-15
Well, it's not "attacking" the OS so much as it's just screwing around with the X server settings. Usually it doesn't do any thing like this, and I'm still not 100% convinced it was even the problem, but chain reactions can and do happen and can seriously screw with a system. 

Do you have an ATI graphics driver, by any chance?

---

### Post by mdsmedia on 2007-08-15
I'm sorry I can't offer any advice, but just congratulate you on your attitude and attempts to get to the bottom of your siuation.

I've been using Ubuntu for nearly 2 years, fresh out of XP, and I've never had any sort of problem the way you have, so I would not blame Linux/Ubuntu for the problem. It may well be Compiz. I've never installed it because I thought my laptop's video capabilities probably wouldn't handle it.

I find the problems I had with XP were more than enough reason to TRY Linux. (I really didn't need too much of an excuse) And I find that the Linux experience is far more rewarding than staying with Windows.

Once again, I applaud your continued attempts to get to the bottom of your problem, rather than throwing in the towel and going back to "what works". Because i find "what works" really doesn't work all that well and once the solution is found in "what really works" it works much better than "what works" anyway.

---

