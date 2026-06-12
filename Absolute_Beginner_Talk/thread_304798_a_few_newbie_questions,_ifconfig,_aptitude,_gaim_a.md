---
title: "a few newbie questions, ifconfig, aptitude, gaim and recording"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by izua on 2006-11-22
hey everyone!
I'm Richard and i just got my Kubuntu CD-s a few days ago.

A few words on my background, I'm an amateur programmer for about 5 years, and i covered most of the topics i could, 3d graphics, windows and GUIs, algorithms and web development. I've became pissed at windows and it's limitations a while ago, and i decided to move steadily to linux.

First thing I tried was to configure my net connection. I've been pointed out at ifconfig, I tried it for a while, without doing anything useful. At a latter point, i realised there was some app in KDE, similar to control panel, that helped me configure my network cards (yes, i have two of 'em, I also have a local network). Job done, but how do I do the same thing from the terminal with ifconfig? I've got a weird netmask (255.255.252.0, and the gateway is not in the same C-Class with my IP)

Next, I realised the wonder of aptitude. Having all the software I ever need managed by one program looked great at first. Horribly later, when I tried to install GAIM. It can't, it gives me a BREAK(INSTALL). From what i understood, it's conflicting with another package.

Latter, I installed apache 1.33. It works fine, i even managed to get a page up, but, when i went to php, it won't let me install  libapache-mod-php5. It's conflicting with libapache-mod-php4, but i don't have php4 installed. Tried running an apt-get remove libapache-mod-php4, but, ta-da, that's not installed. I don't get it how a package can conflict with an uninstalled package. This is just too weird. ](*,) 

I'm not even thinking right now at the trouble I'll be having in setting up mysql.

Next, I've been playing guitar for a while, and had everything done with cubase. I need VST chaining, real time processing, monitoring (sound output through the VST chain while i play) and recording, and of course, some method of using VST in nix. I heard it's a real pain, since VST are win32 natives. I'd also need something to play multiple tracks at once (i think sampler is the word).

If anyone can help me, with anything, please reply.
Thanks, and sorry for my bad English,
Richard

---

### Post by Bachstelze on 2006-11-22
Hi and welcome to Ubuntu :)

1. if your network is already configured in static mode and you just want to change the paremeters (IP, netmask, gateway), you can do so by editing the file */etc/network/interfaces* and filling in the correct values. Then restart your networking with 

```
sudo ifdown eth0 && sudo ifup eth0
```

don't forget to change eth0 to the correct interface if needed :)

2. Please paste the output of

```
sudo apt-get install gaim
```

3. Try installing php5 with it's metapackage, like this

```
sudo apt-get install php5
```

if it doesn't work, paste the output as well.

4. I can't help you here, I just play the drums :p

---

### Post by steve.horsley on 2006-11-22
For the network connection, you can do this with ifconfig. Something like:
[B]sudo ifconfig eth0 1.2.3.4 netmask 255.255.252.0
sudo route add default gw 1.2.0.254[/B]
See **man ifconfig** and **man route**.

But these changes are lost when you reboot. Have a look at the file /etc/network/interfaces. This is where the settings are stored. See **man interfaces** for the gory details.

---

### Post by izua on 2006-11-22
ok, thanks.
if I'd tell you copy-paste doesn't work, would you think I'm crazy?

php5 via metapackage says "php5 is already at it's newest version" but no php files work, either embedded in html, or as pure php files.

gaim complains about a few dependencies:
libatk1.0.0 >= 1.9.0
libgtk2.0-0 >= 2.8.0 q
libgtkspell0 >= 2.0.2
liblaunchpad-integration0 >= 0.0patch26
libmeanwhile1 >= 1.0.0
libpango1.0-0 >= 1.12.3

But after each one, it says "but it is not installable".

after all these, comes an "E: Broken packages" and returns back my prompt.

---

### Post by izua on 2006-11-22
erm.. anyone?:p

---

