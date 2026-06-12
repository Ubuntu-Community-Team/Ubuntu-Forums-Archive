---
title: "Ubuntu 7.04 not playing DVDs, not seeing VCDs"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-23
I have downloaded EVERYTHING I could find to enable Ubuntu 7.04 to be able to play VCDs and DVDs:

MPlayer
VLC media player
"Ubuntu restricted extras"
libdvdcss2
w32 codecs

Ubuntu 7.04 recognizes DVDs fine, although it does not play them properly. 

In Totem media player there is no sound, it only give selected still scenes of the DVD. It will not play the DVD as a moving picture.   

MPlayer gives the following error when I try to open the DVD to play it:

"Error opening/initializing the selected video_out (-vo) device"

VLC Media Player, similar to Totem, gives a few still images but will not play the DVD as a moving picture. And no sound.

But Ubuntu is not even seeing VCDs. Ubuntu will not even mount the VCD in the DVD ROM drive, as it says "there is no media in the drive". While in my Windows 98 on the same computer, all these DVDs and VCDs play just fine-- with sound and all.

---

### Post by chamberlain2006 on 2007-05-23
You also need the packages libdvdplay, libdvdnav, and libdvdread.  (There may be numbers at the end of those packages).  Installing those may help.

---

### Post by BangBang on 2007-05-23
Maybe you need to install certain video codecs

EasyUbuntu is a nice easy way to get em.

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

hope this helps

---

### Post by nonewmsgs on 2007-05-23
you need the xine codecs.

---

### Post by chamberlain2006 on 2007-05-23
EasyUbuntu is just a silly shortcut that may break your system.  Install the packages I reccomended and it will probably fix many of your problems.

---

### Post by rohan! on 2007-05-24
i have a similar problem. It is not a codec problem as has been suggested; it is related to compiz i believe. if you turn off desktop effects it should work.

alternately you can change your video driver in mplayer using the -vo option in the command line (for example: $ mplayer -vo x11 dvd://1 ) i have had very limited success with two of them - x11 and gl . 

-- x11 there is no change in scale of the video if i change the size of the window, otherwise it is fine. you can do all the fancy compiz stuff like transparency etc.
-- gl i get a lot of interference from the desktop and it crashes if i try and do anything fancy, i recommend against it, but try.

to make any permanent changes to mplayer you should edit the mplayer configuration file: 
$ sudo gedit /etc/mplayer/mplayer.conf
go to the first line of video settings and change it to what works best for you.

sorry i can't help more, but at least it helps identify the problem

---

### Post by siglost on 2007-05-24
I am having a similar problem.  The drive quit functioning as a DVD player in windows.  I figured it was the driver or something and never bothered to fix it.  The drive is a samsung DVD/CD RW combo, and it burned the iso for my feisty install, then installed over XP.

However, it doesnt recognize a DVD in the drive.  I put a CD in there, and its immediately recognized.  DVD, nothing.  mount /dev/hda which is the DVD drive in fstab, and I get : no medium.  Any pointers would be great.  It took about 3 hours to set up ATI drivers, and its bedtime now.

Thanks in advance

---

### Post by rohan! on 2007-05-24
I have sorted it... 

Changed my video driver to x11 and enabled software scaling. It's cpu intensive, but works for me :)

$ sudo gedit /etc/mplayer/mplayer.conf

go to the video settings section and change the video driver to x11:

```
# Specify default video driver (see -vo help for a list).
vo=x11
```

find the line saying enable software scaling and delete the hash in front of zoom=yes as below:

```
# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
zoom=yes
```

---

### Post by prepaid18 on 2007-05-25
Hi everyone..

I used to play VCDs in Dapper with VLC w/o any much of a problem but with Feisty, it got worst..

I been thru w32 codecs, etc. installation (as well as trying automatix), but to no avail.. though I can play them via cli: "mplayer vcd;//2".. but I want thru VLC..

What I have is quite old PC w/ celeron and 480M RAM..

Any suggestions? Thanks for the help..

---

### Post by rohan! on 2007-05-25
hey prepaid18, what exactly is the problem? if you run vlc from the terminal what error message do you get??

---

### Post by prepaid18 on 2007-05-25
> **rohan! said:**
> hey prepaid18, what exactly is the problem? if you run vlc from the terminal what error message do you get??

Hey, rohan.. thanks for the intention.. the problem is, i cant play vcd if i open vlc thru "Applications" thing.. but when i played it thru cli, it just did!! AMAZING isn't it? :D

Anyway, i still want to resolve the issue though. Any thoughts? Appreciate it bro. Thnx

---

### Post by prepaid18 on 2007-05-25
> **prepaid18 said:**
> Hey, rohan.. thanks for the intention.. the problem is, i cant play vcd if i open vlc thru "Applications" thing.. but when i played it thru cli, it just did!! AMAZING isn't it? :D

Anyway, i still want to resolve the issue though. Any thoughts? Appreciate it bro. Thnx

And one more thing, when i play it thru cli, the audio is not good.. I got "choppy" sounds... :(

---

### Post by rajeev1204 on 2007-05-25
Feisty not mounting vcd is a confirmed bug in ubuntu . 

U can manage to play it in VLC or Mplayer through the command line but it plays bad.

---

### Post by prepaid18 on 2007-05-25
> **rajeev1204 said:**
> Feisty not mounting vcd is a confirmed bug in ubuntu . 

U can manage to play it in VLC or Mplayer through the command line but it plays bad.

Oh, really?!? Hope they can fix it...

Yeah playing VLC thru cli (as from experience) is really bad, though I quite satisfied with Mplayer though..

Could someone out there point us to the right direction?:?:

---

### Post by rajeev1204 on 2007-05-25
No directions :)

U have to wait till the bug is fixed :)



[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786)

---

### Post by prepaid18 on 2007-05-26
> **rajeev1204 said:**
> No directions :)

U have to wait till the bug is fixed :)



[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786)

Hahaha.. I guess so.. Anyway, thanks!:D

---

### Post by yesudeep on 2007-05-27
There are [COLOR="Red"]**three**[/COLOR] ways to **[COLOR="Red"]mounting and playing[/COLOR]** VCDs that I have figured out so far:

**1. MPlayer**

[http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html]("http://www.mplayerhq.hu/DOCS/HTML/en/vcd.html")

```

sudo apt-get install mplayer
mplayer vcd://2 -cdrom-device /dev/sdc0

```

That's one way.

**2. CDFS**

Windows emulates the reading of raw tracks on video CDs. This feature is not available in the official Linux kernel.  There is, however, a filesystem driver called CDFS that allows you to mount VideoCDs and read off of them.  You can find more information here: [http://trappist.elis.ugent.be/~mronsse/cdfs/]("http://trappist.elis.ugent.be/~mronsse/cdfs/")

_Setup_

```

sudo apt-get install build-essential vlc
wget -c http://trappist.elis.ugent.be/~mronsse/cdfs/download/cdfs-2.6.19.tar.bz2
tar jxvf cdfs-2.6.19.tar.bz2
cd cdfs-2.6.19
make
sudo mkdir /media/cdfs

```

_Playback_
```

sudo insmod ~/cdfs-2.6.19/cdfs.ko
sudo mount -t cdfs -o ro /dev/scd0 /media/cdfs
vlc /media/cdfs/videocd-1.mpg

```

Your series of commands may vary depending on your system configuration.  Please 
make the appropriate changes.

**3. K3B**

You can easily use K3B to mount and **rip** VCD tracks to an ISO before mouting the ISO or converting it to another format and playing the VCD tracks.

The exact information is discussed here: [http://ubuntuforums.org/showthread.php?t=450537]("http://ubuntuforums.org/showthread.php?t=450537")

**Note to moderator:**  Please move this thread to "Multimedia and Video" and perhaps make a sticky out of it.

Regards,
Yesudeep.

---

### Post by edwinava1964 on 2007-06-15
:D
very new to Ubuntu, using 7.04. A great community here. I do not have a DVD drive but still not able to play VCD... something about a "VCD source ...." cannot remember exactly. I was not able to use my flash drive last week, then this week after some 10 updates and reboots, I can use my flash drive.

---

### Post by zek725 on 2007-06-16
> **siglost said:**
> I am having a similar problem.  The drive quit functioning as a DVD player in windows.  I figured it was the driver or something and never bothered to fix it.  The drive is a samsung DVD/CD RW combo, and it burned the iso for my feisty install, then installed over XP.

However, it doesnt recognize a DVD in the drive.  I put a CD in there, and its immediately recognized.  DVD, nothing.  mount /dev/hda which is the DVD drive in fstab, and I get : no medium.  Any pointers would be great.  It took about 3 hours to set up ATI drivers, and its bedtime now.

Thanks in advance

DVD/CDRW combo drives use different lasers for DVD and CDR/RW. It seems the DVD laser to read DVDs is not functioning anymore.

---

### Post by snktagarwal on 2008-05-27
Hey pple...... i am using Ubuntu which i modofied myself.... well the GUI of VLC seem to have a problem i suppose when i run the file in CLi by vlc vcd:///dev/<devive, in my case scd0> i am able to do it fine.... though the sound sometimes hangs.... but it's good i suppose!!!! See to the sound problem though!

---

