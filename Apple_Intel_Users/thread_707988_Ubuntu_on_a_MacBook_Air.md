---
title: "Ubuntu on a MacBook Air"
date: 2008-02-25
forum: Apple Intel Users
---

### Post by m4cks on 2008-02-25
I'm surprised this thread does not exist yet.

In any case, I just went and checked out the hardware of an Air at the store - it seems mostly the same as the MacBook (Intel X3100 video, screen, etc), so I'm assuming most stuff from [this tutorial]("https://help.ubuntu.com/community/MacBook") will ring true.

I use Ubuntu exclusively at home and at work, and I'm looking for a small form factor (yet large-ish screen) laptop to run it on. Apple quite simply has the sexiest stuff out there at the moment. My main uses of the machine will be web/mail/writing - so the lesser CPU does not bother me.  Unfortunately some people see this as an attack on OS X - it's not - I simply use Ubuntu and I like Apple hardware.

So there are a few obvious differences about the Air which need to be addressed.

1.) No (local) CD booting. I understand it can boot over the Wireless - but through standard systems (like PXE)? Is there any way to install Ubuntu without attaching (buying) an apple usb dvdrom?

2.) Multi-touch pad - will this require tweaks to the drivers in linux for it to even work? I can't find any answers to this yet. I'm sure the drivers haven't taken advantage of 2 and 3 touch - but I question if they will still even work at all.

All the rest: intel video, iSight, bus seem to be inline with the MacBook - but I may have missed some other differences.

I guess the best thing would be to ask someone who has tried it - but I haven't even found that yet.

Thank you.

edit: [this ]("http://www.flickr.com/photos/isriya/2265405622/")and [this ]("http://www.flickr.com/photos/isriya/2264613881/in/photostream/")seem to indicate some level of success but this guy hasn't posted any details.

---

### Post by cyberdork33 on 2008-02-25
Nobody has really even tried this yet, so you are pretty much in the dark. The mactel-linux mailing list might be a good place to start.

---

### Post by m4cks on 2008-02-25
It's been out for over a month now! C'mon guys! :)

I'll ping the mailing list and see what happens.

---

### Post by cyberdork33 on 2008-02-26
> **m4cks said:**
> I'll ping the mailing list and see what happens.That is not very long. We are still having issues with the Santa Rosa Macbooks. The other issue is the limited appeal of the Macbook Air. Well, yes the appeal is great, but I don't think as many people are purchasing it... not yet anyway. Add to that the limited number of Air purchasers that have attempted to install Linux, and you have one person with photos on flickr :)
[http://www.flickr.com/photos/isriya/2265405622/in/photostream/](http://www.flickr.com/photos/isriya/2265405622/in/photostream/)

---

### Post by tgalati4 on 2008-02-26
For the sales tax on an Macbook Air, you can buy an eeePC.  It comes with Linux already installed.

---

### Post by sublime on 2008-02-26
> **tgalati4 said:**
> For the sales tax on an Macbook Air, you can buy an eeePC.  It comes with Linux already installed.

Yeah but you don't get to be as hip and trendy at Starbucks with an eeePC.

---

### Post by GuillaumeR on 2008-02-27
I've just baught a macbook air.
I've tried to install Ubuntu on it, basic functions works well but for the moment there's some issues:
WIFI doesn"t work, even with ndiswrapper
Touchpad gesture is not very good (i don't try to improve it yet)
Keyboard mapping is not perfect
sound doesn't work (i don't try to make it works)

But ISight works!!!!

For those who say that macbook air is a stupid thing, just baught a brain, i'm waiting for a notebook like this one for years, not because i want to show it but i need a lightweight portable and i need to work properly with it. The EEEPC is absolutely not a real notebook because 7'' is not enough to work, even just for internet browsing it sucks. Previously i've baught an Sony 12'' and obviously, macbook air is one hundred times better than Sony one...

---

### Post by kool_kat_os on 2008-02-27
> **sublime said:**
> Yeah but you don't get to be as hip and trendy at Starbucks with an eeePC.

i think its ugly....but thats just one persons opinion...

---

### Post by markpeak on 2008-02-28
Hi, I'm the one that post that picture on Flickr. I installed it via superdrive. Follow the guide from Ubuntu Wiki on MacBook and MacBook Santa Rosa.

I can confirm GuillaumeR comment that Wi-Fi doesn't work, even I use Ndiswrapper and the driver from Leopard (Air) DVD. When I add the Ndiswrapper to modprobe and reboot again, the kernel just die.

I also buy a cheap USB-to-Ethernet to use with MBA but no luck. Ubuntu recognise it but can not get IP from my router DHCP. Don't know why. Mac OS X doesn't recognise it at all. Should be an Apple's trick to force us to buy its USB converter.

---

### Post by cyberdork33 on 2008-02-28
I guess it is lack of windows driver then. Great :(

Can you post the verbose lspci for the Wi-Fi card?

Also, there are USB Wi-Fi dongls that work with Ubuntu, you might look into that for the time being.

---

### Post by GuillaumeR on 2008-02-28
He he, WIFI works now.... sound too!!! :)
suspend to ram works and 3D acceleration too, then compiz can run just out of the box!!!!!!! really impressive!

I still have an issue with microphone and keyboard backlight but i don't try to make it work yet.
For touchpad i've seen some interesting topic to improve gesture, I'm going to try.

---

### Post by cyberdork33 on 2008-02-28
> **GuillaumeR said:**
> He he, WIFI works now.... sound too!!! :)
suspend to ram works and 3D acceleration too, then compiz can run just out of the box!!!!!!! really impressive!

I still have an issue with microphone and keyboard backlight but i don't try to make it work yet.
For touchpad i've seen some interesting topic to improve gesture, I'm going to try.
Would you mind sharing how you get things to work?

---

### Post by GuillaumeR on 2008-02-28
quite easy (for 8.04, don't know for 7.10)
For WIFI you just have to use ndiswrapper and windows drivers on OSX macbook air CD. (go to broadcom and WindowsXPinstallation)
Verify that you remove ndiswrapper module and previously installed drivers (if you have already tried before).
Don't forget to add ndiswrapper to /etc/modules if you want to load it on startup.
for sound you just have to add the line
options snd_hda_intel model=mbp3
to your /etc/modprobe.d/options

Good luck!

---

### Post by Macchi on 2008-03-01
I am running Ubuntu 7.10 through VirtualBox on my MacBook Air. This gives me a good pragmatic trade-off between best of all worlds. If there is any interest I could post some comments on how to get it up and running.

PS: I would love to run pure Linux on this lovely hardware platform, the MacBook Air. I really support Linux and try hard to disseminate it in professional environments.  But at some point reality takes over and my practical solution so far is to run it on virtual machines for this platform. When things get stable enough I might attempt to run Linux natively on my MacBook Air.

---

### Post by fairyliquidizer on 2008-03-01
> **kool_kat_os said:**
> i think its ugly....but thats just one persons opinion...

The EEE PC is sooo cool up close.  Pictures don't capture it's magic.

---

### Post by pveith on 2008-03-02
The eeePC is just a poor reaction to the innovative device OLPC ([www.laptop.org](www.laptop.org)). It really hurts the project. Feel free to read on the OLPC project and rethink you attitude towards the eeePC.

---

### Post by HenningS on 2008-03-02
> **tgalati4 said:**
> For the sales tax on an Macbook Air, you can buy an eeePC.  It comes with Linux already installed.Yeah, but the MacBook Air comes with OS X installed, which makes it worth every little cent. Not for the OP, but for everyone else.

---

### Post by LuisAugusto on 2008-03-02
Are you really comparing the eeePC with the MacBook Air? 

That´s a joke, they´re completely different products! The eeePC is a crap hardware wise, but it´s a small, and cheap crap. The MacBook Air has decent hardware, but it´s a small and expensive device.

It´s like comparing an Atos car with a Smart, come on guys.

---

### Post by cyberdork33 on 2008-03-02
Alright getting a bit OT here... This is not a chat thread, this is a support forum... for Macs, so forget about the eeePC

---

### Post by markpeak on 2008-03-03
Now I'm success with the Wi-Fi on MacBook Air. Use GuillaumeR's method (ndiswrapper and broadcom driver from Leopard DVD1).

Now updating to Hardy Alpha 5

---

### Post by markpeak on 2008-03-06
I start writing the instruction on Ubuntu Wiki. Please Join!!!

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

---

### Post by cyberdork33 on 2008-03-06
I noticed that you say the iSight works out-of-the-box. Is this to say that you do not have to load firmware like most other iSights? Can you post your lspci?

---

### Post by cassowary on 2008-03-10
> **GuillaumeR said:**
> For touchpad i've seen some interesting topic to improve gesture, I'm going to try.

Did you get the touchpad working? Where did you see the interesting topic? Thanks!

---

### Post by markpeak on 2008-03-10
Here is my lspci

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)

---

### Post by jeff1985 on 2008-03-13
I have the same problem with my Macbook Air an Windows Divers from the Leopard DVD.
the network manager doesnt see any network card, but the controller is present in lspci tike in the post above.
Does anyone have a solution?

---

### Post by cyberdork33 on 2008-03-13
> **jeff1985 said:**
> I have the same problem with my Macbook Air an Windows Divers from the Leopard DVD.
the network manager doesnt see any network card, but the controller is present in lspci tike in the post above.
Does anyone have a solution?it being in lspci doesn't mean anything as far as functionality. Are you following a guide for ndiswrapper somewhere? what steps did you take?

---

### Post by sublime on 2008-03-13
> **jeff1985 said:**
> I have the same problem with my Macbook Air an Windows Divers from the Leopard DVD.
the network manager doesnt see any network card, but the controller is present in lspci tike in the post above.
Does anyone have a solution?

Look up getting wifi working on the santa rosa macbook.  They use the same card.  You need to install ndiswrapper and use the windows xp driver to get it working.

---

### Post by jeff1985 on 2008-03-13
I've just found a solution.

It seems that the wifi card of the macbook air has some problems with the actiual hardy release.
it is documented here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558)

the solution, that worked for me:
add to /etc/modprobe.d/ndiswrapper the following line. don't forget, that you need root-permissions to edit this file, so you could do this to edit:
```
sudo gedit /etc/modprobe.d/ndiswrapper
```
add following:
```
install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd
```

---

### Post by jeff1985 on 2008-03-13
> **sublime said:**
> Look up getting wifi working on the santa rosa macbook.  They use the same card.  You need to install ndiswrapper and use the windows xp driver to get it working.

please read properly! i did use the ndiswrapper and winxp driver! 

(see my upper post) the problem was a bug in ndiswrapper

---

### Post by jeff1985 on 2008-03-13
does anyone have a sulution for the touchpad?

and what's about backlight of the keyboard and brightness of the screen?
a can't set the brightness with the panel plugin...

---

### Post by cyberdork33 on 2008-03-13
you need pommed 1.16

Getting gestures / mutitouch working is going to take a lot of development in underlying drivers so I wouldn't expect that anytime soon.

---

### Post by Joshua Swink on 2008-04-22
Help! I can't boot into Ubuntu. I followed the instructions here:

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

Installation seemed to go very well. Then I rebooted and held down Alt. But the only boot option available is "Macintosh HD" which starts OS X.

Step 10 says:

10. (...refit deleted...) If not, hold 'Alt' button for a while and select the Windows partition for Ubuntu.

But no "windows" partition shows up.

On second thought, perhaps it's because I created a swap partition in addition to the ext3 partition for Ubuntu. And now Boot Camp Assistant won't touch the disk anymore. It may be that creating a swap partition is a serious mistake.

---

### Post by cyberdork33 on 2008-04-22
> **Joshua Swink said:**
> Help! I can't boot into Ubuntu. I followed the instructions here:

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

Installation seemed to go very well. Then I rebooted and held down Alt. But the only boot option available is "Macintosh HD" which starts OS X.

Step 10 says:

10. (...refit deleted...) If not, hold 'Alt' button for a while and select the Windows partition for Ubuntu.

But no "windows" partition shows up.

On second thought, perhaps it's because I created a swap partition in addition to the ext3 partition for Ubuntu. And now Boot Camp Assistant won't touch the disk anymore. It may be that creating a swap partition is a serious mistake.
no that doesn't matter. 

Did you install Hardy? boot into OSX and install refit. then reboot and in the refit menu choose the partition tool to sync partitions.

---

### Post by tannewt on 2008-04-23
Touchd probably works on the Air.  I just released Alpha 2.  It supports two finger scrolling, right click, left click and middle click. Check it out at sf.net/projects/touchd.

---

### Post by andreimatei on 2008-04-23
Hello guys,

I'm thinking about buying a Macbook Air, and of course I'll want Ubuntu on it. I see that the wireless will work, but I'm confused about the touchpad and the keyboard backlight... Will I at least be able to simulate a "right-click", forget the fancy stuff? And what's the situation exactly with the keyboard backlight? I understand that I won't be able to adjust the brightness of the screen... Will it use the highest brightness?

Thanks

---

### Post by Joshua Swink on 2008-04-23
> **cyberdork33 said:**
> no that doesn't matter. 

Did you install Hardy? boot into OSX and install refit. then reboot and in the refit menu choose the partition tool to sync partitions.

Thanks for this information. Without it, I don't see how Ubuntu ever would have booted on this system.

Before I installed refit, holding down "Alt" during booting didn't cause Ubuntu to be shown as a boot option.

After installing refit, Linux was available as an option, but choosing it only got the error message "No bootable device -- insert boot disk and press any key".

It was only after installing refit and performing the partition sync that Ubuntu could be booted.

So has anyone gotten Ubuntu to boot on a Macbook Air without refit? The wiki page currently suggests that it's possible - it should clarify how that might happen, or be updated to state that refit is required.

Also, refit is definitely in the hacker stage. It deserves its own section just as much as "wireless setup", "keypad" or the other subjects on the wiki page. I had to go to /efi/refit in the terminal and run enable-always.sh to get it to do anything. Any step that requires a terminal session deserves a detailed walkthrough in my opinion.

---

### Post by cyberdork33 on 2008-04-23
> **Joshua Swink said:**
> It was only after installing refit and performing the partition sync that Ubuntu could be booted.

So has anyone gotten Ubuntu to boot on a Macbook Air without refit? The wiki page currently suggests that it's possible - it should clarify how that might happen, or be updated to state that refit is required. It shouldn't be required. There is a bug in the new installer that seems to have effected a few people. The installer should sync the partitions itself.

> **Joshua Swink said:**
> I had to go to /efi/refit in the terminal and run enable-always.sh to get it to do anything. Any step that requires a terminal session deserves a detailed walkthrough in my opinion.It is a bug that they know about. It will get fixed eventually. They don't make releases very often.

---

### Post by water on 2008-04-29
So has anyone got this working? I've installes 8.04 but can't get passed that...

When I try without rEFit I don't get the "windows" choice after booting holding the option key. 

When I try using rEFit I get a Linux choice, but it never boot and simply hangs on the first screen with the penguin logo in the middle of the screen.


Any suggestions?

---

### Post by cyberdork33 on 2008-04-29
> **water said:**
> So has anyone got this working? I've installes 8.04 but can't get passed that...

When I try without rEFit I don't get the "windows" choice after booting holding the option key. 

When I try using rEFit I get a Linux choice, but it never boot and simply hangs on the first screen with the penguin logo in the middle of the screen.


Any suggestions?

did you sync the partition tables in refit?

also, please post in the new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by m4cks on 2008-05-14
There are new linux apple multi-touch drivers here:

[http://tannewt.org/touch/]("http://tannewt.org/touch/")

Also, refer to this guide for fedora on fixing the touchpad w/o tannewt's multitouch:

[http://www.mactel-linux.org/wiki/Fedora9OnMacBookSantaRosa]("http://www.mactel-linux.org/wiki/Fedora9OnMacBookSantaRosa")

---

### Post by donpaco69 on 2008-05-19
Ok, i've got a nice macbook air now :)

out of the box without firmware i've got isight working, nice !

but i've some other things not working:

- FN key, even with pommed 1.16 and pommed 1.17 from debian, fn key seems not to work, but brightness adjust itself when i disconnect or reconnect the adapter, so it's seems not everything is wrong, as i have no FN key, i couldn't also try the keyboard lighting?

-sound: ok with modprobe option set to mbp3

- bluetooth: impossible to sync my mouse i was using on my macbook from this january, maybe a bug on an update on hardy, as it seems the name of teh adatper disapear after 1 seocn on kbluetooth, so i cannot tell legitimately it's not working.

- wireless ok with tutorial

-touchpad: touchd needs uinput (what's that???? i don't have it)
so classical xorg.conf and fedora's one have same result: basic touchpad with just 1clic button only on the button and not on touchpad, also no scrolling possibility.

- i've tried to set right click on the eject button with xmodmap, but no effect, even if xev says: Pointer_button3 :s

so the most important thing for me: 


FN KEY !! help meeeee!!


PS: has anyone tried the USB->ethernet devide from apple on ubtuntu?

---

### Post by cyberdork33 on 2008-05-19
Please post in the new Apple Support Forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by _alex_ on 2008-05-19
To get the fn key to work on your Macbook Air, see this post:
[http://ubuntuforums.org/showthread.php?p=4984452](http://ubuntuforums.org/showthread.php?p=4984452)

---

### Post by tannewt on 2008-05-19
touchd needs uinput which is a kernel module.  modprobe uinput should do the trick.

---

### Post by kosumi68 on 2008-05-31
> **donpaco69 said:**
> Ok, i've got a nice macbook air now :)

out of the box without firmware i've got isight working, nice !

but i've some other things not working:

- FN key, even with pommed 1.16 and pommed 1.17 from debian, fn key seems not to work, but brightness adjust itself when i disconnect or reconnect the adapter, so it's seems not everything is wrong, as i have no FN key, i couldn't also try the keyboard lighting?

-sound: ok with modprobe option set to mbp3

- bluetooth: impossible to sync my mouse i was using on my macbook from this january, maybe a bug on an update on hardy, as it seems the name of teh adatper disapear after 1 seocn on kbluetooth, so i cannot tell legitimately it's not working.

- wireless ok with tutorial

-touchpad: touchd needs uinput (what's that???? i don't have it)
so classical xorg.conf and fedora's one have same result: basic touchpad with just 1clic button only on the button and not on touchpad, also no scrolling possibility.

- i've tried to set right click on the eject button with xmodmap, but no effect, even if xev says: Pointer_button3 :s

so the most important thing for me: 


FN KEY !! help meeeee!!


PS: has anyone tried the USB->ethernet devide from apple on ubtuntu?
The USB->ethernet device works with the patch listed here: [https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air).

I on the other hand am having problems getting the front microphone working, it seems others have reported something similar. When running on the stock 2.6.24-17-generic kernel, i get sound via the snd_hda_module, but for the microphone, no dice. The sound preferences list ALC882 as a module, does anybody know if this is correct? I have no idea how the sound setup works.

---

### Post by kosumi68 on 2008-06-16
I got the keyboard backlight working on my MBA. Two kernel drivers need patching: hid/hid-input.c and hwmon/applesmc.c. It is assumed below that you know how to compile a kernel and install new modules.

hid/hid-input.c: Map the F5 and F6 keys to KEY_KBDILLUMDOWN and KEY_KBDILLUMUP respectively. This is what my translation table looks like:

> 
static struct hidinput_key_translation apple_fn_keys[] = {
        { KEY_BACKSPACE, KEY_DELETE },
        { KEY_F1,       KEY_BRIGHTNESSDOWN,     APPLE_FLAG_FKEY },
        { KEY_F2,       KEY_BRIGHTNESSUP,       APPLE_FLAG_FKEY },
        { KEY_F3,       KEY_CYCLEWINDOWS,       APPLE_FLAG_FKEY }, /* Exposé */
        { KEY_F4,       KEY_FN_F4,              APPLE_FLAG_FKEY }, /* Dashboard */
        { KEY_F5,       KEY_KBDILLUMDOWN,       APPLE_FLAG_FKEY },
        { KEY_F6,       KEY_KBDILLUMUP,         APPLE_FLAG_FKEY },
        { KEY_F7,       KEY_PREVIOUSSONG,       APPLE_FLAG_FKEY },
        { KEY_F8,       KEY_PLAYPAUSE,          APPLE_FLAG_FKEY },
        { KEY_F9,       KEY_NEXTSONG,           APPLE_FLAG_FKEY },
        { KEY_F10,      KEY_MUTE,               APPLE_FLAG_FKEY },
        { KEY_F11,      KEY_VOLUMEDOWN,         APPLE_FLAG_FKEY },
        { KEY_F12,      KEY_VOLUMEUP,           APPLE_FLAG_FKEY },
        { KEY_UP,       KEY_PAGEUP },
        { KEY_DOWN,     KEY_PAGEDOWN },
        { KEY_LEFT,     KEY_HOME },
        { KEY_RIGHT,    KEY_END },
        { }
};


hwmon/applesmc.c: The latest version wrongly interpets the DMI string as a MacBook, which does not have backlights. Add the MacBookAir to the applesmc_whitelist, preferably at the first position (if below MacBook it will not be recognized). Ideally, the correct set of sensors should be defined for the MBA, but for now, my definitions look like this:

> 
static __initdata struct dmi_system_id applesmc_whitelist[] = {
        { applesmc_dmi_match, "Apple MacBook Air", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"MacBookAir") },
                (void*)&applesmc_dmi_data[0]},
        { applesmc_dmi_match, "Apple MacBook Pro", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"MacBookPro") },
                (void*)&applesmc_dmi_data[0]},
        { applesmc_dmi_match, "Apple MacBook", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"MacBook2") },
                (void*)&applesmc_dmi_data[1]},
        { applesmc_dmi_match, "Apple MacBook", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"MacBook") },
                (void*)&applesmc_dmi_data[2]},
        { applesmc_dmi_match, "Apple Macmini", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"Macmini") },
                (void*)&applesmc_dmi_data[3]},
        { applesmc_dmi_match, "Apple MacPro2", {
          DMI_MATCH(DMI_BOARD_VENDOR,"Apple"),
          DMI_MATCH(DMI_PRODUCT_NAME,"MacPro2") },
                (void*)&applesmc_dmi_data[4]},
        { .ident = NULL }
};


After the new modules are in place and the machine is rebooted, applesmc will recognize the MBA as having keyboard backlights, HID will output the correct keys for  those, and pommed will lower and raise the keyboard backlight when the function keys are pressed.

---

### Post by involutaryhaxor on 2008-06-17
> **tgalati4 said:**
> For the sales tax on an Macbook Air, you can buy an eeePC.  It comes with Linux already installed.

I have an eee pc. I went to an apple store and sat it next to a MacBook Air.

1) My laptop is smaller
2) My laptop runs any OS that I want it to (I've heard reports of OS X)
3) It comes with Linux on it as you mentioned.
4) It's lighter than the MacBook Air. My eee pc weighs less than a kg where the MacBook Air weighs 1.36.

It's also a 6th of the cost and that's being fair with using the cheapest MacBook :)

Unfortunately, it seems to be equally difficult to install Ubuntu on my eee pc. I'm looking to download eeebuntu but the website seems to be down.

---

### Post by chenqinbo5 on 2008-06-22
do drop by to [www.shop-foco.com](www.shop-foco.com) <http://www.shop-foco.com>  look through the articles there. With information on anything from getting the  cheapest shoes, you'll find something that helps you save a lot of money.
-- 
the cheapeast shoes
[www.shop-foco.com](www.shop-foco.com)
<msn:shop-foco@hotmail.com>
E-mail:shopfoco@gmail.com
Thank you for your E-mail and your order

---

### Post by mass_ga on 2008-06-24
Hi everybody. I'm in trouble 'cause I've tried to install Ubunut 8.04 on my MBA but wireless doesn't want to work even if I've followed tutorial.

@edit
Wireless works fine now without passkey.

---

### Post by kosumi68 on 2008-06-27
There is now a kernel driver for the multitouch trackpad: [http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)

---

### Post by kauelinden on 2008-06-30
Hi,

I am from Brazil and i got a macbook air.. its seems running nice but I cant type "dead keys" I am in trouble cause i really need type words like:

não, atenção, é 

But when i try to type "dead keys" it comes like n~ao, aten'c~ao, 'e... so there is any advice to me?

Thanks

---

### Post by kosumi68 on 2008-06-30
Hello kauelinden, could you provide the output of the lsusb command? You might also want to try searching the active threads or post a new thread; this is an archive thread, and thus not as frequented anymore.

---

### Post by gurth4ng on 2008-07-22
any luck with booting the ubuntu installer on a Macbook Air without the external cd drive?

Via some short of network install, either using WiFi or the ethernet usb thingy..

---

### Post by cyberdork33 on 2008-07-23
> **gurth4ng said:**
> any luck with booting the ubuntu installer on a Macbook Air without the external cd drive?

Via some short of network install, either using WiFi or the ethernet usb thingy..
Please bring your discussion to the new Apple Users forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

This forum is an archive.

---

