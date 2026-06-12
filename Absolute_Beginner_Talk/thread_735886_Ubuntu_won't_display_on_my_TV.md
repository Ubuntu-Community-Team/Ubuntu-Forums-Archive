---
title: "Ubuntu won't display on my TV"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-03-26
I've just installed Ubuntu on my media PC and after a fairly smooth install I have hit upon a problem at the login screen. Everything runs through fine from boot; I get the BIOS screen, the OS selector screen and finally the Ubuntu logo and the orange progress bar. But when we get to the login screen the TV just shows a crazy patchwork of random colours.

Now I'm sure this must be down to me having it at the wrong resolution or something, but I don't know how to amend this at command line. The GFX card in use is an old NVidia 6600 256mb, which I had working with Ubuntu a few weeks back.

So how do I amend the display resolution etc in command line?

Many thanks


Mark

---

### Post by overdrank on 2008-03-26
> **NeonSamurai said:**
> I've just installed Ubuntu on my media PC and after a fairly smooth install I have hit upon a problem at the login screen. Everything runs through fine from boot; I get the BIOS screen, the OS selector screen and finally the Ubuntu logo and the orange progress bar. But when we get to the login screen the TV just shows a crazy patchwork of random colours.

Now I'm sure this must be down to me having it at the wrong resolution or something, but I don't know how to amend this at command line. The GFX card in use is an old NVidia 6600 256mb, which I had working with Ubuntu a few weeks back.

So how do I amend the display resolution etc in command line?

Many thanks


Mark

Hi and you can try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by NeonSamurai on 2008-03-26
> **overdrank said:**
> Hi and you can try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks overdrank. When I run the command line it comes back saying:

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080326100702


Do I need to make any amendments to this *.conf file? Also, if I wanted to undo these changes, how can that be done?

Thanks


Mark

---

### Post by overdrank on 2008-03-26
> **NeonSamurai said:**
> Thanks overdrank. When I run the command line it comes back saying:



Do I need to make any amendments to this *.conf file? Also, if I wanted to undo these changes, how can that be done?

Thanks


Mark

Hi and you may make changed to your xorg.conf, As stated in the message it made a backup of the original file so you may restore it. The command used reconfigures your xorg and if you it does not work then you may have to use the command without the -phigh tag and this will allow you to make choices on your xorg.
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by antmenj on 2008-03-26
I had the same issue on a monitor.  The login screen rendered the screen out of horizontal lock.  I grabbed a newer monitor and that worked.

If someone knows how to write a command to change the login screen resolution I think your problem will be solved.

One would expect that a lower resolution would be used as a default setting.

---

