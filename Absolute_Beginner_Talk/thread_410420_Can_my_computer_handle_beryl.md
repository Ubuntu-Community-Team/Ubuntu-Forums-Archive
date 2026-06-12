---
title: "Can my computer handle beryl?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Nepenthesrajah on 2007-04-15
Using Ubuntu 6.10 is there a way to test and see if beryl would work on that computer?  I see posts like “Beryl with ATI 1600, fglrx” I’m new to this but I’m assuming ATI is a hardware upgrade.  I just have all standard hardware in my test computer which has a Intel Celeron Processor an 512 ram.  I do have a 2048ram with a Intel Core 2 Dou Processor HP but I don’t really want to be messing with that for a while since I’m still new using Ubuntu.
 
Thanks,
-Jeremiah-

---

### Post by n3tfury on 2007-04-15
you could test your system and get a good idea by running the [Sabayon live cd]("http://www.sabayonlinux.org/")

---

### Post by bobplano on 2007-04-15
well beryl is more graphics than processer so you should post what kind of card you have. ATI (and nvidia) are graphics card makers and ATI 1600 is a card. fglrx are the newest drivers for ATI cards and can handle 3-d effects which is needed for beryl.

---

### Post by Nepenthesrajah on 2007-04-15
I see, how could I find out what graphics card I have?

Thanks again,
-Jeremiah-

---

### Post by jem7v on 2007-04-15
Well, there are a lot of ways you could find out.  Suggestions:
- You could read whatever manual (if any) came with your computer and see if it says
- You could open up your computer, locate your graphics card, and read the label
- You could open the /etc/X11/xorg.conf file and scroll down to the "Device" section and see what it says

Meanwhile, I'll point out that generally NVidia cards have better support than ATI for composite desktops.  [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) (and the pages it links to) is a good primer that you should read if you're interested in Beryl or Compiz.

---

### Post by Nepenthesrajah on 2007-04-15
Ok s so it looks like it is a Intel Extreme Graphics 3D (845GL shared).

So if I go to the wiki on Beryl site it gives these installation instructions...

"Graphic Card Drivers 
Install Beryl on Ubuntu Edgy with XGL 
Install Beryl on Ubuntu Edgy with AIGLX 
Install Beryl on Ubuntu Edgy with nVidia (1.9xxx or higher) 
Install Beryl on Ubuntu Edgy with XGL and ATI (Automatic installation) 
Installing SVN snapshots"

Which on would I use with that card?

Thanks
-Jeremiah-

---

### Post by n3tfury on 2007-04-15
by now you could've run that live cd....

---

### Post by jem7v on 2007-04-15
Well, you're using an Intel card, probably with the i810 driver... I think that's probably better supported by AIGLX than XGL, so probably "Install Beryl on Ubuntu Edgy with AIGLX"

[https://help.ubuntu.com/community/CompositeManager/AIGLX](https://help.ubuntu.com/community/CompositeManager/AIGLX) will help you get AIGLX going, which should be pretty easy because you're running edgy instead of dapper.

---

### Post by Nepenthesrajah on 2007-04-16
&#8220;by now you could've run that live cd....&#8221;

That&#8217;s is what I thought but for some reason I&#8217;m having hard time finding the finding the .ios file for the live CD download on their site, I must be stupid or just some how missing it.  Once it is downloaded I&#8217;m assuming I can just use InfraRecorder and burn an image right?  I would have to use the 3.3 mini addition because the computer I&#8217;m putting it on does not have a DVD drive.


jem7v
Thanks for the advice, that is just what I needed to know.  Once I get my other problem worked out [http://ubuntuforums.org/showthread.php?t=410563](http://ubuntuforums.org/showthread.php?t=410563) I will give it a try.

Thanks,
-Jeremiah-

---

### Post by n3tfury on 2007-04-16
> **Nepenthesrajah said:**
> &#8220;by now you could've run that live cd....&#8221;

That&#8217;s is what I thought but for some reason I&#8217;m having hard time finding the finding the .ios file for the live CD download on their site, I must be stupid or just some how missing it.  Once it is downloaded I&#8217;m assuming I can just use InfraRecorder and burn an image right?  I would have to use the 3.3 mini addition because the computer I&#8217;m putting it on does not have a DVD drive.


jem7v
Thanks for the advice, that is just what I needed to know.  Once I get my other problem worked out [http://ubuntuforums.org/showthread.php?t=410563](http://ubuntuforums.org/showthread.php?t=410563) I will give it a try.

Thanks,
-Jeremiah-

[ftp://mirror.fpux.com/](ftp://mirror.fpux.com/)

specifically this one:  *right click , save as* [ftp://mirror.fpux.com/SabayonLinux-x86-3.3b.miniEdition.iso](ftp://mirror.fpux.com/SabayonLinux-x86-3.3b.miniEdition.iso)  (unless you're running 64bit).  the mini is the cd version which is what i used to test my system with and it worked great.  not familiar with infrarecorder, but any burner software worth a damn will burn an .iso image.

---

