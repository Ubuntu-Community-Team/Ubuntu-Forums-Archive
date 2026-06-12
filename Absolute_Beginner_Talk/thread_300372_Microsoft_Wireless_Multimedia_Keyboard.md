---
title: "Microsoft Wireless Multimedia Keyboard"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by webjames on 2006-11-15
Hi there, just installed Ubuntu, firstly thanks for the help you gave me! secondly, it works brilliantly! :D 

Just wondering if there is a simple way of getting the multimedia keys to work on my keyboard? i have a Microsoft Wireless Multimedia Keyboard version 1.1, has keys running left to right:
My Documents - thought could be 'home'
My pictures
My Music
Mute (That works)
Play/Pause
Stop
Volume up/down (that works)
previous track
skip track
media
mail
web/home
messenger

any ideas how i can map these keys to functions?

Thanks,

Kind Regards,
James

---

### Post by bodhi.zazen on 2006-11-16
I have used the keyboard before and I liked it. I was a little flaky and I could not configure the keys as you are asking.

At the time I did an extensive google search, but never found a solution I could live with.

This is what I found:

"Compatibility

Does it work with GNU/Linux? Yes, but many of the special buttons and functions will not work without manually configuring your keyboard map and mouse settings." [Microsoft Wireless Laser Desktop 6000 review](http://www.hardwareinreview.com/cms/content/view/42/1/)

Start here [Manuel keyboard configuration](http://wiki.linuxquestions.org/wiki/Configuring_keyboards)

In the end I found the keyboard became unstable after a month (never did figure out why, but the keyboard started to work intermittently) and was not willing to go through the effort.

I hope this helps.

---

### Post by webjames on 2006-11-16
yeah thanks, i think i'll leave it as is!

Regards,

James

---

### Post by m_memmory on 2007-03-21
I've tried searching and looking around and I can't seem to get the buttons on my Microsoft Wireless Desktop 6000 V2.0

I've tried running xev and pressing the keys and a fair few of them aren't actually resulting in anything at all.  Is there any assistance that you can provide as to where I should be looking?

Thanks for any information that you can provide.

---

### Post by ViRMiN on 2007-03-21
Install KeyTouch and make use of your extra buttons!

---

### Post by gjtoth on 2007-03-21
> **webjames said:**
> Hi there, just installed Ubuntu, firstly thanks for the help you gave me! secondly, it works brilliantly! :D 

Just wondering if there is a simple way of getting the multimedia keys to work on my keyboard? i have a Microsoft Wireless Multimedia Keyboard version 1.1, has keys running left to right:
My Documents - thought could be 'home'
My pictures
My Music
Mute (That works)
Play/Pause
Stop
Volume up/down (that works)
previous track
skip track
media
mail
web/home
messenger

any ideas how i can map these keys to functions?

Thanks,

Kind Regards,
James

System/keyboard shortcuts should do it.

---

### Post by m_memmory on 2007-03-22
I downloaded KeyTouch and tried running it but it doesn't include a keymap for my desktop.  So then I downloaded the KeyTouch-editor and tried creating my own keymap,  However no matter what event I use as an argument with the editor the extra keys don't lead me to the next part of the editor.  It just stays with the display

> 
Device information:
 Input driver version is 1.0.0
 Input device ID: bus 0x3 vendor 0x45e product 0xf9 version 0x2
 Input device name: "Microsft Microsoft Wireless Desktop Receiver 3.1"

Press now one of the extra function keys of your keyboard.
If nothing happens you have probably chosen the wrong event device (which
is /dev/input/event2). In such case terminate this program, by pressing Ctrl+C,
and run this program again with another event device as a parameter.

---

### Post by silkstone on 2007-03-22
I've not tried KeyTouch because my current keyboard doesn't have the extra keys, but I'm sure I read somewhere that you should connect via PS2 rather than USB for it to work properly at the moment. Sorry if I've got that wrong, and of course it doesn't help with a wireless keyboard.

---

### Post by m_memmory on 2007-03-22
I've since tried uninstalling keytouch-editor and downloading the latest version and installing that from the keytouch website (previously I'd used apt-get install to get the editor)

This version seemed able to actually read the keyboard and add some of the keys in but there is still about a dozen keys that it's not able to read (things like the music & pictures folder buttons, the zoom in/out and the 5 favourites keys at the top.

I guess I'll just have to make do with what I'm able to use and use the rest only when I'm in WinXP (which unfortunately I still have to use from time to time but is helped by how well the keyboard/mouse combi works within it)

---

### Post by JoSSte on 2007-10-22
I'm having a similar problem after updating to gutsy gibbon from feisty fawn (7.04 --> 7.10) my shortcut buttons on my Logitech Cordless Dekstop Pro (PS/2 connection)are non functional. 

They worked fine before (mute, volume up, volume down) but now the mute button brings up the correct OSD picture, but it doesn't mute, the volume down button gives the muted OSD, and the volume up the Unmute OSD pic. But they don't affect the sound at all...

I verified and reverified the system-preferences-"keyboard shortcuts" settings, but to no avail.

could it be that something is broken?

---

### Post by JoSSte on 2007-10-26
all fixed - deleted the following, and all the shortcut buttons work superbly
/home/jss/.gconf/desktop/gnome/sound
/home/jss/.gconf/desktop/gnome/sound/%gconf.xml
/home/jss/.gnome/sound
/home/jss/.gnome/sound/events
/home/jss/.gnome/sound/events/gnome.soundlist
/home/jss/.gconf/desktop/gnome/volume_manager
/home/jss/.gconf/desktop/gnome/volume_manager/%gconf.xml
/home/jss/.gconf/apps/gnome-volume-control
/home/jss/.gconf/apps/gnome-volume-control/ui
/home/jss/.gconf/apps/gnome-volume-control/ui/%gconf.xml
/home/jss/.gconf/apps/gnome-volume-control/%gconf.xml

---

