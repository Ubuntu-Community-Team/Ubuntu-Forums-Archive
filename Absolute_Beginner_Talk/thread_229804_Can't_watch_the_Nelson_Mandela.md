---
title: "Can't watch the Nelson Mandela"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-04
Hi
My computer is a Toshiba Satellite 31CDT la ptop with 20G hard drive and pentium III. I'm using the "device manager" to try to find out how much RAM I have in case that will help you understand, but I cannot find where to get that information. 

Anyway, I just installed ubuntu and there is that Nelson Mandela video so I tried to watch it. The video was not smooth at all - basically a sequece of stills - and there was no sound until finally half way through the video some sound started. I had Firefox running and another window open about the system, so I closed everything except the video (which had opened by the default video player). Still though the video was not at all smooth and I could catch only parts of sentances. My computer had no such problems with Windows 2000 or Windows ME so it would surprise me if my computer is somehow to slow.

Grateful for any remedy, as I see this may be a symptom of worse things to come.
Justin

---

### Post by benuski on 2006-08-04
Have you installed the codecs for wmv?  If not, go [here]("https://help.ubuntu.com/community/RestrictedFormats") and install the w32 codecs, and that should help you out.

---

### Post by cantormath on 2006-08-04
> **woodlandjustin said:**
> Hi
My computer is a Toshiba Satellite 31CDT la ptop with 20G hard drive and pentium III. I'm using the "device manager" to try to find out how much RAM I have in case that will help you understand, but I cannot find where to get that information. 

Anyway, I just installed ubuntu and there is that Nelson Mandela video so I tried to watch it. The video was not smooth at all - basically a sequece of stills - and there was no sound until finally half way through the video some sound started. I had Firefox running and another window open about the system, so I closed everything except the video (which had opened by the default video player). Still though the video was not at all smooth and I could catch only parts of sentances. My computer had no such problems with Windows 2000 or Windows ME so it would surprise me if my computer is somehow to slow.

Grateful for any remedy, as I see this may be a symptom of worse things to come.
Justin

in terminal
for memory
```

cat /proc/meminfo

```

hardrive
```
cat /proc/partitions
```
or 
```
df -h
```

for video/audio/java/flash codec, this will install and config it for you.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by woodlandjustin on 2006-08-05
> **benuski said:**
> Have you installed the codecs for wmv?  If not, go [here]("https://help.ubuntu.com/community/RestrictedFormats") and install the w32 codecs, and that should help you out.

I think the Mandela video is ogg. At least it says "ogg". So is this still relevant, to do the Windows codecs thing?

Anyway I at least tried doinf what you said, but failed anyway. On the link you refer to it says

"    *

      You can download the package from an unoffical repository and install it with dpkg:

    *

      wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
      sudo dpkg -i w32codecs_20060611-0.0_i386.deb
"

I barely understand what that means, but I get that I sould perhaps open a terminal and type in what they said. When I type in wget -c and hit return, it says
wget: missing URL
Usage: wget [OPTION]... [URL]...

By the way, also how do you copy and paste when using the terminal? It would make my hopeless errors a lot quicker to accomplish!
Thanks
Justin

---

### Post by moma on 2006-08-05
Step 5) here 
o--> [http://www.futuredesktop.org/ubuntu6.06.html]("http://www.futuredesktop.org/ubuntu6.06.html")
Install also proper driver for your graphic card.

Copy/Paste in a terminal:
Use right mouse button and popup menu.

---

### Post by woodlandjustin on 2006-08-05
That's really wierd. I just viewed my post, and it displays this:

wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

but on the actual page I copied and pasted it from ( [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ), it appears not like that but like this:

wget -c 
[http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

Is there something wrong with the page? Or my Ubunbuntu copy and paste function?
Anyway I am working on the assumption that the instructions are followable through the use of intelligent guesswork, so as my previous attempt did not work, now that I see the two first lines may have actually meant to be one line, I enter that one line ( wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb) ) into the terminal. It says "wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
--01:11:51--  [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
           => `ubun...1plf1_i386.deb'
Resolving packages.freecontrib.org... 88.191.21.245
Connecting to packages.freecontrib.org|88.191.21.245|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:11:54 ERROR 404: Not Found.



What am I doing wrong?
Thanks
Justin

---

### Post by woodlandjustin on 2006-08-05
> **moma said:**
> Step 5) here 
o--> [http://www.futuredesktop.org/ubuntu6.06.html]("http://www.futuredesktop.org/ubuntu6.06.html")
Install also proper driver for your graphic card.

Copy/Paste in a terminal:
Use right mouse button and popup menu.

I followed your instructions and it says "
Install Automatix and look in the Applications [...]"

But I do not understand how to install Automatix. I did a search for it with the Synaptic Package Manager but it could find nothing under that name. How do I instal it?
Thanks
Justin

---

### Post by Lord Illidan on 2006-08-05
Automatix is on the forums. 
[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=Automatix+download](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=Automatix+download)

About your problem, it might also be a dma related problem.

Do a quick ```
sudo hdparm /dev/hd*
``` and post output here.

---

### Post by catlett on 2006-08-05
> **woodlandjustin said:**
> That's really wierd. I just viewed my post, and it displays this:

wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

but on the actual page I copied and pasted it from ( [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ), it appears not like that but like this:

wget -c 
[http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

Is there something wrong with the page? Or my Ubunbuntu copy and paste function?
Anyway I am working on the assumption that the instructions are followable through the use of intelligent guesswork, so as my previous attempt did not work, now that I see the two first lines may have actually meant to be one line, I enter that one line ( wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb) ) into the terminal. It says "wget -c [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
--01:11:51--  [http://packages.freecontrib.org/ubun...1plf1_i386.deb](http://packages.freecontrib.org/ubun...1plf1_i386.deb)
           => `ubun...1plf1_i386.deb'
Resolving packages.freecontrib.org... 88.191.21.245
Connecting to packages.freecontrib.org|88.191.21.245|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:11:54 ERROR 404: Not Found.



What am I doing wrong?
Thanks
Justin

You did it correctly, there is a server issue on the other end.
wget is a downloader. Much like the ftp downloaders that are popular now. you enter wget and the url where the package is and wget goes there and downloads.
In your case the repo/server that was holding the package was down.
Use the Dapper Guide for all your multimedia if you have issues with automatix. It is cut/paste type of stuff but it helps you learn.
You can highlight and right click to cpoy/paste or you can highlight/drag into the terminal the text and it will print out.[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by woodlandjustin on 2006-08-05
> **Lord Illidan said:**
> Automatix is on the forums. 
[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=Automatix+download](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=Automatix+download)

About your problem, it might also be a dma related problem.

Do a quick ```
sudo hdparm /dev/hd*
``` and post output here.

That results in this:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38760/16/63, sectors = 39070080, start = 0

/dev/hda1:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38760/16/63, sectors = 37575972, start = 63

/dev/hda2:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38760/16/63, sectors = 2, start = 37576035

/dev/hda5:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 38760/16/63, sectors = 1493982, start = 37576098

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


Sounds kind of funny, "invalid argument"!
Thanks
Justin

---

