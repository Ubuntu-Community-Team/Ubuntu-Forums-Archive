---
title: "[SOLVED] problem installing ntfs-3g"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-03-20
well... think i made a bit of a mess!
i was following the instructions of this link [http://www.ubuntu-es.org/node/21061]("http://www.ubuntu-es.org/node/21061")
(it's in spanish i know,but the commands remain the same) and after I had installed the fuse-2.5.3, for installing the ntfs-3g downloaded from the link provided, it said that i should be using the updated version of fuse-2.6.0  in order to be able to istall it.
So I downloaded and tried to install the fuse 2.6.0 with the same commands, without trying to uninstall the older version, thinking that it would overwrite it. Part of the result was 

 [B]make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'fuse.pc' '/usr/local/lib/pkgconfig/fuse.pc'
make[2]: Leaving directory `/home/morkhaar/fuse/fuse-2.6.0'
make[1]: Leaving directory `/home/morkhaar/fuse/fuse-2.6.0'
morkhaar@beethra:~/fuse/fuse-2.6.0$ sudo gedit/etc/modules
sudo: gedit/etc/modules: command not found
[/B]

so i tried to uninstall the 2.5.3 and in a bright moment of... experimental innovative techniques
i wrote sudo make **uninstall** at the terminal,  which of course had no effect.
Any attempt whatsoever to uninstall/reinstall  fuse from that point results in the same message, both for 2.5.3 and 2.6.0, I tried downloading and installing from another folder but the result is the same. And i think that I made things a bit more complex for me by erasing the folders of fuse from my home directory, which i think i have read i should never do in any case... :-s 
please. help?

---

### Post by h0ax on 2007-03-21
If you want to add/remove programs either do it via Applications -> Add/Remove Programs or through the Synaptic Package Manager in System->Admin

sudo make uninstall doesn't do anything
Also - 
> 
[B] morkhaar@beethra:~/fuse/fuse-2.6.0$ sudo gedit/etc/modules
sudo: gedit/etc/modules: command not found

[/B]Not a huge error here, just need another space after the T in gedit
so should be
```

sudo gedit /etc/modules 

```

Helped?

---

### Post by haricharan on 2007-03-21
looks like you are following an old tutorial...do it as it is said in [http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009")

---

### Post by Morkhaar on 2007-03-21
well, you advice is sure helpful for the future, but add/remove didn't show up fuse, and in  synaptics i can't find the option to uninstall a package. 
as for the space, i noticed that a little while later and i was finally able to install it. guess I should switch back to the old copy paste routine (even though givre says we shouldn't) and  save myself some frustration! :)  

thanx for the new link haricharan, i'll try it tonight! with the other thread I can now access my files but I 'm still experiencing some problems. hope I get better results

---

