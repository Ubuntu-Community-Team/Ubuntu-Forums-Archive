---
title: "Can I set video mode refresh rates in xorg.conf?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-06-13
I have a Compaq FS740 monitor. Below are the supported modes. Is there a way to set this up in xorg.conf?

Supported Video Modes:
      640 x 480                                         120 Hz
      800 x 600                                         110 Hz
      1024 x 768                                        85 Hz
      1152 x 864                                        75 Hz
      1280 x 1024                                       65 Hz

Thanks for your help.
kh

---

### Post by DoricMan on 2007-06-13
> **kittyhawk63 said:**
> I have a Compaq FS740 monitor. Below are the supported modes. Is there a way to set this up in xorg.conf?

Supported Video Modes:
      640 x 480                                         120 Hz
      800 x 600                                         110 Hz
      1024 x 768                                        85 Hz
      1152 x 864                                        75 Hz
      1280 x 1024                                       65 Hz

Thanks for your help.
khI have been interested in editing xorg.conf to get more buttons etc on my Logitech mouse. I would appreciate finding out more on editing this file, with, of course, a way of returning to the last version, should I make a mess of this important file.
Thanks. :KS

---

### Post by Sparkster185 on 2007-06-13
> 
I would appreciate finding out more on editing this file, with, of course, a way of returning to the last version, should I make a mess of this important file.

I always make a copy of mine by just doing

```

cp /etc/X11/xorg.conf ~/tmp/xorg.conf.OLD
```

To the original poster:

If you edit xorg.conf, you should find a section that lists Display Modes, or something.  there you can add the resolutions you want.

---

### Post by Songwind on 2007-06-13
> **kittyhawk63 said:**
> I have a Compaq FS740 monitor. Below are the supported modes. Is there a way to set this up in xorg.conf?

Supported Video Modes:
      640 x 480                                         120 Hz
      800 x 600                                         110 Hz
      1024 x 768                                        85 Hz
      1152 x 864                                        75 Hz
      1280 x 1024                                       65 Hz

Thanks for your help.
kh

If you want those specifically, then in the "screen" section of your xorg.conf, add _<refresh> to each mode where it's listed.

So if you have a line under the 24 bit color depth that looks like:
```

"1280X1024" "1152X864" "1024X768"....
```

Change them to:
 ```

"1280X1024_65" "1152X864_75" "1024X768_85" and so on.

```

---

### Post by Songwind on 2007-06-13
> **DoricMan said:**
> I have been interested in editing xorg.conf to get more buttons etc on my Logitech mouse. I would appreciate finding out more on editing this file, with, of course, a way of returning to the last version, should I make a mess of this important file.
Thanks. :KS

[Here's a great tutorial.]("http://ubuntuforums.org/showthread.php?t=28374")

---

### Post by kittyhawk63 on 2007-06-13
> **DoricMan said:**
> I have been interested in editing xorg.conf to get more buttons etc on my Logitech mouse. I would appreciate finding out more on editing this file, with, of course, a way of returning to the last version, should I make a mess of this important file.
Thanks. :KS

Ask, and ye shall receive. To back up your xorg.conf file, copy and paste the following in Terminal.
sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by kittyhawk63 on 2007-06-13
> **Songwind said:**
> If you want those specifically, then in the "screen" section of your xorg.conf, add _<refresh> to each mode where it's listed.
So if you have a line under the 24 bit color depth that looks like:
```

"1280X1024" "1152X864" "1024X768"....
```Change them to:
 ```

"1280X1024_65" "1152X864_75" "1024X768_85" and so on.

```

Great! Thanks.
kh

---

