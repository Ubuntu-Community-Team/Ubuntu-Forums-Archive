---
title: "Starting without GUI"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-26
Is there a way I can start the computer without the GUI? just terminal view...

And in te same idea...
Where can I get Terminal programs? I mean, is there a mail client or something?
I've got the browser, curretly using Elinks... but what about other stuff?

Thanks...
Josh

---

### Post by gondilon on 2006-04-26
to start without the GUI, choose recovery mode in ubuntu.  AS for getting terminal programs, you shoud be able to use synaptic.

---

### Post by Ensnared on 2006-04-26
If you want to have the option to start without a GUI, you need to define a runlevel that won't start GDM or KDM. Or you could set it up to not start any of them in the default runlevel if you don't need the option of starting with a GUI.

You can do it like this:
```
sudo apt-get install sysv-rc-conf
```This will install a command-line tool to edit the runlevel startup-scripts. Run it as root:```
sudo sysv-rc-conf
```Use the arrow-keys to move around. Go to the column labeled "2" (which is the default, and probably your current, runlevel). Move down until you find GDM or KDM, and hit spacebar to remove the X in the box. This will make them not start up when the computer boots in runlevel 2. The changes you make are saved automatically, so just hit q to exit.

If you want it optional the the GRUB menu instead (like I've set up), you do the same but you remove GDM/KDM for another runlevel than 2 (I use 3 for this myself). You can use any of them except for 0, 1 and 6 as they are pre-defined (0=halt, 1=single-user, 6=reboot).
Then you do this:```
sudo nano -w /boot/grub/menu.lst
``` ...or use your preferred editor if you don't like nano. Locate the line that looks like this:```
# altoptions=(recovery mode) single
```Add the following line before or after it (depending on which order you want them to show up in the bootmenu)```
# altoptions=(textmode) init 3
```
Replace "textmode" with "no GUI" or whatever you want the label to be. Save and exit (ctrl-x followed by y and enter in nano), and update the bootloader menu:```
sudo update-grub
```Next time you boot, all your kernels will have 3 options in the menu - regular (unlabeled), textmode and recovery mode.

As for terminal-apps, there are heaps of them. I don't like them much myself as I prefer GUI for these kinds of things (e.g. mail, web, usenet, etc), but mutt is a very popular mail-client, as is pine (although that may not be available as it's got a different license). A good place to start searching is [Freshmeat](http://www.freshmeat.net/).

---

### Post by kabus on 2006-04-26
some terminal programs :

screen - terminal multiplexer, a bit like firefox tabs for the comand line
mutt - mail client
irssi - irc client
slrn - newsreader
snownews - rss reader
mc - file manager
vim - text editor
mplayer - movie player
mpd / ncmpc - music player

all available from the repositories.

---

### Post by Caligula on 2006-04-26
Thanks guys...
I managed to start without the GUI, but I've got some difficulties with the programs...

When I was installing pdm it came up with an error message "PDM system not installed", I then installed that other ncmpc, but when I try to type "ncmpc" in the terminal is says it can't find localhost or something.. (WHAT??)

I also can't figure out how to configure mutt to my POP and SMTP servers...
oh, and the irc client didn't install... is it in multiverse?

I also can't figure out how to use "screen"...

Thanks, anyway...
Josh:) ](*,)

---

### Post by Caligula on 2006-04-26
MPD, not PDM...

---

### Post by kabus on 2006-04-26
[QUOTE=Caligula]I then installed that other ncmpc, but when I try to type "ncmpc" in the terminal is says it can't find localhost or something.. (WHAT??)
[/QUOTE]

Oops, my fault. I didn't make clear that ncmpc is a client for mpd (music player daemon), so you need to have that running first. 
If you prefer a standalone music player you could try moc or mp3blaster.

[QUOTE=Caligula]
I also can't figure out how to configure mutt to my POP and SMTP servers...
[/QUOTE]

Mutt doesn't do that, it leaves those tasks to specialised apps.
Setting up mutt for the first time is a bit of a hassle, but it is worth it. 
Here's some guides :

[http://mutt.blackfish.org.uk/](http://mutt.blackfish.org.uk/)
[http://home.nyc.rr.com/computertaijutsu/mutt.html](http://home.nyc.rr.com/computertaijutsu/mutt.html)

[QUOTE=Caligula]
I also can't figure out how to use "screen"...
[/QUOTE]

Some beginner tutorials :

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

I know, a lot of these apps might look cumbersome and overly difficult, but once you have figured them out you'll never want to use anything else again :-D

---

### Post by Caligula on 2006-04-26
thanks, it's getting easier now...
I installed both moc and mp3blaster, but does mp3blaster play ogg files? I'm not using mp3...

Moc just doesn't start... i type "moc", and it just doesn't do anything, i mean, it shows as if it's waiting, but it doesn't launch...

I'll read the manuals for Mutt, thanks:)

---

### Post by kabus on 2006-04-26
[QUOTE=Caligula]thanks, it's getting easier now...
I installed both moc and mp3blaster, but does mp3blaster play ogg files? I'm not using mp3...

Moc just doesn't start... i type "moc", and it just doesn't do anything, i mean, it shows as if it's waiting, but it doesn't launch...

I'll read the manuals for Mutt, thanks:)[/QUOTE]

Mp3blaster can play ogg, as far as I know.
Don't know what the problem with moc could be.

---

### Post by Caligula on 2006-04-26
Succes!
I'm listening to Elton John from the Terminal... haha:D :D 

Though I don't have much succes with fetchmail, getmail or anything of that sort...

---

### Post by rov on 2007-11-15
> **Ensnared said:**
> If you want to have the option to start without a GUI, you need to define a runlevel that won't start GDM or KDM. Or you could set it up to not start any of them in the default runlevel if you don't need the option of starting with a GUI.

You can do it like this:
```
sudo apt-get install sysv-rc-conf
```This will install a command-line tool to edit the runlevel startup-scripts. Run it as root:```
sudo sysv-rc-conf
```Use the arrow-keys to move around. Go to the column labeled "2" (which is the default, and probably your current, runlevel). Move down until you find GDM or KDM, and hit spacebar to remove the X in the box. This will make them not start up when the computer boots in runlevel 2. The changes you make are saved automatically, so just hit q to exit.

If you want it optional the the GRUB menu instead (like I've set up), you do the same but you remove GDM/KDM for another runlevel than 2 (I use 3 for this myself). You can use any of them except for 0, 1 and 6 as they are pre-defined (0=halt, 1=single-user, 6=reboot).
Then you do this:```
sudo nano -w /boot/grub/menu.lst
``` ...or use your preferred editor if you don't like nano. Locate the line that looks like this:```
# altoptions=(recovery mode) single
```Add the following line before or after it (depending on which order you want them to show up in the bootmenu)```
# altoptions=(textmode) init 3
```
Replace "textmode" with "no GUI" or whatever you want the label to be. Save and exit (ctrl-x followed by y and enter in nano), and update the bootloader menu:```
sudo update-grub
```Next time you boot, all your kernels will have 3 options in the menu - regular (unlabeled), textmode and recovery mode.

As for terminal-apps, there are heaps of them. I don't like them much myself as I prefer GUI for these kinds of things (e.g. mail, web, usenet, etc), but mutt is a very popular mail-client, as is pine (although that may not be available as it's got a different license). A good place to start searching is [Freshmeat](http://www.freshmeat.net/).

i have xubuntu 7.10 installed.  seems the old /etc/inittab was replaced with upstart, which must be better b/c it's MUCH more complicated.  as far as i can tell, runlevels don't exist in upstart.  what i'm trying to do is set the boot menu to give me 2 choices (in addition to recovery and memtest) 1) full session without graphics (old runlevel 3 i think) and 2) full session WITH graphics (old runlevel 5).

would the approach you outlined above work with upstart replacing /etc/inittab??

thx,rov

---

### Post by tim_phillips on 2007-12-29
rov - i am trying to do exactly the same thing. have you found a way to do it (have a grub option to boot to multiuser with network and all services but just CLI not gnome)? the approach given by Ensnared doesn't seem to work on 7.10 - it just boots to gnome as per usual.

??

---

### Post by airtonix on 2008-01-02
The screen program sort of implements virtual workspaces for the CLI.

and doesnt quit session if you where to be running it on a remote computer via ssh, and be unlucky to have a net-dissconnect or power outage.

---

