---
title: "serial 56k modem says no dial tone when trying to connect"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Shin Natsume on 2006-01-08
hi, whenever i try to connect to the net, my modem makes some noises, then doesnt want to connect (it makes some noises before it actually starts dialing)

so when i do this thru the gui i done see anything happing afterwards

so after reading somewhere that wvdial provides information when ur trying to connect and so forth, i set it up and tryed dialing up, so what i found out was when i try and dial up, it finds no dial tone

everything is plugged in, so it has to be either the modem, or some configuration problems 

the thing is it does connect eventually, usually after a few tries, except i spent most of today trying, and ive only just connected, this after reading a few modem how to guides i downloaded, i had nothing else to try till i got onto the net again

thanks for the help

ciao

---

### Post by mesocool on 2006-01-08
[QUOTE=Shin Natsume]hi, whenever i try to connect to the net, my modem makes some noises, then doesnt want to connect (it makes some noises before it actually starts dialing)

so when i do this thru the gui i done see anything happing afterwards

so after reading somewhere that wvdial provides information when ur trying to connect and so forth, i set it up and tryed dialing up, so what i found out was when i try and dial up, it finds no dial tone

everything is plugged in, so it has to be either the modem, or some configuration problems 

the thing is it does connect eventually, usually after a few tries, except i spent most of today trying, and ive only just connected, this after reading a few modem how to guides i downloaded, i had nothing else to try till i got onto the net again

thanks for the help

ciao[/QUOTE]

Do you upgrade your driver? Because I had the same problem before upgrading the drivers..

---

### Post by Shin Natsume on 2006-01-08
as far as i know it doesnt need, nor has drivers

ciao

---

### Post by mesocool on 2006-01-08
[QUOTE=Shin Natsume]as far as i know it doesnt need, nor has drivers

ciao[/QUOTE]

if it doesn't have driver, how is it able to work...

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by Shin Natsume on 2006-01-08
> Hardware modems don't need a special driver

my modem is a serial modem, not a winmodem, so it doesnt need drivers, just configuration, as far as i could tell from that guide, and from several others, serial modems dont need drivers

ciao

---

### Post by Mustard on 2006-01-08
Firstly, are you using /dev/modem in your config or are you manually setting /dev/ttyS0 or /dev/ttyS1 ?

Also, I'd be curious to view your .wvdial.conf file from your $HOME directory and compare it to mine.  If you post it in here just make sure you **remove your username and password** beforehand.

I know that when I use gnome-ppp I have a box I can tick that says 'Wait for dialtone'.  I have this ticked atm, as it was something that I used to have to do in windows to get my modem to work.  Looking through my .wvdial.conf file I can't see a specific part that relates to this function, so I don't know how to set it up using the pppconfig command.  I'm hoping I can deduce it from viewing your .wvdial.conf file.

Lastly I wonder if you could show the ouput of this command as well...
```
lsmod
```

---

### Post by Shin Natsume on 2006-01-08
> Firstly, are you using /dev/modem in your config or are you manually setting /dev/ttyS0 or /dev/ttyS1 ?

its set to /dev/ttyS0

> Also, I'd be curious to view your .wvdial.conf file from your $HOME directory and compare it to mine.  If you post it in here just make sure you **remove your username and password** beforehand.


> 
[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 56700
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
ISDN = 0
Modem Type = Analog Modem
 Phone = **********
 Username = ********
 Password = ********


> I know that when I use gnome-ppp I have a box I can tick that says 'Wait for dialtone'.  I have this ticked atm, as it was something that I used to have to do in windows to get my modem to work.  Looking through my .wvdial.conf file I can't see a specific part that relates to this function, so I don't know how to set it up using the pppconfig command.  I'm hoping I can deduce it from viewing your .wvdial.conf file.

im certain i saw somewhere , maybe in some config file i was searching thru talking about waiting for a dial tone, but i can remember what its set to, or how to find that setting

ciao

---

### Post by Shin Natsume on 2006-01-08
> Module                  Size  Used by
ppp_deflate             5888  0 
zlib_deflate           20760  1 ppp_deflate
bsd_comp                5760  0 
ppp_async              10240  1 
crc_ccitt               2176  1 ppp_async
nls_cp437               5888  0 
isofs                  32824  0 
udf                    75524  0 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0 
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  8 
ppp_generic            25748  7 ppp_deflate,bsd_comp,ppp_async
slhc                    6656  1 ppp_generic
joydev                  9280  0 
snd_mpu401              6344  0 
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
analog                 10528  0 
gameport               14472  1 analog
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
snd_intel8x0           30144  2 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  1 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_sis96x              5252  0 
i2c_core               19728  2 i2c_acpi_ec,i2c_sis96x
pci_hotplug            24628  0 
sis_agp                 8452  1 
agpgart                32328  1 sis_agp
tsdev                   7616  0 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  2 
jbd                    48536  1 ext3
dm_mod                 50364  4 
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
usbhid                 30688  0 
8139too                23552  0 
8139cp                 18432  0 
mii                     5248  2 8139too,8139cp
ohci_hcd               18564  0 
usbcore               104316  3 usbhid,ohci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
sis5513                14472  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   24624  684 
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


ciao

---

### Post by Mustard on 2006-01-08
I'm thinking it might be in the Advanced options when you run pppconfig.  I'm guessing that it might be the 'Carrier Check' option.  Mine is set to 'on' at the moment, but yours may need to be set to off.

It could even be the X3 part at the end of the initialisation string.  As I've been googling up some stuff on the subject and I recall reading that an ATX3 string is used to set this option (I'm not totally sure about that one though).

These are the hreads I'm currently reading anyway...

[http://www.die.net/doc/linux/man/man5/wvdial.conf.5.html](http://www.die.net/doc/linux/man/man5/wvdial.conf.5.html)
[http://www.linuxquestions.org/questions/showthread.php?t=378323](http://www.linuxquestions.org/questions/showthread.php?t=378323)
[http://www.manlib.com/man/495](http://www.manlib.com/man/495)

I googled using the search terms 'modem wait for dialtone wvdial.conf' if you  are interested in doing a bit of a search yourself.  You might be able to make more sense of it than me. :)

At the moment a lot of what I'm proposing is simply guesswork.

-edit-

With regards to the output of lsmod, from my rough understanding of how to interpret it, there appear to be modules loading that relate to ppp.  From this I am assuming that the kernel is loading drivers to handle the modem.

This what my .wvdial.conf looks like anyway....

```
mustard@slave:~$ cat .wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyS0
ISDN = off
Modem Type = Analog Modem
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 =
Init4 =
Init5 =
Init6 =
Init7 =
Init8 =
Init9 =
Phone = **********
Phone1 =
Phone2 =
Phone3 =
Phone4 =
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L1DT
Ask Password = off
Password = ********
Username = *********
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = on
;Minimize = on
;Dock = on
;Do NOT edit this file by hand!

```

---

### Post by Shin Natsume on 2006-01-08
thanks, ill have a google, and im checking thru pppconfig now, as well as ur links, let u know if i can figure out anything

ciao

---

### Post by Mustard on 2006-01-08
This paragraph down the bottom of the wiki HOW to link seems to be relevant to this problem....I've put the relevant sections in **bold**.  I am increasingly thinking that it is the X3 part of your initialisation string that is causing it to start dialing before the dialtone is present.  So I would think that you could edit this out (always make a backup first) and try it without the X3 string.

I've been looking at my .wvdial.conf in my $HOME directory.  The HOW TO talks of a wvdial.conf in your /etc/ directory, but I don't have one of those.  Do you have an /etc/wvdial.conf file?

[quote=WikiHOWTO]I prefer wvdial, because it tells you whether your modem is configured or not. Type in a terminal

    *

 $ sudo wvdialconf /etc/wvdial.conf

If it says 'no modem found' or something similar, sorry... the driver for your modem seems not to be installed properly yet. The lack of a /dev/modem is not supposed to break wvdial's configuration. If the modem is found, finish the setup with:

    *

 $ sudo nano /etc/wvdial.conf

After opening the wvdial.conf file, input your ISP information where needed (look inside the file for fields) and add other options that might be needed for your software modem. You will know what these options are if you asked for help from linmodems.org mailing list. Examples options that you can try to add, if dialling does not work:

    *

      **add X3 to Init2 (means dial without waiting)**
    *

**      add Carrier Check = no as a new line (useful for Smartlink modems)**
    *

**      add Stupid mode = on as a new line (will start pppd immediately--required by some ISPs)**

Typing man wvdial.conf in a separate terminal will give details on options.

Once you are ready, save the file (Ctrl-o) and exit (Ctrl-x), and try to dial:

    *

sudo wvdial

will dial and connect. Upon connection, it will spit out some information about your connection (local IP, remote IP, DNS address, etc.). Do not close the terminal where wvdial is running. Leave it alone until you want the connection to be terminated, and hit CTRL+C on that terminal once you want to end the connection.

If you lose the connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:

sudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a '#' at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4.

If you connect successfully but your Internet applications do not function (eg. web pages do not load in Firefox), you might need to add defaultroute as a new line in the pppd option file.
[/quote]

---

### Post by Shin Natsume on 2006-01-08
thanks im just reading the links u put up, so i ill start lookin at the apropriate man pages, as well as try a  modded version of ur .conf file, btw how did u copy the text off the terminal, i usually do a ">" into a text file... , or is that wat u did?

edit: ok cool, will give that a go, cheers :D

edit edit: yes i do have one in my /etc folder, that was the one i thought u were refering to 

ciao

---

### Post by Mustard on 2006-01-08
[QUOTE=Shin Natsume]thanks im just reading the links u put up, so i ill start lookin at the apropriate man pages, as well as try a  modded version of ur .conf file, btw how did u copy the text off the terminal, i usually do a ">" into a text file... , or is that wat u did?

edit: ok cool, will give that a go, cheers :D

edit edit: yes i do have one in my /etc folder, that was the one i thought u were refering to 

ciao[/QUOTE]

I'm on gnome desktop using gnome-terminal, so I just drag select and copy and paste from the terminal.

With regards to the /etc/wvdial.conf I don't know what the difference is between that one and the one I have in my $HOME (user home) directory.  My connection seems to work ok without it though.  Obviously you'll have to work with whatever config file you have. :)  In my $HOME directory it is a hidden file called .wvdial.conf.

---

### Post by Shin Natsume on 2006-01-08
well i logged off, and then it did same ol same ol, so i restarted the pc, and it worked, im not sure if i was lucky with it just connecting first time, or not, so ill let everyone know whether it worked after i log off and then on again

ciao

---

### Post by Shin Natsume on 2006-01-08
well i did manage to log in, but not automatically, and after 6 no dial tone errors

ciao

---

### Post by Mustard on 2006-01-08
If you can log in and be online for an extended period of time, I would download and install gnome-ppp.  Its a gui interface for dialup.  It's available through the synaptic package manager or you can use the apt-get command below in terminal..

```
sudo apt-get install gnome-ppp
```

That might make it a bit easier to get a connection going.

NOTE:- You may need to enable the universe repository before the gnome-ppp package is available for download.  Refer to this page on the wiki for instructions on enabling the Multiverse and Universe repositories.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Shin Natsume on 2006-01-08
thanks, will give it a go :)

ciao

---

### Post by Mustard on 2006-01-08
Good luck.  Its seems you are making progress anyway. :)

---

### Post by Shin Natsume on 2006-01-13
well i found out it ws the X3 part of the config file that was casusing the problems, so after i formated i just decided not to mess with it and just set it up via the gui, and now it runs perfectly fine

thanks for all the help

ciao

---

### Post by Mustard on 2006-01-13
Thanks for the update :)

---

