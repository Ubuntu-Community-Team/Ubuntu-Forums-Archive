---
title: "installing kiba in fiesty?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-27
Hi! this guide seems to be great but it also seems to be broken temporarily:
[http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)
Does anyone of you know how to fix it? Or is there any other noob guide out there?

James

---

### Post by starcraft.man on 2007-04-27
Ummm... I think most of the dock projects are either unstable or abandoned... truth is they really just eat up your cpu cycles. It's much easier just to drag a program from your menu to your upper taskbar. or right click and Add to Panel.

---

### Post by the_axiom on 2007-04-27
I got enough cpu/ram power, it would be sad to not use it =D
Tell me!

---

### Post by starcraft.man on 2007-04-27
sigh, ok... if you absolutely need one I guess the kooldock is the one I've heard the most positive reviews for. Its available in the repos, I think Edgy and Feisty.

```
sudo aptitude install kooldock
```

Theres the code for installing, I take no responsibility for anything that happens to your comp as a result, nor do I know how to tweak it specifically.

If your into eyecandy you might also wanna look at beryl, that I can vouch runs very stable now that its 2.0

---

### Post by the_axiom on 2007-04-27
Yes its quite obvious it's my responsibility =D.
Thank you for your tip, but I have allready beryl installed.

After I've typed your code in the terminal, how do I run it?
Excuse me but I'm a noob, hope I didn't bother you to much.

James

---

### Post by starcraft.man on 2007-04-27
> **the_axiom said:**
> Yes its quite obvious it's my responsibility =D.
Thank you for your tip, but I have allready beryl installed.

After I've typed your code in the terminal, how do I run it?
Excuse me but I'm a noob, hope I didn't bother you to much.

James

LOL, thats funny... Naw, ya dun annoy me, I always help people with a smile no question is stupid. Also incase ya didn't notice I only been on these forums since March :p (one month before ya). I guess I'm just a quick study with Ubuntu though, I know how to do lots of things already and still learning. 

To run kooldock, I assume like most every program installed via the repos you can just type in kooldock in the terminal. Also is ya wanna set it to run every start up System > Sessions. Then push add program to startup tab and type in the same command "kooldock".

That can be used for almost every other program you'll ever encounter.

Have fun.

---

### Post by the_axiom on 2007-04-27
[IMG]http://i11.tinypic.com/2u9077s.jpg[/IMG]
Didn't look to good. It leavs ugly traces after itself. But it's no problem just to uninstall it. =D
How do I get the applications from [http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645) to work?
It may be unstable, but I've got nothing to lose. The worst thing that could happen is that I need to reinstall Ubuntu.

---

### Post by starcraft.man on 2007-04-27
Seeing as I've never really installed Kiba... I can only direct you to the official Kiba place which I glanced over a few weeks ago and tell ya to register and look in the wiki section for installation help.

Link [Here.]("http://www.kiba-dock.org/")

Hope that does it for ya... tell me how it works out.

---

### Post by xpod on 2007-04-27
If and when you get fed up of the kiba-dock thing you can always just make your bottom panel look dock-like

[http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx/3/](http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx/3/)

I only keep kiba cause my 2 Yr old likes to click the icons and make em bounce.......honest:)

---

### Post by starcraft.man on 2007-04-27
> **xpod said:**
> If and when you get fed up of the kiba-dock thing you can always just make your bottom panel look dock-like

[http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx/3/](http://www.supriyadisw.net/2006/09/ultimate-ubuntu-dapper-look-like-osx/3/)

I only keep kiba cause my 2 Yr old likes to click the icons and make em bounce.......honest:)

ROFL... why do I find that so believable? :p

Nice link though, heh, maybe I will try one...

---

### Post by the_axiom on 2007-04-27
Got it to work at last with following guide: [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)
But anyone have a clue how to get the "addons" that make it bounce and crap like that? =D

James

---

### Post by starcraft.man on 2007-04-27
> **the_axiom said:**
> Got it to work at last with following guide: [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)
But anyone have a clue how to get the "addons" that make it bounce and crap like that? =D

James

I thought bouncing was built right into the main program >.<, sorry, thats the end of my knowledge. It doesn't list any instructions in the wiki for an addon?

---

### Post by jiminycricket on 2007-04-29
Is it just me?  Kooldock is completely glitchy on my computer, if I try to scroll over the icons, the backgorund gets completely corrupted.  I can't find kibadock.  I can't get any docks to work properly in Feisty.

And kxdocker won't start, it crashes with this:
```
$ kxdocker
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-10286' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.


```

---

