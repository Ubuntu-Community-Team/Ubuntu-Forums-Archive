---
title: "Can't use Flash Player or GNASH on Gutsy!!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by dragonblade on 2008-04-03
I Can't use Flash Player or GNASH.
I try to install it but I get an error.







:guitar::guitar::guitar::lolflag::guitar::guitar::guitar:

---

### Post by privaterolf on 2008-04-03
I assume you're trying to install inside Firefox.

For some, you may need to install manually.

Try Synaptic Package Manager [System->Administration->Synaptic Package Manager], when loaded, hit Ctrl+f and search for flashplugin-nonfree

Post back with your results.

---

### Post by dragonblade on 2008-04-05
I found nothing

---

### Post by Madoperator on 2008-04-05
I also had this problem, it was a error in my installation CD. The CD wasn't burned properly, so I had to reinstall ubuntu. It could be the same with you..

---

### Post by HereInOz on 2008-04-05
I have found that to successfully install flash player that I needed to download the file from Adobe and manually install it.  The install via the repositories almost always resulted in an error.

I think also that if you install the flash player as downloaded from Adobe, you may have to write a symbolic link from the /usr/lib/firefox/plugins directory to the directory where the libflashplayer.so plugin file is located.  Not sure about this - it has been a while since I did it.

---

### Post by bubba_169 on 2008-04-05
Make sure the multiverse, restricted and universe sources are ticked in system->administration->software sources then use synaptic to reload and try searching again

---

### Post by dragonblade on 2008-04-05
> **HereInOz said:**
> I have found that to successfully install flash player that I needed to download the file from Adobe and manually install it.  The install via the repositories almost always resulted in an error.

I think also that if you install the flash player as downloaded from Adobe, you may have to write a symbolic link from the /usr/lib/firefox/plugins directory to the directory where the libflashplayer.so plugin file is located.  Not sure about this - it has been a while since I did it.
I can't, when I click on the link it does nothing. I don't know why. Do you know why?

> **bubba_169 said:**
> Make sure the multiverse, restricted and universe sources are ticked in system->administration->software sources then use synaptic to reload and try searching again
What?
Can you put it in words that I, a 13 year-old with slightly above-average computer knowledge, can understand!

---

### Post by TheFuzz4 on 2008-04-05
Ok I just reinstalled ubuntu last night for the first time in about 8 months.  Installing flash player was easy as pie.  Go to adobe's website ([www.adobe.com]("http://www.adobe.com")) and download the flash player (I did all of this through firefox) Just save it to your desktop (default location for firefox) after the download completes you will need to close all browser windows and then do this
Go to your applications menu and click on run
Type in xterm
ok now your at your command prompt now do the following 
cd /Home/<username>/Desktop/install_flash_player_9_linux and hit enter
now type in sudo sh flashplayer-installer
it will ask you for your password just type that in and go
The installer might ask you for your firefox install directory just type in 
/usr/lib/firefox for the install location
That should do the trick if you have any problems just ask.

---

### Post by oblivioncth on 2008-04-05
Yay, I'm a 13 year old with too much computer knowledge(dad has worked with computers all his life) but thats besides the point. What he means is, Make sure the multiverse, restricted and universe sources... have a check in the box when you go to,  system->administration->software sources, then use synaptic pack manger and try searching again .

---

### Post by dragonblade on 2008-04-05
> **TheFuzz4 said:**
> Ok I just reinstalled ubuntu last night for the first time in about 8 months.  Installing flash player was easy as pie.  Go to adobe's website ([www.adobe.com]("http://www.adobe.com")) and download the flash player (I did all of this through firefox) Just save it to your desktop (default location for firefox) after the download completes you will need to close all browser windows and then do this
Go to your applications menu and click on run
Type in xterm
ok now your at your command prompt now do the following 
cd /Home/<username>/Desktop/install_flash_player_9_linux and hit enter
now type in sudo sh flashplayer-installer
it will ask you for your password just type that in and go
The installer might ask you for your firefox install directory just type in 
/usr/lib/firefox for the install location
That should do the trick if you have any problems just ask.

> **oblivioncth said:**
> Yay, I'm a 13 year old with too much computer knowledge(dad has worked with computers all his life) but thats besides the point. What he means is, Make sure the multiverse, restricted and universe sources... have a check in the box when you go to,  system->administration->software sources, then use synaptic pack manger and try searching again .
Wow, it seem baerly like anyone under 18 has even heard about Ubuntu, I just red PC Mag(Because I'm obsessed wit PCs). Anyway, I tried that and I will download it in seconds.

---

### Post by thiebaude on 2008-04-05
Here is something that worked for me, [http://launchpadlibrarian.net/107610...untu2_i386.deb](http://launchpadlibrarian.net/107610...untu2_i386.deb), I hope it works for you.

---

### Post by thiebaude on 2008-04-05
sorry, my link to that file didn't work

---

### Post by thiebaude on 2008-04-05
[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by bubba_169 on 2008-04-06
> **dragonblade said:**
> Wow, it seem baerly like anyone under 18 has even heard about Ubuntu, I just red PC Mag(Because I'm obsessed wit PCs). Anyway, I tried that and I will download it in seconds.

You should go to [www.teensonlinux.org]("http://www.teensonlinux.org"), theres a friendly community for teens who use linux!

---

### Post by billgoldberg on 2008-04-06
Open up a terminal (applications -> acessories) and copy.paste this:

sudo apt-get install ubuntu-restricted-extras

That will install flash.

Or you could install using the .tar.gz from adobe's site.

Right-click that file and choose "extract here".

Then inside that folder, right-click the installer script. Go to properties. Then to the permission tab and enable executing of the file.

Then doulbe click and choose "run in terminal", follow the instructions.

---

### Post by dragonblade on 2008-04-07
> **bubba_169 said:**
> You should go to [www.teensonlinux.org]("http://www.teensonlinux.org"), theres a friendly community for teens who use linux!
Thanks,
I'll check that out.

> **oblivioncth said:**
> Yay, I'm a 13 year old with too much computer knowledge(dad has worked with computers all his life) but thats besides the point. What he means is, Make sure the multiverse, restricted and universe sources... have a check in the box when you go to,  system->administration->software sources, then use synaptic pack manger and try searching again .
   I did that but still can't use flash for some reason.

---

### Post by dragonblade on 2008-04-07
> **thiebaude said:**
> [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
I'm trying that now
> **billgoldberg said:**
> Open up a terminal (applications -> acessories) and copy.paste this:

sudo apt-get install ubuntu-restricted-extras

That will install flash.

Or you could install using the .tar.gz from adobe's site.

Right-click that file and choose "extract here".

Then inside that folder, right-click the installer script. Go to properties. Then to the permission tab and enable executing of the file.

Then doulbe click and choose "run in terminal", follow the instructions.
Tried the first one, didn't work.
I got error code (2), and it said another process was using it.

---

### Post by Mazza558 on 2008-04-07
> **dragonblade said:**
> I'm trying that now

Tried the first one, didn't work.
I got error code (2), and it said another process was using it.

Close all of the following and try again:

- Add/Remove programs
- Synaptic
- Terminal
- Update Manager.

---

### Post by dragonblade on 2008-04-07
> **thiebaude said:**
> [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Finnaly it works! Thank You!

---

