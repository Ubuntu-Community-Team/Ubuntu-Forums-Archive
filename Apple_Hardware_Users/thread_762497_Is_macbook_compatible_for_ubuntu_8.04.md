---
title: "Is macbook compatible for ubuntu 8.04?"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by dazedoracle on 2008-04-22
I wanna bought a mac book for ubuntu8.04 only, but it's said that touch pad may not work correctly, and also the hot key, who can give me a hand please
Thanks a lot!!

---

### Post by Zelut on 2008-04-22
I just installed Ubuntu 8.04 RC on my macbook (second gen) and everything but the camera is working.  The touchpad works fine, the hotkeys work fine.

I don't know how well it'll work on the third gen though.  I hear those are yet a bit problematic.

---

### Post by cyberdork33 on 2008-04-22
> **dazedoracle said:**
> I wanna bought a mac book for ubuntu8.04 only, but it's said that touch pad may not work correctly, and also the hot key, who can give me a hand please
Thanks a lot!!
It should work fine with the Macbook4,1. (The touchpad issues are in the Macbook Pro). There have been some issues with Apple keyboards recently.
There is a collection of bug reports effecting mactels here:
[https://bugs.launchpad.net/mactel-support/](https://bugs.launchpad.net/mactel-support/)

---

### Post by mabovo on 2008-04-22
> **Zelut said:**
> I just installed Ubuntu 8.04 RC on my macbook (second gen) and everything but the camera is working.  The touchpad works fine, the hotkeys work fine.

I don't know how well it'll work on the third gen though.  I hear those are yet a bit problematic.

I am upgrading since Hardy Alpha1 and never reinstalled. Isight doesn't load too but a little problem of shutdown disturb me since Alpha5 when acpi was upgraded. There is no menu to suspend hibernate or shutdown from gnome-session only in GDM login screen is possible to have access to these options.

Have you noticed this problem installing from RC ?

Thanks.

---

### Post by cyberdork33 on 2008-04-22
> **mabovo said:**
> I am upgrading since Hardy Alpha1 and never reinstalled. Isight doesn't load too but a little problem of shutdown disturb me since Alpha5 when acpi was upgraded. There is no menu to suspend hibernate or shutdown from gnome-session only in GDM login screen is possible to have access to these options.

Have you noticed this problem installing from RC ?

Thanks.
you need to reinstall from the latest cd... you probably have many issues that are related to "fixing" things in earlier releases. iSight works fine, and there are the correct options in the menu to shutdown, suspend, etc.

---

### Post by Nioclas on 2008-04-23
Installed last night.  Worked out of the box pretty much after update.  Haven't tried camera etc yet and sound volume is low (but appears to be a common problem?).  Overall, as this is my first proper excursion into linux and since I'm moving completely over to linux, I am impressed and enjoying i.e. seems to work pretty good with a macbook!

 NB: I'm using macbook 1st generation.

---

### Post by mustang on 2008-04-23
> **Nioclas said:**
> Installed last night.  Worked out of the box pretty much after update.  Haven't tried camera etc yet and sound volume is low (but appears to be a common problem?).  Overall, as this is my first proper excursion into linux and since I'm moving completely over to linux, I am impressed and enjoying i.e. seems to work pretty good with a macbook!

 NB: I'm using macbook 1st generation.

Hi Nioclas,

good to see another first generation macbook user. Two questions:

1) What kind of battery life do you get?

2) Is suspend temperamental?

---

### Post by Jackster on 2008-04-23
> **Nioclas said:**
> sound volume is low (but appears to be a common problem?).
 NB: I'm using macbook 1st generation.

I've got this same problem on a second gen Macbook. It's pretty annoying. What's worse is the headphone jack doesn't seem to work under Ubuntu either so I can't just plug in speakers and turn them up :(

---

### Post by loweringimpactaz on 2008-04-23
I cannot get my sound working PERIOD, does anyone know why? C2D macbook, got it about a month before the current ones.

---

### Post by kye_ on 2008-04-23
> **Jackster said:**
> I've got this same problem on a second gen Macbook. It's pretty annoying. What's worse is the headphone jack doesn't seem to work under Ubuntu either so I can't just plug in speakers and turn them up :(
I had this problem too. I searched launchpad and found a work-around in the comments of this particular bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957)

It goes like this-

open volume control
open edit menu and click preferences
check the surround sound box, close preferences
unmute surround sound in volume control

---

### Post by Nioclas on 2008-04-24
> Hi Nioclas,

good to see another first generation macbook user. Two questions:

1) What kind of battery life do you get?

2) Is suspend temperamental?

Battery life is awful!  My battery is wrecked as it is and I am in the process of buying a replacement!  So I can't say it would be an accurate picture.  I get about 70% under 0S X and 29% (virtually unusable) in Ubuntu - roughly!

Suspend isn't working correctly right either, but I think this is related to the battery.  I'll get back to you on this.

Sound problems... 

My sound works alright now, enabling those other channels in the preferences pane really helped.  The sound quality etc is not upto OS X as far as my ears can determine, but it may all be in my head now!

---

### Post by cyberdork33 on 2008-04-24
> **Nioclas said:**
> Battery life is awful!  My battery is wrecked as it is and I am in the process of buying a replacement!  So I can't say it would be an accurate picture.  I get about 70% under 0S X and 29% (virtually unusable) in Ubuntu - roughly!
If you haven't already, try resetting the SMC controller:
[http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

---

### Post by n0greenfx on 2008-04-24
ok so lets ask this question one more time cuz idk if it really got answered in the post yet. does hardy work out of the box with a macbook 3,1. or does one hafta follow the wiki steps to get it all working? iv tried it with gutys and never got the video out or the trackpad working correctly and the bottom got quite hot which scared me.

---

### Post by cyberdork33 on 2008-04-24
> **n0greenfx said:**
> ok so lets ask this question one more time cuz idk if it really got answered in the post yet. does hardy work out of the box with a macbook 3,1. or does one hafta follow the wiki steps to get it all working? iv tried it with gutys and never got the video out or the trackpad working correctly and the bottom got quite hot which scared me.I think that those issues will be the same for you in Hardy... other than maybe the trackpad, but that doesn't mean it isn't compatible.

---

### Post by bobisimo on 2008-04-26
Hi!

I've slowly fallen in love with Ubuntu. I've found so many articles lately talking about ways to tweak the OS and it's gotten me to the point where I'm really happy with where I'm sitting.

The problem is that I have a 1st-gen MacBook (w/ a gig of RAM).

As others have said in this thread, I'm having serious battery problems. When I run my Ubuntu partition, my fan averages around an audible 3000+ rpm, and the laptop runs hot. This is when I'm not doing anything. On the Mac OS partition, the fan is silent, averaging 1500 rpm, and the laptop isn't noticeably warm.

If I run something like Firefox under Ubuntu, the fan often (but not always) ramps up loudly and the laptop gets even warmer. I'm guessing I'm hitting something like 5000+ or 6000+ rpms. Under Mac OS, there is no change unless I'm opening lots of tabs, watching videos, etc.

My battery health usually rates around 80 % these days. However, If I leave my laptop plugged in and running Ubuntu for a while, when I later fire up my Mac OS partition to check on the battery health, it's often sitting around 55-65 % on health - forcing me to run the battery down and recharge it fully a couple times to get it back around 80 %.

I've spent the past few days digging around on Google and searching through the forums here, and going through sites like Lifehacker. The best I seem to be finding are comments from 13 or 14 months ago asserting that Ubuntu just isn't really kind to laptops - not yet, anyway. Is this true? Has nothing changed since then? I've tried things like using no graphical enhancements, things that I thought might help out, but it doesn't appear to change much.

This kills me! Like I said, I'm falling in love with Ubuntu. I'd love to format the drive, wiping the Mac OS partition, and go 100 % Ubuntu, but it just doesn't seem like I can - not without risking destroying my laptop. Thoughts? Or should I just hopefully wait for the next major release? :\

---

### Post by PartisanEntity on 2008-04-26
I installed Hardy on my MacBook, it's the latest generation (is that 3rd?).

Sound is not working, my external screen is merely a clone, these are two issues I am trying to resolve currently.

Touchpad worked out of the box, wifi worked using ndiswrapper.

---

### Post by McLeod Brennaman on 2008-04-26
Sound is tricky to diagnose, seeing as we 3rd-gen users have Realtek -and- intel chipsets. You want to use intel, trust me, it's much simpler. Assuming you're using a cookie-cutter iso install, open up the Menu -> System -> Preferences -> Sound Preferences. Set -everything- to ALSA- Advanced Linux Sound Architecture and the "Device" to HDA-Intel (Alsa Mixer). Test it. If you're not getting sound still, right click on the volume control applet in the panel, "Open Volume Control." Make sure that Master and PCM are cranked, and on the (I believe, disabled this myself) Switches tab, turn the Front Speaker on or off to your preference if you're using the line out jack or not.

If that doesn't work, try purging and reinstalling gstreamer, if that doesn't work, try another backend like xine, and if that doesn't work, you're beyond me and I apologize.

And wish I could help you with external screens, but haven't gotten around to tackling that myself just yet. X11 display settings in /etc/X11/xorg.conf will undoubtedly need tweaking, but once again, you're beyond my help there, but I'm sure the issue's been brought up somewhere on the forums.

---

### Post by shgadwa on 2008-04-26
Will a macbook run xubuntu 8.04??? The newer macboks should run just about anything.

Furthermore, if I could voice my opinion, Mac OS X is the best OS availabe, especially leapord. With that, you can run linux, you can run windows cp, you can run vista, you can run soloris.....the lsit is endless, with an emulator.

---

### Post by bobisimo on 2008-04-27
> **shgadwa said:**
> Will a macbook run xubuntu 8.04??? The newer macboks should run just about anything.

Well, my MacBook is first-gen but it still seems to handle Ubuntu well. I don't notice any performance hits regardless of what's going on, compared against how everything handles with OS 10.4 - aside from the battery, fan, and over-heating. :)

---

### Post by McLeod Brennaman on 2008-04-28
Quick and dirty fix for that.

In OS X, download (something like) smcFanControl. That puts a little applet in the menubar that controls your fan speeds. Set it to max, should be 6000? Restart out of OS X, load up Ubuntu, and it -should- keep humming along at 6000. Don't quote me on that, I use default dynamic speeds on my 3rd gen, but I have tried it using Window$ with and without all the boot camp software, and it works there, so I'm assuming it's the same deal for any other OS.

Irritating part about this fix is that after restarting that one time, you have to keep booting into OS X first just to set the fans to what you want. Apparently it only works for one load, unsure as to why. Another interesting tidbit to note is that graphics card overclocking also carries over to the next reboot in this same manner, so OC's done in Linux/Window$ will carry over into OS X or Linux, not sure about Window$ here, but I'm assuming it's the same case.

---

### Post by cyberdork33 on 2008-04-28
> **McLeod Brennaman said:**
> Quick and dirty fix for that.

In OS X, download (something like) smcFanControl. That puts a little applet in the menubar that controls your fan speeds. Set it to max, should be 6000? Restart out of OS X, load up Ubuntu, and it -should- keep humming along at 6000. Don't quote me on that, I use default dynamic speeds on my 3rd gen, but I have tried it using Window$ with and without all the boot camp software, and it works there, so I'm assuming it's the same deal for any other OS.

Irritating part about this fix is that after restarting that one time, you have to keep booting into OS X first just to set the fans to what you want. Apparently it only works for one load, unsure as to why. Another interesting tidbit to note is that graphics card overclocking also carries over to the next reboot in this same manner, so OC's done in Linux/Window$ will carry over into OS X or Linux, not sure about Window$ here, but I'm assuming it's the same case.
much on the mac is stored in variables in the firmware somewhere, which is different from most PCs...

You can control fan speed directly in Linux though, see the Intel FAQ.

---

### Post by border on 2008-04-29
I recently updated from 7.10 to 8.04 on a first generation (I think so) macbook. I have two problems I want to get rid of:

1. My screen doesn't work if I boot into ubuntu the normal way. I just get a black screen (with a bit of flickering) it's like some xconfig is trying but failing to load the xserver. I cannot get to the commandline or do anything else
It is fixed if I boot into recovery mode, try xfix (which doesn't seem to do anything) and then resume boot.
But ubuntu doesn't seem to save the configuration, so next time I boot, I'm having the same problem all over again.

2. Other problem is that I use a second screen, and I don't seem to be able to configure it anymore. Maybe part of the same first problem. I used to do it with xrandr, but the same commands don't seem to have the desired effect

Apart from that, sound using alsa works well. And I haven't experienced any other problems. Now I leave my macbook booted, but once I'm going back on the road with it that's gonna be a problem

anyone any useful input?

---

### Post by border on 2008-04-29
I did some further testing, and it to have to do something with ubuntu failing to load the intel driver (which workedd previously in 7.10 and with which I had a decent dual monitor setup with xrandr).
I think it loads the vesa driver, or maybe the 915resolution driver.
How can I make sure which driver is loaded? displayconfig-gtk doesn't seem to give me the right information.
And the xrandr GUI (monitor resolution settings) doesn't work very well...

---

### Post by bobisimo on 2008-04-30
> **McLeod Brennaman said:**
> 

... controls your fan speeds. Set it to max, should be 6000? ... 

That's a great way to keep the laptop healthy; I bet it will certainly help protect the important ingredients of the laptop by keeping everything cool. I don't want to sound unappreciative of such suggestions, but... who wants to run a laptop where the fan is going, well... even 3000 RPMs, let alone 6000 RPMs? :\

Then again, people deal with similar annoyances on the Xbox 360 without complaint. Haha.

---

### Post by billbear on 2008-04-30
I think setting fan speed to max will collect more dirt inside my Macbook, I won't do that.

---

### Post by border on 2008-05-08
When I boot into recovery mode and just choose resume once asked my xserver boots fine. When I choose the normal boot, I just get a black screen with no options to do.
Booting in recovery without choosing xfix doesn't seem to alter my xconfiguration so I have been able to set it up so that I can use xrandr to get a usable dual screen setup.

What's so different between normal boot and recovery boot that my display driver loads fine in recovery and not when normal booting?

---

### Post by anat on 2008-05-22
same problem here with ubuntustudio on a macbook revision 1. after upgrade to hardy heron i have troubles with the X server.
when booting normaly:
[LIST]
[*]X shows up with weird pixels on the screen.
[*]black again.
[*]then one more time weird pixels (you can see, that something is going on in the buffer).
[*]black again. 
[*]i'm not shure, if it tries to start X again. at least the backlight seems to be switched on/off.
[*]no response anymore.
[/LIST]

booting in recovery mode and pressing resume works fine.
the xorg.conf was generated by the xfix entry in the recoverymenu some time ago. i only added some lines to get my graphictablet working.

see the files attached.

uname -a
Linux kami 2.6.24-17-rt #1 SMP PREEMPT RT Thu May 1 16:23:33 UTC 2008 i686 GNU/Linux

it's really annoying. anyone with good news out there?

---

### Post by anat on 2008-05-22
i've got it!
> **border said:**
> What's so different between normal boot and recovery boot that my display driver loads fine in recovery and not when normal booting?
it's usplash that kind of messes up the video card so that X cannot start anymore. when booting in recovery mode the splash option is ommited.

to fix it:
```
sudo gedit /boot/grub/menu.lst
```
search for the line starting with
```
# defoptions=...
```
and delete the "splash" option.

save the file and call
```
sudo update-grub
```

that worked for me. no more splash while booting, but at least it's useable again.

hth,
anat

---

### Post by border on 2008-05-23
It works!!!

Thanks a lot

Did it have anything to do with the intel graphics card, the macbook or is it a bug in an ubuntu package somewhere?

---

### Post by cyberdork33 on 2008-05-23
> **border said:**
> It works!!!

Thanks a lot

Did it have anything to do with the intel graphics card, the macbook or is it a bug in an ubuntu package somewhere?
It could really be either... a bug in usplash or a bug in the driver for your card.

---

