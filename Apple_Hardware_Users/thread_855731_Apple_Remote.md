---
title: "Apple Remote"
date: 2008-07-10
forum: Apple Hardware Users
---

### Post by Mbengi Bongi on 2008-07-10
Hi Guys

Have decided to join the Ubuntu bandwagon again after having migrated from x86 to the Mac platform, after having got the wireless set up (eventually), I'm still having one problem - getting my remote to work.

After having read all the other threads regarding lirc, elisa etc, I still cannot get my Apple Remote to work in Ubuntu.

I have a 1st Generation (White) Intel iMac (with the new aluminium keyboard), and am dualbooting Ubuntu 8.04 (Hardy) with Mac OS X 10.4 (Tiger).  At the moment my main use for the remote outside OS X is using it at boot time due to the issue with the aluminium keyboard with 1st Gen intel Macs!

All the threads I've read mention a prompt, or configuration menu and say to choose 'macmini', but every time I install **lirc**, it just goes back to the prompt, can anyone help? [CENTER][/CENTER]:confused:

---

### Post by Dinatius on 2008-07-11
Actually, this is something that I've been wondering about, myself.

It wouldn't really be all that necessary for me, but it would still be a cool little something to add on to this side of my machine.
I can get the IR Receiver to show up in Device Manager, but it doesn't look like its doing much of anything.

---

### Post by all2ez on 2008-08-02
Not sure if you're still looking or if it will even work for you, but I have a 2nd gen MacBook and just today followed the community wiki for MacBook Pro and it works.  Well it works for the desktop volume, and in Amarok (which is what I really wanted), and Totem, but not in VLC using that author's lircrc file.  I'll have to play with the VLC settings but everything else seems good.

Should be worth a try if you haven't gotten it.

[https://help.ubuntu.com/community/MacBookPro#Apple%20Remote%20Control](https://help.ubuntu.com/community/MacBookPro#Apple%20Remote%20Control)

Edit:  I just reread your post and realized that the real answer to your question is:

```
sudo dpkg-reconfigure lirc
```

I had the same problem.  The first time I ran the install I didn't choose the mac mini setting and had to run the above command in a terminal to get back to that prompt.

---

### Post by repinel on 2011-02-05
Check out this GNOME applet.

[http://code.google.com/p/ir-switcher/](http://code.google.com/p/ir-switcher/)

---

