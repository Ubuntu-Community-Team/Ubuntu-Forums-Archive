---
title: "Lightweight Ubuntu vs. mini distro - efficiency"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by secdroid on 2006-08-31
I'm a happy Ubuntu Dapper user (former Fedora user) on my main box.

I've been experimenting with Xubuntu, Ubuntu server install with Icewm, Ubuntu server install with Fluxbox, and some mini distros, with a view toward giving new life to a 300 Mhz/192 MB laptop.  

I'm not sure how to evaluate how CPU and space-efficient the core of Ubuntu (no GUI) is compared to the core of the mini distros.  (My test box is 750 Mhz/378 MB, so it isn't a challenge).

A lite install of Ubuntu with appropriate WM has the advantages of the Ubuntu repositories and user community.  OTOH, DSL and other mini distos are likely more efficient.

I've come to the conclusion that Xubuntu might be a bit of a tight fit on the laptop, but that Ubuntu server with Fluxbox and Thunar might be about right.

Appreciate comments & suggestions from those of you with more experience.

---

### Post by bodhi.zazen on 2006-08-31
Ubuntu server + fluxbox is how I go these days.

Consider xfe or rox as an alternate to Thunar.

Advantages: Ubuntu repository and community.

Alternates: Debian server install, Vector, Zenwalk.

---

### Post by secdroid on 2006-08-31
Thanks for the comments.  Will check out xfe & rox.

I just tried Zenwalk (Xfce) on my "rocket ship" 750 Mhz/378 MB test box.  Nice distro, but didn't feel appreciably faster than Ubuntu server & Fluxbox on the same machine.  The difference might have been more apparent with less memory.

For anyone else interested in this topic, I just ran across an article "Linux distros for older hardware" at [http://www.linux.com/article.pl?sid=06/02/13/1854251]("http://www.linux.com/article.pl?sid=06/02/13/1854251")
  The author is Joe 'Zonker' Brockmeier, who is usually worth reading.  The test box he used is "Pentium II 233MHz machine with 64MB of RAM, an 8x CD-ROM drive, a 3GB hard drive, and an integrated ATI 3D Rage Pro video card with 4MB of video RAM," not too dissimilar from the sort of old laptops people use for lightweight installs.

Zonker didn't have Ubuntu, but did try Debian with Blackbox.

---

### Post by kerry_s on 2006-08-31
I use the server install and fluxbox too. I just find it alot better than a premade distro. I love being able to choose what i want. I also like making my own menu. Mini distro's are good but i always find them limiting what i can do or install.Here's my menu and screen shot(duel monitors)->
```
[begin] (Fluxbox)

[exec] (ROX) {rox} 

[submenu] (Terminals)
 [exec] (Eterm) {Eterm}
 [exec] (Eterm-Trans.) {Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false}
 [exec] (Eterm-Trans.-Bar) {Eterm --borderless --trans --shade 0 --scrollbar false}
[end]
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Gaim) {gaim}
[end]

[submenu] (Office)
 [exec] (Gimp) {gimp}
 [exec] (Leafpad) {leafpad}
 [exec] (AbiWord) {abiword}
[end]

[submenu] (Sound)
 [exec] (XMMS) {xmms}
 [exec] (Mplayer) {gmplayer}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {sudo synaptic}
 [exec] (Run-Root) {gksuexec}
 [exec] (Terminal-Root) {sudo Eterm}
[end]

[submenu] (Fluxbox)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {fbrun}
[submenu] (Tools)
 [exec] (Kill) {xkill}
 [exec] (Xfburn) {xfburn}
[end]

[separator]
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---

### Post by secdroid on 2006-08-31
Thanks for the screenshots & fluxbox menu.  Very nice!

Downloaded Rox to my test box.  _Very interesting._  Still got some learning to do, but it is far more powerful than Thunar.  Fast!

Conky looks like a big improvement on Torsmo.  Hadn't seen it before, but it is going on my "must have" list.

I suspect that Damn Small Linux must sacrifice some speed because it must decompress applications on-the-fly.  (Maximizes space-efficiency, at the expense of speed.)  Looks like Ubuntu server install + lightweight WM & lightweight apps will be larger, but faster.  Each approach has plusses & minuses.  I prefer the Ubuntu approach.

Appreciate the tips, kerry_s & bodhi.zazen.

---

### Post by dannyboy79 on 2006-08-31
I have Xubuntu installed on a Pentium MMX 266mhz with 128 mb ram and it runs fine. I use Opera instead of Firefox because Firefox was slower than a snail! Everything is cool. there are a few things I don't like about Xubuntu but I am still leearning Linux so I am not giving up on this Lite Distro just yet!

---

### Post by secdroid on 2006-08-31
I'm impressed, dannyboy79.  I thought Xubuntu was just too "rich" to run well in 128 MB.  

Opera makes sense.  For even faster browsing, you might try Dillo.  _Fast_, graphical, tiny, but doesn't work with some sites. 

FWIW, I think you will grow to like Xubuntu.  You might want to "sudo apt-get install rox-filer", as suggested above.  (You can always apt-get remove... later).  I'm very impressed with Rox.  Makes Thunar look stone age.  ;)

---

### Post by bodhi.zazen on 2006-08-31
Check out this site:
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by orb9220 on 2006-08-31
There is also a new distro called nUbuntu which might fit the bill don't  know the link tho. and also ubuntu lite 

[http://www.ubuntulite.org/drupal/?q=node/1](http://www.ubuntulite.org/drupal/?q=node/1)

---

### Post by bodhi.zazen on 2006-08-31
kerry_s. I like some of the ideas from your menu and will likely edit my own.

No icons?

FYI here is my menu:

```
[begin] (Arch) </usr/share/pixmaps/explorer.xpm>
		[exec] (Run) {fbrun}
	[separator]
		[exec] (Terminal) {terminal --geometry=80x30} </usr/share/pixmaps/terminal.xpm>
		[exec] (Xfe File Manager) {/usr/bin/xfe} </usr/share/pixmaps/xfe.xpm>
		[exec] (ROX Filer) {/usr/bin/rox} </usr/share/pixmaps/rox.png>
		[exec] (Dragon) {wine /home/bodhi/.wine/c/Program\ Files/ScanSoft/NaturallySpeaking/Program/natspeak.exe} </mnt/Zen/Icons/Wine/exe/wine6.png>
		[exec] (Leafpad) {/usr/bin/leafpad} </usr/share/pixmaps/leafpad.xpm>
		[exec] (Dillo) {/usr/bin/dillo} <>
		[exec] (Firefox) {firefox} </usr/share/pixmaps/mozilla-firefox.png>
		[exec] (Galeon) {galeon} </usr/share/pixmaps/galeon.xpm>
	[separator]
		[workspaces] (Workspaces)
	[separator]
#	[submenu] (Development)
#		[exec] (Mozilla) {mozilla}
#		[exec] (Python [v2.4]) {xterm -e python2.4}
#		[exec] (reportbug) {xterm -e reportbug --exit-prompt}
#	[end]
	[submenu] (Editors)
#		[exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} </usr/share/nano/nano-menu.xpm>
#		[exec] (Pico) {xterm -e pico}
#		[exec] (Vi) {teminal -e vi}
		[exec] (Vim) {terminal -e vim}
	[end]
	[submenu] (Graphics)
		[exec] (Eye of GNOME) {eog} </usr/share/pixmaps/gnome-eog.xpm>
		[exec] (GQview) {/usr/bin/gqview} </usr/share/pixmaps/gqview.xpm>
		[exec] (GIMP) {gimp} </usr/share/pixmaps/gimp.png>
		[exec] (xCHM) {xchm} </usr/share/pixmaps/xchm-16.xpm>
         	[exec] (Xfi Image Viewer) {/usr/bin/xfi} </usr/share/pixmaps/xfi.xpm>
	[end]
#	[submenu] (Help) {}
#		[exec] (Info) {terminal -T "Info" -e info} <>
#	[end]
	[submenu] (Multimedia)
		[exec] (ALSA mixer) {xterm -e alsamixer -c 1}
		[exec] (K3b) {k3b} </usr/share/pixmaps/k3b.xpm>
		[exec] (Kaffeine) {kaffeine} </usr/share/pixmaps/kaffeine.png>
		[exec] (streamtuner) {/usr/bin/streamtuner} </usr/share/pixmaps/streamtuner.png>
#		[exec] (streamripper) {/usr/bin/streamripper} <>
		[exec] (volume control) {gnome-volume-control}
#		[exec] (wmXMMS) {/usr/bin/wmxmms} </usr/share/pixmaps/wmxmms_32.xpm>
		[exec] (XMMS) {/usr/bin/xmms} </usr/share/pixmaps/xmms.xpm>
	[end]
	[submenu] (Network)
		[submenu] (Torrent)
			[exec] (Azureus) {azureus} </usr/share/pixmaps/Azureus.png>
			[exec] (utorrent) {wine /home/bodhi/.wine/c/Program\ Files/utorrent} </usr/share/pixmaps/utorrent.xpm>
		[end]
#		[exec] (D4X) {d4x} <>
		[exec] (Dillo) {/usr/bin/dillo} <>
		[exec] (Downloader for X) {/usr/bin/nt} </usr/share/pixmaps/nt.xpm>
#		[exec] (Firefox) {firefox} </usr/share/pixmaps/firefox.xpm>
#		[exec] (FTP) {terminal -e ftp}
		[exec] (Gaim Instant Messenger) {/usr/bin/gaim} </usr/share/pixmaps/gaim-menu.xpm>
		[exec] (Galeon) {/usr/bin/galeon} </usr/share/pixmaps/galeon.xpm>
#		[exec] (Telnet) {xterm -e telnet}
#		[exec] (W3m) {xterm -e w3m}
#		[exec] (w3m) {xterm -e w3m /usr/share/doc/w3m/MANUAL.html}
	[end]
	[submenu] (Office)
	        [exec] (AbiWord) {/usr/bin/abiword} </usr/share/pixmaps/abiword.xpm>
		[exec] (Evince) {evince} </opt/gnome/share/icons/hicolor/48x48/apps/evince.png>
        	[exec] (LeafPad) {/usr/bin/leafpad} </usr/share/pixmaps/leafpad.xpm>
#		[exec] (MousePad) {/usr/bin/mousepad} </usr/share/pixmaps/mousepad.xpm>
		[exec] (Xfv File Viewer) {/usr/bin/xfv} </usr/share/pixmaps/xfv.xpm>
	[end]
	[submenu] (Other)
		[exec] (ObConf) {obconf}
	[end]
#	[submenu] (Programming) {}
#		[exec] (Python (v2.4\)) { x-terminal-emulator -T "Python (v2.4)" -e /usr/bin/python2.4} </usr/share/pixmaps/python2.4.xpm>
#	[end]
	[submenu] (Shells)
#		[exec] (Aterm) {aterm}
#		[exec] (Bash) {xterm -e bash --login}
		[exec] (Eterm) {Eterm} </usr/share/pixmaps/gksu-debian.xpm>
#		[exec] (mrxvt) {mrxvt-full}
#		[exec] (Rxvt) {rxvt}
#		[exec] (Rxvt) {rxvt-xterm}
#		[exec] (Sh) {xterm -e sh --login}
		[exec] (Terminal) {Terminal} </usr/share/pixmaps/terminal.xpm>
#		[exec] (Xterm) {xterm}
#		[exec] (XTerm [Unicode]) {uxterm}
#		[exec] (X-Terminal as root [GKsu]) {gksu -u root /usr/bin/x-terminal-emulator} </usr/share/pixmaps/gksu-debian.xpm>
	[end]
	[submenu] (System)
         [submenu] (Admin) {}
#		[exec] (aptitude) { x-terminal-emulator -T "aptitude" -e /usr/bin/aptitude} <>
#		[exec] (Synaptic Package Manager) {gksu /usr/sbin/synaptic} </usr/share/synaptic/pixmaps/synaptic_32x32.xpm>
#			[exec] (Synaptic Package Manager) {gksu /usr/sbin/synaptic}
#		[exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e /usr/sbin/su-to-root -p root -c /usr/sbin/alsaconf} <>
#		[exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e /usr/sbin/su-to-root -p root -c /usr/sbin/pppconfig} <>
		[exec] (NVIDIA X Server Settings) {nvidia-settings}
         [end]
#	[submenu] (Settings)
#			[submenu] (GNOME)
#				[exec] (Login Window) {gksu gdmsetup}
#			[end]
#			[submenu] (KDE)
#				[submenu] (Components)
#					[exec] (KDE Resources) {kcmshell kresources}
#				[end]
#				[submenu] (Look & Feel)
#					[exec] (GTK styles and fonts) {kcmshell kcmgtk}
#				[end]
#			[end]
#		[end]
#		[exec] (DSL/PPPoE configuration tool) {xterm -e pppoeconf}
#		[exec] (GDM flexiserver) {gdmflexiserver} </usr/share/pixmaps/gdm.xpm>
#		[exec] (GDM flexiserver in Xnest) {gdmflexiserver -n} </usr/share/pixmaps/gdm.xpm>
#		[exec] (GDM Photo Setup) {gdmphotosetup} </usr/share/pixmaps/gdm.xpm>
#		[exec] (GDM Setup) {gksu gdmsetup} </usr/share/pixmaps/gdm.xpm>
#		[exec] (NVIDIA X Server Settings) {nvidia-settings}
#		[exec] (Pstree) {xterm -e pstree.x11} </usr/share/pixmaps/pstree16.xpm>
#		[exec] (Run as different user [GKsu]) {gksuexec} </usr/share/pixmaps/gksuexec-debian.xpm>
#		[exec] (Xfq RPM Manager) {xfilequery} </usr/share/pixmaps/xfq.xpm>
	[end]
	[submenu] (Utilities)
#		[exec] (docker) {docker}
#		[exec] (fbpager) {fbpager}
#		[exec] (fbpanel) {fbpanel}
         	[exec] (File-Roller) {file-roller} </usr/share/pixmaps/file-roller.xpm>
		[exec] (Xarchiver) {xarchiver} </usr/share/pixmaps/xarchiver.png>
#		[exec] (GTK+ 1.2 Theme Switch) {switch}
#		[exec] (GTK+ 2.0 Theme Switch) {switch2}
#		[exec] (Info) {xterm -e info}
#		[exec] (KDE Kicker) {/usr/bin/kicker} <>
#		[exec] (PerlPanel) {perlpanel} </usr/share/pixmaps/perlpanel.xpm>
#		[exec] (pypanel) {pypanel}
#		[exec] (Rclock) {rclock}
#		[exec] (Top) {terminal -e top}
	[end]
	[submenu] (WindowManagers) {}
		[restart] (FluxBox)  {/usr/bin/startfluxbox}
		[restart] (IceWM)  {/usr/bin/icewm}
		[restart] (Openbox)  {/usr/bin/openbox}
	[end]
	[separator]
	[submenu] (FluxBox)
		[workspaces] (Workspaces)
		[submenu] (Styles)
			[stylesdir] (/usr/share/fluxbox/styles)
		[end]
		[submenu] (Usr Styles)
			[stylesdir] (/home/bodhi/Zen/Fluxbox/Themes/.fluxbox/styles)
		[end]
		[submenu] (Favorite Styles) (~/.fluxbox/favorite)
			[stylesdir] (~/.fluxbox/favorite)
		[end]
		[exec] (gtk2 themes) {/usr/bin/gtk-chtheme}
		[config] (Configure)
		[reconfig] (Reconfig)
		[restart] (Restart)
		[separator]
		[exit] (Exit)
	[end]
[end]
```

---

### Post by kerry_s on 2006-09-01
Na, I don't like to use icons if i dont have to, that's just extra eye candy but serves no purpose. I like keeping my system small even though i have a ton of room. I built mine kinda like DSL-N but with none of the draw backs. I also don't like crowding my menus, so somethings that i don't use by themselves are not there. like for example xpdf is in my rox-filer run action so when i click on a .pdf it will open xpdf, i do the same with xarchiver and xzgv,  i also set custom menu actions for opening rox as root or editing with leafpad as root. I also use rox as my downloader, you just drag the link of the thing you want to download to rox and it will use wget to down load, that way you don't need a extra app like d4x. I use to have a large menu like yours, but i changed as i got older and my sight worse, that's why don't keep nothing i don't use installed and my apps can be reached quick in the menus. I tried your menu it is really long, i just renamed mine to menu.old and made a new menu and pasted yours in there. What i did is open the menu and a blank leafpad copied and pasted the things i wanted from the old menu or make a shorter entry for the same thing in the new menu, it just takes a little time be patient with it.

---

### Post by bodhi.zazen on 2006-09-01
I understand.

1. I wanted to demonstrate that Fluxbox can display menu icons, shows the potential of Fluxbox to GNOME/KDE/XFCE users considering a change. This is not very resource intensive.

2. I am blessed with good eyes (1600x1200 resolution, dual monitor) and I can recognize the color of the icons rapidly.

3. Note: Change in mane of the "menu" from Fluxbox to Arch.

4. Common programs listed first, run command on top of course (fluxbox equivalent of mini-command line).

5. Workspace in middle -> rapid change to programs/desktops

6. Long list so I do not have to search for all these programs (in case I forget the names). Can shorten the list by commenting out (#) any time I like. All the benefits of a long and short list. (I use this across multiple OS and comment out what is not installed).

7. I prefer wget, but I have problems with large files. d4x interfaces with Firefox (flash got) and handles large downloads (iso) better.

8. This is what I love about Linux, we can each configure our desktop to our unique preferences (unlike windows).

---

### Post by secdroid on 2006-09-01
> **bodhi.zazen said:**
> Check out this site:
[http://fluxbuntu.org/](http://fluxbuntu.org/)
> **Fluxbuntu nBuild1 Alpha is coming; New Support Forums, Wiki Coming Soon**
The livecd for Fluxbuntu nBuild1 Alpha was built from the Ubuntu 6.06 Desktop CD. This release is a livecd with the option to install. The Alpha Cd is 542MB in total size (158MB less than the Ubuntu Desktop CD smile ). I have tested and successfully installed Fluxbuntu nBuild1 Alpha on an IBM Thinkpad....  [http://fluxbuntu.org/]("http://fluxbuntu.org/") 
Nice idea, but I see problems with this approach.  The Live CD installer is not at the same level of maturity as the Alternate CD installer.  Less robust with atypical machines.

More importantly, the Alternate CD installer works well with low memory machines, while the Live CD installer will fail.  This rules out a natural constituency for this sort of distro.

On the other hand, the Xubuntu project passed through this stage and now has a very professional project with Live & Alternate CDs.  Fluxbox is widely liked, so we can hope that Fluxbuntu matures to the same level as Xubuntu.  

The Ubuntu Lite project seems to be barely sputtering along.  I note that there is also [http://groups.google.com.au/group/ubuntu_lite]("http://groups.google.com.au/group/ubuntu_lite")

---

### Post by secdroid on 2006-09-01
> **orb9220 said:**
> There is also a new distro called nUbuntu which might fit the bill don't  know the link tho. and also ubuntu lite 

[http://www.ubuntulite.org/drupal/?q=node/1](http://www.ubuntulite.org/drupal/?q=node/1)
I think that you will find that the nUbuntu distro is at [http://www.nubuntu.org/]("http://www.nubuntu.org/")  

nUbuntu is really a special-purpose distro > The main goal of nUbuntu is to create a distribution which is derived from the Ubuntu distribution, and add packages related to security testing, and remove unneeded packages, such as Gnome, Openoffice.org, and Evolution.  [http://www.nubuntu.org/about.php]("http://www.nubuntu.org/about.php")
Like a lot of systems & network administrator-oriented distros, it is Fluxbox based.  [http://shots.osdir.com/slideshows/slideshow.php?release=691&slide=3&title=nubuntu+6.06+screenshots]("http://shots.osdir.com/slideshows/slideshow.php?release=691&slide=3&title=nubuntu+6.06+screenshots")

---

### Post by bodhi.zazen on 2006-09-01
A discussion about Fluxbox? I am tickled pink.

Secdroid I agree with  both of you points.

What is exciting about Fluxbuntu?

It is coming and they seem open to user input.

Personally, I am an Arch Linux convert but I love the Ubuntu forums.

The problem with Ubutnu is:
1. It is slow as the default install loads a lot that I do not need (Gnome for example).
2. It has been somewhat unstable, the recent debacle with X as an example.

Soultion: When I dabble in Ubuntu I do a server install, install only what packages I need, and run Fluxbox.

I do not see Fluxbuntu replacing my custom install any time soon, but as experineced Fluxbox users we can help shape the distro and bring some sanity to Ubuntu -> Smaller, faster, and well ... Fluxbox, or is that  Fluxbuntu.

---

### Post by justin whitaker on 2006-09-01
I've been looking at what you open/flux/blackbox users have been doing, and it seems right up my alley. 

On XP, I use BBlean, so I'd feel right at home with a custom install, or Fluxbuntu.

There seems to be as much capability to customize Ubuntu as any other distro, so I don't really see the point of moving away from it: as long as I can do a server install and pick and choose from the repositories, I don't feel the need to do move away. 

As for why Fluxbuntu....seems like alot of people are trying to install Ubuntu on a spare or aged machine, usually one that is less powerful than their main rig....a properly done, professional looking fluxbox edition would be perfect for those users. 

And for speed freaks like me. :smile:

---

### Post by secdroid on 2006-09-01
> **bodhi.zazen said:**
> 
...
What is exciting about Fluxbuntu?

It is coming and they seem open to user input.
Yes.  Also, the forum administrator said something that would seem to indicate that they won't need to re-invent the wheel.
> The Developer of nUbuntu, TomB is my friend... His distribution is a security-tool live cd based os, whereas Fluxbuntu maintains a current position of a desktop/server based distribution. We both use fluxbox but our objectives for the Operating Systems are somewhat different.[http://fluxbuntu.org/forum/index.php/topic,15.msg24.html#msg24]("http://fluxbuntu.org/forum/index.php/topic,15.msg24.html#msg24")
They already have a "Feature Requests" thread at [http://fluxbuntu.org/forum/index.php/board,16.0.html]("http://fluxbuntu.org/forum/index.php/board,16.0.html")
> **bodhi.zazen said:**
> 
The problem with Ubutnu is:
...
2. It has been somewhat unstable, the recent debacle with X as an example.

Yes, that nailed me.  A lot of us thought the Live CD installer was somewhat rushed.  The Ubuntu leads do seem to "get it," but all projects have glitches.  (Even mine...)  ;) 

> **bodhi.zazen said:**
> 
I do not see Fluxbuntu replacing my custom install any time soon, but as experineced Fluxbox users we can help shape the distro and bring some sanity to Ubuntu -> Smaller, faster, and well ... Fluxbox, or is that  Fluxbuntu.
Yes, and I think I will go join the Fluxbuntu community.

---

### Post by kapetanski on 2006-09-05
I've used slax, about 100 MB with fluxbox and xfce, and really fast as you can load the whole operating system into ram. 

[http://www.slax.org]("http://www.slax.org")

---

### Post by bodhi.zazen on 2006-09-05
> **kapetanski said:**
> I've used slax, about 100 MB with fluxbox and xfce, and really fast as you can load the whole operating system into ram. 

[http://www.slax.org]("http://www.slax.org")

slax is nice, I have run it in Windows (at work) with QEMU.

Problems:
1. Does not boot my hardware.
2. Small repository.

---

### Post by secdroid on 2006-09-05
Fluxbuntu site is down.  
> The requested URL /forum/index.php was not found on this server.

Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request
I did manage to download fluxbuntu-nbuild1-alpha-i386.iso, but the md5sum did not compare to that contained in md5.htm.  (Firefox's download tool did say I had a complete download.)  Tried burning & booting the iso anyway and syslinux boot failed.

******

I tried out Arch.  Very impressive, but I'll have to do some work on getting the correct parms for my xorg.conf.  The hardware detection in Arch just didn't cut it.

Odd that Knoppix does this so well, Puppy does it well (using their own code), while Ubuntu does it less well (confused by my KVM switch), and Arch does it poorly.  

Still, many things to admire in Arch.  Great way to improve one's Linux skills, if not quite up to "Linux From Scratch" build process.

---

### Post by bodhi.zazen on 2006-09-05
> **secdroid said:**
> I tried out Arch.  Very impressive, but I'll have to do some work on getting the correct parms for my xorg.conf.  The hardware detection in Arch just didn't cut it.

Although this the Ubuntu site.... Welcome to Arch.

You should be able to copy MOST (not all) of your xorg.conf from Ubuntu to Arch. Copy everything but the "Files section".

Arch is Oh sooo sweet.

A few commands:

pacman -Sy = apt-get update.
pacman -Syu = apt-get dist-upgrade.
pacman -S <application> = apt-get install <application>

etc/pacman.conf = /etc/apt/sources.list (enable community)

pkgbuild (AUR) [Arch AUR](http://aur.archlinux.org/packages.php)
Download and un pack AUR.
makepkg = ./configure; make
pacman -A <application> = checkinstall

---

### Post by Omnios on 2006-09-05
Hi I have tryed both Fluxbox and XFCE. The new Xubuntu desktop is nice because you have a preset desktop. Only problem I had was that was when I just first started using Linux and had a hard time finding reading material on how to set them up. 

 Also I have been doing a lot of reading on Evelution E-16 and E-17 and apperently it can run with very little ram thought I can not seem to get this confirned yet. It might be interesting to try this out with a low ram 128meg ram computer to check it out. I think the thing I like about it is you get alot of functionality for very little ram

[http://ubuntuforums.org/showthread.php?t=248880&highlight=E-17](http://ubuntuforums.org/showthread.php?t=248880&highlight=E-17)
[http://ubuntuforums.org/showthread.php?t=248683&highlight=E-17](http://ubuntuforums.org/showthread.php?t=248683&highlight=E-17)

 There is also a [B]Enlightenment how to
[/B][http://ubuntuforums.org/showthread.php?t=97199&highlight=E-17](http://ubuntuforums.org/showthread.php?t=97199&highlight=E-17)

---

### Post by bodhi.zazen on 2006-09-05
> **Omnios said:**
> Also I have been doing a lot of reading on Evelution E-16 and E-17 and apperently it can run with very little ram thought I can not seem to get this confirned yet. It might be interesting to try this out with a low ram 128meg ram computer to check it out. I think the thing I like about it is you get alot of functionality for very little ram

Have you tried ELive? Here is the Ubuntu take:
[Elive](http://ubuntuforums.org/showthread.php?t=231274&highlight=Elive)

And the most recent Elive:
[Download ELive](http://elivecd.org/gb/Download/Development/)

Elive is Debian and suffers most from hardware detection although I have not tried the most recent Beta.

---

### Post by comppsyco on 2006-09-05
If you really want to go lightweight, try Linux From Scratch. I haven't done it, but it looks intriguing.

---

### Post by bodhi.zazen on 2006-09-05
LFS scratch takes time. time. time. and knowledge or willingness to learn.

[color=brown]Start with an Ubuntu server install.[/color]

---

### Post by kerry_s on 2006-09-05
I vote for the server install too. Just grab the alternate cd, do the server install then login and->

1. sudo su  <-makes you root
2. nano /etc/apt/sources.list
3. comment(#) out the cdrom and uncomment  the rest of the repo's
4. ctrl and x and y and enter   <-to save your changes to sources.list
5. apt-get update
6. apt-get install x-window-system-core xterm gdm fluxbox leafpad rox-filer synaptic   <basic system with filemanager(rox), editor(leafpad), terminal(xterm) and synaptic to grab what ever else you need.
7. now reboot
8. at gdm login select fluxbox as session(important) and log in

That's it done it would have taken longer to read the linux from scratch instructions. ;)

---

### Post by kerry_s on 2006-09-05
whoo, I just tried that fluxbuntu and i fricken hated it, man that thing blows.

1. They need to put the user and passwd at the xdm login, i had to shut it down to go look for the user(fluxbuntu) and the password(livecd) you talk about your nonstandard livecd login. Who could guess that? Sucks.

2. Also at the login, there's no shutdown or reboot, so you got to use your reset button. Sucks. I really think they should have used "GDM" instead.

3. So i login and i need to edit my /etc/X11/xorg.conf to change the nv to vesa so both my monitors have a pic instead of one being scrambled. Hey! There's only nano,ted,abiword, the default is nano, i know how to use nano, but for a newby, whoo. They should have at least had leafpad, which is very simple to use and still small.

4. The selection of apps, is this suppose to be a mini distro? I opened up synaptic to see the list of installed, ho, there's alot of stuff, no wonder the iso is so big, they might as well have included some real app's and made it full size(700mb).

5. The actions for rox need to be set up to do things, like click on a compressed package should open xarchiver, a iso xfburn,

6. I know it's still alpha, but this one sucks!

Here's what i would recommend-> gdm(the size is worth it), firefox(for those older machines that can use it), dillo(it's there), rox(it's there), xfburn(for cd burning, it's the smallest gui one), xmms(it's there), mplayer(the best), ...

Sorry, lost my chain of thought. It just still needs work, i hope it gets better on the next one. I really hope they put some real thought in to the apps, even a basic gnome install has less apps but at least there the good ones.

Just my thoughts and my take on it.

---

### Post by bodhi.zazen on 2006-09-05
LOL kerry_s =D>

I must admit I find these two posts back-to-back amusing. #-o

I hope you don't mind, but I posted them in Fluxbuntu...

[list]
[*]Did you not see the user name and password on Fluxbuntu? :shock:
[*]I always thought nano was newbie friendly. :-k
[*]Learn vim
[*]Ctrl-Alt-F1 to tty1 - shutdown -h now; shutdown -r now :KS
[*]You have a pont re: rox, but  rox is easy to configure.
[*]The point is a light, fast distro.
[*]try apt-get install firefox.
[/list]

---

### Post by joejaxx on 2006-09-06
> **kerry_s said:**
> whoo, I just tried that fluxbuntu and i fricken hated it, man that thing blows.

1. They need to put the user and passwd at the xdm login, i had to shut it down to go look for the user(fluxbuntu) and the password(livecd) you talk about your nonstandard livecd login. Who could guess that? Sucks.

2. Also at the login, there's no shutdown or reboot, so you got to use your reset button. Sucks. I really think they should have used "GDM" instead.

3. So i login and i need to edit my /etc/X11/xorg.conf to change the nv to vesa so both my monitors have a pic instead of one being scrambled. Hey! There's only nano,ted,abiword, the default is nano, i know how to use nano, but for a newby, whoo. They should have at least had leafpad, which is very simple to use and still small.

4. The selection of apps, is this suppose to be a mini distro? I opened up synaptic to see the list of installed, ho, there's alot of stuff, no wonder the iso is so big, they might as well have included some real app's and made it full size(700mb).

5. The actions for rox need to be set up to do things, like click on a compressed package should open xarchiver, a iso xfburn,

6. I know it's still alpha, but this one sucks!

Here's what i would recommend-> gdm(the size is worth it), firefox(for those older machines that can use it), dillo(it's there), rox(it's there), xfburn(for cd burning, it's the smallest gui one), xmms(it's there), mplayer(the best), ...

Sorry, lost my chain of thought. It just still needs work, i hope it gets better on the next one. I really hope they put some real thought in to the apps, even a basic gnome install has less apps but at least there the good ones.

Just my thoughts and my take on it.


1. thank you for commenting on my distro
2. there is a reason i called it alpha and there is a reason i called it a developmental release (nbuilds are a works in progress there is a reason i did not call this Launch 1)
3. I clearly laid on the the main site what to do for the login credentials and to install the os
4. your vivid statements and criticisms have been noted
5. if you whould like to input constructive criticism you can join the forums here : [http://community.fluxbuntu.org/](http://community.fluxbuntu.org/) and constructively criticize the distro all you want. You can also add what you think should be in Fluxbuntu in the feature request forums.
6. If you are a real fellow developer i whould be happy to have you join the team. Anyone can contribute to Fluxbuntu.
7. Thank You for your time and input. :)

---

### Post by kerry_s on 2006-09-06
My bag, i was just having a bad day and it made me madder when i got to the login and couldn't guess the login and passwd. The idea is a good one, i would like to see a lite fluxbuntu that i can just go straight to the install instead of installing the server and apt-getting. 

"Did you not see the user name and password on Fluxbuntu? "

No, i did not read the front page at fluxbuntu, i just went straight to the download. Again my bag i just rushed along.

"if you whould like to input constructive criticism you can join the forums here : [http://community.fluxbuntu.org/](http://community.fluxbuntu.org/) and constructively criticize the distro all you want. You can also add what you think should be in Fluxbuntu in the feature request forums."

Maybe later, i don't like joining forums just to complain :-# 

"If you are a real fellow developer i whould be happy to have you join the team. Anyone can contribute to Fluxbuntu."

No, im not, wish i had the brains for it. I'm just regular joe who tried it.
I'm just one of those people who love to try different distro's, i'll usally go through a 100 cdr's a month, so yes i'm addicted.


joejaxx,  i apologize if it sounded a little mean, but i went off my first impressions. I think just the fact you got a distro together is a fantastic accomplishment in itself. I hope you continue to improve and lighten fluxbuntu even more. Yes, i do know it is alpha, but even a alpha shouldn't have the feeling like a bunch of app's were just slapped together with no thought about the apps working together, every distro i've tried at least took some time to configure the environment so it works with the installed apps.
Since rox is the filemanger it is like the backbone of the system it should be configured, so the newby doesn't have to see no run action set.

---

### Post by joejaxx on 2006-09-06
> **kerry_s said:**
> My bag, i was just having a bad day and it made me madder when i got to the login and couldn't guess the login and passwd. The idea is a good one, i would like to see a lite fluxbuntu that i can just go straight to the install instead of installing the server and apt-getting. 

"Did you not see the user name and password on Fluxbuntu? "

No, i did not read the front page at fluxbuntu, i just went straight to the download. Again my bag i just rushed along.

"if you whould like to input constructive criticism you can join the forums here : [http://community.fluxbuntu.org/](http://community.fluxbuntu.org/) and constructively criticize the distro all you want. You can also add what you think should be in Fluxbuntu in the feature request forums."

Maybe later, i don't like joining forums just to complain :-# 

"If you are a real fellow developer i whould be happy to have you join the team. Anyone can contribute to Fluxbuntu."

No, im not, wish i had the brains for it. I'm just regular joe who tried it.
I'm just one of those people who love to try different distro's, i'll usally go through a 100 cdr's a month, so yes i'm addicted.


joejaxx,  i apologize if it sounded a little mean, but i went off my first impressions. I think just the fact you got a distro together is a fantastic accomplishment in itself. I hope you continue to improve and lighten fluxbuntu even more. Yes, i do know it is alpha, but even a alpha shouldn't have the feeling like a bunch of app's were just slapped together with no thought about the apps working together, every distro i've tried at least took some time to configure the environment so it works with the installed apps.
Since rox is the filemanger it is like the backbone of the system it should be configured, so the newby doesn't have to see no run action set.

Well If you do join Please Stop By the Feature Request Forums and post what you think ;)

---

### Post by secdroid on 2006-09-06
Woo hoo!  Fluxbuntu download succeeded this time.  Guess I got nailed by the first mirror failing.  Torrent was speedy & MD5 correct.

LiveCD runs with no problems on my test box.  While one might quibble about the choice of apps (or lack of apps), Fluxbuntu is an easier way for Fluxbox newbies to get started than instaling Fluxbox themselves.  Also, the Fluxbuntu community is a great resource for the newbies.

All in all, a promising start.

Note an interesting change:
> **Minimum Requirements:**
CPU: Pentium 2 233MHz (It might work on lower i have only tested it on this cpu)
**RAM: [was]128 MB [now] 96MB!! (This Has Been Verified!!)**
HardDrive Space: 2GB (1.2GB Installed)  [http://fluxbuntu.org/]("http://fluxbuntu.org/")
This brings lightweight Ubuntu into the same efficiency "ballpark" as DSL-N (Damn Small Linux's larger sibling).  Very impressive!  (And Fluxbuntu is more beginner-friendly, IMHO.)

---

### Post by lapsey on 2006-09-06
To get a truly lightweight, human themed environment, I installed ubuntu server and then the appropriate bits afterwards.

This all turns out to be only around 700MB on the disk.
```

sudo aptitude install x-window-system-core icewm menu xterm gtk2-engines-ubuntulooks tangerine-icon-theme gksu

```
To get icewm and gtk apps looking great, I 
[LIST][*]installed [this icewm setup](http://xubuntu.wordpress.com/2006/07/20/my-icewm-setup/)
[*] to get icons and theme properly I created a .gtkrc.mine file with ```
gtk-icon-theme-name = "Tangerine"
gtk-theme-name = "Human"
```
[*].gtkrc-2.0 should look like ```
include "/usr/share/themes/Human/gtk-2.0/gtkrc"

style "user-font"
{
font_name="Bitstream Vera Sans 8"
}
widget_class "*" style "user-font"

include "/home/public/.gtkrc-2.0.mine"

```
[*]switched off antialising for the default font as mentioned [here](http://ubuntuforums.org/showthread.php?p=1417453#post1417453)
[*]added " startx " to the end of .bash_profile
[/LIST]

this way, you login to normal shell and go into icewm env immediately.

gtk2 software is all themed with human, correctly and icewm is really easy  to edit. see ~/.icewm/

from here you can install what you like :)

I should also say that when installing, aptitude is far better than apt-get when you are worried about HD space. this is because aptitude removes un-necessary dependencies, while apt-get does not.

---

### Post by bodhi.zazen on 2006-09-06
lapsey: Nice "how-to" with icewm. Icewm is under rated.

I agree with your comments re: aptitude. I have been typing apt-get in the forums, but will change.

Here is a nice icewm how-to:
[[color=brown]Lou's IceWM how-to (Debian)[/color]](http://forums.debian.net/viewtopic.php?t=5450&highlight=icewm&sid=f3bf3ff392c8fb3cf161e5a0a5edd485)

---

### Post by Peter76 on 2006-09-06
Here is a really nice great howto ( IMHO :-) I've written a while back on setting up icewm with rox:

[http://www.ubuntuforums.org/showthread.php?t=171203&highlight=icewm+howto](http://www.ubuntuforums.org/showthread.php?t=171203&highlight=icewm+howto)

---

