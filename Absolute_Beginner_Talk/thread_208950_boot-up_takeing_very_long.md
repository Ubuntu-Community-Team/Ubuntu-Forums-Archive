---
title: "boot-up takeing very long"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-07-04
i timed it...its about a half an hour to get to the logon screen

how do i make it faster then that? cuz a half hours really bad

---

### Post by notjohn101 on 2006-07-04
and oh if this helps

Intel celeron prosessor - 633 MHz

192 MB of ram

10 GB HDD

---

### Post by Rui Pais on 2006-07-04
half an hour :shock: what powers your computer a steam engine?

Seriously... You must give more information.

Where it stops and stays most of the time?
Do you have dhcp (some can be very slow...) or static network?
Sometimes is a conflicting hardware that holds the boot while kernel trys to load a module or activate a configuration. 
What dmesg shows? /var/log/messages show weird stuff or error messages?

---

### Post by notjohn101 on 2006-07-04
it gets stuck on "preparing resricted drivers" (majory of the problem)

but its only slow on boot up...during normal operation its normal

is there a way to maunally set the IP address...like windows has

---

### Post by Rui Pais on 2006-07-04
Probabily an hardware problem/compatibility.

Whats you video card and what driver you use for it. 

whats the output of
```
cat /var/log/Xorg.0.log | grep "(EE)"
```
if none (besides the legend "(WW) warning, (EE) error, (NI)...") whats the output of,
```
cat /var/log/Xorg.0.log | grep "(WW)"
```


seting a static IP gives usually faster results.
> sudo network-admin 
under connections select the network card and press button Properties.
On Configuration, change from DHCP to Static and give the data needed (ip.. and so on)

I find easier edit /etc/network/interfaces file, but its up tp you :)

---

### Post by notjohn101 on 2006-07-04
im useing the onboard video card

also...if u cant already tell...im new...can tell me were to go to learn about coding ans such

---

### Post by Rui Pais on 2006-07-04
[QUOTE=notjohn101]im useing the onboard video card

also...if u cant already tell...im new...can tell me were to go to learn about coding ans such[/QUOTE]
Oops, sorry.

Open a terminal, is called gnome-terminal for Gnome and konsole for KDE. Look at menus. On Gnome is under Utilities or System. Under gnome you can type ALT+F2 to get a Run command and run gnome-terminal.

Copy past those commands to the command line and enter ;)

---

### Post by notjohn101 on 2006-07-04
ok...ill do that...just gotta turn it on first....talk to u in a 1/2 hour

---

### Post by Rui Pais on 2006-07-04
[QUOTE=notjohn101]....talk to u in a 1/2 hour[/QUOTE]

damn it that is very annoying half an hour just to boot your machine.

By do way, i forget. To check what modules/drives you are using use 
```
lsmod
```
if you don't mind post the output too, to check which module are you using from restricted package.

---

### Post by notjohn101 on 2006-07-04
sorry it took so long...i had company as well...heres all the commands

**linux@linux:~$ cat /var/log/Xorg.0.log | grep "(EE)"**
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
**linux@linux :~$ cat /var/log/Xorg.0.log | grep "(WW)"**

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) (1280x1024,eView 17f2) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1152x864,eView 17f2) mode clock 121.5MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,eView 17f2) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
(WW) I810(0): Direct rendering disabled

**linux@linux:~$ lsmod**
Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
3c59x                  45608  0
mii                     5888  1 3c59x
i2c_i810                5252  0
snd_intel8x0           33692  1
tsdev                   8000  0
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
hw_random               5652  0
i2c_algo_bit            9608  1 i2c_i810
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
intel_agp              22940  1
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
serio_raw               7300  0
agpgart                34888  2 intel_agp
pcspkr                  2180  0
psmouse                36100  0
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
floppy                 62148  0
rtc                    13492  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
linux@linux:~$
linux@linux:~$

---

### Post by notjohn101 on 2006-07-04
bump

---

### Post by Rui Pais on 2006-07-05
hi,
(sorry, my internet provider is migrating my account to 5Mb "gradually" as they say and now every day they cut - why?!?! - my adsl line for hours... :evil: :evil:)

One of the problems is kernel try to load a module, wacon, for an hardware that it was not detected. We can take care of that later. 
Anyway, are you on laptop? do you have any those things (touchpad? is that the name) that flat sensors that moves mouse pointer following the touch of a finger? Are all your pointer devices working?

Looking at your loaded modules (lsmod output) don't seems that any restriced modules are loaded, at least that i can see. The problem should be while it trying to load them. 
Type on console:
```
sudo lrm-manager
```
Check if there is any output messages. It it do nothing for 2 or 3 minutes you can stop it with Ctrl+Alt+C or closing the terminal window.

And just one more output, what
```
lspci
```
says? (to check what hardware its detected)

---

### Post by notjohn101 on 2006-07-05
no...im using a regular PC....and yea my mouse and keyboard work

also it hangs on "Uncompressing Linux...0k, booting the kernel"

---

### Post by Rui Pais on 2006-07-05
[QUOTE=notjohn101]no...im using a regular PC....and yea my mouse and keyboard work

also it hangs on "Uncompressing Linux...0k, booting the kernel"[/QUOTE]

Thats normal (if it takes something 3, 4 minutes). 
Your computer is slow and have little memory. 
Linux is usually slow on load and start things... but is relatively faster after everything is loaded.

Since you are not using restricted modules you can avoid that check on the boot time (that seems to be the problem) by turn it off or removing the package. 
An easy way to turn it off is get sysv-rc-conf:
```
sudo apt-get install sysv-rc-conf
```
run it on a terminal:
```
sudo sysv-rc-conf 
```
search for the line liux-restricted (usually trunced to linux-res$) and on that line move the cursor over any [X] you find and press space bar (it turn the check off from the boot levels).

A more radical but more simple way is simply uninstall:
```
sudo apt-get remove linux-restricted-modules-common
```
if you need later for some hardware you can install it again.

That should make the thing faster... lets hope.

---

### Post by notjohn101 on 2006-07-05
problem?

[B]
linux@linux:~$ sudo apt-get install sysv-rc-conf[/B]
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate
linux@linux:~$

---

### Post by Rui Pais on 2006-07-05
no,
sysv-rc-conf belongs to a repertoir that you dont have enabled.

to do it quickly:
```
sudo gedit /etc/apt/sources.list
```
add the line:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```
I assume you are on dapper, replace it for breezy if it was the case.
save and do 
```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```

---

### Post by notjohn101 on 2006-07-06
im also going to uprage my memory from 192MB to 386

---

### Post by Rui Pais on 2006-07-06
Good. Increasing memory is always a good way of get thing faster.

But note that your half an hour boot time is not a question of optimize settings and/or get better hardware. I have a slower computer (pentium mmx 200MG w 98M ram) and it boots on less then 5 minutes. You got something wrong.

Do you installed sysv-rc-conf. Did boot without 'Preparing restricted modules' make thing go better and if so how much better?

There is other things you can try too. Here some ideas:

- Avoid trying load the wacom tablet driver that you don't have. 
Comment out (add a # on the begining of a line) on /etc/X11/xorg.conf at section started with:
> Section "InputDevice"
  Driver        "wacom" till the first 
> EndSection after the line with Driver "wacom".

- Turn off IPV6:
```
sudo gedit /etc/modprobe.d/bad_list
```
and add:
> alias net-pf-10 off
(reboot to make efect)

- If you don't use LVM:
sudo sysv-rc-conf
and disable lvm and evms from all levels.

- Check others boot processes that could be redundantly eating your system resources and killing booting time:
[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

- Try use a static IP.

- Check other light Desktop environment. Xfce4 is close to gnome and is lighther, fluxbox is even lighter and very configurable, just to mention two.

good luck.

---

### Post by notjohn101 on 2006-07-07
ok ill try all those things but "sysv-rc-conf" will not install...it says it can not find it in the achives

---

### Post by Rui Pais on 2006-07-07
> **notjohn101 said:**
> ok ill try all those things but "sysv-rc-conf" will not install...it says it can not find it in the achives


uhmmm... thats very strange. I checked, sysv-rc-conf is part or universe repo, [here]("http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz").
Are you sure that you have done a 
```
sudo apt-get update
``` after add the line with universe to sources.list?

Anyway you can download it manually from [here]("http://archive.ubuntu.com/ubuntu/pool/universe/s/sysv-rc-conf/sysv-rc-conf_0.99-3_all.deb") and install it with dpkg -i sysv-rc-conf*.deb
 Or get bum instead (sudo apt-get install bum). Bum offer less control but should managed to turn it off.

---

### Post by notjohn101 on 2006-07-07
i think i no the problem...when i added that url to download it from...i put a # next to it

o and everytimei try to save (for example) sources.list...it says i dont have to permission to do it...and im on the only user name on the computer

---

### Post by Rui Pais on 2006-07-07
> **notjohn101 said:**
> i think i no the problem...when i added that url to download it from...i put a # next to it

You mean in sources.list files? that explain it :lol:
That way apt or synaptic can see it. Just remove the #, update and you are on your way.


good luck

---

### Post by Rui Pais on 2006-07-07
don't forget sudo is needed. Try

> gksudo gedit /etc/apt/sources.list

---

### Post by notjohn101 on 2006-07-07
ok ill do that

---

