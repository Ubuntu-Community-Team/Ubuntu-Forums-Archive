---
title: "Need Help Installing Libdvdcss 1.2.5"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by glubrani on 2007-03-19
I did all this :

    *

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui


but I need help installing Libdvdcss 1.2.5

it downloads as a TAR and I'm able to extract it to a folder but what do I do to install it now?

---

### Post by al1b1 on 2007-03-19
go to [www.getautomatix.com](www.getautomatix.com) download it and it will install all the codecs for you.

what you have is a source code file whcih needs to be decrompressed, and then you cd to the directory, ./configure, make, sudo make install however copiling from source is not advisable use atuomatix

---

### Post by Scunizi on 2007-03-19
If you're just trying to playback DVD check this link out.  It's a little easier and will get you up and running in no time.  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by glubrani on 2007-03-19
I downloaded automatix and during install there is a warning that I need to pay
for the codecs or I will be using them illegally. Is this true and if so, how do I pay for them?

I went to [https://help.ubuntu.com/community/Re...ts/PlayingDVDs](https://help.ubuntu.com/community/Re...ts/PlayingDVDs) and they don't say anything about the codecs being illegal if I don't pay for them. What's going on?

---

### Post by aysiu on 2007-03-19
Just paste these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://medibuntu.sos-sts.com/repo/pool/edgy/free/i386/libdvdcss2_1.2.9-2medibuntu2_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
``` If you'd rather do it the proper way, follow these instructions:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by glubrani on 2007-03-19
ok, IT WORKS ! When I use GXine there's a flicker every few seconds so I did an auto start with Totem and it plays well (picture is beautiful using Trinitron crt). 

Thanks for all the help  {8^ )

Only question is, what about that codec warning when I used automatix ?

---

### Post by Scunizi on 2007-03-19
The codecs are propriatory... like MP3 is a propriatory format for audio.  When you buy a copy of windows or a computer with win installed part of the price is to pay for the licensing.  There are countries like the USA where some if not all these codecs are illegal to use without a license.  The gray area is if you already own a copy of windows you've already paid for the licensing and therefore should be allowed to use it despite the system it's on..  I think I've got all that right.  If not someone will come along and make corrections.... Happy watching!  :popcorn:

---

