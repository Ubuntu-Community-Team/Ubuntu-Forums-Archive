---
title: "Unable to play VCDs"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by shivkumars on 2006-12-18
I have recently installed Ubuntu 6.06 Dapper Drake and searching on Ubuntu website, I have installed restricted format, win32codecs and DVD packages as suggested [ here ](https://help.ubuntu.com/community/RestrictedFormats). I have also installed VLC player and Mplayer. After all this I am able to play almost all audio formats, windows format videos and even DVDs but I am unable to play any VCDs. I searched the forum and found one partially [ relevant thread ](http://www.ubuntuforums.org/showthread.php?t=320543), but this also didn't help. Please help me play VCDs.

Thanks in Advance

---

### Post by shivkumars on 2006-12-18
No reply till now,
guys please help me

---

### Post by jimrz on 2006-12-18
> **shivkumars said:**
> No reply till now,
guys please help me

you might getting VLC media player from synaptic. it wil play nearly anything and, I believe, it even comes with it's own codecs

---

### Post by shivkumars on 2006-12-19
VLC player doesn't help, nor I am able to play any VCDs using Mplayer. The same VCDs are playing nicely in my other OS but I would like to play them in Ubuntu.

---

### Post by vruum on 2006-12-19
when you put the cd in the drive, does it show up on the desktop?

---

### Post by Ashrael on 2006-12-19
Eh, didn't read enough before i posted...(shame)

---

### Post by vivin_west on 2006-12-19
Install Totem-xine and w32codecs. You should be able to play. What is the format of the file in your VCD?

---

### Post by mand0 on 2006-12-19
What if you convert the VCD movie to another format?

Look here for more help:

[http://tinyurl.com/yatp9q](http://tinyurl.com/yatp9q)

---

### Post by shivkumars on 2006-12-19
> 
Posted by vruum

when you put the cd in the drive, does it show up on the desktop?

Yes, it does shows up on the desktop and also tries toplay by Totem Media Player but fails, btw i mentioned in the first post that I am able to watch DVDs
> 
Posted by vivin_west

Install Totem-xine and w32codecs. You should be able to play. What is the format of the file in your VCD?

Already installed Totem-xine and w32codecs using universe and multiverse repository. I also uninstalled and reinstalled the codecs, but no use. I am still struck at the same point.

I checked the format using g-spot. it reported the video format as mpeg-1.

> 
Posted by mand0

What if you convert the VCD movie to another format?

Look here for more help:

[http://tinyurl.com/yatp9q](http://tinyurl.com/yatp9q)


I can try out your suggestion and report back,but that doesn't seem to be a feasible solution to me.

Guys any more suggestions, Btw totem player is giving some error message, whether that will help inidentifying and solving the problem.

---

### Post by TooRight on 2006-12-19
Have you tried installing automatix? It has access to a couple multimedia, nonfree audio and video codecs packages, and it even does the work for ya!! :D

---

### Post by shivkumars on 2006-12-19
Here is the output of my attempt to play video cd with different players installed in the system.

0.Upon initially inserting the VCD, the error is
**Totem could not play 'vcd:///media/cdrom0'.**
*No URI handler implemented for "vcd".*

1.Xine : Nothing happens on playing the VCD, the player automatically gets closed. Upon selecting the file separately the error is :
**The xine engine failed to start.**
*No demuxer found - stream format not recognized.*

2.Totem movie player: Upon selecting to play VCD, the error is 
**Totem could not play 'vcd://'.**
*No URI handler implemented for "vcd".*
Also if I try to play the file by selecting it separately
**Totem could not play 'file:///media/cdrom0/mpegav/avseq01.dat'.**
*Could not read from resource.*

3.Ogle: Nothing happens upon selecting the “Open Disk” option. Same effect if I try to open the file from VCD. The VCD spins up and stops spinning in few seconds

4.Real Player: The player simply gets closed upon trying to play the video file.

5.VLC Player: The CD drive keeps up spinning on selecting the option “Open Disk -> VCD” again on selecting the video file, the Cd drive keeps spinning without playing the video file.

6.Mplayer: Selecting to play VCD disk plays the file for few seconds and give the error
**Mplayer interrupted by signal 11 in module: decode_video**
followed by 
[b] -Mplayer crashed by bad usage of CPU/FPU/RAM.
Recompile Mplayer with –enable-debug and make a 'gdb'
backtrace and 
disassembly. Details in DOCS/HRML/en/
bugreports_what.html#bugreports_crash.[/b]
and finally with this message
[b] -Mplayer crashed. This shouldn't happen.
It can be a bug in Mplayer code_or_in your drivers_or_in 
your
gcc version. If you think it's Mplayer's fault, please read 
DOCS/HRML/en/bugreports.html and follow the instructions
there. We cant and 
won't help unless you provide this information when reporting
a possible bug.[b]

See guys, if this helps. I am running Ubuntu on IBM laptop R40e with ATI Radeon 330 video chipset.

Waiting  for guidance to solve this problem.

^^TooRight: I have heard that automatix is buggy in nature and ususally ends up creating more problem than solving them. BTW can i install automatix through apt-get ???

---

### Post by mand0 on 2006-12-19
> **shivkumars said:**
> 
^^TooRight: I have heard that automatix is buggy in nature and ususally ends up creating more problem than solving them. BTW can i install automatix through apt-get ???

I've used automatix2 with no problems.  I recommend you try installing all the codec related options that it comes with.  Search for automatix in synaptic and or add/remove programs.

Let us know how it goes.

---

### Post by shivkumars on 2006-12-20
I am unable to find automatix either through apt-get or synaptic... i am downloading Kaffiene to try my luck with it. 
Anyways guys can you make some sense out of the error messages which i have posted earlier. May be that will be more helpful

---

### Post by PotOfVB on 2006-12-20
hi there,

automatix site
[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

see this thread on ubuntuforums
[http://www.ubuntuforums.org/showthread.php?t=80295]("http://www.ubuntuforums.org/showthread.php?t=80295")

Another way to look at vcd's, this is is not the best solution, but should work:

open vlc or other media player that supports mpeg 1/2 video (I know you tried totem, but do other media players work?)

goto file open

browse vcd cd, In the folder _Mpegav_, find _*.dat_ files, these are your mpeg video files

open, should play, but you will not be able to access menus this way

---

### Post by TooRight on 2006-12-20
Give the Automatix a go babe, you'll loveeeeeeeeeeee it!! It has saved me many headaches!! :D

---

### Post by kebayan on 2006-12-24
Have you tried GXINE?

Play it from File > VCD, and it should play VCD from your cdrom device.

---

### Post by bottleman on 2006-12-24
I was having similar error messages until I tried GXINE.  now seems to be working fine.  Thanks, kebayan.

---

### Post by nayk on 2007-01-20
I finally got VCDs to work by following these instructions. [http://alternativenayk.wordpress.com/2007/01/20/playing-vcds-on-ubuntu-linux-how-to/]("http://alternativenayk.wordpress.com/2007/01/20/playing-vcds-on-ubuntu-linux-how-to/")

Hope it works for you.

---

