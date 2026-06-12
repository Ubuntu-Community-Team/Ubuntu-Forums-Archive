---
title: "Starcraft in MoL"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by Ryan Marcus on 2006-09-06
I've got one major complaint about Linux... I have to launch MoL to run Starcraft, but I survive. I've even got a wacky PHP/SSH/REALBasic scripts set up so I can run Starcraft from my Applications menu, but thats not the point.

Now, I want to play Starcraft in fullscreen mode. When I don't run MoL in fullscreen (I have x-video turned on) Starcraft just resizes the MoL window. When I run MoL in fullscreen mode (x-video turned off) it simply puts a think black border around my Starcraft window!

I turned on zooming within Mac OS X, just to find the mouse moved whenever it bumped a corner, so thats not an option.

I hope I've explained my problem well, let me know if anything is unclear.

---

### Post by QwertyDitto on 2006-09-07
SC ROX no really it does
although not related to this problem...:D

---

### Post by sekre on 2006-09-07
This is not a solution to your problem,
but I was curious what MoL stands for?

And yes of course, SC is gooooot. Especially the movies, oh I love the last one in Protos campaign. Got to try and find my disc....I wonder where it might be, hm..:-k

---

### Post by Ryan Marcus on 2006-09-07
Arg... somebody has got to know how to do this..

---

### Post by skymt on 2006-09-07
Correct me if I'm wrong, but doesn't Starcraft only run in 640x480? Try changing your resolution and then open it in full screen mode.

---

### Post by SWedd on 2006-09-08
I'm pretty sure I have run Starcraft in full-screen mode under MoL. Have you tried running SC in window mode, and then using the keyboard shortcut to change to full-screen?

I'll double check this when I get a chance, but I don't think I have experienced your problem.

---

### Post by QwertyDitto on 2006-09-08
:-k MOL stands for mac-on-linux btw...

---

### Post by SWedd on 2006-09-08
Yeah just tested it then and it works fine for me. I start in a window and then change to full-screen before running starcraft.

If that doesn't work maybe try running molvconfig again and check your settings.

---

### Post by andb on 2006-09-08
your starcraft copy is mac? Why not just use the pc version under Wine, which works fine? You can always get a torrent for starcraft and use your serial from the mac product to get on battlenet.

---

### Post by QwertyDitto on 2006-09-09
Want a call from the friendly cops?
Have fun in jail  :mrgreen: :mrgreen: :mrgreen: ;)

---

### Post by 3rdalbum on 2006-09-10
> **andb said:**
> your starcraft copy is mac? Why not just use the pc version under Wine, which works fine? You can always get a torrent for starcraft and use your serial from the mac product to get on battlenet.

What a loser. And what a |\|00|3 too. You can't run WINE on PPC; well, let's just say if you ran Starcraft on Wine on QEMU on PPC it wouldn't be playable :-)

---

### Post by Ryan Marcus on 2006-09-10
Thanks for letting people know you can't run WINE on PPC... I'm not even newbish enough to think that.

Yes, if I could get my MoL to switch to 800x600, it would work. But I can't. Thats the problem. I guess I'm stuck rebooting.

---

### Post by SWedd on 2006-09-10
> **3rdalbum said:**
> You can't run WINE on PPC; well, let's just say if you ran Starcraft on Wine on QEMU on PPC it wouldn't be playable :-)

hehe I once ran starcraft on a QEMU win xp install (for some reason my SC CD didnt have a mac version on it) and it was surprisingly playable. That is, I could play the first single player mission without going insane at least.

> **Ryan Marcus said:**
> Yes, if I could get my MoL to switch to 800x600, it would work. But I can't. Thats the problem. I guess I'm stuck rebooting.

Can't you configure your video modes in molvconfig? Also, did you try running in a window and then changing to full screen via keyboard shortcut?

---

### Post by Ryan Marcus on 2006-09-10
I tried Qemu, but I'm on a 1 Ghz single processor... not a chance of it being playable.

I've ran molvconfig and answered everything correctly. When I run MoL with X11 off (in full screen mode) I only get one resolution... Its above 1000x1000. When I run MoL with X11 on (windowed mode) I get quite a few resolutions, but when I change the resolution, it just changes the size of the window.

I've tried switching from windowed to full screen. It remains in its small little box surronded by black.

---

### Post by ryan86corolla on 2006-09-11
I am trying to play Starcraft in MoL as well, but I can't play games on Battlenet because "port 6112 isn't accepting UDP." Or "my internet connection is very poor," but I don't think that's the case since I can browse at normal speed in Camino.

I imagine there's some MoL config file somehwere I can edit to open the port I need...but I googled it for a while and couldn't find anything even remotely related. Did it just work for you? Any advice on what I can do to fix it? Thanks!

By the way, for full screen I have to hit ctrl-alt-f8 to go full screen and then ctrl-cmd-f7 to exit. This works whether Starcraft is running or not. It seems that somehow the alt and cmd keys switch functions depending on the screen mode...like to copy and paste I have to use alt-c and alt-v in windowed mode, but cmd-c and cmd-v in fullscreen. I guess the cmd key just gets stuck sometimes. Switching back and forth between screen modes seems to alleviate this...sometimes.

---

### Post by SWedd on 2006-09-11
> **Ryan Marcus said:**
> I've ran molvconfig and answered everything correctly. When I run MoL with X11 off (in full screen mode) I only get one resolution... Its above 1000x1000. When I run MoL with X11 on (windowed mode) I get quite a few resolutions, but when I change the resolution, it just changes the size of the window.

Except for the only one resolution in full-screen bit, that sounds the same as my system.

> **Ryan Marcus said:**
> I've tried switching from windowed to full screen. It remains in its small little box surronded by black.

Damn ... that just doesn't happen for me. Really wish I could help. Are there any settings in particular I could check for you?

If it helps I am pretty sure my default (windowed) resolution for MoL is 800x600.

> **ryan86corolla said:**
> I am trying to play Starcraft in MoL as well, but I can't play games on Battlenet because "port 6112 isn't accepting UDP." Or "my internet connection is very poor," but I don't think that's the case since I can browse at normal speed in Camino.

Sounds like you just need to open port 6112 in your Apple firewall and (if you have one installed) also your ubuntu firewall. (Port 6112 is necessary to use battle.net)

If that doesn't work I think there is a config file somewhere that defines port forwarding between ubuntu and OSX, but damned if I can remember anything about it now. :(

---

### Post by ryan86corolla on 2006-09-12
> **SWedd said:**
> Sounds like you just need to open port 6112 in your Apple firewall and (if you have one installed) also your ubuntu firewall. (Port 6112 is necessary to use battle.net)

I can play fine when booted into OS X so it's not that firewall, but I hadn't looked at Ubuntu's firewall yet...I'll try that and let you know how it goes.

Do you think you could share that script you mentioned at the beginning of the thread? I would surely use it. :)

Edit: So I'm not an idiot, Ubuntu has no firewall installed by default. I installed firestarter from Universe and looked around but couldn't find an settings dealing with ports. I also looked in Network Tools but couldn't find anything there either. If it's even an issue without a firewall (i turned Firestarter's off once I got done with it), where can I look to change port traffic configurations?

---

### Post by SWedd on 2006-09-14
> **ryan86corolla said:**
> Edit: So I'm not an idiot, Ubuntu has no firewall installed by default. I installed firestarter from Universe and looked around but couldn't find an settings dealing with ports. I also looked in Network Tools but couldn't find anything there either. If it's even an issue without a firewall (i turned Firestarter's off once I got done with it), where can I look to change port traffic configurations?

Sorry no good news from my end. I've checked up on my mol configuration and can't find any files that define port forwarding between ubuntu and OSX. It just works for me :confused: I've logged on to battle.net and sat in chat before (though admittedly not joined a game. I'll try that now).

I assume you set up your tun0 interface as described by the [howto]("https://help.ubuntu.com/community/MacOnLinuxHowto#head-11a36cac4a033ef4bef636c1979016be90ac89b8")?

Edit: OK just tried it then and yes I could join a game with no problems. I havent done anything special except follow the instructions in the howto. (except a minor tweak to stop ipmasq screwing up my internet in ubuntu - I turned it off by default so that it only runs when running mol... but pretty sure it worked before I did that too)

---

### Post by ryan86corolla on 2006-09-14
Well, thanks a ton for all your help. I did indeed set up networking as described in the howto, and a) my networking in ubuntu hasn't been affected by ipmasq, b) everything else involving networking works fine on MoL, and c) I can play games on battle.net when booted into Mac OS X just fine. From MoL, I can chat but not join or create games. I suppose I'm out of luck at this point.
I might try reinstalling maconlinux and reconfiguring networking from the ground up just to see if I messed something up somewhere. If it just worked for you, perhaps I'll get lucky as well. I'll let you know how it goes.

---

### Post by Ryan Marcus on 2006-09-15
Yes, I could get SC to a playable size, buy my Ubuntu system only seems to support one resolution.

As for your problem, you should try downloading my bot, Luxer: [http://luxer.cjb.net](http://luxer.cjb.net)

If you can get it to connect, then you know there is nothing wrong with the connection. If not, you've got some networking problems within MoL.

As for me, I think I'm stuck.

Also, my scripts consist of a shell script that looks like this:
```

wget http://example.com/rmarcus/molconfig.php?txt=SC
rm ~/molconfig.php?txt=SC
startmol --osx

```

Then I created a REALBasic application and set it as a startup item. The PHP script at the URL sets the content of a text file on the server. The REALBasic application looks at that text file and opesn SC on it own. I set up a similar system for opening RB and Photoshop.

---

