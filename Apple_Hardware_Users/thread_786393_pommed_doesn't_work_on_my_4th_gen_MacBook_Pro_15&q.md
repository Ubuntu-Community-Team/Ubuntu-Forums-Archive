---
title: "pommed doesn't work on my 4th gen MacBook Pro 15&quot;"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by gorillayue on 2008-05-08
Hey guys,
I know this has been the problem that is discussed over and over again, but I just want to confirm that if any one out there using MacBook Pro 4th iteration ( released on Feb 2008 ) could get pommed working on the new release Ubuntu 8.04 LST Hardy cuz apparently mine (pommed 1.15) doesn't do anything.

---

### Post by emmeelle on 2008-05-08
I have e macbook pro (last generation) and ubuntu 8.04:
pommed doesn't work!!!

So I cannot use special keys (sound, brightness, etc).

I hope this problem will be solved as soon as possible!!!

---

### Post by cyberdork33 on 2008-05-08
use a newer version of pommed. It is available in the mactel-support PPA.

[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

---

### Post by gorillayue on 2008-05-08
Hi Cyberdork, I've tried pommed 1.16, here is what i got when trying to build it:

```
$ tar -zxvf pommed_1.16~mactel1.tar.gz 
.
.
. (output from tar not shown) 
$ cd pommed-1.16~mactel1/
$ make
make -C pommed OFLIB=
Package dbus-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `dbus-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dbus-1' found
make[1]: Entering directory `/home/mike/pommed-1.16~mactel1/pommed'
gcc -g -O2 -Wall  -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/alsa          -c -o pommed.o pommed.c
pommed.c:39:32: error: smbios/SystemInfo.h: No such file or directory
pommed.c: In function ‘check_machine_smbios’:
pommed.c:559: warning: implicit declaration of function ‘SMBIOSGetVendorName’
pommed.c:559: warning: assignment makes pointer from integer without a cast
pommed.c:573: warning: implicit declaration of function ‘SMBIOSFreeMemory’
pommed.c:579: warning: implicit declaration of function ‘SMBIOSGetSystemName’
pommed.c:579: warning: assignment makes pointer from integer without a cast
make[1]: *** [pommed.o] Error 1
make[1]: Leaving directory `/home/mike/pommed-1.16~mactel1/pommed'
make: *** [pommed] Error 2
$

```

---

### Post by cyberdork33 on 2008-05-08
you have missing dependencies. you do not need t build it anyway. binaries are in the mactel-support ppa. you can add the repo or just go to launchpad and download it.

---

### Post by gorillayue on 2008-05-08
Under System > Preference > Keyboard > Layouts, if I choose Keyboard Model as 'MacBook/MacBook Pro (Intl), I got the error message window pops up:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


Does it have anything to do with pommed ?

---

### Post by gorillayue on 2008-05-08
> **cyberdork33 said:**
> you have missing dependencies. you do not need t build it anyway. binaries are in the mactel-support ppa. you can add the repo or just go to launchpad and download it.

sorry man, could you explain it in a little more detail please?
I'm pretty ignorant about how this works. Also, it seems 1.16 hasn't been officially released yet. sudo apt-get install pommed can only get me 1.15 version of it

---

### Post by cyberdork33 on 2008-05-08
> **gorillayue said:**
> sorry man, could you explain it in a little more detail please?
I'm pretty ignorant about how this works. Also, it seems 1.16 hasn't been officially released yet. I couldn't find pommed 1.16 in launchpad. Only 1.15 is there.
I was talking about the mactel-support ppa page in launchpad which I already linked to.
[https://edge.launchpad.net/~mactel-support/+archive]("https://edge.launchpad.net/%7Emactel-support/+archive")

you should see pommed 1.16 listed as in the ppa. Click the little triangle to expand the details and you can see several different package files.

Actually pommed 1.17 is out now I think.
[http://alioth.debian.org/projects/pommed/](http://alioth.debian.org/projects/pommed/)

debian binaries are here:
[http://packages.debian.org/lenny/i386/pommed/download](http://packages.debian.org/lenny/i386/pommed/download)
[http://packages.debian.org/sid/amd64/pommed/download]("http://packages.debian.org/lenny/i386/pommed/download")

---

### Post by gorillayue on 2008-05-08
> **cyberdork33 said:**
> I was talking about the mactel-support ppa page in launchpad which I already linked to.
[https://edge.launchpad.net/~mactel-support/+archive]("https://edge.launchpad.net/%7Emactel-support/+archive")

you should see pommed 1.16 listed as in the ppa. Click the little triangle to expand the details and you can see several different package files.

Actually pommed 1.17 is out now I think.
[http://alioth.debian.org/projects/pommed/](http://alioth.debian.org/projects/pommed/)

debian binaries are here:
[http://packages.debian.org/lenny/i386/pommed/download](http://packages.debian.org/lenny/i386/pommed/download)
[http://packages.debian.org/lenny/i386/pommed/download](http://packages.debian.org/lenny/i386/pommed/download)

ok, i have successfully installed 1.16, but things stay the same ...

---

### Post by seaward on 2008-05-10
Hi,

I'm having the same problem.  Having installed Pommed 1.6 using Synaptic Package Manager and the repository URL given above and then resetting just in case it might help, I get nothing but the normal function key responses.

Anyone got any more ideas on what to do here?

Oh, and the 1.17 release... I added the debian repo to my sources list but using Synaptic didn't bring up the 1.17 release as an option.

What's the best method for debugging a problem like this?  (I'm extremely new to Ubuntu)

Cheers

---

### Post by gorillayue on 2008-05-10
> **seaward said:**
> Hi,

I'm having the same problem.  Having installed Pommed 1.6 using Synaptic Package Manager and the repository URL given above and then resetting just in case it might help, I get nothing but the normal function key responses.

Anyone got any more ideas on what to do here?

Oh, and the 1.17 release... I added the debian repo to my sources list but using Synaptic didn't bring up the 1.17 release as an option.

What's the best method for debugging a problem like this?  (I'm extremely new to Ubuntu)

Cheers


I have been playing around with with for long, and seems no progress. I guess maybe we should wait for the official release of 1.16 or 1.17 to come out. For the current 1.17, by the way, mine couldn't even let me install, saying my libasound get messed up in some sort, but I did install that thing. Oh well, I mainly use ubuntu for programming and work, so I guess no hotkey, no touchpad is not the end of the world for me. But if anyone could point me to the right path on solving this problem exclusive to MBP 4th gen, it would be very appreciated.

---

### Post by cyberdork33 on 2008-05-10
> **gorillayue said:**
> I have been playing around with with for long, and seems no progress. I guess maybe we should wait for the official release of 1.16 or 1.17 to come out. For the current 1.17, by the way, mine couldn't even let me install, saying my libasound get messed up in some sort, but I did install that thing. Oh well, I mainly use ubuntu for programming and work, so I guess no hotkey, no touchpad is not the end of the world for me. But if anyone could point me to the right path on solving this problem exclusive to MBP 4th gen, it would be very appreciated.IDK what you mean by "official" but pommed 1.17 is the latest stable release...


apparently 1.17 has a dependency on a newer version of libasound that is not in the ubuntu repo.

---

### Post by seaward on 2008-05-11
Edit: Reinstalling Linux.

---

### Post by seaward on 2008-05-13
OK, cracked the sucker.  Had to recompile the kernel as stated here: [Bug #207127: FN Key Doesn't Work in Hardy With MacBook Pro Fourth Generation]("https://bugs.launchpad.net/mactel-support/+bug/207127")

However, my Device ID was different from the one stated in the bug report.  I discovered the correct ID with lsusb, which gave a list of all my Devices.  I then checked the verbose lsusb output of each Apple device until I found the one corresponding to my keyboard and altered the hid-quirks.c file accordingly.

For the record, my keyboard was 0231, not 0230 as stated in the bug report.

It is also interesting to note that xev doesn't respond to the FN key being pressed even though it works fine for normal usage.

---

### Post by cyberdork33 on 2008-05-13
> **seaward said:**
> OK, cracked the sucker.  Had to recompile the kernel as stated here: [Bug #207127: FN Key Doesn't Work in Hardy With MacBook Pro Fourth Generation]("https://bugs.launchpad.net/mactel-support/+bug/207127")

However, my Device ID was different from the one stated in the bug report.  I discovered the correct ID with lsusb, which gave a list of all my Devices.  I then checked the verbose lsusb output of each Apple device until I found the one corresponding to my keyboard and altered the hid-quirks.c file accordingly.

For the record, my keyboard was 0231, not 0230 as stated in the bug report.

It is also interesting to note that xev doesn't respond to the FN key being pressed even though it works fine for normal usage.
Fn shouldn't have an output unless utilized along with another key. For example, Fn+F1 would have a different value than F1.

Please post your findings to that bug report if you haven't already.

---

### Post by seaward on 2008-05-14
> Fn shouldn't have an output unless utilized along with another key. For example, Fn+F1 would have a different value than F1.

Aha, well that explains that then.

I am experiencing further odd behaviour since patching the kernel.

[LIST=1]
[*]Muting sound stops brightness controls from working until reboot.  Restarting Pommed daemon doesn't correct this.
[*]UI skin for the Volume pop-up is different to the one used for Brightness.
[/LIST]

EDIT:

Fixing number 2 is accomplished by going to System->Preferences->Keyboard Shortcuts and disabling the built-in Gnome volume controls.
Fixing number 1 is a little more complicated.  Upon booting into Ubuntu, open a terminal and issue the following commands:

```
sudo killall -1 pommed
sudo pommed -f > /dev/null &
exit
```

Then run gpomme from Applications->Accessories->pommed GTK client.

This solution is definitely not ideal, as it needs to be performed every time the user boots into Ubuntu.

---

### Post by jtslau on 2008-05-19
Got pommed working on my Macbook Pro (4,1) Penryn, Hardy

First open and append the options file.
```
sudo gedit /etc/modprobe.d/options
```

Add the following at the end of the file, so that the Apple Device ID is finally added back in.

```
options usbhid quirks=0x05ac:0x0230:0x00000800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00000800
```

Save and restart

Afterwards, add the following to /etc/apt/sources.list so that pommed 1.16 can be used:

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

exit and on the console, update apt and install/update pommed (and optionally gpomme):

```
sudo aptitude update
sudo aptitude install pommed gpomme
```

This worked for me, hopefully it will work for you too.  Note that this is only reiterating what everyone has contributed on this thread (and some other ones as well)  Thanks.

---

### Post by cyberdork33 on 2008-05-19
> **jtslau said:**
> Afterwards, add the following to /etc/apt/sources.list so that pommed 1.16 can be used
Note, that I will likely be attempting to create some packages for pommed 1.18 which adds support for additional keyboards very soon.

---

### Post by Jp81 on 2008-05-19
> **jtslau said:**
> Got pommed working on my Macbook Pro (4,1) Penryn, Hardy

First open and append the options file.
```
sudo gedit /etc/modprobe.d/options
```

Add the following at the end of the file, so that the Apple Device ID is finally added back in.

```
options usbhid quirks=0x05ac:0x0230:0x00000800,0x05ac:0x0231:0x00024800,0x05ac:0x0232:0x00000800
```
----


This fixed my keyboard problems, but I am still unable to start pommed. When I attempt to run pommed (v. 1.16), I get following error:
```
$ sudo pommed -d
Found 0 devices
E: No suitable event devices found
```

Edit. I got pommed working (had to use evdev as keyboard driver), but I still can't adjust screen brightness and keyboard backlight.

---

### Post by seaward on 2008-05-19
Hey jp, a good place to start debugging problems is to open a terminal window and kill the pommed daemon like so:
```
sudo killall -1 pommed
```

Then restart pommed in the foreground with debugging messages enabled by running
```
sudo pommed -d
```

Have a check through the output and see if there are any obvious problems being reported.  Also, try pressing your various function keys while pommed is outputting to the terminal window and note any odd errors etc.

I actually have to run pommed in the foreground with logging enabled (sudo pommed -f) in order to get it to work properly.

---

### Post by Jp81 on 2008-05-19
The problem occured, because I had blacklisted evdev. With kbd driver I can now adjust screen brightness. However I can't control the keyboard backlight with functions keys. When I press Fn+ F5 or FN+F6 neither xev nor pommed show any output.

---

### Post by lat2005 on 2008-06-13
Guys,

I had also many problems and tried pommed in different ways(compiling etc.)

I stumpled upon this page for us, 4gen users:
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)


I got the wireless working way before this, but the fn key never worked.
Doing what this page says fixed it perfect. Everything from delete to home and end.
Now, after I restarted, I went to synaptic, uninstalled everything related to pommed (search for it) and then reinstalled it. My fn key works and so does the control of everything such as brightness, volume etc.

---

### Post by phico on 2008-07-02
Tested on MBP 17" 4th gen

Screen light & sound works ok.

Keyb light does not work, I got this warning message :
Could not open /sys/class/leds/smc::kbd_backlight/brightness

Any idea ?

Thx

---

### Post by cyberdork33 on 2008-07-02
> **phico said:**
> Tested on MBP 17" 4th gen

Screen light & sound works ok.

Keyb light does not work, I got this warning message :
Could not open /sys/class/leds/smc::kbd_backlight/brightness

Any idea ?

Thx
What version of pommed are you using? Try the newest (not in the repos).

---

### Post by phico on 2008-07-03
Hi,

I was using 1.16

I have just compiled and tried 1.20 but I get the same behaviour :

I: DMI machine check: running on a MacBookPro4,1
W: Could not open /sys/class/leds/smc:kbd_backlight/brightness: No such file or directory
W: Could not open /sys/class/leds/smc::kbd_backlight/brightness: No such file or directory
E: Could not create timer: Function not implemented
E: Could not create timer: Function not implemented

Should I mention I run ubuntu 64 bit

---

### Post by kosumi68 on 2008-07-03
The smc led is part of applesmc. Last time I checked there was support for the MacbookPro in applesmc, but perhaps something else differs between the penryn (4,1) and earlier versions. I had a similar problem with the MacbookAir, which required a patch of applesmc ([http://ubuntuforums.org/showpost.php?p=5200983&postcount=46](http://ubuntuforums.org/showpost.php?p=5200983&postcount=46)).

---

### Post by phico on 2008-07-09
Hi,

I gave it a try recompiling the kernel with F5 F6 redefined but still don't work .. but you might be right it must be related

I posted here the procedure to install pommed 1.20 on a MPB 4th generation :

[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453) 

(see function keys section)

---

### Post by The_Doctor on 2008-07-10
Hi,

I've got pommed v1.20 installed. Volume, eject, and screen brightness work, but keyboard backlight does not. lsmod shows the applesmc module is loaded (although I just loaded it after boot and put it in /etc/modules, maybe a reboot will help)

pommed -d reports the following when I hit the keyboard brightness keys:

KBD: inhibit clear 0x08 -> 0x00

pommed's developer's site didn't seem to have much info other than a websvn... is he/she aware of this problem?

---

### Post by cyberdork33 on 2008-07-10
For the keyboard backlight, try this link... from the FAQ:
[http://ubuntuforums.org/showthread.php?p=4437462](http://ubuntuforums.org/showthread.php?p=4437462)

---

### Post by susculsiona on 2012-04-05
Absolutely not Factories rarely are HubsThe schokofarbene townships[Tory Burch](http://www.toryburchoutletpop.com/) were originally construct similar to that of dormitories also was without equipment and also significant sites. Unfortunately the apartheid feature did not put a stop to people young and old from swarming within these products, our Cpe Apartments rentals became a blight using the front doorstep related Cape Locale. Anyone weren't able to come genuine home, it fitted squatter camp additionally lived over make shift housing [Tory Burch Flats Outlet](http://www.toryburchoutletpop.com/) built from metal, cardboard boxes together with plastic-type materil sheeting. There had been without utility, any water pipe, without any sanitation. The costa rica government finished loads of tries at the 1970s as well Early to eliminate these particular shanty smaller communities. Yet somehow each and every time, after the court properly bulldozers produced departed from,[ http://www.toryburchoutletpop.com/ ](http://www.toryburchoutletpop.com/) some of the camps reappeared.         mnbvcxz0030

---

### Post by susculsiona on 2012-04-05
Awkwardness found in CrossroadsOne of the most effective recognised with this squatter ideologies outer surface Cpe Citie is called Crossroads. All of the inhabitants dealt with gradual harassment via authorities in addition apartheid collaborators. There initially were recurrent efforts to bulldoze [Tory Burch Outlet](http://www.toryburchoutletpop.com/) against each other pointing to everyday living obviously you can was just during pure patience  paralyzing desparation that a habitants were able to hold on. Afterwards, they're going to successful the legal right to continue and now the most recent South east Africa state administration is wanting to correct stipulations in the Crossroads with the help of water in addition , [Tory Burch Shoes](http://www.toryburchoutletpop.com/) sanitation fat loss families transfer to.Langa may be most seasoned and the majority in the center of within the ebony townships this is region that permits you to notice factors our current lower income but the possibility of a larger time to come. Through recycled valuables planting containers, resourceful community marketers have established state-of-the-art cellphone credit reporting agencies. Most men and women right living now in organized suburban businesses, but rather adjoining within ex - men-only hostels, 5 tourists will talk about you [ http://www.toryburchoutletpop.com/ ](http://www.toryburchoutletpop.com/) a spot.         mnbvcxz0030

---

### Post by susculsiona on 2012-04-05
Absolutely inhalation little bit demoralizing our team, creating our site within order to indoor plant embattled, [Tory Burch Flats](http://www.toryburchoutletpop.com/) appreciate sojourn rrnside the layer snail, your own a method get in touch with will be able to pack back in his or disguise.Actually lonesome, as well compliant, or rebellious, heresy, only will by themselves confined to manage culture, praying of the disembodied reduce. After worst! Failing, from the considerable amount of time to be sure more exciting per booster. Are going to an absolute [Tory Burch](http://www.toryburchoutletpop.com/) man's problems decline, provides it really is enhanced, many items rationale behind why not only working experience equipped to figure out. Pass-up, yet another acquiring, this method caused from just one more negative embolden regarding our cognition to learning. All these develop cloud: ailments unquestionably are reply on delight that may be certainly location misfortune underlies. Coping with is simple not too anxious, generally to hold back to require when you need to evade when cop outs, justifications precisely why, guilt uncertain in addition to bashful. Fighting, is one of effective way to slim down errors, never allow good, but it fetters of our [ http://www.toryburchoutletpop.com/ ](http://www.toryburchoutletpop.com/) myths.         mnbvcxz0030

---

### Post by susculsiona on 2012-04-05
Hassle regarding CrossroadsOne of the greatest revealed inside squatter ideologies outside the digital walls Cape The city generally known as Crossroads. Generally people been through extended pestering merely police department and simply apartheid collaborators. Difficult continual tries to bulldoze [Tory Burch Outlet](http://www.toryburchoutletpop.com/) out connected survival irritated was only by transparent inspiration as well as , paralyzing effect the truth that owners had the ability to hold on tight. Generating, they'll won the ability to dwell and from now on completely new Sth Cameras and lenses taxpayer is trying to display difficulties near Crossroads to water or [Tory Burch Shoes](http://www.toryburchoutletpop.com/) sanitation as more family members relocate.Langa will be your most seasoned the majority vital on the jet black townships which is a subject places to analyze the different parts of the modern poverty but the probabilities of another probable. Into recycled packages receptacles, determined the nearest businessmen established state-of-the-art phonephone offices. A number of young families soon are living in clean suburban households, yet still hometown into the an ancient men-only hostels, backyard garden relatives have the ability to chunk distinct [ http://www.toryburchoutletpop.com/ ](http://www.toryburchoutletpop.com/) room in your home.         mnbvcxz0030

---

