---
title: "Minimal ubuntu/GNOME install w/ no apps"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Amiga on 2006-07-02
I want to install ubuntu and GNOME with really nothing other than Synaptic. I would rather learn how to install things on my own and a lot of the default applications aren't my cup of tea.

From this post, [http://www.ubuntuforums.org/showpost.php?p=1193615&postcount=14](http://www.ubuntuforums.org/showpost.php?p=1193615&postcount=14) , it looks as though I need to use the Alternate Install CD and do a server install.

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic

Is the software that is listed above installed from the Alternate Install CD or downloaded from the net? I just want to make sure I have the latest Firefox, which I assume I could download through Synaptic. Am I able to skip any of the software mentioned above and still have a usable UI?

---

### Post by DJ Scribblinni on 2006-07-02
Here's a link to the so called Alternate Install .iso's.  Which includes not only the usual desktop that most users use, but also a server install, and thee alternate install. 
[http://releases.ubuntu.com/6.06/]("http://releases.ubuntu.com/6.06/")
This obviously using the Dapper release.  
Hope that helps.....

---

### Post by woedend on 2006-07-02
it should pick the latest for you(ie, if firefox on the net is newer, grab it).
but the lines there don't install gnome by default.  But i'd say thats one of the smallest usable UI's you could get.

---

### Post by muep on 2006-07-02
Hi.

Software is installed from the install cd when the most recent version is available there, but you probably edit your sources.list right after the installation, so it is likely that you disable the cd repository right away.

After the server install you will only have the command line, so be prepared to use the command line. It's not hard. 

You might miss some graphical config tools, too. In addition, the command you have doesn't seem to install gnome, but Icewm instead.

sudo aptitude install gnome may solve that, but I'm not sure.

---

### Post by John.Michael.Kane on 2006-07-02
The server install is a good way to go if your trying to learn command line/custom installing.when your more comfortable with linux,and have the time have a look at [**this**]("http://www.linuxfromscratch.org/").

---

### Post by Amiga on 2006-07-02
Okay, anyone able to alter these lines to just give me GNOME & Synaptic please?

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic

---

### Post by John.Michael.Kane on 2006-07-02
[QUOTE=Amiga]Okay, anyone able to alter these lines to just give me GNOME & Synaptic please?

sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic[/QUOTE]


Frist of all installing gnome will give you file-roller evolution ect. if you still want to install gnome fine.

sudo aptitude install x-window-system-core gnome-desktop-environment firefox synaptic

---

### Post by fparri on 2006-07-04
[QUOTE=SD-Plissken]sudo aptitude install x-window-system-core gnome-desktop-environment firefox synaptic[/QUOTE]

Not gnome-desktop-environment, but gnome-core, which should install less applications ;)

---

### Post by nuihc on 2006-08-11
If you only install gnome-core you don't get a window manager (e.g. gdm)

In addition to the above packages I can recommend xubuntu-system-tools and gnome-app-install. If you install these you get all(?) the tools in the System-Administration menu. You also get Applications-Add/Remove...

A complete semi minimalistic gnome installation would be:
[FONT="Courier New"]sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install[/FONT]

/nuihc

---

### Post by starscalling on 2006-10-24
yeah you can get it with gnome-core etc in under a gig

---

### Post by veli on 2006-10-30
How is the situation with minimal install on edgy?

I tried the suggested set-up for minimal gnome from Edgy-server, but it seems that in Edgy the packages are different, i.e, there is no gnome-core, neither x-window-system core etc.
There were alternative packages proposed, however I couldn't boot into the full desktop. I ended up with the brown screen and a terminal from which I was able to run Firefox and other programs.

Does anybody manage to get the desktop on Edgy Server?

---

### Post by az on 2006-10-30
> **veli said:**
> How is the situation with minimal install on edgy?

I tried the suggested set-up for minimal gnome from Edgy-server, but it seems that in Edgy the packages are different, i.e, there is no gnome-core, neither x-window-system core etc.
There were alternative packages proposed, however I couldn't boot into the full desktop. I ended up with the brown screen and a terminal from which I was able to run Firefox and other programs.

Does anybody manage to get the desktop on Edgy Server?

Did you enable the universe repo?

Also, install linux-386 if you installed from the server cd; otherwise you get the server kernel which may or may not work with your desktop hardware (mouse, etc...)

---

### Post by veli on 2006-10-31
I think I enabled all repos by uncommenting in the source list. I did that with nano, saved the file, but I didn't know how to go back to the command line. Just restarted, and did apt-get inastall .... etc.

Probably, I've made a mistake somewhere. Anyway, I install the Edgy desktop and remove the programs I don't use.

The reason to try on the minimal gnome install is that when I remove the unneeded packages, the sound disappears and it's available only after moving the PCM and Volume sliders in the sound mixer. This is not a big deal, but it's a bit annoying. I tried many options to solve the sound problem, but no luck so far.
I just believe that installing only the minimum packages will not make the sound disappear??

I'll try some day again.

---

### Post by veli on 2006-10-31
I'm looking at the alternate CD options. It misses the "install server" option, but it has "install command line system".

Does anybody know what exactly it's going to be installed by doing this? Is it gonna be e server, or just the desktop command line without the desktop?

Veli,

---

### Post by az on 2006-11-01
> **veli said:**
> I think I enabled all repos by uncommenting in the source list. I did that with nano, saved the file, but I didn't know how to go back to the command line. Just restarted, and did apt-get inastall .... etc.

You need to do 

sudo apt-get update

first.

---

### Post by az on 2006-11-01
> **veli said:**
> I'm looking at the alternate CD options. It misses the "install server" option, but it has "install command line system".

Does anybody know what exactly it's going to be installed by doing this? Is it gonna be e server, or just the desktop command line without the desktop?

Veli,

A "server" install is just that - a bbase system with noting else installed.

To install a LAMP server, install the base system and then install

apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by tolder on 2006-11-02
A complete semi minimalistic gnome installation would be:
[FONT="Courier New"]sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install[/FONT]

/nuihc[/QUOTE]


Works great , better than PCLinuxOS "minimal" distro, but then - it is using the terrible / horrible KDE desktop !




Regards

---

### Post by stream303 on 2006-11-03
Heh, got me thinking about a "retro-Ubuntu" :)

Maybe minimal server install, basic xwindow with default TWM as the window manager. (Okay, maybe get FVWM2 - pick your low-resource fav).

Mutt for mail
SLRN for newsgroups etc.
Lynx and LINKS for web...
Well, since we have xwindow installed maybe throw in ImageMagick for good measure..

Reminds me of my old Slackware / *BSD boxes a few years ago..
Wish I had an old one around - this would be a fun project, although the ease of apt-get might take the thrill out of downloading source.. :)

So, get a basic usable system up and running with minimal hassle and take it from there.  Sorry, guess I'm getting off-topic..

---

### Post by tolder on 2006-11-04
> **stream303 said:**
> Heh, got me thinking about a "retro-Ubuntu" :)



Well, I'm just experimenting with a distro, abel to act as a Citrix / Cisco VPN client (to replace Windows 95).



Regards

---

### Post by myuninstalledlife.com on 2006-11-04
Hi guys, thanks for helping us newbies out ;). I did a command-line installation and then I did:
[FONT="Courier New"]sudo apt-get update[/FONT]
...and then:
[FONT="Courier New"]sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install
[/FONT]
I reboot and get to a good-looking Ubunto-login screen. I login but all I get to is a brown background with a black commandwindow at the top to the left. Do I need to do anything else to get to the menu? (see attached screendump)

---

### Post by veli on 2006-11-07
For the minimal Gnome install of Dapper, which is better to use:

x-window-system-core
or
xserver-xorg-core

Actually, what is the difference between both.

---

### Post by mtecknology on 2008-02-12
There is no difference, one is a link to the other.

---

### Post by mtecknology on 2008-02-12
sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install

That will give you a "minimal" gnome installation. This means, no menu bar, no desktop, no time, nothing. You can choose to install each of these packages separately or to install all gnome packages with ubuntu-desktop.

This really is exactly what you want.

Minimal Install: sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install

All Gnome: sudo aptitude install ubuntu-desktop

---

### Post by kerry_s on 2008-02-12
> **myuninstalledlife.com said:**
> Hi guys, thanks for helping us newbies out ;). I did a command-line installation and then I did:
[FONT="Courier New"]sudo apt-get update[/FONT]
...and then:
[FONT="Courier New"]sudo aptitude install x-window-system-core gnome-core gdm firefox synaptic xubuntu-system-tools gnome-app-install
[/FONT]
I reboot and get to a good-looking Ubunto-login screen. I login but all I get to is a brown background with a black commandwindow at the top to the left. Do I need to do anything else to get to the menu? (see attached screendump)


did you select gnome in the login menu?

i would, if it were me:
sudo apt-get install xorg gdm gnome-core synaptic menu
reboot(ctrl+alt+delete)

you can install the rest when you get to the desktop.

---

