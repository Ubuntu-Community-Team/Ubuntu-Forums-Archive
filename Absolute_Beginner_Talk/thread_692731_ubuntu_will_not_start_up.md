---
title: "ubuntu will not start up"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by xecure on 2008-02-10
I connected my laptop to a LCD TV via a VGA cable. When i unplugged the cable the window titles and windows seemed a little wierd to me so i tried to restart my ubuntu. My ubuntu did not restart, after the ubuntu logo my screen flashes a few times and then an error message is displayed: "bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available or load failed ubuntu 162"  I have no clue what i did to have made this happen (recently played around with the xorg.conf file, but restarted after that a few times and it restarted fine)

---

### Post by gulliccj on 2008-02-10
The problem may lye with a confused video card, so if it is a desktop (with a video card), unplug the card, and then boot the computer. if it is a laptop or a desktop with an onboard graphics array, then you will have to reinstall ubuntu. Sorry for your loss.:(

---

### Post by xecure on 2008-02-10
will i lose all my files? i dual boot my laptop with vista, is there any possible way to recover them via vista before i reinstall ubuntu?

---

### Post by JoshuaRL on 2008-02-10
I wouldn't go that far yet.  When I was getting my Radeon Mobility card running I reinstalled 4 times, but now I know that you rarely need to reinstall.  Can you boot into rescue mode?

---

### Post by xecure on 2008-02-10
no i cant even do that

---

### Post by JoshuaRL on 2008-02-11
I have no idea what this is, but someone on this thread on page 37 put out the same error as you:

[http://ubuntuforums.org/showthread.php?t=442483&page=37](http://ubuntuforums.org/showthread.php?t=442483&page=37)

post number 369.

---

### Post by aquavitae on 2008-02-11
Can you boot off a live cd?  Then you can access your files and find out what you changed in xorg.conf - I don't know if this is the problem but its a start point.  Also, maybe a screenshot of the error message would help (with a camera:))

---

### Post by oedha on 2008-02-11
it happen to me last week when i plug and unplug from an LCD projector....
it was because the second display was not correctly configured.
i just did :==> sudo-reconfigure -phigh xserver-xorg
twice.....first when the LCD attached...the second....with LCD unplugged
now...i have no problem like that again....would you like to try ?

---

### Post by xecure on 2008-02-11
I  took a picture of the error but it sucks. i don't have access to a camera other then my cell phone camera. But this is basically what it says:```
[     21.100000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
 * starting anac(h)ronistic cron anacron
 * Starting deferred execution scheduler atd
 * starting periodic command scheduler crond
 * enabling additional executable binary formats binfmt-support
 * Checking battery state ...
 Running local boot scripts (/etc/re.local)
```
Also, I tried starting up in rescue mode, and it works. (sorry about before, i thought i couldn't)[IMG]http://img116.imageshack.us/img116/2479/photo0043sp8.jpg[/IMG]

---

### Post by JoshuaRL on 2008-02-11
Alright, what happens when you do the following from rescue mode:

```

startx

```

---

### Post by xecure on 2008-02-11
my screen flickers and then i get a whole bunch of error messages and then at the end of the message it says:```
Fatal server error:
failed to initialize core devices
XIO:   fatal IO error 104 (connection reset by peer) on X server ":0,0"
       after 0 requests (0 known processed) with 0 events remaining

```

---

### Post by Sinkingships7 on 2008-02-11
i may have over-looked something, but can you boot from your live cd?

---

### Post by jw5801 on 2008-02-11
bcm43xx_microcode.fw relates to the bcm43xx series of wireless chipsets. Were you recently trying to get wireless working using bcm43xx-fwcutter? If so, the first place I'd think to check would be /etc/modules, to make sure it doesn't mention anything about bcm43xx, try ```
cat /etc/modules
```from your rescue terminal.

---

### Post by gulliccj on 2008-02-11
The best thing that i think you can do is to boot from a live CD, OR wipe the hard drive. Other than that this seems like your DELL laptop isn't configured correctly for the TV.

---

### Post by xecure on 2008-02-12
so i cant save it at all?

---

### Post by jw5801 on 2008-02-12
Of course you can, you just need to identify what was changed between when it was running and now. This can be an onerous task when it comes to the X server, however, so it can often be easier to reinstall. If it drops you to a root terminal however then you can quite easily copy anything you want to keep to a different partition or device. I personally keep my /home directory on a seperate partition, that way I keep all my application settings over a fresh install, it's just a matter of reinstalling them and applying any tweaks I had!

Now, you mentioned that you altered your Xorg.conf? What changed in it? If you ran a script to alter it (aticonfig or something similar) then it's almost guaranteed that the script made a backup of your old config so restoring it should fix the issue. I don't think we're quite at the reinstalling stage yet!

From your root shell, run:
```
ls -la /etc/X11/
```
That will tell you how recently each of the files in there were altered, the ones we're interested in are xorg.conf and the same with any other extension. If you notice that the last updated time for xorg.conf is around about the same time you stopped being able to load X, then I think we might be onto something! You'd probably also notice that there's a backup with another file extension (xorg.conf.failsafe or similar) that was last altered slightly before the one that's not working! In that case try:
```
cd /etc/X11/
mv xorg.conf xorg.conf.false
mv *xorg.conf.backup* xorg.conf
startx
```
The italics you'll need to replace with whatever the backup is actually called. I'm also assuming you're in a root shell, if you're logged in as a user then you'll need to use "sudo" to move the files. If you're unsure, post back here! I won't be around for a few hours but someone else can probably help.

---

### Post by xecure on 2008-02-13
The last updated time for xorg.conf is around the same time I stopped being able to load X, I have also tried what you said jw5801, it does not work for me it gives me an error after i type on startx as before. I can also boot from the live CD. Any other possibilities

---

### Post by xecure on 2008-02-13
I've decided to go ahead and just reinstall. I put in my install CD and when I choose start or install ubuntu it just run ubuntu from the CD. Ho do i reinstall ubuntu?

---

### Post by jw5801 on 2008-02-13
Well it's something in xorg.conf that's causing the problem!

If you want to reinstall you do it the same way as you did when you installed first off. Click on the install icon from the livecd and follow the prompts. When it gets to the partitioning section, make sure that it's installing over the partition you have at the moment.

Another thing to maybe try before you reinstall. Try replacing the xorg.conf you have with the one on the LiveCD, then try booting your system and see how it does! It should be a relatively failsafe xorg.conf.

---

### Post by xecure on 2008-02-13
its too late for that. i already wiped the partition.

when i first installed i put the CD in, hit restart and then the installation process started. When i hit install now it seems to boot linux from the CD

---

### Post by jw5801 on 2008-02-13
Did you use the alternate CD the first time around? The LiveCD will boot into it's own environment and the installer runs from there.

---

### Post by xecure on 2008-02-15
is it possible to install ubuntu with the live CD? if so how ouwldi do it?

---

### Post by jw5801 on 2008-02-15
When the LiveCD environment loads, double click on the icon that says "install" that's on the Desktop.

---

### Post by xecure on 2008-02-15
wow...
I am so lethargic sometimes...

---

### Post by xecure on 2008-02-15
> **jw5801 said:**
> I personally keep my /home directory on a seperate partition, that way I keep all my application settings over a fresh install, 
Also, how would i do that?

---

### Post by jw5801 on 2008-02-15
There's a good guide on the psychocats site:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

