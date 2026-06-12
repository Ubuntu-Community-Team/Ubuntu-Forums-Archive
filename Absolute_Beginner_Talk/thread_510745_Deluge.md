---
title: "Deluge"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by InflammatoryWin.Apologist on 2007-07-26
I'm having trouble with Deluge. I just installed Ubuntu (7.4) yesterday. I installed Deluge today, and it seems to open fine. But, I click on the link to download something, then select to open it with Deluge, but Deluge never responds in any way. Any ideas?

Also, in case it comes up, how do I open a port?

---

### Post by Armman on 2007-07-26
You could try saving the .torrent file to your desktop and then open Deluge and drag the .torrent into Deluge. Then Deluge will ask you where to download the file(s).

---

### Post by Armman on 2007-07-26
To open ports for Deluge it depends what kind of router/gateway you have.

---

### Post by InflammatoryWin.Apologist on 2007-07-26
I tried dragging, and it showed up in there for a second, but then closed automatically. I opened it again and it was gone.

---

### Post by Armman on 2007-07-26
Ok then go to your home folder and click ctrl + h to see the hidden files. Then open the .config folder, then click the deluge folder and delete the persistent.state file inside. After that, open up deluge to see if it quits on you.

---

### Post by InflammatoryWin.Apologist on 2007-07-26
Okay, I did, I tried it again, same thing.

---

### Post by Armman on 2007-07-26
All right I'm not sure why Deluge keeps doing that. Can you run Deluge through terminal and post the output?

---

### Post by InflammatoryWin.Apologist on 2007-07-26
> **Armman said:**
> All right I'm not sure why Deluge keeps doing that. Can you run Deluge through terminal and post the output?

I don't know how.

---

### Post by Armman on 2007-07-26
type "deluge" in terminal and then paste the output in a post.

---

### Post by deadlikeoscar on 2007-07-26
How did you install Deluge? Did you use the one that is in Synaptic? If so, you may be happier removing that one and going to deluge-torrent.org and downloading the Ubuntu package from there. I haven't heard many good things about the one in Synaptic.

---

### Post by InflammatoryWin.Apologist on 2007-07-26
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Debug 1 {} []
Debug 2 0 0
['']

---

### Post by deadlikeoscar on 2007-07-26
Highlight the text and then click with the scroll wheel of your mouse where you want to paste it or right click and select copy.

---

### Post by Armman on 2007-07-27
OK since you seem to be new to Linux I recommend installing automatix. Download it here [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) Then you can install deluge through that. Thats how I installed it and everything works perfectly. Also remove deluge before installing it.

And the output you posted looks fine. There shouldn't be anything wrong.

---

### Post by deadlikeoscar on 2007-07-27
I would still recommend downloading the package from Deluge's website over Automatix. (Unless of course if that is where you got it) Automatix is nice but sometimes it messes things up and that's just one more thing to troubleshoot.

---

### Post by InflammatoryWin.Apologist on 2007-07-27
Yeah, Automatrix I believe is where I got it.

Hmmm... thanks a lot for your help, regardless.

---

### Post by Armman on 2007-07-27
Yeah ok then, I guess you should just follow Deadlikeoscar's advice and install it from Deluge's  website. Automatix might of messed something up I guess.

---

### Post by deadlikeoscar on 2007-07-27
I would remove it from Automatix and then download either the 32-bit version from ```
http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.3/&file=deluge-torrent_0.5.3-1_i386.deb
```
or the 64-bit from ```
http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.3/&file=deluge-torrent_0.5.3-1_amd64.deb
``` and save it to your desktop or somewhere. Then double-click on the file and let it install that way.

Their web forum is moderated by the developers and they may be able to help you if you find that it refuses to run. It really is one of the best so I hope you can get it to work.

---

### Post by InflammatoryWin.Apologist on 2007-07-27
The first problem is fixed, but now I have a new weird problem: after a few seconds, I lose all my seed, and then it starts back finding them, then goes back to 0, et cetera.

---

### Post by deadlikeoscar on 2007-07-27
Your seeds disappear or it says downloading and then it keeps pausing and unpausing?

---

### Post by InflammatoryWin.Apologist on 2007-07-27
> **deadlikeoscar said:**
> Your seeds disappear or it says downloading and then it keeps pausing and unpausing?

Pausing and unpausing, now that I look closer.

---

### Post by deadlikeoscar on 2007-07-27
I thought they fixed that. Go to preferences and click on use compact storage allocation. You may have to reload your torrents. See if that helps.


By the way, do you know what file system you are trying to download to? Is it a shared NTFS drive, default ext3 Linux partition or something else? I guess they didn't fix it for all file systems but I just wanted to make sure. If you don't know, don't worry about it.

---

### Post by InflammatoryWin.Apologist on 2007-07-27
> **deadlikeoscar said:**
> I thought they fixed that. Go to preferences and click on use compact storage allocation. You may have to reload your torrents. See if that helps.


By the way, do you know what file system you are trying to download to? Is it a shared NTFS drive, default ext3 Linux partition or something else? I guess they didn't fix it for all file systems but I just wanted to make sure. If you don't know, don't worry about it.

I'm guessing shared NTFS; it's a second disk I formatted with Windows.

---

### Post by deadlikeoscar on 2007-07-27
Well, regardless, that should fix your problem. Let me know if it works.:)

Oh, if it DOESN't work. Did you enable NTFS write support with ntfs-3g and ntfs-config or whatever they are called?

---

### Post by InflammatoryWin.Apologist on 2007-07-27
I even went as far as to delete the torrents and download them again, but it's still doing it.

---

### Post by InflammatoryWin.Apologist on 2007-07-27
> **deadlikeoscar said:**
> Well, regardless, that should fix your problem. Let me know if it works.:)

Oh, if it DOESN't work. Did you enable NTFS write support with ntfs-3g and ntfs-config or whatever they are called?

I don't know. I would assume not.

---

### Post by deadlikeoscar on 2007-07-27
Step 1: Open a terminal and type ```
sudo apt-get install ntfs-config
```

Step 2: Go to Applications-->System Tools-->NTFS Configuration Tool

Step 3: Click to enable internal drive or external drive depending on whether the drive is inside your computer or a USB external.

Step 4: Select the mount point. I think you can click to let you type here. You should use /media/windows or you can replace windows with whatever you want to name the drive.

Step 5: If all goes well, you can reboot and it should auto mount your drive. When saving your torrents you would navigate to /media and then the folder you named the drive as.

It's been a while since I have installed this but it should be all you need to know.

---

### Post by InflammatoryWin.Apologist on 2007-07-27
Who da man, again? Oh right, Deadlikeoscar's da man. Everything is working great. Thanks a million.

---

### Post by deadlikeoscar on 2007-07-27
No prob. :) You can probably uncheck that use compact storage allocation option (since it wasn't the problem) if you would rather Deluge allocate the entire size of the file before downloading. It doesn't really matter though. If you leave it on it will only use as much space as it needs and will allocate space as needed.

---

