---
title: "Problem with Windows installation"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Fanactism on 2007-01-29
ok so first off i am completely new to linux. i have tryed quite a few different types but none have worked for me. yesterday a friend of mine tells me there is a new version out where it installs straight from windows so i jumped on it. I downloaded the file and let it do its thing. once it was done i restarted my system and noticed it brought up windows right away. My friend is very skilled with all this so i asked him for advice. he told me he found out on this site that i needed to add something to the boot.ini so i did. then i restarted and the menu came up, i chose ubuntu and it ran through some text then up in the top left corner there was a flashing underscore. i saw it and thought it meant it was doing its thing after awhile i decided i would press enter for no apparent reason and the underscore dissapeared. i then went back to my friend for help and he told me to add this to the end replacing what i had put there before multi(0)disk(0)rdisk(0)partition(1)\grldr="Ubuntu".
i tried that and the same thing happened so i changed it back to what it was befor. then i went into the GRUB menu and tried most of those but the only one that got anywhere was recovery. when i go into recovery it does its thing than gives me the following error: "cant access tty; job control turned off.
up a little more it also says : " ALERT! /dev/sda1 does not exist. dropping to a shell!


any help would be much appreciated and any other info you may need i would be happy to supply. thank you

---

### Post by vir3nt on 2007-01-29
Instead of multi(0)disk(0)rdisk(0)partition(1)\grldr="Ubuntu", try the `C:\grldr="Ubuntu"' line. This is mentioned in the help on the Prototype download page.

Good luck.:guitar:

---

### Post by seshomaru samma on 2007-01-29
In order to help you we will need some more information

As far as I know you cannot install Ubuntu directly from Windows.
Can you explain in more details how you installed?

Also , do you have an Ubuntu live CD , the install CD can usually work as a live CD,
boot from the Ubuntu Live CD
open a terminal (from the top panel, I'm using a different interface so I don't remeber how to access a terminal from the default interface , you should be able to find it through the main menues)
paste this command into the terminal :
```
sudo fdisk -l
```
and paste the output here

---

