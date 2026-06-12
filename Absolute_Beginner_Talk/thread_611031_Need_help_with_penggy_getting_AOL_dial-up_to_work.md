---
title: "Need help with penggy: getting AOL dial-up to work"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by SmartRutter on 2007-11-12
I've just been able to get the drivers for my Lucent Win Modem earlier, and figured out how to dial out.
Right now, i have to use Martian in order to get it working, since doing modprobe ltserial doesn't work. _[This]("https://help.ubuntu.com/community/DialupModemHowto/Lucent")_ page helped me figure out how to get it working, but now i have a problem connecting to the internet through aol dial-up.

So, i found penggy in the ubuntu repositories ( [http://packages.ubuntu.com](http://packages.ubuntu.com) ) and downloaded it from there. I started it up, and messed with the config for a while. Right now, i'm stuck at the error message i get after starting it and dialing the aol access number:
```

Connection at 52000b/s done.
Executing chat script (/usr/share/penggy/chat/aolnet.scm)...
Script: String 'UQKT2' matched
Script: String 'login' matched
Script: Send 'aol '
Script: String 'Password' matched
Script: Send 'aol '
Script: String 'Connected' matched
Script: Chat success
Chat success, connected...
Unable to register P3 protocol functions, access is not connected
engine - No data to wait
Server drop the connection.

```

I'm fairly new to ubuntu and I currently have ubuntu 7.10 dual-booted with Windows XP.  I'm using Windows right now to get online, since i have no other way to access the internet.

So if anyone has anything that might help me, I'd greatly appreciate it.

---

### Post by jfinkels on 2007-11-12
Did you install penggy with ```
sudo aptitude install penggy
```? If not I recommend making a backup of any configuration files you've edited, doing```
sudo remove penggy
``` and then doing ```
sudo aptitude install penggy
```If you *did* install penggy using aptitude or apt-get, I'm afraid I can't help you.

---

### Post by SmartRutter on 2007-11-13
I just grabbed a .deb package of it from [http://packages.ubuntu.com](http://packages.ubuntu.com) and double-clicked on the file to install it after rebooting into ubuntu, since there is no way for me to download the package while inside ubuntu.

I'll try doing sudo remove penggy and then sudo install penggy in a while once i reboot into ubuntu.
EDIT: errr oops i mean sudo **aptitude** install penggy

---

### Post by jfinkels on 2007-11-13
Oh right, no internet connection...good point...well then, no need to reinstall it, don't bother. That would be silly. I apologize for misleading you :\.  I'm afraid I cannot help you any further, though :(

Have you searched the web using Google?

---

### Post by SmartRutter on 2007-11-13
yeah tried that, found something on it that looked similar to the error i got, but its some sort of site that requires a registration of some sort. :( No way i'm going to do that.

Also, i looked around the config file again for anything useful.  It sounds to me like there might be something up with the protocol or something.  I tried running it another protocol type by using: penggy --protocol=FLAP
This got me past the previous error, but it just ends after a few secs due to "segmenation fault" or something...

It seems to me that after looking through the config yet again, this program didn't support that protocol fully in the version i downloaded.  Perhaps i'll see if theres newer version out there, probably not, but its worth a try.

---

### Post by mike555 on 2007-11-14
There are many ISPs that are better than AOL , I'm surprised that anyone would want AOL .........

---

### Post by jfinkels on 2007-11-14
> **mike555 said:**
> There are many ISPs that are better than AOL , I'm surprised that anyone would want AOL .........

Some may not have the luxury of a choice :|

---

### Post by SmartRutter on 2007-11-14
yeah, i'm pretty much stuck with aol right now... :(  I really wish i could get dsl.

Well, there's no newer version avalible then what i downloaded, i tried a slightly older version, same results.

Well, if no one knows how to get this program to work for me, does anyone know any other way for me to get online with aol?

---

### Post by mike555 on 2007-11-14
I don't think AOL works with anything but Windows , their browser is just a modified Internet Explorer ............. if you live in the US you might try doing a search for ISP's ....... here in Florida I recommend BasicISP ,    [http://www.basicisp.net](http://www.basicisp.net)    , it's $6.95 a month and works good .......

---

### Post by jfinkels on 2007-11-14
> **mike555 said:**
> I don't think AOL works with anything but Windows , their browser is just a modified Internet Explorer ............. if you live in the US you might try doing a search for ISP's ....... here in Florida I recommend BasicISP ,    [http://www.basicisp.net](http://www.basicisp.net)    , it's $6.95 a month and works good .......

AOL offers dial-up connection service, I believe, independently of the AOL web browser, and I believe that is what we're talking about here.

And again, as the OP says, he or she is stuck with AOL for now.

As for solving your problem with penggy, I'm afraid I don't know how to help you...maybe you can try using the Ubuntu Live CD on a different computer, installing penggy, and seeing if it works on a different set of hardware.

---

### Post by SmartRutter on 2007-11-15
Yeah, i'm certainly stuck with AOL for now.

As for trying penggy on another computer, i don't think i'll be able to.  My dad's computer is horribly ancient and i don't really have access to any other computers.  Plus, my dad would probably not want me messing around with ubuntu on his computer cause he'd think i'll somehow mess his computer up.

Well, i can do is hope i'll be able to get dsl sometime soon, unless anyone else has any good ideas.

---

### Post by jfinkels on 2007-11-15
When in doubt, try a different distribution.

Knoppix, like Ubuntu, is a Debian-based distribution renowned for it's hardware recognition. It runs directly from a Live CD. Try it out: [http://www.knoppix.net/](http://www.knoppix.net/)

Of course, there are a million other Linux distributions, this is just one that I would recommend first.

---

### Post by SmartRutter on 2007-11-16
Thanks, but i'm probably going to stick to ubuntu for now.

I'll either just have to hope i can get dsl, or find out some way to fix this.

---

