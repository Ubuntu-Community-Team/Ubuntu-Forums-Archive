---
title: "MBP 4,1 | Intrepid | Software Update Messed My System!"
date: 2009-02-27
forum: Apple Hardware Users
---

### Post by brentgrunenberg on 2009-02-27
Hi All, 

I ran software update and had to stop it at some point before its completion, and let it install what it had dl'd so far (1st 1/3) bit since then:

1. I've lost my graphics driver. Even after I selected the Nvidia updates listed, dl'd them and installed them I still get:

- Hardware Drivers Menu --> Select Nvidia 177 driver, activate, --> get dling and installing window for one second, window vanishes and the driver is not activated. Even After three reboots! ...so  I have no graphics

2. I've for some reason lost horizontal scrolling (with two fingers on trackpad) which was working just fine before.

3. there seems to be no spellcheck library in OO Word Processor, but its there as I type in mozilla. 

4. My trackpad does not disable when im typing, which was fine before.

... If I finish the updates will these problems go away? Or has something gone wrong on a deeper level?

Thanks guys, dont know how anyone could get anywhere with  Linux without generous people like yourselves.

Thanks!

BG

---

### Post by deltaiscain on 2009-02-27
1. go to software update, and hit check, then when it finished checking, you don't have to hit install, go to the the drivers and hit activate, that will make it do it's thing.
2. go to system, preferences, mouse, and then the trackpad section, and enable horizontal scrolling
3. are you sure you have it enable to do so automatically? the abc and the checkmark symbol. Otherwise, go to the preferences and look there. Or to languages. 
4. i don't know anything about that. 

hope that helps

---

### Post by brentgrunenberg on 2009-02-27
Thanks for your response, though there are still a number of problems. 

1. When I did the check first and then the driver selection, it did the same thing... its simply not installing for some reason. it doesnt even try to download.  

2. Horizontal scrolling is (and was) enabled in mouse settings to no avail. 

3. AutoSpellCheck is enabled, but is not working. 

4. No Worries. 

Thanks again for your help!

BG

---

### Post by deltaiscain on 2009-02-28
1. hmm, this is strange. make sure you are connected to the internet. Open firefox and go to some page to check. Leave it open, just in case. Then go to software update again, and have it check. Leave software update open. Then go to the Hardware Drivers again, and double click on the 177 one, then click activate. i am 99% certain that should fix it, because it did that too, had the same problem at first. it will most likely open a windows with has a bar bouncing saying 0%. It will move eventually, and install. Be carefull that you don't download/install anything while it's doing this, or you'll have to hit activate again. 

2. hmm, i just checked and i can't either. will look into it and update

3. [IMG]http://farm4.static.flickr.com/3623/3316394926_1960af2da0.jpg?v=0[/IMG] it's that checkbox. And are you using the correct language? tools language

---

### Post by deltaiscain on 2009-02-28
1. You can also try the checking thing, and then right click on your desktop and click change desktop background, and then go to visual effects and enable normal of extra. This should also activate the driver. 

2. Fixed it :)
You need to have the bcm5974 trackpad package installed, and the xfree86 package. [link to both files]("https://launchpad.net/~mactel-support/+archive/ppa")
Then open terminal, and type: ```
sudo nautilus
``` Then go to file system, then etc, then hal, then fdi, then policy, and then copy and paste the preferences file. With the new one, rename it, and call it bcm5974.fdi. 
then open it in text editor, and replace everything with this:
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
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
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
        <merge key="input.x11_options.VertScrollDelta" type="string">15</merge>
	<merge key="input.x11_options.HorizScrollDelta" type="string">15</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.LockedDragTimeout" type="string">1</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>
```
This will enable horizontal scroll, plus tap to click. With this, you can totally change what your trackpad does. To learn what stuff does, or change stuff, go to terminal, and type ```
man synaptics
```
when you replaced it, or modified it, close the file, close the file browser, and then type: ```
sudo modprobe -r bcm5974 && sudo modprobe bcm5974
```
then, all your settings have been applied, and it should work.

---

### Post by cyberdork33 on 2009-02-28
yes the bcm driver is the actual kernel driver that makes the hardware function. the other driver is the xorg "translator" that maps the hardware information to GUI control inputs.

---

### Post by brentgrunenberg on 2009-02-28
Thanks for all your help people! Really appreciate it! All is well now!

BG

---

### Post by deltaiscain on 2009-02-28
no problem! ;)

---

