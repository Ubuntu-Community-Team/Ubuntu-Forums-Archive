---
title: "Help to stop breaking Ubuntu - 6 times installed"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-06-29
Hi,
HELP.
This will be the seventh time  ( seventh install) and its all to do with video cards, display and broken xorg if I can't fix it.

My woes start with a video card - end with a viseo card.
Bought a new one - yes Gforce nvidia 7300 GT - does feisty recognise it - NO.
Hoped a video card that Ubuntu would support would get me a screen resolution and 3D graphics.
Windows XP recognises it and the other card.

The old one was a Raedon 9200 - xorg defualted everything install in safe graphics, xorg display and wesa.
So bought a new card and installed it. Removed the Raedon
Ubuntu wouldn't boot past the dos screen - xorg disabled - wrong config file - couldn't get past the dos screen. OK put the old video card back.

OK - try to reinstall - why not.
If windows can recognise the two cards and I can't switch it off to boot ubuntu I'll leave it there.

Boots up using the first card - raedon then starts up the second monitor and continues with it , the other goes to sleep. Installs OK - don't have to use reduced safe graphics - nvidia seems to be doing the job.

Use envy - get the drivers - say yes - update conf file - BROKEN - as to use nvidia you have to get the binnaries.

Restart in safe mode - still dos - xorg disabled - don't pass go.

What is it with Ubuntu - new card not recognised.
New card old card - reinstall - first card starts it second takes over - then zap.
Now that all I have is a DOS screen in recovery with the
root@billp-desktop: ~#

Can anyone HELP
Would be nice not to have to reinstall it all again.
How can i recover from here? - easily.

I would so love to use both cards it enables a big desk top in windows not a clone.
How do I recover Ubuntu graphics from here?

HELP
Ta
Bill

---

### Post by lazyart on 2007-06-29
new video card means you have to run```
sudo dpkg-reconfigure xserver-xorg
```after you have logged in via text mode.  Be sure to select nv as your video driver.  Then do [/code]sudo apt-get install nvidia-glx-new[/code].  Reboot and you should be in the clear.  Does the new card have dual monitor outputs?

---

### Post by wapfu on 2007-06-29
Hi about to try the code. In windows at present to read this.
Reboot and try.
Thanks.
The new card only allows for clone and vertical, horizontal, expansion  plus as a single monitor.
It has a DVI and VGA output. It doesn't allow to expand the desktop.

Best Regards
Bill

---

### Post by Seine on 2007-06-30
> **wapfu said:**
> Hi about to try the code. In windows at present to read this.
Reboot and try.
Thanks.
The new card only allows for clone and vertical, horizontal, expansion  plus as a single monitor.
It has a DVI and VGA output. It doesn't allow to expand the desktop.

Best Regards
Bill
Hi Bill. I have big troubles with nvidia drivers too. In fact I'm in the terminal screen right now trying to fix up issues after the nvidia driver upgrade.
I suspect you did not need to reinstall so many times. You're on the right track now. You will most likely be able to fix your issues without a reinstall.
To save you dual booting into windows to post on the forum, you can use lynx as I am doing now. It's a text only browser. It can be tricky to get started with but it should serve you well.
Finally, DOS is a microsoft technology and hence Linux does not have a DOS mode. Best to call it a terminal.
Cheers
Jem

---

### Post by buzzmandt on 2007-06-30
> To save you dual booting into windows to post on the forum, you can use lynx as I am doing now. It's a text only browser. It can be tricky to get started with but it should serve you well.
How do you browse in terminal as you were doing there?

---

### Post by wapfu on 2007-06-30
Hi Seine,
How do you browse in the terminal?
I had to reinstall yes seven times.
The nvidia card is detected I had to use.
"Sudo apt-get install nvidia -glx-new"
before it would get the graphics back , but only at the xorg screen.
By downloading sysinfo, I was able to adjust the nvidiadisplay but for the life of me I cannot get it to stay.
Each rebbot sees the screen default to xorg standard not my 1440x900 I can get - and save in the nvidia program.

Best Regards
Bill

---

### Post by buzzmandt on 2007-07-01
have you tried editing your /etc/X11/xorg.conf file?
check to see if 1440x900 is an option under screens, maybe take out all options and leave this as the only option for each of the screens lines (not real sure about this one but it worked for me on a similar issue)
also check that your driver is "nvidia" and not "nv" or "vesa"

---

### Post by chamberlain2006 on 2007-07-01
To browse using lynx, install it (sudo apt-get install lynx) and run it (lynx).

---

### Post by wapfu on 2007-07-02
Cheers

---

### Post by Seine on 2007-07-02
Yes. **lynx ubuntuforums.org** will take you straight to this forum. Use tab to hop between hyperlinks and enter or right cursor to follow a link.

---

