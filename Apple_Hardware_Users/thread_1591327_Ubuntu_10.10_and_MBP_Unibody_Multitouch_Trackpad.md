---
title: "Ubuntu 10.10 and MBP Unibody Multitouch Trackpad?"
date: 2010-10-09
forum: Apple Hardware Users
---

### Post by kennethsime on 2010-10-09
So with all this talk about MultiTouch in Ubuntu 10.10 Maverick Meerkat, I wonder what it means for us with Unibody MBPs which have the wonderful multi-touch trackpad? This has been one reason why I still use my osx partition more than Ubuntu: Ubuntu really, really doesn't handle the multi-touch trackpad very well. I had to teach myself how to get Ubuntu to do what I wanted.

Thoughts? Has anyone else had problems with this? Has anyone installed Maverick yet? I'm waiting for the official release...

---

### Post by docryan on 2010-10-11
You are not alone :-) I also use OSX more than Ubuntu on my MacBook Pro 5.5. Besides the problem with the touchpad I also have the had problems with wifi, therefore I have upgraded to 10.10 today. But now the touchpad is even more broken and I havent found out how to fix it :-/

---

### Post by cha0s_unity on 2010-10-11
I just put 10.10 on a partition on my MBP. Everything works fine for me except for the touchpad. IT is jumpy when i slide my finger over the pad. The strange thing is, 2 finger scrolling of screens works just fine as does 2 finger right click. If anyone figures out how to fix this it would be nice to hear.

---

### Post by kennethsime on 2010-10-11
> **cha0s_unity said:**
> I just put 10.10 on a partition on my MBP. Everything works fine for me except for the touchpad. IT is jumpy when i slide my finger over the pad. The strange thing is, 2 finger scrolling of screens works just fine as does 2 finger right click. If anyone figures out how to fix this it would be nice to hear.

This has been true at least since 10.04. A lot of us were hoping UTouch would work a lot better with the MBP touchpad, but I think they have designed it more with touchscreens in mind...

I've only tried 10.10 in the Virtual Machine, going to install today and I'll report my findings...

---

### Post by teejmya on 2010-10-11
Utouch helps *slightly* with my Uni Whitebook Late09. The biggest thing is tapping to click, because if you click physically, it also detects a tap and therefore double clicks. 

Personally, as someone who has always tapped and not clicked, I find this a feature and not a bug.

But I seem to be the only person here who uses Ubuntu only on my Macbook, which is my main machine. I love it. Everything that doesn't work out of the box works with restricted drivers. 

The only thing that is buggy is shutdown/restart. It hangs on the last part, resulting in a "Restarting System." dialog. Everything is halted, but it hangs. This fixed it: [http://mac.linux.be/content/improve-battery-life-macbook-ubuntu](http://mac.linux.be/content/improve-battery-life-macbook-ubuntu)

---

### Post by youbuntu on 2010-10-11
> **teejmya said:**
> Utouch helps *slightly* with my Uni Whitebook Late09. The biggest thing is tapping to click, because if you click physically, it also detects a tap and therefore double clicks. 

Personally, as someone who has always tapped and not clicked, I find this a feature and not a bug.

But I seem to be the only person here who uses Ubuntu only on my Macbook, which is my main machine. I love it. Everything that doesn't work out of the box works with restricted drivers. 

The only thing that is buggy is shutdown/restart. It hangs on the last part, resulting in a "Restarting System." dialog. Everything is halted, but it hangs. This fixed it: [http://mac.linux.be/content/improve-battery-life-macbook-ubuntu](http://mac.linux.be/content/improve-battery-life-macbook-ubuntu)

This is my "/etc/default/grub" from my Late 2009 Unibody MacBook (MacBook6,1). I use Linux Mint 9.0, which is based on Ubuntu 10.04, and the rebooting works a treat - I have highlighted the pertinent code which ensures a clean reboot:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR=Red]reboot=pci[/COLOR] **nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```So you need to do:

1/
```
 sudo nano /etc/default/grub
```edit the line beginning with

```
GRUB_CMDLINE_LINUX_DEFAULT=
```and insert the [COLOR=Red]**highlighted**[/COLOR] [COLOR=Black]por[/COLOR]tion, then...

2/ do:

```
 sudo update-grub 
```3/ SHUTDOWN (not reboot) your MacBook, and test reboot the next time you want to... well, reboot! :)

---

### Post by oleink on 2010-10-18
> **kennethsime said:**
> This has been true at least since 10.04. A lot of us were hoping UTouch would work a lot better with the MBP touchpad, but I think they have designed it more with touchscreens in mind...

I've only tried 10.10 in the Virtual Machine, going to install today and I'll report my findings...

11.04 is when they plan to "spend more time" on the multitouch.  They just added the feature it's like a beta version (but in a stable operating system)

---

### Post by zalletn on 2010-10-21
i believe this should work , [Touchpad_Synaptics]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics")

i'm not too sure how it's working u may need an uTouch or so to connect every thing together, i'll spend more time on it after midterms ...... since most of new laptops and netbook have multi-touch touch-pads drivers should come out soon for Linux too ;)

---

### Post by kosumi68 on 2010-10-21
[http://ubuntuforums.org/showpost.php?p=10007145&postcount=280](http://ubuntuforums.org/showpost.php?p=10007145&postcount=280)

All binaries should be built in an hour or so.

This thread seems awfully similar to [http://ubuntuforums.org/showthread.php?t=1586340](http://ubuntuforums.org/showthread.php?t=1586340), btw.

---

### Post by kennethsime on 2010-10-21
> **kosumi68 said:**
> [http://ubuntuforums.org/showpost.php?p=10007145&postcount=280](http://ubuntuforums.org/showpost.php?p=10007145&postcount=280)

All binaries should be built in an hour or so.

This thread seems awfully similar to [http://ubuntuforums.org/showthread.php?t=1586340](http://ubuntuforums.org/showthread.php?t=1586340), btw.

Yes!!! Thank you!!! Could you post again once they are built to confirm? I'll keep checking both this thread and the solution you linked to.

---

