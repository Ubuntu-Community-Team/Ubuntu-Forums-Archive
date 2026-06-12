---
title: "LXDM, getting to be usable"
date: 2012-10-01
forum: Any Other OS
---

### Post by Kansasguy on 2012-10-01
Could someone please walk me through the changes I need to do to get LXDM working?  It's on my computer, and I have two users, but it keeps loading to me, and I want it to default to the other user. Following this link,

[https://wiki.archlinux.org/index.php/LXDM](https://wiki.archlinux.org/index.php/LXDM)

where it says " Autologin

To log in to one account automatically, without providing a password, find the line in /etc/lxdm/lxdm.conf that looks like this:

#autologin=username

Uncomment it, then substitute your own username instead of "username". "

It's been a long time since I have done anything "sudo", and the file manager is PCMANF_

Averatec (older) laptop, dual booted with XP and Linux Mint LXDE (I know, it's not Ubuntu, but this is a huge forum and they are so much the same)

Thanks in advance

---

### Post by nothingspecial on 2012-10-01
Moved to Other OS/Distro Talk.

---

### Post by 2F4U on 2012-10-01
At the moment I am a bit unsure what the problem exactly is, is the description from Arch incorrect or do you have a problem editing the file.
While there are several ways to edit the file, opening a terminal and typing

```
sudo nano /etc/lxdm/lxdm.conf
```

should do the trick. When you are finished editing, type Ctrl-O to save the file and Ctrl-X to exit the editor.

---

### Post by Kansasguy on 2012-10-01
Thanks, you are right, trouble editing the file, will try that when I get home from work tonight.

Also, it seems that there should be some sort of "splash screen" , like


[http://www.google.com/imgres?q=lxdm&num=10&hl=en&biw=1022&bih=456&tbm=isch&tbnid=GClWFTW0WQMjiM:&imgrefurl=http://blog.lxde.org/%3Fp%3D595&docid=rG0jLEEZqoFl2M&imgurl=http://blog.lxde.org/wp-content/uploads/2010/01/lxdm-industrial-480x360.png&w=480&h=360&ei=dqppULq7CobY9ATRqIGIBg&zoom=1&iact=hc&vpx=426&vpy=4&dur=4995&hovh=194&hovw=259&tx=130&ty=72&sig=111316756002773886878&page=1&tbnh=121&tbnw=159&start=0&ndsp=10&ved=1t:429,r:2,s:0,i:79](http://www.google.com/imgres?q=lxdm&num=10&hl=en&biw=1022&bih=456&tbm=isch&tbnid=GClWFTW0WQMjiM:&imgrefurl=http://blog.lxde.org/%3Fp%3D595&docid=rG0jLEEZqoFl2M&imgurl=http://blog.lxde.org/wp-content/uploads/2010/01/lxdm-industrial-480x360.png&w=480&h=360&ei=dqppULq7CobY9ATRqIGIBg&zoom=1&iact=hc&vpx=426&vpy=4&dur=4995&hovh=194&hovw=259&tx=130&ty=72&sig=111316756002773886878&page=1&tbnh=121&tbnw=159&start=0&ndsp=10&ved=1t:429,r:2,s:0,i:79)

Am I missing something?   Thanks again

---

### Post by mips on 2012-10-01
> **Kansasguy said:**
> Thanks, you are right, trouble editing the file, will try that when I get home from work tonight.

Also, it seems that there should be some sort of "splash screen" , like


[http://www.google.com/imgres?q=lxdm&num=10&hl=en&biw=1022&bih=456&tbm=isch&tbnid=GClWFTW0WQMjiM:&imgrefurl=http://blog.lxde.org/%3Fp%3D595&docid=rG0jLEEZqoFl2M&imgurl=http://blog.lxde.org/wp-content/uploads/2010/01/lxdm-industrial-480x360.png&w=480&h=360&ei=dqppULq7CobY9ATRqIGIBg&zoom=1&iact=hc&vpx=426&vpy=4&dur=4995&hovh=194&hovw=259&tx=130&ty=72&sig=111316756002773886878&page=1&tbnh=121&tbnw=159&start=0&ndsp=10&ved=1t:429,r:2,s:0,i:79](http://www.google.com/imgres?q=lxdm&num=10&hl=en&biw=1022&bih=456&tbm=isch&tbnid=GClWFTW0WQMjiM:&imgrefurl=http://blog.lxde.org/%3Fp%3D595&docid=rG0jLEEZqoFl2M&imgurl=http://blog.lxde.org/wp-content/uploads/2010/01/lxdm-industrial-480x360.png&w=480&h=360&ei=dqppULq7CobY9ATRqIGIBg&zoom=1&iact=hc&vpx=426&vpy=4&dur=4995&hovh=194&hovw=259&tx=130&ty=72&sig=111316756002773886878&page=1&tbnh=121&tbnw=159&start=0&ndsp=10&ved=1t:429,r:2,s:0,i:79)

Am I missing something?   Thanks again

You need to specify that in the config file, download or create your own splash screen.

---

