---
title: "Using Proprietary Radeon drivers in 13.04 on MacBookPro8,3 (same as MacBookPro8,2) ?"
date: 2013-09-28
forum: Apple Hardware Users
---

### Post by petersphilo on 2013-09-28
Hello All,

I have been trying to install the proprietary drivers for the Radeon 6770M (on a MacBook Pro 8,3 running 13.04) with no success -- every time i restart, the screen goes black...
Everything works fine with the default 'xorg' drivers, but not the AMD ones...

Has anyone gotten these to work?

I am only interested in the Radeon, i've no use for the i915 intel chip -- need maximum performance to run X-Plane...

Any help would be appreciated!

Here are some of the things i tried:
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)
[http://askubuntu.com/questions/285609/how-to-install-amd-ati-radeon-graphics-hd-6770m-on-ubuntu-13-04-64bit](http://askubuntu.com/questions/285609/how-to-install-amd-ati-radeon-graphics-hd-6770m-on-ubuntu-13-04-64bit)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


EDIT: Note that _i have no problems using the Open Source drivers_, however, _the Proprietary drivers (ie: Catalyst or[FONT=Ubuntu Mono, monospace][COLOR=#000000] [/COLOR][/FONT]fglrx) will not function_.
It seems the proprietary drivers are needed to run X-Plane (that is my ultimate goal here)...

Thank you!

---

### Post by petersphilo on 2013-10-03
Hello All,

i tried [following these instructions]("http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069"), because it seemed promising.

i still have not succeeded in using the fglrx (AMD Proprietary) drivers, but i have figured out how to recover from the black screen without having to reinstall the whole shebang...

it is suggested [on the AMD unofficial wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide") that you remove the drivers by running the following commands:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*

```

In my case, the script on the first line did not exist because i built the drivers from beta as indicated on the [ATI Binary Drivers Howto page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

However, i had also installed the intel drivers, so i had to remove those first.

finally, with fglrx purged, i managed to re-install the default open-source drivers:
```

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

```

At least my system is functional again :rolleyes:

And, please, if anyone has succeeded in using the fglrx or Catalyst drivers on a MacBook Pro 8,3 (or 8,2 -- same card), please post any instructions you might deem useful (i don't care about the intel chip, just the Radeon).

Even if you just have suggestions of new ways to go about it that are not covered here -- any help would be greatly appreciated!

[B]Thank you!!
[/B]

---

### Post by petersphilo on 2013-10-20
Just a quick note:
i was hoping the proprietary Radeon drivers would finally work in 13.10; well, it's still the same black screen...

Please, anyone, any help would be greatly appreciated!
Cheers!

---

### Post by entangled on 2013-10-24
It's my understanding that the radeon drivers, open source and prop, select the wrong video out channel on linux systems running on some macs (my iMac 2010 at least). You will probably find a visible screen if you plug in an external monitor (I've done this with a TV on HDMI link). I don't know any way to make the driver recognize the right output.

---

### Post by petersphilo on 2013-10-25
Thank you so much for your response!
i'll definitely try this out, if that's the case, i'm certain some boot options can be passed to force the selection of the proper channel...

On second thought, 
The only thing that bugs me with your post is that i have no problems with the Open Source drivers for the Radeon, only the Proprietary drivers...

Indeed, i followed [these instructions on how to boot in efi and run the Radeon at all times (the last section called Additional settings for discrete graphics)]("https://help.ubuntu.com/community/MacBookPro8-2/Raring")...

I will check it out anyway, though...
Thank you!

---

