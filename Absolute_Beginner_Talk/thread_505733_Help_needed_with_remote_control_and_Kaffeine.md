---
title: "Help needed with remote control and Kaffeine"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Shootmeagain57 on 2007-07-20
Can anyone help a newbie(me) with what to do to get my remote control for my Nebula PCI DVB card to work with Kaffeine or any other app.

Any help or pointers welcomed

---

### Post by philter on 2007-07-23
I'm not an expert on the subject at all but I've heard about using LIRC to enable functionality for some remotes.  

The table of supported devices is available at:[ http://www.lirc.org/html/table.html]("http://www.lirc.org/html/table.html") and the homepage for LIRC is [ http://www.lirc.org/]("http://www.lirc.org/")

Hope this helps a bit.

EDIT:  I also found this How To on the Ubuntu Wiki  [https://wiki.ubuntu.com/LircHowto?highlight=%28LIRC%29]("https://wiki.ubuntu.com/LircHowto?highlight=%28LIRC%29")

---

### Post by luckyjonny on 2007-07-29
I've got the remote control working for my Nebula DigiTV PCI card using LIRC, for use with MythTV, Xine and XMAME. 

Follow the Remote Control section of Garry Parker's [[COLOR="Red"]MythTV installation guide[/COLOR]]("http://parker1.co.uk/mythtv_ubuntu2.php"), using the information posted on the [[COLOR="Red"]MythTV wiki[/COLOR]]("http://www.mythtv.org/wiki/index.php/Nebula_DigiTV_Remote") for the LIRC configuration files, rather than the Hauppauge Nova-T specific files he provides (the orange exclaimation mark on the page is slightly alarming, but basically if you've got an up-to-date Feisty install everything will work). I've attached the Nebula DigiTV PCI versions. Copy hardware.conf and lircd.conf to your /etc/lirc directory. If you download these to your home directory, this'll be something like:

```
sudo cp ~/hardware.conf /etc/lirc/hardware.conf
```

and

```
sudo cp ~/lircd.conf /etc/lirc/lircd.conf
```

in case you're floored by the permissions on the /etc directory. 

Make the LIRC device static, as Garry Parker describes [[COLOR="Red"]here[/COLOR]]("http://parker1.co.uk/mythtv_tips.php"). Then it's just a case of creating a .lircrc file to go in your home directory to match commands for Kaffeine to the buttons you've defined on your remote for LIRC. I've attached mine, in case it's useful.

After a quick Google search, it seems that Kaffeine works slightly differently to MythTV in terms of .lircrc entries. [[COLOR="Red"]This[/COLOR]]("http://www.hauppauge.co.uk/board/showpost.php?p=40221&postcount=7") post might help you create yours.

Have fun you lazy sod, your bed's next to your computer anyway :p

P.S. The file .lircrc in the attached zip has a dot in front of its name because it's a hidden file. Once you've extracted it to your home folder, click View > Show Hidden Files to be able to see it and edit it.

---

### Post by Shootmeagain57 on 2007-08-06
Thanks for the replies, I tried this:

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

and a combination of the links listed, but it still needs a few tweeks.

---

