---
title: "HOW-TO: get the MBP keyboard backlight working properly"
date: 2008-03-01
forum: Apple Intel Users
---

### Post by droazen on 2008-03-01
Hi,

Like several others on this forum, I found that the keyboard backlight on my MBP wasn't working properly in Gutsy "out of the box", even with pommed installed. Eventually I managed to get it working more or less as well as in OS X, and thought it might be useful to make a post here detailing the steps I took.

1. Install pommed:

```
sudo aptitude install pommed
```

2. Add applesmc to /etc/modules:

```
echo applesmc | sudo tee -a /etc/modules
```

3. Adjust the "on_threshold" and "off_threshold" values in the "kbd" section of /etc/pommed.conf to something a bit more responsive to ambient light changes than the default values of 20 and 40, respectively. After some experimenting, I found that 40 for the "on_threshold" and 80 for the "off_threshold" works very nicely (nicely as in "the backlight comes on if I turn the lights off in my room, and goes off if I turn the lights on"). Also make sure that the "auto" setting is set to "yes", and the "default" setting is set to your desired default brightness. Below is my kbd section for reference:

```
# Keyboard backlight control
kbd {
        # default value for automatic backlight (0 - 255)
        default = 255 
        # step value (1 - 127)
        step = 50
        # ambient light thresholds for automatic backlight (0 - 255)
        on_threshold = 40
        off_threshold = 80 
        # enable/disable automatic backlight
        auto = yes
}
```

4. reboot

5. If you find that the values you entered for on_threshold and off_threshold are not giving you the behavior you want, tweak them in /etc/pommed.conf and then type the following to make the new settings take effect:

```
sudo /etc/init.d/pommed restart
```

The way these threshold values seem to be used by pommed is as follows: if the backlight is currently off and the left and right ambient light sensors *both* dip below the on_threshold, the backlight gets turned on. Otherwise, if the backlight is currently on and *either* the left or the right ambient light sensor goes above the off_threshold, the backlight gets turned off.

This is based on my interpretation of the following section of the kbd_backlight_ambient_check() function in the v1.8 pommed source:

```
  if ((amb_r < kbd_cfg.on_thresh) && (amb_l < kbd_cfg.on_thresh))
    {
      logdebug("Ambient light lower threshold reached\n");

      /* backlight already on */
      if (kbd_backlight_get() > KBD_BACKLIGHT_OFF)
	return;

      /* turn on backlight */
      kbd_bck_info.auto_on = 1;

      kbd_backlight_set(kbd_cfg.auto_lvl, KBD_AUTO);
    }
  else if (kbd_bck_info.auto_on)
    {
      if ((amb_r > kbd_cfg.off_thresh) || (amb_l > kbd_cfg.off_thresh))
	{
	  logdebug("Ambient light upper threshold reached\n");

	  kbd_bck_info.auto_on = 0;

	  kbd_backlight_set(KBD_BACKLIGHT_OFF, KBD_AUTO);
	}
    }
```

Hope this helps someone someday :)

---

### Post by ronocdh on 2008-03-01
Great post, simple and informative. Can't wait to try it out!

---

### Post by cyberdork33 on 2008-03-01
Excellent Post. I am adding it to the FAQ.

---

### Post by ronocdh on 2008-03-04
I haven't seen this materialize on the [MacBookPro Wiki]("https://wiki.ubuntu.com/MacBookPro") yet. Are you planning on adding it, droazen? If not, one of us will gladly jump on it, I'm sure.

---

### Post by The Spy on 2008-03-27
How to you get into the config file? Do you think this will work on a Powerbook G4?

---

### Post by cyberdork33 on 2008-03-27
> **The Spy said:**
> How to you get into the config file? Do you think this will work on a Powerbook G4?

Does the Powerbook G4 have a keyboard backlight?

---

### Post by The Spy on 2008-04-16
Yeah. The keyboard has three buttons. one is on F8 and it's just a line. The next is on F9 and it's a line with small, thin rays, I guess you could call them, above the line, and the third (on F10) is a line with bigger rays above it. So I'm guessing these are to turn the keyboard backlight on and off. I've also heard other people talk about a keyboard backlight on their Powerbooks, and how it worked in OS X, but now it doesn't, just like everyone else.

---

### Post by hyperboloid on 2008-06-10
This did not work for me. I have a brand new MacBook Pro Penryn running Ubuntu 8.04, and I'm running pommed 1.18 since I read in one of the postings that earlier versions of pommed do not work with the Penryn version of MB Pro. 

All my function hotkeys work except F5, F6. I can manually dim the screen, for instance, and control volume using F19, F10, F11 keys. 

But keyboard backlighting is still no go for me. Any suggestions?

---

### Post by cyberdork33 on 2008-06-11
> **hyperboloid said:**
> This did not work for me. I have a brand new MacBook Pro Penryn running Ubuntu 8.04, and I'm running pommed 1.18 since I read in one of the postings that earlier versions of pommed do not work with the Penryn version of MB Pro. 

All my function hotkeys work except F5, F6. I can manually dim the screen, for instance, and control volume using F19, F10, F11 keys. 

But keyboard backlighting is still no go for me. Any suggestions?

Please make new posts in the new Apple forum.

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by pravinbravi on 2008-07-13
Still doesn't work for me. My dmesg still outputs he following -

applesmc: wait status failed: c != 8


My backlight comes on, stay on for a while and then goes off. This keeps happening intermittently.

--
Pravin

---

