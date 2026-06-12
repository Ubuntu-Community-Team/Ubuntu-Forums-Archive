---
title: "Screen Resolution"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by will peavy on 2007-08-14
In my screen resolution preferences, I only have the option to choose 800x600 or 640x480. However, my monitor should optimally run at 1280x800. How can I fix this?

---

### Post by diatribe on 2007-08-14
what kind of video card?

---

### Post by brownknight on 2007-08-14
Do you know what kind of video card you have?

---

### Post by creedog on 2007-08-14
take a look at the file xorg.conf under /etc/X11

see if it detected your video card correctly. In that file you will also see a section that X uses to set the resolution. Here is a bit of mine. Its a bit tricky because I use custom modes (refresh rates and other complex crap that I do not understand) to set the res/refresh rate. However in theory, you should be able to plug the res in that you want to use.
 ```


Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option          "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "1440x900_85.00" "1440x900_75.00"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1440x900_85.00" "1440x900_75.00"
    EndSubSection
EndSection

                           
```


Best bet is to fine an xorg.conf of someone who has the same video card as you and copy theirs.

Also remember the first rule..... always make a backup before you start futzing with a file. Ok?

---

### Post by will peavy on 2007-08-14
Dia and Brown,

I have: VIA® Chrome9™ HC IGP.

Cree,

Here is what is in my xorg.conf file:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
EndSection

```

---

### Post by OZTack on 2007-08-14
see this post, then send a thank you to Ec0nomik :)
[http://ubuntuforums.org/showpost.php?p=3111514&postcount=2]("http://ubuntuforums.org/showpost.php?p=3111514&postcount=2")

---

### Post by will peavy on 2007-08-14
Hi OZT,

I started following Ec0nomik's directions, but received this message:

[IMG]http://willpeavy.net/misc/xorgbak.png[/IMG]

---

### Post by Arthur Archnix on 2007-08-14
start with "sudo",  no quotes

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```

---

### Post by creedog on 2007-08-14
Try this..... note that I am eliminating the extra depths that you will never end up using.
cntrl-alt-bacspace 
will restart x

if this does not work then log in on the command line and copy your backup file over your xorg.conf. Note that at this point you may have to research custom mode lines to add to your xorg.conf


```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"800x600" "(pitch" "800)" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "(pitch" "800)" "1280x800"
	EndSubSection
EndSection
```

---

### Post by will peavy on 2007-08-15
sudo solved the permission issue, thanks Arthur. I went ahead and followed Ec0nomik's directions, but it broke the GUI. So I copied the backup file over from the command line and was back to where I was originally. creedog, I added your edits to xorg.conf, but it had no effect on the graphics. 

Thank you for your help everyone that has responded. It looks someone else is dealing with the same graphics card issue in a thread at [http://ubuntuforums.org/showthread.php?t=504849](http://ubuntuforums.org/showthread.php?t=504849) , so I'm going to move over there unless anyone has more ideas here?

---

### Post by Arthur Archnix on 2007-08-15
I might have one or two. Post the output of lspci
```
lspci
```
If it's long, put it in code or quote so that it's easier for us to read.

EDIT: If it doesn't turn out (your post I mean) how you wanted, use edit then "go advanced" to try another. I'm sorry, I'm not sure what the right tag is to prevent a real long post of output. Maybe you can tell me if you find out. ;)

EDIT2: oh and nice job copying back your original. It shows a strong ability for linux figuring that out on your own!

---

### Post by will peavy on 2007-08-26
Hi Arthur,

Here's what I got with lspci

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6364

00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge

00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)

00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)

00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge

01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

05:01.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```

---

