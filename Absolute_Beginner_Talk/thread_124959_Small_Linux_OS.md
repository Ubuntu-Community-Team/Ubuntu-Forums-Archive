---
title: "Small Linux OS?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by viper474 on 2006-02-02
Hello, I need to find some kind of linux os that can run on my old Windows 98 laptop.  It is a Intel MMX 266 processor, it's got about 3 GB of space (like I said, old), and 96 MB of RAM.  Anyone got any ideas?

Edit: Hello, the computer brand and model is NEC 330T, I'm having trouble getting the thing to boot from the CD.  I have set it to the top of my bios list on what to run first (cd,floppy, hard drive).  Are there any key combos that might get this thing to boot from disk?  Either that or would you thing it might be my Cd-Rom drivers?

---

### Post by viper474 on 2006-02-02
I've downloaded and tried installing Puppy Linux, but it just holds for a few seconds then starts normal Windows boot.  I looked at the site and noticed I needed a required 128 MB of RAM...so...that's not going to work out.  Just to let those who'd recommend that version.

---

### Post by Zelut on 2006-02-02
I've got similar specs on a machine.  It isn't lightning fast (nothing with those specs will be) but its useable.

I installed 'server' ubuntu on the machine & then added xubuntu-desktop & gdm.  This runs Xfce desktop instead of gnome (which is heavier & takes up more space).  You could give that a try..

---

### Post by viper474 on 2006-02-02
The server version of ubuntu?  How different is that from the normal and how will it help my situation?

---

### Post by madmetal on 2006-02-02
try what kuyaedz suggests..
also look at ubuntu lite or damn small linux if you want more options.

---

### Post by Zelut on 2006-02-02
If you install server it doesn't install any extras, graphical desktop managers, etc.  Its the bare-bones 'terminal-only' version of ubuntu.  That saves A LOT of disk space.  (My full installation including Xfce is still under 1G using that method.)

Then if you install a lighter graphical desktop manager like Xfce it still doesn't add much to the hard disk & runs MUCH lighter on the processor than gnome or KDE.

---

### Post by carlosqueso on 2006-02-02
Also you can install IceWM if you want to go even lighter

```
sudo apt-get install gdm icewm menu icewm-gnome-support
``` It's a pretty light window manager that'll make you feel at home if you're coming from windows.   Not as easily configurable as Xfce, but has good keyboard support and some really cool themes.

EDIT: do this after a server install--just to make sure it's clear.

---

### Post by cwaldbieser on 2006-02-02
[QUOTE=viper474]Hello, I need to find some kind of linux os that can run on my old Windows 98 laptop.  It is a Intel MMX 266 processor, it's got about 3 GB of space (like I said, old), and 96 MB of RAM.  Anyone got any ideas?[/QUOTE]
Have you tried this?
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

---

### Post by viper474 on 2006-02-02
I haven't tried the d*** small linux program, but my main concern is the memory on my laptop.

---

### Post by Protex on 2006-02-02
[QUOTE=viper474]I haven't tried the d*** small linux program, but my main concern is the memory on my laptop.[/QUOTE]

DSL will run, trust me. It's intended for systems with low specs.

---

### Post by AndyCooll on 2006-02-02
[QUOTE=Protex]DSL will run, trust me. It's intended for systems with low specs.[/QUOTE]

And despite what you may have read on the website Puppy Linux 
**will** run ok on your laptop. It runs perfectly ok on my 166/32mb laptop.

By the way, to stop it jumping in to Windoze have you changed the bios settings?
And if that don't work, I remember that on another of my old laptops you had to hit a key (F7 IIRC) to bring up some options, one of which was to boot from CD

:cool:

---

### Post by viper474 on 2006-02-02
Um...stupid question here, maybe, um...how do you download dsl?  It keeps showing me these lists of files.  How do I just download the whole thing?

---

### Post by viper474 on 2006-02-02
Well, um...on the puppy software, I'm not exactly sure what's messing up then.  I have the floppy, cd, then the hard drive.  Do I have to move the cd up to the top?  It's either that or when I restarted in MS-Dos it told me something about CD-ROM drivers.  Just don't jump to conclusions about the drivers, I may have read it wrong.

---

### Post by sabredog on 2006-02-02
I have a P166MMX with 128Mb and 2x1Gb HDD's.

I currently have Feather Linux installed which I am not no keen on.

What Ubuntu flavour would work on this PC?

Would Xubuntu or Ubuntu Lite be the way to go?

Otherwise it may well be easier to re-install Win98SE...

Cheers and thanks

---

### Post by viper474 on 2006-02-02
> I have a P166MMX with 128Mb and 2x1Gb HDD's.

I currently have Feather Linux installed which I am not no keen on.

What Ubuntu flavour would work on this PC?

Would Xubuntu or Ubuntu Lite be the way to go?

Otherwise it may well be easier to re-install Win98SE...

Cheers and thanks
Nah, the thing's a peice of junk compared to our other 2 computers.  The only reason I have it out is I wanna use it to try Linux even without using a Live version on this computer.  I just can't get the thing to boot from the disk I suppose...I have gone into the BIOS and told it to do the cd first, floppy next, and then hard drive.  I haven't found a button combination to let me say distinctively "boot from disk."  By the way, my laptop is a NEC Ready 330T.

---

### Post by AndyCooll on 2006-02-02
[QUOTE=viper474]Well, um...on the puppy software, I'm not exactly sure what's messing up then.  I have the floppy, cd, then the hard drive.  Do I have to move the cd up to the top?  It's either that or when I restarted in MS-Dos it told me something about CD-ROM drivers.  Just don't jump to conclusions about the drivers, I may have read it wrong.[/QUOTE]

Yes, you need to change the bios settings so that the boot order has the CD drive as the first choice.

:cool:

---

### Post by viper474 on 2006-02-02
> Yes, you need to change the bios settings so that the boot order has the CD drive as the first choice.
I tried that.  It just goes through like normal booting.  If I was to need to replace the drivers (which would be a pain) is there a website I could get them off of?

---

### Post by AndyCooll on 2006-02-02
[QUOTE=sabredog]I have a P166MMX with 128Mb and 2x1Gb HDD's.

I currently have Feather Linux installed which I am not no keen on.

What Ubuntu flavour would work on this PC?

Would Xubuntu or Ubuntu Lite be the way to go?

Otherwise it may well be easier to re-install Win98SE...

Cheers and thanks[/QUOTE]

Not sure how knowledgeable you are with Linux. It is possible to install Puppy Linux on that. Or you can use Puppy Linux as a Live CD, but store the files on the hard disk only.

I haven't tried either Lite or Xubuntu. Pays your money takes your pick. Though reading the Lite thread it looks as if it'll do the trick.

:cool:

---

### Post by xXx 0wn3d xXx on 2006-02-02
try this: start your computer, then insert the cd and restart. It will boot from the cd. My computer is also old and doesn't have the bios option. this is how I did it :)

---

### Post by viper474 on 2006-02-02
MasterCheif1234, I have tried this, but it doesn't seem to work with my computer.

---

### Post by AndyCooll on 2006-02-02
[QUOTE=viper474]I tried that.  It just goes through like normal booting.  If I was to need to replace the drivers (which would be a pain) is there a website I could get them off of?[/QUOTE]

Yeah sorry, was writing and posting as you were doing an update. It's not the drivers. As I mentioned before as another possibility. It may be that you need to try a combination of keys to first halt its boot sequence. I had a laptop displaying similar properties to what yours does and even though the bios settings told it to select the CD drive first it didn't seem to work. I solved it by chance when selecting a combination of keys on a boot up.

I've never tried it, but I believe there is a Linux boot floppy disk that might work, i.e boot from that and then choose the CD drive (it was how the early Linux OS's were installed). Just a thought.

:cool:

---

### Post by viper474 on 2006-02-02
> I've never tried it, but I believe there is a Linux boot floppy disk that might work, i.e boot from that and then choose the CD drive (it was how the early Linux OS's were installed). Just a thought.
Problem is, with this laptop you can either have the Cd drive in or the floppy, not both :-(

---

### Post by viper474 on 2006-02-02
Any more ideas anyone?

---

### Post by Alapelli on 2006-02-02
Don't know if you have USB port on your laptop ?  I was also tired of changing the Cd to Floppy on my Laptop, so I bought for around $35.00 CDN a USB floppy.
May be an expensive solution but, you asked for suggestions :D 
That way you should be able to use both

---

### Post by viper474 on 2006-02-02
Yeah, thanks for the comment, but I'm not planning to spend any extra money than the electricity, cd, and time.

---

### Post by xequence on 2006-02-02
Damn Small Linux worked on my Pentium 77Mhz, with 16 MB RAM

---

### Post by sabredog on 2006-02-02
[QUOTE=AndyCooll]Not sure how knowledgeable you are with Linux. It is possible to install Puppy Linux on that. Or you can use Puppy Linux as a Live CD, but store the files on the hard disk only.

I haven't tried either Lite or Xubuntu. Pays your money takes your pick. Though reading the Lite thread it looks as if it'll do the trick.

:cool:[/QUOTE]

I am a Linux newbie, but learning fast in between busy work and family life.

I have DL'ed the Ubuntu Lite ISO so will have a play with that. Essentially I want something on this PC that resembles Win98SE's functionality. It will be disconnected from the home LAN once all is installed and used as a standalone workstation.

cheers and thanks

---

