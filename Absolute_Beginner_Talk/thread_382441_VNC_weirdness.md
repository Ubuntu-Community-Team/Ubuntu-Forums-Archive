---
title: "VNC weirdness"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by klapauciuspdx on 2007-03-12
Okay, for the most part I have this working, however, there are some strange things going on.

I can SSH to the box, no problem, commands work just fine.

I can launch vncserver, no problem.

I can have it throw a window to an xserver on the box that I'm coming from.

Here's the weird thing.  If I have it throw a window to the local xserver or I'm connected via ssh, everything types the way it's supposed to.  

The weird part is when I am using VNC through an SSH tunnel, if I try to type something on the VNC screen, it seems to be mapped differently, and I get gibberish.  Consistent gibberish, but gibberish nonetheless.  A seems to be A, but B maps to S, C maps to D, and there really seems to be something wrong with the mapping.  I set the keyboard mapping to default in Gnome, and  killed/restarted vncserver, but it is still not behaving correctly. 

Any ideas?  I would appreciate any suggestions.  Ooops... btw, running Feisty Fawn.

Klapauciuspdx :confused:

---

### Post by bluecat9 on 2007-03-18
I too have the issue with the keyboard funk..

No problems locally.. but after I log into GDM using vnc all keys appear to be mapped incorrectly..

I'm using Feisty Fawn with Xtightvnc server.

Note: No issue with vnc before upgrading from Edgy Eft.

Good luck.

---

### Post by Cypher on 2007-04-25
Same problem here..the keyboard mapping seems to be messed up through Tighvnc. However, if I use the Remote Desktop (VINO) option, things work as expected.

I also noticed that though I'm starting up 'vncserver' manually, vino-server is also starting up..

In my xstartup, if I leave it as the default:
```

x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```
Then the keyboard works as normal.
If I start up a GNOME session instead using
```

gnome-session &

```
then everything breaks..

---

### Post by czimmerman on 2007-04-30
Has anyone figured anything more out on this yet? I've been messing around with it all morning at work and have yet to get a resoltuion. I mean, most things I can do through SSH, but for the times that I need to access a desktop, it would be nice to get it to work.

---

### Post by Cypher on 2007-04-30
I found that this issue is only when I run a "gnome-session" through VNC. I went ahead and installed the Kbuntu-desktop on my machine and use "startkde" to startup a KDE session through VNC and everything works OK. As this is my rarely used machine at work, this solution works for me..

---

### Post by Woody@N87 on 2007-04-30
in case this helps the diagnosis of the problem,  i'm having similar issues but the only keys i've found so far that are mapped wrong is cap i which comes out a dash - quotations which show up as 4 (the number four) and the forward slash which shows as 8 (the number eight) Using Remote desktop on the fiesty linux machine (server)  and vnc viewer personal edition on the remote xp machine (client).  just found a new one the question mark comes up as 2 (the number two).:confused: 
  Mike

---

### Post by screddajames on 2007-05-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've got similar problems with vino on gnome desktop, but I don't think the key mappings are getting mangled in quite the same way (for me, the real irritants are | showing up as ` and < and > showing as z and x).  

I've filed bug # 112955 as I'm pretty sure everything was working fine before the Feisty upgrade.

---

### Post by tgalati4 on 2007-05-06
Something that works for me is to use ssh -2 -Y username@machinename
Once logged in, I run gnome-panel and it will display your desktop.  I find it uses less CPU time on the remote machine, so the desktop is a little more responsive.  This may not be as secure as tunneling VNC through an ssh session, but you can set up xauth (search the forums) and lock out the xsession for anyone else.

I'm running Dapper, so I haven't experience the keyboard problems between Mac OS X (chicken of the VNC), Ubuntu 6.06.1 Dapper and DSL 3.1.

---

### Post by gregmark on 2007-05-11
Trying to keep this topic alive.  The Bug Report for this at launchpad (#112955) is still listed as unconfirmed.  Like others, I am assuming that the problem is gnome and not vino or vnc.  I am connecting from a Mac using Chicken of the VNC to a tightvnc server running on my Fiesty box.  Starting gnome shifts the key mappings by four or five places.   As I am not Rainman or some other like genius, this makes using gnome over vnc impossible.

---

### Post by srpouyet on 2007-05-14
I found a workaround by Randy Sargent here:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/3]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955/comments/3")

For your convenience I've pasted this workaround below. The result is a stripped version of your gnome desktop (no wallpaper or ubuntu artwork). No more keyboard weirdness though.

Randy Sargent posted:
[I]I have the same problem described in "bug description". On 7.04, I can start a vnc server (tightvnc), and the keyboard is fine until I type "gnome-session", after which point it's remapped as described.

If instead, I run:
gnome-wm &
gnome-panel &
nautilus --no-default-window &
gnome-cups-icon &
gnome-volume-manager &

it seems to give me most of gnome, minus the inconvenient keyboard remapping.

Workaround: I modified my ~/.vnc/xstartup to be:

#!/bin/sh

xrdb $HOME/.Xresources
gnome-wm &
gnome-panel &
nautilus --no-default-window &
gnome-cups-icon &
gnome-volume-manager &
xterm &[/I]

---

### Post by srpouyet on 2007-05-14
An alternative solution is posted here: [http://ubuntuforums.org/showpost.php?p=2539412&postcount=4]("http://ubuntuforums.org/showpost.php?p=2539412&postcount=4")

I've tested this and it works. You can edit the settings in gconf-editor as described in the post by Labanana (I entered layout sdhfjskghjks which is invalid off course) and start gnome-session, starngely enough with the invalid layout my keyboard (us international) works fine!

---

### Post by srpouyet on 2007-05-14
> **srpouyet said:**
> An alternative solution is posted here: [http://ubuntuforums.org/showpost.php?p=2539412&postcount=4]("http://ubuntuforums.org/showpost.php?p=2539412&postcount=4")

I've tested this and it works. You can edit the settings in gconf-editor as described in the post by Labanana (I entered layout sdhfjskghjks which is invalid off course) and start gnome-session, starngely enough with the invalid layout my keyboard (us international) works fine!

Update: this solution generates errors / instability, be careful :-(

---

### Post by xtravagan on 2007-05-17
Hello,

I have the same problem, to reproduce I merely have to start the theme manager(without starting anything else), after that the keyboard is waco, don't know if that helps.

Cheers,
Niclas

---

### Post by Metallinut on 2007-05-18
Same problem here, on a fresh install of Fiesty.  So I don't think it's a problem with the upgrade.  It's still shown as unconfirmed on the bug site.  How long before something like this gets confirmed as a bug?

---

### Post by bur[n]er on 2007-05-28
This works, but without your theme applied.  If you click system->preferences->theme it then loads your theme, but breaks the keyboard yet again.

So for you devs looking to fix this, look in the themes!

---

### Post by thatcooldude on 2007-06-01
So according to the bugfix availble here:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955)

That solves this problem.  Question is...how do I apply the 'patch'?

Also, while we're at it, what do bugfixes mean when they send something "upstream"?  Or "Fixed Upstream"?

Thanks!

---

### Post by Cypher on 2007-06-01
Unless you're keen on re-building Gnome, you can't use the 'patch' provided in that bug. Upstream, in terms of development means to send it to "head" of the class and in turn ready to be built the next time a build is generated and released.

If this bug has been fixed upstream, whenever Ubuntu sends out another Gnome update, we'll get it.

Now, this bug is specifically fixed within Vino, but if you are using a Tightvnc-server, then I wonder if the bug will still exist or not..

---

### Post by thatcooldude on 2007-06-02
Thanks for the clarification!

Hopefully they'll roll out a new version soon then :/  Although, I doubt it'll be anytime soon, eh?

Seeing as Pidgin has yet to make it into the repositories, I doubt I'll be seeing a fix for this anytime soon.  Guess I'll just have to make do with the realllllly slow built in remote desktop (which also forces you to leave an open session :()

Thanks again!

---

### Post by langosta on 2007-06-08
I was having the same problem with keyboard mapping running vncserver on Feisty.  I used this tutorial:

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

And made the following changes:

In file /etc/xinetd.d/Xvnc, "port = 5902" and server_args should read (all one line):
server_args = -inetd :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

That "-extension XFIXES" got rid of the black and white checkered screen on login.

Ubuntu's built in remote package uses 5901, and it seems like I can not use this even if "netstat -tap" shows this port is currently closed.

I also had to uncheck "Disable multiple logins for a single user" in the login window preferences.

This got things going for me, no open session needed, hope it helps.

---

### Post by mcook2 on 2007-06-14
I get a similar problem, but not using Gnome Vino, as follows.

I'm running OSX 10.4.9 PPC with X11 1.1.3 - XFree86 4.4.0 using Apple keyboard thru KVM to Feisty.

I'm using Canadian English on the Mac, US English on Ubuntu, and Gnome  thinks I have a regular US 106-key keyboard (with windows keys) [sic], but this still happens if I tell Gnome I have a US Macintosh keyboard.     

Here's what happens:

1) I start X11 on the Mac

2) From xterm on the Mac I do ssh -X to my_username@my_Feisty_host

3) I get logged in and run xterm &, get the window on the Mac, and can type normally.

4) If I use gnome-panel all is well.

5) If I use gnome-session then I get a yard of error messages that I'm still trying to capture to post here [but see below], and the keyboard is incorrectly mapped in all xterms, including one started locally on the OSX box.

- Return maps to j
- The rest of the keyboard maps like this - not a complete list but enough to show you:

Normal:  

~!@#$%^&*()_+
`1234567890-=
QWERTYUIOP{}|
qwertyuiop[]\
ASDFGHJKL:"
asdfghjkl;'
ZXCVBNM<>?
zxcvbnm,./

Incorrect:

1) Upper case top row is disabled
2) `12345678 becomes mertziuõ
3) QW becomes two white question marks on a black shield then I get a return
4) qw becomes üó
5) and 6) the row ASDFGH is dead (upper and lower case).
7) ZXCV does nothing
6) zxcvbnm,./ becomes y5678öxcûvy.

One interesting thing is  that after this starts happening - i.e. after "gnome-session" is entered in the remote xterm - even a native xterm started subsequently on the Mac will be greyed out and the keyboard is mostly locked though Return becomes j as it does in the remote session. 

I have to kill and restart X11 on the Mac to be able to use even a regular local xterm correctly after this happens.  

I posted my .xsession-errors here: [http://skyprod.net/~mcook/Ubuntu/my-dot.xsession-errors.txt]("http://skyprod.net/~mcook/Ubuntu/my-dot.xsession-errors.txt").  To me, none of those messages seems to bear on the problem but someone else might spot something.  

Also, my xorg.conf is posted at [http://skyprod.net/~mcook/Ubuntu/my-xorg.conf.txt]("http://skyprod.net/~mcook/Ubuntu/my-xorg.conf.txt"). Most likely this isn't relevant, nor is the fact that I'm using Beryl+Emerald on Feisty.

Please let me know if I can provide any more information about this problem.

BTW [http://bugzilla.gnome.org/show_bug.cgi?id=440429](http://bugzilla.gnome.org/show_bug.cgi?id=440429) suggests this was fixed in Vino, but is there also a related fix for Gnome itself?  

Finally, since I'm not using Vino, I guess I should keep looking meantime, and maybe I will cross-post this messsage elsewhere. 

Have a nice day,

Michael Cook

---

### Post by mcook2 on 2007-06-14
Hmm - I just looked back again at [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/112955") and [http://bugzilla.gnome.org/show_bug.cgi?id=440429]("http://bugzilla.gnome.org/show_bug.cgi?id=440429") so I guess I really am using Vino after all and the fix is "in the pipe".  

But does anyone know when it'll be available as an automagical update for Feisty?  

Thanks, M.C.

---

### Post by david.ross@wolfeon.com on 2007-06-21
When will a package be sent through updates to fix this bug? Its annoying. I'm trying to convert the medical center I work at to use Ubuntu, this type of bug is embarrassing.

Please send the fix to updates.

---

### Post by OmahaVike on 2007-07-13
And to add to the reports of wierdness...

(using Dapper)

At terminal, host successfully interprets keyboard 100%, no problem.

Using a SSH'd VNC connection, Virtualbox doesn't understand my keystrokes.  Here's the kicker, everything else on the Dapper host works perfectly fine - no keyboard problems whatsoever.  Only Virtualbox and only on an SSH'd VNC connection.

Bizzarre.

---

### Post by bur[n]er on 2007-07-13
A better alternative to ssh & tightvncserver combo is to just use NoMachine!  [www.nomachine.com](www.nomachine.com) is free (not opensource though) and works very, very well over an encrypted ssh connection.

It allows you to create a virtual session or login to the console via the option shadow.  VNC is no longer necessary and keyboard weirdness goes away!

---

### Post by saaz on 2007-10-01
I have a fresh install of Feisty with all updates applied and this problem still exists. I suppose at this point that a fix won't come until I upgrade to Gusty Gibbon?

---

### Post by geertn on 2007-10-11
I use Gutsy with the latest updates and I still see this problem with Xvncserver.

---

### Post by tofagerl on 2007-10-25
Using Gutsy updated from Feisty, and this problem is still here. I tried changing theme to Clearlooks, but no change.

---

### Post by tofagerl on 2007-10-31
Today the Gnome Settings Daemon for some reason didn't start on my computer, although everything else works (including themes.)

And the keyboard works fine in VNC for the first time in months!

Therefore I assume the problem is in Gnome Settings Daemon, and I will try to uninstall it.

Edit: It turns out to be even simpler! If I simply delay starting gnome-settings-daemon untill after Gnome is fully loaded, VNC works! I have tested this on two separate machines by doing:

```
sudo chmod a-x /usr/bin/gnome-settings-daemon
```
(this makes gnome-settings-daemon unable to start)

and then the following after gnome has restarted:

```
sudo chmod a+x /usr/bin/gnome-settings-daemon
gnome-settings-daemon
sudo chmod a-x /usr/bin/gnome-settings-daemon
```
(this temporarily enables gnome-settings-daemon to start, starts it, and then disables it again.)

---

### Post by combatwombat_nz on 2007-10-31
Don't know if this helps y'all with the problem "The X system keyboard settings differ from your current GNOME keyboard settings", but I was having that issue at every reboot, and googled till I was blue. But then I found that the gnome-settings-daemon is the key, the problem is in the gconf registry.

sudo killall gnome-settings-daemon
gnome-settings-daemon

error message pops up

go into the gconf-editor

desktop/gnome/peripherals/keyboard

make sure the strings in kbd and kbd.sysbackup are the same, in my case pc105

kill gnome-settings-daemon again, then reload it. Fixed?

---

### Post by trausti on 2007-12-14
A possible cause is the keymap. To clear it, copy and past the following into a terminal:

echo '#!/bin/bash' > clear_keymap.sh
echo 'echo "" > empty.keymap' >> clear_keymap.sh
echo 'xmodmap empty.keymap' >> clear_keymap.sh
chmod 755 clear_keymap.sh
./clear_keymap.sh

---

