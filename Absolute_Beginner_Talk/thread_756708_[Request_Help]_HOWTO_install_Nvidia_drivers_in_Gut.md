---
title: "[Request Help] HOWTO install Nvidia drivers in Gutsy Gibbon 7.10?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by MachineHead on 2008-04-16
Hello there Ubuntu users,

I'm a spoiled kid, raised with knowing nothing better than Windows operating system.
Because I like gaming, I need Windows, Cedega and Wine can't run what I play, so I have to.

I downloaded the installations I needed, the 7.10 Desktop, Alternate and Edubuntu *.iso's.
Burned them all to disk and tried the Desktop cd first, No Go!

I have 2 XFX Geforce 8600 GTS graphic cards, so they weren't picked up by the desktop cd.
Ok the Alternate cd then, I did that before ages ago with 7.04.

Problem is, Mr. Alberto Milone has stopped making guides?
I didn't try his guide for 7.04 yet, cause I'm working on another GPU issue in Windows atm.

So the question is:[INDENT]**Where are some good Nvidia Howto guides to install the drivers for 7.10 Gutsy Gibbon through console in the alternate installer?**

[/INDENT]I tried every combination of keywords I can imagine on both google and the forums and I came up with nothing really nice.
Praying for help.

-MachineHead

---

### Post by arochester on 2008-04-16
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by MachineHead on 2008-04-16
I edited the question mentioned in my first post.

Though your effort to help is much appreciated, it did not help me.
I can find good HOWTO files for the 7.04 distro, but none for 7.10.
The problem is that my hardware is not picked up by the desktop installer.
So I have to install the driver manually through console while installing from the alternate cd.

This means I need to know common commands to use to exit and start the X server.
I need to know how to get into the internet in console (can't remember how)
I need to download and install the driver.
And after that I can follow the Nvidia guide, yes.

-MachineHead

---

### Post by arochester on 2008-04-16
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) ... "These instructions are for Ubuntu 7.04 or later"

---

### Post by 3rdalbum on 2008-04-16
The 8600 is supported in the Restricted Drivers Manager (System > Administration > Restricted Drivers Manager) on Gutsy. If you get crashes, you should upgrade to the latest version. There's a program called Envy which can easily install the latest Nvidia drivers - you should check it out.

---

### Post by MachineHead on 2008-04-16
> **3rdalbum said:**
> The 8600 is supported in the Restricted Drivers Manager (System > Administration > Restricted Drivers Manager) on Gutsy. If you get crashes, you should upgrade to the latest version. There's a program called Envy which can easily install the latest Nvidia drivers - you should check it out.

Please guys do read my first post.
The problem is that I cannot get into X.
My system just blacks out.

> **arochester said:**
> [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) ... "These instructions are for Ubuntu 7.04 or later"

I really am thankfull for the effort, but without any GUI I can do jack with this guide.
Sorry mate, thanks for trying to help, might work for other folks though.

I'm on the following system:

AMD 6000+ 64 bit
4 GB RAM
2 x XFX Geforce 8600 GTS SLi

Wich means that with X searching for a nice vga video device, my Samsung 22 inch on DVI won't get any input.
Will it work to change it to VGA temporarily?
LoL! Nevermind, my GPU's and monitor don't have any VGA connections.

I need to install the drivers through console before I can do my first "GUI" login.
I have just been rambling around for an hour in the console with my old 7.04 notes that I used.

When trying to edit the X11/xorg.conf i find a blank file with nothing to edit.
Following the instructions on the Nvidia website, saying I better edit my inittab file to level 3 so I will boot into console automatically, gives me another blank file with nothing to edit.

I know of Envy, it is what I used before.
That is Alberto Milone's program, wich is supported until 7.04 as far as I know, does it work with 7.10 Gutsy?

If you know, please tell me:[INDENT]Command used to unlock the restricted drivers manager through concole.
Command used in 7.10 gutsy to edit the configuration files I need to edit through console.
Maybe some info on the proper use of the sudo / su command.
Command to run / find the package I downloaded with the drivers from the Nvidia website.
[/INDENT]I have the driver named:
NVIDIA-Linux-x86_64-100-14-06-pkg1.run
But I don't know how to navigate to that file and execute/run/unpack it through console.
If there was just a list of commands out there I would be fine I think :)

-MachineHead

---

### Post by arochester on 2008-04-16
See [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0) and/or [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) and/or [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) -  if all else fails choose Vesa as the driver

---

### Post by Winawer on 2008-04-16
Machinehead, I was recently in the same position as you - I'd accidentally borked my X11/GNOME and I couldn't get X to start at all.  I used Envy from the command line - just follow the instructions on the page to clean out the NVIDIA drivers and then reinstall.  It does it all from the command line with no trouble, and you don't have to go into X before it's done.

---

### Post by smurphy_it on 2008-04-16
The reason you got a blank file when trying to edit the xorg file from your post seems to be a wrong location (hence why it was blank).

in the terminal type sudo nano /etc/X11/xorg.conf

Su --> Switches to the root user and does everything as that user.... Can be a secuirty risk.

sudo --> perform a command(s) as the root user, then relinguish root access and swap back to normal user (much better to use).

Yes Envy is supported up to Hardy 8.04....

I belive Envy 7.10 and below uses the legacy driver, and hardy uses the new driver.

---

### Post by MachineHead on 2008-04-16
Hey there,

I just booked some nice succes on getting it all to work.
Here is what I did.

**Actions taken before driver install:**[LIST=1]
[*]Clean install from the Alternate cd "Ubuntu 7.10 Gutsy Gibbon AMD 64"
[*]Reboot after finishing installation.
[*]In the Grub menu, press arrow UP (To prevent Grub from auto-loading an OS)
[*]Read the instructions written under the Grub selection menu. 
Edit the second command line and remove the "quiet splash" addition to that rule.
[*]Boot Ubuntu normal.
[*]Wait until everything is finishing loading and flashing (text), then when you get the black screen and CPU + HDD are silent, press "CTRL + ALT + F1" to get to the console.
[*]Log in with your username and password to gain control over your session.
[*]Type the following command lines to update your current Ubuntu installation:
```
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo apt-get install -f
```[/LIST]If I'm right, and I honestly can't say I am 100% right, this should be enough to prepare your Ubuntu installation to proceed to installing Alberto Milone's *Envy* and install the driver through that program.

That is the easy part, now I will try and give you all the command lines I used to get to the part where I am now, still stuck but way better than before.[B]

Commands used to install the driver with Envy:[/B][LIST=1]
[*]Follow these command lines to install *links* a simple text based web browse utility, wich you need to download and install envy and the driver.

(NOTE: All this should be executed in a console, and is only neccessary in this way if you're X server won't boot with a nice GUI)

```
sudo apt-get install links
links www.albertomilone.com
```
[*]On the Alberto Milone website, browse to *"Projects"* then select *"Envy"* scroll down the page again untill you get a table with descriptions of version of the Envy program. Select the first option *"Envy Legacy"* and press 'ALT + F' to navigate to the LINKS section and download the *.deb file.
[*]After the download is complete press 'ALT + F' again and the X to close links.
[*]Type in your console:
```
dir  (just to find out if the envy *.deb package is in the folder you are navigating)
sudo dpkg -i envy_0.9.10-0ubuntu10_all.deb  (mind the zer0)
```
[*]You will think it failed, but it worked.
[*]Type in console to get the Envy text based console:
```
sudo envy -t
```
[*]Follow the program instructions carefully.[/LIST][B]The Final Stage:

[/B]This is it, the end of what I know now.
I have a black screen after reboot, but I do hear the Ubuntu drums, meaning Xserver booted allright.
When searching for solution I have seen the solution for this problem, but discarded it because it didn't seem related.

As soon as I find the solution to this one, I will update what I did to overcome the problem.
[B]
Links to webpages:[/B]

[http://www.albertomilone.com]("http://www.albertomilone.com/")
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)


-MachineHead

p.s. Thanks all for directing me around to guides, howto's and other threads, they were part of the puzzle.

---

### Post by stchman on 2008-04-16
> **MachineHead said:**
> Hello there Ubuntu users,

I'm a spoiled kid, raised with knowing nothing better than Windows operating system.
Because I like gaming, I need Windows, Cedega and Wine can't run what I play, so I have to.

I downloaded the installations I needed, the 7.10 Desktop, Alternate and Edubuntu *.iso's.
Burned them all to disk and tried the Desktop cd first, No Go!

I have 2 XFX Geforce 8600 GTS graphic cards, so they weren't picked up by the desktop cd.
Ok the Alternate cd then, I did that before ages ago with 7.04.

Problem is, Mr. Alberto Milone has stopped making guides?
I didn't try his guide for 7.04 yet, cause I'm working on another GPU issue in Windows atm.

So the question is:[INDENT]**Where are some good Nvidia Howto guides to install the drivers for 7.10 Gutsy Gibbon through console in the alternate installer?**

[/INDENT]I tried every combination of keywords I can imagine on both google and the forums and I came up with nothing really nice.
Praying for help.

-MachineHead

I have an 8800GT on a Feisty machine and it works well.  I used Envy 0.9.10 and did a manual install and selected the 169.12 driver.  Before you install make sure you completely uninstall any Nvidia driver.  Envy will do it for you as there is an option.

I do not know if the Linux Nvidia driver supports SLI.  I would imagine it would.

Don't be diappointed if Ubuntu does not run all your DX9/DX10 Windows games.  I have WINE installed and it can run some older games but the new stuff is pretty much a no go for me.  I have not immersed myself into getting new games to run under WINE since I have both XP and Vista as a triple boot.

I just get sick of people bashing Linux saying they cannot run their Windows apps flawlessly.  Linux was made to run Linux apps.  The fact that it runs ANY Windows apps is surprisinf as XP does not run Linux apps.

I recommend you keep XP or Vista and dual/triple boot.  Use Ubuntu for everything else and M$ for games.

---

### Post by MachineHead on 2008-04-16
Hey Stchman,

That's my intention.
Do all my browsing, homework, movies/audio, all of it on Ubuntu, and Game on a Windows platform.

But first I need it to work ;)
Check my last post, I'm almost there.
Do you have a tip for that final horde?

[B][Edit]
Well I got Ubuntu up and running...
The Solution?
Download the new BETA release 8.04 and install.
I used the Desktop installer on my pc, no need for alternate, everything smooth as a whistle.
3 hurrays for the dev team that made this hardware support possible.
This will be the downfall of M$ one day :D
[/Edit][/B]


-MachineHead

---

### Post by JoCoProductions on 2008-05-02
I'm having this EXACT same problem, the only thing is now I am in ubuntu because I edited xorg and added vesa drivers which worked. But If I enable the restricted drivers, it brings me back to the black screen (of death). And if I use Envy NG to install the drivers it outputs this as an error:

```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

---

### Post by MachineHead on 2008-05-02
Hey JoCoProductions,

I didn't get any errors except for the black screen persisting.
Though this isn't really an error, and I think it is more related to my crappy console work.
My best suggestion is do what I did JoCo, download the new release and install it.
No need for the alternate cd, just get the desktop one.
Mine is still up and running and no errors, mistakes or lock-ups untill now.
Fragging awesome!


[echo]Is there an expirienced user out there to correct us in this thread?
Yes we know the new version is out and that it works, but still there will be people out there using the 7.10 release and it would be awesome to complete this HOWTO.
[/echo]

-MachineHead

---

### Post by JoCoProductions on 2008-05-02
The thing is I am getting this problem with the NEW 8.04 distrobution. I couldnt install witht he livecd due to graphical problems (again), but using the alternate CD it worked just fine. Just to be clear I am getting a blank idle screen just where the login should be unless I edit my xorg beforehand to add vesa drivers.

---

### Post by MachineHead on 2008-05-03
Hey again,

Are you using the same GPU's as I am?

-MachineHead

---

### Post by JoCoProductions on 2008-05-04
Im using an Nvidia Geforce 6800

---

### Post by MachineHead on 2008-05-04
Hey JoCo,

Then that cannot be the problem you are encountering I would say.
Because I'm running 2 XFX Geforce 8600 GTS cards.
I don't know if you have Ubuntu installed at the moment so try either of these things:


[LIST=1]
[*]At the boot splash of the GRUB screen, press arrow UP (To prevent Grub from auto-loading an OS)
Read the instructions written under the Grub selection menu. 
Edit the second command line and remove the "quiet splash" addition to that rule.
[/LIST]
This will allow you to see any errors while loading Ubuntu.
If you still have to install Ubuntu, you can do the same at the moment you enter the splash screen of the desktop or alternate cd.
You have to press one of the F keys and then you can remove "quiet splash" there to see errors.
Can't remember wich F key it was, so good luck on trying them ^^.

With the information on the error provided (should you find any) you can open another thread and ask for help specificly on that issue.

-MachineHead

---

### Post by bobblehat on 2008-05-07
Thanks folks. This thread helped.

My problem was on an install of 7.10 Gutsy AMD64 Desktop. I could boot to root prompt (recovery mode) then start x manually fine. If I booted as a normal user I just got the black screen and the Ctrl-Alt-F1 combination didn't seem to work for me. Two fixes both worked in the end:

I edited grub as above to remove quiet splash and I could get a non-root prompt that way, then configure and start x manually. Worked fine.

I also tried Hardy and that went on fine with no problems.

---

### Post by MachineHead on 2008-05-07
Hey Bobblehat,

Good to hear, cheerio :KS

If you can let us know what hardware you use, it can be helpfull to others aswell.
There was a special Hardy thread to create a hardware support list but I can't remember where it is located.

I'm running on a:

AMD Athlon x64 6000+
MSI K9N SLi Platinum
XFX Geforce 8600 GTS (2 in SLi)
4 GB RAM 800 Mhz (Corsair C4)

Some little list like that can really add up to the value of this thread, so other people can compare and single out errors encountered if their hardware is or isn't supported.

Thanks for the compliment on the thread.

Cheers,

-MachineHead

---

