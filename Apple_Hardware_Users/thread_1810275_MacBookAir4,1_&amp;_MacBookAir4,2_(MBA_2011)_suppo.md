---
title: "MacBookAir4,1 &amp; MacBookAir4,2 (MBA 2011) support"
date: 2011-07-22
forum: Apple Hardware Users
---

### Post by dentifrice on 2011-07-22
Hey there,

Has anyone got the chance to try install Debian or Ubuntu on the new MacBookAir models yet? Just to be clear, I am **[COLOR=black]not[/COLOR]** talking about the MBA models that came out late 2010, but about the MBAs that were issued on July 20th, 2011.

I would be very interested to know about using the SSD with the AHCI driver and booting the laptop in EFI mode (both being unresolved issues with the previous MBA model). Of course, I would also like to know about support for the intel HD graphics and the new broadcom wifi/bluetooth chipset, as well as Thunderbolt (but there's a [separate thread for that last bit]("http://ubuntuforums.org/showthread.php?p=11076266")).

Thanks!

---

### Post by Tchernobog76 on 2011-07-23
I would say that they're developing drivers as we speak. 
But respectively have you google'd for 'em yet?

---

### Post by dentifrice on 2011-07-23
> **Tchernobog76 said:**
> I would say that they're developing drivers as we speak. 
But respectively have you google'd for 'em yet?

What drivers and who are you referring to? The new chipsets, or the Thunderbolt protocol?

If it's about Thunderbolt, yeah, I googled a lot, only to come up with people asking the same question and not getting an answer. Didn't find anything in the LKML archives either.

---

### Post by ShakataGaNai on 2011-07-24
I'm also curious if anyone has got this working, and can't find anything.  Not really surprising since the units just came out a week or two ago.

As for the individual hardware components. I can tell you that the graphics adapter (Intel HD 3000) is supported in 11.04.  I've used that on a couple different machines with varying degrees of success (Dell E4310, Dell M4600, Lenovo X220).

---

### Post by gvzdus on 2011-07-24
Hi, I got a MacBook Air 4.2 and unfortunately, Ubuntu 11.04 does not support it yet. After the initial language selection and decision ("Try it from CD", "Install it" ...) the cursor blinking occurs, but after that the "Ubuntu" text graphic is not shown and the screen remains dark.

System info says (sorry, in german):

Intel HD Graphics 3000:

  Chipsatz-Modell:	Intel HD Graphics 3000
  Typ:	GPU
  Bus:	Integriert
  VRAM (gesamt):	384 MB
  Hersteller:	Intel (0x8086)
  Geräte-ID:	0x0116
  Versions-ID:	0x0009
  Monitore:
Color LCD:
  Auflösung:	1440 x 900
  Pixeltiefe:	32-Bit Farbe (ARGB8888)
  Hauptmonitor:	Ja
  Synchronisierung:	Aus
  Eingeschaltet:	Ja
  Integriert:	Ja
  Verbindungstyp:	DisplayPort

So, if you intend to run Ubuntu on MBA 4-2, you might have to wait...

Cheers, Georg

---

### Post by User4519 on 2011-07-24
> **gvzdus said:**
> Hi, I got a MacBook Air 4.2 and unfortunately, Ubuntu 11.04 does not support it yet. After the initial language selection and decision ("Try it from CD", "Install it" ...) the cursor blinking occurs, but after that the "Ubuntu" text graphic is not shown and the screen remains dark.

Hi Georg! Thanks for the report :)

Any chance you might try with the 11.10 Alpha 2? My MBA is on its way ATM, and either way my plan is to put Oneiric on it straight away.

---

### Post by dfacto on 2011-07-25
I was able to install Ubuntu by following this guide:
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

There is one notable exception.  Before booting from the cdrom, choose the partition editor from refit and let refit sync the mbr.  After this I was able to avoid the "cursor freeze" as described in an earlier post.

As I am only just now installing I cannot answer any other questions yet.

Cheers!

---

### Post by User4519 on 2011-07-25
Progress? :D And is this Natty or Oneiric?

---

### Post by dfacto on 2011-07-25
Natty.  Wifi, audio works.  Video stuck at 1024x768.  No multitouch yet.

This is my first mactel--maybe this is nothing--but I'm happy to have it booting w/o any hiccups...now on to xorg.

---

### Post by dentifrice on 2011-07-26
> **dfacto said:**
> Natty.  Wifi, audio works.  Video stuck at 1024x768.  No multitouch yet.

Could you attach the output of the following commands to your next post?

```
sudo lspci -v
sudo lshw
```Thanks, and good luck with xorg!

---

### Post by User4519 on 2011-07-26
> **dfacto said:**
> No multitouch yet.

Interesting... iFixit noted when they tore the new MBA apart, that the touchpad was the same as the previous model. Not having installed on an Air myself yet, I'm not yet sure which guide is the "right" one, but did you follow one, and have you succeeded in getting multitouch to work yet?

---

### Post by poliva on 2011-07-26
@dfacto: where you able to fix the issues with resolution and multitouch? Is the wifi working properly? how long does the battery last when using ubuntu? does it have any heating issues or any other issues worth mentioning? Thanks for your comments!!

---

### Post by dfacto on 2011-07-26
Hey all.  Sorry for not being very detailed in my earlier posts.  I am trying to do this as quickly as possible as I *should* be working on my thesis.  (I know everyone always tries to get Ubuntu running in five seconds--I'm not complaining per se!)  Oh, and this is my first Apple (since my Apple IIc; been linux-only for a decade tho).

First, this is the Guide I followed:
[https://help.ubuntu.com/community/MacBookAir3-2/Narwhal](https://help.ubuntu.com/community/MacBookAir3-2/Narwhal)

Deviations:

0) As I mentioned, I needed to run refit's mbr sync twice; once before booting the live cd and once after installing grub.

1) I had to update-grub with "nomodeset" added to the defaults.

2) Obviously I ignored any nvidia setup stuff (which is the majority of the guide.)
  
3) I used options "snd_hda_intel model=intel-mac-auto" in /etc/modprobe.d/alsa-base.conf although I don't know if it was needed.  To get speakers on I had to unmute the "Surround" device in alsamixer.  This was not discovered until after booting with the above alsa-base modified configuration.


Comments:

As I said, video is still stuck at 1024x768.  Also it is "fuzzy" I suspect due to the 6bits/dithering not set (guide uses nvidia specifics).

By "no multitouch" what I should have said is that gestures don't seem to work (want scrolling).  I didn't have luck with the five seconds I spent in xorg.conf.  I used the intel driver with the multitouch input section per the guide and gdm wouldn't load.  Xorg.0.log said "No device".  There is a good chance it was user error--as I said I was/am hurrying.

I also cannot get fn+up==pgup fn+delete=="pc delete" and the like to work.

Hopefully you hackers can point me in the right direction on these problems!  Once I have happy video and hid's then I will play with suspend but the priority is obviously video, hid.

The hardware profile is attached--I masked out any of the serial numbers--let me know if I took out too much (or too little!).

Cheers!

---

### Post by dfacto on 2011-07-26
@dfacto: where you able to fix the issues with resolution and multitouch? 

No.

Is the wifi working properly? 

Yes--even worked in the livecd.

how long does the battery last when using ubuntu? 

Only had this for 18 hours but IIRC I got 4-5 hours on default brightness with no peripheral devices connected.

does it have any heating issues or any other issues worth mentioning? 

Runs icy cold.  (My old sony vaio literally burns your finger-tips!)

Thanks for your comments!!

You're welcome--now help me make this work dammit!  (j/k)


Cheers

---

### Post by dfacto on 2011-07-26
@dfacto: where you able to fix the issues with resolution and multitouch? 

No.

Is the wifi working properly? 

Yes--even worked in the livecd.

how long does the battery last when using ubuntu? 

Only had this for 18 hours but IIRC I got 4-5 hours on default brightness with no peripheral devices connected.

does it have any heating issues or any other issues worth mentioning? 

Runs icy cold.  (My old sony vaio literally burns your finger-tips!)  Also, I have not heard any fan noise...does this thing even have a fan?

Thanks for your comments!!

You're welcome--now help me make this work dammit!  (j/k)


Cheers

---

### Post by dfacto on 2011-07-26
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude safe-upgrade

```

Did *NOT* seem to fix anything.

Also, using output of "sudo Xorg -configure" as my base config file for twiddling (which is not the one I posted before).

This is pretty much the end of the road for any ideas that I have.  Suggestions welcome!

---

### Post by User4519 on 2011-07-26
It might be worth trying an Oneiric Alpha LiveCD - I'm currently running Oneiric on my HTPC/server as Natty's Xorg is broken on this rig, and using xorg-edgers didn't help. Oneiric's Xorg works fine on this machine, might work for the MBA, too?

---

### Post by dfacto on 2011-07-26
Thanks for the tip--will try right now.  (I wouldn't have either--I was assuming edgers was sufficient.)

Cheers

---

### Post by poliva on 2011-07-26
Check the suggestions in these two links:

[http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768](http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768)
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by dfacto on 2011-07-26
@poliva  Thanks for the idea.  Here is what I tried:

```

$ cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

$ xrandr --newmode "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default

$ xrandr --addmode default 1440x900
xrandr: Failed to get size of gamma for output default

$ xrandr --output default --mode 1440x900
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

The screen then blinks and stays the same.  I think editing xorg.conf to include this modeline is the same unless I'm wrong.

Thanks for the idea tho!

---

### Post by poliva on 2011-07-26
damn it! well, let us know your results.. i'm waiting to see how well Linux is supported to decide between buying a MBA or going for a Vaio Z series :)

---

### Post by User4519 on 2011-07-26
> **poliva said:**
> damn it! well, let us know your results.. i'm waiting to see how well Linux is supported to decide between buying a MBA or going for a Vaio Z series :)

Yeah, me too - until I had the Z on-hand in a store. It just felt like cheap plastic, and it's SOOOO expensive :) I **hate** Apple more than any other company, and I feel like showering having ordered the MBA, but here I am. It's just so effing desirable. I'm gonna spray-paint tux on the lid eating that glowing apple, that's for sure... It's just... Argh! I hate that I just bought the MBA, but I'm also really glad I did. You know?

I have a VAIO TX3, which I bricked, in my closet - it's a really neat machine. But it's plasticky, and I'm not going back to Sony unless they start making machines that feel like what they cost.

My advice to you; find a Sony store and handle that Z series, then an Apple crap attack store and handle the Air, then make a choice.... I don't know, the... I... Hmmm...

---

### Post by dfacto on 2011-07-26
Exactly my sentiments as well.  I own a vaio z-series from 2008 (the first of this line) and it has ALWAYS been a nightmare.  I will never buy a sony ever again.  Hence Apple becomes the lesser of evils.

---

### Post by User4519 on 2011-07-26
> **dfacto said:**
> the lesser of evils.

Life in a nutshell! :D LOL

---

### Post by dfacto on 2011-07-26
BTW it seems the intel driver is not working at all and the reason the res is pinned to 1024x768 is because its using the fallback fbdev.

I'm burning oneiric alpha-2 now.  If this doesn't work I'm guessing we're SOL.

**Update**: In 11.10 live session now and its the same story. :(  I'm doing a fresh install of oneiric anyway but it won't make a difference.  End of the road for now?

---

### Post by Sarvatt on 2011-07-26
I've filed this about it so far:
[https://bugs.freedesktop.org/show_bug.cgi?id=39533](https://bugs.freedesktop.org/show_bug.cgi?id=39533)

some more logs (like lsusb) here if someone still wanted them
[http://sarvatt.com/downloads/macbookair/](http://sarvatt.com/downloads/macbookair/)

this is the drm-intel-next kernel where X works with i915 but the display is still blank that I'm referencing in the bug report:
[http://kernel.ubuntu.com/~sarvatt/edp/](http://kernel.ubuntu.com/~sarvatt/edp/)

---

### Post by jonny on 2011-07-27
Please keep this thread updated: I'm following it with interest, as my wife's air arrives tomorrow.  I've used Ubuntu since the Warty Warthog days, so that machine *will* run Ubuntu somehow - there's no way she'll downgrade to OS X!  I dislike Apple's approach to business as much as the rest of you, but until someone else starts to make attractive hardware, I'll be forced to buy from them.

It's a long shot, but did you try [Stefan Glasenhardt's PPA]("https://launchpad.net/~glasen/+archive/intel-driver")?  It seems to have a later version of the Intel driver than xorg-edgers (2.15 vs 2.14 for xserver-xorg-video-intel and 2.4.26 vs 2.4.23 for libdrm).  He doesn't seem to have Oneiric packages, yet, though.

---

### Post by berto- on 2011-07-27
I just got the latest macbook air and my goal is to run linux on this thing almost exclusively.  Any help dialing this thing in would be great.  I tried 11.04 and am now on 11.10 alpha 2.  As others have said I'm also stuck at 1024x768 resolution.

I found a phoronix article at [COLOR="Teal"][http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA]("http://www.phoronix.com/scan.php?page=news_item&px=ODk2OA")[/COLOR] describing what software is needed to get graphics running top notch.  From the article:

> For the proper Sandy Bridge experience you are left looking for the Linux 2.6.37 kernel, Mesa 7.10, the latest libdrm, and the xf86-video-intel 2.14.0 DDX that should be released in the next week or so. 

Anyone know how to start compiling these packages the ubuntu way for 11.04 or 11.10?  I can go either way, but at the end of the day I'm looking for a stable machine to work on.

I would **highly suggest** everyone run a few tweaks to conserve the SSD.  From the article at [http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html]("http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html"), the top 2 are:

[LIST]
[*]setup noatime on /
[*]setup /tmp on tmpfs
[/LIST]

I would have also reconfigured FF cache to go to /tmp, but couldn't since I don't have a way to right click!  :-P

On 11.10 alpha 2, the lines in [FONT="Courier New"]/etc/fstab[/FONT] for [FONT="Courier New"]/[/FONT] is:

```
UUID=XXXXXXX / ext4 errors=remount-ro,noatime 0 1
```

My [FONT="Courier New"]tmpfs[/FONT] line is:

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777,size=128m 0 0
```

When running [FONT="Courier New"]mount[/FONT], they look like this:

```

/dev/sda6 on / type ext4 (rw,noatime,errors=remount-ro,commit=0
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777,size=128m)

```

Things on the todo list:

[LIST]
[*]get 1440x900 native resolution
[*]control keyboard backlight
[*]setup trackpad scrolling
[*]setup two-finger trackpad click for right-click
[*]figure out fn+<left>,<right> for home,end
[*]figure out fn+<up>,<down> for page up, page down
[*]figure out fn+delete for PC delete
[*]figure out power management settings
[*]setup F-keys for screen dimming, keyboard dimming, and volume control
[*]convert caps lock to ctrl
[*]configure audio
[*]configure camera
[/LIST]

Thanks!

---

### Post by User4519 on 2011-07-27
Thanks for the tips on Intel graphics. I'm getting mine tomorrow, if UPS isn't lying to me, gonna be interesting to see when it'll be running Kubuntu problem-free :)

But,

> **berto- said:**
> I would **highly suggest** everyone run a few tweaks to conserve the SSD.  From the article at [http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html]("http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html")

Please only do noatime and other tweaks to gain performance. Those tips were given by a guy with an original Eee, that's like practically the dawn of time with regards to SSDs. These days, SSDs are theoretically more likely to live longer than you, even if you write to them continually.

[Here's a more recent article]("http://www.storagesearch.com/ssdmyths-endurance.html") (and in fact, **four** years old now, so expect even longer life with the newer drives) doing a little calculus on life expectancy of an 80G SSD if you were to write to it non-stop at 80 MB/s until it dies. **51 years later**.

What you **should** do, however, and that's not mentioned in your article link as it's too old, is choose an FS that is able to issue SSD TRIM commands (such as ext4 or btrfs), and remember to edit your fstab to enable said support (keywords "discard" for ext4, "ssd" for btrfs). Don't worry about swap, as it's already TRIM aware, and will issue the proper ATA commands out-of-the-box.

Don't worry about the life of your SSD - the logic board or your physical self will die before the memory cells do ;)

---

### Post by berto- on 2011-07-27
Hmm, good call.  I don't mind the [FONT="Courier New"]noatime[/FONT] for performance either, so I'm going to keep the setting.  Thanks for pointing out the [FONT="Courier New"]ext4[/FONT] TRIM option; I'll be adding [FONT="Courier New"]discard[/FONT] to the options straight away.

What's up with the option being called [FONT="Courier New"]discard[/FONT]?  Wouldn't [FONT="Courier New"]trim[/FONT] or [FONT="Courier New"]ssd[/FONT] like [FONT="Courier New"]btrfs[/FONT] make more sense?

One thing that might make a lot of sense is backups.  Apparently SSDs are not the most reliable.  So, while the SSD might not break because it's written to, it might just up and die anyway.  Check out this article at coding horror: [http://www.codinghorror.com/blog/2011/05/the-hot-crazy-solid-state-drive-scale.html]("http://www.codinghorror.com/blog/2011/05/the-hot-crazy-solid-state-drive-scale.html").

---

### Post by User4519 on 2011-07-27
> **berto- said:**
> What's up with the option being called [FONT="Courier New"]discard[/FONT]?  Wouldn't [FONT="Courier New"]trim[/FONT] or [FONT="Courier New"]ssd[/FONT] like [FONT="Courier New"]btrfs[/FONT] make more sense?

Totally agree :D I guess if you asked them, they'd probably have a really good reason. If anything, I think stuff like that ought to have some kind of standard, so that even if they thought "butterflies" would be the proper name to use, than all FSes would use it. I mean, it's noatime regardless of the filesystem AFAIK, why not stick with that consensus? :)

> **berto- said:**
> One thing that might make a lot of sense is backups.  Apparently SSDs are not the most reliable.  So, while the SSD might not break because it's written to, it might just up and die anyway.  Check out this article at coding horror: [http://www.codinghorror.com/blog/2011/05/the-hot-crazy-solid-state-drive-scale.html]("http://www.codinghorror.com/blog/2011/05/the-hot-crazy-solid-state-drive-scale.html").

Good link - I remember reading that after having bought my insanely expensive OCZ Vertex II 240G and thinking, "dammit!". I actually bought that SSD prematurely to add to either the ASUS or the Lenovo I was planning on getting, and now it turns out I'm getting an Air which won't eat my drive anyway. LOL, that's one lesson learned for not being so damn impatient next time :)

---

### Post by dfacto on 2011-07-27
Actually I am reading that discard may not be the best choice either. [This guy]("https://patrick-nagel.net/blog/archives/337") has found that his SSD is better off with an fstrim cron job....

---

### Post by dfacto on 2011-07-27
oops--dup

---

### Post by dfacto on 2011-07-27
@berto  That article is from Jan--if you use the xorg-edgers ppa then you get this and it still won't work.  It is possible that v2.15 intel driver will work tho as I haven't tried this (per Jonny's suggestion).

I should add that when I used xorg-edgers in Natty there was no improvement over the default install.  When I used edgers in Oneiric I wasn't even able to get the failsafe display device to work (so not even 1024x768 ).  This may actually be a good thing--it may mean that the intel driver was loading but that it bugged out.

I didn't save the log but I recall it was "/dev/fb0 missing" (this is the failsafe error).  The intel driver listed support for sandy bridge-integrated.  Anyway, I reverted to Natty and will upgrade if someone is able to get video to work (and this is a required step).

---

### Post by jonny on 2011-07-27
**dfacto** and **Sarvatt**, exactly which version(s) of Ubuntu did you use - ie 32/64 bit desktop/server, etc?  And how did you install it - did you use an external CD drive or DD a live USB onto a spare partition?  Did you use ReFIT or GRUB, and on which partitions?

There are recurrent horror stories on the web about recent Macs being completely borked by linux installations - even Michael Larabel of Phoronix [has fallen victim]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_apple&num=1") with a new generation Mac Mini - and, while I'm well up for compiling a fresh graphics stack from source, I'm rather keen to avoid destroying some shiny new hardware.

Reports of failure all seem to involve 64 bit installs without the use of ReFIT.  How did you keep the EFI demons at bay?

---

### Post by dfacto on 2011-07-27
I used 64bit-desktop-natty and 64bit-desktop-oneiric (the one specifically built for mac).  Both were the live cds which I booted from using a borrowed superdrive ($79...are you kidding me?!). I have the MacBookAir4,2. 

I installed both natty and oneiric (separately of course) by basically following the [mactel guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") in the ubuntu community docs.  It was a piece of cake.  Here are my steps (from memory so could be wrong).
```

 1) boot mac osx and install all/any updates
 2) install refit, reboot, choose mac os x
 3) start "disk utilities" and repartition mac osx to 32gb and the remaining to msdos (fat) [i hate so you may want to go 50/50 or something]
 4) shutdown
 5) power on and select resync from refit hit y then choose power down
 6) power on, load macosx and plug-in superdrive. insert natty or oneiric-alpha-2 
 7) reboot and select "boot from legacy cdrom" (there was also a bootx64.efi but i ignored it)
 8) when screen turns purple hit space bar
 9) select language
10) hit F6 then escape and after the "--" type " nomodeset" and hit enter (I couldn't understand the pop-up menu--better to just type it myself.)
11) load gparted and repartition the empty space; i did:
      (leftover...something like 70gb) ext4 /home
      12288   ext4  /
       6144   swap
12) "install ubuntu"
13) choose "other configuration" and map as above (also did reformat).  Also ***Important***: set boot drive to the "/" partition (for me this was sda4)
15) proceed with install
16) reboot select resync from refit and hit y.  power down from refit.
17) power on, choose ubuntu, type 'e' add "nomodeset" and hit F10
18) once in ubuntu edit /etc/default/grub to have nomodeset and then invoke update-grub

```
All set!

When all done I booted into mac osx and did the bless thing, ie ```
bless --device /dev/disk0s4 --setBoot --legacy
``` but it didn't seem to make any difference.  Note: your partition might be different, to find out: ```
diskutils list
```

During several points while trying to figure this out things seemed to hang--when that does I typed ctrl-shift-power to shut off.

If you use refit and a superdrive I *really* don't see how you could brick your machine.  Anyway, it should still be under warranty right?

[s]Finally regarding phoronix--this article is accurate but has nothing to do with bricking the machine.[/s]  High quality video will simply not work (as the article indicates).  You will be stuck at a fuzzy (stretched) 1024x768 until the intel video driver is fixed (this includes xorg-edgers as of this writing).
**OOPS:** Guess I didn't read far enough in!  Well that *is* scary but luckily no such issues on the MBA4,2 and of course phoronix was working with the mac mini.

---

### Post by Sarvatt on 2011-07-27
> **jonny said:**
> **dfacto** and **Sarvatt**, exactly which version(s) of Ubuntu did you use - ie 32/64 bit desktop/server, etc?  And how did you install it - did you use an external CD drive or DD a live USB onto a spare partition?  Did you use ReFIT or GRUB, and on which partitions?

There are recurrent horror stories on the web about recent Macs being completely borked by linux installations - even Michael Larabel of Phoronix [has fallen victim]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_apple&num=1") with a new generation Mac Mini - and, while I'm well up for compiling a fresh graphics stack from source, I'm rather keen to avoid destroying some shiny new hardware.

Reports of failure all seem to involve 64 bit installs without the use of ReFIT.  How did you keep the EFI demons at bay?

resized disk, installed refit, manually ran the refit install script afterwards, created natty livecd from 64 bit amd+mac desktop disk using this method:[http://www.devslashzero.com/node/160]("http://www.devslashzero.com/node/160"), rebooted into refit, picked the boot linux option, picked nomodeset in the installer menu and installed. the biggest headache in the whole process was that liveusb's created via usb-creator-gtk didn't work.

---

### Post by dfacto on 2011-07-27
@Sarvatt So what exactly is the difference between the vanilla amd64 desktop and the amd64+mac desktop?  I can't seem to find the distinction anywhere...

---

### Post by berto- on 2011-07-27
I can confirm a brick-free install of both 64-bit natty and 64-bit oneiric.  My process for installing was:

[LIST]
[*]resizing the partition
[*]installing rEFIt
[*]rebooting 3 or so times for rEFIt to show up when booting
[*]download an ubuntu ISO
[*]created hybrid ISO following instructions at [http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive]("http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive")
[*]booted into USB and installed
[*]switch between OS X and ubuntu using rEFIt at boot
[/LIST]

So far, no badness aside from not having the system dialed in.

---

### Post by berto- on 2011-07-27
> **dfacto said:**
> @Sarvatt So what exactly is the difference between the vanilla amd64 desktop and the amd64+mac desktop?  I can't seem to find the distinction anywhere...
This is a great question; I was wondering the same thing.

---

### Post by jonny on 2011-07-27
Thanks for the detailed steps on installing without bricking the device.  I'll give it a go over the weekend and I'll try building an up-to-date graphics stack, too.

I know it seems implausible that it's possible to damage a motherboard by installing Linux, but that is being reported around the web and is being seriously discussed in a couple of bug reports that I've read.  Some users have resuscitated their machines by running a firmware update, but others have reported that they've needed logic board replacements - which seem to be offered without question by Apple.

BTW, FWIW, my wife managed a £164 discount plus a £65 appstore voucher on her Air for simply being a student.  Interestingly, Apple didn't want to see any evidence of her educational status, and simply allowed me to buy the machine on her behalf.  If anyone is still in education, don't forget to ask for cash off - the discounts only seem to be promoted on line, so they're easily overlooked.  I mention it here, as this thread is likely to be read by prospective purchasers.

---

### Post by berto- on 2011-07-27
> **jonny said:**
> BTW, FWIW, my wife managed a £164 discount plus a £65 appstore voucher on her Air for simply being a student.  Interestingly, Apple didn't want to see any evidence of her educational status, and simply allowed me to buy the machine on her behalf.  If anyone is still in education, don't forget to ask for cash off - the discounts only seem to be promoted on line, so they're easily overlooked.  I mention it here, as this thread is likely to be read by prospective purchasers.

I second that.  My wife is a student and I got ~$60 off the machine + $100 App store coupon (USA).  In our case, they did ask for a student ID, or proof of registration by logging into the school's website.

---

### Post by dfacto on 2011-07-27
So I can confirm that it is possible to install from USB per Sarvatt's suggestion of [http://www.devslashzero.com/node/160]("http://www.devslashzero.com/node/160").  I am including my walk-through as I made minor deviations.  Standard disclaimer applies: PLEASE be careful with these commands noting that mkfs will erase all contents of the destination device.

The key "trick" from the blog is to NOT partition the usb drive (note the -I flag to mkfs.vfat).

[Here]("http://almostsure.com/mba42/setup_mac_usb_boot.sh") is a script which does the necessary steps.  You will need to modify the path to the usb device.

**UPDATE**:
In theory, starting with 11.10 (including daily builds) you can simply dd the iso to the usb drive (device not partition). See [this post]("http://ubuntuforums.org/showpost.php?p=10945413&postcount=1") for detailed instructions.  Here are the steps I took (after replacing sdX of the fourth line with the correct letter--for me this was "sdb").
```

sudo aptitude install zsync
# Daily Builds: http://cdimage.ubuntu.com/daily-live/current/
zsync http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64+mac.iso.zsync
sudo fdisk -l # to find the correct device
sudo dd if=oneiric-desktop-amd64+mac.iso of=/dev/sdX oflag=direct bs=1048576
# if dd gives problems, drop the "oflag=direct bs=1048576"

```
I also [used gparted]("http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#extrapart") to allocate the unused space.

However, I haven't had luck with this approach.

---

### Post by dfacto on 2011-07-27
@jonny How out-of-date is xorg-edgers?  I just ask because I question if its worth the effort/electricity for you to try "building an up-to-date graphics stack, too"... I'm guessing [our sarvatt]("https://wiki.ubuntu.com/Sarvatt") is an xorg-edgers maintainer and he seems to be all over this problem.

From  [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty") you can see that natty builds are frequent and that he is listed as maintainer.

Perhaps there is some other way we can be more helpful? (@Sarvatt et. al.)

---

### Post by dfacto on 2011-07-27
So since we're waiting on the graphics driver...anyone get their touchpad working right?  All I have is standard mouse movement and primary click capability.

I posted in the [mtrack thread]("http://ubuntuforums.org/showthread.php?p=11093861#post11093861") and in the [bcm5974 thread]("http://ubuntuforums.org/showthread.php?p=11093913#post11093913").  I'm stumped on how to debug this further.  Again it seems, end-of-the-line for me. :(

---

### Post by berto- on 2011-07-28
@dfacto For the trackpad, have you tried the mactel support PPA at [https://launchpad.net/~mactel-support/+archive/ppa]("https://launchpad.net/~mactel-support/+archive/ppa")?  My system is currently on Oneiric and the PPA only goes up to Natty so I've not tried it yet.

```
sudo add-apt-repository ppa:mactel-support/ppa
audo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2B97B7B8
```

---

### Post by berto- on 2011-07-28
I noticed when rebooting my machine the rEFIt menu would take about 20 seconds to show up.  I found the post below that says to reset the PRAM by holding down cmd+option+p+r and letting the machine chime twice before letting go.

After that rEFIt shows up nice and quick again.

[http://scothoser.blogspot.com/2007/09/slow-boot-process-on-mac-try-clearing.html]("http://scothoser.blogspot.com/2007/09/slow-boot-process-on-mac-try-clearing.html")

---

### Post by dfacto on 2011-07-28
@berto This was the first thing I tried. :)  No good.

Also good to know about the PRAM trick.  Eventually I think we will have a nice *consolidated* collection of tips in this thread!

---

### Post by dfacto on 2011-07-28
So I am just learning about this video card business as we go but here is why having to boot with "nomodeset" officially qualifies as a bug. (Although everyone but me probably already knows this...)

By setting "nomodeset" as a kernel parameter you are disabling kernel mode setting (KMS), ie, essentially telling the kernel to not handle video and let the specific driver handle it.  The driver for new intel cards exclusively relies on KMS so by disabling KMS you are effectively disabling the intel video driver by selecting nomodeset.  The nvidia driver is  designed similarly but I believe the radeon driver still supports user mode setting (ie not kernel mode setting).

Since this driver is disabled, xorg falls-back to the fbdev for display.  The fbdev has limited resolution support which is why we are limited to 1024x768 resolution.

Bottomline: if you wish to test different intel driver builds and you booted with nomodeset (because you added it to grub per my suggestion) make sure to reboot and remove this option when in grub.  To do this, enter into grub, hit 'e', delete nomodeset, and hit 'F10'.  (I have been testing by "sudo service gdm restart" from tty1 so my tests have been inadequate.)

Cheers

---

### Post by dfacto on 2011-07-28
So [here]("http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image") is the answer as to what is different about the amd64+mac desktop install.

Speaking from my experience, if you use refit the amd64+mac iso is not needed.  You will see two boot options (in refit) for the live cd or usb if thats what you're using.  One option is boot using bootx64.efi (IIRC) and the other is boot using legacy.  Choose the legacy mode and you'll be fine.

---

### Post by dfacto on 2011-07-28
We can monitor the progress of the intel driver [here]("http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/log/?showmsg=1") and track our bug [here]("https://bugs.freedesktop.org/show_bug.cgi?id=39533") (same link as provided by Sarvatt--just trying to consolidate information).  Then once the fix gets committed it should make its way to [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty").

---

### Post by DrMeers on 2011-07-29
I created [http://help.ubuntu.com/community/MacBookAir4-2]("http://help.ubuntu.com/community/MacBookAir4-2") to log my experience before stumbling upon this thread; glad to see there are others out there working on this also!

Edit: moved content from wiki to here:

> I believe this is the correct name for the 13-inch 2011 MacBook Air?

I bought one with the 1.8GHz i7 option intending to run Ubuntu on it full-time given the positive compatibility reports for the 2010 models. In some regards it appears more compatible, however the main problem is the Intel HD 3000 graphics card, which it appears is not yet compatible with Xorg. The device remains "UNCLAIMED" according to lshw -C video, and I was unable to figure out how to get Ubuntu to use anything higher than 1024x768 resolution (which is obviously also the wrong aspect ratio).

The wireless and touchpad worked out of the box.

Geekbench gave a score of 6340 in Ubuntu, higher than the 5800 from within Lion.

Had all sorts of fun with the GPT/MBR partitioning, and rEFIt kept selecting the wrong ext4 partition for booting when I tried to create a separate data partition. Deleting it seemed to work. At one point the partition table got corrupted so that even "parted" would segfault trying to print it. Installing "gdisk" on OS X repaired this by deleting the troublesome partition. Though in the process I also managed to lose my Lion Recovery partition. It seems the only way to get this back is to Command-R boot, wait 30-60 minutes for the recovery utility to download from the network and then reinstall Lion. Though if you've mucked about with Ubuntu partitions, chances are Disk Utility will refuse to edit your partitions anymore anyway, so fix them up using Ubuntu (or the Recovery mode on the alternate installer CD). -- or, it may be possible to use DiskUtility to "convert" the 1.39GB recovery image to a saved image on the HDD, and reinstate it as a partition?

I had to use the "alternate" installer with "nomodeset" to get Natty in. Oneiric alpha2/daily-july-28 installers halted with an error at 71% of installing the core system. I tried all sorts of combinations, but superdrive with alternate i86 Natty installer was the only way that worked for me; I almost got syslinux'd USB to work, but it halted with an error.

I added the touchpad drivers to the SUSPEND list, but Ubuntu still refused to wake from suspend.

After messing about for a couple of days I've decided that I'll try to use Mac OS until the Intel HD 3000 drivers are released; even if I can get it to use the correct resolution somehow, without the drivers I don't think we'll get brightness control, correct suspend behaviour, etc. So; bring on the Intel HD 3000 drivers!

Has anyone tried these: [http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers) / [http://launchpad.net/~oibaf/+archive/graphics-drivers/](http://launchpad.net/~oibaf/+archive/graphics-drivers/) ?

---

### Post by dfacto on 2011-07-29
@DrMeers  Thanks for taking the time to start a wiki.  However, I am concerned that your bad luck may dissuade people from putting Ubuntu on their new MBA.  Many of us had no issues at all and are simply waiting for an intel driver bugfix (which btw is done and waiting on someone to give it a try).

Perhaps you would consider moving your log to the forums here and either you or someone else can replace it with the information in this thread (USB disk, step-by-step install, etc)?  I certainly do think its important that people know the risks but I would hate for this to turn people away particularly since I am quite pleased with the progress we have made and am optimistic that we will have an intel driver in the coming week if not weekend.  (Leaving only multitouch and suspend to be supported.)

Oh yes, and to set-up xorg-edgers, FIRST go read this [disclaimer]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty").

Next install aptitude if haven't done so already (why its better: [1]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/") and [2]("http://www.andrewault.net/2010/05/03/aptitude-vs-apt-get-comparison-2/")).
```

sudo apt-get install aptitude

```

Then,
```

sudo aptitude install ppa-purge
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update && sudo aptitude safe-upgrade
# Make sure to do safe-upgrade; do NOT pick and choose packages.

```

Or, to install only the bleeding-edge drivers (and not bleeding-edge xserver)
```

# no need to do this AND xorg-edgers/ppa
sudo aptitude install ppa-purge
sudo add-apt-repository ppa:xorg-edgers/drivers-only
sudo aptitude update && sudo aptitude safe-upgrade

```

To actually test the new intel driver make sure to remove nomodeset from your kernel boot line in grub.

If you have some kind of a problem (I didn't) then:
```

sudo ppa-purge ppa:xorg-edgers/ppa
# or if installed it:
#sudo ppa-purge ppa:xorg-edgers/drivers-only

```


Note: I have not tried drivers only--I have installed (and upgraded to) the xorg-edgers ppa.

---

### Post by gschwind on 2011-07-29
Hello, 

Do some one try pure EFI boot ?

For the keyboard issue, this is probably due to a new hardware id, so a very simple kernel patch should solve the issue. (same issue was found for MBA 3,1 & 3,2).

thanks for your reports

---

### Post by dfacto on 2011-07-29
> **gschwind said:**
> Hello, 

Do some one try pure EFI boot ?

For the keyboard issue, this is probably due to a new hardware id, so a very simple kernel patch should solve the issue. (same issue was found for MBA 3,1 & 3,2).

thanks for your reports

I have not tried pure EFI--I'm a tad afraid to actually.

Have you already filed a bug for keyboard?  Also, do you mean keyboard or touchpad (or both)?

---

### Post by gschwind on 2011-07-29
I did not filled bug for MBA 4,2. I don't own one MBA 4.

---

### Post by dfacto on 2011-07-29
Well I tried to modify the bcm5974 driver source myself but it didn't work and I don't know why.  I have attached the patch file I used and my devices list.  You can get the bcm5974 source from:
```

git clone http://bitmath.org/git/bcm5974-dkms.git

```

---

### Post by DrMeers on 2011-07-29
> **dfacto said:**
> @DrMeers  Thanks for taking the time to start a wiki.  However, I am concerned that your bad luck may dissuade people from putting Ubuntu on their new MBA. 

Agreed; moved content to my original post, and left a link to this thread.

---

### Post by dfacto on 2011-07-31
So good news!  I got the multitouch to work meaning you can scroll with two fingers (among other things).

```

# (1) Get my patched bcm5974 driver.
# You can find the source in: http://www.almostsure.com/bcm5974
# ref: http://bitmath.org/code/bcm5974-dkms/
wget http://www.almostsure.com/bcm5974/bcm5974-dkms_1.1.91_all.deb

# (2) Install it.
sudo dpkg -i bcm5974-dkms_1.1.91_all.deb

# (3) Edit the boot script.
sudo gedit /etc/rc.local
# add the following three lines before the "exit 0" line:
modprobe -r usbhid
modprobe bcm5974
modprobe usbhid

# (4) Install the xserver driver.
# ref: https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty
sudo add-apt-repository ppa:mactel-support/ppa
sudo aptitude update
# ref: http://ubuntuforums.org/showthread.php?t=1334696
sudo aptitude install xf86-input-multitouch

# (5) Edit xorg.conf.
sudo gedit /etc/X11/xorg.conf
# add the following six lines
Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
    MatchDevicePath "/dev/input/event*"
EndSection

# (6) Reboot.
sudo reboot


```

[Alternate xserver driver; replaces steps 4 and 5.]
```

# (4) Install the xserver driver.
# xserver-xorg-input-mtrack - Xorg Multitouch Trackpad Driver
# ref: http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/
# ref: http://ubuntuforums.org/showthread.php?t=1730361
wget http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb
# ref: https://github.com/BlueDragonX/xf86-input-mtrack
dpkg -i xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb

# (5) Edit xorg.conf.
sudo gedit /etc/X11/xorg.conf
# add the following six lines
Section "InputClass"
   MatchIsTouchpad "on"
   Identifier      "Touchpads"
   Driver          "mtrack"
   MatchDevicePath "/dev/input/event*"
EndSection

# (6) Reboot.
sudo reboot


```


After rebooting you can see some simple options in System->Preferences->Mouse->"Third Tab".  If the the third tab isn't there open a terminal and type synclient then check again.

The /etc/rc.local thing is a total kludge but I couldn't get blacklisting to work.  Suggestions welcome!  Also, poke around the forums to see what fancy things you can add to your xorg.conf to make it work even more like mac os x.

Cheers!

---

### Post by jonny on 2011-08-02
dfacto, thanks for your guide on making a bootable USB stick for use on a Macbook.  You should consider adding this to the Ubuntu wiki pages - it worked perfectly and saved me from buying an outrageously priced Apple external CD drive.  The only caveat that I'd add is that, if you use Ubuntu 10.04 LTS (Lucid) to create the bootable USB drive, there's a bug in syslinux which results in an error message when you attempt to boot.  It's easily fixed by editing syslinux/syslinux.cfg on the USB stick and removing the 'ui' from the line 'ui gfxboot bootlogo' - see [this link]("http://alexsleat.co.uk/2010/11/27/how-to-fix-unknown-keyword-in-configuration-file-ubuntu-usb-boot/")

---

### Post by karlkoch23 on 2011-08-02
> **dfacto said:**
> Exactly my sentiments as well.  I own a vaio z-series from 2008 (the first of this line) and it has ALWAYS been a nightmare.  I will never buy a sony ever again.  Hence Apple becomes the lesser of evils.

I sooooooooooo agree I had the Z Series as well and it looked great, but starting falling apart after working with it for 6 month...speed with an SSD was fantastic....
I also considered a MacAir, but in the end my despise for apple was strong enough...just looking at the pricing and their waranty policy made me go to the more heavy but much more sturdy X220 Tablet... I had to adjust to the different design, but after wanting to switch hardware components and finding how extremly easy it was made me understand why so many professionals are running around with thinkpads....

---

### Post by dfacto on 2011-08-02
@jonny Good to know.  Once we get a system with the essentials working we can transfer and cleanup this thread into the wiki.  Right now it just links back here.

Recap:
Everything now works except:

1) suspend (haven't tried hibernate), and
2) the intel graphics driver.

Aside from these issues, the only thing that needs some post-install tinkering is the [multitouch driver]("http://ubuntuforums.org/showpost.php?p=11106203&postcount=59").  I updated my [xorg.conf]("http://www.almostsure.com/bcm5974/patch/xorg.conf") which should get you started.  I am using the xserver-input-mtrack driver not the xserver-input-multitouch.

There is a bug report open on the graphics driver.  Sarvatt seems to be taking care of this.

As far as suspend, I haven't looked at this.  It would be nice if someone else could look into this as I am pretty busy these days.

Cheers

---

### Post by orangegold on 2011-08-02
How were you able to get the audio to work?  Can you show me what drivers / configuration you're using?

---

### Post by dfacto on 2011-08-02
> **orangegold said:**
> How were you able to get the audio to work?  Can you show me what drivers / configuration you're using?

open terminal, run alsamixer, unmute surround.

---

### Post by jonny on 2011-08-02
I'm having trouble with the trackpad - I can't get the third tab to display in the mouse preferences dialogue.  Running synclient doesn't help - it can't seem to find any synaptics device.  I've tried both drivers that you suggested - any thoughts on how to debug this?

---

### Post by qweefb on 2011-08-02
Hey guys, 

I am a newbie to Linux and I bought a MacBook Air. Since I am greatly interested in Linux, I want to install Ubuntu on my new MacBook Air. I have no superdrive so I tried the USB installation method mentioned here [http://ubuntuforums.org/showpost.php?p=10886829&postcount=320](http://ubuntuforums.org/showpost.php?p=10886829&postcount=320). However, unetbootin does not work on Lion. What can I do if I want to install Ubuntu by using USB thumb drive?

---

### Post by jonny on 2011-08-03
> **qweefb said:**
> Hey guys, 

I am a newbie to Linux and I bought a MacBook Air. Since I am greatly interested in Linux, I want to install Ubuntu on my new MacBook Air. I have no superdrive so I tried the USB installation method mentioned here [http://ubuntuforums.org/showpost.php?p=10886829&postcount=320](http://ubuntuforums.org/showpost.php?p=10886829&postcount=320). However, unetbootin does not work on Lion. What can I do if I want to install Ubuntu by using USB thumb drive?
The way that worked for me was to create a USB stick using the method described in [earlier]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43") in this thread.  However, note that this assumes that you already have access to a Linux machine - can a friend help you out, perhaps.  Also note that if you use Ubuntu 10.04 LTS Lucid to create the stick, you'll need to fix a bug as described by me a few posts back.  Finally, note that you'll fail to boot from the USB stick on a Macbook Air unless you add nomodeset to the boot line - again, this is described earlier in the thread.

---

### Post by qweefb on 2011-08-03
> **jonny said:**
> The way that worked for me was to create a USB stick using the method described in [earlier]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43") in this thread.  However, note that this assumes that you already have access to a Linux machine - can a friend help you out, perhaps.  Also note that if you use Ubuntu 10.04 LTS Lucid to create the stick, you'll need to fix a bug as described by me a few posts back.  Finally, note that you'll fail to boot from the USB stick on a Macbook Air unless you add nomodeset to the boot line - again, this is described earlier in the thread.

Actually, I have a Ubuntu virtual machine on my iMac. I will have a try when I go home. Thanks for your help!

---

### Post by f00fc7c8 on 2011-08-03
FWIW, the 11.10 daily builds can be dd'ed straight to a USB stick and booted on the Air since Ubuntu finally [switched to using hybrid disc images]("http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html").

---

### Post by dfacto on 2011-08-03
Stick this in your .bash_aliases:
```

keybacklight () { echo $(($1*$1*255/100)) | sudo tee /sys/devices/platform/applesmc.768/leds/smc\:\:kbd_backlight/brightness; }

```
Then type keybacklight 5 (or some number between 0 and 10) to be able to adjust the keyboard backlight.

---

### Post by qweefb on 2011-08-04
I have successfully  installed Natty on my MacBook Air. However, are there any ways to adjust the birghtness of the monitor? Also, I followed the instruction to install the bcm5974 but multitouch still doesn't work.

Also, I don't find /etc/X11/xorg.conf file. Should I make one?

---

### Post by preacher37 on 2011-08-04
FYI, I booted my MBA 2011 with Ubuntu installed while having my new mini display port to HDMI-cable attached to my external widescreen monitor. I did not use "nomodeset" while booting.

No image on laptop screen but 1920x1080 resolution external monitor, using Intel drivers.

Not much help when you want to go mobile but at least it seems the intel driver is working fine, just not together with the laptop screen (yet).

Btw, has anyone managed to get bluetooth working?

---

### Post by dfacto on 2011-08-04
@preacher37 Thanks for the info; I cross-posted your comment to the [bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").

I haven't tried bluetooth so I can't help.  Have you gotten your fn key to work? (I miss pageup/down.)

---

### Post by berto- on 2011-08-04
> **qweefb said:**
> Also, I don't find /etc/X11/xorg.conf file. Should I make one?

You need to logout, drop to a console, stop [FONT="Courier New"]gdm[/FONT], and then run the command:

```
Xorg -configure
```

---

### Post by dfacto on 2011-08-04
**UPDATE (9/15)**:
Scripts to get Ubuntu Oneiric 11.10 running nicely on MBA 13" (11" coming soon!):
[LIST]
[*][setup_mac_usb_boot.sh]("http://almostsure.com/mba42/setup_mac_usb_boot.sh") script to show you how to make a mac bootable usb drive
[*][post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh") script to get oneiric configured for the MBA 11" and 13"
[/LIST]
Code [post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh") will automatically download:
[LIST]
[*][fix-i915.sh]("http://almostsure.com/mba42/fix-i915.sh") script to apply a hack to make video work
[*][keyboard-backlight]("http://almostsure.com/mba42/keyboard-backlight") script to control the keyboard backlight
[*][dotXmodmap]("http://almostsure.com/mba42/dotXmodmap") settings to make the mouse "reverse scroll" and swap alt/super to be more like a PC
[*] [btusb.patch]("http://almostsure.com/mba42/btusb.patch") update bluetooth driver for MBA4
[*][bcm5974.patch]("http://almostsure.com/mba42/bcm5974.patch") update trackpad driver for MBA4
[*][hid-apple.patch]("http://almostsure.com/mba42/hid-apple.patch") update keyboard driver for MBA4
[/LIST]
Additional code that is not used but could be useful to some people:
[LIST]
[*][pommed.patch]("http://almostsure.com/mba42/pommed.patch") update pommed program for MBA4
[/LIST]


**UPDATE (9/12)**: A lot of this is out-dated (esp. if you're installing Oneiric) since it was too hard to describe the difference between the "new way" and the "old way."  Basically all you need to do is run either,
[post-install-natty.sh]("http://www.almostsure.com/mba42/post-install-natty.sh"),
or
[post-install-oneiric.sh]("http://www.almostsure.com/mba42/post-install-oneiric.sh"),
depending on which flavor of Ubuntu you are using.  The Natty script should work for versions prior to Natty as well.  In fact, the Oneiric script should ALSO work for any version (in theory) but has only ever been tested on Oneiric.  The Oneiric version uses more recent drivers, but will need to be re-run after every kernel update.  The Natty version uses older drivers but they automatically recompile themselves when you get a new kernel.  However, since the [fix-i915.sh]("http://www.almostsure.com/mba42/fix-i915.sh") script relies on the same methods of the Oneiric script, you will likely have to manually re-run the script after each kernel update.  (More details [here]("http://ubuntuforums.org/showpost.php?p=11240635&postcount=257").)

Bottomline: The Oneiric script is preferable (despite extra maintenance), but no one has told me if it works for versions other than Oneiric.

----

Here are all of the tweaks I've made so far.  I will keep updating this post so there is a central source of information.(*)  Just to recap, I edited both the trackpad driver and the keyboard driver as well as various conf files.  The driver patches may or may not make it into oneiric (the patches were submitted however).  At this point everything works for me except the video driver and suspend (I have not tested the microphone).
**Update Aug 7**: Thanks to [koadman]("http://ubuntuforums.org/showpost.php?p=11126406&postcount=80"), the btusb dkms now works (although I personally have not tested it).  Post-install.sh has been updated.

My [post-install.sh]("http://www.almostsure.com/mba42/post-install.sh") script installs all the tweaks that I'm currently using. It isn't really tested so someone should go through and run each line manually and alert me if there are bugs (or if it works).

The script optionally relies on these four files:
[bcm5974-dkms.patch]("http://www.almostsure.com/mba42/bcm5974-dkms.patch")
[hid-apple-dkms.patch]("http://www.almostsure.com/mba42/hid-apple-dkms.patch")
[dotXmodmap]("http://www.almostsure.com/mba42/dotXmodmap")
[xorg.conf]("http://www.almostsure.com/mba42/xorg.conf")

If it doesn't find these files in the current working directory then it continues gracefully. That is, if you don't want to build the debs yourself using my patches, you can just NOT download the patch files and pre-built debs will be downloaded. (Regarding the config files, if you don't want 'em installed, don't download 'em).

(Note: I know the Xmodmap has obvious bugs in it--I would love if someone figured out the right key codes/maps for me! :))

For reference, the pre-built debs are here:
[hid-apple-dkms_1.0.3_all.deb]("http://www.almostsure.com/mba42/working/hid-apple-dkms_1.0.3_all.deb") - MBA4,2 Keyboard Support
[bcm5974-dkms_1.2.0_all.deb]("http://www.almostsure.com/mba42/working/bcm5974-dkms_1.2.0_all.deb") - MBA4,2 Trackpad Support

And you can see all files from this directory:
[http://www.almostsure.com/mba42/](http://www.almostsure.com/mba42/)

Also, for reference, here is my [setup_mac_usb_boot.sh]("http://www.almostsure.com/mba42/setup_mac_usb_boot.sh") script to make a mac bootable flash drive. (Note that [jonny]("http://ubuntuforums.org/showpost.php?p=11110359&postcount=60") has an additional comment regarding lucid which I have not incorporated into this script. Also note that [f00fc7c8]("http://ubuntuforums.org/showpost.php?p=11115809&postcount=69") points out that future Ubuntu releases will be much [easier to make bootable USB images]("http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html").)

(*) - It would be really great if someone transferred all of this information into the [MacBookAir4-2 wiki]("https://help.ubuntu.com/community/MacBookAir4-2").  I'm pretty much tapped out here.  The [MacBookPro8-1Natty]("https://help.ubuntu.com/community/MacBookPro8-1/Natty") looks nice and should be our template (the other MBA ones seem not so polished).  Also just to motivate you: the more people that use linux on MBA, the more support YOU have! :)

---

### Post by berto- on 2011-08-04
> **preacher37 said:**
> FYI, I booted my MBA 2011 with Ubuntu installed while having my new mini display port to HDMI-cable attached to my external widescreen monitor. I did not use "nomodeset" while booting.

No image on laptop screen but 1920x1080 resolution external monitor, using Intel drivers.

Not much help when you want to go mobile but at least it seems the intel driver is working fine, just not together with the laptop screen (yet).

Btw, has anyone managed to get bluetooth working?

Just for kicks, what if you have the display port -> HDMI connected to the laptop, but no monitor?  Does the laptop screen work?

---

### Post by preacher37 on 2011-08-05
> **berto- said:**
> Just for kicks, what if you have the display port -> HDMI connected to the laptop, but no monitor?  Does the laptop screen work?

Good suggestion, I will check this as soon as I can. Am at work now and a bit busy tonight though, but will try to squeeze it in.

@dfacto: Great work at cataloging all the tweaks and general troubleshooting! Have not gotten as far as fn-keys yet I'm afraid, just been playing around with the install in my limited free time.

---

### Post by dfacto on 2011-08-05
> **preacher37 said:**
> Good suggestion, I will check this as soon as I can. Am at work now and a bit busy tonight though, but will try to squeeze it in.

@dfacto: Great work at cataloging all the tweaks and general troubleshooting! Have not gotten as far as fn-keys yet I'm afraid, just been playing around with the install in my limited free time.

No problemo. :)  Just waiting on this modeset kernel issue and we'll be set!

---

### Post by preacher37 on 2011-08-06
> **berto- said:**
> Just for kicks, what if you have the display port -> HDMI connected to the laptop, but no monitor?  Does the laptop screen work?

Unfortunately no change, that is: without nomodeset just a black screen, with nomodeset fbdev and 1024x768 resolution.

---

### Post by koadman on 2011-08-06
Hi all, I just received a (shiny, new) 13" macbook air and have been following the discussion here to get ubuntu running.  Many thanks to all of you!

Things are not yet running as well as they should based on dfacto's suggestions, and I have some questions about that.  But first, I'd like to contribute something.  I looked into the **bluetooth** issue and it seems to have been as easy as adding the correct vendor hardware codes to btusb.c.  I've made an updated .deb with the driver and posted it here:
[URL="http://edhar.genomecenter.ucdavis.edu/%7Ekoadman/btusb-dkms_1.0-maverick-mactel4_all.deb"]http://edhar.genomecenter.ucdavis.edu/~koadman/btusb-dkms_1.0-maverick-mactel4_all.deb
[/URL]
install with sudo dpkg -i 
and then reboot and your bluetooth should be working.

Also of note for folks planning to use dfacto's script to build their  kernel modules, you may need to install `sudo apt-get install debhelper`  before the script will work (at least the current version as of August  6th requires this).

Now for my questions...  I followed dfacto's instructions and used his scripts with a few changes required to fit my system.  Unfortunately I am not able to use an external display with or without nomodeset, the kernel will not boot and instead complains about something being corrupt immediately after grub (sorry don't have the exact error message handy right now).  Anyone else experiencing this?

---

### Post by dfacto on 2011-08-07
@koadman Thanks for updating the btusb.  When I sent my patches to the kernel team I was informed that most of the apple-related dkms modules that were floating around were pretty out of date.  Since it would be nice to get your patch into oneiric (I think there is just barely enough time) you may want to get in touch with the kernel team.  

I subscribed to [kernel-team@lists.ubuntu.com]("https://wiki.ubuntu.com/KernelTeam/") and just mentioned that I need help and that I patched the keyboard/mouse dkms's.  Then a very friendly [canonical developer]("https://launchpad.net/~chasedouglas") walked me through the process of making a patch.  It took a total of an hour (and would have taken 5min if not for my fumbling around).

Also please let me know what specifically didn't work in the post-install script and I will fix it. (Already added debhelper and a wget to your btusb-dkms.)

If you prefer, you can send me your patch and I can repeat the process on your behalf (although it won't be signed off by you which is a pity for you since I think its cool to have contributed, minor though it may be).

Cheers!

PS Once you have the exact error maybe I can help...not sure what it could be otherwise...

---

### Post by koadman on 2011-08-07
@dfacto: The changes for btusb.c are really simple and you're welcome to contribute them to the linux kernel devs on my behalf and take all the credit.  [Patch here]("http://edhar.genomecenter.ucdavis.edu/%7Ekoadman/btusb.diff").  One thing I wonder about is whether bluetooth 4 has any new features that aren't supported by btusb.c, in which case the functionality might still be limited even with that little patch.  I'm no bluetooth expert.

On a different topic, I accidentally discovered  that I am able to boot without nomodeset so long as I use the fbdev driver.  Perhaps this is already known but I didn't see mention in the thread. I get a full resolution display, but it seems that the framebuffer is boxed into 1280x800 in the upper left corner.  The remaining pixels at right and below show repeated garbage of the upper right sides.  It's still nowhere near perfect but for me it beats looking at a blurry 1024x768 until the drivers are fixed.  I made some efforts to get the full 1440x900, including xrandr mentioned earlier in the thread and setting the video res to 1440x900 on the grub kernel command-line but nothing has worked so far.

---

### Post by dfacto on 2011-08-07
@koadman How on earth did you get 1280 to work?  I thought I tried everything!

I will go a head and make the patch.

---

### Post by koadman on 2011-08-07
Dunno how it happened.  Maybe it's the karma I get from having used linux as my main OS for 13 years :)

If I tell the kernel to do 1440x900 with video-*VGA*-*1*:1440x900 on the grub commandline I can get 1440x900 virtual display res but its squished into the 1280x800 pixel frame.  Maybe that info is useful to someone somewhere.  This is all happening on a stock 2.6.38-10 kernel from natty.  I tried the patched 3.0.0 kernel from sarvatt's page and get a crasher instead.

---

### Post by dfacto on 2011-08-07
> **koadman said:**
> Dunno how it happened.  Maybe it's the karma I get from having used linux as my main OS for 13 years :)

If I tell the kernel to do 1440x900 with video-*VGA*-*1*:1440x900 on the grub commandline I can get 1440x900 virtual display res but its squished into the 1280x800 pixel frame.  Maybe that info is useful to someone somewhere.  This is all happening on a stock 2.6.38-10 kernel from natty.  I tried the patched 3.0.0 kernel from sarvatt's page and get a crasher instead.

This doesn't work for me (assuming you meant video**=**VGA-1:1440x900).  Are you using xorg-edgers?  What does your xorg.conf look like?  What else is on your boot parameter line?  I want 1280 so badly I could scream!  Also Im surprised VGA-1 is what you used I was tryiing LVDS1 and LVDS-1....

Update 1: I ppa-purged xorg-edgers and stripped down my xorg.conf and I still only get a blank screen.  I can't figure out how you did this! :(

Update 2: Koadman, what is your display model? 
```

sudo aptitude install read-edid
sudo get-edid 2>/dev/null|strings -5

```

Mine is:
```

LP133WP1-TJA3
Color LCD

```
(which is a LG/Philips product code; also I have the SM128C SSD.)

---

### Post by koadman on 2011-08-07
Aha! I seem to have a samsung LCD, along with the 256GB ssd.

sudo get-edid 2> /dev/null | strings -5
LTH133BT01A03
Color LCD

Never occurred to me to try LVDS instead of VGA, I'll give that a go.  Suspend works for me, need to look into hibernate next.  I accidentally set my swap space too small for hibernate but thankfully still have some room to grow it.

---

### Post by dfacto on 2011-08-07
> **koadman said:**
> Aha! I seem to have a samsung LCD, along with the 256GB ssd.

sudo get-edid 2> /dev/null | strings -5
LTH133BT01A03
Color LCD

Never occurred to me to try LVDS instead of VGA, I'll give that a go.  Suspend works for me, need to look into hibernate next.  I accidentally set my swap space too small for hibernate but thankfully still have some room to grow it.

How exactly are you using the fbdev driver?  Can you share your xorg.conf so we can make sure we are using the same configuration? Also do you have i7 or i5?

---

### Post by koadman on 2011-08-07
It's an i5.  I just tried setting video=LVDS-1:1440x900 to no effect.

I [posted my xorg.conf]("http://edhar.genomecenter.ucdavis.edu/%7Ekoadman/xorg.conf") 
I'm guessing the xorg.conf may not have much to do with getting 1280x800 since the fb consoles all have that res too (and the annoying tiling in the lower right corner).  I think that suggests it's coming from within the kernel driver not X.

No luck with hibernate even after I had swap sized big enough.  Some error message about not being able to connect to the disk but I'm not sure if that's related.

---

### Post by koadman on 2011-08-07
I've been playing with getting power usage down using suggestions from powertop.  So far the lowest I've been able to achieve is about 7.7 watts.  This is with a fully dimmed screen, not running any compute, sata power management, audio power management, usb autosuspend, and bluetooth disabled.  Disabling the wifi seems to make no difference.  Disabling bluetooth and dimming the screen helped the most.

Here's some commands to run as root to achieve the effect:

hciconfig hci0 down ; rmmod hci_usb
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1 | sudo tee /sys/bus/usb/devices/2-1.1/power/autosuspend
echo 1 | sudo tee  /sys/devices/virtual/backlight/acpi_video0/brightness 

With these settings the ACPI claims I'll be getting 7-8 hours of battery, depending on how much I touch the mouse (trackpad seems to be the biggest remaining power hog!)

My previous lappie, an Asus UL30A, could run at 4.5W.  I miss it already...

---

### Post by dfacto on 2011-08-07
Yeah--Im so sick of KMS right now.  I literally wasted the whole day trying to do better than 1024x768.  I guess its back to sitting on my hands and waiting for this bugfix.

The thing that stinks is that OS X is terrible!  You can't change the font size and you can't change resolution without making it ridiculously blurry.  I thought OS X was supposed to be "the world's most advanced operating system!"  Sigh...

---

### Post by qweefb on 2011-08-08
@dfacto

Thanks for your post-install.sh. However, I can't use it on my MacBook Air4,1. It said it supports MacBook Air 4,2 only. I tried to remove the code which are used for checking the computer model since I guessed the drivers can run on both models. After that, I ran the shell script but some error messages were shown when running. Anyway, thank you very much! :D 

I've just removed Ubuntu on my MacBook Air 4,1 and wait for the full installation guide.

---

### Post by dfacto on 2011-08-08
> **qweefb said:**
> @dfacto

Thanks for your post-install.sh. However, I can't use it on my MacBook Air4,1. It said it supports MacBook Air 4,2 only. I tried to remove the code which are used for checking the computer model since I guessed the drivers can run on both models. After that, I ran the shell script but some error messages were shown when running. Anyway, thank you very much! :D 

I've just removed Ubuntu on my MacBook Air 4,1 and wait for the full installation guide.

You can just hit y to continue anyway....

And Im not sure what errors you are referring to... I only put the warning because I personally have only tested it on my macbookair4,2.  Everything should be the same with the possible exception of the device ids for the keyboard and trackpad.  And *if* that's the case nothing would happen (it would neither cause a problem nor work).

---

### Post by qweefb on 2011-08-08
> **dfacto said:**
> You can just hit y to continue anyway....

And Im not sure what errors you are referring to... I only put the warning because I personally have only tested it on my macbookair4,2.  Everything should be the same with the possible exception of the device ids for the keyboard and trackpad.  And *if* that's the case nothing would happen (it would neither cause a problem nor work).

Oooops.... I didn't notice that.

Thank you very much! I will have a try later!:D

---

### Post by ben.fazekas on 2011-08-10
Hi Guys,

i am planning to buy a macbook air if (rather big IF) i can install linux/ubuntu on it. I short of reviewed this thread and the bigest problem seems to be the graphic driver, or the lack of it. as i checked out there is an intel driver for the intel 3000hd integrated in the core i5/i7 processors. [see [http://intellinuxgraphics.org/documentation.html]("http://intellinuxgraphics.org/documentation.html")]

am i missing something here? cant we/you just use the intel driver?

---

### Post by dfacto on 2011-08-10
> **ben.fazekas said:**
> Hi Guys,

i am planning to buy a macbook air if (rather big IF) i can install linux/ubuntu on it. I short of reviewed this thread and the bigest problem seems to be the graphic driver, or the lack of it. as i checked out there is an intel driver for the intel 3000hd integrated in the core i5/i7 processors. [see [http://intellinuxgraphics.org/documentation.html]("http://intellinuxgraphics.org/documentation.html")]

am i missing something here? cant we/you just use the intel driver?

You're mostly right. In theory everything should be fine--all that has changed other than video are the device codes (which we have patches for).

Video drivers have technically existed since Jan (maybe longer? see phoronix.com) but there is a kernel bug that is apparent on the MBA42 (and 41 too I think).

Bottomline is that as of this moment you are stuck at 1024x768... unless you are lucky enough to get the samsung display which apparently gives you an off-center 1280x800.  Even this obviously falls short of 1440x900.

Other than this I will say that in terms of hardware for your dollar I think its a pretty good deal and that eventually the bug will be fixed... (I hope!)  Also, I should add that  my bias is (and has been for some time) that I loathe apple and the fervor they encourage.

Cheers!

---

### Post by ben.fazekas on 2011-08-11
> **dfacto said:**
> You're mostly right. In theory everything should be fine--all that has changed other than video are the device codes (which we have patches for).

Video drivers have technically existed since Jan (maybe longer? see phoronix.com) but there is a kernel bug that is apparent on the MBA42 (and 41 too I think).

Bottomline is that as of this moment you are stuck at 1024x768... unless you are lucky enough to get the samsung display which apparently gives you an off-center 1280x800.  Even this obviously falls short of 1440x900.

Other than this I will say that in terms of hardware for your dollar I think its a pretty good deal and that eventually the bug will be fixed... (I hope!)  Also, I should add that  my bias is (and has been for some time) that I loathe apple and the fervor they encourage.

Cheers!

Hi dfacto,

thx for the answer. As of your last paragraph i completely agree, i looked at thinkpad x220 as well but with ssd and stuff it gets more expensive than the air and it is not even available in this config in my country so i would have to do extra organization and stuff to get one. So air would be hardwarewise the best option now and although i would not mind give the lion a try my main OS is linux/ubuntu and i intend to keep it this way.

---

### Post by dfacto on 2011-08-11
I am currently using macfanctld without any problems but there is an [alternative]("http://ubuntuforums.org/showpost.php?p=10795052&postcount=1").

I am curious, has anyone tried both macfanctld and smcFanControl?  Is one better than the other?

Can't remember if I already posted this... but one of the kernel developers has mentioned to me that most of the dkms's that are floating around are quite old.  Whenever someone suggests to install it, I would be dubious. (With the exception of my script because we need those patches for natty...hopefully by the time we get to oneirc, the kernel will have the patches included.)

Also. Would anyone be interested in setting up a bounty to get our video card working?  Its probably a long shot that someone other than those already working on it could help but, I'd be willing to commit at least $50 maybe even $100.  The patch would have to be submitted to the kernel-team (as well as make my video work).  If anyone else is interested, then I will make this pledge "official."  (Is there like a free escrow service we can use?)

---

### Post by dentifrice on 2011-08-11
Has anyone tried to boot in EFI mode using grub-efi?

---

### Post by berto- on 2011-08-12
> **dfacto said:**
> Also. Would anyone be interested in setting up a bounty to get our video card working?  Its probably a long shot that someone other than those already working on it could help but, I'd be willing to commit at least $50 maybe even $100.  The patch would have to be submitted to the kernel-team (as well as make my video work).  If anyone else is interested, then I will make this pledge "official."  (Is there like a free escrow service we can use?)

+$50 here.

---

### Post by koadman on 2011-08-12
I'll kick in another $50.

Yesterday my display slowly went wild after a resume from suspend.  It seems even 1280x800 on the samsung display has occasional problems.

Agree with others about the hardware.  The MacBook Air is in a league of its own.  Between the hi-res display, speedy ULV chip, SSD, build quality, and form factor, nothing else on the market even comes close right now.  Just need to get that display driver going...

On another note, has anyone been able to bless their partition from Lion?  I'm getting an error message:

Could not find object for s4
Can't determine legacy media type for s4

Googling was little help and I didn't find anything obvious in Apple's source code for bless either.  Any ideas?  I repartitioned when running linux at one point.  Could it be that OS X can no longer understand this part of the partition table?

---

### Post by berto- on 2011-08-12
> **ben.fazekas said:**
> As of your last paragraph i completely agree, i looked at thinkpad x220 as well but with ssd and stuff it gets more expensive than the air and it is not even available in this config in my country so i would have to do extra organization and stuff to get one. So air would be hardwarewise the best option now and although i would not mind give the lion a try my main OS is linux/ubuntu and i intend to keep it this way.

I was seriously considering the thinkpad X1; the high-end MBA was a better machine for my dollar.  I'm bummed that I'm currently not able to run Linux natively on it; can't wait for the video drivers to get sorted out.

My biggest concern is battery life under Linux.  Apple has done a great job with making OS X conserve battery.

The UI has some really nice elements as well.  For example, I am continually using spotlight for calculator and dictionary lookups; seamless.

---

### Post by berto- on 2011-08-12
> **dfacto said:**
> Is there like a free escrow service we can use?

I looked for about an hour and found nothing useful!  Incredible; sounds like a nice side project.

Anyone here using bitcoin?  Would that work?  Not exactly escrow, but it makes sending money pretty trivial.

---

### Post by ben.fazekas on 2011-08-12
> **berto- said:**
> +$50 here.

+$50 as well

---

### Post by dfacto on 2011-08-12
Great! I'm officially in for $50 USD (although maybe I should be using a more stable currency? Yikes.).  My terms are that the solution is a patch to the kernel or a patch to drm/i915.  The patch must be submitted to [email]kernel-team@lists.ubuntu.com[/email].

As this bug is already filed at freedesktop.org are their employees eligible?  Are canonical's?  I don't care who gets my money I just want something that works and its mainlined so it will *keep* working.

Should we add a comment to [bug 39533]("https://bugs.freedesktop.org/show_bug.cgi?id=39533")?

@berto Yes--does sound like an intriguing project.  I am guessing that we can't find one because such a service would have to meet the criteria of a bank or something like this.  I googled ubuntuforums and found some people discussing it circa 2007 but nothing since.  Anyway we can always do a person-to-person transfer with paypal (which are free if you have their base account).  Still though, this is not an escrow which would make the bounty more "official."

---

### Post by dfacto on 2011-08-12
> **berto- said:**
> I was seriously considering the thinkpad X1; the high-end MBA was a better machine for my dollar.  I'm bummed that I'm currently not able to run Linux natively on it; can't wait for the video drivers to get sorted out.

My biggest concern is battery life under Linux.  Apple has done a great job with making OS X conserve battery.

The UI has some really nice elements as well.  For example, I am continually using spotlight for calculator and dictionary lookups; seamless.

I want to like MacOS--I really do.  I just can't get over the inability to change resolution (I have bad eyes).

---

### Post by dfacto on 2011-08-12
@koadman Yes I was able to bless (at least it didn't return an error).  I think you probably already tried the same thing that I did but double check my post-install.sh for some comments (which I don't remember at the moment).

---

### Post by dfacto on 2011-08-12
Bounty for getting KMS/drm/i915 working on the MacBookAir4,2 HD 3000 Intel graphics card.  Interested persons should follow this [bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").

 $USD      User
 50.00  [berto-]("http://ubuntuforums.org/showpost.php?p=11143488&postcount=99")
 50.00  [koadman]("http://ubuntuforums.org/showpost.php?p=11143693&postcount=100")
 50.00  [ben.fazekas]("http://ubuntuforums.org/showpost.php?p=11143869&postcount=103")
 50.00  [dfacto]("http://www.almostsure.com/contactinfo.html#digits") [1]
 50.00  [russell.sim]("http://ubuntuforums.org/showpost.php?p=11148998&postcount=115")
100.00  [orangegold]("http://ubuntuforums.org/showpost.php?p=11152838&postcount=116") [2]
100.00  [riksta]("http://ubuntuforums.org/showpost.php?p=11157187&postcount=120")

Total Pledged Bounty: $450(USD)

Pledger-Specific Additional Conditions:
[1] - Must get patch accepted by [email]kernel-team@lists.ubuntu.com[/email].
[2] - Expires August 21, 2011. Must also fix suspend/hibernate.

**Update**: No one has expressed interest in this bounty and I guess we have a temporary work-around so I imagine these bounties are no longer valid.  Please correct me if I am wrong.

---

### Post by riksta on 2011-08-12
Hi guys, just to let you know that some ubuntu installations seem to be set with their default shell as dash instead of bash

You can find out which shell you are using before you execute the script by:

```
readlink /bin/sh
```

If it returns "dash" then you will need to run 

```
sudo dpkg-reconfigure dash
```

and then say 'NO' in the curses interface.

This will allow the pipe operators used for tee to work correctly

Here's hoping we get the video driver fix so we can have native resolutions!

---

### Post by berto- on 2011-08-12
> **dfacto said:**
> Bounty for getting KMS/drm/i915 working on the MacBookAir4,2 HD 3000 Intel graphics card.  Interested persons should follow this [bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").


I updated the freedesktop post with reference to this bounty.

---

### Post by dfacto on 2011-08-12
@riksta Its interesting that you had this problem as the [link]("https://wiki.ubuntu.com/DashAsBinSh") you provided suggests that as long as you she-bang bash, you are fine, ie #!/bin/bash at the top of the file (which post-install.sh has done).

Were you executing the commands line by line?

---

### Post by riksta on 2011-08-12
@dfacto no i just executed the script with 'sh post-install.sh' actually. So it seems that the shebang was ignored!

---

### Post by rluble on 2011-08-12
I think for the shebang to work you have to execute the script directly as in
./post-install.sh 
after chmod +x of course

Or you could do /bin/bash instead of sh.

---

### Post by dfacto on 2011-08-12
Ah yes--this confusion all makes sense now.  Yes you need to invoke as either "bash ./post-install.sh" or "chmod 0744 ./post-install.sh && ./post-install.sh".

In general you can find out how to execute a non-execute flagged script by looking at the she-bang line.  So a script with #!/bin/bash should never be called with sh.

I would NOT recommend "dpkg-reconfigure dash" as dash is resolved for any sh call for speed reasons.   Better to either check the she-bang or better still, just flag as user-execute either by chmod 0744 or chmod u+x

---

### Post by darren.shepherd on 2011-08-13
Two things.

1) The product ID on the MacbookAir4,1 for the trackpad/keyboard is different than the 4,2.  At least on mine I guess.  lsusb shows the product id as 0249.  So from what I can guess, I changed the hid and bcm patches so that the new id's were 0249, 024a, and 024b and it worked on my 4,1 (actually I don't think the keyboard one worked, I never got the fn keys to work).  I didn't do a proper patch of actually adding new ID's, but instead just changeds the "6" ones that were added.

2) I really need to use my macbook, so no suspend basic kills the possibility of my using it day to day.  (I can live with super bright 1024x768 graphics).  As a work around though, I've been running 11.04 in virtualbox in OS X and it works really quite nice.  Since I don't use OS X at all, I devoted 4 cores and 3GB+ of memory to the VM.  If you enable 3D accelartion unity works and all the compiz goodness I love.

If you run full screen you never even see OS X.  You have to disable the stupid menus that virtualbox puts on the screen, but I got rid of all of them.  The only time you see OS X is the lock screen after resume.  If you disable the lock screen, then you'll never see OS X, but less security :(

Another nice thing was I found this OS X prog called DoubleCommand that makes the fn key work like ctrl.  I haven't found a corresponding hack in linux.

I'd much rather run linux native (first time my computer hasn't had linux native in 12 years), but it works and I need it to work, so I can work, so I can make money :)

---

### Post by russell.sim on 2011-08-13
> **berto- said:**
> +$50 here.

Yeah put me down for $50 too

---

### Post by orangegold on 2011-08-14
$100 more for video drivers and suspend/hibernate, expires on 21 August.

---

### Post by dfacto on 2011-08-15
> **darren.shepherd said:**
> Two things.

1) The product ID on the MacbookAir4,1 for the trackpad/keyboard is different than the 4,2.  At least on mine I guess.  lsusb shows the product id as 0249.  So from what I can guess, I changed the hid and bcm patches so that the new id's were 0249, 024a, and 024b and it worked on my 4,1 (actually I don't think the keyboard one worked, I never got the fn keys to work).  I didn't do a proper patch of actually adding new ID's, but instead just changeds the "6" ones that were added.

2) I really need to use my macbook, so no suspend basic kills the possibility of my using it day to day.  (I can live with super bright 1024x768 graphics).  As a work around though, I've been running 11.04 in virtualbox in OS X and it works really quite nice.  Since I don't use OS X at all, I devoted 4 cores and 3GB+ of memory to the VM.  If you enable 3D accelartion unity works and all the compiz goodness I love.

If you run full screen you never even see OS X.  You have to disable the stupid menus that virtualbox puts on the screen, but I got rid of all of them.  The only time you see OS X is the lock screen after resume.  If you disable the lock screen, then you'll never see OS X, but less security :(

Another nice thing was I found this OS X prog called DoubleCommand that makes the fn key work like ctrl.  I haven't found a corresponding hack in linux.

I'd much rather run linux native (first time my computer hasn't had linux native in 12 years), but it works and I need it to work, so I can work, so I can make money :)

Yes--I expected the product codes to be different but no one gave them to me so I couldn't patch the kernel.  You can see what I did though and recreate it.  I suggest you send the product codes to [email]patches@bitmath.org[/email].

---

### Post by dfacto on 2011-08-15
Someone may want to give [3.1-rc2]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc2-oneiric/") a go (make sure to try in conjunction with xorg-edgers). It almost surely won't make a difference but who knows?

Update: Just saw the thread ["Ubuntu 11.04 sandy bridge support"]("http://ubuntuforums.org/showpost.php?p=11114284&postcount=1").  Could be worth trying/following.

---

### Post by riksta on 2011-08-16
@defacto

You are correct, I will have executed 
```

#sh post-install.sh

```

rather than

```

#chmod +x
#./post-install.sh

```

...because i am lazy ;)

I agree with you about not changing from dash !

> **dfacto said:**
> Ah yes--this confusion all makes sense now.  Yes you need to invoke as either "bash ./post-install.sh" or "chmod 0744 ./post-install.sh && ./post-install.sh".

In general you can find out how to execute a non-execute flagged script by looking at the she-bang line.  So a script with #!/bin/bash should never be called with sh.

I would NOT recommend "dpkg-reconfigure dash" as dash is resolved for any sh call for speed reasons.   Better to either check the she-bang or better still, just flag as user-execute either by chmod 0744 or chmod u+x

---

### Post by riksta on 2011-08-16
I'll donate $100 to the bounty.

---

### Post by ipstacks on 2011-08-17
Does the thunderbolt port work with Ubuntu/Linux?

EDIT: Yes, at some point anyway.  [http://linuxplumbersconf.org/2011/ocw/proposals/99](http://linuxplumbersconf.org/2011/ocw/proposals/99)

---

### Post by dentifrice on 2011-08-17
> **ipstacks said:**
> Does the thunderbolt port work with Ubuntu/Linux?

EDIT: Yes, at some point anyway.  [http://linuxplumbersconf.org/2011/ocw/proposals/99](http://linuxplumbersconf.org/2011/ocw/proposals/99)

There's a dedicated thread for that, with no more news unfortunately as of now: [http://ubuntuforums.org/showthread.php?t=1810273](http://ubuntuforums.org/showthread.php?t=1810273)

---

### Post by redil on 2011-08-18
Hi Folks
I am considering to get a new macbook air to put ubuntu on it (we are a complete Linux shop) because I like the hardware. To help the decision I would like to run one of our applications as a benchmark on such a machine. So I wonder if someone would be willing to run this job for me on their ubuntu macbook air. The time it take is about one minute.
I could send a tar ball. and the its untaring and starting it on the command line.

any takers?


greetings

---

### Post by dfacto on 2011-08-19
> **redil said:**
> Hi Folks
I am considering to get a new macbook air to put ubuntu on it (we are a complete Linux shop) because I like the hardware. To help the decision I would like to run one of our applications as a benchmark on such a machine. So I wonder if someone would be willing to run this job for me on their ubuntu macbook air. The time it take is about one minute.
I could send a tar ball. and the its untaring and starting it on the command line.

any takers?


greetings

Sorry but I don't think its a good idea to run untrusted code.  You should probably post it for people to make sure its safe, if you are actually serious.

---

### Post by redil on 2011-08-19
> **dfacto said:**
> Sorry but I don't think its a good idea to run untrusted code.  You should probably post it for people to make sure its safe, if you are actually serious.

Yes, running untrusted code is generally speaking not a good idea. But I have written the code and know what it does. 

But what do you mean by '... post it for people..'?

---

### Post by ngativ on 2011-08-19
Ok, any advance on this issue? Multitouch and video acceleration is all we need.

---

### Post by dfacto on 2011-08-19
nope; google "freedesktop hd 3000" and complain there

---

### Post by dfacto on 2011-08-20
So since it looks like a fix may come along slowly, I am now using VirtualBox and I am *very* happy with this setup.

I was able to make virtualbox use my existing Ubuntu partitions (both root and home) and can run at 1440x900 with 3D (although there are a few minor quirks).  All of my pre-existing settings seem to work very nicely with virtualbox (once I remapped the host key to the right-alt).

It was a tad annoying to get both partitions to play nicely.  This [post]("http://blog.jardinmagique.info/2009/08/setup-virtualbox-on-macosx-to-boot.html") proved very helpful (make sure to follow Steve Cheng's comments not the blogger's). At some point I will try to write-up a howto.

---

### Post by rluble on 2011-08-20
> **redil said:**
> Yes, running untrusted code is generally speaking not a good idea. But I have written the code and know what it does. 

But what do you mean by '... post it for people..'?

I know you trust your code, but why would anybody else?

---

### Post by dfacto on 2011-08-20
Here are the steps I took to get my Ubuntu partitions working in MacOS.  This stop-gap measure gives me a nicely working Ubuntu on the Air which I will use until the Intel KMS bugs are sorted out.  It is based largely on [this blog post]("http://blog.jardinmagique.info/2009/08/setup-virtualbox-on-macosx-to-boot.html").

The following steps should be completed from MacOS.

[LIST=1]
[*] Determine your partition information.
```

$ diskutil list
/dev/disk0
#:                 TYPE NAME           SIZE      IDENTIFIER
0: GUID_partition_scheme             *121.3 GB   disk0
1:                  EFI               209.7 MB   disk0s1
2:            Apple_HFS Macintosh HD   32.0 GB   disk0s2
3:           Apple_Boot Recovery HD   650.0 MB   disk0s3
4: Microsoft Basic Data Linux Root     12.9 GB   disk0s4
5:           Linux Swap                 6.4 GB   disk0s5
6: Microsoft Basic Data Linux Home     69.1 GB   disk0s6

```
For my Ubuntu setup I have root, swap, and home on partitions 4, 5, and 6.  Partitions 1, 2, and 3 belong to MacOS.


[*] Install [ExtFS for Mac OS X 8.0]("http://www.paragon-software.com/home/extfs-mac/features.html"). This allows you to have read/write access to the ext4 Linux partitions.  It is not free but was the only driver I could find that has read/write support (it integrates seamlessly with MacOS and I think it worth the investment).  The open source alternative [ext4fuse]("https://www.ohloh.net/p/ext4fuse") doesn't seem to have write support.

Note: this step may not be necessary--I did this before setting up VirtualBox so I don't know. It is definitely not necessary if your Ubuntu partitions are not ext4 (although they should be if you followed my set-up howto).

Warning: Make sure to eject (unmount) the ext4 drives before using VirtualBox.


[*] Install [VirtualBox for OS X hosts]("http://www.virtualbox.org/wiki/Downloads").


[*] [Setup raw disk]("http://www.virtualbox.org/manual/ch09.html") information.
```

mkdir -p ~/VirtualBox\ VMs/Linux/
cd ~/VirtualBox\ VMs/Linux/
# set read/write access for the Linux related partitions
sudo chown root:admin /dev/disk0s{4,5,6}
sudo chmod g+rw /dev/disk0s{4,5,6}
# copy the master boot record
sudo dd if=/dev/disk0 of=gpt.vmdk bs=512 count=40
# create a VirtualBox disk
sudo VBoxManage internalcommands createrawvmdk -filename \
Linux.vmdk -rawdisk /dev/disk0 -partitions 4 -mbr gpt.vmdk
# restore owbership to $USER
sudo chown $USER *.vmdk

```

Note that in creating the vmdk, we only selected one of the partitions (in this case disk0s4, i.e., my root).  We will correct this in the following two steps.  We must follow this circuitous step as VirtualBox seems to only scan up to four partitions, hence additional partition information needs to be manually specified.


[*] Collect partition data.
```

$ sudo gpt -r show /dev/disk0
    start       size  index  contents
        0          1         MBR
        1          1         Pri GPT header
        2         32         Pri GPT table
       34          6         
       40     409600      1  GPT part - C12A7328
   409640   62500000      2  GPT part - 48465300
 62909640    1269536      3  GPT part - 426F6F74
 64179176       1048         
 64180224  135053312      6  GPT part - EBD0A0A2
199233536   25163776      4  GPT part - EBD0A0A2
224397312   12578816      5  GPT part - 0657FD6D
236976128       2015         
236978143         32         Sec GPT table
236978175          1         Sec GPT header

```


[*] Replace the "extent description" section of Linux.vmdk.  I replaced my extent section with the following (which is based on the output of the previous step):
```

# Extent description
RW 40 FLAT "gpt.vmdk" 0
RW 409600 ZERO
RW 62500000 ZERO
RW 1269536 ZERO
RW 1048 ZERO
RW 135053312 FLAT "/dev/disk0s6" 0
RW 25163776 FLAT "/dev/disk0s4" 0
RW 12578816 FLAT "/dev/disk0s5" 0
RW 2015 ZERO
RW 33 ZERO

```

The second column corresponds to the size column of the gpt result.  The first four rows of the gpt output are summed together (for a total of 40) as are the last two rows (for a total of 33). The order must be the same as that of gpt.


[*] Set-up an Ubuntu VirtualBox session and select Linux.vmdk as a SATA drive. More details on setting up VirtualBox can be found in the [manual]("http://www.virtualbox.org/manual/").


[*] After virtually booting Ubuntu I installed the [VirtualBox 4.1.2 Oracle VM VirtualBox Extension Pack]("http://www.virtualbox.org/wiki/Downloads") and I also installed VBoxGuestAdditions.iso.
[/LIST]

A word of caution: make sure to never select the MacOS partitions from inside GRUB (from inside VirtualBox).  This would result in a double mount and would be a very bad thing.  Ideally I would set the MBR to avoid this, but things work and I don't want to fiddle with it any further.

Also note, you will need to set the disk0s{4,5,6} read/write access after every MacOS reboot.

---

### Post by Objectivity on 2011-08-22
:: My own experience installing Ubuntu on MAcbookair :::-({|=

 *I am jumping in* on this topic if you do not mind ! just want to express my feeling about HOW MUCH I hate apple simply because these folks are MONOPOLIZING almost everything !  By the way, my English is not great.

 Here is my odd story about installing Ubuntu :

 1 . I made 2 partitions using stupid " apple disk utility " one for swap one for Ubuntu.
      I restarted the computer with "nomodeset " HOPING Ubuntu detects the partitions !     INSTEAD Ubuntu got stuck on detecting the partitions ! NO PARTITIONS WERE FOUND AT ALL . 

( I GOT SO MAD AT APPLE ! why ? lack of support for linux )

2. I restarted the computer and removed those 2 partitions I made using stupid " apple disk utility ". I restarted the computer HOPING Ubuntu detects the hard drive - SSD at least ! This time IT DID.

( I GOT CONFUSED AND ALSO MAD AT APPLE AT THE SAME TIME )

3. I made 2 partitions again, THIS TIME using " ubuntu " one for swap one for Ubuntu. But I was Unable to *proceed with installation !!! *The installation strangely crashed !!! I was told by Ubuntu that I can report this error to the developer which I DID NOT.

( I GOT CONFUSED AND ALSO MAD AT APPLE AGAIN )

4. I restarted the computer in order to do the whole thing again HOPING ubuntu this time DETECTS " 2 partions I ALREADY MADE WITH UBUNTU " !!! but, IT DID NOT ! got 
stuck on detecting the partitions AGAIN !!!

( I GOT CONFUSED AND ALSO MAD AT APPLE AGAIN + Saying F words this time )

5. I restarted the computer and AGAIN REMOVED the partitions using stupid " apple disk utility "  hoping I could back to were I was on detecting the hard drive - SSD at least ! This time again Ubuntu detected the hard drive - SSD.

( I GOT CONFUSED AND ALSO MAD AT APPLE AGAIN but no F words this time )


6. I again made 2 partitions using " ubuntu " HOPING Ubuntu does not crash this time and *proceed with installation ! which IT DID.  *Everything was installed .

 ( I WAS STILL CONFUSED BUT A BIT HAPPY THIS TIME )

7. I restarted the computer HOPING Ubuntu boots ! but INSTEAD everything WAS BLACK ! no movement, nothing ! just a black screen.

 ( I GOT CONFUSED AGAIN SINCE I ALREADY SET " NOMODESET " through installation )

8. I restarted the computer and set " nomodeset " on grub. Finally, I was able to log in.

( I WAS STILL CONFUSED BUT HAPPY THIS TIME )

9. I tried to UPDATE Ubuntu HOPING I could get the graphic card to work but instead the update manager CRASHED ! I tried almost 10 times but IT DID CRASH again. I also restated the computer and tried one more time, again CRASHED and could not complete the task.

( I GOT MAD AGAIN AND TRIED TO SEARCH FOR SOME ANSWERS WHICH I CAME ACROSS THIS FORUM AND SAW HOW MUCH HASSLE YOU MUST TAKE IN ORDER TO USE UBUNTU ON MACBOOKAIR !! ) so, I decided to remove ubuntu and stick to MacOSX for now.

 Sorry, I had to speak my mind ! otherwise I could not sleep tonight.

 Again, I hate apple + Microsoft for one simple reason :
 MONOPOLIZING almost everything ! Morally 100% wrong . If these 2 companies did not monopolize  the market, we could have enjoy THIS beautiful operating system called Linux a bit MORE ! AT LEAST ME.

 GOD BLESS linus torvalds ! I only wish Bill and Steve were like HIM ! morally speaking .

 Yours,
 Elmo

---

### Post by redil on 2011-08-22
> **rluble said:**
> I know you trust your code, but why would anybody else?
alright, if you think I want to bork your mac or worse, then this is clearly not for you.

and, as has been suggested to throw 20000 lines of Fortran code is also not a really good idea either. 

It seems that we sometimes unduly complicate our lives....

be it so

---

### Post by Objectivity on 2011-08-23
Folks ...

 please let us know on this forum whenever the graphic card driver IS ready for MacbookAir 2011.

 I will check this forum every single day ! I am waiting to get rid of MacOS X as soon as possible.

 Regards,
  Elmo

---

### Post by dfacto on 2011-08-23
> **Objectivity said:**
> Folks ...

 please let us know on this forum whenever the graphic card driver IS ready for MacbookAir 2011.

 I will check this forum every single day ! I am waiting to get rid of MacOS X as soon as possible.

 Regards,
  Elmo

Instead of checking here, you can check the [source]("https://bugs.freedesktop.org/show_bug.cgi?id=39533") for yourself. :)

---

### Post by Objectivity on 2011-08-23
> **dfacto said:**
> Instead of checking here, you can check the [source]("https://bugs.freedesktop.org/show_bug.cgi?id=39533") for yourself. :)


 Fantastic ! and THANK YOU.

 If I get the graphic card installed, I will celebrate by destroying the apple logo on back of my MacBookAir lol I PROMISES. :guitar:   WILL send the picture to you all !

---

### Post by dfacto on 2011-08-23
> **Objectivity said:**
> Fantastic ! and THANK YOU.

 If I get the graphic card installed, I will celebrate by destroying the apple logo on back of my MacBookAir lol I PROMISES. :guitar:   WILL send the picture to you all !

Let me know if you find a cool decal or something to cover up the apple.  All I could find is [this]("http://www.artfire.com/ext/shop/product_view/1237140").

---

### Post by Objectivity on 2011-08-23
> **dfacto said:**
> Let me know if you find a cool decal or something to cover up the apple.  All I could find is [this]("http://www.artfire.com/ext/shop/product_view/1237140").

 Sure I will. I am thinking of making one ! I already have made this one but is not Ubuntu though ...  It is a combination of " Open source TM and GNU operating system. See the attachment .

 I got " Clear window decals " from Staples and printed my artwork on it and cut it .

 I think it looks not bad ! I will make one for Ubuntu after I get the graphic card installed :-\"

---

### Post by Objectivity on 2011-08-23
> **Objectivity said:**
> Sure I will. I am thinking of making one ! I already have made this one but is not Ubuntu though ...  It is a combination of " Open source TM and GNU operating system. See the attachment .

 I got " Clear window decals " from Staples and printed my artwork on it and cut it .

 I think it looks not bad ! I will make one for Ubuntu after I get the graphic card installed :-\"


 
 By the way, we should glorify the concept of " open source " all the time and not specific distribution ! 
 By glorifying specific distribution we " unconsciously " are trying to  monopolize like apple + microsoft.  After all, linux is not about  monopolizing ! so, I would rather mention on my logo the concept of OPEN  SOURCE first then the distribution.

---

### Post by dfacto on 2011-08-23
> **Objectivity said:**
> By the way, we should glorify the concept of " open source " all the time and not specific distribution ! 
 By glorifying specific distribution we " unconsciously " are trying to  monopolize like apple + microsoft.  After all, linux is not about  monopolizing ! so, I would rather mention on my logo the concept of OPEN  SOURCE first then the distribution.

Nice work!  I hadn't thought of the GNU logo--fantastic idea. :)

Just as an aside though...given that half the point of open source is free (as in libre) one probably shouldn't get too overbearing in promoting it!
And for that matter, since its free (as in gratis) we should be patient for the driver fix! :)

---

### Post by dfacto on 2011-08-24
> **koadman said:**
> Aha! I seem to have a samsung LCD, along with the 256GB ssd.

sudo get-edid 2> /dev/null | strings -5
LTH133BT01A03
Color LCD

Never occurred to me to try LVDS instead of VGA, I'll give that a go.  Suspend works for me, need to look into hibernate next.  I accidentally set my swap space too small for hibernate but thankfully still have some room to grow it.

koadman, I was wondering, did you do a pure EFI setup or are you using BIOS emulation?  I still am having a hard time believing that your screen works because its a different brand.

---

### Post by dfacto on 2011-08-24
Here is a list of other distributions that we can use to track progress of MBA41/2.

[LIST]
[*][Gentoo]("http://forums.gentoo.org/viewtopic-t-889652.html")
[*][Arch Linux]("https://bbs.archlinux.org/viewtopic.php?id=123258")    
[*][Vine Linux]("http://microgroove.jp/shaolin/2011/08/installing_vine_linux_on_macbook_air_middle_2011.html")    
[*][FC15]("http://forums.fedoraforum.org/showthread.php?t=263521")
[/LIST]

Please let me know if you find other places to track.

---

### Post by Objectivity on 2011-08-24
> **dfacto said:**
> Here is a list of other distributions that we can use to track progress of MBA41/2.

[LIST]
[*][Gentoo]("http://forums.gentoo.org/viewtopic-t-889652.html")
[*][Arch Linux]("https://bbs.archlinux.org/viewtopic.php?id=123258")
[*][Vine Linux]("http://microgroove.jp/shaolin/2011/08/installing_vine_linux_on_macbook_air_middle_2011.html")
[*][FC15]("http://forums.fedoraforum.org/showthread.php?t=263521")
[/LIST]

Please let me know if you find other places to track.


 Thank you :rolleyes:

---

### Post by User4519 on 2011-08-25
> **dfacto said:**
> Let me know if you find a cool decal or something to cover up the apple.  All I could find is [this]("http://www.artfire.com/ext/shop/product_view/1237140").

That one is actually pretty clever :) Would be nice in all-white or all-black, though.

Seems like I wasn't the only one to consider making one? I already went into some depth trying to find some vinyl clear sticker paper that one could print to, but it's either very hard to find or extremely expensive and not very durable. I did find that you can have it made for you by professionals by uploading an artwork file, and you can then have clear stickers with coating made for outdoor use that should last for more than a year in rain and sun - sounds like something that could last a while on an MBA, too ;)

Anyway, if there are a few of us, the price drops drastically, from like $60 bucks to like $10 or $15 bucks for a large clear durable sticker.

My thought was an all-black stencil-like Tux eating that apple logo. Not the "cute" tux eating an apple that can be found as a wallpaper online, but more like the classic tux we know from wikipedia etc. redrawn to eat that California fruit somehow. I'm not a designer myself, but I do work with Photoshop and Illustrator occasionally, so my plan is - after my current job project is done and my vacation is over - to start sketching in Illustrator and make this tux. Possibly with a little help from my brother who's lead designer in a very large design company.

I'll make sure to throw the results in here and check if any of you like it and want to pitch in to have him made as stickers professionally to bring down the price :)

Cheerio,
Daniel

PS: While waiting for drivers to advance, I'm making great progress in making Mac OS X suck less. Some tips:
[LIST]
[*]Get LiteSwitch X for a better Cmd+Tab among other things
[*]AND/OR get Witch to create a much better Alt+Tab like the rest of the world uses it.
[*]Get Path Finder as a better alternative to that horrible, horrible Finder
[*]Go to mission controls in sysprefs and have a look at the three checkboxes
[*]Get DoubleCommand to fix Home/End buttons among other things
[*]Get RightZoom to fix the broken maximize buttons on windows
[*]Discover the Keyboard pane in sysprefs to first make the F keys behave normally, then create [better shortcuts]("http://danielsmedegaardbuus.dk/2011-08-21/creating-missing-keyboard-shortcuts-in-applications-on-mac-os-x/") to get back F3 for searching, F2 and F10 to rename and create folders in Path Finder etc.
[*]Fix Terminal using a .bashrc from ubuntu and redefine keys in settings (unfortunately, when doublecommand makes home and end work in every other application, getting them to work in terminal seems impossible). Also, install SIMBL and MouseTerm to get mouse scrolling in terminal.
[*]Get homebrew "package manager" to easily install wget etc.  
[/LIST]

There are more tips... I'm hoping to throw together a howto eventually on how to make OS X stop sucking, but let's see if I can find the time :) In general, I'm flabbergasted that people seriously consider this OS as something a usability person should look to for inspiration. It's a usability NIGHTMARE akin to having rubberbands around your fingers while typing. No concistency, no logic, loads of pitfalls and annoyances. But there are still serious qualities once you get the worst bull fixed :)

---

### Post by Objectivity on 2011-08-25
> **DanielBuus said:**
> That one is actually pretty clever :) Would be nice in all-white or all-black, though.

Seems like I wasn't the only one to consider making one? I already went into some depth trying to find some vinyl clear sticker paper that one could print to, but it's either very hard to find or extremely expensive and not very durable. I did find that you can have it made for you by professionals by uploading an artwork file, and you can then have clear stickers with coating made for outdoor use that should last for more than a year in rain and sun - sounds like something that could last a while on an MBA, too ;)

Anyway, if there are a few of us, the price drops drastically, from like $60 bucks to like $10 or $15 bucks for a large clear durable sticker.

My thought was an all-black stencil-like Tux eating that apple logo. Not the "cute" tux eating an apple that can be found as a wallpaper online, but more like the classic tux we know from wikipedia etc. redrawn to eat that California fruit somehow. I'm not a designer myself, but I do work with Photoshop and Illustrator occasionally, so my plan is - after my current job project is done and my vacation is over - to start sketching in Illustrator and make this tux. Possibly with a little help from my brother who's lead designer in a very large design company.

I'll make sure to throw the results in here and check if any of you like it and want to pitch in to have him made as stickers professionally to bring down the price :)

Cheerio,
Daniel

PS: While waiting for drivers to advance, I'm making great progress in making Mac OS X suck less. Some tips:
[LIST]
[*]Get LiteSwitch X for a better Cmd+Tab among other things
[*]AND/OR get Witch to create a much better Alt+Tab like the rest of the world uses it.
[*]Get Path Finder as a better alternative to that horrible, horrible Finder
[*]Go to mission controls in sysprefs and have a look at the three checkboxes
[*]Get DoubleCommand to fix Home/End buttons among other things
[*]Get RightZoom to fix the broken maximize buttons on windows
[*]Discover the Keyboard pane in sysprefs to first make the F keys behave normally, then create [better shortcuts]("http://danielsmedegaardbuus.dk/2011-08-21/creating-missing-keyboard-shortcuts-in-applications-on-mac-os-x/") to get back F3 for searching, F2 and F10 to rename and create folders in Path Finder etc.
[*]Fix Terminal using a .bashrc from ubuntu and redefine keys in settings (unfortunately, when doublecommand makes home and end work in every other application, getting them to work in terminal seems impossible). Also, install SIMBL and MouseTerm to get mouse scrolling in terminal.
[*]Get homebrew "package manager" to easily install wget etc.
[/LIST]

There are more tips... I'm hoping to throw together a howto eventually on how to make OS X stop sucking, but let's see if I can find the time :) In general, I'm flabbergasted that people seriously consider this OS as something a usability person should look to for inspiration. It's a usability NIGHTMARE akin to having rubberbands around your fingers while typing. No concistency, no logic, loads of pitfalls and annoyances. But there are still serious qualities once you get the worst bull fixed :)




Throw the results in here when you are done then lol Tux eating apple logo ! :D heheh. Nice Idea.  I know there is already "android eating apple logo " out there ... 

 See the attachment.
*It is a bit violent, though* I try my best not to glorify the violence.

---

### Post by User4519 on 2011-08-26
> **Objectivity said:**
> Throw the results in here when you are done then lol Tux eating apple logo ! :D heheh. Nice Idea.  I know there is already "android eating apple logo " out there ... 

 See the attachment.
*It is a bit violent, though* I try my best not to glorify the violence.

Yeah, I love that one :D Android is soooo much better than that iOS crap. Fun to watch the latest keynote with the advancements in iOS5 and listen to the religious fanboys go wrorooooohooooh when Steve showed off functionality copied from Android ;)

---

### Post by daveMustane on 2011-08-27
> **Objectivity said:**
> 
lol Tux eating apple logo !  heheh. Nice Idea.


How can they sell computers without an installation media?

I'd much prefer a sticker to hide their ugly logo.

---

### Post by undoIT on 2011-08-27
> **Objectivity said:**
> Fantastic ! and THANK YOU.

 If I get the graphic card installed, I will celebrate by destroying the apple logo on back of my MacBookAir lol I PROMISES. :guitar:   WILL send the picture to you all !

The GNU head is always one of my favorites ;)

[http://shop.fsf.org/product/super-sticker-mega-multi-pack/](http://shop.fsf.org/product/super-sticker-mega-multi-pack/)

---

### Post by Objectivity on 2011-08-28
> **daveMustane said:**
> How can they sell computers without an installation media?

I'd much prefer a sticker to hide their ugly logo.

 If you HATE apple that much then why don't you go and buy " samsung 9 series "

 IT IS ALMOST the same as Air " Hardware + *thickness , and etc *".   Even the graphic card is the same. I have to say Air is a bit more well designed ! specially the keyboard. I really like the feel of the keyboard ! it is amazing. But, if you do hate apple THAT much... I would say get Samsung instead \\:D/

 No news for fixing the graphic driver bug yet ...  AAAhhhh .... :confused:

---

### Post by daveMustane on 2011-08-28
> **Objectivity said:**
> If you HATE apple that much then why don't you go and buy " samsung 9 series "

I've been using using a 2010 MBA with Ubuntu as my main mobile machine for eight month and it was good. The 2010 MBA did however come with an installer stick. And I sure needed it one day, because sometimes things break and you want to fix them.

So why would anyone sell a computer without an installer disk (or USB stick)? To save a $1? Maybe, but I'm not convinced. I'd really like to understand why this decission was made. It appears awfull and arrogant. Yes, I really, badly dislike their attitude. But mainly because, for some reason, they seem to dislike me (and you).

Also, I'm sure the Samsung is made of plastic.

---

### Post by dfacto on 2011-08-28
Actually the new Apple's are supposed to support internet re-installs from EFI.  Many would argue I'm nuts, but I actually think this is safer (assuming you can't somehow bork that part of the firmware).  This way, any reinstall automatically has all the latest security patches....

Anyway, I'm all for Apple bashing but BIOS really is pretty crappy.

Also, the Samsung chassis is not 100% duralumin--it has significant plastic and does not give me the impression of durability (whether it is or isn't I'm not referring to, just my impressions).

---

### Post by rluble on 2011-08-28
> **dfacto said:**
> Actually the new Apple's are supposed to support internet re-installs from EFI.  Many would argue I'm nuts, but I actually think this is safer (assuming you can't somehow bork that part of the firmware).  This way, any reinstall automatically has all the latest security patches....


I can confirm that it reinstalls beautifully from the net. I was overconfident that Ubuntu would run with no problems, so when, in the process of resizing the Mac Os partition with diskutil to install linux destroyed the recovery partition I did not give it a though. But in the end with so many attempts I ended up messing the osx partition. I though I had a very good looking brick, but then recovery from the net through EFI worked great albeit a bit slow....

I still have a brick for now, one that runs only osx :( but well I know the issue will get resolved eventually...

---

### Post by Objectivity on 2011-08-29
> **daveMustane said:**
> Yes, I really, badly dislike their attitude. But mainly because, for some reason, they seem to dislike me (and you).



  One very simple reason apple is succesful is because they stick to the concept of " Minimalism " in their industrial designs. I'm sure there are other reasons as well but I want to stick to ONLY one for now. 

*As far as the industrial design's concern*, this guy is their main brain ... " Jonathan Ive "   

I JUST don't know *why no one else* ever took this idea seriously but only few companies. If we had like 10 to 15 more companies using the same concept, apple would have backed of a little bit ! They are arrogant because they are the ONLY one who uses this concept seriously in their industrial designs . They even used it on their operating system - the way it looks and operates.   ( Google ) also  uses the SAME concept - people LOVE it when they see just a plain SIMPLE page SAYS  GOOGLE - NO ADS, NO DISTRACTION - where the work is stripped down to its most fundamental features. People are SICK and tired of distractions in this century ! they are bombarded with information ! That is why most of them " unconsciously "  LOVE the concept of Minimalism. That is why they get hypnotized when they see apple products without EVEN knowing WHY.

 The ONLY small company AS FAR AS I KNOW tried to took the same idea seriously  WAS " Voodoopc" !  but unfortunately """ HP """ took over and DESTROYED them totally ! I have attached " Envy 133 " picture. See HOW they used Minimalism in their industrial designs and HOW BEAUTIFUL THAT IS ! EVEN if the hardware specifications are lousy, you still WANT IT unconsciously ! that is the power of Minimalism in this century.

 Think about it :roll:

 Yours,
 Elmo[URL="http://en.wikipedia.org/wiki/Industrial_Design"]
[/URL]

---

### Post by Objectivity on 2011-08-30
Seems ... they gave up on the driver BUG fix .

Joshua Dillon                                                  2011-08-29 07:52:00 PDT                    Its been a month with no updates. Any way we can get a picture of where things are at?  Is it realistic to hope for a bugfix on this in the near-term or will this one persist? Cheers, Josh

[https://bugs.freedesktop.org/show_bug.cgi?id=39533](https://bugs.freedesktop.org/show_bug.cgi?id=39533)

 This is nonsense ! fixing that bug is not a [I]not a rocket science ! ](*,)
 I am Still using Mac OS and might sell my MacbookAir soon. 
[/I]

---

### Post by dfacto on 2011-08-30
> **Objectivity said:**
> Seems ... they gave up on the driver BUG fix .

Joshua Dillon                                                  2011-08-29 07:52:00 PDT                    Its been a month with no updates. Any way we can get a picture of where things are at?  Is it realistic to hope for a bugfix on this in the near-term or will this one persist? Cheers, Josh

[https://bugs.freedesktop.org/show_bug.cgi?id=39533](https://bugs.freedesktop.org/show_bug.cgi?id=39533)

 This is nonsense ! fixing that bug is not a [I]not a rocket science ! ](*,)
 I am Still using Mac OS and might sell my MacbookAir soon. 
[/I]

Yeah; me too.

---

### Post by Objectivity on 2011-08-30
Sorry, posted twice ! mistake .

Seems ... they gave up on the driver BUG fix .

Joshua Dillon                                                  2011-08-29 07:52:00 PDT                    Its been a month with no updates. Any way we can get a picture of where things are at?  Is it realistic to hope for a bugfix on this in the near-term or will this one persist? Cheers, Josh

[https://bugs.freedesktop.org/show_bug.cgi?id=39533](https://bugs.freedesktop.org/show_bug.cgi?id=39533)

 This is nonsense ! fixing that bug is not a [I]not a rocket science ! ](*,)
 I am Still using Mac OS and might sell my MacbookAir soon. 
[/I]

---

### Post by berto- on 2011-08-30
> **dfacto said:**
> So since it looks like a fix may come along slowly, I am now using VirtualBox and I am *very* happy with this setup.


What model Macbook Air do you have?  I have the 13"/i7/256G and with virtualbox ran into some serious issues when putting the machine to sleep and waking it up.  The laptop would completely freeze and I'd have to force it to power down and reboot.

I've since switched to Parallels and it's been great.  Super stable for over a couple of weeks now.

In case anyone wonders, I also tried vmware fusion, but it didn't support 3D, therefore no Unity support, so I switched to Parallels.

My virtualbox issues are likely due to this i7 bug:

[http://www.virtualbox.org/ticket/8474](http://www.virtualbox.org/ticket/8474)

Also note, interestingly, I have run a Windows XP image on virtual box and have not run into an issue.  That said, I barely fire up that VM, so it may just be luck.

---

### Post by berto- on 2011-08-30
I've been way out of the loop in this thread, but the following update on another thread seems to show some success:

[http://ubuntuforums.org/showpost.php?p=11164803&postcount=29](http://ubuntuforums.org/showpost.php?p=11164803&postcount=29)

---

### Post by dfacto on 2011-08-30
@berto I have the 4,2/i5/128 so I guess that explains why it worked for me.  Glad to hear you figured out something though.  If you can, would you share the specifics of how you set it up?

---

### Post by berto- on 2011-08-30
> **dfacto said:**
> @berto If you can, would you share the specifics of how you set it up?

I didn't do anything too special.  Parallels pretty much took care of the entire setup.  Settings-wise, I used 128MB for video, 1280MB of RAM, a 64G "expanding disk" image, and a shared network connection.  I found the VM runs well with 1280MB of RAM, it gives OS X enough RAM to do what it needs to do, and leaves enough wiggle room to launch a browser in OS X if needed.

The only potential tweak I  did was [a plist patch]("http://kb.parallels.com/6913") to get USB working.  Though, I'm not sure if another VM was conflicting with the USB device or if it was a Parallels issue.

More general details of my experience are [here]("http://rcaguilar.wordpress.com/2011/08/30/ubuntu-11-04-on-a-2011-macbook-air/").

---

### Post by Objectivity on 2011-08-31
Folks ...

 MUST SEE ...  [http://www.youtube.com/watch?v=-aLwBxaNDiA&feature=related](http://www.youtube.com/watch?v=-aLwBxaNDiA&feature=related)

 ALSO see TOP rated comment =D>

 I must say, it looks solid and nice !  Maybe, we should all just sell our MacbookAirs and get one of those ...    

 What do you think ?  Lets do it !

---

### Post by Objectivity on 2011-08-31
> **berto- said:**
> I've been way out of the loop in this thread, but the following update on another thread seems to show some success:

[http://ubuntuforums.org/showpost.php?p=11164803&postcount=29](http://ubuntuforums.org/showpost.php?p=11164803&postcount=29)


 I am gonna try this to see what happens ! I DO really need to get rid of Mac OS as soon as possible . I cannot tolerate using MAC OS more than 2 months ! ---- >  By usuing MAC OS , I *feel like being imprisoned in **fascist* concentration camp   <---- #-o

 Mine is Intel i5  
 same as [dfacto]("http://ubuntuforums.org/member.php?u=52141") .

 Anyone yet tried this ? before I waste my whole NIGHT installing Ubuntu again.

---

### Post by berto- on 2011-08-31
> **Objectivity said:**
> I am gonna try this to see what happens ! I DO really need to get rid of Mac OS as soon as possible . I cannot tolerate using MAC OS more than 2 months ! ---- >  By usuing MAC OS , I *feel like being imprisoned in **fascist* concentration camp

I think you're over-reacting just a wee bit.  Let's try to stay on topic.

---

### Post by Objectivity on 2011-08-31
> **berto- said:**
> I think you're over-reacting just a wee bit.  Let's try to stay on topic.

 Maybe you are right.  But when I see a company such as apple tries  to monopolize the market exactly like Microsoft "  Obtain exclusive possession or control of most (trade, commodity, or service ",  it reminds me of fascist ideology automatically and makes me feel sick.  By reacting to the way they do business I think I react morally right. Yes ... sometimes it is irrelevant to this topic and we should stay on topic as much as we can. 

 :-k

---

### Post by eti.que on 2011-08-31
> **Objectivity said:**
> By reacting to the way they do business I think I react morally right.

No you don't.

The MBA 2011 is the best hardware on the market, be it feat- or price-wise, period. Apple makes wise choices in hardware (EFI, openfirmware, Thunderbolt), it's a shame Linux support is still whacky.

It takes sometime to get the Linux-laptop stack ported on it, no surprise, it's the case with all new hardware be it Apple or not. In the mean time you're up to use Mac OS, which isn't a bad OS at all with loads of excellent FOS software on it if you don't want to use Apple's ones (which is understandable).

You're yelling in a way which is just wrong, man. If you're so upset about that, come on... just resell it but give us a break.

---

### Post by dfacto on 2011-08-31
> **Objectivity said:**
> Folks ...

 MUST SEE ...  [http://www.youtube.com/watch?v=-aLwBxaNDiA&feature=related](http://www.youtube.com/watch?v=-aLwBxaNDiA&feature=related)

 ALSO see TOP rated comment =D>

 I must say, it looks solid and nice !  Maybe, we should all just sell our MacbookAirs and get one of those ...    

 What do you think ?  Lets do it !

I've been tracking the UX21 for some time.  Last I check it isn't yet available but should be in the coming weeks.

In any event, there is no guarantee the story will be any better.  Although I don't have specific evidence, I think its the Intel video card that is the problem not something due to Apple.  I say this because other mobile i5/i7 chipsets with integrated graphics are also having a host of problems.  Of course who knows.

It certainly will be interesting to see if the UX21 runs w/o problems though.

---

### Post by undoIT on 2011-08-31
The ASUS UX21 / UX31 are the first laptops from a PC manufacturer that actually come close to the Macbook Air. One thing I like about the UX31 is the 1600x900 resolution display:

[http://www.pcauthority.com.au/News/267122,first-look-asus-13in-ux31-ultrabook.aspx](http://www.pcauthority.com.au/News/267122,first-look-asus-13in-ux31-ultrabook.aspx)

For me, anything below 1440x900 is a major drag on productivity and usability.

However, the UX series still don't match the build quality and aesthetic appeal of the Macbook Air imo. When you look at the profile of the UX21 with lid closed, it is nowhere near as clean as the Macbook Air.

Apple really hit the nail on the head with the new Macbook Air. The only minor complaint I have is the glossy screen. If Apple provided a matte option, this would be a perfect laptop.

I'm just patiently waiting for support with the Intel graphics driver and expect it will come before Oneiric is released. I'm sure it will be much better than the other Apple laptops I own with Nvidia graphics cards. It took a while for the Macbook 5,1 to have all the kinks ironed out. Never again will I buy a laptop with Nvidia graphics card.

---

### Post by Objectivity on 2011-08-31
> **eti.que said:**
> No you don't.

The MBA 2011 is the best hardware on the market, be it feat- or price-wise, period. Apple makes wise choices in hardware (EFI, openfirmware, Thunderbolt), it's a shame Linux support is still whacky.

It takes sometime to get the Linux-laptop stack ported on it, no surprise, it's the case with all new hardware be it Apple or not. In the mean time you're up to use Mac OS, which isn't a bad OS at all with loads of excellent FOS software on it if you don't want to use Apple's ones (which is understandable).

You're yelling in a way which is just wrong, man. If you're so upset about that, come on... just resell it but give us a break.

 I will give you a break since you are the only one who complaind so far about what I think.

 By the way, this did not work ! I tried it last night ... [http://ubuntuforums.org/showpost.php...3&postcount=29]("http://ubuntuforums.org/showpost.php?p=11164803&postcount=29")

 The bug is still there . ](*,)

---

### Post by Objectivity on 2011-08-31
> **undoIT said:**
> The ASUS UX21 / UX31 are the first laptops from a PC manufacturer that actually come close to the Macbook Air. One thing I like about the UX31 is the 1600x900 resolution display:
  

However, the UX series still don't match the build quality and aesthetic appeal of the Macbook Air imo. When you look at the profile of the UX21 with lid closed, it is nowhere near as clean as the Macbook Air.

 I agree. I even left a comment on that chanel saying ...

 
                      :: At [2:02]("http://www.youtube.com/watch?v=-aLwBxaNDiA#")  :: Can't be open easily ! They always try to clone apple products but  always forget some very important parts lol I am glad MBA opens&#65279; easily !  lol


and 15 people liked what I NOTICED .


 Yours,
 Elmo

---

### Post by Objectivity on 2011-08-31
:: By the way ::  I have listed my MBA on ebay just now ! so, bye bye MBA.

 I will buy something which I can install ubuntu on it easily !  

 Bye all and thank you for being patient with me . ):P

---

### Post by undoIT on 2011-08-31
I am very happy with my ThinkPad T420s for a long list of reasons. That's my primary laptop. I actually have Fedora with KDE installed on it and it is running beautifully. I'd imagine Ubuntu would run just as well. Of course, it is nowhere near as sleek and beautiful as the Macbook Air, but there are also a lot of advantages, i.e. dual hard drive setup with MSATA SSD, 1600x900 resolution etc.

---

### Post by dfacto on 2011-09-01
[Go read this post.]("http://ubuntuforums.org/showpost.php?p=11212044&postcount=176")


[s]I tried to resize my partition scheme and somehow borked my partition table in such a way that gptsync would not resync the table.  I decided to use the mac recovery firmware app and just wipe every partition and reinstall.  Also, I was curious about how this would work.

The only problem I had was that my home internet was apparently too slow causing the download to stall (I have a 10mbit pipe so I don't know why this was a problem).  When this happens the re-download does not resume.  Eventually I just gave up and brought it to work.
[/s]

Otherwise I think the web-based restore is very impressive. Assuming you have a moderately fast wan connection it takes 60min to download the iso and maybe another 15 of install.  My home connection uses WPA2-personal and my work uses WPA2-enterprise.  Both worked fine.

**Update**:
Now that I've done this a *second* time I need to clarify my earlier comments.
1) The web recovery actually has two stages (at most).
[s]
2) Either the formating step or the installation of grub that comes with oneiric alpha-3 live does something very bad to the partition table. Avoid using it until this is resolved (I had previously thought it was partitioning that caused the problem but I eliminated this by using disk utility).
[/s]
1) The first stage is nothing more than a cheesy graphic (of an eerily distorted earth) and a pull-down menu from which you can select from either WPA or WPA2-personal wireless networks.  Apparently this stage downloads the software that will be used in setting up Lion (second stage).  The download takes about 10-15min on my 10mbps connection.

The second stage has a more complete GUI (menu-bar, windows, etc) from which you can choose a greater variety of wireless networks, i.e., WEP and WPA2-personal/enterprise encryption ([more details]("http://support.apple.com/kb/HT4718")).  This stage allows for time machine restores, Lion re-installation, online help, and the disk utility.  This (Lion) download takes ~2hours on my 10mbps followed by a ~15min install.
[s]
2) I have now borked my partition tables twice while following the exact same procedure I outlined in an earlier post.  The only difference is that this time I was using oneiric alpha-3.  I believe the fault lies with gparted.  I recommend that you use disk utility to do all your partitioning and then reformat from the ubuntu installer.  My layout is:
40gb HFS+ "Mac OS"
60gb MSDOS "Linux Home"
16gb MSDOS "Linux Root"
4.5gb MSDOS "Linux Swap"
which I will then format the MSDOS partitions to ext4,ext4,swap. Note: I used 4.5gb to be absolutely sure there is enough room for swapping out all RAM (I do not know if there is overhead hence the extra 512mb).
[/s]

---

### Post by daveMustane on 2011-09-01
Still waiting for the graphics driver fix. But I also have another problem, that is booting my Ubuntu installation from a secondary partition. I reduced the size of the OSX partition (it's on /dev/sda2). When booting Ubuntu from a USB stick and running the installer, what should be selected as the &quot;Device for boot loader installation&quot;? Would that be /dev/sda, or the partition that is being used as root for Ubuntu (/dev/sd5 in my case)?  I first tried /dev/sda but this didn't let me boot Ubuntu and it also hosed my OSX installation. I had to do the network recovery which took ages, didn't work the 1st time but finally it DID fix OSX. I started from scratch, tried putting the bootloader on /dev/sda5, and while OSX booting is still fine, I'm not able to boot Ubuntu (neither through rEFit nor via alt-key booting). Whatever I try, I always get a black screen with a blinking cursor, that's all. What can I do to get Ubuntu starting up (in 1024 for now)?

---

### Post by srs5694 on 2011-09-01
> **daveMustane said:**
> I also have another problem, that is booting my Ubuntu installation from a secondary partition..... I started from scratch, tried putting the bootloader on /dev/sda5, and while OSX booting is still fine, I'm not able to boot Ubuntu (neither through rEFit nor via alt-key booting). Whatever I try, I always get a black screen with a blinking cursor, that's all. What can I do to get Ubuntu starting up (in 1024 for now)?

You might look into EFI booting options, rather than booting using BIOS emulation, which is what most procedures do. I've got a [Web page describing one way to do this,](http://www.rodsbooks.com/ubuntu-efi/index.html) but it's a bit out of date (I wrote it with Ubuntu 10.10 as a reference), and there are a lot of subtle but important differences between the various Mac models, so you may need to deviate from what that page describes. Broadly speaking, though, the trick is to put an EFI-capable boot loader in the EFI System Partition (ESP). GRUB 2 seems to work, but can be tricky to get properly configured. ([This page](https://help.ubuntu.com/community/UEFIBooting) may be a useful reference.) On UEFI-based PCs, I've had better luck with [ELILO,](http://elilo.sourceforge.net/) but I've not had much luck getting ELILO working on my 1st-generation Intel-based Mac Mini.

---

### Post by dfacto on 2011-09-01
@daveMustane Have you read the earlier posts?  You should install grub to the linux root partition (as described earlier) and you should append either nomodeset or i915.modeset=0 to the grub defaults.  Please do let us know if you have done this already.

---

### Post by daveMustane on 2011-09-02
@srs5694 to me the possible disadvantages (no screen brightness control, no suspend/resume, no virtual terminals) speak against EFI boot for now. The advantages (quicker boot time graphics card flexibility) play a rather small role on a 2011 MBA. Without OSX boot media I'm also a bit hesitant to again attempt to put the bootloader on /dev/sda. 
Thank you for providing the link to the Ubuntu UEFIBooting site. It seems to explain what went wrong the 1st time I tried to install a standard x86_64 Ubuntu 11.04 ISO (...due to corrupted firmware...) and refers to an alternative ISO CD for Mac's only. Interesting! I installed gdisk in OSX. Good to have. 

@dfacto yes, I did add nomodeset to my grub defaults before. I just verified this. I can boot Ubuntu from USB stick, chroot to my Ubuntu root partition (/dev/sda5) and change my grub settings any way I like. But when trying to boot from /dev/sda5 directly I always get the black screen with a blinking cursor. 

I guess if the graphics driver was functioning already, my booting issue would be a little more painful : )

---

### Post by dfacto on 2011-09-02
@daveMustane Well it just so happens that I am your new best friend.  I just made this fight for the last 24 hours and isolated the problem.  Since you will be destroying your Linux partitions to make the fix, I would greatly appreciate it if you gave Oneiric a try and get back to us.  A word of caution: my fix applies to Natty. It is possible that Oneiric will still necessitate an Internet recovery.

The short answer. sda5 is just a no-no.  The MBR partition must be sda4 (or smaller, ie sda1 sda2 sda3).

The long answer:

After running Natty for a few weeks I thought I would give Oneiric another clean try (its now [beta]("http://www.phoronix.com/scan.php?page=news_item&px=OTg2NA") as of yesterday or so).  I prefer to have /home and / as separate mount points and this worked for Natty so I LiveCD(usb) booted as [as before]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43") and gparted to the following layout:

Table:
sda1 "EFI"        (FAT)     [OSX invisible; 200mb]
sda2 "Apple_HFS Mac OS" (HFS+) [disk utilities resized to ~40gb]
sda3 "Apple_Boot" (unknown) [OSX invisible; 650mb]
sda4 "Linux Home" (ext4)    [gparted to ~55gb]
sda5 "Linux Root" (ext4)    [gparted to ~16gb]
sda6 "Linux Swap" (swap)    [gparted to  ~4gb]

As before I mounted / to the "Linux Root" partition and installed the MBR to the same (sda5). Install went fine, I rebooted, and refit resync worked (the first time).

Shutting down and running refit resync a second time (which shouldn't be necessary) gave the error:
"Error: Not Found returned from gptsync.efi"
Using the LiveCD and installing the gptsync package (universe) also gave the same error.  I also tried fsck.hfsplus (hfsprogs from universe !!!after disabling journaling from OSX!!!).

At this point I could not boot the Linux drive. Refit shows both Linux and Mac boot options, but choosing Linux hangs at the Tux/white background screen. Mac OSX still booted, but disk utilities indicated partition errors and would not allow any changes to the partition table.  The EFI partition now shows up as visible in disk utilities as does the Recovery partition (this is bad).

So I wiped everything and did the Internet recovery...THREE TIMES.  Each time I tried some different variations and on the third try I gave up and decided to return to Natty.

After re-following my [original walk-through]("http://ubuntuforums.org/showpost.php?p=11091959&postcount=36") I chose Linux from refit and saw the "No Operating System Found".  This means that either the grub-install failed and the MBR was not pointing to any boot image OR refit could not find a MBR.

Luckily, since Natty had worked before I was able to isolate the only change from before. When I used gparted the very first time (some weeks ago), I specified the size/location of the root partition FIRST and to be in the middle of the ~80gb reserved for Linux.(*) The second time I chose the swap first (placing it at rear) then root (middle) then home (head). 

The difference?  Notice that when things worked the layout was:
  sda5 home
  sda4 root (mbr)
  sda6 swap
and when it failed to boot:
  sda6 home
  sda5 root (mbr)
  sda4 swap.

Why should this make a difference?  It seems legacy partitioning allows up two FOUR partitions (which is why on legacy systems one creates a logical partition as needed).  I suspect that resync gets confused when the MBR is on a partition outside the legacy admissable range.  I *think* it then either disregards the existence of any MBR partition and/or incorrectly maps the EFI partition (the only remaining boot flagged partition).

Final conclusion: make sure to use gparted and not disk utilities so that way you can ensure that the MBR'ed partition is located at 4 (or less if you intentionally nuked OSX).

Two final comments.

1) Some people have reported Oneiric install crashing at or near 71%.  I believe this is when initramfs and grub-install happens and could be related to the above comments/observations. It does not seem to happen as of alpha-3 but there are certainly still issues (viz. corrupting the table in such a way that OSX still boots but cannot alter the configuration).
2) I have not tried re-partitioning and re-installing Oneiric afeter making these discoveries.  It is very easy to use the Internet Recovery and I encourage anyone to try and report back to us (now that we know how to return to a working state). I won't because I am sick-to-death of waiting the requisite hours for Lion reinstall (which would only be necessary if the Oneiric problem is not related to my partition-ordering problem.) 

Cheers!

(*) - Doing it this way results in less mouse clicks which is tedious with the unconfigured trackpad. Also I wanted root to be in middle for possible future resizing purposes.
(!!!) - ```
diskutil disableJournal disk0s2
```

---

### Post by daveMustane on 2011-09-02
@defacto I recreated my partitions with root (11.10) + MBR now on /dev/sda4. But no difference. Still no boot. Still only a cursor to look at. What you say about the 1st four partitions makes sense. But something else isn't working for me. It might have something to do with me trying to install from USB stick. 

Anybody out there able to install 11.04 or 11.10 on a MBA 2011 from USB drive? I was able to get this done on the MBA 2010 - but can't get there with the new model.

---

### Post by dfacto on 2011-09-02
> **daveMustane said:**
> @defacto I recreated my partitions with root (11.10) + MBR now on /dev/sda4. But no difference. Still no boot. Still only a cursor to look at. What you say about the 1st four partitions makes sense. But something else isn't working for me. It might have something to do with me trying to install from USB stick. 

Anybody out there able to install 11.04 or 11.10 on a MBA 2011 from USB drive? I was able to get this done on the MBA 2010 - but can't get there with the new model.

Wow really sorry to hear that.  I actually did use a USB stick. If you can boot it once then this is not the problem.  I suggest trying 11.04.  Also, have you shutdown then refeit resync then shutdown again?  (Not reboot but SHUTDOWN.)

---

### Post by daveMustane on 2011-09-02
> **dfacto said:**
> Wow really sorry to hear that.  I actually did use a USB stick. If you can boot it once then this is not the problem.

Thank you. I can boot from USB. I'm just not able to boot from disk what I have installed after booting from USB. I thought you were mentioning superdrive somewhere.

When you run the installer from USB, don't you have do something like 'sudo umount -l -r -f /cdrom' before? I do. I also have to do one other nasty step to prevent the installer from crashing during file copy. It's described here: [http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0](http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0)

> **dfacto said:**
> I suggest trying 11.04.  Also, have you shutdown then refeit resync then shutdown again?  (Not reboot but SHUTDOWN.)

I will and will report back. Thank you very much for your support.

---

### Post by User4519 on 2011-09-03
> **dfacto said:**
> 
Table:
sda1 "EFI"        (FAT)     [OSX invisible; 200mb]
sda2 "Apple_HFS Mac OS" (HFS+) [disk utilities resized to ~40gb]
sda3 "Apple_Boot" (unknown) [OSX invisible; 650mb]
sda4 "Linux Home" (ext4)    [gparted to ~55gb]
sda5 "Linux Root" (ext4)    [gparted to ~16gb]
sda6 "Linux Swap" (swap)    [gparted to  ~4gb]


Question... This doesn't look valid either way. We're talking MBR, i.e. maximum four primary partitions sda1-4 OR three primary partitions (sda1-3) and an extended partitions (sda4) containing the remaining number of logical partitions (sda5...).

That is, you can't have a partition containing an FS on sda4 if you also have sda5, as sda4 would then have to be the extended area containing the remaining logical partitions. In other words, your table - if valid - should either be:


```

Table:
sda1 "EFI"        (FAT)     [OSX invisible; 200mb]
sda2 "Apple_HFS Mac OS" (HFS+) [disk utilities resized to ~40gb]
sda3 "Apple_Boot" (unknown) [OSX invisible; 650mb]
sda4 "Linux Home" (ext4)    [gparted to ~75gb]

```

or

```

Table:
sda1 "EFI"        (FAT)     [OSX invisible; 200mb]
sda2 "Apple_HFS Mac OS" (HFS+) [disk utilities resized to ~40gb]
sda3 "Apple_Boot" (unknown) [OSX invisible; 650mb]
sda4 Extended [~75gb]
sda5 "Linux Home" (ext4)    [gparted to ~55gb]
sda6 "Linux Root" (ext4)    [gparted to ~16gb]
sda7 "Linux Swap" (swap)    [gparted to  ~4gb]

```

Please excuse me if it's just a typo :)

---

### Post by srs5694 on 2011-09-03
> **DanielBuus said:**
> Question... This doesn't look valid either way. We're talking MBR, i.e. maximum four primary partitions sda1-4 OR three primary partitions (sda1-3) and an extended partitions (sda4) containing the remaining number of logical partitions (sda5...).

I got the impression that the disk was a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) disk -- in other words, a GPT disk with a hacked MBR to enable Windows to boot from it. Linux doesn't require a hybrid MBR (it reads the GPT side just like OS X does), but many Linux installation procedures for Macs create hybrid MBRs anyhow, apparently to get the Mac's BIOS emulation mode to start up. This is confusing and dangerous, but its common.

In any event, if it's a hybrid MBR, then those are perfectly valid GPT partitions, but only three of them will be copied over into the MBR. (One MBR entry will be a type-0xEE partition to identify the disk as a GPT disk.)

> That is, you can't have a partition containing an FS on sda4 if you also have sda5, as sda4 would then have to be the extended area containing the remaining logical partitions.

Even in a pure MBR setup, this isn't quite right. *Any* of the four primary partitions can be an extended partition, not just the fourth one. It's a bit less confusing if the extended partition is the fourth primary and if it (and therefore the logical partitions it contains) occupies the end of the disk, but neither of these is an actual requirement.

One other comment, since I began by describing hybrid MBRs: Hybrid MBRs should *not* contain extended or logical partitions. Although it's theoretically possible to create a layout like that, it would be an absolute nightmare to maintain. Fortunately, I don't know of any program that makes the attempt.

---

### Post by dfacto on 2011-09-03
Well the table you quoted me is the table that I found to not work.

Second, I have been successfully using 6 partitions in both Mac and Linux so your comment about correctness, perhaps true, doesn't seem to matter.

Thrid, I wasn't able to install an extended partition (which is what I would obviously perfer).  Were you?

Finally its important to note that this process builds a hybrid MBR--I do not know what is "acceptable" for hybrid MBR, but I am certain that it deviates from the conventions of a typical MBR.

---

### Post by dfacto on 2011-09-03
@srs5694  Thank you for helping us figure things out on the Mac.  I spent quite a bit of time on your site and you are doing a great service to the community.

I wonder if you might help me figure out an alternative to having to wipe everything upon a bad install (ie I've been doing Internet recovery after every gptsync problem--this is slowing my ability to try different configurations).  Here is what happens, as best I can account.

I use Mac "disk utility" to partition the drive into two partitions, one HFS+ and one MSDOS.

I shutdown, resync (fromm refit), shutdown, and boot into Oneiric LiveCD (using USB).

I use gparted and delete the MSDOS partition and carve out:
```

Loc MiB    FS         Label
4   16384  ext4       "root"
5    4352  linux-swap "swap"
6   56009  ext4       "home"

```


I prefer to have swap in the middle so that I could, theoretically, reassign it to either root or home as needed.

I install Oneiric, setting the MBR to sda4.  Upon shutdown, refit, shutdown, boot, I check refit again, this time it gives:
Analysis inconclusive, not touching disk.
Error: Not found ... from gptysync.efi.
At this point choosing Mac still boots but choosing Linux hangs at the Tux screen.

Now running Disk Utility from either the Internet recovery or Mac (which still boots fine) shows the EFI partition (which obviously should be hidden).

My question: what could oneiric install be doing that natty install didn't?  (I know this is a big question to ask, but I'm hoping nonetheless that your experience yields some insight.)

Second question: what can I do when gptsync status is "inconclusive"?  I played with your fixpart and gdisk but I didn't know what I should choose. (I have a moderate amount of nix experience but this whole EFI/Hybrid business is still relatively new to me. Point being--brevity is okay!:)

Third question: I have found that oneiric sorts the logical ordering.  So life is easier (when using the oneiric install) to simply partition the soon-to-be-MBR partition to be physically located as the fourth partition.  A nice feature to add to gdisk might be the ability to specify a particular order (fdisk doesn't have this either I think).  I could not find *ANY* tool to do this.  (Note: talking about logical order not physical order.)  This issue seems surprising to me as you can create partitions out-of-order (in gparted for example) and you can sort in fdisk (gdisk too right?) but you cannot, say, "undo" a sort.

Cheers

---

### Post by srs5694 on 2011-09-03
> **dfacto said:**
> Thrid, I wasn't able to install an extended partition (which is what I would obviously perfer).  Were you?

As noted in my earlier post, using an extended partition on a hybrid MBR would be a nightmare. Do not attempt it. Period.

> Finally its important to note that this process builds a hybrid MBR--I do not know what is "acceptable" for hybrid MBR, but I am certain that it deviates from the conventions of a typical MBR.

Technically, a hybrid MBR is illegal -- it violates the GPT specification, and is therefore inherently "unacceptable." As a practical matter, though, hybrid MBRs exist and must be dealt with, warts and all.

> I use Mac "disk utility" to partition the drive into two partitions, one HFS+ and one MSDOS.

Whenever you use Disk Utility to create a GPT layout with any FAT partitions, it converts the disk to a hybrid MBR form. Most people don't realize this.

> I shutdown, resync (fromm refit), shutdown, and boot into Oneiric LiveCD (using USB).

The gptsync program (or the rEFIt "resync" option, or whatever it's called) creates a hybrid MBR. In this case, it probably has no real effect, although it might create a slightly *different* hybrid MBR than what Disk Utility originally created.

> Ii use gparted and delete the MSDOS partition and carve out:
4 ext4 "root"
5 swap
6 ext4 "home"

Ordinarily, GParted replaces a hybrid MBR with a protective MBR, which is a standard part of a GPT disk. Thus, GParted turns the (illegal) hybrid MBR into a (legal) GPT disk.

> I install Oneiric, setting the MBR to sda4.  Upon shutdown, refit, shutdown, boot, I check refit again, this time it gives:
Analysis inconclusive, not touching disk.
Error: Not found ... from gptysync.efi.

I'm not sure what you mean by "setting the MBR to sda4"; interpreted literally, that makes no sense, because the MBR is sector 0 of the disk, and no partition can contain it, in either the MBR or the GPT schemes. I suspect you mean that you install GRUB to /dev/sda4.

I'm not sure why gptsync is giving you the error. One possibility is that it's confused by GRUB being in /dev/sda4, but that's just a guess.

It's also possible that there's been a recent change to libparted (upon which both GParted and the Ubuntu installer's partitioning tool are based) that's causing gptsync to be confused. One specific possibility for such a change is a new Linux-specific partition type code, which is in the pipeline for inclusion in libparted. I haven't checked its status, though, and I don't know if it's in the Oneiric alpha or beta or whatever the current version is. You can test this by installing the latest version of [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) version 0.7.2, and viewing the partition table. If the "Code" for the Linux partitions is "8300", then the Oneiric installer is using this new type code. (Older versions of gdisk will show a code of "FFFF" for this new partition type.) If the type code is "0700", then it's using the old code, and this hypothesis is incorrect. If this hypothesis is correct, then you can either work around it by changing the type code of the Linux partitions to 0700 or by using gdisk itself to create a hybrid MBR. Better yet, you can find a way to get Linux installed and booting that does *not* involve a hybrid MBR. One possibility is to boot Linux in EFI mode, as described [here.](http://www.rodsbooks.com/ubuntu-efi/index.html) Another would be to get the Mac's BIOS emulation active even when there's no hybrid MBR, but I'm not sure how possible that would be.

> Now running Disk Utility from either the Internet recovery or Mac (which  still boots fine) shows the EFI partition which should be hidden.

I'm not sure why that would be, unless the Ubuntu installer is changing its type code. Again, the output of gdisk might provide an answer. The EFI System Partition should have a type code of EF00. If it's something else, changing it back to EF00 should do the trick.

> Second question: what can I do when gptsync status is "inconclusive"?  I  played with your fixpart and gdisk but I didn't know what I should  choose. (I have a moderate amount of nix experience but this whole  EFI/Hybrid business is still relatively new to me. Point being--brevity  is okay!:smile:

My [hybrid MBR page](http://www.rodsbooks.com/gdisk/hybrid.html) describes how to create hybrid MBRs in gdisk. FixParts is useless on GPT disks (including hybrid MBR disks), and in fact it should terminate immediately when launched on one.

---

### Post by dfacto on 2011-09-03
Thanks srs5694, I believe I have a properly configured hybrid MBR.

Here are the steps I took to repair the hybrid MBR (hMBR).  It seems the new libparted (oneiric) does something to the hMBR that gptsync (e.g., from refit) does not know how to repair. This should solve the refit (permanent) hang after choosing the Linux partition. 

The following procedure will rebuild the hybrid MBR so gptsync (in refit or otherwise) doesn't complain. Everything that follows was done from a Mac OS terminal. You could just as easily do steps 1-8 from the USB Live session; you need to use /dev/sda or the appropriate device instead of /dev/disk0.
[LIST=1]
[*] Install [gdisk]("http://sourceforge.net/projects/gptfdisk/") and thank [srs5694]("http://www.rodsbooks.com/") for this gem!
[*] Run gdisk. We intend to manually create a new hybrid MBR.
```
sudo gdisk /dev/disk0
```
[*] Choose 'r' to repair and 'o' and 'p' to see current setup. Later you will need to refer to the current set-up.
[*] Choose 'h' to build a new hybrid MBR.
[*] For my set-up, I chose partitions "2 3 4" which correspond to "Mac OS", "Recovery HD", and "Linux-Root," respectively. Linux-Root should be the partition that contains the grub boot data. Also, if you are not on Mac OS X Lion, you won't(?) have the "Recovery HD" partition.
[*] Accept the default/recommended placement of EFI. This will add another partition to the selected three; hMBR has a maximum of four.
[*] For all but the Linux-Root, accept the defaults and always choose 'N' for not boot. For Linux-Root (the fourth for me), choose "83" (fs-type: Linux) and 'Y' to boot. (*)
[*] Choose 'o' to verify and 'w' to write.
[*] To fix the 30sec hang at tux (not a necessary step in repairing hybrid MBR):
```
sudo bless --device /dev/disk0s4 --setBoot --legacy --verbose
```
where disk0s4 is my Linux partition (yours may differ).

[/LIST]

Relevant documentation:
[Hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html")
[Partition Types]("http://www.win.tue.nl/~aeb/partitions/partition_types-1.html")

(*) - If you accept the default "07" then running gptsync (e.g., from refit) will prompt for a table update and then just change it to "83".

Also, the filesystem for the "Recovery HD" partition (650mb) will be unknown after a clean install (at least for the Macbook Air 4).  You must go BACK into the recovery system one more time then the drive will be formatted and loaded with the recovery system.

Options used in gdisk:

```

r	recovery and transformation options (experts only)
o	print protective MBR data
p	print the partition table
h	make hybrid MBR
w	write table to disk and exit

```

Options not used but good to know:
```

?	print [help] menu
q	quit without saving changes

```

---

### Post by dfacto on 2011-09-03
Also if anyone is interested, here is my partition table information. Note your values will most likely be different; this is for comparison purposes only.

Here is my GPT:
```

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        78534639   37.3 GiB    AF00  Mac OS
   3        78534640        79804175   619.9 MiB   AB00  Recovery HD
   4        79804416       113358847   16.0 GiB    0700  
   5       113358848       122271743   4.2 GiB     8200  
   6       122271744       236976127   54.7 GiB    0700  

``` where 4,5,6 are root, swap, and home (resp.).

Problematic hybrid MBR after oneiric grub-install. I have no idea why grub-install did this or how to stop it from happening.
```

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1           39   primary     0xEE
   2                    40       409639   primary     0x0B
   3      *         409640     78534639   primary     0xAF
   4              78534640     79804175   primary     0xAF

```

Updated hybrid MBR after using gdisk. This should be the same as if using gptsync (ie from refit).
```

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAB
   4      *       79804416    113358847   primary     0x83

```

---

### Post by srs5694 on 2011-09-03
I'm glad you got your system sorted out. I have a couple of observations, just to help fill in some gaps....

> **dfacto said:**
> Also if anyone is interested, here is my partition table information. Note your values will most likely be different; this is for comparison purposes only.

Here is my GPT:
```

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        78534639   37.3 GiB    AF00  Mac OS
   3        78534640        79804175   619.9 MiB   AB00  Recovery HD
   4        79804416       113358847   16.0 GiB    0700  
   5       113358848       122271743   4.2 GiB     8200  
   6       122271744       236976127   54.7 GiB    0700  

``` where 4,5,6 are root, swap, and home (resp.).

One unusual thing I note here is your partition #3. This has a type code of AB00 ("Apple boot"). I'm guessing this is a recovery partition of some sort, possibly taking the place of a physical installation disc. This is the first time I've heard of this partition type "in the wild," although it's been documented [on the Wikipedia page on GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) and on [Apple's Tech Note 2166](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html) for quite some time. (It's GUID 426F6F74-0000-11AA-AA11-00306543ECAC, FWIW.) It's possible that gptsync just didn't recognize it; gptsync tends to refuse to touch a disk that holds partition types it doesn't understand.

One thing I note is that you've got no [BIOS Boot Partition,](http://en.wikipedia.org/wiki/BIOS_Boot_partition) which GRUB (in its BIOS version) uses on GPT disks to improve reliability. It's possible that the lack of this partition is part of the reason for your problems. It's also possible that your problems will return after a kernel or GRUB update if this is the case. If so, you can either install an EFI version of GRUB or some other boot loader (which is likely to be an adventure) or shrink one of your partitions by ~1 MiB and create a BIOS Boot Partition (which may require creating another fresh hybrid MBR).

> Problematic hybrid MBR after oneiric grub-install. I have no idea why grub-install did this or how to stop it from happening.
```

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1           39   primary     0xEE
   2                    40       409639   primary     0x0B
   3      *         409640     78534639   primary     0xAF
   4              78534640     79804175   primary     0xAF

```

In theory, this should work -- as I said, Linux does *not* refer to the MBR side of a hybrid MBR. Its main purpose on a Linux/OS X dual-boot is to kick the Mac's firmware into BIOS emulation mode, enabling use of the BIOS version of GRUB (in the Ubuntu grub-pc package). That said, the MBR's partition #2 matches the EFI System Partition (ESP), and so would more properly be of type 0xEF. The partition #4's type code is debatable -- it's probably got HFS+, which makes 0xAF correct, but the MBR code 0xAB (which gdisk generated for this partition) is "Darwin boot," but I'm not sure if that's really an equivalent type. (It *sounded* similar, which is why I assigned the equivalency when I wrote gdisk, but that was just a guess on my part.)

> Updated hybrid MBR after using gdisk. This should be the same as if using gptsync (ie from refit).
```

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAB
   4      *       79804416    113358847   primary     0x83

```

If it works, you might as well stick with it. You might also want to back up your GPT data using the "b" option on gdisk's main menu. This will create a binary file containing all the GPT data structures, including the MBR. You can easily restore it using the "L" option on the recovery & transformation menu. Of course, you should store your backup on a USB flash drive, CD-R, or some other disk other than the one you're backing up!

---

### Post by dfacto on 2011-09-04
Thanks again srs5694.

What I find the most interesting is that things "just worked" for the old libparted.  I suspect there will be many upset people in the not-too-distant-future.  In any event, gdisk is exceedingly easy to use and the fix is just a matter of accepting some defaults.

Indeed it is a recovery partition.  Lion install carves it out of whatever partition you plop lion in.  After booting into Internet recovery on an originally blank drive and installing Lion results in the partition having fs type "unknown" (as per gparted).  Booting into Internet recovery a second time results in the fs you saw as well as one directory containing a dozen or so files (one of which is boot.efi another is a large-ish .dmg).

Oh, and now after understanding more about the hMBR and GPT I see why renumbering partitions really is unnecessary.  Its a pity that the refit documentation doesn't refer people to gdisk when gptsync falls short.  In fact, gdisk should ship with refit if you ask me.

Cheers

---

### Post by jcs2 on 2011-09-04
i've been following this thread waiting for the intel xorg driver fix, and although i'm running a different operating system (openbsd) next to mac os x on my 11" air, i thought i'd mention that it is possible to still use refit if you have encrypted your mac partition with filevault.

although openbsd (and probably linux) boot fine by just holding down option at boot and selecting the bootcamp partition, with refit, the ssd shows up as a SCSI disk instead of emulated IDE, so i wanted to continue using it.

when encrypting an hfs partition with filevault, it turns it into a corestorage partition and changes the boot process, disabling refit.  to re-enable refit, manually mount the recovery partition (probably /dev/disk0s3) in os x with "[FONT=Courier New]mkdir /Volumes/recovery; mount -t hfs /dev/disk0s3 /Volumes/recovery[/FONT]".  once mounted, copy your old /efi/{refit,tools} directories from / into /Volumes/recovery/efi/, then run the [FONT=Courier New]./enable-always.sh[/FONT] script from /Volumes/recovery/efi/refit.

on the next reboot, refit will only show the mac recovery partition and linux (openbsd in my case) partition, though selecting the recovery partition will boot the normal (now encrypted) mac partition, not recovery.  recovery is still available through command+r before refit boots (i hope).

it's also worth noting that after enabling filevault, it wiped out my hybrid MBR and just created one big protective MBR, so openbsd no longer booted through refit.  i had to boot into mac os and use gdisk to create a new hybrid MBR with my openbsd partition.  my layout now looks like:

```

jcs@air:~> sudo gdisk /dev/disk0
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B5B2EB0B-58F4-43EF-8422-2AE142433801
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 2317 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       156659639   74.5 GiB    FFFF  mac
   3       156659640       157929175   619.9 MiB   AB00  Recovery HD
   4       157929472       236976127   37.7 GiB    FFFF  OpenBSD

Command (? for help): x

Expert command (? for help): o

Disk size is 236978176 sectors (113.0 GiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640    156659639   primary     0xFF
   3             156659640    157929175   primary     0xAB
   4      *      157929472    236976127   primary     0xA6

Expert command (? for help): 

```

---

### Post by kujuntuluntufurtu on 2011-09-05
Was looking for a fix ...

 Can someone tell me what this means ?  Totally new to linux. How can I apply that temporary fix on my ubuntu ? 

[https://bugs.freedesktop.org/show_bug.cgi?id=39533](https://bugs.freedesktop.org/show_bug.cgi?id=39533)

freedesktop                                                  2011-09-03 00:06:10 PDT                    [Created an attachment (id=50855)]("https://bugs.freedesktop.org/attachment.cgi?id=50855") [[details]]("https://bugs.freedesktop.org/attachment.cgi?id=50855&action=edit") script to make the fbdev experience slightly more tolerable  The attached script is the result of sitting down for a little while with a new MacBook Air and the Intel HD3000 manual. It doesn't produce real 1440x900 but it does fix the aspect ratio, the blurriness, and the full-intensity backlight.  At this point I'm convinced that the mode-setting trouble in the existing Intel driver is simple sloppiness, not something subtle. Doing the Right Thing might take effort, but making a workaround for MacBook Air users should be a tiny patch. A few days from now I'll have time to look at what the driver is doing.

---

### Post by dfacto on 2011-09-05
It means that the user read the SNB manual and determined which register and the appropriate code to make the aspect ratio and brightness look better.  It will still be 1024x768 so at this point its not a big change.  If you don't know how to follow the steps listed in the attachment, I wouldn't worry.  Its not a huge deal.

Also, the submitted script is unnecessarily complicated for Ubuntu users; for example, you can change the brightness by:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update -q2
sudo aptitude install intel-gpu-tools
sudo intel_backlight 50

```

---

### Post by kujuntuluntufurtu on 2011-09-06
> **dfacto said:**
> It means that the user read the SNB manual and determined which register and the appropriate code to make the aspect ratio and brightness look better.  It will still be 1024x768 so at this point its not a big change.  If you don't know how to follow the steps listed in the attachment, I wouldn't worry.  Its not a huge deal.

Also, the submitted script is overly complicated in many regards; for example, you can change the brightness by:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude install intel-gpu-tools
sudo intel_backlight 50

```


 Ok then I will wait for the final :- ) thank you

---

### Post by dentifrice on 2011-09-06
Intel driver issue solved, apparently (but not yet commited upstream AFAIK): _[https://bugs.freedesktop.org/show_bug.cgi?id=39533#c25](https://bugs.freedesktop.org/show_bug.cgi?id=39533#c25)_

Note that I couldn't test it myself for I haven't yet upgraded my Air (waiting for that bug to be resolved, basically).

I'd love to know if there's any showstopper still, and how the MBA4{1,2} behaves when booted in EFI mode (especially with the intel driver fix).

---

### Post by dfacto on 2011-09-06
[Macbook Air + Ubuntu = Happy.]("http://www.almostsure.com/mba42/fix-i915.sh")

---

### Post by jonny on 2011-09-06
I confirm this works perfectly with 11.04, kernel 2.6.38-11-generic.  I didn't follow dfacto's script to the letter as I'd already patched the relevant file by the time his post appeared, but the compilation steps certainly performed as expected when entered one line at a time in a terminal.

Now to upgrade to Oneiric and get the other bits working that I hadn't previously bothered with - touchpad, Mac-specific keyboard, etc.

Brilliant.  I can go to bed a very happy man.

---

### Post by dfacto on 2011-09-06
Please let me know any improvements you can make over [post-install.sh]("http://almostsure.com/mba42/post-install.sh") so we can track all tweaks.

I believe I have everything working but the trackpad is still kind of annoying.  Key re-mapping needs work too. (Haven't done suspend yet either.)

---

### Post by berto- on 2011-09-06
This entire thread is an excellent source of information for getting the MBA running with Ubuntu, but has anyone seen a single-post writeup on getting the system running end-to-end?  I think the list of must-haves is:

- full 1440x900 resolution
- screen brightness control
- keyboard brightness control
- trackpad support
   - right-click
   - scrolling
   - other gestures?
- wifi
- bluetooth
- mic
- camera

On a similar note, does anyone have numbers on how long the battery lasts using ubuntu on an MBA?  i've seen decent lifetime using Parallels; I imagine it should be even better running ubuntu directly.

---

### Post by dfacto on 2011-09-06
> **berto- said:**
> This entire thread is an excellent source of information for getting the MBA running with Ubuntu, but has anyone seen a single-post writeup on getting the system running end-to-end?  I think the list of must-haves is:

- full 1440x900 resolution
- screen brightness control
- keyboard brightness control
- trackpad support
   - right-click
   - scrolling
   - other gestures?
- wifi
- bluetooth
- mic
- camera

On a similar note, does anyone have numbers on how long the battery lasts using ubuntu on an MBA?  i've seen decent lifetime using Parallels; I imagine it should be even better running ubuntu directly.

Everything works for me except camera.  (Suspend works MARVELOUSLY--as fast as OSX!?)  You could start translate the items in my post-install script to the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2").  I think that would be nicer than the forums.  Anyway it shouldn't be hard and even if no one steps up, its not strictly necessary.  I just reinstalled oneiric and running my script gets everything up and running with no problems. Also, don't forget [this post]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75").

**Update**: I cleaned up [the script]("http://www.almostsure.com/mba42/post-install.sh") some more.  Make sure to get a fresh snapshot and let me know if there is a problem.

---

### Post by kujuntuluntufurtu on 2011-09-06
Plz ...

 I am confused ! can someone tell me STEP BY STEP how I should install this fix ?

 I have downloaded the 32 BIT ( 11.4 )   Of course I should install that first then what ?
 Is this fix also works on 64 Bit ?

 By the way,

 Is there any way I could REMOVE MAcOs totally ? just running linux instead  ?  I removed MACOSx once but the linux booting was taking so so so much time ...  it took a min or so to detect Linux partition - got stuck at gray screen for a min or so ,

 Thank you

---

### Post by kujuntuluntufurtu on 2011-09-06
> **dfacto said:**
> Everything works for me except camera.  (Suspend works MARVELOUSLY--as fast as OSX!?)  You could start translate the items in my post-install script to the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2").  I think that would be nicer than the forums.  Anyway it shouldn't be hard and even if no one steps up, its not strictly necessary.  I just reinstalled oneiric and running my script gets everything up and running with no problems.

**Update**: I cleaned up [the script]("http://www.almostsure.com/mba42/post-install.sh") some more.  Make sure to get a fresh snapshot and let me know if there is a problem.


 dFacto, can you tell me how I should run this script ? As I told you once totally new to linux.

   install ubuntu first then what should I do ?  I also want to remove MACOSX totally. I did once but got stuck on gray screen for a min till booted into linux.

 ***UPDATE*** : I googled and found my answer I think ...
 [http://www.zimbio.com/Ubuntu+Linux/articles/294/How+install+run+sh+file+Linux](http://www.zimbio.com/Ubuntu+Linux/articles/294/How+install+run+sh+file+Linux)

 Hope that works for me .

---

### Post by dfacto on 2011-09-06
@kujuntuluntufurtu That link looks right to me. You may want to just wait for some of the other regulars to confirm the script works okay though.  As I said, I have personally used it and everything works but I would hate for something to happen to a novice's system.  Most of the people on this thread are very active so I am sure there will be an answer by tonight or tomorrow.

Seriously.  Oneiric on MBA4,2 is a GLORIOUS thing.  It was well worth the wait!  I could NOT be happier!

---

### Post by kujuntuluntufurtu on 2011-09-06
> **dfacto said:**
> @kujuntuluntufurtu That link looks right to me. You may want to just wait for some of the other regulars to confirm the script works okay though.  As I said, I have personally used it and everything works but I would hate for something to happen to a novice's system.  Most of the people on this thread are very active so I am sure there will be an answer by tonight or tomorrow.

Seriously.  Oneiric on MBA4,2 is a GLORIOUS thing.  It was well worth the wait!  I could NOT be happier!


 Oneiric is still in Alpha state right ? maybe I should download that ?

 By the way, I really want to install 64 bit version ... that script works on 64 bit right ?

 I will give it try anyways ! Got my MBA recently so happy to install linux on it .

 so much thanks to you .

 ***UPDATE :*** Ubuntu 11.10 Oneiric is Beta now. I googled again. 
**[http://fridge.ubuntu.com/2011/09/01/ubuntu-11-10-beta-1-oneiric-ocelot-released/](http://fridge.ubuntu.com/2011/09/01/ubuntu-11-10-beta-1-oneiric-ocelot-released/)**

---

### Post by dfacto on 2011-09-06
32 or 64 shouldn't matter....however...if you are just getting things set-up I would use this as an opportunity to put on 64bit. Then youll never have to worry about it ever again.

Stay with natty for now.  You don't *need* oneiric to get everything up and running.  For new-users its always best to stay with stable releases.

---

### Post by kujuntuluntufurtu on 2011-09-06
> **dfacto said:**
> 32 or 64 shouldn't matter....however...if you are just getting things set-up I would use this as an opportunity to put on 64bit. Then youll never have to worry about it ever again.

Stay with natty for now.  You don't *need* oneiric to get everything up and running.  For new-users its always best to stay with stable releases.


 Ok thank you. By the way, I removed MACOSX once and installed ubuntu on my MBA but booting time was taking so much time ... got stuck on gray screen for a min or so then booted into ubuntu finally.   Do you know why when you remove MACOSX totally this happens ? Any links or help ? cause I want to remove Macosx totally .

---

### Post by kujuntuluntufurtu on 2011-09-06
> **dfacto said:**
> 32 or 64 shouldn't matter....however...if you are just getting things set-up I would use this as an opportunity to put on 64bit. Then youll never have to worry about it ever again.

Stay with natty for now.  You don't *need* oneiric to get everything up and running.  For new-users its always best to stay with stable releases.

 I installed Oneiric + run the script and also fixi915 ...  

 STILL have to type nomodeset on grub ! cannot boot without it ! still get low resolution .

 Any idea ?

---

### Post by kujuntuluntufurtu on 2011-09-07
Folks ...

 Can anyone tell me why when I run the script and restart I still need to set modeset in order to log in the resolution is still 124 x 768 ? 

 I ran the script and just restart the computer ! nothing happens. DO I HAVE to do anything more ?

 Ubuntu is not for NERDS ! I suppose you should help people like me who are totally new to linux ! 

 I ran the script on 11.4 version 32 bit ...( removed Oneiric and installed 11:4 32 bit )  and restart the computer nothing happens Still same ****.

 Do I have to do anything more besides running  that script ?  I am asking this becasue some of you already solved the problem. So can someone be kind and make the proccess simple for people like me who are not familiar with linux ?  or I should just leave this forum and say ubuntu is not for human being but stil for the nerds ! ! !

 This is what I get when I run in terminal ... the the terminal closes unexpectly ...

[QUOTE= [sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-2.6.38-8-generic'
The following NEW packages will be installed:
  asciidoc binutils-dev docbook-dsssl docbook-utils docbook-xsl gawk jadetex
  kernel-wedge libdw-dev libdw1 libelf-dev libosp5 libostyle1c2 libsgmls-perl
  libsp1c2 luatex lynx lynx-cur makedumpfile openjade sgmlspl sharutils sp
  tex-common texlive-base texlive-binaries texlive-common texlive-doc-base
  texlive-fonts-recommended texlive-latex-base texlive-latex-recommended tipa
  transfig xmlto
The following packages will be upgraded:
  binutils
1 upgraded, 34 newly installed, 0 to remove and 222 not upgraded.
Need to get 21.8 MB/60.5 MB of archives.
After this operation, 169 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main texlive-base all 2009-11 [14.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main texlive-fonts-recommended all 2009-11 [7,166 kB]
Fetched 21.8 MB in 56s (384 kB/s)                                              
Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended_2009-11_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended_2009-11_all.deb)   Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
E: Failed to process build dependencies
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-2.6.38-8-generic'
NOTICE: 'linux' packaging is maintained in the 'Git' version control system at:
[http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-natty.git](http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-natty.git)
Skipping already downloaded file 'linux_2.6.38-11.48.dsc'
Need to get 99.6 MB of source archives.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main linux 2.6.38-11.48 (tar) [94.1 MB]
.[/QUOTE]

 seems some failing going on ...

 **UPDATE :  **I left the forum and also removed ubuntu. God bless MACOSX. Easy and just works.

 Bye .

---

### Post by daveMustane on 2011-09-07
> **dfacto said:**
> Seriously.  Oneiric on MBA4,2 is a GLORIOUS  thing.  It was well worth the wait!  I could NOT be happier!
 
I can confirm native resolution + sleep/wake + Bluetooth on my MBA2011  13'' w/ Oneiric x64, basically just following the two scripts. What a  major step forward! Wonderful. Thank you so much.

No multitouch + no special keys. And my vents seem to go on a little  quicker + get a little louder under load. Do you have that as well?

---

### Post by dfacto on 2011-09-07
> **daveMustane said:**
> I can confirm native resolution + sleep/wake + Bluetooth on my MBA2011  13'' w/ Oneiric x64, basically just following the two scripts. What a  major step forward! Wonderful. Thank you so much.

No multitouch + no special keys. And my vents seem to go on a little  quicker + get a little louder under load. Do you have that as well?

You can tweak the fan settings in /etc/macfanctld.conf. If you find a better setting (ie one that more closer mimics OSX), please let us know. I don't even know if macfanctld is strictly necessary but for now I'm keeping it.  There are one or two other alternatives out there,  but this one seemed simple and was binary (which for daemons is obviously preferable).

What do you mean "No multitouch + no special keys"?  I can two-finger-click to signal secondary mouse click and two-finger scroll.  My fn+key combos work too.  IIRC, I may have done xmodmap ~/.Xmodmap one more time.  I think Gnome knows to read the file so unity should too.

---

### Post by dfacto on 2011-09-07
> **kujuntuluntufurtu said:**
> Folks ...

 or I should just leave this forum and say ubuntu is not for human being but stil for the nerds ! ! !

  **UPDATE :  **I left the forum and also removed ubuntu. God bless MACOSX. Easy and just works.

 Bye .



My favorite part was when he yelled at us AS we OURSELVES were working out the solution. :)

In any case I updated the [i915 fix-it script]("http://www.almostsure.com/mba42/fix-i915.sh") to handle the 11" MBA in addition to the 13" (kujuntuluntufurtu, I'm talking to you.)

---

### Post by dfacto on 2011-09-07
Can someone with a working Ubuntu and who did NOT use gdisk do me a favor? 

Can you enable universe and install gptsync, run it (sudo gptsync /dev/sda), and paste the results back here?

I want to double-check that my manually specified hybrid MBR is the same as it was before my libparted escapades.  (I am pretty sure it is, but now that everything is humming nicely I want to follow up on this.)

This gptsync is the same as the one you ran in refit and so it can't do any harm, particularly if you're already in Ubuntu.  Moreover, the hybrid MBR is not needed by OSX (nor even Linux) and is only needed to put the firmware in legacy mode for non-efi booting.

---

### Post by berto- on 2011-09-07
I am dual-booting right now using rEFIt; is there a better way?  Sometimes rEFIt takes forever, which is not desirable.

dfacto, my MBA is at home, so I can check gptsync after work.

---

### Post by dfacto on 2011-09-07
> **berto- said:**
> I am dual-booting right now using rEFIt; is there a better way?  Sometimes rEFIt takes forever, which is not desirable.

dfacto, my MBA is at home, so I can check gptsync after work.

Great thanks berto-.  Yeah mine is painfully slow at times too.  It takes 8-9 seconds for the firmware to kick-in the legacy bios layer (ie white tux for 8-9 sec then grub loads).  Only option is pure EFI and I guess none of us are brave enough to try it.  After all, we only just got this up and running. :)

---

### Post by dfacto on 2011-09-07
Webcam now working too.  I added a FaceTime section to [post-install.sh]("http://almostsure.com/mba42/post-install.sh").

Anything else left to do?

---

### Post by berto- on 2011-09-07
> **dfacto said:**
> Webcam now working too.  I added a FaceTime section to [post-install.sh]("http://almostsure.com/mba42/post-install.sh").

Anything else left to do?

Wow, that's awesome, dfacto!

I'll soon find out myself, but how good is the trackpad integration.  Does it provide vertical and horizontal scrolling?

---

### Post by dfacto on 2011-09-07
> **berto- said:**
> Wow, that's awesome, dfacto!

I'll soon find out myself, but how good is the trackpad integration.  Does it provide vertical and horizontal scrolling?

Yes and yes.  

HOWEVER, it definitely needs some tweaking.  Its hard to explain...it responds to the thumb differently than I expect.  You'll see. :)

I think we can just about close the book on get the MBA up and running.  Now it remains to see how annoying it will be to maintain our various hacks.  In any event things look great!

---

### Post by dfacto on 2011-09-07
Oops--seems that something changed between yesterday and today because now suspend doesn't work.  Feel free to explore it but I'm chalking this up to Oneiric being beta.

---

### Post by berto- on 2011-09-07
> **dfacto said:**
> I think we can just about close the book on get the MBA up and running.  Now it remains to see how annoying it will be to maintain our various hacks.  In any event things look great!

Does it make sense to create a PPA on launchpad specifically for the MBA?

---

### Post by dfacto on 2011-09-07
> **berto- said:**
> Does it make sense to create a PPA on launchpad specifically for the MBA?

Nah, I don't think so.  Here's the break-down:

Modified with patch submitted to kernel.org:
- bcm5974-dkms
- hid-apple-dkms

Modified but patch not submitted to kernel.org:
- btusb-dkms

Mactel doesn't have a Oneiric build and was necessary to modify for 3.0+ headers.  This package is only needed when using dkms (above) so we won't need it once the patches start trickling down.
- hid-dkms

Regularly built by [someone]("http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/"):
- xserver-xorg-input-mtrack

Using kernel version:
- applesmc

Not needed at all:
- snd-hda-dkms
- mbp-nvidia-bl-dkms

Mactel:
- xf86-input-multitouch
- isight-firmware-tools
- macfanctld


So, basically we only need to build 3+1 packages. When two of those kick-in, then the fourth is not needed.  Someone should get btusb in--I haven't had time.  Everything else is Mactel ppa.  Also, everyone should be aware that using these dkms's is BAD because its stale code.  The kernel has new code, but I am still using the dkms's because its easier to get going and help other people. (Although the i915 fix kind of defeated my plan since I wanted to avoid this kind of a revuild-the-kernel-hack. Note: dkms's auto rebuild upon new kernel install.)

So the conclusion is that really all I did was to collect all the relevant info in one place.  The best thing now is to either update the wiki or simply wait until all these packages go away then update the wiki.  Probably both are best.

Oh, and suspend works if you make the call directly, ie, 
```
sudo /etc/acpi/sleep.sh
```
Dunno why it doesn't work from dash.

---

### Post by dfacto on 2011-09-07
gpt-sync?

---

### Post by berto- on 2011-09-08
I ran apt-get update && apt-get upgrade on my oneric install and after a reboot I was unable to get on the network and everything was super funky.  If I'm not able to get it on the network I'll likely have to start from scratch again.  :(

In any case, I wasn't able to run gptsync, but will do so once I have a working system again.

---

### Post by dfacto on 2011-09-08
> **berto- said:**
> I ran apt-get update && apt-get upgrade on my oneric install and after a reboot I was unable to get on the network and everything was super funky.  If I'm not able to get it on the network I'll likely have to start from scratch again.  :(

In any case, I wasn't able to run gptsync, but will do so once I have a working system again.

Bummer...wonder what went wrong?  Which install cd did you use, alpha or beta?  I used beta...

---

### Post by jonny on 2011-09-08
Well, after a lengthy and somewhat confusing debugging session, I've found a small problem with the fix-i915 shell script.

On a fresh install of the Oneiric AMD64 daily build from 7 September, kernel 3.0.0-10-generic, I found that I was unable to boot into glorious 1440x900.  I finally tracked the problem down to the newly compiled module being placed in the wrong folder, and fixed things with the following commands:
```
sudo cp /lib/modules/3.0.0-10-generic/extra/i915.ko /lib/modules/3.0.0-10-generic/kernel/drivers/gpu/drm/i915/i915.ko
sudo depmod -a
sudo update-initramfs -u
```
I'm not sure that the last two commands were strictly necessary, but I included them for good measure to save multiple reboots.

---

### Post by jonny on 2011-09-08
> **dfacto said:**
> Can someone with a working Ubuntu and who did NOT use gdisk do me a favor? 

Can you enable universe and install gptsync, run it (sudo gptsync /dev/sda), and paste the results back here?

Output is as follows:
```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    175645591  Mac OS X HFS+
 3      175645592    176915127  Mac OS X Boot
 4      176915128    176917081  BIOS Boot Partition
 5      176917082    228772550  Basic Data
 6      228772551    236978142  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  0b  FAT32 (CHS)
 3 *       409640    175645591  af  Mac OS X HFS+
 4      175645592    176915127  af  Mac OS X HFS+

Status: Analysis inconclusive, will not touch this disk.
```

---

### Post by berto- on 2011-09-08
> **dfacto said:**
> Bummer...wonder what went wrong?  Which install cd did you use, alpha or beta?  I used beta...

I think the main problem was not running apt-get distupgrade.  When running nmcli I was getting errors that the command was not compatible with the backend or something to that effect.

---

### Post by berto- on 2011-09-08
> **jonny said:**
> Well, after a lengthy and somewhat confusing debugging session, I've found a small problem with the fix-i915 shell script.


Hmm, I may have put the fix in the wrong script, but here is a fix in a gist on github.  Should it be relocated?

Please take a look; any comments welcome.

[https://gist.github.com/1205289](https://gist.github.com/1205289)

---

### Post by dfacto on 2011-09-08
So what's the deal with the fix-i915.sh script as is?  I ran it on 3.0.0-10 oneiric and had no problems.  berto- do you also have this problem?  I don't mind adding it to the script but I'd like to understand why the make is failing (which it shouldn't be).  Perhaps the source tree is out-of-date (this seems unlikely)? Anyway I updated the fix-i915.sh with your copy line (generalized for any kernel).

jonny - thanks for posting your gptsync.  Looks like you have the same problem I did.  I was hoping to see a working output for reference purposes--perhaps someone running Natty can post theirs?  Anyway, you can follow my earlier post to fix yours.

---

### Post by Objectivity on 2011-09-08
I am back ...

 As I told you before I have listed my MBA on eBay.... but I was not lucky enough to sell it ! the guy who won the auction  DID NOT PAY for the item !  I do not know if I should say bad luck or good luck ! cause seems the graphic card driver now fixed and maybe I can hold on to my MBA. 

 I am going to try it out on my MBA 13.

 By the way, are we able to use [I]Compiz ? 3d also works right ?

 YOurs,
 Elmo
[/I]

---

### Post by Objectivity on 2011-09-09
> **dfacto said:**
> My favorite part was when he yelled at us AS we OURSELVES were working out the solution. :)

In any case I updated the [i915 fix-it script]("http://www.almostsure.com/mba42/fix-i915.sh") to handle the 11" MBA in addition to the 13" (kujuntuluntufurtu, I'm talking to you.)


 I used this script you made for him and worked for me well ! now I have got the resolution fixed ! 

 WOW ... love it ! :guitar:

 Few things not working for me :

 1. [B]Backlit Keyboard
 2. Got the MS saying, Sorry, the program " Zeitgeist-daemon" closed unexpectedly << what ever that means lol  

   

[/B]

---

### Post by undoIT on 2011-09-09
> **Objectivity said:**
> I am back ...

 As I told you before I have listed my MBA on eBay.... but I was not lucky enough to sell it ! the guy who won the auction  DID NOT PAY for the item !  I do not know if I should say bad luck or good luck ! cause seems the graphic card driver now fixed and maybe I can hold on to my MBA. 

 I am going to try it out on my MBA 13.

 By the way, are we able to use [I]Compiz ? 3d also works right ?

 YOurs,
 Elmo
[/I]

A matter of perspective. Perhaps it was a stroke of luck that it didn't sell. :D

Ubuntu on the new Macbook Air is going to be awesome, considering how much progress has been made before Oneiric stable has even been released.

For the record, I own a Macbook 5,1, a Macbook Pro 6,2 and now the Macbook Air 4,2 along with a few other laptops and netbooks. If anyone needs to sell something on Ebay, it is me.

---

### Post by undoIT on 2011-09-09
@dfacto

any chance of getting your hacks included in the stable release?

---

### Post by berto- on 2011-09-09
> **dfacto said:**
> Can you enable universe and install gptsync, run it (sudo gptsync /dev/sda), and paste the results back here?


Here's my output:

```
berto@g6:~$ sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    244687407  Mac OS X HFS+
 3      244687408    245956943  Mac OS X Boot
 4      245956944    245958897  EFI System (FAT)
 5      482422208    489972567  Linux Swap
 6      245958898    245960851  BIOS Boot Partition
 7      474216711    482422207  Linux Swap
 8      245960852    466011633  Basic Data
 9      466011634    474216710  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  0b  FAT32 (CHS)
 3 *       409640    244687407  af  Mac OS X HFS+
 4      244687408    245956943  af  Mac OS X HFS+

Status: Analysis inconclusive, will not touch this disk.
```

---

### Post by berto- on 2011-09-09
Finally have Oneiric running with native resolution.  The script ran fine for me, but after the first reboot I did not get native resolution.  I power cycled, ran linux with nomodeset, ran the script again, and after the second reboot I was able to get native resolution.

I don't know if it was just the reboot or if it was running the script a second time that fixed the problem.

There has been great progress, but I'm still not ready to use this system full-time.  There are a couple of issues I've noticed immediately:

- the trackpad is absolutely terrible!

The trackpad does not work well at all with more than one finger on it.  Some simple examples.  Try to drag a window after clicking on the title bar; not possible.  Another is right clicking; very finicky.  Two-finger scrolling?  Nope.  I've also managed to get it to sporadically do things like highlight half this post and delete; I must have accidentally brushed my thumb on it.

- strange flicker

My terminal windows flicker and I'm not sure why.  It's not only distracting, but a little disconcerting; is this a slightly-off setting in the i915 module?  Is it a 3D issue?

- random crashes

Services simply crash unexplicably.  The biggest offender is the zeitgeist daemon.  I'm guessing this is more Oneiric's beta-ness rather than a MBA issue, but still a bit frustrating to have misc stuff just go belly up while trying to work.

All that said, amazing progress!  I can't wait to be able to use this exclusively.  One thing to note is that Ubuntu feels snappier running on bare metal.  For now, though, I'll be in parallels.

---

### Post by Objectivity on 2011-09-09
> **berto- said:**
> Finally have Oneiric running with native resolution.  The script ran fine for me, but after the first reboot I did not get native resolution.  I power cycled, ran linux with nomodeset, ran the script again, and after the second reboot I was able to get native resolution.

I don't know if it was just the reboot or if it was running the script a second time that fixed the problem.

There has been great progress, but I'm still not ready to use this system full-time.  There are a couple of issues I've noticed immediately:

- the trackpad is absolutely terrible!

The trackpad does not work well at all with more than one finger on it.  Some simple examples.  Try to drag a window after clicking on the title bar; not possible.  Another is right clicking; very finicky.  Two-finger scrolling?  Nope.  I've also managed to get it to sporadically do things like highlight half this post and delete; I must have accidentally brushed my thumb on it.

- strange flicker

My terminal windows flicker and I'm not sure why.  It's not only distracting, but a little disconcerting; is this a slightly-off setting in the i915 module?  Is it a 3D issue?

- random crashes

Services simply crash unexplicably.  The biggest offender is the zeitgeist daemon.  I'm guessing this is more Oneiric's beta-ness rather than a MBA issue, but still a bit frustrating to have misc stuff just go belly up while trying to work.

All that said, amazing progress!  I can't wait to be able to use this exclusively.  One thing to note is that Ubuntu feels snappier running on bare metal.  For now, though, I'll be in parallels.


 I had exactly the same problems ...

 I removed  Oneiric totally . It was just too much crash !

I installed 11.4 ( 64 bit ) run the script again now relatively speaking everything works just fine. 

On ( ONERIC ) even I could not run Compiz ! it was crashing ALL THE TIME ! but now is just fine.

---

### Post by jonny on 2011-09-09
> **dfacto said:**
> So what's the deal with the fix-i915.sh script as is?  I ran it on 3.0.0-10 oneiric and had no problems.  berto- do you also have this problem?  I don't mind adding it to the script but I'd like to understand why the make is failing (which it shouldn't be).  Perhaps the source tree is out-of-date (this seems unlikely)? Anyway I updated the fix-i915.sh with your copy line (generalized for any kernel).
Sorrry.  I hadn't for a moment meant to suggest that your script - which is an impressive piece of work - was at fault.  I simply meant that it didn't cater for an issue with the AMD64 kernel in the latest daily build, and offered a solution for any other hair-pulling-out victims.

I'm not sufficiently skilled to understand the problem rather than propose a rather kludgy solution.  I suspect it's another manifestation of Oneiric's beta status; I seem to recall that a kernel update was pushed out 2-3 days back and it might have arisen then.

If it helps, I was using a completley clean install with no additional repositories (eg xorg-edgers) enabled.

---

### Post by jonny on 2011-09-09
> **berto- said:**
> There has been great progress, but I'm still not ready to use this system full-time.Me neither, but it's a great plaything and I'm sure I'll be using it full time before long.
> **berto- said:**
> - the trackpad is absolutely terrible!

The trackpad does not work well at all with more than one finger on it.  Some simple examples.  Try to drag a window after clicking on the title bar; not possible.  Another is right clicking; very finicky.  Two-finger scrolling?  Nope.  I've also managed to get it to sporadically do things like highlight half this post and delete; I must have accidentally brushed my thumb on it.Completely agree, but I have different issues from you.  I enabled two finger scrolling on both axes using the standard Gnome tool, and, for me, a simple two-finger click yields a right-click.  My biggest issues are:
 - Excessive sensitivity on tap-to-click
 - Unlike OS X, it's not possible to use a second finger to complete a long-distance drag-and-drop.  As a result, the trackpad isn't large enough to complete some operations

> **berto- said:**
> - strange flicker

My terminal windows flicker and I'm not sure why.  It's not only distracting, but a little disconcerting; is this a slightly-off setting in the i915 module?  Is it a 3D issue?I don't have this at all.  It seems to be something unique to your setup.

> **berto- said:**
> - random crashes

Services simply crash unexplicably.  The biggest offender is the zeitgeist daemon.  I'm guessing this is more Oneiric's beta-ness rather than a MBA issue, but still a bit frustrating to have misc stuff just go belly up while trying to work.This happens all the time for me, too, on my Air and on both my other Oneiric set ups.  It also happened for me when Natty was in Beta, so I imagine it will disappear (perhaps by simply switching off the notification meassages) when the final release is issued.  It's harmless enough, as the daemons concerned generally respawn automatically.

> **berto- said:**
> All that said, amazing progress!  I can't wait to be able to use this exclusively.  One thing to note is that Ubuntu feels snappier running on bare metal.  For now, though, I'll be in parallels.I can't say that I've noticed any perceptable additional snappiness over running in Virtualbox.  The VirtualBox solution has the benefit of perfect touchpad behaviour, but, sadly, doesn't work with Compiz on Oneiric.

---

### Post by dfacto on 2011-09-09
Wow so much to reply to.

@berto- Thanks for posting your gptsync; unfortunately you have the same weird gptsync I did.  Your flicker problems are almost certainly a result of not using xorg-edgers.  Sandybridge is new hardware and you are using old drivers (drm, intel, mesa; not i915 which is in kernel).  Perhaps you downloaded the script for the second run after I added the cp line?

@jonny No worries about script.  I just want to know why it doesn't work for others but works for me.  ...Actually now that I think about it, I may have run it before upgrading from 3.0.0-9-generic to 3.0.0-10-generic.  Still though, the source-tree shouldn't be different from the build tree and, if it is, represents a Canonical goof.  Like I said though, I put the cp in because I can't see that it causes any more harm than the hack itself.  It sounds like you are using the multitouch driver and not mtrack?  Have you tried both?  Which one do you prefer and why?

@Objectivity (Or anyone on *Natty 11.04*) Can you please run gptsync? Sounds like you're the only one on natty.  This will help me figure out what libparted is doing to our mbr.  It is a read-only procedure (hit n if it asks you to change something):
```

sudo aptitude install gptsync
sudo gptsync /dev/sda

```
and paste the results back here.  Also, your backlit keyboard and multitouch capability of trackpad do not work because I don't know the product codes of the 11" MBA (I own the 13").  See the last paragraph of this post.  Yes, compiz works.

@undoIT Yes, I agree.  From my first impressions with Oneiric this is the biggest UI leap yet.  Things are really starting to look polished and more "mainstream."  Frankly, I don't understand all the unity complaints...but admittedly I almost exclusively use the terminal (as I have for the last six years--I find mousing around slow and tedious).  Still, I'm happy to go on record and say I think unity looks pretty and I think that its a big step in the goal of mainstream adoption.  Regarding stable: I submitted product codes for the 13" to kernel mainline.  I don't know when they will be included.  I wish I had the 11" codes but I don't so those are not even pending.  I have not submitted a patch for btusb as I have not had time and bt is a low priority for me.  Obviously the i915 "patch" is not remotely acceptable for submission.

@berto,jonny Regarding the trackpad: are you using my xorg.conf?  It should help some, but I agree there is more work to be done.  The driver mtrack is ridiculously customizable.  I suggest you look through the [mtrack thread]("http://ubuntuforums.org/showthread.php?t=1730361") and try out some of the options.  I believe it is possible to make mtrack work as well as MacOS.  (Just in case you didn't know, you can hit ctrl-alt-F1 to drop to a tty and use [FONT="Courier New"]sudo service lightdm restart[/FONT] to quickly try out out new mouse settings.)  I tried to get this process started by putting in all options in xorg.conf with description.  One need only uncomment and alter the parameter.

To All:

You will have zeitgeist crashes, among others, while on Oneiric beta.  None of these crashes should "get in your way."  At least, for me it certainly hasn't been a problem (and you can disable subsequent crash notifications).  Still, if you are a novice, I recommend Natty for now.  Please let me know if  the [fix-i915.sh]("http://www.almostsure.com/mba42/fix-i915.sh") script works in Natty.

Finally, at some point, I will be modifying [post-install.sh]("http://www.almostsure.com/mba42/post-install.sh") and removing all of the dkms module lines (I was hoping that my kernel mainline patches would have made 3.0.0).  These are deprecated modules and we shouldn't be using them (I chose them because they each had their own git tree and of course they are dkms which makes deployment easier).  I will make patches for the ubuntu patched kernel source, just as I did for the [i915 fix]("http://www.almostsure.com/mba42/fix-i915.sh").  This should get us back on current drivers while also supporting our machines. To any 11" users out there: get me your [FONT="Courier New"]lsusb[/FONT] output if you want your trackpad, fn keys, keyboard backlight to work.

Has anyone else noticed that gamma/contrast seem to be nicer on Ubuntu?  I tried to fix MacOS's but was never happy with the result.  Maybe this is just my imagination.  Certainly fonts are a disaster on MacOS but thats another story.

---

### Post by berto- on 2011-09-09
> **dfacto said:**
> Perhaps you downloaded the script for the second run after I added the cp line?


Perhaps; I ran it twice last night about an hour or two before posting.

> **dfacto said:**
> 
From my first impressions with Oneiric this is the biggest UI leap yet.  Things are really starting to look polished and more "mainstream."


Agreed, the UI looks great.

> **dfacto said:**
> 
Frankly, I don't understand all the unity complaints...but admittedly I almost exclusively use the terminal (as I have for the last six years--I find mousing around slow and tedious).  


I'm mostly in terminals as well, even on OS X.  But a steamlined, usable UI is indispensable.

> **dfacto said:**
> 
Still, I'm happy to go on record and say I think unity looks pretty and I think that its a big step in the goal of mainstream adoption.


I've been using OS X as my primary OS for about 8 years.  In my experience the biggest advantage it has over other OSs is working seamlessly.  When you install OS X from scratch on a Mac it has sensible defaults that work.  You don't have to spend days tweaking xorg.conf files to get the screen right, or the mouse working, or [...].

If and when Ubuntu can match that sort of experience, it has a shot at becoming mainstream.  "Mainstream" means the masses, not power users.  Works out of the box is masses, run post-install.sh is power user, tweaking xorg.conf is high-end power user, recompiling the kernel is linux hacker.

I consider myself technically proficient and don't want to spend an entire day "fixing" the computer, I want to get to the reason I'm on the computer as quickly as possible.

Users that just want a computer to work will look elsewhere if there is any friction.  In fact, the masses are going towards iPads, which are more appliance than computer.

Granted the MBA is brand new hardware so there will be bumps, that's understandable.  Ubuntu also has to work on "everything", which makes seamless integration difficult.

> **dfacto said:**
> 
Regarding stable: I submitted product codes for the 13" to kernel mainline.  I don't know when they will be included.  I wish I had the 11" codes but I don't so those are not even pending.


What are the steps to get the product codes?

> **dfacto said:**
> 
I have not submitted a patch for btusb as I have not had time and bt is a low priority for me.  Obviously the i915 "patch" is not remotely acceptable for submission.


What are the issues with the i915 patch?

> **dfacto said:**
> 
@berto,jonny Regarding the trackpad: are you using my xorg.conf?  It should help some, but I agree there is more work to be done.  The driver mtrack is ridiculously customizable.  I suggest you look through the [mtrack thread]("http://ubuntuforums.org/showthread.php?t=1730361") and try out some of the options.  I believe it is possible to make mtrack work as well as MacOS.  


I will check this out when I have a chance, thanks!

> **dfacto said:**
> 
You will have zeitgeist crashes, among others, while on Oneiric beta.  None of these crashes should "get in your way."  At least, for me it certainly hasn't been a problem (and you can disable subsequent crash notifications).


Do you know why this crashes on non-release versions?  Maybe it's easy to detect a non-release version and simply disable the daemon if it's simply going to crash loudly anyway.

> **dfacto said:**
> 
Please let me know if the [fix-i915.sh]("http://www.almostsure.com/mba42/fix-i915.sh") script works in Natty.


The script warns if it's not Natty; should that be changed to Oneiric?

> **dfacto said:**
> 
Has anyone else noticed that gamma/contrast seem to be nicer on Ubuntu?  I tried to fix MacOS's but was never happy with the result.  Maybe this is just my imagination.


I think the bare-metal feeling I have is my imagination, so you're not alone imagining things.  ;)

> **dfacto said:**
> 
Certainly fonts are a disaster on MacOS but thats another story.

What do you mean?  Installation and management, format support, etc?

---

### Post by dfacto on 2011-09-09
Just paste back the output of lsusb to get me the keyboard and trackpad codes.


No idea why its crashing.


The i915 patch forces a particular mode (1440 for 13" and 1366 for 11") whether or not your monitor supports it!

---

### Post by daveMustane on 2011-09-09
> **berto- said:**
> 
- the trackpad is absolutely terrible!

The trackpad does not work well at all with more than one finger on it.  Some simple examples.  Try to drag a window after clicking on the title bar; not possible.  Another is right clicking; very finicky.  Two-finger scrolling?  Nope.  I've also managed to get it to sporadically do things like highlight half this post and delete; I must have accidentally brushed my thumb on it.


I'm running Oreinic and was able to fix the trackpad issue you describe by using the following in xorg.conf:

Section "InputClass"
    MatchIsTouchpad "on"
    Identifier      "Touchpads"
    Driver          "mtrack"
    MatchDevicePath "/dev/input/event*"
EndSection # "Multitouch Touchpad"

You need to replace the existing section with all the options listed. It will let you use your index finger to point and you thumb to click without you having to release the index finger first. It will do what you want instead of opening the alternative action menu. Also selecting an area or text, say, in a browser using index finger + thumb is now (at least) doable. Also, when you want to invoke the 2nd button action, in addition to doing a two-finger tap, you will also be able to do this: keep an already touching index finger on the pad, put another finger on the touchpad and use your thumb to click. I'm used to do it this way. But it wasn't possible before.

I'm NOT totally happy with the feel of the touchpad yet. It's OK now, but not yet fantastic.

I don't have strange flicker and I don't have random crashes (anymore). Probably because I removed all off zeitgeist using Synaptic.

Fan

I changed the following 6 values in /etc/macfanctl.conf.

temp_avg_floor: 65 # 45
temp_avg_ceiling: 74 # 55

temp_TC0P_floor: 65 # 50
temp_TC0P_ceiling: 74 # 58

temp_TG0P_floor: 65 # 50
temp_TG0P_ceiling: 74 # 58

This is supposed to keep the fan from running all the time. Be careful with these settings. You might be causing harm. I'm not sure about this. However, my fan(s?) are mostly quiet now.
When I do some serious stuff, like using the compiler, my cpu temperatures go above 92ºC for 3-4 seconds, before the fan (almost jumping to ~6000rmp) brings the temperatures back down to ~80ºC (during compile = fan is quite loud) and then afterwards back to ~70ºC (fan off). Btw, I am using the cpu scaling applet (in ondemand or conservative) since I installed "Gnome (semi) classic" for Gnome3. Not sure how to configure cpu scaling in Gnome3 standard or in Unity.

Booting

Last not least, I measured the boot time (by hand). 

mac jingel         0 
partition select  10
grub boot start   22
graphical login   49

I can log in after 49 secs. Not super fast, but I can live with that. Is this what you see as well?

So in short: I have started using this machine for serious work. I sure keep a dd-backup of my root partition in a save place. Yeah, this is what I use OSX for : - )

PS: One question. Thunderbird doesn't start for me under Oreinic. Anybody else seing this?

---

### Post by dfacto on 2011-09-09
@daveMustane Does this mean you didn't try my [xorg.conf]("http://www.almostsure.com/mba42/xorg.conf")?

---

### Post by daveMustane on 2011-09-09
> **dfacto said:**
> @daveMustane Does this mean you didn't try my [xorg.conf]("http://www.almostsure.com/mba42/xorg.conf")?

I am using your xorg.conf. I only replaced the long <b>Section "InputClass" with Driver "mtrack"...</b> with those 6 lines. I was not able to find one particular setting in the long list to cause the issue. I think it is probably easier to apply some (likely needed) additional settings from a (mostly) working base, than trying to finetune a broken configuration. To have all possible settings in the file, but in remarks is really a great idea. If there wasn't some sort of side effect. Maybe a parsing error. Maybe some outremarked special character causing issues.

Please apply the change and lmk if your two finger touchpad behaviour doesn't improve a lot.

---

### Post by dfacto on 2011-09-09
> **daveMustane said:**
> I am using your xorg.conf. I only replaced the long <b>Section "InputClass" with Driver "mtrack"...</b> with those 6 lines. I was not able to find one particular setting in the long list to cause the issue. I think it is probably easier to apply some (likely needed) additional settings from a (mostly) working base, than trying to finetune a broken configuration. To have all possible settings in the file, but in remarks is really a great idea. If there wasn't some sort of side effect. Maybe a parsing error. Maybe some outremarked special character causing issues.

Please apply the change and lmk if your two finger touchpad behaviour doesn't improve a lot.

Hrmm seems fishy to me--commented out is equivalent (I'm sure the parse library is >20yo by now...).  In theory that is a working base as its what I am using.  Oh well, hopefully someone can figure it out.  BTW, the settings that are in there are what I cherry-picked (then tested) from the mtrack thread.

---

### Post by dfacto on 2011-09-09
So if you're on 3.0.0-10, here is how you can remove all the -dkms packages (except btusb-dkms).  This isn't necessary and I don't want to add this to post-install.sh as I don't like it entirely. More importantly, you should only follow these steps if you're running Oneiric.

Anyway, if you want to put your install a bit closer back to "what it should be" AND you are on 3.0.0-10, then you can run:
```

sudo dpkg -r applesmc-dkms bcm5974-dkms

```
which removes two of the packages that my post-install.sh installed.

Removing [FONT="Courier New"]hid-apple-dkms[/FONT] (and [FONT="Courier New"]hid-dkms[/FONT]) is more interesting.

For some reason my hid-apple patch made it to the 3.0.0 source tree but its not in the binary.  Honestly, I didn't even know this was possible and seems mildly disturbing.  In any event, the following steps will get rid of two more of our custom dkms:
```

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
cd linux-$(uname -r|cut -d- -f1)/drivers/hid
make -C /lib/modules/$(uname -r)/build M=$(pwd) hid-apple.ko
sudo make -C /lib/modules/$(uname -r)/build M=$(pwd) modules_install
sudo dpkg -r hid-apple-dkms hid-dkms

```

Its probably better to reboot for this one to take effect.

So to summarize: Following these steps keeps everything working as before, but puts us back on "stock" Ubuntu kernels, with the exception of i915 and btusb-dkms (which we should be using the non-dkms version which is newer). Obviously the re-make of above is "stock" but there was no editing to the file...

**Update**: Perhaps these disturbing out-of-sync issues (also the cp line in fix-i915.sh) are related to this message which I did not notice when I pulled the source before (in which I used apt-get):
```

Picking 'linux' as source package instead of 'linux-image-3.0.0-10-generic'
NOTICE: 'linux' packaging is maintained in the 'Git' version control system at:
[http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-oneiric.git](http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-oneiric.git)

```

**Update 2**: All new changes are in [new-post-install.sh]("http://almostsure.com/mba42/new-post-install.sh").  This is for Oneiric only! If you are using Oneiric, then new-post-install.sh is much better to use than the original.  Also, you can re-run new-post-install.sh everytime there is a kernel upgrade (in fact you MUST do this until i915 and btusb are fixed).

**Update 3**: The cp hack in fix-i915 and new-post-install.sh is now resolved.  I was using the wrong path (obviously).

---

### Post by mike909 on 2011-09-10
To update those that might stumble on this thread w/ out reading it's entirety...Using MBA 4,2 13" stock 11.04 (natty) and running post-install.sh, according to [this dfacto post]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75"). Everything working great for me, except microphone. 
Don't forget to unmute 'surround' in alsamixer to get audio.

---

### Post by dfacto on 2011-09-10
Microphone should be working too.  Are you sure its unmuted?

---

### Post by jonny on 2011-09-10
Trackpad is working much better for me after a reboot, but I can't get a 4-finger tap or swipe to show Dash or the Unity launcher in the way it's supposed to.  Three finger tap and swipe to move windows is simply awesome... I love it!

One very minor problem is that the function keys don't map perfectly.  F10 reduces the volume instead of muting; F11 increases the volume instead of reducing it; and F12 attempts to eject a non-existent CD instead of increasing the volume.

Getting happier all the time!

---

### Post by jonny on 2011-09-10
And, after a kernel update today, suspend seems to work perfectly - both from the menu and by shutting the lit.  This is good... very good!

---

### Post by dfacto on 2011-09-10
@jonny My [.Xmodmap]("http://almostsure.com/mba42/dotXmodmap") fixes that.

Also to everyone else.  If you are just installing Oneiric, please use [new-post-install.sh]("http://almostsure.com/mba42/new-post-install.sh").

It sets-up things the "right way" as opposed to the original post-install.sh which did things in a way that is not as nice (but also has its own merits).  Basically the old post-install is more "stable" but the new one is "better."

For Oneiric users: you can re-run new-post-install.sh every time there is a kernel upgrade (in fact you MUST do this until i915 and btusb are fixed).  Eventually it will ask you if you want to continue setting the system up, at which point you can say 'no' to not proceed.

Hopefully this all makes sense to someone.  Trust me, everything you need is in these scripts (I'm not a documentation person!).

---

### Post by daveMustane on 2011-09-10
> **dfacto said:**
> Hrmm seems fishy to me--commented out is equivalent (I'm sure the parse library is >20yo by now...).  In theory that is a working base as its what I am using.  Oh well, hopefully someone can figure it out.  BTW, the settings that are in there are what I cherry-picked (then tested) from the mtrack thread.

 The only setting that is causing me touchpad issues is 'IgnorePalm'.

'IgnorePalm' defaults to 'false'. If set to 'true', it becomes impossible to thumb click anything, without lifting the index finger first. Doing so often dispositions the mouse pointer. And you end up clicking the wrong thing. Painful! So I guess this is a bug in code. All other settings in xorg.conf are OK. And in theory, this one is as well.

---

### Post by dfacto on 2011-09-10
> **daveMustane said:**
> The only setting that is causing me touchpad issues is 'IgnorePalm'.

'IgnorePalm' defaults to 'false'. If set to 'true', it becomes impossible to thumb click anything, without lifting the index finger first. Painful! So I guess this is a bug in code. All other settings in xorg.conf are OK. And in theory, this one is as well.

Thanks for tracking that down. I had enabled it under the hope that it would prevent spurious mouse movements while typing.  There is another program listed on the mtrack thread that should accomplish this, but I have not tried it.

---

### Post by daveMustane on 2011-09-10
Welcome. The spurious mouse movements do happen indeed. Once in a while I find my cursor kicked out of sight and hitting some keys then makes the letters appear in the wrong place. But 'IgnorePalm' 'true' does not fix that ATM. It's only causing the thumb click issue, currently.

---

### Post by jonny on 2011-09-10
> **daveMustane said:**
> Welcome. The spurious mouse movements do happen indeed. Once in a while I find my cursor kicked out of sight and hitting some keys then makes the letters appear in the wrong place. But 'IgnorePalm' 'true' does not fix that ATM. It's only causing the thumb click issue, currently.
Why are you guys using a customised xorg.conf?  What benefits does it bring?  My screen and touchpad seem to work admirably with the default settings - unless the post-install.sh script has created a custom file in some place that I can't find.

---

### Post by dfacto on 2011-09-10
My feeling was that the multitouch driver wasn't as good as the mtrack driver. *shrugs*  You need to declare mtrack in xorg.conf if you want to use it (at a minimum).

The mtrack defaults were, for the most part, acceptable.  The few that I changed were under the recommendations of those posting in the mtrack thread.  My conclusion was that the extent of customizations facilitated by mtrack driver more than justified any added trouble of configuring it.  It also seems to be more actively developed, so this makes the long-term picture more favorable.

Update: I should also mention that just about everything else in my xorg.conf is not needed.  These were left-over from when I was trying to get the video to work.  However, they shouldn't hurt anything.

---

### Post by mike909 on 2011-09-11
> **dfacto said:**
> Microphone should be working too.  Are you sure its unmuted?
Correct, it is working. System defaults to 'analog line-in' instead of 'internal mic'. Just needed to change that.
So as of now, fresh install with post-install.sh things are pretty much perfect; though I too am experimenting with touchpad settings to reduce accidental mouse-movements while typing.

Thanks.

---

### Post by dfacto on 2011-09-11
So the xcalib hack that the Mactel people cooked up really isn't very good and doesn't work for Oneiric.  Here is a better way(*):

```

sudo aptitude install gnome-color-manager
sudo cp /media/Mac\ OS/Library/ColorSync/Profiles/Displays/Color\ LCD-00000610-0000-9CDF-0000-0000042737C0.icc \
    /usr/share/color/icc/Apple_MacBookAir4.icc
gcm-import /usr/share/color/icc/Apple_MacBookAir4.icc

```

Then, go to "System Settings" then "Color" and click "Apple Computers Inc - Color LCD".  Then click "Add profile" and choose "Display".  This should be the Apple shipped color calibration.  Upon activation you will see a significant reduction in the blue tint present in the default setting.

I have made this change to [post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh") (note that this script is still available as [new-post-install.sh]("http://almostsure.com/mba42/new-post-install.sh") which is just a symlink).

(*) - If your Mac OS parititon is not mounted, go to the Unity dock, select the home folder and click "Mac OS" under devices. Or if you prefer the terminal:
```

sudo mkdir /media/Mac\ OS
sudo mount -o ro /dev/sda2 /media/Mac\ OS

```

---

### Post by dfacto on 2011-09-11
@mike909 Thanks for looking into this.  Its gonna take a fair amount of tweaking so I'm glad someone is giving it a go.

I'd like to have tap-to-drag; is there an option for this? I can't recall.

Another thing I would like to have, if you happen to stumble across it, is the nice "momentum scrolling" available in MacOS and just about every smart phone.  This is where you can swipe-to-scroll and the page keeps scrolling even after you have removed your fingers.  Of course pinch-to-zoom and other gestures would be nice but I have no idea how to enable this or if its even possible.

---

### Post by dfacto on 2011-09-11
I changed the poor naming of the post-install scripts.  Please link to:
[post-install-natty.sh]("http://almostsure.com/mba42/post-install-natty.sh")
and
[post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh")

The scripts are still available under their former names (symlink'ed) but this should make it more clear which one is appropriate for which release. The scripts still check if you have the right version when run.

Note: I will probably not be updating [post-install-natty.sh]("http://almostsure.com/mba42/post-install-natty.sh") unless there is some big problem.  I am running Oneiric so I would have to make tweaks to this script "blindly" which I am not comfortable doing.

Please see this [earlier post]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75") for more details.

---

### Post by dfacto on 2011-09-11
I'm beginning to [agree with daveMustane]("http://ubuntuforums.org/showpost.php?p=11234940&postcount=239") that the touchpad settings are best when at their defaults.

Here are the contents of my /etc/X11/xorg.conf
```

Section "InputClass"
    Identifier      "Multitouch Touchpad"
    Driver          "mtrack"
    MatchIsTouchpad "yes"
    MatchDevicePath "/dev/input/event*"
    Option          "CorePointer"    "true"
    Option          "Sensitivity"    "0.95"  
EndSection # "Multitouch Touchpad"

```

The mtrack developer offers "dispad" to disable the trackpad while typing (actually it disables clicking while typing).  It seems to work well.  To get it up and running:
```

wget -q http://www.dev.fatedmariner.org/packages/dispad/ubuntu/dispad_0.1_natty_amd64.deb
sudo dpkg -i dispad_0.1_natty_amd64.deb

```
Then, to make dispad run upon log-in, go to the Unity dock, type "Startup Applications."
Choose "Add" and enter the following information:
```

Name:    dispad
Command: /usr/bin/dispad
Comment: Disable trackpad while typing.

```
and click "Save."

---

### Post by koadman on 2011-09-12
Just checking in to say that Oneiric seems to be running well on my air too.  Not surprising, the 1440x900 hack works with the Samsung display in my laptop. The post-install script made configuration a breeze. Thanks to all of you for all the support!

There's still a few lingering issues I'd like to fix/change and wonder if anyone else has suggestions:

**power button**. it shuts down the machine, even though the power settings are configured to ask before doing anything when the power button is pressed.  this can be really problematic if i fat-finger the delete key.

**tap&drag** someone mentioned this earlier. i goog'd for x11 settings but didn't find anything that worked.

**power usage**. Is it me or is Oneiric running like a hog?  powertop says my laptop's battery is discharging at > 19W/hour when the system is idling.  Previously on Natty it was at 7-10W/hour depending on settings. What gives? A solution to this issue might also help reduce the fan noise.

---

### Post by undoIT on 2011-09-12
Has anyone tried touchegg (a nice config tool for touchpad gestures) on the 4,1 or 4,2? It works well for me on my other Macs (don't have access to the Air at the moment).

[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)

[https://launchpad.net/~utouch-team/+archive/daily](https://launchpad.net/~utouch-team/+archive/daily)

---

### Post by jonny on 2011-09-12
> **koadman said:**
> **power usage**. Is it me or is Oneiric running like a hog?  powertop says my laptop's battery is discharging at > 19W/hour when the system is idling.  Previously on Natty it was at 7-10W/hour depending on settings. What gives? A solution to this issue might also help reduce the fan noise.No, it's not your imagination.  Battery life under Linux is around half that on OS X, and powertop gives similar results for me.  I've made some basic attempts towards tuning power usage using powertop, but only managed to shave a couple of watts at the cost of reducing network throughput by a factor of 10: not a great tradeoff.

There have been some pretty nasty power regressions in Linux recently, and they're probably at the heart of the problem.  If your interested, Phoronix has had several articles exploring the matter in depth.  There are a few suggested kernel patches drifting around the internet, but I'll just stay close to a power outlet for now - three hours battery life is generally sufficient for me.

---

### Post by jonny on 2011-09-12
I haven't yet tried it myself (I'm not at home), but you can read about a possible partial fix for the excessive power consumption [here]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html").  There are at least two other power regression issues that aren't addressed by this fix, but this is alleged to be the big one, accounting for much more than half of the excessive power draw compared with earlier kernels.

First person to try it, please post before and after results with notes of any other issues - eg system hanging.

---

### Post by dfacto on 2011-09-12
> **koadman said:**
> Just checking in to say that Oneiric seems to be running well on my air too.  Not surprising, the 1440x900 hack works with the Samsung display in my laptop. The post-install script made configuration a breeze. Thanks to all of you for all the support!

There's still a few lingering issues I'd like to fix/change and wonder if anyone else has suggestions:

**power button**. it shuts down the machine, even though the power settings are configured to ask before doing anything when the power button is pressed.  this can be really problematic if i fat-finger the delete key.

**tap&drag** someone mentioned this earlier. i goog'd for x11 settings but didn't find anything that worked.

**power usage**. Is it me or is Oneiric running like a hog?  powertop says my laptop's battery is discharging at > 19W/hour when the system is idling.  Previously on Natty it was at 7-10W/hour depending on settings. What gives? A solution to this issue might also help reduce the fan noise.

My power button brings a pop-up to choose one of, restart, shutdown, hibernate, suspend.  Perhaps my [.Xmodmap]("http://almostsure.com/mba42/dotXmodmap") fixes this (I don't remeber but I'm fairly certain it does NOT).

The trackpad settings seem to be better with just the defaults (see [earlier post]("http://ubuntuforums.org/showpost.php?p=11242539&postcount=258")).  Still I don't think tap&drag works at least not for title bars.  I can tap-to-select--which is close--but this is based on a double-click not a single-click.

Power is known issue--there are several phoronix articles on the topic [[1]("http://www.phoronix.com/scan.php?page=news_item&px=OTg5NA")] [[2]("http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg")]. Koadman, your fans shouldn't be running all the time.  Make sure all of the macfanctld related steps of the script were successfully applied.  The default macfanctld settings work great for me. 

Powertop gives me 15.2W as I am writing this post and 16.8W when I just ran update-grub (basically the same as you report).  I'll try the "pcie_aspm=force" boot flag right now.

After reboot: I do not notice any difference when using the "pcie_aspm=force" flag nor do I see system hangs. Perhaps this flag is ineffective because I am using legacy mode rather than pure EFI.

Oh, and I forgot to mention some time back.  It takes me about ~20 seconds to to a full reboot (ballpark).  The refit Tux logo takes 8-9 seconds (this measurement was precise) and the rest is the standard linux stuff (grub+startup sequence).  If you have anything more than 10 sec at the Tux logo, then something is wrong.

**Update**: Someone [try this]("http://ubuntuforums.org/showpost.php?p=11207887&postcount=99") and see what happens (here are [some more tweaks]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")).  In general [that thread]("http://ubuntuforums.org/showthread.php?t=1822629&goto=newpost") seems to be the best source of information, particularly since steevven1 has seemingly tried every boot arg under the sun. He has also filed bug [834037]("https://bugs.launchpad.net/ubuntu/+bug/834037") which I encourage you to check-out and click the "Does this bug affect you" link.

---

### Post by happicow on 2011-09-12
> **dfacto said:**
> Wow so much to reply to. To any 11" users out there: get me your [FONT=Courier New]lsusb[/FONT] output if you want your trackpad, fn keys, keyboard backlight to work.



Hi,

I don't know if you are still looking for the lsusb output from an 11 inch air, but here it is.  I tried to update your script myself but I am not sure where to look.  Thanks for putting it out there though!

- Chris

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp.  
Bus 001 Device 003: ID 05ac:850a Apple, Inc.  
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp.  
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) 
Bus 001 Device 005: ID 05ac:0249 Apple, Inc.  
Bus 001 Device 006: ID 05ac:820a Apple, Inc.  
Bus 001 Device 007: ID 05ac:820b Apple, Inc.  
Bus 001 Device 008: ID 05ac:821f Apple, Inc.

---

### Post by koadman on 2011-09-13
Thanks for the tips, power usage comes down to 9-10 watts by adding i915.i915_enable_rc6=1 to the kernel command-line.  Haven't tried the sparse irq kernel config.  The phoronix article suggests other tweaks but their effect is small compared to i915.i915_enable_rc6=1.  I haven't observed any graphics rendering problems so far, but I haven't tried much 3D either.

---

### Post by dfacto on 2011-09-13
@koadman Looks like post-install-oneiric.sh was not installing macfanctld since this is not in the Mactel ppa.  The problem is fixed now.

---

### Post by dfacto on 2011-09-13
To whoever posted the script on git hub: do you mind removing it? :) I don't think its smart to have old copies floating around (unless you keep updating it). For the time being I prefer to keep editing it on my own machine because this is simpler for me to maintain.  Once we all agree its stable, then we can share its maintenance (or ideally someone else can carry the torch). In general, it seems to me the Mactel community is quite fractured (for God's sake look at the Ubuntu Mactel commuity wiki!) so let's at least try to keep the MBA4 stuff in one place.  :)

Oh, on the issue of "stability": I just reinstalled Oneiric last night and re-ran the script.  Aside from discovering the macfanctld issue it seems to work quite nicely.  Next it would be nice to /var/log all the build messages so it is more clear what changes are being made to the system. (I put in echo's all through-out but at run-time you can hardly tell they're there.)

---

### Post by kiffykroker on 2011-09-13
Appreciate all the effort you guys have put in to this. I have an 11" Air running 11.04 / 3.1.0-0301rc4-generic, the resolution is correct thanks to dfactos fix-i915.sh(*) but I've encountered the following issues so far:

- the fans are going all the time
- trackpad only recognize movement and primary clicks
- fn key doesn't work

Browsing through the thread it seems that some of you have experienced at least some of these issues, anyone solved them? Perhaps dfactos post install script fixed the last two for the 13"?

Also, I noticed that dfacto asked for lsusb from an 11", here's mine

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 05ac:821f Apple, Inc. 
Bus 001 Device 005: ID 05ac:024a Apple, Inc. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:850a Apple, Inc. 
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```(*) = I had to change $(uname -r) on line 77 in fix-i915.sh to a hard coded folder

```
# patch
cd linux-3.0.0/drivers/gpu/drm/i915/
```since the kernel source the script grabbed was linux-3.0.0 (or atleast the folder name) and not $uname -r

---

### Post by dfacto on 2011-09-13
> **kiffykroker said:**
> Appreciate all the effort you guys have put in to this. I have an 11" Air running 11.04 / 3.1.0-0301rc4-generic (*), the resolution is correct thanks to dfactos script but I've encountered the following issues so far:
- the fans are going all the time

Mactel doesn't have macfanctld in the ppa for Oneiric.  See what the revised script does.

> 
- trackpad only recognize movement and primary clicks
- fn key doesn't work


Both of these are because the script is for 13" and I didn't have the product codes until recently.  I'll have to make a patch when I get time but anyone should be able to figure it what I did from the post-install-natty.sh script.  (The oneiric version didn't do it because I submitted those patches to mainline so they are already in 3.0.0.)

There is extremely high probability that I won't have time to do this--I graduate in two weeks!

> 

Browsing through the thread it seems that some of you have experienced at least some of these issues, anyone solved them? Perhaps dfactos script fixed the last two for the 13"?

Also, I noticed that dfacto asked for lsusb from an 11", here's mine

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 05ac:821f Apple, Inc. 
Bus 001 Device 005: ID 05ac:024a Apple, Inc. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:850a Apple, Inc. 
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Thanks; this is necessary information to make the patch. Also need the bluetooth product id.

> (*) = I had to change $(uname -r) on line 77 in fix-i915.sh to a hard coded folder

```
# patch
cd linux-3.0.0/drivers/gpu/drm/i915/
```since the kernel source the script grabbed was linux-3.0.0 (or atleast the folder name) and not $uname -r

You must have a really old fix-i915.sh?  My version has a `cut` to lop off the excess from uname -r.  Make sure you are actually downloading a fresh copy and not getting your browsers cache (perhaps use wget).

---

### Post by jonny on 2011-09-13
> **koadman said:**
> Thanks for the tips, power usage comes down to 9-10 watts by adding i915.i915_enable_rc6=1 to the kernel command-line.  Haven't tried the sparse irq kernel config.  The phoronix article suggests other tweaks but their effect is small compared to i915.i915_enable_rc6=1.  I haven't observed any graphics rendering problems so far, but I haven't tried much 3D either.I can confirm that I see very similar results on my 13" Air, too.  Huge power saving and no obvious adverse effects. :D

---

### Post by dfacto on 2011-09-14
Patched hid-apple with 11" product code (I think) and also fixed key mappings so xmodmap hack is not needed.  Changes in post-install-oneiric.sh as usual.

Now the keyboard brightness keys cause a pop-up but they still don't change the brightness and I don't know why.

---

### Post by User4519 on 2011-09-14
> **dfacto said:**
> 
There is extremely high probability that I won't have time to do this--I graduate in two weeks!


Congratulations, man! That's awesome! :cool:

---

### Post by dfacto on 2011-09-14
Thanks DanielBuus!

In the interest of screwing myself over by way of procrastination here is a better [keyboard-backlight]("http://almostsure.com/mba42/keyboard-backlight") script.  I tried to assign this as the default action using the keyboard settings but it isn't following the keyboard shortcut I specified (the key definitely works as the right osd notify pops-up).

I think it would be nice to use [pommed]("http://blog.technologeek.org/category/hacks/pommed") but I can't patch it for the MBA4 since there is some unresolved [build dependency issue]("https://bugs.launchpad.net/ubuntu/+source/pommed/+bug/832915").

---

### Post by dfacto on 2011-09-14
FYI: I have been having some problems with WPA2 in Linux which seem to have been resolved by the latest Apple firmware update.  As I don't know much about EFI, I'm not sure if its reasonable to assume some connection between these two issues but...*shrugs*

---

### Post by preacher37 on 2011-09-15
Thanks to dfactos great script and other replies in this thread I now have a mostly usable MBA.

One problem I'm having on this new install of Oneiric though is unity 3d segfaulting at startup. Anyone else seeing this? I'm stuck at unity-2d right now.

Also cannpt get swipe with the trackpad to work, but if I understand correctly this support only exists in unity 3d.

---

### Post by dfacto on 2011-09-15
I had this problem a week  ago, assuming it  happened after you  upgraded  packages. Sadly the only  "fix" I  could   come up with was to reinstall.  Chalk this one up to running an unstable release. :(  Anyway  everything does  work for me now  and should  for you too.

**Update**: Actually as of today's update I now lost suspend and the brightness dim doesn't work.  Can someone confirm this?  (So that way I know it isn't the tweaks I just made to the hid-apple driver...although this really shouldn't be possible.)

Also, I'm seeing more weirdness on the wl and lib80211 drivers in dmesg and lots of drop-outs (for WPA2-enterprise).  I don't have any problems with WPA2-personal (at home). I guess the firmware update really didn't have anything to do with my random, temporary improvement.

---

### Post by dfacto on 2011-09-15
I know I asked for this already (and got it) but can someone with the 11" MBA re-send their (verbose) usb list?
```

sudo lsusb -v 2>&1|gzip -c >MBA41-lsusb.txt.gz

```

I'll add the bluetooth and bcm5974 (trackpad) support.  You *should* have fn keys working as is.  I have all the patches in place and simply need to plug-in the right values.

The sooner I get this, the sooner you get an MBA is slick as the 13"! :)

---

### Post by kiffykroker on 2011-09-15
> **dfacto said:**
> I know I asked for this already (and got it) but can someone with the 11" MBA re-send their (verbose) usb list?
```

sudo lsusb -v 2>&1|gzip -c >MBA41-lsusb.txt.gz

```I'll add the bluetooth and bcm5974 (trackpad) support.  You *should* have fn keys working as is.  I have all the patches in place and simply need to plug-in the right values.

The sooner I get this, the sooner you get an MBA is slick as the 13"! :)

Attached! Big thanks for looking in to this for us 11"-ers!

---

### Post by dfacto on 2011-09-15
kiffykroker: I need to know which keyboard variant you have.

USB_DEVICE_ID_APPLE_WELLSPRING6A_ANSI
USB_DEVICE_ID_APPLE_WELLSPRING6A_ISO
USB_DEVICE_ID_APPLE_WELLSPRING6A_JIS

If you are American then you probably have ANSI.  JIS is Japan and ISO is everything else (I guess?)  This is not something that lsusb would tell you. If you don't know, then tell me what country you live in.

Ah: read [this]("http://www.stefanoubbiali.com/macbook-13-inch-late-2006-mid-2007/replacing-mitsumi-keycaps.html") to identify the keyboard.

 ISO (Europe), JIS (Japan), and ANSI. The ANSI keyboard is a standard 101-key layout widely used in the US, North America, and many other parts of the world.
[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh2234.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh2234.html)
(hexadecimally speaking, I hope you're in Europe, otherwise things are annoying)

---

### Post by kiffykroker on 2011-09-15
I do have the ISO (Europe) keyboard format, sorry I forgot to mention that.

---

### Post by dfacto on 2011-09-15
2011 MBA 11": Godspeed.
[post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh")

---

### Post by kiffykroker on 2011-09-15
> **dfacto said:**
> 2011 MBA 11": Godspeed.
[post-install-oneiric.sh]("http://almostsure.com/mba42/post-install-oneiric.sh")

Awesome! Gonna try it out tonight, big thanks!

---

### Post by dfacto on 2011-09-15
Yeah--I hope it works. I'm a little concerned that I actually didn't have to change anything (my id guesses were all correct).  This is bad because presumably this script was already run by 11" users and it didn't work...

Anyway, there is no real harm in trying it.  And, for what its worth, I'm am as confident as I can be that everything is correct.

---

### Post by chaffin on 2011-09-16
Hi everyone,

I'm having trouble getting the post-install-oneiric script to yield satisfactory results on my MBA. I did a clean install of first natty, and later oneiric and was able to load the X server as long as i inserted nomodeset into the bootloader. After running the post-install script, the bootloader appears to be running the new driver (at least, the command now includes "i915.i915_enable_rc6=1"), but the X server doesn't start. I've attached my Xlog, which indicates that the X server can't find any screens on startup.

I don't really know any of the high-level magic some of you are using (for example, recompiling the kernel); but I'm pretty stubborn and willing to follow instructions.

My thoughts, as of right now: could this be caused by differences in the processor? I got the i7 model of the 4,2 , which might differ with some who have reported success. Another option is that the display is different and that's the source of the problem: running 

sudo get-edid 2> /dev/null | strings -5

returns

LTH133BT01A03
Color LCD

which means I've got the Samsung display and not the LG/Phillips.

I will note that many of the minor tweaks did propagate correctly: two-finger scrolling is enabled, for example.

A final note: the post-install-oneiric.sh file appears to have a bug: it refers to a 'working' directory that while present in previous versions has been replaced by mba4-tmp: line 246 in the script as of right now. There's also an error in line 252, inside the else statement (i suppose because there's nothing in there except a comment). These may seem like minor errors to some, but tripped me up at first.


Not sure what to do--- any help is appreciated. Thanks in advance.

---

### Post by dfacto on 2011-09-16
neither of those "errors" have  any affect  whatsoever but they do represent poor style. thanks for letting me know and ill remove line 246. i can stick a ;; in 251 if that makes you more comfortable. :)

i dont know why your video isnt working (its not because your hardware is "different;" youre barking up the wrong tree again). that is an actual problem. why dont you send then output  of the script as a .gz?

---

### Post by morloch on 2011-09-16
First of all, a big thanks to everyone who has worked on this, especially dfacto... the series of scripts you prepared have been a huge help.

I had the same problem as chaffin where the X server still wouldn't start.  Long story short, the answer is already in fix-i915.sh.  I had to manually copy the new i915.ko file from /lib/modules/$(uname -r)/extra/i915.ko to /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/i915/i915.ko.

I couldn't remember reading that anywhere (and I've read all 29 pages :)), but after copying the file over, running depmod and update-initramfs (also in the script), I rebooted to a very satisfying 1440x900 login screen.

Edit:

My apologies, here's the link to original .ko fix: [Post 222]("http://ubuntuforums.org/showpost.php?p=11232460&postcount=222")

---

### Post by hueythecat on 2011-09-16
Hi All

Can someone please advise me where im going wrong.

Im running a 2011 4,1 11"

I've partitioned OK (additional ms-dos)
I've installed reFit OK
I've run sync partitions from refit tool
I've used the Ubuntu MacBook Air Help to create the 11.04-amd64 USB
I've tested the USB on other systems and know it works

At this point I can only access the ubuntu install menu if I choose the EFI Boot option
I've edited the grub options and added nomodeset

I then press F10 to boot (It says that or ctrl+x I assume its the same and if i press ctrl+x it just types an x on the screen)

At this point it just goes to a black/blank screen my usb light flashes for a while and then just stops. 

Please advise

---

### Post by dfacto on 2011-09-16
> **morloch said:**
> First of all, a big thanks to everyone who has worked on this, especially dfacto... the series of scripts you prepared have been a huge help.

I had the same problem as chaffin where the X server still wouldn't start.  Long story short, the answer is already in fix-i915.sh.  I had to manually copy the new i915.ko file from /lib/modules/$(uname -r)/extra/i915.ko to /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/i915/i915.ko.

I couldn't remember reading that anywhere (and I've read all 29 pages :)), but after copying the file over, running depmod and update-initramfs (also in the script), I rebooted to a very satisfying 1440x900 login screen.

Edit:

My apologies, here's the link to original .ko fix: [Post 222]("http://ubuntuforums.org/showpost.php?p=11232460&postcount=222")

Thanks Morloch.  I thought I had fixed this by using the correct path for the "make modules_install".  I uncommented the line from fix-i915.sh.  It is still curious why seemingly everyone needs this except for me (and I have built/depmod'ed/rebooted many many times and have reinstalled several times too).

Anyway, thanks again for re-reporting the fix.

Do you happen to be on the 11"?  I am curious if the patches make everything work for the 11".

---

### Post by hueythecat on 2011-09-16
> **hueythecat said:**
> Hi All

Can someone please advise me where im going wrong.

Im running a 2011 4,1 11"

I've partitioned OK (additional ms-dos)
I've installed reFit OK
I've run sync partitions from refit tool
I've used the Ubuntu MacBook Air Help to create the 11.04-amd64 USB
I've tested the USB on other systems and know it works

At this point I can only access the ubuntu install menu if I choose the EFI Boot option
I've edited the grub options and added nomodeset

I then press F10 to boot (It says that or ctrl+x I assume its the same and if i press ctrl+x it just types an x on the screen)

At this point it just goes to a black/blank screen my usb light flashes for a while and then just stops. 

Please advise

My bad - i'd installed the usb on /dev/sdc1 instead of /dev/sdc

---

### Post by dfacto on 2011-09-16
I updated the [.Xmodmap]("http://almostsure.com/mba42/dotXmodmap") so that now the mouse has "reverse" scrolling (more like Lion).  It also remaps the keys, reading left-to-right:
  Fn Control_L Alt_L Super_L Space Super_R Alt_R
    -to-
  Fn Control_L Super_L Alt_L Space Alt_R Menu

The main reason to map it this way, is to make the keyboard "feel" more like a PC keyboard. Also, I think its nice to have a Menu key, particularly since if the trackpad driver borks, you still have the ability to signal a right-click. (I'm surprised there are things like "mousemu" floating around when the easiest thing is just sacrifice your redundant Super_R key.)

Its commented in such a way that should make it easy for you do modify it to your own taste.

---

### Post by chaffin on 2011-09-16
> **morloch said:**
> First of all, a big thanks to everyone who has worked on this, especially dfacto... the series of scripts you prepared have been a huge help.

I had the same problem as chaffin where the X server still wouldn't start.  Long story short, the answer is already in fix-i915.sh.  I had to manually copy the new i915.ko file from /lib/modules/$(uname -r)/extra/i915.ko to /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/i915/i915.ko.

I couldn't remember reading that anywhere (and I've read all 29 pages :)), but after copying the file over, running depmod and update-initramfs (also in the script), I rebooted to a very satisfying 1440x900 login screen.

Edit:

My apologies, here's the link to original .ko fix: [Post 222]("http://ubuntuforums.org/showpost.php?p=11232460&postcount=222")

Thanks very much for this post! I too had lost this in the mass of information spread over 29 pages. After a clean install of oneiric and the post-install script, my MBA now runs Ubuntu at full 1440x900. I had to run fix-i915 once more after reboot, but everything seems to be working now.

Major thanks to dfacto, without whose script I would surely have foundered upon the rocks of Sandy Bridge. Good luck with wrapping everything up in time for graduation, and congratulations!

---

### Post by dfacto on 2011-09-16
Thanks Chaffin--glad everything is working now.  Did you say you are using the 11" and if so, can you confirm trackpad, fn keys, and bluetooth are working?

---

### Post by hueythecat on 2011-09-18
Hey all.

I've successfully installed 11.04 on my mba 4,1
I chose /dev/sda4 as my boot partition for the "/" mount point 

When I restart after install (second time now) - launching the tux option immediately after the tux splash I just get a black screen with the flashing cursor.

Any tips?

---

### Post by morloch on 2011-09-18
> **dfacto said:**
> Do you happen to be on the 11"?  I am curious if the patches make everything work for the 11".

Sorry, I've got the 13".

---

### Post by chaffin on 2011-09-18
> **dfacto said:**
> Thanks Chaffin--glad everything is working now.  Did you say you are using the 11" and if so, can you confirm trackpad, fn keys, and bluetooth are working?

I'm on the 13" too.

On an unrelated note, I've found excellent support for multitouch gestures in the package [touchegg]("http://code.google.com/p/touchegg/"). The version found by apt-get isn't the most recent, but if you compile the 1.0 version from source, you can customize gestures to your heart's content. I disabled the mtrack driver and went back to the default by removing dfacto's xorg.conf --- then used a wrapper startup script to relaunch touchegg if it should fail, since there seem to be some errors in the current version that cause segfaulting. Here's the script I run on startup:

[INDENT]#toucheggwrapper
#!/bin/bash

if [ ! `pidof toucheggwrapper` ] ; then
while true
do
if [ ! `pidof touchegg` ] ; then
touchegg
fi
sleep 5
done
fi
[/INDENT]

Unity 3d has some annoying gestures enabled by default, and I haven't found any way to disable them, so for now I run unity 2d, and touchegg handles all my gestures, including two finger scrolling. If you miss compiz effects in unity 2d, you can create a startup script to have compiz steal the window manager when you log in.

---

### Post by dfacto on 2011-09-18
@chaffin Does it have inertial scrolling?  That's what I'm missing the most (from the ten minute I suffered with Mac OS).

Also, there is an up-to-date PPA for this--you don't need to build anything.

```

sudo add-apt-repository ppa:utouch-team/daily
sudo aptitude update -q2
sudo aptitude install touchegg

```

---

### Post by hueythecat on 2011-09-18
> **hueythecat said:**
> Hey all.

I've successfully installed 11.04 on my mba 4,1
I chose /dev/sda4 as my boot partition for the "/" mount point 

When I restart after install (second time now) - launching the tux option immediately after the tux splash I just get a black screen with the flashing cursor.

Any tips?

Anyone else here using a MBA 11"?

I've had the same problem now twice again with the 11.10 daily as well

Install goes fine set grub boot to /dev/sda4 

reboot - always two tux icons for some reason one hangs on the tux icon the other black screen flashing cursor...

---

### Post by dfacto on 2011-09-18
Are you using nomodeset when you boot?

---

### Post by chaffin on 2011-09-18
> **dfacto said:**
> @chaffin Does it have inertial scrolling?  That's what I'm missing the most (from the ten minute I suffered with Mac OS).

Also, there is an up-to-date PPA for this--you don't need to build anything.

```

sudo add-apt-repository ppa:utouch-team/daily
sudo aptitude update -q2
sudo aptitude install touchegg

```

No kinetic scrolling; but you can configure all sorts of three finger gestures that are analogous to what you get with the four finger pinch in OSX.

Based on [http://packages.ubuntu.com/source/oneiric/touchegg]("http://packages.ubuntu.com/source/oneiric/touchegg") it looks like the version installed by aptitude is 0.3, not the 1.0 version available from the code project itself. I couldn't get the 0.3 version to work, but the 1.0 built with no problems.

[http://manpages.ubuntu.com/manpages/oneiric/man4/synaptics.4.html]("http://manpages.ubuntu.com/manpages/oneiric/man4/synaptics.4.html") indicates that there's a "coasting" feature in the synaptics driver which replicates the inerital scrolling of OSX, but installing that driver using aptitude in oneiric broke my unity 3d and 2d both and I couldn't fix it without a reinstall.

---

### Post by hueythecat on 2011-09-18
> **dfacto said:**
> Are you using nomodeset when you boot?

Thanks for the reply

Yes the first time to do the install. Its phase two post install.

I don't get the opportunity as I never get to any screen where I can do this. i.e I'm not even getting to a Grub loader to press e or F6

Do the creation of all partitions pre-install ("/", "/home" & swap etc)
have to be made from OSX Disk Manager?

---

### Post by dfacto on 2011-09-18
Sounds like you need to do the gptsync from refit. If that doesnt work do the gdisk as described earlier in this thread.

---

### Post by dfacto on 2011-09-19
@chaffin Yeah you're right--I wasted 30 min trying to figure out what wasn't working--looks like the old version has a different conf type.  Anyway, to others who want to play with it:
```

wget http://touchegg.googlecode.com/files/touchegg-1.0.tar.gz
tar xzvf touchegg-1.0.tar.gz
cd touchegg-1.0
sudo aptitude install build-essential checkinstall fakeroot libqt4-dev utouch libx11-6 libxtst-dev
qmake
make -j2
fakeroot checkinstall -yD make install
mv touchegg_1.0-1_amd64.deb ..
cd ..
sudo dpkg -i touchegg_1.0-1_amd64.deb

```

It actually works with compiz 3d for me....sometimes.  And when it crashes, it seems to crash hard enough to warrant a lightdm restart.

I'm sticking with mtrack for now but touchegg definitely has potential to be the best.  I just can't give up these pretty 3d effects.

BTW, to run it you can just use:
```
 while :;do touchegg;done
```
to workaround the weird startup problem.

Anyway, I added the build code to the post-install-oneiric.sh script if anyone wants to try it out.

---

### Post by hueythecat on 2011-09-19
> **dfacto said:**
> Sounds like you need to do the gptsync from refit. If that doesnt work do the gdisk as described earlier in this thread.

no dice with gptsync

I'm out of ideas - I'll do a total OSX recover & start from scratch

---

### Post by dfacto on 2011-09-19
hueythecat, you *REALLY* need to be more specific. what EXACTLY doesn't work. what EXACTLY is the message. my crystal ball is in the other room! :)

read the old posts. I still have a hunch gdisk will fix things for you.  you can install it from the live usb session.

---

### Post by srs5694 on 2011-09-19
> **dfacto said:**
> hueythecat, you *REALLY* need to be more specific. what EXACTLY doesn't work. what EXACTLY is the message. my crystal ball is in the other room! :)

+1

In addition, information on your current partitions and boot loader setup may be useful. To that end, I recommend downloading and running the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) You'll need to run it from the Ubuntu install CD in its "try it now" mode. It will produce a file called RESULTS.txt. Post it here, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This script might not produce all the diagnostic data that's important, but it should produce enough to serve as a starting point.

---

### Post by hueythecat on 2011-09-19
> **dfacto said:**
> hueythecat, you *REALLY* need to be more specific. what EXACTLY doesn't work. what EXACTLY is the message. my crystal ball is in the other room! :)

read the old posts. I still have a hunch gdisk will fix things for you.  you can install it from the live usb session.


My apologies if I came across as vague.

After install & resyncing the MBR my system would not make it to grub - it just went to a black screen with flashing cursor forever.

At some stage I'm guessing I installed grub to the wrong partition. And failed from that point forwards.

After doing a total rebuild from scratch I've successfully installed.

On a side note (if you manage to delete your Lion recovery partition) - The internet recovery ONLY works if your wifi is WPA/WPA2 encrypted. So if your connected via open wifi it appears like its taking forever instead of informing you of the latter.

---

### Post by hueythecat on 2011-09-19
Also

I've run fix-i915.sh post install & it does not appear to resolve the resolution.(though no issues with installation)
I double checked a post regarding copying the i915.ko but this was in the correct location.

i.e. I can only boot if i use nomodeset

Am I the only 4,1 11" user here?

---

### Post by dfacto on 2011-09-20
> **hueythecat said:**
> Also

I've run fix-i915.sh post install & it does not appear to resolve the resolution.(though no issues with installation)
I double checked a post regarding copying the i915.ko but this was in the correct location.

i.e. I can only boot if i use nomodeset

Am I the only 4,1 11" user here?

First:
1) Can you tell me if bluetooth is working (icon next to wifi?)?
2) Does the fn+up fn+dn give pageup pagedown?
3) Can you right-click when you use two-finger click?

Next:
Are you using the most recent fix-i915.sh?  It should have a comment at the top that reads:
# Sun Sep 18 00:55:17 EDT 2011 - MBA4,1 Panel-type code
Also the most recent post-install-oneiric.sh has the comment:
# Mon Sep 19 00:53:49 EDT 2011 - code to build touchegg

Now, I need some information.  Run the following commands and post-back.
```

uname -a
cat /etc/issue
cat /sys/class/dmi/id/product_name
sudo get-edid 2>/dev/null|strings -5

```

You may need to install get-edid if the command is unavailable.
```

sudo aptitude install read-edid

```

---

### Post by ingineer on 2011-09-20
First off, Thanks for all your work Defacto (and everyone else) for working on this!

A few weeks ago I got a new MBA 13" (4,2).  Panel is LP133WP1-TJA3.

I installed Natty after some partitioning hell, and ran fix-i915 & post-install-natty.  Got proper graphics, touchpad, bluetooth, etc.  

A few days ago I decided to reinstall because I'm doing a triple-boot scheme, and now neither script works properly with natty any longer.  I assumed I did something wrong, so I tried again, and again.  I've done so much screwing around that I'm sure I've got the install in a screwed up state so troubleshooting is silly without yet another fresh install.  I don't have all the output when it failed but I did copy down a few:

```
fix-i915.sh: line 80: cd: linux-2.6.38/drivers/gpu/drm/i915/: No such file or directory
```

```
patching file intel_bios.c
Hunk #1 FAILED at 175.
1 out of 1 hunk FAILED -- saving rejects to file intel_bios.c.rej
```

I wanted to let you know that it appears broken for natty, and also to ask if in your opinion running oneiric is stable enough to use as a primary machine right now.  If so, I'll just go that route rather than trying to screw with installing natty yet again.

Thanks!

-Phil

---

### Post by dfacto on 2011-09-20
@ingineer Thanks for the feedback.

Yes I'm not surprised you had problems with Natty.  I sort of forgot that people would be using fix-i915.sh on Natty.

That script is basically a hack on top of a hack.  I suspect it will only work for 3.0.0-10 and 3.0.0-11 because these are the kernels I wrote it for.

Because of this issue you raised, I would recommend to all MBA4 owners to just go ahead and use Oneiric.  There are a few random crashes, but for the most part its stable.  Occasionally unity acts weird, but in [http://almostsure.com/mba42/](http://almostsure.com/mba42/) you will find a kick-unity script that can be run from a TTY to restart Unity (without having to logout).  This is nice because none of running windows are closed.

You can still probably make Natty work.  The best would be to make sure the kernel is newest (reboot to activate it) then try fix-i915.sh.  If it doesn't work (ie the patch is rejected) then you'll probably have to go the Oneiric route.

I think Oneiric is now only three weeks away so its probably a safe bet.

---

### Post by kiffykroker on 2011-09-20
I've been quite busy the last few days and haven't had much time to play around with this, since there's some issues regarding the 11" this is what I've encountered so far:

- The fix-i915 script does work with 11.04 and MBA4,1, just upgrade to 3.0.0 kernel

- I can't install any beta of 11.10 (have probably wasted 10+ discs), I always get "ubiquity closed unexpectedly", might be something wrong with my usb dvd drive, 11.04 installs however.

- Just for the sake of it I ran dfactos oneiric post-install script on my natty install and, while I ended up with a quite broke desktop interface, the script seemed to have done it's job regarding keyboard and touchpad.

So I still haven't tried anything on 11.10 but it seems that dfactos script might work just as well on MBA4,1 (thanks!).

At the moment I'm back on a fresh install of 11.04 with upgraded kernel and gonna see where I end up this time.

Once again thanks to defacto for your work!

---

### Post by dfacto on 2011-09-20
@kiffykroker Great! I suspected that the oneiric script would work for Natty too.  The main thing really is that you need to be on the 3.0.0, as you already pointed out.

In fact, there is nothing in the script that should break anything. The worst that can happen is that some things simply won't install.  I'm guessing the weird problems you had were from something else you did?

Please let me know if you find bugs.  Remember you can always run each line copy-and-paste style to track what's happening. (In fact, that's usually how I run stuff.)

If you have a USB thumb drive, its MUCH easier/faster to just install from that.  I have a script for that too.

Oh, and someone submitted patches for the 11" so hopefully those will be in for one of the release candidates of the 3.1 kernel.  Probably the Ubuntu people will backport it too.  Point being, with time my script won't do any kernel stuff, which would be great.

---

### Post by kiffykroker on 2011-09-20
> **dfacto said:**
> @kiffykroker Great! I suspected that the oneiric script would work for Natty too.  The main thing really is that you need to be on the 3.0.0, as you already pointed out.

In fact, there is nothing in the script that should break anything. The worst that can happen is that some things simply won't install.  I'm guessing the weird problems you had were from something else you did?

Please let me know if you find bugs.  Remember you can always run each line copy-and-paste style to track what's happening. (In fact, that's usually how I run stuff.)

I'm gonna try oneiric post install again on my fresh 11.04 install later tonight, but what I remember from last time was that Gnome looked really weird and my system said it was on 11.10(!).


> If you have a USB thumb drive, its MUCH easier/faster to just install from that.  I have a script for that too.

Oh, and someone submitted patches for the 11" so hopefully those will be in for one of the release candidates of the 3.1 kernel.  Probably the Ubuntu people will backport it too.  Point being, with time my script won't do any kernel stuff, which would be great.I did buy me a USB thumb drive today actually (while I also loaded up on more CD-R), but your script is not for OSX right? My OSX partition on my MBA has all the iso and works as my main machine at the moment. I might try it on my Ubuntu server or XBMC machine though, since they're on wired network the iso download should be pretty fast aswell.

---

### Post by hueythecat on 2011-09-20
Hey dfacto

I'll get on to this this afternoon. Don't have my MBA on me this morning.
PS 

The fix-i915.sh I ran was directly from [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

I ran it yesterday so it would have had
# Sun Sep 18 00:55:17 EDT 2011 - MBA4,1 Panel-type code

Also when it first arrived I checked the panel type and it was the samsung.


Will supply full deets later today.

---

### Post by hueythecat on 2011-09-20
P.S You want me to change my install to 11.04 to 11.10 first?

---

### Post by dfacto on 2011-09-20
@kiffykroker I *think* it would work on Mac too.  You'll need to change the path, I think Mac likes /dev/diskx over /dev/sdax.  Off the top of my head it should work. The post-install script cannot possibly change any version-ing from 11.04 to 11.10. :)

@hueythecat Its up to you. Personally I'd install Oneiric (and I have) but I am curious if my script works on Natty.  I guess it largely depends on your comfort with Ubuntu/Linux. If you think you can handle a few minor problems (ie compiz/unity bugs) then you'll be fine in Oneiric.

One other option is "both."  You could install Natty then do:
```

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude install
sudo do-release-upgrade -d

```
which would put you on Oneiric.

I like to do the install line because sometimes packages are held for various reasons.

---

### Post by ingineer on 2011-09-20
Thanks Defacto!

Oneiric installed without a hitch.  I ran fix-i915 and rebooted w/o nomodeset and I had working graphics!

I then ran post-install-oneiric and let it do it's thing, and upon reboot, Everything still worked except Wifi.  It shows up in the interface list and looks like iwconfig will talk to it, but it's dissappeared from the gui.

UPDATE: Looks like NetworkManager lost one of it's shared libraries when post-install did it's thing:

```
NetworkManager: error while loading shared libraries: libnss3.so: cannot open shared object file: No such file or directory
```Not sure low to fix this.  I also don't seem to have TouchPad support, but Bluetooth and KB are working OK.  I'll keep poking around.

---

### Post by dfacto on 2011-09-21
Yep, I had this too.  I also had xorg-edgers take a crap on me (fixed with ppa-purge).

Install this and you'll be good to go:
64bit:
[http://packages.ubuntu.com/oneiric/amd64/libnss3/download](http://packages.ubuntu.com/oneiric/amd64/libnss3/download)

32bit:
[http://packages.ubuntu.com/oneiric/i386/libnss3/download](http://packages.ubuntu.com/oneiric/i386/libnss3/download)

BTW, its not post-install that did that, its Canonical.  Welcome to development branch! :)

On the plus side, todays updates made the keyboard buttons work properly so you don't need my keyboard-backlight script.

---

### Post by hueythecat on 2011-09-21
Tried to install the daily of oneric - got through the install but rebooting always lead to -> missing operating system & refit didnt say it wanted to resync

Re installing natty went fine

Deets post initial update(have not yet run fix-i915.sh)

Linux jman-MacBookAir 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

no right click

no fn+up or down

backlit keyboard ok

no bluetooth icon & launching bluetooth says no hardware detected

cat /etc/issue
Ubuntu 11.04 \n \l

cat /sys/class/dmi/id/product_name 
MacBookAir4,1 

sudo get-edid 2>/dev/null|strings -5
LTH116AT01A04
Color LCD

---

### Post by ingineer on 2011-09-21
@Defacto, Thanks again.  I had already located another libnss3, which did fix NetMan.  Now I have everything working but touchpad.  Keyboard, Bluetooth, KB LEDs, etc, all ok!

I've tried all variants of xorg.conf, nothing seems to make a difference.

What modules should be loaded for the current iteration of touchpad support?

```
Module                  Size  Used by
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
nls_utf8               12557  1 
hfsplus                88963  1 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_cirrus    18601  1 
rfcomm                 47946  8 
bnep                   18436  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
wl                   2568210  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72711  0 
lib80211               14991  1 wl
bcma                   20219  0 
videodev               93004  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
v4l2_compat_ioctl32    17083  1 videodev
applesmc               19554  0 
input_polldev          13896  1 applesmc
btusb                  18600  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              631693  0 
bluetooth             166112  23 bnep,rfcomm,btusb
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 brcmsmac,mac80211
binfmt_misc            17540  1 
crc_ccitt              12667  1 brcmsmac
apple_bl               13225  0 
i915                  556365  3 
mei                    41480  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_apple              13281  0 
usb_storage            57901  0 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
```

---

### Post by hueythecat on 2011-09-21
Update

Living on the edge i've installed the 3.1 kernel rc4 on 11.04

I've rebooted without nomodeset

Then run the fix-i915.sh

initially i booted into unity @ a whacked out 1920x1080
I can reset the screen to 1360x768 16:9 - things are still stretched & theres a good 1 inch chunk of garbage on the right hand side. 

Is anyone out there running a perfect 1366x768?

---

### Post by dfacto on 2011-09-21
@ingineer.  Good; here are the drivers I modified:

i915       video
btusb      bluetooth
hid_apple  keyboard
bcm5974    trackpad

Looks like you're missing bcm5974.  Try `modprobe bcm5974` then ctrl-alt-F1 and do `sudo service lightdm restart`.  If that fixes it then you can add bcm597 to /etc/modules.  If that does't woek then try to walk through the post-install script by running sections at a time (from the top) to make sure everything worked.  This will add repeated lines to the conf files (which shouldn't be a problem but you may want to clean it up later).

@hueythecat  I guess you still haven't taken my advice and looked at the previous [gdisk discussion]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185"). Reinstalling is the windows way--in Linux-world there is usually a much easier solution.  So nothing works after the post-install script or nothing works out-of-the-box?

---

### Post by kiffykroker on 2011-09-21
Hmm, I can't get the touchpad to work on 11.04. I've followed the post-install-oneiric line by line and patched the kernel and installed mtrack and dispad, yet nothing.

It's a shame since it seems all other critical stuff is working. Any ideas?

---

### Post by dfacto on 2011-09-21
dmesg ? /var/log/Xorg.0.log ?

---

### Post by ingineer on 2011-09-21
@Defacto:

Looks like there is an error in line 110 of your oneiric script.  The path for locating bcm5974.patch is incorrect.  I fixed that and voila, it works!

Of course the TP config is horrible, my old habit of clicking with my right thumb is generating right-clicks instead of left.  Maybe I'll screw with a better config.

Thanks again!

-Phil

---

### Post by dfacto on 2011-09-21
@ingineer

Yes I agree the trackpad really is pretty bad.  I tried three different: multitrack, track, touchegg.  All had defects but maybe you can tweak the settings of one or more and make it work as well as OSX.

Regarding the bug, I can't seem to find the problem.  What was your fix?  When I paste the bcm5974 code block in a terminal, the patch applies successfully and the make/install chain works.

**Aha**! I see I recursed one-too-many directories (and I happened to have a copy of the patch that dir too).  It is now fixed and uploaded. Thanks for the correction!

@kiffykroker This should fix your issue too.

---

### Post by kiffykroker on 2011-09-21
> **dfacto said:**
> @ingineer

Yes I agree the trackpad really is pretty bad.  I tried three different: multitrack, track, touchegg.  All had defects but maybe you can tweak the settings of one or more and make it work as well as OSX.

Regarding the bug, I can't seem to find the problem.  What was your fix?  When I paste the bcm5974 code block in a terminal, the patch applies successfully and the make/install chain works.

**Aha**! I see I recursed one-too-many directories (and I happened to have a copy of the patch that dir too).  It is now fixed and uploaded. Thanks for the correction!

@kiffykroker This should fix your issue too.

Unfortunately not, I used a correct path to the patch when I ran the script line by line. I guess something else could have gotten messed up though, will try the updated script.

What should I look for in dmesg and Xorg.0.log?

I found this in Xorg.0.log
```
[    17.167] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event5)
[    17.167] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev pointer catchall"
[    17.167] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    17.167] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.167] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    17.167] (**) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event5"
[    17.167] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Found 3 mouse buttons
[    17.167] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Found relative axes
[    17.167] (--) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Found x and y relative axes
[    17.167] (II) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as mouse
[    17.167] (**) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: YAxisMapping: buttons 4 and 5
[    17.167] (**) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.167] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input5/event5"
[    17.167] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: MOUSE)
[    17.168] (II) evdev: Apple Inc. Apple Internal Keyboard / Trackpad: initialized for relative axes.
[    17.168] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) keeping acceleration scheme 1
[    17.168] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration profile 0
[    17.168] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration factor: 2.000
[    17.168] (**) Apple Inc. Apple Internal Keyboard / Trackpad: (accel) acceleration threshold: 4
[    17.168] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/mouse0)
[    17.168] (II) No input driver/identifier specified (ignoring)
```

---

### Post by dfacto on 2011-09-21
I'll bet you're using an older xorg.conf.  I see its loading ev_dev not mtrack.  Make sure the file /etc/X11/xorg.conf agrees with the one that's embedding inside post-install-oneiric.sh.

---

### Post by kiffykroker on 2011-09-21
> **dfacto said:**
> I'll bet you're using an older xorg.conf.  I see its loading ev_dev not mtrack.  Make sure the file /etc/X11/xorg.conf agrees with the one that's embedding inside post-install-oneiric.sh.

The /etc/X11/xorg.conf should be the one that's created from the script, right? I ran the script again and still no luck. It's so weird because I know I had it working with a previous install of 11.04 I did on this system.

```
## touchegg
#Section "InputClass"
#   Identifier      "touchpad catchall"
#   Driver          "evdev"
#   MatchIsTouchpad "true"
#   MatchDevicePath "/dev/input/event*"
#   #MatchUSBID     "05ac:024c"
#EndSection # "touchpad catchall"
## mtrack
Section "InputClass"
    Identifier      "Multitouch Touchpad"
    Driver          "mtrack"
    MatchIsTouchpad "true"
    MatchDevicePath "/dev/input/event*"
    Option          "CorePointer" "true"
    Option          "Sensitivity" "0.95"
EndSection # "Multitouch Touchpad"
```

---

### Post by hueythecat on 2011-09-21
@Defacto: 

Switched again from 11.04 to 11.10 on my MBA 4,1

THEN

Followed the gdisk post verbatim.  
Of note: after initial reboot from Lion, Tux still hung. A second power down and restart resolved.

post install run default update
presently running fix-i915

Update:
Now running @ native resolution. Woot!

Where to from here? 
I see post install oneric comments its time to identify device ID's and mod accordingly.

FYI: 
[lspci]("http://dl.dropbox.com/u/964168/lspci.txt")
[lshw]("http://dl.dropbox.com/u/964168/lshw.txt")

---

### Post by dfacto on 2011-09-21
@hueythecat I don't understand.... Just run the script?

---

### Post by hueythecat on 2011-09-21
Sure - I thought it was only for the MBA 4,2.

After running:

Note: script failed to download libcogl2

Post reboot:

Not much (appears to have) changed:

No bluetooth detected 
No fn+up dn etc
System not auto mounting usb
trackpad not doing anything new (xorg.conf set to load mtrack)


Question: If i rerun the post install - for all the stuff thats detected as patched, is it fine to skip?

---

### Post by dfacto on 2011-09-21
Dude. Just run the script, eh?

---

### Post by hueythecat on 2011-09-21
> **dfacto said:**
> Dude. Just run the script, eh?

"After running:" = After running the oneric post install script

sorry for not being more specific - I'm trying to be helpful

---

### Post by ChinaSailor on 2011-09-22
Nice work on the script

But unfortunately, same here... no worky... 
Essentially nothing is different from the cd generic install (I have did probably 7 different re-installs)

The very obvious problems I encountered:
AppleUSBVideoSupport  (the program fails to use complete "mounted" location path)
LCD-00000610-0000-9CDF-0000-0000042737C0.icc (I think it is named something else on my mba)

I manually copied them to my home directory and modified the script accordingly, but still no go. (that is, did not affect the final outcome to mba after script was successfully run), nothing other than what the generic cd will do.

Are you manually editing config files afterwards to get these display settings to show up..?
(I noticed an 'xorg.conf' file on your mba42 site, are you manually copying that in after the script is run..?)

The only errors I was able to see:

Current status: 0 broken [-1], 39532 new [-1].
doesn't appear that firmware was properly extracted
coretemp
hid_apple
options hid_apple fnmode=2
FATAL: Error inserting coretemp (/lib/modules/3.0.0-11-generic/kernel/drivers/hwmon/coretemp.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Configuring macfanctld to ignore some sensors. On my system three
sensors gave bogus readings, i.e.,
    TH0F: +249.2 C                                    
    TH0J: +249.0 C                                    
    TH0O: +249.0 C
Run 'sensors' to see current values; run 'macfanctld -f' to
obtain the list of sensors and their associated ID.
Applying this exclude: 13 14 15.
./post-install-oneiric.sh: line 414: /home/tim/.gconf/desktop/gnome/keybindings/custom0/%gconf.xml: No such file or directory

---

### Post by dfacto on 2011-09-22
@ChinaSailor Thanks; this is specific enough that I can actually do something about it.

First, the easy one: line 414.  Actually, as of two days ago, unity does its job and appropriately handles the keyboard backlight.  So I just added an if false around that key-binding block.

Second, coretemp.  This bug does not have anything to do with the script.  I only load coretemp--I never modify it.  Loading this module shouldn't be a problem.  I need to see some more info to be sure.  Try this:
```

sudo modprobe -r coretemp
sudo modprobe -a coretemp
dmesg|gzip >dmesg.txt.gz

```
and post back the file.

when I run `zcat dmesg.txt.gz |tail -2`, I see,
```

[ 2734.258958] coretemp coretemp.0: TjMax is 100 C. 
[ 2734.259007] coretemp coretemp.0: TjMax is 100 C.

```

Third, video.  If the mount didn't work (which is likely--I made assumptions about how you have things set-up) then you can do it yourself.  Mount you MacOS drive and run:
```

sudo dpkg-reconfigure -phigh isight-firmware-tools

```
and choose the correct path.

Fourth, color.  That file just makes the colors calibrated. Wherever it lives on you system, just run: gcm-import /path/to/file.icc

Fifth, xorg.conf. You shouldn't need to download an xorg.conf.  The correct /etc/X11/xorg.conf reads:
```


#Section "InputClass"
#   Identifier      "touchpad catchall"
#   Driver          "evdev"
#   MatchIsTouchpad "on"
#   MatchDevicePath "/dev/input/event*"
#   #MatchUSBID      "05ac:024c"
#EndSection

Section "InputClass"
    Identifier      "Multitouch Touchpad"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver          "mtrack"
    Option          "CorePointer" "true"
    Option          "Sensitivity" "0.95"
EndSection # "Multitouch Touchpad"

```
(I just changed default sensitivity to .65 which works better with the "Mouse and Trackpad" app.)

What else doesn't work?

---

### Post by ChinaSailor on 2011-09-22
@[dfacto]("http://ubuntuforums.org/member.php?u=52141") 

Thank you, I will try all of your suggestions first thing tomorrow morning.

Essentially, I wouldn't say what doesn't work, but rather what works... 
None of the fixes you mentioned (on your site), work on mine. 
I haven't been able to get anything working, other than, what would be generated by a standard install. 

The display is stuck at a max of 1024x768 
(but I have not tried to change it through anything other than the gnome "Displays" portal)

I would be happy with just getting the screen resolution and intensity / brightness working 
(keyboard back-lighting and the simulated 'function' of the right mouse click would also be nice) 
But I will take, what-ever you have working.

Thanks.

---

### Post by dfacto on 2011-09-22
What exactly is "none"?  Right-click, FN keys, 1440x900 video?

I'm not sure I can help more.  It was my understanding that it worked for other 4,1 users but I could be mistaken.  If you can't figure it out, you may need to wait until someone more experienced has time to play with the script on their 4,1 and see what's broken.  Honestly though, its hard to imagine that there isn't some other issue as the script isn't magical--it just does some simple tweaks.

---

### Post by hueythecat on 2011-09-22
> **dfacto said:**
> What exactly is "none"?  Right-click, FN keys, 1440x900 video?

I'm not sure I can help more.  It was my understanding that it worked for other 4,1 users but I could be mistaken.  If you can't figure it out, you may need to wait until someone more experienced has time to play with the script on their 4,1 and see what's broken.  Honestly though, its hard to imagine that there isn't some other issue as the script isn't magical--it just does some simple tweaks.

From 4,1 mba:

1. 11.10 install(oneiric daily build)
2. gdisk fix from Lion(in order to boot after install)
3. initial ubuntu update
4. fix-i915.sh
5. reboot to native resolution(no configuration required on my behalf)

---

### Post by hueythecat on 2011-09-22
@defacto

Is there anything you want me to do/try with the mba 4,1?

---

### Post by dfacto on 2011-09-22
Sorry, I'm out of ideas.  Hopefully someone who has a 4,1 can be more helpful.

---

### Post by hueythecat on 2011-09-22
4,1 Notes:

Browsing dmesg I'm not noticing any errors/failed to load

Bluetooth appears to be detected - but my GUI bluetooth tools are not detecting any devices.(need to look further)

The one thing puzzling me is the mtrack module:

Its present on my system & its mentioned in the updated xorg.conf

Its not however mentioned in the Xorg.0.log at all i.e loaded or failed to load. Not sure what to do from here

---

### Post by chaffin on 2011-09-22
After a little while using my machine after post-install-oneiric.sh I noticed that the .Xmodmap file created by dfacto's script reverts to default on suspend/wake. In case anyone else has the same problem I found the solution here: [https://bbs.archlinux.org/viewtopic.php?id=88369](https://bbs.archlinux.org/viewtopic.php?id=88369) . The solution is to create a new script at /etc/pm/sleep.d/11Xmodmap

```
#!/bin/bash
case $1 in
    hibernate)
        echo "Hey guy, we are going to suspend to disk!"
        ;;
    suspend)
        echo "Oh, this time we're doing a suspend to RAM. Cool!"
        ;;
    thaw|resume)
        echo "oh, suspend is over, we are in $1 phase..."
            # Set Display #
    DISPLAY=:0.0 ; export DISPLAY
    /bin/su - **me** -c "sleep 3; /usr/bin/xmodmap /home/**me**/.xmodmaprc" &
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac
```

Replace **me** with your username and make sure to chmod +x the file. Suspend issues fixed!

Hope this helps someone out.

---

### Post by ChinaSailor on 2011-09-22
> **dfacto said:**
> What exactly is "none"?  Right-click, FN keys, 1440x900 video?

I'm not sure I can help more.  It was my understanding that it worked for other 4,1 users but I could be mistaken.  If you can't figure it out, you may need to wait until someone more experienced has time to play with the script on their 4,1 and see what's broken.  Honestly though, its hard to imagine that there isn't some other issue as the script isn't magical--it just does some simple tweaks.


Ok, I just ran the script again, from the start (the new updated 22sept version) and no change from before.
It will run, without any errors, but after the reboot, there is no change. Display resolution will max out at 1024x768. I even copied the xorg.conf from your site into my X11/, but then gnome will not start, and it goes into cmd line "kernel oops" mode. 

Just fyi, I am running a mba 4.2 i7 1.8ghz, I assume this is what everyone else here is running.  

I do not know what you guys are using or editing to get into Native (or near Native) display resolutions...

Do I manually need to run xrandr to update to the new resolutions...? Or should it automatically be picked up after the script runs..?

Thanks

---

### Post by dfacto on 2011-09-22
@chaffin  Oops I forgot to share that.  I also wrote a version:
[http://almostsure.com/mba42/00_usercustom](http://almostsure.com/mba42/00_usercustom)

In general if you don't see something in post-install-oneiric.sh check the directory: [http://almostsure.com/mba42/](http://almostsure.com/mba42/) as there is a good chance its there. :)

@ChinaSailor well I am guessing you have a different modeline--there was some chatter about that on the [bug list]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").  i really can't help you other than to say boot with "drm.debug=0x06" then paste "dmesg|grep Modeline" back here.

If you still have trouble [read this]("http://intellinuxgraphics.org/how_to_report_bug.html") and submit your info [here]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").

BTW chinasailor, you may be one of the people I was expecting to have a problem.
Look in fix-i915.sh:

    'MacBookAir4,2/LTH133BT01A03')
        # not known if LP patch works; falling-through
        ;&

Whats the output of:
sudo get-edid 2>/dev/null|strings -5

---

### Post by ChinaSailor on 2011-09-22
> **dfacto said:**
> @chaffin  Oops I forgot to share that.  I also wrote a version:
[http://almostsure.com/mba42/00_usercustom](http://almostsure.com/mba42/00_usercustom)

In general if you don't see something in post-install-oneiric.sh check the directory: [http://almostsure.com/mba42/](http://almostsure.com/mba42/) as there is a good chance its there. :)

@ChinaSailor well I am guessing you have a different modeline--there was some chatter about that on the [bug list]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").  i really can't help you other than to say boot with "drm.debug=0x06" then paste "dmesg|grep Modeline" back here.

If you still have trouble [read this]("http://intellinuxgraphics.org/how_to_report_bug.html") and submit your info [here]("https://bugs.freedesktop.org/show_bug.cgi?id=39533").

BTW chinasailor, you may be one of the people I was expecting to have a problem.
Look in fix-i915.sh:

    'MacBookAir4,2/LTH133BT01A03')
        # not known if LP patch works; falling-through
        ;&

Whats the output of:
sudo get-edid 2>/dev/null|strings -5


Done, but there are NO Modeline(s) in the dmesg. 
Is there something else I should look for in the dmesg?

I did notice that my BOOT cml line:
"Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-11-generic root=UUID=3aea32b5-4f92-46e2-9c0a-e1dac6275834 ro nomodeset drm.debug=0x06 quiet splash i915.i915_enable_rc6=1 vt.handoff=7"

Shouldn't it specify something like "video=eDP1:1440x900-24@6" ?

thanks

---

### Post by dfacto on 2011-09-22
That wont work.  Try drm.debug=0x14

See if you can do it WITHOUT nomodeset.  You may need to login and dump dmesg blind. If it doesn't kernel panic, you could also SSH in from a second machine.  If indeed your modelines are different then your model is the last piece of the puzzle.  Also you never sent me your get-edid.

---

### Post by ChinaSailor on 2011-09-22
> **dfacto said:**
> That wont work.  Try drm.debug=0x14

See if you can do it WITHOUT nomodeset.  You may need to login and dump dmesg blind. If it doesn't kernel panic, you could also SSH in from a second machine.  If indeed your modelines are different then your model is the last piece of the puzzle.  Also you never sent me your get-edid.

When I ran that cmd, nothing

No, kernel panic without the nomodeset.
I will try ssh.

---

### Post by ChinaSailor on 2011-09-23
> tim@macbookair:~$ dmesg | grep -i modeline
[    5.368208] [drm:drm_mode_debug_printmodeline], Modeline 0:"1280x800" 0 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    5.368224] [drm:drm_mode_debug_printmodeline], Modeline 0:"1600x1200" 0 162000 1600 1664 1856 2160 1200 1201 1204 1250 0x8 0xa
[    6.916642] [drm:drm_mode_debug_printmodeline], Modeline 24:"1280x800" 60 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    7.346912] [drm:drm_mode_debug_printmodeline], Modeline 0:"" 0 0 0 0 0 0 0 0 0 0 0x0 0x0
[    7.346915] [drm:drm_mode_debug_printmodeline], Modeline 25:"1280x800" 60 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    7.346927] [drm:drm_mode_debug_printmodeline], Modeline 25:"1280x800" 60 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    7.399277] [drm:drm_mode_debug_printmodeline], Modeline 25:"1280x800" 60 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    8.861510] [drm:drm_mode_debug_printmodeline], Modeline 24:"1280x800" 60 72500 1280 1328 1360 1423 800 803 809 846 0x8 0xa
[    8.861515] [drm:drm_mode_debug_printmodeline], Modeline 28:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa
[    8.916600] [drm:drm_mode_debug_printmodeline], Modeline 27:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa
[    9.488804] [drm:drm_mode_debug_printmodeline], Modeline 27:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa
[    9.543930] [drm:drm_mode_debug_printmodeline], Modeline 27:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa
[   10.039690] [drm:drm_mode_debug_printmodeline], Modeline 27:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa
[   10.094771] [drm:drm_mode_debug_printmodeline], Modeline 27:"1440x900" 0 88890 1440 1488 1520 1600 900 903 909 926 0x48 0xa


drm.debug=0x14 & no nomodeset

---

### Post by dfacto on 2011-09-23
Try the new [fix-i915.sh]("http://almostsure.com/mba42/fix-i915.sh").  Make sure it has a revision dated "Fri Sep 23 08:46:45 EDT 2011".

And you still didn't tell me the output of:
```

sudo get-edid 2>/dev/null|strings -5

```
(Get and save this information before running fix-i915.sh.)

After applying the patch, make sure to remove "nomodeset" and "i915.modeset=0" from the grub boot parms (if they are present) so we can see if it is working.

I am fairly certain that this will fix your problem.

---

### Post by ChinaSailor on 2011-09-23
> **dfacto said:**
> Try the new [fix-i915.sh]("http://almostsure.com/mba42/fix-i915.sh").  Make sure it has a revision dated "Fri Sep 23 08:46:45 EDT 2011".

And you still didn't tell me the output of:
```

sudo get-edid 2>/dev/null|strings -5

```(Get and save this information before running fix-i915.sh.)

After applying the patch, make sure to remove "nomodeset" and "i915.modeset=0" from the grub boot parms (if they are present) so we can see if it is working.

I am fairly certain that this will fix your problem.

Sorry, maybe I should have stated explicitly, but that cmd yielded nothing at all.


The patch works great!
Thank you!

---

### Post by ChinaSailor on 2011-09-23
Just FYI - One item I did notice.

After I completed the patch,
and rebooted, I ran package manager to update, and it prompted me to do a 'partial-upgrade'
so it added 26 packages, they all looked like display drivers, and it also removed 1 package, 
a vm-ware display driver. (it installs 2 or 3 input packages, including a 'trackpad')

After I rebooted, the display is fine, no change, but the track-pad, mouse pointer is dead, will not accept any internal input from the track-pad. But if I plug in an external usb mouse, the pointer will spring to life.
But as soon as you remove the external mouse, the pointer is dead again.

I always clone the partition before making any major changes, so I just re-wrote the partition back to it's last state.

Great work on the fix-i915.sh!

---

### Post by dfacto on 2011-09-24
Great; glad to hear everything works for you.  I also had a problem with the most recent xorg-edgers.  An easier/quicker solution is to just:
```

sudo ppa-purge ppa:xorg-edgers/ppa

```
which would undo any of the xorg-edgers updates.

Also, if you find that the drivers don't work, just re-run post-install-oneiric.sh and at some point it will ask you if you want to proceed.  Say no.  Reboot.  Good to go.

---

### Post by poliva on 2011-09-24
Finally got my 13" MBA and installed ubuntu 11.10, almost everything works fine thanks to dfacto scripts and efforts (thanks man!).

I found two minor issues with the post-install-oneiric.sh script which you might want to fix:

1) Dispad doesn't install correctly because of unmet dependency:
```

dpkg: dependency problems prevent configuration of dispad:
 dispad depends on libconfuse0 (>= 2.6-2); however:
  Package libconfuse0 is not installed.
dpkg: error processing dispad (--install):
 dependency problems - leaving unconfigured

```

To fix, just install the dependencies before installing dispad:
```

$ sudo apt-get install libconfuse-common libconfuse0

```

2) Folder '~/.config/autostart' doesn't exist by default, so files dispad.desktop and xmodmap.desktop are not created successfully if the directory is not created previously:

```

tee: /home/poliva/.config/autostart/dispad.desktop: No such file or directory
tee: /home/poliva/.config/autostart/xmodmap.desktop: No such file or directory

```

Finally, I wanted to ask if hibernate is working for you guys? (I can hibernate, but when I power on again, it doesn't recover, so it's useless at the moment). Will have a look and see if I can understand why it's failing.

---

### Post by dfacto on 2011-09-24
@poliva Thanks--I made the fixes you pointed out.  I confirm that hibernate does not work.  After resuming hibernate, selecting kernel from grub, the system pauses on a blank purple-ish screen.  After a timeout it reboots back to refit and selecting the kernel again results in a non-resumed session.

---

### Post by dfacto on 2011-09-24
I made a few tweaks to xorg.conf.
```

Section "InputClass"
    Identifier      "Multitouch Touchpad"
    MatchDevicePath "/dev/input/event*"
    MatchIsTouchpad "on"
    Driver          "mtrack"
    Option          "CorePointer"       "true"
    Option          "Sensitivity"       "0.65"  #    1 : movement speed
    Option          "ScrollDistance"    "100"   #  150 : two-finger drag dist for click
    Option          "ClickTime"         "35"    #   50 : millisec to hold emulated click
EndSection # "Multitouch Touchpad"

```

I think this gives better scrolling and more responsive clicking.  I lowered the sensitivity so that way the "Mouse and Trackpad" sensitivity is better calibrated.

---

### Post by ingineer on 2011-09-24
Had to reinstall, and now seeing new failures I didn't see before (running post-install-oneiric):

```
Downloading mtrack (xorg multitouch driver).
Downloading dispad (touchpad pause daemon).
Downloading macfanctld (fan control daemon).
Installing packages: macfanctld xserver-xorg-input-mtrack dispad.
dpkg: error processing xserver-xorg-input-mtrack_*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing dispad_*.deb (--install):
 cannot access archive: No such file or directory
Selecting previously deselected package macfanctld.
(Reading database ... 198144 files and directories currently installed.)
Unpacking macfanctld (from macfanctld_0.5~mactel1~maverick_amd64.deb) ...
Setting up macfanctld (0.5~mactel1~maverick) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg-input-mtrack_*.deb
 dispad_*.deb
```Looks like mtrack is failing because:
```
wget  http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb
--2011-09-24 12:41:52--  http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb
Resolving www.dev.fatedmariner.org... 24.166.184.246
Connecting to www.dev.fatedmariner.org|24.166.184.246|:80... failed: No route to host.

```I can't find the mtrack package anywhere else, but newer source appears to be available.  Can anyone send me the 0.2.0 package?  Until fatedmariner comes back, this project is dead in the water.

Update: I compilied from source, and confirmed it's working properly.  Here's the package in case others have this problem:
[http://ingineerix.com/xserver-xorg-input-mtrack_0.2.0_amd64.deb](http://ingineerix.com/xserver-xorg-input-mtrack_0.2.0_amd64.deb)

---

### Post by ingineer on 2011-09-24
Found some other new bugs:

In line 533 there is the cp command to copy the ICC profile, but the destination directory doesn't exist. 
Fix: add this before line 533:
```
sudo mkdir /usr/share/color/icc
```Also, the iSight firware extractor is looking for /MacOSX/ rather than the mounted /media/Mac OS/ for extraction as default.  Maybe a symlink would be useful?

---

### Post by poliva on 2011-09-24
> **ingineer said:**
> I can't find the mtrack package anywhere else, but newer source appears to be available.  Can anyone send me the 0.2.0 package?  Until fatedmariner comes back, this project is dead in the water.

Here's a copy in dfacto's server:

[xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb]("http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb")

---

### Post by ingineer on 2011-09-24
> **poliva said:**
> Here's a copy in dfacto's server:

[xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb]("http://almostsure.com/mba42/mba4-tmp/xserver-xorg-input-mtrack_0.2.0_natty_amd64.deb")Thanks Poliva, but by the time I saw this, I had already figured out how to build it from source.  Here's my package confirmed working:
[http://ingineerix.com/xserver-xorg-input-mtrack_0.2.0_amd64.deb](http://ingineerix.com/xserver-xorg-input-mtrack_0.2.0_amd64.deb)

---

### Post by ChinaSailor on 2011-09-24
Perhaps somebody knows this or I didn't catch it on this thread.

Is there a way to fix the "Right-Click" with this trackpad..?

I am a little unsure, what the exact behavior of the tractpad is after the fix 
(my mba has been a special case, so far...)

Normally on the mac, you hold Cntr + trackpad click, but this yields nothing.

What I have found that works, depending on where the pointer is located, either the F12 
Or Command + F12

Anyone know of a quickie fix, to make the behavior standard, in some fashion or form or is this the best I should hope for without expending dozens of man-hours?
(Maybe I can alias it in my inputrc?)


Thanks

---

### Post by dfacto on 2011-09-24
Thanks all; bugs fixed.

---

### Post by poliva on 2011-09-25
@ChinaSailor: for the right click, just click with two fingers. For the middle (3rd button) click, click with 3 fingers.

---

### Post by jonny on 2011-09-25
> **poliva said:**
> For the middle (3rd button) click, click with 3 fingers.
That depends on what changes you've made.  By default, Ubuntu uses a three finger tap for the incredibly useful window-dragging and resizing facility.  And, if you haven't already discovered it, a four finger sideways swipe hides or reveals the Unity launcher.

---

### Post by davidpitkin on 2011-09-25
Hello,

Thanks for all this great work, and congratulations Joshua on graduating.

I have a mba4,1 and its mostly working. The display works at full resolution after I move the i915.ko to the drm folder manually, but this might be because I did not always delete the mba-tmp folder and had an older fix915.sh.

Right now bluetooth, keyboard backlight, multitouch and the FN keys are not working.

I am not running 64-bit since I only have 4GB of ram but the mtrack .deb packages linked here are all 64-bit.

I attached the lsusb, lspci and lshw outputs.

My MBA is obviously an 11" i7, US Keyboard

Hope this helps the effort.

David

---

### Post by dfacto on 2011-09-26
All of the drivers for the hardware you listed is built from source in post-install-oneiric.sh.  This means there should be no issues of whether its 32 or 64.  Since other MBA41 people have it working, you must be doing something different?  Use the latest version of post-install-oneiric.sh (which will automatically download and run fix-i915.sh if needed or local copy is older).

I didn't look at your hardware dumps but there is nothing that I need to know.  The device id's have already been determined.

---

### Post by ChinaSailor on 2011-09-26
@[poliva]("http://ubuntuforums.org/member.php?u=586448") - Indeed the two fingers do work, although a bit tricky.

Is anyone running 11.04..? Obviously there is a working script for that too, but I am just curious as to how that runs vs the 11.10 (on this MBA)..?

I know that the 11.04 is running the 2.6.38-11 and the 11.10 has the 3.0.0-11, I wonder are there any real advantages to running the 11.10..? 
I.E... Like increased native architect chip support or mac device stuff? I am constantly getting those gnome pop-up errors. 
So if there are no real disadvantages, esp concerning the "post-install" scripts, I will probably re-install the 11.04. 

thanks

---

### Post by dfacto on 2011-09-26
Its best to run 11.10 for too many reasons to list.

I'm so sick of gnome-3/unity bashing I could vomit.  Its linux. Install whatever window manager you want! The ubuntu version doesn't force you to use anything.  You could probably run the solaris window manager if you wanted.

Honestly, there is absolutely no reason for anyone to complain.  Everything you want is in the repos. And Im sure there are five-gazillion howtos too.

---

### Post by ChinaSailor on 2011-09-27
Noted... Thank you.

---

### Post by jonny on 2011-09-27
> **dfacto said:**
> I'm so sick of gnome-3/unity bashing I could vomit.I, for one, love Unity.  And Gnome 3 is brilliant, too.

Once you've adapted to either and learned a few keyboard shortcuts and touchpad gestures, the primary roles of a desktop shell - window management and program launching - need significantly fewer or less precise muscle movements than under Gnome 2, Windows 7 / XP or OS X.  As I see it, the only real disadvantage is that it's harder to discover installed software than with the older menu system.

And, if you want a modern desktop shell, 11.10 is the way to go rather than 11.04.  11.10 is much more polished and has dealt with many of the worst usability flaws from 11.04.

I'm not going back.

---

### Post by dfacto on 2011-09-27
> **jonny said:**
> I, for one, love Unity.  And Gnome 3 is brilliant, too.

Once you've adapted to either and learned a few keyboard shortcuts and touchpad gestures, the primary roles of a desktop shell - window management and program launching - need significantly fewer or less precise muscle movements than under Gnome 2, Windows 7 / XP or OS X.  As I see it, the only real disadvantage is that it's harder to discover installed software than with the older menu system.

And, if you want a modern desktop shell, 11.10 is the way to go rather than 11.04.  11.10 is much more polished and has dealt with many of the worst usability flaws from 11.04.

I'm not going back.

Hear, hear! (or in the parlance of our times: +1)

Honestly, I think all the bashing is just because people want to demonstrate how knowledgeable they are at terminal hacking or something. I code for a living and exclusively use vim to do it--I've never even used eclipse.  And I love shiny, pretty GUIs. Not mutually exclusive!
[http://xkcd.com/378/](http://xkcd.com/378/)

---

### Post by kiffykroker on 2011-09-27
I tried once again to get the touchpad to work with 11.04/MBA4,1 and this time - finally - success!

First I uncommented the copy line in the bcm5974 part of post-install-oneiric
```

    #sudo cp /lib/modules/$(uname -r)/extra/bcm5974.ko \
    #    /lib/modules/$(uname -r)/kernel/drivers/input/mouse/bcm5974.ko

```Now the mouse was totally frozen when logged in again, however, when i dropped in to a shell (Ctrl+ALt+F1) and then back to GUI, (Ctrl+Alt+F7), the touchpad was suddenly recognized and all multi touch gestures works.

I'm currently using touchegg and it's pretty good, however, it's a pain not being able to click with one finger and drag with the other to move objects and highlight text, is this a limitation to touchegg or my config?

Anyway my MBA4,1 finally has all the essential working on 11.04 and I couldn't be happier!

BIG thanks (again) dfacto!

---

### Post by dfacto on 2011-09-27
@kiffykroker Thanks; I uncommented those lines from the post-install-oneiric.sh.  I really didn't want to uncomment them but too many people reported this problem.

As far as gestures, I personally didn't feel touchegg was mature enough.  Using mtrack I have the most important gestures working:
one-finger tap-to-primary-click
two-finger tap-to-secondary-click
two-finger vertical scroll
two-finger horizontal scroll

---

### Post by kiffykroker on 2011-09-27
> **dfacto said:**
> @kiffykroker Thanks; I uncommented those lines from the post-install-oneiric.sh.  I really didn't want to uncomment them but too many people reported this problem.


It seems as those lines did cause the trackpad to freeze at first though? Do you think that might be a MBA4,1 or 11.04 issue? Not a problem for me since I know how to go around it at login but for someone else who runs the script might think it all failed when booting in to a frozen touchpad? Unless I'm the only one who experienced that issue?

> 
As far as gestures, I personally didn't feel touchegg was mature enough.  Using mtrack I have the most important gestures working:
one-finger tap-to-primary-click
two-finger tap-to-secondary-click
two-finger vertical scroll
two-finger horizontal scrollAgree, however, it's pretty cool to assign three and four finger swipes to various commands. At the moment I have three finger up to Compiz Expo and three finger down to Compiz Scale and right/left to switch workspace. Very much how OSX Lion handles those swipes - one of few features i miss from the odd month having to use it as my main os.

---

### Post by dfacto on 2011-09-27
It froze because you over-wrote an active driver.  That's why I don't like the copy approach.

Yeah--I really do like touchegg.  A couple more release cycles and it'll be my default choice.  The main problem I have with it now which I forgot(!) to mention is that it doesn't play nice with the new unity on 11.10.  But you're on 11.04 so this doesn't affect you.

---

### Post by kosumi68 on 2011-09-27
Thanks, Dr. dfacto, for your excellent work!

---

### Post by dfacto on 2011-09-27
hahah not Dr yet!  Ask again tomorrow after noon EDT! :-D

---

### Post by ChinaSailor on 2011-09-27
> **dfacto said:**
> Hear, hear! (or in the parlance of our times: +1)

Honestly, I think all the bashing is just because people want to demonstrate how knowledgeable they are at terminal hacking or something. I code for a living and exclusively use vim to do it--I've never even used eclipse.  And I love shiny, pretty GUIs. Not mutually exclusive!
[http://xkcd.com/378/](http://xkcd.com/378/)


People that code for a living (at least in the linux environment) probably do not use ubuntu, much less gnome-3. (Maybe on that 2nd notebook)

If your purpose is coding, you might try Ratpoison or *Xfce*. They are much more *Terminal* productive and lower resource environments.

But it would be rather senseless to spend a $1500 on a notebook with decent graphics, 
only to run a terminal.

---

### Post by dfacto on 2011-09-27
I code. I use Ubuntu. Why would resources be a problem?  I spent 1300.  I use gnome-terminal.

---

### Post by ChinaSailor on 2011-09-27
That's great dude...
I like ubuntu because of the deb package management and the driver support.

 > Why would resources be a problem?
Again, I think you are reading too much into the post...

---

### Post by User4519 on 2011-09-28
One praise, three questions.

First of all, this work is fantastic — you're a life saver and I hope you realize how many people you're touching in a good way doing what you're doing here! Thank you :)

Question 1) All of this debugging and fixing and whatnot. I have yet to actually install Ubuntu — been living (not to disgrunted, but with a rising urge to "return home") with Mac OS X since I bought the MBA a couple of months back now. Is the original "here's my script" post still up-to-date with all that's been accumulated fixes and knowledge wise? I have more than a dozen bookmarks from following this thread for when I finally get the time to install Ubuntu.

Question 2) Is this going into mainline before Oneiric launch? As in we won't have to run the post install script, it'll just work OOTB? Not that it's difficult to run the script, but this stuff needs to go help more people than the ones following this thread I think.

Question 3) Are you a doctor yet? :D

Cheers,
Daniel

---

### Post by steve on 2011-09-28
Has anyone had any luck on a MBA4,2 with the Oneiric Beta2 CD?

Following dfacto's instructions on the wiki ([https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)) the boot process just seems to hang after attempting to boot to the LiveCD. The 'nomodeset' tweak doesn't seem to help -- in fact, the boot process makes it farther without it. With 'nomodeset' the system hangs as soon as I hit 'Enter' -- no response and the superdrive stops spinning.

Without 'nomodeset' the LiveCD boots and I can select "Try Ubuntu" but the display fails (obviously). I can then CTRL+ALT+F1 to get a terminal, if someone has thoughts on how I could diagnose this further. Though, of course, without 'nomodeset' I just get the old '(EE) Screen found, but none have a usable configuration' in '/var/log/Xorg.0.log' once xorg attempts to use fbdev.

I've read all 39 pages of this thread but I didn't see anyone with this same issue.

Any and all thoughts appreciated!

---

### Post by ChinaSailor on 2011-09-28
> First of all, this work is fantastic — you're a life saver and I hope  you realize how many people you're touching in a good way doing what  you're doing here! Thank you :smile:Worth repeating, thank you.

---

### Post by ChinaSailor on 2011-09-28
> **steve said:**
> Has anyone had any luck on a MBA4,2 with the Oneiric Beta2 CD?

Following dfacto's instructions on the wiki ([https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)) the boot process just seems to hang after attempting to boot to the LiveCD. The 'nomodeset' tweak doesn't seem to help -- in fact, the boot process makes it farther without it. With 'nomodeset' the system hangs as soon as I hit 'Enter' -- no response and the superdrive stops spinning.

Without 'nomodeset' the LiveCD boots and I can select "Try Ubuntu" but the display fails (obviously). I can then CTRL+ALT+F1 to get a terminal, if someone has thoughts on how I could diagnose this further. Though, of course, without 'nomodeset' I just get the old '(EE) Screen found, but none have a usable configuration' in '/var/log/Xorg.0.log' once xorg attempts to use fbdev.

I've read all 39 pages of this thread but I didn't see anyone with this same issue.

Any and all thoughts appreciated!


Have you tried the "Alternate Install" Text Based (vga I think)...?
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by steve on 2011-09-28
Hmm. I haven't. But I think I'd be more confident were I able to boot a GUI from the LiveCD... unless of course this has become an impossibility with recent Oneiric releases. Particularly given that no one else in the thread has attempted this, I'll probably only stray that far as a last resort.

**Update:** If I choose the 'bootx64.efi' option from refit I can edit the grub config to include 'nomodeset' and it seems to do more work before hanging. Sadly, the screen is weirdly interlaced and I can't read any of the messages once it stops. Ha! But perhaps it's a step closer.

---

### Post by ChinaSailor on 2011-09-28
> **steve said:**
> Hmm. I haven't. But I think I'd be more confident were I able to boot a GUI from the LiveCD... unless of course this has become an impossibility with recent Oneiric releases. Particularly given that no one else in the thread has attempted this, I'll probably only stray that far as a last resort.


I don't know the actual differences between the regular cd and the alternate, 
it's not actually, "text" based, i.e.. like freeBSD, it is graphical. 

You will still need to F6 and then check the 'nomodeset.'
But there are a few other mba -> linux "how-to's" that recommend using the alt install cd.
(I've used it myself, a number of times)

---

### Post by steve on 2011-09-28
> **ChinaSailor said:**
> it is graphical. 

You will still need to F6 and then check the 'nomodeset.'

(I've used it myself, a number of times)

I've used the alt CD for previous installs. If all else fails, I'll give it a shot.

I'm not particularly anxious to get 11.10 on the MBA for now, though - I have another Ubuntu laptop that's just not as pretty. Current plan is: fight with Beta2 in an attempt to flush out the issue (if it's resolvable, others will benefit). If I fail, my next step is to wait for the 11.10 release.

Thanks for the tip, though.

---

### Post by dfacto on 2011-09-29
> **DanielBuus said:**
> One praise, three questions.

First of all, this work is fantastic — you're a life saver and I hope you realize how many people you're touching in a good way doing what you're doing here! Thank you :)

Question 1) All of this debugging and fixing and whatnot. I have yet to actually install Ubuntu — been living (not to disgrunted, but with a rising urge to "return home") with Mac OS X since I bought the MBA a couple of months back now. Is the original "here's my script" post still up-to-date with all that's been accumulated fixes and knowledge wise? I have more than a dozen bookmarks from following this thread for when I finally get the time to install Ubuntu.

Question 2) Is this going into mainline before Oneiric launch? As in we won't have to run the post install script, it'll just work OOTB? Not that it's difficult to run the script, but this stuff needs to go help more people than the ones following this thread I think.

Question 3) Are you a doctor yet? :D

Cheers,
Daniel


1) I updated [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2) so check here for everything you need.

2) All patches should be in place by 3.1.  Maybe Canonical will backport?  Not sure how this process works.

3) I am(!)...sort of.  My committee gave me some minor revisions which I need to work on.  I'd like to be able to say "Yes!" but I can't quite.  Anyway they all signed the little piece of paper that says "Yes!" and seemed to think it shouldn't take too much time to make the corrections. :)  Thanks for asking! :)

---

### Post by DigitalDJ on 2011-09-29
> **steve said:**
> Has anyone had any luck on a MBA4,2 with the Oneiric Beta2 CD?


Hi steve,

I used the Oneiric Beta 2 CD with my MBA4,2. I installed rEFIt, then dd'd the CD image to my USB drive.

dd if=ubuntu.iso of=/dev/disk1 bs=4m

After restarting, rEFIt detected my USB drive and I could boot to it. In fact, I didn't even need to use "nomodeset" to install Ubuntu...but it does give graphical errors. I found I HAD to use nomodeset (by editing the GRUB entry after install) to boot into the OS.

dfacto, thanks for the install script. Everything seems to work except my trackpad (MBA4,2, Oneiric Beta 2 (fully updated)).

After running the script, everything seems to be successful (except applying the color profile). After restarting, the trackpad does nothing, mouse does not move and buttons don't work. Any idea what's going on here?

Just an FYI, the color profile on my 13.3" MBA4,2 (Core i7) is Color LCD-00000610-0000-9CF0-0000-000004273C00.icc

---

### Post by poliva on 2011-09-29
> **DigitalDJ said:**
> After restarting, the trackpad does nothing, mouse does not move and buttons don't work. Any idea what's going on here?

I believe this is a problem with the latest xorg-edgers, should work if you remove it:

```
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by DigitalDJ on 2011-09-29
> **poliva said:**
> I believe this is a problem with the latest xorg-edgers, should work if you remove it:

```
sudo ppa-purge ppa:xorg-edgers/ppa
```

Gave that a shot and rebooted but still no go. :(

---

### Post by DigitalDJ on 2011-09-30
I just did a new clean install of Oneiric Beta 2, after install I installed all the packges I could via Update Manager then rebooted so I'd have the newer kernel. Trackpad works at this stage but obviously no gestures. 

After running the script and rebooting, the trackpad is completely non-functional.

I'd love to get this working, but in terms of the trackpad, I have no idea where to start.

EDIT: I re-ran the script after already running it and magically the trackpad now works. I had to go back through some of the config files to delete some of the duplicate text though. However now that I've re-run the script, my desktop seems to be offset. I can get 1440x900 resolution but part of my desktop area is black :/

EDIT2: Apparently the desktop offset is a recently introduced bug. Trackpad works (although no idea why I needed to run the script twice) and fixed my desktop. Hooray.

---

### Post by dfacto on 2011-10-02
"they" already have.  things should make it on or before kernel 3.1.0.

i would recommend using the alternate cd.  early in this thread i explained the difference. although, i have used both without problems.  on other macbooks it can cause serious problems if you dont use the mac alternate.

---

### Post by dentifrice on 2011-10-06
Hey guys,  does the SuperDrive work under GNU/Linux, or is it restricted to MacOS X like the previous version? I've read superdrive compatibility was improved to allow the new MacMini to use it for instance, but does that mean non OS X systems can power it enough?

---

### Post by diafygi on 2011-10-07
Hey all, so I followed the instructions from the [community wiki]("https://help.ubuntu.com/community/MacBookAir4-2"). And after I ran the fix-i915.sh script and rebooted, the login screen came up normally at full resolution (yay!). However, when I logged in only the desktop background and mouse appeared (the mouse moved normally).

After about 60 seconds I got an [error report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/870092") that compiz crashed, then about 5 seconds later, an [error report]("https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/850893") that 2d-Unity crashed.

The way I got around this was to select Unity 2d at the login screen (from the dropdown gear icon by your username/password). I guess this prevents Compiz from loading. My desktop and unity panel appear normally now. However, I still get crash reports after 60 sec that compiz and unity-2d have crashed. I don't know why is says unity-2d crashed, because the unity panel still works fine.

Anyway, for people who are stuck at the blank desktop background, use the 2d unity option at the login screen (you can select it from the dropdown on the gear icon by your username/password).

---

### Post by dfacto on 2011-10-07
The superdrive works; you need to plug it in and restart.  No plug-and-play as far as I know.  *shrugs*

Compiz still gives me hiccups on a regular basis.  I use this script to restart it (which works from a TTY, ie, ctrl-alt-F1)

[http://almostsure.com/mba42/kick-unity](http://almostsure.com/mba42/kick-unity)

---

### Post by diafygi on 2011-10-07
So I have a USB mouse I'd like to use with the mackbook air 4,2. However, the scroll wheel on the mouse is reversed, just like the trackpad. I'm assuming that is because the [dotXmodmap config]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75") in post-install-oneiric.sh changed the pointer settings.

Is there any way to have normal scrolling for the external mouse, but reversed scrolling for the trackpad?

---

### Post by DrSchiwago on 2011-10-08
Hi there,
may I ask about experiences with battery life when running ubuntu?
Best,
DrSchiwago

---

### Post by poliva on 2011-10-09
> **DrSchiwago said:**
> may I ask about experiences with battery life when running ubuntu?

In my case it last between 3 to 6 hours depending on usage, I'd say around 5 hours if you just do normal browsing + email activity (no flash, video playback, compiling, etc...).

---

### Post by Murphy2712 on 2011-10-09
> **diafygi said:**
> when I logged in only the desktop background and mouse appeared (the mouse moved normally).

The way I got around this was to select Unity 2d at the login screen (from the dropdown gear icon by your username/password).

I got into that issue and unity-2d works, thanks!

Anyone knows a fix for low sound?
(volume is already max and nothing muted in alsamixer).
My alsa conf is:
options snd-hda-intel model=mba32

Thanks!

Edit: headphones works as expected.

---

### Post by jebus_beler on 2011-10-12
> **poliva said:**
> In my case it last between 3 to 6 hours depending on usage, I'd say around 5 hours if you just do normal browsing + email activity (no flash, video playback, compiling, etc...).

Hi,

I just got a new macbook air 13" and I was originally planning to just wipe OS X in favor of ubuntu.  On second thought, I'm vaguely considering keeping OS X around as a backup but was hoping to ask some questions to help me make up my mind:

- How does the power usage compare with OS X.  This is the first time I'm using it but I seem to be getting a very decent 7+ hr battery life on OS X even on wifi and doing some work (installing apps, etc...).  The system claims its using 890 mA at 7884 mV.  Can anyone get similar figures for linux (when the system is idling)?  I think the idle power usage is the easiest to compare and gives a good baseline for how power efficient the system is.

- How fast/stable is suspend/resume.  My impression from browsing the thread is that this works well but a confirmation would be appreciated.

- Besides iffy touchpad support are there any other issues with linux on the MBA?  On my old MBP linux had problems identifying the battery percentage and would often report an empty battery while this was definitely not the case.

- How much more painful is it to keep an OS X install around?

- Has anyone tried installing linux on an external SD card.  From what I can tell in OS X's system profiler the reader is on a USB 2 bus so its not gonna be very fast but there are 128 GB SDXC cards out there so using it could greatly boost the system's capacity.

thanks!

---

### Post by jonny on 2011-10-12
> **jebus_beler said:**
> - How does the power usage compare with OS X.  This is the first time I'm using it but I seem to be getting a very decent 7+ hr battery life on OS X even on wifi and doing some work (installing apps, etc...).  The system claims its using 890 mA at 7884 mV.  Can anyone get similar figures for linux (when the system is idling)?  I think the idle power usage is the easiest to compare and gives a good baseline for how power efficient the system is.
I get significantly worse battery life (c25%) on Ubuntu than on OS X.  I've added some power optimisations to my boot parameters (these are described earlier in the thread), and my idle power usage with a fairly dim screen is around 1000mA.  However, the Air has pretty good battery life and the power supply is pretty portable, so I'm not too unhappy.

> **jebus_beler said:**
> - How fast/stable is suspend/resume.  My impression from browsing the thread is that this works well but a confirmation would be appreciated.
It's pukka - slightly better than OS X, in my experience.  I find that around 10% of resumes in OS X lead to an unresponsive touchpad - although this is easily sorted by opening and closing the lid.  Suspend / resume has never failed for me under Ubuntu.

> **jebus_beler said:**
> - Besides iffy touchpad support are there any other issues with linux on the MBA?  On my old MBP linux had problems identifying the battery percentage and would often report an empty battery while this was definitely not the case.
Touchpad support isn't iffy at all.  It's a little more sensitive to lightweight taps than under OS X, but, once you adapt your muscle memory, it's perfect.  The only real quirk for me is that I can't work out how to remap the keyboard backlight keys, so I need a user-hostile root-user-only command line hack to turn the light on.

A secondary issue is that dfacto's keyboard mapping isn't quite right for a UK keyboard: the media keys and a few symbols, most critically the backtick ` character, are incorrectly mapped.  I have a revised mapping file if anyone's interested, but it only works under GUI applications - a ctrl-alt-F1 terminal session leads me frantically hunting for the right buttons.  It's on my to-do list.
> **jebus_beler said:**
> - How much more painful is it to keep an OS X install around?
Just a few seconds extra on boot when REFIt kicks in - but I hardly ever restart, anyway - and a few lost GB off the SSD.  OS X does have a couple of decent programs that make it useful to have around.  My kids particularly like iMovie, for example.
> **jebus_beler said:**
> - Has anyone tried installing linux on an external SD card.  From what I can tell in OS X's system profiler the reader is on a USB 2 bus so its not gonna be very fast but there are 128 GB SDXC cards out there so using it could greatly boost the system's capacity.
Not tried, but, as you say, it would be slow; an SD card hanging out of the slot might offend the Apple aesthetic, too.  I imagine it would work, though, as REFIt always offers to attempt to boot from any FAT32 SD card that's present at startup.

---

### Post by jebus_beler on 2011-10-12
Hi Jonny,

thanks a lot for all the info!

> **jonny said:**
> I get significantly worse battery life (c25%) on Ubuntu than on OS X.  I've added some power optimisations to my boot parameters (these are described earlier in the thread), and my idle power usage with a fairly dim screen is around 1000mA.  However, the Air has pretty good battery life and the power supply is pretty portable, so I'm not too unhappy.

That's manageable but kinda lame...will play around with it once installed and see if there's anyway to get a comparable battery life.  That's one reason to keep OS X around -- to have a good baseline for how the machine can perform.

> **jonny said:**
> 
It's pukka - slightly better than OS X, in my experience.  I find that around 10% of resumes in OS X lead to an unresponsive touchpad - although this is easily sorted by opening and closing the lid.  Suspend / resume has never failed for me under Ubuntu.

Touchpad support isn't iffy at all.  It's a little more sensitive to lightweight taps than under OS X, but, once you adapt your muscle memory, it's perfect. 


So far I've had no such problems in OS X (insensitive touchpad) but its great to hear that its so good on ubuntu.  Suspend/resume was one of the issues I had when running my MBP on linux (admittedly quite some time ago).  A jittery trackpad was the other main issue (and vastly decreased battery life).  I really don't need multitouch and all that stuff (at least I don't think I do but maybe its cause I haven't learned to play with it) but on my MBP I couldn't reproduce the balance between sensitivity and smoothness that OS X seemed to have.

---

### Post by poliva on 2011-10-12
> **jonny said:**
> The only real quirk for me is that I can't work out how to remap the keyboard backlight keys, so I need a user-hostile root-user-only command line hack to turn the light on.
weird, it's working for me with Fn + F5/F6 to change the keyboard backlight, and haven't done anything special to make it work.

---

### Post by diafygi on 2011-10-12
Help! I'm stuck in nomodeset after kernel update!

I was using Oneiric Beta2 (see [my post]("http://ubuntuforums.org/showpost.php?p=11319223&postcount=395")), and the Update manager updated the kernel (to 3.0.0.12.14). When I restarted, I couldn't boot into the login screen without adding "nomodeset" to the grub launch (from [step 17]("http://ubuntuforums.org/showpost.php?p=11091959&postcount=36")).

I tried running i915-fix.sh from [dfacto]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75"), but it asks for "Assume -R". What does this mean? I've tried both the yes and no, but both still crash Ubuntu before the login screen.

Can anyone help getting back to normal?

---

### Post by dfacto on 2011-10-12
> **diafygi said:**
> Help! I'm stuck in nomodeset after kernel update!

I was using Oneiric Beta2 (see [my post]("http://ubuntuforums.org/showpost.php?p=11319223&postcount=395")), and the Update manager updated the kernel (to 3.0.0.12.14). When I restarted, I couldn't boot into the login screen without adding "nomodeset" to the grub launch (from [step 17]("http://ubuntuforums.org/showpost.php?p=11091959&postcount=36")).

I tried running i915-fix.sh from [dfacto]("http://ubuntuforums.org/showpost.php?p=11119553&postcount=75"), but it asks for "Assume -R". What does this mean? I've tried both the yes and no, but both still crash Ubuntu before the login screen.

Can anyone help getting back to normal?

Regarding the assume -R thing: rm -fr mba4-tmp/linux-3.0.0 (or whatever the directory is I can't remember off the top of my head)

---

### Post by jonny on 2011-10-12
Now that support for the MacBook Air 4,2 and 4,1 seems to be reasonably stable, I've [updated the wiki](https://help.ubuntu.com/community/MacBookAir4-2#preview) with reasonably detailed and, hopefully, novice-friendly instructions.  If anyone can see any obvious howlers, please correct my efforts or let me know so that I can make the requisite changes.

---

### Post by dfacto on 2011-10-12
Way-to-go Jonny!  Very nice!  Thanks!!!!

---

### Post by dfacto on 2011-10-13
Does isight now work out-of-the-box?  I think it probably still needs the steps in the script, no?

sensors work from applesmc driver (out-of-the-box).  To format sensor data requires lm-sensors. I updated the wiki to reflect this.

---

### Post by jonny on 2011-10-13
> **dfacto said:**
> Does isight now work out-of-the-box?  I think it probably still needs the steps in the script, no?
It works from a live USB session for me.

---

### Post by dfacto on 2011-10-13
> **jonny said:**
> It works from a live USB session for me.

post-install-oneiric.sh updated.

---

### Post by jebus_beler on 2011-10-13
I'm having problems installing the final release of oneiric on my 2011 MBA 13".  I tried following the instructions here:

[http://ubuntuforums.org/showpost.php?p=11091959&postcount=36](http://ubuntuforums.org/showpost.php?p=11091959&postcount=36)

with some modifications: namely, the nomodeset option is in a dropdown window so I just selected it and used "install ubuntu". I get a few steps through the graphical install but when i try to manually partition (creating a root and a swap partition and leaving the OS X partition untouched) and then hit "Install Now".  I then get this spinning cursor and nothing happens...for a long time(and the CD is not spinning so its not installing anything).  I thought it might be formatting but it can't take that long.

Need to head out so might just shut it down and try again later but was wondering if anyone might know what the problem is.  In the link above I noticed it suggested loading gparted and partitioning before hitting "Install Ubuntu".  I didn't see this option so just skipped that step...is that perhaps the problem?

Btw I'm installing from a CD since i have a superdrive.

thanks!

---

### Post by diafygi on 2011-10-13
> **dfacto said:**
> post-install-oneiric.sh updated.

I'm now getting an error at line 404:
```

$sudo ./post-install-oneiric.sh

...<snip>...

Comment=Load custom .Xmodmap.
Making xmodmap run after resume (custom keys).
./post-install-oneiric.sh: line 404: syntax error near unexpected token `fi'
./post-install-oneiric.sh: line 404: `fi'

```

EDIT:Added more output text.

---

### Post by hueythecat on 2011-10-13
Hey All

Has anyone with a mba 4,1 installed the now live 11.10 and run post-install.sh script

If so please advise on what's working/not etc.

---

### Post by jebus_beler on 2011-10-13
Ok, so apparently its important to use the "Try ubuntu without installing" option and run gparted _before_ running the installer.  So that problem is solved...

But now i made a second mistake.  I forgot to change the boot partition from the installer partition window and it installed grub on the drive /dev/sda rather than on my linux partition /dev/sda5.  I went back and re-installed, selecting /dev/sda5 as the boot partition and now I think grub is installed on both the disk and the partition.

This of course meant rEFIT wouldn't touch the disk so I followed dfacto's instructions here:

[http://ubuntuforums.org/showpost.php?p=11215214&postcount=185](http://ubuntuforums.org/showpost.php?p=11215214&postcount=185)

which let rEFIT happily sync the partitions.  But it still presents me with two penguins, one for sda and one for sda5 (presumably).  Trying to boot on either one gives me the gray background with a faded penguin for a while and then a blinking cursor.  I tried rebooting/shutting down several times to no avail.  Trying to follow the instructions here:

[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

(which i found via some links from the mactel wiki) doesn't work because the instructinons seem to apply to an old version of grub.  

So instead I just re-installed everything, including grub but I still get the blinking cursor.  I've actually cycled through all of the above a few times but nothing changes.  I'm guessing having an extra grub partition on sda is messing things up but I don't know how to remove it.

Strangely on the last go I noticed that refit suggested updating my MBR in a very weird way.  The MBR has the EFI partition, HFS partition, the boot recovery, and my linux root with the latter *'ed -- i.e. bootable.  rEFIT wants to replace the linux root with the linux swap partition (so in its new MBR the linux root doesn't appear) and wants to make the HFS partition bootable.  Does this make any sense?

Does anyone have any suggestions as to how to proceed as I'm somewhat at wit's end?

---

### Post by diafygi on 2011-10-13
> **hueythecat said:**
> Hey All

Has anyone with a mba 4,1 installed the now live 11.10 and run post-install.sh script

If so please advise on what's working/not etc.

I installed Oneiric on my 4,2 today according to the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2"), but I am getting an error in post-install-oneiric.sh on line 404 (see my [post]("http://ubuntuforums.org/showpost.php?p=11338694&postcount=413")). So far, still having to add "nomodeset" to Grub in order to get to the login screen.

---

### Post by hueythecat on 2011-10-13
Cheers. 
Really need some feedback from other 4,1 owners. 
If you look at earlier posts the 4,1 doesn't get the same results as the 4,2 does from post-install.sh

---

### Post by Murphy2712 on 2011-10-13
According to the wiki, the multitouch pad can be enabled using the "Mouse and Touchpad" application.

But when I launch this application I only have a "Mouse" tab, nothing about multitouch.

Is there a package to install to have the touchpad/more options?

---

### Post by jebus_beler on 2011-10-14
> **hueythecat said:**
> My apologies if I came across as vague.

After install & resyncing the MBR my system would not make it to grub - it just went to a black screen with flashing cursor forever.

At some stage I'm guessing I installed grub to the wrong partition. And failed from that point forwards.

After doing a total rebuild from scratch I've successfully installed.

On a side note (if you manage to delete your Lion recovery partition) - The internet recovery ONLY works if your wifi is WPA/WPA2 encrypted. So if your connected via open wifi it appears like its taking forever instead of informing you of the latter.

Hi Huey,

I think I find myself in the same position as you.  How exactly did you resolve this?  When you say rebuild from scratch I'm not sure what you mean.  How did you wipe grub from the wrong partitions?  You didn't have to wipe the whole disk did you (please tell me you didn't)?  

Thanks

---

### Post by dfacto on 2011-10-14
@hueythecat,jebus I believe there was some discussion already in this thread about reinstalls as I had to go through this process.  Have looked at this?

---

### Post by jebus_beler on 2011-10-14
> **dfacto said:**
> @hueythecat,jebus I believe there was some discussion already in this thread about reinstalls as I had to go through this process.  Have looked at this?

Hi dfacto,

Actually the post of hueythecat's that  I responded to is such a very old discussion but i was looking for more details about what he did since its not clear from his post.  I did a search on the thread for grub related stuff and his was the main relevant post i found but I haven't tried reading all 42 pages...  I will look through the thread more but since I found huey's post I was hoping he could tell me what he did (since he seemed to have the same problem).   If you're referring to your gdisk post I tried that and it let rEFIT resync but didn't help with booting...

thanks!

---

### Post by jebus_beler on 2011-10-14
I've been going through the full thread trying to find relevant advice but haven't yet hit it.  I'm guessing my problem comes from having grub installed on /dev/sda (instead of /dev/sda5) so was thinking of trying to remove it using dd:

# dd if=/dev/null of=/dev/sda bs=446 count=1

a command I found from:

[http://linux.koolsolutions.com/2009/06/08/howto-how-to-erase-un-install-grub-from-mbr-to-restore-windowsdos-bootloader/](http://linux.koolsolutions.com/2009/06/08/howto-how-to-erase-un-install-grub-from-mbr-to-restore-windowsdos-bootloader/)

But since mac's use EFI and have weird setup I'm not sure the above command is correct.  Anyone know if this is a Good or Bad Idea (tm)?

Ideally I'd like to avoid wiping my OS X install since I've already spent some time installing some programs on it (I had to get some work done while trying to get linux installed ;->).

thanks!

---

### Post by dfacto on 2011-10-14
I would not do that.  That kind of dd magic just seems like a recipe for disaster, although its quite possible that it would work.

Have you read this thread?
[http://ubuntuforums.org/showthread.php?t=1849373](http://ubuntuforums.org/showthread.php?t=1849373)

---

### Post by jebus_beler on 2011-10-14
> **dfacto said:**
> I would not do that.  That kind of dd magic just seems like a recipe for disaster, although its quite possible that it would work.

Have you read this thread?
[http://ubuntuforums.org/showthread.php?t=1849373](http://ubuntuforums.org/showthread.php?t=1849373)

Thanks, that's very useful but it hasn't solved my problem :-(  I created a usb-boot for faster "livecd" access and chrooted but for some reason aptitude is not installed and apt-get behaves strangely.  It let me uninstall grub but not reinstall it.  So I just did another install (with a usb-stick and the fast ssd this is not even that painful -- its probably the 4th time I've tried).  

Unfortunately this got me nowhere.  After reinstalling grub gave me a giberrish screen (ASCII chars) and then when I rebooted again just the blinking cursor.  refit wouldn't touch the MBR so I went back to OS X and did the whole gdisk thing. Strangely, and this should somehow be my problem, when I go back to refit after created a hMBR in gdisk refit wants to overwrite my MBR.  It shoes the hMBR which I created with a bootable 4th partition (/dev/sda5) but tells me it must be updated.  It wants to update it with an MBR with /dev/sda4 (my swap) instead of /dev/sda5 (my root).  Morevoer it wants to set the HFS+ (OS X main) partition as bootable. This must somehow be related to my problem but I don't understand why.  Will try reinstalling refit and see if that helps...

Otherwise I'm kind of going in circles...re-installing ubuntu doesn't seem to be changing anything.

---

### Post by jebus_beler on 2011-10-14
So I re-installed switching my swap and root partition so now root is /dev/sda4 and swap /dev/sda5.  When I run gdisk and then refit the latter gives me a more sane result...it just keeps the hMBR I setup in gdisk.  So that seems like some progress.  But I still get the blinking cursor of frustration and still have two penguins on my refit screen.  Do I need to try re-installing grub again?

---

### Post by jebus_beler on 2011-10-14
Re-installed grub (purge/installed packages), ran gdisk and still this blinking cursor.  I'm beginning to think it will never go away...

Any ideas?

---

### Post by mike909 on 2011-10-15
> **diafygi said:**
> I installed Oneiric on my 4,2 today according to the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2"), but I am getting an error in post-install-oneiric.sh on line 404 (see my [post]("http://ubuntuforums.org/showpost.php?p=11338694&postcount=413"))...
Same here. Fresh install Oneric (Official release), mba4,2 13" getting > Making xmodmap run after resume (custom keys).
./post-install-oneiric.sh: line 404: syntax error near unexpected token `fi'
./post-install-oneiric.sh: line 404: `fi'

---

### Post by charlies8282 on 2011-10-15
> **mike909 said:**
> Same here. Fresh install Oneric (Official release), mba4,2 13" getting
 
Same also here. Oneric official amd 64 desktop install cd on mba 4,2 13"

---

### Post by jebus_beler on 2011-10-15
Ok, I managed to get grub to work!!!

I tried the instructions on this thread which probably got me part way but ultimately didn't work:

[http://ubuntuforums.org/showthread.php?t=1849373](http://ubuntuforums.org/showthread.php?t=1849373)

What finally worked was creating a BIOS grub partition as explained here:

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

Thanks a lot dfacto and srs5694!

To give more details:

I rebooted into OS X, started gdisk and deleted my linux root and swap partition.  I then created just a BIOSgrub partition of 128 Mb size as explained in the second link above.  I then booted from the live-install CD and used gparted to create a root and a swap partition.  Then I continued installing on the live-install as normal and, at the ubuntu installer partition screen I chose /dev/sda as my grub partition (again as in the second link above).  When I rebooted I tried refit gptsync but it wouldn't touch the partition.  I did _not_ run gdisk to fix this but just tried booting into linux (there should only be one penguin on the refit menu) and that just gave me the gray penguin screen.  I rebooted and tried again and this time I got the grub menu!!

There's still the little issue that my MBR in refit is wrong (i.e. not synced and refit won't touch it) and I haven't blessed the disk.  I don't know whether I should try to fix these things as I now have a booting install and don't wanna risk messing that up.  Anyone know if there's a risk or reason to fix my MBR or bless if I can boot?

I think it would be good to link to srs5694's page from the wiki.  If no one else wants to do this I can later once I've gotten my system up.

I'm on fighting with the install script...

---

### Post by jebus_beler on 2011-10-15
> **charlies8282 said:**
> Same also here. Oneric official amd 64 desktop install cd on mba 4,2 13"

Yeah I'm having the same problem.  But even on the way to this error the script is giving all sorts of weird errors.  Even though my laptop (13" macbook 4,2) is identified as a MacBookAir4,2 the script is giving a weird error, not accepting it.  It then gives a few other (non-fatal) errors before giving the final error quoted by charlies and mike.  Also, after the script ran and failed my fans just went crazy and stayed that way until I shut down.  Anyone else have the same?

I think I'm just gonna try to manually redo what the script does to see what's causing the problem.

---

### Post by jebus_beler on 2011-10-15
Just a warning to other users...the post-oneiric-install.sh script really seems to have messed up my install.  I'm not completely sure of this since I didn't do much with the install before that but now the system hangs when I try sudo or even some other commands the command line just hangs and the ubuntu package updater is warning that packages are broken, etc...

---

### Post by dfacto on 2011-10-15
@mike909 bug fixed thanks.

@jebus_beler Try it again.  Probably it just never made it to the step of updating the macfanctld config.  Its always a good to run each block manually so you can verify it makes sense. I run my own script this way.

---

### Post by struanhmb on 2011-10-15
I'm really very grateful for all the work on MacBook Air 4.2/Ubuntu compatibility, particularly by the author of post-install-oneiric.sh - thanks! I've re-installed Ubuntu on my MacBook Air 4.2 (July 2011 model), and re-run the post-install-oneiric.sh script, about 6 times since yesterday (as I get to grips with partitioning my MacBook and so on)! The changes made to this script in recent hours did seem to fix a bug I had yesterday with 'if false' missing a 'then'. That said, I'm having a problem today I don't think I had yesterday.

After running the script today (on a fresh Ubuntu install) everything seemed to complete without errors, but on reboot I found that the trackpad didn't work, with Xorg.log reporting:

```
[   583.457] (II) LoadModule: "mtrack"
[   583.457] (II) Loading /usr/lib/xorg/modules/input/mtrack_drv.so
[   583.457] (II) Module mtrack: vendor="X.Org Foundation"
[   583.457] (II) UnloadModule: "mtrack"
[   583.458] (II) Unloading mtrack
[   583.458] (EE) Failed to load module "mtrack" (module requirement mismatch, 0)
[   583.458] (EE) No input driver matching `mtrack'

```
Googling this, I found advice to run these commands:

```
sudo apt-add-repository ppa:xorg-edgers
sudo apt-get update
sudo apt-get upgrade

```
I'm not sure this was a good idea. This did install a range of new xorg packages, and afterwards the mtrack errors went away and the trackpad started working. But now I can't log into Ubuntu from the login screen unless I select Ubuntu 2D (from the desktop choice menu). With the original "Ubuntu" choice of login, I get the coloured screen (and a mouse pointer I can move) but it no longer loads the Unity desktop.

Not sure what's the best way to proceed, but once again thanks very much. I'm very pleased indeed to have been able to get this far!

---

### Post by jebus_beler on 2011-10-15
Hi dfacto,

First thanks again for the great script and all the other help.  You've really done a lot to get so many people up and running with linux on their Airs!  Even as a script to just follow its really helpful.  I actually reinstalled (again!) and ran the script and it seemed to work fine though I noticed when it tries to download the linux-image-3.0.0... apt-get actually tries to download a meta-package called "linux" instead that seems to contain a lot more stuff than is actually used (I'll put some output at the end of this post).  Oh, and another point: it might be good to note (in the wiki) that users should enable the source repositories before running the script.

But since having everything working would just be too much to ask for compiz and Unity 3d now don't work and i think its somehow related to some touchpad library.  When I try to start unity after a fresh install and running post-oneiric-install.sh I get the following error (output of dmesg):

compiz[1641]: segfault at 5f3f14007c00 ip 00007f0817961d30 sp 00007ffff20affa8 error 4 in libutouch-geis.so.1.2.0[7f0817957000+17000]

Anyone else get this?  Unity 3d doesn't work (just get a background screen and a mouse but no other window-manager stuff) but unity 2d seems to work fine.

A small, unrelated question, is the post-oneiric-install supposed to enable some kind of touchpad-disable while typing because my touchpad is still quite enabled and its a bit infuriating ;->

Here's the output of the install script when it tries to install linux-image-3.0.0... (which I think is installed by default anyway):

Building hid-apple (keyboard driver).
Reading package lists... Done
Building dependency tree
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-3.0.0-12-generic'
The following NEW packages will be installed:
  asciidoc binutils-dev docbook-dsssl docbook-utils docbook-xsl gawk jadetex kernel-wedge libdw-dev libdw1
  libelf-dev libosp5 libostyle1c2 libsgmls-perl libsigsegv2 libsp1c2 libxml2-utils luatex lynx lynx-cur
  makedumpfile openjade sgmlspl sharutils sp tex-common texlive-base texlive-binaries texlive-common
  texlive-doc-base texlive-fonts-recommended texlive-latex-base texlive-latex-recommended tipa transfig xmlto
  xsltproc

---

### Post by jebus_beler on 2011-10-15
> **struanhmb said:**
> 
```
sudo apt-add-repository ppa:xorg-edgers
sudo apt-get update
sudo apt-get upgrade

```I'm not sure this was a good idea. This did install a range of new xorg packages, and afterwards the mtrack errors went away and the trackpad starteecd working. But now I can't log into Ubuntu from the login screen unless I select Ubuntu 2D (from the desktop choice menu). With the original "Ubuntu" choice of login, I get the coloured screen (and a mouse pointer I can move) but it no longer loads the Unity desktop.

Not sure what's the best way to proceed, but once again thanks very much. I'm very pleased indeed to have been able to get this far!

Oops...just missed this post while writing mine.  Yes indeed I get the same but in my case I guess I accepted some option from the post-oneiric script that you didn't because my trackpad  worked immediately (though it does a few annoying things like having "natural" scrolling and no three finger tap and most infuriatingly is not disabled when I type but I think these are all configurable things) but my Unity 3d didn't.

I think the problem is compiz and libutouch-geis (not sure what that is).  So maybe if you install kde or gnome 3 and use them instead (assuming the latter doesn't use compiz) then you can at least have a 3d system.  Haven't tried myself.

---

### Post by jebus_beler on 2011-10-15
Oh, I noticed this on my last install when I did the manual install and I see its still there as an issue now.  Dispad can't install because it requires libconfuse0 which requires libconfuse-common.  The install script actually leaves your package manager in a broken state which has to be repaired by launching the software manager or synaptic.  This might also be borking later stages of the install.

Btw I noticed three finger tap does work but firefox was just ignoring middle-button paste for some reason.  For disable-touchpad-while-typing I seem to remember (back from linux on my MBP) that this was done by pommed which I noticed is no longer installed by the post-oneiric-instal.sh.  Is there some reason why pommed is commented out in the dpkg line?

---

### Post by jebus_beler on 2011-10-15
> **jebus_beler said:**
> 
compiz[1641]: segfault at 5f3f14007c00 ip 00007f0817961d30 sp 00007ffff20affa8 error 4 in libutouch-geis.so.1.2.0[7f0817957000+17000]



Actually Unity-2d-launch gives a similar error yet manages to start nonetheless so maybe libutouch ins't the problem.

I have to say I'm finding quite a few issues with oneiric that are probably not even MBA related (will post on another thread).  When I try to connect to my WPA1 network at home it fails and I get some error of a hung process in the kernel log.  But any attempt to access the network afterwards, even via ethernet, just hangs though the rest of the system is responsive.  So e.g. typing "ifconfig eth0" just hangs at the terminal and not even ctrl-c will get it back.  I'll post some log messages in another thread but just wanted to ask if anyone was seeing anything similar?

---

### Post by jebus_beler on 2011-10-16
Very strangely unity 3d worked once for me but has not worked again since then.  I thought it might be related to my strange networking issues but those turned out to somehow be related to my router.  A router reboot strangely fixed those but I'm still stuck in unity 2d.  I installed gnome 3 and it seems to work (if you can say that about it) so its not a 3d issue but unity specific.

And for those, like myself, who are not big unity fans: give gnome 3 a shot and you'll see that canonical made the right choice ditching gnome!

---

### Post by hueythecat on 2011-10-16
> **jebus_beler said:**
> Hi Huey,

I think I find myself in the same position as you.  How exactly did you resolve this?  When you say rebuild from scratch I'm not sure what you mean.  How did you wipe grub from the wrong partitions?  You didn't have to wipe the whole disk did you (please tell me you didn't)?  

Thanks

That was the result of not reading the post about gedit earlier in this forum. This would have sorted if I read it first.
In short you create a new MBR and redefine your linux partition as type 83 and bootable. Find the post and read it. It will resolve.

---

### Post by Daegalus on 2011-10-16
So, I managed to get everything working with a lot of trickyness and I had to wipe my windows parition due to bad MBRing.

It all works, but I have a few comments and a problem.

1. You should use HTTP for the github urls because I had a lot of problem with git not cloning because it for some reason couldnt connect or resolve if it used https

2. You should add flags or parameters to only run parts of the script. Many cases I needed to run the last few parts to get it. SO I opened up the script and ran them manually in a terminal, but it would be nice to do it from the command.

Now for my problem. I can't get the mtrack driver working. As soon as I add the config for it in the xorg.conf, my touchpad doesnt work, at all, nothing. If I use the default (aka no xorg.conf) it works marvelously, but for some reason, I can click+move the mouse.

What I want to do is if I click, then use another finger to move the mouse, it doesn't. It immediately activates the 2 button gesture for scrolling, and the mouse just gets stuck.

So in a lot of places where I need to Click+Drag, I can't and the 3 finger drag doesn't work.

Any ideas how to get this working?

Other than that, everything works marvelously. I even have keyboard backlight working out of the box.

Though I also noticed that the Wifi sometimes stops working, and I have to reconnect to my router to get it to connect again. But I don't know if thats a problem on Linux side or my Router, but OSX and Win work without problems.

Thank you for your efforts on the script. It really helped.

---

### Post by jebus_beler on 2011-10-17
> **hueythecat said:**
> That was the result of not reading the post about gedit earlier in this forum. This would have sorted if I read it first.
In short you create a new MBR and redefine your linux partition as type 83 and bootable. Find the post and read it. It will resolve.

@huey:  actually sadly my case was a lot more complicated.  running dfacto's gdisk instructions and reinstalling grub multiple times didn't help.  Ultimately I had to follow srs5694's instructions and create a new BIOSGRUB partition as explained here:

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

When I have a moment I'll try to modify the wiki with some pointers to this.

@Daegalus: is unity 3d working for you?  for some reason it won't start on my machine (but unity 2d does).

---

### Post by jonny on 2011-10-17
I'm not close enough to the inner workings of the post-install script to answer all of the questions that have been raised in the past few days, but here are a few hints that might help you to start looking for solutions:

 - Unity 3D works perfectly on my 13" Air; I definitely don't need to resort to a 2D login.  However, I found that xorg-edgers killed my 3D desktop, so I reverted to the stock display with just the screen resolution patch.  If you haven't already discovered it, ppa-purge is the easiest tool to remove all traces of a ppa from your system

 - I don't use the mtrack touchpad driver, but stick to the default multitouch driver.  It works perfectly for me, with the only problem being that I can't use a third finger to continue a drag operation if I reach the edge of the touchpad.  I deal with this limitation by setting high acceleration in the mouse pointer settings, so, if I reach the edge of the touchpad, I simply reverse slowly and then move forward rapidly to get the pointer to the place I need without releasing my finger

 - I'm not in fornt of my Air now, but I'm fairly sure that I don't have an xorg.conf file; I simply rely on automatic configuration.

---

### Post by dfacto on 2011-10-17
@jebus_beler Thanks for updating the wiki.  It really would be nice to have some documentation on how to deal with all the possible reasons (and fixes) for problems booting Oneiric.

If I find some freetime, I will do a reinstall to see if I can recreate the problem.  Did you deviate from my install steps in any way?

---

### Post by hueythecat on 2011-10-17
4,1 update

Just ran post-install again with release build of 11.10

No errors during script execution
At login the system only serves up the purple wallpaper and no Unity - If I reboot and choose Unity 2D no problems.

Bluetooth is running
Trackpad with multi finger support appears functional
 
@dfacto Should I remove xorg-edgers to "try" and address the Unity 3D issue.
If so How do I do this.

---

### Post by dfacto on 2011-10-17
Yes--remove edgers.  The answer is already in this thread.  Search this thread (post #390).

---

### Post by hueythecat on 2011-10-17
On a side note while thats running.

After installing restricted extras when testing with banshee - the audio appears to buffer and play but no sound.

I've checked alsamixer volume and gui volume.
Is there a specific device that should be selected in the sound prefs?(there are lots)

---

### Post by hueythecat on 2011-10-17
RATS.

After removing ppa:xorg-edgers trackpad is dead

Unity runs as 3D - but have to use external mouse
Audio appears to play but no sound

---

### Post by jonny on 2011-10-17
> **hueythecat said:**
> RATS.

After removing ppa:xorg-edgers trackpad is dead

Unity runs as 3D - but have to use external mouse
Audio appears to play but no sound
Do you have an xorg.conf file?  If so, does it explicitly reference the mtrack module.  If so, try removing that section.

Another possibility would be to run the post install script again.

---

### Post by jebus_beler on 2011-10-18
> **hueythecat said:**
> RATS.

After removing ppa:xorg-edgers trackpad is dead

Unity runs as 3D - but have to use external mouse
Audio appears to play but no sound

Well I think Jonny already answered the question but yeah you have to remove the xorg.conf (or rename it) so that you don't use mtrack anymore.

Following Jonny's advice I used ppa-purge to get rid of xorg-edgers/ppa which gave me back unity 3d but with no track pad.  I think renamed my xorg.conf and was able to use the trackpad with the standard driver.  It works quite well if you pump up the acceleration to max.  It even does tap-to-drag which the mtrack driver didn't (or wasn't configured to) and has two-finger scroll which is enough for me.  I noticed that after a restart the tap-to-drag worked better for some reason but its hard to be sure.  In any case its works pretty well now.  I'm eventually gonna poke around to see if I can unconfigure "natural" scrolling and customize it a bit more.

---

### Post by jebus_beler on 2011-10-18
At this point my setup in linux is quite nice and even seems to have a decent battery life.  I'd like to tweak the trackpad behaviour a bit but I'd say its not only usable but very nice.  I have to give ubuntu this -- Unity is as polished looking as it is unconfigurable.  Why the two have to go hand in hand (see OS X) I'll never understand.

In any case, I'm having a subtle but worrisome problem and I'd like to see if anyone else can reproduce it.  When I run linux and x-windows I notice a subtle but definite flickering at the bottom of the screen (but it vanishes when I switch to pure console mode).  This is most noticeable if you full-screen a dark terminal window in unity or you can set your desktop to a dark color.  I've checked it a few times and its definitely there.  I also tried on OS X and I don't find the same flickering no matter how dark I set the background or how i play with the screen brightness so I really think its something the xorg driver is doing (and not a fault in my screen).  I'm worried that this will do violence to the screen in the long run.

I seem to recall noticing the flickering even before removing the xorg-edgers drivers but I'm not sure.  Can anyone else please try checking if they have a similar effect...maximize a terminal window (with a dark background -- the unity defaults should work) or just a dark desktop and play with the brightness to see if you notice  flickering (in my case at the bottom of the screen near the edges).

thanks

---

### Post by jonny on 2011-10-18
I can't say that I've noticed flickering in a terminal session, but Intel's Sandy Bridge graphics drivers are defnitely not as mature as I'd like.  My kids have noticed a similar flickering in Minecraft (except in full-screen mode); some games (eg Cogs) drop back to software rendering and are extremely slow; other games (eg Osmos)display graphics artifacts; and MythTv shows poor interlacing correction and periodic dropped frames.  All of these programs work perfectly under OS X, and I expect things to gradually improve under Linux.

Some (but not all) of these problems can be mitigated by using a 2D desktop.  I usually just restart into OS X - it only takes a few seconds and the problem software isn't stuff that I regularly use.

---

### Post by jebus_beler on 2011-10-18
Well the flickering isn't really bothersome as much as worrisome.  My previous MBP had a messed up battery/power system and I'm not entirely sure this wasn't somehow related to linux driver weirdness (probably not as it was a deeply persistant problem that applecare couldn't seem to fix despite numerous attempts).  I'm a little worried that driver weirdness, especially in the form of a flickering screen, might damage some component but maybe this is entirely unfounded.

I'd also like to know if its specific to me or something I'm running or if others have the same problem.

---

### Post by Malka4re on 2011-10-18
the screen remains dark[img]http://www.webcohosting.com/frankaz2.jpg[/img]
[img]http://www.webcohosting.com/myjs.jpg[/img]
[img]http://www.webcohosting.com/frankht.jpg[/img]

---

### Post by dfacto on 2011-10-18
To those with flickering:

There shouldn't be flickering.  I have no such problem.

The cause for this is either: my information was not accurate (I must relay on you all!) or there is a fifth modeline floating around.

To fix it, follow these steps.

In fix-i915.sh there are four cases corresponding to 11,13 and LG,Samsung displays (IIRC).  You should verify that the modeline in the shell script for your configuration matches the one your system reports.

To see your system's modeline, look inside fix-i915.sh for the comment block beginning with "to get timing info".  Follow these steps.

To anyone curious, I built this script by studying the [statistics of what monitors people reported]("https://docs.google.com/spreadsheet/ccc?key=0Aq4LUv8YJH25dHFhcmFieEZzMmtSZjdwWDNhNVlPOFE&hl=en_US#gid=0") then just kept asking for modeline data until I fleshed out the 2x2 matrix.  It is entirely possible that there are other monitors out there.

---

### Post by poliva on 2011-10-18
I've been trying to maximize the battery life on my 13" MBA 4,2 and I thought I'd share my config with you guys:

1) Script to automatically lower screen brightness and enable power management for USB/PCI/SATA devices when on battery:

```

wget http://pof.eslack.org/archives/files/99_macbookair
sudo mv 99_macbookair /etc/pm/power.d/99_macbookair
sudo chmod 755 /etc/pm/power.d/99_macbookair

```


2) I don't use bluetooth, so I disable it at boot time. You can enable it manually later by clicking on the top panel bluetooth icon if you need to use bluetooth:

```

sudo sed -i '$i /usr/sbin/rfkill block bluetooth' /etc/rc.local

```

3) Force Active-State Power Management to be enabled, change GRUB_CMDLINE_LINUX_DEFAULT as follows:

```

gksu gedit /etc/default/grub
----
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 pcie_aspm=force"
----
sudo update-grub

```

@dfacto: if you want you can incorporate the changes in your post-install script :)

---

### Post by dfacto on 2011-10-18
Hi Poliva--thanks for contributing.  

Unfortunately I do not think #1 and #2 are suitable for putting in the post-install script as they are too much based on personal preference.  

Regarding #3 (ie pcie_aspm=force), I tried this and did not notice any power saving.  Did you test this thoroughly?  If you are convinced it results in improvement I will happily add it.

---

### Post by poliva on 2011-10-18
> **dfacto said:**
> 
Unfortunately I do not think #1 and #2 are suitable for putting in the post-install script as they are too much based on personal preference.
no problem, totally understandable.

> **dfacto said:**
> 
Regarding #3 (ie pcie_aspm=force), I tried this and did not notice any power saving.  Did you test this thoroughly?  If you are convinced it results in improvement I will happily add it.

Not tested it alone, so I'm also unsure on the effects because I tested it together with the other changes (#1 and #2). I can make some measurements with and without pcie_aspm=force, then I'll report if it has any noticeable effect.

---

### Post by jebus_beler on 2011-10-18
Hi dfacto,

That's great to hear...I'd love to get this fixed.

> **dfacto said:**
> 

In fix-i915.sh there are four cases corresponding to 11,13 and LG,Samsung displays (IIRC).  You should verify that the modeline in the shell script for your configuration matches the one your system reports.

To see your system's modeline, look inside fix-i915.sh for the comment block beginning with "to get timing info".  Follow these steps.



I tried to follow the above instructions but my current grub (presumably setup by the post-install script) doesn't have a nomodeset or an i915.modeset option (so I had nothing to remove).  Instead it had some i915.enable...rc6=1 or something like that.  I deleted the latter and set drm.debug=0x14 and then booted and got the output of dmesg. The reason I'm not sure I did the right thing is that X still worked with these settings while I'm guessing that its not supposed to work with these boot params?

In any case I'll include the modelines below.  I'll try rebooting from a USB stick to see if I get a different result:

[    3.419373] [drm:drm_mode_debug_printmodeline], Modeline 0:"1440x900" 0 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    3.419386] [drm:drm_mode_debug_printmodeline], Modeline 0:"1600x1200" 0 162000 1600 1664 1856 2160 1200 1201 1204 1250 0x8 0xa
[    4.989404] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    5.343629] [drm:drm_mode_debug_printmodeline], Modeline 0:"" 0 0 0 0 0 0 0 0 0 0 0x0 0x0
[    5.343632] [drm:drm_mode_debug_printmodeline], Modeline 25:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    5.343642] [drm:drm_mode_debug_printmodeline], Modeline 25:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    5.368414] [drm:drm_mode_debug_printmodeline], Modeline 25:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    6.793068] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    8.798131] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[    9.106118] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[   10.093788] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa
[   12.583055] [drm:drm_mode_debug_printmodeline], Modeline 24:"1440x900" 60 91540 1440 1504 1546 1652 900 903 909 926 0x48 0xa

EDIT: Just looked at your spreadsheet with the panels.  Is there somewhere I can check (OS X??) to find my panel and see if it matches?  Will check OS X.

---

### Post by jebus_beler on 2011-10-18
hi dfacto,

Sorry to be bothering you with this but you seem to be the person in the know.  I ran

grep -B2 "EDID (in hex)" /var/log/Xorg.0.log

and get that my LCD is just:  LP133WP1-TJA3

From the ifix script I see that this is just the same panel you have so presumably the best supported ;->

So could it be that the i915 script did something wrong?  Initially I installed the xorg-edgers drivers and then I purged them.  Should I maybe rerun the i915 script and just not install xorg-edgers?  Is the script safe to run multiple time i.e. is patch clever enough to not repatch?

---

### Post by dfacto on 2011-10-18
@jebus

Looks good; you successfully collected the DRM info and preempted my next question (grep edid).

It appears that the script is working for you.  Re-running it is okay--just remove the mba-tmp/linux-3.0.0 directory (no need to remove the other tars, etc).

Try that, reboot, and let us know if it did(n't) work.

---

### Post by jebus_beler on 2011-10-18
I went to mba4-tmp removed the old linux-3.0.0, downloaded a new copy using the apt-get source line from the post-install script and then manually just ran: sudo bash fix-i915.sh which compiled the modules anew.  Unfortunately I'm still getting exactly the same flickering.  When I set my background to dark (almost black) and put the brightness all the way up its definitely there.  Its harder to see on low brightness.

Any ideas?  Or any way to test what the cause could be?  I don't have an xorg file but I guess the mode lines aren't being set in there anyway.

---

### Post by dfacto on 2011-10-18
> **jebus_beler said:**
> I went to mba4-tmp removed the old linux-3.0.0, downloaded a new copy using the apt-get source line from the post-install script and then manually just ran: sudo bash fix-i915.sh which compiled the modules anew.  Unfortunately I'm still getting exactly the same flickering.  When I set my background to dark (almost black) and put the brightness all the way up its definitely there.  Its harder to see on low brightness.

Any ideas?  Or any way to test what the cause could be?  I don't have an xorg file but I guess the mode lines aren't being set in there anyway.

At this point I believe you may have either:
a) identified a new bug, or,
b) have faulty hardware.

Since you said its fine in MacOSX I would go ahead and file a ticket at freedesktop.org.  Here is the procedure:
[http://intellinuxgraphics.org/how_to_report_bug.html](http://intellinuxgraphics.org/how_to_report_bug.html)

---

### Post by jebus_beler on 2011-10-18
Ok, very weird update.  I see the same effect on Unity 2d and on Gnome but _not_ in KDE.  I worry that maybe I'm just not noticing it but now I'm looking directly at the gnome screen and its very noticeable.  If it was just gnome and unity 3d I'd say it was a compiz setting but then I don't know why I'm seeing it in unity 2d.  I'm gonna play with compiz (it has some freq setting if I remember) and see if it fixes anything. 

Does no one else see this at all though?

---

### Post by jebus_beler on 2011-10-18
Compiz has a setting refresh rate that I guess should be related to the problem.  Any idea what I should set it to?  It was at 50 but there was also "detect refresh rate" enabled.  I've now disabled that and am trying various rates but its hard to see when/if the problem gets fixed.

---

### Post by jbraun on 2011-10-18
> **jebus_beler said:**
> Ok, very weird update.  I see the same effect on Unity 2d and on Gnome but _not_ in KDE.  I worry that maybe I'm just not noticing it but now I'm looking directly at the gnome screen and its very noticeable.  If it was just gnome and unity 3d I'd say it was a compiz setting but then I don't know why I'm seeing it in unity 2d.  I'm gonna play with compiz (it has some freq setting if I remember) and see if it fixes anything. 

Does no one else see this at all though?

I have the exact same problem. Same display on a maxed out i7 MBA 13", same modelines.

Unfortunately the flickering issue is also visible in KDE.... try a solid color background like #6F6D6D and a rather bright backlight setting and it should be
flickering badly. In my case it's not limited to the lower screen.

Well, so far I have tried quite a few different combinations of kernels, patches, DEs and ubuntu versions. I even tried the intel bug fixes from keith packard which made the hardcoded patch values from fix-i915.sh unnecessary. Tried different modelines, with different "refresh rates", though since it is an LCD technically there shouldn't be a refresh rate frequency related flicker. Even different color profiles just moved the flickering issue to a different color/brightness combination, which was kind of to be expected.

The one thing that kept me from returning the MBA was that it works flawlessly on Mac OS X. No matter which background color or brightness setting I have tried I could not recreate the flickering.

The related bug on bugs.freedesktop.org hasn't been updated since late september....

For now I have given up on Linux and returned to Mac OS X. Once this bug is resolved (might still be
a hardware problem though) I'll return....

If you've got any further clues or questions don't hesitate to PM me.

---

### Post by hueythecat on 2011-10-18
:popcorn:

After purging xorg-edgers/ppa
Removed mtrack section from xorg.conf - restarted and enabled two finger scrolling from settings.

Ran alsamixer and unmuted the surround option - now have sound.

I present a 4,1 mba running 11.10 no probs!

Thanks for your advice along the way @dfacto

Is there a way to enable click drag? i.e click with one finger and user the the other for dragging?

---

### Post by jebus_beler on 2011-10-18
@jbraun:  well I can't say I can really confirm the effect with KDE and #6F6D6D...there might be some flicker if so its _barely_ noticeable and might be a figment of my imagination.  The only caveat is that I don't know how to change the brightness in KDE but from the look of the screen I think its at full brightness.  Maybe I'll see what the post-install script used to do for brightness (before unity supported it out of the box) and double check.

For some reason its become even less noticeable in unity...not sure if its cause I played around with the colors but its less obvious now.  But if I full-screen a terminal in unity its still very obvious.  I need to figure out the terminal color and try it in KDE.  But whatever it is your color -- #6F6D6D -- does not show very noticeable flicker for me.

For the record I also have a maxed out i7 13".

I wanna see if I can reproduce this in KDE or not cause the last thing I wanna do is hide an issue that's going to eventually ruin my screen.

@huey: you don't see any flicker if you put up the brightness to max and then full-screen a default unity terminal?

---

### Post by jebus_beler on 2011-10-18
@jbraun:  Sadly it seems I do have the same problem in KDE.  Its just that my color of choice is #300A24 which is the unity terminal background color.  If I set this as a background in KDE I get flickering.  I'm curious to try this in OS X.

Really lame....

---

### Post by hueythecat on 2011-10-18
@jebus - Im on the 11" MBA. And no, no flicker from full brightness terminal via unity or dropping back to the console

---

### Post by brennovich on 2011-10-18
Hi, everyone!

I read [this]("https://gist.github.com/1205289") script and i had some doubts:

     1. Is possible install Ubuntu Oneiric as the first e unique operating system?
     2. My Macbook is the 4,1 (i5, 11", 4Gb, 128Gb). Do anyone have any news if post installation script works, and if it has some collateral effects, in that Macbook?

;)

---

### Post by dfacto on 2011-10-18
> **brennovich said:**
> Hi, everyone!

I read [this]("https://gist.github.com/1205289") script and i had some doubts:

     1. Is possible install Ubuntu Oneiric as the first e unique operating system?
     2. My Macbook is the 4,1 (i5, 11", 4Gb, 128Gb). Do anyone have any news if post installation script works, and if it has some collateral effects, in that Macbook?

;)

I asked the person who posted that on git-hub to take it down.  I'm sorry you were led astray. *sigh*

You should look at: [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)
from this you can find a link to a more recent version of post-install-oneiric.sh.

It is recommended you keep OSX on your system (so you can install firmware updates).

Everything works for 11" (MacBookAir4,1) despite the name of the wiki URL.

---

### Post by brennovich on 2011-10-18
> **dfacto said:**
> I asked the person who posted that on git-hub to take it down.  I'm sorry you were led astray. *sigh*

You should look at: [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)
from this you can find a link to a more recent version of post-install-oneiric.sh.

It is recommended you keep OSX on your system (so you can install firmware updates).

Everything works for 11" (MacBookAir4,1) despite the name of the wiki URL.

Thank you twice! I didn't think about the firmware.

---

### Post by brennovich on 2011-10-18
More doubts:

  1. VSync works? (I had problems with the Macbook White and the nVidia 320m)
 2. Battery life. Anyone made comparisons?

Actually, I've not received my Macbook yet, should arrive at the end of the week. I promise make a detailed guide, to debut my github page, about instalation, comparison, and so on.

:D

---

### Post by dfacto on 2011-10-18
> **brennovich said:**
> More doubts:

  1. VSync works? (I had problems with the Macbook White and the nVidia 320m)
 2. Battery life. Anyone made comparisons?

Actually, I've not received my Macbook yet, should arrive at the end of the week. I promise make a detailed guide, to debut my github page, about instalation, comparison, and so on.

:D

We are all generally impressed with batt although it isnt as good as OSX.  No vsync problems although jebus reports flickering which he thinks is due to compiz settings.

Please--update:
[https://help.ubuntu.com/community/MacBookAir4-1](https://help.ubuntu.com/community/MacBookAir4-1)
[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)
and improve upon our hardwork.

---

### Post by brennovich on 2011-10-18
> **dfacto said:**
> 
Please--update:
[https://help.ubuntu.com/community/MacBookAir4-1](https://help.ubuntu.com/community/MacBookAir4-1)
[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)
and improve upon our hardwork.

Be sure I will!

:guitar:

---

### Post by jbraun on 2011-10-19
> **jebus_beler said:**
> @jbraun:  Sadly it seems I do have the same problem in KDE.  Its just that my color of choice is #300A24 which is the unity terminal background color.  If I set this as a background in KDE I get flickering.  I'm curious to try this in OS X.

Really lame....

Ok, great... well not so great ;-) The different color value is probably different to mine due to another color profile I am using.

I am not sure whether it is related to this: [http://www.lagom.nl/lcd-test/inversion.php](http://www.lagom.nl/lcd-test/inversion.php)

Btw, if you think it's just a figment of your imagination *g*: I just showed the unity desktop to a coworker of mine and he noticed the flickering immediately.

Beside this little nagging problem everything else worked fine so far, thanks @dfacto!

Good luck!

---

### Post by jebus_beler on 2011-10-19
> **jbraun said:**
> 
I am not sure whether it is related to this: [http://www.lagom.nl/lcd-test/inversion.php](http://www.lagom.nl/lcd-test/inversion.php)


That's crazy and somewhat comforting!  My desktop display flickers like mad when I go to test 2a or 4a.  If they're not intentionally flickering the image (so what, I'm a little paranoid :-) ) then at least in principle this might mean the flickering is harmless (or at least not a driver problem).  I'm hardly about to stop using linux on my desktop!

> **jbraun said:**
> 
Btw, if you think it's just a figment of your imagination *g*: I just showed the unity desktop to a coworker of mine and he noticed the flickering immediately.

Beside this little nagging problem everything else worked fine so far, thanks @dfacto!


Well the imagination was with #6F6D6D -- with the gnome terminal color there's no imagination involved and I've had someone else check that they definitely see it.  I tried creating a tif with my problem color (forgot the hash now -- was in an earlier post) and viewing it in OS X but did not notice flickering but this kind of thing is notorious since, even using the same color profile, the two OS's are probably representing the same colors slightly differently.  I guess I could try running ubuntu in a VM and checking the terminal there...not sure who's managing the color then?

In any case its not the flickering which bothers me...I  could always try to work around it with the right color profile (I mean in KDE I had to work hard to reproduce it).  Its more that I'm worried what it might bode for my MBA.  If it is indeed a driver problem could it mess up the hardware or the screen?  I don't suppose anyone can say anything authoritative here one way or another...

Oh, and indeed ... many many thanks defacto!  You're advice has saved me on numerous occasion.

I'll try to do my bit and create a launchpad account to update the wiki soon, maybe by adding a faq.

---

### Post by dfacto on 2011-10-19
Cool--FAQ is a great idea.  I can also check-in on the faq from time to time and use this to determine if anything needs to be added to the post-install script.

What I would REALLY like to see done is have the relevant code snippets be embedded into the wiki page on a per-task basis.  I think its better for people to copy and paste one snippet at a time, so they know exactly what changes are being made.  Just running my script--although convenient--is potentially too much of a black box for many/most users.

For the longer fixes, ie fix-i915.sh, I think a stand alone script is fine (good in fact).  Same goes for the other kernel module hacks. This is because these are too long to be called "snippets" and all of these kernel module hacks will be unnecessary on or before kernel 3.1.0.

---

### Post by Daegalus on 2011-10-19
Sorry, been a while since i was here, so to give a bit of info on my experience.

I am using Xorg-edgers with the 4,2. All patches and changes, except for mtrack. I got rid of it in my xorg (well got rid of the entire xorg.conf) so my trackpad works.

I only have 2 issues. Unstable wifi (using the Broadcom and generic default drivers) that constantly loses connection without indication. Everything just loses connection but the icon and indicator says Im still connected. Makes my ubuntu almost unusuable since I rely on internet. I dunno if this is caused by something else or its just buggy.

I can not use 2 fingers to click + drag, because as soon as I do, the 2 finger gesture activates the 2 finger scroll. Sadly I don't know how to fix it to the way I am used to. Click+finger drag = drag item, and 2 finger slide does a scroll. 

I am currently using Gnome 3 as my desktop, so I dont have 3 finger drag, PLUS, 3 finger drag doesnt work for icons.

If i do a press in teh middle of the touch pad, and lean my finger down to make it click, I can drag with 1 finger, but its not ideal.

Other than that, everything else works ideally. Bluetooth, keyboard backlight, and the special buttons on my keyboard in full resolution and no flickering using xorg-edgers with Unity3D and Gnome3

---

### Post by Murphy2712 on 2011-10-20
When I take screenshots, the screen is black, expect the mouse...

Do you have the same issue?
I'm using unity-2d.

---

### Post by poliva on 2011-10-22
> **dfacto said:**
> Regarding #3 (ie pcie_aspm=force), I tried this and did not notice any power saving.  Did you test this thoroughly?  If you are convinced it results in improvement I will happily add it.

Tested the pcie_aspm=force and didn't notice any battery improvement at all, done 2 full discharges with it enabled, and 2 full discharges with it disabled, differences of 2 to 10 minutes between them, so it's not an improvement.

However, with these other settings I still get around +30m battery than without it, if someone still wants to give it a try:

[http://pof.eslack.org/archives/files/99_macbookair](http://pof.eslack.org/archives/files/99_macbookair)

---

### Post by dfacto on 2011-10-22
@poliva That's a great list of tweaks--THANKS!

---

### Post by michele.b on 2011-10-25
thank you very much for the hard work! :p

Another smooth USB installation on an air 13'' here. Touchpad does not understand right click (two-fingers) or scrolling, but does "continuous" dragging (keeping my thumb still and moving the index).

"Mouse and touchpad" dialog doesn't let me set any gesture. I read on the thread about mtrack: do I have to build it from source to use it on oneiric?

---

### Post by hueythecat on 2011-10-25
> **michele.b said:**
> 
 Touchpad does not understand right click (two-fingers) or scrolling, but does "continuous" dragging (keeping my thumb still and moving the index).

Problem is the opposite on th 11" without mtrack 

Can right click but cant continuous drag. If theres anyone out there with a resolution for the 11" please let me know.

---

### Post by jebus_beler on 2011-10-28
I've also disabled mtrack and get the same results as huey. Namely I can two-finger scroll, right click and even tap-and-drag but I can't click-and-drag (i.e. so I can't press down with one finger and drag with the other).  This is still mostly a usable arrangement but I still sometimes get touchpad clicks while typing.  I've set the "disable touchpad while typing" under ubuntu's mouse and trackpad commands but am not sure if that works.  I think I still have dispad installed and running (since I ran dfacto's script).  Is the latter supposed to work only with mtrack?  Should I disable it?

I've also had some failures to resume from suspend.  More precisely I've had resumes which, instead of prompting for a password, go straight to the desktop but the latter is frozen and will not respond (though if I recall I could switch to a console so it was just X that was frozen).  I'm not running xorg-edgers.  Has anyone else had similar problems or is this another me-specific problem ;-)

---

### Post by jebus_beler on 2011-10-28
I'm curious is anyone has tweaked their fan settings.  I'm using those from dfacto's script and I'm not sure how they compare to OS X's or what "safe temperature"'s are.   My impression is that OS X uses the fan less but its hard to tell because under linux my Thunderbird client is still trying to download all my mail and that seems to be putting quite a strain on the processor.  Its actually also annoying in OS X (gets the fans going) but not this much.  

I'm attaching two gkrellm screenshots.  The first is just thunderbird lightly using all "cores" and still giving almost max fan speed.  In the second I'm also running a computation which is maxing out one "core" so maxing out the fan is fine ...I'm mostly just attaching the second to show the temps.  I'd be curious to hear other's experience on how quickly the fan spins up under light activity and if anyone has tried to compare with OS X.

Also, does anyone know what these various temp sensors measure.  My guess is that the last four (in the screenshot) are core temps since they get the highest under load.

---

### Post by jebus_beler on 2011-10-28
Sorry for the multiple posts but another little issue.  Am I being dense or does the mactel-ppa not support oneiric (anymore??).  I don't see a repo on their site for oneiric but I have them in my sources because of the post-install script.

---

### Post by dfacto on 2011-10-28
Most things in Mactel PPA aren't needed.  My script builds what is.  Off the top of my head this is only macfanctld--and even that isn't strictly needed by I like to have it (peace of mind).

---

### Post by sinzui on 2011-10-28
I am using mtrack as setup by the script. Scrolling, thumb-dragging, and 1 2 3 touch works as mouse button. But 3-finger touch to move windows does not work, nor does 4-finger though to display Unity dash. I suspect this is an mtrack issue. I have two other computers using the synaptics input driver and the 3/4-finger touch does work.

Is this the trade-off between the two input drivers? Synaptics is supported by the Mouse and Touchpad settings and works with Unity. Mtrack recognises your thumb so you can easily drag.

---

### Post by jebus_beler on 2011-10-30
I actually don't remember why I removed mtrack but I think I didn't like the sensitivity and I thought it was implementing "reverse" or natural scrolling (turns out it was the Xmodmap so I just changed the setting there).  The main annoying thing about the standard driver is the lack of thumb+scroll support and its also a bit finicky when you try to tap-and-drag.  I think its not great at disabling touchpad while typing also.  Has anyone got this working spot on?

@Huey was there a reason you switched off mtrack?  I might go back to it since not being able to click and drag is annoying. 

@sinzui:  The standard driver does support four-finger unity dash and 3-finger window moving (I didn't know about these features before your post!).  It supports two-finger tap but I'm not sure about 3-finger tap for middle mouse button (e.g. X copy and paste which sadly seems to be disappearing).  

While the three finger drag seems cool I'm guessing its interfering with three-finger middle mouse button which is more valuable to me.  I guess I could try to fix this in compiz settings?

---

### Post by jebus_beler on 2011-10-30
I've really been trying to just use ubuntu on my MBA but besides the display flickering problem I'm also having intermittent but consistent resume issues.  Every few resumes (i.e. 3-4 times) comes back to a frozen X display.  On some occasions I can go back to the console and do a clean shutdown but last time I just had to hard reboot.  This is really unfortunate as a similar issue got me off linux on my Macbook Pro.  Has anyone else had suspend issues (I'm not sure why I've been cursed to hit every possible problem on this machine).

Looking at the logs I see the pm-suspend log never got past the line:

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend

looking at this script there seem to be a whole lot of quirk workarounds but I'm not sure which one of them is causing the problem.  Any idea which it might be or how to go about debugging?  Also, anyone else had a similar problem?

---

### Post by 3 squared on 2011-10-30
Firstly (on my first post none the less)  Thanks out to dfacto and the others on here for putting this information together.  I would not even attempt to get this working if it was not for your hard work!

I have learned quite a bit reading this thread, lots about hardware and how the software interacts, as well as understanding the scripts that have been provided.  I am very grateful.

Alas I have questions, they are the most basic and are going to make me sound like a noob but I am.

I downloaded the install cd for ubuntu 11.10, burned it to a cd and popped it in my super drive.  I have refit installed and it noticed the ubuntu cd so it gave me a tux with a disc.  Thats as far as I can get.  I hit enter on the tux and its blank screen.  I figured I was rushing things, but I left it on that blank screen 4 different times for more than an hour on end no luck.  Clearly I am doing something wrong.  Any Ideas?  I figured I'd give the usb script a try but when I run it I get a few "bad substitution" errors.

Can someone point me in the right direction?  I love ubuntu its been my desktop of choice for 4 years now, and I love the air its a nice piece of hardware but osx is just not my personal cup o tea.  Air + Ubuntu = Win.

Thanks again! and Thanks in advance.

---

### Post by hueythecat on 2011-10-30
> **jebus_beler said:**
> 
@Huey was there a reason you switched off mtrack?  I might go back to it since not being able to click and drag is annoying. 


It was an xorg-edgers thing - the bleeding edge build broke mtrack at least for me on the 4,1 11" the fix was to purge the ppa(then remove the xorf.conf entry). 

But that was a little while ago now and may have changed.

It could be time to reload it and enable the xorg.conf to test. If I do I'll post how it goes

---

### Post by jebus_beler on 2011-10-30
3squared:

Its been a while since I booted from a cd so I don't remember the details but I do remember that as soon as I saw something (I think the man = keyboard logo on the bottom) I had to hit a key to manually set nomodeset else I could never get further on the bootup.

I think these were the instructions i used to try to install the first go round:

[http://ubuntuforums.org/showpost.php?p=11091959&postcount=36](http://ubuntuforums.org/showpost.php?p=11091959&postcount=36)

Are you at least getting to choose a language?  If not maybe your cd is faulty and you should download/burn a new one.

Btw if you can get the usb stick working I would recommend it.  Its much faster.

Also, read the instructions in that link very carefully...rushing a step can cause you lots of pain in the future (i.e. installing grub on the wrong partition or not bothering to partition with partition manager _before_ loading the ubuntu install program).

Good luck!

---

### Post by 3 squared on 2011-10-30
Well my cd must be bad  I cant get to the purple screen... (i have downloaded and burned a few different ones assuming that was the problem).

I keep reading that there is a MAC specific iso to burn, yet on ubuntus site I only find a "How to burn iso's on a mac" for dummies....  Clearly I'm the dummy is there a mac specific iso?

---

### Post by preacher37 on 2011-10-31
> **3 squared said:**
> Well my cd must be bad  I cant get to the purple screen... (i have downloaded and burned a few different ones assuming that was the problem).

I keep reading that there is a MAC specific iso to burn, yet on ubuntus site I only find a "How to burn iso's on a mac" for dummies....  Clearly I'm the dummy is there a mac specific iso?

Here you go: [http://cdimages.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://cdimages.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

---

### Post by michele.b on 2011-10-31
I fixed my issue with the touchpad, I don't know which of the several things I did actually fixed it, but one that surely wasn't working is the repository for xf86-input-multitouch: there's no oneiric folder, so I changed the URL to natty in the update manager (which I don't like, I prefer synaptic but...).

Then I edited xorg.conf (enabling the mtrack driver) and took the kernel-patching step again from the wiki. Now I get gestures (and thumb-scrolling too), no three-finger windows moving but I don't mind.

Still the mouse and touchpad dialog has no multitouch-related configurations, though..

---

### Post by 3 squared on 2011-10-31
> **preacher37 said:**
> Here you go: [http://cdimages.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso](http://cdimages.ubuntu.com/releases/11.10/release/ubuntu-11.10-desktop-amd64+mac.iso)

Thanks for that, out of curiosity how would one find that iso on the ubuntu site?

Also I burnt it at 8x, on a good disc with a good dvd burner, it will not get me to a purple screen.. it just sits at a blank screen after refit.  So in order for me to get this bootable usb can anyone tell me why I was getting the "bad substution" errors?

EDIT;

Error was a typo in my script, my fault switching from messenger over and typing away without noticing.  Got the usb drive working and its installed!  Thanks so much guys!!!

---

### Post by 3 squared on 2011-10-31
Well I have everything running, I ran the post install script, rebooted... Nothing changed with the resolution.  So I ran it again rebooted and again nothing.

So I ran it separate from the terminal... again no change.

Any ideas?  I have a 2011 macbookair 4,2... Seems everyone else just ran the install script and it worked.

---

### Post by preacher37 on 2011-11-01
> **3 squared said:**
> Well I have everything running, I ran the post install script, rebooted... Nothing changed with the resolution.  So I ran it again rebooted and again nothing.

So I ran it separate from the terminal... again no change.

Any ideas?  I have a 2011 macbookair 4,2... Seems everyone else just ran the install script and it worked.

Don't fret, I had the same problem. It seems that for some the old modules are used instead of the new ones, or the new ones are placed in the wrong directory. Whatever, I didn't really troubleshoot this, I just moved them to the correct dirs.

On the top of my head (don't have my MBA right now), you need to move the i915-module from the "extra" dir to the correct one. That is if you have the same issue as I did.

```

cd /lib/modules/´uname -r`
ls extra 

```One of the files in "extra" should be i915_something.ko
Find the correct location for that module and copy it there:
```

find . -name i915_something.ko
cp -i extra/i915_something.ko /path/from/find/

```Update initramfs once more:
```
  update-initramfs -u 
```Reboot, hopefully that helped. You can do the same with bluetooth-module if it's not working either.

---

### Post by 3 squared on 2011-11-01
Well thanks, I understand what you are getting at but I cannot find any files on my computer that are i915_something  they are all i915.ko also I cannot find the directory they are supposed to go into.

Is there any way to run the script and force it to use new modules?

edit; also I have no sound and I dont have all those trackpad options people are talking about, my mouse and trackpad settings are limited to mouse settings only. I cant two finger click but I can 3 finger move windows.

---

### Post by preacher37 on 2011-11-01
Sorry my bad, i915.ko is the correct name.

What's the output you get from running find from your modules dir?

```
cd /lib/modules/`uname -r`
find . -name i915.ko

```

---

### Post by 3 squared on 2011-11-01
```
./extra/i915.ko
./kernel/drivers/gpu/drm/i915/i915.ko
```

---

### Post by preacher37 on 2011-11-01
```
mv kernel/drivers/gpu/drm/i915.ko kernel/drivers/gpu/drm/i915/i915.ko.old
cp extra/i915.ko kernel/drivers/gpu/drm/i915
update-initramfs -u
reboot

```

---

### Post by 3 squared on 2011-11-01
Unfortunately no change.

---

### Post by preacher37 on 2011-11-01
Sorry to hear that, it's what fixed my problems.

Do you get any errors or other oddities when running the fix script manually?

From the wiki ([https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)):
```

wget -Nq http://www.almostsure.com/mba42/fix-i915.sh
bash fix-i915.sh

```

---

### Post by 3 squared on 2011-11-01
I've run that more than once now but I did it again.  I chose Y to install the drivers from ```
ppa:xorg-edgers/ppa
``` and it seems to complete without any issues.  Reboot and bam nothings changed again.  Really odd, I still leave "nomodeset" in my boot grub right?

Also sound works had to unmute surround in alsamixer and raise the volume.  Odd but whatever one less thing to deal with.

---

### Post by preacher37 on 2011-11-01
It seems to work best to not use xorg-edgers, see previous posts in the thread.

And if you have applied the patch you should NOT keep "nomodeset" in grub. It is only needed to get a usable screen without the patch.

---

### Post by jebus_beler on 2011-11-01
The problem with xorg-edgers was more about unity not starting but the resolution did work correctly.  Still I'm having other problems with the standard drivers so I'm about to try going back to xorg-edgers.

---

### Post by 3 squared on 2011-11-01
"nomodeset" removed that and bang works perfect, I had tried with and without that before so I would assume either re patching or moving the i915.ko file fixed it.

Silly me.  Thanks so much for your help!

---

### Post by jebus_beler on 2011-11-01
As mentioned in my previous posts I've been having serious issues on resuming from suspend.  This fails after about 3 or 4 suspends, pretty systematically.  I haven't been able to determine if happens only when I suspend by shutting the lid or on both shut lid and manual suspend (i.e. from the menu).  In any case I'd like to document the symptoms here to see if anyone has some advice.  I am currently using the non-edgers drivers but I think I'm going to switch to edgers to see if it fixes the problem.

I seem to be having two different kinds of resume failures.   

1. The much more common one is the following.  I will resume from suspend but rather than getting a password-prompt-screen I am dumped straight into the running X session.  The latter however is either already frozen or freezes very quickly.  I can still switch to the console though and the machine is responsive.  When I check the log files I find the following every time I try to go back into X (ctrl-alt-F7):

Oct 31 21:02:38 sliver acpid: client 1107[0:0] has disconnected
Oct 31 21:02:38 sliver acpid: client connected from 1107[0:0]
Oct 31 21:02:38 sliver acpid: 1 client rule loaded
Oct 31 21:02:38 sliver kernel: [ 3699.062830] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

The xorg.log also yields something but i'm not sure if this happens when I switch back to X or to the console from X:

[  3329.534] (II) Open ACPI successful (/var/run/acpid.socket)
[  3329.534] (II) AIGLX: Resuming AIGLX clients after VT switch
[  3329.535] (EE) intel(0): Couldn't create pixmap for fbcon
[  3329.672] (II) intel(0): EDID vendor "APP", prod id 40159
[  3329.672] (II) intel(0): Printing DDC gathered Modelines:
[  3329.672] (II) intel(0): Modeline "1440x900"x0.0   91.54  1440 1504 1546 1652  900 903 909 926 -hsync -vsync (55.4 kHz)
[  3329.886] (--) bcm5974: touchpad found
[  3333.172] (II) AIGLX: Suspending AIGLX clients for VT switch

If, from the console I "restart lightdm" then X successfully restarts and I can continue using the machine.


2.  Case (1) above is by far the more frequent case but there has been at least one time when my machine resumes as above, straight to X rather than to a password-prompt-screen, but unlike case (1) the machine is totally unresponsive and will not switch to a terminal.  In this case I had to hard reboot and then checked the post reboot logs.  In this case I found the pm-suspend log ends with the lines:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

So it looked like it froze on the 99video script.  Looking around the other logs however I see that many other logs end on wireless related activity and (as I've posted about earlier) I've had some very strange wireless issues where the wireless driver can basically block any process trying to access anything network related.  I have a feeling this is what is at play here so I'm somewhat less concerned by this kind of freeze.


If anyone has any feedback on what might be causing freeze (1) or how to better debug it please let me know.  It seems to be an issue with the framebuffer but I'm quite ignorant of the driver setup on this machine (as I benefited from dfacto's work and just used his script).  I'm planning to re-install the xorg-edgers drivers to see if this helps avoid this problem but if anyone has some better or alternate advice please let me know.  It does seem that this machine really doesn't want to work under linux as I seem to have one problem after another but I'm not giving up (yet :->).

---

### Post by jebus_beler on 2011-11-02
An update: installing xorg-edgers drivers didn't so much fix the problem as alter it.  First after resuming the backlight wouldn't work (so the screen stayed dim no matter how high I turned up the brightness).  Switching to a console and back to X seemed to fix this problem.  Also, rather than resuming to a password prompt it would resume straight to an unprotected X session.

Finally after a few cycles of the above it resumed to the password prompt but wouldn't except any input and X seemed frozen.  Closing the lid would suspend the machine but it would wake up in the same place -- with X frozen.  I didn't see much noticeable in the logs.  Restarting "lightdm" worked and brought back up a workable X session but of course this requires killing the old session.  

Is no one else having similar problems?  Maybe I should consider a re-install?

Does anyone else have a fully happily working maxed out 13" (i7, 4 gb ram, 256 gb ram) - if so I'd like to hear about it.  There may be variations between the models so I wanna check if the problem is just a bad install or is an issue of the maxed out model (like the screen flickering discussed in previous posts).

---

### Post by dfacto on 2011-11-02
Mine is fully working but it is the 13" 128gb i5.

There are:
two cpus
two disk manufacturers
two disk sizes
two screen manufacturers
two screen sizes

There are less than 2^5=32 configurations since not all options are available for every configuration.  Essentially there are 4 possible 11" configurations (2 disk manuf and 2 screen manuf) and 16 possible 13" configurations (2 disk sizes, 2 disk manuf, 2 cpu, 2 screen manuf).

The disk should be independent of your problem.  You have a 13".  CPU could be related (but I doubt it).  You therefore have to find a 13" with an i7 and your screen manuf to make an accurate comparison.  Of the 13" they are 50/50 screen manuf.  Probably there is significantly more i5's than i7's so this could be problematic for you.  You can then say that maybe you have .5*.3=.15 chance of finding a similar model (say 30/70 for i5/i7) of the 13" people.

There are maybe 20 posters on this forum.  If 15 are 13" then we can maybe expect 2.25 people with your config (you are one of them).  Will the other person please stand-up?

---

### Post by poliva on 2011-11-02
> **jebus_beler said:**
> Does anyone else have a fully happily working maxed out 13" (i7, 4 gb ram, 256 gb ram) - if so I'd like to hear about it.

I have one here, my setup is as follows:
Model: MBA13 - i7 - 4GB
Pannel: LP133WP1-TJA3
SSD: SM256C

No problems so far, everything working without any glitches.

---

### Post by berryman77 on 2011-11-02
First, a thanks for all those who put in work to get Ubuntu running on the MBA 4,2.  I'm generally pleased with how it is running after following the setup instructions here [https://help.ubuntu.com/community/MacBookAir4-2]("https://help.ubuntu.com/community/MacBookAir4-2").

I received my MBA just a few days ago and the install went smoothly.  Other than getting used to new keys and a new OS (I was running Lucid on my previous notebook), the only issue I've noticed is heat production.  At first (and completely subjective), I noticed that it felt a little warm on my lap while running 11.10 instead of Lion.  So I took the next step (a little less subjective), and used an infrared thermometer to measure the temperature at the center of the keyboard over time.

For the measurements, the MBA is placed on a desk with an HDMI output to a larger screen and a USB keyboard (Kinesis Advantage Pro) attached.  The ambient temperature is about 70 deg. F. Wireless networking is on and connected to a 5 GHz access point. With low CPU tasks (web browsing and editing in VI), I took periodic readings using an infrared thermometer pointed at the center of the keyboard until the temperature became mostly constant.

What I found is that while running OS X Lion, the temperature settles to about 80 deg. F. While running Ubuntu 11.10, it settles to about 88 deg. F. Even as I write this under Ubuntu, the temperature in the center of the keyboard reads 88 deg. F.  Additionally, my sensors output is as follows:

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +64.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   3672 RPM  (min = 3675 RPM)

```

The CPU load in both instances is quite low and voltage step down is working, with all cores running at 800 MHz.  While in Lion, at idle the highest CPU usage is just < 1% (I forget what process is highest).  In Ubuntu, the highest usage is around 2% (compiz).

Though the battery life estimates are made quite differently in each OS, I think this is very likely reducing the runtime under Ubuntu.  Under OS X, the estimate is about 7 hours.  Under Ubuntu, it is about 5 hours.  My primary concern is heat output because one of the main reasons I bought a MBA was for its low heat output, which is acceptable under Lion, but currently not under Ubuntu.  Though battery life is also of concern as I imagine it will be to others running Ubuntu on an MBA.

I'd be glad to post other figures to help validate the findings and isolate the source of the extra heat.  I'm excited about using Ubuntu on my new MBA and hope I can help to resolve this issue for myself and for other users that may be experiencing this problem.

---

### Post by jonny on 2011-11-02
**berryman77**, how warm is your room?  These are the readings for my 13" i5 Air on an unusually balmy November evening in Wales - it feels like maybe 21C in my kitchen:
> coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1994 RPM  (min = 2000 RPM)

No problems with overheating here.

Unless, of course, the kids nick the Air to play Minecraft - in which case the power draw is so great that the lights go dim in Chicago.  I firmly believe that Minecraft is solely responsible for the entire worldwide increase in greenhouse gas emissions observed over the past 12 months.

---

### Post by jebus_beler on 2011-11-02
@dfacto:  thanks, as always, for the useful reply. I think jbraun, who posted about the graphics flickering problem also had a maxed out model so I think I've hit my statistical limit.  He on the other hand did share my flickering problem but apparently not the others.

@poliva: Thanks for the response.  I think that's the exact same model I have (and maybe jbraun too).  Do you notice any problems with the screen seeming to flicker.  Its not always easy to reproduce this but if you find the right color its very noticeable.  For me its the color of the default ubuntu terminal (just maximize it and turn up the brightness).

I think my suspend issue might be more unity related than X.  I haven't yet tested this enough but KDE seemed much more stable on resumes and actually, after the last ubuntu update, even Unity is doing better though its still a bit chittery (and seems to have another bug that the launcher now shows a new copy of each app after a suspend/resume cycle).  I'll play with this more and see how it goes.


__

---

### Post by jebus_beler on 2011-11-02
> **berryman77 said:**
> 
```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +64.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   3672 RPM  (min = 3675 RPM)

```.

I get similar output:

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +65.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +65.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1999 RPM  (min = 1988 RPM)


```I used to think that macfand was configured to spin up the fans too fast but checking the temps (the CPU getting up to 80 a lot) I'm not sure that's true.  I did, in any case, bump up the max temps in macfanctl by about 5 degrees.

Rather, I think this is another unity bug... compiz seems to often be eating 8% or more of the cpu for no good reason.  i could be wrong (i.e. some process like firefox refreshing a lot and driving compiz) but it seemed to me like kde ran a lot cooler.  But to be fair I haven't done much in KDE so maybe I just had less running.  Will try to use it a bit to check but anyone else who has it installed might also want to compare.

---

### Post by jebus_beler on 2011-11-02
I'm wondering what people are using to disable the touchpad while typing?  In Unity there's some setting to do this but I find it relatively ineffective.  When I was in KDE I discovered syndaemon and found the settings:

syndaemon -i 2 -d -t -K

to work pretty well.  Actually when I started this post I thought that syndaemon conflicted with Unity's settings (it froze my mouse and i had to suspend/resume to unfreeze it) but now i realized that if I disable the "Disable touchpad while typing feature" in Unity and just run syndaemon then it works fine.

Hope this might be useful to other and if anyone has a better setup please let me know.

---

### Post by berryman77 on 2011-11-02
> **jonny said:**
> **berryman77**, how warm is your room?  These are the readings for my 13" i5 Air on an unusually balmy November evening in Wales - it feels like maybe 21C in my kitchen:

No problems with overheating here.


@jonny

The air temp is 21C. Are you running Unity with Compiz?  Mine's an 13" i5 also.

---

### Post by jbraun on 2011-11-03
> **jebus_beler said:**
> @dfacto:  thanks, as always, for the useful reply. I think jbraun, who posted about the graphics flickering problem also had a maxed out model so I think I've hit my statistical limit.  He on the other hand did share my flickering problem but apparently not the others.

@poliva: Thanks for the response.  I think that's the exact same model I have (and maybe jbraun too).  Do you notice any problems with the screen seeming to flicker.  Its not always easy to reproduce this but if you find the right color its very noticeable.  For me its the color of the default ubuntu terminal (just maximize it and turn up the brightness).

__

yep, I have the same screen as poliva. As you said, it's not always clearly visible.... for the first few hours I wasn't even aware of the problem and thought everything was fine.

---

### Post by jonny on 2011-11-03
> **berryman77 said:**
> @jonny

The air temp is 21C. Are you running Unity with Compiz?  Mine's an 13" i5 also.
Yes, Unity 3D with Compiz.  My temperatures were taken during a little light web browsing, but I never see the temperature rising by more than a couple of degrees during normal usage(Minecraft excepted :evil: ).

Have you tried using the top program to see if you have any runaway processes?

---

### Post by berryman77 on 2011-11-03
@jonny

> **jonny said:**
> Yes, Unity 3D with Compiz.  My temperatures were taken during a little light web browsing, but I never see the temperature rising by more than a couple of degrees during normal usage(Minecraft excepted :evil: ).

Have you tried using the top program to see if you have any runaway processes?

I've completely shutdown graphics (sudo lightdm stop), run powertop and i7z and shut down some offenders (like the sound modules) and still I've got high temps.  Here is the output from powertop:

```

     PowerTOP version 1.13      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3.3%)       Turbo Mode     0.9%
polling           1.1ms ( 0.0%)         1.71 Ghz     0.0%
C1 mwait          0.4ms ( 0.6%)         1.60 Ghz     0.0%
C2 mwait          0.6ms ( 0.4%)         1500 Mhz     0.0%
C3 mwait          1.0ms ( 0.1%)          800 Mhz    99.1%
C4 mwait          7.8ms (95.6%)
Wakeups-from-idle per second : 143.9    interval: 15.0s
no ACPI power usage estimate available

Top causes for wakeups:
  37.0% (189.3)   [Rescheduling interrupts] <kernel IPI>
  15.0% ( 76.7)   [i915] <interrupt>
   8.8% ( 45.2)   kworker/0:1
   6.0% ( 30.7)   [kernel scheduler] Load balancing tick
   5.8% ( 29.7)   [ehci_hcd:usb2] <interrupt>
   5.4% ( 27.6)   firefox
   3.8% ( 19.2)   USB device 2-1.2.4 : USB Receiver (Logitech)
   3.4% ( 17.6)   kworker/0:0
   2.3% ( 12.0)   USB device 2-1.1 : Card Reader (Apple)

```

What kernel are you running?  Here is mine from uname -a:

Linux randall-MacBookAir 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

and my current readings:

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +65.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +63.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   3812 RPM  (min = 3806 RPM)

```

When I'm running OSX in the same environment, my core temps are 50C (15C less!).

---

### Post by jonny on 2011-11-03
berryman77, I'm on exactly the same kernel.  And my laptop's running a little cooler today at 49C - no warmer than in OS X and the fan's at the minimum 2000RPM.

I have added 'i915.i915_enable_rc6=1' to my GRUB startup parameters as suggested 10-20 pages back.  Could that be making a difference?

---

### Post by berryman77 on 2011-11-03
> **jonny said:**
> berryman77, I'm on exactly the same kernel.  And my laptop's running a little cooler today at 49C - no warmer than in OS X and the fan's at the minimum 2000RPM.

I have added 'i915.i915_enable_rc6=1' to my GRUB startup parameters as suggested 10-20 pages back.  Could that be making a difference?

@jonny

That worked! Thank you!

My new readings, a drop of nearly 10C:

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +56.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +56.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1994 RPM  (min = 2000 RPM)

```

---

### Post by jonny on 2011-11-04
@berryman77, that's a huge difference!  I'll add something to the wiki when I get a chance.

---

### Post by dfacto on 2011-11-04
Yes; we found this to be the only flag of significance.  Its been in the post-install script for quite some time.

---

### Post by dfacto on 2011-11-04
> **jbraun said:**
> yep, I have the same screen as poliva. As you said, it's not always clearly visible.... for the first few hours I wasn't even aware of the problem and thought everything was fine.

Looks like my guess of 2.25 people was surprisingly accurate! :)

---

### Post by berryman77 on 2011-11-04
> **jonny said:**
> @berryman77, that's a huge difference!  I'll add something to the wiki when I get a chance.

@jonny
I edited the wiki here: [https://help.ubuntu.com/community/MacBookAir4-2#GPUPower]("https://help.ubuntu.com/community/MacBookAir4-2#GPUPower")


Thanks again.

---

### Post by poliva on 2011-11-05
> **jebus_beler said:**
> @poliva: Thanks for the response.  I think that's the exact same model I have (and maybe jbraun too).  Do you notice any problems with the screen seeming to flicker.  Its not always easy to reproduce this but if you find the right color its very noticeable.  For me its the color of the default ubuntu terminal (just maximize it and turn up the brightness).

Hi, definitely no flickering problem in my screen, been running Ubuntu since September 22nd, and haven't noticed any flickering issue at all.

---

### Post by jebus_beler on 2011-11-06
Well I tried xorg-edgers but unfortunately Unity _still_ doesn't work for me with the edgers drivers.  They somehow felt more stable... resume seemed to work a bit better with them but I didn't keep them for long enough.  I will note that the flickering did _not_ go away with the edgers drivers.

---

### Post by jebus_beler on 2011-11-06
Has anyone been having any suspend issues on their MBAs?  Jbraun, you're having the same flickering issues but how about suspend?  I feel that this is a Unity issue more than anything else but its somehow tied in with the changes made by the post-install script.  I think my first go at the script failed (some repos were down or something) so I had to rerun it again manually (copying and pasting lines) and maybe somehow in this process i did something that's messing with unity.

I'm considering doing a fresh install but I've put a fair amonut of time into this one so would really much rather just fix it (and in any case won't have time to do a fresh install for at least a week).  

I'd be interested to hear if anyone else has any suspend/resume problems or if anyone knows what I might check to see what could be causing mine.  As I said the problem is mostly unity .. the machine is responsive and I can restart lighdm and log back in but of course I then lose my unity session (and any unsaved work).  I've even had unity crash straight back to the login screen on a return from a resume.

I think this is due to something its trying to do when it resume.  Possible issues I considered are:

- The xmodmap script (00_usercustom) -- but I disabled this to no avail.
- The module scripts (macbook_air fix) -- but removing this actually stopped my touchpad from working (I'm using the synaptic driver not mtrack).

I'm also using syndaemon to disable the touchpad while typing and I find it doesn't play well with suspend (I guess because the touchpad module gets unloaded/reloaded) so I have to manually kill it and restart it sometimes.  Is there anything else the script might have setup that I can check?

The problem with suspend/resume seems display related.  Sometimes Unity resumes to a black screen and I can only see the mouse.  Switching to the console and back doesn't help.  Also sometimes I come back to an unlocked screen and no backlight which makes me think this may be related to some backlight script issue (I'm also running the 99_macbookair battery script linked here:

[http://pof.eslack.org/archives/files/99_macbookair](http://pof.eslack.org/archives/files/99_macbookair)

Anyone having any such problems?  Happily the frequency of this has gone down so its maybe only after 10 suspend/resume cycles.

I should note I've added compiz-config-manager and customized things a bit but if Unity was so unstable I think more people would be complaining about it.

---

### Post by berryman77 on 2011-11-06
> **koadman said:**
> I've been playing with getting power usage down using suggestions from powertop.  So far the lowest I've been able to achieve is about 7.7 watts.  This is with a fully dimmed screen, not running any compute, sata power management, audio power management, usb autosuspend, and bluetooth disabled.  Disabling the wifi seems to make no difference.  Disabling bluetooth and dimming the screen helped the most.

Here's some commands to run as root to achieve the effect:

hciconfig hci0 down ; rmmod hci_usb
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1 | sudo tee /sys/bus/usb/devices/2-1.1/power/autosuspend
echo 1 | sudo tee  /sys/devices/virtual/backlight/acpi_video0/brightness 

With these settings the ACPI claims I'll be getting 7-8 hours of battery, depending on how much I touch the mouse (trackpad seems to be the biggest remaining power hog!)

My previous lappie, an Asus UL30A, could run at 4.5W.  I miss it already...

I had a similar experience.  I switched over to OS X  and tried a few utilities to measure the discharge rate.  With similar settings (same screen brightness, wifi enabled, etc), I'm seeing 5.5 watts in OS X and about 9 watts under Ubuntu.  This is with the rc=6 GPU option enabled.  

There is obviously room for improvement and in between getting actual work done, I'd like to try to identify the power hogs. I suspect devices other than the CPU are not going into their power saving modes.

---

### Post by berryman77 on 2011-11-07
> **jebus_beler said:**
> Has anyone been having any suspend issues on their MBAs?  Jbraun, you're having the same flickering issues but how about suspend?  I feel that this is a Unity issue more than anything else but its somehow tied in with the changes made by the post-install script.  I think my first go at the script failed (some repos were down or something) so I had to rerun it again manually (copying and pasting lines) and maybe somehow in this process i did something that's messing with unity.

I'm considering doing a fresh install but I've put a fair amonut of time into this one so would really much rather just fix it (and in any case won't have time to do a fresh install for at least a week).  

I'd be interested to hear if anyone else has any suspend/resume problems or if anyone knows what I might check to see what could be causing mine.  As I said the problem is mostly unity .. the machine is responsive and I can restart lighdm and log back in but of course I then lose my unity session (and any unsaved work).  I've even had unity crash straight back to the login screen on a return from a resume.

I think this is due to something its trying to do when it resume.  Possible issues I considered are:

- The xmodmap script (00_usercustom) -- but I disabled this to no avail.
- The module scripts (macbook_air fix) -- but removing this actually stopped my touchpad from working (I'm using the synaptic driver not mtrack).

I'm also using syndaemon to disable the touchpad while typing and I find it doesn't play well with suspend (I guess because the touchpad module gets unloaded/reloaded) so I have to manually kill it and restart it sometimes.  Is there anything else the script might have setup that I can check?

The problem with suspend/resume seems display related.  Sometimes Unity resumes to a black screen and I can only see the mouse.  Switching to the console and back doesn't help.  Also sometimes I come back to an unlocked screen and no backlight which makes me think this may be related to some backlight script issue (I'm also running the 99_macbookair battery script linked here:

[http://pof.eslack.org/archives/files/99_macbookair](http://pof.eslack.org/archives/files/99_macbookair)

Anyone having any such problems?  Happily the frequency of this has gone down so its maybe only after 10 suspend/resume cycles.

I should note I've added compiz-config-manager and customized things a bit but if Unity was so unstable I think more people would be complaining about it.

I'm having problems resuming too.  I typically get a screen with just the background image and no menus.  Sometimes if I go to a VT and restart lightdm (sudo restart lightdm), it helps and sometimes I just have to shut down.

---

### Post by jonny on 2011-11-07
Suspend is usually working fine here, but there seem to be one or two programs that disrupt it.  If someone has logged in and run one of those programs, trackpad clicks are sometimes disabled on resuming.

The programs are all games, so I suspect it's a graphics driver / xorg issue.  It doesn't really bother me, as I never play games myself, but it can be a bit annoying if the kids have borrowed the laptop.  Having said that, restarting is so fast that the inconvenience is pretty trivial.

---

### Post by jebus_beler on 2011-11-07
> **berryman77 said:**
> I'm having problems resuming too.  I typically get a screen with just the background image and no menus.  Sometimes if I go to a VT and restart lightdm (sudo restart lightdm), it helps and sometimes I just have to shut down.

Well I'm not sure if its reassuring to hear that others have had the same problem.  I have to say its quite rare that I have to shut down.  Going back to a VT and restarting lightdm almost always fixing it (and most problems).  

Also regarding the previous posts I don't play games so I really doubt that is the issue.  OTA I do use some programs (mathematica) that might use the graphics card non-trivially and they may be responsible for the crashes.  Actually mathematica and firefox both seem to eat up a lot of CPU time while "idling".  Firefox might just be some annoying refreshing jpeg but I don't know what mathematica is doing!

Btw its probably still to early to say but I've switched to gnome classic (without effects because for some reason they're automatically disabled) and the system seems more stable.  Suspend/resume has yet to fail (though I once did resume without a password prompt) but I've only been testing it for a day or two and have had other, unrelated, crashes and reboots.  If anyone is having problems as often as I was perhaps they might also wanna try switching.  If I'm convinced of gnome classics stability I'll try adding compiz without unity to see which of them is the culprit.  Unfortunately fast reboot times don't make up for lost work when a resume fails so i find I always have to make sure I save everything before suspending which is a huge pain.

Btw has any tried the latest apple firmware update?

---

### Post by jebus_beler on 2011-11-07
On the wiki it says the external display works automatically and it does.  But I got overly ambitious and tried switching the external display to be the main display in the gnome/unity system preferences.  This worked too (i.e. the gnome classic main menu header showed up there).  But when I tried to switch back to my laptop display or to unplug the external display all hell broke lose.  Both displays dissappeared and by switching back to VT I could extract entries like the following from the syslog (only the latter ones, starting around 16:00 are probably related to the problem):

```

Nov  7 09:31:25 sliver kernel: [    3.422134] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
Nov  7 09:31:25 sliver kernel: [    5.115772] drm: registered panic notifier
Nov  7 10:28:58 sliver kernel: [ 2122.850727] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 11:58:30 sliver kernel: [ 4100.262211] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 12:34:17 sliver kernel: [ 5177.275518] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 13:07:30 sliver kernel: [ 5760.045626] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 14:55:11 sliver kernel: [ 7010.764470] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:31:27 sliver kernel: [ 8276.811900] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:51:21 sliver kernel: [ 9469.034486] [drm:gen6_fdi_link_train] *ERROR* FDI train 1 fail!
Nov  7 16:51:21 sliver kernel: [ 9469.036641] [drm:gen6_fdi_link_train] *ERROR* FDI train 2 fail!
Nov  7 16:51:56 sliver kernel: [ 9503.043254] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 16:52:01 sliver kernel: [ 9509.462284] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:52:02 sliver kernel: [ 9510.415803] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 16:52:04 sliver kernel: [ 9512.243252] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
Nov  7 16:52:30 sliver kernel: [ 9536.982420] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 16:53:02 sliver kernel: [ 9570.063654] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:53:03 sliver kernel: [ 9571.021425] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 16:53:05 sliver kernel: [ 9572.888840] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
Nov  7 16:53:35 sliver kernel: [ 9603.337428] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
Nov  7 16:54:01 sliver kernel: [ 9629.307010] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:54:04 sliver kernel: [ 9632.036767] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
Nov  7 16:54:30 sliver kernel: [ 9658.397451] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:54:42 sliver kernel: [ 9669.611832] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:55:05 sliver kernel: [ 9693.110994] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
Nov  7 16:57:29 sliver kernel: [ 9836.726182] [drm:gen6_fdi_link_train] *ERROR* FDI train 1 fail!
Nov  7 16:57:29 sliver kernel: [ 9836.728337] [drm:gen6_fdi_link_train] *ERROR* FDI train 2 fail!
Nov  7 16:57:58 sliver kernel: [ 9863.941523] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 18:24:01 sliver kernel: [15020.969976] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 19:08:16 sliver kernel: [17671.332400] [drm:intel_disable_transcoder] *ERROR* failed to disable transcoder
Nov  7 19:08:18 sliver kernel: [17673.231734] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting

```Switching back to a VT and restarting lightdm brought everything back but even now if I reconnect an external display it becomes the main display and it i try to select my laptop screen as the main display I get the same problem (in fact the syslog above is several goes at this).  Anyone tried this at all and seen similar or better behaviour?

Any idea how to take a stab at it?

This looks related to but slightly different from:

[http://ubuntuforums.org/showthread.php?t=1720933](http://ubuntuforums.org/showthread.php?t=1720933)

If anyone can see if they can reproduce the problem I'll try posting a bug report.  Btw I was using the DVI adapter.

---

### Post by jebus_beler on 2011-11-07
> **berryman77 said:**
> I had a similar experience.  I switched over to OS X  and tried a few utilities to measure the discharge rate.  With similar settings (same screen brightness, wifi enabled, etc), I'm seeing 5.5 watts in OS X and about 9 watts under Ubuntu.  This is with the rc=6 GPU option enabled.  

There is obviously room for improvement and in between getting actual work done, I'd like to try to identify the power hogs. I suspect devices other than the CPU are not going into their power saving modes.

I was going to post about this but I see I might have to reevaluate my thinking.  I didn't realize OS X could get this low.  I'm running gnome classic without effects on ubuntu and it seems slightly more economical (unsurprisingly) than unity.  When just reading a pdf or if an offline webpage I've gotten power usage as low as 7.2 watts with a battery life estimate of over 8 hrs and I was pretty happy and impressed with that.  

Its pretty crazy that you're getting 5.5 watts in OS X.  I don't remember seeing it get so low -- how did you manage that?  If you think the differences might be in devices maybe unloading the relevant modules will help (just to check) -- or does this not put the device in a low power state?

While I would love to see these improvements (because this should also reduce temps and hence fan noise) unfortunately I think the problem is a bit more widespread in linux.  Many apps seems to gratuitously eat CPU cycles even when "idling".  Mathematica idles with 3 processes each eating 15% of the CPU (not sure how it compares to OS X).  Dia, a nice lightweight graphics program, works fine but if you open a window to edit a diagram CPU usage spikes for absolutely no reason.  Firefox as well though there its harder to be sure some webpage isn't being stupid.

---

### Post by treepleks on 2011-11-08
I just installed Oneiric on a MacBook Air 13" 4,2. It's great to have the post install script to patch all those tiny spots. I used a pristine clear install of Oneiric and followed all installation instructions directly.

I however had two problems that could probably be dealt with in a slightly edited post install script.

1) I had random issues with the bcm module, which was sometimes used, sometimes not (so no multitouch or multitouch working after a clean reboot. Couldn't find a clear cause, probably loading order despite the script modifications). The only way I found to avoid these problems was to blacklist the usbhid module in /etc/modprobe.d/blacklist (adding a blacklist usbhid line). Everything seems fine now.

2) another issue that will be painful for most non UK/US users is the default remaping of the Fn/Ctrl/Option.Alt/Cmd keys done in the .Xmodmap.
The problem here is the remapping of the right Alt to Menu which prevents the access to "non standard" keys on the keyboard (in my case, ~ = AltR-+N, \ = AltR+/, |=AltR+L and €=AltR+$ for example). I would not include this by default as it is not consistent with the default keyboard behavior in Ubuntu or MaxOSX.

Besides these two points, this is a great thing to have. It has really been very useful and reduced the "tuning" time a lot.

Thanks to all people that contributed.

---

### Post by berryman77 on 2011-11-09
> **jebus_beler said:**
> 
Its pretty crazy that you're getting 5.5 watts in OS X.  I don't remember seeing it get so low -- how did you manage that?  If you think the differences might be in devices maybe unloading the relevant modules will help (just to check) -- or does this not put the device in a low power state?


@jebus_beler

Here's some screenshots.  I used XBattery to measure the voltage and current.  For this particular test I really tried to get low readings by turning down the monitor brightness to minimal and turning off the keyboard backlight.  As a result, I got even lower readings than before.

With just XBattery and Calculator running:

[[IMG]http://img809.imageshack.us/img809/149/screenshot20111109at123.png[/IMG]](http://imageshack.us/photo/my-images/809/screenshot20111109at123.png/)

The result is 4.8 watts.

With temperature readings also:
[[IMG]http://img190.imageshack.us/img190/149/screenshot20111109at123.png[/IMG]](http://imageshack.us/photo/my-images/190/screenshot20111109at123.png/)

The result is 5.1 watts.

BTW, the ambient temperature is 73 F (23 C) and as you can see, the proximity temp is 38 C.  Under Ubuntu, I can barely get under 50 C and that's with the rc=6 kernel boot option, which would support the evidence gathered from XBattery that OS X is using less power.

I'm not trying to dis Ubuntu. On the contrary, I'd rather use Ubuntu than OS X (I've used Linux exclusively for 10 years) and I'm confirming to myself and to others that Ubuntu currently is less efficient than OS X on this hardware.  With that fact established, I hope that I can work with others to identify and rectify issues related to power consumption.

Is there a better place to organize issues, test results, and solutions related to this topic?  I don't want to pollute the official wiki (and confuse users who stumble upon it), but rather have a working area.  The forum is nice, but this effort could benefit from better organization.

---

### Post by jebus_beler on 2011-11-09
@berryman7:  thanks for the info.  I would definitely be interested if you're looking to systematically try to find the sources of power drain on the laptop.  As i said, I've managed to get ubuntu down to 7.2 W by using a 2-d interface and turning off wifi and reducing screen brightness.  This was not an artificial test ... it was just the natural state of the laptop as I read a pdf when commuting on a train.  But shaving off another two watts would be great (and doing this while compositing would be even better).  

I'm not really sure how to start about doing this but powertop is one useful tool.  I think it shows a lot of wakeup from the i915 driver so this might be the first problem.  This might be addressable by the fix suggested here (section <interrupt> i915@pci):

[http://www.lesswatts.org/projects/powertop/known.php]("http://http://www.lesswatts.org/projects/powertop/known.php")

But only if you don't need 3d (i.e. no compositing).  

Actually the majority of wakeups are "interprocessor interrupts" due to "local interrupts" -- not really sure what this is.

There's also some stuff in the lin above about the apple multitouch driver.  I don't know if the patch is in the mainline kernel or it should be applied.

---

### Post by jebus_beler on 2011-11-09
I've had additional issues trying to suspend after plugging in a DVI adapter.  If I use an external screen on a DVI adapter (probably same for VGA) and then disconnect the adapter and close the laptop it won't suspend.  At first I thought this was just a bug but I'm now guessing its related to a "feature gone wrong'...namely the ability to work with only an external screen by shutting the main screen.  In any case I found that if  I unplug the external screen and then suspend from the ubuntu menu (rather than by shutting the screen) it works fine.  After waking from resuming the behavior goes back to normal and closing the lid causes a suspend.  All this is not ideal but at least I now can use my laptop an on external screen and still be able to suspend and use it normally afterwards without having to reboot.

I'll also add that plugging/unplugging an external screen seems to work fine so long as the laptop display stay the "main" display (i.e. the one with the title bar in the OS-X-ripped off "Display" preferences screen in Ubuntu).  If you switch to the external display as main then all hell breaks lose when you try to disconnect it (or even try to set the laptop display back to being the main one).  But if you stick with the laptop as the main display you seem to get reasonable behavior.

Anyone else getting any better behavior?

---

### Post by hueythecat on 2011-11-10
4,1 - 11" Update

xorg-edgers ppa: Still no dice on 3d desktop

---

### Post by jebus_beler on 2011-11-11
> **hueythecat said:**
> 4,1 - 11" Update

xorg-edgers ppa: Still no dice on 3d desktop

Yeah sorry I should have said the same is true on 13" 4,2 (maxed out).  So I went back to using gnome classic no effects and the standard drivers.  Seems much more stable if painful.

Huey have you tried just compiz (no unity)?  To do so disable unity from compiz configuration manager and then install the PPA and enter gnome classic.  Then start compiz from the terminal "compiz --replace".  I might do this later as I want to isolate whether compiz or the unity plugin is causing all my stability issues.

Btw here's another useful power link:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=4](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=4)

---

### Post by jebus_beler on 2011-11-11
@berryman7:

Here are some more tools for power debugging.  I'll try to try them out eventually but several involve rebooting and resetting grub params and right now I actually need to work on my laptop so can't do that ;->

First powertop on 11.10 doesn't show interrupts so its best to get the latest source and compile it as explained here:

[http://www.lesswatts.org/projects/powertop/download.php](http://www.lesswatts.org/projects/powertop/download.php)

This is much more informative!

I noticed I get mostly rescheduling interrupts:

  23.5% ( 89.0)   [Rescheduling interrupts] <kernel IPI>

so i found this page with some useful explanations:

[https://help.ubuntu.com/community/ReschedulingInterrupts](https://help.ubuntu.com/community/ReschedulingInterrupts)

but I haven't had time to do much with that.  If anyone has any success reducing their power usage please do tell.

---

### Post by dfacto on 2011-11-13
To those wanting to use this version of powertop:
```

FN='powertop-1.13'
if [ ! -f ${FN//-/_}-1_amd64.deb ]; then
    URL='http://www.lesswatts.org/projects/powertop/download'
    [ -f $FN.tar.gz ] || wget "$URL/$FN.tar.gz"
    sudo aptitude install libncursesw5-dev libncurses5-dev gettext
    sudo aptitude remove powertop
    tar xzvf $FN.tar.gz
    cd $FN
    make
    fakeroot checkinstall -yD make install
    mv ${FN//-/_}-1_amd64.deb ..
    cd ..
    sudo dpkg -i ${FN//-/_}-1_amd64.deb
fi

```

---

### Post by hueythecat on 2011-11-13
Unity 3D works fine for me on standard xorg - and given my smaller screen its grown on me.

(I "REALLY" don't like the new gnome look IMHO)

But I have to disable mtrack in the xorg.conf.

The only real problem I have now is that sometimes the trackpad dies on me randomly, I then have to plug a mouse in.

---

### Post by leeyc0 on 2011-11-15
I am using the 13" model.

I found that I cannot use xorg-edgers, otherwise I cannot login to desktop (the screen is blank except background wallpaper).

For mtrack, I found that I need to tweak /etc/X11/xorg.conf to have the trackpad working properly.

Replace the whole mtrack InputClass with the following:
```

Section "InputClass"

    Identifier       "Multitouch Touchpad"
    Driver           "mtrack"
    MatchDevicePath  "/dev/input/event*"
    MatchIsTouchpad  "on"
    Option           "CorePointer"     "true"
    Option           "Sensitivity"     "0.65"  #    1 : movement speed
    Option           "ScrollDistance"  "100"   #  150 : two-finger drag dist for click
    Option           "ClickTime"       "25"    #   50 : millisec to hold emulated click
    Option           "ClickFinger1"    "0"
    Option           "ClickFinger2"    "3"
    Option           "TapButton1"      "1"
    Option           "TapButton2"      "3"
    Option           "TapButton3"      "2"
    Option           "ScrollUpButton"  "5"
    Option           "ScrollDownButton" "4"
    Option           "ButtonTouchExpire" "0"
    Option           "GestureWaitTime" "200"
#   Option           "ThumbSize"       "35"    #   25 : min size of thumb
#   Option           "PalmSize"        "55"    #   40 : min size of palm
EndSection # "Multitouch Touchpad"


```The ScrollUpButton and ScrollDownButton are swapped from the default to have the same "more natural" behaviour as MacOS.

Also, to have 2 finger+click = right click, I have to set ClickFinger2 to 3. Also, you need to set ButtonTouchExpire to 0, otherwise 2 finger+click works only when you put the 2 fingers on touchpad and press the trackpad button simultaneously.

After editing xorg.conf, restart lightdm service (service lightdm restart) or simply reboot to make new config effective

The meaning of the options are documented in
[https://github.com/BlueDragonX/xf86-input-mtrack](https://github.com/BlueDragonX/xf86-input-mtrack)

---

### Post by markbl on 2011-11-15
> **leeyc0 said:**
> 
I found that I cannot use xorg-edgers, otherwise I cannot login to desktop (the screen is blank except background wallpaper).

The xorg edgers launchpad ppa site had a note that the ppa could not be used with Unity 3D. However, that was fixed in the ppa updates today. So you could enable it again now and you should find that Unity 3D works. Gnome-shell has worked all along and is better than Unity anyhow ;)

PS I am a linux guy who has never had a Mac but am looking around here because the current offer of intel ultrabooks is so pathetic.

---

### Post by dfacto on 2011-11-15
> **markbl said:**
> 
PS I am a linux guy who has never had a Mac but am looking around here because the current offer of intel ultrabooks is so pathetic.

You're in good company--many of us here share this sentiment.

---

### Post by jebus_beler on 2011-11-15
> **markbl said:**
> The xorg edgers launchpad ppa site had a note that the ppa could not be used with Unity 3D. However, that was fixed in the ppa updates today. So you could enable it again now and you should find that Unity 3D works. Gnome-shell has worked all along and is better than Unity anyhow ;)

PS I am a linux guy who has never had a Mac but am looking around here because the current offer of intel ultrabooks is so pathetic.

Thanks for the pointer.  I can confirm that the xorg edgers ppa suddenly works with unity 3d which was never the case for me before.

---

### Post by jebus_beler on 2011-11-18
Will also add...since switching to xorg-edgers my resume problems seem to have gone away even using unity/compiz.  So I guess that was the difference between my setup and many other peoples.  In any case the whole linux experience is becoming much much nicer.  Thanks for all help everyone here!

---

### Post by poliva on 2011-11-18
@jebus_beler: weird, I'm not using xorg-edgers and never had a suspend/resume problem at all.

---

### Post by jebus_beler on 2011-11-18
I must have bungled something on my install but somehow when running compiz (with or without unity) resumes would consistently fail within a couple of cycles (usually less than 5).  Disabling compiz and just using gnome classic resolved the problem and I also never noticed in in KDE (though I didn't run the latter for long).  But now with the new xorg-edgers I don't have this problem.  Not sure why but am just very happy its gone!

---

### Post by jebus_beler on 2011-11-18
> **leeyc0 said:**
> I am using the 13" model.

I found that I cannot use xorg-edgers, otherwise I cannot login to desktop (the screen is blank except background wallpaper).

For mtrack, I found that I need to tweak /etc/X11/xorg.conf to have the trackpad working properly.

Replace the whole mtrack InputClass with the following:
```

Section "InputClass"

    Identifier       "Multitouch Touchpad"
    Driver           "mtrack"
    MatchDevicePath  "/dev/input/event*"
    MatchIsTouchpad  "on"
    Option           "CorePointer"     "true"
    Option           "Sensitivity"     "0.65"  #    1 : movement speed
    Option           "ScrollDistance"  "100"   #  150 : two-finger drag dist for click
    Option           "ClickTime"       "25"    #   50 : millisec to hold emulated click
    Option           "ClickFinger1"    "0"
    Option           "ClickFinger2"    "3"
    Option           "TapButton1"      "1"
    Option           "TapButton2"      "3"
    Option           "TapButton3"      "2"
    Option           "ScrollUpButton"  "5"
    Option           "ScrollDownButton" "4"
    Option           "ButtonTouchExpire" "0"
    Option           "GestureWaitTime" "200"
#   Option           "ThumbSize"       "35"    #   25 : min size of thumb
#   Option           "PalmSize"        "55"    #   40 : min size of palm
EndSection # "Multitouch Touchpad"


```The ScrollUpButton and ScrollDownButton are swapped from the default to have the same "more natural" behaviour as MacOS.

Also, to have 2 finger+click = right click, I have to set ClickFinger2 to 3. Also, you need to set ButtonTouchExpire to 0, otherwise 2 finger+click works only when you put the 2 fingers on touchpad and press the trackpad button simultaneously.

After editing xorg.conf, restart lightdm service (service lightdm restart) or simply reboot to make new config effective

The meaning of the options are documented in
[https://github.com/BlueDragonX/xf86-input-mtrack](https://github.com/BlueDragonX/xf86-input-mtrack)

@leecy0:  I'm currently using the synaptic drivers (default) which actually work quite well except they don't support click plus drag and that's annoying so I'm thinking of trying your mtrack config.  With synaptic i seem to have the trackpad nicely disabled while typing.  I had setup syndaemon manually and used to have to restart it after resumes but it now seems to be mysteriously behaving very well (not complaining but its nice to see stuff all come together).  I'm a little worried that I'll spoil this nice setup by switching to mtrack -- does it require dispad or something to disable the trackpad while typing?  Would be useful to hear what people are doing to sort out trackpad while typing.  My syndaemon options are as follows:

syndaemon -i 2 -d -t -K

---

### Post by tlee on 2011-11-20
First of all, I have to say that I am extremely pleased to be running Linux again.  Been with OS X since I bought the MBA last summer, and it has been maddening.  Finally worked up the courage to try putting Ubuntu on this weekend.  Great success.  Much gratitude to everyone for the hard work.

I am encountering one small problem that I can't figure out... my option and command keys keep getting switched.  The command key will function as the "alt" key, but then after waking up from a suspend, it's the option key that functions as "alt."

Any thoughts?

---

### Post by ceti331 on 2011-11-20
anyone know if linux wm's can be setup to trigger expose/spaces on trackpad gestures , & 3 finger drag... the pinnacle of desktop management IMO was SnowLeopard with multitouch.
I would be interested in configurations such as pinch to 'zoom out' (show desktops) or maybe multiple fingers to drag and resize windows simultaneously

---

### Post by sinzui on 2011-11-21
I have upgraded to 3.0.0-13-generic and ran the post install script before rebooting. X does not start properly. I was able to get it to start after several attempts from recovery mode, but the resolution is buggered. Could fix-i915.sh be incompatible?

I am running 3.0.0-12-generic for the time being.

---

### Post by Murphy2712 on 2011-11-21
> **jebus_beler said:**
> Thanks for the pointer.  I can confirm that the xorg edgers ppa suddenly works with unity 3d which was never the case for me before.

In my case Unity 3D is now launching (both top bar and left bar), but it's still not fully working:
- no alt-tab to switch between windows,
- no alt-right/left to switch between desktops.

My alt key is working well otherwise.
Any hint?

---

### Post by jebus_beler on 2011-11-21
I'm also very glad to be running Linux as for a while I was worrying that it wouldn't happen.  Its still not perfect but my current setup is much more stable than it used to be and with some trackpad fixes and battery life improvements will not want for functionality over OS X.

@tlee:  I had the same issue.  The post install script sets up a resume script to reload Xmodmaps on wakeup but the latter fails because for some reason its called when the X environment isn't fully setup yet.  I actually like using the "command" key as a super key so I just removed the ~/.Xmodmap (which also implements annoying reverse scrolling btw -- so called natural scrolling).  I also removed the script 00_usercustom that the post-install script sets up in /etc/pm/sleep.d.  Unfortunately if you do want the keys reversed I'm not sure how to fix this though maybe someone else can pipe in.

@ceti331:  first I guess you might need the touchegg drivers to do this.  Not sure if compiz has support for gestures yet but you can look in CompizConfigSettings.  I noticed KDE does allow one to define arbitrary actions for gestures.  I for one use hot corners (which are supported by Compiz via CompizConfigSettings) and that's good enough for me.  If you get gestures to work, either via mtrack or touchegg, then please let us know. 

@sinzui: Is this part of the latest ubuntu update (haven't run it myself) or did you do something special?  I'm loath to break my install by updating with some borked kernel.

@Murphy2712:  sounds weird.  i had something happen in gnome2d.  I would recommend installing CompizConfigSettings and try setting whichever window-switcher you prefer to use alt-tab.  Btw try super-tab as well since that's often set to be an alternate window-switcher.  This can also be used to configure switching desktop (and all other) shortcuts.

---

### Post by hueythecat on 2011-11-21
What are the chances- I finally transition to my mba this morning and the kernal update screws my resolution(mba 4,1).

Running the fix-i915.sh presently

---

### Post by hueythecat on 2011-11-21
How do you boot back to 3.0.0-12 - its not in the grub menu?

My resolution is poked even after running post-install on 3.0.0-13

---

### Post by hueythecat on 2011-11-21
Ok 

I'm beyond my depth here - but I noticed the the problem was the patch not applying to the intel_bios.c

I manually pasted over (based on you panel model)

panel_fixed_mode->hdisplay = 1366;
+	panel_fixed_mode->hsync_start = 1398;
+	panel_fixed_mode->hsync_end = 1566;
+	panel_fixed_mode->htotal = 1734;
+	panel_fixed_mode->vdisplay = 768;
+	panel_fixed_mode->vsync_start = 772;
+	panel_fixed_mode->vsync_end = 776;
+	panel_fixed_mode->vtotal = 792;
+	panel_fixed_mode->clock = 72500;
+	panel_fixed_mode->type = 0x48;
+	panel_fixed_mode->flags = 0xa;
+	drm_mode_set_name(panel_fixed_mode);
 	drm_mode_debug_printmodeline(panel_fixed_mode);
 
(but not this) 	temp_mode = kzalloc(sizeof(*temp_mode), GFP_KERNEL);
It gave me an error and was specified already in the file

then followed the rest of the shell script - running native res on my mba4,1 linux kernel 3.0.0.13 now.

Some strange things happening though:

My dash overlay is launching windowed not full screen & my alt-tab gui is basic(small icons) not fancy gui.

---

### Post by Murphy2712 on 2011-11-22
> **jebus_beler said:**
> 
@Murphy2712:  sounds weird.  i had something happen in gnome2d.  I would recommend installing CompizConfigSettings and try setting whichever window-switcher you prefer to use alt-tab.  Btw try super-tab as well since that's often set to be an alternate window-switcher.  This can also be used to configure switching desktop (and all other) shortcuts.

You're right, super-tab works!
I think the keyboard layout is wrong, I have other issues with keys and unity-3d:
- changing the keyboard backlight doesn't work,
- volume keys are shifted (mute=F9, vol down=F10, vol up=F11, eject(!??)=F11),
- super does not open the left bar.

I noticed another minor problem: when using the usb-to-ethernet cable, after sleep/resume, it does not connect to network, I need to unplug/replug.


Today I updated some packages and had no login screen when rebooting.
=> I needed "nomodeset".
I've run post-install-oneiric.sh but it didn't help.
Then I downloaded and run "sudo ./fix-i915.sh" and now it works again (with full resolution) :KS

---

### Post by sinzui on 2011-11-22
@hueythecat I recall the grub menu has an item names something like "previous linux" which will list the older kernels.

---

### Post by poliva on 2011-11-22
> **berryman77 said:**
> 
BTW, the ambient temperature is 73 F (23 C) and as you can see, the proximity temp is 38 C.  Under Ubuntu, I can barely get under 50 C and that's with the rc=6 kernel boot option, which would support the evidence gathered from XBattery that OS X is using less power.

On Linux the proximity temperature is on applesmc-isa-0300/TC0P, I am getting approximately the same results on OS X than on Ubuntu (using unity2D). My proximity temp is around 39ºC to 42ºC when the laptop is idle:

```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +52.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +51.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   1999 RPM  (min = 2000 RPM)
TB0T:         +30.0°C - Battery TS_MAX Temp 
TB1T:         +30.0°C - Battery TS1 Temp 
TB2T:         +27.8°C - Battery TS2 Temp 
TC0C:         +47.8°C  
TC0D:         +45.5°C - CPU 0 Die Temp 
TC0E:         +49.5°C  
TC0F:         +51.2°C  
TC0P:         +41.8°C - CPU 0 Proximity Temp 
TC1C:         +52.0°C  
TC2C:         +51.0°C  
TCGC:         +47.0°C  
TCSA:         +43.0°C  
TH0F:        +249.0°C *EXCLUDED* 
TH0J:        +249.0°C *EXCLUDED*
TH0O:        +249.0°C *EXCLUDED*
TH0o:         +28.0°C  
THSP:         +37.2°C  
TM0P:         +40.8°C  
TPCD:         +48.0°C  
Ta0P:         +44.0°C  
Th1H:         +31.0°C  
Tm0P:         +39.0°C - Battery Charger Proximity Temp 
Tm1P:         +42.5°C  
Ts0P:         +28.2°C - Palm Rest Temp 

```

---

### Post by dfacto on 2011-11-22
The post-install sets-up my preferences (which are more PC-like).  

...You can comment out the natural scrolling if you don't like it.

...Feel free to comment out the code which sets the shift-special settings.

---

### Post by diafygi on 2011-11-22
Hey all, I've been using the MBA 4-2 for a while without issue (after I followed the instructions on the wiki). But yesterday when I updated, the display appears to have shifted and now overlapping on the bottom and right sides. Everything is still usable, but is there any way to expand the display back to the full screen size?

Here's a picture. Notice how the right and bottom edges of the display end early, then restart the display.

[http://i.imgur.com/v9Cof.jpg](http://i.imgur.com/v9Cof.jpg)

---

### Post by hueythecat on 2011-11-22
No strange things - Unity had launched in 2d not 3d - all good in 3d

---

### Post by jebus_beler on 2011-11-23
@huey:  so just to be sure.  After updating you just reran fix_i915 but without the line:

```

  temp_mode = kzalloc(sizeof(*temp_mode), GFP_KERNEL);

```

And you have everything back up and running like normal?

---

### Post by poliva on 2011-11-23
@jebus_beler: just upgrade the kernel normally, then reboot with the "nomodeset" kernel parameter and re-run the post-install-oneiric script to have the kernel modules updated. It should patch keyboard, trackpad and bluetooth modules, then the i915 module. Once it finishes updating the modules just quit.

All patches are ok, and everything works fine after upgrading. hueythecat probably had problems because he applied the patch to an already patched source... if you are having the same problem remove the mba4-temp directory and re-run the script again (it will re-download the sources, and apply the patch clean).

---

### Post by ChinaSailor on 2011-11-24
> **diafygi said:**
> Hey all, I've been using the MBA 4-2 for a while without issue (after I followed the instructions on the wiki). But yesterday when I updated, the display appears to have shifted and now overlapping on the bottom and right sides. Everything is still usable, but is there any way to expand the display back to the full screen size?

Here's a picture. Notice how the right and bottom edges of the display end early, then restart the display.

[http://i.imgur.com/v9Cof.jpg](http://i.imgur.com/v9Cof.jpg)


Had the same exact problem last week when I updated via 'Update-Manager'
this was xubuntu with xfce (no gnome-3 stuff), and another thing I noticed was that there were about 10 more monitor settings, going all the way up to (2080 x 1800 or something ridiculous like that, the fonts and icons will be so small you could fit 10 Desktops in there).

Just re-run dfacto's post-install script, that's what I did, works like a charm.

---

### Post by ChinaSailor on 2011-11-24
Has anyone been able to get the plug-able Iphone / Ipod support working..?
I am not sure if it's a hardware conflict with the new 3.0 kernel or what, but I have a 2010 MBA with Natty and once I installed the libimobiledevice, everything worked 4.0 (regardless of what IOS, even 5.0). But with the latest MBA 4.2, I have tried installing every / all the different mobile libs available for the 3.0 kernel / oneiric, but nothing seems to work, it does not get recognized.[I] Didn't noticed any significant dmesg's

[/I][LEFT]
[/LEFT]

---

### Post by zmiq2 on 2011-11-24
Hi, I recently bough my macbook air 11'', and since this week update, I'm faced with the same issues regarding the screen.

I have solved it:

the issue is that the fix-915-sh script downloads linux version 3.2.0 (from one of the added ppa sources), while ubuntu's kernel is 3.0.0-13.

I have done through the process of downloading the ubuntu linux kernel, manually apply the patch included in the fix-i915.sh script, and manually run the configuration and install commands, and everything is back to normal again!!

For anyone here who doesn't want to go through all these, and has the same environment as mine:

product name: MacBookAir4,1
panel type:LTH116AT01A04
OS:ubuntu, kernel 3.0.0-13-generic

To know your exact computer model, open a terminal and run the following commands:

for product name:
cat /sys/class/dmi/id/product_name

for panel type:
grep -B2 "EDID (in hex)" /var/log/Xorg.0.log | head -n 1|cut -b30-

for OS:
uname -r

I'm posting [here the i915.ko module already compiled.]("https://sites.google.com/site/spareinfosite/Home/i915.ko?attredirects=0&d=1")

Instructions are:
- **as root**, copy downloaded file in the following directories:
/lib/modules/3.0.0-13-generic/extra/
/lib/modules/3.0.0-13-generic/kernel/drivers/gpu/drm/i915/ 

- reboot, and you are done!

HTH

---

### Post by zmiq2 on 2011-11-24
Hi again,

everyhting seems ok now, but sound: when I go to 'Sound Preferences', 'Output', in 'Connector' option I only have 'Analog Headphones' available, so the speakers are not working.

In 'Sound Preferences'->'Hardware', i have the Profile 'Analog Stereo Duplex' selected.

Any ideas how to restore built-in speakers?

Thanks

---

### Post by poliva on 2011-11-24
> **zmiq2 said:**
> Any ideas how to restore built-in speakers?

sudo alsamixer

---

### Post by zmiq2 on 2011-11-24
and then? what do I have to do in alsamixer? everything there seems ok ....


=> it's ok now; it seems that 'Surrond' was too low (how the heck that happened?)

Thanks!!

---

### Post by ChinaSailor on 2011-11-24
> **zmiq2 said:**
> and then? what do I have to do in alsamixer? everything there seems ok ....


=> it's ok now; it seems that 'Surrond' was too low (how the heck that happened?)

Thanks!!

(just checked the surround sound settings, no effect)

So you are using alsamixer to get audio working..?
When I installed ubuntu, the first thing I checked was the alsamixer settings, but I still didn't have any sound, so my next course of action was to apt-get remove pulse-audio, (which has worked for me a number of times getting sound to work) but in this case, did nothing.

Any hints about getting sound working?

---

### Post by zmiq2 on 2011-11-25
Hi ChinaSailor,

pulse audio needs to be installed; once you have it, go to alsamixer and make sure that 'Master', 'Headphones', 'PCM',  'Front Sp' and 'Surround' are at max level (the label below the bars should display 00, MM means 'muted')

HTH

---

### Post by thebino on 2011-11-25
Hi zmiq2,

your [i915.ko module]("https://sites.google.com/site/spareinfosite/Home/i915.ko?attredirects=0&d=1") dosn't work for me ;(
I think becaus i've the 13" Air

perhaps you can explain how to patch itself or compile witch patch?

product name: MacBookAir4,2
panel type: P133WP1-TJA3
OS:ubuntu, kernel 3.0.0-13-generic

Thx Bino

---

### Post by zmiq2 on 2011-11-25
> **thebino said:**
> Hi zmiq2,

your [i915.ko module]("https://sites.google.com/site/spareinfosite/Home/i915.ko?attredirects=0&d=1") dosn't work for me ;(
I think becaus i've the 13" Air

perhaps you can explain how to patch itself or compile witch patch?

product name: MacBookAir4,2
panel type: P133WP1-TJA3
OS:ubuntu, kernel 3.0.0-13-generic

Thx Bino

Hi Bino,

yes, the reason it doesn't work is because both the product name and the panel type are different!

Since I have al the environment already setup, I just compiled the module for your macbook air, for free!

You can [download  it here]("https://sites.google.com/site/spareinfosite/Home/i915.ko.mba13?attredirects=0&d=1"). Remember, after downloading, to rename the file to i915.ko and then follow the easy install instructions. Please report back whether or not it works for you.



HTH

---

### Post by thebino on 2011-11-25
Thx HTH for your work, but it dosn't work anyway ;(

Bootoptions: quiet splash i915.i915_enable_rc6=1

I've tried without i915.i915_enable_rc6=1

Only boot WITH "nomodeset" (where no resolution Change to (1440 × 900) is available)

---

### Post by markbl on 2011-11-25
I just bought a 13" 256GB MacBook Air yesterday and tried installing ubuntu today following the community guide. However, as above, my screen only appears at 1024x768. Also the trackpad does not seem to work correctly and there are probably other issues I have not seen in the 10 mins I have spent in Unity.

I am a bit disillusioned when I see how much munging around that post-install-oneiric.sh does. With all that, clearly the installation will be very fragile to ubuntu package updates (and particularly xorg-edgers etc) as we see here. Is running ubuntu on this thing really feasible? Or should I just resign myself to running ubuntu within VirtualBox?

---

### Post by jebus_beler on 2011-11-26
Well its up to you to decide how much effort is worth it to you but you sound like you're intent on using linux anyway.  I haven't tried virtualbox in OS X and maybe its almost as smooth but I max out the ram on this machine a lot so can't afford that kind of overhead.  I probably had more problems than most people on this forum but when the dust settled its very nice having a running ubuntu on this machine.  The way I see it things should only get better and right now they're pretty alright.  For update, etc... it does sound like a pain but to be honest I have the same issue with my desktop because I run some development nvidia modules.  I just don't let ubuntu update that often and then realize I'll have to baby sit it when it does.  Hopefully in the next release of ubuntu this machine will be supported out of the box.

---

### Post by dfacto on 2011-11-26
@markbl ..."fragile"...? I have no idea what this could mean.  I assure you though, there is no fragility.  Packages have configurations.  My script alters the configurations.  "Clearly" it is designed to work this way.  Type "man man" for more details.

@zmiq2 Instead of sharing a binary, wouldn't it be easier to just share your tool chain (the commands you used to build the source).  I'm guessing you merely ran the fix-i915.sh script and are now polluting the thread with dated binaries for only some of the modelines.

I had hoped to set a precedent by adding comments and listing all the steps to build binaries (even when it could just be downloaded from my site). Many (most) appreciate this attempt...some...do not.  If you want to show off your mad linux "skillz," please tell us *how* you did something. Don't just plop some binary on the forum and expect praise to be showered upon you. You'll have none from me.

---

### Post by thebino on 2011-11-27
I found a kernel wich supports my display:

[http://kernel.ubuntu.com/~sarvatt/macbook-air/](http://kernel.ubuntu.com/~sarvatt/macbook-air/)

---

### Post by jebus_beler on 2011-11-28
I'm guessing this is not an MBA specific problem so I'll probably post elsewhere but I just wanted to ask if anyone is experiencing weird network lock-ups of the following sort.  Often when my MBA tries to connect to an encrypted wireless network it gets caught in some weird race condition and my logs are full of things like:
```

Nov 24 11:28:48 sliver kernel: [88782.761236] INFO: task wpa_supplicant:1185 blocked for more than 120 seconds.
Nov 24 11:28:48 sliver kernel: [88782.761240] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 24 11:28:48 sliver kernel: [88782.761245] wpa_supplicant  D 0000000000000001     0  1185      1 0x00000000
Nov 24 11:28:48 sliver kernel: [88782.761253]  ffff880167ad38f8 0000000000000082 0000000000000282 ffff880167ad3908
Nov 24 11:28:48 sliver kernel: [88782.761262]  ffff880167ad3fd8 ffff880167ad3fd8 ffff880167ad3fd8 0000000000012a40
Nov 24 11:28:48 sliver kernel: [88782.761271]  ffff880164028000 ffff880167abae40 ffff880167ad38d8 ffff880168f77160
Nov 24 11:28:48 sliver kernel: [88782.761279] Call Trace:
Nov 24 11:28:48 sliver kernel: [88782.761288]  [<ffffffff815e8e27>] __mutex_lock_slowpath+0xd7/0x150
Nov 24 11:28:48 sliver kernel: [88782.761327]  [<ffffffffa0196d3f>] ? nl80211_trigger_scan+0xff/0x500 [cfg80211]
Nov 24 11:28:48 sliver kernel: [88782.761337]  [<ffffffff815e8a3a>] mutex_lock+0x2a/0x50
Nov 24 11:28:48 sliver kernel: [88782.761361]  [<ffffffffa01e026e>] ieee80211_request_scan+0x2e/0x60 [mac80211]
Nov 24 11:28:48 sliver kernel: [88782.761387]  [<ffffffffa01ee7e9>] ieee80211_scan+0x69/0x90 [mac80211]
Nov 24 11:28:48 sliver kernel: [88782.761410]  [<ffffffffa0197081>] nl80211_trigger_scan+0x441/0x500 [cfg80211]
```Moreover after this the rest of the machine works fine but anything trying to access the network just hangs (e.g. running "ifconfig" from the terminal) and nothing I do besides a reboot helps.

At first I thought this was just a random thing with my wireless at home but now I notice that it seems to happen on many wireless networks.  For my wireless at home somehow rebooting the router solves the problem but obviously I can't do this on a general wireless.

If anyone has seen something similar or has some idea where I might go to start debugging this please let me know.

---

### Post by zmiq2 on 2011-11-28
@Bino,

- my bootoptions are quiet splash i915.i915_enable_rc6=1 vt.handoff=7

- I'm disappointed the built module doesn't work for you; on the other hand, I'm glad that you found a kernel that works four you!

@markbl

I think running ubuntu on this machine is completely worth the effort! Probably a more methodic / reliable method for doing the upgrades in sync with ubuntu updates is needed. I find myself spending like 2 hours a week to keep my mba correctly setup...

@jebus_beler

In my mba I had wifi connecting issues when I had little coverage. With just one bar (whatever that means), it kept he network manager connecting /disconnecting; I moved closer to my access point, and then I had a reliable connection. I hoped the network manager to give a more friendly message like 'cannot connect, signal too low', because Even with 1 bar I expected to connect without issues. Maybe it's not related to your problem, just in case it might work

---

### Post by jebus_beler on 2011-11-29
> **poliva said:**
> @jebus_beler: just upgrade the kernel normally, then reboot with the "nomodeset" kernel parameter and re-run the post-install-oneiric script to have the kernel modules updated. It should patch keyboard, trackpad and bluetooth modules, then the i915 module. Once it finishes updating the modules just quit.

All patches are ok, and everything works fine after upgrading. hueythecat probably had problems because he applied the patch to an already patched source... if you are having the same problem remove the mba4-temp directory and re-run the script again (it will re-download the sources, and apply the patch clean).

A quick note on the update for those who haven't done it yet.  If you're using xorg-edgers first disable the PPA (don't purge, just uncheck it in software sources) or else the script tries to download kernel 3.2 from the PPA and then all the patches break.  This might have been the problem huey was having.  To upgrade I first removed (actually just renamed) my old mba4-tmp dir and then ran the post-intall-oneiric script just up to the point when its done building the modules (to be sure I actually copied the script and deleted everything after that but I acknowledge that this is overkill :-) ).  After upgrading things seem to work as before (so far).

---

### Post by poliva on 2011-11-29
> **jebus_beler said:**
> If you're using xorg-edgers first disable the PPA (don't purge, just uncheck it in software sources) or else the script tries to download kernel 3.2 from the PPA and then all the patches break.

Ah that was it! damn xorg-edgers, why do you people use it? what's the benefit? I have been using my MBA without xorg-edgers since the beginning and have had no issues at all (upgrading daily without problems).

---

### Post by jebus_beler on 2011-11-29
Strange as it may sound my system is _much_ more stable with xorg-edgers.  While xorg-edgers didn't work with unity/compiz I basically had to switch to unity-2d because I compiz/unity would consistently crash on resume after a few cycles.  After xorg-edgers fixed their issue and became unity compatible I started using them and my resume problems went away.  A lot of other problems simultaneously went away (trackpad niggles and unity funkiness) but maybe it was due to unrelated ubuntu updates.  Do you use compiz without xorg-edgers?

---

### Post by poliva on 2011-11-29
> **jebus_beler said:**
> Do you use compiz without xorg-edgers?

No, i'm using unity-2d since day 1, i don't like all those fancy 3d effects :)

---

### Post by hueythecat on 2011-11-29
WOW! One person other than me running Ubuntu on the MBA 4,1

I had the same problem with the kernel update. I thought the issue was the patch for the gpu driver not applying. I manually edited to resolve. But I've found stuff like bluetooth etc is also no longer working too.

---

### Post by poliva on 2011-11-29
> **hueythecat said:**
> WOW! One person other than me running Ubuntu on the MBA 4,1

Just got one for my girlfriend today, already running Ubuntu on the MBA 11" too now :)

> **hueythecat said:**
> But I've found stuff like bluetooth etc is also no longer working too.

run the post-install-oneiric.sh script again, it patches 4 modules:
- hid-apple (keyboard)
- bcm5974 (trackpad, only for 11")
- btusb (bluetooth)
- i915 (screen)

make sure you delete the "mba4-tmp" folder first, and disable xorg-edgers prior to running the script as pointed out by jebus_beler a few hours ago.

---

### Post by zmiq2 on 2011-11-30
Hi all,

I'm having trouble with my external monitor after a resume.

After resum, it doesn't show gnome, just a violetish background; pressing ctr-alt-f1, ctr-alt-f7 doesn't reset that external monitor, so after resume I have to reboot in order to have the external monitor working again.

BTW, I'm using gnome3 with all 3d effects, and it's kind of nice!

Any ideas?

Thanks.

---

### Post by jebus_beler on 2011-11-30
I had problems using an external monitor but not at the level of resuming but simply even unplugging it and plugging it back in didn't work (I've posted about this here or on other threads a while ago).  I found that if I didn't set the external display to be the main display (in ubuntu's display tool) then I didn't have these problems and I could plug/unplug the external display and even do it after suspend/resume.  This was with gnome classic and the standard xorg drivers.  I've been meaning to do it with xorg-edgers but haven't yet.  If I manage to I'll let you know how it goes.

---

### Post by jebus_beler on 2011-11-30
> **leeyc0 said:**
> I am using the 13&quot; model.

I found that I cannot use xorg-edgers, otherwise I cannot login to desktop (the screen is blank except background wallpaper).

For mtrack, I found that I need to tweak /etc/X11/xorg.conf to have the trackpad working properly.

Replace the whole mtrack InputClass with the following:
```

Section &quot;InputClass&quot;

    Identifier       &quot;Multitouch Touchpad&quot;
    Driver           &quot;mtrack&quot;
    MatchDevicePath  &quot;/dev/input/event*&quot;
    MatchIsTouchpad  &quot;on&quot;
    Option           &quot;CorePointer&quot;     &quot;true&quot;
    Option           &quot;Sensitivity&quot;     &quot;0.65&quot;  #    1 : movement speed
    Option           &quot;ScrollDistance&quot;  &quot;100&quot;   #  150 : two-finger drag dist for click
    Option           &quot;ClickTime&quot;       &quot;25&quot;    #   50 : millisec to hold emulated click
    Option           &quot;ClickFinger1&quot;    &quot;0&quot;
    Option           &quot;ClickFinger2&quot;    &quot;3&quot;
    Option           &quot;TapButton1&quot;      &quot;1&quot;
    Option           &quot;TapButton2&quot;      &quot;3&quot;
    Option           &quot;TapButton3&quot;      &quot;2&quot;
    Option           &quot;ScrollUpButton&quot;  &quot;5&quot;
    Option           &quot;ScrollDownButton&quot; &quot;4&quot;
    Option           &quot;ButtonTouchExpire&quot; &quot;0&quot;
    Option           &quot;GestureWaitTime&quot; &quot;200&quot;
#   Option           &quot;ThumbSize&quot;       &quot;35&quot;    #   25 : min size of thumb
#   Option           &quot;PalmSize&quot;        &quot;55&quot;    #   40 : min size of palm
EndSection # &quot;Multitouch Touchpad&quot;


```The ScrollUpButton and ScrollDownButton are swapped from the default to have the same &quot;more natural&quot; behaviour as MacOS.

Also, to have 2 finger+click = right click, I have to set ClickFinger2 to 3. Also, you need to set ButtonTouchExpire to 0, otherwise 2 finger+click works only when you put the 2 fingers on touchpad and press the trackpad button simultaneously.

After editing xorg.conf, restart lightdm service (service lightdm restart) or simply reboot to make new config effective

The meaning of the options are documented in
[https://github.com/BlueDragonX/xf86-input-mtrack](https://github.com/BlueDragonX/xf86-input-mtrack)

I'm currently running mtrack with the above options but I found that the  touchpad is not actually being disabled while I type (i.e. I'm  accidentally moving and pressing the cursor).  I think mtrack has  options to enable this (disableonthump, disableonpalm) but they seem  disabled in the above config for some reason.  I was wondering how  people are managing with disabling the touchpad while typing.  Do you  have to run dispad along with mtrack or are the mtrack options enough.   Does anyone have a better config than the above?

---

### Post by poliva on 2011-11-30
@jebus_beler: AFAIK mtrack does not have an option to disable the trackpad while typing. It has some options to ignore bogus thumb and palm gestures (IgnoreThumb, DisableOnThumb, ThumbRatio, ThumbSize and s/Thumb/Palm/), see the full list of options here:

[https://github.com/BlueDragonX/xf86-input-mtrack](https://github.com/BlueDragonX/xf86-input-mtrack)

---

### Post by leeyc0 on 2011-11-30
> **jebus_beler said:**
> I'm currently running mtrack with the above options but I found that the  touchpad is not actually being disabled while I type (i.e. I'm  accidentally moving and pressing the cursor).  I think mtrack has  options to enable this (disableonthump, disableonpalm) but they seem  disabled in the above config for some reason.  I was wondering how  people are managing with disabling the touchpad while typing.  Do you  have to run dispad along with mtrack or are the mtrack options enough.   Does anyone have a better config than the above?

It's just because I didn't have much test for this :(, I was just testing the possibility on installing ubuntu on macbook air but never actually using it yet, and I just left it aside afterwords when it seems worked.

Most probably you will need dispad to disable trackpad while typing...

---

### Post by hueythecat on 2011-11-30
> **poliva said:**
> 
make sure you delete the "mba4-tmp" folder first, and disable xorg-edgers prior to running the script as pointed out by jebus_beler a few hours ago.

Thanks for the heads up!

---

### Post by hueythecat on 2011-11-30
re: xorg.conf mtrack

    Option           "ScrollUpButton"   "5"
    Option           "ScrollDownButton" "4"

Swap 4 and 5 around if you prefer normal scrolling (my laptop isn't an ipad thanks)

---

### Post by jebus_beler on 2011-12-01
Yeah the xorg config I got from leecy0 has Civilized Scrolling (my laptop never was, is, or will be an ipad :-)  ) but what are you using for touchpad disabling, huey?  

@poliva: yeah thanks sorry I think my post was confusing.  I didn't mean actually disabling the touchpad while typing as it obviously wasn't doing that.  But I figured that while typing most "taps" are palm sized so if you have it configured to ignore the palm that's almost as good.  Does anyone know how OS X does this?  I haven't used it in a while but I don't remember this being much of an issue on OS X but I doubt they disable the touchpad while typing as its always responsive afterwards.

With e.g. syndaemon and the synaptic driver you sometimes annoyingly have to wait a second or whatever time you pick before you can use the touchpad again -- its always tradeoff between accidental hits and waiting for an irresponsive trackpad.  I was hoping that a multitouch trackpad with "palm detection" could just avoid this issue.  So I was wondering if anyone has played with the "palm" and "thumb" setting of mtrack with the goal of avoiding extra hits while typing.  Or is everyone using dispad?  And if so how well does it work?  Even without the palm settings I find I'm somehow hitting the trackpad less now then I was with synaptic driver but maybe I'm just being more careful :-)

---

### Post by leeyc0 on 2011-12-01
> **jebus_beler said:**
> Yeah the xorg config I got from leecy0 has Civilized Scrolling (my laptop never was, is, or will be an ipad :-)  ) but what are you using for touchpad disabling, huey?  

@poliva: yeah thanks sorry I think my post was confusing.  I didn't mean actually disabling the touchpad while typing as it obviously wasn't doing that.  But I figured that while typing most "taps" are palm sized so if you have it configured to ignore the palm that's almost as good.  Does anyone know how OS X does this?  I haven't used it in a while but I don't remember this being much of an issue on OS X but I doubt they disable the touchpad while typing as its always responsive afterwards.

With e.g. syndaemon and the synaptic driver you sometimes annoyingly have to wait a second or whatever time you pick before you can use the touchpad again -- its always tradeoff between accidental hits and waiting for an irresponsive trackpad.  I was hoping that a multitouch trackpad with "palm detection" could just avoid this issue.  So I was wondering if anyone has played with the "palm" and "thumb" setting of mtrack with the goal of avoiding extra hits while typing.  Or is everyone using dispad?  And if so how well does it work?  Even without the palm settings I find I'm somehow hitting the trackpad less now then I was with synaptic driver but maybe I'm just being more careful :-)


Unfortunately it is still true using mtrack. It needs a dispad daemon (also available from BlueDragonX's website), which is also simply disabling trackpad for a while after typing, but at least you can change the hold time by editing ~/.dispad file....

---

### Post by poliva on 2011-12-01
This helps if you want to "customize" the dispad settings in ~/.dispad config file, for example:

disable = X

A value of 1 will disable tapping and gestures but not movement.
A value of 2 will disable all input
A value of 3 will disable all input and physical buttons


1) Kill existing dispad instances:

$ killall dispad

2) Run in foreground debug mode to test

$ dispad -F -D

---

### Post by hueythecat on 2011-12-01
->but what are you using for touchpad disabling, huey?


Not sure what you mean by this - please explain.

---

### Post by hueythecat on 2011-12-01
After clearing mba-tmp and xorg-edgers and running post-install all well except for bluetooth on my 4,1.

---

### Post by poliva on 2011-12-01
what's the problem with bluetooth? it works well on my 4,1 after running post-install script with kernel 3.0.0-13-generic.

---

### Post by jebus_beler on 2011-12-02
@dfacto:  I've found that adding asix usbnet to the following line in /etc/pm/config.d/macbookair_fix brings back eth0 after suspend:

SUSPEND_MODULES="bcm5974 usbhid asix usbnet"

Unless someone finds this causes them a problem maybe you could add this to the post-install-oneiric.sh (which now only has bcm5974 and usbhid).

---

### Post by jebus_beler on 2011-12-02
> **hueythecat said:**
> ->but what are you using for touchpad disabling, huey?


Not sure what you mean by this - please explain.

I mean disabling the touchpad while typing.  I'm guessing you're using dispad since that's what post-install-oneiric sets up.

---

### Post by poliva on 2011-12-02
> **dfacto said:**
> I confirm that hibernate does not work.  After resuming hibernate, selecting kernel from grub, the system pauses on a blank purple-ish screen.  After a timeout it reboots back to refit and selecting the kernel again results in a non-resumed session.

Just got hibernation working :D

It's as simple as adding the resume parameter with the correct swap partition to the kernel boot options. Example:

In my case, swap is at /dev/sda5 so I updated /etc/default/grub as follows:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 resume=/dev/sda5"

```

after making this change, remember to run 'sudo update-grub'.
Tested a few times and hibernation works without issues now :)

---

### Post by ChinaSailor on 2011-12-03
-

---

### Post by markbl on 2011-12-04
I just psyching myself up to try this install again but have some questions. The community wiki says to install rEFIt but I don't think this is necessary is it? I just used the OS X disk utility and split my main Mac partition in 2 leaving the new space spare and then the ubuntu installer seemed happy to partition that space as necessary. I prefer to keep things as simple so is that the recommended approach (granted that Bootcamp won't work which would be ideal)?

Also, I have not been through this entire thread but what "special notes" do I currently have to deal with. E.g. the first time I tried this last week I could not get the screen to work correctly but recent comments here imply that the fix for this is to disable the xorg-edgers ppa. Where was that ppa installed? It does not seem to be referenced in post-install-oneiric.sh?

I am happy to document my exact steps somewhere as I find that community wiki a bit of a hodge-podge of confusing references for different generation MBAs. My MBA is a current 2011 13" 256GB i5 with Samsung screen and Samsung SSD.

---

### Post by poliva on 2011-12-04
> **markbl said:**
> The community wiki says to install rEFIt but I don't think this is necessary is it?

I haven't tried without rEFIt, I guess it's not necessary but convenient to dual boot OS X and Ubuntu. Are you doing a pure-EFI install?

> **markbl said:**
> ...disable the xorg-edgers ppa. Where was that ppa installed? It does not seem to be referenced in post-install-oneiric.sh?

It's installed by "fix-i915.sh", which is downloaded and executed from post-install-oneiric.

---

### Post by poliva on 2011-12-04
If you want to enable automatic keyboard brightness level, based on the ambient light sensor (just as OS X does), you can install lightum:

```

sudo add-apt-repository ppa:poliva/lightum-mba
sudo apt-get update
sudo apt-get install lightum

```

I've put the source code on github:

[https://github.com/poliva/lightum](https://github.com/poliva/lightum)

---

### Post by markbl on 2011-12-04
> **poliva said:**
> I haven't tried without rEFIt, I guess it's not necessary but convenient to dual boot OS X and Ubuntu.

Can I ask why it is more convenient? I just did as I said above and could get a list of boot disks simply by pressing the option button at boot time. I can also change the default via the OS X "Startup Disk" setting. That's convenient enough for me and probably most.

> 
Are you doing a pure-EFI install?

Don't really know what you mean but given the procedure I stated above then I guess that is "pure-EFI" as I just partitioned the disk via the OSX disk utility and then just ran the ubuntu installer from a USB drive. That's all.

I tried this ubuntu install a few days ago but gave up in frustration after the screen problem and re-partitioned my disk all back to OSX. I was away on holidays and only had dodgy 3G internet though. Now I am back home I may try again.

---

### Post by khilman on 2011-12-05
Trying to get an analog stereo headset with mic working on my MacBookAir4,1.

Stereo output to the headset works fine, but can't get the mic working (works fine in OSX.)

Under System Settings -> Sound, I have the 'Analog Stereo Duplex' profile selected.  Going to the 'Input' tab, I have a choice of 4 connectors: 

- Analog Line-in
- Rear Microphone
- Analog Microphone
- Internal Microphone

Using the last two, I get input working via the mic on the MBA, but none of them seem to select the headset mic.

Any ideas?

---

### Post by hueythecat on 2011-12-05
try running alsamixer from the command line

---

### Post by khilman on 2011-12-06
> **hueythecat said:**
> try running alsamixer from the command line

Tried that already, and verified the various capture inputs were all unmuted, and volumes raised.  Didn't help.

I think the problem has do to with detection of a headset with mic in the headphones jack.  When I plug in the headset with mic under OSX, it detects it and switches the input from 'internal microphone' to 'external microphone'.  I suspect I just need to tell tne HDA intel driver to do the same, but don't know how.

---

### Post by jaduncan on 2011-12-08
Here comes a new challenger!

I have a machine that fails out on the fix-i915.sh script like so:

"ERROR: 'MacBookAir4,1/#@06' not recognized"

It is the new 11 inch Air with 256GB SSD.

What can I do to

a) make the display work, and;
b) what useful commands would the devs like me to copy the results of?

---

### Post by dfacto on 2011-12-08
Give us the output of
```
sudo get-edid 2>/dev/null
```
and attach
```

gzip -c /var/log/Xorg.0.log >Xorg.0.log.gz

```

---

### Post by artik1024 on 2011-12-10
Great !!

Many things works now on my 11 inch 2011 with Natty. Many thanks for the kernel 3.1.0 patched given by other member earlier that saved my life ! (Dfacto, your script doesn't run on a 11 inch / Natty ... what a pity ;))

Now one of the lastest things to do is map correctly the FN buttons (volume up / down, adjust keyboard backlight..)

I tried to ptch the file, but got an error :

```
artik /linux-3.1.0/drivers/hid sudo patch -p2 <hid-apple.patch
patching file hid-ids.h
Hunk #1 FAILED at 112.
1 out of 1 hunk FAILED -- saving rejects to file hid-ids.h.rej
patching file hid-core.c
Hunk #1 FAILED at 1343.
1 out of 1 hunk FAILED -- saving rejects to file hid-core.c.rej
patching file hid-apple.c
Hunk #1 succeeded at 104 (offset 22 lines).
Hunk #2 FAILED at 205.
Hunk #3 succeeded at 537 with fuzz 2 (offset 19 lines).
1 out of 3 hunks FAILED -- saving rejects to file hid-apple.c.rej

```

A little help could be welcome, here is original (or if someone could patch mine please)

---

### Post by jennie_p on 2011-12-11
I've had my Air about a week now, and although the Ubuntu installation was kind of scary, everything seems to be working great now. Big thanks to everyone who worked on this!

So, now I'm thinking of simply deleting my osx partition and single-booting ubuntu. I've been using Ubuntu exclusively for 4.5 years now, so, on any other laptop I wouldn't hesitate. But seeing as this is my first Apple product, I thought I'd ask first. Will I be safe, or is there a high enough probability that I'll end up with an unusable machine at some point in the future?

Also, can I follow the standard [guide for single-booting]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Single-Boot:_Ubuntu_Only"), or are there any MBA4.2-specifics I must be aware of? I've got the 13-inch 4.2 model.

Finally, I probably wouldn't mind keeping the osx partition, if only I could bring it down to around 15GB. But, I resized the partitions with disk utility from inside osx, and it wouldn't let me go under 28GB. Is there a solution to that?

---

### Post by jonny on 2011-12-11
I'd be wary of deleting OS X, as, without it, you won't be able to snag any future firmware updates.  I'm no OS X expert - like you, I use Ubuntu almost exclusively - but, when I needed to release some space from my OS X partition, I found that by far the easiest way was to go back to the command line: du to find the space-hogging files and rm to zap them permanently.  After some judicious pruning, you might be able to relase some extra space.  Also note that gparted claims to be able to shrink hfs+ file systems.  Never tried it myself, though.

---

### Post by jebus_beler on 2011-12-12
> **artik1024 said:**
> Great !!

Many things works now on my 11 inch 2011 with Natty. Many thanks for the kernel 3.1.0 patched given by other member earlier that saved my life ! (Dfacto, your script doesn't run on a 11 inch / Natty ... what a pity ;))



Can you say a bit more about running 3.1 on oneiric with the MBA (or could someone else)?  This article:

[http://www.phoronix.com/scan.php?page=article&item=intel_snb_linux31&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_linux31&num=1)

Suggests that there should be a significant speed improvement over 3.0 and i was wondering if this was noticeable.  I've also noticed that after a while (maybe after running virtualbox or going through suspend/resume cycles) compiz starts eating more CPU and consequently battery life goes down and tearing while moving windows becomes more noticeable.  I was hoping some driver improvements would fix this.  Anyone else notice that the system becomes less responsive and there's more idle cpu usage (via X or compiz) after a while?

---

### Post by ChinaSailor on 2011-12-13
Has anybody updated via the "Update Manager" recently, like last 1.5 days..?

There have been quite a few changes and some kernel patches, and after the update, the display resolution is totally screwed. I re-ran the post-install script, and re-removed the nomodeset from the grub.cfg, and everything seems to go back to normal, but this time, the track-pad driver will work for about a minute and a half, and then you will lose the track-pad, your cursor will be frozen, and will not return, no matter how many times you remove / re-insert the modules. Luckily if you have a usb mouse, that will still work, but the track-pad will be dead, until the next re-boot.

Anyone experiencing this problem..?


Any ideas when the macbook air changes will finally make it into the official ubuntu repository, so that every time we update, we don't have run a bunch of hand made scripts, just to get back to normal again..?

Thank you in advance!

(and please leave the attitude at the door, we're all adults here, you have no idea who's at the other end of the terminal....)

---

### Post by poliva on 2011-12-14
> **ChinaSailor said:**
> Anyone experiencing this problem..?

Fully updated as of today, running kernel 3.0.0-14 on both MBA4,2 and MBA4,1. Not experiencing issues at all.

---

### Post by artik1024 on 2011-12-14
> **jebus_beler said:**
> Can you say a bit more about running 3.1 on oneiric with the MBA (or could someone else)?

Im under Natty ;)

---

### Post by hueythecat on 2011-12-14
> **ChinaSailor said:**
>  
Anyone experiencing this problem..?



Yeah - My 4,1 upgraded 1-2 days ago from 3.0.0.13 -> .14 after reboot I got the usual bad video. 
But things then went SUPER LAGGY i.e couldn't login, mouse super unresponsive. 
So I went back to .13.

I tried again this morning with the same results. Instead of giving up I dropped to console and ran the post install from there.

AND SUCCESS
Posting this very message from my 3.0.0.14 install.

PS

Whats all this about a 3.1 kernel patch? Share the knowledge please.

---

### Post by hueythecat on 2011-12-14
After several reboots I can confirm there is major lag between login and unity.

The only difference between .14 and .13 I can note is the .14 post install did not use the xorg-edgers repository.

Can any one else confirm?

---

### Post by ChinaSailor on 2011-12-14
> **hueythecat said:**
> After several reboots I can confirm there is major lag between login and unity.

The only difference between .14 and .13 I can note is the .14 post install did not use the xorg-edgers repository.

Can any one else confirm?

Wow, just noticed there is an updated post-install-oneiric.sh.
I am running a 13" MBA 4.2, no unity, I'm using xfce, so haven't noticed any lag, just the track-pad freezing up after 1.5 mins. So I can plug a usb mouse in and the cursor will jump to life, but with the mouse, I do notice some strange keyboard input type issues... I.E... when using the mouse, sporadically, then keyboard input will either lag or completely miss keyboard input, I.E... If you Type "ABCD", it may pick up, "BCD" or "CD."

I will have to run the latest post-install when I get within range of a high-speed internet connection.

Thanks.

---

### Post by rubiojr on 2011-12-15
I upgraded to Precise in my MBA 4,1 and had to go back to the Oneiric kernel because of that. Keyboard doing really weird things. Not sure if related to your issue though:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903655)

---

### Post by ChinaSailor on 2011-12-15
> **hueythecat said:**
> After several reboots I can confirm there is major lag between login and unity.

The only difference between .14 and .13 I can note is the .14 post install did not use the xorg-edgers repository.

Whats all this about a 3.1 kernel patch? Share the knowledge please.

Can any one else confirm?


Ok, as far as my MBA 4.2 neither post-install-oneiric.sh 
(one from more than a month ago or newest one dated 4 DEC) did anything toward resolving the frozen cursor issue. I've had the 3.0.0-14-generic (Oneiric) for more than a month, and never had any issues until that "Update" about 3 days ago. I did notice with the latest post-install-oneiric script, that it prompts you to select (1) track-pad something, and (2) touch-egg something, I selected "1" but I saw in the output that it selected (the script) a bunch of "touch-egg" stuff. So I am not exactly sure what it installed or configured.

Also not sure what you mean by 3.1 kernel patch (I haven't looked at individual patch names, if that's what you're referring too) I wasn't aware if there was an actual 3.1 kernel on the streets? (in any case, I do not have it)

When I mentioned "Update-Manager," I meant exactly that, just update existing packages, not upgrade the ubuntu version. Still at 3.0.0-14-generic (Oneiric) and as of today (16 Dec 2011) just ran the latest updates (there was at least one xorg-edgers in there) and still have the frozen cursor. I did time it exactly, the trackpad will work for approximately 40 seconds, before it freezes up.

Any specific kernel modules I might want to try re-loading..? Because it works fine for 40 seconds, then something else gets loaded or starts and the trackpad dies.

Thanks in advance!

---

### Post by poliva on 2011-12-15
@ChinaSailor:

1) remove the xorg-edgers ppa: sudo ppa-purge xorg-edgers
2) delete the file xorg.conf: sudo rm /etc/X11/xorg.conf
3) delete the file touchegg autostart: sudo rm ~/.config/autostart/touchegg.desktop
4) re-run the latest version of post-install-oneiric.sh, not only the first part (kernel modules) but also the second part (system configuration). When prompted to choose the trackpad driver choose option 1.

After that, reboot and mouse should be working.

---

### Post by ChinaSailor on 2011-12-16
> **poliva said:**
> @ChinaSailor:

1) remove the xorg-edgers ppa: sudo ppa-purge xorg-edgers
2) delete the file xorg.conf: sudo rm /etc/X11/xorg.conf
3) delete the file touchegg autostart: sudo rm ~/.config/autostart/touchegg.desktop
4) re-run the latest version of post-install-oneiric.sh, not only the first part (kernel modules) but also the second part (system configuration). When prompted to choose the trackpad driver choose option 1.

After that, reboot and mouse should be working.


Thank you for the help,
unfortunately, still doesn't work, I'm assuming you mean the cursor (not usb mouse) when you say, "mouse should be working," because that's the only thing that has been working consistently.

Followed your instructions to the letter, but now, the cursor, doesn't even work upon boot up (usb external mouse still works though, as before) With the last configuration, the normal trackpad cursor would give me about 40 seconds of use before it froze up, now, it's DOA...
But thanks for the suggestions.

---

### Post by ChinaSailor on 2011-12-16
> **poliva said:**
> @ChinaSailor:

1) remove the xorg-edgers ppa: sudo ppa-purge xorg-edgers
2) delete the file xorg.conf: sudo rm /etc/X11/xorg.conf
3) delete the file touchegg autostart: sudo rm ~/.config/autostart/touchegg.desktop
4) re-run the latest version of post-install-oneiric.sh, not only the first part (kernel modules) but also the second part (system configuration). When prompted to choose the trackpad driver choose option 1.

After that, reboot and mouse should be working.


Ok, Resolved...
I re-added ppa: org-edgers/ppa, updated,
then blacklisted the following modules:

bnep
btusb
rfcomm

Back to normal working state, minus the bluetooth (which I never used anyway)
So 'evidentially' one of these (or the hid module(s) which drive the trackpad) has changed in the last five days, and now causes some conflicts in / or with the user space modules.

---

### Post by ChinaSailor on 2011-12-17
> **ChinaSailor said:**
> Ok, Resolved...
I re-added ppa: org-edgers/ppa, updated,
then blacklisted the following modules:

bnep
btusb
rfcomm

Back to normal working state, minus the bluetooth (which I never used anyway)
So 'evidentially' one of these (or the hid module(s) which drive the trackpad) has changed in the last five days, and now causes some conflicts in / or with the user space modules.

Scratch that fix, too soon.
I found that, after a cold reboot, (instead of simply logging out) the problem returns, 
at about the same time frame approximately 40~ seconds after logging in. 

What appears to fix the problem is simply booting up, logging in, then, waiting a minute or two, then logging out, and Re-logging back in again. No idea, why this works, same modules are getting loaded (and reloaded).
(fyi xfce and xubuntu)

---

### Post by hueythecat on 2011-12-18
arrgg. If it aint broke dont fix it.
Just ran the new post install on my 4,1. Broke my video again.
Rolled back and now my trackpad no longer works. 
Crap

---

### Post by hueythecat on 2011-12-19
Whos using a 4,1 mba?

If so what touchpad drivers are you using?

---

### Post by zmiq2 on 2011-12-20
I have a 4,1; i'm using the touchpad drivers setup by the post-install-oneiric.sh script, and seems to work ok.

What I'm having trouvle with is with resume and external monitor; any hints?

Thanks.

---

### Post by pr0ximity on 2011-12-23
Hi all, having some issues installing on my 4,2 MBA.

I've followed the instructions to the T, however my installation always hangs on the step in installation after a WiFi network is selected, where partitions are setup. If I run in Live mode first, then install, I get a bug report saying that GParted has failed. If I try and run GParted from Live, it immediately hangs indefinitely with a similar error.

I originally guessed this had something to do with my prior installation of Windows 7 via bootcamp possibly messing with my partitions, however after completely re-partitioning (into 3, I'm attempting a triple boot with 7, starting with Ubuntu) the problem persists.

After some searching online, it seems in some older installations of Ubuntu ([http://ubuntuforums.org/showthread.php?t=1518764](http://ubuntuforums.org/showthread.php?t=1518764)), GParted crashes when USB devices, SD cards, etc. are connected to the PC. However, as I'm installing from my USB drive, I'm not sure how to remedy the situation if that's the case, and why it doesn't seem to be a problem for others.


Any ideas aside from completely wiping the SSD of OS X and all?

---

### Post by ChinaSailor on 2011-12-25
> **pr0ximity said:**
> Hi all, having some issues installing on my 4,2 MBA.

I've followed the instructions to the T, however my installation always hangs on the step in installation after a WiFi network is selected, where partitions are setup. If I run in Live mode first, then install, I get a bug report saying that GParted has failed. If I try and run GParted from Live, it immediately hangs indefinitely with a similar error.

I originally guessed this had something to do with my prior installation of Windows 7 via bootcamp possibly messing with my partitions, however after completely re-partitioning (into 3, I'm attempting a triple boot with 7, starting with Ubuntu) the problem persists.

After some searching online, it seems in some older installations of Ubuntu ([http://ubuntuforums.org/showthread.php?t=1518764](http://ubuntuforums.org/showthread.php?t=1518764)), GParted crashes when USB devices, SD cards, etc. are connected to the PC. However, as I'm installing from my USB drive, I'm not sure how to remedy the situation if that's the case, and why it doesn't seem to be a problem for others.


Any ideas aside from completely wiping the SSD of OS X and all?

I have an MBA 4.2, currently running the 11.10 (without unity)
I am not exactly sure why it's using gparted... I don't remember gparted being run, unless that's the default format tool, but I thought it used fdisk, I may be wrong. 

I am not exactly sure the instructions you followed, but basically, use the Mac Disk Utility in Mac to create your partition (you can select vfat, it doesn't matter what type, it will be changed).

I highly recommend using he "Alternate Install CD" (I didn't follow the usd directions, you can use ANY cd rom that will connect via usb for the CD install) The USB (via USB memory stick) install is a bit involved, unless you like spending a lot of time, use the CD.

Boot the Alternate CD (holding 'C' will cause mac to boot cd)
Select F6 -> Nomodeset
Standard Install 
When the format tool (I believe this is just a graphical wrapper for fdisk) opens, 
select the partition that you created in Mac (Not the Mac partition)
then click on the partition, partition type = ext3 or 4 and "mount point /" and 'Y' the Format Flag
(It might just toggle an 'F' can't remember, self explanatory)
(don't touch 'Bootable'  Flag, just leave the default)
(before you select "Finish" you can optionally create a swap partition) But probably not needed.

Continue on with standard install.
It's not that difficult, but use Alternate CD.

Hope this helps.

---

### Post by berryman77 on 2011-12-29
> **berryman77 said:**
> I'm having problems resuming too.  I typically get a screen with just the background image and no menus.  Sometimes if I go to a VT and restart lightdm (sudo restart lightdm), it helps and sometimes I just have to shut down.

As a follow up on this message, I consistently see this same problem. After resuming from suspend (with nothing connected to the laptop), I plug into an external monitor via HDMI and see nothing but the background color.  In the kernel logs, I see:

```

[drm:drm_mode_getfb] *ERROR* invalid framebuffer id

```

which coincides with the external monitor activation.

---

### Post by berryman77 on 2011-12-29
After applying [Other Power Saving Tips]("https://help.ubuntu.com/community/MacBookAir4-2#Other_Power_Saving_tips") (thanks Poliva), I can get the power usage just under 8 watts in ideal circumstances.  This is still nearly 3 watts above OS X.  I've tried different approaches to reduce power usage further including monitoring/satisfying powertop, killing every unnecessary process and unloading kernel modules.  Still I can't get close to the 4.8 watts OS X achieves.  I'm wondering if BIOS emulation could be the culprit.  How likely is it that BIOS emulation could be chewing 2-3 watts?

---

### Post by shivamurti on 2011-12-30
> **dfacto said:**
> 

# (1) Get my patched bcm5974 driver.
# You can find the source in: [http://www.almostsure.com/bcm5974](http://www.almostsure.com/bcm5974)
# ref: [http://bitmath.org/code/bcm5974-dkms/](http://bitmath.org/code/bcm5974-dkms/)
wget [http://www.almostsure.com/bcm5974/bcm5974-dkms_1.1.91_all.deb](http://www.almostsure.com/bcm5974/bcm5974-dkms_1.1.91_all.deb)



403 Forbidden :(

---

### Post by pr0ximity on 2011-12-30
> **ChinaSailor said:**
> ...
The USB (via USB memory stick) install is a bit involved, unless you like spending a lot of time, use the CD.
...
Hope this helps.

Not to be rude, but unfortunately, no.

I'm looking to install via a USB drive, as I don't own a USB CD drive, and would rather not buy one just to install Ubuntu.

---

### Post by leeyc0 on 2011-12-31
> **pr0ximity said:**
> Not to be rude, but unfortunately, no.

I'm looking to install via a USB drive, as I don't own a USB CD drive, and would rather not buy one just to install Ubuntu.

You may find the steps at
[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

---

### Post by Wolfador on 2012-01-01
I can't get my touchpad to work when using xf86-input-mtrack. It seems to work okay when I re-ran the script and selected touchegg. Is there anything I am missing by not using mtrack?

---

### Post by mediamind on 2012-01-02
Hey Everyone,

I'm running 3.0.0-14 on a Macbook Air 4,2 with mtrack. I've played around with the **[mtrack configuration settings]("https://github.com/BlueDragonX/xf86-input-mtrack")** but can't figure out how to activate the Unity Grab handles via the touchpad. 

Any suggestions?

---

### Post by uBeer on 2012-01-04
> **pr0ximity said:**
> Not to be rude, but unfortunately, no.

I'm looking to install via a USB drive, as I don't own a USB CD drive, and would rather not buy one just to install Ubuntu.

I found a page with a working solution: [http://userpages.uni-koblenz.de/~ceinig/howto/artikel.php?id=92](http://userpages.uni-koblenz.de/~ceinig/howto/artikel.php?id=92)

Has anybody tested Precise on the MBA already?

---

### Post by Wolfador on 2012-01-04
> **pr0ximity said:**
> Not to be rude, but unfortunately, no.

I'm looking to install via a USB drive, as I don't own a USB CD drive, and would rather not buy one just to install Ubuntu.

I used UNetBootin to create my USB key. Just pointed it to the iso.

To prep for the install, I used disk utility to shrink my OSX parititon and left the new space as free.

---

### Post by shivamurti on 2012-01-05
Having problems with suspend on a Macbook Air 4.2 (Samsung LCD & 256GB SSD).

When I'm closing the lid the apple would stay lit for a sec and then backlight is switches off.
If I open the lid - everything is ok, I'm promted for a password.

But in above situation, if I won't open the lid immediately, after a couple of seconds the logo would lights and dims again. Then when I'm opening the lid afterwards the screen behaves crazy: either I can see the desktop but everything is laggy, have a lot of special effects or I just get a screen of random waves of light like northern lights.

I have been trying to install Ubuntu on this machine for about a week now. And it seems that I'm the only one having this issue.

---

### Post by Wolfador on 2012-01-06
> **shivamurti said:**
> 
But in above situation, if I won't open the lid immediately, after a couple of seconds the logo would lights and dims again. 

mine does that also but it corrects itself after a second and prompts for the password. 

maybe try running just the i915 script? 

```
wget -Nq http://www.almostsure.com/mba42/fix-i915.sh
./fix-i915.sh

```
should reinstall everything for the display without messing with anything else.

---

### Post by shivamurti on 2012-01-06
> **Wolfador said:**
> 
maybe try running just the i915 s cript?

Didn't work. I've already tried reinstalling system a  few times and running script part by part.
By the way, my panel number is LTH133BT01A03.

Tomorrow I will post a video of those 'special effects'.

Here's the video:
[http://youtu.be/GBuYbb3-ly4](http://youtu.be/GBuYbb3-ly4)

---

### Post by davidpitkin on 2012-01-08
Hi,

Great news, I just upgraded a clean install and update of 11.10 to 12.04 (Precise) and everything on my Air is working flawlessly. This is on a MacBookAir4,1 (11") and without running the post-isntall-oneiric.sh script.

I still have some getting used to the default touchpad behavior and will post my progress.

Previously in Oneiric/11.10 my touchpad would not work sometimes without installing a external mouse first and video support after each kernel update was a problem.

---

### Post by deanproxy on 2012-01-08
Is anyone having trouble with suspend?

My 4,2 will not suspend.  Whenever I close the lid or click on suspend in the gnome shell menu, it appears to start to suspend but then wakes back up and stays awake.  the screen stays on the lock screen.

Any suggestions to fix this? Last night my battery died cause I thought it suspended when it didn't and found out this was why...

---

### Post by mrmorris on 2012-01-08
I have the problem that, no matter which key layout I use (i.e. the default Danish, Macintosh) for my 4.2 Air, I can not enable "3'rd level" characters (pipe |, back-slash \, at-sign @ etc.) similar to how Alt-Gr behaves on a PC. 

Instead when I use the Right Alt, I get a context popup (Menu).

As far as I an tell, this giant thread does not mention others with this problem, though I am able to find other references to the problem: [http://javahacker.com/?p=189e](http://javahacker.com/?p=189e)

Does anyone else have any advice as to what could be going on here? I am fairly sure that, at some point, I did see Right-Alt work as the 3'rd level selector as I would expect.

---

### Post by uBeer on 2012-01-08
> **davidpitkin said:**
> Hi,

Great news, I just upgraded a clean install and update of 11.10 to 12.04 (Precise) and everything on my Air is working flawlessly. This is on a MacBookAir4,1 (11") and without running the post-isntall-oneiric.sh script.

Cool! I wanted to try it out, but I have to use my machine the coming few weeks for some important stuff so I'd rather not upgrade just yet. But this makes me more happy to upgrade after my exams/projects are over :P

---

### Post by poliva on 2012-01-09
> **mrmorris said:**
> I have the problem that, no matter which key layout I use (i.e. the default Danish, Macintosh) for my 4.2 Air, I can not enable "3'rd level" characters (pipe |, back-slash \, at-sign @ etc.) similar to how Alt-Gr behaves on a PC.

Check the [xmodmap section of the wiki](https://help.ubuntu.com/community/MacBookAir4-2#Keyboard_functions_.28Brightness.2Cvolume.2C....29).

---

### Post by deanproxy on 2012-01-09
> **deanproxy said:**
> Is anyone having trouble with suspend?

My 4,2 will not suspend.  Whenever I close the lid or click on suspend in the gnome shell menu, it appears to start to suspend but then wakes back up and stays awake.  the screen stays on the lock screen.

Any suggestions to fix this? Last night my battery died cause I thought it suspended when it didn't and found out this was why...


after testing, I found that suspend works fine when the battery is fully charged.  it will not suspend after it starts to lose a charge. how very odd....

---

### Post by mrmorris on 2012-01-09
> **poliva said:**
> Check the [xmodmap section of the wiki](https://help.ubuntu.com/community/MacBookAir4-2#Keyboard_functions_.28Brightness.2Cvolume.2C....29).

Thanks. The pof settings worked for me (except now I think scrol direction is reversed).

---

### Post by deanproxy on 2012-01-09
> **deanproxy said:**
> after testing, I found that suspend works fine when the battery is fully charged.  it will not suspend after it starts to lose a charge. how very odd....

Oddly enough, I did a reinstall and this appears to have fixed my suspend issue.  I don't know how or why.  If I figure it out or it happens again, I'll update...

---

### Post by mrmorris on 2012-01-09
Have anyone experimented with inverting the scroll direction as per the new default in Mac OSX Lion? I had gotten used to this little change (the only thing about OSX Lion I found more intuitive).

---

### Post by poliva on 2012-01-10
> **mrmorris said:**
> Have anyone experimented with inverting the scroll direction as per the new default in Mac OSX Lion? I had gotten used to this little change (the only thing about OSX Lion I found more intuitive).

Edit ~/.Xmodmap and change the following line (note 5 and 6 are permuted):

scrolling like in OS X default:
```
pointer = 1 2 3 5 4 6 7 8 9 10 11 12 
```

scrolling reversed:
```
pointer = 1 2 3 4 5 6 7 8 9 10 11 12 
```

---

### Post by deanproxy on 2012-01-10
For some reason the "Natural Scrolling" is enabled by default with my install. I didn't have to do anything special to get it to do it...

---

### Post by hueythecat on 2012-01-10
FYI 

I just finished doing a 12.04 upgrade on my 4,1 using the mac amd64 daily iso

Early days - but everything just works with no tweaks scripts etc.

Only thing I can note that is - no click drag out of the box.

Video ok
Bluetooth ok

My 11.10 install was fine but I screwed it by re running a newer post-install
 
This "just works" and I'm happy :D

---

### Post by deanproxy on 2012-01-10
I figured out what my suspend issue was...  It wouldn't suspend whenever I had a filesystem mounted.  I had a filesystem mounted as sshfs and whenever I do, it would not suspend.  Unmounting the filesystem would allow it to suspend properly.

---

### Post by User4519 on 2012-01-11
> **hueythecat said:**
> FYI 

I just finished doing a 12.04 upgrade on my 4,1 using the mac amd64 daily iso

Early days - but everything just works with no tweaks scripts etc.

Only thing I can note that is - no click drag out of the box.

Video ok
Bluetooth ok

My 11.10 install was fine but I screwed it by re running a newer post-install
 
This "just works" and I'm happy :D

Good to hear! I've been putting off replacing OS X on mine for a while, as I hacked it enough to make it usable, but lately I've been wondering about exactly that - 12.04 and how it'd fare out-of-the-box. I'm sick of the horrible hardware support on Mac OS X. Every little update breaks something and you have to get drivers from somewhere and hope they work. Currently, I cannot get either my 100 Mbit or 1 Gbit USB ethernet dongles to work - both of which work OOTB in Linux.

I miss my Linux on this baby. Looking forward to 12.04. I think that'll be my first try :)

---

### Post by uBeer on 2012-01-11
> **hueythecat said:**
> FYI 

I just finished doing a 12.04 upgrade on my 4,1 using the mac amd64 daily iso

Early days - but everything just works with no tweaks scripts etc.

Only thing I can note that is - no click drag out of the box.


Have you tried three finger drag??? :D

I loaded a live install for a quick look and found out that touchpad support is quite good, especially in comparison with 11.10!
Nice to see that probably nothing needs patching with the next release!

---

### Post by hueythecat on 2012-01-12
> **uBeer said:**
> Have you tried three finger drag??? :D




What sorcery is this......... :P


I have now - no good for scrolling

---

### Post by uBeer on 2012-01-12
> **hueythecat said:**
> What sorcery is this......... :P


I have now - no good for scrolling

New updated driver magic!
Two-finger scrolling can be enabled in the mouse properties in the tab touchpad.

---

### Post by mrmorris on 2012-01-13
Really really happy about my Ubuntu Macbook Air setup, except for one thing... every time my left fingers touch the lower part of the touchpad, tracking of my right hand (cursor navigation) halts - very annoying compared to how it behaves on OSX.

Any suggestions around this problem using the "xf86-input-mtrack" driver? I would be happy with only the physical button, lowering the sensitivity of the pad, disable tracking on the lower part... or a combination hereof. I can't imagine being the only one with this "overly sensitive" trackpad.

---

### Post by engla on 2012-01-13
I'm waiting for my Macbook Air 13" to arrive. Is it rude to ask for a summary of this thread? 

Things should be much better for linux on sandy bridge and macbook air-2011 now than it was half a year ago. The recent 3.2 kernel fixes further bugs with graphics, says phoronix: [http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTQ)

Maybe the wiki page is a good summary, in that case, looks complicated!

---

### Post by modulationz on 2012-01-14
Has anyone been able to get a single-boot system setup using an EFI based method as opposed to the "BIOS compatibility" method that is outlined here ([https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation%29?"))?  I have been having no luck getting this working.  The archlinux macbook wiki page gives me some hope that this is possible in Ubuntu, but I haven't been able to figure it out yet. Any tips would be appreciated!

---

### Post by engla on 2012-01-14
There's a comparatively simple Howto for Arch here: [http://d.goodlad.net/articles/arch_linux_on_mba_42/](http://d.goodlad.net/articles/arch_linux_on_mba_42/)  has anyone tried something similar for Ubuntu (use only GPT, install grub manually)?

---

### Post by artik1024 on 2012-01-16
Woaw ! 12.04 daily build is amazing, everything works outofbox (keyboard backligt, suspend, screen resolution, screen backlight ...).

Since Kernel 3.2.0, all has been fixed. So I installed 11.04, then downloaded all 64bits kernel here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2-precise/")

> linux-headers-3.2.0-030200-generic_3.2.0-030200.201201042035_amd64.deb        
linux-headers-3.2.0-030200_3.2.0-030200.201201042035_all.deb  
linux-image-3.2.0-030200-generic_3.2.0-030200.201201042035_amd64.debin a terminal , install them :

> sudo dpkg -i *.debReboot, it works without any patch or tricks !

But fan speed is very high (in all conf), strange .... any help ?

NOTE :

WiFi works before 3.2.0 (and nomodeset or patch applied) under 11.04
WiFi doesn't works since 3.2.0 under 11.04
WiFi works since 3.2.0 under 12.04

---

### Post by tlee on 2012-01-16
Okay, a couple things:

1) There are so many different "threads" running through this thread that I wonder if the MBA doesn't deserve its own forum.  Any thoughts about that?  

2) I'm experiencing a problem with Unity that seems to be related to websites using flash.  Occasionally (seemingly randomly), Unity crashes when I open a website with flash.  The screen goes blank and then I'm back at the login screen.  It doesn't happen all the time--sometimes the same website will load without any trouble.  And it doesn't matter which browser I'm using.  Has anyone else had this problem?

I'm running Oneiric on a 13" MBA.  This is Unity 3D.

---

### Post by dfacto on 2012-01-17
> **tlee said:**
> Okay, a couple things:

1) There are so many different "threads" running through this thread that I wonder if the MBA doesn't deserve its own forum.  Any thoughts about that?  

2) I'm experiencing a problem with Unity that seems to be related to websites using flash.  Occasionally (seemingly randomly), Unity crashes when I open a website with flash.  The screen goes blank and then I'm back at the login screen.  It doesn't happen all the time--sometimes the same website will load without any trouble.  And it doesn't matter which browser I'm using.  Has anyone else had this problem?

I'm running Oneiric on a 13" MBA.  This is Unity 3D.

Regarding #1--this is the only thread I reliably check.  If you want me to make something work, it will have to be posted here.  Anyway, I don't think this thread is out-of-control and I think its reasonably on-topic.

Regarding #2, I haven't had this problem. Sorry I can't be more helpful. I will add tho that this sounds more like a problem with flash and/or your graphics card driver than it does with Unity.

---

### Post by artik1024 on 2012-01-17
Good news, Wifi will be fixed soon : [https://bugzilla.kernel.org/show_bug.cgi?id=42591](https://bugzilla.kernel.org/show_bug.cgi?id=42591)

Waiting for 3.3 RC1 Kernel. After that no more need patch for use on macbook air.

---

### Post by tlee on 2012-01-18
dfacto, given what you said about the graphics card driver, I wonder if the crash/logout problem is related to this message I get when running "sudo apt-get upgrade":

> tlee-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-radeon
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


I haven't been able to figure out why these packages are held back and what to do about it.

I appreciate your thoughts on this.

Note: I tried "dist-upgrade," but no luck.

---

### Post by blackjay0419 on 2012-01-18
Installing ubuntu 12.04 daily build on macbook air 4 is almost out of box.:)  (the minor issue is my backlight keyboard didn't work and the battery life is just ok)
By default, Unity use fourfinger tap to bring up Dash. However, after in gnome shell, fourfinger tap cannot bring up overview. Is there anyone know how to set fourfinger-tap equal the command key (superkey)?

Thanks

---

### Post by uBeer on 2012-01-19
> **blackjay0419 said:**
> Installing ubuntu 12.04 daily build on macbook air 4 is almost out of box.:)  (the minor issue is my backlight keyboard didn't work and the battery life is just ok)
By default, Unity use fourfinger tap to bring up Dash. However, after in gnome shell, fourfinger tap cannot bring up overview. Is there anyone know how to set fourfinger-tap equal the command key (superkey)?

Thanks


I have found a solution, but it is not that elegant...
You can install touchegg and start it from the command line. Only problem is (at least with my laptop) that it segfaults most of the times that I try to start it, but after 5-10 times it starts without faults.
If that works you can edit ~/.config/touchegg/touchegg.conf to make 4 finger swipe.

I removed most 3 and 4 finger stuff from my config file and put in:
```
<gesture type="DRAG" fingers="3" direction="ALL">
    <action type="DRAG_AND_DROP">BUTTON=1</action>
</gesture>
```
and
```
<gesture type="DRAG" fingers="4" direction="UP">
    <action type="SEND_KEYS">Super</action>
</gesture>

<gesture type="DRAG" fingers="4" direction="DOWN">
    <action type="SHOW_DESKTOP"></action>
</gesture>
```
This enables 3 finger drag n drop, 4 finger swipe up is Super key -> shell overview, 4 finger swipe down is Show desktop.

Here [-link-]("http://code.google.com/p/touchegg/wiki/AllActions") are all actions supported by Touchegg.

Hope this will help you out a bit...

---

### Post by artik1024 on 2012-01-20
> **blackjay0419 said:**
> Installing ubuntu 12.04 daily build on macbook air 4 is almost out of box.:)  (the minor issue is my backlight keyboard didn't work and the battery life is just ok)
By default, Unity use fourfinger tap to bring up Dash. However, after in gnome shell, fourfinger tap cannot bring up overview. Is there anyone know how to set fourfinger-tap equal the command key (superkey)?

Thanks
Yes ! but :

You don't have fan speed issue ? Mine is running fast since 3.2. If someone has solution to slow it down ... post kernel bugtracker.

---

### Post by blackjay0419 on 2012-01-20
Thanks for tip.
However, when I start touchegg in terminal, it always appears as the following:[INDENT] Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Reading config from  "/home/taijan/.config/touchegg/touchegg.conf" 
Segmentation fault (core dumped)
[/INDENT]I have try to start it several times, but it never works.



> **uBeer said:**
> I have found a solution, but it is not that elegant...
You can install touchegg and start it from the command line. Only problem is (at least with my laptop) that it segfaults most of the times that I try to start it, but after 5-10 times it totarts without faults.
If that works you can edit ~/.config/touchegg/touchegg.conf to make 4 finger swipe.

I removed most 3 and 4 finger stuff from my config file and put in:
```
<gesture type="DRAG" fingers="3" direction="ALL">
    <action type="DRAG_AND_DROP">BUTTON=1</action>
</gesture>
```and
```
<gesture type="DRAG" fingers="4" direction="UP">
    <action type="SEND_KEYS">Super</action>
</gesture>

<gesture type="DRAG" fingers="4" direction="DOWN">
    <action type="SHOW_DESKTOP"></action>
</gesture>
```This enables 3 finger drag n drop, 4 finger swipe up is Super key -> shell overview, 4 finger swipe down is Show desktop.

Here [-link-]("http://code.google.com/p/touchegg/wiki/AllActions") are all actions supported by Touchegg.

Hope this will help you out a bit...

---

### Post by blackjay0419 on 2012-01-20
The fan speed issue sometimes occurs, but it did not happen all the time.  When it happens, the machine could be quite hot on the top-left corner. I don't know why.

> **artik1024 said:**
> Yes ! but :

You don't have fan speed issue ? Mine is running fast since 3.2. If someone has solution to slow it down ... post kernel bugtracker.

---

### Post by allebone on 2012-01-20
> **blackjay0419 said:**
> The fan speed issue sometimes occurs, but it did not happen all the time.  When it happens, the machine could be quite hot on the top-left corner. I don't know why.

That would sound to me personally like the GPU is being taxed. Have you tried installing gnome and logging in with gnome no effects to see if the GPU is taked less, and this doesnt occur?

Pete

---

### Post by blackjay0419 on 2012-01-20
Back-light keyboard also worked out of box. Sorry for the prvieous incorrect information.
If anyone wants to install ubuntu on macbook air 4, I highly recommend install 12.04 instead of 11.10 with post-install scripts (it never works for me).

After using ubuntu 12.04 (gnome-shell) for few hours, I have found the most annoying thing is the touchpad. It is oversensitive. For example, when I scroll down my gmail inbox with two-fingers scroll, it frequently misread it as one tap-click (so I jump into a specific mail I don't intend to read). Another example is when I type with keyboard, it is nearly unavoidable to accidentally trigger the one-click tap. It ends up I have to disable touchpad whenever I want to type something.



> **blackjay0419 said:**
> Installing ubuntu 12.04 daily build on macbook air 4 is almost out of box.:)  (the minor issue is my backlight keyboard didn't work and the battery life is just ok)
By default, Unity use fourfinger tap to bring up Dash. However, after in gnome shell, fourfinger tap cannot bring up overview. Is there anyone know how to set fourfinger-tap equal the command key (superkey)?

Thanks

---

### Post by blackjay0419 on 2012-01-20
I tried gnome with no effect, the fan and heat problem still occurs . Actually the problem is not improved at all under gnome with no effect.

The another problem I found out is touchpad cannot work after resuming from suspend under gnome shell.I have to log out and log in again to make it work. This does not happen with unity.



> **allebone said:**
> That would sound to me personally like the GPU is being taxed. Have you tried installing gnome and logging in with gnome no effects to see if the GPU is taked less, and this doesnt occur?

Pete

---

### Post by deanproxy on 2012-01-20
Has anyone figured out the horrible scrolling experience?  Scrolling inside of any application is miserable for me... I know I'm pretty used to the "smooth" scrolling on the mac now, but I've never had such a bad scrolling experience as I have had with the Macbook Air running Ubuntu 11.10.  I'm guessing there is some way to tweak this to make it a bit more bearable.

---

### Post by mrmorris on 2012-01-20
> **deanproxy said:**
> Has anyone figured out the horrible scrolling experience?  Scrolling inside of any application is miserable for me... I know I'm pretty used to the "smooth" scrolling on the mac now, but I've never had such a bad scrolling experience as I have had with the Macbook Air running Ubuntu 11.10.  I'm guessing there is some way to tweak this to make it a bit more bearable.

Unfortunately not. This also remains my main gripe with running Ubuntu on the Macbook Air. What I find to be the worst, is how touching with a second finger, even when just preparing to clicking the physical button, cancels normal tracking of scrolls/moves.

---

### Post by deanproxy on 2012-01-20
> **mrmorris said:**
> Unfortunately not. This also remains my main gripe with running Ubuntu on the Macbook Air. What I find to be the worst, is how touching with a second finger, even when just preparing to clicking the physical button, cancels normal tracking of scrolls/moves.

Yes!  I tend to keep my thumb on the bottom of the trackpad while tracking so that I can make quick clicks on things.  this does not work at all under Ubuntu due to what you described.  it makes it very difficult to get at corners to drag or anything that requires precision clicking like that.

---

### Post by jonny on 2012-01-21
> **deanproxy said:**
> Has anyone figured out the horrible scrolling experience?  Scrolling inside of any application is miserable for me... I know I'm pretty used to the "smooth" scrolling on the mac now, but I've never had such a bad scrolling experience as I have had with the Macbook Air running Ubuntu 11.10.  I'm guessing there is some way to tweak this to make it a bit more bearable.
It works perfectly for me using the default driver (I've never bothered with mtrack) but I found that it was essential to adjust the trackpad's sensitivity to get a really good experience.  Scrolling now works perfectly, with all the speed and inertia effects that OS X has.  The only problem I've found is that Evince (the pdf viewer in Ubuntu) doesn't play nicely with trackpad scrolling unless you position the mouse over the scroll bar on the right of the screen.

You need to use the command-line synclient program to adjust the trackpad.  Used with no arguments, it lists all of the trackpad's settings, and you can set any of these with 'synclient <setting>=<value>'.  The ones that keep me sane are:
```
synclient fingerhigh=50
synclient fingerlow=40
```
Play around with those values, as I like a fairly sensitive touchpad so you might want to go a little higher.  Fingerhigh is the level of  pressure needed for a touch to be recognised, and fingerlow is the level of pressure needed for a touch to continue to be recognised once it's been initially identified.  A larger gap between the two therefore reduces the risk of touches being derecognised halfway through a gesture.

Once you've found values that you like, you can add a section to your xorg.conf file to make the changes system-wide and permanent.  Mine looks like this:
```
Section "InputClass"
       Identifier "touchpad catchall"
       Driver "synaptics"
       MatchIsTouchpad "on"
      MatchDevicePath "/dev/input/event*"
      Option "FingerLow" "40"
      Option "FingerHigh" "50"
EndSection
```
I think that someone's written a GUI to allow these settings to be changed, but I've never bothered to look for it.

---

### Post by deanproxy on 2012-01-21
> **jonny said:**
> It works perfectly for me using the default driver (I've never bothered with mtrack) but I found that it was essential to adjust the trackpad's sensitivity to get a really good experience.  Scrolling now works perfectly, with all the speed and inertia effects that OS X has.  The only problem I've found is that Evince (the pdf viewer in Ubuntu) doesn't play nicely with trackpad scrolling unless you position the mouse over the scroll bar on the right of the screen.

You need to use the command-line synclient program to adjust the trackpad.  Used with no arguments, it lists all of the trackpad's settings, and you can set any of these with 'synclient <setting>=<value>'.  The ones that keep me sane are:
```
synclient fingerhigh=50
synclient fingerlow=40
```
Play around with those values, as I like a fairly sensitive touchpad so you might want to go a little higher.  Fingerhigh is the level of  pressure needed for a touch to be recognised, and fingerlow is the level of pressure needed for a touch to continue to be recognised once it's been initially identified.  A larger gap between the two therefore reduces the risk of touches being derecognised halfway through a gesture.

Once you've found values that you like, you can add a section to your xorg.conf file to make the changes system-wide and permanent.  Mine looks like this:
```
Section "InputClass"
       Identifier "touchpad catchall"
       Driver "synaptics"
       MatchIsTouchpad "on"
      MatchDevicePath "/dev/input/event*"
      Option "FingerLow" "40"
      Option "FingerHigh" "50"
EndSection
```
I think that someone's written a GUI to allow these settings to be changed, but I've never bothered to look for it.


You, sir, are awesome!  This totally makes scrolling much more like it was on OSX.  Thank you so much.

Now, do you know how to get click-drag working?  As in, I want to click with my thumb, and drag with another finger.  This makes it easier to drag something across the entire screen.  If there is some way to fix this, all of my problems with Ubuntu on the Air will be completely resolved.

---

### Post by jebus_beler on 2012-01-21
> **deanproxy said:**
> You, sir, are awesome!  This totally makes scrolling much more like it was on OSX.  Thank you so much.

Now, do you know how to get click-drag working?  As in, I want to click with my thumb, and drag with another finger.  This makes it easier to drag something across the entire screen.  If there is some way to fix this, all of my problems with Ubuntu on the Air will be completely resolved.

I don't think this works with the synaptic driver since click drag relies on multitouch so I might be wrong.  This works fine with the mtrack driver.

Curious, does anyone have some optimal setting for mtrack?  I've been using the default one from the post-install script and they're ok but some tweaking might be nice (in particular tap and drag on titlebars doesn't work because its picked up as a double-click and ends up maximizing the window).

---

### Post by deanproxy on 2012-01-22
> **jebus_beler said:**
> I don't think this works with the synaptic driver since click drag relies on multitouch so I might be wrong.  This works fine with the mtrack driver.

Curious, does anyone have some optimal setting for mtrack?  I've been using the default one from the post-install script and they're ok but some tweaking might be nice (in particular tap and drag on titlebars doesn't work because its picked up as a double-click and ends up maximizing the window).

Synaptic appears to work with multitouch for me...  maybe just not gestures.

I tried Mtrack but it still wasn't a good experience.  I couldnt rest my thumb on the trackpad and still track with my finger.  I do this when I need to get a quick click in while tracking. Like when I'm about to resize a window or I'm clicking quickly through Nautilus file folders.  It stops tracking when I do this.  maybe I need to adjust the settings more.  However, the scrolling experience with Mtrack was terrible. Much better with synaptic...

---

### Post by deanproxy on 2012-01-24
> **deanproxy said:**
> Synaptic appears to work with multitouch for me...  maybe just not gestures.

I tried Mtrack but it still wasn't a good experience.  I couldnt rest my thumb on the trackpad and still track with my finger.  I do this when I need to get a quick click in while tracking. Like when I'm about to resize a window or I'm clicking quickly through Nautilus file folders.  It stops tracking when I do this.  maybe I need to adjust the settings more.  However, the scrolling experience with Mtrack was terrible. Much better with synaptic...

I messed with the thumbsize setting in mtrack and got it to ignore my thumb successfully.

Now if mtrack could fix its scrolling to be as smooth as synaptics...

---

### Post by blackjay0419 on 2012-01-24
> **deanproxy said:**
> I messed with the thumbsize setting in mtrack and got it to ignore my thumb successfully.

Now if mtrack could fix its scrolling to be as smooth as synaptics...

to deanproxy:

would you like to share your setting of mtrack in xong.conf ?
I have tried the mtrack, click and drag did work, but overall experience is much worse than synaptic drivers.
maybe the forum could find a good setting for Macbook air 4.
  
thanks

---

### Post by blackjay0419 on 2012-01-24
> **blackjay0419 said:**
> 

After using ubuntu 12.04 (gnome-shell) for few hours, I have found the most annoying thing is the touchpad. An example is when I type with keyboard, it is nearly unavoidable to accidentally trigger the one-click tap. It ends up I have to disable touchpad whenever I want to type something.


the problem of accidentally move cursor  while typing can be solved by the following command:
synclient PalmDetect=1

additional information can be found at:
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

I think this might be helpful for some people.

---

### Post by sinzui on 2012-01-25
> **rubiojr said:**
> I upgraded to Precise in my MBA 4,1 and had to go back to the Oneiric kernel because of that. Keyboard doing really weird things. Not sure if related to your issue though:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903655)

I am also experiencing problems with the keyboard and touchpad when I first login under precise. The first few key presses work, and then they become unreliable. Touchpad is also broken and I think the trying to use the touchpad makes the keyboard lag worse.

WORKAROUND
The keyboard and touchpad can be made to work by switching away from X then back to it.
1. Press <Control>+<Alt>+<Fn>+F1 to go to console 1.
2. Press <Control>+<Alt>+<Fn>+F7 to return to the desktop.
3. Verify that the keyboard responds immediately to your typing and that the touchpad will scroll.

You may need to do step 1 multiple times because input is not reliably captured.

---

### Post by wkretzsch on 2012-01-26
Hi everybody,
After kernel upgrade to 3.0.0-15 and running post_install_oneiric.sh my external monitor shows a grey screen and the mba screen turns black when I connect the external monitor through the thunderbolt port.

I've searched for this problem on google and in this thread, but I haven't found anything, so I assume I've missed a step somewhere.  I've installed ubuntu 2D, but I get the same problem there.  Any ideas what else I might try?

---

### Post by wkretzsch on 2012-01-26
I tried booting the mba with the external monitor attached into unity 3d and that solved the problem.  This was probably my 10th reboot today, so I think the change had something to do with the external monitor being connected from the start.

---

### Post by orfeas0 on 2012-01-27
**I need help with the installation of ubuntu on my 2011 macbook air and I didn't know if I should make a new thread, so here I am.**

I already have rEfit, I used to have a windows partition alongside mac OSX but I delete that one and made another for ubuntu.
I created a bootable USB drive following the instructions of the ubuntu installation page, but I'm not sure it was created properly, as it does not appear in the refit boot menu.
Is it normal that the .iso I downloaded has wubi.exe in it? Do all the ubuntu images have that , even if you don't want it?
I don't have a superdrive so please don't ask me to make a bootable CD, I can only use USBs.

Since refit doesn't recognize my usb key does that mean it was not properly created? Or must I do something else?

I also think that my refit might be... bugged (or something like that).
Because when I had 1 single partition (after removing my windows partition), it still showed "Mac OSX Lion" AND "Boot legacy disk" in the boot page. Is that normal, even though I had nothing connected on my mac and only 1 partition in it?

---

### Post by poliva on 2012-01-27
Follow the install instructions in the wiki, you will find the right ISO to download and a script to make a proper bootable USB from the ISO.

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

---

### Post by orfeas0 on 2012-01-27
> **poliva said:**
> Follow the install instructions in the wiki, you will find the right ISO to download and a script to make a proper bootable USB from the ISO.

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

Thanks but... After running the script I get those at the last lines:
unmount: /dev/sdb: not mounted
sudo: aptitude: command not found
syslinux: invalid media signature (not a FAT filesystem?)

I'm on another PC running ubuntu 11.10.
Any help?

EDIT: I ran apt-get install aptitude and it fixed the sudo:aptitude error.
But I still get syslinux: invalid media etc.
How can i fix that?

---

### Post by blackjay0419 on 2012-01-27
> **orfeas0 said:**
> Thanks but... After running the script I get those at the last lines:
unmount: /dev/sdb: not mounted
sudo: aptitude: command not found
syslinux: invalid media signature (not a FAT filesystem?)

I'm on another PC running ubuntu 11.10.
Any help?

EDIT: I ran apt-get install aptitude and it fixed the sudo:aptitude error.
But I still get syslinux: invalid media etc.
How can i fix that?


I encountered the same problem while installing ubuntu via USB.
Unfortunately I didn't find a way to make this work, so I just bought Superdive to install ubuntu from CD.
I think maybe there is something wrong with the USB scripts, or the wiki could be more specific about the steps.

---

### Post by jonny on 2012-01-28
> **orfeas0 said:**
> Thanks but... After running the script I get those at the last lines:
unmount: /dev/sdb: not mounted
sudo: aptitude: command not found
syslinux: invalid media signature (not a FAT filesystem?)

I'm on another PC running ubuntu 11.10.
Any help?

EDIT: I ran apt-get install aptitude and it fixed the sudo:aptitude error.
But I still get syslinux: invalid media etc.
How can i fix that?
From memory, the script is fussy about whether the USB stick is mounted before you start.  I *think* then it expects it to be mounted, but I might be wrong.

The easiest way to ensure it's mounted is to browse to the folder in Nautilus (the standard ubuntu file browser) and then to close your Nautilus window (to ensure nothing is accidentally locked) before you run the script.  If that doesn't work, try ejecting the drive with Nautilus (there's a button to do this in the left hand pane) and running the script again.

---

### Post by orfeas0 on 2012-01-28
I finally managed to work it!
I didn't actually make a usb with the script as described, I just followed the ubuntu-on-mac instructions on the ubuntu download page but using the mac iso given above.
It didn't boot normally at first time and I had to enter the recovery mode, and in there installed the post-install oneiric script. I had to install the lcd panel driver and reboot quite some times for it to work witohut recovery mode but it works now.
If anyone needs help with the process post here. Point is you don't really need that script to make a bootable usb, it can be done in mac OSX ;)

---

### Post by dfacto on 2012-01-28
> **orfeas0 said:**
> I finally managed to work it!
I didn't actually make a usb with the script as described, I just followed the ubuntu-on-mac instructions on the ubuntu download page but using the mac iso given above.
It didn't boot normally at first time and I had to enter the recovery mode, and in there installed the post-install oneiric script. I had to install the lcd panel driver and reboot quite some times for it to work witohut recovery mode but it works now.
If anyone needs help with the process post here. Point is you don't really need that script to make a bootable usb, it can be done in mac OSX ;)

Also, you can do all the steps under OSX by simply installing the dependencies with port.

---

### Post by orfeas0 on 2012-01-28
> **dfacto said:**
> Also, you can do all the steps under OSX by simply installing the dependencies with port.

What steps under OSX and what dependencies with port?

I followed this instructions (before install):
> Download the desired file
Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
Note: OS X tends to put the .dmg ending on the output file automatically.
Run diskutil list to get the current list of devices
Insert your flash media
Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
Run diskutil eject /dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick
And post-install i ran the oneiric script. 
What you must be aware:
USE THE MAC ISO (It might work with the other one but I wouldn't recomment it).
After installation, it will probably give you a black screen when trying to log in ubuntu.
LOGIN IN RECOVERY MODE. Install the oneiric script in recovery mode.
After the oneiric install, if normal mode doesn't work, reinstall the LCD driver ([https://help.ubuntu.com/community/MacBookAir4-2#LCD](https://help.ubuntu.com/community/MacBookAir4-2#LCD)) in recovery mode.
repeat the last steps as necessary ;)

---

### Post by ChinaSailor on 2012-01-28
Latest batch of ubuntu updates for 11.10

I ran the latest updates via the update manager, I noticed there were some kernel updates so I waited until I was home until ran these, because usually I have to run the post-install-oneiric.sh script to get the system working again.

Downloaded the latest "post-install-oneiric.sh" script dated 15JAN2012, and ran updates, via update manager (257 in total) and then ran the post-install scrip after the first reboot.

I did have a problem with the mouse pointer (cursor) freezing up, (had this issue since ubuntu changed something in October) but I have always been able to log-out, and re-login again, and everything would spring to life, but not this time.

I will attempt to re-run the post-install a 2nd time, but I doubt it will make any difference.

Anyone experiencing this? frozen cursor..? after latest updates?

---

### Post by ChinaSailor on 2012-01-28
Ubuntu latest updates (11.10)

Frozen Cursor + Keyboard Brightness permanently set to "High"

Anyone know a way to roll-back, just these latest updates..? Anyone?

Thanks in advance!

---

### Post by orfeas0 on 2012-01-29
Wow, thank got i didn't do the ubuntu updates ;)

---

### Post by dfacto on 2012-01-29
> **ChinaSailor said:**
> Ubuntu latest updates (11.10)

Frozen Cursor + Keyboard Brightness permanently set to "High"

Anyone know a way to roll-back, just these latest updates..? Anyone?

Thanks in advance!

I always keep everything up-to-date (11.10) and I don't have any problems nor have I had any hiccups in a long time.

You must have some other problem.

---

### Post by jonny on 2012-01-29
> **ChinaSailor said:**
> Ubuntu latest updates (11.10)

Frozen Cursor + Keyboard Brightness permanently set to "High"

Anyone know a way to roll-back, just these latest updates..? Anyone?

Thanks in advance!
Have you tried choosing an earlier kernel from the startup menu?  If that works, open Synaptic (you might need to install it first) and remove the latest kernel (linux-image-3.0.0-15-generic).

I haven't yet had time to apply the latest updates so I can't comment on whether things work for me.

---

### Post by ChinaSailor on 2012-01-30
> **jonny said:**
> Have you tried choosing an earlier kernel from the startup menu?  If that works, open Synaptic (you might need to install it first) and remove the latest kernel (linux-image-3.0.0-15-generic).

I haven't yet had time to apply the latest updates so I can't comment on whether things work for me.


I'll look for any earlier kernel, but the only two I remember seeing (you are talking grub menu correct..?) is the latest and recovery mode kernel, unless that's what you mean?

The cursor freezing up issue, began back in October, but I've always been able to log-out, and login again, and it would work, but after the latest updates, the cursor will work only until about 1.5 mins after the login, then it will load possibly the bluetooth module, and something else, and then it will die. I have been able (previously) to plug a usb mouse in, and that would work, so it's something to do with the trackpad & possibly the bluetooth driver(s). I had spent a few hours before troubleshooting it, by process of elimination, by systematically blacklisting modules, that only get loaded upon login, but I wasn't able to pin anything down. I blacklisted basically all the modules, that got loaded at login time, and it still froze up. But as I said before, I did discover (before) that a quick logout / re-login would correct it, but not this time.

---

### Post by poliva on 2012-01-30
> **dfacto said:**
> I always keep everything up-to-date (11.10) and I don't have any problems nor have I had any hiccups in a long time.

Same here, I update almost daily and never had a problem using 11.10.

---

### Post by zmiq2 on 2012-01-30
Same here, I update almost daily and never had a problem using 11.10.

Well, the only problem I have is resuming from suspend, when suspended using the laptop screen and resuming with external monitor attached; in that case, I need to rebbot to be able to use the external monitor again.

---

### Post by deelerious on 2012-01-30
**MacBookAir 4,1 alternate install with full disk encryption**

Many, many thanks to [srs5694]("http://ubuntuforums.org/member.php?u=1032238"), [dfacto]("http://ubuntuforums.org/member.php?u=52141"), the Mactel team and too many others to mention for the great work on getting Ubuntu working on the MacBook Air and the valuable information in this thread.

I recently acquired a 11" MacBook 4,1 with 2GB RAM and 64GB disk. A requirement I had to meet was full disk encryption on the Ubuntu side. The LiveCD at this time does not support installing with full disk encryption which means I had to diverge from the [community documentation]("https://help.ubuntu.com/community/MacBookAir4-2") and perform the installation from the [Mactel alternate install CD]("http://cdimages.ubuntu.com/releases/11.10/release/ubuntu-11.10-alternate-amd64+mac.iso").  

Quick notes I took to document the installation where it diverges from the standard desktop LiveCD one: 

You will need 2 USB drives for installation. 1GB drives will be sufficient.

I started from a fresh install of OS X, thus 3 GPT partitions: EFI, Macintosh HD and Recovery CD.

[LIST=1]
[*]In OS X Disk Utility, resize the OS X partition as needed. The EFI and Recovery HD partitions will not be affected. I resized it to 25GB, approximately double the footprint of the installed OS, leaving a little over 12GB free. Install rEFIt. Install GPT fdisk to have on hand should you need to fix the hybrid MBR post install. Thanks again [srs5694 ]("http://ubuntuforums.org/member.php?u=1032238")for this great tool and the superb [documentation]("http://www.rodsbooks.com/gdisk/"). Power off OS X.
[*]Use the [setup_mac_usb_boot.sh]("http://almostsure.com/mba42/setup_mac_usb_boot.sh") script linked at the community article to create a USB image of the Mactel desktop LiveCD. 
[*]Boot from the Mactel desktop LiveCD USB drive to prepare the partitions for Ubuntu alternate install.
[*]Select Try Ubuntu and start GParted.
[*]Create two new partitions to hold the Ubuntu installation. I left 128M space between partitions as I've read from several sources that OS X likes to see them, especially for updates.

New partition for /boot:
Free space preceding: 128 MiB
New size: 256 MiB
File system: ext4

New partition that will later be encrypted and hold the rest of the filesystem in a LVM volume group:
Free space preceding: 128 MiB
New size: remaining free space
File system: unformatted


[*]Power off
[*]Prepare a USB drive with the alternate image. Tweak the setup_mac_usb_boot.sh script by adding the alternate image (tweaked script attached to this post). You can reuse the LiveCD USB drive as we won't need it again.
[*]Prepare a second USB drive by copying the alternate installer ISO to it. Any readable file system will do. I used FAT32. We will use this in the alternate install in place of a CD-ROM.
[*]Boot from the alternate image USB drive and select Install Ubuntu. I haven't had a need to add 'nomodeset' to the kernel parameters but adjust as needed.
[*]At the 'Select a language' initial screen follow the installer until the detection of the CD-ROM fails. To 'Retry mounting the CD-ROM?', answer 'No' then 'Continue' on the next screen.
[*]You will be returned to the Ubuntu installer main menu. Select 'Execute a shell'.
[*]Insert the USB drive with the alternate image ISO.
[*]Mount the USB drive. For me the drive was on /dev/sdc1.
```
mount -t vfat /dev/sdc1 /mnt
```
[*]Mount the alternate image ISO
```
mount -t iso9660 -o loop /mnt/ubuntu-11.10-alternate-amd64\+mac.iso /cdrom
```
[*]Type 'exit' to leave the shell.
[*]Select 'Detect and mount CD-ROM'.
[*]It should start loading additional components.
[*]Depending on the MacBook Air model, you may receive a 'No network interfaces detected' error as the alternate install does not support the wireless adapter on at least my model of MBA. If so, just select 'Continue'. Follow the installer to partitioning. 
[*]Answer 'No' to all 'Unmount partitions that are in use?' questions that pop up periodically in the installer.
[*]Use manual partitioning to assign /boot to the unencrypted partition that will be used to start the encrypted system. In my case it was /dev/sda4. Create an encrypted volume on /dev/sda5. An excellent tutorial can be found at [http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/](http://joernfranz.net/2011/01/20/installing-ubuntu-10-10-with-full-disk-encryption/). I created 3 logical volumes: 3GB swap, 8GB /, 16GB /home, leaving some room on the volume group for future adjustments.
[*]The base system will be installed.
[*]Depending on whether or not you have network, the installer may walk you through the rest of the install or drop you at the main menu. For me, with no network, the 'Select and install software' entry did not do anything so I had to finish with just the base system installed.
[*]At the end, select 'Install the GRUB loader on a hard disk'. Enter the device name for your /boot partition, /dev/sda4 in my case.
[*]Remove USB drives and restart.
[*]If all went well, you should be able to select Linux at the rEFIt prompt. Note: I ended up with two Linux rEFIt entries that seemed identical. They both launch GRUB just fine.
[*]If you were able to do a full install, you should be able to login to your encrypted disk and continue with the post-install steps. Otherwise, if you only installed the base system, follow the next steps.
[*]At the GRUB menu, select recovery mode and enter the password for the encrypted disk.
[*]Insert the alternate image ISO USB drive.
[*]Mount the USB drive. For me the drive was on /dev/sdb1
```
mount -t vfat /dev/sdb1 /mnt
```
[*]Mount the alternate image ISO
```
mount -t iso9660 -o loop /mnt/ubuntu-11.10-alternate-amd64\+mac.iso /media/cdrom
```
[*]Install the rest of the system, or whatever packages you wish. I installed Ubuntu desktop.
```
apt-get install ubuntu-desktop
```
[*]Power off and remove the USB drive.
[*]Start and you should be able to select the regular GRUB entry now and add 'nomodeset' as described in the community tutorial, then be prompted for the disk password. Otherwise, you will need to troubleshoot and possibly repair the hybrid MBR. If you selected to install Ubuntu desktop, once you authenticate to the disk, you should be taken to the lightdm login. 
[*]Adjust your 'Software Sources' or /etc/apt/sources.list to remove the CD-ROM and enable the Internet repos. Make sure to add the sources repo as it will be required for the post-install script. 
[*]Proceed with the post-install.
[/LIST]

Please let me know if you come across errors.

Thanks and enjoy your new encrypted system.

---

### Post by ChinaSailor on 2012-01-30
Just out of curiosity, everyone here, that reports everything just Great,

You are all running Unity with 11.10..? I Assume...

---

### Post by ChinaSailor on 2012-01-30
Ok, Here's a zinger, how can I just remove (or disable) the keyboard back lighting?
(hint, I've already tried rm-ing the ~/bin/keyboard-backlight)

If I can permanently disable this keyboard backlight,  which is now permanently set to HIGH, (just one more thing draining my battery), I can plug a usb mouse in and, at least, have a usable pc, otherwise I have a 2.5 lbs brick, that was working soooo well until 3 days ago.

Tried booting the previous kernels at least the "-14" generic, same issues (probably because it's loading these new modules, with old kernel) 

So I suspect, something is up with the new modules, and it freezes up, right about when the bluetooth daemon / module gets loaded.

---

### Post by deelerious on 2012-01-30
> **ChinaSailor said:**
> Just out of curiosity, everyone here, that reports everything just Great,

You are all running Unity with 11.10..? I Assume...

Unity with 11.10, vanilla setup as it comes out of the box except for tweaking a few things in Settings such as power settings and the like.

However, I installed 11.10 and ran post-install just last night and did not do an upgrade.

---

### Post by zmiq2 on 2012-01-31
I'm using 11.10 with gnome3.

I Rebuilt the touchapd, video and keyboard drivers last week after upgrading to -15 kernel, using the standard update manager.

---

### Post by ChinaSailor on 2012-01-31
Finally, Ubuntu is caving under pressure, and will again offer builds with normal Gnome, and those that want that fancy windows wannabe, 'Unity,' can still install it, but it will not be the only supported option.


Thank You, Thank You, and Thank You Linus!

---

### Post by dfacto on 2012-02-01
> **ChinaSailor said:**
> Finally, Ubuntu is caving under pressure, and will again offer builds with normal Gnome, and those that want that fancy windows wannabe, 'Unity,' can still install it, but it will not be the only supported option.


Thank You, Thank You, and Thank You Linus!

Linus? He's been vocal but I hardly think he deserves any credit in this regard.

---

### Post by ngativ on 2012-02-02
> **ChinaSailor said:**
> Finally, Ubuntu is caving under pressure, and will again offer builds with normal Gnome, and those that want that fancy windows wannabe, 'Unity,' can still install it, but it will not be the only supported option.


Thank You, Thank You, and Thank You Linus!

Gnome 3 is a fail, the worst desktop enviroment ever, so what are you talking about? Unity is great UI concept, but sadly has been kind of buggy from the start until a few month ago.


If you want to use the best DE then use KDE4, is a pro .

Anyway i just want to say that the linux kernel 3.2.1 solves most of the driver issues for the macbook air 4,2 and 4,1. so theres no need to patch the kernel.

---

### Post by jebus_beler on 2012-02-07
Hi All,

Two unrelated questions regarding quality of life improvements on the MBA.

First, is anyone successfully using touch-egg and is it better than mtrack?  Mtrack works pretty well for me except for two issues (one quite minor):

- I often have to restart dispad after resume (could put this in a script).  With dispad I don't have issues of accidental track hits while typing.

- More seriously I cannot tap-and-drag windows.  I thought this was a compiz or gnome issue but I've found a description of this issue on the mtrack website.  Has anyone gotten tap-and-drag to work as I quite miss this?

The second question regards power-consumption and the new kernel.  Apparently the new 3.2 kernel solves some power regression issues and i was wondering if anyone is running a new kernel (e.g. in precise pangolin) and seeing the benefits.  Has anyone gotten < 7 watts power in  a reasonably active session (low backlight, wifi, etc...)?

---

### Post by blackjay0419 on 2012-02-08
> **jebus_beler said:**
> Hi All,

Two unrelated questions regarding quality of life improvements on the MBA.

First, is anyone successfully using touch-egg and is it better than mtrack?  Mtrack works pretty well for me except for two issues (one quite minor):

- I often have to restart dispad after resume (could put this in a script).  With dispad I don't have issues of accidental track hits while typing.

- More seriously I cannot tap-and-drag windows.  I thought this was a compiz or gnome issue but I've found a description of this issue on the mtrack website.  Has anyone gotten tap-and-drag to work as I quite miss this?

The second question regards power-consumption and the new kernel.  Apparently the new 3.2 kernel solves some power regression issues and i was wondering if anyone is running a new kernel (e.g. in precise pangolin) and seeing the benefits.  Has anyone gotten < 7 watts power in  a reasonably active session (low backlight, wifi, etc...)?


1. I couldn't successfully run touch-egg either. 
    The dispad issue did not happended to me. It works well.
    tap-and-drag works awkwardly, you have to tap the menubar and then move the window. Besides it cannot   work in gnome shell overview mode.

2. I am running 12.04. The battery could run for near 3.5 hours with ordinary use (typing, browsing).
    I didn't install 11.10, so I could not compared them.
   I found 12.04 is very stable, even though it is still alpha.

---

### Post by ChinaSailor on 2012-02-13
> **dfacto said:**
> Linus? He's been vocal but I hardly think he deserves any credit in this regard.


Don't you mean, "Linus Who..?" 

Thank You, You've just made my point...

---

### Post by zmiq2 on 2012-02-13
Just upgraded to newest kernel, 3.0.0-16, re-run the usual scripts and everything is fine (at least as good) as before.

FYI.

---

### Post by Murphy2712 on 2012-02-14
I was lazy to fix again the graphic drivers on 11.10 so I upgraded to 12.04 using:
sudo update-manager -d

The mouse wasn't working, I needed to manually install xserver-xorg-input-mtrack.

But then all works fine like before :popcorn:

---

### Post by jebus_beler on 2012-02-15
> **Murphy2712 said:**
> I was lazy to fix again the graphic drivers on 11.10 so I upgraded to 12.04 using:
sudo update-manager -d

The mouse wasn't working, I needed to manually install xserver-xorg-input-mtrack.

But then all works fine like before :popcorn:


How stable is 12.04?  Any idea if touch-egg works?  Lack of tap-and-drag in mtrack is really annoying.  But upping the sensitivity and reducing  the scroll-distance gives me the kind of responsiveness I see in OS X.  For anyone's ref I'm find the following:

Option           "Sensitivity"     "0.90"
Option           "ScrollDistance"  "50"

To be good setting for the mtrack driver though maybe sensitivity could be dropped to 0.85 as it is very sensitive now.  The reduced ScrollDistance helps avoid the problem of the mouse moving while you try to two-finger scroll.

---

### Post by dfacto on 2012-02-15
> **ChinaSailor said:**
> Don't you mean, "Linus Who..?" 

Thank You, You've just made my point...

I don't understand.

---

### Post by ngativ on 2012-02-17
> **jebus_beler said:**
> How stable is 12.04?  Any idea if touch-egg works?  Lack of tap-and-drag in mtrack is really annoying.  But upping the sensitivity and reducing  the scroll-distance gives me the kind of responsiveness I see in OS X.  For anyone's ref I'm find the following:

Option           "Sensitivity"     "0.90"
Option           "ScrollDistance"  "50"

To be good setting for the mtrack driver though maybe sensitivity could be dropped to 0.85 as it is very sensitive now.  The reduced ScrollDistance helps avoid the problem of the mouse moving while you try to two-finger scroll.

The utouch framework is not working yet in 12.04 . But i found that the multitouch driver works a lot better than the mtrack driver.

---

### Post by jebus_beler on 2012-02-20
> **ngativ said:**
> The utouch framework is not working yet in 12.04 . But i found that the multitouch driver works a lot better than the mtrack driver.

I'm actually still using 11.10.  Is there a "multitouch" driver as a part of the standard X distribution in 12.04?  If so I'll try it but can you tell me what does and doesn't work and maybe show your xorg.conf.

Also, any reason not to update to 12.04?  It seems a bit early to me (I already spend enough time fiddling around getting things to work) but if others have done it and have had good results maybe I'll try.

thanks!

---

### Post by Murphy2712 on 2012-02-21
> **jebus_beler said:**
> How stable is 12.04?

Actually it's not that stable, I got a lot of crashes like launcher restarting several times a day, but nothing major.

I noticed that the launcher is a LOT faster than before, the entire system is very responsive now :)

Sorry I don't have time to test touch-egg/multitouch drivers.

---

### Post by ngativ on 2012-02-22
> **jebus_beler said:**
> I'm actually still using 11.10.  Is there a "multitouch" driver as a part of the standard X distribution in 12.04?  If so I'll try it but can you tell me what does and doesn't work and maybe show your xorg.conf.

Also, any reason not to update to 12.04?  It seems a bit early to me (I already spend enough time fiddling around getting things to work) but if others have done it and have had good results maybe I'll try.

thanks!

Multitouch works out of the box using  either xorg-input-multitouch ,the xorg-input-mtrack or synaptics

I installed the 12.04 because all the features will work out of the box (mostly). But you will still have to tweak your linux for a better handling of the SSD (the solid state drive ) and power saving.

I like to live in the edge so ive installed the 3.3 rc4 kernel because it contains up to date fixes for the intel gpu. I am using grub efi and the btrfs filesystem with its ssd optimizations, and zram to avoid using a swap partition that hurts the ssd.

---

### Post by Murphy2712 on 2012-02-22
> **ngativ said:**
> zram to avoid using a swap partition that hurts the ssd.

Do you have a tuto to install/use zram?
Thanks

---

### Post by mr_manny on 2012-02-27
> **ngativ said:**
> Multitouch works out of the box using  either xorg-input-multitouch ,the xorg-input-mtrack or synaptics

I installed the 12.04 because all the features will work out of the box (mostly). But you will still have to tweak your linux for a better handling of the SSD (the solid state drive ) and power saving.

I like to live in the edge so ive installed the 3.3 rc4 kernel because it contains up to date fixes for the intel gpu. I am using grub efi and the btrfs filesystem with its ssd optimizations, and zram to avoid using a swap partition that hurts the ssd.

anything other then the usual?

```
$ grep tmpfs /etc/fstab
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives/ tmpfs defaults,noatime 0 0

```

and

```
$ grep 915 /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
```

you wish to share? :)

---

### Post by User4519 on 2012-02-28
> **ngativ said:**
> and zram to avoid using a swap partition that hurts the ssd.

Why would you think a swap partition would hurt the SSD? If you're thinking swap prevents TRIM from working, you're wrong — TRIM has been supported in swap partitions for quite a long time now.

---

### Post by berryman77 on 2012-02-29
> **berryman77 said:**
> As a follow up on this message, I consistently see this same problem. After resuming from suspend (with nothing connected to the laptop), I plug into an external monitor via HDMI and see nothing but the background color.  In the kernel logs, I see:

```

[drm:drm_mode_getfb] *ERROR* invalid framebuffer id

```

which coincides with the external monitor activation.

Is there anyone switching between laptop and external monitor that is not having this problem?  I did find that if I suspend to disk and resume the external monitor will work again.  I'm not sure if and what that might point to.  Any ideas?  I'm using packages from x-updates.  Surely there are others who's work routine consists of plugging and unplugging an external monitor.

Thanks.

---

### Post by undoIT on 2012-03-01
> **ngativ said:**
> Multitouch works out of the box using  either xorg-input-multitouch ,the xorg-input-mtrack or synaptics

I installed the 12.04 because all the features will work out of the box (mostly). But you will still have to tweak your linux for a better handling of the SSD (the solid state drive ) and power saving.

I like to live in the edge so ive installed the 3.3 rc4 kernel because it contains up to date fixes for the intel gpu. I am using grub efi and the btrfs filesystem with its ssd optimizations, and zram to avoid using a swap partition that hurts the ssd.

I also installed 12.04 with Btrfs on my Macbook 4,2. Do you encrypt your filesystem? I'm trying to figure out how to optimize for an SSD that is encrypted.

---

### Post by dbanck on 2012-03-02
Since there is no recent work on Oneiric with the MacBookAir3,X, I'm gonna try this.

Has anybody done it before?

---

### Post by ngativ on 2012-03-02
> **mr_manny said:**
> anything other then the usual?

```
$ grep tmpfs /etc/fstab
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives/ tmpfs defaults,noatime 0 0

```

and

```
$ grep 915 /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
```

you wish to share? :)

Should be:

[HTML]grep btrfs /etc/fstab 
LABEL=ubuntu1204 / btrfs defaults,ssd,compress=lzo,autodefrag,discard,noatime 0 1
[/HTML]

Then, with the compress=lzo option you could do this

btrfs filesystem balance / 

to recompress all your  files
 
Note that if you do that then youll need the lastest grub version with lzo support. Other wise youll not be able to boot if your boot/ folser is inside the btrfs partition

So is better to use the bzr version of grub2 1.99999... efi. 


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 elevator=noop"
```

Your tmpfs are ok

---

### Post by ngativ on 2012-03-02
> **undoIT said:**
> I also installed 12.04 with Btrfs on my Macbook 4,2. Do you encrypt your filesystem? I'm trying to figure out how to optimize for an SSD that is encrypted.

No, i dont know

---

### Post by hpsch on 2012-03-03
Does anybody else experience X freezes with MacBookAir4,2 and Ubuntu 12.04 Beta 1?
After a a few minutes to 1/2 an hour X just freezes, which results in a still moving mouse cursor, but nothing else moves anymore. Switching to console and back to X still works, though (but does not "unfreeze X").

At the moment, I do not use the "nomodeset" kernel option, so maybe it's related to that. Do all of you use this kernel option with Ubuntu 12.04?

br
HPS

_Update:_ With the nomodeset kernel option I just get garbage on the display and X does not load.
[U]
Update 2:[/U] This seems to be the related bug in launchpad [Bug #944415]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/944415")

---

### Post by sinzui on 2012-03-05
I experienced this X/trackpad issues. X freezes when I ran the synaptics driver. 12.04 has been stable since I switched to mtrack. I report Bug #932746 about the issue.

---

### Post by hpsch on 2012-03-06
It seems there exists a fix for it already (see Bug Report [#942625]("https://bugs.launchpad.net/unity/+bug/942625")). Let's hope that they are going to bring Unity 5.6.0 to Ubuntu 12.04 soon or backport the fix to Unity 5.4.0.

In the meantime I think I am going to try mtrack too. So far I only tested it for a short time and then switched back to synaptics.

br
HPS

---

### Post by mr_manny on 2012-03-09
Have you guys installed the proprietary wireless driver on your MBA 4,2?

Wireless works fine on 12.04...not sure if the proprietary driver install is necessary.

thanks

---

### Post by tlee on 2012-03-10
Small problem here...

11.10 on the 2011 13" 120gb MBA... it's been running fine since last November.  I just ran the latest upgrade, which installed the 3...16 kernel.  I added "nomodeset" and ran the post-install script as usual, but the display still isn't working properly (wrong resolution, choppy, and freezes if I try to use alt-tab to switch windows).

At first, I noticed that Grub wasn't keeping "nomodeset."  I sudo-edited /etc/default/grub and now it keeps it, but there is still the display problem.

I tried booting previous versions, but that doesn't change anything.

Any ideas?

---

### Post by tlee on 2012-03-10
Err.. nevermind.  I re-ran the post-install script, this time also doing the configuration part, and that seems to have fixed it.

---

### Post by mr_manny on 2012-03-22
Did you guys notice that the latest 12.04 updates fixed touchpad issues?

thank you :)

---

### Post by dfacto on 2012-03-22
> **mr_manny said:**
> Did you guys notice that the latest 12.04 updates fixed touchpad issues?

thank you :)

Cool!  I haven't install 12.04 yet--but I fully hope (expect?!) that it makes my script unnecessary.

---

### Post by preacher37 on 2012-03-23
> **mr_manny said:**
> Did you guys notice that the latest 12.04 updates fixed touchpad issues?

thank you :)

What issues are you referring too?

After updating to 12.04 my very beloved three-finger move disappeared, and four finger swipe and touch to bring up unity got a bit harder to do (better timing required, it feels like).

I just updated now and three-finger move is still missing for me. And a few updates ago the keys for increase/decrease keyboard backlight started crashing unity/compiz.

It's a big step forward that most things actually work out of the box, but there are some more bugs to iron out.

---

### Post by dfacto on 2012-03-23
> **preacher37 said:**
> What issues are you referring too?

After updating to 12.04 my very beloved three-finger move disappeared, and four finger swipe and touch to bring up unity got a bit harder to do (better timing required, it feels like).

I just updated now and three-finger move is still missing for me. And a few updates ago the keys for increase/decrease keyboard backlight started crashing unity/compiz.

It's a big step forward that most things actually work out of the box, but there are some more bugs to iron out.

Is there anything you can cherry-pick from the post-install script?  I left a lot of "vestigial code" in there for reference purposes.

---

### Post by preacher37 on 2012-03-23
> **dfacto said:**
> Is there anything you can cherry-pick from the post-install script?  I left a lot of "vestigial code" in there for reference purposes.

I thought of that, and have read through your script quickly without finding anything at first glance. I am running the synaptics driver out of the box, same as I was on 11.10 if I'm not mistaken.

I will try and have a closer look when I have time, but I am a bit swamped with work at the moment.

Is there anybody on 12.04 that three finger move works for?

---

### Post by preacher37 on 2012-03-23
> **preacher37 said:**
> 
Is there anybody on 12.04 that three finger move works for?
 
Just a short reply to to myself here, it seems that the function to activate the move and resize handles is called "Unity MT Grab Handles" in ccsm. But it only has configurable keyboard shortcuts to activate it, not mouse movements or buttons/presses. Don't know how it looked in 11.10.

I really liked those handles, I have a pain hitting the exact spot on window borders to resize them.

---

### Post by mr_manny on 2012-03-23
> **preacher37 said:**
> 
Is there anybody on 12.04 that three finger move works for?


sorry, not familiar with the three finger move?


successfully tested the following on my MBA 4,2 running ubuntu 12.04

two finger touch = left-click
two finger on touchpad with a third touch = middle button click

two finger swipe up = page up
two finger swipe down = page down

and the standard single finger = right-click

---

### Post by dpsci on 2012-03-24
Is there a FAQ or howto on installing ubunto on a MBA 13in from late 2011?  I'd really like to totally wipe OSX and just use ubuntu.  I found [this but it's for 10.10]("http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive")

Is there a more updated howto somewhere?  The first post in the thread seems to be horribly out of date.
[]("http://ubuntuguide.net/how-to-install-ubuntu-on-macbook-air-3-1-via-usb-flash-drive")

---

### Post by jonny on 2012-03-25
The [wiki](https://help.ubuntu.com/community/MacBookAir4-2) is the best place to look.  To the best of my knowledge it's firly up to date.

---

### Post by zmiq2 on 2012-04-04
I just uograded to 12.04, running the usual update-manager -d command, and I do not recommend to do it yet (it's beta now): external monitor doesn't work, I see some fan errors in the logs


After upgrading (took less than 1 hr), my external monitor doesn't work anymore.

In order to have the external monitor working, I boot using a previous 3.0.0-17 kernel.


Issue #1:
My monitor is a 24'' dell, and in dmesg I see the error:

drm: intel_cpt_verify_modeset: ERROR: mode set failed: pipe 0 stuck

which I have googled, and it seems there's an open bug report for it.

Does anyone have any hints about how to solve the external monitor issue?



Issue #2:
In dmesg I see some applesmc errors; does anyone know if those are important?


Thanks

---

### Post by dfacto on 2012-04-04
Hi zmiq2.  I'm not sure about the specific problems you list... But I also did do-release-update -d and unity wouldn't load.  I reformatted root and re-installed from iso (using the [Basic Instructions]("https://help.ubuntu.com/community/MacBookAir4-2")) and everything works beautifully.

Upon loading I installed:

macfanctld
xserver-xorg-input-mtrack

and I added coretemp to /etc/modules.conf.

So since this was so simple, I suggest you also do a clean install and see if this fixes things.

Also.  I had the same problem that I had before with the hybrid MBR getting messed up.  I followed [my own steps]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185") and it worked on the first try. (It worked the first try because I actually expected this problem and ran gdisk right after installing ubuntu from the live session.)

---

### Post by zmiq2 on 2012-04-04
Hi dfacto,

many thanks for your reply, but for me re-installing is not an option .... (unless I cannot get it working in two moths)

I'll try your hints about the fans.

On the other hand, are you able to connect an external display without any problems?


Thanks

---

### Post by dfacto on 2012-04-04
I don't have an adapter so I cannot test an external display.

In general I am not an advocate of re-installing as this is a Windows-type "solution."  I just went this route because I wanted to test the out-of-box-ness of the latest release.

In any event, what prevents you from doing this?  In my case I just rsync-ed everything to another computer, re-installed, and rsync-ed back. (Strictly speaking I didn't need to do this since I do have a separate home partition, but since I had partition-table issues the first time I was cautious...which is always recommended anyway.)

---

### Post by zmiq2 on 2012-04-04
I don't want to re-install because it's my main computer, and I don't want to risk and spend the time and effort to rebuild it, call me lazy ....., re-installing is too-windows for me and there's no proof that re-installing will make it work.

I'll keep an eye on google to see if the issue gets solved sometime ....


Thanks anyway!

---

### Post by zmiq2 on 2012-04-10
Hi again,

after today updates, I still have problems with the external monitor.

But I have good news: external monitor works as expected when booting with linux kernel 3.2.0-21 (current one, 3.2.0-22 doesn't work).


HTH

---

### Post by zmiq2 on 2012-04-11
I'm still facing problems with the external monitor; with kernels 3.2.0-22 and -21, I have finally found a consistent way to have the external monitor working:

boot without external monitor
log into X
connect external monitor -> doesn't work

repeat about 2/3 times:
  disconnect external monitor
  suspend
  connect external monitor
  resume

It worked for me for 3.2.0-22 and -21 kernels. Probably there's a better way, but meanwhile I'm sticking to this.

HTH

---

### Post by dfacto on 2012-04-11
If that works then surely xrandr will do the trick.

---

### Post by zmiq2 on 2012-04-13
With latest update, kernel 3.2.0-23, external monitor seems to work ok!!

Now I can recommend going to ubuntu 12.04:

- everything seems snapier

- ubuntu works out-of-the-box

Happy camper now !

---

### Post by dvarnes on 2012-04-13
> **zmiq2 said:**
> With latest update, kernel 3.2.0-23, external monitor seems to work ok!!

Now I can recommend going to ubuntu 12.04:

- everything seems snapier

- ubuntu works out-of-the-box

Happy camper now !


zmiq2: What resolution is your external monitor ?

---

### Post by zmiq2 on 2012-04-13
Hi,

I have a 1920x1200 (dell 24'').

But, even my earlier post, I still have some problems with the external monitor, which the only way I found to have it solved is to go through a supend-resume cycles (normally 2) until it works.

I have found another problem: when playing a video (mp4 or avi, not flash), using the Video Player or mplayer, my computer hungs; mouse moves, but gnome is freezed, keyboard doesn't work, and the only way is to recover is power cycle the computer.

Any hints about this video issue?

Thanks in advance.

---

### Post by Zeleran on 2012-04-13
Not sure if this should be here or in the mtrack thread, think it fits both...

Anyways, just installed Ubuntu 11.10 on my MBA 4,2 last night, and I cannot get the trackpad to work at all.  It was working with basic function (moving around and left clicking) before I ran the post-install-oneiric.sh script, but after that it doesn't work at all.  

That script was supposed to install mtrack, and it said it did it correctly, so I'm a bit stumped as to what went wrong.

---

### Post by Obfuscator on 2012-04-15
> **Zeleran said:**
> Not sure if this should be here or in the mtrack thread, think it fits both...

Anyways, just installed Ubuntu 11.10 on my MBA 4,2 last night, and I cannot get the trackpad to work at all.  It was working with basic function (moving around and left clicking) before I ran the post-install-oneiric.sh script, but after that it doesn't work at all.  

That script was supposed to install mtrack, and it said it did it correctly, so I'm a bit stumped as to what went wrong.

Hi! I just installed and figured out that the postinstall script fails silently when the mtrack and dispad packages cannot be fetched. The urls are [http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_oneiric_amd64.deb](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_oneiric_amd64.deb)

and 

[http://www.dev.fatedmariner.org/packages/dispad/ubuntu/dispad_0.1_oneiric_amd64.deb](http://www.dev.fatedmariner.org/packages/dispad/ubuntu/dispad_0.1_oneiric_amd64.deb)

You just need to grab these and install them. For me the site is still down, so I compiled them myself instead using the commented out instructions in the script. Look around those urls in the script and you will find the compilation instructions.

---

### Post by Zeleran on 2012-04-15
> **Obfuscator said:**
> Hi! I just installed and figured out that the postinstall script fails silently when the mtrack and dispad packages cannot be fetched. The urls are [http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_oneiric_amd64.deb](http://www.dev.fatedmariner.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.2.0_oneiric_amd64.deb)

and 

[http://www.dev.fatedmariner.org/packages/dispad/ubuntu/dispad_0.1_oneiric_amd64.deb](http://www.dev.fatedmariner.org/packages/dispad/ubuntu/dispad_0.1_oneiric_amd64.deb)

You just need to grab these and install them. For me the site is still down, so I compiled them myself instead using the commented out instructions in the script. Look around those urls in the script and you will find the compilation instructions.


So I just tried doing what I think you recommended and Im still stuck in the same situation without a working touchpad.

Could you maybe give a quick run through of the commands you used?

Thanks

---

### Post by zmiq2 on 2012-04-16
Hi,

I'm again having problems booting with an eternal monitor attached. I'm currently running 12.04, but booting kernel 3.2.0-17, and waiting for a new kernel that works...

I've spent last hour booting, rebooting, x-restarting, plug/unpluggin external monitor, and no way. I have external monitor working only by booting -17.

HTH

---

### Post by Obfuscator on 2012-04-17
> **Zeleran said:**
> So I just tried doing what I think you recommended and Im still stuck in the same situation without a working touchpad.

Could you maybe give a quick run through of the commands you used?

Thanks

Sure, no problem.

This is copied straight out of the script:

```
sudo aptitude install autoconf libtool libmtdev-dev xserver-xorg-dev xutils-dev
	git clone https://github.com/BlueDragonX/xf86-input-mtrack.git
	cd xf86-input-mtrack/
	# http://ubuntuforums.org/showpost.php?p=10881280&postcount=105
	# libtoolize && aclocal && autoconf && automake --add-missing --copy
	autoreconf --install --force
	# should install to: /usr/lib/xorg/modules/input/
	./configure --prefix=/usr
	dpkg-buildpackage
	cd ..

```
and

```
# --- dispad
	echo "Building dispad (touchpad pause daemon)."
	sudo aptitude install autoconf libtool libconfuse-common libconfuse0 \
		libx11-dev libconfuse-dev libxi-dev xserver-xorg-dev 
	git clone https://github.com/BlueDragonX/dispad.git
	cd dispad
	autoreconf --install --force
	./configure 
	dpkg-buildpackage
	cd ..

```

Then you need to install the two resulting .deb-s with ```
dpkg -i example.deb
```

I'll try to attach the debs that I've built as well if you want to try. I cannot guarantee anything, but they worked for me.

---

### Post by petelox1 on 2012-04-17
Hi,

I have recently installed ubuntu on my macbook air (mid 2011) by following the instructions on the ubuntu macbook air 4,1 and 4,2 page. I ran the post-install script for the LCD and trackpad only, and both seemed to work well (i.e the correct resolution was displayed and the trackpad worked). 

The problem I have is that suddenly, after several reboots (where everything appears to work fine), I get the "grub rescue" command prompt appearing after selecting to boot linux in the refit menu. The error message is "error: file not found". I have re-installed ubuntu from scratch several times now, and always see the same behaviour. 

Does anyone have any suggestions as to what is most likely causing this, and how to fix it?

---

### Post by petelox1 on 2012-04-17
To add to the previous post, running the _[COLOR=black]FULL[/COLOR]_ post-install script, then rebooting leads to the following:

"An error occurred while mounting /"

Using sudo mount /dev/sda4 (sda4 is the linux partition set to root in the instructions on the ubuntu page) gives 

"/dev/sda4 already mounted or / busy"

---

### Post by petelox1 on 2012-04-17
Am I going to have to learn Mac OS?!! Or swap this cool hardware for a PC?

---

### Post by Zeleran on 2012-04-17
> **Obfuscator said:**
> 
Then you need to install the two resulting .deb-s with ```
dpkg -i example.deb
```


Brilliant! I just realized in my frustrated attempt to get this fixed, I had completely forgotten to install the actual mtrack dev, I only install the dispad one (not that useful, hah).

Thanks so much, this got it working perfectly.

---

### Post by jrm7262 on 2012-04-19
Hi All

      Have finally got everything working on my Macbook Air except the multitouch on the trackpad. (which means I have no right click and no tap to click, which is what I'm after)

Have followed all the steps for installing the mtrack and dispad but with no joy.

When I run synclient it keeps telling me I have no synaptic driver installed, anyone any ideas?


Kindest regards
James

---

### Post by jonny on 2012-04-20
petelox1, Zeleran, jrm7262: Ubuntu 12.04 will be out in a metter of days.  11.10 needs significant tweaking and, if you're struggling to make things work immediately, you're probably best to wait for the new release.  ALternatively, you might hit lucky in the meantime with the Beta or daily update of 12.04.

---

### Post by jrm7262 on 2012-04-20
Hi jonny,

               Thanks for the reply.

Being relatively new to ubuntu, is there an easy upgrade path from 11.10 to 12.04, or is it a compete re-install?


Kindest regards
James

---

### Post by jonny on 2012-04-21
> **jrm7262 said:**
> Hi jonny,

               Thanks for the reply.

Being relatively new to ubuntu, is there an easy upgrade path from 11.10 to 12.04, or is it a compete re-install?


Kindest regards
James
When it's released, you'll be prompted to upgrade within a day or two.  If you're feeling impatient, you can upgrade to the latest daily release with the command
```
sudo update-manager -d
```
You might get cleaner results with a fresh installation if you've messed around with your 11.10 installation trying to get it to work properly.  Otherwise, an upgrade will be fine.  I have one computer that I've upgraded through ten different release cycles with no significant problems.

---

### Post by jonny on 2012-04-21
I should say, though, that a fresh installation is usually much faster - 5 minutes to download and burn the USB stick and another 10 to install it.  Upgrading can take several hours on a slower PC, although it should be much faster on an Air due to the SSD.  I'll find out for myself in a few days.

---

### Post by jrm7262 on 2012-04-21
Hi Jonny,

                     The touchpad now works as expected, thank you.

Just in case anybody else wants to try this - this was my experience:
I had to change some settings before the upgrade would work, I found I had it set to Long term upgrades only initially.
The upgrade took about 45 minutes in total. (This is on the 11" Macbook air with 4GB memory)
I have Ubuntu on an 8GB partition and during the upgrade it got to within a couple of hundred MB (mega) of full.
After the upgrade I'm back to about 1GB (giga) free.
On the initial restart the touchpad didn't work at all, I plugged in a mouse and installed gpointing and touchegg (not sure yet which one solved the problem) the touchpad now works fine.
Also initially the keyboard was very slow in responding to key presses but on second restart that seemed to sort itself out.

The only thing that doesn't seem to work is screen brightness, any ideas on this?

(Update - Did a clean install of 12.04 using AMD64+Mac.iso, everything works, and takes 2.5GB of my 8 GB partition. And for Washakie below - this was on an 11" Macbook Air bought in London about 3 weeks ago)


Kindest regards
James

---

### Post by washakie on 2012-04-22
Jonny et al,

I'm thinking to buy a new MBA 11" with the i7 processor. I'm after the hardware, and I want to put 12.04 on it. It seems there is a variety fo possibilities, and from what I've found it seems the hardware will be mostly supported. What I haven't been able to understand is whether I go to the applestore.com today and order the machine, will it be a 4.2 Mac?

I just want to make sure that all the 'successful' installation stories are working with contemporary hardware, and that Apple hasn't done anything to make it more difficult to install a more open OS on their hardware.

Could someone post a link to the most recent and complete set of tutorials to follow to do the installation? I would currently start with the ubuntu forums guides, but if there is anything else I should be aware of, please let me know.

Thanks!

---

### Post by jonny on 2012-04-23
> **washakie said:**
> Jonny et al,

I'm thinking to buy a new MBA 11" with the i7 processor. I'm after the hardware, and I want to put 12.04 on it. It seems there is a variety fo possibilities, and from what I've found it seems the hardware will be mostly supported. What I haven't been able to understand is whether I go to the applestore.com today and order the machine, will it be a 4.2 Mac?

I just want to make sure that all the 'successful' installation stories are working with contemporary hardware, and that Apple hasn't done anything to make it more difficult to install a more open OS on their hardware.

Could someone post a link to the most recent and complete set of tutorials to follow to do the installation? I would currently start with the ubuntu forums guides, but if there is anything else I should be aware of, please let me know.

Thanks!
If you buy one today from Apple, it will be a 4.2 Mac.  It's impossible to guarantee that Apple won't have suddenly decided to change supplier for some components, but that seems unlikely.

Based on others' recent experieces, you're best to install the Mac version of Ubuntu 12.04 - even though it's not yet been formally released - rather than 11.10.  Most of this thread and most of the MAcbook Air 4,2 page on the Ubuntu wiki concerns workarounds needed for 11.10 and can therefore be safely ignored.  I'm not using 12.04 myself yet, so I can't point to definitive instructions.  However, the general approach will be to:

1. Download the latest version of 12.04 AMD64 for Mac, using either the latest Beta or the latest daily snapshot according to your appetite for stability vs recency.

2. Follow the instructions on the Ubuntu Wiki to burn a USB stick and install the software, including the steps for Refit.

3. DON'T attempt to install any of the post-installation patches

I'm sure that someone who's already installed 12.04 will be along to add extra details if I've missed anything out.

---

### Post by washakie on 2012-04-23
Thanks this is helpful. I'll probably go ahead an wait until 12.04 is official anyway, not for any other reason than I won't have the hardware before then.

I'm glad you included the part about the post install scripts. Thanks again for the response!

This is my 'starting' point:
[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

In the meantime, I also noticed this thread was just produced, so I'll follow it:
[http://ubuntuforums.org/showthread.php?t=1963418](http://ubuntuforums.org/showthread.php?t=1963418)

Lastly, it seems there are a variety of bugs to follow up on here:
[https://launchpad.net/+search?field.text=macbook+air+4%2C2+12.04&field.actions.search=Search](https://launchpad.net/+search?field.text=macbook+air+4%2C2+12.04&field.actions.search=Search)

I've found no 'walk through tutorial' on line so far.. so if anyone knowledgeable is listening 8)

---

### Post by zmiq2 on 2012-04-24
Hi washakie,

i have a 11'' mba, i7, 6g RAM with ubuntu 12.10.

Everything is running great except:

- cannot play non-flash videos (computer hangs)

- issues with external monitor; I can only have the external monitor running with an ld kernel ....


HTH

---

### Post by zmiq2 on 2012-04-25
I just installed the xorg-edges ppa, and now everything seems to work fine: external monitor, video playing, suspend-resume !!


HTH

---

### Post by jrm7262 on 2012-04-26
Hi zmiq2,

                     Ive just had a problem with the cursor freezing after a suspend/resume cycle.
You say you installed the xorg-edges ppa and it seems to have solved the suspend-resume problems you had.

So my question is : What is the "xorg-edges ppa" and how do I install it?


Kindest regards
James

---

### Post by jebus_beler on 2012-04-26
Hi All,

I'm happily running 11.10 on a macbook air 4,2 and have been doing so for a while now but I'm tempted to do the auto-upgrade to 12.04 since I'd like better multitouch support (everything else works pretty damn well now) and maybe better battery life.

Has anyone done an upgrade and can recommend for/against doing so.  I've run the 11.10. post-install scripts quite often (after updates, etc...) so I'm a little worried its modifications to the base configuration might conflict with the automated 12.04 update.

Normally I would just try it and sort out any issues but I'm on the road for another few weeks and I need my laptop to work so I'm weary of any issues...

I'd be grateful to hear of how others have weathered the update.  Also is the macbook air better in 12.04?  i.e. battery or trackpad.

---

### Post by inspiredbylasers on 2012-04-26
I'm actually having issues with my trackpad/mouse freezing after the Mac is reawakened from Standby.

I don't feel as though the dock is working properly, either. However, that doesn't actually come off as an issue.

---

### Post by zmiq2 on 2012-04-27
Hi jrm,

this will install automatic upgrade to latest X builds:

```


sudo add-apt-repository ppa:xorg-edgers/ppa


```

After doing that, just go to update manager, 'check' for new upgrades, and install found upgrades.

Even though, with 12.04, I'm still facing issues with external monitor, so I still cannot recommend going to 12.04 completely ....

---

### Post by mr_manny on 2012-04-27
> **inspiredbylasers said:**
> I'm actually having issues with my trackpad/mouse freezing after the Mac is reawakened from Standby.

I don't feel as though the dock is working properly, either. However, that doesn't actually come off as an issue.


trackpad solution that worked for me was proved from following thread:

[http://ubuntuforums.org/showthread.php?t=1952532](http://ubuntuforums.org/showthread.php?t=1952532)

adding the following to /usr/lib/pm-utils/defaults worked like a charm :)

SUSPEND_MODULES="bcm5974"

---

### Post by jrm7262 on 2012-04-27
zmiq2

        Thank you


                          Another rather simple question to anyone - how do I type a ¨hash¨ ? 
                           alt 3 doesn work. Is the hash hidden somewhere, or how do I remap a key?
(this is on a macbook air)


Kindest regards
James

---

### Post by jonny on 2012-04-28
> **jrm7262 said:**
> zmiq2

        Thank you


                          Another rather simple question to anyone - how do I type a ¨hash¨ ? 
                           alt 3 doesn work. Is the hash hidden somewhere, or how do I remap a key?
(this is on a macbook air)


Kindest regards
JamesHave you tried using the right-hand Alt key?  Confusingly, the left key does something different.

---

### Post by jrm7262 on 2012-04-28
Thanks for the reply jonny.

Interestingly the right alt key gives me a great collection of many useful symbols in conjunction with the shift and cmd keys (thanks for the tip) but alas no hash.

Is there a simple way to remap a key?

Kindest regards
James

---

### Post by nibbuti on 2012-04-29
> **jrm7262 said:**
> Is there a simple way to remap a key?
xmodmap

---

### Post by nibbuti on 2012-04-29
Which version is preferable for MBA Mid '11?

64bit or 32bit?

:confused:

---

### Post by ts3 on 2012-04-29
> **nibbuti said:**
> Which version is preferable for MBA Mid '11?

64bit or 32bit?

:confused:

For what it's worth I've been using the 64bit version on an 11'' mid 2011 MBA. 

With 12.04 almost everything works out of the box, including the function keys for sound, screen brightness and keyboard backlights; the only exception is the touchpad freezing after suspending by closing the lid.  There is an easy fix for that (see a few posts above) so no complaints.  I'm not even sure whether the 32bit version will work at all.

---

### Post by NickSH on 2012-04-30
A quick question.  I bought my macbook air about 2 months ago.  I am assuming based on some posts I read that it is a macbook 4.2.

My question is (just want to make sure I'm reading this right) is the new Ubuntu more stable (or have less driver issues) on a macbook air than previous versions.  

I ask because I'm a linux newbie and would like to get something where everything works so I can start exploring the system, rather than constantly trying to figure out how to install a trackpad driver.

What are your thoughts?

Nick

---

### Post by langerak on 2012-05-02
I've installed Ubuntu 12.04 on my MacBook Air 4,2 today and all is working great!

There is one thing that bugs me and that is the laptop screen that constantly dims after 5 seconds if the machine is not used.

I've tried the brightness settings and put the slider all the way to the right and unchecked the dim checkbox, but the slider always reverts back to it's position...

Is there a way to solve that issue?

---

### Post by poliva on 2012-05-02
> **langerak said:**
> I've installed Ubuntu 12.04 on my MacBook Air 4,2 today and all is working great!

There is one thing that bugs me and that is the laptop screen that constantly dims after 5 seconds if the machine is not used.


Change the screenidle configuration option in ligtum, edit ~/.config/lightum/lightum.conf and add the following at the end:

```
screenidle=30
```

it will dim after 30 seconds.
You need to restart lightum for this to work (or logout your current session, and login again).

---

### Post by warpino on 2012-05-02
Hi everyone,

can you point me to a decent guide for installing 12.04 on MBA 2011? All infos seem to be so messy!! ;-)

Furhtermore, in some posts a 12.04+mac iso file is explicitly named, I try to download it from here:

[http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64+mac.iso)

but the link doesn't seem to work!

One more thing. Somewhere (but I can't find the post anymore) it is stated that installing from CD is  supported only and installing from USB is not suggested. Some posts in this thread seem to say the opposite. Am I missing something?

Thank you all for your help!

---

### Post by poliva on 2012-05-02
> **warpino said:**
> Hi everyone,

can you point me to a decent guide for installing 12.04 on MBA 2011? All infos seem to be so messy!! ;-)


The download ISO of 12.04 for Mac is here:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

Just install normally as you would on any other PC, for detailed instructions read the wiki, although they are for 11.10 they are still valid for 12.04:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

Just don't run the post-install-oneiric script, as it is 11.10 specific (you can selectively pick any custom changes from the script if you want to have some of its goodness on 12.04, but most things already work out of the box on 12.04).

And yes, you can install from USB without issues, it's explained in the wiki too.

---

### Post by warpino on 2012-05-02
> **poliva said:**
> The download ISO of 12.04 for Mac is here:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)



The download link still seems not to work for me :(

---

### Post by warpino on 2012-05-02
The file is not even listed on [www.ubuntu.com](www.ubuntu.com) and I cannot find the md5 sum either:

[https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS](https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS)

what happens?

---

### Post by poliva on 2012-05-02
> **warpino said:**
> The file is not even listed on [www.ubuntu.com](www.ubuntu.com) and I cannot find the md5 sum either:

[https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS](https://help.ubuntu.com/community/UbuntuHashes#A12.04_LTS)

what happens?

Try here:
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

And md5sum here:
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/12.04/release/MD5SUMS](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/12.04/release/MD5SUMS)

---

### Post by warpino on 2012-05-02
it's downloading now, thank you very much!
So you reckon it is more appropriate to install this version rather than the "normal" one?

---

### Post by poliva on 2012-05-02
yes, this image is adjusted to work properly on Mac systems.

Btw, I've modified the post-install-oneiric script, removed the 11.04 specific stuff and added a few customizations for 12.04, you can download it here:

[http://pof.eslack.org/archives/files/mba42/post-install-precise.sh](http://pof.eslack.org/archives/files/mba42/post-install-precise.sh)

---

### Post by poliva on 2012-05-02
Wiki page updated with instructions for 12.04:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

---

### Post by jebus_beler on 2012-05-03
Still haven't bothered with the update.  Any reason to do a fresh install of 12.04 over an update of 11.10 (which has had post-install run on it)?

Also in 11.10 suspend works fine but the apple light flashes on and off a few times before finally sleeping and waking is also a pain since I first get my pre-suspend screen then the screen slowly locks and then I have to type a password.  No chance this has been improved in 12.04 (I'm guessing its a general X issue and not MBA specific but just checking anyway).

---

### Post by poliva on 2012-05-03
> **jebus_beler said:**
> Still haven't bothered with the update.  Any reason to do a fresh install of 12.04 over an update of 11.10 (which has had post-install run on it)?

Both options are perfectly fine.

> **jebus_beler said:**
> Also in 11.10 suspend works fine but the apple light flashes on and off a few times before finally sleeping and waking is also a pain since I first get my pre-suspend screen then the screen slowly locks and then I have to type a password.  No chance this has been improved in 12.04 (I'm guessing its a general X issue and not MBA specific but just checking anyway).

The password after resume can be disabled on both 11.10 and 12.04:
```

gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'

```

---

### Post by langerak on 2012-05-03
> **poliva said:**
> Change the screenidle configuration option in ligtum, edit ~/.config/lightum/lightum.conf and add the following at the end:

```
screenidle=30
```

it will dim after 30 seconds.
You need to restart lightum for this to work (or logout your current session, and login again).

Thanks for the tip! That solved my issue :).

---

### Post by jamesgg on 2012-05-03
Anyone else also experiencing the screen brightness and the backlit keyboard reseting to maximum after every restart? I have a 4,2 13-inch macbook stock 12.04 ubuntu kernel. Is there a script to allow the OS to save these settings?

---

### Post by zmiq2 on 2012-05-04
I'm with 12.04, and a 11'' mb, and I experience the same issue with keyboard back-light.

For me is not a problem since I just reboot when there's a new kernel update; I suspend/resume for days, and that keeps those settings between sessions.

HTH

---

### Post by jamesgg on 2012-05-04
> **jamesgg said:**
> Anyone else also experiencing the screen brightness and the backlit keyboard reseting to maximum after every restart? I have a 4,2 13-inch macbook stock 12.04 ubuntu kernel. Is there a script to allow the OS to save these settings?

After running the script on the wiki 4,2 macbook 12.04 page with a combination of software update through the manager, the brightness and keyboard backlight is unable to be changed at all, the brightness being set to minimum. Perhaps unrelated, but luminance crashes very often. Being new to linux, I have no idea if it was wise to update the list of software from the manager.

---

### Post by poliva on 2012-05-04
@jamesgg: 

the keyboard brightness and screen backlight are automatically adjusted depending on ambient light (from the iSight camera). You can tune the functionality on the config file ~/.config/lightum/lightum.conf

If you want to disable it completely, just uninstall it: aptitude remove lightum.

---

### Post by PiSToLBR on 2012-05-04
> **poliva said:**
> Wiki page updated with instructions for 12.04:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)


Thanks mate!

PiSToL

---

### Post by dfacto on 2012-05-06
Has anyone had a problem with the network driver being very slow to load and connect after resuming from suspend?  I'm on 12.04.

---

### Post by minicheffe on 2012-05-07
> **dfacto said:**
> Has anyone had a problem with the network driver being very slow to load and connect after resuming from suspend?  I'm on 12.04.

Same here!

---

### Post by poliva on 2012-05-07
@dfacto: yes, it's much slower on 12.04 than it was on 11.10... it also bugs me having to wait those extra seconds for the wifi to connect when resuming.

---

### Post by timuckun on 2012-05-08
> **poliva said:**
> Wiki page updated with instructions for 12.04:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

I just tried those instructions and they don't quite work.

the script they tell you download and run does not work because the directory structure is different with 12.04. I changed the script a little bit to point to the right files but it doesn't boot up giving the error

mounting /dev/loop0 on //filesystem/squashfs failed no such device

cannot mount /dev/loop0 (/cdrom/casper/filesystem/squashfs) on (//filesystem.squashfs)

Just FYI

---

### Post by zaphod777 on 2012-05-09
How is the external monitor support running Ubuntu 12.04? I am thinking of getting one of these but I want to connect it to an external display.

---

### Post by warpino on 2012-05-09
Hi guys,

in the guide you pointed me to: [https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2) they say:

> The MacBookAir4,2 has no CD/DVD drive, and cannot start Ubuntu from a USB stick created using the standard tools. However, a script is available that will create a suitable USB image - do not believe the opinion widely expressed on other websites that it is necessary to purchase an Apple Superdrive. Note that: lines 21 and 22 of the script need to be edited in accordance with the adjacent comments; the script must be run from within Ubuntu and will not work under OS X, so you'll need another PC with Ubuntu (possibly running from a Live CD or Live USB image) to complete the task; and the script will not work on Ubuntu 10.04 Lucid Lynx. Once the script has been edited, it must be made executable and executed with root privileges: 

```
cd [path to script]
chmod a+x setup_mac_usb_boot.sh
sudo ./setup_mac_usb_boot.sh
```


This doesn't seem to apply to me, as I actually followed this guide to make a bootable usb from osx: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)
and I can boot into ubuntu live from the USB with no problems.

Can I install ubuntu right from there then?

---

### Post by mr_manny on 2012-05-09
> **poliva said:**
> @dfacto: yes, it's much slower on 12.04 than it was on 11.10... it also bugs me having to wait those extra seconds for the wifi to connect when resuming.

Wonder if this is a window mgr thing...no noticable wifi issues when using fluxbox :)

---

### Post by uBeer on 2012-05-10
> **zaphod777 said:**
> How is the external monitor support running Ubuntu 12.04? I am thinking of getting one of these but I want to connect it to an external display.

Well, connecting to an external monitor is fine, just like configuring one. But what is not working fine is when you disconnect the monitor...
Display turns black.
After that I have to go to a tty and restart lightdm service to get the xserver to find my display again.

So now I close all my important programs before I disconnect so that I can savely restart X.

---

### Post by zmiq2 on 2012-05-10
I'm also having issues with my external monitor; sometimes it works, sometimes it doesn't, sometimes I have to let the computer go into screen-saving and at resume it works ...

I haven't found a rule to always have the external monitor working, so, in order to have it working, my safe bet is to boot with the 3.2.0-17 kernel, which always makes the external monitor work.

HTH

---

### Post by berryman77 on 2012-05-11
Ditto on the external monitor.  I'm connecting via thunderbold/hdmi and having to use Ubuntu2D to function in 12.04.  In 11.10 I could use the 3D desktop and just closing and opening (not suspending - AC is connected) the lid would correct the external display (sometimes orange, sometimes black).

I've run xorg-edgers with the latest kernel and there seems to be no progress (assuming the problem is in the driver or kernel) upstream.  I don't see any errors logged to correlate with the display problems, so I'm not sure how to report this bug with any useful detail.  I'd like to get this bug reported properly.  Has anyone here attempted a bug report and can you post a link?

Anyone know if this is somehow specific to the Macbook Air or are other Sandy Bridge platforms having the same issue(s).  I was hoping that it would get ironed out given how common these graphics are.  And hey, even Linus uses a Macbook Air, but I guess he doesn't connect it to an external monitor :)

---

### Post by zmiq2 on 2012-05-11
Hi Berryman,

regarding the external monitor issue, I'm following this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929635)

but I doesn't seem to have many activity since last month ....


HTH

---

### Post by warpino on 2012-05-13
Maybe I'm asking for too much... is it possible to share a logical volume between the two OSs? I'd like to set up a HFS+ shared partition using LVM in ubuntu. Can I do that?

w.

---

### Post by minicheffe on 2012-05-14
> **warpino said:**
> Maybe I'm asking for too much... is it possible to share a logical volume between the two OSs? I'd like to set up a HFS+ shared partition using LVM in ubuntu. Can I do that?

w.

Yes sure. But when you use the hfs+ format I think you have to disable the journaling in osx.
It would be easier to format the "share partition" in ntfs or fat.

Christoph

---

### Post by NickSH on 2012-05-15
Hello,
I just updated to 12.04 on macbook air 4,1.  Overall, I'm very impressed on how easy the installation went, compared to 11.10.

Having said that, I'm having a problem with the post install script.

When it gets to the part where it wants to install lightum, it either gives an error, which says

cat: /home/nick/.config/lightum//lightum.conf.
This is on the third time trying to run the script.
Previously, it gave an actual error stating that a directory that had something to do with icons was not there.

Anythoughts?

Thanks,
Nick

---

### Post by shuhart on 2012-05-15
> **NickSH said:**
> Hello,
I just updated to 12.04 on macbook air 4,1.  Overall, I'm very impressed on how easy the installation went, compared to 11.10.

Having said that, I'm having a problem with the post install script.

When it gets to the part where it wants to install lightum, it either gives an error, which says

cat: /home/nick/.config/lightum//lightum.conf.
This is on the third time trying to run the script.
Previously, it gave an actual error stating that a directory that had something to do with icons was not there.

Anythoughts?

Thanks,
Nick

Try to launch post install script without sudo. Do just
```
./post-install-precise.sh
```

---

### Post by poliva on 2012-05-15
@shuhart: good catch! I've updated the wiki instructions, and added an extra check in the script to make sure it is run as regular user, not root.

---

### Post by Kallun on 2012-05-15
Hi

If it's not too much trouble, would some of you mind taking a look at [my thread](http://ubuntuforums.org/showthread.php?t=1980036) for setting up various things on the MBA 4,1?

It'd be greatly appreciated! :D

---

### Post by NickSH on 2012-05-15
It seemed to work, but again got to the lightum install and stopped. It gsve the message...
/usr/share/lightum-indicator/lightum-indicator-include: line 101: /home/nick/.config/lightum//indicator.icon: Permission Denied

As a seperate, (or perhaps related) issue, why would

/etc/X11/xorg.conf be empty?  It's just a blank file when I open it, yet it seems that a lot of the trackpad configuration should be in there.

Thanks,
Nick

---

### Post by poliva on 2012-05-15
> **NickSH said:**
> It seemed to work, but again got to the lightum install and stopped. It gsve the message...
/usr/share/lightum-indicator/lightum-indicator-include: line 101: /home/nick/.config/lightum//indicator.icon: Permission Denied


run the following:
```

$ sudo rm -r /home/nick/.config/lightum/
$ sudo killall lightum
$ sudo killall cappind-lightum
$ lightum
$ lightum-indicator

```

this should start lightum clean, and create a new default config.

> **NickSH said:**
> 
As a seperate, (or perhaps related) issue, why would

/etc/X11/xorg.conf be empty?  It's just a blank file when I open it, yet it seems that a lot of the trackpad configuration should be in there.

If it's empty you're using the default synaptics module for the trackpad, if you want to use a different mouse driver, then it's configured there, see instructions in the wiki.

---

### Post by NickSH on 2012-05-15
I tried it.  This is the response.  Do you think possibly something went wrong with install?


nick@nick-MacBookAir:~$ lightum
lightum v2.3 running in auto mode forked into background
nick@nick-MacBookAir:~$ Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.Solid.PowerManagement was not provided by any .service files
Can't manage screen backlight on this system.
Please disable backlight with config option 'workmode='1' or command line switch '-w 1'.
If you believe this is an error, open a bug report: [https://github.com/poliva/lightum/issues](https://github.com/poliva/lightum/issues)

nick@nick-MacBookAir:~$ lightum-indicator
lightum v2.3 running in auto mode forked into background
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.kde.Solid.PowerManagement was not provided by any .service files
Can't manage screen backlight on this system.
Please disable backlight with config option 'workmode='1' or command line switch '-w 1'.
If you believe this is an error, open a bug report: [https://github.com/poliva/lightum/issues](https://github.com/poliva/lightum/issues)

Thanks,
Nick

---

### Post by poliva on 2012-05-15
> **NickSH said:**
> I tried it.  This is the response.  Do you think possibly something went wrong with install?

That's weird, have you changed the default window manager? does it happen after a reboot?

---

### Post by NickSH on 2012-05-15
Nope.  Haven't changed any defaults.  Though I am using Lubuntu, which uses LXDE desktop, rather than Ubuntu.

I'm goin try reinstalling, as I'd like to change my partitions a bit anyway.

Nick

---

### Post by poliva on 2012-05-15
> **NickSH said:**
> Though I am using Lubuntu, which uses LXDE desktop, rather than Ubuntu.

That explains it, lightum cannot adjust the backlight in LXDE, you'll need to edit ~/.config/lightum/lightum.conf and change workmode=3 to workmode=1

---

### Post by poliva on 2012-05-15
> **dfacto said:**
> Has anyone had a problem with the network driver being very slow to load and connect after resuming from suspend?  I'm on 12.04.

I've attached some info on this bug:

[https://bugs.launchpad.net/bugs/994739](https://bugs.launchpad.net/bugs/994739)

Please click on the "this bug affect you" so it gets more bug heat score :)

---

### Post by poliva on 2012-05-17
Finally found the reason of the ~30 seconds after resume for the wifi to associate to an AP:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994739/comments/9](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994739/comments/9)

Basically, in 11.10 we were using the brcmsmac module for the wifi, but 12.04 uses the closed 'wl' driver, which is the one causing the problem. If you switch to brcmsmac in 12.04 you'll get again the 5 seconds resume time like it was in 11.10 :D

---

### Post by berryman77 on 2012-05-17
I also have the lag, though I am reluctant to switch drivers because with wl, I get a better signal and power management settings work.  I'd like to hear if anyone has worked around these issues with brcmsmac.

---

### Post by poliva on 2012-05-17
@berryman77: In quantal (12.10) there's a newer version of the wl driver available (5.100.82.112), I haven't tested it though, but maybe it's worth a try if it has the benefits of wl driver and eliminates the 30s delay...

---

### Post by poliva on 2012-05-17
FYI I just built the broadcom-sta 5.100.82.112-7 from [source package]("https://launchpad.net/ubuntu/+source/broadcom-sta/5.100.82.112-7") on 12.04, tried it and worked successfully, but still has the 30 seconds delay issue. bummer. :(

---

### Post by poliva on 2012-05-19
Here's a script that wiill download and patch wpa-supplicant automatically, to fix the timeout when using wl driver:

[http://pof.eslack.org/archives/files/mba42/fix-wl.sh](http://pof.eslack.org/archives/files/mba42/fix-wl.sh)

---

### Post by minicheffe on 2012-05-21
> **poliva said:**
> Here's a script that wiill download and patch wpa-supplicant automatically, to fix the timeout when using wl driver:

[http://pof.eslack.org/archives/files/mba42/fix-wl.sh](http://pof.eslack.org/archives/files/mba42/fix-wl.sh)

Thank you works great! =D>

---

### Post by poliva on 2012-05-22
Just FYI, I've been able to reduce the time to associate after resume to 8 seconds using the wl driver :-) for those interested in the details (it's a long story) I've written a blog post here: 

[Why Broadcom 802.11 Linux STA driver sucks, and how to fix it]("http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/")

I put the new broadcom-sta package to a launchpad PPA here: [https://launchpad.net/~poliva/+archive/pof](https://launchpad.net/~poliva/+archive/pof)

At the moment, it's still pending to build in launchpad... when it's done I'll update the wiki with instructions to add the ppa and install the updated driver.

---

### Post by poliva on 2012-06-03
@DanielBuus: if you already have GRUB2 working, there's no point in using rEFIt (or the newer [rEFInd]("http://www.rodsbooks.com/refind/")) unless you want a nicer boot screen.

The EFI boot timeout before GRUB can be avoided using bless, on OSX: ```
sudo bless --device /dev/disk0sX --setBoot --legacy --verbose
``` (where /dev/disk0sX is your linux boot partition).

---

### Post by Cloudane on 2012-06-04
It works so well!

... except for the trackpad.

Well it's not BAD, but the gesture support is rather limited - there's the 3-finger drag for moving a window if you don't mind it moving at about 100MPH :)  There's a 4-finger tap to bring up the Unity menu.  And.. that's about it, with no way of customising it.

Is there any way at all to get the trackpad gestures to work as they would on OS X, AND have everything else working properly?  For example I'd like to drag 4 fingers down to trigger Scale (Expose equivalent).

I've tried using the mtrack driver instead of the default synaptics driver and I can get it working that way - I give it Swipe4DownButton = 16 and use Compiz Settings Manager, Scale menu, and enable all applications scale with button 16.  Great flexibility, however, IMO, the mtrack driver is awful in every other way - it doesn't seem to support acceleration or scrolling inertia, and scrolling is horribly choppy.

touchegg is another suggestion, but doesn't work.  The binary package is simply broken (segfaults) - the SVN version works but:
1) In Unity/GNOME it doesn't register any gestures
2) In KDE, it registers the gestures but they're called "unknown gesture" and don't seem to have any effect.  I can apply various keystrokes either manually or using touchegg-gui and they're not triggered.

Any way to get it working how I'd like?  I'm trying my best not to just boot back into OS X but it's proving difficult at this time :P

---

### Post by Cloudane on 2012-06-05
Further investigation showed that "ginn" is probably what I should be using to customise gestures, but unfortunately ginn doesn't work as Unity hijacks multitouch support via utouch-geis, preventing ginn from starting up.

I managed to stop Unity from hijacking Multitouch with the assistance of
[http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity](http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity)
This version has changed a little but the basics in the answer there are the same.  After removing all references to geis in the source code, recompiling and installing my hacked version of Unity, ginn starts up successfully.

However, it'll only respond to taps. I can set up a 3- or 4-finger tap to do whatever I like, but drag, pinch and other gestures don't work :/  They display just fine in ginn's standard output, the deltas are within range, but the action isn't triggered.  Weird weird weird.

Edit: Okay, not sure if I should be using touchegg or ginn.  Either way, it appears that GEIS has changed and gesture types are possibly not being picked up by either of these tools.
Watching these bug reports: 
[https://code.google.com/p/touchegg/issues/detail?id=148](https://code.google.com/p/touchegg/issues/detail?id=148)  (touchegg on Precise)
and [https://bugs.launchpad.net/utouch-geis/+bug/986886?comments=all](https://bugs.launchpad.net/utouch-geis/+bug/986886?comments=all)   (GEIS possibly returning invalid arguments)
Hopefully we'll eventually see a version of touchegg that works with the new API, and all will be well.

---

### Post by Cloudane on 2012-06-06
I seem to have the monopoly on this thread now :P

But just to say that from a clean reinstall I tried the script mentioned on the wiki related to this thread, and the updated wl driver that it installs doesn't seem to work.  The module loads, but the network manager doesn't acknowledge its existence.  I followed the instructions for using the open source driver instead, and all is well.

Edit: except that my mouse pointer randomly refuses to move after a resume.  (It'll click, and oddly enough, it'll move while the button is clicked down)
Just as I was getting somewhere :(  I may call Linux "still not quite ready" and expand my OS X partition again - it's driving me nuts with all these little bugs.

---

### Post by poliva on 2012-06-06
[QUOTE=Cloudane]But just to say that 
om a clean reinstall I tried the script mentioned on the wiki related to this thread, and the updated wl driver that it installs doesn't seem to work.  The module loads, but the network manager doesn't acknowledge its existence.[/Quote] 

Blacklist the bcsma module, is a known bug, sorry, will fix it tomorrow morning!

---

### Post by User4519 on 2012-06-06
> **Cloudane said:**
> I seem to have the monopoly on this thread now :P

But just to say that from a clean reinstall I tried the script mentioned on the wiki related to this thread, and the updated wl driver that it installs doesn't seem to work.  The module loads, but the network manager doesn't acknowledge its existence.  I followed the instructions for using the open source driver instead, and all is well.



Yeah, I also saw no reason to install proprietary software on this one. I was already manually stepping through the install script as I'm on Kubuntu, so seeing that one I was basically, "Why?"

For me, the kernel driver reconnects only one or two seconds slower than when using Mac OS X, so I was pretty much surprised to even see a suggestion to use something else for the wifi. Thought it was Ubuntu-specific, now I'm thinking it may be pre-Precise?

---

### Post by Cloudane on 2012-06-06
> **poliva said:**
> Blacklist the bcsma module, is a known bug, sorry, will fix it tomorrow morning!

Thanks for the info.  I take it that it's bcma not bcsma (the latter had no effect) but unfortunately blacklisting that, while it's allowed the network manager to see the adapter, has prevented it from actually connecting to my network :)

---

### Post by poliva on 2012-06-06
@DanielBuus : Read the full story here [http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/](http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/)

---

### Post by Cloudane on 2012-06-06
> **DanielBuus said:**
> Yeah, I also saw no reason to install proprietary software on this one. I was already manually stepping through the install script as I'm on Kubuntu, so seeing that one I was basically, "Why?"

For me, the kernel driver reconnects only one or two seconds slower than when using Mac OS X, so I was pretty much surprised to even see a suggestion to use something else for the wifi. Thought it was Ubuntu-specific, now I'm thinking it may be pre-Precise?

I think it's because, according to the wiki, the OSS driver isn't as good with power management. Also it's chosen by default by Ubuntu when installing.  Though my main concern at the moment is that the OSS driver actually *works* whilst this one doesn't :)
I'd be curious to know how much of a power saving it is.

---

### Post by poliva on 2012-06-06
Cloudane: rmmod wl ; modprobe wl and it should work

---

### Post by User4519 on 2012-06-06
> **poliva said:**
> @DanielBuus : Read the full story here [http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/](http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/)

But that's exactly one problem I don't have? If I close up my Air and let it sleep, then reopen it, it'll wake up and reconnect within, I'd estimate, five seconds.

---

### Post by poliva on 2012-06-06
> **DanielBuus said:**
> But that's exactly one problem I don't have? If I close up my Air and let it sleep, then reopen it, it'll wake up and reconnect within, I'd estimate, five seconds.

because you're using the open source driver, which has far worse power management than the proprietary one.

---

### Post by User4519 on 2012-06-06
> **poliva said:**
> because you're using the open source driver, which has far worse power management than the proprietary one.

Hmm... But still, the battery life I seem to get from Kubuntu is significantly better than what I get from OS X (~5 hrs. vs ~7 hrs.)... So I'm really not moved to do anything proprietary.

Are the prop drivers better in regards to battery life?

---

### Post by poliva on 2012-06-06
> **DanielBuus said:**
> Are the prop drivers better in regards to battery life?

I measured the difference between both drivers using powerstat, and there's around 1 Watt less power used with the wl driver, in my case it increased around 25-30 min the battery life. 

BTW, the wl driver is also open source, but it uses a proprietary binary blob (firmware I assume) from broadcom.

---

### Post by Cloudane on 2012-06-06
> **poliva said:**
> Cloudane: rmmod wl ; modprobe wl and it should work

Great! That did the trick.  I thought a reboot would be enough but obviously it wasn't :P

It's still a bit of a dilemma - it consistently takes a couple more seconds to connect than the open driver, both sleeping and rebooting (especially rebooting, that takes a bit longer).  I'm a speed demon, heh.  Will have to play with some battery timings and see what a difference it makes.  But I appreciate the help with having the choice between the two - that's what Linux is all about eh!

Edit: oh, thanks also for the measurements while I was typing this.  25-30 minutes of battery is significant.

---

### Post by User4519 on 2012-06-07
> **poliva said:**
> I measured the difference between both drivers using powerstat, and there's around 1 Watt less power used with the wl driver, in my case it increased around 25-30 min the battery life. 

BTW, the wl driver is also open source, but it uses a proprietary binary blob (firmware I assume) from broadcom.

Cool :) Guess I'll install it then :) Thanks

---

### Post by minicheffe on 2012-06-09
I use the mtrack driver because I want to use some gestures. Overall it makes the job but it peeves me that when I put two fingers on the pad I can't move the courser. I think it's the same with synaptics. Any ideas?

> **Cloudane said:**
> I've tried using the mtrack driver instead of the default synaptics driver and I can get it working that way - I give it Swipe4DownButton = 16 and use Compiz Settings Manager, Scale menu, and enable all applications scale with button 16.  Great flexibility, however, IMO, the mtrack driver is awful in every other way - it doesn't seem to support acceleration or scrolling inertia, and scrolling is horribly choppy.

Which Scale menu do you mean?

> **poliva said:**
> Blacklist the bcsma module, is a known bug, sorry, will fix it tomorrow morning!
thanks for the update works fine!

---

### Post by Cloudane on 2012-06-09
Anyone else finding that TRIM isn't working?

The "discard" parameter has been correctly added to fstab by the post-install script on the wiki, but following these instructions - which work fine on my desktop SSD:
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)
After deleting the test file and syncing, the data is still present in the sector.

the fstrim command doesn't help either...

> **minicheffe said:**
> Which Scale menu do you mean?


Under Compiz Config (you have to install it) - window management group - Scale is in there.

---

### Post by minicheffe on 2012-06-12
@ Cloudane
thank you.

> **Cloudane said:**
> Anyone else finding that TRIM isn't working?

The "discard" parameter has been correctly added to fstab by the post-install script on the wiki, but following these instructions - which work fine on my desktop SSD:
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)
After deleting the test file and syncing, the data is still present in the sector.

the fstrim command doesn't help either...


same here!

---

### Post by pindar on 2012-06-12
Can any of those running ubuntu on the MBA tell me about its temperature? I have the 11" model and installed the latest linux mint last week (double-boot), and in principle, everything works well (except the touchpad, but I haven't tried other drivers yet). However, I'm really afraid I will fry the machine. Temperature is always higher than in os x, even when most of the cpu is just waiting for input. When I run intensive tasks (luatex), temperature rises beyond 90&#730; C. It's not simply the fan either. When I run the same tex job in os x, the fan stays at 2000 rpm, temperature goes up to ca. 75&#730; or a little bit more. But in linux, the heat seems really excessive, so I'm just wondering what others are experiencing.

pindar

---

### Post by poliva on 2012-06-12
@pindar: something is wrong with your setup, mine stays between 55ºC and 60ºC when idle, with fan at ~2000RPM, and going up to ~80ºC when doing CPU intensive tasks, with fan at ~6000RPM.

---

### Post by pindar on 2012-06-13
> **poliva said:**
> @pindar: something is wrong with your setup, mine stays between 55ºC and 60ºC when idle, with fan at ~2000RPM, and going up to ~80ºC when doing CPU intensive tasks, with fan at ~6000RPM.

Yes, I have no doubt that there's something wrong. But to be quite honest - even your numbers don't look that reassuring. In OS X, I've never seen the fan going up to 6000. It seems that linux doesn't quite have the tools to manage this baby the same way apple does, so I may end up chickening out and deleting my linux partition. This laptop is too important for my to risk it... Thanks anyway!

---

### Post by poliva on 2012-06-13
@pindar: Are you viewing the CPU temperature or the Proximity temperature in OSX? I have more or less the same values in both operating systems when doing the same tasks. The proximity temperature in linux is shown by the TC0P sensor.

---

### Post by Teknoman117 on 2012-06-17
I'm having some issues getting Ubuntu 12.04 installed on my Macbook Air 4,2 (Late 2011).  I've booted into the Live CD, partitioned, ran the installer, got all the way to the end but the bootloader failed to install.  It says in the guide that the small partition created with the flag bios-grub is where you tell grub to install.  However it fails to install.  Does anyone know about this?  I'm using the standard ubuntu 12.04 desktop+mac.iso.

Teknoman

---

### Post by pindar on 2012-06-19
> **poliva said:**
> @pindar: Are you viewing the CPU temperature or the Proximity temperature in OSX? I have more or less the same values in both operating systems when doing the same tasks. The proximity temperature in linux is shown by the TC0P sensor.
I'm looking at CPU temperature in both OS X and Ubuntu. Some quick and unscientific tests show: when process the same long and complex document, in OS X temperature rises to ~ 90&#730;, fans stay at around 2000 rpm. Under linux, temperature rises to ~95&#730;, but fans go way up (in the 4000-5000 rpm, never even heard them go that fast under OS X). Looks like linux is not quite doing the right thing to control this CPU, I don't know if I'll have the courage to keep using Ubuntu on this machine...

---

### Post by jebus_beler on 2012-06-20
> **pindar said:**
> I'm looking at CPU temperature in both OS X and Ubuntu. Some quick and unscientific tests show: when process the same long and complex document, in OS X temperature rises to ~ 90&#730;, fans stay at around 2000 rpm. Under linux, temperature rises to ~95&#730;, but fans go way up (in the 4000-5000 rpm, never even heard them go that fast under OS X). Looks like linux is not quite doing the right thing to control this CPU, I don't know if I'll have the courage to keep using Ubuntu on this machine...

This is of course configurable with macfanctld.  I use the settings:


temp_avg_floor: 45
temp_avg_ceiling: 60
temp_TC0P_floor: 50
temp_TC0P_ceiling: 65

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

in /etc/macfanctl.conf which works ok in cool weather since then the fans only get going when the CPU is busy (which is a Good Thing (tm) I think).  But in warm weather the fans go crazy even if nothing is going on.  Has anyone got any hints on what would be some safe settings?  I don't mind the fan noise but I do worry about the fans lifetime.

---

### Post by jebus_beler on 2012-06-20
I recently updated (quite late) to 12.04 and have to say its been a great experience overall.  The laptop is much smoother: the touchpad works very nicely with synaptic, resume is faster and cleaner (no drop to console in between) and even locking the screen is much snappier.  That aside I've had some problems, some MBA related others not.

The main MBA related one is the fact that the trackpad sometimes (like right now) stops being "multitouch" and goes back to its old 11.10 mtrack behaviour.  It won't accept taps but only clicks and won't two-finger scroll.  This just happens spontaneously and also goes away spontaneously so I don't know what could be causing it.

I'm running just the standard synaptic driver (I think).  I tried touchegg but the daemon segfaulted as soon as it started.  Anyone having similar problems?

---

### Post by jebus_beler on 2012-06-20
> **jebus_beler said:**
> I recently updated (quite late) to 12.04 and have to say its been a great experience overall. 

Scratch that...things aren't so rosy.

I seem to have a very consistent crash when I try to run a certain java application (jabref).  It crashes compiz and apparently corrupts the state of the graphics driver so badly that a reboot is needed.  That is, I can run metacity afterwards but if I try to rerun compiz i get all sorts of crazy screen artifacts even if I restart X.

Kinda lame...I was hoping to not go backwards with 12.04 but in this respect it seems less stable than 11.10 (even though its a few months old).  Anyone seen anything similar?

---

### Post by Murphy2712 on 2012-06-21
> **jebus_beler said:**
> 
The main MBA related one is the fact that the trackpad sometimes (like right now) stops being "multitouch" and goes back to its old 11.10 mtrack behaviour.  It won't accept taps but only clicks and won't two-finger scroll.  This just happens spontaneously and also goes away spontaneously so I don't know what could be causing it.

I'm running just the standard synaptic driver (I think).  I tried touchegg but the daemon segfaulted as soon as it started.  Anyone having similar problems?

I have the same issue!
It happens after several hours of use and I know how to fix it when it happens!
Simply change your terminal back and forth one time:
Ctrl-Alt-F6 (or Ctrl-command-F6) => go to a new terminal session
Ctrl-Alt-F7 (or Ctrl-command-F7 or Ctrl-command-F8 ) => go back to your X session

That's it!
(until next time it breaks...)

---

### Post by jebus_beler on 2012-06-21
> **Murphy2712 said:**
> I have the same issue!
It happens after several hours of use and I know how to fix it when it happens!
Simply change your terminal back and forth one time:
Ctrl-Alt-F6 (or Ctrl-command-F6) => go to a new terminal session
Ctrl-Alt-F7 (or Ctrl-command-F7 or Ctrl-command-F8 ) => go back to your X session

That's it!
(until next time it breaks...)

Thanks a lot!  Should have tried that.  Not great to have to use this fix but as long as it works...  Anyone submitted a bug report I can vote on?

---

### Post by jebus_beler on 2012-06-21
The problems just keep piling on...

I'm not getting a very horrific and consistent GPU crash which I submitted in this bug report:

[https://bugs.launchpad.net/ubuntu/+bug/1016062](https://bugs.launchpad.net/ubuntu/+bug/1016062)

Basically it happens when I run a certain graphical java application (should try it with other java applications) and its pretty consistent.  Unity or Gnome 3 come crashing down and even restarting X doesn't fix the corrupted GPU state.  Metacity seems to work but to use Unity or Gnome I have to reboot.

Anyone got the same, please vote on or update the bug report.

---

### Post by poliva on 2012-06-21
@jebus_beler: are you using unity3d or unity2d? I use unity2d and haven't had any similar issue.

---

### Post by jebus_beler on 2012-06-21
> **poliva said:**
> @jebus_beler: are you using unity3d or unity2d? I use unity2d and haven't had any similar issue.

I'm using unity 3d and gnome 3.  I think its a GPU thing so if you're not using the GPU you probably won't see it.

I've had two different kinds of X lockups, one very reproducable (just using a particular java app), the other more difficult to reproduce.  I found another bug that seems related:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1007904](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1007904)

I've upgraded to precise-proposed and at leasst the reproducable bugs seems less reproducable but I wanna use it for a day or two to see if these issues have really been resolved.

When I first start using 12.04 it seems great but I invariably run into one of these bugs within a couple of hours and it makes the machine unusable.  i really hope that this update fixes things.

---

### Post by User4519 on 2012-06-24
> **jebus_beler said:**
> But in warm weather the fans go crazy even if nothing is going on.  Has anyone got any hints on what would be some safe settings?  I don't mind the fan noise but I do worry about the fans lifetime.

Well, this isn't very scientific, but I'm just going with personal experience and what I believe is logic here.

Since OS X seems to think it's okay to have the CPU running a 95+ degrees centigrade for indeterminate amounts of time, and Intel seem to agree (with Tmax at 100 degrees), and my newly purchased quad core desktop CPU seems to run fine with being at the same temp, I'm assuming this is safe.

This means that I'm actually happy to be able to turn down the fans in Linux which I'm not allowed to in Mac OS X. So I've set up macfanctld to only really kick in at temps >85 degrees. And only get noisy at >95. And to stop being noisy quickly when temps drop again. Whereas in Mac OS X, the fans will stay on until they manage to get the CPU near 60 degrees, at least. Not sure what the logic is there. 

I'm not that worried about longevity of the processor here. Each and every processor I've ever owned (I'm 35 and been a geek since 11) has outlived its purpose except for one Athlon which I accidentally cracked in two trying to fit a cooler on top of it. Never ever have I managed to kill a processor by heat or overclocking. And I've overclocked every one I've ever been able to overclock — including laptop ones.

So, to me, "safe" means Tmax, i.e. 100 degrees centigrade, and I'm using that to turn down that annoying fan whenever possible.

In all fairness, though, I'm not actually using Kubuntu as my main OS (atm), so I haven't stress-tested it. But I'll still say: go with Tmax, ignore the "don't go over 60" mantra thought up by overclockers (which is very valid with extreme overclocking btw), and just try to get a silent operation at stock speeds. Do keep in mind, though, that these chips automatically downstep on the multiplier to protect themselves when getting really hot (which is good, IYAM).

---

### Post by asting on 2012-06-24
> **DanielBuus said:**
> Well, this isn't very scientific, but I'm just going with personal experience and what I believe is logic here.

Since OS X seems to think it's okay to have the CPU running a 95+ degrees centigrade for indeterminate amounts of time, and Intel seem to agree (with Tmax at 100 degrees), and my newly purchased quad core desktop CPU seems to run fine with being at the same temp, I'm assuming this is safe.

This means that I'm actually happy to be able to turn down the fans in Linux which I'm not allowed to in Mac OS X. So I've set up macfanctld to only really kick in at temps >85 degrees. And only get noisy at >95. And to stop being noisy quickly when temps drop again. Whereas in Mac OS X, the fans will stay on until they manage to get the CPU near 60 degrees, at least. Not sure what the logic is there. 

I'm not that worried about longevity of the processor here. Each and every processor I've ever owned (I'm 35 and been a geek since 11) has outlived its purpose except for one Athlon which I accidentally cracked in two trying to fit a cooler on top of it. Never ever have I managed to kill a processor by heat or overclocking. And I've overclocked every one I've ever been able to overclock — including laptop ones.

So, to me, "safe" means Tmax, i.e. 100 degrees centigrade, and I'm using that to turn down that annoying fan whenever possible.

In all fairness, though, I'm not actually using Kubuntu as my main OS (atm), so I haven't stress-tested it. But I'll still say: go with Tmax, ignore the "don't go over 60" mantra thought up by overclockers (which is very valid with extreme overclocking btw), and just try to get a silent operation at stock speeds. Do keep in mind, though, that these chips automatically downstep on the multiplier to protect themselves when getting really hot (which is good, IYAM).

While i agree with most of what you say, that seems a tad aggressive. A lot of laptops reach high temps, but I'd try to get it a tad cooler. 
Doesn't it get a bit warm to use on your lap also?

---

### Post by berryman77 on 2012-06-29
I may have found a solution to the external monitor problem. Previously, I've had to run Ubuntu 2D because my screen would freeze using the default Unity.  While addressing a video tearing issue, I enabled settings in Compiz which also corrected my external monitor issue.

Using the Compiz Settings Manager (ccsm), under Utility -> Workarounds, I checked both "Don't wait for video sync" and "Force full screen redraws (buffer swap) on repaint".  I'm now able to use compositing (Unity 3D) (in addition to playing h.264 1080p video @ 60fps fullscreen with mplayer-vaapi).  I hope this helps someone else and I'll report any other relevant findings here.  If this fix is confirmed I'll post it to the wiki.

---

### Post by diafygi on 2012-07-04
Howdy all, I'm trying to get 12.04 installed on my MBA 4-2 by following the instructions on the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2"). I had 11.10 installed before, but I removed all of those partitions to start from a clean slate again for 12.04.

The installation went fine, but now refit is showing two linux icons, and each just boot to a black screen with a blinking cursor in the top left. I'm assuming that the problem is with the MBR, so I've tried to repair my MBR by following [dfacto's instructions]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185"). However, even after repairing, the two linux icons are still there and they still only go to the black screen.

Ideas on what I need to repair?

Here's my MBR outputs:
```

Recovery/transformation command (? for help): o

Disk size is 236978176 sectors (113.0 GiB)
MBR disk identifier: 0x00007997
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1         2047   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAF
   4      *           2048         4095   primary     0x83

Recovery/transformation command (? for help): p
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003BCB-6883-0000-5258-000031770000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 409813 sectors (200.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          409640        78534639   37.3 GiB    AF00  Customer
   2        78534640        79804175   619.9 MiB   AF00  Recovery HD
   3        79804176        80213775   200.0 MiB   EF00  EFI System Partition
   4            2048            4095   1024.0 KiB  EF02  
   5        80214016       234469375   73.6 GiB    0700  
   6       234469376       236976127   1.2 GiB     8200  

```

---

### Post by squelchy on 2012-07-05
Hi Guys,

Thanks for everybody's hard work getting ubuntu onto the MBA, was getting very sick of Mac OS!

I'm having trouble install 12.04. I've installed as per the wiki article, but there seems to be some problem with the graphics drivers as the laptop screen is blank, though an external monitor work fine. The laptop screen does work with the "nomodeset" kernel flag, but then only with 1024x768 screen resolution. 

Has anyone else encountered this or have any clues? I've tried using the X-Org Edgers ppa but that hasn't seemed to help. 

I've got the 15" i5 2011 MBA.

Cheers

---

### Post by diafygi on 2012-07-05
Okay, can anyone explain why there is one Mac icon and two Linux icons in my refit menu when I restart my computer? Neither of the two Linux icons boot into anything besides a black screen with a cursor in the top left. What can I do to troubleshoot this?

Here's my MBR:
```
Recovery/transformation command (? for help): o

Disk size is 236978176 sectors (113.0 GiB)
MBR disk identifier: 0x00007997
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAF
   4      *       80214016    233842687   primary     0x83

Recovery/transformation command (? for help): p
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003BCB-6883-0000-5258-000031770000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 411861 sectors (201.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          409640        78534639   37.3 GiB    AF00  Customer
   2        78534640        79804175   619.9 MiB   AF00  Recovery HD
   3        79804176        80213775   200.0 MiB   EF00  EFI System Partition
   4        80214016       233842687   73.3 GiB    0700  
   5       233842688       236976127   1.5 GiB     8200  
```

---

### Post by poliva on 2012-07-05
@diafygi: looks like your hibrid MBR is broken and needs to be rebuild (as per [dfacto instructions]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185"), as you posted). If that's not the problem, make sure you have installed grub in the 4th MBR partition (linux /dev/sda4) and not in the disk (/dev/sda).

---

### Post by diafygi on 2012-07-06
> **poliva said:**
> @diafygi: looks like your hibrid MBR is broken and needs to be rebuild (as per [dfacto instructions]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185"), as you posted). If that's not the problem, make sure you have installed grub in the 4th MBR partition (linux /dev/sda4) and not in the disk (/dev/sda).

Hey poliva, thanks for the reply. I did follow dfacto's instructions, which is why the MBR table lines up with the partition table below. When I try to sync the MBR in the refit menu, it say's it's not touching anything and displays the same tables as below.

How can I see if grub is installed on the /dev/sda4 partition?

Also, I'm still curious as to why there are two Linux icons on the refit menu when I boot? Does it thing that the Recovery partition is a Linux partition?

```
Recovery/transformation command (? for help): o

Disk size is 236978176 sectors (113.0 GiB)
MBR disk identifier: 0x00007997
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAF
   4      *       80214016    233842687   primary     0x83

Recovery/transformation command (? for help): p
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003BCB-6883-0000-5258-000031770000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 411861 sectors (201.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          409640        78534639   37.3 GiB    AF00  Customer
   2        78534640        79804175   619.9 MiB   AF00  Recovery HD
   3        79804176        80213775   200.0 MiB   EF00  EFI System Partition
   4        80214016       233842687   73.3 GiB    0700  
   5       233842688       236976127   1.5 GiB     8200  
```

---

### Post by poliva on 2012-07-06
> **diafygi said:**
> How can I see if grub is installed on the /dev/sda4 partition?

$ sudo strings /dev/sda |head -n 30 |grep -i grub
$ sudo strings /dev/sda4 |head -n 30 |grep -i grub

The place where grub is installed, should output something like "grub/stage... whatever"

> **diafygi said:**
> 
Also, I'm still curious as to why there are two Linux icons on the refit menu when I boot? Does it thing that the Recovery partition is a Linux partition?

no idea, maybe because it sees two ext partitions? but according to the table you pasted it should only see one. If having problems, you can use [refind]("http://www.rodsbooks.com/refind/") instead of refit.

---

### Post by diafygi on 2012-07-06
> **poliva said:**
> $ sudo strings /dev/sda |head -n 30 |grep -i grub
$ sudo strings /dev/sda4 |head -n 30 |grep -i grub


Hey poliva, I booted into the Ubuntu live USB and ran the command for all of the sda* shown: both sda and sda1 returned "GRUB" output. There is also a grub folder in /boot/ for that partition (i.e. /boot/grub/). Does that mean anything to you?

```
$ sudo strings /dev/sda |head -n 30 |grep -i grub
GRUB
$ sudo strings /dev/sda1 |head -n 30 |grep -i grub
$ sudo strings /dev/sda2 |head -n 30 |grep -i grub
$ sudo strings /dev/sda3 |head -n 30 |grep -i grub
$ sudo strings /dev/sda4 |head -n 30 |grep -i grub
GRUB
$ sudo strings /dev/sda5 |head -n 30 |grep -i grub

```

> **poliva said:**
> 
no idea, maybe because it sees two ext partitions? but according to the table you pasted it should only see one. If having problems, you can use [refind]("http://www.rodsbooks.com/refind/") instead of refit.

Ok, I removed rEFIt and installed rEFInd, following the instructions to manually install it using Mac OS X and installing it to the /Volumes/esp/ partition (disk0s3 for me).

Now when I reboot, rEFInd is showing only the Mac icon and no other icons. The MBR is exactly the same as before. What can I do for next steps to troubleshoot this?

```
Recovery/transformation command (? for help): o

Disk size is 236978176 sectors (113.0 GiB)
MBR disk identifier: 0x00007997
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1       409639   primary     0xEE
   2                409640     78534639   primary     0xAF
   3              78534640     79804175   primary     0xAF
   4      *       80214016    233842687   primary     0x83

Recovery/transformation command (? for help): p
Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 00003BCB-6883-0000-5258-000031770000
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 8-sector boundaries
Total free space is 411861 sectors (201.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          409640        78534639   37.3 GiB    AF00  Customer
   2        78534640        79804175   619.9 MiB   AF00  Recovery HD
   3        79804176        80213775   200.0 MiB   EF00  EFI System Partition
   4        80214016       233842687   73.3 GiB    0700  
   5       233842688       236976127   1.5 GiB     8200
```

---

### Post by poliva on 2012-07-06
Looks like you have grub on the drive (no partition), and also on sda4. Try installing a MBR that will chain to grub on partition 4:

$ sudo apt-get install mbr
$ sudo install-mbr -p 4 /dev/sda

---

### Post by diafygi on 2012-07-06
> **poliva said:**
> Looks like you have grub on the drive (no partition), and also on sda4. Try installing a MBR that will chain to grub on partition 4:

$ sudo apt-get install mbr
$ sudo install-mbr -p 4 /dev/sda

Hey poliva, thanks for the commands. I ran those using the Ubuntu live USB, and the "sudo strings /dev/sda |head -n 30 |grep -i grub" no longer shows GRUB. Thanks!

However, I'm still only seeing the Mac icon in my rEFInd menu when I boot up. What would my next steps be to troubleshoot why the linux partition isn't showing up in the rEFInd menu?

---

### Post by audiohobbyist on 2012-07-08
Has anybody been able to get the Thunderbolt to Gigabit Ethernet Adapter to work on Ubuntu 12.04? I have a Macbook Air 4.2.

---

### Post by cargath on 2012-07-13
I'm trying to install Ubuntu 11.10 on my MBA (i need exactly this version, the software i'm going to work on for my diploma thesis doesn't work with a newer version of Ubuntu), but i can't get it to boot from a live USB drive.

I created a bootable USB drive using the app from penguintosh.com. It enables me to select the USB drive as my startup partition when restarting the Mac. With 12.04 everything seems to work fine. With 11.10, after a terminal screen telling me "booting Linux kernel, this may take a while" all i get is a black screen.

The installation guide says "When booting from the USB stick, it is necessary to edit the boot parameters to achieve a usable graphical login: press F6 at the initial menu and add 'nomodeset' before the final '--'. If you're comfortable with the command line, this step isn't necessary - simply press ctrl-alt-F1 to gain a login prompt."

I don't even know what initial menu is meant - the screen goes black before any menu appears.

---

### Post by jonny on 2012-07-17
> **cargath said:**
> I'm trying to install Ubuntu 11.10 on my MBA (i need exactly this version, the software i'm going to work on for my diploma thesis doesn't work with a newer version of Ubuntu), but i can't get it to boot from a live USB drive.

I created a bootable USB drive using the app from penguintosh.com. It enables me to select the USB drive as my startup partition when restarting the Mac. With 12.04 everything seems to work fine. With 11.10, after a terminal screen telling me "booting Linux kernel, this may take a while" all i get is a black screen.

The installation guide says "When booting from the USB stick, it is necessary to edit the boot parameters to achieve a usable graphical login: press F6 at the initial menu and add 'nomodeset' before the final '--'. If you're comfortable with the command line, this step isn't necessary - simply press ctrl-alt-F1 to gain a login prompt."

I don't even know what initial menu is meant - the screen goes black before any menu appears.
If you're seeing "booting Linux Kernel", you've gone too far.  You need to stop things when you first see any sign of life (from memory, I think that a keyboard icon comes first) by pressing any key and then using one of the menu options to edit the boot command.

Alternatively, wait until you see the black screen and your USB stick has stopped flashing, and press ctrl-alt-f1 to log in using the command line.

---

### Post by YannBuntu on 2012-07-20
Hello
Has anyone managed to boot MacOS from GRUB? if yes, how?

---

### Post by mr_manny on 2012-07-21
> **audiohobbyist said:**
> Has anybody been able to get the Thunderbolt to Gigabit Ethernet Adapter to work on Ubuntu 12.04? I have a Macbook Air 4.2.

If you need Ethernet, you might have better results with a USB adapter:

[http://pcfolkcom.wordpress.com/2012/07/04/works-great-on-my-macbook-air-and-linux-workstation/](http://pcfolkcom.wordpress.com/2012/07/04/works-great-on-my-macbook-air-and-linux-workstation/)

---

### Post by thorsten-by on 2012-07-31
Hi, 

I've some problems with OS/X since I've Linux on a secound partition on my mba. I'd like to know if anybody else experienced such problems. 

Linux works fine with partitions and fs but on OS/X I had some problems deleting partitions when I had to reinstall OS/X the last time. Now I wanted to upgrade to 10.8 but the OS/X installer says that It can't boot from "Macintosh HD".  Unfortenately it won't tell me why it can't boot from this drive.

Does anybody know if this could have been caused by the repartitioning for linux? I dont think so because I created all partitions with the OS/X diskutility so that the linux installer only had to format them. But I cant figure out why the installer wont start.

---

### Post by Marvin Stodolsky on 2012-07-31
For my 2011 MacBookAir bought in May 2012, the Mac diskutils was used to shorten the Mac partition.  rEFIt installation was routine.
Then Ubuntu Precise was installed from a USB stick, standard install. As reported by parted, the resultant partitions are:
------
Model: ATA APPLE SSD TS128C (scsi)
Disk /dev/sda: 121GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      20.5kB  210MB   210MB   fat32           EFI system partition  boot
 2      210MB   80.2GB  80.0GB  hfs+            Customer
 3      80.2GB  80.8GB  650MB   hfs+            Recovery HD
 4      80.8GB  80.8GB  1000kB                                        bios_grub
 5      80.8GB  117GB   36.3GB  ext4
 6      117GB   121GB   4201MB  linux-swap(v1)
-----
All devices seem to work OK, including the wireless using the wl.ko driver.  The partition 4 was presumbably created to support the Ubuntu installation and (per below) is not essential.

The recent Mac upgrade from Lion to Mountain Lion was successful,
BUT it is 1st Essential to run EFI partition Inspector/Manager available under the bootup EFI choices, to synchronize GPT and MBR style partition records.

Apple next provided a firmware update. After installation Ubuntu did NOT boot, with an accompanying complaint from EFI about the partition 4. Also EFI would not attempt to synchronize the GPT and MBR style partition records. Using the Precise installation UBS stick to boot, the MAC "disk" Ubuntu installation seemed to be intact.  It could be mounted and files read with cat.

The previously mentioned partition is not present on an older Nacbook. So crossing toes and fingers, gparted was used to delete this partition 4 from the MacBook.  After which:
---------
Model: ATA APPLE SSD TS128C (scsi)
Disk /dev/sda: 121GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      20.5kB  210MB   210MB   fat32           EFI system partition  boot
 2      210MB   80.2GB  80.0GB  hfs+            Customer
 3      80.2GB  80.8GB  650MB   hfs+            Recovery HD
 5      80.8GB  117GB   36.3GB  ext4
 6      117GB   121GB   4201MB  linux-swap(v1)
------

Upon the following bootup managed by EFI, the partition inspector/manager did read and update the partition tables.

The 1st trial to boot Ubuntu was aborted by a poweroff, as it was taking inordicnately long.  But subsequent Mac and Ubuntu boots have been trouble free.

Concerning the original Partition 4, I presume it had been partially overwritten, during the Mac firmware update, including an extension or replacement of the original Recovery partition 3.
Using gparted to examine the Mac "disk", there is now NO free space reported between partitions 3 & 5.

MarvS

PS I have checked to ascertain which drivers can be unloaded,
with the successful efforts summarized in the following script.

#!/bin/sh
sudo modprobe -r joydev
sudo modprobe -r wl
sudo modprobe -r uvcvideo
sudo modprobe -r applesmc
sudo /etc/init.d/networking stop
sudo modprobe -r rfcomm
sudo modprobe -r btusb
sudo modprobe -r bnep
sudo /etc/init.d/pulseaudio stop
sudo modprobe -r snd-hda-intel
sudo modprobe -r parport_pc
sudo modprobe -r ppdev
sudo modprobe -r snd_seq_midi
sudo modprobe -r mei
sudo modprobe -r lp
sudo avahi-daemon --kill
sudo /etc/init.d/cups stop
sudo /etc/init.d/resolvconf stop
modprobe -r michael_mic
modprobe -r arc4
modprobe -r snd_hda_codec_hdmi
modprobe -r snd_hda_codec_cirrus
/etc/init.d/pppd-dns stop
/etc/init.d/resolvconf stop
# end

---

### Post by Dr.Paneas on 2012-08-01
> **cargath said:**
> I'm trying to install Ubuntu 11.10 on my MBA (i need exactly this version, the software i'm going to work on for my diploma thesis doesn't work with a newer version of Ubuntu), but i can't get it to boot from a live USB drive.

I created a bootable USB drive using the app from penguintosh.com. It enables me to select the USB drive as my startup partition when restarting the Mac. With 12.04 everything seems to work fine. With 11.10, after a terminal screen telling me "booting Linux kernel, this may take a while" all i get is a black screen.

The installation guide says "When booting from the USB stick, it is necessary to edit the boot parameters to achieve a usable graphical login: press F6 at the initial menu and add 'nomodeset' before the final '--'. If you're comfortable with the command line, this step isn't necessary - simply press ctrl-alt-F1 to gain a login prompt."

I don't even know what initial menu is meant - the screen goes black before any menu appears.


What if you install 12 and then downgrade to 11 via apt-get ?

---

### Post by Dr.Paneas on 2012-08-01
I followed the [wiki]("https://help.ubuntu.com/community/MacBookAir4-2") and I discovered that the [script]("http://almostsure.com/mba42/setup_mac_usb_boot.sh") provided for USB Flash preparation has lot's of error and its also outdated. So I made some modifications:

[PHP]#!/bin/bash

# Joshua V. Dillon
# jvdillon (a) gmail (.) com
#
# Script to make Mac bootable USB.
#
# Copyright (c) 2011 Joshua V Dillon
# All rights reserved. See end-of-file for license.

# Sun Dec  4 13:23:50 PST 2011 - 01_add-nomodeset-to-usb-iso.patch (poliva)
# Sun Dec  4 13:27:58 PST 2011 - 02_usb-iso-sanity-checks.patch (poliva)

# Modified by Panos Georgiadis at 2/8/2012
# Added Ubuntu 12.04 and fix some bugs in the code

# plug in USB drive and obtain device name:
# dmesg|tail
# unmount it if it was  mounted

 wget http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso
 
# update these:
UBUNTUISO="/home/panos/Downloads/ubuntu-12.04-desktop-amd64+mac.iso"
USBDEV="/dev/sdb"
# NOTE: the USBDEV should not have any numbers in it. Replace 'X' with the
# appropriate LETTER ONLY.

# 0) sanity checks
mount | grep "${USBDEV}" | awk '{print $1}' | xargs -n1 sudo umount 
[ ! -f "${UBUNTUISO}" ] && \
    { echo >&2 "ERROR: Can't find ${UBUNTUISO}";exit 1; }

# 1) format the usb thumb drive
sudo mkfs.vfat "${USBDEV}" -I

# 2) mount the iso
sudo mkdir /media/iso
sudo mount -o loop "${UBUNTUISO}" /media/iso

# 3) mount the usb drive
sudo mkdir /media/external
sudo mount "${USBDEV}" /media/external

# 4) copy the iso contents to usb drive
sudo rsync -avPh --stats /media/iso/ /media/external/

# 5) prep for syslinux
sudo mv /media/external/isolinux /media/external/syslinux
sudo mv /media/external/syslinux/isolinux.cfg /media/external/syslinux/syslinux.cfg

# 6) add nomodeset to grub parameters (needed for 2011 MBA)
sudo sed -i "s/quiet splash/quiet splash nomodeset/g" /media/external/boot/grub/loopback.cfg
sudo sed -i "s/quiet splash/quiet splash nomodeset/g" /media/external/syslinux/txt.cfg

# 7) unmount
sudo umount /media/iso
sudo umount "${USBDEV}"

# 8) make disk bootable
sudo apt-get install syslinux mtools
sudo syslinux "${USBDEV}"

# 9) Remove folders
sudo rm -rf /media/external/
sudo rm -rf /media/iso

#  Redistribution and use in source and binary forms, with or
#  without modification, are permitted provided that the
#  following conditions are met:
#   * Redistributions of source code must retain the above
#     copyright notice, this list of conditions and the
#     following disclaimer.
#   * Redistributions in binary form must reproduce the above
#     copyright notice, this list of conditions and the
#     following disclaimer in the documentation and/or other
#     materials provided with the distribution.
#   * Neither the name of the author nor the names of its
#     contributors may be used to endorse or promote products
#     derived from this software without specific prior written
#     permission.
#  
#  THIS SOFTWARE IS PROVIDED BY JOSHUA V DILLON ''AS IS'' AND
#  ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
#  TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
#  A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL JOSHUA
#  V DILLON BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
#  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT
#  NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
#  LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
#  HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
#  CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
#  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
#  SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
[/PHP]

---

### Post by Dr.Paneas on 2012-08-03
Sorry for posting once again in a row.

Can you help me to make windows move using 3 fingers ? Have anyone managed this ?

---

### Post by ChinaSailor on 2012-08-07
[http://www.technewsworld.com/story/75820.html](http://www.technewsworld.com/story/75820.html)

For those Unity lovers, don't bother reading..... All others, you might enjoy this article...


[LEFT][COLOR=#000000][FONT=verdana]"For me GNOME has been irrelevant since they went from 2.x to 3.x," Pogson said. "I have been using XFCE4 ever since," he noted. "

**I can manage my own desktop, thank you very much.**[/FONT][/COLOR][/LEFT]

---

### Post by berryman77 on 2012-08-13
> **berryman77 said:**
> I may have found a solution to the external monitor problem. Previously, I've had to run Ubuntu 2D because my screen would freeze using the default Unity.  While addressing a video tearing issue, I enabled settings in Compiz which also corrected my external monitor issue.

Turns out I still ran into trouble.  After using Unity 2D, I finally decided to give xubuntu another chance (tried it years ago).  I was impressed and how much it had improved (more polish), while still remaining simple.  I'm using compositing and I've had no graphics issues at all.  I'm still running xorg-edgers because ppa-purge can't revert it, so I don't know if there are any issues with xubuntu and the main drivers/xorg.  While there are some things about Unity I do like, for now I am most satisfied with XFCE4.

---

### Post by zmiq2 on 2012-08-29
Hi All,

after coming from vacations this past Monday, and proceeding with the usual packages update, my 4,1 11' mba had very frequent x-logouts. I never happened that to me before.

I'm using an external monitor, I don't known if that's the cause.

After being impossible to work, I decided to upgrade to ubuntu quantal, 12.10, which is already in beta.

Been a happy camper since!!! 12.10 seems smoother to me, and external monitor, which was a real pain, now works smoothly.

HTH

---

### Post by warpino on 2012-09-12
Dear all,

I'm a happy macbook air 4.2 + ubuntu 12.04 64 bit user since a few months.
There are just three "minor" issues I have not been able to solve yet:

1) bluetooth is not working. I can turn it on from the tray, but when I go into bluetooth settings it is stuck on "off" and can not be switched to "on" in any way

2) I wish I could reproduce Max OS X 10.7 Lion touchpad gestures. Any straight guide about how to achieve that?

3) Each time I turn on, reboot, revert from suspend or even unlock the computer screen the keybord light is back to the maximum. Any way to make it keep the last value?

Thanks for your help!

---

### Post by xHrvoje on 2012-09-27
I recently got a MBA 4,1 and installed 12.04 alongside OS X and my main concern are somewhat higher CPU temperatures. I'm running 3.2.0-29-generic, broadcom-sta WL driver, using Unity-2D, have enabled i915 rc6 powersave and every other power saving technique I could think of (post-install along with few others). My powertop reports 8.79 W at idle and tunables all report "Good". I can't think of anything else to do, my laptop gets significantly hotter after using it for a while than it does on Os X which remains at 2000 rpm fan and 44 degrees CPU at idle (quite comfortable). Please offer any advice, I really want to use Ubuntu on this laptop. Thanks! 


[FONT="Courier New"]
Summary: 244,2 wakeups/second,  0,0 GPU ops/second and 0,0 VFS ops/sec

                Usage       Events/s    Category       Description
             16,0 ms/s      68,7        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background n
              1,4 ms/s      37,3        Timer          tick_sched_timer
              0,8 ms/s      22,5        Timer          hrtimer_wakeup
              3,9 ms/s      21,1        Process        /usr/lib/chromium-browser/chromium-browser
              9,8 ms/s      16,7        Process        gnome-terminal
            145,1 µs/s      18,2        kWork          flush_to_ldisc
              1,7 ms/s      16,0        Process        metacity
              5,2 ms/s      10,6        Process        /usr/lib/chromium-browser/chromium-browser --type=renderer --lang=hr --force-fieldtest=C
              1,4 ms/s       9,4        Interrupt      [6] tasklet(softirq)
            384,3 µs/s       5,9        Interrupt      [11] ata_piix
            183,2 µs/s       3,1        Process        syndaemon -i 2.0 -K -R -t
              1,1 ms/s       1,8        Process        powertop
            467,6 µs/s       2,0        Interrupt      [21] i915
              5,5 ms/s       0,0        Timer          wl_timer
              2,7 ms/s       0,1        Process        /usr/sbin/macfanctld
              2,3 ms/s       0,0        Interrupt      [11] ehci_hcd:usb1
            185,9 µs/s       0,8        Interrupt      [9] acpi
            155,4 µs/s       0,8        Interrupt      [9] RCU(softirq)
             83,5 µs/s       0,8        Process        /usr/sbin/mouseemu
            543,5 µs/s       0,6        kWork          acpi_os_execute_deferred
            184,4 µs/s       0,7        Interrupt      [4] block(softirq)
             13,8 µs/s       0,7        kWork          i915_gem_retire_work_handler
              1,6 ms/s       0,1        Process        /usr/lib/chromium-browser/chromium-browser --type=renderer --lang=hr --force-fieldtest=C
            494,8 µs/s       0,5        Process        unity-2d-shell
              1,4 ms/s       0,0        Interrupt      [11] wlan0
             81,6 µs/s       0,5        Process        update-notifier
            699,3 µs/s       0,2        kWork          kcryptd_crypt
              2,4 µs/s       0,5        kWork          blk_delay_work
            384,6 µs/s       0,3        Process        [ksoftirqd/1]
[/FONT]


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +56.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +55.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   3009 RPM  (min = 3010 RPM)
TB0T:         +36.2°C  
TB1T:         +36.2°C  
TB2T:         +35.2°C  
TC0C:         +53.8°C  
TC0D:         +54.0°C  
TC0E:         +55.0°C  
TC0F:         +57.0°C  
TC0P:         +50.8°C  
TC1C:         +54.0°C  
TC2C:         +54.0°C  
TCGC:         +54.0°C  
TCSA:         +53.0°C  
TH0F:        +249.0°C  
TH0J:        +249.0°C  
TH0O:        +249.0°C  
TH0o:         +28.0°C  
THSP:         +45.8°C  
TM0P:         +50.0°C  
TPCD:         +53.0°C  
Ta0P:         +47.5°C  
Th1H:         +38.0°C  
Tm0P:         +44.8°C  
Tm1P:         +45.8°C  
Ts0P:         +34.8°C

---

### Post by berryman77 on 2012-09-27
The lowest I've gotten the power to under Linux is 7W and I haven't heard of anyone doing better on the Macbook Air.  Under OSX, I can get it down to 4W.

I'm running Cinnamon (with compositing) on Ubuntu and all the latest stuff from xorg-edgers.

Here are my sensor readings for comparison.

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +58.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +59.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   2005 RPM  (min = 2000 RPM)
TB0T:         +34.8°C  
TB1T:         +34.8°C  
TB2T:         +31.5°C  
TC0C:         +57.5°C  
TC0D:         +56.8°C  
TC0E:         +57.8°C  
TC0F:         +59.5°C  
TC0P:         +53.0°C  
TC1C:         +56.0°C  
TC2C:         +56.0°C  
TCGC:         +56.0°C  
TCSA:         +56.0°C  
TH0F:        +249.0°C  
TH0J:        +250.0°C  
TH0O:        +250.0°C  
TH0o:         +24.0°C  
THSP:         +47.8°C  
TM0P:         +54.0°C  
TPCD:         +69.0°C  
Ta0P:         +57.8°C  
Th1H:         +38.0°C  
Tm0P:         +48.8°C  
Tm1P:         +55.5°C  
Ts0P:         +32.2°C

I have no idea what's drawing the extra power.  I've tried shutting down the radios (wifi and bluetooth) and unloading as many modules as possible.

I think the ZenBook can get under 5W, but it has its own issues:

[https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook)

Please post if you make any progress in this area.  I get the impression that most people here are content with the higher power draw and heat or don't know that the hardware is capable of better power conservation.  I'm willing to try new ideas.

---

### Post by pindar on 2012-10-22
> **berryman77 said:**
> 
Here are my sensor readings for comparison.

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +58.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +59.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

I have no idea what's drawing the extra power.  I've tried shutting down the radios (wifi and bluetooth) and unloading as many modules as possible.

Please post if you make any progress in this area.  I get the impression that most people here are content with the higher power draw and heat or don't know that the hardware is capable of better power conservation.  I'm willing to try new ideas.

I was going to post that Ubuntu 12.10 handles the MBA better, but after one hour of light use, I get temperatures in the 90&#730;C range. I had hoped that the kernel 3.5 would make progress in this area, but alas... I'm not willing to risk frying my MBA, so I guess I will delete the linux partition.

---

### Post by jonkue on 2012-11-14
I installed Debian  wheezy and Ubuntu 12.10 on my Macbookair 4,2.
On both systems I had temperature problems until I installed under Debian the kernel 3.5.5 from the experimental Repisitories (they removed it some days later from the repistory). In Ubuntu I tested 3.5.5, 3.6.0 and 3.6.3 and some days ago there was a update from 3.5.0.17 to 3.5.0.18.

With the standard kernel 3.5.0.17 I had some crashs. Nothing really chrashed, but I got a popup message. I thried the other kernels but didn't use them because of no wlan support.

Now I got an external USB-Wlanstick. So, I tested the Kernel 3.6.3 and the temperature is ok (watch a flash video 10 minutes ago):

> coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +64.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +61.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +65.0°C  (high = +86.0°C, crit = +100.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   2012 RPM  (min = 2000 RPM)
TB0T:         +36.5°C  
TB1T:         +36.5°C  
TB2T:         +33.8°C  
TC0C:         +63.2°C  
TC0D:         +61.0°C  
TC0E:         +65.5°C  
TC0F:         +66.5°C  
TC0P:         +56.5°C  
TC1C:         +64.0°C  
TC2C:         +64.0°C  
TCGC:         +63.0°C  
TCSA:         +54.0°C  
TH0F:          -5.5°C  
TH0J:          -6.0°C  
TH0O:          -6.0°C  
THSP:         +42.5°C  
TM0P:         +54.2°C  
TPCD:         +60.0°C  
Ta0P:         +51.0°C  
Th1H:         +38.2°C  
Tm0P:         +44.2°C  
Tm1P:         +51.2°C  
Ts0P:         +32.8°C  
Ts0S:         +40.0°C  

This is the good news. But the bad is, that I don't get the internal wlan to work. In debian with kernel 3.5.5 it works. 

Tried to reinstall the module (ignore the german words:) ) :
> 
sudo apt-get install --reinstall bcmwl-kernel-source
....
Vorbereitung zum Ersetzen von bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (durch .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Ersatz für bcmwl-kernel-source wird entpackt ...
bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) wird eingerichtet ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.6.3-030603-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.6.3-030603-generic
Anybody with simular problem or with a hint?

---

### Post by jonkue on 2012-11-14
wifi now works. Had to install the packages:

[LIST]
[*]linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb
[*]linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb
[/LIST]
and reinstall:

[LIST]
[*]bcmwl-kernel-source
[/LIST]

---

### Post by pindar on 2012-11-15
> **jonkue said:**
> wifi now works. Had to install the packages:

[LIST]
[*]linux-headers-3.6.3-030603-generic_3.6.3-030603.201210211349_amd64.deb
[*]linux-headers-3.6.3-030603_3.6.3-030603.201210211349_all.deb
[/LIST]
and reinstall:

[LIST]
[*]bcmwl-kernel-source
[/LIST]

This sounds promising. Did you get the kernel and these debs from the kernel-mainline ppa?

---

### Post by jonkue on 2012-11-15
Yes, got them from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)

downloaded them and installed with "open with" Softwarecenter. First installed the ...all.deb package, because the ...amd64.deb depends on the ...all.deb. 

Maybe you can add the ppa to the apt. In the german documentation [http://wiki.ubuntuusers.de/Mainline-Kernel](http://wiki.ubuntuusers.de/Mainline-Kernel) , it is stated that you have to download the packages manually.

---

### Post by pindar on 2012-11-17
> **jonkue said:**
> 
Maybe you can add the ppa to the apt. In the german documentation [http://wiki.ubuntuusers.de/Mainline-Kernel](http://wiki.ubuntuusers.de/Mainline-Kernel) , it is stated that you have to download the packages manually.

Thank you. Looks like the ppa is structured in a way that it cannot directly be added, but downloading manually and installing via dpkg worked, and first tests were good: max temperature around 91 degrees, but goes quickly down as soon as there's less load on the cpu. I'll have to look into it more thoroughly.

---

