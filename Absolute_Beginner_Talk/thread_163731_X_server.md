---
title: "X server"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by prezbedard on 2006-04-21
ok I got gnome desktop installed using apt-get install ubuntu-desktop

but now I get an error 

X Server now disabled. Restart GDM when it is configured correctly.

How do I configure X Server?

---

### Post by Andrew-buntu on 2006-04-21
> sudo dpkg-reconfigure xserver-xorg
Then just follow the prompts.  The defaults are usually safe.  When you're done, type:
> sudo /etc/init.d/gdm restart

---

### Post by prezbedard on 2006-04-21
[QUOTE=Andrew-buntu]Then just follow the prompts.  The defaults are usually safe.  When you're done, type:[/QUOTE]


ok thanks.

I assume this should work in recovery mode as after the error appears I get a blank screen to which I can type but nothing actually executes so I can only get into recovery mode at the moment.

---

### Post by Andrew-buntu on 2006-04-21
Yep, should work in recovery mode.  After your xserver fails, can you get to a terminal by pressing Ctrl+Alt+F1?  I usually get dropped right back there if my Xorg doesn't start.

---

### Post by prezbedard on 2006-04-21
ok well I ran 

dpkg-reconfigure xserver-xorg

then

/etc/init.d/gdm restart

and got the following error

using config file /etc/X11/xorg.conf

Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_debugclip.o
No symbols found
Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_debug_norm.o
No symbols found
Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_xform.o
No symbols found



I did try the Ctrl+Alt+F1 and it did work. wasn't aware of it still pretty new to ubuntu.

---

### Post by Andrew-buntu on 2006-04-21
[QUOTE=prezbedard]
Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_debugclip.o
No symbols found
Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_debug_norm.o
No symbols found
Skipping
/usr/X11R6/lib/modules/extensions//libGLcore.a:m_xform.o
No symbols found

[/QUOTE]

So you didn't get to the login screen?  Looks as if it still should've started up.

---

### Post by echo $USER on 2006-04-21
> sudo apt-get install gdm

Will give you the graphical login screen.  Should solve your problem.  Then run 

> startx

---

### Post by prezbedard on 2006-04-21
Nope got the same error

X Server now disabled. Restart GDM when it is configured correctly.

I did get more detailed errors from the log

(ww) The Directory 

/usr/share/X11/fonts/cyrillic does not exist

Entry deleted from path

(ww) The Directory 

/usr/share/X11/fonts/CID does not exist

Entry deleted from path

(**) FontPath Set to
/usr/share/fonts/misc, /usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled, /usr/share/X11/share/X11/fonts/Type1, /usr/share/X11/fonts/100dpi, /usr/share/X11/fonts/75dpi, /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID

(==) RgbPath set to /usr/X11R6/lib/modules
(==) ModulePath Set to /usr/X11R6/lib/
(ww) OpenAPM failed (/dev/apm_bios) (no such file or directory)

---

### Post by prezbedard on 2006-04-21
tried apt-get install gdm

and it told me I have the latest gdm installed

---

### Post by prezbedard on 2006-04-21
startx gave me

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining

---

### Post by Andrew-buntu on 2006-04-21
Which driver did you select when running through the dpkg-reconfigure?  It would've been the first thing you had to choose.
Also, which video card are you using?

---

### Post by prezbedard on 2006-04-21
I chose the one that was selected by deafault. VESA.

My video card is just an integrated one with only 1MB memory

The system is an old compaq proliant 1600

---

### Post by bodhi.zazen on 2006-04-21
try dpkg-reconfigure gdm

reboot

if this does not work:

Remove kdm (from the start script) and reboot.

If you do not know how to disable start scripts, re-post for instructions.

If this does not work post the contents of your xorg.conf
     /etc/X11/xorg.conf

---

### Post by prezbedard on 2006-04-21
ok I was looking around at the different log files and found the daemon.log with some related errors

localhost modprobe: Fatal: Error inserting apm (/lib/modules/2.6.12-9-386/kernal/arch/i386/kernal/apm.ko): No such device

this one was in it 3x

localhost gdm[6481]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

localhost gdm[6383]: deal_with_x_crashes: Running the X keeps crashing script

Failed to start X server several times in a short period; disabling display: 0

---

### Post by prezbedard on 2006-04-21
How do I remove the kdm from the startup script?

---

### Post by bodhi.zazen on 2006-04-21
I am rusty with Ubuntu.

Are you running a GUI or command line?

If command line, can youstart KDE

At the command prompt type
     sudo kdm

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]I am rusty with Ubuntu.

Are you running a GUI or command line?

If command line, can youstart KDE

At the command prompt type
     sudo kdm[/QUOTE]


cli right now can't get gui working

I have gnome installed not KDE

---

### Post by prezbedard on 2006-04-21
do I remove gdm from the init.d?

---

### Post by bodhi.zazen on 2006-04-21
To disable kdm:

     sudo update-rc.d -f  kdm remove

to enable kdm:

     sudo update-rc.d kdm defaults

After disabling kdm type

     sudo init 2

It that does not work, re-boot

(recongfigure gdm first)

---

### Post by bodhi.zazen on 2006-04-21
I am sorry, I assumed you installed kbuntu first and then installed ubuntu

What did you install??

---

### Post by Andrew-buntu on 2006-04-21
What do you get from "sudo cat /var/log/Xorg.0.log | grep EE"?  The errors you've mentioned so far aren't show-stoppers - WW is a warning, EE is an error.

---

### Post by bodhi.zazen on 2006-04-21
Do not remove anything from init.d

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]I am sorry, I assumed you installed kbuntu first and then installed ubuntu

What did you install??[/QUOTE]


ubuntu

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]Do not remove anything from init.d[/QUOTE]


not yet

---

### Post by prezbedard on 2006-04-21
[QUOTE=Andrew-buntu]What do you get from "sudo cat /var/log/Xorg.0.log | grep EE"?  The errors you've mentioned so far aren't show-stoppers - WW is a warning, EE is an error.[/QUOTE]


nothing just what the symbols stand for

---

### Post by bodhi.zazen on 2006-04-21
Don't bother with kdm if you have not installed KDE (Kbuntu)

Stupid things:

Does Control-Alt-F7 bring you to the log in (graphical) screen?

If not, have you re-booted?

If so, what happens when you type X at the cli?
     If you get a grey screen with a "X" for a curser type control-Alt-Backspace to exit X

If X is working, what happens when you type gnome-session?

---

### Post by bodhi.zazen on 2006-04-21
By the way, Ubuntu installs Gnome, why did you apt-get install ubuntu-desktop?

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]By the way, Ubuntu installs Gnome, why did you apt-get install ubuntu-desktop?[/QUOTE]


I did the install with the server option not realizing it was a very basic install

---

### Post by bodhi.zazen on 2006-04-21
Where are you now in de-bugging? I have seen several posts and it has been an hour.

---

### Post by prezbedard on 2006-04-21
When I type X I get a blank screen. I need to use Ctrl-Alt-F1 to get back to the cli

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]Where are you now in de-bugging? I have seen several posts and it has been an hour.[/QUOTE]


I'm going to try the last couple of things you suggested. just got back from some errands.

---

### Post by prezbedard on 2006-04-21
When I type

gnome-session I get

(gnome-session:6401): Gtk-WARNING ** : cannot open disply;

---

### Post by bodhi.zazen on 2006-04-21
Give me an update when you are ready.

---

### Post by bodhi.zazen on 2006-04-21
Type
     X & gnome-session

---

### Post by prezbedard on 2006-04-21
Control-Alt-F7 does nothing

---

### Post by prezbedard on 2006-04-21
X & gnome-session

gives the same result as just typing X

---

### Post by bodhi.zazen on 2006-04-21
sorry to be rusty on Ubuntu

try X gnome-session

Wait, this may start gnome with a small delay

---

### Post by bodhi.zazen on 2006-04-21
by the way, if you get a grey secreen with an "X" that responds to mouse movements, x-server is not the problem.

If X gnome-session works,

Try- sudo gdm

Also, if you want Ubuntu, why not a typical install. For that matter, why not drapper drake?

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]sorry to be rusty on Ubuntu

try X gnome-session

Wait, this may start gnome with a small delay[/QUOTE]


It reported that gnome-session was an unrecognized option

---

### Post by bodhi.zazen on 2006-04-21
Re-try 

X & gnome-session

Wait a while longer. Often there is a 20-30 second delay to start of Gnome

---

### Post by bodhi.zazen on 2006-04-21
If you can get gnome up and running, you can configure gdm with a graphical interface from within gnome.

---

### Post by bodhi.zazen on 2006-04-21
gotta go

Will check in later

---

### Post by prezbedard on 2006-04-21
[QUOTE=bodhi.zazen]Re-try 

X & gnome-session

Wait a while longer. Often there is a 20-30 second delay to start of Gnome[/QUOTE]


nope nothing I typed it and let it sit for a few minutes and went back and it was still a blank screen.

---

### Post by aktiwers on 2006-04-21
If this is a fresh install, why dont you just reinstall it normally?

Else, have you tried removing gdm and installing it again?

I think its done this way:

```


sudo apt-get remove gdm
sudo apt-get install gdm


```

Or is it?

```

sudo apt-get remove gdm-desktop
sudo apt-get install gdm-desktop

```

Sorry im a noob my self, so im not sure, but it might fix your problem removing it, and installing it again.

---

### Post by prezbedard on 2006-04-21
Thanks but it didn't change anything.

---

### Post by prezbedard on 2006-04-21
[QUOTE=aktiwers]If this is a fresh install, why dont you just reinstall it normally?

.[/QUOTE]


Well I really wanted to resolve this without having to reinstall.

I figure I learn more this way.

---

### Post by Andrew-buntu on 2006-04-21
I think reinstalling is the best way, too - it's been a few hours since you first posted and it takes less than an hour for a fresh install.  Don't worry, you'll learn plenty by tweaking your system, installing fresh software, etc.
Plus, your Xserver doesn't work but it also doesn't throw out any errors in the log, which makes diagnosis really tough.

---

### Post by prezbedard on 2006-04-21
I just finished up a fresh install this time doing the normal one and after it finished up I am left with a blank screen. Ctrl-Alt-F1 won't even bring up a cli login.

---

### Post by Andrew-buntu on 2006-04-21
OK.  Let's find you the right driver for your video card. boot into recovery mode and get the
 output of "lspci" - this will tell us what video card you're using.
While you're at the cli, try sudo dpkg-reconfigure xserver-xorg again.  Use the vga driver instead of the vesa driver.

---

### Post by bodhi.zazen on 2006-04-21
We seem to be going in circles here.

I think xserver is working OK. Test this by typing X.
It would be helpful if I knew if X works, specifically do you see a grey screen wtih an X which moves when you move the mouse.

If yes, the problem is not with the xserver.

Please advise.

---

### Post by bodhi.zazen on 2006-04-21
I think the problem is ubuntu server install is a minimal interface, cli only type of thing.

Once you get back to the cli try this:

sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal ubuntu-base ubuntu-minimal ubuntu-standart ubuntu-desktop

---

### Post by Andrew-buntu on 2006-04-21
He posted that he had just finished a regular install (I'm assuming that means not the server install) and he still can't get to gnome.  I think Xserver is running (he's not getting any errors in the logs).  The problem is that the settings aren't correct so he's not seeing what the server displays.  Perhaps his resolution is too high or he's using a not-quite-right driver.

---

### Post by bodhi.zazen on 2006-04-21
Thank you Andrew-buntu

My impression was different.

Back to prezbedard

1. What type of install did you do, server or Ubuntu (with gnome/kde)?

2. Is X working? What happens when you type X, is there an X that moves with the mouse?

3. We can try to configure X if it is not working. Need to know you video card and monitor.

to configure X:

nano /etc/X11/xorg.conf

Look for the lines regarding yor monitor:

Section "Monitor"

make sure you have the proper vert and horizontal sync
     Google search you monitor

Then go to section "Screen"
Change defaultdepth to 16

reboot

However, if the server version is installed, this is different. The server install is a minimal install and try installing additional packages as needed (see my previous post)

---

### Post by prezbedard on 2006-04-22
[QUOTE=bodhi.zazen]We seem to be going in circles here.

I think xserver is working OK. Test this by typing X.
It would be helpful if I knew if X works, specifically do you see a grey screen wtih an X which moves when you move the mouse.

If yes, the problem is not with the xserver.

Please advise.[/QUOTE]

Well I do know when I type X I get a blank screen with no X when I move the mouse.

also I believe it is cirrus video driver it use because with this normal install that is what it got detected during the xserver-xorg initial setup.

I will post the output from lspci


Yes I just did a normal install last night not "server" this time and still can't get into gnome

---

### Post by prezbedard on 2006-04-22
ok the line regarding the video from the lspci output is

VGA compatible controller:  Cirrus Logic GD 5446 (rev 45)

---

### Post by prezbedard on 2006-04-22
I ran nano /etc/X11/xorg.conf and made and saved the changes ,rebooted and same result.

---

### Post by prezbedard on 2006-04-22
btw guys thanks for all help. :) 

This is one of the better (computer)forums I have been on.

---

### Post by bodhi.zazen on 2006-04-22
prezbedard:

Thank you for the clarification.

It now seems you are having a problem with compatibility problems with you video card, as has been suggested by Andrew-buntu.

I do not have the technical skills to be of much assistance. You should do a Google search on your video card and monitor. I have had problems with monitors and Ubuntu in the past, but the changes to xorg.config I gave to you have solved them for me.

Do you know your monitors vertical and horizontal refresh rates and did you put the correct values into the xorg.config?

You can also try running a command line to configure X. I am not sure of the command in Ubuntu. Try running:

  sudo xorgconfig

Or

  sudo dpkg-reconfigure xserver-xfree86

You will need technical details of your monitor. You will need to comb through a text based menu and select the driver for your video card. If it is not on the list Google (best compatible or download and install a driver). You will likely need to know how much memory is on your video card.

You should also consider installing Drake (Ubuntu 6.06 LTS - codenamed 'Dapper Drake'). Do not let the fact that it is a Beta scare you off. It is very stable. On a beta there may be small bugs, and updates occurr with some frequency. On the whole runs very smoothly.

I like your idea of a server install of Ubuntu and in fact may toy with the idea myself (I have been interested in minimal installs)

You may also consider switching to an alternate version of Linux. Try a Live CD (Knoppix or Mepis ?) and see if you can configure your video card from there.

Mepis Alpha runs off Ubuntu, but I am not sure it will give a server install. The hardware detection, howerver, is somewhat better then Ubuntu.

Zenwalk is based on Slackware, and seems to be a very functional minimal install. It defaults to XFCE (very nice desktop). KDE is easy to install. If you want gnome, you must download and install slapt-get (very easy, takes < 1 minute), add a repository for gnome (see [http://www.linuxpackages.net/](http://www.linuxpackages.net/) for details). Gnome then take an hour or so to download and install. You must then re-configure gdm (which is a bit of a hassle). This may be the kind of install your are seeking with less initial hassle.

I hope this helps, and most of all I hope you stay with Ubuntu. I have tried several distros and keep coming back to Ubuntu. I had video problems when I stated Ubuntu and learned how to fix my issues on other distros. As such I have returned to Ubuntu. Very helpful users on the Forums and up to date with releases, although I run Drapper Drake as it is more up to date then 5.x .

---

### Post by prezbedard on 2006-04-22
Thanks  bodhi.zazen.

Yes I did find and enter my monitor specs in the xorg.conf file.

I do know the the video card only has 1MB of memory.

I will follow your suggestions.

I had been reading that RH may be a better fit for the compaq proliant. It did have RH 7 when I inherited it. I did want to try ubuntu though aftere hearing so  about it.

Thanks again.

---

### Post by bodhi.zazen on 2006-04-22
Consider Fedora Core 5.  Not light, but very nice.

---

### Post by prezbedard on 2006-04-22
I did one more ubuntu attempt using the live 5.10 CD and got the same result of a blank screen.

---

### Post by Andrew-buntu on 2006-04-22
I looked around and didn't find a lot on that computer - but those proliants were shipped with linux so there must be a way to configure that card.  I poked around google and only found one person who had posted their xorg.conf.  They didn't post the whole thing but their device and screen sections looked like this:
```


Section "Device"
	Identifier  "Videocard0"
	Driver      "cirrus"
	VendorName  "Videocard vendor"
	BoardName   "Cirrus Logic GD544x"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     16
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Try replacing your own device and screen sections with that.  It looks as if that Cirrus card has its own driver so that's the one I'd work with.  Try going through dpkg-reconfigure xserver-xorg a few more times, adjusting to different resolutions and color depths.
I've had a few computers with uncooperative Xservers, too, and the solution usually involves forcing a specific resolution/color depth.
Can you post your xorg.conf?  I'd like to see what your display section looks like.

---

### Post by prezbedard on 2006-04-22
Thanks Andrew-buntu,

I'll give it a try. I did just do a live test of the beta 6.06 with same results but still have 5.10 installed.

---

### Post by prezbedard on 2006-04-22
I tried to mount the floppy and copy the xorg.conf. It seems to execute with no problem but the file is not on the disk.

---

### Post by prezbedard on 2006-04-22
What I don't get is why Ctrl-Alt-F1 doesn't work anymore to bring me back to a terminal after X doesn't work. It is a pain having to reboot everytime now.:evil:

---

### Post by Andrew-buntu on 2006-04-23
[QUOTE=prezbedard]What I don't get is why Ctrl-Alt-F1 doesn't work anymore to bring me back to a terminal after X doesn't work. It is a pain having to reboot everytime now.:evil:[/QUOTE]
What happens when you press Ctrl-Alt-Backspace?  That should kill the X server.
To keep X from starting, go into /etc/inittab and change the "default runlevel" from 2 to 1.  Then you won't have X starting itself if you forget to enter recovery mode:
```

# The default runlevel.
id:1:initdefault:

```
You can change the runlevel back to 2 when you have Xorg, gdm and gnome up and running.

Also, consider installing OpenSSH on your linux box.  It's very simple (sudo apt-get install openssh-server) and it'll let you gently reboot your machine if you get into X trouble.  Plus, you can use your linux box from any machine in the house, which is nice.  I use "putty" on Windows to connect.  Make sure you have a router with a firewall so the world can't log on.

Have you tried starting the computer with Knoppix yet?  Knoppix detects just about any old piece of hardware and if you can get that to find the proper resolution/depth settings you can just copy them down then write them into your xorg.conf.  And it never hurts to have a Knoppix CD around - download one from knoppix.org and give that a shot, too.

To get your xorg onto a floppy:
```

mount /dev/fd0 /media/floppy0
cp /etc/X11/xorg.conf /media/floppy0
umount /media/floppy0

```
You might have differently named drives so check that before you type.  Just "cd" into your /dev and /media folders and look for "fd" and/or "floppy"

I'll try to give you some more specific info when I see that xorg.conf.  Good luck!

---

### Post by prezbedard on 2006-04-23
I checked the /dev dir and there is nothing relating the floopy drive

so when I type 

mount /dev/fd0 /media/floppy0

it tells me fd0 doesn't exist and there doesn't seem to anything that would represent the floppy.

also what fs should I specify in the command? because it tells me  I must specify a fs type

---

### Post by prezbedard on 2006-04-23
ok it seems when I listed the contents of /dev at the local console it didn't show all devices since it was too much for the screen.

I got open ssh installed and used putty to get in. I got a better look at the /dev dir and saw a fd however I was told 

fd is not a block device

 when I attempted to mount the floppy.

---

### Post by Andrew-buntu on 2006-04-23
[QUOTE=prezbedard]ok it seems when I listed the contents of /dev at the local console it didn't show all devices since it was too much for the screen.

I got open ssh installed and used putty to get in. I got a better look at the /dev dir and saw a fd however I was told 

fd is not a block device

 when I attempted to mount the floppy.[/QUOTE]
 
Try fd0 rather than fd.  fd is the device, fd0 is the data.  If you need the type, it's vfat.  So you need to type:
```
mount -t vfat /dev/fd0 /media/floppy
```
if there's no "floppy" directory, you can make one with
```
sudo mkdir /media/floppy
```

---

### Post by prezbedard on 2006-04-23
ok when I did mount -t vfat /dev/fd0 /media/floppy

it tells me that 

special device /dev/fd0 does not exist

---

### Post by uzi09 on 2006-04-23
sorry, not sure if u mentioned or not (sorry, LOTs of reading ;))

did it EVER work for u?

if not, i'd recommend giving dapper a try (even the live cd) cuz i had a similar problem with my computer. breezy didn't support my vid card (nothin special, just the cpu based one)  and when i researched it, i ended up needing a program called 915 resolution. dapper has this by default, so i ended up switching.

the only thing is, my machine is fairly new, and urs i believe is fairly old right? i'd figure ubuntu should have been able to support that, but then again, u never know.

i'd def recommend givin dapper live a try.

good luck,
uzi

---

### Post by prezbedard on 2006-04-23
Thanks, I did give the live CD version of drapper and it was a no go.

---

### Post by Andrew-buntu on 2006-04-23
[QUOTE=prezbedard]ok when I did mount -t vfat /dev/fd0 /media/floppy

it tells me that 

special device /dev/fd0 does not exist[/QUOTE]

Hmm.  OK then, try fd again.  Do you have that /media/floppy folder already?

---

### Post by prezbedard on 2006-04-23
[QUOTE=Andrew-buntu]Hmm.  OK then, try fd again.  Do you have that /media/floppy folder already?[/QUOTE]


Yes I do have the /media/floppy

When I use

mount -t vfat /dev/fd /media/floppy

it reports

mount: /dev/fd is not a block device

---

### Post by Vignesh Sugumar on 2006-04-24
Hi
  This xserver problem can be solved quite simply if u are facing problem with ATI based graphics card. After u type the cmd, **sudo dpkg-reconfigure xserver-xorg**, u will proceed with typical OK settings to the coming configurations, but at the point it ask for graphics type DONT LEAVE ATI, _REPLACE ATI WITH VESA_, this would solve the problem.

Vignesh

---

### Post by prezbedard on 2006-04-24
[QUOTE=Vignesh Sugumar]Hi
  This xserver problem can be solved quite simply if u are facing problem with ATI based graphics card. After u type the cmd, **sudo dpkg-reconfigure xserver-xorg**, u will proceed with typical OK settings to the coming configurations, but at the point it ask for graphics type DONT LEAVE ATI, _REPLACE ATI WITH VESA_, this would solve the problem.

Vignesh[/QUOTE]

[QUOTE=Andrew-buntu]Hmm.  OK then, try fd again.  Do you have that /media/floppy folder already?[/QUOTE]


Its not an ATI card but a Cirrus Logic integrated into an old compaq proliant 1600.

---

### Post by steve.horsley on 2006-04-24
[QUOTE=prezbedard]Its not an ATI card but a Cirrus Logic integrated into an old compaq proliant 1600.[/QUOTE]

OK, so replace "cirrus" with "vesa" instead.

**sudo dpkg-reconfigure xserver-xorg** seems to be the standard way to fix up video problems, and vesa is a pretty-much standard driver that works with most things.

For the floppy, try this command:
**sudo modprobe floppy**
and then try to mount it as before. That command says to load the floppy driver module (if it's not already loaded).

---

### Post by prezbedard on 2006-04-24
[QUOTE=steve.horsley]OK, so replace "cirrus" with "vesa" instead.

**sudo dpkg-reconfigure xserver-xorg** seems to be the standard way to fix up video problems, and vesa is a pretty-much standard driver that works with most things.

For the floppy, try this command:
**sudo modprobe floppy**
and then try to mount it as before. That command says to load the floppy driver module (if it's not already loaded).[/QUOTE]


Thanks I'll give that a try tonight after work.

Not usre about the VESA since I did initially try that but I'll give it another go with the dpkg cmd.

Thanks

---

### Post by Andrew-buntu on 2006-04-24
Since Ubuntu made you a /media/floppy folder, maybe it gave you the correct entry in your /etc/fstab, too.  Put your formatted floppy in the machine and type: ```
 mount /media/floppy 
```
If that doesn't work, post your /etc/fstab file (it's short, just copy over the lines dealing with the floppy).
Are you using a formatted floppy?  If your floppy isn't formatted, then you won't be able to mount it.  Throw it in your windows machine (you are using a windows machine to post, right?) and make sure it is.

---

### Post by Zimmer on 2006-04-24
Personally, 1 meg of video ram does not sound enough. I have just junked an old PII system with an Orchid 3d card (HDD eventually failed) that was not happy with graphics and Linux.
I tried DSL and these Ubuntu versions.
[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)
[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)
The best was DSL, but no where near satisfactory in terms of speed and useability....

---

