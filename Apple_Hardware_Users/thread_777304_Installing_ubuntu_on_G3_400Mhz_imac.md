---
title: "Installing ubuntu on G3 400Mhz imac?????"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-05-01
I have htis problem with xubuntu 8.04 as my previous thread mentioned....I was wondering, will kubuntu or plain jane ubuntu work where xubuntu did not???

I also tried to isntall Gentoo,,I did everything jsut like they said in the handbook, it took HOURS. Then, I rebooted, and I get this friendly corrupt or missing file system notice when I try to type in the Linux command at second boot prompt....oh well.

If that does not work...what is the most current Linux OS that will work adn does not require me burning a DVD, because I do nto have blank DVDs???

---

### Post by abtabt on 2008-05-01
i have now  installd 804 on a imac 333mhz 96 mb ram

works like a charm 

xubuntu-desktop

but i use icewm 

start with the server installation 

then apply what you want

---

### Post by stream303 on 2008-05-01
abtabt: That is great news, especially with only 96mb!  Glad to see a server-install being used for a desktop with minimal ram..

shgadwa: I've got a feeling that no matter what recent distro you use, you will still have to disable glx and dri for that ati-rage-128 card.

Have you tried modifying your /etc/X11/xorg.conf file, especially in regards to steps 3 and 4 of the following:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

---

### Post by avtolle on 2008-05-01
shgadwa: given all your problems, I'm wondering two things. One: is the graphics card functional (you mentioned at some point that you had acquired various computers from owners)? Two, have you done this ```

free-m
```
from the terminal, command line, whatever, to ensure there is in fact 512 Mb RAM, or are you relying upon the person from whom you acquired the computer?

---

### Post by shgadwa on 2008-05-01
Yes, I did edit the xorg.conf file. I did not try the free-m thing....

Well, I tried kubuntu. For some reason, it never worked because it was never able to properly install yaboot boot loader, it always said it could not install it. I tried three times.

Right now, it is finishing up with the 2007 version of debian....hope that works :)

---

### Post by stream303 on 2008-05-02
> **shgadwa said:**
> I did not try the free-m thing....

Please try that and report the results here.

```
free -m
```
note the space.

It is vitally important to us to see what amount of memory the computer thinks it has, even if you have been told otherwise, or seem to have ram filling the slots.

This will tell us something I suspect (although I could be wrong) if your ram is actually very low.

1) Someone has sold you a "512" mb box, by merely putting in some 3rd-party ram into an empty slot.

2) Even if that ram is ok spec-wise for your box, if they have NOT performed a firmware upgrade, it is unlikely to work.  Either that, or the ram is actually bad.

3) If we find out that in fact, a firmware upgrade has not been performed, it might be an indicator that you have to limit your hard drive partitioning to less than 8gb total - ideally 7gb.

If you have the machine I think you do, it was a transitionary model that for some models, it had the 7gb limitation, and later versions did not.

By performing the memory-check, and posting the results of the output here, we can save a lot of time.

Otherwise, I believe we may be just chasing our tails.

**WARNING** - the firmware upgrade can ONLY be performed from a working install on the HARD-DRIVE with the older Mac-Os.  DO NOT attempt to run any OSX installers or other OSX utilities on the machine unless the firmware has been upgraded FIRST.

So run the free -m command and let us know what it shows.

---

### Post by shgadwa on 2008-05-02
The memory is 512MB RAM. I know because this computer was running drapper just fine before and it said in the terminal that it had 512MB ram.

---

### Post by stream303 on 2008-05-02
Well, since you don't plan on keeping this machine, and need to turn it around, Dapper will be supported for awhile yet.  Perhaps reinstall that since it won't be a keeper.  In the sources prefs, enable the backports repository.

With Hardy, there may be issues with ram, so please post the output of free -m here and we can take it further - otherwise, anything beyond this may be for nought.

---

### Post by shgadwa on 2008-05-02
well, I will keep it for maybe another 4-5 months or until i ahve the money to buy a brand new mac book. then I can properly do my business.

For now, i installed openSUSE network install on it. seems to work fine though it is a little slower than drapper, yet more advanced and I think it has a better photo organizer. What do all you guys think of openSUSE 10.3????

I am kind of undecided right now...I might try to run xubuntu 8.04 server and then install the desktop environment and configure the X11/xorg.conf. file...is that all I need to do?

OR, I could run mac OS X which is a GREAT OS but slower than linux on this box. When i get my macbook, I will run mac OS X on it as well as Linux, windows and other OSes.

Also, about speed, would making a larger swap partition drive increase speed? I think it would. How can I do that without reinstalling the OS?

THANKS!

---

