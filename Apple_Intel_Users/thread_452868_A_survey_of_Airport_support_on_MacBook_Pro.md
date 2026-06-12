---
title: "A survey of Airport support on MacBook Pro?"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by ThufirHawat on 2007-05-23
All right, I was rather optimistic, and now I am lost again.
Problem: how to get my MacBook Pro where, thanks to the advice in this forum, I have loaded also Feisty Fawn, to hook onto my WPA2 home Airport network, which I can of course use with Mac OS X without any problems.
Before you start telling me what to do, let me summarise the problems as I have seen them so far:
a. identifying the actual hardware installed is not obvious from Mac OS X-perhaps somehow easier  from Ubuntu;
b. ambiguous snippets here and Brownian motion there seem to indicate that WPA may be possible with lots of  effort, but WPA2 wouldn't; 
as a security specialist I fail to see why; is there a definite answer, as in WPA2 yes or WPA2 no?
c. as by now customary in the thick jungle of Linux documentation, you have to make a choice before you can actually assess the elements of the choice (between madwifi and the other main competitor).
I understand I am a greenie and therefore everything looks odd to me, but has anybody ever published a short concise survey of these issues (which would probably interest more than five people, myself included), rather than the  details of how to tweak the rightmost endian byte on an Atheron card on a misty Sunday morning?
Would anybody point me to something in this direction?
Thank you.

Thufir, perplexed Mentat

---

### Post by ronocdh on 2007-05-23
Actually, there was recently a post about the creation of packages for the Mactels. This project is in its infancy, so don't count on it for your purposes now, but I think it's absolutely headed in the right direction.

As for your hardware detection (which is very key to this package creation project!), try **sudo update-pciids** and then *lspci*. But if you have a C2D MBP, it's safe to assume you have the Atheros chipset AR54xx, and so you might as well start by giving Madwifi a crack. Failing that, ndiswrapper works for most. [This]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") is the most helpful post I can point you to.

I don't have solid facts about WPA and WPA2; in my experience, I have been unable to get WPA2 working. Comb through the Madwifi documentation, and I'm sure you'll find information.

Good luck!

---

### Post by ThufirHawat on 2007-06-04
> **ronocdh said:**
> 
As for your hardware detection (which is very key to this package creation project!), try **sudo update-pciids** and then *lspci*. But if you have a C2D MBP, it's safe to assume you have the Atheros chipset AR54xx, and so you might as well start by giving Madwifi a crack. Failing that, ndiswrapper works for most. [This]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") is the most helpful post I can point you to.


Dear ronocdh,

thank you.
Am realising that there are a few rules applicable to me, inter alia:

a. being a geek does not entitle to Linux-geek status;
b. in this world, more than in conventional OS system programming, documentation is mostly hopelessly obsolete;
c. you are accustomed to understand why every bit does not work; not here.

Having said that, I am trying to understand what's up.
The Atheros chip is indeed a AR5418 rev 01 (without **sudo update-pciids** I would have never been able to find out-thank you!).
I have then started trying to bring my Feisty Fawn system up to scratch, but have meanwhile found out that:
- the apt system is not the most user-friendly system in the world (my idiotic system keeps asking for a CD I never used and will not take a desktop live nor an alternate Ubuntu CD);
- Gnome has some unpleasant aspects (it resembles a lot WinXP...), as for instance in some case the pointer resting onto an option will have as effect to click it, and I haven't found out how to disable this-this must be the single most stupid default I have seen in twenty-seven years of operating system programming (think of weapon controls working like this, for goodness' sake!); also the human interface is visibly inconsistent among applications: I now understand why Apple is very strict on how to develop stuff...

However, complaning won't change much, so I think my most urgent problems are:

1. how to get apt right (any way of killing the ghost CD request?);
2. understanding how to load the Gnome Network Manager (apparently iti is installed: how do I call it?);
3. wpa_supplicant is included in my system; how do I check which version is it?

I am aware I need to read ASAP a book like "Fundamentals of Linux system programming" or similar. I promise I will...

Do meanwhile lend me a hand, please...

My problem is further compounded by the fact that at work I am on a corporate Ethernet network, which Ubuntu understands without configuration (but I have plenty of other things to do), whilst at home I have my WPA2 Airport network which I cannot use until I configure correctly the whole shabang...

---

### Post by ivesjd on 2007-06-04
Okay, for the cd, open up synaptic from the System > Administration menu. Then go to Prefences and then Repositores. At the bottom uncheck the cd option. I wish I could help with the other two, but I'm not running Gnome-Network-Manager so I cant tell you how to start it, although it should be in one of the menus. And there are various tutorials on madwifi, just search madwifi in the forum search box and find one that works.

---

### Post by cevans on 2007-06-04
> **ThufirHawat said:**
> 
- the apt system is not the most user-friendly system in the world (my idiotic system keeps asking for a CD I never used and will not take a desktop live nor an alternate Ubuntu CD);
- Gnome has some unpleasant aspects (it resembles a lot WinXP...), as for instance in some case the pointer resting onto an option will have as effect to click it, and I haven't found out how to disable this-this must be the single most stupid default I have seen in twenty-seven years of operating system programming (think of weapon controls working like this, for goodness' sake!); also the human interface is visibly inconsistent among applications: I now understand why Apple is very strict on how to develop stuff...

If you start using apt on the command line, then I will agree that it isn't very user friendly. Try either editing /etc/apt/sources.list to remove the line for the CD (not user friendly), or going to the Repositories preferences and removing the CD entry (user friendly). 

GNOME actually has strict UI guidelines, and I believe that the project follows them more closely than Apple. The pointer resting on an something *will not* have the effect of clicking it - that would be an insane default! The reason you can't figure out how to disable it is because enabling it isn't even an *option* with GNOME! Are you sure this isn't a problem with either the touchpad driver or the touchpad itself? I've found with my MBP that the mouse button is very poor, and will click itself when the laptop is held in the wrong way - this happens in OS X as well. The touchpad driver is also very experimental and rather poor. Try using the system with an external mouse, with the computer placed carefully on a flat surface, and see if the problem goes away.

> 
2. understanding how to load the Gnome Network Manager (apparently iti is installed: how do I call it?);
3. wpa_supplicant is included in my system; how do I check which version is it?


For wpa_supplicant you can check the version with apt, or synaptic. Gnome network manager is accessible through one of the icons in the top right corner. You can click on it to select the network.

Unfortunately, the MBP is a very poor laptop to use for Ubuntu.

---

### Post by ronocdh on 2007-06-04
> **cevans said:**
> Unfortunately, the MBP is a very poor laptop to use for Ubuntu.
Oh dear. Is this discussion really starting again? I can't imagine a better computer to run Ubuntu on, but hey, that's all I have to say about that.
> GNOME actually has strict UI guidelines, and I believe that the project follows them more closely than Apple. The pointer resting on an something *will not* have the effect of clicking it - that would be an insane default! The reason you can't figure out how to disable it is because enabling it isn't even an *option* with GNOME!
Agreed. Thufir, have you tried KDE or any of the other Desktop Environments? Some quick Googling will get you a long way as far as relative pros and cons of those major two, and there are many more options for you. Remember, the interface isn't the operating system, it's the desktop environment!
> Are you sure this isn't a problem with either the touchpad driver or the touchpad itself?Also agree. Have you yet set up Qsynaptics or something similar, Thufir? This is vital to getting around in Ubuntu on one of the MacBooks.
> I've found with my MBP that the mouse button is very poor, and will click itself when the laptop is held in the wrong way - this happens in OS X as well. This sounds like a hardware defect to me. I have **never** had trackpad issues in OS X. Have you seen any articles which document this in other users? I sort of hope you're not alone, but it's something I'd definitely check out.

---

### Post by cevans on 2007-06-05
> **ronocdh said:**
> Oh dear. Is this discussion really starting again? I can't imagine a better computer to run Ubuntu on, but hey, that's all I have to say about that.
I should have been clearer in explaining my views here - the MBP is a very nice computer, but setting up Ubuntu on it isn't as easy as on some other computers - wireless requires very unstable drivers, suspend and hibernate are difficult to set up, the touchpad driver is in need of considerable improvement, and I don't have time to improve the drivers. Of course, I ended up having to write my own kernel patches for my last laptop, so I suppose I can't complain too much.

> 
Agreed. Thufir, have you tried KDE or any of the other Desktop Environments? Some quick Googling will get you a long way as far as relative pros and cons of those major two, and there are many more options for you. Remember, the interface isn't the operating system, it's the desktop environment!

I fear you may have misinterpreted both what he was saying and what I was saying - from his opinions, I expect that he would dislike KDE immensely. I was pointing out that he couldn't figure out how to disable what he is referring to as the worst default he has ever seen because GNOME's developers agree with him entirely, and the "feature" he is complaining about doesn't actually exist.

> Also agree. Have you yet set up Qsynaptics or something similar, Thufir? This is vital to getting around in Ubuntu on one of the MacBooks.
The synaptics configuration programs helped somewhat for me, even though they shouldn't have, as our defaults should be sane  (I've had this problem with the (rather poor) synaptics driver on other systems as well), but the touchpad still works rather poorly. There is something wrong with the driver, and changing the configuration settings isn't going to resolve that.

> This sounds like a hardware defect to me. I have **never** had trackpad issues in OS X. Have you seen any articles which document this in other users? I sort of hope you're not alone, but it's something I'd definitely check out.
It only manifests when there is a slight strain on the system. For example, it might be sitting on an uneven surface, and pressure from underneath, or a shear force, will cause the button to be pressed. The issue is understandable, given the design.

---

### Post by ivesjd on 2007-06-05
@cevans
Sounds like you had/have a bad laptop. I havent had any strange mouse clicks from sitting on  uneven surfaces. And it was easier to install Ubuntu on my macbook then on any other computer Ive installed it on. Macbooks are some of the nicest laptops around.

---

### Post by ThufirHawat on 2007-06-05
> **ivesjd said:**
> @cevans
Sounds like you had/have a bad laptop. I havent had any strange mouse clicks from sitting on  uneven surfaces. And it was easier to install Ubuntu on my macbook then on any other computer Ive installed it on. Macbooks are some of the nicest laptops around.

No, no.
Mine is a MacBook **Pro**, yours a MacBook. 
The two machines are quite different, as to HW (CPU, graphic module, etc.).
My trackpad is absolutely impeccable under MacOS X. 
I therefore very much doubt that it is a HW issue. 
It would should up also under Mac OS X and it does not.

Now on miscellaneous issues:

1. no Network Manager icon is available on top right of my screen (what it is there is not called Network Manager);
2. the various "recipes" provided in previous posts and often quoted here no longer work, because the 0.9.30.13 madwifi release is obsolete and superseded by Lord knows what (I do not even understand the archiving principle there).

Am going to madwifi trying to understand what could be done there.

Thanks for the tip on unchecking CD on the synaptic package manager.

---

### Post by russo.mic on 2007-06-05
Hi!

So, I have a MBP C2D running ubuntu feisty 7.04 and it works great!  3d accel worked out of the box, and beryl was a snap!  although, triple booting with os X and XP was a bit of a pain, but now that it's setup, I'm in heaven!

The touchpad can be configured in xorg.conf, and i've gotten my to be pretty good, but not great.  I don't like touchpads anyway, so I just use a bluetooth mouse.  It would, however, be nice if the drivers were better.  I'm thinking of devling into that myself.  

As far as wireless support goes, I've found the best way to get it to work is to bite the bullet and use ndiswrapper.  there are plenty of good how-tos around.  I've also found that for some reason networkmanager-gnome always fails, espically on WPA and WPA2 networks.  My solution?  remove network-manager-gnome and install WCID.  do a search for it on these forums, and you'll find a link to download it.  it's a wonderful program that seems to have no problem handeling encryption.

Good luck, and don't give up.  Ubuntu on my MBP is great!

Russo

---

