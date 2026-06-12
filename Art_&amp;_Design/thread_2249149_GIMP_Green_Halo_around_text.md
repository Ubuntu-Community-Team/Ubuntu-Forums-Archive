---
title: "GIMP: Green Halo around text"
date: 2014-10-19
forum: Art &amp; Design
---

### Post by yousufinternet on 2014-10-19
Hello every one.. 

I have a big problem with GIMP, that makes it completly useless to me.. as u can see from the linked screenshot ( [https://www.dropbox.com/s/5aiivc9mvs79v4t/Screenshot%20from%202014-10-19%2001%3A20%3A11.png?dl=0](https://www.dropbox.com/s/5aiivc9mvs79v4t/Screenshot%20from%202014-10-19%2001%3A20%3A11.png?dl=0) ) there is a green halo that appears around the text I type, the problem persists even after exporting the photo into jpg or png :mad: please help me, this problem is killing me and I need GIMP a lot, I have done some google search and found the same problem with other people: 

[https://mail.gnome.org/archives/gimp-user-list/2014-September/msg00024.html](https://mail.gnome.org/archives/gimp-user-list/2014-September/msg00024.html)

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1010421](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1010421)

[http://www.infinality.net/forum/viewtopic.php?f=2&t=229](http://www.infinality.net/forum/viewtopic.php?f=2&t=229)

but none of the solutions suggested worked for me, I don't have infinality installed, I am using ubuntu 14.04 on a MacBook Pro 9,2

---

### Post by yousufinternet on 2014-10-20
How I can turn subpixel antialiasing off in ubuntu 14.04, I am using the normal unity distribution..

---

### Post by yousufinternet on 2014-10-20
Finally, I have solved this issue by entering the following commands: 
"
sudo rm /etc/fonts/conf.d/10-*
Note that /etc/fonts/conf.d just contains a set of symlinks to the full set of configuration files in /etc/fonts/conf.avail. To restore the default configuration in Ubuntu, you can run:
cd /etc/fonts/conf.d
sudo ln -s /etc/fonts/conf.avail/10-antialias.conf
sudo ln -s /etc/fonts/conf.avail/10-hinting.conf
sudo ln -s /etc/fonts/conf.avail/10-hinting-slight.conf
"

the original post can be found here: 
[http://askubuntu.com/questions/29827/weird-font-hinting-in-firefox-4](http://askubuntu.com/questions/29827/weird-font-hinting-in-firefox-4)

---

### Post by jehan-marmottard on 2014-11-06
Hi,

Good you found a solution that suits you. But I'm not sure that's the real cause that you removed, more a workaround. Especially since you removed various configuration files for fontconfig, it may come back and bite you back in the future.

I just wanted to note that your issue looks like a known issue with a third party package.
See bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=708052](https://bugzilla.gnome.org/show_bug.cgi?id=708052)

It is caused by a package called "fontconfig-infinality". Have you installed it?
Several people reported a problem with this package and the developer of infinality could reproduce and acknowledged the issue:
[http://www.infinality.net/forum/viewtopic.php?f=2&t=229](http://www.infinality.net/forum/viewtopic.php?f=2&t=229). I have no idea it is has finally been fixed in some dev version of this software or not though.

---

