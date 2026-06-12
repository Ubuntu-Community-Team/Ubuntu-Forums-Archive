---
title: "updates are failing so I can't install any new applications"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by feistyalana on 2007-06-08
Hi -- I am very new to Linux.  I just got the Dell Inspiron E1505 with Ubuntu 7.04 pre-installed.  I have been trying to install software both through add/remove programs and synaptic, but I'm not having any luck.  Every application says "program cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."  I looked in the forums to see how to address this, and the answer I found was to run apt-get update in the terminal.  I did that, but some indexes failed.  Here is what it said on the terminal (I skipped past the updates that were successful to take up less space):

Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1307kB]
94% [21 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  Sub-process gzip returned an error code (1)
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
98% [22 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1307kB]
98% [23 Packages gzip 0] [Waiting for headers]                      1036kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
  Sub-process gzip returned an error code (1)
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]          
99% [Waiting for headers]                                           1036kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
  Sub-process gzip returned an error code (1)
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages [2277B]   
99% [25 Packages gzip 0]                                            1036kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages              
  Sub-process gzip returned an error code (1)
Fetched 104kB in 4m52s (356B/s)                                                
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone please help me with this?  I am very frustrated that I'm not able to install any new applications.  I mainly want to be able to play mp3s and watch DVDs, but I'd also like to just play around and see what else Ubuntu has to offer!  Everything I've read makes it seem like it's very easy to install programs, but I haven't been able to install a single one so far, apparently because of these updates failing.  What can I do?  Thanks in advance for your assistance.

Alana

---

### Post by pbw on 2007-06-09
edit /etc/apt/sources.list, switch to using a different mirror and then run update. See if that helps.

---

### Post by zvacet on 2007-06-09
Try this source list
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by feistyalana on 2007-06-09
Could you please explain how to do that, or point me somewhere that I can read step-by-step directions?  I don't know how to change to another mirror.  I already had added the extra repositories under software sources.  Thanks!

---

### Post by zvacet on 2007-06-09
```
sudo gedit /etc/apt/sources.list
```

After that you can delete your source list by edit>mark all>delete . After that copy/paste source list from link I posted to you and save file.In terminal type

```
sudo aptitude update
```

to change mirror go to the system>administration<software sources and select any mirror you want.I think you have choices between main,local and other.Try local because it should be faster than others but if you have no luck with it try main or some other (if you choose other try to select one near your country).

---

### Post by feistyalana on 2007-06-09
Thank you very much.  I followed your instructions, but after I typed "sudo aptitude update" I got the following errors:

E: Malformed line 14 in source list /etc/apt/sources.list (dist)
E: Couldn't read list of package sources

What next?  :(

---

### Post by feistyalana on 2007-06-09
I just tried it again to make sure that I cut and pasted everything correctly, and this time I got a different error when I ran "sudo aptitude update".  It said:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory . . are you root?

---

### Post by theredcross on 2007-06-09
that last error means apt is running somewhere on the system, the simple way to fix that is to log out and back in again. try that and then running ```
sudo aptitude update
``` once again.

---

### Post by feistyalana on 2007-06-09
Sorry, my connection keeps timing out.  I will let you know how it goes . . .

Thanks again for all your help, guys!

---

### Post by feistyalana on 2007-06-10
Partial success!  I was able to download XMMPlayer, but I still can't get GStreamer.  I'm very happy that I can now play mp3s, but I would still like to be able to play DVDs.  Anything you would suggest trying next?

Thanks again,

Alana

---

### Post by space_boy on 2007-06-10
You could try by using Automatrix ([http://www.getautomatix.com/](http://www.getautomatix.com/)). This script can help in installing many of the mp3/dvd codecs you need. Follow the install instructions on website for your version of Ubuntu. I have used it for both Dapper and Feisty with no problems. Good luck.

---

### Post by MenZa on 2007-06-10
I won't recommend using Automatix; it's a dangerous tool and often breaks things. Instead, I suggest you add the Medibuntu repository and read [this](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

---

### Post by space_boy on 2007-06-10
> **MenZa said:**
> I won't recommend using Automatix; it's a dangerous tool and often breaks things. Instead, I suggest you add the Medibuntu repository and read [this](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

Thanks for the info:p

---

### Post by feistyalana on 2007-06-10
Thanks for the info, MenZa -- I will try the suggestions on that page later tonight.

---

### Post by djchandler on 2007-06-10
> **feistyalana said:**
> Thanks for the info, MenZa -- I will try the suggestions on that page later tonight.

Have you tried installing VLC media player and its mozilla plug-in ? I haven't run into anything it won't play, audio or video. It should be in the default repositories as it is licensed under the GNU General Public License. Run Synaptic and do a search for VLC. I'm interested to know if it has been included in your default repositories that Dell installed. I don't think I had to add that repository.

It has lots of options, so you might want to read about it first. Go to

[http://www.videolan.org/](http://www.videolan.org/)

---

### Post by feistyalana on 2007-06-10
Okay, I tried "sudo apt-get install libdvdread3 libxine1-ffmpeg" and this is what I got:

Package libdvdread3 is not available, but is referred to by another package.  This may mean that the package is missing, had been obsoleted, or is only available from another source.
E: Package libdvdread3 has no installation candidate

djchandler: nope, nothing comes up when I search for VLC in Synaptic.

---

### Post by abn91c on 2007-06-10
on a root terminal type apt-get check, if it suggests a command to use type that at the prompt.
also try apt-get update, and apt-get upgrade

---

### Post by feistyalana on 2007-06-10
For both apt-get check and apt-get update I get the following errors:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Do I have to do something specific to log in as "root"?  I am very, very new to this.  I have just been using the sudo command.  (I am the only user).

---

### Post by abn91c on 2007-06-10
type sudo in front of the commands:
sudo apt-get check
sudo aptget update
also on the terminal windows if you have a sessions on the toolbar clikc there then select new root shell, that is if you are using kconsole :-)

---

### Post by Moop on 2007-06-10
You may want to take a look at this thread. [http://ubuntuforums.org/showthread.php?t=470043]("http://ubuntuforums.org/showthread.php?t=470043")

They seemed to be having the same problem and worked it out.

---

### Post by feistyalana on 2007-06-10
Yes, I've been doing that.  I realized my internet connection went down (on the laptop where I'm using Linux and a wireless connection; I'm on this forum on my desktop, which uses Windows and is connected by cable), so maybe that's why I can't update right now.  I'll try again tomorrow.

---

### Post by feistyalana on 2007-06-11
Okay, I'm still having the same problem.  When I run aptitude update, I'm still getting packages that are failing (with the "not in gzip format" error).  I've tried switching mirrors, logging out and logging back in, running aptitude update, apt-get update and apt-get check.  

apt-get check did not produce any prompts -- it just said:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

There are just a few packages I can't seem to get.  Here are the errors I get from aptitude update:

```
Get:26 http://us.archive.ubuntu.com
 feisty/main Packages [1307kB]               
Get:27 http://us.archive.ubuntu.com feisty/universe Packages [4912kB]           
15% [26 Packages gzip 0] [27 Packages 130961/4912kB 2%]           7481B/s 21m23s

gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages                           
  Sub-process gzip returned an error code (1)
Err 
http://us.archive.ubuntu.com feisty/universe Packages                       
  Connection timed out
Get:28 http://us.archive.ubuntu.com feisty-updates/main Packages [24.5kB]
14% [28 Packages gzip 0]                                 185kB/s 49710d 6h27m24s
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty-updates/main Packages                   

  Sub-process gzip returned an error code (1)
Fetched 1320kB in 33m4s (665B/s)                                                
Reading package lists... Done
```

Also, when I try "sudo apt-get install libdvdread3 libxine1-ffmpeg" I still get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate
```

Does anyone else have any ideas about why I can't get all the packages I need?

Thanks for your continuing assistance!

---

### Post by abn91c on 2007-06-11
did you try on adept manager> adept.>manage repositories and enabling other repositories

---

### Post by feistyalana on 2007-06-12
They are enabled except for "source code."

---

### Post by djchandler on 2007-06-15
Is there any chance of getting a router and sharing that cable connection with your laptop on a local  area network? The download times we are seeing seem awfully long. At least part of the reason the downloads are failing is you are getting timed out and losing your connection. How is the cable modem connected to your Windows box? If it is USB, you may be able to share the internet connection in Windows, making it the gateway, and connect to the windows box via ethernet. If the cable modem is connected by ethernet, go with the router. It will make you a lot happier. "Connection timed out" sticks out like a sore thumb to me.

---

### Post by feistyalana on 2007-06-24
Sorry, I was away on a trip out of town and put this aside for a while.  I hooked the laptop up to my cable Internet connection and was able to get the updates I needed.  I'm playing DVDs in Totem now, yay!  I installed mplayer, since I read that was better, but I haven't been able to figure out how to get the DVD to play in mplayer instead of Totem.  Not a big deal -- I'm just happy I can play movies at all!  But I feel like it should be simple to switch to another player and feel kind of dumb . . .

Thanks everyone for your help!!

Alana

---

### Post by feistyalana on 2007-06-24
Is there a way for me to mark this thread as "resolved"?

---

