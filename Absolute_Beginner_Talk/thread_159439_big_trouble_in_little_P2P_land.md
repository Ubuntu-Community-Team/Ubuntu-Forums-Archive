---
title: "big trouble in little P2P land"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-12
I had limewire installed and it worked great. I did not use it for two days while I was figuring out the ipod video encoding thing.  I got that working and went to open limewire to get more video to try, but limewire freezes during its bootup. froze the system i had to cold reboot...twice.  any idea why it freezes now?:confused: 

Problem two, I installed frostwire fine and it opened now and found results, but they are incredibly hard to see...I can see faint images of the file names in the box, if i click on one it highlights and i can read it., but all the text appears very faint, any clues on that?  :-k thanks to all

Now I click to download a result found in frostwire and it gets stuck..... WTF

---

### Post by x5452 on 2006-04-12
im lost now, all of a sudden i cant find gtkpod, icon gave error, said wont load cant find it, and gtkpod is gone from my menu. but if i type it in terminal, the gui pops up?  any ideas??

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=x5452]im lost now, all of a sudden i cant find gtkpod, icon gave error, said wont load cant find it, and gtkpod is gone from my menu. but if i type it in terminal, the gui pops up?  any ideas??[/QUOTE]
 Use Automatix: Copy and paste the following in terminal

> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
sudo dpkg -i automatix_5.7-3_i386.deb

After it's done installing you can find it under Applications > System Tools > Automatix. Use it to install everything that you need.

---

### Post by x5452 on 2006-04-12
Thanks for the reply, I have automatix installed, and i would redo gtkpod with it but isnt it the old version?  I have .99.4 installed, which i need for the ipod video encoding transfer, is there a way to update/or reinstall parts of what .99.4 that i have?

---

### Post by felosi on 2006-04-13
limewire freezes on me as well with jre 1.42 and 1.5

---

### Post by jms830 on 2006-05-02
There are debs that I have used for **gtkpod video** at the following links:

[http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb](http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb)

[http://box.go.dyndns.org/dev/gtkpod_...-0cvs_i386.deb](http://box.go.dyndns.org/dev/gtkpod_...-0cvs_i386.deb)

all I did was install them
```
sudo dpkg -i libgpod_0.3.0-1_i386.deb 
sudo dpkg -i gtkpod_0.99.3-0cvs_i386.deb
```


and for p2p I would HIGHLY HIGHLY recommend nicotine (soulseek)
```
sudo apt-get install nicotine
```
info in my sig. about nicotine, as you have to configure your firewall to forward ports. (its easier than it sounds, [www.portforward.com](www.portforward.com) for further info on that.)

---

