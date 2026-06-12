---
title: "Wacom with Ubuntu: what is your experience?"
date: 2014-09-28
forum: Art &amp; Design
---

### Post by shuichi on 2014-09-28
Greetings, this is one of my first posts, so if is something wrong with it, please let me know to correct it.
Id like to work on design, recently i completely changed from windows to Lubuntu in a Lenovo 3000 N500, im really glad with the result, even if im still getting accustom to the change from corel and photoshop to Inkscape and Gimp.
Now, i want to buy a Wacom tablet, but surfing through the web, and specially in the forum, i find that it could be troubly, i would like to read about the experience of people using it before to spend money. Thanks

---

### Post by ofnuts on 2014-09-29
I have a Wacom tablet (Bamboo One) that I use with Gimp and it works well. Gimp 2.8 has trouble with tablets, but AFAIK this is a problem with the Windows version of the GTK library.

---

### Post by Bucky Ball on 2014-09-29
"Troubly"? I like that word, and welcome!

I bought a Wacom Bamboo (not at home at moment so can't relate the model); plug in, worked immediately. The drivers for most Wacom devices are alrealy in the Linux/Ubuntu kernel. They play nice ... ;)

PS: I will qualify that with I use Xubuntu (xfce4 minimal install actually) but the drivers are there. Should work with lxde.

---

### Post by mcduck on 2014-09-30
I've been using my Intuos3 with Gimp, Inkscape & Blender for years now and it's always been a pleasant experience with Ubuntu. Especially these days when it's recognised automatically and some of the basic settings are available without even having to install any additional software or drivers for it...

(I also had a quick try with my friend's Intuos5 and that seemed to be working nice as well. S0 based on my experience Wacom tablets work nice these days, all the truly important stuff like pressure/tilt/rotation and the buttons on the pen itself work out-of-the-box these days, but you might need to install additional software to configure some of the extra buttons and controls on the Intuos series and to tweak pressure curves etc in finer detail. )

---

### Post by shuichi on 2014-09-30
Thanks for your answer!

---

### Post by shuichi on 2014-09-30
> **Bucky Ball said:**
> "Troubly"? I like that word, and welcome!

I bought a Wacom Bamboo (not at home at moment so can't relate the model); plug in, worked immediately. The drivers for most Wacom devices are alrealy in the Linux/Ubuntu kernel. They play nice ... ;)

PS: I will qualify that with I use Xubuntu (xfce4 minimal install actually) but the drivers are there. Should work with lxde.

Yeah, as english is not my native anguage, usually i end creating new words... but that one doesnt sounds bad eh? haha... thanks for your answer! and if you remember the model of your wacom, please let me know!

---

### Post by Bucky Ball on 2014-09-30
> **shuichi said:**
> ... if you remember the model of your wacom, please let me know!

I'm actually 750kms away from it at the moment and don't remember the model, sorry. Think it's about three or four years old if that is any help.

---

### Post by joe_7 on 2014-10-10
Wacom has good Linux support, and Ubuntu is no exception. If you buy a late model you might have to install a newer driver or upgrade to the latest distribution. For example my particular tablet needed a newer driver under 13.10 but worked out of the box on 14.04 LTS.

---

### Post by pablo-petzen on 2014-10-22
Well just plugin on usb and used it.. Perfectly worked.. same as the xbox 360 controler =)

---

### Post by kurja on 2014-10-25
I have a bamboo pen & touch CTH-470. It works out of the box, but buttons need to be configured from command line as there is no GUI to do that. There are good instructions for that though, no particular skills needed to do it.

---

### Post by Retro_Garage on 2014-10-28
I was given a discarded Aiptek drawing tablet, it's older, but I plugged in and had to do NOTHING. Worked perfectly under gimp. It goes used for about $50. Very happy it found me because I was about to buy one! It's no WACOM new tablet but it gets the job done for my animation project I'm working on. I was able to get all my pencil and paper drawn ideas drawn into gimp so I could give them some life.

It's an Aiptek HP 12000U model and works out of the box with 13.10 and up.

hp pavillion 753n, 2.53ghz pentium 4, 768mb ram (runs smooths), dual boot ubuntu 13.10 and winXP sp3.

---

### Post by Bucky Ball on 2014-10-28
@Retro_Garage: Just an off-topic note. 13.10 has reached end-of-life and is no longer supported by Canonical or these forums. See [HERE]("https://help.ubuntu.com/community/EOLUpgrades").

---

### Post by jehan-marmottard on 2014-11-06
Just to confirm other people saying that modern kernels supports most Wacom tablets out of the box and very well.
Sometimes very new models may be supported a little later on Linux distributions than on proprietary OSes, but most of the time because newer kernels take some time to be integrated downstream (i.e. Ubuntu would not provide the kernels as soon as it is released obviously since it needs testing and integration time).
In my case, we use a Wacom Bamboo, as well as an Intuos 5 without any issue.

As for configuration, there are GUIs actually. It is not mandatory to do it by command lines. Unfortunately they are often integrated as desktop (GNOME, KDE, etc.) tools, so it's hard to recommend one and stick with it. See for instance, for GNOME: [http://libregraphicsworld.org/blog/entry/wacom-configuration-made-easier-with-gnome-3-10](http://libregraphicsworld.org/blog/entry/wacom-configuration-made-easier-with-gnome-3-10)

---

### Post by kurja on 2014-11-07
> **jehan-marmottard said:**
> 

As for configuration, there are GUIs actually. It is not mandatory to do it by command lines. Unfortunately they are often integrated as desktop (GNOME, KDE, etc.) tools, so it's hard to recommend one and stick with it. See for instance, for GNOME: [http://libregraphicsworld.org/blog/entry/wacom-configuration-made-easier-with-gnome-3-10](http://libregraphicsworld.org/blog/entry/wacom-configuration-made-easier-with-gnome-3-10)

afaik there is no gui for 'vanilla ubuntu' that would allow button configuration.

---

### Post by Gustaf_Alhll on 2014-11-08
I got a Wacom Intuos S Pen. It's small, but it works. I use it for making artwork on the computer and I have no problems doing it.
The program I use is called MyPaint. It's made for usage with a Wacom and it works really well.
MyPaint doesn't have any powerful image editing tools like Photoshop and GIMP, but it has really well pen physics unlike the others.
It's the best one out there when you're writing on the computer. I usually combine it with GIMP to make it look better, but I write the image with MyPaint.

---

### Post by Sasha_Aderolop on 2014-11-15
Ubuntu has great Wacom support. It's all plug and play but with great graphical configuration options. You can configure pens and erasers and buttons for all common Wacom tablets. I was even surprised to find that you can lock a tablet to a single monitor in a dual-monitor set-up.

---

### Post by Linuxratty on 2014-11-17
I have a Wacom tablet and it works great with the Gimp. I just plugged it in and it works without a hitch. I've had it for several years and never had a problem with it.

---

### Post by shuichi on 2014-11-22
Well, my experience, after finally buy a my first wacom, on the beggining noting happened and i became desperate, began to look for tutorials but nothing worked, finally just rebooted system and voila! working great in gimp and inkspace, by now im just a little concern about what i was trying before to reboot, but if everything seems right, maybe i didnt touch anything important... just wonder if it happened to some of you in this way, after a reboot.

---

### Post by cornellg on 2015-08-11
My experience is that it has lately become a bit more troubly, but don't let that stop you. I have used an intuos2 and now use an intuos4 L and an intuos5 M. When unity was introduced, programs like Blender, Krita and a few others became a bit cumbersome because lots of cutomizability options disappeared that I needed on a regular basis. I switched to KDE and was surprised at how good that had become. Pretty good support for the tablets too. But with 15.04, plasma is a mess and pain in the bum, so switched back and it isn't as bad as it was a few upgrades ago. To get the most out of the tablets, quite a bit of tinkering is needed, but apart from the LED displays for the buttons, I got everything to work (including modifier key buttons and touch ring switch control), and while unity or whatever it is called nowadays is still getting in the way of other stuff, the tablets are fine. They are definitely worth the money, even if Canonical seems to be partially ignoring the demographic using them.

If you switched from corel and photoshop to Inkscape and Gimp, you should also add Krita to your toolset. Powerful stuff there that the other two are not aiming for. Good luck!

---

### Post by krikun on 2016-02-16
I have Wacom One. And with Ubuntu 14.04LTS it doesn't work correctly. Pressure level is not defined, also buttons on pen don't work as desired (on Windows first button acts like scrolling). So I have bad experience of using Wacom tablet with Ubuntu.

---

### Post by Bucky Ball on 2016-02-19
*Thread closed.*

This is an old thread with three posts in two years and in a discussion area. 

If you're having troubles with your Wacom tablets, try posting a new thread with the model and as much info as you can give about the problems maybe someone can help.

Good luck.

---

