---
title: "iPod songs showing in Ubuntu but not in iPod."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by bucktron on 2007-06-22
Hi all,

I'm new to Ubuntu and I have an iPod 3rd gen originally formatted in Windows. I used [ this thread]("http://ubuntuforums.org/showthread.php?t=103071&highlight=ipod") to mount it and get it to show in gtkpod. All well and good. 

Until later that day. I'm listening a song (by electro prog outfit Battles - v.g.) and it starts to play all glitchy & stuttery. So I pause & reset it. Apple sign ...it loads main menu....but now I can't see a single song on the iPod. No artists, no albums, no playlists. Only thing thats left is my iPod name. Buckpod. 

However! When i connect it to my Ubuntu box, and it automounts, I can see that everything is still in there. Also Windows won't recognise it anymore. Well it sees it as a removable disk but iTunes ignores it.

Have I corrupted it somehow? How can I solve this heinous state of affairs?

Thanks for any help in advance.

---

### Post by corney91 on 2007-06-22
These could be stale or orphaned (I can never remember which is which) tracks. In Amarok you can rebuild your iPod's database in the devices browser. Sorry, I don't know how to do it on other programs but if you do use amarok (it really is a great program) you could give it a shot.

---

### Post by bucktron on 2007-06-24
Amarok tells me :
> Media Device: could not find iTunesDB on device mounted at /mnt/ipod. Should I try to initialize your iPod?

Then when I click initalize it gives me:
> 
Media device: failed to write iPod database

Media Device: Failed to initialize iPod mounted at /mnt/ipod


But my ipod is definitely mounted. Result of 'mount' in terminal:
> /dev/sda2 on /mnt/ipod type vfat (rw,noexec,nosuid,nodev,umask=000,user=chris)

I've tried to use gtkpod too and it's giving me this error when I try to Load iPod:
> Error initialising iPod: Opening of '/mnt/ipod/iPod_Control/iTunes/iTunesDB' for writing failed (Not a directory).

I notice that when i'm browsing the ipod what i assume is the iTunesDB isn't actually called that - its just called iTunes. 

At this point I'd consider reinstalling the ipod software and reloading it with all my music. Does anyone know how to do that?

---

### Post by Funk Phenomena on 2007-06-24
I'm pretty clueless too, but I did recall getting a warning when trying to sync with Rhythmbox that it would change things so that iTunes wouldn't recognize what was going on.  So it may be that your Linux software and iTunes are not intercompatible.

---

### Post by bucktron on 2007-06-25
Yeah, I think I'll try and restore the iPod to to it's original factory state. But Windows isn't recognising it at the moment so I'll have to do a bit of research about how to do that. And just use Windows/iTunes for it in future.

---

