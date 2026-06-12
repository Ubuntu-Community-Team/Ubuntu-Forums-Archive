---
title: "Why is ATI video so slow (feisty gutsy restricted-drivers)"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Rene7705 on 2007-10-02
Hi..

I have a windoze XP laptop that's 3 years older than my recently bought box but my new box with new midrange ATI video is slower than the old XP laptop in 2D video operations, especially with semitransparent windows.
(plz provide me with command that shows me which videocard/drivers i have installed)..

I build a CMS with a lot of draggable semitransparent windows, and in dragging those windows under Ubuntu/FF is literally 5-8 times slower than on a XP that's 3 / 4 years older.
On that XP laptop, I can drag the windows "live" and it updates the screen while dragging (onMouseMove) correctly. 
On Ubuntu, i'm lucky to get a screenupdate every 3 to 4 seconds while dragging..

And it's not just FF / transparent windows.. It's virtually all window operations on complexly-filled windows...

I'm sorry to say that despite me Loving opensource, i'm moving back to vista/xp, because I couldn't find a fix to these 2D video issues.. If you have one, please-o-please let me know.. If I need to run a different flavor of Ubuntu (or even another linux distro) then i'm willing to.

I was considering contributing code to curlftpfs or another FTPS / FTP over SSH library (caching features and automated retries and statuswindows), but that won't happen if I can't use Ubuntu as my primary OS.
And while there's something to be said for developing on a platform with slow 2D video-operations, it's just *too* frustratinly slow in Ubuntu/ATI right now..

But if there's a fix for these video issues (upcoming), i'd love to hear about it asap..
Vista sucks too. ;)

---

### Post by Kubunteando on 2007-10-02
What is your ATI model?

What drivers version are installed?

I sounds strange to me. The 2D acceleration has been working quite ok with ATI cards.

---

### Post by Rene7705 on 2007-10-03
> **Kubunteando said:**
> What is your ATI model?

What drivers version are installed?

I sounds strange to me. The 2D acceleration has been working quite ok with ATI cards.

Sorry i dont know the commands to retrieve that information..
if u tell me the commands i'll let u know..

---

### Post by markoloka on 2007-10-03
Try fglrxinfo on terminal. Are you using feisty or gutsy??? In gutsy beta my ati (rx2400pro) is like swimming in tar when i use kde or dolphin or kongueror or so (even kate)...only firefox scrolls fast etc. 
I used this advice to install my ati...[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Is your problem similar to this topic: [http://ubuntuforums.org/showthread.php?t=565958&highlight=ati+wiki](http://ubuntuforums.org/showthread.php?t=565958&highlight=ati+wiki)

---

### Post by Rene7705 on 2007-10-03
> **markoloka said:**
> Try fglrxinfo on terminal. Are you using feisty or gutsy??? In gutsy beta my ati (rx2400pro) is like swimming in tar when i use kde or dolphin or kongueror or so (even kate)...only firefox scrolls fast etc. 
I used this advice to install my ati...[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)


:~$sudo apt-get install linux-restricted-modules-$(uname -r) # (Okay if it is already installed)
...
Reading state information... Done
linux-restricted-modules-2.6.22-12-generic is already the newest version.

:~$sudo apt-get install xorg-driver-fglrx
...
Reading state information... Done
xorg-driver-fglrx is already the newest version.

> **markoloka said:**
> 
Is your problem similar to this topic: [http://ubuntuforums.org/showthread.php?t=565958&highlight=ati+wiki](http://ubuntuforums.org/showthread.php?t=565958&highlight=ati+wiki)

Eh no, it display just fine, and with normal webpages video responsiveness is good enough.. It's complicated windows with high widget/picture density (and transparency) that's too slow..

---

### Post by Rene7705 on 2007-10-03
It's "solved".. Transparent divs in firefox can now be dragged with semi-smoothness, screen updates <1second instead of 3-4 seconds..

I think the solution was an upgrade of the linux-restricted-drivers by "upgrade manager"'s "partial upgrade" feature that I was offered this mornin..

[http://ubuntuforums.org/showthread.php?p=3467017#post3467017](http://ubuntuforums.org/showthread.php?p=3467017#post3467017)

---

