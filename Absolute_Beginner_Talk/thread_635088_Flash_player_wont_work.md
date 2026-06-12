---
title: "Flash player wont work?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by JoeDaPro on 2007-12-08
I download Flash of the site, i install it through the terminal, it tells me installation complete but when i go to run a flash video, it just wont load and says missing plug ins :S?

---

### Post by taurus on 2007-12-08
It depends how you install it if you do it by hand.  You need to link it to the plugin directory.  However, why not do it the easy way.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```
Now, start firefox again and see if you have flash plugin this time.

---

### Post by JoeDaPro on 2007-12-08
17:10:50 (19.17 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

joe@joe-desktop:~$

nope

---

### Post by leegold on 2007-12-08
I have exactly same issue:

Xbuntu 7.10

Tried Adobe Flash and Gnash plugings loaded via Synaptic Manager on both FF and Opera. The plugin installs but NO flash.

---

### Post by taurus on 2007-12-08
> **JoeDaPro said:**
> 17:10:50 (19.17 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

joe@joe-desktop:~$

nope

> **leegold said:**
> I have exactly same issue:

Xbuntu 7.10

Tried Adobe Flash and Gnash plugings loaded via Synaptic Manager on both FF and Opera. The plugin installs but NO flash.

[http://ubuntuforums.org/showthread.php?t=635204](http://ubuntuforums.org/showthread.php?t=635204)

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by ryrules1 on 2008-01-26
nice, I was having this problem and it worked for me gnash is garbage I hate to admit. It would hardly load videos on youtube.

---

### Post by daradib on 2008-01-28
> **ryrules1 said:**
> nice, I was having this problem and it worked for me gnash is garbage I hate to admit. It would hardly load videos on youtube.

No problem.

---

### Post by jan quark on 2008-01-28
here my small easy guide for beginners
how to install flash via the official adobe site
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by daradib on 2008-01-28
> **jan quark said:**
> here my small easy guide for beginners
how to install flash via the official adobe site
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

It is a good tutorial. However, it would be recommended to used a ["fixed" or update package to keep consistent]("http://ubuntuforums.org/showthread.php?t=636397") with Ubuntu's package management. Of course, one must take into account the fact that a third-party package can be potentially risky if the third-party is not trusted.

Quoting [Conrad Knauer]("https://bugs.launchpad.net/~atheoi") who [said this nicely]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/142").

> Bourne inquired: "Is it advisable to download a random .deb file?"

Radom DEBs would not be advisable, no, but I am pointing out a specific one ;)

Seriously though, users may judge the relative risks of downloading that specific DEB; its been up on UF since the beginning of December, the person who started the thread has been posting for over a year, some 23 users have left a "thank you" on the bottom of that post and the thread extends over three pages without (by my skimming) any serious issues with the DEB.

Users may also weigh the relative risks of said DEB against the one in the repositories which either doesn't work or has installed software with a known security vulnerability.

"Wouldn't it be best to advise those user who want or need flash to install it using the .tar.gz method outlined on the adobe website?"

I would not, no. That would defeat the purpose of having excellent package management; e.g. how would said users know if a new update (let's say a 120 release is made available in a week) became available? For Ubuntu, a DEB is always preferable IMHO.

---

