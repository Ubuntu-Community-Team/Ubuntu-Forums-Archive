---
title: "Regarding WINE...."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-05-26
I think I let myself be mislead about WINE

Last night, I backed up my Windows files to CD, then installed Ubuntu 7.04, using my entire hard drive (wiping out WindowsXP).  I have just grown so weary of Windows and things not working right for me.

I've been getting around fairly well in Feisty Dawn and have been configuring things to my liking.  I just installed WINE and I think I just now realized that WINE works with Windows programs that are already installed on a Windows partition.... is this correct??

For some reason, after reading through the compatibility charts and other things, I thought that Windows programs could be installed and made to run through WINE.... but this is wrong, isn't it?

Like I said, I wiped out my Windows XP and now Ubuntu 7.04 is laptop's OS.  I guess if I'm to continue with Linux, I should uninstall WINE and forget about it, huh?

I suppose if I didn't have several hundred dollars worth of Windows programs, I wouldn't be so concerned.

Thoughts?  Advice?  Snickers? ;)

---

### Post by meng on 2007-05-26
Some Windows programs run in wine, but definitely not all. Some run okay, some run very poorly, some won't even start. Go to [www.winehq.com](www.winehq.com) and look at AppDB to get an idea which ones work and which don't.

But in any case, if you need to run lots of Windows programs (whether games or applications), then stick with Windows. It doesn't make sense to use Linux mainly to run Windows programs. You install Linux in order to run mostly Linux programs (of course).

---

### Post by yabbadabbadont on 2007-05-26
[http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index)
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)
[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)

Read through those, they will answer most of your questions.  Basically though, you just have to install your programs using wine so that they are available to be run with wine.  Example:
```
wine path-to-setup-program.exe
```

Be sure to check out the wine application database to see how well (or even if) your program is supported under wine.  [http://appdb.winehq.org/](http://appdb.winehq.org/)

Edit: Too slow yet again.  :lol:

---

### Post by meng on 2007-05-26
By the way, wine MAY run programs already installed on a Windows partition, but this is not the proper way to use wine. You should install the programs in wine before running them in wine.

---

### Post by ElEdwards on 2007-05-26
In all reality, there's only one Windows program I'm interested in running...which is Adobe Audition 1.5.   I do commercial voice-overs (and I'm the "You've got mail" guy) and I do all of my recordings with Audition.

As far as the rest of the apps I use/need, OpenOffice will handle that very nicely.  Firefox is perfect for me.:D

---

### Post by meng on 2007-05-26
[http://appdb.winehq.org/appview.php?iVersionId=3665](http://appdb.winehq.org/appview.php?iVersionId=3665)
[http://appdb.winehq.org/appview.php?iVersionId=5869](http://appdb.winehq.org/appview.php?iVersionId=5869)

You could start another thread asking for native Linux alternatives to Adobe Audition.
I'm definitely no expert, but I believe one can record and edit sound using Audacity. No doubt there are other choices, and you'll want to hear from the experts.

---

### Post by ElEdwards on 2007-05-26
OK..... I just used WINE to install a Windows program and the installation seemed to go just fine.... after the required reboot, there is now a WINE Menu item under Applications.... but this menu entry only takes me to a configuration screen for this Windows program and not the program itself, so I can't make it run.

I used the File Browser but I can't find a DOS or Windows partition, such as "C:\Windows" or anything like that.

Where do I have to look to see what I installed?

Thanks!

---

### Post by yabbadabbadont on 2007-05-26
Firstly, read the documentation in the links provided by the various posters (including me).  :D

Secondly, wine creates a "C" drive  in the hidden ~/.wine directory which is used whenever you install programs in wine.  You'll need to create a custom launcher for your program using
```
wine ~/.wine/drive_c/Program\ Files/program-directory/program-name.exe
```

Edit: "drive_c" may be "c_drive", I don't remember which and I'm not currently at my own computer.

---

