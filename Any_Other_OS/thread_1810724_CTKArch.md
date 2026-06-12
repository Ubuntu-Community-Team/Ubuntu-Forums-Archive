---
title: "CTKArch"
date: 2011-07-23
forum: Any Other OS
---

### Post by Timmer1240 on 2011-07-23
I always thought Arch was intimidating but then I learned about CTKarch a preconfigured live version of arch thats installable on a hard drive!Tryed it out on a virtual machine and installed it on there pretty cool Idea for us not as good at Linux.Anyone else tryed out CTK Arch pretty good Idea for the newbies.

---

### Post by Thewhistlingwind on 2011-07-23
The whole appeal of arch is making you feel like a l33t Unix hacker. (Without having to compile.) 

If anything, a preconfigured arch derivative is missing the point. Sort of like the gentoo based distros that try to be cool out of the box.

Not that they don't have a use, just that their going against their community tide.

---

### Post by krapp on 2011-07-23
What does CTK stand for?

---

### Post by MonolithImmortal on 2011-07-23
I always preferred ArchBang as a preconfigured Arch system. The reason I used arch was the rolling release and AUR.

---

### Post by handy on 2011-07-24
Preconfigured are great, but they don't teach you about how Arch works, as going through the installation process goes a long way towards doing.

---

### Post by nothingspecial on 2011-07-24
The arch setup process teaches you how to remove comments from a config file.

Rather like setting up mpd.

---

### Post by handy on 2011-07-24
> **nothingspecial said:**
> The arch setup process teaches you how to remove comments from a config file.

Rather like setting up mpd.

:lolflag:

You are full of it! :P

---

### Post by nothingspecial on 2011-07-24
> **handy said:**
> :lolflag:

You are full of it! :P

It's been at least a year since a post like this. I promised myself never ever, but I cracked :P

---

### Post by trollolo on 2011-07-24
arch is simply hipster-cred without being hardcore enough for gentoo

---

### Post by nothingspecial on 2011-07-24
Gentoo and Arch have absolutely nothing in common (the fact that they are both linux excluded).

Install Arch

run

```
/arch/setup
```

or whatever it is.

Uncomment your location

Uncomment your keyboard

Uncomment the servers in your country

Select somewhere to install grub

pacman -Syu

install X plus desktop environment

done.

Gentoo is something else alltogether.

---

### Post by handy on 2011-07-24
> **nothingspecial said:**
> Gentoo and Arch have absolutely nothing in common (the fact that they are both linux excluded).

Install Arch

run

```
/arch/setup
```

or whatever it is.

Uncomment your location

Uncomment your keyboard

Uncomment the servers in your country

Select somewhere to install grub

pacman -Syu

install X plus desktop environment

done.

Gentoo is something else alltogether.

Like I said before...

Except you have more of it than I gave you credit for! =D>

---

### Post by nothingspecial on 2011-07-24
> **handy said:**
> Like I said before...

Except you have more of it than I gave you credit for! =D>

I'm just getting warmed up :P

To me, installing Arch teaches you nothing more (arch specific stuff aside) about linux than installing Ubuntu minimal.

Apart from having to specify your own keyboard layout.

---

### Post by handy on 2011-07-24
> **nothingspecial said:**
> 
I'm just getting warmed up :P 

Does that mean it will run thinner & faster?

> **nothingspecial said:**
> 
To me, installing Arch teaches you nothing more (arch specific stuff aside) about linux than installing Ubuntu minimal. ...

Don't know about an Ubuntu minimal install.

Arch gave me all but complete control of my system;- what is installed on it, how it looks, everything but the "core" is up to me. (I know that Arch is not alone in this ability.)

I really like how the maintenance is handled in such a simple fashion. There are so few config files that I have to deal with. If I want to change any of my rolling release specifics I use /etc/pacman.d/mirrorlist or more likely /etc/pacman.conf .

If on the very rare occasion I upgrade (do it everyday) & some bug has come down from upstream, then I use the following command to restore the previous version from my cache:

pacman -U /path/to/package/package_name-version.pkg.tar.gz

The list of upgraded packages are in the /var/log/pacman.log .

Most everything else that I ever need to bother with is in /etc/rc.conf
```

#
# /etc/rc.conf - Main Configuration for Arch Linux
#
# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_AU.utf8"
HARDWARECLOCK="UTC"
TIMEZONE="Australia/Sydney"
KEYMAP="us"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

#
# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# Scan hardware and load required modules at bootup, following line is
# required for udev, which is in the process of replacing hal. 
# Nolonger need to load the @hal DAEMON, but it must still be installed for
# for the sake of Worker.
#
MOD_AUTOLOAD="yes"
#
# ***** MODULE BLACKLIST IS NOW DEPRECATED **************************
# Module Blacklist - modules in this list will never be loaded by udev
# MOD_BLACKLIST=(net-pf-10 pcspkr) ## turns off ipv6 & pc speaker
# *******************************************************************
#
# Modules to load at boot-up (in this order)
#   - prefix a module with a ! to blacklist it
#
MODULES=(!net-pf-10 !pcspkr sky2 snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore fuse radeon cdc-acm ftdi_sio) ## fglrx
#
# You scan for LVM volume groups at startup, required if you use LVM
USELVM="no"
#
# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
HOSTNAME="archtypical"
#
# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available
# interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
#
# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")
#
lo="lo 127.0.0.1"
#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255" ### uncommented
### for radeon-tesing kernel network bug, if need to re-enable check settings
### with ifconfig -a
eth0="dhcp"
INTERFACES=(lo eth0)
#
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in RO[Edit:2]UTES with a ! to disable it
#
#gateway="default gw 192.168.0.1"  ### uncommented in attempt to get around 
### radeon-testing kernel network failure bug, if need to use, check IPCop address.
ROUTES=(gateway)
#
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network-profiles
#
#NET_PROFILES=(main)
#
#
# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
### handy - @hal - out though still installed due to Worker;
### @fam replaced by gamin, which auto loads ###
### @sensors -> for lm-sensors, monitoring of hardware; fans, temps & such ###

DAEMONS=(syslog-ng network rpcbind nfs-common @netfs @polipo @crond @sshd @sensors @alsa @stb-sdmin @gpm)

# End of file

```

Beyond that, there's ~/.bashrc which rarely gets touched these days as it suits my desires.

The same goes for the ~/.config/openbox/autostart.sh & rc.xml files. Once you have Openbox setup how you want it, there isn't much that you need to do beyond modify your menu occasionally. The same goes for the GTK theme I use with Openbox; once setup, forget about it.

So really, the differences that you & I are looking at you articulated in your reply. I've not said anything about Arch teaching a person more about Linux, I say that a person will learn much more about how Arch works if they follow the Beginners' Guide to install it than if they use one of the quick install Arch spin-off's. Arch IS different than the other distros, (that I've seen anyway) & I think that it is essential that an Arch based distro user knows about those differences, so (again) doing a full install teaches you about those fundamentals.

I installed Arch on No.1 box, nearly 3.5 years ago now; during that time I have been learning a lot more about Linux. Arch still uses the Linux kernel, it just does so in a simpler manner than the other distros. :)

---

### Post by nothingspecial on 2011-07-25
I have a heavily edited rc.xml that I modified from the default crunchbang one somewhere. I found it easier to strip and modify that than write it from scratch.

The arch wiki is an excellent piece of documentation and I have made use of it many times whatever distro I happen to be using.

That being said, and I'm sure I've posted this before, but can't find it......


I saw a post in this forums absolute beginner section.

The user had just installed Ubuntu for the first time that morning and was trying to set up his dual monitors. For some reason google led him to the arch-wiki.

[https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)

Now bear in mind this guy doesn't know the first thing about linux. He thinks Ubuntu is linux and doesn't know what a distro is. All the information in that page looks like gobbldygook to him, but he want's his dual monitors. So even though he already has xorg-xserver (and gnome, unity etc) and a perfectly good Ubuntu install, he tries it.

He's hoping that if he copies and pastes all that nonsense into a termina, it might resolve his situation so he does

```
pacman -Syu xorg-xserver
```

Gnome terminal helpfuly informs him that

```
The program 'pacman' is currently not installed.  You can install it by typing:
sudo apt-get install pacman

```

ok, so he follows the instructions. Then tried the first command again. Imagine his suprise when this happened



[ATTACH]198379[/ATTACH]

---

### Post by handy on 2011-07-25
So what does your post have to do with anything that is being discussed in this thread nothingspecial?

---

### Post by nothingspecial on 2011-07-25
> **handy said:**
> So what does your post have to do with anything that is being discussed in this thread nothingspecial?

Not a lot really.

We were discussing Arch and I was pointing out how useful I've found the arch wiki which reminded me of the help thread, so I posted it.

Not completely offtopic, but I can see why you asked.

---

