---
title: "X Server Crashes"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by sbjaved on 2006-07-27
Hi,
I'm a newbie to Linux and ubuntu is the second distro i've gathered  up courage to try (First being RedHat 9.0)
Upon popping in ubuntu CD and selecting install, i encountered a "X Server Crash" message and a suggestion that i should reconfigure it. Frankly i don't have clue what "X Server" is (so much for reconfiguring it), but i didn't throw the CD out of the window...I gave it another shot. I tried to use the "Safe Graphics" mode which yielded a similar result. For the technically enlightened, here's what the screen told me (It seems gibberish to me though):

-------------------------------------------------------------------
Failed to start X Server

X Windows System 7.0.6
X Protocol Version 11

(WW) VESA: No Matching Device Section
(WW) ****INVALID MEM ALLOCATION**** b: 0x20000000 e: 0x27ffffff
correcting^G
(EE) VESA(0): cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuration
-------------------------------------------------------------------

Note: I have Windows XP SP2 on Primary C: Drive and my ATi card works perfectly with it, if ubuntu is suggesting something's wrong with my card.

MY SYSTEM:

Intel Pentium 4 1.8GHz 
Intel D845GLVA
Kingston 512MB RAM 
ATi Radeon 9200SE 128MB PCI version (Intel's integrated Video disabled)
Seagate HDD 80GB IDE
Liteon DVD-ROM

---

### Post by wpshooter on 2006-07-27
Well I am probably no more technically enlighted than you are (may be the blind leading the blind), but my first question would be, is this the desktop installation version or is it the alternate CD version ?

And my second question would be did you run the sum check utility that is shown on the initial boot menu when you boot from the CD ?

I don't think this is probably related to your troubles but of all the ATI cards I have, my machines that is using the 9200 seems the most tempermental as opposed to say my ATI Radeon 7000, 9600 and 9600XT.

Good luck.

---

### Post by The Noble on 2006-07-27
When the errors send you to the black screen in command line, login and type
```

sudo nano /etc/X11/xorg.conf

```
There will be a lot of text, so use the arrows on your keyboard and go to the part that says
```

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
        Option          "RenderAccel"           "false"
	Option          "NoLogo"                "true"
EndSection

``` 
Note that mine is way different than yours, so go to the Section "Device". Your "Driver" will be vesa, if it isn't set it to vesa. If it already vesa, change it to mesa.

---

### Post by djsroknrol on 2006-07-27
My specs are the same as yours...go to your xorg.conf, and in the device section, try inserting the bold item:

```
Section "Device"
	Identifier	******
	Driver		"**ati**"
	BusID		"PCI:1:0:0"

```

That should get you going...

---

### Post by atrus123 on 2006-07-27
Perhaps there is some issue with the open source driver and your particular card.

No matter, you can simply install the ATI binary (closed source) driver.

I assume that X is kicking you to the command line.  Good, that's the best place from which to install files.

Type:

# sudo apt-get install xorg-driver-fglrx 

Once that is complete, you need to edit an aforementioned file.

# sudo nano -w /etc/X11/xorg.conf

From here, look up:

Section "Device"
        Identifier "..."

and change your driver to "fglrx".

Reboot into X.  Profit.

---

### Post by sbjaved on 2006-07-28
> **wpshooter said:**
> Well I am probably no more technically enlighted than you are (may be the blind leading the blind), but my first question would be, is this the desktop installation version or is it the alternate CD version ?

And my second question would be did you run the sum check utility that is shown on the initial boot menu when you boot from the CD ?

I don't think this is probably related to your troubles but of all the ATI cards I have, my machines that is using the 9200 seems the most tempermental as opposed to say my ATI Radeon 7000, 9600 and 9600XT.

Good luck.
Trust me dude...You're not as dumb as me...My knowledge of linux is about as ept as my grandmother's :)

But what do you mean about "alternate installation CD"...I only have a single ubuntu CD which i requested over the internet...

---

### Post by sbjaved on 2006-07-28
> **djsroknrol said:**
> My specs are the same as yours...go to your xorg.conf, and in the device section, try inserting the bold item:

```
Section "Device"
	Identifier	******
	Driver		"**ati**"
	BusID		"PCI:1:0:0"

```

That should get you going...
You mean when the "X Server" takes me to something that looks suspiciously like DOS Prompt??? Should i enter this 'code' there??

P.S: I'm quite scared of sculpting and tailoring THE code...i've this sneaky feeling it always leaves you in a hole you can't climb out of...

---

### Post by 3rdalbum on 2006-07-28
> **sbjaved said:**
> You mean when the "X Server" takes me to something that looks suspiciously like DOS Prompt??? Should i enter this 'code' there??

P.S: I'm quite scared of sculpting and tailoring THE code...i've this sneaky feeling it always leaves you in a hole you can't climb out of...

When you get to the "DOS Prompt" (it's just a command-line), type:

```
sudo nano /etc/X11/xorg.conf
```

(that's a capital X in X11)

Type in your user password, and then that brings up a text editor. In the bit that says Section "Device", change whatever information you have there to the information given in this thread.

When you have changed it, press Control-X, then the Y key, then press Enter. You will be brought back to the command prompt. Type "startx" and then press Enter, and hopefully you will be looking at a GUI.

--
Other posters in this thread: The original poster mentioned that he was using his SECOND video card, with his first card disabled. Please adjust your instructions accordingly if you haven't done so already.

---

### Post by djsroknrol on 2006-07-28
Yes.."ati" is the default driver in a ubuntu install with ati cards..don't be afraid of the command line as it really is your friend..:) Just follow the above instructions and replace whatever is in that driver line in your xorg.conf file with "ati" and I'm sure you'll be good to go.

---

### Post by sbjaved on 2006-07-28
> **djsroknrol said:**
> Yes.."ati" is the default driver in a ubuntu install with ati cards..don't be afraid of the command line as it really is your friend..:) Just follow the above instructions and replace whatever is in that driver line in your xorg.conf file with "ati" and I'm sure you'll be good to go.
Here's what my xorg.conf file shows:

Section "Device"
Identifier: "intel D845/825 Brookdale Chipset"
Driver: "i820"
BusID: 0:2:0

That's all very well but the thing is that i have already disable d the built in intel graphics adapter and my monitor is currently plugged into my radeon 9200SE...So why is it showing a disabled adapter instead of the in-use one? Plus should i go ahead and change the 'Identifier' and 'Driver' entries to "ati"? 

Just thought i'd ask before doing something stupid...

---

### Post by djsroknrol on 2006-07-28
The reason being is that you haven't reconfigured the Xserver...change the identifier to:

```
"ATI Technologies, Inc. Radeon 9200 SE (RV280)secondary"

```

with the quotes, and the driver to:

```
"ati"
```

quotes there as well..save the file and you'll be all set..I'm running the 9200Se as well so I can vouch for the integrity of the driver..don't forget to restart x...]

---

### Post by djsroknrol on 2006-07-28
EDIT..I gave you part of my multi monitor Xorg by mistake...the identifier is:

```
"ATI Technologies, Inc. Radeon 9200 SE"
```

That's the correct identifer...

---

### Post by sbjaved on 2006-07-29
what about the BusID?? Leave it to 0:2:0???

---

### Post by GuitarHero on 2006-07-29
Yes that should be fine.

---

### Post by sbjaved on 2006-07-29
> **GuitarHero said:**
> Yes that should be fine.
The X Server error file shows the intel graphics chip at BusID 0:2:0 while the ATI Card at BusID 1:0:0...so i tried djsroknrol's advice and did following:

*****************************************************************
File: /etc/X11/xorg.conf

Section "Device"
Identifier: "**ATI Technologies Inc RV280 [Radeon 9200 SE] rev 1**"
Driver: "**ati**"
BusID: PCI:**1:0:0**

Ctrl^X

Yes

Sudo Reboot
*****************************************************************

After reboot the CD crashed at the SAME error!!
What did i do wrong? I thought the file was modified...why didn't it follow my instructions. The X Server error log(Blue Screen one) again showed "intel D845/825 Brookdale Chipset Graphics" as indentifier and the only change was that driver changed from "i810" to "vesa"...WTF???

Maybe some command is required to start the GDM without reboot...or reboot restores the file to default??What is it guys?

---

### Post by djsroknrol on 2006-07-29
I do believe you should have left the BusID at 0:2:0 as it found your original graphics card on another busID and the ati card at yet another...I'd change it back and see what happens...

---

### Post by djsroknrol on 2006-07-29
EDIT..I believe the command you're looking for is:

```
sudo dpkg-reconfigure xserver-xorg
```

That will rebuild your xserver and write a whole new Xorg.conf file for you...double check to make sure your i810 graphics card is disabled before you attempt it.

---

### Post by sbjaved on 2006-07-29
> **djsroknrol said:**
> I do believe you should have left the BusID at 0:2:0 as it found your original graphics card on another busID and the ati card at yet another...I'd change it back and see what happens...
Leaving it to 0:2:0 doesn't work...i think i know why, maybe cause we're trying to force the integrated graphics chip (which is disabled) to work using "ati" driver...bcz as i earlier said the BusID for the integrated chip is 0:2:0 while for the ATI card is 1:0:0...But when you enter 1:0:0 it doesn't work as well! 

The following blue screen X Server error was encountered when the driver settings in xorg.conf were changed from "i810" to "ati":

(EE) I810 (0): Cannot read V_BIOS
(EE) I810 (0): VBE initialization failed

These are different from the errors i recieved earlier.

These are the things i wanna know:

1) what does "cannot read V_BIOS" means?
2) Is a "sudo reboot" command required to view the changes made to xorg.conf file?(Because thats what i've been doing after each change)
3) what if ubuntu doesn't recognize that Intel's integrated chip is disabled and still tries to use it as primary adapter(which ofcourse causes errors as i disabled it in Windows)...How can i check IN UBUNTU's COMMAND LINE if the chip is disabled or not? Or disable it if its not?

I need an miracle...i'm starting to lose it...

---

### Post by sbjaved on 2006-07-29
> **djsroknrol said:**
> EDIT..I believe the command you're looking for is:

```
sudo dpkg-reconfigure xserver-xorg
```

That will rebuild your xserver and write a whole new Xorg.conf file for you...double check to make sure your i810 graphics card is disabled before you attempt it.
I've tried this command but no avail...It asks at the start to automatically detect the Video Hardware and automatically uses the disabled chip...why oh why doesn't it reconize the ATI card in the PCI slot???

Plus how do i check in UBUNTU's CLI(command line interface) whether the chip is disabled or not? Its definitely shows as disabled in my XP...

---

### Post by djsroknrol on 2006-07-29
I'm at a loss as to why it's not working...you could check your /var/log/dmesg log, your /var/log/messages log and your /var/log/kern.log to see if there are any conflicts that we're missing...

---

### Post by sbjaved on 2006-08-02
The dpkg-reconfigure xserver-xorg did the trick!!!!

I was welcomed by a Ubuntu screen with all the icons...Yayyy!

But i didn't find an install button to install Ubuntu on the Hard disk...

Where would that be? Plus if i reboot will the xorg.conf file be restored to default values??? I would have to run the configuration utility again?

---

### Post by djsroknrol on 2006-08-02
That's great that it is running, but I'm confused..is it a install CD you're running?...if it is, the install icon should be at the top left corner of your screen.

Yes, Xorg.conf will change if you're running a "live" version of Ubuntu...

---

### Post by sbjaved on 2006-08-03
> **djsroknrol said:**
> That's great that it is running, but I'm confused..is it a install CD you're running?...if it is, the install icon should be at the top left corner of your screen.

Yes, Xorg.conf will change if you're running a "live" version of Ubuntu...
Umm i'm confused too...

There are 3 types of CD's i'm hearing about:
a) Desktop CD
b) Live CD
c) Install CD

I don't know what type i'm using...I only requested an Ubuntu CD over the internet and they sent me a single CD...that's all i know!!

---

### Post by sbjaved on 2006-08-03
:confused:

---

### Post by zisme on 2006-08-03
They *should* all be the same! The desktop CD is the type of CD you ordered. There's desktop and alternate I think. The Live CD is also on there, so you can boot up to it without actually instatlling it. The Install CD is there too, once you go to Live CD, you can Install from there.

---

