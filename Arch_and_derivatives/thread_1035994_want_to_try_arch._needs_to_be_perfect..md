---
title: "want to try arch. needs to be perfect."
date: 2009-01-10
forum: Arch and derivatives
---

### Post by inxygnuu on 2009-01-10
Hello, I wanted to try arch, and after hearing many great stories, speed, and flexibility, I tried it on a test machine. Did not go so well... But I am willing to give it a 2nd chance, this time with my good machine. Can someone guide me through some steps, from Grub to a GUI? Or is this too much? I have looked at the wikis, but I always have a udev problem.

---

### Post by kaivalagi on 2009-01-10
> **inxygnuu said:**
> Hello, I wanted to try arch, and after hearing many great stories, speed, and flexibility, I tried it on a test machine. Did not go so well... But I am willing to give it a 2nd chance, this time with my good machine. Can someone guide me through some steps, from Grub to a GUI? Or is this too much? I have looked at the wikis, but I always have a udev problem.

Have you tried it in a VM, I would suggest that route first....then you've removed any potential hardware particularities...or at least any that are hard to problem solve.

---

### Post by crimesaucer on 2009-01-10
This is a VERY OLD guide: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)

Just cross-reference it with: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)


There are a few parts that have changed.... like:

The rc.conf on "page 5" of the guide is written slightly different now, just use the ArchWiki Beginners Guide: [http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Fresolv.conf_.28for_Static_IP.29](http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Fresolv.conf_.28for_Static_IP.29)


Then on "page 7" of the guide. The part that is about /etc/pacman.d is different now. Use this: [http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Fpacman.d.2Fmirrorlist](http://wiki.archlinux.org/index.php/Beginners_Guide#.2Fetc.2Fpacman.d.2Fmirrorlist)


On "page 8" I would rather follow the newer guides for installing X and your video driver: [http://wiki.archlinux.org/index.php/Beginners_Guide#Install_X](http://wiki.archlinux.org/index.php/Beginners_Guide#Install_X)


This part is new so pay attention to it: [http://wiki.archlinux.org/index.php/Beginners_Guide#Input_hotplugging](http://wiki.archlinux.org/index.php/Beginners_Guide#Input_hotplugging)


"Page 9": [http://www.raiden.net/?cat=2&aid=276&pid=9](http://www.raiden.net/?cat=2&aid=276&pid=9) is going to be different but easy to figure out.


...... Basically that guide is nice because it has screenshots of what the install will look like.... but you have to use the new updated info from the actual ArchWiki..... just read both and you should figure it out..... it also covers the "Grub to GUI" pretty well. (gnome will be slightly different with the new version)

---

### Post by jrusso2 on 2009-01-10
Everyone keeps saying how easy arch is and how great the forum and documentation are so you should be able to find what you need pretty easy.

---

### Post by SomeGuyDude on 2009-01-10
If you follow the Arch Beginners Guide step-by-freakin-step you won't have any problems I am 99% sure.

Problems occur when people skim or otherwise don't pay perfect attention to the steps and then wonder why X won't load or something.

---

### Post by Dr Small on 2009-01-10
> **SomeGuyDude said:**
> If you follow the Arch Beginners Guide step-by-freakin-step you won't have any problems I am 99% sure.

Problems occur when people skim or otherwise don't pay perfect attention to the steps and then wonder why X won't load or something.
+1
I didn't have any problems when I installed Arch, because I had a laptop setting beside me with the Beginners Guide loaded on Firefox. It really helped me get setup.

---

### Post by SomeGuyDude on 2009-01-10
> **Dr Small said:**
> +1
I didn't have any problems when I installed Arch, because I had a laptop setting beside me with the Beginners Guide loaded on Firefox. It really helped me get setup.

The problem I had my first few tries was I tended to skip the normal text and just look at the commands and bold text. I figured all the stuff in between was just fluff and as long as I copied and pasted commands I was good. I kept saying I couldn't get my wireless working, only to discover it worked fine when I read more closely.

Oh, and here's a tip for your wireless: use Wicd. It's perfect and won't require any config file fiddling.

---

### Post by ghindo on 2009-01-10
> **Dr Small said:**
> +1
I didn't have any problems when I installed Arch, because I had a laptop setting beside me with the Beginners Guide loaded on Firefox. It really helped me get setup.The nice thing is that now the Arch install media [includes the Beginners Guide in it]("http://wiki.archlinux.org/index.php/Beginners_Guide#Documentation"), so you can reference it without having another computer with you.

---

### Post by kerry_s on 2009-01-10
i agree, you have to read and follow the beginners guide closely to get it right. you also want to at lease know your basic hardware and you can't fear the command line. basically right after install you start with xorg.

my steps are something like this:
pacman -Syy
pacman -S xorg xf86-input-evdev xf86-video-savage

then i configure xorg cause i need some settings for it to work right and add hal to the daemons. after that i just pick what gui i want to use and follow the wiki.

---

### Post by Dr Small on 2009-01-10
> **kerry_s said:**
> i agree, you have to read and follow the beginners guide closely to get it right. you also want to at lease know your basic hardware and you can't fear the command line. basically right after install you start with xorg.

my steps are something like this:
pacman -Syy
pacman -S xorg xf86-input-evdev xf86-video-savage

then i configure xorg cause i need some settings for it to work right and add hal to the daemons. after that i just pick what gui i want to use and follow the wiki.
xorg was about midways for me, since I enjoy tweaking my /etc/rc.conf file, setting up networking, audio and installing my favorite CLI applications, then I move onto Xorg and nvidia drivers. :)

---

### Post by kerry_s on 2009-01-10
> **Dr Small said:**
> xorg was about midways for me, since I enjoy tweaking my /etc/rc.conf file, setting up networking, audio and installing my favorite CLI applications, then I move onto Xorg and nvidia drivers. :)

well i'm still getting to know this laptop(ibm t20 700mhz 256mb ram) i like to make sure things work before i take the time to tweak it, if there's a problem with X i know it's not because i tweaked something, trust me i have have a habit of tweaking everything i can till it breaks so i like to know up front if it was working. :lolflag:

---

### Post by handy on 2009-01-10
It seems to me that the two common stoppers to a successful Arch install, are: 

1.) The Beginners Guide is not followed to the letter. 

2.) Hardware support problems.

---

### Post by kerry_s on 2009-01-10
having the second computer to look things up made the difference for me.
the first thing that hit me was no display, i guess a driver issue, for this laptop i have to add:
```

        Option      "DmaType" "PCI"
        Option      "BusType" "PCI"

```

to xorg.conf or i would just have a blank/black screen when i startx.
so it really helps to have another means to look for answers, cause somethings are just not in the guide.

---

### Post by sisco311 on 2009-01-10
> **inxygnuu said:**
> Hello, I wanted to try arch, and after hearing many great stories, speed, and flexibility, I tried it on a test machine. Did not go so well... But I am willing to give it a 2nd chance, this time with my good machine. Can someone guide me through some steps, from Grub to a GUI? Or is this too much? I have looked at the wikis, but I always have a udev problem.

[list]
[*]rtfm (wiki, man, google, forum ...)
[*]learn to use the cli
[*]learn to edit config files
[*]use a search engine to find a solution
[*]rtfm and/or google before you ask a question 
[*]try to answer your own questions
[*]when you ask a question be specific (error messages/log files)
[*]rtfm
[*]don't repeat yourself :P
[/list]

---

### Post by handy on 2009-01-10
> **kerry_s said:**
> 
so it really helps to have another means to look for answers, cause some things are just not in the guide.

I agree. 

I always have a 2nd machine that I can use for reference. Some projects I wouldn't even start if I didn't have the 2nd machine available.  It often makes an otherwise hard & time consuming job quick & easy.

In much of the world, a 2nd internet capable computer, monitor, keyboard & mouse will cost  < $10- from the recyclers.

---

### Post by Open-SuSe-A-Me on 2009-01-12
> **handy said:**
> It seems to me that the two common stoppers to a successful Arch install, are: 

1.) The Beginners Guide is not followed to the letter. 

2.) Hardware support problems.

#1

+1

From my experiences, the beginners guide is great if you follow it 100%, though there are a few areas that could be worded slightly clearer/ more thorough, and other small areas that can be skipped accidentally.

#2

+10000

Hardware support is the only thing keeping me from converting both of my computers into Arch boxes.  Very frustrating.

---

### Post by billgoldberg on 2009-01-12
Yes, during installation you can switch to another terminal and use nano to open de beginners guide.

Or you could print the whole thing out before starting, or use another pc to read it while installing.

The beginners guide has everything and is easy to follow. Just don't skip any steps.

---

### Post by gjoellee on 2009-01-12
[http://archux.com/](http://archux.com/) is a great website for Arch Linux beginner tutorials. You can find the tutorials in the sidebar to the left if you scroll down on the page.

Here is a video tutorial of the installation of the latest Arch Linux: [http://archux.com/page/arch-linux-video-installation-guide](http://archux.com/page/arch-linux-video-installation-guide)

It is with that website be adventures with Arch started

---

### Post by SomeGuyDude on 2009-01-12
If it's possible to have an extra machine handy, do so. Makes things SO much easier when you can quickly search in text and look at the various other articles from the Wiki. There are a few things I recall needing to look at the separate article to fully get working.

---

### Post by MisfitI38 on 2009-01-12
> **Open-SuSe-A-Me said:**
> Hardware support is the only thing keeping me from converting both of my computers into Arch boxes.  Very frustrating.
Linux is a kernel. Either your hardware is supported by the kernel, or not. (Besides a handful of modules outside of the mainline, like madwifi, for instance.)
;)
If you are having trouble configuring your hardware, maybe we can help.
Unless, you are referring to hardware which is neither i686 nor x86-64...

---

### Post by SomeGuyDude on 2009-01-12
Some kernels are modified, if I'm not mistaken. You occasionally hear about someone who just couldn't get whatever to work in A, but B worked just fine.

---

### Post by smartboyathome on 2009-01-12
The ONE thing the beginners guide on the livecd (which is basically a copy of the wiki page) is missing is the Wireless section. It would have been easier to have it on the livecd if I could have. :)

---

### Post by MisfitI38 on 2009-01-13
> **smartboyathome said:**
> The ONE thing the beginners guide on the livecd (which is basically a copy of the wiki page) is missing is the Wireless section. It would have been easier to have it on the livecd if I could have. :)

The reason for this is simple. I uploaded that version of the guide to Simo before having access to the actual iso...sort of a chicken-and-egg issue, actually.
If the devs decide to put the guide on the new iso, the version I uploaded does have the wireless quickstart section.
There is or was some debate about whether to include the guide on the iso, so I am not sure about the status of it.

---

### Post by inxygnuu on 2009-01-16
ok!:D I think I might try installing today, because i have no school (cancelled because of weather!):P:D:p:KS)
Thanks! (I would thank some of you that helped, but they removed the thanks feature)

---

### Post by mips on 2009-01-16
> **inxygnuu said:**
> 
Thanks! (I would thank some of you that helped, but they removed the thanks feature)


I'm glad the thanks button is gone as people were abusing it. I'm sure some people got thanked just for saying 'hello' ;) The 'Solve' buttun is the one we want back.

Typing ou the word 'thanks' indicates that you went through more effort than simply clicking on a button :)

---

### Post by handy on 2009-01-16
> **mips said:**
> I'm glad the thanks button is gone as people were abusing it. I'm sure some people got thanked just for saying 'hello' ;) The 'Solve' buttun is the one we want back.

Typing ou the word 'thanks' indicates that you went through more effort than simply clicking on a button :)

I agree, the Solved button is of practical value, whereas giving thanks offers the opportunity relatively rarely, to show others there is additional support for a a persons posted suggestion.

Solved wins by a smile. :-)

---

### Post by inxygnuu on 2009-01-18
The solved is gone? that sucks.:( I think that they should keep that, that way you don't have to search through a thread to see if it is solved. I just installed, now I need to configure GRUB.

---

### Post by smartboyathome on 2009-01-18
> **inxygnuu said:**
> The solved is gone? that sucks.:( I think that they should keep that, that way you don't have to search through a thread to see if it is solved. I just installed, now I need to configure GRUB.

They had to get rid of solved (temporarily) because it puts more overhead on the database (and right now database stability is more important than the solved feature ;)).

---

### Post by cardinals_fan on 2009-01-18
> **inxygnuu said:**
> ok!:D I think I might try installing today, because i have no school (cancelled because of weather!):P:D:p:KS)

Schools here have been closed for three days thanks to icy roads.  -30°F to 45°F in less than a week is not pretty.

Anyway, take a few notes on the Beginner's Guide (one 3x5 provides plenty of space) and give it a shot.

---

### Post by Speed Demon on 2009-01-20
I can't ever keep Arch for VNC issues, found a solution and will be re-installing sometime this week for the 4th time in about 5 months :P
Arch Linux FTW!!!

---

### Post by SomeGuyDude on 2009-01-20
The first time you get it working, you'll wonder how in the world you lived without it!

---

