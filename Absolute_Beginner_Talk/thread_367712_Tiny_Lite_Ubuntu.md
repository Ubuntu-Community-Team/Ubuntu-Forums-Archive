---
title: "Tiny Lite Ubuntu ??"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by sabme on 2007-02-22
Hello

Don't know where best to post this request so just diving in.

Why doesn't Ubuntu come as a Lite version?  Can't the guys that develop Ubuntu allow us to choose what packages we want during installation?  

This would be easy enough & doesn't have to be confusing.  Just have an advanced section in the installer which allows us to choose our packages, maybe with some useful presets like, minimum, full, etc.

I've scowered the web for help on this & found:
* UbuntuLite - seems to have dried up.
* BeatrIX - same,  
* BeaFanatIX - more promising but only uses Breezy packages, 
* nUbuntu - only just discovered, can't comment yet

Still don't see why we can't just have a minimal install straight from Ubuntu.

Sab

---

### Post by teaker1s on 2007-02-22
possibly because the goal is a fully featured desktop with or without internet access and therefor the bare min is done to match this

---

### Post by lucia_engel on 2007-02-22
You can install a command-line system. (only available on Alternate Install disc so there's no gui installer)[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

Then install, xorg and choose a Windows Manager or a DE. Add synaptic (if you want the gui) and you're good to go.

---

### Post by nickoli_02 on 2007-02-22
Like lucia said, there is an option when you first install Ubuntu to install a server. This basically installs Ubuntu with minimal packages, so all you get is the basics and a command line. This is most likely as close as a "tiny lite Ubuntu" as it'll ever get, since, like stated above, the goal of Ubuntu is to be a fully featured desktop OS, not a tiny OS for conservative hardware specs.

---

### Post by tgalati4 on 2007-02-22
If you need something lighter than Xubuntu then it's time to try damn small linux.  damnsmalllinux.org

---

### Post by sabme on 2007-02-22
Thanks guys for your tips.

I didn't realise I had to choose the command line install on the alternate cd to get a server install.  Thanks for the link I'll be giving that a go.

I still think there is a place for a minimal Ubuntu disk.  One distro that started to get me hooked on Linux was Slax precisely because it was small and a live cd that did mostly everything I needed.  I just missed being able to install in as a real system.

Ubuntu gave me renewed confidence in Linux and promoting it to friends but I'm sure you could get more hooked if there was a lite version from the outset; smaller download, faster install, etc.  And if folks really like it they can upgrade there existing system without too much  hassel.

I just think that would be a good move for the Linux world.

I like DSL in principle but I have trouble with it recognising all my hardware.

Cheers

---

### Post by lhtown on 2007-02-22
Xubuntu in Fiesty feels pretty fast to me compared to Gnome. Of course, it isn't among the super-lights, but it still provides a user experience similar to Kde and Gnome.

---

### Post by gigaferz on 2007-02-22
Why don't you try Fluxbuntu, its like DSL but its ubuntu, so anything you need you can find it here!!

I tried dsl and puppy but their communtit,its,,well,,like those distros, small. Besides I think Debian distros offer more packages and programs for the user.

I am on the "test period" on an old gateway, and its damn fast!,

However!!!!!

It does not have some packages or applications, but you can get those later (i guess?)

---

### Post by kerry_s on 2007-02-22
Here's the mini.iso net installer-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
With this you can choose to install any ubuntu desktop or go strait for a server/command-line system build up.

---

### Post by sabme on 2007-02-22
Thanks all again

Trying out Fluxbuntu now under VMWare.  My Virtual Machine folder after install is around 1GB.

Thanks for the tip on the netboot mini.iso!  How come I never heard of that before.  I think that should get more publicity!

Sab

---

### Post by zombiepkx on 2007-02-22
Just start off with XFCE then switch over to gnome manually choosing the packages you want, then completely uninstall Xubuntu

---

### Post by sabme on 2007-02-25
Hey zombiepkx  

     "Just start off with XFCE then switch over to gnome manually choosing the packages you want, then completely uninstall Xubuntu"

Can you elaborate?  Do you mean install Xubuntu first or do you mean do the 'command line system' install then install XFCE?  

I'd rather switch over to KDE but either way how do I switch over?

Also how do I completely uninstall Xubuntu.  I don't know linux packages well enough to know everything I can get away with removing.

This does sound like a promising approach if you can get back to me.

Thanks

---

### Post by sabme on 2007-02-25
Hello

Tried the 'install a command line system' but it didn't pick up my wireless card (ipw 3945).  Anyone know why that was but more importantly how to fix it?

Also most times I try to install new packages (sudo aptitude install ...) it asks me for my install cd which is a pain.  Is there a way round this?

If I wanted to install KDE on top of the command line system what do I put here:
sudo aptitude install ... ?

Thanks

---

### Post by sabme on 2007-02-25
Just tried out Fluxbuntu but it seems to be built on an old version of Ubuntu.

It uses kernel 2.6.15 and Dapper packages.

Although I changed the repositories to edgy and upgraded ubiquity to let me choose where to install grub.  I plan to upgrade other stuff later.

Other niggles are/where:

 *   you can't choose where to install grub with standard system,
 *   you have to redirect the Home Icon on the desktop after install,
 *   no graphical way to shutdown.

Tried to install nUbuntu but hangs at 'configuring sytem locales 78%'

Cheers

---

### Post by sabme on 2007-02-26
If anyone's still following this I'd still like a pure Mini K/X/Ubuntu.  Call or market it as a Web or Browser edition.  Something as small as possible to get people on line, playing media files and into Linux as quick as possible.  Easier to download, given smaller size, faster booting and you can still upgrade as and when.  I think that would be brilliant!

I know other distro's can (try to) do this but they all lack something, usually full hardware compatibility in my case, or successful installation.  Ubuntu has been the best and simplest in all my experience (apart from the choose you own root partition bug in Ubiquity).  I just wish it were smaller and faster.

---

### Post by bodhi.zazen on 2007-02-26
For the moment I can think of only the following :

1. Fluxbuntu will be coming out with a new release 7.04 with will be much more polished.

2. In the mean time, you can do a server install + minimal gnome (or other window manager).

[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

3. Take a look at Zenwalk, it seems right up your alley ...

4. Then again, ELive is also nice ...

---

### Post by sabme on 2007-03-11
Hi

OK I'll give ZenWalk a try.

But can someone tell me why if I do a '[COLOR="Navy"]command line system only[/COLOR]' (server) install I don't seem to have my IPW 3945 installed??

Thanks

---

### Post by igknighted on 2007-03-11
> **sabme said:**
> Hi

OK I'll give ZenWalk a try.

But can someone tell me why if I do a '[COLOR="Navy"]command line system only[/COLOR]' (server) install I don't seem to have my IPW 3945 installed??

Thanks

Probably there was no wireless because the "CLI" install is really the server install, and not a lot of servers use wireless, so I doubt they thought it an important package to include.

---

### Post by sabme on 2007-03-11
Any idea how I get the wireless working?  
Hopefully nothing too complicated.

I searched Synaptic for ipw3945 but nothing.

> Zombiepkx
Just start off with XFCE then switch over to gnome manually choosing the packages you want, then completely uninstall Xubuntu

Can you give some more detail.  How do I completely remove Xubuntu?

Thanks

---

### Post by sabme on 2007-03-13
Found the answer to my wireless problem:

sudo aptitude install linux-restricted-modules-generic

Still would like some pointers as to what to remove from Xubuntu.

Thanks

---

### Post by sabme on 2007-03-13
I wasn't all that impressed with ZenWalk Live CD.  It didn't pick up my IPW3945.

I am a bit of a fan of Fluxbuntu though so I'm looking forward to a newer release.  I have used the current Fluxbuntu and upgraded the packages to Edgy.

Ta

---

### Post by sabme on 2007-03-13
So I got my wireless working but Firefox scrolls pages unbelievably slowly.

Anyone know why that is?

---

### Post by freebird54 on 2007-03-13
If you upgraded to Edgy - you probably picked up the ipv6 defaulting to 'ON' problem.  Just blacklist ipv6, and perhaps set the 'network_disable_ipv6' to TRUE in Firefox (address about:config) by double-clicking on it.

If you need more detail I'll try to do better - but I'm on an old Win laptop right now with no links/bookmarks/notes/Firefox to check with!  The only thing worse would be no internet!

Hope this helps...


BTW - speaking of tiny lite Ubuntu - is it possible to get one so small that it'll run on this Win95/98 laptop?  All it needs to do is logon to an Ubuntu box and run things on it!  Even this box OUGHT to be able to do that...

---

### Post by kerry_s on 2007-03-13
> BTW - speaking of tiny lite Ubuntu - is it possible to get one so small that it'll run on this Win95/98 laptop? All it needs to do is logon to an Ubuntu box and run things on it! Even this box OUGHT to be able to do that...

Yes, you can do a custom install. You just do a server install which is the base system with no gui yet. It's just base that you can build on to get only exactly what you need.

Net installer, you need internet.
edgy iso-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

fiesty iso-> [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso)


server install
login
sudo su
(edgy, you have to turn all the repos on,fiesty you can skip this step)
nano /etc/apt/sources.list
uncomment(#) all the deb lines
ctrl and x and y and enter to save
apt-get update
apt-get install xorg gdm synaptic (DE/WM) (what ever else you want)
DE examples:
apt-get install xorg gdm synaptic gnome-core
apt-get install xorg kdm synaptic kde-core
WM examples:
apt-get install xorg gdm synaptic xfce4 leafpad
apt-get install xorg gdm synaptic icewm icemc emelfm leafpad
apt-get install xorg gdm synaptic fluxbox leafpad emelfm
etc...
reboot
select your session, login, open synaptic and continue building up.

---

### Post by sabme on 2007-03-14
> 
apt-get install x-window-system-core gdm synaptic (DE/WM) (what ever else you want)
DE examples:
apt-get install x-window-system-core gdm synaptic gnome-core
apt-get install x-window-system-core kdm synaptic kde-core
WM examples:
apt-get install x-window-system-core gdm synaptic xfce4 leafpad
apt-get install x-window-system-core gdm synaptic icewm icemc emelfm leafpad
apt-get install x-window-system-core gdm synaptic fluxbox leafpad emelfm
etc...


For Edgy you need to change 'x-window-system-core' to 'xorg'.  Obviously without quotes ''.

You could also use the xfce login manager 'xdm'.

You might also need 'fluxconf' when installing fluxbox.

---

### Post by sabme on 2007-03-14
So far with:
[COLOR="Navy"]linux-restricted-modules-generic fluxbox firebird mozilla-thunderbird synaptic mousepad thunar gaim[/COLOR]
,a few other packages and an upgrade my system is now bigger than when I installed Fluxubuntu!

I'm assuming the [COLOR="Navy"]linux-restricted-modules-generic[/COLOR] was the real biggy.  If so there must be a simpler way to get my wireless working.  Can anyone help?  Otherwise I have to stick with Fluxubuntu and nUbuntu.

Apart from the locale being stuck on US English, nUbuntu is my favourite.  I would go with BeaFanatix but the kernel's too old to support my network interfaces.

I still think there is a place for a Mini Ubuntu Mubuntu.  I would start a project if I had the know how and time.  

If BeaFanatix can make a decent live & instalable cd at 160MB using Gnome and Dapper packages I'm sure a sub 200MB Ubuntu could be done.

Cheers

---

### Post by kerry_s on 2007-03-14
> **sabme said:**
> For Edgy you need to change 'x-window-system-core' to 'xorg'.  Obviously without quotes ''.

You could also use the xfce login manager 'xdm'.

You might also need 'fluxconf' when installing fluxbox.

Alright, i see what they did, updated x-window-system-core to xorg.
Xdm is old as crap and gives problems with the new xorg.

---

### Post by noalternative on 2007-03-15
There is a tiny version of ubuntu called "[ubuntu-lite]("http://ubuntuforums.org/showthread.php?t=98233")"  It is based on icewm.  Icewm starts twice a quickly as fluxbox.

also consider installing jwm.  It starts almost twice as quickly as icewm.

---

### Post by sabme on 2007-03-17
> **noalternative said:**
> ... called "[ubuntu-lite]("http://ubuntuforums.org/showthread.php?t=98233")".

I would give it a try if there site was ever working.  Has development stopped?

---

### Post by Kateikyoushi on 2007-03-17
You can grab it from this site. [LINK]("http://groups.google.com.au/group/ubuntu_lite")

---

### Post by noalternative on 2007-03-20
> **sabme said:**
> So I got my wireless working but Firefox scrolls pages unbelievably slowly.

Anyone know why that is?

Firefox has a flaw in how it handles memory.  It can be [corrected.]("http://www.freerepublic.com/focus/f-bloggers/1327586/posts")

---

### Post by noalternative on 2007-03-20
> **sabme said:**
> I would give it a try if there site was ever working.  Has development stopped?

It has a mailing list [Shae Smittie has taken over development]("http://groups.google.com/group/ubuntu_lite?lnk=sg")

---

