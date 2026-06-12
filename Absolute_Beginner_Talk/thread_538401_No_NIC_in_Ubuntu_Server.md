---
title: "No NIC in Ubuntu Server"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by RobUK on 2007-08-29
Hi all,

I'm an absolute newbie with Linux, so pardon me if this is a dumb question.

I have a small Windows based workgroup, sharing my broadband connection via a router - all wired, no wireless. I've been toying with the idea of running a local web / database server for quite a while, and after a little reading around, thought that Ubuntu server looked like a good move. So I've downloaded the latest version and installed it on an old PIII 600 / 128Mb RAM / 13Gb HDD - installation got off to a rough start because the CD wasn't prepared to boot properly from either of the drives in the system, but a BIOS upgrade sorted that out.

However, the installation routine didn't pick up on the nic I'd just installed in the machine - it's a Sweex LancardPCI, based on the RTL8139 series. According to ifconfig, only the local loopback is available.

The card's Linus Readme says:

"Check the directory " /lib/modules/¡K./net " if you could find "rtl8139.o" Your kernel had supported RTL8139 series. You could easy use "linuxconf" to setup your card. If you don't like linuxconf, you also could use "modprobe rtl8139" and "ifconfig up eth0" to load module. If your driver load properly, your "/etc/conf.modules" should include
line of "alias eth0 rtl8139"."

I can't find that directory, but I undestand that different distributions might put things in different places - where do I look for it under Ubuntu Server? And even if I could find it, the instructions are a little vague.

Am I right in thinking I'll have to edit /etc/network/interfaces somewhere along the line?

Any suggestions on getting this nic up and running would be much appreciated, as would any comments on whether the PC is poweful enough to run LAMP effectively.

TIA

Rob.

---

### Post by dwhitney67 on 2007-08-30
Did you try the modprobe?  The instructions you are reading could have been written a little better, but this is what it is trying to say:

First, try loading the kernel driver using the following command:

[FONT="Courier New"]$ sudo modprobe rtl8139[/FONT]

Then the instructions say that if that command succeeds, then to attempt to bring up your eth0 ethernet connection using this command:

[FONT="Courier New"]$ sudo ifconfig eth0 up[/FONT]

Hopefully if this works, then you can verify your IP address running this command:

[FONT="Courier New"]$ sudo ifconfig eth0[/FONT]

If all is well, then insert the following string, "alias eth0 rtl8139", into the file /etc/modules using this command to launch the editor:

[FONT="Courier New"]$ gksudo gedit /etc/modules[/FONT]

This will ensure that the kernel driver is loaded each and every time you reboot so that you do not have to repeat the steps above.

I hope the info above enlightens you and is helpful.

P.S.  If you do succeed in obtaining an IP address from your router, you can also test your ethernet connection by running a simple command like:

[FONT="Courier New"]$ ping [www.google.com](www.google.com)[/FONT]

---

### Post by chuckyp on 2007-08-30
This nic should work natively if thats the chipset.  Perhaps you just need to configure it?
```

sudo ifconfig eth0

```

The interfaces file you are talking about is for configuring the nic on boot.

---

### Post by dwhitney67 on 2007-08-30
Rob,

I should have mentioned earlier... the 128MB of RAM you have in your system is on the low side.  Ubuntu recommends at least 256MB.

Consider installing a light-weight "Ubuntu" system, a.k.a. Xbuntu, which runs the XFCE window manager in lieu of Gnome (which is in Ubuntu) or KDE (which is in Kbuntu).

Everything else should be transparent as far as services (HTTPD, SSHD, MySql Server, etc) are concerned regardless of what distro you choose.

---

### Post by hyper_ch on 2007-08-30
> **dwhitney67 said:**
> Rob,

I should have mentioned earlier... the 128MB of RAM you have in your system is on the low side.  Ubuntu recommends at least 256MB.

Consider installing a light-weight "Ubuntu" system, a.k.a. Xbuntu, which runs the XFCE window manager in lieu of Gnome (which is in Ubuntu) or KDE (which is in Kbuntu).

Everything else should be transparent as far as services (HTTPD, SSHD, MySql Server, etc) are concerned regardless of what distro you choose.

He did a server install and not a GUI one ;) so 128 are sufficient...

---

### Post by RobUK on 2007-08-30
Thanks for the replies, folks.

I tried:

```
$ sudo modprobe rtl8139
```

and got FATAL: module rtl8139 not found.

In the meantime, I'd been doing some further reading, and found this thread, which seemed as though it might be useful:

[http://ubuntuforums.org/showthread.php?t=462878&highlight=8139+irqpoll](http://ubuntuforums.org/showthread.php?t=462878&highlight=8139+irqpoll)

I've followed the suggestions:

```
sudo modprobe 8139too
ifconfig eth0
```

Modprobe didn't return anything, just dropped me back to the prompt, so I assume it's done something? But ifconfig eth0 gives me: error fetching interface information: Device not found.

I also tried:

```
sudo modprobe 8139cp
dmesg | grep 8139
ifconfig
```

Again modprobe dropped me back to the prompt, dmesg ... gave me:

[31593.260000] 8139too Fast Ethernet driver 0.9.28
[32517.100000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

And ifconfig again just gave me the local loopback.

I've tried moving the card to another slot, too, and then done all of the above again. I'm tempted to just use another card (I can probably scavenge one from another maching) but I don't like to give up on things:-)

Any further suggestions would be much appreciated!

Rob.

---

### Post by dwhitney67 on 2007-08-30
Slap (insert) the module name, 8139too, into the **/etc/modules**.  The entry should be on a separate line and look like the following:

[FONT="Courier New"]alias eth0 8139too[/FONT]

After you save the file, reboot and see if the Ethernet is up/running.

P.S.  When modprobe succeeds, it does not return (echo) anything to the terminal.  When it fails, then it does.  So it was normal for the prompt to appear immediately after the module was loaded.

---

### Post by RobUK on 2007-08-30
Thanks for that. Unfortunately, it didn't help - ifconfig still shows just local loopback :-(

The offending nic is a Sweex LA000030, if that helps at all.

Rob.

---

### Post by dwhitney67 on 2007-08-30
Please run the following command and post what the output is:

[FONT="Courier New"]$ lspci -n | grep 8139[/FONT]

I want to make sure it is not this type of NIC:  see this [post]("http://lists.samba.org/archive/linux/2006-August/015771.html").

Also, for grins, replace the 8139too with the 8139cp in the /etc/modules file and reboot.

Btw, I know you find it interesting to troubleshoot this problem, but if it proves to much, there are many inexpensive NICs that work well with Linux right out of the box.  In the US these run about $10 if not less.

---

### Post by RobUK on 2007-08-30
I'm starting to think you might be right about replacing the nic!

I replaced 8139too with 8139cp and rebooted - no difference.

$ lspci -n | grep 8139

didn't return anything at all.

$ lspci on its own listed just the following:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/BX Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0b.0 Communication Controller: Rockwell International HSF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
00:0d.0 Multimedia audio controller: ESS TEchnology ES1969 Solo-1 Sudiodrive (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

No sign of any nic - I wonder if the pesky card is dead? It shouldn't be, given that it's brand new, straight out of the box, but since it's not listing...?

Rob.

---

### Post by dwhitney67 on 2007-08-30
I would just replace the card.  Be thankful that you are not dealing with an integrated chip-set within a notebook PC.

---

### Post by RobUK on 2007-08-30
Ohhh I am!

I pulled the card and replaced it with an 8139C that I just scavenged out of a dead PII box.

lspci now shows the card, so I put 8139too back into /etc/modules and rebooted.

ifconfig eth0 now shows info for the card, and doing

sudo dhclient eth0

gets me an IP address and I can ping [www.google.com](www.google.com) :-)

Many thanks for your help in getting this far, it's much appreciated! Am I right in thinking that the next step is to edit /etc/network/interfaces in order to give it a static IP?

Rob.

---

### Post by dwhitney67 on 2007-08-30
Doing the static IP is helpful if you reboot your system often an there are other systems on your LAN (that are also rebooted).

Here's the instructions that are applicable to Fedora Core.  I'm sure it is very similar for Ubuntu.

[PHP]Go to System Settings --> Network

Edit the eth0 interface and deselect DHCP. Modify as necessary with IP, gateway, and DNS info. Then restart the interface.[/PHP]

Btw, congrats on getting the Ethernet connection up an running.  I bet you wish you had swapped cards long ago.

---

### Post by RobUK on 2007-08-30
Cheers for that. I've also been reading [http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm) in an attempt to get my head around networking from the Linux point of view.

Since I'm aiming for this thing to run as a local web and database server (got a LOT of reading to do before I get to that point!) and maybe some other little tasks too, static seems like a good plan.

Anyhow, I've assigned it a static IP, rebooted to make sure everything stays put, pinged out to google and pinged in from my Windows box - looks like I'm in business!

Many, many thanks for you help on this, it's much appreciated.

No doubt I'll be back with more dumb questions as I start to feel my way through the Linux world :-)

Rob.

---

### Post by dwhitney67 on 2007-08-30
No problem.  If you ever have a problem or need ideas on how to setup something under Ubuntu, I have found this [site]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") very helpful.  I recommend that you bookmark it.

---

