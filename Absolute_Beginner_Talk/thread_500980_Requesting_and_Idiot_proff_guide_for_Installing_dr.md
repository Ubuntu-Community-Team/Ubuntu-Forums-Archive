---
title: "Requesting and Idiot proff guide for Installing drivers...."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-07-14
Hello everyone,

Over the past 3 days I have spent over 8 hours scanning through guides/google trying to figure out how to install my graphics drivers properly so I can run my 3D apps on linux. I have yet to manage to come up with anything even remote successful. What I need is an idiot proof guide to guide me along installing what I need to install for my 3D apps to work. All my buddies keep telling me to throw window back on and be done with it but I like alot of the other features Kubuntu has and don't want to have to revert... 

Here are my system specs/os/kernal for anyone that has the time to write me a tutorial on how to do this(along with links to what drivers I should be downloading)

Hardware Specs:
Processor:
AMD Core2 4600+
Mother Board:
Basic HP Mother board for AMD Dual Cores(I can look up what model if it is needed)
RAM:
2 One Gig sticks of DRR2 running in dual channel
Graphics Card:
Nvidia 7800GT
Hard Drive:
80Gig Sata(Again I can look up who makes if that would help)

Software Specs:
Linux Distro:
Kubuntu 7.04(Feisty Fawn) PC(Intel x86) desktop CD which I downloaded from this link: [http://www.gtlib.gatech.edu/pub/ubuntu-releases/kubuntu/feisty/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/kubuntu/feisty/)
Kernal:
Ubuntu, kernel 2.6.20-16-generic (I believe this is the most current)

Hope that is enough information needed to help me out. I like what I have working on here much better than windows if I could just get the rest of stuff working I'll never have to endure windows again on my home system. Also if more information is needed to help me out let me know what is needed and I can post it.

~J3ff

---

### Post by starcraft.man on 2007-07-14
Quickest and fastest way would be [Envy.]("http://www.albertomilone.com/nvidia_scripts1.html") To my knowledge it works with all NVidia cards to get the drivers in (rest of your hardware should be irrelevant, long as card detects driver is all that matters).

Download the stable version deb, double click and install. Go to Applications > System Tools > Envy and then pick automatically install drivers for nvidia. I am a bit worried, I don't know exactly what you've done with all those different guides if you've modified too many files without knowing what you were editing you might have done your system harm that could break Envy from working for you. Give it a try, if it fails I recommend a clean install and then try again.

Oh and please ignore your friends, it's clear they aren't trying to be helpful. Oh and your not an idiot, you don't need an idiot proof guide. Everyone has a bit of trouble starting :).

Oh and once your up and running, please see my blue guide in my sig for installing things, it should be helpful to you starting. It's long I know, but trust me you'll understand more when your done with it (just make sure to read my notes in 5b) since your in Kubuntu (my guides written mostly for Ubuntu users).

---

### Post by sad_iq on 2007-07-14
Ahhh....don't remember how I installed mine :( have the same one..recently bought...try envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and download envy_0.9.6-0ubuntu1_all.deb or try this : ```
sudo aptitude install restricted-manager && sudo restricted-manager
```

---

### Post by starsky on 2007-07-14
hi there :)
I had a look for your specific 7800 GT nvidia card and the best way seems to be to install automatix which would 1) cut down the amount of time we talk in this message 2) help you get your 3d cards capability sooner ;)

so here it is [http://ubuntuforums.org/showthread.php?t=310203](http://ubuntuforums.org/showthread.php?t=310203)

HTH

post back :)

---

### Post by starsky on 2007-07-14
oh didn't realise there's envy. :)
give that a try first and if not try automatix.
also remember to back up your xorg.conf file!

HTH

---

### Post by beastrace91 on 2007-07-14
Yes I had found envy now I have another question when I click the link to download it(This is the link I am using : [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb))

It opens as an editable text file and I get this message: Binary File Opened - Kate saving it will result in a corrupt file

How do I save it so I can run it? I saw this before but I was never able to download it properly. Hints?

On a side note I really don't want to have do a fresh install I like how I got my stuff on here now.. but I will if I have to.(My bet is I prop messed something up with all the different things I was trying*sigh*)

Thnx for the speedy respones,
~J3ff

---

### Post by starcraft.man on 2007-07-14
> **beastrace91 said:**
> Yes I had found envy now I have another question when I click the link to download it(This is the link I am using : [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb))

It opens as an editable text file and I get this message: Binary File Opened - Kate saving it will result in a corrupt file

How do I save it so I can run it? I saw this before but I was never able to download it properly. Hints?

On a side note I really don't want to have do a fresh install I like how I got my stuff on here now.. but I will if I have to.(My bet is I prop messed something up with all the different things I was trying*sigh*)

Thnx for the speedy respones,
~J3ff

Uh, right click and say save link as... It isn't a text file, it's a prepackaged debian installer. It works on all versions of Ubuntu without trouble. It should download properly, I don't have any problem doing it for me.

---

### Post by annda on 2007-07-14
have you tried synaptic to install the driver? or the restricted drivers manager(recommended on feisty)? nvidia-glx is and has been good for a year or so.

after the install and reboot check that /etc/X11/xorg.conf has 'nvidia' and not 'nv' as video driver. use this to configure your display if something is not right:
```

gksudo nvidia-settings
```

---

### Post by beastrace91 on 2007-07-14
Err I feel dumber with each question first I have to ask how to download it now well...

How do I run it? Do I use terminal or is there something I click in the .deb file?

Also thanks for the understanding

~J3ff

---

### Post by starsky on 2007-07-14
> **beastrace91 said:**
> Yes I had found envy now I have another question when I click the link to download it(This is the link I am using : [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb))

It opens as an editable text file and I get this message: Binary File Opened - Kate saving it will result in a corrupt file

How do I save it so I can run it? I saw this before but I was never able to download it properly. Hints?

On a side note I really don't want to have do a fresh install I like how I got my stuff on here now.. but I will if I have to.(My bet is I prop messed something up with all the different things I was trying*sigh*)

Thnx for the speedy respones,
~J3ff


hi there :)

all you have to do is this in your terminal -

$ wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb)

After that finishes, go to the directory you saved and do this -

$ sudo  dpkg -i envy_0.9.6-0ubuntu1_all.deb

-----------------OR--------------------

If you want a better Graphical front-end (if you prefer it that way) then go to the terminal and install gdebi

$ sudo apt-get install gdebi

then do ,
$ sudo gdebi
follow the prompts in gdebi

HTH

---

### Post by beastrace91 on 2007-07-14
Ok slowly but surly the turtle wins the race..... 

I have manged to install envy on my system now how do I run it? (Using windows for the past 6 years has gotten me used to just clicking a .exe I am trying to break that habbit XD)

~J3ff

---

### Post by sad_iq on 2007-07-14
Well it's **K->System->Envy**.. It will prompt for your password...then click Install nvidia driver!!!

---

### Post by beastrace91 on 2007-07-14
> **sad_iq said:**
> Well it's **K->System->Envy**.. It will prompt for your password...then click Install nvidia driver!!!


hrm not seeing a file called install driver anywhere... sorry. "**K->System->Envy**" is that the file path I can find it in? I dont have a folder labled "K" anywhere on my system.

~J3ff

---

### Post by sad_iq on 2007-07-14
Loool...soory for that...bad habits...**K** is the equivalent of the **Start **button in windows...from there choose **System** then choose **Envy**(whatever's next)...or in the konsole type **kdesu envy** ...it's the same thing!!!

---

### Post by beastrace91 on 2007-07-14
Ahh alrighty well I was bored while I was waiting for you to respond so I was able to do it myself by cd /usr/share/envy/ and then I used the command: envy -g and it started up but I'm glad to know it throws programs on the kmenu I didnt know it did that on its own.

~J3ff

---

