---
title: "xserver error on edgy"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-28
Hello, I'm getting this error on boot up:

[17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0

[17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0

[17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0

then I get a blue/gray/ text screen about the xserver error and when I tried to fix it with sudo apt-get install --reinstall xserver-xorg and the a reboot it does nothing. I've tried some other things that I read in the first 5 threads searched for "xserver" and none of them worked.

like for instance: sudo dpkg -reconfigure xserver-xorg
and, sudo dpkg -reconfigure -phigh xserver-xorg

anybody know how to fix this?
Thanks,
-c.

---

### Post by jwbirdsong on 2006-10-28
> like for instance: sudo dpkg -reconfigure xserver-xorg
and, sudo dpkg -reconfigure -phigh xserver-xorg


You re not typing them like that are you?? There should be **NO** space between the **dpkg** and the **-reconfigure**

---

### Post by crimesaucer on 2006-10-28
I wrote it with a space, I'm new at this, do you think that might fix the problem and which one should I write.

---

### Post by crimesaucer on 2006-10-28
it sort of worked. now I have no panels and no menu, I only had a small gray block in the upper left corner showing, i clicked on to it and added a xfce menu so I could get firefox to write this.

Now I don't know how to fix the panel errors so I'm gonna try -f install and also reinstall the upgrades and dist-upgrade.

If any one knows the correct ways then please let me know.
Thanks,
-c.

Oh yeh, I also don't have scroll function unless I use firefox's auto scroll.

---

### Post by jwbirdsong on 2006-10-28
**sudo dpkg-reconfigure xserver-xorg**
The -phigh in the other one is for when you MANUALLY edit the /etc/X11/xorg.conf file and want it to be auto upated later....

It may not stop the errors but it should get your "screen" fixed so you can boot all the way...do a search on the forums here for pci+region..there are several other who have the same problem (no solution listed) but they all boot fine
Not sure if this link will work for you or not..it the search results for me...[http://www.ubuntuforums.org/search.php?searchid=9219363](http://www.ubuntuforums.org/search.php?searchid=9219363)

---

