---
title: "Azureus veterans how do you make this program run smooth?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-19
Previously I've been told by some Linux veterans to not run programs especially those in /opt with chmod 777.  But without running Azureus with such permissions it won't be able to update, refresh and do it's thing whenever it wants to.  I can't switch back and forth from 755 and 777 every time Az wants to do something.

> mikey@renaissance:/opt$ **sudo chmod -R 777 azureus**


How do you make Az go smoothly?
Also I've been told that Azureus in Windows is ran as 777 so if I run it with likewise permissions on Ubuntu it won't be worse than in Windows right :confused:

---

### Post by xpod on 2007-07-19
I just used to restart it and run "sudo azureus" from terminal when there was updates. 

Personally i installed ktorrent and all my azureus problems went away:)

---

### Post by pbaehr on 2007-07-19
Have you experienced problems running it normally? I have it installed from the repos and it worked fine with no adjustments to the permissions.

How did you install it?

EDIT: Xpod responded at the same time and reading his post it seems that I am just fortunate that it works, I guess, so never mind. Good luck!

---

### Post by Ralob on 2007-07-19
> **xpod said:**
> I just used to restart it and run "sudo azureus" from terminal when there was updates. 

Personally i installed ktorrent and all my azureus problems went away:)

here here! :guitar:

---

### Post by xpod on 2007-07-19
> Have you experienced problems running it normally? I have it installed from the repos and it worked fine with no adjustments to the permissions.

How did you install it?

EDIT: Xpod responded at the same time and reading his post it seems that I am just fortunate that it works, I guess, so never mind. Good luck!

It sounds like an automatix job to me:)
Thats how i had it installed at the time, with that same permission issue.It was never really a problem though.
I actually liked azureus at first, i`d chose it from amonst others i`d tried but even with the 10meg connection i had at the time i would still suffer slowdowns with browsing & the download speeds were never the greatest either.

Eventually came across ktorrent one day and it zooms along compared to azureus with no browsing slowdowns either.

---

### Post by misfitpierce on 2007-07-19
I installed from automatix 2 and it works flawlessly...

---

### Post by jingo811 on 2007-07-20
> How did you install it?
Automatix.

When running Azureus by default Ubuntu permissions blocks it from performing updates and such.  The program works and so but the updates part get blocked and Az displays a bunch of error messages saying it couldn't complete its tasks.
Does Ktorrent have plugins such as Safepeer?  If so how do you install such plugins I couldn't see instructions for that kind of things?
Can I use Ktorrent with GNOME Desktop?

---

### Post by tomcheng76 on 2007-07-20
just use ktorrent
Azureus always crash and slow + memory hog ....

it has PeerGuardian plugin

---

### Post by jingo811 on 2007-07-20
Will it work on GNOME Desktop?  I don't want to install extra Desktops environment such as KDE in order to run certain programs.  I'm a simple guy with simple needs.

---

### Post by tomcheng76 on 2007-07-20
yup
it work on GNOME Desktop
just run
sudo apt-get install ktorrent

for the dependencies, please read
[http://packages.ubuntu.com/feisty/net/ktorrent](http://packages.ubuntu.com/feisty/net/ktorrent)

---

### Post by tomcheng76 on 2007-07-20
For the PeerGuard Function
Go to KTorrent Setting->Plugin
then choose IP FIlter and load button
IPBlocking tab will come out
i remember that i have to register @ [www.bluetack.co.uk](www.bluetack.co.uk) inorder to dl the ip blacklist

[http://www.bluetack.co.uk/config/splist.zip](http://www.bluetack.co.uk/config/splist.zip)

---

### Post by kerry_s on 2007-07-20
Try gtk-gnutella it's light weight, no java needed. ya just have to get past the ugly, i prefer performance over looks.

---

### Post by jingo811 on 2007-07-20
Tnx I have one last problem with KTorrent.

**IPFilter plugin (PeerGuardian)**
> Error - KTorrent
Timeout on server
Connection was to [www.bluetack.co.uk](www.bluetack.co.uk) at port 80

How do I fix it?

......IC you've posted already :-)
......hmmm Server at blutack seems to be down at the moment guess I'll just have to try later and download that *.zip file manualy.

---

### Post by tomcheng76 on 2007-07-20
try
[http://www.btack.info/splist.zip](http://www.btack.info/splist.zip)
i cannot access bluetack too = =

---

### Post by jingo811 on 2007-07-20
tnx dude you're a life saver! :)

---

### Post by jingo811 on 2007-07-23
I've managed to download that .zip file both from bluetack and from your link.  But I can't convert it?
It's been running for 30 min still it says 0%,  is there something wrong with the plugin?

---

### Post by walkerk on 2007-07-23
try deluge or qbittorrent..

---

### Post by xpod on 2007-07-23
> I've managed to download that .zip file both from bluetack and from your link. But I can't convert it?
It's been running for 30 min still it says 0%, is there something wrong with the plugin?

I had a the same issue myself the first time round with the safepeer plugin.I`m sure just restarting Ktorrent and running it again did the job though.

---

### Post by jingo811 on 2007-07-23
I did that and now it says:
> Status: Loaded and running
But how much is loaded? 10%, 50%, 100%.  Sure would like a little more overview info like in Windows Peerguardian.  I'm trying to do the conversion process after having rebooted it's still gets stuck at 0%.

Maybe it's time to complain to the plugin programmer...

....
....
....mmm seems to be a common bug when searching in the Ktorrent forum.

---

### Post by xpod on 2007-07-23
Downloading...
[ATTACH]38906[/ATTACH]

"Loaded and running":)
[ATTACH]38907[/ATTACH]

---

### Post by jingo811 on 2007-07-23
Yeah me too have that.
Also everytime you try and convert it get stucks at 0% the plugin has some bug, that means I have trouble trusting it even if it says.
> Status: Loaded and running

How much is loaded? 10%, 50%, 100%.  It would be nice to be able to visually confirm how much is truly loaded like in Windows Peerguardian.

---

### Post by kelvin spratt on 2007-07-23
Iv'e used them all using peer garden or safe peer looks a good idea but in my experience they slow down the application and they certainly don't hide  your Ip and what you are downloading from the outside world and if you use a good site you can tell what's good or bad by the comments.The blue frog  needs to be downloaded from soundforge as source, its easy to install in its own folder in your home folder not in system files copy paste the start button to the desktop,its then isolated from the rest of the system when you first run it
java will download to to the blue frog.The secret is to manually set download and upload speeds keep the upload speed as low as possible its the uploading that kills your ram, also disable any non essentials they just use resources enable port forwarding, use a port like 61401  that way the frog will run really well i max out my connection on good downloads, this will basicely set up any app. and Ktorrent as well.I'm running Ktorrent in Feisty, the blue in Elive and Feisty and they both give the same results DHT is the key, and i multitask all the time. 
remember its the eye candy and things not req that use resourcestamel the frog and it will find the seeders or use Ktorrent In my experience Utorrent always starts well then tails of, the other two just get stronger as the download progresses but that's on my system,

---

