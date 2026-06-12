---
title: "Gimp, Ink, and Xara"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Akira_Oni on 2006-08-18
Ok... already I'm tired of the GIMP. 

I'm also in need of more than Inkscape can provide.

I found a program called Xara, which looks promising, however I can't desipher what the installation instructions are telling me.

Can someone please translate this into noob?

[http://www.xaraxtreme.org/download/](http://www.xaraxtreme.org/download/)

---

### Post by Cone on 2006-08-18
Downloading right now to check if this is correct, but I'm thinking...

```
wget http://downloads.xara.com/opensource/RecomXaraLX0.7_rev1692.tar.bz2
tar xvjf RecomXaraLX0.7_rev1692.tar.bz2
cd (insert-XaraLX-folder-here)/bin
sudo chmod +x xaralx
./xaralx
```

Once again, I'm not sure and I'll post back in a minute when I check :)

---

### Post by Cone on 2006-08-18
Oh, well, that was quick.

Here's what you do.

```
wget http://downloads.xara.com/opensource/RecomXaraLX0.7_rev1692.tar.bz2
tar xvjf RecomXaraLX0.7_rev1692.tar.bz2
cd xaralx/bin
./xaralx
```

And that should work :)

~Cone

---

### Post by bluntu on 2006-08-18
[http://www.xaraxone.com/](http://www.xaraxone.com/)

Have fun.

---

### Post by Akira_Oni on 2006-08-18
akiraoni@Oni-San:~$ cd xaralx/bin
bash: cd: xaralx/bin: No such file or directory

that's the response... I'm not really sure where it downloaded too

---

### Post by Marsolin on 2006-08-18
Xara LX is in the Ubuntu edgy, Debian etch, and Debian sid repositories.

---

### Post by Akira_Oni on 2006-08-18
> **Marsolin said:**
> Xara LX is in the Ubuntu edgy, Debian etch, and Debian sid repositories.

Wha? Translate into n00b please.

---

### Post by Akira_Oni on 2006-08-18
Erm... so, can anyone help me trouble shoot this?

---

### Post by Marsolin on 2006-08-18
Sorry.  This link [http://linuxappfinder.com/package/xaralx](http://linuxappfinder.com/package/xaralx) has links to the deb files so you can install Xara LX through the package management system.

I'm guessing that you are using the Dapper (6.06) release of Ubuntu. If so, you can try downloading this file ([http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xaralx/xaralx_0.6r1442-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xaralx/xaralx_0.6r1442-4_i386.deb)) and typing "sudo dpkg -i xaralx_0.6r1442-4_i386.deb" from the Terminal. Make sure you are in the same directory as the file. I haven't tried to install it myself, but it should work if they haven't unnecessarily restricted dependencies.

---

### Post by Akira_Oni on 2006-08-18
```
Selecting previously deselected package xaralx.
(Reading database ... 89194 files and directories currently installed.)
Unpacking xaralx (from xaralx_0.6r1442-4_i386.deb) ...
dpkg: dependency problems prevent configuration of xaralx:
 xaralx depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 xaralx depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 xaralx depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 xaralx depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 xaralx depends on libgtk2.0-0 (>= 2.10.0); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.
 xaralx depends on libpango1.0-0 (>= 1.13.3); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 xaralx depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 xaralx depends on libwxbase2.6-0 (>= 2.6.3.2.1.1ubuntu2); however:
  Package libwxbase2.6-0 is not installed.
 xaralx depends on libwxgtk2.6-0 (>= 2.6.3.2.1.1ubuntu2); however:
  Package libwxgtk2.6-0 is not installed.
 xaralx depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing xaralx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xaralx
akiraoni@Oni-San:~/Desktop$    
```

Not my fault... honest

---

### Post by Marsolin on 2006-08-18
Darn. I was hoping that wouldn't happen. It looks like the deb files won't work on Dapper. My next suggestion is to download the .package file ([http://downloads.xara.com/opensource/RecXaraLX0.7_rev1692.package](http://downloads.xara.com/opensource/RecXaraLX0.7_rev1692.package)).

And here ([http://www.xaraxtreme.org/developers/documentation/autopackage_installation.html](http://www.xaraxtreme.org/developers/documentation/autopackage_installation.html)) are the instructions for what to do after that. Hopefully this will work.

---

### Post by Akira_Oni on 2006-08-18
Thank you sir, it works now.

But I'm confused... I was told this performed like a vector version of the gimp. However there is no wide brush... are there plugins for this?

---

### Post by Cone on 2006-08-18
Not quite sure if it's what you're looking for, but make a path and at the top pull down the menu that says .5 pt and pick a different number of your choice.

That what you want? :)

---

### Post by Marsolin on 2006-08-18
Unfortunately I'm not proficient with Xara, so I can't help with actual use. Hopefully someone else can. Another vector drawing program that you could try is Sodipodi ([http://linuxappfinder.com/package/sodipodi](http://linuxappfinder.com/package/sodipodi)). To install it just run Synaptic and search for it. I'm not sure if it is in the Add/Remove Programs section or not.

---

### Post by Akira_Oni on 2006-08-18
sorry, I was a bit general in that statement.

I'm looking for a round brush that I can resize... I notice the options for it are there (on top) however I'm not sure about where I can find brushes. Speaking of which, can I do similar things with Inkscape?

*edit* Consider having the ability to make the caligraphy pen round. That's what I want.

---

### Post by BLTicklemonster on 2006-11-02
I like Gimp, I like Xara, and man, photoshop kicks them llamas head in, but it ain't free. :(

Anyway, I haven't tried it yet, but Krita looks interesting:
[http://www.linux.com/article.pl?sid=06/10/23/1853220](http://www.linux.com/article.pl?sid=06/10/23/1853220)

---

