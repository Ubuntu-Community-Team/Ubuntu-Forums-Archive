---
title: "I am alien to Alien"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-07-06
I am having big problems with my printer because all the drivers, fixes and support that is available, is not working.  I think this is because it is a japanese printer and it wants japanese drivers.  I bought a Canon Pixus 560i printer.  I have looked on the Japanese canon support site [http://cweb.canon.jp/drv-upd/bj/bjlinux240.html](http://cweb.canon.jp/drv-upd/bj/bjlinux240.html)
and it says:
 "Canon Bubble Jet Print Filter Ver.2.40 for Linux"
Then if you scroll down it says:
 560irpm&#12497;&#12483;&#12465;&#12540;&#12472;  	 PIXUS 560i&#29992;&#12501;&#12451;&#12523;&#12479;&#12467;&#12510;&#12531;&#12489;&#12289;&#12487;&#12540;&#12479;&#12505;&#12540;&#12473;&#12289;&#12473;&#12463;&#12522;&#12503;&#12488;&#19968;&#24335;&#12290; 
I downloaded the rpm packages, and then tried to use alien to convert them to .deb files and I get errors up the yin-yang.  Something about it cannot chmod or chown.  I don't know why I am having permission problems since I am using sudo.](*,)   I even signed in as root and tried and still had another helping of errors.  Any help would be greatly appreciated.  Thanks

---

### Post by lordlollo on 2006-07-06
[QUOTE=legolas]
 560irpm&#12497;&#12483;&#12465;&#12540;&#12472;  	 PIXUS 560i&#29992;&#12501;&#12451;&#12523;&#12479;&#12467;&#12510;&#12531;&#12489;&#12289;&#12487;&#12540;&#12479;&#12505;&#12540;&#12473;&#12289;&#12473;&#12463;&#12522;&#12503;&#12488;&#19968;&#24335;&#12290; 
[/QUOTE]

:confused: Kind of translation? :confused:

---

### Post by bwayman on 2006-07-06
More like lost in translation.

---

### Post by legolas on 2006-07-06
sorry guys.   560irpm&#12497;&#12483;&#12465;&#12540;&#12472; PIXUS 560i&#29992;&#12501;&#12451;&#12523;&#12479;&#12467;&#12510;&#12531;&#12489;&#12289;&#12487;&#12540;&#12479;&#12505;&#12540;&#12473;&#12289;&#12473;&#12463;&#12522;&#12503;&#12488;&#19968;&#24335;&#12290;
It says:  560irpm'package' 'for Pixus 560i filter command, database, 'all scripts'

---

### Post by christhemonkey on 2006-07-06
Let us now of any errors from these commands:
```
sudo alien package.rpm 
sudo dpkg -i package.deb 
```

---

### Post by legolas on 2006-07-06
> **christhemonkey said:**
> Let us now of any errors from these commands:
```
sudo alien package.rpm 
sudo dpkg -i package.deb 
```

:~$ sudo alien package.rpm
Password:
File "package.rpm" not found.

:~$ sudo dpkg -i package.deb
dpkg: error processing package.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 package.deb


That don't look right does it!?

---

### Post by nalmeth on 2006-07-06
He meant to replace package.rpm with the package that you're trying to convert.

Can you post the errors you get with alien?

---

### Post by rafaelsdmf on 2006-07-06
Hey man, my advise is to use Turboprint. I had the same issue with my Canon printer, I just installed it and problem solved. 


[http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")

I know there's a guide somewhere around the forums, but right now I don't remember where is it.

I hope it helps

---

### Post by woedend on 2006-07-06
sudo alien *.rpm

---

### Post by legolas on 2006-07-07
> **christhemonkey said:**
> Let us now of any errors from these commands:
```
sudo alien package.rpm 
sudo dpkg -i package.deb 
```

Duh, can you tell I am a newbie???

Here it is:-k 
i$ sudo alien bjfiltercups-2.4-0.i386.rpm
Password:
chown: changing ownership of `bjfiltercups-2.4//usr/lib/cups/backend/canon_parallel': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/lib/cups/backend/canon_usb': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/lib/cups/filter/pstocanonbj': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/bin/bjcups': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/bin/bjcupsmon': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/bjcupsmon.glade': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24b.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24b1.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24b2.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24b3.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24bf.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24c.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24c1.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24c2.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24c3.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_24cf.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_bb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_bk.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_cy.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_el.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_er.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_low.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_low010.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_low040.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_low070.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_low_bb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_ma.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_out.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_out_bb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_pb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_pc.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_pm.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_re.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_sb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_sp.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Ink_ye.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_bb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_bk.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_cy.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_el.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_er.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_ma.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_pb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_pc.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_pm.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_re.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_sb.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_sp.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/bjcupsmon/pixmaps/Inkg_ye.xpm': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/local/share/locale/ja/LC_MESSAGES/bjcupsmon.mo': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/share/cups/model/canonpixus560i.ppd': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/share/cups/model/canonpixus860i.ppd': Operation not permitted
chown: changing ownership of `bjfiltercups-2.4//usr/share/cups/model/canonpixus990i.ppd': Operation not permitted
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
install: cannot change owner and/or group of `debian/bjfiltercups/usr': Operation not permitted
dh_installdocs: command returned error code 256
make: *** [binary-arch] Error 1
find: bjfiltercups-2.4: No such file or directory

What do you guys think?
Thanks again, and sorry for the really long post.

---

### Post by legolas on 2006-07-22
C'mon guys!  I am dying here!  Where did everybody go???

---

### Post by nalmeth on 2006-08-03
Hey Legolas

I've been reading into your issue, and it seems you have definitely followed the right path to get your printer working.

I understand it must be getting quite frustrating.

Even though Canon does not seem to support linux at all, you may have lucked out in that they have these japanese drivers, if you could only get them working.

Earlier I found a couple of posts were people had essentially the same issues you are having, and my advice is the following:

The output you're getting from alien is bizarre, and I can only conclude that this .rpm was built for an older CUPS system, as aparently many have had this driver break upgrading to dapper.
Also, being an .rpm, it was built (probably poorly) for an .rpm based system.

The way I see it, you have the following options:
- Find an older build of CUPS, and try to replace the current one in Dapper
- Find an older build of Alien, as this may be a bug in a newer version (unlikely though) 
- Downgrade to Breezy
- Install .rpm based distro like Suse or Fedora
- Pay for the TurboPrint driver's (which you can try first for free)
- Buy a new printer :p

Lastly, you may want to read Aysiu's sticky in the Absolute Beginner area, [For all those with Zero-Answer Posts]("http://ubuntuforums.org/showthread.php?t=82471") 

I know this isn't a zero answer post, but eventually people stopped posting, because the problem became somewhat obscure. Starting a new thread with all new information you have, and with the options you now have, you are bound to get some more help, as the issue now is a little less clouded. 

Also, if you manage to track down exactly why you can't get this going, please post the solution, and/or make a bug report, so that you can prevent others from going thru the same headache you are going thru.

Hope I was able to help you some, I'll try to keep an eye on your progress :)

BTW, you aren't using the 64-bit architecture are you?

---

### Post by legolas on 2006-08-04
Wow.  Thank you so much for your help.  No, I am not 64-bit.  It is a weird problem.  I think my next move will be looking into the Japanese unbuntu site and see if I can't find the answer- my Japanese is not that good though.  Thanks man

---

