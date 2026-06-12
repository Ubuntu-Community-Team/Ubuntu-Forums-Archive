---
title: "MacBook 2: possible solution for static / noise / distortion in left speaker"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by boomshop on 2009-02-02
Hi there!

If always had problems (since 7.04) with some static or distorted sound from the left speaker / left headphone on my book. I found serveral solutions on the internet like:

- options in /etc/modprobe.d/alsa-options: only worked out on 7.10, never in 7.04, 8.04, 8.10 for me
- reloading snd-hda-intel on boot with /etc/rc.local: dind't work since alsa or pulse is already running at that time

...but reloading the module was a fix I found in several tests with different inits.

So a simple solution for me is reloading the module BEFORE anything else sound relevant is started. I've done this through rc-inits:

```
echo -e '#!/bin/bash\nrmmod snd-hda-intel\nmodprobe snd-hda-intel' | sudo tee /etc/init.d/soundrestart
```

This one adds a script to init.d wich is only removing and loading the snd-hda-intel module.

```
sudo chmod +x /etc/init.d/soundrestart
```

This line will make the script executable.

```
sudo update-rc.d soundrestart start 10 2 3 4 5 .
```

And the last one will add it to the different inits at a really early stage (10), before hal (24) pulse (25) or anything else is loaded.

Never had any static, distortion or noise in my left output anymore - neither after boot, nor after reboot, wakeup or something.

---

### Post by cyberdork33 on 2009-02-02
awesome. 

Can you add this information to the wiki page for your hardware?

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by boomshop on 2009-02-02
Done for Hardy on 2.1. [https://help.ubuntu.com/community/MacBook2-1/Hardy#Sound](https://help.ubuntu.com/community/MacBook2-1/Hardy#Sound)

Additional (hopefully useless) information: If this one doesn't work for your book, undo everything with:

```
sudo update-rc.d -f soundrestart remove
sudo rm /etc/init.d/soundrestart
```

---

### Post by cyberdork33 on 2009-02-02
If someone can test this in Intrepid, we can put this in that document too.

---

### Post by boomshop on 2009-02-02
ooops... I got intrepid but actually there's no wiki page for it and macbook 2.1...

---

### Post by cyberdork33 on 2009-02-02
> **boomshop said:**
> ooops... I got intrepid but actually there's no wiki page for it and macbook 2.1...
sorry, I see. OK, something that needs fixed...

---

### Post by boomshop on 2009-02-02
I've put my [add on the wiki]("https://help.ubuntu.com/community/MacBook2-1/Hardy") in comment tags so it can easily be restored. Perhaps we better wait for some proofs before editing the help pages. That was the intention why I posted my solution in the forums first.

---

### Post by cyberdork33 on 2009-02-03
> **boomshop said:**
> I've put my [add on the wiki]("https://help.ubuntu.com/community/MacBook2-1/Hardy") in comment tags so it can easily be restored. Perhaps we better wait for some proofs before editing the help pages. That was the intention why I posted my solution in the forums first.
I actually think I remember having seen something like that before ;)

---

### Post by mabovo on 2009-02-03
> **cyberdork33 said:**
> sorry, I see. OK, something that needs fixed...

Sure it does. Not a big deal.

Intrepid and Mac 2,1 sound works nice with this tip.

Thanks.

---

### Post by cyberdork33 on 2009-02-03
> **mabovo said:**
> Sure it does. Not a big deal.

Intrepid and Mac 2,1 sound works nice with this tip.

Thanks.
OK, I took an initial whack at the Intrepid page for Macbook2,1. PLEASE PLEASE PLEASE someone that has installed Intrepid on their Macbook2,1 take a look at it and make sure that the information I migrated from the Hardy page is still valid!

I uncommented this fix there as well.

[https://help.ubuntu.com/community/MacBook2-1/Intrepid](https://help.ubuntu.com/community/MacBook2-1/Intrepid)

---

### Post by boomshop on 2009-02-04
Hey! looks good as far as I can tell, thanks for your work! I've got only two points:

In "keyboard" section there is a tip about disabling "use ambient light to adjust LCD brightness" - is there any macbook with this feature? Don't know.

And second: In the sound section there is a test with "ubuntu-sax.ogg" below the new fix. This will only work out if you reboot your machine before - I've simply forgotten to write it down. So we have to insert the reboot or put the test above the section with init.d, I think.

---

### Post by cyberdork33 on 2009-02-04
> **boomshop said:**
> In "keyboard" section there is a tip about disabling "use ambient light to adjust LCD brightness" - is there any macbook with this feature? Don't know.even if there is, it is only for macbook2,1 so if it doesn't, remove it.

There was a lot of info for macbook pros and other macbook versions in the old page. I was just porting stuff over.

> **boomshop said:**
> And second: In the sound section there is a test with "ubuntu-sax.ogg" below the new fix. This will only work out if you reboot your machine before - I've simply forgotten to write it down. So we have to insert the reboot or put the test above the section with init.d, I think.
I put it in a macbook2,1 owner's hands now :)

---

### Post by boomshop on 2009-02-04
Hey! After taking a look over my shoulder it seems you're pointing at me? :)

Okay, added the reboot and stripped the ambience-dim stuff. Hopefully I'm not wrong.

It's getting more and more off topic - I'll push it a bit further.

After a closer look in my own macbook_install.sh script, it seems I have some other stuff to offer for the wiki:

keyboard model and level3 chooser:
```
gconftool-2 --set /desktop/gnome/peripherals/keyboard/kbd/model --type string "apple_laptop"
gconftool-2 --set /desktop/gnome/peripherals/keyboard/kbd/options --type list --list-type string ["lv3`echo -e "\t"`lv3:rwin_switch"]
```

Screenshots on Ctrl+1 and Ctrl+2 (missing "print" button):
```
gconftool-2 --set /apps/metacity/global_keybindings/run_command_screenshot --type string "<Control>1"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_window_screenshot --type string "<Control>2"
```

F12 as eject (since intrepid it doesn't work anymore, haven't found a fix for me):
```

gconftool-2 --set /apps/gnome_settings_daemon/keybindings/eject --type string "F12"
```

KP-return (between right apple and left arrow) as DEL (missing button):
```
echo "keycode 104 = Delete" > ~/.Xmodmap_del
xmodmap .Xmodmap_del 

```

To autostart the DEL-key - change your username in second to last line:
```
echo '[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=Xmodmap Delete
Comment=KP-Return as Delete
Exec=xmodmap /home/[username]/.Xmodmap_del
X-GNOME-Autostart-enabled=true' > .config/autostart/Xmodmap_del.desktop

```

Function key for multimedia (F-buttons as default):
```
test=`grep "# Fn-Key" /etc/crontab -c`
if [ $test -eq 0 ]; then
	sudo sed -i.backup -e 's/exit 0/# Fn-Key\necho -n "0x02" > \/sys\/module\/hid\/parameters\/pb_fnmode\n\nexit 0/' /etc/rc.local
fi
```

Mactel repository:
```
test=`grep "mactel-support" /etc/apt/sources.list -c`
if [ $test -eq 0 ]; then
	echo "
# Mactel		
deb http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu intrepid main
" | sudo tee -a /etc/apt/sources.list
	GPGKEY=7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8 && gpg --no-default-keyring --keyring /tmp/tmp.keyring --keyserver keyserver.ubuntu.com --recv ${GPGKEY} && gpg --no-default-keyring --keyring /tmp/tmp.keyring --export --armor ${GPGKEY} | sudo apt-key add - && rm /tmp/tmp.keyring
	sudo apt-get update
fi
```

HFS-support:
```
sudo apt-get install -y hfsplus hfsutils hfsprogs
```

MacOS HD always mounted (change username and partition):
```
sudo mkdir /media/MacOSX
sudo chown username:username /media/MacOSX
test=`grep "# MacOSX" /etc/fstab -c`
if [ $test -eq 0 ]; then
	echo "
# MacOSX
/dev/sda2 /media/MacOSX auto rw,exec,auto,uid=1000,gid=1000,noatime 0 0" | sudo tee -a /etc/fstab
	sudo mount -o rw,exec,auto,uid=1000,gid=1000,noatime /dev/sda2 /media/MacOSX
fi
```

And then you can easily change your user ID from 500(?) to 1000 in MacOSX to have full access to your MacOSX home.

Ubuntu preferred in rEFIt menu:
```
sudo sed -i.backup -e 's/#legacyfirst/legacyfirst/' /media/MacOSX/efi/refit/refit.conf
```

ugly brown background before GDM:
```
sudo sed -i.backup -e 's/76848F/000000/' /etc/gdm/PreSession/Default
```

All mixer channels active, PCM as default:
```
gconftool-2 --type list --list-type string --set /desktop/gnome/sound/default_mixer_tracks [PCM]
gconftool-2 --type string --set /desktop/gnome/sound/default_mixer_device alsamixer:hw:0
gconftool-2 --type string --set /apps/panel/applets/mixer_screen0/prefs/active-track PCM
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerAufnahme --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerAufnahme1 --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerCenter --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerIEC958 --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerIEC958Aufnahme --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerIEC958DefaultPCM --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerInputSource --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerLFE --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerMux --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerMux1 --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerSurround --type bool 1
gconftool-2 --set /apps/gnome-volume-control/HDAIntelAlsamixerSwapCenterLFE --type bool 1
```

Better bash completion:
```
sudo sed -i.backup -e 's/#if [ -f \/etc\/bash_completion ]; then/if [ -f \/etc\/bash_completion ]; then/' /etc/bash.bashrc
sudo sed -i.backup -e 's/# . \/etc\/bash_completion/ . \/etc\/bash_completion' /etc/bash.bashrc
sudo sed -i.backup -e 's/#fi/fi/' /etc/bash.bashrc
```

Finally I fiddled a bit around with monitor colors. But after creating a profile under MacOS and loading it under Ubuntu, my colors are horrible out of range. Green becomes brown and so on. For me just a little more gamma is excellent:

```
sudo apt-get install xcalib
echo "
[Desktop Entry]
Type=Application
Name=XCalib
Exec=xcalib -a -gc 1.3
Icon=system-run
Comment=LCD colors" | tee ~/.config/autostart/XCalib
```

There's a lot more stuff in this script but that's more my personal setup stuff, packets, programs, desklets and so on. Perhaps the community is interested in one or the other idea...

And hopefully nothing went wrong by copy&pasting - in original it's a shell script which informs by zenity for status and reboots two times during install process.

If this post really doesn't fit the main thread anymore, please cut it off and move it to your desired location. Thanks.

---

### Post by cyberdork33 on 2009-02-04
Maybe continue here:
[http://ubuntuforums.org/showthread.php?t=969360](http://ubuntuforums.org/showthread.php?t=969360)

Things like the one for the mactel ppa should go on the mactel ppa page since it is not specific to the macbook2,1 hardware. the hardware pages should only have info specifically for getting that hardware to a normal running state. Things that can apply to all Macs (or even all computers) really do not belong there (not that it isn't good information or can't go somewhere else... hope that isn't too confusing :) )

---

### Post by boomshop on 2009-02-04
Hey!

No worry, I understood what you mean. I don't want to make the decisions wich of the informations above is useful enough to enter the wiki (and even *where*), since you and the mactel-team have spent a lot of time and brain building up that great docs. I Don't think that anyone in the team is like the guys at de.wikipedia, but I've learned to be really careful in editing another ones work even if I don't have enough knowledge about the direction you are working.

Is this forum software able to split and glue threads? In this case I think it would be best to split our talking about the wiki and the scripts above from this thread and paste it in the thread you've posted?

[edit]Just asked matthew about.[/edit]

---

### Post by cyberdork33 on 2009-02-05
> **boomshop said:**
> Hey!

No worry, I understood what you mean. I don't want to make the decisions wich of the informations above is useful enough to enter the wiki (and even *where*), since you and the mactel-team have spent a lot of time and brain building up that great docs. I Don't think that anyone in the team is like the guys at de.wikipedia, but I've learned to be really careful in editing another ones work even if I don't have enough knowledge about the direction you are working. You have to eventually otherwise you just a whole bunch of outdated info that nobody will delete.

---

### Post by Funnyguts on 2009-03-08
Sorry to drag this up from the dead, but I tried the suggestion on the first post to get rid of my left speaker static. However it only works itermittently. On some boots there will be lovely sounds, but on others the static will still be there. Any recommendations?

I'm running Ubuntu on Macbook 2,1.

---

### Post by boomshop on 2009-03-08
Hi!

After having this fix up and running 'til I wrote this topic I never got any static or distortion in left speaker anymore. So the only thing I could do is guessing.

Did you notice any regularity depending on reboot or cold start?

And have you tried to add some options to your modprobe.d? I don't need them anymore but before I hit upon this idea it brought me an experience like yours - sometimes it worked, sometimes it didn't.

so perhaps try:

```
sudo pico /etc/modprobe.d/options
```

and add the following line to this file:

```
options snd-hda-intel model=intel-mac-v2 position_fix=2 probe_mask=1
```

You can try to set position_fix to 1 or choose one of the following models:

#intel-mac-v1   : Intel Mac Type 1
#intel-mac-v2   : Intel Mac Type 2
#intel-mac-v3   : Intel Mac Type 3
#intel-mac-v4   : Intel Mac Type 4
#intel-mac-v5   : Intel Mac Type 5
#macmini        : Intel Mac Mini (equivalent with type 3)
#macbook        : Intel Mac Book (eq. type 5)
#macbook-pro-v1 : Intel Mac Book Pro 1st generation (eq. type 3)
#macbook-pro    : Intel Mac Book Pro 2nd generation (eq. type 3)
#imac-intel     : Intel iMac (eq. type 2)

You have to reboot every time for testing because you won't be able to unload/reload the module in an up and running system. By copying this information from my old options file I saw that my last choice was intel-mac-v5 while my crapbook is a 2.1.

Another test could be to change the stage when the fix is run via update-rc.d.

Just my first thoughts about, sorry that I couldn't help you out right away.

---

### Post by Funnyguts on 2009-03-09
I think I found the problem. I already modified the options file, but when I did I left brackets around [intel-mac-v2] when they should have been taken out. So far everything is working, but I need to start Ubuntu up a few more times to be sure.

Thanks!

---

### Post by tchorix on 2009-05-16
Hi guys,

Just to thank boomshop for the fix on the extremely annoying noise on the left channel. I'm using MacBookPro 1,1 with Ubuntu 9.04. After a couple of reboots is still working fine.

I just needed the steps described on the first post. The second one, adding options to /etc/modprobe.d/ . Somehow, that created some problems with the wireless, no idea why. The only thing I noticed was a warning about the options file, saying that I needed a .conf file instead. 

But so far the sound is working well, so thanks a lot.

cheers
Tchorix

---

### Post by cyberdork33 on 2009-05-16
> **tchorix said:**
> Hi guys,

Just to thank boomshop for the fix on the extremely annoying noise on the left channel. I'm using MacBookPro 1,1 with Ubuntu 9.04. After a couple of reboots is still working fine.

I just needed the steps described on the first post. The second one, adding options to /etc/modprobe.d/ . Somehow, that created some problems with the wireless, no idea why. The only thing I noticed was a warning about the options file, saying that I needed a .conf file instead. 

But so far the sound is working well, so thanks a lot.

cheers
Tchorix
if this is still an issue after all this time, could someone with the hardware in question find / create a bug report and link here or add the suggested fix there?

---

### Post by tiagobt on 2009-05-17
> **cyberdork33 said:**
> if this is still an issue after all this time, could someone with the hardware in question find / create a bug report and link here or add the suggested fix there?

The sound is fine in MacBook 2,1 (Jaunty).

---

### Post by tablebreaker on 2009-10-02
Hey guys, I was having the static in the left speaker problem, and I tried this and a few other things to fix it, and ended up completely losing my sound altogether. It doesn't even find my sound card anymore.

Any ideas? Should I just start a new thread?

---

### Post by ninjaaron on 2010-12-14
I may be the only person who still has a macbook 2.1, but I can confirm that this still works in 10.10 Maverick, for whatever it's worth.

---

### Post by NeoStrider on 2011-10-31
> **ninjaaron said:**
> I may be the only person who still has a macbook 2.1, but I can confirm that this still works in 10.10 Maverick, for whatever it's worth.

I'm using a MacMini 2.1 (almost same hardware as MacBook 2.1), with 10.10 and had the same issues. Tried the solution from the first post and after a reboot, it seems to be working. Got a very clear sound! I'm trully amazed!

But I still can't get my mic to work...Can you suggest me any post to look for a solution?

---

### Post by moonpoppy on 2012-05-01
using a macbook 2,1 with 12.04. i had the crackling sound issue in left speaker and this solution fixed it.

brilliant. 

thanks!

---

### Post by moonpoppy on 2012-05-01
double post

---

