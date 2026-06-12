---
title: "Wine: sound but no image"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by anemon on 2007-01-04
Hello everyone!

I'm just starting to dabble with Wine, trying to get a good old Win 95 game running, and I've been able to handle all the minor quirks and quibbles by myself this time! ;) That is, the game is working!

Eh ... so why am I posting here?

Well, I just said it's working, I didn't say I can actually see it! I know it's working because I can hear the music in my loudspeakers, but Wine's "virtual desktop" window only displays a boring cyan which I believe is the standard background color or something. And if I move my mouse into this vast field of cyan, the pointer disappears. Wierd?

So, I try changing the graphics settings in winecfg. Doesn't help. Without the "virtual desktop" option checked, the game tries to go fullscreen and leaves me with a 640x480 version of the Gnome desktop, plus the background music. Same thing without the "let the windows manager manage your windows" option. 

What do I do? :( It's no fun playing a game without the graphics, even if they weren't that good in back in '95...

---

### Post by pseudonym on 2007-01-04
> **anemon said:**
> What do I do? :( It's no fun playing a game without the graphics, even if they weren't that good in back in '95...
What errors do you get when trying to run the game from the command line? You may just be missing a dll or two...

If you don't know already, you might also find help at [winehq]("http://appdb.winehq.org/") .

If you have a really fast machine, and the game also has a DOS mode, you can also try running it under dosbox (it's in the Ubuntu repositories).

---

### Post by anemon on 2007-01-05
I'm afraid I don't get any interesting errors, at least no missing .dll:s ... First out is a snippet about ALSA (but, as I said, the sound actually works):

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

Then comes some stuff that I don't really understand, but none of it looks too serious to me:

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16c368) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16bac0)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now
```

Could just as well be the program's idle chit-chat with itself, right?

As far as WineHQ goes, I've scavenged though their user guide and even posted to their Google list, but to no avail (i.e. no answer). So I'm stuck with you guys! Will try Dosbox, but it would sure be satisfying to solve the problem as it stands: I thought I was doing so good!

In my mind, it must have something to do with when the game tries to go into fullscreen mode. And it seems to work to, otherwise the sound would not be running, but the fullscreen ends up somewhere else. Does anyone have a clue to how Wine handles these things?

---

### Post by hostage on 2007-01-05
When i tried to install Counterstrike steam i got no text and the buttons where gone.

Then i tried to copy all the dll files from windows "system 32 " and all the FONTS and then it worked good for me.. i could play the game online perfectly. Try the same and se if it works :D

---

### Post by anemon on 2007-01-05
Hmm ... copy to where, precisely? I could give it a try, I guess, but it really doesn't sound like the same problem -- or does it? But thanks for taking the time! :)

BTW, I tried the Dosbox solution, but the game won't run in DOS mode, so ... I'll still have to come up to some solution that entails Wine.

---

### Post by anemon on 2007-01-05
Latest update: still haven't been able to solve the problem. No matter how I fiddle with the graphics settings in winecfg, I get the same results. And since the game is actually running somewhere in the background, I don't figure that the fixme messages I posted above are the root of the problem. The only good clue I've got is still the plain cyan window in the virtual desktop mode ... 

Why won't Wine display the graphics when the game is running? Why does my mouse pointer disappear when I drag it into the cyan field? 

Still don't understand a thing. Someone, PLEASE HELP!

---

### Post by anemon on 2007-01-05
Wait! There is one more thing that I just discovered. It doesn't show up in the terminal window, but if I switch to real terminal mode (Shift+Control+F1) I find the message:

```
Application tried to create a window, but no driver could be loaded. 
Make sure that your X server is running and that $DISPLAY is set correctly.
```

If this isn't what I've been looking for, I'll eat my hat. But what does it mean?

---

### Post by pseudonym on 2007-01-05
> **anemon said:**
> If this isn't what I've been looking for, I'll eat my hat. But what does it mean?
It could be related to something in DirectX that wine doesn't, or no longer, understands (regressions aren't uncommon in wine), if it ever did.

I had the same type of issues when trying to get the game MDK to work in wine, which is a game of similar vintage to yours. Everything seemed to be going alright until the most important moment - launching an actual game. At that point the screen was all messed up, despite the sound running in the background. X locked up so I had to kill it to get back to normal.

Installing the game in windows and copying the folder over to linux didn't help either, though this is often a good strategy to get other games going in wine. It's how Far Cry worked for me in Linux, for example (to the extent that it did, and for as long as it did).

In the end, though, I decided all the googling and trial-and-erroring and whatever, just was a waste of time. I still have a disk devoted to windows, and this game (not to mention the many other non-working in wine/cedega games) still worked fine in it. So I just played the game in windows.

You may not want to hear this, but if you still have windows it makes little sense to mess around too much trying to get things to work in wine. You have better things in life to do :) . If things work 'out of the box', then maybe that's OK. But if they don't, and especially if your game is not a very common one, then you have probably got a big mystery on your hands that more than likely is impossible to solve.

I say this not as someone trying to discourage you on purpose, but as someone who spent many long hours wrestling with wine/cedega trying to get windows games working on linux. At the end of the day I found all that trouble just isn't worth it.

But don't despair, because there is [light at the end of the tunnel]("http://www.ubuntuforums.org/showpost.php?p=1929486&postcount=22") :)

On the other hand, if you don't have 'another OS' which plays your game, then I apologise for wasting your time.

---

### Post by anemon on 2007-01-05
Thanks for all your help, Psudonym! And I agree with all you say about Windows and "Wintendo" and not wasting ones time. The irony of it all is that I *do* have a Windows partition on my computer, but for some stupid reason I wanted XP 64-bit, and it won't run the game either (nor will it connect to the Internet, for that matter)... I'd replace it with the old 32 bit version right away, but I'm afraid it will wipe out my Ubuntu partition or overwrite Grub or something. 

Perhaps I should just give up. It's just that my girlfriend really, *really* wanted to play this game. Still, going through so much trouble for "Curse of Monkey Island 3"... ](*,)

---

### Post by pseudonym on 2007-01-05
If you haven't tried it yet, I think your chances of getting 'Monkey Island' working are better on winxp64 than on wine. I run 64-bit Ubuntu and the linux games I play are all 32-bit. To work they use the 32-bit compatibility libraries readily available in ubuntu.

For 32-bit games that don't work or if I want wine I can install a 32-bit'[chroot]("https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29")' environment, which is like a system within the system, so you can run 32-bit apps that don't otherwise work on 64-bit.

I don't know anything at all about winxp64, but I'm guessing there are some similar 32-bit compatibility options for it? I could of course be completely wrong. Remember, it is windows we're talking about ;)

If you wanted to re-install 32-bit windows it can be done without destroying Ubuntu. Grub will be overwritten, but can be reinstalled easily enough. There are many threads in the forum about it. I strongly advise making a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy") first, in case you do run into trouble. This way you will still be able to boot both OSes.

But hopefully you won't need, or want, to do anything this drastic.

---

### Post by anemon on 2007-01-06
I've tried once more running the game in XP64, and it resolutely refuses, saying that the .exe is "intact" or something like that (i.e. perfectly OK), but "for another machine type than the current machine". It should be backwards compatible, and I do run several 32 bit apps on it. Might it not be that Monkey Island -- the game, not the installer, which is working just fine -- actually runs in 16 bits? XP64 is compatible only with 32 bit apps!

So I'm stuck with Wine. So close, yet so far away... Perhaps I'll give the first to games in the series a try instead!

Although this whole "Make sure that your X server is running and that $DISPLAY is set correctly" business is still driving me nuts! :-k

---

### Post by anemon on 2007-01-09
Ever heard of ScummVM? I just did, and it works like a dream! Goodbye, Wine (at least for now)...

---

