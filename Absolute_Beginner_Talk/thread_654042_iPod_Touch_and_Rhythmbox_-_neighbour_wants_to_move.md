---
title: "iPod Touch and Rhythmbox - neighbour wants to move back to Windows"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-12-30
So I've read that in September, programmers were mad because Apple changed their encryption methods on the new iPods (the iPod Touch): [http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html](http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html)

I then read that they cracked it in a weekend: [http://ipodminusitunes.blogspot.com/2007/09/weve-won.html](http://ipodminusitunes.blogspot.com/2007/09/weve-won.html)

Now my neighbour has an iPod Touch (thanks Christmas! </sarcasm>) and has been using Ubuntu since 7.04. She's now upgraded to 7.10, but, of course, her iPod Touch doesn't work with Ubuntu (fully).

I found instructions here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) but can't use them because they don't have wireless Internet. ipod-convenience needs an IP address apparently.

So what can I do for this poor girl who has threatened to go back to Windows just for iTunes? It's her choice, so I'll have to abide by it but I was hoping I could get this working some how without her having to do something too cryptic just to use it every time she plugs it in.

I know VMware server through and through but it's ability to handle USB devices currently lack and to run a whole operating system (Windows) just to play iTunes seems incredibly labourious. Not to mention that I'd have to mount her ext3 music folder and get iTunes to read it...

What can I do?

---

### Post by blueridgedog on 2007-12-30
This is no answer, just ranting.

I love my ipod (60 gig video).  It is full of songs and videos and I carry tons of stuff in it (want to see my daughter's Christmas play?)

But, the day a device dictates an OS is the day I move on to another device.  The fact that Apple will do the dirty tricks that they do and still claim to have a unix/BSD core for their OS is strange.

---

### Post by LowSky on 2007-12-30
Its her choice. I still use windows for alot of stuff. I use Ubuntu for my normal stuff, but for games/iTunes/MS Access, I have no choice. I understand that alot of people resent microsoft ways of business but they are the standard in which most people work within. Sure I dont like all their products but some I have to use.

---

### Post by blueridgedog on 2007-12-30
Like I said, just ranting.

My last Access client moved on to other things so my need to dual boot went down to nearly zip.

---

### Post by altonbr on 2007-12-31
Mmm, has anyone got Rhythmbox working with the iPod Touch?

---

### Post by dcstar on 2007-12-31
> **altonbr said:**
> 
.............
I know VMware server through and through but it's ability to handle USB devices currently lack and to run a whole operating system (Windows) just to play iTunes seems incredibly labourious. Not to mention that I'd have to mount her ext3 music folder and get iTunes to read it...


I have just setup vmware server running XP so I can use my Sony Network Walkman, vmware handles the USB for this device fine and it works just as it does when XP is booted.

---

### Post by blueridgedog on 2007-12-31
Is there still a vmware product you can use for free? (as in Beer)

---

### Post by altonbr on 2008-01-01
> **blueridgedog said:**
> Is there still a vmware product you can use for free? (as in Beer)

In Gutsy, if you enable the Canonical Partner repositories, then you can install vmware via:
```
sudo aptitude install vmware-server
```

To enable the repository, use System > Administration > Software Sources > Third-party Source and enable "http://archive.canonical.com/ubuntu gutsy partner". Or edit your /etc/apt/source.list file.

---

### Post by altonbr on 2008-01-01
Well, it looks like she's bringing the tower over... This might be the first time I've had to wipe Ubuntu and put Windows on.
> F***ING IPODs!

---

### Post by scopo on 2008-01-01
Why not just install Virtualbox and run XP & Itunes in it for now - until the hash fix is sorted once and for all ???

---

### Post by altonbr on 2008-01-01
> **scopo said:**
> Why not just install Virtualbox and run XP & Itunes in it for now - until the hash fix is sorted once and for all ???

Is that the one that can superimpose Windows applications over GNOME (or KDE, etc.) and have it appear as if it's actually there?

---

### Post by scopo on 2008-01-01
It allows you to run a 'virtual' copy of windows (XP, Vista, ME, 200 etc etc.) in a separate window.

Its like you are running a virtual machine or computer over Ubuntu.

One word of warning though - DON'T install the version from "Applications > Add/Remove" as this dosent have USB support.  
Instead, get the PUEL version from here...
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by LordTyrans on 2008-01-01
You could install wine which will let you install and use itunes 7.3.

Here is a link to the page showing the results on Gusty.

"http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248&iTestingId=18884"

From my experience wine is Extremely easy to install on Ubuntu so you should have no problem with that.

---

### Post by LordTyrans on 2008-01-01
I have just found the answer:).
"
You need to first Jailbreak your iPod Touch and install ssh on in (the same exact way you would with an iPhone). Install the latest SVN build of libgpod/gtkpod and sshfs, mount /var/root/Media on the iPod Touch to the directory of your choosing on your filesystem, and transfer away with GTKPod.

If you need more in depth instructions, Google is your friend. 
"

I got that from [this]("http://forums.macrumors.com/showthread.php?t=381860") Thread. I believe thay have more detailed descriptions there, but they have confermed that it works.
Here is the post 
"
What the hell is going on.

ANYWAY, this method does in fact work (its how I use my iPod Touch with Linux). The iTunesDB thing is why you need an SVN build of libgpod; the current stable release doesn't support the checksumming that the iPhone and Touch use in their DBs. And also, cover art support has come a *long* way in only a week or so: you might even at this point be able to write the covers and ArtworkDB directly to the sshfs mounted iPod. If that doesn't work though (and if it doesn't work it will wipe your your ArtworkDB, so backup that directory first), the work-around I've been using is to keep a copy of the iPod Touch's directory structure on a local directory on my file system, use GTKPod to write to that, and *than* mount the iPod and copy the files over with cp -urv.

libgpod apparently has some problems correctly scaling the cover art if its less than 320x320px large (the covers will end up being one pixel to small in either dimension), and it doesn't center the cover art if its not square, but those are trivial to deal with.
"

I hope that has solved the mystery.

---

### Post by ntetreau on 2008-01-02
> **LordTyrans said:**
> I have just found the answer:).
"
You need to first Jailbreak your iPod Touch and install ssh on in (the same exact way you would with an iPhone). Install the latest SVN build of libgpod/gtkpod and sshfs, mount /var/root/Media on the iPod Touch to the directory of your choosing on your filesystem, and transfer away with GTKPod.

If you need more in depth instructions, Google is your friend. 
"

I got that from [this]("http://forums.macrumors.com/showthread.php?t=381860") Thread. I believe thay have more detailed descriptions there, but they have confermed that it works.
Here is the post 
"
What the hell is going on.

ANYWAY, this method does in fact work (its how I use my iPod Touch with Linux). The iTunesDB thing is why you need an SVN build of libgpod; the current stable release doesn't support the checksumming that the iPhone and Touch use in their DBs. And also, cover art support has come a *long* way in only a week or so: you might even at this point be able to write the covers and ArtworkDB directly to the sshfs mounted iPod. If that doesn't work though (and if it doesn't work it will wipe your your ArtworkDB, so backup that directory first), the work-around I've been using is to keep a copy of the iPod Touch's directory structure on a local directory on my file system, use GTKPod to write to that, and *than* mount the iPod and copy the files over with cp -urv.

libgpod apparently has some problems correctly scaling the cover art if its less than 320x320px large (the covers will end up being one pixel to small in either dimension), and it doesn't center the cover art if its not square, but those are trivial to deal with.
"

I hope that has solved the mystery.
  
Something is telling me it hasn't solved the mistery as the original poster did write that she had no wifi network.  That's the deal breaker for her at this point since you need to communicate, with sshfs, through wifi for this method to work.  

I do think that this would be the simplest way for her to use her touch in Linux.  The price for a wireless router is so low these days, she could probably make the jump.  You have to admit that the idea of leaving your touch on its stand anywhere in the house and syncing through wifi is sexy enough to warrant seting up a wifi network in your house!

Nic

---

### Post by altonbr on 2008-01-02
> **ntetreau said:**
> Something is telling me it hasn't solved the mistery as the original poster did write that she had no wifi network.  That's the deal breaker for her at this point since you need to communicate, with sshfs, through wifi for this method to work.  

I do think that this would be the simplest way for her to use her touch in Linux.  The price for a wireless router is so low these days, she could probably make the jump.  You have to admit that the idea of leaving your touch on its stand anywhere in the house and syncing through wifi is sexy enough to warrant seting up a wifi network in your house!

Nic

Very true, I'll see what I can do.

---

### Post by altonbr on 2008-01-02
> **LordTyrans said:**
> You could install wine which will let you install and use itunes 7.3.

Here is a link to the page showing the results on Gusty.

"http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248&iTestingId=18884"

From my experience wine is Extremely easy to install on Ubuntu so you should have no problem with that.

[QUOTE=http://docs.info.apple.com/article.html?artnum=306640]iPod touch requires iTunes 7.4 or later. [/QUOTE]

I know how to get the latest Ubuntu Wine repositories so lets see how it goes... ([http://winehq.org/site/download-deb](http://winehq.org/site/download-deb))

---

### Post by altonbr on 2008-01-02
Nope, couldn't get it (iTunes 7.4+ and Wine and VirtualBox/VMware server is too taxing on this computer and too confusing for this user) to work, had to wipe to Windows. Not fun.

---

### Post by ntetreau on 2008-01-02
Too bad, I've had only joy using my iphone under ubuntu...

---

### Post by dn_nb on 2008-01-02
My experiences with itunes under windows so far have been a nightmare.. the program has locked up my otherwise stable install a handful of times now. I was thinking about switching back to linux just to see how the ipod support is. Wireless syncing sounds great, although probably slower. The only deal breaker for me right now is photo syncing, but there seems to be ways around that, so i may give it a shot.

Maybe when she realizes how horrible itunes is she will want to give a wireless router and ubuntu another try. of course, she would have to jailbreak it, but if you show her everything you can do with a jailbroken pod i'm sure she wouldn't have a problem with that. ; )

---

### Post by xjgnsdof on 2008-03-14
> **altonbr said:**
> Mmm, has anyone got Rhythmbox working with the iPod Touch?

I've gotten the iPod Touch to play in Rhythmbox. I posted an addendum to the official wiki: [http://ubuntuforums.org/showthread.php?t=722750]("http://ubuntuforums.org/showthread.php?t=722750"). Make sure you use the "ipod-touch-mount" and  "ipod-touch-umount" commands exclusively. That is, don't try and mount or unmount the iPod in the media playing app itself.

I haven't synched music in Rhythmbox yet because I tried doing so in gtkpod and Amarok, but they screwed up my iPod's ability to read cover art, forcing me to ssh into my iPod, delete the Artwork folder, and resynch my library. If I have time, I may try synching media. Until then, I will use Rhythmbox to play songs.

---

