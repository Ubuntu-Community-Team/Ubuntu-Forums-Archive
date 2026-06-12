---
title: "Beryl screws up my ubuntu"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Leela on 2007-01-21
Hi,
Yesterday, I tried to install Beryl on my computer, and I followed this guide:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

I followed the guide perfect, and when I rebooted, I saw that whole my screen was messed up, so I thought that was normal with beryl, and I try to start Beryl, when I do that, I see the starting stuff, ut then i see a White screen, that sometimes changes in a cube. I'm not able to get out of Beryl, so I was in need to reboot unsafe. now I tried to reverse the  guide, (changing everything back in the /etc/apt/sources.list and in the /etc/X11/xorg.conf, but i still got the same problem.
Here's a screenshot of my 'messed up' screen: 
[[IMG]http://img206.imageshack.us/img206/7913/screenshot2mf.th.png[/IMG]](http://img206.imageshack.us/my.php?image=screenshot2mf.png)

Oh ya, since i installed that, my computer works alot slower too, like when i scroll in firefox, it needs like 1 second to scroll 1 piece down.

Can anyone help me on this?
Thanks in advance
Leela

---

### Post by Leela on 2007-01-21
Anyone?

---

### Post by harrisony on 2007-01-21
what processor and gfx card are you using? also how much memory do you have?

---

### Post by Rhubarb on 2007-01-21
What video card are you running on your system?
What video drivers (and version) are you running on your system?

Please remember that Beryl is currently Beta software, so it isn't very stable.
I myself am experiencing a few small glitches with Beryl and the newest nVidia Beta drivers, but everything mostly works bug-free.

---

### Post by mendingo84 on 2007-01-21
i'm having the same problem here with beryl on edgy as well.
fun fact is:
> 
glxinfo | grep direct
direct rendering: No

lsmod|grep 915
i915                   21632  2
drm                    74644  3 i915
tsdev                   9152  0

as you can see, my graphic card is Intel, vresion 855GM, and the driver is i810

---

### Post by Leela on 2007-01-21
my video card is ASUS Extreme AX550 Series
And I haven't installed any drivers for my ubuntu, I did for my windows tho...

---

### Post by kinematic on 2007-01-21
> **Leela said:**
> my video card is ASUS Extreme AX550 Series
And I haven't installed any drivers for my ubuntu, I did for my windows tho...


[[IMG]http://img226.imageshack.us/img226/7017/doh0uf.th.gif[/IMG]](http://img226.imageshack.us/my.php?image=doh0uf.gif)

---

### Post by Leela on 2007-01-21
Look, the thing is, I got the drivers, but they are for windows...

---

### Post by kinematic on 2007-01-21
install the linux drivers :wink: 
do a search in synaptic for ati and see what driver is compatable with your card(this forum has a search function people!)

---

### Post by medley on 2007-01-21
> **Leela said:**
> Look, the thing is, I got the drivers, but they are for windows...

Who's chipset does your gfx card use (ie Nvidia, Ati)? You need to determine that first and install the drivers. Make sure they are Linux drivers;) 

If your card uses Nvidia, you will find the Envy utility very helpful. Once you have installed your drivers, start a terminal (what we used to call dos prompts in Windows parlance) and type 'glxinfo | render' without the quotes. If you don't see 'Direct Rendering: Yes', then Berly won't work for you until you get that fixed. This is not a simple as some would make it sound. I just got Beryl working last night after wrestling with it for 2 weeks.

---

### Post by Leela on 2007-01-21
> **kinematic said:**
> install the linux drivers :wink: 
do a search in synaptic for ati and see what driver is compatable with your card(this forum has a search function people!)

I tried searchin in synaptic, and it looked like they were installed already, even drivers for video cards i didn't need...
Well, I don't really need Beryl, I just want that ubuntu runs normal again

> **medley said:**
> Who's chipset does your gfx card use (ie Nvidia, Ati)? You need to determine that first and install the drivers. Make sure they are Linux drivers;) 

If your card uses Nvidia, you will find the Envy utility very helpful. Once you have installed your drivers, start a terminal (what we used to call dos prompts in Windows parlance) and type 'glxinfo | render' without the quotes. If you don't see 'Direct Rendering: Yes', then Berly won't work for you until you get that fixed. This is not a simple as some would make it sound. I just got Beryl working last night after wrestling with it for 2 weeks.
I don't know what chipset my gfx card uses, how do I see that?

---

### Post by kinematic on 2007-01-21
> **Leela said:**
> ]I don't know what chipset my gfx card uses, how do I see that?

enter the following in a terminal
> lspci | grep VGA
or use google and search for asus extreme ax550.

---

### Post by Leela on 2007-01-21
```
04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
```

---

### Post by medley on 2007-01-21
> **Leela said:**
> ```
04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
```

I wish I could help you more, but my system uses an Nvidia card, and I know that when I screwed up the drivers I had a tough time getting everything back in shape until I found a utility the "just works".

I'm afraid you'll have to rely on others with more experience. Good luck...you'll get it fixed eventually.

---

### Post by Leela on 2007-01-21
> **medley said:**
> I wish I could help you more, but my system uses an Nvidia card, and I know that when I screwed up the drivers I had a tough time getting everything back in shape until I found a utility the "just works".

I'm afraid you'll have to rely on others with more experience. Good luck...you'll get it fixed eventually.
Thanks anyway ;)

---

### Post by laosboyme on 2007-01-21
Just delete beryl by using this command

code
sudo apt-get remove beryl beryl-manager

If you don't want to delete it

Enable you're 3d rendering using this code:

glxinfo | grep direct
direct rendering: No(yes)

If it says no you need to enable it :guitar: 

Bad english](*,)

---

### Post by Leela on 2007-01-21
> **laosboyme said:**
> Just delete beryl by using this command

code
sudo apt-get remove beryl beryl-manager


I tried this, but i still got the ugly stuff and slow working

---

### Post by peresko on 2007-01-21
Hi Leela,
try this guide, if u have Ubuntu Edgy.
U have an ati videocard, with the x550 chipset, so the fglrx driver mentioned in the guide will work just fine.

h t t p : / / wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide

---

### Post by Rev. Nathan on 2007-01-21
Hi, I got one. It seems the install went OK, but whenever I enable Beryl (in the Terminal, beryl-manager), I get an odd one.

It looks just like my session is in gnome, except that all the window borders go away, and nothing is clickable, or keyboardable. I don't know what to do here, but from the output the Terminal has given me, something about no directory to pixmaps or something. I'm sure it's been reported before -- help?

---

### Post by Jacksoon on 2007-01-21
I have this same problem.

I figured it was my drivers, so i downlaoded and installed the latest nvidia drivers.

It made me re-name something to nv instead of Nvidia on the guide.

Now whenever i boot to linux, it doesnt load and i get error screen saying that a screen cannot be found.

help.

---

### Post by moshuptrail on 2007-01-21
If you just want to get back working again, you need to restore your xorg.conf file.

It's located in /etc/X11.  If the beryl instructions were good they had you make a copy as a backup.
e.g.  sudo cp xorg.conf xorg.conf.bak (reverse the parameters to get it back)

If you don't have a backup, you might try: (this command is found in xorg.conf near the top)
sudo dpkg-reconfigure -phigh xserver-xorg

which should reconfigure your video the way the install did originally.
then you can go about troubleshooting beryl

I found (trying to get compiz going) that a good understanding of xorg.conf, and backup copies saved me many a re-install.

good luck with beryl.  it's pretty cool stuff!

---

### Post by Leela on 2007-01-21
> **peresko said:**
> Hi Leela,
try this guide, if u have Ubuntu Edgy.
U have an ati videocard, with the x550 chipset, so the fglrx driver mentioned in the guide will work just fine.

h t t p : / / wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide
Are you sure ati = asus?

---

### Post by harrisony on 2007-01-21
> 04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]from [http://ubuntuforums.org/showpost.php?p=2043801&postcount=13](http://ubuntuforums.org/showpost.php?p=2043801&postcount=13)
^you said so 
and not all asus cards are ati some are nvidia but yours is an ati

---

### Post by Leela on 2007-01-21
ok lol, sorry

---

### Post by harrisony on 2007-01-21
> **Jacksoon said:**
> I have this same problem.

I figured it was my drivers, so i downlaoded and installed the latest nvidia drivers.

It made me re-name something to nv instead of Nvidia on the guide.

Now whenever i boot to linux, it doesnt load and i get error screen saying that a screen cannot be found.

help.

> **Rev. Nathan said:**
> Hi, I got one. It seems the install went OK, but whenever I enable Beryl (in the Terminal, beryl-manager), I get an odd one.

It looks just like my session is in gnome, except that all the window borders go away, and nothing is clickable, or keyboardable. I don't know what to do here, but from the output the Terminal has given me, something about no directory to pixmaps or something. I'm sure it's been reported before -- help?

> **mendingo84 said:**
> i'm having the same problem here with beryl on edgy as well.
fun fact is:

as you can see, my graphic card is Intel, vresion 855GM, and the driver is i810
Please dont hijack this thread make your own posts
and try this [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

[quote=Leela]ok lol, sorry[/quote]
you dont need to be sorry i do it all the time ;) 
as someone else said i think have you tried [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)  or [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.htmlhttp://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.htmlhttp://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by pissedoffdude on 2007-01-21
What happens when you create a new panel? Try creating a new panel and see if that works.

---

