---
title: "cant find Flash player"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by jeff_flynn on 2008-02-06
i went to [http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual) and followed the steps to install flash player but got this error message:

An error occured while extracting files.
Command Line Output

tar: install_flash_player_9_linux/libflashplayer.so: Wrote only 3072 of 10240 bytes
tar: Error exit delayed from previous errors

---

### Post by papuccino1 on 2008-02-06
Let me point you in the right direction, to a guide I made. It works 100%. :)


Edit: Here's the link: [http://ubuntuforums.org/showthread.php?t=664242]("http://ubuntuforums.org/showthread.php?t=664242")

Make sure to follow every step there. Happy flashing. Erm...

---

### Post by jeff_flynn on 2008-02-06
thanks a lot! but how do i uninstall to gnash or flash player partial files i already have?

---

### Post by erfahren on 2008-02-07
might have been just a bad download - try redownloading it

note: if you just select "Save to disk" in Firefox's download dialog you can then just right-click on the archive on your desktop (or whever you saved it to) and select "Extract here".

then just open that folder that is extracted and you should see the file "libflashplayer.so"

-- this is all you really need to do with it...

press Alt+F2 and in that dialog type in:
```

gksudo nautilus

```
that will open Ubuntu's file browser with root permissions (so don't do anything crazy!)

--- then just navigate the filesystem to /usr/lib/filefox/plugins and cut and paste the libflashplayer.so file into there.

restart Firefox and find some (weird?) YouTube video to test it.

---

### Post by papuccino1 on 2008-02-07
> **jeff_flynn said:**
> thanks a lot! but how do i uninstall to gnash or flash player partial files i already have?

If you want to uninstall gnash (you SHOULD) go to synaptic manager.

System > Administration > Synaptic 

Search for it there "gnash"-


If I helped ya put a Solved status on the thread.

---

### Post by aysiu on 2008-02-07
> **jeff_flynn said:**
> i went to [http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual) and followed the steps to install flash player but got this error message: > **papuccino1 said:**
> Let me point you in the right direction, to a guide I made. It works 100%. :)


Edit: Here's the link: [http://ubuntuforums.org/showthread.php?t=664242]("http://ubuntuforums.org/showthread.php?t=664242") What's the difference? Both involve downloading the .tar.gz, extracting it, using *gksudo nautilus*, and running in the terminal.

---

### Post by papuccino1 on 2008-02-07
No difference "behind the scenes" but my guide did help him didn't it? I think it's more newbie friendly since it has pictures. 

I remember when I first started I had no IDEA what gksudo nautilus was. How would he?

---

### Post by aysiu on 2008-02-07
> **papuccino1 said:**
> No difference "behind the scenes" but my guide did help him didn't it? I think it's more newbie friendly since it has pictures. 

I remember when I first started I had no IDEA what gksudo nautilus was. How would he?
My guide has pictures as well, and it also explains what *gksudo nautilus* does.

---

### Post by erfahren on 2008-02-07
@aysiu - your guide doesn't mention uninstalling gnash if it has been installed - maybe it would be good to include that

-- it's strange that people still have problems with the flashplugin available in Synaptic - I thought that was fixed long ago. Awhile back I noticed that the flashplayer-nonfree deb package was in /var/cache - so I thought that maybe if someone tried to reinstall it, the "bad" package was used from there instead of downloading the new, fixed one. (it doesn't end up in /var/cache/apt/archives so just cleaning the apt cache wouldn't work.) - I don't know

---

### Post by gandaran on 2008-02-07
the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

gandaran

---

