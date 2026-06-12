---
title: "Realtek RTL8180L 802.11b MAC cannot detect networks"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by bryncoles on 2008-02-11
Hi there. Running ubuntu 7:10, Gutsy Gibbon. 

im having major headaches trying to get wireless networking up and running with my realtek RTL8180L card. I just cant figure it out! i tried following the advice in various other posts i found but came acropper each time. 

Im hoping someone will be able to give me a hand-holdingly simple guide to getting things up and running!


i've tried doing 'sudo lshw' and got:

  *-network:0
                description: Wireless interface
                product: RTL8180L 802.11b MAC
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:01:01.0
                logical name: wlan0
                version: 20
                serial: 00:10:60:8d:e3:a4
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b

while typing 'ifconfig' gets me 


wlan0     Link encap:Ethernet  HWaddr 00:10:60:8D:E3:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:295872 (288.9 KB)
          Interrupt:11 Memory:de97c100-de97c200 

and 'iwconfig'


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.484 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   Sensitivity=80/85  
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

but when i type: 'sudo ndiswrapper -l'

i get the output 

WARNING: /etc/modprobe.d/blacklist.save line 28: ignoring bad line starting with 'V'

and typing 'sudo modprobe r818x'

gets me 

WARNING: /etc/modprobe.d/blacklist.save line 28: ignoring bad line starting with 'V'
FATAL: Module r818x not found.

net8180 : driver installed
        device (10EC:8180) present (alternate driver: r8180)


and 'sudo modprobe ndiswrapper'

WARNING: /etc/modprobe.d/blacklist.save line 28: ignoring bad line starting with 'V'

Finally, 'sudo iwlist wlan0 scan'

tells me

wlan0     No scan results

and i dont knaow what to do about all this! except use a cable connection!

can someone help me please?

---

### Post by alan34 on 2008-02-11
Hi, are you using the windows drivers for your card? It appears so. I have rtl8185 chipset

on my wireless network card so had to use the windows drivers to get it to work.

This just a guess but from the errors you are getting has the r8180 linux driver

been blacklisted correctly? Try opening a terminal ( Applications - Accessories -Terminal) then

sudo gedit /etc/modprobe.d/blacklist

Then go to line 28 in that file and check if it is correct - should be

blacklist r8180

nothing else if there is a comment of some sort there it must have a # before it such as

# blacklist linux wireless driver

Also do you load ndiswrapper to the kernal when the system boots?

sudo gedit/etc/modules

should have ndiswrapper on a line on its own at the bottom (other things too so do not delete
those).

The help file is very good ( the lifebuoy on the top toolbar ) for windows drivers

or have a look at this

[http://ubuntuforums.org/showthread.php?t=646320](http://ubuntuforums.org/showthread.php?t=646320)

Will not be able look until tomorrow night - 24h. so good luck

---

### Post by bryncoles on 2008-02-12
Hi there alan34, appreciating your help! you're right about me having (tried to) install the windows drivers - i think they're there and if i go to network manager, my wireless is there and roaming mode is enabled. it just detects nothing, and connects to nothing!

i have followed your advice, and interestingly, my 'sudo gedit /etc/modprobe.d/blacklist' stopped at line 26! i have tried adding 'blacklist r8180' to line 28, but it still gives me the error message. 

'sudo gedit /etc/modules' showed me that ndiswrapper wasnt loading at boot, so as advised in the post you linked to, i have added that to this file.

i still dont have wireless networking though, and i still get the 

WARNING: /etc/modprobe.d/blacklist.save line 28: ignoring bad line starting with 'V'


error message. only now im also told 

net8180 : driver installed

and 

FATAL: Module r818x not found.

what else should i try?

---

### Post by dstew on 2008-02-12
> WARNING: /etc/modprobe.d/blacklist.save line 28: ignoring bad line starting with 'V'It looks like there is a funny character stuck in your blacklist, and that causes the line to be ignored. Look carefully at the file. It might be a control character that is invisible. Try to remove the whole line, and enter it fresh. Also, I am not sure if it matters, when using graphical programs like gedit it is more correct to do **gksudo** gedit /etc/modprobe.d/blacklist

---

### Post by alan34 on 2008-02-12
Back again, as the last post. I would cursor down to about line 20 then cursor across the text

to see if it ends at the end of the text on the screen.

Also could you in a terminal do a 

ls -l /etc/modprobe.d

you appear to a file blacklist.save in that directory which I have have not got in my directory
here is my listing is yours the same?

alan@alan-desktop:~$ ls -l /etc/modprobe.d/
total 80
-rw-r--r-- 1 root root 4624 2007-10-05 17:41 aliases
-rw-r--r-- 1 root root 2219 2007-10-19 15:45 alsa-base
drwxr-xr-x 2 root root 4096 2007-10-16 00:17 arch
lrwxrwxrwx 1 root root    9 2007-10-19 14:57 arch-aliases -> arch/i386
-rw-r--r-- 1 root root  789 2007-10-19 14:31 blacklist
-rw-r--r-- 1 root root  628 2007-10-05 17:41 blacklist-framebuffer
-rw-r--r-- 1 root root  156 2007-10-05 15:06 blacklist-modem
lrwxrwxrwx 1 root root   41 2007-10-19 14:57 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root   38 2007-10-05 16:26 blacklist-scanner
-rw-r--r-- 1 root root  838 2007-10-05 17:41 blacklist-watchdog
-rw-r--r-- 1 root root  484 2007-10-03 09:55 bluez
-rw-r--r-- 1 root root  343 2007-09-19 01:01 fuse
-rw-r--r-- 1 root root  205 2007-10-15 12:41 ipw3945
-rw-r--r-- 1 root root  299 2007-10-05 17:41 isapnp
-rw-r--r-- 1 root root   16 2007-09-07 09:04 libpisock9
-rw-r--r-- 1 root root  294 2007-10-15 12:41 lrm-video
-rw-r--r-- 1 root root   24 2007-10-19 14:29 ndiswrapper
-rw-r--r-- 1 root root   29 2006-10-09 14:33 nvidia-kernel-nkc
-rw-r--r-- 1 root root  173 2007-10-05 17:41 options
-rw-r--r-- 1 root root   60 2007-09-19 10:50 thinkpad_acpi.modprobe
-rw-r--r-- 1 root root   41 2007-09-19 10:50 toshiba_acpi.modprobe
alan@alan-desktop:~$ 

No blacklist.save, has this file been created as some sort of backup?

Sorry about not using the gksudo gedit command as I always use an editor called vi
but don't tell other people to use it:?

Is this a pci card or a usb stick, if it a usb stick try

blacklist r8180usb

in the /etc/modprobe.d/blacklist file

Good Luck

---

### Post by bryncoles on 2008-02-13
i tried removing and re-entering line 28, as dstew suggested, although there was no line there anyway when i first looked at the blacklist file. it doesnt see to make any difference anyway.

how do i check for hidden control lines/lines/characters?


i tried typing 'ls -l /etc/modprobe.d', and it gets me:

total 92
-rw-r--r-- 1 root root 4624 2007-10-05 17:41 aliases
-rw-r--r-- 1 root root 2184 2007-10-05 15:06 alsa-base
drwxr-xr-x 2 root root 4096 2007-10-16 00:17 arch
lrwxrwxrwx 1 root root    9 2008-01-06 16:01 arch-aliases -> arch/i386
-rw-r--r-- 1 root root  758 2008-02-13 09:28 blacklist
-rw-r--r-- 1 root root  758 2008-02-12 09:48 blacklist~
-rw-r--r-- 1 root root  628 2007-10-05 17:41 blacklist-framebuffer
-rw-r--r-- 1 root root  156 2007-10-05 15:06 blacklist-modem
lrwxrwxrwx 1 root root   41 2008-01-06 16:01 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw------- 1 root root  745 2008-01-18 09:41 blacklist.save
-rw-r--r-- 1 root root   38 2007-10-05 16:26 blacklist-scanner
-rw-r--r-- 1 root root  838 2007-10-05 17:41 blacklist-watchdog
-rw-r--r-- 1 root root  484 2007-10-03 09:55 bluez
-rw-r--r-- 1 root root  343 2007-09-19 01:01 fuse
-rw-r--r-- 1 root root  205 2007-10-15 12:41 ipw3945
-rw-r--r-- 1 root root  299 2007-10-05 17:41 isapnp
-rw-r--r-- 1 root root   16 2007-09-07 09:04 libpisock9
-rw-r--r-- 1 root root  294 2007-10-15 12:41 lrm-video
-rw-r--r-- 1 root root   24 2008-01-16 18:19 ndiswrapper
-rw-r--r-- 1 root root   29 2006-10-09 14:33 nvidia-kernel-nkc
-rw-r--r-- 1 root root  173 2007-10-05 17:41 options
-rw-r--r-- 1 root root  252 2007-09-30 01:07 sl-modem-daemon.modutils
-rw-r--r-- 1 root root   60 2007-09-19 10:50 thinkpad_acpi.modprobe
-rw-r--r-- 1 root root   41 2007-09-19 10:50 toshiba_acpi.modprobe

which is all Greek to me!

i notice i do have a blacklist save though, but ive not idea why. i haven't deliberately created a backup of the file (im still a bit to green to be doing things like that). 

i notice that if i navigate to the folder -> etc -> modprobe.d -> blacklist and look myself, there is a blacklist, a blacklist.save (which has a big 'X' next to it), along with a blacklist frame buffer, blacklist oss, blacklist modem, blacklist scanner and blacklist watchdog. i don't know if this helps....

i think my wireless is a PCI (its built in anyway).

---

### Post by dstew on 2008-02-13
> how do i check for hidden control lines/lines/characters?
One easy way is to open the file using a more powerful word processor, like OpenOffice. It has a menu option to show all characters, like tabs and spaces, that don't always appear. I can't remember the exact menu location. In Microsoft Word, it is a paragraph sign in the toolbar.

---

### Post by bryncoles on 2008-02-13
aha! progress, but not success (yet). i found the badline starting with V - it was hiding in 'blacklist.save', while i was originally looking in 'blacklist'. im not sure why i have two blacklist files, but they now both read the same (is there a chance they could be conflicting with each other?). i added blacklist r8180 to both of them, just to be sure. 

now, when i type '$ sudo ndiswrapper -l', i get

net8180 : driver installed
        device (10EC:8180) present (alternate driver: r8180)

and for '$ sudo modprobe r818x', 

FATAL: Module r818x not found.

while '$ sudo modprobe ndiswrapper' gets no output whatsoever! '$ sudo iwlist wlan0 scan' still gives me: 

wlan0     No scan results

BTW, thanks for joining in on this dstew! ;-)

---

### Post by dca on 2008-02-13
Wait, someone help me out with this:
 
Should there be an alternate driver displaying when typing ndiswrapper -l???
 
That looks like it's loading two drivers when the system starts...

---

### Post by dca on 2008-02-13
...if someone can verify the above then you should be able to type at CLI:
 
sudo rmmod r8180
sudo modprobe -i ndiswrapper
 
...then be sure to add the ndiswrapper to the bottom of the modules file as suggested in above post...  but wait a sec to see if that sounds correct...

---

### Post by alan34 on 2008-02-13
Here is the output from my pc

alan@alan-desktop:~$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)
alan@alan-desktop:~$ 

so you will get the alternate driver listed that must be okay.

I don't think you should be running this command it will insert the r818x driver
into the kernel

sudo modprobe r818x

Try this in both your blacklist files make the last line

blacklist r818x

make sure you have ndiswrapper in /etc/modules

and reboot

Also you could try to move your blacklist.save file out of /etc/modprobe.d directory
this would be

mkdir /home/temp

sudo mv /etc/modprobe.d/blacklist.save /home/temp

and to move it back

sudo mv /home/temp/blacklist.save /etc/modprobe.d

If no joy do a lsmod in a terminal and post the output.

Good luck

---

### Post by bryncoles on 2008-02-13
have followed all the advice given so far, but still no wireless. :-(

so heres the output to $ lsmod:

Module                  Size  Used by
xt_limit                3584  6 
xt_tcpudp               4224  12 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
ipv6                  273892  8 
af_packet              24840  2 
i915                   25856  2 
drm                    83348  3 i915
binfmt_misc            12936  1 
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
container               5504  0 
battery                11012  0 
video                  18060  0 
button                  8976  0 
ac                      6148  0 
dock                   10656  0 
ndiswrapper           185240  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
soundcore               8800  1 snd
serio_raw               8068  0 
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
8139too                27776  0 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
bryn@bryn-laptop:~$ 


and just to check im not being uber-stupid, '$ sudo iwlist wlan0 scan' should detect a network, right?

---

### Post by alan34 on 2008-02-13
Yes sudo iwlist wlan0 scan should find all the networks near you.

From lsmod it looks like your wireless driver is being loaded correctly to the kernel but as you
by now realise wireless in linux/gnu can be quite problematic, not all windows drivers work
with ndiswrapper. Not the fault of Ubuntu just the hardware people do not release drivers.

I would remove the existing driver with sudo ndiswrapper -r nameofyourdriver and try another
driver, there must be more on the cd that came with the wireless card. If you look on the Ndiswrapper website 
they say the XP driver is best then W2000 driver and the Vista driver will NOT work.

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

There is a graphical user interface to ndiswrapper called ndisgtk you can load it through
System - Administration - Synaptic Package Manager might be a bit easier for you.

Or as a last resort just go and buy a wireless card that supports linux, not ideal but...........

Google wireless cards in linux

Let us know how you get on, all the best

Alan

---

### Post by bryncoles on 2008-02-14
no problem. ill try all these things and see what happens. just one complete dunce question... what do i do to find out the name of my wireless drivers? is there a command i type at terminal? im understandably terrified at the prospect of any command with the '-r' thing in it and dont want to remove the whole of my hard drive by accident (i can see myself doing that!)

ill let you know what the outcome is, currently its between 

a) persevere and see how far i get
b) give up and stay cabled
c) buy a new wireless. 

i think b and a are most likely, as i could never get wireless to work with windows either (i think some of my security protocols forbade it), so i see wireless as a luxury anyway!

*edit*

ok, ive looked at ndisgtk, and it looks friendly and useful. hooray! but im scared, cause it only shows the one driver - net8180. this is just the wireless driver, yes? unistalling this wont kill my whole internet, will it....?

*edit 2*

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#372](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#372)

has linux drivers for fedora. Kernel 2.6.x. is this any use to me?

*edit 3*

i think the card is a billionton mwlrp... if that helps anyone....

*edit 4*

i can find wireless drivers but they all seem to be damnable .exe files... would i be able to go wireless using wine i wonder? does anyone know?

---

### Post by dstew on 2008-02-14
> what do i do to find out the name of my wireless drivers?Do you mean, what are the wireless drivers that I have currently installed in my kernel, or drivers that are somewhere out there that you want to install, or use with ndiswrapper? From my reading about gutsy and this chipset you have, you should concentrate on trying the ndiswrapper route. Did you see [this thread]("http://ubuntuforums.org/showthread.php?t=584046")? The post by Rzulf has a link to a driver that worked with ndiswrapper. Click on the link, and you get a .bz file. Double click on it to extract. You should get a folder that contains the driver and the .inf file.

If you want to know what drivers to use, you can check the chipset of your card using the **lspci** command. This lists all the PCI devices, and the wireless card will be among them. If you want to know what modules are available to your kernel, use the **modprobe -l **command. To make a short list of just the wireless modules, use```
modprobe -l | grep wireless
```To list the modules currently installed and in use, use **lsmod** (but you know that already).

Also: there is a way to extract the driver files from those .exe files. I think the program is called **cabextract**. You can install it using synaptic, and check it out.

---

### Post by alan34 on 2008-02-14
Hi 
You say you cannot get wireless to work in Windows, does this mean your signal is too poor
to get any sort of wireless connection? You could try logging into your router and taking off
any encryption on it. If you look in the paperwork that came with your router you should find
an IP address username and password to access the router. Like mine is

192.168.0.1 username admin password admin

just enter the IP address in any web browser

but they do vary from router to router look here

[http://www.cyberpunkcafe.com/routerpasses.html](http://www.cyberpunkcafe.com/routerpasses.html)

You should be able to back up your router settings to a file so do that first before changing.

Removing the net8180 driver will only affect your wireless card, your ethernet card uses
another driver. Do you have a cd that came with the card or PC the drivers are on that
they will be something.sys and something.inf copy them both to a directory before
using ndisgtk.

I have thought of another solution for your problem but it would mean re-installing Ubuntu.

The realtek chips worked for me (no guarentee it will work for you!!!) with the linux driver in Ubuntu ver 7.04 Feisty with the slight hack of adding an extra letter to the end of your ESSID. for example my ESSID is

alananddave so this became alananddaveX

You can still download ver 7.04 from here.There is still over a year of support on 7.04 so perhaps it might be worth installing that and hope the next version works with your card.

[http://www.mirrorservice.org/sites/releases.ubuntu.com/](http://www.mirrorservice.org/sites/releases.ubuntu.com/)

Keep posting you will get get there in the end.

---

### Post by bryncoles on 2008-02-15
i didnt see that thread, but i am encouraged by the *solved* aspect of it ;-) if nothing else, i realise that wireless issues arent necessarily 'terminal' (theres a GUI joke there if someone wants it....)

anyway, i did a silly thing yesterday when trying to remove the current driver set through ndisgtk: i forgot to run as sudo! it removed the wireless drivers, but when i try and install some new ones i get the message:

'module configuration already contains alias directive'

im guessing this can be resolved, probably through they terminal (theres that pun opportunity again). 

ill read through the other thread, and see what i can learn, and all investigate cabextract while im at it. 

im really appreciating all this help BTW. :-D

*edit*

heh heh heh, when i type 'ndiswrapper -l' now it tells me:

net8180 : invalid driver!

oops! what did i do?

*edit*

ok, ndiswrapper -l now doesnt tell me anything, so i must have successfully somehow removed the remenants of driver from there. good-ho!

still getting 'module configuration already contains alias directive' though, and thats preventing me from reinstalling any drivers. googling the phrase gets a lot of hits, none of which seem to address what to do about this issue!

plus, i have no wireless anything acknowledged in my network computer thingy. i suspect this is a good thing, because it means the blacklisting has worked at least....

*edit 3*

'ifconfig -a'

no longer displays my wlan0.

---

### Post by bryncoles on 2008-02-18
ok, havent yet figured out how to get past this 'module already contains alias' issue, and looking at other forum posts just seems to strongly suggest that noone knows what this means. as soon as someone posts this issue, the help with ndisgtk stops dead ha ha! encouraging!

nevertheless, i can confirm that the problem is not with my wireless router, as i have borrowed a wifi dongle off someone, and that both detects wireless networks, and connects to them. 

the problem then, is with the wifi card in my laptop. the optimal solution then might actually be getting a new wireless card - sigh. 

im gonna have another stab at getting the built-in to work this week first though....

*edit*

when i do $ 'sudo iwconfig' for the built in wireless, it tells me 
lo        no wireless extensions.

eth0      no wireless extensions.

so ive lost the wlan interface. good, i think. when i type $ 'sudo ndiswrapper -i net8180.INF'

it says 

installing net8180 ...
couldn't open net8180.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.

which i get confused by

finally, $ 'ndiswrapper -l' results in 

net8180 : invalid driver!


so, where do we stand? with external wireless dongles? ;-)

---

### Post by alan34 on 2008-02-18
Are you in the directory where the something.inf and something.sys files are?

cd tothecorrectdirectory

ls -l

See the files?

copy and paste

sudo ndiswrapper -i something.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l

should get some output

gksudo gedit /etc/modules

add ndiswrapper at the bottom

gksudo gedit /etc/modprobe.d/blacklist

add

blacklist r8180
blacklist r818x

Restart the computer

go to the network icons top right if on gnome and see if you have a connection

click on wireless connection then properties then network name drop down arrow.

Good luck

---

### Post by bryncoles on 2008-02-19
ok... did all that and heres what i got in return...

bryn@bryn-laptop:~$ cd /home/bryn/Desktop/stuff/computers/linux\ installers/windows\ wireless\ drivers/Archiwum/

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ ls
NET8180.INF  Release.txt  rtl8180.sys

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ ls -l
total 220
-rw------- 1 bryn bryn  14747 2004-10-06 10:48 NET8180.INF
-rw------- 1 bryn bryn  12518 2004-10-14 11:25 Release.txt
-rw------- 1 bryn bryn 185344 2004-10-07 15:37 rtl8180.sys

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ sudo ndiswrapper -i NET8180.INF

[sudo] password for bryn:

driver net8180 is already installed

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ sudo depmod -a

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ sudo modprobe ndiswrapper

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ sudo ndiswrapper -m

module configuration already contains alias directive

bryn@bryn-laptop:~/Desktop/stuff/computers/linux installers/windows wireless drivers/Archiwum$ sudo ndiswrapper -l

net8180 : invalid driver!

Im guessing that this 'invalid driver' thing is a sticking point.... but at least i know its there ;-)
and im learning quite a lot in the process too. im so proud i manage to navigate to a directory in the terminal! :-D

---

### Post by alan34 on 2008-02-19
HI again not there yet then

In a terminal

sudo ndiswrapper -r net8180

This will remove the windows driver.

gksudo gedit /etc/modules 

and delete the line ndiswrapper

Then restart the computer and hopefully you should be back to a "normal" kernel.

In a terminal

sudo ndiswrapper -l

should give you NO output.

Now I am not sure if this makes any difference but the permissions on your files are
not the same as on mine when I installed the windows drivers, so we shall change them to
 be the same.

Info         in linux there is three types of computer users and three types of access to files
and directories

Computer Users are
1) user
2) group
3) other

File Access
1) read
2) write
3) execute

so when you do a ls -l like so

alan@alan-desktop:~/Software/ndiswrapper$ ls -l
total 304
-rw-r--r-- 1 alan alan   7962 2005-12-11 20:24 net8185.cat
-rw-r--r-- 1 alan alan  14276 2005-12-09 07:51 net8185.inf
-rw-r--r-- 1 alan alan 282240 2005-10-20 12:05 rtl8185.sys

the first - is for directories and links (shortcuts). The next rw- are user file access. The next r--
are group access and the last r-- is access for others. The first alan is the user and the second
alan is the group alan who other users on the computer can belong to. Sorry there is no easy
way of explaining this but its nice for you to know whats going on.

As you can see from above my files are -rw-r--r-- net8185.inf and yours are -rw------- etc.etc

to change copy and paste

sudo chmod go+r NET8180.INF
sudo chmod go+r rtl8180.sys

chmod is the command     go is group and others     +r add read permission for group and others.
( a plus sign adds permissions so a minus sign will take away permissions yes:) )

Do a ls -l and your output should be -rw-r--r--

Now go through all the commands in my post yesterday and the very best of luck

PS make sure you are in the directory where the files are:)

---

### Post by bryncoles on 2008-02-20
ok, ive followed your instructions and while everything worked, im still wifiless! boo!

the output im getting now is:

sudo ndiswrapper -l
[sudo] password for bryn:
net8180 : driver installed
        device (10EC:8180) present (alternate driver: r8180)


(which is right, as i have uninstalled and reinstalled the drivers. i got the no output as expected after i did sudo ndiswrapper -r net8180)

navigating to my wireless drivers folder now gets me: 

 ls -l
total 220
-rw-r--r-- 1 bryn bryn  14747 2004-10-06 10:48 NET8180.INF
-rw------- 1 bryn bryn  12518 2004-10-14 11:25 Release.txt
-rw-r--r-- 1 bryn bryn 185344 2004-10-07 15:37 rtl8180.sys

which is good (i assume). 

sudo ndiswrapper -m tells me 

module configuration already contains alias directive

but sudo ndiswrapper -l is telling me 

net8180 : driver installed
        device (10EC:8180) present (alternate driver: r8180)

 so something is working! ill try going through everything again tonight, and see if ive missed anything obvious...

:)

---

### Post by dstew on 2008-02-20
Once the driver is working, it is a matter of configuration. Focus on that. Print the output of **ifconfig**

---

### Post by bryncoles on 2008-02-21
ok, cool. the iwconfig gets me 

eth0      Link encap:Ethernet  HWaddr 00:40:D0:6B:20:16  
          inet addr:148.88.171.163  Bcast:148.88.171.255  Mask:255.255.252.0
          inet6 addr: fe80::240:d0ff:fe6b:2016/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12189634 (11.6 MB)  TX bytes:800820 (782.0 KB)
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:8D:E3:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:174848 (170.7 KB)
          Interrupt:11 Memory:de968100-de968200 

id like to say a thanks again for everybodies help on this!

---

### Post by dstew on 2008-02-21
So you have an internet connection on eth0, and your wlan0 is working but not connected. At this point you should be able to configure the wireless setup in your System --> Administration --> Networking window.

---

### Post by bryncoles on 2008-02-21
i see the network interface, and i can configure the card. i have roaming mode enabled, but it sees no networks! phooey!

though its good to know its there i suppose ;-)

---

### Post by dstew on 2008-02-21
I am not sure how to proceed from here, but several things might be an issue. The channel setting is one, and others like the sensitivity. It seems from the above output that some of the parameters are not listed. It looks more like an ifconfig output than an iwconfig output. If you think the post is really an ifconfig output, then post the result of **iwconfig wlan0**
EDIT: You might need to do **sudo** iwconfig wlan0

---

### Post by bryncoles on 2008-02-21
ill give everything a go! its possible i did the wrong command the first time heh heh heh!

'ifconfig':

eth0      Link encap:Ethernet  HWaddr 00:40: D0:6B:20:16  
          inet addr:148.88.171.163  Bcast:148.88.171.255  Mask:255.255.252.0
          inet6 addr: fe80::240:d0ff:fe6b:2016/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114225740 (108.9 MB)  TX bytes:4407592 (4.2 MB)
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59524 (58.1 KB)  TX bytes:59524 (58.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:8D:E3:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1104512 (1.0 MB)
          Interrupt:11 Memory:de968100-de968200 

'iwconfig':

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.432 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   Sensitivity=80/85  
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i just realised that 'wlan0' wasnt a separate command ha ha ha! oh well, it gets the same output as iwconfig, just without the lo and eth0. :-)

---

### Post by dstew on 2008-02-21
Now do ```
iwlist
```to see what frequencies (channels) are supported. Post the result. Usually, the driver will pick the frequency, but maybe not. Do you know what channel the access point uses?

---

### Post by alan34 on 2008-02-21
Hi Bryn and dstew 

I believe the command is

sudo iwlist wlan0 scan

Please post the output

A question how far away from the wireless router is your PC? If is far away, can you move it nearer?

Do you know

1) The network name ESSID

2) Password and type of encryption  WEP/WPA

3) IP address of the router (something like 192.160.0.1 or 192.168.1.1)

If you know these you may be able to configure your network anyway.

Are we getting anywhere I hope so:)

---

### Post by bryncoles on 2008-02-22
I'll do both: they get different results!

'iwlist'

iwlist		[interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

and 'sudo iwlist wlan0 scan'

wlan0     No scan results

this might be misleading cause im at work (uni) trying to find the uni wireless network... which people usually can detect from my office, so i assume its active. theres no one around i can check with atm though. ill try again at home, and i dare say i can sit next to the router while i try it!

i know the essid, password etc. ill post back after the weekend, or during the weekend if i have success!

and i do appreciate all the help you guys are giving me. im leaning a lot about terminal commands, about the support of the 'nix community and about my 'pooter. its all good!

---

### Post by alan34 on 2008-02-22
Hi the command

iwlist 

will give you like a help file for the command

sudo iwlist wlan0 scan

is a actual scan by your interface wlan0 unfortunately with no results see how you get
on later

Heres some reading for you though you must be sick to death of the terminal by now!


[http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html)

---

### Post by bryncoles on 2008-02-25
aha! useful post to the beginner pages, thankyou!

according to [http://www.linux.com/feature/56946](http://www.linux.com/feature/56946), typing 'sudo lsmod | grep net8180.inf' should get me some feedback if my driver is loaded. i get no feedback.... am i not loaded?

---

### Post by dstew on 2008-02-25
> typing 'sudo lsmod | grep net8180.inf' should get me some feedbackNo, that driver is "wrapped" inside of ndiswrapper and won't show up there. The kernel sees the driver as ndiswrapper. Try sudo lsmod -l | grep ndiswrapper to see if ndiswrapper is loaded. To see what driver is wrapped inside, use ndiswrapper -l

---

### Post by bryncoles on 2008-02-28
typing 'sudo lsmod -l | grep ndiswrapper'

gets me the feedback 

'Usage: lsmod'

is that right? does that mean Ndiswrapper is loading? i still dont have functionality of the integrated wireless card... though i do also still have access to the cable and a functioning wireless dongle...

also: busy reading through alan34's useful link to the beginner lessons.

---

### Post by dstew on 2008-02-28
> typing 'sudo lsmod -l | grep ndiswrapper'

gets me the feedback

'Usage: lsmod'There is an error in your command. It should be sudo lsmod | grep ndiswrapper

---

### Post by bryncoles on 2008-02-29
ah, winner!

now 'sudo lsmod | grep ndiswrapper' gets me:

ndiswrapper           185240  0 
usbcore               138632  10 rt2500usb,rt73usb,rt2x00usb,usb_storage,libusual,ndiswrapper,usbhid,ehci_hcd,uhci_hcd

so its definitely in. roaming mode still doesn't detect anything though. Hmmm. ill try configuring it again at the weekend to not be roaming i think, see where that gets me.

---

### Post by bryncoles on 2008-03-20
ah, phooey! just logging on to let you both know, i haven't managed to get the built in wireless working. but as it works with an external dongle, i know that i have some wireless connectivity at least. i think ill leave it at that. 

i appreciate the help you guys gave though, and while we may not have achieved what we'd hoped, i learned a lot about how 'buntu works., which should steer me right in the future. 

so once again, thank-you alan34 and dstew for trying! ;-)

---

