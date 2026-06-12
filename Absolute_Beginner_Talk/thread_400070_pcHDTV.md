---
title: "pcHDTV"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ddover on 2007-04-03
I just installed ubuntu 7.04. Everything works fantastically except for my TV Tuner
I am using the pcHDTV 5500. The picture works fairly well (I am not sure if it is possible to get a more clear picture through a patch) but it does not have any sound. I have verified that sound does work on this system. (aka I can hear the startup sound) and that all the channels on the alsamixer are up. Any advice would be much very helpful

Thanks

---

### Post by johnny4north on 2007-04-03
try the restricted drivers manager [panel>system>administration>resricted driver manager.  i would also search your synaptic package manager for 'hdtv 5500" install package, if found.  do your udates as well.  i found your drivers for the hdtv 5500 here at this link - [http://www.pchdtv.com/](http://www.pchdtv.com/)  the good news is that card will work well, but need to install packages and/or drivers.:)  good luck i will check back 9:00 Ak time.

---

### Post by ddover on 2007-04-03
OK here are more details

Asus P5L-MX mobo
adi1986a intergrated sound

It seems that the problem might be that the line and microphone jacks aren't working on my sound card. I plugged a laptop into the ports and played some music to no avail.

I downloaded the pchdtv drivers and installed them. No difference.
I wasn't able to find the restricted drivers manager.

I am currently downloading all of the updates from Synaptic manager.
i will post tomorrow when this done.

thanks in advance for your help.

---

### Post by johnny4north on 2007-04-03
here is the only way that i found to fix soundcard - dont do till some one can walk you through it!
Sound problem with HDA Intel AD1986A chip

Try putting the following into a new file inside** /etc/modprob.d/** folder (call is sound or something):
"options snd-hda-intel position_fix=1 model=3stack"
(without the quotes)
Then run in terminal {found here - panel>applications>accessorys, then Terminal.}
Code:


sudo update-modules


run updates again and then reboot your pc. 
good luck and be patient..:)

---

### Post by ddover on 2007-04-03
Almost have everything fixed.
Only problem now is that I can't play HDTV. I am using mythtv .20.
I know from experience that I have to configure the card as a DVB DTV capture card (v3.x) Unfortunetly the system does not detect the card for this. It does detect it for other kinds of set ups but they don't work for HDTV.

I read else where that I might try a modprob dvb but I am not sure what that means.

Thanks

---

### Post by johnny4north on 2007-04-03
i sorry im late.  im upgrading a friends pc.  here is a excellent web site w/ many possible solutions and a fourm to boot...:)     [http://linuxmce.com/](http://linuxmce.com/)   be back later 2:00pm  AK time.

---

### Post by ddover on 2007-04-03
I looked alot into the linuxmce system this past month. The intergration between pluto and mythtv is very interesting. Unfortently I think the software is too buggy and not useable in its current condition. I plan on checking back on that project periodically to view its progress.

I am still working on the HD problem. I am fairly certian it has something to do with installing or condifguring the pcHDTV 5500 as a DVB card. This has worked for me in Fedora Core 5. I just can't get it to work in Ubuntu.

---

### Post by johnny4north on 2007-04-03
have you installed all the packages and plug-ins for mythtv.  how to here - [http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy](http://www.mythtv.org/wiki/index.php/Installing_MythTV_SVN_on_Ubuntu_Breezy) 
i wish could be of more help.  i have a Ati aiw 32mb i tryed to install to use w/ mythtv[no-go]. i will again later this summer.  i believe you know more about this then i.  good luck.

---

### Post by ddover on 2007-04-03
ok well thanks for all your help!!! It is people like you who make the open source community as great as it is

---

