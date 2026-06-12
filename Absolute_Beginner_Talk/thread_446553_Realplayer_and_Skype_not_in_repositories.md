---
title: "Realplayer and Skype not in repositories?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-17
Where did they go in the repositories?

I'm using Fiesty on PPC.

I know I can download them from the site, but how can I make them deb packages?

---

### Post by diargasm on 2007-05-17
I don't remember skype being in the repository.  I always used automatix.

---

### Post by wormser on 2007-05-17
Skype is in the Feisty repository.

>  apt-cache search skype
skype - A VoIP software
skype-static - A VoIP software

>  apt-cache show skype
Package: skype
Priority: optional
Section: net
Installed-Size: 12160
Maintainer: The Medibuntu Team <medibuntu@sos-sts.com>
Architecture: i386
Version: 1.3.0.53-1medibuntu2
Replaces: skype
Depends: libasound2 (>> 1.0.12), libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libqt3-mt (>= 3:3.3.6), librte1, libxext6, libx11-6, libstdc++5
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Conflicts: skype
/i386/skype_1.3.0.53-1medibuntu2_i386.deb
Size: 10061512
MD5sum: aa105d6c130c3bacf201991ff894bd2b
SHA1: c4d48dda6ff69e3e3aac9d0c5b7559760b7a964c
SHA256: 2578b3898f08f08e1d1e17825a65f1e80a2a71ef3b84a27630b90de577037442
Description: A VoIP software
 Skype is a proprietary peer-to-peer Internet telephony (VoIP) software.
 The Skype communications system is notable for its broad range of features,
 including free voice and video conferencing, and its ability to use peer to
 peer (decentralized) technology to overcome common firewall and NAT problems.
 .
 Homepage: [http://www.skype.com/](http://www.skype.com/)
 .
 NOTE: You must accept Skype's EULA prior to successfully installing
 this package.
 .
 This is in Medibuntu because of its non-free license.


I thought the show command showed where the package is coming from.  It could be from this line:  Filename: pool/feisty/non-free.  I have a non-free in /etc/apt/sources.list.  I added them.  Here are the details:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

I believe that is where skype is at.

---

### Post by Obor on 2007-05-17
Skype has also its own debian repo
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

Once you got current stable you can try new alpha version (which works much better for me) More about it [here]("http://forum.skype.com/index.php?showforum=141")

```
wget http://www.skype.com/go/getskype-linux-alpha-static
tar -xvjf skype-alpha_staticQT-1.4.0.58-generic.tar.bz2
cd skype-1.4.0.58_alpha
sudo mv /usr/bin/skype /usr/bin/skype1.3
sudo mv skype /usr/bin/
sudo mv sounds /usr/share/skype/
cd ..
sudo apt-get install libsigc++-2.0-0c2a
sudo rm -rf skype-1.4.0.58_alpha
```

---

### Post by Najand on 2007-05-17
*Realplayer for linux* is in fact, ***Helix Player*** with *"Realplayer" looks*. 
You can find helix player in the repositories. 
"**Skype**" cannot be installed on PowerPC architecture. Sorry for that.

---

### Post by Xarok on 2007-05-17
> **wormser said:**
> Skype is in the Feisty repository.





I thought the show command showed where the package is coming from.  It could be from this line:  Filename: pool/feisty/non-free.  I have a non-free in /etc/apt/sources.list.  I added them.  Here are the details:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

I believe that is where skype is at.

I went to Synaptic Package Manager > Settings > Repositories > 3rd Party Software > I added 
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
but it has an error saying there is no public key

What is this?

Also, where did Real PLayer go?

---

### Post by Najand on 2007-05-17
Look at this:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by Xarok on 2007-05-17
> **Najand said:**
> *Realplayer for linux* is in fact, ***Helix Player*** with *"Realplayer" looks*. 
You can find helix player in the repositories. 
"**Skype**" cannot be installed on PowerPC architecture. Sorry for that.

Doesn't Helix player only play real media streams?

I need to play an rmvb file...

&#33980;&#20117;&#12381;&#12425;&#12434;&#35211;&#12383;&#12356;&#12391;&#12377;>_>

---

### Post by Xarok on 2007-05-17
> **Najand said:**
> Look at this:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Thank you!

gxine will play rmvb, but other applications will not.

---

### Post by Xarok on 2007-05-17
I installed the repo, but skype will not work on ppc? I can't find skype or real player.

---

### Post by ugm6hr on 2007-05-18
I found Realplayer 10 in a Debian installer - see my post here:
[http://ubuntuforums.org/showthread.php?t=445027](http://ubuntuforums.org/showthread.php?t=445027)

---

