---
title: "My Arch install queries, experiences &amp; other ramblings..."
date: 2011-07-07
forum: Any Other OS
---

### Post by mips on 2011-07-07
I have FileRoller & Disk Utility installed in my OB system. Problem is the fonts & icon themes are all wrong and I cant seem to change them to the same as the rest of the system.

These apps seem to be from Gnome 3.

---

### Post by handy on 2011-07-07
Have you tried using LXappearance? I find it to work well in combination with OB Config' Manager.

Hopefully it helps.

I'll install those two & see how they look on my system & get back to you.

---

### Post by handy on 2011-07-07
Where'd you get those two from, when I just tried to install them they don't exist in the Arch or AUR repo?

---

### Post by mips on 2011-07-08
> **handy said:**
> Where'd you get those two from, when I just tried to install them they don't exist in the Arch or AUR repo?

Weird. I installed them with pacman if I remember correctly. I installed some stuff (fileroller) being one that had some gnome dependencies like Nautilus etc which it just installed.
Edit: [http://www.archlinux.org/packages/extra/i686/file-roller/](http://www.archlinux.org/packages/extra/i686/file-roller/)

I did read somewhere that Gnome3 was pulled into the normal repos recently so maybe run a update on the repos.

---

### Post by mips on 2011-07-08
> **handy said:**
> Have you tried using LXappearance? I find it to work well in combination with OB Config' Manager.

Hopefully it helps.

I'll install those two & see how they look on my system & get back to you.

Yes, I installed LXappearance hoping it would solve my problems (which it did before) but no go. Fileroller, disk utility & nautilus (did not want this one but fileroller needs it) still look like the default gnome config)

I'm wondering if it has anything to do with the fact that these packages are part of Gnome3 which is now in the repos.

---

### Post by handy on 2011-07-08
> **mips said:**
> Yes, I installed LXappearance hoping it would solve my problems (which it did before) but no go. Fileroller, disk utility & nautilus (did not want this one but fileroller needs it) still look like the default gnome config)

I'm wondering if it has anything to do with the fact that these packages are part of Gnome3 which is now in the repos.

I reckon your right, I just called file-roller & got the "3"s on all:

```
Targets (3): gnome-desktop-3.0.2-1  nautilus-3.0.2-1  file-roller-3.0.2-1
```

I didn't go through & install, the last thing I want is the Gnome desktop. :)

You could use Worker to handle your de/compression, it has everything that file-roller has built in I think, & if anything is missing you can easily add it.

---

### Post by mips on 2011-07-09
> **handy said:**
> I reckon your right, I just called file-roller & got the "3"s on all:

```
Targets (3): gnome-desktop-3.0.2-1  nautilus-3.0.2-1  file-roller-3.0.2-1
```

I didn't go through & install, the last thing I want is the Gnome desktop. :)

You could use Worker to handle your de/compression, it has everything that file-roller has built in I think, & if anything is missing you can easily add it.

I thought about uninstalling the gnome apps but then realised that somewhere in the future I will probably install a gnome app out of need so maybe I should look at fixing this instead. No rush though, can live with it in the interim.

---

### Post by handy on 2011-07-09
I run a things that use both the GTK & QT stack on Openbox, they all look pretty good these days.

I've forgotten the name of the tool that allows QT to integrate well with GTK? Whatever its called it works! lol

e.g. I use VLC all the time & you would never know it is built on QT.

---

### Post by wojox on 2011-07-09
Does it look like this? I don't use file-roller (terminal) but I've always had this problem with some non-root related apps.

---

### Post by mips on 2011-07-09
> **wojox said:**
> Does it look like this?

Exactly like that!

Just installed VLC and I have the same problem with it but this is a QT app though.


Edit: lol, just ran htop and I'm only using 47MB of RAM, 70MB with chromium open :biggrin:

.

---

### Post by wojox on 2011-07-09
> **mips said:**
> Exactly like that!

Just installed VLC and I have the same problem with it but this is a QT app though.


Edit: lol, just ran htop and I'm only using 47MB of RAM, 70MB with chromium open :biggrin:

.

I'm gonna have a look at Archbang again. I don't think they have this problem. That's where I found the theme I'm using there. They make a good spin but it still pulls in a lot of unneeded packages. I got some good ideas from them about what lightweight apps to install in my Arch setup.

Check [AUR]("https://aur.archlinux.org/packages.php?O=0&K=vlc&do_Search=Go") for VLC they have vlc-nox and vlc-nogui which does not use QT.

---

### Post by handy on 2011-07-09
As I previously mentioned there is something you can do that makes QT app's look fine on GTK themed systems, (like Openbox). The QT app uses the GTK theme, font sizing & all that.

I did it along time ago & can't remember how, unfortunately. That is one of the problems of using Arch, as the years go by, if you don't make a note of what you did you can easily (well I can) forget how & what you've done!

---

### Post by wojox on 2011-07-09
> **handy said:**
> As I previously mentioned there is something you can do that makes QT app's look fine on GTK themed systems, (like Openbox). 

I think it's qtconfig your talking about?

---

### Post by mips on 2011-07-10
> **wojox said:**
> I'm gonna have a look at Archbang again. I don't think they have this problem. That's where I found the theme I'm using there. **They make a good spin but it still pulls in a lot of unneeded packages.**

Was gonna go with Archbang and then decided against it for this very reason.

Let me know what you find.

---

### Post by handy on 2011-07-10
> **wojox said:**
> I think it's qtconfig your talking about?

Yep, that's it, I'll add it to my Openbox menu now. 

Thanks for refreshing my memory. :)

---

### Post by mips on 2011-07-10
qtconfig gives me a "QGtkStyle was unable to detect the current GTK+ theme." error.

---

### Post by handy on 2011-07-10
What theme are you running?

I'm using Aero that I modified to suit my dark tastes...

---

### Post by mips on 2011-07-10
> **handy said:**
> What theme are you running?

I'm using Aero that I modified to suit my dark tastes...

Orta
[http://gnome-look.org/content/show.php/Orta?content=134123](http://gnome-look.org/content/show.php/Orta?content=134123)
[http://box-look.org/content/show.php/Orta+Openbox?content=142451](http://box-look.org/content/show.php/Orta+Openbox?content=142451)

Got the qtconfig error sorted by running with sudo. VLC however is not 100% like it's on my desktop.

EDIT: I've attached a screenshot. See VLC & Nautilus at the bottom.

---

### Post by handy on 2011-07-10
Hmm, that's strange, I wonder why you can't adjust your way out of the VLC problem at least, using QTconfig?

Between QTconfig, LXappearance & OB Config' Manager, my VLC (& everything else except Picassa - Wine) is themed & looks identical to the GTK files.

I just had a poke around in ~/.config & ~/.themes , I can't see anything that brings me the ah! ha! experience.

Have you posted in the Arch forum mips?

---

### Post by mips on 2011-07-11
> **handy said:**
> Hmm, that's strange, I wonder why you can't adjust your way out of the VLC problem at least, using QTconfig?

I just had a poke around in ~/.config & ~/.themes , I can't see anything that brings me the ah! ha! experience.

Ok, qt/vlc problem sorted by adding ***export GTK2_RC_FILES="$HOME/.gtkrc-2.0"*** to *.xinitrc* file.



> **handy said:**
> Have you posted in the Arch forum mips?

Yip, [https://bbs.archlinux.org/viewtopic.php?pid=959664#p959664](https://bbs.archlinux.org/viewtopic.php?pid=959664#p959664)

As suspected the gnome apps problem is Gnome3 related which uses gtk3 which the Orta theme does not support. Hopefully support will be added.

**I take it gnome shell themes <> gtk3 themes?** Sorry, I have not been following this whole gnome3 thing.

I have uninstalled the problematic gnome apps, good news is Thunar can do archives via the archive pluging by the looks of things so I just need to install some form of archive manager.

Bad news is I lost the auto mount features and now have to find a substitute.

---

### Post by handy on 2011-07-11
> **mips said:**
> 
Ok, qt/vlc problem sorted by adding ***export GTK2_RC_FILES="$HOME/.gtkrc-2.0"*** to *.xinitrc* file. 

I don't have that in my .xinitrc ?

> **mips said:**
> 
Yip, [https://bbs.archlinux.org/viewtopic.php?pid=959664#p959664](https://bbs.archlinux.org/viewtopic.php?pid=959664#p959664)

As suspected the gnome apps problem is Gnome3 related which uses gtk3 which the Orta theme does not support. Hopefully support will be added.

**I take it gnome shell themes <> gtk3 themes?** Sorry, I have not been following this whole gnome3 thing. 

This thread is about as close as I've got to Gnome3. ;)

> **mips said:**
> 
I have uninstalled the problematic gnome apps, good news is Thunar can do archives via the archive pluging by the looks of things so I just need to install some form of archive manager. 

There's usually an alternative to everything in this FOSS world.

> **mips said:**
> 
Bad news is I lost the auto mount features and now have to find a substitute.

I barely run a desktop with Openbox, no icons, just the xfce4-panel with 4 applets, I've got worker set up so that I manually mount & umount optical media, but I have external USB drives & chip readers auto-mount.

I think the developments with udev has been improving this situation. I've not run an xorg.conf on this machine for many months, but I've had to run @hal in the rc.conf DAEMONS line because my mouse & keyboard would disappear if I didn't.

I've just removed @hal, & I'll check with a warm boot whether udev has got that problem sorted now.

[I]**[edit:]** Keyboard & mouse work without hal. cool. I wonder what will break when I remove hal from the system? 

**[edit2:]** Do you have udisks installed?

[https://wiki.archlinux.org/index.php/Udev#UDisks](https://wiki.archlinux.org/index.php/Udev#UDisks) 

**[edit:3]** I deleted hal, the only dependency was picasa, which I also deleted as I don't use it. I'll test the USB auto mount routine tomorrow, I expect it will work, as I think that udev - udisks is how I set it up a while back. 

Bed now. :) 

**[edit:4]** I just discovered that Worker won't start without hal installed. It doesn't need the DAEMON called, just hal installed?[/I]

---

### Post by mips on 2011-07-11
> **handy said:**
> I don't have that in my .xinitrc ?

Black magic I suspect.


> **handy said:**
> This thread is about as close as I've got to Gnome3. ;)

That makes two of us then ;)


> **handy said:**
> There's usually an alternative to everything in this FOSS world.

Xarchiver did the job, just gotto figure out what bzip is complaining about.



> **handy said:**
> I barely run a desktop with Openbox, no icons, just the xfce4-panel with 4 applets, I've got worker set up so that I manually mount & umount optical media, but I have external USB drives & chip readers auto-mount.

I think the developments with udev has been improving this situation. I've not run an xorg.conf on this machine for many months, but I've had to run @hal in the rc.conf DAEMONS line because my mouse & keyboard would disappear if I didn't.

I've just removed @hal, & I'll check with a warm boot whether udev has got that problem sorted now.

[I]**[edit:]** Keyboard & mouse work without hal. cool. I wonder what will break when I remove hal from the system? 

**[edit2:]** Do you have udisks installed?

[https://wiki.archlinux.org/index.php/Udev#UDisks](https://wiki.archlinux.org/index.php/Udev#UDisks) 

**[edit:3]** I deleted hal, the only dependency was picasa, which I also deleted as I don't use it. I'll test the USB auto mount routine tomorrow, I expect it will work, as I think that udev - udisks is how I set it up a while back. 

Bed now. :) 

**[edit:4]** I just discovered that Worker won't start without hal installed. It doesn't need the DAEMON called, just hal installed?[/I]

I only installed HAL today as apparently it's required by consolekit.
Edit: I removed HAL from my startup daemons.

I do have udisks installed. Do I need any of the wrappers though to make automounting work?

---

### Post by jeffathehutt on 2011-07-11
> **mips said:**
> I do have udisks installed. Do I need any of the wrappers though to make automounting work?

I use udisks with pcmanfm, and as far as I remember, all you need to do is add yourself to the storage group and automounting will start working. (It's been a while, so I might be wrong) :)

---

### Post by mips on 2011-07-11
> **jeffathehutt said:**
> I use udisks with pcmanfm, and as far as I remember, all you need to do is add yourself to the storage group and automounting will start working. (It's been a while, so I might be wrong) :)

Unfortunately that does not work for me.

I came across this thread and it seem to be driving people up the wall, [https://bbs.archlinux.org/viewtopic.php?id=111867](https://bbs.archlinux.org/viewtopic.php?id=111867) 3 pages for a problem on the Arch forums is a lot :biggrin:

Here is the 'solution':
**pacman -S gvfs gvfs-afc** (This unfortunately pulls in disk-utility again but I could care less right now)
start openbox with **exec dbus-launch ck-launch-session openbox-session**

[https://wiki.archlinux.org/index.php/ConsoleKit#Running_several_applications_from_xinitrc](https://wiki.archlinux.org/index.php/ConsoleKit#Running_several_applications_from_xinitrc)
[COLOR="Red"]Warning: If you run several applications which may spawn others that need CK, please read both following sections[/COLOR]
Read the above section as it requires you to create a .startx file with all the apps (including openbox) you want to run that is called from the .xinitrc file.

I'm glad to say my auto mounting now works a charm and I can even see the network & my trash.

---

### Post by handy on 2011-07-11
I just call "exec openbox-session" in .xinitrc.

(Preceded by this line "**setxkbmap -option terminate:ctrl_alt_bksp &**" which allows me to ctrl_alt_backspace to kill X. I also have "**ca::ctrlaltdel:/sbin/shutdown -t3 -r now" in innitab"**.)

Do you have anything in your fstab/mnt/media relating to your network or for USB disks/chips

Mine looks like this:

```
# /etc/fstab: static file system information
#
# <file system> <dir>           <type>          <options>       <dump>  <pass>
none            /dev/pts        devpts          defaults        0       0
none            /dev/shm        tmpfs           defaults        0       0


/dev/cdrom      /media/cd       iso9660   ro,user,noauto,unhide   0      0
/dev/dvd        /media/dvd      udf       ro,user,noauto,unhide   0      0
/dev/sda3       /               ext3    defaults,noatime        0       1
/dev/sda4       /home           jfs     defaults,noatime        0       2
###/dev/sda5    swap            swap    defaults                0       0
/dev/sda5       /mnt/store      ext3    defaults,noatime        0       2
192.168.1.15:/media /mnt/NAS-media nfs  defaults,hard,intr,noatime      0       0
192.168.1.15:/backup /mnt/NAS-backup nfs defaults,hard,intr,noatime     0       0
/dev/sdb1       /mnt/sdb1       vfat    rw,noauto,flush,user    0       0
```

I use run level 5, in innitab, & the following in ~/.bash_profile:

```
. $HOME/.bashrc
#if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
	exec xinit -- :0 
	logout
fi
```

I log in my user at the prompt & it auto-starts Openbox, which is setup to open Firefox, Sakura & Worker on their own set desktops.

To cold or warm boot I have a couple of scripts which I've connected to buttons in Worker which do the job of umounting my NAS device & shutting me down quickly, without these scripts, I had to manually umount the two partitions, which when I forgot to do it used to take a looooong time to cold or warm boot:

umount.cold.sh
```

#!/bin/bash
if [[ `whoami` != "root" ]];
then
  echo "Must be root to run this script."
  exit
fi
echo "Unmounting NFS volumes."
umount 192.168.1.15:/media
umount 192.168.1.15:/backup
echo "Unmounting complete, shutting down now."
shutdown -h now
```

umount.reboot.sh

```
#!/bin/bash
if [[ `whoami` != "root" ]];
then
  echo "Must be root to run this script."
  exit
fi
echo "Unmounting NFS volumes."
umount 192.168.1.15:/media
umount 192.168.1.15:/backup
echo "Unmounting complete, shutting down now."
reboot -h
```

---

### Post by el_koraco on 2011-07-11
you might need to install a newer version of the engine that Orta uses? If the correct engine version is not present, GTK apps default to this monstrosity.

---

### Post by mips on 2011-07-12
> **handy said:**
> I just call "exec openbox-session" in .xinitrc.

(Preceded by this line "**setxkbmap -option terminate:ctrl_alt_bksp &**" which allows me to ctrl_alt_backspace to kill X. I also have "**ca::ctrlaltdel:/sbin/shutdown -t3 -r now" in innitab"**.)

Do you have anything in your fstab/mnt/media relating to your network or for USB disks/chips


I'll add the ctrl-alt-backspace to my .xinitrc, very handy to have.

My fstab is pretty clean, no usb or optical devices.
Auto mounting working really well now after the changes I made.


> **el_koraco said:**
> you might need to install a newer version of the engine that Orta uses? If the correct engine version is not present, GTK apps default to this monstrosity.

Orta has no support for gtk3 at this stage so not much that can be done about it.

---

### Post by el_koraco on 2011-07-12
I'm guessing that's your problem then. I treid to use some themes with GTK3 which haven't been ported, and the results are the same.

---

### Post by mips on 2011-07-12
> **el_koraco said:**
> **I'm guessing that's your problem then.** I treid to use some themes with GTK3 which haven't been ported, and the results are the same.

Correct. I'm sure Orta will be updated for gtk3 support seeing the theme is so popular, I did however notice that the author ( (SkiesOfAzel) is working on a new project [http://skiesofazel.deviantart.com/#/d30xkl4](http://skiesofazel.deviantart.com/#/d30xkl4) so hopefully it supports gtk3.

---

### Post by mips on 2011-07-12
I'm using the Ubuntu fonts with openbox but on my old 1024x768 res laptop they don't look to great (I applied the patches) as the lcd is generally soft (read old). The ubuntu fonts are not the problem if you get what I'm saying.

I'm looking to replace the font with a nice crisp font, almost something like terminus, any ideas & suggestions?

I'm using the [AwOken]("http://browse.deviantart.com/?qh=&section=&q=AwOken#/d2pdw32") icon theme which is really cool.

---

### Post by handy on 2011-07-12
Tahoma, preferred on the web.
Sans, on my system.

They look great here.

---

### Post by el_koraco on 2011-07-12
I'm using Droid Sans exclusively. The GS Cantarell is also a nice looking font.

---

### Post by mips on 2011-07-12
> **handy said:**
> Tahoma, preferred on the web.
Sans, on my system.

They look great here.

> **el_koraco said:**
> I'm using Droid Sans exclusively. The GS Cantarell is also a nice looking font.

Is Tahoma not the default WinXP font? I still have a XP partition (desktop) but I changed the fonts to Ubuntu :biggrin:

Thanks, I will have a look at the suggestions.

Edit: I have settled on Droid Sans Hebrew 8 which is identical to Sans but it also offers a monospace font which I use in the terminal.

---

### Post by handy on 2011-07-12
> **mips said:**
> Is Tahoma not the default WinXP font? I still have a XP partition (desktop) but I changed the fonts to Ubuntu :biggrin: 

I don't know, I haven't used XP for over 5.5 years. :mrgreen::biggrin::mrgreen::biggrin::mrgreen:

If you had of just stayed with Arch mips, you wouldn't have to be going through all of this setup routine again. [-X

***[edit:]** I'm not really an Arch fundamentalist... ;)*

---

### Post by mips on 2011-07-13
> **handy said:**
> 
If you had of just stayed with Arch mips, you wouldn't have to be going through all of this setup routine again. [-X

I see it as exercising that muscle called the brain and it's been a fun experience for me again :biggrin: 
I've also discovered some new things along the way like pinta (really great image edinting/drawing app), skippy (like expose in OS X), gftp, pkgbrowser etc.

My laptop is almost finished, looking good so far.
I still need to configure tint2 to add wicd, vattery & volicon to it as well as a nice theme, then I need to work on logout/shutdown/hibernate/suspend and clean up the openbox menus. Might also do a single line conky config at the bottom of the screen.

How can I set the default terminal to sakura instead of xterm when calling terminal apps?



.

---

### Post by handy on 2011-07-13
> **mips said:**
> 
I see it as exercising that muscle called the brain and it's been a fun experience for me again :biggrin: 

Fair enough, the installation is fun. :)

I've been exercising mine with Arduino:

[http://tronixstuff.wordpress.com/tutorials/](http://tronixstuff.wordpress.com/tutorials/)

It is incredibly powerful, & not hard to learn. I can see me creating a very small business out of it, designing & implementing smart garden irrigation systems, that sense the soil moisture, turn on the water via solenoids, at the specified time for a designated period, also have moisture sensors strategically located to sense if there is too much moisture after the irrigation has been turned on & if so turn it off, which would recover from a failed join or hose.

You can easily make it infra red remote controllable, so if a person has a number of garden beds they could just select from different programs (that I would have created & installed in the Arduino device) using the remote control. 

So if for example they are resting any of the beds, they could choose a program that would not irrigate those beds & water the other beds effectively.

There are so many other possibilities as you'll see if you are interested enough to have a look at the link. Anyway, I'll revert from my divert. :)  

> **mips said:**
> 
...

How can I set the default terminal to sakura instead of xterm when calling terminal apps?


I don't remember if I've made a configurations change or not.

In ~/.config/openbox/rc.xml , I call 3 programs & send them to their own dedicated desktops. Sakura is one of those app's.

If I call any terminal based app's from Worker, they are automatically opened in Sakura on its desktop, but I have set Sakura to be the terminal application in the Worker config'.

In the Openbox menu I don't have any terminal app's apart from Sakura itself. You could of course just call your terminal based app's into Sakura in your Openbox menu command line.

If you want to auto-start any app's onto their own specific desktops this is the script that I use, it is positioned at the very end of rc.xml they have to also be called in ~/.config/openbox/autostart.sh :

```
  # end of the example
-->

<application class="Sakura">
      <desktop>5</desktop>
	  <maximized>yes</maximized></application>
<application class="Gvim">
	  <desktop>4</desktop>
	  <maximized>yes</maximized></application>
<application class="Worker">
      <desktop>6</desktop>
    <focus>default</focus><position force="yes"><x>0</x><y>0</y><monitor>0</monitor></position></application>
<application class="Firefox">
      <desktop>1</desktop>
      <maximized>yes</maximized>
    <focus>yes</focus><position force="yes"><x>0</x><y>0</y><monitor>0</monitor></position></application>
 </applications>
</openbox_config>

```

---

### Post by handy on 2011-07-21
I've been away for the best part of a few days, so on settling back in, I just typed the equivalent of a pacman -Syu --aur (I use packer these days) & noticed that ***gnome-disk-utility*** was being upgraded!

Due to mips mentioning disk-utility, I searched for disk-utility (every way you could string the two words together) I got no worthwhile result in Scroogle, the Arch package database or AUR.

Which is a bit disappointing really.

---

### Post by mips on 2011-07-21
Also noticed the update.

---

### Post by mips on 2011-07-22
[[img]http://ompldr.org/tOWwzdg[/img]](http://ompldr.org/vOWwzdg)

Click on thumbnail for full size.

Seeing this thread has been mostly about my new install I though I would provide some feedback in the form of a picture. You all know that Chinese proverb about a picture is... ;)

Anyway, boots up in 42MB of ram, not something I'm used to :shock:


Here is the other thing I just realised, with no place for desktop icons (I'm not gonna install idesk) it has forced me to have neat & ordered folders&files in my /home. I have never had such a neat & ordered file system in my life as I usually just dump stuff on the desktop. Now as I copy or download stuff it goes into the correct folder, openbox has disciplined me :biggrin:

---

### Post by handy on 2011-07-22
Your desktop looks nice mips.

I always disliked working on other people's computers that had icons all over the desktop. I rarely ever saw any obvious order & it makes it time consuming to find whatever in such a (seemingly) disorganised mess. (No offence intended mips, just my reaction to the situation.:))

I have Worker set to land on its own specified workspace when Openbox starts, with ~/downloads open in the left hand window & /mnt/store in the right. Anything that comes in via the ReadyNAS box via torrent stays in it until I clean it up (removing any junk files that may have come along with it, if it is a movie adding subtitles if required & possible) then copied to the appropriate locations in /mnt/store & likewise in the (externally) tiny ReadyNAS box for backup.

My ~/downloads folder gets a clean out every week or so, as it can pick up quite a bit of stuff from browsing & via email. Some gets deleted after a review other gets treated the same way as the torrents mentioned above.

Basically it is a pretty tidy system though not to the point of obsessive compulsive perfection. ;)

---

### Post by jeffathehutt on 2011-07-22
It's hackerific! :)

Dark themes always remind me of old computers in some generic 70's or 80's movie.  But it is much easier on the eyes. :)

---

### Post by mips on 2011-07-23
I overclocked this old lappy of mine tonight by using a hardware pin mod, [http://www.notebookreview.com/default.asp?newsID=3226&article=pin+mod](http://www.notebookreview.com/default.asp?newsID=3226&article=pin+mod). It went from stock 1.4Ghz to 1.876GHz. This was achieved by increasing the FSB from 400Mhz to 533Mhz.

The best thing however is that the temperature dropped because I changed the thermal paste to AS5! Running Geekbench at 1.4GHz 100% CPU load the temp was 60°C, overlocked to 1.88GHz with new thermal paste it is running at 50°C at 100% load.

Can I feel the difference? Definitely!

1.4GHz
```

<geekbench version="Geekbench 2.1.13" checksum="cb894729a40769766581c91697f9bf18">
<score>1144</score>
<elapsed>78.9</elapsed>
<metrics>
<metric id="1" name="Platform" value="Linux x86 (32-bit)" ivalue="0" />
<metric id="2" name="Compiler" value="GCC 4.1.2 20070925 (Red Hat 4.1.2-33)" ivalue="0" />
<metric id="3" name="Operating System" value="Linux 2.6.39-ARCH i686" ivalue="0" />
<metric id="4" name="Model" value="Linux PC (Intel Celeron M)" ivalue="0" />
<metric id="5" name="Motherboard" value="Unknown Motherboard" ivalue="0" />
<metric id="6" name="Processor" value="Intel Celeron M" ivalue="0" />
<metric id="7" name="Processor ID" value="GenuineIntel Family 6 Model 13 Stepping 6" ivalue="0" />
<metric id="8" name="Logical Processors" value="1" ivalue="1" />
<metric id="9" name="Physical Processors" value="1" ivalue="1" />
<metric id="10" name="Processor Frequency" value="1.40 GHz" ivalue="1400000000" />
<metric id="11" name="L1 Instruction Cache" value="0.00 B" ivalue="0" />
<metric id="12" name="L1 Data Cache" value="0.00 B" ivalue="0" />
<metric id="13" name="L2 Cache" value="0.00 B" ivalue="0" />
<metric id="14" name="L3 Cache" value="0.00 B" ivalue="0" />
<metric id="15" name="Bus Frequency" value="0.00 Hz" ivalue="0" />
<metric id="16" name="Memory" value="1.22 GB" ivalue="1310740480" />
<metric id="17" name="Memory Type" value="N/A" ivalue="0" />
<metric id="18" name="SIMD" value="1" ivalue="1" />
<metric id="19" name="BIOS" value="N/A" ivalue="0" />
<metric id="20" name="Processor Model" value="Intel Celeron M" ivalue="0" />
<metric id="21" name="Processor Cores" value="1" ivalue="1" />
</metrics>
<sections>
<section name="Integer" id="1" percent="9">
<score>984</score>
<benchmarks>
<benchmark name="Blowfish" id="101" units="2">
<results>
<result threads="1" simd="0" result="41954383.1" comment="40.0 MB/sec" score="910" percent="9" />
<result threads="2" simd="0" result="41935481.4" comment="40.0 MB/sec" score="975" percent="9" />
</results>
</benchmark>
<benchmark name="Text Compress" id="102" units="2">
<results>
<result threads="1" simd="0" result="3452681.8" comment="3.29 MB/sec" score="1029" percent="10" />
<result threads="2" simd="0" result="3275377.7" comment="3.12 MB/sec" score="952" percent="9" />
</results>
</benchmark>
<benchmark name="Text Decompress" id="103" units="2">
<results>
<result threads="1" simd="0" result="4284665.6" comment="4.09 MB/sec" score="994" percent="9" />
<result threads="2" simd="0" result="4276042.9" comment="4.08 MB/sec" score="1023" percent="10" />
</results>
</benchmark>
<benchmark name="Image Compress" id="104" units="9">
<results>
<result threads="1" simd="0" result="7736219.1" comment="7.74 Mpixels/sec" score="936" percent="9" />
<result threads="2" simd="0" result="7746235.3" comment="7.75 Mpixels/sec" score="920" percent="9" />
</results>
</benchmark>
<benchmark name="Image Decompress" id="105" units="9">
<results>
<result threads="1" simd="0" result="12192965.7" comment="12.2 Mpixels/sec" score="726" percent="7" />
<result threads="2" simd="0" result="12088710.4" comment="12.1 Mpixels/sec" score="740" percent="7" />
</results>
</benchmark>
<benchmark name="Lua" id="107" units="10">
<results>
<result threads="1" simd="0" result="500923.9" comment="500.9 Knodes/sec" score="1301" percent="13" />
<result threads="2" simd="0" result="504598.1" comment="504.6 Knodes/sec" score="1311" percent="13" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Floating Point" id="2" percent="15">
<score>1591</score>
<benchmarks>
<benchmark name="Mandelbrot" id="201" units="1">
<results>
<result threads="1" simd="0" result="733868442.0" comment="733.9 Mflops" score="1103" percent="11" />
<result threads="2" simd="0" result="733579740.9" comment="733.6 Mflops" score="1121" percent="11" />
</results>
</benchmark>
<benchmark name="Dot Product" id="202" units="1">
<results>
<result threads="1" simd="0" result="842383344.4" comment="842.4 Mflops" score="1743" percent="17" />
<result threads="2" simd="0" result="842115774.8" comment="842.1 Mflops" score="1847" percent="18" />
<result threads="1" simd="1" result="1564696711.0" comment="1.56 Gflops" score="1306" percent="13" />
<result threads="2" simd="1" result="1553235254.9" comment="1.55 Gflops" score="1493" percent="14" />
</results>
</benchmark>
<benchmark name="LU Decomposition" id="203" units="1">
<results>
<result threads="1" simd="0" result="813737854.6" comment="813.7 Mflops" score="914" percent="9" />
<result threads="2" simd="0" result="814598151.7" comment="814.6 Mflops" score="929" percent="9" />
</results>
</benchmark>
<benchmark name="Primality Test" id="204" units="1">
<results>
<result threads="1" simd="0" result="188418839.1" comment="188.4 Mflops" score="1261" percent="12" />
<result threads="2" simd="0" result="182125182.9" comment="182.1 Mflops" score="981" percent="9" />
</results>
</benchmark>
<benchmark name="Sharpen Image" id="205" units="9">
<results>
<result threads="1" simd="0" result="5733391.9" comment="5.73 Mpixels/sec" score="2457" percent="24" />
<result threads="2" simd="0" result="5718977.0" comment="5.72 Mpixels/sec" score="2481" percent="24" />
</results>
</benchmark>
<benchmark name="Blur Image" id="206" units="9">
<results>
<result threads="1" simd="0" result="1830753.2" comment="1.83 Mpixels/sec" score="2313" percent="23" />
<result threads="2" simd="0" result="1828515.4" comment="1.83 Mpixels/sec" score="2325" percent="23" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Memory" id="3" percent="8">
<score>864</score>
<benchmarks>
<benchmark name="Read Sequential" id="302" units="2">
<results>
<result threads="1" simd="0" result="1632543437.1" comment="1.52 GB/sec" score="1241" percent="12" />
</results>
</benchmark>
<benchmark name="Write Sequential" id="304" units="2">
<results>
<result threads="1" simd="0" result="603431777.7" comment="575.5 MB/sec" score="821" percent="8" />
</results>
</benchmark>
<benchmark name="Stdlib Allocate" id="306" units="4">
<results>
<result threads="1" simd="0" result="4725682.7" comment="4.73 Mallocs/sec" score="1266" percent="12" />
</results>
</benchmark>
<benchmark name="Stdlib Write" id="307" units="2">
<results>
<result threads="1" simd="0" result="1056996424.0" comment="1008.0 MB/sec" score="475" percent="4" />
</results>
</benchmark>
<benchmark name="Stdlib Copy" id="308" units="2">
<results>
<result threads="1" simd="0" result="576988073.2" comment="550.3 MB/sec" score="521" percent="5" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Stream" id="4" percent="7">
<score>702</score>
<benchmarks>
<benchmark name="Stream Copy" id="401" units="2">
<results>
<result threads="1" simd="0" result="924372017.2" comment="881.5 MB/sec" score="629" percent="6" />
<result threads="1" simd="1" result="941463450.9" comment="897.8 MB/sec" score="676" percent="6" />
</results>
</benchmark>
<benchmark name="Stream Scale" id="402" units="2">
<results>
<result threads="1" simd="0" result="1017536355.2" comment="970.4 MB/sec" score="730" percent="7" />
<result threads="1" simd="1" result="1037825853.6" comment="989.7 MB/sec" score="716" percent="7" />
</results>
</benchmark>
<benchmark name="Stream Add" id="403" units="2">
<results>
<result threads="1" simd="0" result="1149866184.4" comment="1.07 GB/sec" score="709" percent="7" />
<result threads="1" simd="1" result="1195175463.9" comment="1.11 GB/sec" score="800" percent="8" />
</results>
</benchmark>
<benchmark name="Stream Triad" id="404" units="2">
<results>
<result threads="1" simd="0" result="1150492841.8" comment="1.07 GB/sec" score="775" percent="7" />
<result threads="1" simd="1" result="1177076033.9" comment="1.10 GB/sec" score="585" percent="5" />
</results>
</benchmark>
</benchmarks>
</section>
</sections>
</geekbench>

```


1.88GHz
```

<geekbench version="Geekbench 2.1.13" checksum="89ad21b24d40d94ea30652e8f9999091">
<score>1476</score>
<elapsed>59.5</elapsed>
<metrics>
<metric id="1" name="Platform" value="Linux x86 (32-bit)" ivalue="0" />
<metric id="2" name="Compiler" value="GCC 4.1.2 20070925 (Red Hat 4.1.2-33)" ivalue="0" />
<metric id="3" name="Operating System" value="Linux 2.6.39-ARCH i686" ivalue="0" />
<metric id="4" name="Model" value="Linux PC (Intel Celeron M)" ivalue="0" />
<metric id="5" name="Motherboard" value="Unknown Motherboard" ivalue="0" />
<metric id="6" name="Processor" value="Intel Celeron M" ivalue="0" />
<metric id="7" name="Processor ID" value="GenuineIntel Family 6 Model 13 Stepping 6" ivalue="0" />
<metric id="8" name="Logical Processors" value="1" ivalue="1" />
<metric id="9" name="Physical Processors" value="1" ivalue="1" />
<metric id="10" name="Processor Frequency" value="1.87 GHz" ivalue="1866000000" />
<metric id="11" name="L1 Instruction Cache" value="0.00 B" ivalue="0" />
<metric id="12" name="L1 Data Cache" value="0.00 B" ivalue="0" />
<metric id="13" name="L2 Cache" value="0.00 B" ivalue="0" />
<metric id="14" name="L3 Cache" value="0.00 B" ivalue="0" />
<metric id="15" name="Bus Frequency" value="0.00 Hz" ivalue="0" />
<metric id="16" name="Memory" value="1.22 GB" ivalue="1310740480" />
<metric id="17" name="Memory Type" value="N/A" ivalue="0" />
<metric id="18" name="SIMD" value="1" ivalue="1" />
<metric id="19" name="BIOS" value="N/A" ivalue="0" />
<metric id="20" name="Processor Model" value="Intel Celeron M" ivalue="0" />
<metric id="21" name="Processor Cores" value="1" ivalue="1" />
</metrics>
<sections>
<section name="Integer" id="1" percent="13">
<score>1311</score>
<benchmarks>
<benchmark name="Blowfish" id="101" units="2">
<results>
<result threads="1" simd="0" result="55977045.7" comment="53.4 MB/sec" score="1215" percent="12" />
<result threads="2" simd="0" result="55939044.0" comment="53.3 MB/sec" score="1301" percent="13" />
</results>
</benchmark>
<benchmark name="Text Compress" id="102" units="2">
<results>
<result threads="1" simd="0" result="4566760.5" comment="4.36 MB/sec" score="1361" percent="13" />
<result threads="2" simd="0" result="4355174.7" comment="4.15 MB/sec" score="1266" percent="12" />
</results>
</benchmark>
<benchmark name="Text Decompress" id="103" units="2">
<results>
<result threads="1" simd="0" result="5714036.5" comment="5.45 MB/sec" score="1326" percent="13" />
<result threads="2" simd="0" result="5696055.9" comment="5.43 MB/sec" score="1363" percent="13" />
</results>
</benchmark>
<benchmark name="Image Compress" id="104" units="9">
<results>
<result threads="1" simd="0" result="10311273.9" comment="10.3 Mpixels/sec" score="1248" percent="12" />
<result threads="2" simd="0" result="10323037.7" comment="10.3 Mpixels/sec" score="1226" percent="12" />
</results>
</benchmark>
<benchmark name="Image Decompress" id="105" units="9">
<results>
<result threads="1" simd="0" result="16217835.8" comment="16.2 Mpixels/sec" score="966" percent="9" />
<result threads="2" simd="0" result="16077958.8" comment="16.1 Mpixels/sec" score="985" percent="9" />
</results>
</benchmark>
<benchmark name="Lua" id="107" units="10">
<results>
<result threads="1" simd="0" result="668200.5" comment="668.2 Knodes/sec" score="1735" percent="17" />
<result threads="2" simd="0" result="673587.7" comment="673.6 Knodes/sec" score="1751" percent="17" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Floating Point" id="2" percent="21">
<score>2121</score>
<benchmarks>
<benchmark name="Mandelbrot" id="201" units="1">
<results>
<result threads="1" simd="0" result="978833010.8" comment="978.8 Mflops" score="1471" percent="14" />
<result threads="2" simd="0" result="978493246.1" comment="978.5 Mflops" score="1495" percent="14" />
</results>
</benchmark>
<benchmark name="Dot Product" id="202" units="1">
<results>
<result threads="1" simd="0" result="1123645740.4" comment="1.12 Gflops" score="2325" percent="23" />
<result threads="2" simd="0" result="1123312186.7" comment="1.12 Gflops" score="2465" percent="24" />
<result threads="1" simd="1" result="2087966172.3" comment="2.09 Gflops" score="1742" percent="17" />
<result threads="2" simd="1" result="2072875670.4" comment="2.07 Gflops" score="1993" percent="19" />
</results>
</benchmark>
<benchmark name="LU Decomposition" id="203" units="1">
<results>
<result threads="1" simd="0" result="1091500594.6" comment="1.09 Gflops" score="1226" percent="12" />
<result threads="2" simd="0" result="1089833238.7" comment="1.09 Gflops" score="1242" percent="12" />
</results>
</benchmark>
<benchmark name="Primality Test" id="204" units="1">
<results>
<result threads="1" simd="0" result="251993160.5" comment="252.0 Mflops" score="1687" percent="16" />
<result threads="2" simd="0" result="237793677.8" comment="237.8 Mflops" score="1281" percent="12" />
</results>
</benchmark>
<benchmark name="Sharpen Image" id="205" units="9">
<results>
<result threads="1" simd="0" result="7640012.8" comment="7.64 Mpixels/sec" score="3274" percent="32" />
<result threads="2" simd="0" result="7621709.0" comment="7.62 Mpixels/sec" score="3307" percent="33" />
</results>
</benchmark>
<benchmark name="Blur Image" id="206" units="9">
<results>
<result threads="1" simd="0" result="2442014.6" comment="2.44 Mpixels/sec" score="3086" percent="30" />
<result threads="2" simd="0" result="2438808.5" comment="2.44 Mpixels/sec" score="3101" percent="31" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Memory" id="3" percent="10">
<score>1040</score>
<benchmarks>
<benchmark name="Read Sequential" id="302" units="2">
<results>
<result threads="1" simd="0" result="1964317952.7" comment="1.83 GB/sec" score="1494" percent="14" />
</results>
</benchmark>
<benchmark name="Write Sequential" id="304" units="2">
<results>
<result threads="1" simd="0" result="672466503.2" comment="641.3 MB/sec" score="915" percent="9" />
</results>
</benchmark>
<benchmark name="Stdlib Allocate" id="306" units="4">
<results>
<result threads="1" simd="0" result="6277573.1" comment="6.28 Mallocs/sec" score="1682" percent="16" />
</results>
</benchmark>
<benchmark name="Stdlib Write" id="307" units="2">
<results>
<result threads="1" simd="0" result="1199445081.5" comment="1.12 GB/sec" score="539" percent="5" />
</results>
</benchmark>
<benchmark name="Stdlib Copy" id="308" units="2">
<results>
<result threads="1" simd="0" result="632475449.7" comment="603.2 MB/sec" score="571" percent="5" />
</results>
</benchmark>
</benchmarks>
</section>
<section name="Stream" id="4" percent="6">
<score>670</score>
<benchmarks>
<benchmark name="Stream Copy" id="401" units="2">
<results>
<result threads="1" simd="0" result="869007411.8" comment="828.8 MB/sec" score="591" percent="5" />
<result threads="1" simd="1" result="871008097.3" comment="830.7 MB/sec" score="625" percent="6" />
</results>
</benchmark>
<benchmark name="Stream Scale" id="402" units="2">
<results>
<result threads="1" simd="0" result="1044635613.2" comment="996.2 MB/sec" score="749" percent="7" />
<result threads="1" simd="1" result="1048058505.5" comment="999.5 MB/sec" score="723" percent="7" />
</results>
</benchmark>
<benchmark name="Stream Add" id="403" units="2">
<results>
<result threads="1" simd="0" result="1082507243.2" comment="1.01 GB/sec" score="667" percent="6" />
<result threads="1" simd="1" result="1106287639.6" comment="1.03 GB/sec" score="740" percent="7" />
</results>
</benchmark>
<benchmark name="Stream Triad" id="404" units="2">
<results>
<result threads="1" simd="0" result="1072803295.7" comment="1023.1 MB/sec" score="723" percent="7" />
<result threads="1" simd="1" result="1093701339.4" comment="1.02 GB/sec" score="544" percent="5" />
</results>
</benchmark>
</benchmarks>
</section>
</sections>
</geekbench>

```

From the above results I probably got about a 30%+ performance boost, not to bad for a little piece of jumper wire :biggrin:

---

### Post by handy on 2011-07-24
That little piece of jumper wire gouged a big chunk out of the geekbench time. I can see why you're happy. 

Good idea to get at the thermal paste (whilst you were passing through), all things considered. ;)

---

### Post by mips on 2011-07-24
Been thinking about this since I had the laptop open, these laptop heatsinks are badly designed. They are way to thin to be a proper 'sink' resulting in rapid heat spikes. Making them a little thicker would go a long way in reducing these spikes. But that would cost a $1 more to which would eat into profits...

I ran geekbench again today (letting the paste settle) and it's now hitting 51°C with the odd spike of 52°C. Still 9°C cooler than stock and much faster ;)

---

### Post by mips on 2011-07-26
I can not reboot my laptop, I though I would get round to sorting it out when I got to suspend/hibernate setup which I got sorted in a few minutes but I cannot reboot for the life of me.

Here is my post on the arch forums,
[https://bbs.archlinux.org/viewtopic.php?pid=966176#p966176](https://bbs.archlinux.org/viewtopic.php?pid=966176#p966176)
> Running 2.6.39.3-1 and I can't reboot my HP nx6110 laptop as it just hangs at restarting, shutdown works fine though. I've even tried kernel line options like reboot=b/h.

---

### Post by handy on 2011-07-26
What changes did you make that since you could reboot?

Obvious question I guess, but somewhere in there lies the answer I think.

---

### Post by mips on 2011-07-26
> **handy said:**
> What changes did you make that since you could reboot?

Obvious question I guess, but somewhere in there lies the answer I think.

Thing is reboot never worked from day one, I just left it as I thought I would eventually get around to to it.

Today I decided to tackle hibernate, suspend, shutdown & reboot. I got the first 3 to work just fine but something as simple as reboot does not work. *shutdown -r now* (which performs the same function as reboot) also does not work, just like reboot it hangs at 'restarting' and then I have to hold the bower button in to force a power down.

I think this is a bug of sorts as I've seen other people on the arch forums with a similar issue but I found no solution.

Edit: Almost 4am here, time for me to go sleep...

---

### Post by mips on 2011-07-27
Screenshot:
[[img]http://ompldr.org/tOW5jcA[/img]](http://ompldr.org/vOW5jcA)

Output of strace -v for reboot: [http://pastebin.com/Kk9tib1C](http://pastebin.com/Kk9tib1C)
.xinitrc: [http://pastebin.com/9YZPPHnq](http://pastebin.com/9YZPPHnq)
ob autostart.sh: [http://pastebin.com/T6rm3yc0](http://pastebin.com/T6rm3yc0)

The wiki was followed to the letter, [https://wiki.archlinux.org/index.php/Allow_Users_to_Shutdown](https://wiki.archlinux.org/index.php/Allow_Users_to_Shutdown)

Using consolekit/dbus does exactly the same thing as well.

If you guys need to see any other of my config files let me know.

---

### Post by boydrice on 2011-07-28
> **mips said:**
> Thing is reboot never worked from day one, I just left it as I thought I would eventually get around to to it.

Today I decided to tackle hibernate, suspend, shutdown & reboot. I got the first 3 to work just fine but something as simple as reboot does not work. *shutdown -r now* (which performs the same function as reboot) also does not work, just like reboot it hangs at 'restarting' and then I have to hold the bower button in to force a power down.

I think this is a bug of sorts as I've seen other people on the arch forums with a similar issue but I found no solution.

Edit: Almost 4am here, time for me to go sleep...

Are you running the shutdown -r now command as root or a regular user?  Are you using su or sudo?

---

### Post by mips on 2011-07-28
> **boydrice said:**
> Are you running the shutdown -r now command as root or a regular user?  Are you using su or sudo?

As root (login as root) or a regular user. My sudoers file has also been configured to allow these actions without needing a password.

---

### Post by mips on 2011-07-29
The rebooting issue seems to be a kernel bug...

---

### Post by Barrucadu on 2011-07-29
If you're not doing already, try enabling testing and upgrading. My friend had a regression in 2.6.29 with his HDD not being detected (though it worked in previous kernel versions) - upgrading to 3.0.0 fixed it.

---

### Post by mips on 2011-07-29
I usually don't enable testing but will do so now and try the linux-3.0-2 kernel.

EDIT: Nope, 3.0 has the same problem.

---

### Post by handy on 2011-08-14
I use scripts in Worker that umount my NAS & either reboots or shutsdown Arch.

reboot -h

Does it for me. 

I'm glad I'm not effected by that bug, it would be a pain.

---

### Post by mips on 2011-08-14
Geez, where have you been, I was about to call search & rescue :biggrin:

---

### Post by handy on 2011-08-14
> **mips said:**
> Geez, where have you been, I was about to call search & rescue :biggrin:

:lolflag:

I took off camping (finally had a predicted dry spell!) on my own, bumped my shin hard, which very quickly turned into an infected thrombosis. After carrying it for 5 days I bit the bullet & went & saw a Dr. to get the inevitable antibiotics.

It had me sitting about for the best part of 3 weeks & as many visits to the Dr. for dressing changes & 2 courses of antibiotics. It started to improve about 4 days ago.

Home yesterday arvo', still have the thrombosis, which is slowly diminishing & took the last antibiotic of that course this morning. If the infection flares up again I have another prescription for another course of the things. Hopefully I'll be right now. I don't like the idea of being hospitalised & drip fed antibiotics, which is the worst case scenario. Fortunately I'm a good healer.


You did ask? :)

---

### Post by mips on 2011-08-17
> **handy said:**
> 
You did ask? :)

Looks like my idea about calling search & rescue was the right one then :biggrin:

---

### Post by handy on 2011-08-21
Hey mips, how do you control the sound volume on your Arch/Openbox/Tint2 box?

I've had some problems getting the old faithful xfce4-panel to work with the new openbox 3.5.*. To the point that I thought I'd have a look at tint2. It has strengths & weaknesses compared to xfce4-panel, overall I think I won't have any trouble living with tint2.

I've spent too much time finding & sorting a screenshot tool today (amongst other things). I've ended up using scrot. I tried it & another in rc.xml, but couldn't get them to work there. Then I went to .bashrc, couldn't get scrot to work there either. I was using the following command in .bashrc :

```
alias shot="scrot '%T_$wx$h_scrot.png' -c -d 5 -e 'mv $f ~/documents/.pics/.shots'"
```

But it (& a few variations) won't work. So I ended up making a little screenshot.sh script & calling it from a button in Worker. Which works well. Then I changed the alias in .bashrc to call screenshot.sh & that works too.

As far as my audio volume is concerned I'm using some .xml in rc.xml that allows me to hold down the right hand Ctrl key & use the up & down arrows (cursor control keys). It worked first go which surprised me! :shock:

Time will tell if there are any other things I have to sort out to adapt to tint2.

Here's a screenshot of the (not so dramatically different) new desktop:

---

### Post by mips on 2011-08-21
> **handy said:**
> Hey mips, how do you control the sound volume on your Arch/Openbox/Tint2 box?

I've had some problems getting the old faithful xfce4-panel to work with the new openbox 3.5.*. To the point that I thought I'd have a look at tint2. It has strengths & weaknesses compared to xfce4-panel, overall I think I won't have any trouble living with tint2.

I've spent too much time finding & sorting a screenshot tool today (amongst other things). I've ended up using scrot. I tried it & another in rc.xml, but couldn't get them to work there. Then I went to .bashrc, couldn't get scrot to work there either. I was using the following command in .bashrc :

```
alias shot="scrot '%T_$wx$h_scrot.png' -c -d 5 -e 'mv $f ~/documents/.pics/.shots'"
```

But it (& a few variations) won't work. So I ended up making a little screenshot.sh script & calling it from a button in Worker. Which works well. Then I changed the alias in .bashrc to call screenshot.sh & that works too.

As far as my audio volume is concerned I'm using some .xml in rc.xml that allows me to hold down the right hand Ctrl key & use the up & down arrows (cursor control keys). It worked first go which surprised me! :shock:

Time will tell if there are any other things I have to sort out to adapt to tint2.

Here's a screenshot of the (not so dramatically different) new desktop:

For volume control I have [volumeicon]("https://aur.archlinux.org/packages.php?ID=35793") installed which seem pretty popular. I start it via my ~/.config/openbox/autostart file where I start all my other apps after open box has loaded (nitrogen --restore, tint2, volumeicon, conky, thunar --daemon). It also has hotkey support if I look in preferences for VolUp/VolDown/Mute but I have not setup that yet.

For screenshots I have scrot & [gscreenshot]("https://aur.archlinux.org/packages.php?ID=6363") installed which is a gui frontend for scrot. I just find it easier using a gui than openening a terminal and typing in a command to take screenshots. It has options for All, Selection, Window, hide window, delay & save as. I have it on tint2's launcher with my other most commonly used apps (browser, file manager, terminal, leafpad). The applauncher in tint2 is only available in the SVN version which you can find in AUR.

tint2 seems to do everything I need

---

### Post by handy on 2011-08-21
> **mips said:**
> For volume control I have [volumeicon]("https://aur.archlinux.org/packages.php?ID=35793") installed which seem pretty popular. I start it via my ~/.config/openbox/autostart file where I start all my other apps after open box has loaded (nitrogen --restore, tint2, volumeicon, conky, thunar --daemon). It also has hotkey support if I look in preferences for VolUp/VolDown/Mute but I have not setup that yet. 

Volumeicon looks interesting, I don't know if I'll need it, as the keyboard works fine & the mouse scroll wheel works too in VLC. Which is my primary (all but only) noise maker.

Here is the .xml that I put in rc.xml , if you are using ALSA, & have alsamixer installed it should work for you too:
```

<!-- Keybindings for volume control & muting -->
    <keybind key="C-Up">
      <action>amixer -q set Master 1+ unmute</action>
    </keybind>
    <keybind key="C-Down">
      <action>amixer -q set Master 1- unmute</action>
    </keybind>
    <keybind key="C-0">
      <action>amixer -q set Master toggle</action>
    </keybind> 
```

> **mips said:**
> 
For screenshots I have scrot & [gscreenshot]("https://aur.archlinux.org/packages.php?ID=6363") installed which is a gui frontend for scrot. I just find it easier using a gui than openening a terminal and typing in a command to take screenshots. It has options for All, Selection, Window, hide window, delay & save as. 

Thanks for pointing me at gscreenshot. I put it under the Screenshot (scrot) button in Worker, which is accessed via the RMB, I also stuck it in the Openbox menu. It will be useful if I need to just grab a pic of a window. I could make another script that does windows I guess, but I'm not going to.

> **mips said:**
> 
I have it on tint2's launcher with my other most commonly used apps (browser, file manager, terminal, leafpad). The applauncher in tint2 is only available in the SVN version which you can find in AUR. 

So is the applauncher a menu or does it have little icons? I'm not really interested in using it though, between Worker & having Firefox, Sakura & Worker autostart on their own desktops when Openbox starts, I rarely have any use for the Openbox menu.

I'll post the .xml that does the job for autoloading those guys, I battled with it for a while before urukrama gave me the tip on how to get it to work:

```
<application class="Sakura">
      <desktop>5</desktop>
	  <maximized>yes</maximized></application>
<application class="Gvim">
	  <desktop>4</desktop>
	  <maximized>yes</maximized></application>
<application class="Worker">
      <desktop>6</desktop>
    <focus>default</focus><position force="yes"><x>0</x><y>0</y><monitor>0</monitor></position></application>
<application class="Firefox">
      <desktop>1</desktop>
      <maximized>yes</maximized>
    <focus>yes</focus><position force="yes"><x>0</x><y>0</y><monitor>0</monitor></position></application>

</applications>

</openbox_config> 
```

I put it above the last two lines of .xml (which I included above) in the rc.xml file.

> **mips said:**
> 
tint2 seems to do everything I need

It looks like it will for me too, though if it weren't for the problems I had due to the Openbox 3.5 upgrade I wouldn't have bothered changing from xfce4-panel, it never left me wanting any more out of it.

---

### Post by mips on 2011-08-21
> **handy said:**
> 
So is the applauncher a menu or does it have little icons?

Little icons (you can specify the size).

Click on image for full size. 
[[img]http://ompldr.org/tOXpyeQ[/img]](http://ompldr.org/vOXpyeQ)
From left to right I have Chromium, Thunar, Sakura, Leafpad, Gscreenshot.

See *# Launcher* section
```

# Tint2 config file
# Generated by tintwizard (http://code.google.com/p/tintwizard/)
# For information on manually configuring tint2 see http://code.google.com/p/tint2/wiki/Configure

# To use this as default tint2 config: save as $HOME/.config/tint2/tint2rc

# Background definitions
# ID 1
rounded = 0
border_width = 1
background_color = #101010 15
border_color = #FFFFFF 40

# ID 2
rounded = 0
border_width = 0
background_color = #FFFFFF 40
border_color = #FFFFFF 47

# ID 3
rounded = 0
border_width = 0
background_color = #FFFFFF 15
border_color = #FFFFFF 67

# Panel
panel_items = LTSCB
panel_monitor = all
panel_position = bottom center horizontal
panel_size = 100% 18
panel_margin = 0 0
panel_padding = 7 0 7
panel_dock = 0
wm_menu = 0
panel_layer = top
panel_background_id = 1

# Panel Autohide
autohide = 0
autohide_show_timeout = 0.3
autohide_hide_timeout = 2
autohide_height = 2
strut_policy = follow_size

# Launcher
launcher_icon_theme = AwOken
launcher_padding = 1 2 5
launcher_background_id = 0
launcher_icon_size = 18
launcher_item_app = /usr/share/applications/chromium.desktop
launcher_item_app = /usr/share/applications/Thunar.desktop
launcher_item_app = /usr/share/applications/sakura.desktop
launcher_item_app = /usr/share/applications/leafpad.desktop
launcher_item_app = /usr/share/applications/gscreenshot.desktop

# Taskbar
taskbar_mode = single_desktop
taskbar_padding = 1 2 4
taskbar_background_id = 0
taskbar_active_background_id = 0

# Tasks
urgent_nb_of_blink = 8
task_icon = 0
task_text = 1
task_centered = 1
task_maximum_size = 140 16
task_padding = 2 1
task_background_id = 3
task_active_background_id = 2
task_urgent_background_id = 2
task_iconified_background_id = 0

# Task Icons
task_icon_asb = 70 0 0
task_active_icon_asb = 100 0 0
task_urgent_icon_asb = 100 0 0
task_iconified_icon_asb = 70 0 0

# Fonts
task_font = snap
task_font_color = #FFFFFF 67
task_active_font_color = #FFFF0C 54
task_urgent_font_color = #FFFFFF 82
task_iconified_font_color = #FFFFFF 73
font_shadow = 0

# System Tray
systray = 1
systray_padding = 5 2 5
systray_sort = ascending
systray_background_id = 0
systray_icon_size = 18
systray_icon_asb = 70 0 0

# Clock
time1_format = %H:%M
time1_font = DS-Digital 12
clock_font_color = #FFFFFF 73
clock_padding = 1 0
clock_background_id = 0
clock_rclick_command = orage

# Tooltips
tooltip = 0
tooltip_padding = 2 2
tooltip_show_timeout = 0.7
tooltip_hide_timeout = 0.3
tooltip_background_id = 1
tooltip_font = sans 10
tooltip_font_color = #000000 80

# Mouse
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

# Battery
battery = 1
battery_low_status = 5
battery_low_cmd = notify-send "battery low"
battery_hide = 99
bat1_font = snap 8
bat2_font = snap 6
battery_font_color = #FFFFFF 73
battery_padding = 1 0
battery_background_id = 0

# End of config

```

At some stage I'll setup hot keys to control volumeicon and later on start dabbling in Worker (it's already installed).

---

### Post by handy on 2011-08-21
The Launcher section looks nice & easy to work with.

The front end of your machine looks good. Nice & dark. :)

I don't know if I ever sent you my Worker config', or if you would want it. It has a few things in it that took me a while to work out.

Setting up Worker is like setting up Arch: it has a core system that is built to be customised; it can take quite a while to get everything just the way you want it, after which you tweak it a little this way & that over the years. Keeping a backup of the config' file in a safe place or two. 

When I set up another machine/system I like how I can just copy my Worker config' over & apart from any changes to the path buttons, I don't have to spend all that time over again.

I really should organise a backup of my Arch / partition, everything else of import is backed up.

---

### Post by mips on 2011-08-22
> **handy said:**
> The Launcher section looks nice & easy to work with.

The front end of your machine looks good. Nice & dark. :)

I don't know if I ever sent you my Worker config', or if you would want it. It has a few things in it that took me a while to work out.

Setting up Worker is like setting up Arch: it has a core system that is built to be customised; it can take quite a while to get everything just the way you want it, after which you tweak it a little this way & that over the years. Keeping a backup of the config' file in a safe place or two. 

When I set up another machine/system I like how I can just copy my Worker config' over & apart from any changes to the path buttons, I don't have to spend all that time over again.

I really should organise a backup of my Arch / partition, everything else of import is backed up.

Thanks.

You did send me your worker config but I can't remember where to, could you perhaps email it to me. Easier searching for things in my email than PM's.

I also need to backup my /usr & /home folders as I've made quite a few changes which would take time to do again should I have to go down that road again.

---

### Post by handy on 2011-08-22
> **mips said:**
> 
Thanks.

You did send me your worker config but I can't remember where to, could you perhaps email it to me. Easier searching for things in my email than PM's. 

I'll send it to you later this week, as I'm in the process of polishing up Worker gizzards some. 

After writing my previous post in this thread, I've spent the day reorganising all the data on the iMac Arch install, & on the ReadyNAS. I'm pretty happy with how it has turned out, as it was starting to get a bit messy.

Whilst I was doing that I was for some unknown (now?) reason drawn into the Worker config screen where I started reconfiguring the parts that matter to me re. the types of data that I use - .pdf, .txt, the common graphic file formats, the common movie file formats & other stuff, so that now I can just double click on such data that is listed in Worker & it will automatically load into the appropriate application.

Now it is functioning the way I like it, a lot. :D

I should have stuck my head into that stuff years ago when I first found Worker. I've been carrying the habit of absent mindedly double clicking on files in Worker even though (until today) that did nothing. Now it is behaving how DOpus & Windows Commander behave in that regard, which makes Worker an even more functional front end for my computer. 

> **mips said:**
> 
I also need to backup my /usr & /home folders as I've made quite a few changes which would take time to do again should I have to go down that road again.

The 1.5TB drive in my iMac (the Arch side) has ~90GB of free space, & the 1.5TB drive in the ReadyNAS has ~38GB. So I've got to start thinking about my next move. I think that the iMac won't easily accept a drive with a formatted capacity of over 2.1TB. So perhaps I could get hold of a 2.5TB drive & clone the 1.5TB onto it, as the 2.5TB when formatted should be pretty close to the Mac's legal limit.

Then I could stick the 1.5TB drive into the other draw of the ReadyNAS which should keep me out of trouble for quite some time at that end.

The other problem I have is the difficulty of cloning partitions on the iMac. If I wanted to clone a partition or two every few months or so, it is a bit clumsy to do it. I expect I'll have to use Clonezilla & a USB external drive. It is a shame it is such a time consuming thing to pull the drive out of.

& now my Gigabyte m'board has failed in the full-tower, I'll probably have to fix that up so I can pull the drive out of the iMac & clone it to a new larger one using the tower.

These days I'd really rather not be spending all this money on computers.

I'm open to any ideas/suggestions that you may have on the cloning side of things mips?

---

### Post by mips on 2011-08-22
> **handy said:**
> 
Whilst I was doing that I was for some unknown (now?) reason drawn into the Worker config screen where I started reconfiguring the parts that matter to me re. the types of data that I use - .pdf, .txt, the common graphic file formats, the common movie file formats & other stuff, so that now I can just double click on such data that is listed in Worker & it will automatically load into the appropriate application.

Now it is functioning the way I like it, a lot. :D


I'm looking forward to this config of yours, sounds like it will save me hours!


> **handy said:**
> 
I'm open to any ideas/suggestions that you may have on the cloning side of things mips?

It's a tough one with iMac not being easily accessible. Does it have a eSATA or Firewire port (I suspect it has the latter)? In this scenario it would be fasted most convenient to use Firewire I suspect but I have no experience with linux & firewire. Do you have a firewire HDD enclosure though? If all else fails just use USB and start running the cloning/imaging process before you go to bed, hopefully it will be done in the morning some time.

It's easy for me to open my case and connect via ATA/SATA to clone a drive & copy stuff, iMac would make me frustrated doing this task.

---

### Post by handy on 2011-08-22
It only has firwire. I no longer have an external firewire drive holder. 

It's not that it is hard to remove the iMac drive, it is just time consuming. I have to take the thing into another room where I have workspace, then lay it down, remove the RAM plate Phillips-head screw, put a suction cup on the plasti-glass screen & pull it off, then undo a dozen T9 torx screws which allows you to lift off the aluminium screen surround, disconnecting the mike cable as you go. Then, remove a couple of T6 torx screws that hold the display data cable in, then the eight T9 screws that hold the LCD panel in place, I can't remember any other cables to disconnect but there may be, then carefully fold it back behind the already laying down body, remove the HDD temp sensor, then pull HDD out, which has a connector screwed to it.

Do what ever you came for the drive for stick a drive back in & reverse the procedure.

Understandably I really like using the drive drawers in my old full-tower box. :rolleyes: That doesn't work anymore! :frown:

---

