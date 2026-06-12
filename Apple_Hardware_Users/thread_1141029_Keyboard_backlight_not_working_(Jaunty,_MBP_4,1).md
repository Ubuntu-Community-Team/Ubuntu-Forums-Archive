---
title: "Keyboard backlight not working (Jaunty, MBP 4,1)"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by __david on 2009-04-28
Did anybody get the keyboard backlight to work on a MBP 4,1 with Jaunty?

It works using pommed, but not with HAL. *notify-osd* shows a notification with a blinking progress bar (on keypress). The bar does show that the backlight level remains at 0. At least that’s in sync with the backlight.

Thanks in advance,
David

---

### Post by maffix on 2009-04-28
I have the same issue like you, and I don't understand why the widget's  backlight appears on the screen but any functions works.

Another thing: if I open a terminal and write dmesg, I got this result:

```
 applesmc: Apple MacBook Pro 4 detected:
[   11.637704] applesmc:  - Model with accelerometer
[   11.637706] applesmc:  - Model with light sensors and backlight
[   11.637707] applesmc:  - Model with 12 temperature sensors
[   11.638963] applesmc: device has already been initialized (0xe0, 0xf8).
[   11.638965] applesmc: device successfully initialized.
[   11.639650] applesmc: 2 fans found.
[   11.641723] input: applesmc as /devices/platform/applesmc.768/input/input10
[   11.668311] Registered led device: smc::kbd_backlight
[   11.668326] applesmc: driver successfully loaded.

```

but when I press F6 or F5 the command "dmesg" got me this result:

```
applesmc: wait status failed: 4 != 0

```

Thanks a lot for advice!:)

---

### Post by maffix on 2009-04-28
**_Solved partially!_**

For now there's only manual solution and worked for me.
You have to open a terminal and write this to make backlight max (value switch to 0 for no backlight and 255 for maximum backlight):

```
$ echo 255 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness

```
 
for max

```
$ echo 0 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness
```


for zero backlight. You can choose the right value for 0 to 255.

Until the Mactel PPA project resolves the problem relative to hal-applesmc,
that is the only way!

[HTML]The function keys do not control this yet, I believe we are waiting for hal-applesmc to be built for Jaunty[/HTML]

link: [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty")

---

### Post by undertakingyou on 2009-05-06
So, is does anyone know when the hal-applesmc package will be built? I can't find any timeline anyplace.

---

### Post by cyberdork33 on 2009-05-07
> **undertakingyou said:**
> So, is does anyone know when the hal-applesmc package will be built? I can't find any timeline anyplace.
as soon as someone decides to do it.

---

### Post by hajk on 2009-05-07
The interesting thing is that there has been a regression of sorts with MBP 4,1 screen and keyboard backlighting... While the new apple macintel-related modules in the 2.6.28/29 kernels are a great step forward in hardware recognition in general, there have been a few problems introduced for some of the hardware involved on the MBP 4,1. These things take a little time to sort out, so I'm looking forward to trying a 2.6.30 kernel soon.:)

---

### Post by undertakingyou on 2009-05-07
> **cyberdork33 said:**
> as soon as someone decides to do it.

I wish I was smart enough to do it.
In the meantime I have installed the hal-applesmc package for intrepid and it is working fine on my MBP 3,1.

Thanks.

---

### Post by inphektion on 2009-05-07
> **cyberdork33 said:**
> as soon as someone decides to do it.

which means don't hold your breath...


> **hajk said:**
> The interesting thing is that there has been a regression of sorts with MBP 4,1 screen and keyboard backlighting... While the new apple macintel-related modules in the 2.6.28/29 kernels are a great step forward in hardware recognition in general, there have been a few problems introduced for some of the hardware involved on the MBP 4,1. These things take a little time to sort out, so I'm looking forward to trying a 2.6.30 kernel soon.:)

My opinion/theory is that people(mactel ppa) were waiting to see how the new kernel support did on this hardware.  As you said seems better than the other kernels but still doesn't give out of the box functionality.  To get that unfortuneatley we still have to rely on a PPA (hal-applesmc, etc.) and it doens't seem like the original author is willing to update it so we need to wait for someone else to kindly step in or wait even longer and hope for better out of the box support in karmic koala...

---

### Post by cyberdork33 on 2009-05-07
> **inphektion said:**
> which means don't hold your breath...




My opinion/theory is that people(mactel ppa) were waiting to see how the new kernel support did on this hardware.  As you said seems better than the other kernels but still doesn't give out of the box functionality.  To get that unfortuneatley we still have to rely on a PPA (hal-applesmc, etc.) and it doens't seem like the original author is willing to update it so we need to wait for someone else to kindly step in or wait even longer and hope for better out of the box support in karmic koala...
the main developer that was working the ppa is not returning until karmic. Most of the other packages got updated, but hal-applesmc got skipped for some reason.

Try this:
[https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra](https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra)

---

### Post by inphektion on 2009-05-08
> **cyberdork33 said:**
> 
Try this:
[https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra](https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra)

I'm scared how happy that just made me.  Working in my dimly lit dining room, installed that package, reboot, and right on login the keyboard lit up!

Fn keys control it perfectly.  Guess I need to start diggin through random PPA's more often.  Any chance of that going into the mactelppa?

Thanks a lot.

---

### Post by cyberdork33 on 2009-05-08
> **inphektion said:**
> I'm scared how happy that just made me.  Working in my dimly lit dining room, installed that package, reboot, and right on login the keyboard lit up!

Fn keys control it perfectly.  Guess I need to start diggin through random PPA's more often.  Any chance of that going into the mactelppa?

Thanks a lot.
I had asked this guy to put it in, but it might have been overlooked. I'll try again.

---

### Post by inphektion on 2009-05-08
Though it works perfectly, today when I booted up in a brightly lit office environment the keyboard backlit still came on full.
I know if I boot the mac os I think it uses an ambient light sensor to determine that.  
It doesn't seem that is being used now or maybe I need to configure this somewhere?  
Even if i can set it to off by default and turn it on with fn keys when needed that is fine.

---

### Post by cyberdork33 on 2009-05-08
> **inphektion said:**
> Though it works perfectly, today when I booted up in a brightly lit office environment the keyboard backlit still came on full.
I know if I boot the mac os I think it uses an ambient light sensor to determine that.  
It doesn't seem that is being used now or maybe I need to configure this somewhere?  
Even if i can set it to off by default and turn it on with fn keys when needed that is fine.
I don't think that was working correctly before. I think the problem is that is always gets reset to full. There were some scripts posted that would save the brightness state, and then restore it again later. Might search for that.

---

### Post by inphektion on 2009-05-08
I searched a bit... 

if we come here:
/usr/share/hal/fdi/policy/10osvendor
and look at the 10-macbookpro-utils.fdi file
mine looks like this:
```

<?xml version="1.0" encoding="UTF-8"?>


<deviceinfo version="0.2">
  <!-- this is for Macbook Pro (LCD panel, light sensor, keyboard backlight) -->
  <device>
    <match key="system.kernel.name" string="Linux">
      <match key="system.hardware.vendor" contains="Apple">
        <match key="system.hardware.product" string_outof="MacBookPro1,1;MacBookPro1,2;MacBookPro2,1;MacBookPro2,2;MacBookPro3,1;MacBookPro3,2;MacBookPro4,1">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_pro_light_sensor"/>
          <spawn udi="/org/freedesktop/Hal/devices/macbook_pro_keyboard_backlight"/>
	</match>
        <match key="system.hardware.product" string_outof="MacBookPro1,1;MacBookPro1,2;MacBookPro2,1;MacBookPro2,2">
          <spawn udi="/org/freedesktop/Hal/devices/macbook_pro_lcd_panel"/>
        </match>
      </match>
    </match>
  </device>
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/macbook_pro_lcd_panel">
      <append key="info.capabilities" type="strlist">laptop_panel</append>
      <merge key="info.category" type="string">laptop_panel</merge>
      <merge key="info.product" type="string">MacBook Pro Laptop Panel</merge>
      <merge key="laptop_panel.access_method" type="string">custom</merge>
      <merge key="laptop_panel.num_levels" type="int">229</merge>
      <append key="info.addons" type="strlist">hald-addon-macbookpro-backlight</append>
    </match>
  </device>
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/macbook_pro_light_sensor">
      <append key="info.capabilities" type="strlist">light_sensor</append>
      <merge key="info.product" type="string">MacBook Pro Light Sensor</merge>
      <merge key="light_sensor.num_sensors" type="int">2</merge>
      <merge key="light_sensor.num_levels" type="int">256</merge>
      <append key="light_sensor.sensor_locations" type="strlist">right</append>
      <append key="light_sensor.sensor_locations" type="strlist">left</append>
    </match>
  </device>
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/macbook_pro_keyboard_backlight">
      <append key="info.capabilities" type="strlist">keyboard_backlight</append>
      <merge key="info.product" type="string">MacBook Pro Keyboard Backlight</merge>
      <merge key="keyboard_backlight.num_levels" type="int">256</merge>
    </match>
  </device>

</deviceinfo>


```

I noticed there is no system.hardware.product string for MacBookPro5,1 or MacBookPro5,2, so I added myself and rebooted and now the keyboard backlight doesn't come on at all even though the function key has it at max.  

But it seems a correctly configured .fdi file could set these values correctly based on readings from the light sensors.  

Currently it seems to be just coming on MAX all the time.  even when I turn it down if my machine's power state changes it kicks back on max.  

What is also weird now that I have hal-applesmc installed is seemingly after x amound of time my lcd screen will go from max brightness to about 60%.  

I'd love to troubleshoot this further just would need maybe the dev who did hal-applesmc or someone who know the interaction of hal and the .fdi files to help me out.

---

### Post by cyberdork33 on 2009-05-08
> **inphektion said:**
>  What is also weird now that I have hal-applesmc installed is seemingly after x amound of time my lcd screen will go from max brightness to about 60%.  

I think that is the dimming feature... it should go back to what it was when you move the mouse, but it has been broken before...

[quote=inphektion;7240021] I'd love to troubleshoot this further just would need maybe the dev who did hal-applesmc or someone who know the interaction of hal and the .fdi files to help me out.

you can send email to the mactel-support mailing list:
[https://edge.launchpad.net/~mactel-support](https://edge.launchpad.net/~mactel-support)

---

### Post by josue on 2010-03-09
> **cyberdork33 said:**
> the main developer that was working the ppa is not returning until karmic. Most of the other packages got updated, but hal-applesmc got skipped for some reason.

Try this:
[https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra](https://edge.launchpad.net/%7Eadamhorden/+archive/ppa/+sourcepub/523564/+listing-archive-extra)


Sorry, I have been trying to install that diff for the past two days and can't figure it out. Any hints as to how to apply this -assumed- patch to hal-applesmc?

---

