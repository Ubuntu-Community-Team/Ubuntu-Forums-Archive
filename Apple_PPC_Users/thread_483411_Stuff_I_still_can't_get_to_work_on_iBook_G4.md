---
title: "Stuff I still can't get to work on iBook G4"
date: 2007-06-24
forum: Apple PPC Users
---

### Post by bogoliubov on 2007-06-24
Hello. I'm quite satisfied with how Ubuntu on PPC is shaping up. And I've followed some guides and done some tweaks so most stuff works OK. But there are some things I really need help with:

-> When wakening from sleep, the "tap" option is selected for some reason!

-> The wireless connection is a bit unstable. And when it goes down, I have to restart the router!

-> Flash player. Should I use Swfdec or Gnash or what? How to install latest versions?

-> Support for Non-power of 2 textures from Radeon driver.
    Needed for, amongst other things, Sauerbraten.


-> Sound. It works, but it is not very good compared to what OS X produces.

-> Does all multimedia codecs work?

-> Optimization of Radeon OpenSource driver. It's much slower than the proprietary one (in OS X),

-> TV out! I have managed to get external monitor working in clone-mode, with different resolutions on the two monitors and also I have managed to get external only working. 

-> Easy switching between different Xorg.conf versions. Or, preferrably, just close the lid, connect external monitor and open again; like in OS X! 

-> Skype. I don't really like Skype since it's protocol is closed and the program is proprietary, but it's hard to convince all my friends to use Wengophone or something similar...   But I guess this one is unsolvable.

---

### Post by stmiller on 2007-06-24
See if the PowerPCFAQs can help with some of your questions:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

You can switch easily to an external display, but no need to close the lid. Once you have the xorg file all configured, you just hit Control+Alt+Backspace[Delete key] to restart X.

There is no Skype for PowerPC Linux, unfortunately.

Read the many Gnash threads in this ppc forum section. A new version just came out.

I haven't come across any multimedia thing I couldn't play so far. This includes any HD online content, trailers at gametrailers.com, and other things. Some particular flash video sites will not play, though.

---

### Post by bogoliubov on 2007-06-25
> **stmiller said:**
> You can switch easily to an external display, but no need to close the lid. Once you have the xorg file all configured, you just hit Control+Alt+Backspace[Delete key] to restart X.
.

Yeah, that I knew. But I don't consider it very simple. At least not compared to what you do in OS X...

Thanks for hepling out!

---

### Post by Sodki on 2007-06-27
Hello, I'm a Gentoo PPC user, but an Ubuntu fan, so I'll try to answer a few of your questions (and ask some, too). I'm sorry about all the "it should work in Gutsy". :)

> **bogoliubov said:**
> -> When wakening from sleep, the "tap" option is selected for some reason!
Where do you set the "tap" option?

> The wireless connection is a bit unstable. And when it goes down, I have to restart the router!
I believe things should be better in Gutsy, because of some patches that went into Linux 2.6.22.

> Flash player. Should I use Swfdec or Gnash or what? How to install latest versions?
I prefer Gnash. The latest Gnash, the one that supports YouTube, is already in Gutsy.

> Support for Non-power of 2 textures from Radeon driver.
    Needed for, amongst other things, Sauerbraten.
Sorry, don't know anything about this.

> Sound. It works, but it is not very good compared to what OS X produces.
Have you configured it in "volume controls" or alsamixer? Sometimes the bass and treble are on their lower values and this produced a lousy sound. Try setting them up at 60%.

> Does all multimedia codecs work?
Not quite, but it's not that bad. Your best bet is using VLC to play video files. It's the only one I know that is capable of playing newer WMV files.

> Optimization of Radeon OpenSource driver. It's much slower than the proprietary one (in OS X),
The radeon guys do what they can. Resources, like specs, are limited. :)

> TV out! I have managed to get external monitor working in clone-mode, with different resolutions on the two monitors and also I have managed to get external only working. 

-> Easy switching between different Xorg.conf versions. Or, preferrably, just close the lid, connect external monitor and open again; like in OS X!
I hope this gets fixed in Gutsy. The next Xorg version will be capable of output device hot plugging, so things should work like in OSX. Unfortunately, I don't know if this will be ready for Gutsy or not.

> Skype. I don't really like Skype since it's protocol is closed and the program is proprietary, but it's hard to convince all my friends to use Wengophone or something similar...   But I guess this one is unsolvable.
Yes, this one is unsolvable, at least for now. Proprietary obscured protocol, etc, etc.

---

### Post by bogoliubov on 2007-07-08
Hello. I'm on vacation, so I haven't been able to access internet for a while.
But great thanks for your reply, all help is appreciated!

By the way, how does Ubuntu compare to Gentoo on the iBook (or PPC version in general)?

---

### Post by bogoliubov on 2007-07-08
> **Sodki said:**
> 
Where do you set the "tap" option?



Actually, I don't know. I'll have a look at it, and I'll let you know.

---

### Post by stmiller on 2007-07-08
Hey I used to run Gentoo on my Powermac G5. It's great, but takes more effort at the beginning to get everything set up. There are good Gentoo docs to walk you through an install. I feel that I learned more about Linux from install/using Gentoo than from anything else previous.

You can see the status of your desired packages here:

[http://packages.gentoo.org/](http://packages.gentoo.org/)

---

### Post by Sodki on 2007-07-09
> **bogoliubov said:**
> By the way, how does Ubuntu compare to Gentoo on the iBook (or PPC version in general)?
Gentoo vs Ubuntu on PPC is like Gentoo vs Ubuntu on x86, really. It is just a matter of choice, of which distro you feel most comfortable with.

---

### Post by bogoliubov on 2007-07-10
> **Sodki said:**
> 
Where do you set the "tap" option?


It's set in /etc/pbbuttonsd.conf , which is edited by running powerprefs (as superuser).

If I do 'sudo trackpad show' it says "notap".
Then, if I set the computer to sleep, wake it up and try again, I get "tap". But powerprefs is still set to "notap"!


Any ideas?

---

### Post by Sodki on 2007-07-10
> **bogoliubov said:**
> It's set in /etc/pbbuttonsd.conf , which is edited by running powerprefs (as superuser).

If I do 'sudo trackpad show' it says "notap".
Then, if I set the computer to sleep, wake it up and try again, I get "tap". But powerprefs is still set to "notap"!
I think it might be this bug: [https://bugs.launchpad.net/ubuntu/+source/pbbuttonsd/+bug/90445](https://bugs.launchpad.net/ubuntu/+source/pbbuttonsd/+bug/90445)

---

### Post by bogoliubov on 2007-07-10
> **Sodki said:**
> I think it might be this bug: [https://bugs.launchpad.net/ubuntu/+source/pbbuttonsd/+bug/90445](https://bugs.launchpad.net/ubuntu/+source/pbbuttonsd/+bug/90445)

Ok, so I guess there isn't much to do then? Or can one set up power preferences so that a script is executed when the computer wakes up, and make the script reload pbbuttons?!

---

### Post by Sodki on 2007-07-10
> **bogoliubov said:**
> Ok, so I guess there isn't much to do then? Or can one set up power preferences so that a script is executed when the computer wakes up, and make the script reload pbbuttons?!
Yes, I believe it's possible to run a script when the computer wakes up, via HAL, but I'm not really sure how it's done.

---

### Post by bogoliubov on 2007-07-11
Ok, thanks alot for your help! 

Btw, about Gentoo. I've been thinking about trying it out, but I'm not sure how much time it will take. I use Fink unstable in OS X and installing stuff by compiling takes very long time! 
But many proponents of Gentoo says that it's very fast. But how fast compared to other Linux distros? Will it make a difference on my iBook G4?

If anyone have any more advice on the other issues I'd greatly appreciate it!

---

### Post by Sodki on 2007-07-20
> **bogoliubov said:**
> Btw, about Gentoo. I've been thinking about trying it out, but I'm not sure how much time it will take. I use Fink unstable in OS X and installing stuff by compiling takes very long time!
I would only recommend Gentoo for those who like to tinker with their operating system and have no problems breaking stuff and trying to solve it. Also, it would take longer than fink because you have to compile everything.

> But many proponents of Gentoo says that it's very fast. But how fast compared to other Linux distros? Will it make a difference on my iBook G4?
Gentoo might be 2% faster because of the optimizations, but that's about it. It's not worthy to use it for the speed. The best thing and the worst thing about Gentoo is it's flexibility. It gives you good tools so that you can manually build things your way. but if you're not into building things yourself, it can suck big time.

---

### Post by bogoliubov on 2007-07-23
Ok, so it's not worth is speed-wise. On the other hand, I guess it could be interesting to test, since it seems one can learn alot about computers/OSes by learning Gentoo.

Thanks for the help!

---

### Post by Twiggy003 on 2007-10-19
On the iBook G4 ppc, Gutsy doesnt detect the sound at all, any ideas how to get it working? it worked on 7.04, quite odd.

---

### Post by jackoverfull on 2007-10-19
if i remember correctly, you should do

```
sudo modprobe snd_powermac
```

---

### Post by Twiggy003 on 2007-10-20
Thank you, I did something similar, I added the snd-powermac to /etc/modules file.

---

### Post by jackoverfull on 2007-10-20
right: that works too. :)

---

### Post by bodobuntu on 2007-10-20
Guys, how did you please manage to get wifi working? It's driving me insane :(
It works for a distance of a meter or two from the router for me.
I'm on a ibook G4 broadcom 4318

---

### Post by jackoverfull on 2007-10-21
odd…
on my ibook the airport extreme card now works almost as it does on os x (but without encription!)…

---

### Post by rhetoric on 2007-10-21
> **jackoverfull said:**
> odd&#8230;
on my ibook the airport extreme card now works almost as it does on os x (but without encription!)&#8230;

Mine seems to randomly choose when to work. One day I was getting 500k/sec+ up and down speeds while in class, the next day I couldn't keep a connection for 60 seconds. This is using WPA enterprise though so... I haven't been able to test any other security (or lack thereof), nor have I been able to test distances from the router, because I only have wireless access at school and haven't figured out the exact location of any routers yet. God I hate proprietary drivers :/

---

