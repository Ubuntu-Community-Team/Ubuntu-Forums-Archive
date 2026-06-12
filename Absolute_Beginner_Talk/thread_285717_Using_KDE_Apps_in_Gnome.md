---
title: "Using KDE Apps in Gnome"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by shaunk62 on 2006-10-27
Sorry for the stupid question. I am using Ubuntu and the Gnome desktop (i think that is the right verbiage), and have just discovered what I hope is the second last piece of my M$ conversion puzzle.

There is a OneNote type product called basKet [http://basket.kde.org/index.php]("http://basket.kde.org/index.php") but as you can see it is for KDE.

Can I install this in Ubuntu with Gnome and if so will it work. If I cant install it what are my options. This is day 6 of my Linux experience so still a real newbie. Is it possible to have both KDE and Gnome or is that being stupid or would it be to hard.

Thanks in advance.

---

### Post by docshawnc on 2006-10-27
Hi -
    I don't know about this particular app, but I'm running some KDE apps in Gnome without issue (a VNC client, Krdc, for one) - give it a shot and see what happens

---

### Post by kidders on 2006-10-27
Hi there,

You can have as many graphical environments as you like ... they all work reasonably happily together on the same PC, so don't worry.

Install away :-)

---

### Post by seijuro on 2006-10-27
I'd recommend using apt-get to install it though as I have had several of the gui package managers bork kde installs into gnome apt-get does a fine job pulls any extra kde libraries needed to run whatever app you are getting as well.

---

### Post by SunnyRabbiera on 2006-10-27
Kde apps in gnome isnt too too hard though, but there are a lot of things to do to get them workin.

---

### Post by diepruis on 2006-10-27
> **seijuro said:**
> I'd recommend using apt-get to install it though as I have had several of the gui package managers bork kde installs into gnome apt-get does a fine job pulls any extra kde libraries needed to run whatever app you are getting as well.

Use aptitude instead of apt-get. Here's why: [aptitude vs. apt-get]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by shaunk62 on 2006-10-27
Thanks for the response as usual the support here blows me away.

Well I installed it using the Add/Remove programs and it also installed Kontact although a quick squiz at that doesnt look like its the whole thing. 

Had a super quick play and it looks like it is going to work, although in saying that the help is not working because it is looking for some other KDE app.

Things seem pretty intuitive so I will see how I go.

Regarding the "multi UI" idea, is there any thoughts pros cons etc about doing it. The machine I am running on has plenty or RAM 1Gb (which I needed for running M$) so I am not worried about that, however as a newbie is it best to get familiar with one before diving into others. 

I have noticed there are some other KDE apps that might solve my last problem which is Bluetooth and synchronising with my Pocket PC device... oops cant count as I also need to fix screen rotation and then I believe I am done.

Thanks again for the unbelievable response although I have to say a bit disappointing this time as it took a full FIVE minutes to get a response ... hmmmm I would be still selecting menu items in the MS IVR at that time ;)

---

### Post by SunnyRabbiera on 2006-10-27
Apt get works for me :D

---

### Post by TheWizzard on 2006-10-27
use aptitude instead of apt-get! 

it is possible to have several desktop environments installed on one pc. this can be handy if there's one pc with more users, or if you want to try out different desktops yourself. if hdd space is not a problem, there's not much reason not to try different desktops. i used to switch between gnome and kde for a long time. 
you can install with the command: 
```
sudo aptitude install xubuntu-desktop
```
same works for kubuntu-desktop and edubuntu-desktop

there's also not much of a reason not to use gnome apps in kde or the other way around. there is a slight disbenefit, though, because kde and gnome use different shared libraries. the difference in performance is neglectable for "normal" use. 

basically, you can just play around and use your computer the way you want. linux means freedom!

---

### Post by davec64 on 2006-10-27
If you want to install KDE apps in Gnome, and don't want to do it in the terminal, the Synaptic Packet Manager has proved very useful for me.
It allows you to search for applications and also gives a description, all in a GUI.

---

### Post by shaunk62 on 2006-10-31
Thanks for your help. I have installed a couple of the KDE packages but after reading more about KDE v Gnome I think I will stick to Gnome until I know a lot more.

Again thankyou so much for the help you have made the transition from Windoze a truly great experience

---

