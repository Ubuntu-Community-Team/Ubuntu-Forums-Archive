---
title: "Fedora 19 Beta - Issues with trackpoint and brightness controls. Eh?"
date: 2013-06-23
forum: Any Other OS
---

### Post by Roasted on 2013-06-23
Hi there. Long time Ubuntu user here trying out Fedora 19 beta so far and absolutely loving it. Only hangup I'm having so far is with my brightness keys, which were an issue on any distro I've tried so far. I ended up finding out some information via Arch's wiki/forums and used that alteration in my grub file, which was basically this here (this is what I put in Ubuntu to get it to work):

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""

For what it's worth, here's my full grub file from a working Ubuntu install - [http://pastebin.com/jwdPG0Ei](http://pastebin.com/jwdPG0Ei)

Then just update-grub and reboot and it was fine. I'm having some difficulty here doing that as for one, the grub file looks different than what I'm used to. Secondly, update-grub is not a valid command. What is the equivalent to update-grub in Fedora? Can anybody make sense of the !Windows 2012 entry and how I would apply it?

Also, on this Lenovo I have the usual layout for trackpad/keyboard with the touchpoint and two sets of buttons. The trackpoint buttons are a total of 3... left, middle, right click. If I would hold the middle down before and press up/down on the trackpoint, it would scroll. Here on Fedora 19, it won't scroll. Is there a way to enable that functionality?

I found some other sources with people having issues, although they were slightly different than mine. Some users suggested that you need to add your parameter within GRUB_CMDLINE_LINUX="". On Ubuntu, I had to put it within GRUB_CMDLINE_LINUX_DEFAULT="", but I did not see that in Fedora. So I ended up altering the GRUB_CMDLINE_LINUX="" line so it looks as follows:

GRUB_CMDLINE_LINUX="rd.md=0 rd.lvm=0 rd.dm=0 vconsole.keymap=us $([ -x /usr/sbin/rhcrashkernel-param ] && /usr/sbin/rhcrashkernel-param || rd.luks=0 vconsole.font=latarcyrheb-sun16 rhgb quiet acpi_osi=\"!Windows 2012\""

Everything else was in there except the acpi_osi=\"!Windows 2012\""

Then afterwards, I ran what seems to be the equivalent of update-grub, which is grub2-mkconfig -o /boot/grub2/grub.cfg. Even still, upon rebooting I had nothing. If I press brightness down, it shoots down to 0 instantly in the meter, however my brightness level doesn't actually change. If I press brightness up, suddenly the brightness jumps to 1% and stays there until I reboot. 

In regard to my trackpoint scrolling, I found this link here:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

which was to hold the answers to getting my trackpoint to work. I ran the 3 commands manually in the main vertical scrolling box and they worked perfectly. Problem is I cannot get them to automatically start when I log in. It said to put them in .xsessionrc but I'm questioning if Fedora uses .xsessionrc. A quick Google brought up .Xclients as an alternative suggestion, but the link looked old, so I wasn't sure how applicable it was to modern times with versions like F19. What does F19 use in terms of .xsessionrc or something similar so I can paste in these trackpoint commands and have my vertical trackpoint scrolling working?

---

### Post by Toz on 2013-06-23
Moved to ***Other OS/Distro Support***.

Not a fedora user, but the addition of acpi_osi=\"!Windows 2012\" is correct in the grub entry. You should be able to verify whether it is being used by:
```
cat /proc/cmdline
```

---

### Post by Copper Bezel on 2013-06-23
Are you using the Gnome desktop? (It looks like that's the default for Fedora 19.) I can't help with the low-level stuff, but getting the trackpoint configuration to be set on login isn't too difficult under Gnome. If you install dconf-tools and run dconf-editor, you can navigate down the tree on the left to org.gnome.settings-daemon.peripherals.input-devices, where there's a key called "hotplug-command." It takes a string, which is a path to a script that runs every time you log into the computer or wake it up from suspend. You can create a script with your xinput commands (say, ~/.xinput.sh) and put that path in the key (like /home/[username]/.xinput.sh.) I have a script set up this way to configure my trackpad (specifically, "natural" and horizontal scrolling that I can't set elsewhere) and so far as I know, it's the best way to configure those non-persistent input settings (like xinput, xmodmap, and synclient.)

(There's a terminal command for setting strings in dconf, which would make this simpler, but every time I try it with this string, it adds a space at the start and the command doesn't run.)

---

### Post by Roasted on 2013-06-23
> **Toz said:**
> Moved to ***Other OS/Distro Support***.

Not a fedora user, but the addition of acpi_osi=\"!Windows 2012\" is correct in the grub entry. You should be able to verify whether it is being used by:
```
cat /proc/cmdline
```

This is what returned when I ran that command:

[jsauders@localhost ~]$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.9.6-301.fc19.x86_64 root=UUID=b51b0a85-9323-451f-be2a-6c6dc75e5283 ro rd.md=0 rd.lvm=0 rd.dm=0 vconsole.keymap=us rd.luks=0 vconsole.font=latarcyrheb-sun16 rhgb quiet "acpi_osi=!Windows\x202012" LANG=en_US.UTF-8

Also, I should have specified, the grub I posted in the pastebin is from my Lenovo on a working Ubuntu GNOME setup. This is what it is under Fedora:

[http://pastebin.com/P1xsrg7u](http://pastebin.com/P1xsrg7u)

I just wasn't sure what exactly to do since GRUB_CMDLINE_LINUX_DEFAULT= didn't exist on Fedora... 


> **Copper Bezel said:**
> Are you using the Gnome desktop? (It looks like that's the default for Fedora 19.) I can't help with the low-level stuff, but getting the trackpoint configuration to be set on login isn't too difficult under Gnome. If you install dconf-tools and run dconf-editor, you can navigate down the tree on the left to org.gnome.settings-daemon.peripherals.input-devices, where there's a key called "hotplug-command." It takes a string, which is a path to a script that runs every time you log into the computer or wake it up from suspend. You can create a script with your xinput commands (say, ~/.xinput.sh) and put that path in the key (like /home/[username]/.xinput.sh.) I have a script set up this way to configure my trackpad (specifically, "natural" and horizontal scrolling that I can't set elsewhere) and so far as I know, it's the best way to configure those non-persistent input settings (like xinput, xmodmap, and synclient.)

(There's a terminal command for setting strings in dconf, which would make this simpler, but every time I try it with this string, it adds a space at the start and the command doesn't run.)

Yes, I am going to use Gnome. I know I can set up my own script and even tag it to startup applications, but before I did that I wanted to ask because I wasn't sure if there was a reason .xsessionrc was not working. I assumed there was an equivalent to Fedora that I just didn't know about.

---

### Post by Toz on 2013-06-23
> **Roasted said:**
> This is what returned when I ran that command:

[jsauders@localhost ~]$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.9.6-301.fc19.x86_64 root=UUID=b51b0a85-9323-451f-be2a-6c6dc75e5283 ro rd.md=0 rd.lvm=0 rd.dm=0 vconsole.keymap=us rd.luks=0 vconsole.font=latarcyrheb-sun16 rhgb quiet [COLOR="#FF0000"]"acpi_osi=!Windows\x202012"[/COLOR] LANG=en_US.UTF-8

That doesn't look right. Not sure what fedora is doing. Can you try this version instead (single quotes instead of \"):
```

GRUB_CMDLINE_LINUX="rd.md=0 rd.lvm=0 rd.dm=0 vconsole.keymap=us $([ -x /usr/sbin/rhcrashkernel-param ] && /usr/sbin/rhcrashkernel-param || rd.luks=0 vconsole.font=latarcyrheb-sun16 rhgb quiet acpi_osi='!Windows 2012'"
```

After reboot, post back again the results of:
```
cat /proc/cmdline
```

---

### Post by Roasted on 2013-06-23
Well look what we have here:

[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=950760](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=950760)

Guess I'm not the only one!

I'm back on Ubuntu GNOME now. I'll stay here for now. I'll spin up a Fedora 19 install on another drive. For some reason saving the partition via Clonezilla and restoring it didn't fly. Ubuntu GNOME came up with grub rescue screen when I dumped that image back over Fedora. Not sure what happened. For now I'll kick it here and I'll check out Fedora into the future when I receive word this bug was fixed.

In other news, Ubuntu GNOME is pretty awesome. I'm running the Gnome 3 and Gnome 3 Staging PPA and having some decent success with it. No major complaints. :D

---

### Post by Copper Bezel on 2013-06-23
> **Roasted said:**
> Yes, I am going to use Gnome. I know I can set up my own script and even tag it to startup applications, but before I did that I wanted to ask because I wasn't sure if there was a reason .xsessionrc was not working. I assumed there was an equivalent to Fedora that I just didn't know about.
Ah. I'm silly. I thought .xsessionrc was an X thing, rather than an Ubuntu-specific thing. I'm running into the same thing about .Xclients in Fedora and can't find anything current, either. 

In general, though, it's better to handle these things through the DE, since the DE can unset your carefully-set settings with its own defaults. Even running a script from startup applications doesn't completely remove that risk.

---

### Post by Roasted on 2013-06-24
> **Copper Bezel said:**
> Ah. I'm silly. I thought .xsessionrc was an X thing, rather than an Ubuntu-specific thing. I'm running into the same thing about .Xclients in Fedora and can't find anything current, either. 

In general, though, it's better to handle these things through the DE, since the DE can unset your carefully-set settings with its own defaults. Even running a script from startup applications doesn't completely remove that risk.

With that said, are you still in the same boat of confusion in terms of Xclients vs xsessionrc? Neither work for me, and I'm not sure why... I'd love to use the "proper" method but if it don't work, what else can ya do? :P

---

### Post by AdamWill on 2013-06-27
Interesting bug, but I just added a comment which may help in practical terms: you should be able to just put the correct form of the kernel parameter directly into grub2.cfg. Because of how Fedora handles kernel updates, changes you make directly in grub2.cfg won't be lost on install of a new kernel.

---

### Post by Roasted on 2013-07-09
On my other partition I put Ubuntu GNOME 13.10 alpha. I noticed it did not need any adjustments in order for my brightness keys to work. They simply worked out of the box. Ubuntu GNOME 13.10 is running kernel 3.10. Fedora is currently on 3.9.9, but I'm sure 3.10 will be down the pipe soon. With that said, I wonder if that frustrating bug will be negated completely with the introduction of 3.10. I can only hope this is a true 3.10 kernel feature and not some Ubuntufied fix that works out of the box on *buntu systems but not on other 3.10 distros, like what will soon be Fedora 19. I'd imagine it came from the kernel though, given the magnitude of upgrades 3.10 is bringing to the table.

I'm finding myself at a crossroads of which distro to use. Ubuntu GNOME 13.04 with the Gnome3 PPA seems to have broken Exchange integration. 13.10 and Fedora 19 meanwhile work 100%. Calendar, email, etc., all work great in Evolution, which I think is a first that everything worked so easily with Exchange integration since I've been on Linux.

Do I use a seemingly stable alpha and enjoy the bells and whitles of the *buntu base with the PPA system and super easy restricted drivers installation? Or do I use Fedora 19, a stable bleeding edge distro that should do the job fine as well, but with admittedly a little more interaction for certain things?

Good thing I set up two root partitions, one for each OS. We'll see what happens. ;)

---

