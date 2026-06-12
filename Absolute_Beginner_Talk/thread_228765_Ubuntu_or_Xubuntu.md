---
title: "Ubuntu or Xubuntu"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by mojoman on 2006-08-03
Hi,

I tried to find some threads on the this but couldn't really find what I was looking for. I'm sorry if this has been covered before.

I'm using Ubuntu since a couple of months now on a Toshiba laptop, 1 GHz Celeron, 256 MB RAM, 14 GB HD. This is my first experience with Linux and I'm both satisfied and impressed. However, it is a bit slow, especially the graphic (when I move windows it leaves a trail, video playback is jerky etc). This could either be my graphic card (Trident CyberBlade Ai1 which uses 16 MB RAM of the 256) but as the machine isn't exactly state of the art I gather it could also be that I'm running a distro that requires just a little bit too much from my laptop. 

According to the release notes on Dapper, my machine meets the requirements. However, I'm considering switching to Xubuntu as I've understood that the Xfce requires less and is substantially faster.

Is my machine better suited for Xubuntu?
Is it possible to run Ubuntu with Xfce and would it make any difference?
By chosing Xubuntu, would I be limiting myself as regard to what software is available?
Are there any obvious drawback with Xubuntu for me, who really don't play a lot of games but do use the computer to watch movies (my computer comes with a built-in DVD and TV-out) as well as the ordinary Internet, mail and office?

I'd really appreciate if someone took the time to give me some thoughts on this.

Best regards
/mojoman

---

### Post by ironfistchamp on 2006-08-03
I think that XFCE would work better for you as you have lower specs than is ideal fo Gnome or KDE (I am assuming). By using XFCE I don't think you are limiting the kinds/amount of software for you. I think you just need to have the rights libaries installed for it to work. Synaptic should sort all that out if you get your software from there. Apt-get and aptitude will get all the dependecies aswell.

I was also thinking of trying out XFCE for the hell of it.

Hope this has been of some help (I know I haven't said much :p  )

Ironfistchamp

---

### Post by b_martinez on 2006-08-03
Yes you can install XFCE into your Ubuntu.How it works for you is a different matter. It does not (exactly) work the same as Gnome, but it is a pretty nice desktop. If you have the time and the resources, I would suggest that you d/l the Xubuntu live cd and play with it. I mean learn it. Once installed, the XFCE desktop is configurable. Change the colors, change the resolution, et&c. Read about using it at XFCE.org (?).
For a bit more help, go to Tuxmagazine.com and read and/or download their mag. Better hurry on that , as they are going to go to a paid subscription soon. There are articles on how to use a light weight desktop, and it is writtern for the novice Linux user. there is one article on XFCE, but since I am on the Xubuntu live cd, I don't have access to my /home files in FC5, or I would give you the info as to which issue to get.
hope this maybe helped.
Bill

---

### Post by mockjules on 2006-08-03
I plan on doing this tonight. I see no problems with it so far. It seems that it is possible to install the Xubuntu desktop after you install Ubuntu. THe KDE desktop as well.

First run in terminal:

sudo apt-get install xubuntu-desktop

System ->Log Out -> Log Out

To log in to XFCE click on Sessions and choose XFCE

It seems straight forward enough. GIves you a chance to try both desktops in the same install.

:-?

---

### Post by b_martinez on 2006-08-03
> **mockjules said:**
> I plan on doing this tonight. I see no problems with it so far. It seems that it is possible to install the Xubuntu desktop after you install Ubuntu. THe KDE desktop as well.

First run in terminal:

sudo apt-get install xubuntu-desktop

System ->Log Out -> Log Out

To log in to XFCE click on Sessions and choose XFCE

It seems straight forward enough. GIves you a chance to try both desktops in the same install.

:-?

Totally possible to install XFCE and KDE,but if you are looking to speed up your box, the KDE DM is not what you want. it is more resource intensive than XFCE. There are others, but you probably don't want to learn them right now, as you are learning Linux.
Bill

---

### Post by xander848 on 2006-08-03
> **mockjules said:**
> 
First run in terminal:

sudo apt-get install xubuntu-desktop
:-?

You might want to do:

sudo aptitude update
sudo aptitude install xubuntu-desktop

If you decide to uninstall it, the dependencies will be removed also by using aptitude rather than apt-get.

---

### Post by mojoman on 2006-08-03
Thanks for all the tips! :D 

I installed Xfce using apt-get as an additional desktop on my Ubuntu and it worked just fine. It does seem a bit faster and snappier and all the programs I have on my Ubuntu seem to run fine on it. I'll go for the complete Xubuntu install and hopefully it'll make my laptop a little more user friendly.

Once again, thanks for the help!

Best regards
/Mojoman

---

### Post by mockjules on 2006-08-03
Wow! Never heard of aptitude. Is the primary use of aptitude to removed attached dependencies? I must look into this.

Thanks!

---

### Post by anaconda on 2006-08-03
xubuntu desktop is NOT the same than a real Xubuntu installation! So if you like it you should install xubuntu..

One other distro, which you might like is DamnSmallLinux (about 50MB), which would be lightning fast with your machine, expecially when running from ram...

---

### Post by confused57 on 2006-08-03
Also, there is a "trident" video driver you can select in Ubuntu, if it isn't already.
To see if it is selected open the file:

```
cat /etc/X11/xorg.conf
```

and see which video driver is listed, may not make a difference.

---

### Post by kadymae on 2006-08-03
I'm running Xubuntu on a PowerBook G3/500 and get a "trail" when I move boxes around on the desktop.

Video card in there is a pretty standard ATI chipset with 8mb of dedicated vRAM.  At this point I think it's a driver issue.

Can't tell you about video playback -- the DVD drive in my PowerBook is dying and so I don't use it unless I absoutely have to.

---

### Post by jtgamma on 2006-08-03
kadymae: may i suggest you to change your DVD drive ?:-\" :rolleyes:

---

### Post by mojoman on 2006-08-04
Thought I'd just give some feedback on how things went.

I started by installing XFCE on Ubuntu and it was a little bit faster than Gnome on Ubuntu. So I reckoned that XFCE does require less juice from the machine. As it seemed to work fine with my applications I decided to go for the full monty. I did a complete reinstallation on my laptop and it now runs even better on Xubuntu than Ubuntu with XFCE so I guess that switching to Xubuntu was a good move. However, I've read in some post that XFCE is not always notably faster than Gnome but that might be that case if your machine is already fast enough to optimize Gnome. I think that Ubuntu using Gnome or KDE required just a little bit too much from my laptop (1GHz, 256 RAM) and if you're having similar spec's Xubuntu might be worth a try. All programs seem to be available although I'll try to avoid the ones that require the heavy Gnowe or KDE libraries.

The graphic is a bit faster and windows no longer leave a trail when I move them. The driver used is the same as before (trident, although it identifies my card as a CyberBlade i1 instead of Ai1). However, playing divX or Xvid still is a bit jerky and unsatisfactory but I'll try to twist and tweak the xorg.conf and see what happens. Regardless of how that turns out I reckon that the odds of getting the machine to play movies is a lot better under Xubuntu.

Thanks for all the help, it really makes a world of difference for newbies like me. :D 

/Mojoman

---

### Post by K.Mandla on 2006-08-06
Glad it went well. I used to run Gnome on a gigantamo Dell XPS M170 -- 2.8Ghz, 2Gb ... you get the idea. 

Anyways, I also have some older laptops that couldn't handle Gnome and so I started using Xubuntu. And liked it. And soon it took over on the big machine too. 

Now it's the only thing I use. Gnome is a little more complete in some senses (and to some people), but XFCE is the cat's meow for me.

---

