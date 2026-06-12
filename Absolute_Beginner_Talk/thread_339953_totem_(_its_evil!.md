---
title: "totem :( its evil!"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by wannaBeHacker on 2007-01-16
hey guys im trying to follow these instructions, but i cant get totem-gstreamer to open in the terminal it tells me no such command, when i type type in totem, and player opens up but i cant change the properties.

i even searched for the life totem_config and i couldnt find it

> 4. Fix totem playback

To have an optimised video playing on xorg-aiglx :

-> if you have totem-gstreamer :
launch gstreamer-properties and select on default video playback “XWindow (NoXv)” in video tab.

-> if you have totem-xine :
edit ~/.gnome2/totem_config and replace this line :

    #video.driver:auto

by

    video.driver:xshm

Have fun


after i installed this, my screen saver has been flikering too any1know why?

---

### Post by Shay Stephens on 2007-01-16
I believe totem-xine is installed by default and you have to manually install totem-gstreamer.  Doing so, I believe, will uninstall totem-xine and replace it with toem-gstreamer.  One or the other, but not both.

---

### Post by Delkster on 2007-01-16
> **Shay Stephens said:**
> I believe totem-xine is installed by default and you have to manually install totem-gstreamer.

Looks like [totem-xine](http://packages.ubuntu.com/edgy/gnome/totem-xine) is still in universe in Edgy, so I guess totem-gstreamer is the one that's installed by default.

---

### Post by Shay Stephens on 2007-01-16
Ahh, good find, thank you for the correction.  Installing totem-xine will uninstall the default the totem-gstreamer.

---

### Post by ComplexNumber on 2007-01-16
> **Shay Stephens said:**
> Ahh, good find, thank you for the correction.  Installing totem-xine will uninstall the default the totem-gstreamer.
thats correct. in the case of totem, xine is a lot better than gstreamer. i would recommend using the former.

---

### Post by wannaBeHacker on 2007-01-18
call me stupid, but how do i do what i need to do with xine?](*,)

> errorprone@errorprone-laptop:~$ totem-xine
bash: totem-xine: command not found
errorprone@errorprone-laptop:~$ sudo totem
totem                    totem-video-thumbnailer  
errorprone@errorprone-laptop:~$ sudo totem-video-thumbnailer 
.bash_history              .local/
.bash_logout               .macromedia/
.bash_profile              Mail/
.bashrc                    .metacity/
.config/                   .mozilla/
Desktop/                   .nautilus/
.dmrc                      .openoffice.org2/
.esd_auth                  plugin_stack.trace
.evolution/                .recently-used
Examples/                  .recently-used.xbel
.fonts.cache-1             .rnd
.gaim/                     sent
.gconf/                    .sudo_as_admin_successful
.gconfd/                   .themes/
.gksu.lock                 .thumbnails/
.gnome/                    .Trash/
.gnome2/                   .tsclient/
.gnome2_private/           .update-manager/
.gnome-compiz-manager/     .update-notifier/
.gnomerc                   vmware/
.gnupg/                    .vmware/
.gstreamer-0.10/           .w3m/
.gtkrc-1.2-gnome2          Windows XP Professional/
.ICEauthority              .Xauthority
.icons/                    .xsession-errors
.java/                     
errorprone@errorprone-laptop:~$ sudo totem-video-thumbnailer 


---

### Post by Delkster on 2007-01-18
> **wannaBeHacker said:**
> call me stupid, but how do i do what i need to do with xine?](*,)

Have you installed the totem-xine package yet?

If not, do this:
1. Make sure you have the universe software repository/channel enabled. There are [instructions in the wiki](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096) for doing that if you haven't done it already. The instructions are for Ubuntu 6.06 (Dapper) but you can probably figure out what to do in 6.10 (Edgy) based on them anyway.
2. Open **System > Administration > Synaptic Package Manager**
3. Use the search to find a package called totem-xine. Mark it for installation. That will also automatically mark totem-gstreamer for removal. Don't worry about that.
4. Apply the changes.

Now, when you start Totem (either from the terminal or from the menus, or in any other way you'd previously start it), it'll be the version that uses xine as the player engine (i.e. it plays the formats that xine supports, etc.). In the terminal the command is just "totem" exactly like before; you've just replaced the version of Totem that used gstreamer with one that uses xine.

By the way, while it may be tempting in some cases, you don't need sudo when running applications such as totem. You only need it when installing software, changing system settings etc. The command "totem" runs the media player, doesn't install one. If you want to know how to install and remove software packages from the command line (that *does* require sudo), that's done with either "apt-get" or "aptitude". Look at the [apt-get howto](https://help.ubuntu.com/community/AptGetHowto) in the wiki if you're interested, but you can do most of that stuff in Add/Remove Applications and/or Synaptic as well.

---

### Post by wannaBeHacker on 2007-01-18
thanks Delkster, but if i wanted to do all that from the terminal would i do this?

sudo apt-get install totem-xine

sudo apt-get update

---

### Post by Delkster on 2007-01-27
> **wannaBeHacker said:**
> thanks Delkster, but if i wanted to do all that from the terminal would i do this?

sudo apt-get install totem-xine

sudo apt-get update

Sorry about the slow response.

The "install" command is correct, but you don't need the update command afterwards -- if anything, you'd need it *before* the install command. The "apt-get update" command just refreshes your computer's information about available packages, so it may be a good idea to run it before installing stuff to make sure that you're getting the latest version, but it's generally not needed because Ubuntu rarely gets new versions of applications anyway, and the local information on available package versions is updated regularly in order to automatically find out about updates anyway.

---

