---
title: "Ubuntu Studio"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by baumgc on 2008-02-22
_**Backstory**_
I've always been interested in Ubuntu since Warty Warthog, but never had a real reason to run it. Then I stumbled upon Ubuntu Studio. Being someone who is creative/poor. I figured it would be at least worth a shot since the proapps are so outrageously expensive. I also don't believe in stealing software as I am a computer programmer myself (albeit in college, but regardless).
I'm quite impressed with what came with ubuntu studio, and I still have some testing to do. I used ubuntu frequently when my hard drive failed in my Macbook (it was apart of a bad batch of Seagate drives). I just ran the live disc and things worked great! 
When I got my hard drive replaced, I partitioned a space for Studio to give it a whirl. Anyway, I still have a few bugs to work out and was wondering if I could get some help. They go in order of importance.

_**Issues**_
-_Wifi:_ I can't get it to work with the directions from the macbook page ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)). It asks me to set the kernel path. I thought this was strange. Isn't Ubuntu Studio regular Ubuntu with all the editing apps pre-installed?
-_Touchpad:_ I want it to work like it does in OS X. Double tap to right click. Two finger scroll. Etc. The xorg thinger on the Macbook page didn't work for me.
-_Volume Control/Brightness:_ The buttons work on my keyboard, but nothing happens. Imagine my shock when I tried to show my buddy Ubuntu Studio (thinking I had muted it), and it did its whole song and dance when you log in.... in class. 
-_Function Keys:_ How can I make it so that I don't have to hold 'fn' to use my function keys? I want it to be reversed.
-_Super<-->Control:_ I think the Ubuntu equivalent of apple/command is called super, right? I'm so used to the mac platform that I still press super+c, and super+v and wonder why nothing happens. Is there a way I can flip flop these keys?

Thanks for all the support!

Extra Info:
I updated Studio and it appears to be running at 7.10.
My Mac is a June '07 model with:
2.16 C2D
1 GB
950 GMA
--Not Santa Rosa--
I have been able to get wifi running in regular ubuntu on my mac, but not in studio.

---

### Post by cyberdork33 on 2008-02-22
> **baumgc said:**
> -_Wifi:_ I can't get it to work with the directions from the macbook page ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)). It asks me to set the kernel path. I thought this was strange. Isn't Ubuntu Studio regular Ubuntu with all the editing apps pre-installed?
yes, for the most part. It uses a different kernel as standard (real time), and has some different configurations that are more geared toward media creators. I am going to guess that it is looking for the kernel-headers and cannot find them. Can you try installing them first and try to compile madwifi again?
```
sudo aptitude install linux-headers
```
> **baumgc said:**
> -_Touchpad:_ I want it to work like it does in OS X. Double tap to right click. Two finger scroll. Etc. The xorg thinger on the Macbook page didn't work for me.Unfortunately I cannot help much here. There is a thread that goes into better detail about the various options. It might be helpful to get things to work correctly. [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)
> **baumgc said:**
>  -_Volume Control/Brightness:_ The buttons work on my keyboard, but nothing happens. Imagine my shock when I tried to show my buddy Ubuntu Studio (thinking I had muted it), and it did its whole song and dance when you log in.... in class. try installing pommed, and as for the volume buttons, it might be that "PCM" is the wrong channel to operate (as instructed in the Macbook wiki you linked to). The channel operated by default is usually not the right one on a Mac for some reason. You might have to try selecting various channels to see which one does what you want. You can play some music and run alsamixer to find the channel you need.
> **baumgc said:**
>  -_Function Keys:_ How can I make it so that I don't have to hold 'fn' to use my function keys? I want it to be reversed.I still understand why this is always reversed by default in ubutnu, but I believe it can be fixed with pommed as well. (edit /etc/pommed.conf by changing the value of fnmode).
> **baumgc said:**
>  -_Super<-->Control:_ I think the Ubuntu equivalent of apple/command is called super, right? I'm so used to the mac platform that I still press super+c, and super+v and wonder why nothing happens. Is there a way I can flip flop these keys?I know that there are other people out there doing this, though I have never tried it myself.
[http://ubuntuforums.org/showthread.php?t=48448](http://ubuntuforums.org/showthread.php?t=48448)
[http://www.extremetech.com/article2/0,1697,2126239,00.asp](http://www.extremetech.com/article2/0,1697,2126239,00.asp)

---

### Post by baumgc on 2008-02-22
Thanks. I'll go through these changes when I have an ethernet connection. Hopefully everything goes as planned

---

