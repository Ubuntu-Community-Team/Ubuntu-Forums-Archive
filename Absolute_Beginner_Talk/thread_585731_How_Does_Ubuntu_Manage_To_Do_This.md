---
title: "How Does Ubuntu Manage To Do This?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2007-10-21
Hi everyone at UbuntuForums.org,

I want to install Ubuntu 7.10 on my Dell laptop that I am planning on purchasing. However, I was just wondering if someone could answer my questions.

[LIST]
[*]In Windows, anti-virus and anti-spyware software is usally needed to ensure a secure computer. I understand that Ubuntu does not need these security measures. Is this correct? If so, why is this?
[*]Does Ubuntu come with a software firewall installed by default?
[*]Will I be able to communicate with my Windows Live Messenger (MSN) contacts using GAIM or Pidgin?
[*]Is it easy to make Ubuntu be able to play .mp3s?
[*]Is it possible to play retail DVD movie disks in Ubuntu?
[/LIST]

Thanks very much for your time and help.

---

### Post by s3a on 2007-10-21
> **Crumpets and Jam said:**
> Hi everyone at UbuntuForums.org,

I want to install Ubuntu 7.10 on my Dell laptop that I am planning on purchasing. However, I was just wondering if someone could answer my questions.

[LIST]
[*]In Windows, anti-virus and anti-spyware software is usally needed to ensure a secure computer. I understand that Ubuntu does not need these security measures. Is this correct? If so, why is this?
[*]Does Ubuntu come with a software firewall installed by default?
[*]Will I be able to communicate with my Windows Live Messenger (MSN) contacts using GAIM or Pidgin?
[*]Is it easy to make Ubuntu be able to play .mp3s?
[*]Is it possible to play retail DVD movie disks in Ubuntu?
[/LIST]

Thanks very much for your time and help.
Antivirus is not needed because it doesn't affect this operating system not to mention you have to give the virus permission by typing your password to allow it to affect your computer (if it can anyway). No firewall or antivirus software is pre-installed to my knowledge however firestarter is a good firewall and clamav is a good antivirus software. Yes, Pidgin or Gaim allow you to communicate to people who use MSN (=Windows Live Messenger). You can listen to mp3's and watch DVD's easily on the two latest Ubuntu versions (Ubuntu 7.04 & 7.10), however, for it to be simple, you will need an internet connection.

---

### Post by ed-koala on 2007-10-21
* In Windows, anti-virus and anti-spyware software is usally needed to ensure a secure computer. I understand that Ubuntu does not need these security measures. Is this correct? If so, why is this?

Anti-virus and anti-spyware not needed. The short version:  Linux is built upon the very secure Unix platform, and also isn't popular enough for hackers to waste their time trying compared to the gazillion vulnerable Windows machines out there

    * Does Ubuntu come with a software firewall installed by default?

Not that I'm aware of, but not 100% sure.

    * Will I be able to communicate with my Windows Live Messenger (MSN) contacts using GAIM or Pidgin?

You should be able to, plenty of threads on here on that subject if you have trouble.

    * Is it easy to make Ubuntu be able to play .mp3s?

Yes.

    * Is it possible to play retail DVD movie disks in Ubuntu?

Yes.

Load it up and enjoy!  I'm not going back to Windows!!!

---

### Post by Steveway on 2007-10-21
As an addition to my previous posters:
Ubuntu comes with a firewall called IPtables, it is allready setup perfect for a normal Desktop-computer, so you won't need to configure it.
Firestarter is only a frontend to configure Iptables.

---

### Post by Tux Aubrey on 2007-10-21
Welcome.  See below

---

### Post by Tux Aubrey on 2007-10-21
> In Windows, anti-virus and anti-spyware software is usally needed to ensure a secure computer. I understand that Ubuntu does not need these security measures. Is this correct? If so, why is this? 

You don't need this stuff unless you are transfering stuff to a windows machine via ubuntu - and only then to protect the windows box.  Ubuntu uses an entirely different security model to windows and 99% of viruses are built for windows so won't do anything in a 'nix environment anyway.  There are virus checkers available if you want one.

> Does Ubuntu come with a software firewall installed by default? 

Afirewall is installed but not activated by default - there are no open ports to protect in a default install (unlike windows).  iptables is the basic utility and you can install a graphical frontend called Firestarter if you want it.

> Will I be able to communicate with my Windows Live Messenger (MSN) contacts using GAIM or Pidgin? 

I believe so.

> Is it easy to make Ubuntu be able to play .mp3s? 

Yes. See [here]("https://help.ubuntu.com/community/RestrictedFormats").

> Is it possible to play retail DVD movie disks in Ubuntu? 

Yes.  A bit more involved that the mp3 trick, but certainly do-able.  See the link above.


Welcome to the community!

---

### Post by Paul820 on 2007-10-21
1) Linux by default is locked down so you need 'sudo' privaliges to do anything that will modify your system. Therefore a virus cannot do anything as it's needs the root password to do it. And the only person that can give it the password is you, or the system administrator. **So never log in as root.**

2) Ubuntu uses ipTables that is the firewall. If you want to tweak them you can install firestarter. So yes, there is a built in firewall and it's very good.

3) Yes.

4) Click on an mp3 and ubuntu will get the codecs for you.

5) Yes. To play encrypted dvd's you need libdvdcss2.

---

### Post by Nekiruhs on 2007-10-21
The simple truth about not needing anti-virus/spyware is this:
There is no known viruses "in the wild" for Linux. 
Thats not saying there never will be, and its not diminishing the fact that Ubuntu is very secure- For example nothing outside of your home folder (Like my documents) can be modified as an app running as your user without entering your password. This makes it pretty hard to install virii without your knowledge.- It just says that there are no known viruses. 

Yes Ubuntu comes with the firewall IPtables by default, its always running, but CLI only. Fortunatley there are graphical tools to configure it (Firestarter, for example). 

Yes, Pidgin works excellently for IMing people. File transfer works, but voice and video chat do not.

Due to legal issues Ubuntu can't include an MP3 codec by default, but the first time you try to play an MP3 it offers to download and install one for you.

Just open a terminal (Applications > Accessories > Terminal) and copy/paste the below line:
```
sudo apt-get install libdvdcss2
```
Then enter your password, and watch as it installs. 
Now you can play DVDs

Heres an explanation of the command if you want to know:

sudo tells it to use all permissions (Necessary to install things)
apt-get is the command to manage packages
install tells apt-get to install the package
libdvdcss is the package we need.

---

### Post by Paul820 on 2007-10-21
WOW, you lot type fast. There were no replies when i started. :lolflag:

---

### Post by mlentink on 2007-10-21
> **Crumpets and Jam said:**
> 
[*]In Windows, anti-virus and anti-spyware software is usally needed to ensure a secure computer. I understand that Ubuntu does not need these security measures. Is this correct? If so, why is this?
It's because the developers of Linux are such wonderful sweet guys that wnat to do nothing but keeping al those annoying things away from you. Just kiddin' .  Linux is developed bu people who hateviruses and spyware just as much as you do, and because it was built an a very sound foundation.
> **Crumpets and Jam said:**
> [*]Does Ubuntu come with a software firewall installed by default?Yup. It' s called iptables, which you could try to manage through firestater if you would like to, but if you' re not going to run any servers on your box there's no need to bother.> **Crumpets and Jam said:**
> 
[*]Will I be able to communicate with my Windows Live Messenger (MSN) contacts using GAIM or Pidgin?Sure. Who do you think all those linux-geeks are chatting with... ;-)
> **Crumpets and Jam said:**
> [*]Is it easy to make Ubuntu be able to play .mp3s?I'm listening to one (played by Banshee, btw) right now
> **Crumpets and Jam said:**
> [*]Is it possible to play retail DVD movie disks in Ubuntu?
Yeah. 




btw: Welcome to the Free World. (The real one. Not the one you might think....)

---

### Post by Crumpets and Jam on 2007-10-21
Hey thanks guys. The community on this forum seems to be thriving here, I only went to get a drink and even before I'm back there 8+ replies. I'm my laptop in a few weeks as soon as get some money (I'm 15) so I look forward to sticking around the forums and maybe giving something back to the community (fingers crossed).

---

