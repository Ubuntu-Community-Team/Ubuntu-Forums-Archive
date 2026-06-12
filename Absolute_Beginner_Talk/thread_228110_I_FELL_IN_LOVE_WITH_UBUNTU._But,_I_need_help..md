---
title: "I FELL IN LOVE WITH UBUNTU. But, I need help."
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by bitdefuser on 2006-08-02
This is the most greatest thing ever!!@!@@!!@!@ :p :p :p :p 

But, I really want to use window programs too like CS2 and Microsoft word.  I also want to play 3d video games like windows does.

What can I do to use those on Ubuntu?
I heard Wine can do it but you have to enter some code. I don't want to do that everytime. So can you give me a suggestion? :???: 

MANY THANKS TO ALL. 8-)

---

### Post by bitdefuser on 2006-08-02
Bump please.

---

### Post by GuitarHero on 2006-08-02
Install wine with automatix, type winecfg, then wine -i (path of exe) to run an installer.  For games you need cedega.  I think theres a howto for installing that.  Search for it, its your best bet for games.  Some 3d games like doom3, UT2004, and Wolfenstein ET are linux native, but for most you need cegeda.  Don't bother with Microsoft Office.  OpenOffice.org is just as good.  It misses a few features ms office has, but most likely its not anything you use.  I think CS2 should work with wine, but unless you do professional graphic work for a living, you should try to use GIMP.  Using native linux apps is always best for speed, stability, and supporting open source software.

---

### Post by christhemonkey on 2006-08-02
You can either:
Dual Boot.
Ease and convenience of being able to run *any* windows programs and linux programs!

Emulate windows:
Run any windows programs whilst still being on ubuntu, but big hit on system resources.

Run in wine/cedega/cross over office:
Actually runs programs under ubuntu, but as you say:
> but you have to enter some code. I don't want to do that 

---

### Post by christhemonkey on 2006-08-02
EDIT: double post.
Seems like a lot of this has been happening recently...

---

### Post by GuitarHero on 2006-08-02
Oh yeah, i should have mentioned, dual booting is the best option for gaming if you can do it, not very conveiniant for photo editing or word processing.  I keep windows around just for gaming.  If you dont want to do that, ive heard good things about cedega so its definatly worth a try.  Emulation can be tricky, but if all else fails its worth a go.  Oh and welcome to Ubuntu.

---

### Post by bitdefuser on 2006-08-02
Dual boot requires two hard drives? 



And the guy who said that automatic thing for Wine, It will act like it is running under windows without me enterting anything?

Will it allow me to run any program?

---

### Post by christhemonkey on 2006-08-02
Dual boot requires two different partitions on your hard drive.
Not 2 hard drives (although if you have 2 hard drives you can still dual boot!)

Wine is a windows compatibility layer.
Basically, they wrote dll's and stuff from windows so they work in linux natively.
So it is not emulated but actually run as a linux program.

Wine is not too hard to setup, but different programs have different success'.

---

### Post by christhemonkey on 2006-08-02
EDIT: Why am i double posting?! i only click the button once...

And how do i delete posts?
Can only admins do that?

---

### Post by bitdefuser on 2006-08-02
Dual booting.
Does this allow me to use windows program strait from ubuntu? Or do I have to restart and boot into windows in order to use it.

---

### Post by bitdefuser on 2006-08-02
Dual booting.
Does this allow me to use windows program strait from ubuntu? Or do I have to restart and boot into windows in order to use it. :confused:

---

### Post by bitdefuser on 2006-08-02
Bump please.

---

### Post by orb9220 on 2006-08-02
You will have to boot into windows. But the advantages are better by having two OS's xp for games and graphics like CS. And down the road new games and apps that you would like to try might not be supported by wine.

Having a 20 gig partition for xp is great alternative to wine and worring about config wine and emulation in linux.

If there are some programs you can't do without and need in xp then stick with xp to use them. 

It is easier to have the working xp part. 

You then can try out the wine emulation for games and other programs and if they don't work right then you still have the xp working side.

---

### Post by drosophyllum on 2006-08-02
Its really really easy, just boot from the cd, and install, when you install just resize your windows instead of erasing your entire drive.

there even is a google video of how to do this lol....


[http://video.google.com/videoplay?docid=-6104490811311898236&q=dual+boot+ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=dual+boot+ubuntu)

---

### Post by nalmeth on 2006-08-02
Have you tried abiword? It may replace Microsoft Word for you.

You can try Cedega for your 3D games, but as suggested, if you want 100% for ALL of your games (as you haven't mentioned which ones you play), dual-booting is the  best option to start. 

When you install wine with automatix, simply hit ALT-F2 and enter winecfg to create wine's directories. They are in ~/.wine. They will look like a windows filesystem.

When you find an .exe, right-click it, go into properties, and select wine as the program to open files of this extension. Then you can just double click the .exe like you do in windows.

---

### Post by bitdefuser on 2006-08-02
Thank you nalmeth.

Now I have two questions. (Seperated by the ______'s)
________
Will using Wine slow anything down? or will it run perfectly smooth?

I have the following Specs:

Intel Pentuim M Processor: 1.73 Ghz
1 GB ram
128 mb intregrated graphics.
_________
Another problem. I want to install this into a HP Compaq nx6110 and this page: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

Says that the wireless led doesnt work and tells me to look below.
I don't use infared or bluetooth. I use a built-in 802 wireless. My router is WRT54G from Linksys.

Is this ok?
______________

---

### Post by Tomosaur on 2006-08-02
It depends on the level of wine support for it really. Some things wine is choppy with, others it's perfectly ok. Check the appDB at [http://www.winehq.com](http://www.winehq.com) to see if your program is listed. That way, you can see how well it performs under wine.

---

### Post by bitdefuser on 2006-08-02
I can't seem to find the place where you check if the program is listed. Can you post the link please?

---

### Post by Tomosaur on 2006-08-02
[Certainly](http://appdb.winehq.org/)

---

### Post by abowman on 2006-08-02
> **GuitarHero said:**
> Install wine with automatix, type winecfg, then wine -i (path of exe) to run an installer.  For games you need cedega.  I think theres a howto for installing that.  Search for it, its your best bet for games.  Some 3d games like doom3, UT2004, and Wolfenstein ET are linux native, but for most you need cegeda.  Don't bother with Microsoft Office.  OpenOffice.org is just as good.  It misses a few features ms office has, but most likely its not anything you use.  I think CS2 should work with wine, but unless you do professional graphic work for a living, you should try to use GIMP.  Using native linux apps is always best for speed, stability, and supporting open source software.

Why install automatix to install wine?
Just type:
```

sudo apt-get install wine 

```
Then you should be able to run .exe files by double clicking on them or with the command:
```

wine yourWindowsProgam.exe

```

---

### Post by bitdefuser on 2006-08-02
Last question please.

Another problem. I want to install this into a HP Compaq nx6110 and this page: [https://wiki.ubuntu.com/HardwareSupp...HewlettPackard](https://wiki.ubuntu.com/HardwareSupp...HewlettPackard)

Says that the wireless led doesnt work and tells me to look below.
I don't use infared or bluetooth. I use a built-in 802 wireless. My router is WRT54G from Linksys.

---

### Post by bitdefuser on 2006-08-02
Bump Please.

---

### Post by justintime32 on 2006-08-02
> **bitdefuser said:**
> Last question please.

Another problem. I want to install this into a HP Compaq nx6110 and this page: [https://wiki.ubuntu.com/HardwareSupp...HewlettPackard](https://wiki.ubuntu.com/HardwareSupp...HewlettPackard)

Says that the wireless led doesnt work and tells me to look below.
I don't use infared or bluetooth. I use a built-in 802 wireless. My router is WRT54G from Linksys.

As for the wireless card, make sure it is an IPW2200 (IPW = Intel Pro Wireless) and not a Broadcom card (Broadcom cards are a pain to setup for new users). If it has the Centrino sticker on it, you shouldn't have to worry about this.

Also, please be a little more patient. Not all questions get answered in 7 minutes.

---

