---
title: "E: jre: subprocess post-installation script returned error exit status 1"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-17
Hi,
few days ago I was trying to install JRE 1.3 and there was an error I got. But know every time I install some software I get message: "E: jre: subprocess post-installation script returned error exit status 1".

It looks like software is installed and at the end some kind of script is run. How can I turn off this post-installation script?

My system: Ubuntu 6.10
Thanks,
Abcuser

---

### Post by phossal on 2007-04-17
You were trying to install JRE 1.**3**? What for? Isn't Java, like, version 6 now or something?

---

### Post by abcuser on 2007-04-17
Hi,
I have some software - applet that runs correclty only on JRE 1.3.

But I have stoped bodering with JRE 1.3 install on Ubuntu, I have just spent to much time solving problem [url=http://ubuntuforums.org/showthread.php?t=398477&highlight=abcuser]  	
Installing java JRE 1.3.1_09 on Ubuntu 6.10[/url].

What I would like to do know is just remove somekind of script from jre 1.3 that is automaticaly run after each installation of any program like Application | Add/Remove.

Thanks,
Abcuser

---

### Post by skibum58 on 2007-06-09
I have the same problem, only with a botched VMWare Player install.

After installing and uninstalling the 2 different VMWare Players available, I was finally able to get the VMWare Player ver 1 to work.  This was installed via the Applications | Add/Remove utility.  I could not get ver 2 to work which was a TAR/GZ package from VMWare.

Now, every time I go to install or uninstall a game or other package, it keeps triggering what looks to be a dpkg re-installation of VMWare Player ver 1.  So I have to go through the entire VM configuration routine in order to properly install the originally intended package.  I tell it not to overwrite the previous VM install procedure.

Which brings us back to the original question of this thread:  Is there some kind of script which keeps triggering this attempted reinstall that I can kill?  Is there a line in dpkg which I can comment out to keep this from happening?  VM keeps running well, but this dpkg triggering event is a major annoyance, especially when I'm just now spooling up with package installs.

It throws the "subprocess post-installation script" error whether I'm using Applications | Add/Remove (what program is that, btw?), or Administration | Synaptic.

brain fried skibum

---

### Post by troy1of2 on 2007-08-11
I am having the exact same problem with vmware here. Can someone please tell us how to fix this?

---

### Post by skibum58 on 2007-08-14
To Troy1of2,

Take a look at this thread.  Jonathan Gordon suggested a fix which worked until I ran into a 'missing config file' error, at which point I chose not to rely on the VMWare Player.

[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957)

There is something going on in the scripting which keeps triggering a re-install event.  

The problem shows up for me in VMWare; this thread indicates a problem with JRE, and scanning the forums for the exact error message indicates that the script problem can show up in a number of other locations.

I had no problem with JRE; VMWare is the only time I've seen it, which is a real bugger because I rely on VMWare a lot.  I need an XP install on my Ubuntu Sony laptop for utility purposes, and ended up putting it in a VirtualBox instead of VMWare.

I think it's a "known issue" because recent public comments from Mark Shuttleworth / Ubuntu leadership indicate that getting VMWare and Ubuntu working together better has become a high priority for the next Ubuntu release.

skibum

---

### Post by garythornton1956 on 2007-10-10
I have got this message too after installing strongswan in ubuntu 7.10.  It seems to be related to the installer updating itself but it'll need more knowledgable people than me to resolve it.

From earlier messages regarding XP running in a VM, I have it working fine in VirtualBox but I had to get the package from their website instead of the ubuntu repo.

---

