---
title: "Extremely basic question:  How do I install a program?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-06-21
U. 5.10

I downloaded the latest Firefox, 1.5.0.4.  It arrived as a .tar.gz compressed file to my desk top.  I double clicked it and it was decompressed to a folder named firefox.  Now what do I do from here?  I can't find a folder of Applications to move it to nor an installer that identifies it.  'Add Applications' under the Applications menu doesn't see it.  

Thanks.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by aysiu on 2006-06-21
Use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) or just paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install firefox
``` Read more here: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by CompShrink on 2006-06-21
I see you are using Ubuntu verision 5.10, which is also called Breezy. I would suggest upgrading to 6.06, aka Dapper. Then you will have Firefox 1.5.0.4, along with the newer versions of every other program.

If you just want to stick with 5.10 Breezy, you can install the deb from UbuntuPlus.

Open a terminal (Applications > Accesorries > Terminal) and copy and paste in:

```
sudo echo "deb http://www.tikal26.net/ubuntu/apt breezy main" >> /etc/apt/sources.list && apt-get update && apt-get install ubuntuplus-internet
```

That will download the unofficial Firefox deb made for UbuntuPlus Breezy. This is the easiest way to cleanly and safely install Firefox 1.5 in Breezy (aka 5.10).

---

### Post by JEBB on 2006-06-22
For my introduction to Ubuntu and Linux I am using a old Compaq laptop that has a maximum of 192MB RAM.  Ubuntu 6.06 requires 256MB minimum, U. 5.10 requires only 128MB.  

Must I uninstall the older version of Firefox first or at all?  If so, how will I do that?

---

### Post by muep on 2006-06-22
The harware requirements of 6.06 are no different to those of 5.10. They just have decided to recommend a better machine. Maybe because of the fact that there are now better machines available than at the time of 5.10. 

The Desktop CD installer doesn't work very well on a machine with only 128 MBs of RAM, but, at least for me, it worked. I still recommend the Alternative install cd or a dist-upgrade to get 6.06.

If you computer feels slow with Gnome, Xubuntu might be worth a try.

---

