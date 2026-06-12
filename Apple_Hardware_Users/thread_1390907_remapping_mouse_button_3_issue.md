---
title: "remapping mouse button 3 issue"
date: 2010-01-26
forum: Apple Hardware Users
---

### Post by migel_wimtore on 2010-01-26
Hi. I am looking for a little help and wondering if any other ppc users have had the issue whereby, after the first unsuccessful power down (or sometimes the second or third) of a fresh ubuntu 9.10 install, mouse button 3, which is normally mapped to F12, becomes function (fn) + F12.?

This is really annoying as you now have to use two hands to activate the little drop down menu.

So i tried remapping mouse button three to that strange little key beside the left arrow on an ibook keyboard that looks like a picnic table and which, under os x, renames stuff. 
I ran "gksu gedit /etc/sysctl.d/10-arch-specific.conf" and edited it accordingly: mouse button 3 from keycode 88 to 104. 
It works, but i still have to press function to activate it and fn + F12 still works simultaneously (though it is no longer defined in the conf file), and my new key doesnt offer the same functionality (eg, it doesnt give spell check options in firefox where fn + F12 does).

Arg.
 
Anybody know how to make it so that i can activate mouse button three without having to press function???

Anybody else also experiencing this issue???

I am using an older G4 ibook, 8oomhz, 256 MB RAM, by the way. The option (apple) keys worked straight out of the box which was sweet, but this is really annoying me. Iv even gone to the leangth of reinstalling and trying to avoid a failed power down, but it comes eventually.:(

Cheers.

---

### Post by linuxopjemac on 2010-01-26
I am using mousemu for this

---

### Post by migel_wimtore on 2010-01-26
Hi, thanks for the reply.

I am using mouseemu too, the problem is that it has stopped recognising F12 as mouse button 3 without also pressing function. 

I have tried uninstalling and reinstalling mouseemu and logging out and in (for good measure), but it doesn't stop this behaviour. Its weird though because in /etc/default/mouseemu no modifier is written.

Do you need to press function as well?

---

### Post by linuxopjemac on 2010-01-26
no, just F12....

> By default, mouseemu remaps fn+F11 and fn+F12 to middle-click and right-click; most people prefer using those keys for their intended functions. Removing mouseemu also fixes the LED on the caps lock key.
[https://help.ubuntu.com/community/MacBookPro3-1/Intrepid](https://help.ubuntu.com/community/MacBookPro3-1/Intrepid)

there is a config file for mouseemu at /etc/default/mouseemu, maybe something there ?

if you want, send me a private post and I will have a look in that file myself and post you my config file.

---

### Post by linuxopjemac on 2010-01-26
maybe also interesting:

> I realized early that Ubuntu is not very usable with a 1-button mousepad. After some searching I found out that F12 (or maybe it was F11, it's not working now) was mapped to right-click. WTF, there is no way in hell I'm using any F key for right-clicking. In OS X I can do it by ctrl-clicking, so I should be able to do it in Linux too. I came across this posting about installing mouseemu. I did so, and added to /etc/default/mouseemu:

    ```
MID_CLICK="-middle 125 272" # Command key + mouse click
    RIGHT_CLICK="-right 29 272" # Control key + mouse click
```

Once I did that and restarted mouseemu (sudo /etc/init.d/mouseemu stop/start), I was able to right-click with ctrl-click. Yay! 

---

### Post by migel_wimtore on 2010-01-26
What do you know? Its working. Just deleted the line "dev/mac_hid/mouse_button3_keycode = 88" from "/etc/sysctl.d/10-arch-specific.conf" and unistalled and reinstalled mouseemu. The F12 now does its business unaided by the function key. Wa-hey.

That will do for now i think. Attempting to reassign right click to the "picnic bench" key and and others through " /etc/sysctl.d/10-arch-specific.conf" and "/etc/default/mouseemu" was troublesome and buggy (a mixture of, at times, total loss of mouse functionality, loss of key functionality and total lock up). 
Though now that that line has been deleted from arch-spec.conf perhaps it will now be possible through mouseemu, as (to my lay-mind) the two files seemed to have been interfering with each other in some way following failed power downs.

Anyways, thanks very much for your help linuxopjemac, that heads up on the "sudo /etc/init.d/mouseemu stop/start" command is very useful.

Cheers.

---

### Post by migel_wimtore on 2010-01-27
Just did a fresh install (infernal lost applets issue -tried uninstalling gnome applets and reinstallin in recovery mode - no joy) and have unistalled mouseemu and am using the arch-specific.conf configuration to handle mouse button keyboard commands (hopefully this will be stable now, as the two wont be able to interfere with each other). 
However, after changing th keycode here (from 88 to 104) the picnic table key is still not operable without function and provides less functionality than F12 (just get the standard menu youde get from mouse button three if pressed on the desktop, no special menus like spell check in firefox or the little menu you get if you click on one of the menu bars.

Oh well, this will do for now.

Also, i am now using ext3 and it seems to be more stable (no power down failures). Ar you using ext3 linuxopjemac?

Cheers.

---

### Post by linuxopjemac on 2010-01-27
On my PPC based Pismo G3 I have Debian Lenny with ext3. That one has F11 as 3rd mouse button key with mouseemu.

On my MacBook 2,1 Karmic with ext4 runs (with F12 and mouseemu)

---

### Post by migel_wimtore on 2010-01-27
Right. Cheers for the info, and thanks for the help.

Take care.

---

### Post by afrodeity on 2010-03-02
I am trying to remap the mouse keys on a Samsung NP-R522 which has only one mouse key which is defaulting to right click. Need it to be left click, and right click to be emulation ctrl-click. Installed mousemu and all the keys on the keyboard got thrown out, some were numbers and so on. Removed it. Is there a way to do this without killing the keyboard? Looking for a GUI for mousemu or better method.

---

### Post by linuxopjemac on 2010-03-02
What about making it a left handed mouse ?
Preferences -> Mouse -> General -> Mouse orientation

---

### Post by afrodeity on 2010-03-03
Doesn't appear to change anything. Mouse orientation works on a two button mouse.

---

