---
title: "ibm 600e stuck w/sound tried EVERYTHING!"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-03-21
ok please read... 

i know this must seem like beating a dead horse but i have done my home work... i have tried it this way,

1. Blacklist the incorrect sound card in /etc/hotplug/blacklist. Add lines for

snd-cs46xx
cs46xx

as written above - with the xx's

2. Add the following lines into /etc/modprobe.d/alsa-base

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

3. Add the line

snd-cs4236

to the file /etc/modules

Reboot.

Also important: During power up, if you press F2 (I think), you get into change the config. In this you need to make sure that the Fastboot option is *disabled*.

If you are still having no success: try adding 'acpi=off pnpbois=off' at the end of the kernel boot params. Press 'esc' during Grub countdown and select 'e' to edit the boot command and add these to the end. I need these to allow my Xircom PCMCIA ether card to work.

and Ive tried...

1- Add lines to /etc/discover.conf-2.6

# Sound card on Thinkpad 600E is incorrectly recognized...
# ...skip loading wrong drivers
skip cs46xx
skip snd-cs46xx


2- Add lines to /etc/hotplug/blacklist

# Avoid installing wrong drivers for the soundcard on Thinkpad 600E
cs4232
cs46xx
snd_cs46xx


3- Add lines to /etc/modprobe.d/alsa-base

# Thinkpad 600E sound chipset (Cirrus Logic CS4239 incorrectly recognized as CS46XX) is managed by cs4236 alsa driver
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 port=0x530 fm_port=0x388 sb_port=0x220 cport=0x538 irq=5 dma1=1 dma2=0
install snd-cs4236 /sbin/modprobe --ignore-install snd-cs4236 && /usr/sbin/alsactl restore >/dev/null 2>&1 ||:
remove snd-cs4236 {/usr/sbin/alsactl store >/dev/null 2>&1 ||: ;}; /sbin/modprobe -r --ignore-remove snd-cs4236

4- Add lines to /etc/init.d/rc.local (it has a link from /etc/rcS.d/S99rc.local)

modprobe snd-cs4236

all but #4 because i cant seem to find that file

i have a speaker in the top rt corner but when i got to multimedia system selector i get "Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'" and something like this for the rest.

any sugestions?
thanks

---

### Post by chrluc on 2006-03-22
anyone, anyone at all?

---

### Post by Brunellus on 2006-03-22
thinkwiki.org has a page on the subject:

[http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads](http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads)

---

### Post by chrluc on 2006-03-22
I know, I have read that page and about 15 others and still cannot get this to work at all (tried it on 3 different 600e), like i said in the first post i have tried several methods, i get a speaker in the top right hand corner ( no "x speaker" any more) but still no sound. is there something i need to do after mofifing the various files and rebooting? it seems like sound should be comming out but nothing.

---

### Post by jogege on 2006-03-22
If you are having the same problem on three different 600es then might be you are doing something wrong?

I have used the first part of your post which I also got from this forum successfully several times. If you have your home partition backed up, I would suggest trying afresh from a fresh install?

Also there might be a hardware fault. Have the speakers worked running windows?

Just for clarity, the three steps I take in getting my sound to work are:

1. Blacklist the modules in the blacklist file.
2.Add the extra lines to modprobe.d/aslabase file
3. Add the module to /etc/modules

and also endure that you have disabled quickboot in the IBM BIOS and also pass "pnpbios=off acpi=off" to the kernel when you boot up.

When I was running kanotix, after disabling quick boot in the bios, running alsa always gave me sound on this same laptop.

Good luck.

---

### Post by clembone on 2006-10-23
Did you get this corrected? I too had issues and I could feel your frustration. I got mine to work and I will be putting a step by step together. I have hacked on this all day.

---

### Post by gilf on 2008-02-02
I got mine working (Gutsy 7.10):

Notice the differences marked in red from the original poster's instructions



# Add these lines to /etc/modules:

sound
[COLOR="Red"]ad1848
uart401
snd-cs4236[/COLOR]

# Blacklist the incorrect sound card in[COLOR="Red"] /etc/modprobe.d/blacklist.[/COLOR] Add these lines as written below - with the xx's:

blacklist snd-cs46xx
blacklist cs46xx


Also, to turn off quickboot, he wrote you hold down the F2 key, it is [COLOR="Red"]actually the F1 key.[/COLOR]

While I realize that the 600E is a little old, mine runs great with Gutsy 7.10.

Important to set the color mode to 16 bit color depth instead of 24 bit, and get rid of Ipv6 -- but if you've done those things and have adequate memory, the computer runs more quickly than it did under windows 98SE -- it's quite fast under Ubuntu -- I did not need t go to Xubuntu.

One important thing, though -- make sure you set the CPU speed to be high at all times while in the windows IBM Thinkpad utility (plugged in power). This actually sets bios parameters, otherwise Ubuntu will run the cpu at reduced speed. I originally thought the laptop was too slow for Ubuntu, til I discovered (while dual booting to Windows) that the CPU speed wasn't set to max at all times. This made a BIG difference.

---

### Post by rioguia on 2008-02-15
I share your pain.  I found small variations in the many approaches documented around the web.  After lots of trial and error, I think I have reconstructed the steps I took that worked for me. I hope that this helps.
[my notes]("http://www.substantis.com/blog/?p=38")

---

### Post by rioguia on 2008-02-18
My soundcard setup recently failed but I am not sure how.

dmesg now gives these errors.

[ 5665.957283] pnp: Device 00:0e activated.
[ 5665.957489] CS4232 WSS PnP manual resources are invalid, using auto config
[ 5665.957585] CS4232 WSS PnP configure failed for WSS (out of resources?)
[ 5665.957677] PnP BIOS detection failed for CS4232
[ 5665.977283] pnp: Device 00:0e disabled.
[ 5665.977377] cs4232-pnpbios: probe of 00:0e failed with error -16

---

### Post by gilf on 2008-02-25
Well notice what I posted and the fact that you are failing on a pnp test for a CS4232.

It's CS4236, as I posted.

Why not try what was suggested?

By the way, I'm not only getting sound out of the 600e, but playing encrypted DVDs, and running VMWare player with a full Ubuntu 7.10 install and Win98SE as a virtual machine, running faster than it did natively.

How? I  modified my TP to a Pentium III 8% overclocked to 750 Mhz running 108 FSB instead of 66mhz, 512M memory. 256 cache now instead of 128.  It took me one evening to do it.

This little laptop has the best keyboard and form factor and construction feel of any I've ever tried. And now it's running some amazing stuff at decent speed, it's a fine computer to own, and I actually like using it better than my 2.4G desktop. Just feels good to use it. I'm even going to try XP as a virtual machine inside Ubuntu on a ten year old laptop for giggles.  Maybe I'll throw in a few more VMs for a other linuxflavors and win2000, since I have that too. Then I'm going over to my I-book toting friend's house to casually demo what a $125 computer can do. Mac-attack.

---

### Post by KingWarch on 2008-03-08
im having the same trouble with my tp 600e. when i tru to add the code into /etc/modules/
i get an error mesage saying i cant save is there a way to fix this?

---

### Post by gilf on 2008-03-14
When you try to edit anything in your main system (not in your user home directory) you need to have root (superuser) priveleges.

To get those priveleges while running a program, you first enter the word "sudo" into the command line.

A good editing program to use is called "gedit".

Therefore, you would open a terminal screen (Applications>Accessories>Terminal) and then enter into that terminal the following:

```
sudo gedit /etc/modules
```

to edit the file you are interested in.

---

### Post by senile2 on 2008-03-19
Have you made any headway on this problem?  I hate to play the me2 game, but like you, I have ready enough about the CS4610 IBM sound problem to fill a small book.

I have:
1.  the speaker icon on the toolbar - no x
2.  vol shows 100%
3.  system->preference->sound shows the device as CS4239 (I have done everything listed and some not listed to get this to change to CS4236 to no avail)
4.  all of the test show system busy (usually aplay is the bad boy)
5.  I have followed all the steps in installing the alsa drivers

This is getting kind of maddening..... I can't believe that 7.10 would not have some solution for this - that is understandable.

Guess now is the time for flames..... but this shouldn't be this difficult.

Let me know if you found some magic..... ty

---

### Post by senile2 on 2008-03-19
GILF, how do you verify that the CS4236 modules are infact operational?  I followed all the steps from the lead note and made the same changes you suggested, but still no sound.  I show the CS4239 device in the sys>pref>sound screens and can't get it to change to anything else.

ty

---

