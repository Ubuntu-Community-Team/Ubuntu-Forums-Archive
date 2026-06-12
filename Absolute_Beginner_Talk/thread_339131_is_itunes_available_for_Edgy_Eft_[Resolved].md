---
title: "is itunes available for Edgy Eft? [Resolved]"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-15
I like the way itunes organized my music files for me in windows. Is it possible to get itunes for Ubuntu or a reputable music organizing system like it?

---

### Post by userundefine on 2007-01-15
It might work under wine, but I doubt it.  So, no, there is no iTunes available for Ubuntu.

I suggest you look into Songbird or Amarok for your music collection and playback management.  Amarok is the best music app I've ever used on *any* platform, and I've used iTunes.

---

### Post by tordan on 2007-01-15
I tried amarok and now use exhaile, but neither actually organize the music files like itunes. The problem I am having is that when I am using a burning program like Grip I am having trouble finding the files I want because they are all individually listed in my Music folder and not organized into artist folders (like in itunes). Is there a program that does this?

---

### Post by aysiu on 2007-01-15
I'll tell you what works for me.

When I rip CDs, I make sure the songs are titled as Artist - Number - Title. That way, when I open up my music folder, I can scroll through them all, I can see them sorted by artist easily.

If you like doing it by album, you can change that to Artist - Album - Title.

Also, a lot of music programs like Rhythmbox and AmaroK allow you to burn playlists or burn selected songs, so you don't actually have to know the physical location of songs. You can just organize based off ID3 tags.

---

### Post by oyvindaa on 2007-01-15
It is possible to use iTunes with CrossOver Office, which can be downloaded from [www.codeweavers.com](www.codeweavers.com)

The downside is that it's only the demo that's free, you've to pay $40 for the full version.

You can try the demo for 30 days.

After downloading the CrossOver shell script (put it on your desktop, in your /home, wherever you want), you've to make it executable and then install it.

In the terminal:
```
chmod 744 install-crossover-standard-demo-6.0.0.sh
```

```
./install-crossover-standard-demo-6.0.0.sh
```

A GUI installer will open. Click OK to accept the licensing terms.

By default, CrossOver will install at /home/username/cxoffice.

Once that's done, click 'Begin Install'.

If you use HTTP proxy, you've to enter the correct information for that.

After that you'll be back at the main Setup screen, where a new button has appeared .. 'Install Windows Software'.

From there go on to install iTunes.

Good luck.

---

### Post by tordan on 2007-01-15
Does Amarok have the option to organize your files for you or just view them in Amarok in an organized catalogue?

---

### Post by chipdip on 2007-01-15
The best program for ubuntu edgy I have found that can sync with any iPod is the Banshee Music Player. It is just like iTunes, organizes stuff like it, everything.

---

### Post by userundefine on 2007-01-15
> **tordan said:**
> Does Amarok have the option to organize your files for you or just view them in Amarok in an organized catalogue?
Yes, I'm somewhat sure it does.  It's kind of hidden in the file area if I recall.  I'm not in front of it now so I can't be more specific.

However, I organize my music into directories of Artist/Album/etc. like iTunes.  You can do this automatically with EasyTag if your id3 tags are correct (and even if they aren't).  You scan the folder with all your music, and you set parameters on how you want each file organized based on id3 tags.  So, for me, I use a formula like ~/music/%a/%b/%n - %t.  What this says is that I want EasyTag to read the Artist's name (%a) from the mp3 and create a folder for it.  Then, I want it to read the Album name (%b) of the Artist and put it in the Artist directory as its own folder.  After that, it reads the Track Number (%t) and the Track Title (%t) and change the actual filename to that, so it looks like "~/music/Johnny Cash/Best of Johnny Cash/01 - Ring of Fire.mp3".

This sounds complicated, but only when you're explaining it.  Like I said, if your id3 tags are correct, then this is all automated and very fast.  It takes maybe 20 minutes to set up EasyTag like you want it, and then after that it's automated and simple.  It also forces you to keep your id3 tags set properly and neatly, which I like.

---

### Post by aysiu on 2007-01-15
If you associate your music player with a ripping program like Goobox or Grip, you can actually define in the ripping program the way you want the ripped songs to be organized (~/music/artist/album/song, for example).

As long as your music player (AmaroK, Rhythmbox, Banshee, etc.) is set to scan subfolders, you're okay.

---

### Post by golem3 on 2007-01-15
> **oyvindaa said:**
> It is possible to use iTunes with CrossOver Office, which can be downloaded from [www.codeweavers.com](www.codeweavers.com)

The downside is that it's only the demo that's free, you've to pay $40 for the full version.

You can try the demo for 30 days.

.

Arg..spending for a Linux program??? Not my idea of a good solution.

---

### Post by tordan on 2007-01-15
I'm installing Easytag and am going to attempt the same organization you did. It is the same as I would prefer.

Any more tips in the process?

---

### Post by sloggerkhan on 2007-01-15
I think Banshee and Rhythmbox are pretty much the same as iTunes. (I've used all 3, and find no real difference between them....) (So long as you aren't stupid enough to use the iTunes music store...)

---

### Post by oyvindaa on 2007-01-15
> **golem3 said:**
> Arg..spending for a Linux program??? Not my idea of a good solution.

I never said it's a good solution did I?

He asked whether iTunes can be installed on Ubuntu, so I told him it can be done ;)

I'd never pay $40 for CrossOver Office anyway.

I'm using Banshee at the moment and I'm very happy with it.

---

### Post by Lord Illidan on 2007-01-15
Sure you can organise your files with Amarok. Right click on an artist in the sidebar, and choose Organise files.

---

### Post by tordan on 2007-01-15
Decided to go with Banshee (I like the graphic simplicty). Seems to be organizing as I needed. Thanks all, for your generous advice!

---

### Post by altonbr on 2007-02-12
Yeah, but the organization done my Amarok is sketchy. It creates a whole bunch of folders; doesn't delete the old ones; renames SOME songs, but not others (no matter how perfect the ID tags are) and can only be activated manually (it's NOT automatic).

---

