---
title: "Real Player doesn't launch"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by overyonderthere on 2007-06-02
Hey all;

I need to watch some realplayer stuff for a class, and can't seem to get the player to launch. I uninstalled it and installed Helix, but while Helix will play audio streams, it won't play the video. It refers me to realplayer. Mplayer connects to the stream server, but then jumps to 'stop' and won't play the file. What should I do?

Thanks!

---

### Post by ugm6hr on 2007-06-02
Uninstall helix.

Then look at my post on how to install Realplayer.  It should work fine:
[http://ubuntuforums.org/showthread.php?t=454622](http://ubuntuforums.org/showthread.php?t=454622)

---

### Post by overyonderthere on 2007-06-02
Helix has been uninstalled and realplayer reinstalled. While realplayer is now in my applications menu, it does not launch when I click on it. Now not even the radio works. When I tried to launch a real video in another player, it told me it didn't have the Real Video 3.0 codec, but I couldn't find it in synaptic. There's something else that might be important; earlier I found directions elsewhere telling me to download realplayer as a bin, use chmod and ./. I now have it on my desktop and cannot get rid of it (it seems to be a root file), as well as the one in my application menu. Neither works.

Thanks!

---

### Post by ugm6hr on 2007-06-02
> **overyonderthere said:**
> Helix has been uninstalled and realplayer reinstalled. While realplayer is now in my applications menu, it does not launch when I click on it. Now not even the radio works. When I tried to launch a real video in another player, it told me it didn't have the Real Video 3.0 codec, but I couldn't find it in synaptic. There's something else that might be important; earlier I found directions elsewhere telling me to download realplayer as a bin, use chmod and ./. I now have it on my desktop and cannot get rid of it (it seems to be a root file), as well as the one in my application menu. Neither works.

Thanks!

Sorry about that.  I have no idea how to uninstall programs manually.  I have only used .deb or apt/Synaptic.  I suspect if you can get rid of the previous realplayer installation, the .deb version will run just fine.

---

### Post by overyonderthere on 2007-06-02
OK, thanks for your help. Is there anyone who can help uninstall this realplayer from my desktop?

---

### Post by milambyr on 2007-06-02
Just curious, does Realplayer try to take over your entire system like it does in Windows?
You'd have to put a gun to my head to get me to install that application...i'd hijack a friends computer and install it if I needed it for school...

---

### Post by overyonderthere on 2007-06-02
I don't even think I have to install Realplayer to be able to play .ram files. I should be able to do it in mplayer, but mplayer just doesn't seem to want to work. I have all of the plugins necessary. I just want a simple fix. I wish there was a way to clean everything out and start trying to get this to work again without having to reinstall Ubuntu. As it is, I feel like I'm installing a new fix over top of an old fix (like downloading the bin of Realplayer), and it's making things worse.

---

### Post by ugm6hr on 2007-06-02
> **overyonderthere said:**
> I don't even think I have to install Realplayer to be able to play .ram files. I should be able to do it in mplayer, but mplayer just doesn't seem to want to work. I have all of the plugins necessary. I just want a simple fix. I wish there was a way to clean everything out and start trying to get this to work again without having to reinstall Ubuntu. As it is, I feel like I'm installing a new fix over top of an old fix (like downloading the bin of Realplayer), and it's making things worse.

The reason I opted for realplayer was I couldn't get gxine to play realmedia, despite the correct codecs being installed.  And I don't think VLC does either (I use that now for all other media formats).

---

### Post by overyonderthere on 2007-06-04
I found a solution at this page:[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods) .
 I typed in 

export GTK_IM_MODULE=xim

and it worked a treat.

---

### Post by waiverider on 2007-06-18
Thank you for this information, It worked perfectly. Much appreiated:KS

---

### Post by cowbuntu on 2007-06-18
> **milambyr said:**
> Just curious, does Realplayer try to take over your entire system like it does in Windows?
You'd have to put a gun to my head to get me to install that application...i'd hijack a friends computer and install it if I needed it for school...

No it doesn't.

---

