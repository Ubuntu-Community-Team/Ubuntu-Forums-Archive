---
title: "[SOLVED] How to configure screen and keyboard backlight in Intrepid?"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-11-08
I'm running the 8.10 release on a MBP 4,1 Penryn. Both the keyboard and screen backlight controls work, and the intensity is manually adjustable by appropriate hotkeys (F1-F2 and F5-F6).

Is there a way to change the default settings? The keyboard backlight is always set on, even when on battery. Of course I can manually turn it off using the appropriate key, but I'd like an automatic setup.

Related question: Under OS X the keyboard backlight only comes on when the sensors suggest it is needed, which is pretty nice. Anybody know a way to configure such behaviour in Intrepid?

---

### Post by _mario_ on 2008-11-08
Hi,

> **hyperboloid said:**
> I'm running the 8.10 release on a MBP 4,1 Penryn. Both the keyboard and screen backlight controls work, and the intensity is manually adjustable by appropriate hotkeys (F1-F2 and F5-F6).


a few weeks ago, we were happy that this worked at all ... an now this question ... ;-)

> **hyperboloid said:**
> 
Is there a way to change the default settings? The keyboard backlight is always set on, even when on battery. Of course I can manually turn it off using the appropriate key, but I'd like an automatic setup.

as far as i know, there's no user interface yet, but you can use:
```
gconftool-2 -t int -s /apps/gnome-power-manager/keyboard/brightness_ac 0
gconftool-2 -t int -s /apps/gnome-power-manager/keyboard/brightness_battery 0

```
or gconf-editor. the values are in %.

> **hyperboloid said:**
> 
Related question: Under OS X the keyboard backlight only comes on when the sensors suggest it is needed, which is pretty nice. Anybody know a way to configure such behaviour in Intrepid?

pommed had this feature, but is somewhat deprecated as of Intrepid ...

ciao,
Mario

---

### Post by hyperboloid on 2008-11-08
> **_mario_ said:**
> 
as far as i know, there's no user interface yet, but you can use:
```
gconftool-2 -t int -s /apps/gnome-power-manager/keyboard/brightness_ac 0
gconftool-2 -t int -s /apps/gnome-power-manager/keyboard/brightness_battery 0

```
or gconf-editor. the values are in %.

Thanks, Mario, this works for the current session but if I restart X the pesky keyboard backlight is turned on again, damnit. The values remain unchanged at 0 in /apps/gnome-power-manager/keyboard, but still the backlight comes on. Any idea what's up with that? 

> **_mario_ said:**
> 
pommed had this feature, but is somewhat deprecated as of Intrepid ...

Why deprecated? Ambient sensing control seems like something people would want, and since it was working in pommed, this may be a step backwards? (On the other hand, I'm pleased that the backlight works at all, so don't get me wrong here.)

---

### Post by cyberdork33 on 2008-11-08
> **hyperboloid said:**
> Why deprecated? Ambient sensing control seems like something people would want, and since it was working in pommed, this may be a step backwards? (On the other hand, I'm pleased that the backlight works at all, so don't get me wrong here.)
pommed is depreciated because proper support for the hardware has been migrating to where it should be instead of a separate utility. (i.e. getting closer to "just works") Because of this, pommed now conflicts.

---

### Post by hyperboloid on 2008-11-09
> **cyberdork33 said:**
> pommed is depreciated because proper support for the hardware has been migrating to where it should be instead of a separate utility. (i.e. getting closer to "just works") Because of this, pommed now conflicts.

OK, I misunderstood. Fair enough point about pommed, but one still would like to be able to use the ambient light sensors on a MBP 4,1 for their intended purpose. As I understand it this was working just fine some time ago in pommed. Are there any plans to support this feature at all with the new approach?

---

### Post by kosumi68 on 2008-11-09
> **hyperboloid said:**
> OK, I misunderstood. Fair enough point about pommed, but one still would like to be able to use the ambient light sensors on a MBP 4,1 for their intended purpose. As I understand it this was working just fine some time ago in pommed. Are there any plans to support this feature at all with the new approach?

If you feel like experimenting, you can uncomment the light_sensor settings in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi. It should make gnome-power-manager aware of the light_sensor, and start using it. The reason it is commented out is that the behavior had issues before, and I have not looked further into it. If you would get it work, please report :-)

---

### Post by undertakingyou on 2008-11-09
I'd love to try out the light sensors with my 3rd gen MBP, but I don't have a 10-applesmc.fdi file.  Is there somewhere else that this is stored?

---

### Post by kosumi68 on 2008-11-09
> **undertakingyou said:**
> I'd love to try out the light sensors with my 3rd gen MBP, but I don't have a 10-applesmc.fdi file.  Is there somewhere else that this is stored?

It is in the hal-applesmc package in the mactel PPA: [https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by hyperboloid on 2008-11-09
> **kosumi68 said:**
> If you feel like experimenting, you can uncomment the light_sensor settings in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi. It should make gnome-power-manager aware of the light_sensor, and start using it. The reason it is commented out is that the behavior had issues before, and I have not looked further into it. If you would get it work, please report :-)

OK, Kosumi, thanks. I have uncommented the relevant section. Will see what happens and report back in this thread.

---

### Post by undertakingyou on 2008-11-09
So, I had to remove the applesmc-dmks package and then reinstall the hal-applesmc package to even have the 10-applesmc.fdi.  So, I uncommented the two sections for sensors but I still have no keyboard backlight at all.  Is there something that I am missing?  The applesmc module is loaded, and I now have the ability to change the monitor brightness.  

Another side issue, the screen now auto-dims and goes blank. I went into gconf-editor and told it not to auto-dim, but it still does.  Any thoughts as to why?

---

### Post by hyperboloid on 2008-11-09
> **kosumi68 said:**
> If you feel like experimenting, you can uncomment the light_sensor settings in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi. It should make gnome-power-manager aware of the light_sensor, and start using it. The reason it is commented out is that the behavior had issues before, and I have not looked further into it. If you would get it work, please report :-)

REPORT: 

1. If the keyboard backlight is off, it does not automatically turn itself on when I darken the room. So it seems that part doesn't work. Maybe there are ways to tweak the settings?

2. On the other hand, the screen seems to dim a bit automatically when I switch to battery, and automatically increase when I plug in the power cord. Can't recall if this behavior existed before. 

3. On a positive note, my system is now correctly remembering the previously set keyboard brightness, even after a reboot or suspend! So uncommenting that code seems to have fixed the problem reported at the end of this thread:  [http://ubuntuforums.org/showthread.php?p=6141769#post6141769]("http://ubuntuforums.org/showthread.php?p=6141769#post6141769"). Very strange.
[EDIT: The previous value is NOT remembered. Instead, the keyboard backlight is turned off on each boot/suspend, regardless of the previously setting.]

---

### Post by cyberdork33 on 2008-11-10
> **hyperboloid said:**
> 2. On the other hand, the screen seems to dim a bit automatically when I switch to battery, and automatically increase when I plug in the power cord. Can't recall if this behavior existed before. 
I am pretty sure that is a separate function.

---

### Post by kosumi68 on 2008-11-10
Yes, the AC/Battery switch is separate. If you cover the light sensors at the top of the screen with your hand, the LCD brightness (and possibly the keyboard) should dim down. Regarding remembering the keyboard brightness, I have a hard time thinking the switching on of the light_sensor can affect that. Please check again by commenting out the light_sensor settings and see if it still works. :-)

---

### Post by undertakingyou on 2008-11-10
So, following all of the suggestions given here I still got no keyboard backlighting at all.  Regardless of what I set anything to in gconf or what I comment/uncomment in the .fdi file.  

I have a MacBookPro 3,1 and the applesmc module and the mbp_nvidia_bl module are both loaded.  I also have the mactel g-p-m and the mactel hal-applesmc installed.

Is there something else that I need to do in order to get the keyboard backlight working?

---

### Post by hyperboloid on 2008-11-10
> **kosumi68 said:**
> Yes, the AC/Battery switch is separate. If you cover the light sensors at the top of the screen with your hand, the LCD brightness (and possibly the keyboard) should dim down. Regarding remembering the keyboard brightness, I have a hard time thinking the switching on of the light_sensor can affect that. Please check again by commenting out the light_sensor settings and see if it still works. :-)

In that case, it is NOT working at all. Covering up the sensors with my hand had no effect on display backlight or keyboard backlight. 

The keyboard backlight is turned off on suspend/reboot when the code is uncommented, and when I revert back to the original fdi file I'm getting the backlight turned on (fully) after each suspend/resume.

---

### Post by kosumi68 on 2008-11-10
Two things to check after rebooting:
```

hal-find-by-capability --capability keyboard_backlight

```
```

hal-find-by-capability --capability light_sensor

```

---

### Post by undertakingyou on 2008-11-10
will@will-laptop:~$ hal-find-by-capability --capability keyboard_backlight
/org/freedesktop/Hal/devices/macbook_pro_keyboard_backlight
/org/freedesktop/Hal/devices/applesmc_keyboard_backlight
will@will-laptop:~$ hal-find-by-capability --capability light_sensor
/org/freedesktop/Hal/devices/macbook_pro_light_sensor
/org/freedesktop/Hal/devices/applesmc_light_sensor

So I get output that says that I should get some backlight.  Anyway to try and force the backlight level to see if I can get anything at all?

---

### Post by hyperboloid on 2008-11-10
> **kosumi68 said:**
> Two things to check after rebooting:
```

hal-find-by-capability --capability keyboard_backlight

```
```

hal-find-by-capability --capability light_sensor

```

OK, here you are:
```

me@laptop:~$ hal-find-by-capability --capability keyboard_backlight
/org/freedesktop/Hal/devices/applesmc_keyboard_backlight
me@laptop:~$ hal-find-by-capability --capability light_sensor
/org/freedesktop/Hal/devices/applesmc_light_sensor
me@laptop:~$ 

```

My /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi looks like this:
```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

  <device>
    <match key="platform.id" contains="applesmc">
     <spawn udi="/org/freedesktop/Hal/devices/applesmc_keyboard_backlight"/>

     <spawn udi="/org/freedesktop/Hal/devices/applesmc_light_sensor"/>

    </match>
  </device>

  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/applesmc_keyboard_backlight">
      <append key="info.capabilities" type="strlist">keyboard_backlight</append>
      <merge key="info.product" type="string">Applesmc Keyboard Backlight</merge>
      <merge key="keyboard_backlight.num_levels" type="int">256</merge>
      <merge key="keyboard_backlight.access_method" type="string">custom</merge>
      <merge key="linux.sysfs_path" type="string">/sys/class/leds/smc::kbd_backlight</merge>
      <append key="info.addons" type="strlist">hald-addon-generic-kbd-backlight</append>
    </match>
  </device>


  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/applesmc_light_sensor">
      <append key="info.capabilities" type="strlist">light_sensor</append>
      <merge key="info.product" type="string">Applesmc Light Sensor</merge>
      <merge key="light_sensor.num_sensors" type="int">1</merge>
      <merge key="light_sensor.num_levels" type="int">64</merge>
      <append key="light_sensor.sensor_locations" type="strlist">left</append>
      <merge key="light_sensor.access_method" type="string">custom</merge>
      <merge key="linux.sysfs_path" type="string">/sys/devices/platform/applesmc.768/light</merge>
      <append key="info.addons" type="strlist">hald-addon-generic-light-sensor</append>
    </match>
  </device>


</deviceinfo>

```

---

### Post by kosumi68 on 2008-11-10
> **undertakingyou said:**
> will@will-laptop:~$ hal-find-by-capability --capability keyboard_backlight
/org/freedesktop/Hal/devices/macbook_pro_keyboard_backlight
/org/freedesktop/Hal/devices/applesmc_keyboard_backlight
will@will-laptop:~$ hal-find-by-capability --capability light_sensor
/org/freedesktop/Hal/devices/macbook_pro_light_sensor
/org/freedesktop/Hal/devices/applesmc_light_sensor

So I get output that says that I should get some backlight.  Anyway to try and force the backlight level to see if I can get anything at all?

Ah! You are the victim of an earlier hal bug. Remove all references to your macbook model from the file /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi. Then reboot (or restart hal and X). The problem is described here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918)

---

### Post by kosumi68 on 2008-11-10
> **hyperboloid said:**
> OK, here you are:
```

me@laptop:~$ hal-find-by-capability --capability keyboard_backlight
/org/freedesktop/Hal/devices/applesmc_keyboard_backlight
me@laptop:~$ hal-find-by-capability --capability light_sensor
/org/freedesktop/Hal/devices/applesmc_light_sensor
me@laptop:~$ 

```



Thank you. I believe I found the problem in gnome-power-manager. I have uploaded new versions of hal-applesmc and gnome-power-manager to the mactel PPA, they should be available within half an hour. Please test them :-)

Here are values I changed in the apps/gnome-power-manager/ambient section, using gconf-editor. They work well for me.
```

correction_factor: 50 (how much in percent the ambient sensor should influence the brightness)
correction_scale: 1000 (how much in percent to scale the reading of the ambient sensor. readings are fairly low, so ten times seems ok)
dim_policy: none (unchanged)
enable: checked
poll_timeout: 30 (seconds: reasonable value. dont set too low)

```

---

### Post by hyperboloid on 2008-11-11
> **kosumi68 said:**
> Thank you. I believe I found the problem in gnome-power-manager. I have uploaded new versions of hal-applesmc and gnome-power-manager to the mactel PPA, they should be available within half an hour. Please test them :-)

Here are values I changed in the apps/gnome-power-manager/ambient section, using gconf-editor. They work well for me.
```

correction_factor: 50 (how much in percent the ambient sensor should influence the brightness)
correction_scale: 1000 (how much in percent to scale the reading of the ambient sensor. readings are fairly low, so ten times seems ok)
dim_policy: none (unchanged)
enable: checked
poll_timeout: 30 (seconds: reasonable value. dont set too low)

```

OK, I have the new versions installed and have changed my apps/gnome-power-manager/ambient section, using gconf-editor, to match your values. 

Bu this still isn't working on the MBP 4,1. Nothing happens in response to ambient light changes, as far as I can tell. Thanks for trying, by the way.

---

### Post by kosumi68 on 2008-11-11
> **hyperboloid said:**
> OK, I have the new versions installed and have changed my apps/gnome-power-manager/ambient section, using gconf-editor, to match your values. 

Bu this still isn't working on the MBP 4,1. Nothing happens in response to ambient light changes, as far as I can tell. Thanks for trying, by the way.

I think it will work, it should be some little thing we missed.

1. light readings ok? what do they look like?
```

cat /sys/devices/platform/applesmc.768/light 

```

2. hal device detection seemed ok from before.
```

hal-find-by-capability --capability light_sensor

```
```

hal-find-by-capability --capability keyboard_backlight

```

3. double-check version of hal-applesmc
```

dpkg-query -W hal-applesmc

```

4. double-check version of gnome-power-manager
```

dpkg-query -W gnome-power-manager

```

5. rebooting, just to make sure

---

### Post by hyperboloid on 2008-11-11
> **kosumi68 said:**
> I think it will work, it should be some little thing we missed.

1. light readings ok? what do they look like?
```

cat /sys/devices/platform/applesmc.768/light 

```

2. hal device detection seemed ok from before.
```

hal-find-by-capability --capability light_sensor

```
```

hal-find-by-capability --capability keyboard_backlight

```

3. double-check version of hal-applesmc
```

dpkg-query -W hal-applesmc

```

4. double-check version of gnome-power-manager
```

dpkg-query -W gnome-power-manager

```

5. rebooting, just to make sure

OK, this does seem to be working for the display backlight now, although it is not very sensitive to ambient changes at the moment. It seems that I need to cover up a sensor to make it go pretty close to zero before I see any change in display backlight intensity, and then it is a fairly small change. After uncovering, the intensity goes back up again. This is fairly unpredictable so far - sometimes it seems to miss the change altogether. 

There does not seem to be any effect on the keyboard backlight from this. One might expect to see it turn on when the ambient light is low, but I do not get that at all.  

Just for the record, here are the answers to kosumi's questions:

Question 1. Various readings with one or both sensors covered up.
```

me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(216,177)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(0,176)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(216,177)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(216,175)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(216,10)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(215,4)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(216,4)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(179,29)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(190,23)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(1,173)
me@laptop:~$ cat /sys/devices/platform/applesmc.768/light 
(0,14)

```

Questions 2 - 4. 
```

me@laptop:~$ hal-find-by-capability --capability light_sensor
/org/freedesktop/Hal/devices/applesmc_light_sensor

me@laptop:~$ hal-find-by-capability --capability keyboard_backlight
/org/freedesktop/Hal/devices/applesmc_keyboard_backlight

me@laptop:~$ dpkg-query -W hal-applesmc
hal-applesmc	0.14

me@laptop:~$ dpkg-query -W gnome-power-manager
gnome-power-manager	2.24.0-1mactel4

```
 
I wouldn't mind experimenting with the settings to see if I can get the keyboard backlight to come on when the ambient light gets low enough. Do you have any suggestions where to look?

---

### Post by kosumi68 on 2008-11-11
> **hyperboloid said:**
> OK, this does seem to be working for the display backlight now, although it is not very sensitive to ambient changes at the moment. It seems that I need to cover up a sensor to make it go pretty close to zero before I see any change in display backlight intensity, and then it is a fairly small change.

Your light readings (only the left sensor is in effect currently) are fairly high, so the correction_scale value of 1000% will hit max quickly. Changing the value to 100% should make a difference. Also, tchanging the correction_factor to 90% will give a much greater impact on the brightness. With 99%, its a huge difference.

---

### Post by hyperboloid on 2008-11-11
> **kosumi68 said:**
> Your light readings (only the left sensor is in effect currently) are fairly high, so the correction_scale value of 1000% will hit max quickly. Changing the value to 100% should make a difference. Also, tchanging the correction_factor to 90% will give a much greater impact on the brightness. With 99%, its a huge difference.

A correction_factor of 99% seems to be too high for my model - has no effect at all. Maybe it exceeds some threshold somewhere. But 80% seems pretty decent. I've also set the correction_scale to 100 as suggested. 

These settings make the display backlight response to ambient light changes really noticeable.  

Still no idea how to do same with the keyboard backlight. That will have to wait, I suppose. Anyway, I'm marking this thread "solved" so we can move on to more important things.

---

### Post by hellmitre on 2009-02-10
[http://ubuntuforums.org/showthread.php?t=1022619](http://ubuntuforums.org/showthread.php?t=1022619) fixed my keyboard backlight issue. Different model Macbook; might work though.

---

