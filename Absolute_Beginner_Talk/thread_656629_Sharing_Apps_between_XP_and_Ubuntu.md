---
title: "Sharing Apps between XP and Ubuntu"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by breaking on 2008-01-02
Hey Guys,
Just installed Ubuntu on my new Dell D630, and I have been extremely impressed so far. It recognized all my drivers except for sound, and eve that was easy to install. I do have a few questions, however, and it would be great if anyone had any advice.

I am dual booting Windows/Ubuntu due to applications that will only work in a native Windows environment. I have several applications that I would like to install in both Windows and Ubuntu, Firefox for example. Is it possible to have one installation that both OS's recognize? I would like to have a universal set of cookies, bookmarks, and extensions, and not have to worry about missing a bookmark that I added in Ubuntu and not in Windows, or a cool extension I jsut isntalled inw indows, but not showing up in the Ubuntu Firefox. 

I have partitioned my hard drive with a 20 GB root (ext3), a 20 GB NTFS (windows), a 2 GB swap, and a 40 GB home (ext3). I have installed the EXT2 driver iin windows, so both drives can read/write in each other's partitions. Is it as simple as just installing both programs from each OS in the same directory, are there more steps involved, or is ti impossible. In addition to Firefox, ohter applications that I would love to "share" between the OS's are Office (with WINE), or at least my outlook PST file, Step mania (a small game with both Windows and Linux install packages), and maybe a few more applications in the future. Thanks so much for any imput.

---

### Post by jken146 on 2008-01-02
> **breaking said:**
> Is it as simple as just installing both programs from each OS in the same directory
No.  Windows programs don't run natively in Linux and vice versa.

I think there will be a way to share Firefox bookmarks and the like, probably involving making links to the other OS's files.  Not sure on the details though.

Check out winehq.org to see if your version of MS Office can be supported.  Try Open Office -- it handles MS Office formats.

---

### Post by Xavieran on 2008-01-02
Do you have your ntfs drive automount on startup?If so you can probably just write a few menu entries to execute the windows .exe on windows partition...eg.

wine /media/myntfs/Programs and Apps/yourprogram/yourprograms.exe

---

### Post by thelatinist on 2008-01-02
You can easily move your firefox profile location following these instructions: [http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile).  This should make it possible to point Ubuntu's Firefox to your Windows Firefox profile, and vice-versa.

---

### Post by breaking on 2008-01-02
Thanks for the tips guys, I am still pretty new to the entire Linux scene, so I will go ahead and look up mounting drives and figuring all that stuff out :D Its gonna be a pain trying to figure out how to share a PST between two different programs and two different OS's while not getting duplicate mail messages, heh.

---

### Post by PeterJS on 2008-01-02
I'll save you a the trouble and tell you right now that there aren't any linux apps that use PSTs to save mail. Evolution and Thunderbird can import them, but I don't think they can write back to them. Your best bet for sharing application data between Windows and Linux would be using mozilla apps on both, loading up the ntfs drivers and sym-linking your windows application data in to your linux home folder.

```

ln -s /media/windows/Documents\ and\ Settings/User/Application\ Data/Mozilla/Firefox/Profiles/some.random.string ~/.mozilla/firefox/
gedit ~/.mozilla/firefox/profiles.ini

```

In profiles.ini there should be a line that says
```

path=profile.name

```
Changing that line to the name of new profile you sym-linked in. Rinse and repeat for Thunderbird.

---

### Post by Kenn11 on 2008-01-02
Your Bookmark problem can easily be solved by putting the firefox addon "Foxmarks Bookmark Synchronizer" in both your systems under Firefox.



Kenn

---

