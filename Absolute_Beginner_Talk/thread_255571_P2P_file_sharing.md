---
title: "P2P file sharing?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-11
Whats the best "download" program to use with sites like Thepiratebay.org ... i have looked at azureus but didnt like it on linux any other program? dont want Ktorrent. and please post how to install also

---

### Post by Anonii on 2006-09-11
> **haxer said:**
> Whats the best "download" program to use with sites like Thepiratebay.org ... i have looked at azureus but didnt like it on linux any other program? dont want Ktorrent. and please post how to install also
I'd either recommend utorrent with wine.
[http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent+wine](http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent+wine)
or a native torrent client, tribler:
[http://ubuntuforums.org/showthread.php?t=234700](http://ubuntuforums.org/showthread.php?t=234700)


btw, I'm using utorrent.

---

### Post by haxer on 2006-09-11
Hmm.. sounds weird to use an windows program in wine and download it in linux no have i gone this far so i have installed ubuntu then i want to go ubuntu style no good program that i can use that deosnt require wine? Didnt like that native either want an suited for ubuntu and noobs like me:P

---

### Post by Virak on 2006-09-11
If you're not averse to using a text-based interface, I'd suggest rtorrent; it's extremely fast and lightweight. And since it's in the repos, just type this in the terminal to install it:
```
sudo apt-get install rtorrent
```

---

### Post by haxer on 2006-09-11
Ok maybe a little bit more easy for a noob like azureus or ktorrent but not those programs :) Otherwise if i was a total complete super X hacker i maybe would have tried rtorrent :)

---

### Post by Anonii on 2006-09-12
> **haxer said:**
> Ok maybe a little bit more easy for a noob like azureus or ktorrent but not those programs :) Otherwise if i was a total complete super X hacker i maybe would have tried rtorrent :)
Please, rtorrent is easy as shit to use. Really. And anyway, if you plan on using Linux, you should be confident with the command line. There are many pros of the command line, and you should learn to stop beeing afraid of it, and use it.

---

### Post by haxer on 2006-09-12
okej hmm.. when i typed in rtorrent in the terminal i got a text based really ugly program i think i dont know but i was a little to scary for me and i have only used ubuntu for about 4 days now the only thing i can say is that i love linux havent been to "windows" for about 4 days and it feels great :)

---

### Post by Anonii on 2006-09-12
> **haxer said:**
> okej hmm.. when i typed in rtorrent in the terminal i got a text based really ugly program i think i dont know but i was a little to scary for me and i have only used ubuntu for about 4 days now the only thing i can say is that i love linux havent been to "windows" for about 4 days and it feels great :)
Ok since you didnt like rtorrent, try a program with a GUI, like tribler.
[http://ubuntuforums.org/showthread.php?t=234700](http://ubuntuforums.org/showthread.php?t=234700)

Its freaking easy to use, and it is fast.
For fast installation:
[http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb](http://membres.lycos.fr/bou3ou/packages/tribler_3.5.0-0ubuntu3_i386.deb)
after downloading this, from the console (Cant help it, this time) go to the directory which is downloaded, and use this command:
_sudo dpkg -i trib*.deb_
If it was installed succesfully without problems, a tribler icon will be on  your menu, under the internet category. OR you can just use the command tribler to open it :)

---

### Post by kanem on 2006-09-12
Are you using GNOME? Have you tried just double-clicking on the torrent file? By default, that should start GNOME's built-in bittorrent client. It's really simple. Too simple some might say, but I like it fine.

---

### Post by madmetal on 2006-09-12
> **kanem said:**
> Are you using GNOME? Have you tried just double-clicking on the torrent file? By default, that should start GNOME's built-in bittorrent client. It's really simple. Too simple some might say, but I like it fine.

i am also new to torrents and did that.
the transfer seems to begin but i have nothing downloaded...
what else should i do? 
should i use port forward and how can i change gnome's bittorrent settings?

---

### Post by bodhi.zazen on 2006-09-12
I second the vote for utorrent with wine. Very light and easy setup. utorrent is not microsoft, but it is a fast, full featured torrent client.

---

### Post by 3rr0r on 2006-09-12
I thought wine was very difficult to configure and get working??

---

### Post by Anonii on 2006-09-12
> **3rr0r said:**
> I thought wine was very difficult to configure and get working??
[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

Wrong. 
:P

---

### Post by bodhi.zazen on 2006-09-12
> **3rr0r said:**
> I thought wine was very difficult to configure and get working??

Yes and no. Wine is easy to install and configure. All you need to do is install wine via synaptic and type
```
winecfg
```
This will set up a fake c drive in ~/.wine

Now the hard part.... getting applications to work. This is the hard part.

In the case of utorrent, however, it is not hard at all.
[Ubuntu How-to utorrent](http://ubuntuforums.org/showthread.php?t=191161)

---

### Post by 3rr0r on 2006-09-12
Sounds like something worth checking out.  I was running Frostwire and I hate it.  It lags your entire system when you start doing any downloading, even when I set the bandwidth cap to 60%

---

### Post by moore.bryan on 2006-09-12
*i've had great experience with bittornado ```
sudo apt-get install bittornado && sudo apt-get install bittornado-gui
``` nice gui and fully customizable...*

---

### Post by Peepsalot on 2006-10-21
What's wrong with azureus?

---

### Post by Anonii on 2006-10-21
> **Peepsalot said:**
> What's wrong with azureus?
It uses Java => It requires and drains resources like mad.

---

### Post by DrMilo on 2006-10-21
Is very good. Not a torrent program, more like Froistwire etc. You will have to fiddle with the configuration, eg set up filters, for it to be convenient but it's worth the effort!

You can add it through package manager or Automatix, if you have Automatix.

---

