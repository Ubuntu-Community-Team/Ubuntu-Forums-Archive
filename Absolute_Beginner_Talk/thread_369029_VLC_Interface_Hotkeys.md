---
title: "VLC Interface Hotkeys"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by taurean on 2007-02-24
Hi, 

Not sue if this is the correct place to start with a media player problem, but its true I am new to ubuntu - not necessarily linux, I dabbled with it in the stone age..

Ok, 

Well As I have spent most of my time using PC's with windows installed, and am used to the closed source applications that are unfortunately all over doze with a passion, and now after finally growing a brain and coming to an OS that I actually enjoy using rather than 'needing' to use for one thing or another, I am concerned at the slight, yet overwhelmingly annoying, things that seem to be all over the apps Linux/Ubuntu have to offer.

In windows, I was relient on one media player alone. GOM Player. It did everything I wanted, it was friendly to me, it never crashed on me, it did everything except go get me another beer.

I also used VLC in windows and dont recall any problems with it, but just for the sheer simplicity of it all I liked GOM.

However it is closed source and VLC is open. Hence Im using VLC in Ubuntu, but it seems flakier than a box of corn flakes in a blizzard.

What is the point of the 'HOTKEYS' if they simply dont work ? I've reconfigured them to how I want, but the only keys that I use that actually work are F for full screen and Space for Pause/UnPause.

Im still using it, but I have to have my keyboard at hand if I want to change the volume, as the 'wheel mouse up/down' just doesnt work. I know it works everywhere else, but the with the hotkey settings it just doesnt. Its a hassle in full screen to break out and find the bar to hush it up. (The end of the world I know... )

And the only way I've gotten the 'slow/fast' options to allow me to use the arrow keys is to manually disable every other hotkey setting, or else the 'volume up/down' keys would take on other hotkey functions, like jump minutes ahead or some other crazy things.

I've tried all the other Media Players around, and theyre all so unfriendly. 

All I want is to use my mouse. 

Single Click = Pause/Unpause
Double Click = Full screen.
Mouse wheel up/down = Volume change.

Sorry for the long post, its more a vent than anything, but can anyone reccomend a media player that doesnt seem to be glued together after someone dropped it ?  Or maybe the magick spell to make vlc like me too?

OR ---- Can someone tell me how to get GOM player working under Wine. It loads, works perfectly, but the media files just dont play. :( No Errors, just as if theyre not valid files. It tells me the end time, it resizes the screen appropriately, etc.. but thats all.

Ack, Id be happy to use wine for 1 app, most I use the PC for is office apps and watching my tv shows.

Cheers if anyone can suggest something..

Steve.

---

### Post by FyreBrand on 2007-02-24
I would recommend Kaffeine.  I use both, but mostly Kaffeine.  The hotkey mappings in Kaffeine work really well.  Double clicking does toggle full screen.  I don't think you can configure the other two mouse options though.  At least I haven't been able to find out how to change mouse behavior.  The moue wheel fast forwards and rewinds instead.  I don't know if that will do it for you, but I've found it to be an easy to use player.

Kaffeine uses the Xine engine instead of gstreamer (although I think it can use that, but default is Xine).

So to use it effectively make sure you have all your repositories enabled and then install these by your favorite means (Synaptic, Adept, or apt-get).
1. Kaffeine
2. libxine-extracodecs
3. W32Codecs -- only if it's legal in your region.

From the terminal you can install them by the following commands:
```
sudo apt-get update
sudo apt-get install kaffeine libxine-extracodecs w32codecs

```
If you are using Gnome you might have to create a menu item (I'm not too sure about that part) and if you are using KDE then it will be in the menu.

If you need help enabling the proper repositories to get libxine-extracodecs and w32codecs see this forum and post by ubuntu-demon: [**Ubuntu-Demons Edgy Customization Guide**]("http://www.ubuntuforums.org/showpost.php?p=1645711&postcount=1").  In that post you're mostly looking for the sources.list and especially the seveas repo.  That whole forum is good information on making a few customizations though and definitely worth a read.

---

### Post by chewearn on 2007-02-24
My experience with vlc is totally opposite; switching from Windows to Linux version has been 99% success.  All hotkeys customization behave at it supposed to; the only exception is the <ENTER> key on the numberpad.

One thing to note though, vlc does not check for duplicate key assignments.  If you assigned a key for two different functions, the key simply stop working.  For example, I assigned <ENTER> key to toggle fullscreen, but I have to remember to remove it from DVD OK command.

---

### Post by thinsoldier on 2007-08-26
My keyboard and mouse are totally useless in VLC as well.

... and xine really has the absolute worst gui I have ever seen in a media player. And I'm the kind of person with hundreds of winamp and coolplayer skins. I've seen some ugly and unusable interfaces in my time.

...keyboard shortcuts are good though

---

### Post by cimness on 2008-01-20
Hotkeys worked for me after I turned off embed video in interface (I found a bug report and solution for this with Google before but I can't find it again).

The path is: Preferences -> (tab) Interface ->(tab) Main interfaces -> wxWidgets -> (disable) Embed video in interface. Save and restart VLC, maximize the video output, and it should work.

---

