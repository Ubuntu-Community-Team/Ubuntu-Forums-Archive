---
title: "Linksys 100TX install problem"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by tblehr on 2006-02-01
Ok, so i'm a huge Linux noob with Windows burned into my memory forever!  :-D 
So I got Ubuntu installed fine.  I got my video card, screen res, sound, and my basic stuff setup easily using different forum guides.

Now, i'm trying to get Ubuntu to recognize my Linksys 100TX so I can setup internet sharing in my apartment.  It does regonize it's there, but it says its a NC100 Everywhere Fast Ethernet 10/100.

I've tryed to enable it, but it doesn't work cause I tryed hooking the cable modem straight into it and it didn't work.  So if someone could guide me into the right direction i'd greatly appreciate it.

Another problem i'm having so far is, I installed Automatrix (awesome program) and selected the numlock key and firestarter to both run on startup, but they aren't, so again, if someone could help me with that, that would be awesome.

BTW, i've attempted to use other versions of Linux, and so far, Ubuntu definately has the best support i've seen!

---

### Post by audax321 on 2006-02-01
Did you enable it through System > Administration > Networking... you have to select it, probably tell it to use DHCP, check the box indicating this device is configured and then enable it.

If you did all that, then open up a terminal (Applications > Accessories > Terminal) and type: gedit /etc/network/interfaces

Copy the contents of that file and paste here (censor any passwords or anything that might be in there... although if you don't have wireless you probably don't).

---

### Post by tblehr on 2006-02-01
Thanks for the quick reply!  Ok, I did what you said and here's the results:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp



auto eth0

auto eth1

Also, after I activated it, I tryed to enable internet shaing with Firestarter, but it says that eth1 is not ready, to check my connection.

---

### Post by audax321 on 2006-02-01
Is the Linksys is the only card in your computer? That config looks like there are two cards. Can you run "ifconfig" in a terminal and post the output?

Also try the following commands:

# bring down both interfaces
sudo ifdown eth0
sudo ifdown eth1

# bring up both interfaces
sudo ifup eth0
sudo ifup eth1

---

### Post by tblehr on 2006-02-01
Actually I have two ethernet cards, one's onboard, which works fine.  The one in question is the PCI NIC card I added.  I'm using the onboard one to hook straight into the internet....then the PCI (Linksys) one to hook into a hub which goes to the other computer in the apartment.  I realize a router would prolly be mch easier, but ours blew up, and this is what i'm stuck with for now. :)

Here's the results of the second test you asked for:

eth0      Link encap:Ethernet  HWaddr 00:50:8D:ED:D5:80
          inet addr:24.250.164.11  Bcast:24.250.164.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:feed:d580/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39398513 (37.5 MiB)  TX bytes:2491220 (2.3 MiB)
          Interrupt:16 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:04:5A:81:D8:FB
          inet6 addr: fe80::204:5aff:fe81:d8fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:23 dropped:0 overruns:0 carrier:46
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3251126 (3.1 MiB)  TX bytes:3251126 (3.1 MiB)

---

### Post by audax321 on 2006-02-01
Hmm, the only problem I can think of is opening the config file (sudo gedit /etc/network/interfaces) and maybe try adding: map eth1
under where it says map eth0 in the config file as well. Then reboot your computer and the interface should come up.

If it still doesn't I have no idea what the problem is because the config file looks good. Also I know the Linksys 100TX and the NC100 are very similar cards (maybe even the same card renumbered) and I believe they may even use the same driver. If memory serves me right it should be the tulip driver (although I used this card almost 2 years ago so it could have changed). You can check if its loaded by running the command: lsmod

If its not in the list bring the interfaces down as above, run the command "sudo modprobe tulip", and then bring the interfaces back up.

---

### Post by tblehr on 2006-02-01
Ok I tryed adding the map eth1 and restarting.  It still says eth1 was not ready.  I ran the lsmod and it brought this up:

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
acpi_cpufreq            6020  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  4
tsdev                   7616  0
pcspkr                  3652  0
rtc                    11832  0
usblp                  11776  0
ohci1394               30644  0
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
snd_hda_intel          15872  4
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
dm_mod                 50364  1
evdev                   9088  0
ide_disk               16128  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 acpi_cpufreq,thermal
fan                     4740  0
usbhid                 30688  0
tulip                  45088  0
r8169                  23180  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  5 usblp,usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
ata_piix                9476  0
ahci                   11268  5
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  5 sr_mod,sbp2,sd_mod,ahci,libata
piix                    9476  1
ide_core              125268  4 ide_disk,ide_cd,ide_generic,piix
unix                   24624  628
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

I'm not realy sure i'm looking for, but it does say tulip, which may be good, I don't know.

Ok, also just tryed running "sudo modprobe tulip", but I don't know if it did anything, it just went back to the command line after I hit enter.

---

### Post by audax321 on 2006-02-01
sudo modprobe tulip just loads the tulip driver. Honestly, I'm not sure what the problem is because if tulip is in that list that mean the correct driver is already loaded. Sorry, hopefully someone else will come across this post and be of more help :confused:

---

### Post by tblehr on 2006-02-01
Ah, it's cool!  I appreciate the help!  Maybe i'll just have to get me a router. ;)  But if anyone else wants a shot at this problem, go for it! :)

---

### Post by tblehr on 2006-02-01
Ok, actually, some good news!  Hopefully you'll read this audax321.  I turned the computer off, hooked the cable modem back into the Linksys card and now it works.  So I hooked the onboard card into the hub and tryed running Firestarter with internet sharing enabled and now it says that eth0 is not ready.  So, there's no problem with the hardware, at least not now.  It must be Firestarter.  So is there anything special I need to do to get Firestarter to share the connection.  IE do I need to get a DHCP server app?

---

### Post by mips on 2006-02-01
Deactivate the card.
Reactivate the card.
Click the Start button on Firestarter.

---

### Post by tblehr on 2006-02-01
Ok, I just tryed deactivating and reactivating both eth1 and eth0, but it still says that eth0 (which is hooked to the hub) is not ready.

---

### Post by tblehr on 2006-02-01
CASE CLOSED!

I just didn't have the eth1 configured right.  I had to manually assign IPs so the problem I guess was really that my adapter didn't like DHCP!  Whatever, it works now!  Thanks for everyone's help! :)

---

