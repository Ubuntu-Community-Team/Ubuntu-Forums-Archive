---
title: "new (used) nvidia vid card + driver install ?'s"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-04-14
hi,

this is a dumb question, but i don't want to screw this up..

just got a used nvidia card.  do i install the card, then load the drivers, or vice versa?


also, which set of instructions for driver install should i use?  the instructions at the starter guide here: [http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29")
look the easiest to follow.

also, my vid card is a geforce4 420mx agp.  didn't pay too much for it!

thanks,

takayuki

---

### Post by Mustard on 2006-04-15
You should probably read some info on how to reconfigure your xorg.conf from the command line, just in case you end up there after installing the card.  It's not guaranteed that something won't go wrong and X won't load.

You would put the card in first and then install drivers.  If you get display problems when you start up, reconfigure xorg.conf using whatever method you have looked into ie sudo dpkg-reconfigure xserver-xorg, or manually editing the xorg.conf with a command line text editor.

Two more guides exist for nvidia driver installs at these links...

Ubuntu Wiki
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) 

Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

The instructions in the starter guide you have linked above are good, concise and too the point, if your card is supported by the stock drivers from the repositories.  You might want to do some research on this first.  Most nvidia cards work fine, occasionally some models have problems.  Older cards need different drivers.

Other optional things you might like to investigate before installing:

How to use a web browser from the command line (so you can browse to any helpful links without the need for an X display)

How to use IRC from command line (so you could get to the IRC support channel for ubuntu at irc.freenode.net at #ubuntu)

---

### Post by takayuki on 2006-04-15
mustard,

thank you very much for your detailed advice.  that's what i needed.  i've got my mac via kvm if something goes wrong and i need to get some help.

i've tweaked my xorg.conf file before so i think i'm ready.  i'm hoping it'll go in without much pain, but it's nice to have a plan b just in case.

takayuki

---

### Post by Mustard on 2006-04-15
Good luck. :)

---

### Post by takayuki on 2006-04-15
followup question:

in the [nvidia binary driver how to]("http://https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia") it says: "Note: Be sure to have the right version of linux-restricted-modules installed. It must match the version of the running kernel."

how do i know which kernel i'm running?

i currently have linux-restricted-modules-2.6.12-10-k7 installed.  

thanks,

takayuki

---

### Post by Mustard on 2006-04-16
[QUOTE=takayuki]followup question:

in the [nvidia binary driver how to]("http://https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia") it says: "Note: Be sure to have the right version of linux-restricted-modules installed. It must match the version of the running kernel."

how do i know which kernel i'm running?

i currently have linux-restricted-modules-2.6.12-10-k7 installed.  

thanks,

takayuki[/QUOTE]

This command returns your current kernel version..

```
uname -r
```

You can in fact use this within a command to download the version of the restricted modules you need. Please not that it uses backticks **`**, not single quotes **'**.  They look the same but they are a different character.  The backtick is on the tilda key ~.

```
sudo apt-get install linux-restricted-modules-`uname -r`-k7
```

Either that, or you can just type it out manually after using the uname -r command to find the current kernel version.

It looks like you have the current version you need already, but it doesnt hurt to check.

---

