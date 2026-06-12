---
title: "Installing kubuntu 9.04 on a macbook pro 5,5"
date: 2009-09-22
forum: Apple Hardware Users
---

### Post by lviggiani on 2009-09-22
Hi, has anyone successfully installed and configured kubuntu 9.04 on a macbook 5,5?
I did the installation on an external usb drive and I can run it and boot via rEFIt (a little bit slow to boot, but good as test).

I also installed nvidia-glx-185. I have good performance with kde4 comprising effects etc.
Everithing seems to work fine except for the display and keyb backlit even after installing stuff from mactel ppa.
Display is always at 100%. F1 / F2 don't work.
When I try to dim it from the power manager widget, it changes the keyboard backlit intensity instead.
F5 and F6 don't work as well.
Finally I couldn't properly configure the trackpad. I can't get two fingers scrolling or right click as well as single touch click.
Can some one help me please?

---

### Post by buntuLo on 2009-09-22
> **lviggiani said:**
> Everithing seems to work fine except for the display and keyb backlit even after installing stuff from mactel ppa.
which stuff did you install exactly? are you using the Gnome Power Manager?

---

### Post by lviggiani on 2009-09-23
> **buntuLo said:**
> which stuff did you install exactly? are you using the Gnome Power Manager?

I installed the followings:

nvidia-bl-dkms
applesmc-dkms
hal-applesmc
bcm5974-dkms
pommed

accordingto this
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

I'm not using gnome power manager. I'm using kde4 default power manager widget.

---

### Post by buntuLo on 2009-09-23
> **lviggiani said:**
> I'm not using gnome power manager. I'm using kde4 default power manager widget.
i'm still running intrepid (8.10): for that, only the Gnome PM has been patched, not the KDE one. i know it is not an elegant solution, but it works perfectly. 
i cannot guarantee that the situation is still the same in jaunty and karmic alphas..

---

### Post by lviggiani on 2009-09-23
> **buntuLo said:**
> i'm still running intrepid (8.10): for that, only the Gnome PM has been patched, not the KDE one. i know it is not an elegant solution, but it works perfectly. 
i cannot guarantee that the situation is still the same in jaunty and karmic alphas..

Ok, thanks!
That was my suspect as I saw a patched version of gnome power manager in mactel ppa...
I'll try to use it. So, if I understand, I just have to remove the kde pm from the panel and use gnome one...
How can I run it? I guess it has to be run as super user and automatically started at login... correct?

Finally, could you properly configure the trackpad with two fingers scroll, single touch click etc?
Thanks again for your help.

---

### Post by buntuLo on 2009-09-23
> **lviggiani said:**
> So, if I understand, I just have to remove the kde pm from the panel and use gnome one...
How can I run it? I guess it has to be run as super user and automatically started at login... correct?
i used apt-get to uninstall the KDE PM, and install the (patched) Gnome one. the installation takes care of everything, you'll have it running at the next reboot.
> **lviggiani said:**
> Finally, could you properly configure the trackpad with two fingers scroll, single touch click etc?
yes, i configured it as explained in the MacbookPro51/Intrepid [_page_]("https://help.ubuntu.com/community/MacBook5-1/Intrepid"). what exactly did not work following the instructions for MacbookPro55/Jaunty [_here_]("https://help.ubuntu.com/community/MacBookPro5-5/Jaunty")? i see that the given example disables tapping:```
TapButtonX" type="string">0</merge>
```you can enable tapping setting the value to 1.
instead vert/horiz scrolling with two fingers is enabled..
hope this helps. Lo.

---

### Post by lviggiani on 2009-09-23
> **buntuLo said:**
> i used apt-get to uninstall the KDE PM, and install the (patched) Gnome one. the installation takes care of everything, you'll have it running at the next reboot.

yes, i configured it as explained in the MacbookPro51/Intrepid [_page_]("https://help.ubuntu.com/community/MacBook5-1/Intrepid"). what exactly did not work following the instructions for MacbookPro55/Jaunty [_here_]("https://help.ubuntu.com/community/MacBookPro5-5/Jaunty")? i see that the given example disables tapping:```
TapButtonX" type="string">0</merge>
```you can enable tapping setting the value to 1.
instead vert/horiz scrolling with two fingers is enabled..
hope this helps. Lo.

Thank you very much again! I'll try this evening and let you know... :)

---

### Post by lviggiani on 2009-09-24
Ok, I did few progress...

First of all, I discovered that MBP 5,5 need latest pommed 1,28.
I could download deb from here:

[http://packages.debian.org/sid/i386/pommed/download](http://packages.debian.org/sid/i386/pommed/download)

and here are the dependencies:

[http://packages.debian.org/sid/i386/libpci3/download](http://packages.debian.org/sid/i386/libpci3/download)
[http://packages.debian.org/sid/i386/pciutils/download](http://packages.debian.org/sid/i386/pciutils/download)

After installing it, F5/F6 work perfectly as well as the light sensor which automatically lights the keyboard up in lowlight conditions! And for this it seems that I don't actually need patched gnome-power-manager.

What still doesn't work are F1/F2 keys... the LCD is always at 100% :(
I tried installing nvidia-bl-dmks and mbp-nvidia-bl-dmks but nothing changes.

Still no luck with the track-pad... :(

So, the situation is:

Keyboard back-lit: OK (comprising light sensor)
LCD lightness: not working
Trackpad: no tapping, scrolling etc.

---

### Post by buntuLo on 2009-09-24
> **lviggiani said:**
> First of all, I discovered that MBP 5,5 need latest pommed 1,28.
i thought pommed was deprecated... ::confusion::
where did you find this info?
> **lviggiani said:**
> Keyboard back-lit: OK (comprising light sensor)
good to hear it! and the behaviour as controlled by the light sensor is reasonable? is there any tuning of the light sensitivity in pommed?
> **lviggiani said:**
> LCD lightness: not working
gnome-power-manager needed for the brightness f-keys to work:~( but if you do a search on the forum (sorry, don't have these infos with me right now), you should find also terminal commands to set the brightness.
> **lviggiani said:**
> Trackpad: no tapping, scrolling etc.
what's the problem with the touchpad? got any errors? did you follow every step from the wiki page, and did any of them fail?
ciao, Lo.

---

### Post by lviggiani on 2009-09-24
> **buntuLo said:**
> i thought pommed was deprecated... ::confusion::
where did you find this info?

good to hear it! and the behaviour as controlled by the light sensor is reasonable? is there any tuning of the light sensitivity in pommed?

gnome-power-manager needed for the brightness f-keys to work:~( but if you do a search on the forum (sorry, don't have these infos with me right now), you should find also terminal commands to set the brightness.

what's the problem with the touchpad? got any errors? did you follow every step from the wiki page, and did any of them fail?
ciao, Lo.

Well I didn't hear about pommed being deprecated... anyway, I went to the pommed web site and checked the release date for v2.26 (version that is on mactel ppa) which is prior to macbook 5,5 release date. I then checked latest version 1,28 and I saw on change log that they added support to 5,5 series (already in 1,27).

About gnome-power-manger, the only difference by having it or not on 5,5 is that it displays the popup progress bar while changing keyb / LCD intensity.
In both cases, keyb behaves the same, LCD don't work.

About trackpad, I followed this tutorial:
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

---

### Post by buntuLo on 2009-09-24
> **lviggiani said:**
> Well I didn't hear about pommed being deprecated... anyway, I went to the pommed web site and checked the release date for v2.26 (version that is on mactel ppa) which is prior to macbook 5,5 release date. I then checked latest version 1,28 and I saw on change log that they added support to 5,5 series (already in 1,27).
i see. with intrepid, i managed to get almost everything working without the use of pommed. i will give it a try in karmic.
> **lviggiani said:**
> About gnome-power-manger, the only difference by having it or not on 5,5 is that it displays the popup progress bar while changing keyb / LCD intensity.
In both cases, keyb behaves the same, LCD don't work.
if i'm not wrong, getting the display indication of lcd brightness in KDE was a matter of properly configuring the keyboard in the settings panel. but it did not work to actually change the brightness on intrepid. i hope some of the developers who patched the previous drivers will be able to help you.
> **lviggiani said:**
> About trackpad, I followed this tutorial:
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)
you followed that, and checked back that all the described changes were done properly? does it behave any different from before the changes?
you said that you cannot scroll with two fingers, and you cannot tap with one or two fingers. correct? please also post the configuration file you edited.

---

### Post by lviggiani on 2009-09-24
> **buntuLo said:**
> i see. with intrepid, i managed to get almost everything working without the use of pommed. i will give it a try in karmic.

if i'm not wrong, getting the display indication of lcd brightness in KDE was a matter of properly configuring the keyboard in the settings panel. but it did not work to actually change the brightness on intrepid. i hope some of the developers who patched the previous drivers will be able to help you.

you followed that, and checked back that all the described changes were done properly? does it behave any different from before the changes?
you said that you cannot scroll with two fingers, and you cannot tap with one or two fingers. correct? please also post the configuration file you edited.


Hi, this is the file saved as 

/etc/hal/fdi/policy/x11-synaptics-bcm5974.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
   <match key="info.product" contains="bcm5974">
   <merge key="appledevice" type="bool">true</merge>
   </match>
  
   <match key="appledevice" bool="true">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.FingerLow" type="string">40</merge>
        <merge key="input.x11_options.FingerHigh" type="string">70</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">25</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">250</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

---

### Post by lviggiani on 2009-09-24
UPDATE:

I installed nvidia-bl-dmks (mbp-nvidia-bl-dmks doesn't work) and added nvidia_bl to /etc/modules and now with gnome-power-manager I can finally change the LCD brightness!!!!!

Sadly gnome-power-manager does not start automatically... where can I add a startup script in order to have it automatically started in super user mode?

I kept pommed 1.28 as it uses the light sensor to automatically light up the keyb in low light conditions.

So now I only have to solve the track pad issue and I'll be ready to fully enjoy my MBP!!!! :)

---

### Post by ALLurGroceries on 2009-09-24
Hello,

I've started a howto guide here for the MBP 5,5 on Debian Sid AMD64 but it's also relevant to Ubuntu:
[http://forum.notebookreview.com/showthread.php?t=418403]("http://forum.notebookreview.com/showthread.php?t=418403")

There's a patch for click and drag on the touchpad that might be what you're looking for.

Any feedback on the howto guide is appreciated since I've only just started it.

Cheers.

Edit: Added some of the info from this thread to the guide. :)

---

### Post by buntuLo on 2009-09-24
> **lviggiani said:**
> UPDATE:
I installed nvidia-bl-dmks (mbp-nvidia-bl-dmks doesn't work) and added nvidia_bl to /etc/modules and now with gnome-power-manager I can finally change the LCD brightness!!!!!
happy to hear that!
> **lviggiani said:**
> Sadly gnome-power-manager does not start automatically... where can I add a startup script in order to have it automatically started in super user mode?
k>computer>settings>advanced>autostart
but i did not need to add it..
> **lviggiani said:**
> <merge key="input.x11_options.SHMConfig" type="string">1</merge>
only two differences (apart from the values): the boolean assigned to SHMConfig (you have 1, while i have True), and the name of the file, which in my case is 11-x11-synaptics.fdi. i guess neither makes any difference..

---

### Post by lviggiani on 2009-09-26
@ buntuLo:
By adding it like you said it seems not starting... are you sure that things added there are started in super user mode?

Anyway, I noticed that by switching to tty1, keyb and lcd backlit control works without gnome-power-manager (which in any case does not work in tty1 mode).
So, I'm wondering if there is something running in kde which interfere with pommed. How did you uninstall kde power management system? I mean which package is to be removed?

@ALLurGroceries:
I have followed your useful howto but I still can't get the features I want from my trackpad. I don't know where to look further... is xorg.conf involved in any way?

---

### Post by ALLurGroceries on 2009-09-26
> **lviggiani said:**
> @ALLurGroceries:
I have followed your useful howto but I still can't get the features I want from my trackpad. I don't know where to look further... is xorg.conf involved in any way?

No, xorg has nothing but the defaults in it for my input section. It looks like this:

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

```

It might have something to do with package versions, I'm on Debian Sid:
```
Package: xserver-xorg-input-synaptics
Version: 1.1.2-1

Package: xserver-xorg-core
Version: 2:1.6.3.901-1

Package: hal
Version: 0.5.13-3
```

That patch I mentioned only enables click and drag, it doesn't do anything for two finger scrolling or two finger right click, three finger 3rd mouse button. Those functions worked for me after creating the .fdi file and restarting HAL.

---

### Post by buntuLo on 2009-09-28
> **lviggiani said:**
> @ buntuLo:
By adding it like you said it seems not starting... are you sure that things added there are started in super user mode?
no, i think they're not.
> **lviggiani said:**
> Anyway, I noticed that by switching to tty1, keyb and lcd backlit control works without gnome-power-manager (which in any case does not work in tty1 mode). So, I'm wondering if there is something running in kde which interfere with pommed. How did you uninstall kde power management system? I mean which package is to be removed?
you need to remove the package guidance-power-manager. you can run:
```
sudo apt-get remove --purge guidance-power-manager
```
to delete all its config files, and
```
sudo apt-get autoremove
```
to remove all packages that are no more needed, possible dependencies of whatever you remove.
after this, i installed gnome-power-manager and got it starting up at the next login.

---

### Post by lviggiani on 2009-10-02
> **buntuLo said:**
> no, i think they're not.

you need to remove the package guidance-power-manager. you can run:
```
sudo apt-get remove --purge guidance-power-manager
```
to delete all its config files, and
```
sudo apt-get autoremove
```
to remove all packages that are no more needed, possible dependencies of whatever you remove.
after this, i installed gnome-power-manager and got it starting up at the next login.

Well that's the point...
guidance-power-manager is not installed in kde4...

---

### Post by buntuLo on 2009-10-03
> **lviggiani said:**
> Well that's the point...
guidance-power-manager is not installed in kde4...
kde 4.1 under intrepid ibex, g-p-m was here. if you got only the battery status widget, i would guess it shouldn't interfere..
which power manager do you have?

---

