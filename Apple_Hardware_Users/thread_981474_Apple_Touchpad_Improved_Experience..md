---
title: "Apple Touchpad: Improved Experience."
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by volanin on 2008-11-13
I finally made the switch to Intrepid, and as always, here goes my personal
modifications to the touchpad driver, in order to improve the Ubuntu experience
for Apple users.

The packages attached replace the current touchpad driver in X.org and have
been improved over the original. They add cursor stabilization (the mouse
arrow no longer dances around when multiple fingers are pressed, just
like the MacOSX behaviour), and they improve the finger-click behaviour:
The mode of operation where two fingers on the touchpad + click generates
a right click.

Also attached here, is a fdi file to configure your touchpad to better
match the sensation of MacOSX (at least for my hardware). You can
always tweak the values based on your own preferences.

Copy the contents here to the file **/etc/hal/fdi/policy/appletouch.fdi**:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

Just download the attached deb corresponding to your architecture (i386 or amd64),
and after installing, restart X.org or reboot your computer.
Please, post your opinions here!
:)


_**Attention:**_

**1.** This driver has not been tested on the new multitouch touchpads,
but it has no reason not to work.

**2.** If you prefer, these files are also available from the Mactel PPA:
*deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main*

**_______**

---

### Post by kosumi68 on 2008-11-13
Great work! I am running it on an MBA11 with the bcm5974 driver, with pleasant result. Comparing to the ubuntu version, I can see that the patch is small. How about adding that static variable to the touchpad state and submitting it as a patch upstream?

---

### Post by bryonak on 2008-11-14
kosumi, is it working well with key="info.product" contains="appletouch" on your MBA?
If this does matter, volanin should mention it at the top.

volanin, note that you don't have to restart the X server in order to make the changes take effect. Reloading touchpad modules is sufficient:

MacbookPro 3.1 (Santa Rosa) owners:
```
sudo modprobe -r appletouch && sudo modprobe appletouch
```

MacbookPro 5.1 (Penryn) owners:
```
sudo modprobe -r bcm5974 && sudo modprobe bcm5974
```

MacbookAir and the 5th Gen Laptops should be bcm5974 too, all the other Macbooks use appletouch AFAIK.


Apart from that it looks good, though I personally prefer different settings (VertEdgeScroll for instance... FingerLow and FingerHigh are at 3 resp. 10 with me, also my AccelFactor is four times higher and I've put more of the available options into the file). But yours probably approximates the feeling of OSX better ;)

---

### Post by kosumi68 on 2008-11-14
> **bryonak said:**
> kosumi, is it working well with key="info.product" contains="appletouch" on your MBA?
If this does matter, volanin should mention it at the top.


Right, I was a bit unclear. I am using my own settings, based on the default configuration in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi. As you point out, using appletouch would not work for me. Thanks!

---

### Post by volanin on 2008-11-14
Indeed, as kosumi68 implied, the fdi file provided in entirely optional.
But you have a very good point, and I changed it to work both with appletouch and bcm5974!
:)

Anyway, the point of the post are the new packages.
In my opinion, they improve your experience independent of the settings you prefer!

---

### Post by cyberdork33 on 2008-11-16
Excellent work.

---

### Post by david_edmundson on 2008-11-23
I now get the non-jumpy cursor when using multiple fingers, but I don't have right-click when holding two fingers on the trackpad and clicking. What am I missing? 

Kubuntu, Macbook 2,1

---

### Post by hellmitre on 2008-11-23
Thanks very much! An improvement over the one I wrote myself. Thanks for this!

---

### Post by eir14 on 2008-12-03
Hi, 
I am new to Ubuntu and this is my first attempt at tweaking the touchpad. I was able to create the appletouch.fdi file, however when I click on the link to download the deb file it gives me the error

 "/tmp/xserver-xorg-input-synaptics_0.15.2-0ubuntu7-mactel1_amd64-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

I have no idea what this means. Is there an application that I need?

---

### Post by volanin on 2008-12-04
Try saving the DEB file to your computer first.
Then after downloading it, try running it.
:)

---

### Post by eir14 on 2008-12-04
> **david_edmundson said:**
> I now get the non-jumpy cursor when using multiple fingers, but I don't have right-click when holding two fingers on the trackpad and clicking. What am I missing? 

Kubuntu, Macbook 2,1

Im having this issue as well. Any suggestions?

---

### Post by eir14 on 2008-12-04
I am also having this issue. any suggestions?

edit: didnt mean to double reply.

---

### Post by hanzomon4 on 2008-12-25
This ain't working the fdi file refuses to take. I've rebooted and removed mousemu, it's just not working.

---

### Post by zhark1 on 2008-12-25
> **eir14 said:**
> Im having this issue as well. Any suggestions?

I had to change the file like this to make it work:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
<!--
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
-->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>
```

It seems info.product doesn't match against appletouch or bcm5974.
I also added the VertScrollDelta option but it doesn't seem to do much difference if I set it to 30 or a 1000, I would really like to speed up two-finger scrolling a bit.

Macbook Pro 3,1

---

### Post by macintosh on 2008-12-26
First of all I will wait for Jaunty for this to hopefully be implemented in.

---

### Post by jpugh on 2008-12-26
> **macintosh said:**
> First of all I will wait for Jaunty for this to hopefully be implemented in.

...and 2nd?

I see no LP bug. Without it there will be no update in jaunty.

---

### Post by hanzomon4 on 2008-12-27
> **zhark1 said:**
> I had to change the file like this to make it work:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
<!--
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
-->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>
```

It seems info.product doesn't match against appletouch or bcm5974.
I also added the VertScrollDelta option but it doesn't seem to do much difference if I set it to 30 or a 1000, I would really like to speed up two-finger scrolling a bit.

Macbook Pro 3,1

Dropping it to 20 helps 

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
<!--
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
-->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>

```

---

### Post by skullmunky on 2009-01-02
hm, Multi-finger clicking's not working for me either ... (macbook 1,1).  But the cursor is much more stable.  synclient -m shows that 2 and 3 finger touches are being recognized, but they're not getting translated into M- and R- clicks.

Oh, wait, I get it!  

You have to hold two fingers down AND click the button.  You have to turn on the tap-to-click option to just tap two or three fingers .

---

### Post by cyberdork33 on 2009-01-02
> **skullmunky said:**
> You have to hold two fingers down AND click the button.  You have to turn on the tap-to-click option to just tap two or three fingers .

Yep, they are two different functions. You can disable one or the other.

---

### Post by pepsifx357 on 2009-01-17
> **zhark1 said:**
> I had to change the file like this to make it work:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
<!--
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
-->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>
```

It seems info.product doesn't match against appletouch or bcm5974.
I also added the VertScrollDelta option but it doesn't seem to do much difference if I set it to 30 or a 1000, I would really like to speed up two-finger scrolling a bit.

Macbook Pro 3,1

Whoever you are, you are a God send.  Thank you, right click and scroll works!

---

### Post by ludwigbaum on 2009-02-04
On my McBook June 2006 the tricks above did not work.
In

   /usr/share/hal/fdi/policy/20thirdparty

I found another fdi-file for the synaptics touchpad, which seemed to override fdi-files in /etc/hal.

After killing this file,the following link (in German) and its fdi-file worked perfectly:

  [http://wiki.ubuntuusers.de/Apple_Computer/Einrichtung](http://wiki.ubuntuusers.de/Apple_Computer/Einrichtung)

One-finger-click, two-finger-click as rigth-click, two-finger-vertical and horizontal-scrolling are there.

---

### Post by deltaiscain on 2009-02-24
Is there a way to turn off the drag lock? It is sometimes irritating when i click on the desktop and it makes one of those boxes, it drags it. 
Thanks!

---

### Post by cyberdork33 on 2009-02-24
> **deltaiscain said:**
> Is there a way to turn off the drag lock? It is sometimes irritating when i click on the desktop and it makes one of those boxes, it drags it. 
Thanks!
type 'man synaptics' in a terminal. there are several options that you can use to change the touchpad behavior.

---

### Post by deltaiscain on 2009-02-24
> **cyberdork33 said:**
> type 'man synaptics' in a terminal. there are several options that you can use to change the touchpad behavior.

Thanks!

---

### Post by gfern on 2009-02-26
Hi Volanin! 

I know quite little of Linux in general but am attempting to set up Interpid Ibex on my Macbook 5,1. 
What I mean to ask you is whether what you've is something different from the bcm5974-dkms package that we are told to install when referring to the Ubuntu documentation for Macbooks ([https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad](https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad)). If so, what is it exactly that I should do to intall your improvements? 
Should I copy that code to /etc/hal/fdi/policy/appletouch.fdi, without deleting what was in the file before? Should I just copy and paste and not care about the previous configurations and pieces of code in the file? And, after that, install the deb file for my architecture? - in my case, 64bits.  

Thanks for clearing that up! 

ps; Quite a surprise when I saw that you also live in BH! I kept on with English since I figured other users could benefit from our exchange.

---

### Post by cyberdork33 on 2009-02-26
> **gfern said:**
> Hi Volanin! 

I know quite little of Linux in general but am attempting to set up Interpid Ibex on my Macbook 5,1. 
What I mean to ask you is whether what you've is something different from the bcm5974-dkms package that we are told to install when referring to the Ubuntu documentation for Macbooks ([https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad](https://help.ubuntu.com/community/MacBook5-1/Intrepid#Trackpad)). If so, what is it exactly that I should do to intall your improvements? 
Should I copy that code to /etc/hal/fdi/policy/appletouch.fdi, without deleting what was in the file before? Should I just copy and paste and not care about the previous configurations and pieces of code in the file? And, after that, install the deb file for my architecture? - in my case, 64bits.  

Thanks for clearing that up! 

ps; Quite a surprise when I saw that you also live in BH! I kept on with English since I figured other users could benefit from our exchange.the bcm driver is the Linux kernel driver for the hardware. This driver is the xorg driver. they are used in combination to get the functionality you want.
His driver is the mactel-support PPA though, and you can get it from there.
[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

---

### Post by rabinnh on 2009-02-27
I appreciate all the work done by the people on this forum.

I have Intrepid installed installed on a Macbook Pro 5.1.  I'm not sure what I should expect, but even after installed all the patches and config files, my touchpad makes Ubuntu almost unusable.  The 2 main issues are;

1) When attempting to click on an icon or menu selection, the pad is so sensitive that the pointer jumps all over the place.  I've tried lowering the sensitivity, but then the cursor gets herky-jerky moving over the workspace.

2) I have not been able to figure out how to drag a window.  I can get the "hand" cursor but while I am pressing a button, the cursor will not move.

Any help would be much appreciated.

rabinnh

---

### Post by rmdegennaro on 2009-02-28
Thank you to everyone, the updates are great.  I uninstalled mouseemu & created the fdi file and things work great.  

I still have troubles with sound (using KDE) and 64-Bit Ubuntu or Kubuntu never worked for me.  Back to those when I have another free moment.  ;-)

---

### Post by roulettescars on 2009-03-04
This just doesn't seem to be working at all. I'm on a 3.1 MBP and I'm getting no scrolling, right or middle clicks. Any ideas? I've installed the file without any trouble, and tried all of the different configs.

---

### Post by cyberdork33 on 2009-03-04
> **roulettescars said:**
> This just doesn't seem to be working at all. I'm on a 3.1 MBP and I'm getting no scrolling, right or middle clicks. Any ideas? I've installed the file without any trouble, and tried all of the different configs.
are you in jaunty?

---

### Post by alexander.deca on 2009-03-16
All,

I got the touchpad working but after a reboot the touchpad is not working anymore. 
I followed the thread and installed the .deb from mactelsupport added a bcm5974.fdi in /etc/hal/fdi/policy/ but it seems that the touchpad is recognized.

I am using a macbook pro 4.1 with ubuntu 8.10.

Am I missing something here?

cheers

---

### Post by philcolbourn on 2009-03-16
I found that gsynaptics messes with any setting in a fdi file, so if you want consistent results then un-install gsynaptics.

```
sudo apt-get remove --purge gsynaptics
```

I have attached my fdi file that enables circular scrolling, finger tapping, and the sensitivity seems closer to what I am used to in OS-X.

I placed it in

```
/etc/hal/fdi/policy/21-x11-bcm5974-pc.fdi
```

I also have a script that installs all the recommended packages and modules etc. to get Intrepid working on a MacBook Pro 4,1.

see [http://ubuntuforums.org/showthread.php?t=1096694]("http://ubuntuforums.org/showthread.php?t=1096694")

I have a MacBookPro4,1 so it may not work to same on other models.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities"	contains="input.touchpad">
      <match key="info.product"		contains="appletouch">
        <merge key="appledevice"	type="bool">true</merge>
      </match>
                          
      <match key="info.product"		contains="bcm5974">
        <merge key="appledevice"	type="bool">true</merge>
      </match>              
      
      <match key="appledevice"		bool="true">
        <merge key="input.x11_driver" 			type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig"	type="string">true</merge>
        <merge key="input.x11_options.TopEdge"		type="string">80</merge>
        <merge key="input.x11_options.BottomEdge"	type="string">720</merge>
        <merge key="input.x11_options.LeftEdge"		type="string">128</merge>
        <merge key="input.x11_options.RightEdge"	type="string">1152</merge>
        <merge key="input.x11_options.FingerLow"	type="string">16</merge>
        <merge key="input.x11_options.FingerHigh"	type="string">64</merge>
        <merge key="input.x11_options.FingerPress"	type="string">256</merge>
        <merge key="input.x11_options.TapButton1"	type="string">1</merge>
        <merge key="input.x11_options.TapButton2"	type="string">3</merge>
        <merge key="input.x11_options.TapButton3"	type="string">2</merge>
        <merge key="input.x11_options.MaxTapMove"	type="string">80</merge>
        <merge key="input.x11_options.MaxTapTime"	type="string">128</merge>
        <merge key="input.x11_options.MaxDoubleTapTime"	type="string">160</merge>
        <merge key="input.x11_options.ClickFinger1"	type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2"	type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3"	type="string">2</merge>
        <merge key="input.x11_options.PalmDetect"	type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth"	type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ"		type="string">200</merge>
        <merge key="input.x11_options.RTCornerButton"	type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton"	type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton"	type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton"	type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll"	type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll"	type="string">0</merge>
        <merge key="input.x11_options.HorizScrollDelta"	type="string">26</merge>
        <merge key="input.x11_options.VertScrollDelta"	type="string">16</merge>
        <merge key="input.x11_options.PressureMotionMinZ"	type="string">10</merge>
        <merge key="input.x11_options.VertTwoFingerScroll"	type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll"	type="string">1</merge>
        <merge key="input.x11_options.MinSpeed"		type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed"		type="string">1.6</merge>
        <merge key="input.x11_options.AccelFactor"	type="string">0.11</merge>
        <merge key="input.x11_options.CircularScrolling"	type="string">1</merge>
        <merge key="input.x11_options.CircScrollTrigger"	type="string">1</merge>
        <merge key="input.x11_options.CircScrollDelta"	type="string">0.3</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

> **volanin said:**
> I finally made the switch to Intrepid, and as always, here goes my personal
modifications to the touchpad driver, in order to improve the Ubuntu experience
for Apple users.

The packages attached replace the current touchpad driver in X.org and have
been improved over the original. They add cursor stabilization (the mouse
arrow no longer dances around when multiple fingers are pressed, just
like the MacOSX behaviour), and they improve the finger-click behaviour:
The mode of operation where two fingers on the touchpad + click generates
a right click.

Also attached here, is a fdi file to configure your touchpad to better
match the sensation of MacOSX (at least for my hardware). You can
always tweak the values based on your own preferences.

Copy the contents here to the file **/etc/hal/fdi/policy/appletouch.fdi**:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

Just download the attached deb corresponding to your architecture (i386 or amd64),
and after installing, restart X.org or reboot your computer.
Please, post your opinions here!
:)


_**Attention:**_

**1.** This driver has not been tested on the new multitouch touchpads,
but it has no reason not to work.

**2.** If you prefer, these files are also available from the Mactel PPA:
*deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main*

**_______**

---

### Post by N_Nick on 2009-03-16
Anyone else noticed a delay (about 1 second) when tapping to click?

Edit: Fixed it using gsynaptics.

---

### Post by cyberdork33 on 2009-03-16
so is gsynaptics getting installed by default now or something?

---

### Post by philcolbourn on 2009-03-17
> **cyberdork33 said:**
> so is gsynaptics getting installed by default now or something?

no. I installed it to set the touchpad settings and that is what it did - just took me a while to work it out.

---

### Post by .gurkburk on 2009-03-19
I installed 8.10 (inteprid...?) on my macbook unibody during the weekend, and couldnt get the touchpad to work properly. Ive read some posts/wiki-info about multi-tap for rightclick and 2finger-scroll working out-of-the box, but it did not for sure.
I also failed to get the keyboard to work (shortcuts for managing brightness etc, and light behind the keys).

I did get the keyboard to work perfectly when trying Jaunty briefly, and installing "pommed".

I havent been able to really test more since I had to return it and get a new one because of a pixel that I discovered was broken, but ill try some more later.

Im still not running ubuntu(or any linux dist) on it untill I can get the multitouchpad to work properly (meaning, double-tap for rightclick, 2finger scroll and 3finger back/forward function) like it does in macOS, I havent found anything indicating people getting this to work so im happily awaiting the release of jaunty and perhaps the mactel-projekt making a "breakthrough" :)

---

### Post by cyberdork33 on 2009-03-19
> **.gurkburk said:**
>  Im still not running ubuntu(or any linux dist) on it untill I can get the multitouchpad to work properly (meaning, double-tap for rightclick, 2finger scroll and 3finger back/forward function) like it does in macOS, I havent found anything indicating people getting this to work so im happily awaiting the release of jaunty and perhaps the mactel-projekt making a "breakthrough" :)
you have to use the patched bcm5794 driver in the mactel ppa.

Documentation for your Mac is here:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

---

### Post by .gurkburk on 2009-03-19
> **cyberdork33 said:**
> you have to use the patched bcm5794 driver in the mactel ppa.

Documentation for your Mac is here:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

I tried that in Jaunty but that was a failed attempt.
I havent had the oppertunity to do so in Intrepid, but I will probably do so in the weekend when I have more time.

---

### Post by cyberdork33 on 2009-03-19
> **.gurkburk said:**
> I tried that in Jaunty but that was a failed attempt.
I havent had the oppertunity to do so in Intrepid, but I will probably do so in the weekend when I have more time.
the package for jaunty was recently fixed. It should work now.

---

### Post by laney on 2009-03-20
> **cyberdork33 said:**
> the package for jaunty was recently fixed. It should work now.

Hi,

How do you mean "work"? I have this package installed and dropping policy files into the /etc/hal directory seems to have no effect. For example I cannot run any syn* program because they say that SHMConfig is not enabled. Do I have to do anything more?

---

### Post by inphektion on 2009-03-20
I have same issue.  I can get no policies to apply or act like they are being used and if i run synclient -l i get: 
```
Can't access shared memory area.  SHMConfig disabled?
```

---

### Post by cyberdork33 on 2009-03-20
> **laney said:**
> How do you mean "work"? as in, you can actually install it now.

> **laney said:**
> I have this package installed and dropping policy files into the /etc/hal directory seems to have no effect.
I have this issue as well, and I am not convinced it is related to this driver, but rather to synaptics.

> **laney said:**
> For example I cannot run any syn* program because they say that SHMConfig is not enabled. Do I have to do anything more?
That is a totally different issue. I don't even know that the SHMConfig option will even do anything if it is in the fdi file...

Please report on this bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

### Post by rfordh on 2009-04-29
> **zhark1 said:**
> It seems info.product doesn't match against appletouch or bcm5974.

I had to make this change (commenting out the lines starting with <match key="info.product" contains="appletouch">) as well to get this working on my MacBookPro 3,1 running Jaunty. Unfortunately though, I can only get right click when holding down *3 *fingers and holding down 2 fingers gives a middle click. I can't seem to switch this. I tried changing the lines:
```
<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
<merge key="input.x11_options.ClickFinger2" type="string">3</merge>
<merge key="input.x11_options.ClickFinger3" type="string">2</merge>
```
to
```
<merge key="input.x11_options.ClickFinger1" type="string">1</merge>
<merge key="input.x11_options.ClickFinger2" type="string">2</merge>
<merge key="input.x11_options.ClickFinger3" type="string">3</merge>
```
but nothing changed (even after a reboot).

Any idea on whats going on here?

Thanks!

Ford

---

### Post by __david on 2009-04-29
:mrgreen:

---

### Post by peterandrew011 on 2009-04-30
Nice job, , I am using this, Thanks for sharing this with us.

---

