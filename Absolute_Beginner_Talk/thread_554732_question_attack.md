---
title: "question attack"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Tessea on 2007-09-19
Ok, this is a thread of many questions. I thought I might as well make just one thread instead of bombarding you with a thread for each different question, so here goes.


One! When I try to use Serpentine to burn CDs, it won't work. I can get Serpentine to read a playlist and prepare files to burn to disc, 
[[IMG]http://img217.imageshack.us/img217/5552/onevg5.th.png[/IMG]](http://img217.imageshack.us/my.php?image=onevg5.png)
but when I insert any kind of blank CD (brand new, out of the package), R or RW, it tells me this:
[[IMG]http://img502.imageshack.us/img502/848/twock6.th.png[/IMG]](http://img502.imageshack.us/my.php?image=twock6.png)
This is with literally any blank CD.


[SOLVED]
Two! I have been running a profile on [www.last.fm](www.last.fm) for the last two and a half years and would really like to get the plug-ins installed so I can continue to do so on ubuntu. I went to the website and downloaded the package for feisty ( [http://www.last.fm/download/](http://www.last.fm/download/) ). The package installed fine, but now (haha) I don't know what to do with it. Where is it? How do I start running it? I feel seriously retarded for having to ask this, but so it goes...

My third question was to do with Soulseek and Nicotine+ but I found this thread: [http://ubuntuforums.org/showthread.php?t=12656&highlight=slsk](http://ubuntuforums.org/showthread.php?t=12656&highlight=slsk) and it looks like that will answer any/all of my questions.

Thanks for any/all help, you guys have been great thus far in answering all of my questions (:

---

### Post by tenjin1 on 2007-09-19
For Sepentine:

Go to Edit -> Preferences and make sure the right device is selected that has the blank disc.

As for the plugin for lastfm....go to your Firefox (assuming you are using firefox for your web browser) download directory which is where the plugin you download is located. In firefox go to Edit-> Preferences-> Main tab to find out where the download directory is. Then fire up a terninal and

```
cd /home/yourusernamehere/firefoxdownloaddirectory
```
 once in the download directory install the .deb package
```
dpkg -i lastfm_1.3.2.11_i386.deb

```

---

### Post by Tessea on 2007-09-19
Serpentine: Everything is selected correctly. Unfortunately, I only have one working drive and that's the one that was selected, so... :(

Last.FM: my download directory is set to desktop, which is why I'm so confused about where the package went. I tried
[quote=]
cd / home/tess/desktop[/quote] in terminal

and got [quote=]tess@tess-desktop:~$ 
tess@tess-desktop:~$ cd /home/tess/desktop
bash: cd: /home/tess/desktop: No such file or directory
tess@tess-desktop:~$ cd/home/tess/desktop
bash: cd/home/tess/desktop: No such file or directory
tess@tess-desktop:~$ dpkg -i lastfm_1.3.2.11_i386.deb
dpkg: requested operation requires superuser privilege
tess@tess-desktop:~$ 
[/quote]

also tried
[quote=]tess@tess-desktop:~$ cd/home/tess/firefoxdownloaddirectory
bash: cd/home/tess/firefoxdownloaddirectory: No such file or directory
tess@tess-desktop:~$ 

[/quote]

---

### Post by mikewhatever on 2007-09-19
Terminal in Ubuntu is case sensitive, so try cd /home/tess/Desktop

---

### Post by Steveway on 2007-09-19
Most players on Linux have Last.fm support out-of-the-box.
Rythmbox, Amarok, BMPX(not sure)...

---

### Post by Tessea on 2007-09-19
Really? If so, how do I activate last.fm? I've been using rhythmbox...


I ran that in terminal and it gave me
> tess@tess-desktop:~$ cd /home/tess/Desktop
tess@tess-desktop:~/Desktop$ dpkg -i lastfm_1.3.2.11_i386.deb
dpkg: requested operation requires superuser privilege
tess@tess-desktop:~/Desktop$ 


how do I log in as root? Because I assume that's what 'requires superuser privilege' is saying

---

### Post by Maestro23 on 2007-09-19
> **Tessea said:**
> Really? If so, how do I activate last.fm? I've been using rhythmbox...


I ran that in terminal and it gave me


how do I log in as root? Because I assume that's what 'requires superuser privilege' is saying

> sudo dpkg -i packagename

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by tenjin1 on 2007-09-19
Yea I dont know anything about that lastfm site..but as mentioned it would seem that there should already be support for it. But it looks like its proprietary hence the linux feist .deb package download...so not sure. May want to install mplayer or totem plugin in firefox to see. 

But anyway to install that plugin you downloaded..try:

```
cd ~/Desktop
```

then

```
sudo dpkg -i lastfm_1.3.2.11_i386.deb
```

---

### Post by mocoloco on 2007-09-19
I had the same problem with burning CDs.  Well not *had*, still *have*.  My problem was with the Nautilus built-in CD burner.  I'm not sure if Serpentine uses the Nautilus burner on the backend, but I know there are other apps that do, like Brasero.  My workaround was to install and use Gnomebaker, which apparently had a different backend.
There's a bug  about this issue [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109763").

One supposed fix was to open gconf-editor, go to apps -> nautilus-cd-burner, and check the options for "debug" and "overburn".  That didn't do it for me, but I've just been using Gnomebaker so I haven't tried to fix it any further.

---

### Post by Steveway on 2007-09-19
I use Amarok and I just have to enter my login-details in the settings.
I think that Rythmbox has also a section for last.fm in it's settings.
Why are you using that dpkg command?
You can just double-click the file in nautilus.

---

### Post by Tessea on 2007-09-20
OK, I got Last.FM working. There's a very easy way to do it that I figured out and then felt very stupid for not figuring out sooner.

I gave up on Serpentine and decided to try another program or two to burn CDs. 
Installed Graveman, wouldn't work.
Installed GnomeBaker. Imported the playlist I wanted to burn, made sure my preferences were all set correctly (they were), started burn. It converted the audio files and then gave me an error. The program just said 'CD burn failed' but also
> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX140E  '
Revision       : '1.1a'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 21575 kB/s 122x CD 15x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.019s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:    5.306s
Average write speed 555.5x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.054s timeout 480s
cmd finished after 0.054s timeout 480s
Fixating time:    0.066s
wodim: Cannot fixate disk.

is there anything in there that makes sense/explains my error?


> **mocoloco said:**
> I had the same problem with burning CDs.  Well not *had*, still *have*.  My problem was with the Nautilus built-in CD burner.  I'm not sure if Serpentine uses the Nautilus burner on the backend, but I know there are other apps that do, like Brasero.  My workaround was to install and use Gnomebaker, which apparently had a different backend.
There's a bug  about this issue [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/109763").

One supposed fix was to open gconf-editor, go to apps -> nautilus-cd-burner, and check the options for "debug" and "overburn".  That didn't do it for me, but I've just been using Gnomebaker so I haven't tried to fix it any further.
How do I open gconf-editor? >_> Somebody asked in the thread, I know, but I still couldn't figure it out. GnomeBaker is also giving me trouble. :(

---

### Post by mocoloco on 2007-09-20
You can open gconf-editor it by hitting Alt+F2 and typing in gconf-editor (or from a terminal window if you like).  
If you want you can add it your menu, since it's actually already there, just disabled.  Right-click the Applications menu, select edit, and you'll find "Configuration Editor" under System Tools, just check the box to enable it.

Hopefully making that change will help you ,since it didn't for me I'm not too hopeful, but I don't want to jinx you either :).  If not though, what manufacturer and model is your drive?  If you don't know, you can install a package called sysinfo ("sudo apt-get install sysinfo" in terminal), which would show up under system tools and tell you all about your hardware, etc.   Maybe try searching the forums for your CD writer's name to see if someone else has had and fixed the same issue.

---

### Post by Sayers on 2007-09-20
its the same in Rythmbox most all media players can do last.fm ...

---

### Post by Tessea on 2007-09-21
> **mocoloco said:**
> You can open gconf-editor it by hitting Alt+F2 and typing in gconf-editor (or from a terminal window if you like).  
If you want you can add it your menu, since it's actually already there, just disabled.  Right-click the Applications menu, select edit, and you'll find "Configuration Editor" under System Tools, just check the box to enable it.

Hopefully making that change will help you ,since it didn't for me I'm not too hopeful, but I don't want to jinx you either :).  If not though, what manufacturer and model is your drive?  If you don't know, you can install a package called sysinfo ("sudo apt-get install sysinfo" in terminal), which would show up under system tools and tell you all about your hardware, etc.   Maybe try searching the forums for your CD writer's name to see if someone else has had and fixed the same issue.

Thanks much. I found gconf-editor and changed the settings. Tried to burn an audio CD yet again, in GnomeBaker.

[[IMG]http://img216.imageshack.us/img216/796/burn1yw0.th.png[/IMG]](http://img216.imageshack.us/my.php?image=burn1yw0.png)
[[IMG]http://img218.imageshack.us/img218/6765/burn2qo4.th.png[/IMG]](http://img218.imageshack.us/my.php?image=burn2qo4.png)

So then I got sysinfo and ran it, this is everything it told me:

[[IMG]http://img242.imageshack.us/img242/2315/sysinfo1cl3.th.png[/IMG]](http://img242.imageshack.us/my.php?image=sysinfo1cl3.png)
[[IMG]http://img138.imageshack.us/img138/1533/sysinfo2gl6.th.png[/IMG]](http://img138.imageshack.us/my.php?image=sysinfo2gl6.png)



> **Sayers said:**
> its the same in Rythmbox most all media players can do last.fm ...
Yes, thank you. I have already solved this problem.

---

### Post by tenjin1 on 2007-09-21
> **Tessea said:**
> 
Installed GnomeBaker. Imported the playlist I wanted to burn, made sure my preferences were all set correctly (they were), started burn. 

Did you try to just add the audio files manually after selecting 'AudioCD' instead of using that imported playlist?

---

### Post by Tessea on 2007-09-21
Yes, I tried both ways.

This is really getting to me, guys. I wanna burn CDs. :(

---

### Post by Tessea on 2007-09-21
halp :(

---

### Post by tenjin1 on 2007-09-22
I believe Gnomebaker uses some codecs for burning cds (gstreamer in particualr). If you havent installed any codecs or not sure if you have all, then please do so now...in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install w32codecs
```

```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

Install dvd modules:

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
```

With codecs out of the way...Can you burn files from Nautilus?
```
Places -> CD/DVD Creator
```

    * Drag files/folders into window 

```
File Menu -> Write to Disc... -> Write
```

You can also check these settings in Configuration Editor:
Burnproof:
    * Applications -> System Tools -> Configuration Editor
    * Configuration Editor 

```
/ -> apps -> nautilus-cd-burner -> burnproof (Checked)
```

Overburn:
    * Applications -> System Tools -> Configuration Editor
    * Configuration Editor 

```
/ -> apps -> nautilus-cd-burner -> overburn (Checked)
```

note: if Configuration Editor is not in Applications -> System Tools ...then right-click Applications at top left -> Edit Menus -> System Tools -> Configuration Editor (Checked)

You can also try K3B for your burning needs:
```
sudo aptitude install libk3b2-mp3
```

---

### Post by mocoloco on 2007-09-22
Codecs are NOT required for burning.  Codecs are for encoding/decoding of audio & video files.  You would still be able to burn for example an mp3 file to a disc, even if you didn't have the codecs to actually reproduce the audio from the file.

Tessea, I'm not finding much through searching google or here in the forms about your Sony CRX140E.   [This poster]("http://ubuntuforums.org/showthread.php?t=178581&highlight=sony+crx140e") was able to get it working after upgrading Ubuntu 6.06 (it's an older post obviously).  There was a [post on launchpad]("https://answers.launchpad.net/ubuntu/+source/hal/+question/3003") about it but the person got it working with Gnomebaker.

I see you have two optical drives, so you could boot into a liveCD and still burn a disc.  If I were you at this point I would try a liveCD of Ubuntu 6.06, and failing that, a LiveCD of a different distribution, like [Knoppix]("http://www.knoppix.org/") (which is great at detecting pretty much any hardware).  From there I would look at using launchpad answers or reporting a bug on launchpad.

---

### Post by tenjin1 on 2007-09-23
> **mocoloco said:**
> Codecs are NOT required for burning.  Codecs are for encoding/decoding of audio & video files.  You would still be able to burn for example an mp3 file to a disc, even if you didn't have the codecs to actually reproduce the audio from the file.
This is true for just adding mp3 files straight to disc using Data Disc option. But from the [pic]("http://img218.imageshack.us/my.php?image=burn2qo4.png") Tessea posted she is not using the Data Disc option but using Audio CD and they are mp3 files. So codecs will need to be used for Audio CD.

As for using the liveCD..I think Tessea only has one working drive she mentioned above. So what would be nice is to see the output of the error on the [pic]("http://img218.imageshack.us/my.php?image=burn2qo4.png") Tessea posted (*Show Output* drop down button) or start app from command line.

---

### Post by Martje_001 on 2007-09-23
Hmmm.. the error says it can't fix the cd (close the cd, so it can be read). Maby it's a hardware problem. Can you try an other cd-burner?

---

### Post by Tessea on 2007-09-23
> **mocoloco said:**
> Codecs are NOT required for burning.  Codecs are for encoding/decoding of audio & video files.  You would still be able to burn for example an mp3 file to a disc, even if you didn't have the codecs to actually reproduce the audio from the file.

Tessea, I'm not finding much through searching google or here in the forms about your Sony CRX140E.   [This poster]("http://ubuntuforums.org/showthread.php?t=178581&highlight=sony+crx140e") was able to get it working after upgrading Ubuntu 6.06 (it's an older post obviously).  There was a [post on launchpad]("https://answers.launchpad.net/ubuntu/+source/hal/+question/3003") about it but the person got it working with Gnomebaker.

I see you have two optical drives, so you could boot into a liveCD and still burn a disc.  If I were you at this point I would try a liveCD of Ubuntu 6.06, and failing that, a LiveCD of a different distribution, like [Knoppix]("http://www.knoppix.org/") (which is great at detecting pretty much any hardware).  From there I would look at using launchpad answers or reporting a bug on launchpad.

Unfortunately, my DVD/CD drive doesn't work. I've been stuck with only the seconday CD drive for the last year or two.

> **tenjin1 said:**
> I believe Gnomebaker uses some codecs for burning cds (gstreamer in particualr). If you havent installed any codecs or not sure if you have all, then please do so now...in terminal:
installed codecs. some were already updated/installed, but the rest went in fine.
started up gnomebaker. decided to attempt a data CD this time for kicks.
[[IMG]http://img519.imageshack.us/img519/7151/gno1bj5.th.png[/IMG]](http://img519.imageshack.us/my.php?image=gno1bj5.png)
[[IMG]http://img249.imageshack.us/img249/299/gno2bh3.th.png[/IMG]](http://img249.imageshack.us/my.php?image=gno2bh3.png)
[[IMG]http://img219.imageshack.us/img219/3854/gno3yy4.th.png[/IMG]](http://img219.imageshack.us/my.php?image=gno3yy4.png)
[[IMG]http://img233.imageshack.us/img233/7163/gno4nl7.th.png[/IMG]](http://img233.imageshack.us/my.php?image=gno4nl7.png)
:(

[quote=]
With codecs out of the way...Can you burn files from Nautilus?[/quote]
[[IMG]http://img502.imageshack.us/img502/8659/nau1et7.th.png[/IMG]](http://img502.imageshack.us/my.php?image=nau1et7.png)
[[IMG]http://img265.imageshack.us/img265/9243/nau2ss0.th.png[/IMG]](http://img265.imageshack.us/my.php?image=nau2ss0.png)
[[IMG]http://img515.imageshack.us/img515/8180/nau3ev4.th.png[/IMG]](http://img515.imageshack.us/my.php?image=nau3ev4.png)



> You can also check these settings in Configuration Editor:
Burnproof:
    * Applications -> System Tools -> Configuration Editor
    * Configuration Editor 

```
/ -> apps -> nautilus-cd-burner -> burnproof (Checked)
```

Overburn:
    * Applications -> System Tools -> Configuration Editor
    * Configuration Editor 

```
/ -> apps -> nautilus-cd-burner -> overburn (Checked)
```

note: if Configuration Editor is not in Applications -> System Tools ...then right-click Applications at top left -> Edit Menus -> System Tools -> Configuration Editor (Checked)
unfortunately I was already advised to check those, did, and it didn't help


> You can also try K3B for your burning needs:
```
sudo aptitude install libk3b2-mp3
```
ok, I'll give this a try next.

---

### Post by tenjin1 on 2007-09-24
Hmm at this point not sure....as Martje_001 pointed out it may be faulty hardware (wouldn't think it would be related to your main cd/dvd not working?).I burn cd/dvd alot and know how irritating it may be if it doesn't work. Are you are able to burn cd's in windows with same burner? Does the drive mount and read cds fine in ubuntu? Also, try starting gnomebaker from terminal by just typing *Gnomebaker*, then copy paste error from terminal when it gets to end and error outs. Have a feeling if it doesn't work in gnomebaker, serpentine, etc then probably won't work in k3b either.

Hopefully we can get some more input from others on this problem

---

### Post by Tessea on 2007-09-24
Well, I *was* able to burn CDs in Windows with the same burner until I wiped my harddrive of Windows to install Ubuntu. :(

here's what terminal gave me about gnomebaker
```
tess@tess-desktop:~$ gnomebaker

(process:6429): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
```

---

### Post by tenjin1 on 2007-09-24
> **Tessea said:**
> Well, I *was* able to burn CDs in Windows with the same burner until I wiped my harddrive of Windows to install Ubuntu. :(

here's what terminal gave me about gnomebaker
```
tess@tess-desktop:~$ gnomebaker

(process:6429): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
```

Ok I think that is the message from terminal from just starting Gnomebaker....go ahead and try to burn another audiocd (by starting gnomebaker from terminal again) and when u get the error (gnomebaker failed burning cd)...switch back to terminal window and see if you see anymore lines show up?

---

### Post by tenjin1 on 2007-09-24
Also --is a blank disc being reconized when inserting it into drive ( a popup window saying "blank disc has been inserted, what do u want to do blah blah")? Won't hurt to try K3B either (install from command above).


Just to note: 
[This]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") is a good place to start with **everything** when first installing ubuntu, for beginners and experts alike. It's a good reference guide to say the least :)

---

### Post by Tessea on 2007-10-02
> **tenjin1 said:**
> Ok I think that is the message from terminal from just starting Gnomebaker....go ahead and try to burn another audiocd (by starting gnomebaker from terminal again) and when u get the error (gnomebaker failed burning cd)...switch back to terminal window and see if you see anymore lines show up?

No more lines appear. But does the initial message terminal gives me about gnomebaker tell me of any errors that could be solved? From reading through it, I get the idea that it's pointing out what to do.

```
tess@tess-desktop:~$ gnomebaker

(process:11630): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
```

'the GLib threading system has not been initialised..." etc

...anyway, giving k3b a chance next. Installing now.

---

### Post by Tessea on 2007-10-02
Ok, after reading through another thread on this forum with a similar problem, I downloaded Brasero in hopes of that program working. Brasero recognizes that there is a disc in the drive, however, it says that it's an unknown format of media. ??

---

### Post by Tessea on 2007-10-02
Ok, so k3B doesn't work either. Gives me this error:

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SONY CD-RW  CRX140E 1.1a (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

PIONEER DVD-ROM DVD-115R 1.25 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Text len: 162
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX140E  '
Revision       : '1.1a'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 22169 kB/s 125x CD 16x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
Track 01: audio  161 MB (16:00.10) no preemp swab     
Track 02: audio  138 MB (13:42.10) no preemp swab     
Track 03: audio  172 MB (17:08.08) no preemp swab     
Total size:      472 MB (46:50.29) = 210772 sectors
Lout start:      473 MB (46:52/22) = 210772 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 149076
Starting to write CD/DVD at speed   4.0 in real force SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
/usr/bin/wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 64
cmd finished after 0.008s timeout 200s
/usr/bin/wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
/usr/bin/wodim: Cannot send CUE sheet.
/usr/bin/wodim: Could not write Lead-in.
Writing  time:    3.911s

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=8 -dao -force textfile=/tmp/k3bggHcHb.dat -eject -overburn -useinfo -audio /tmp/kde-tess/k3b_audio_0_01.inf /tmp/kde-tess/k3b_audio_0_02.inf /tmp/kde-tess/k3b_audio_0_03.inf 
```


heeeeelp please, someone

---

### Post by Tessea on 2007-10-03
anyone? :/

---

### Post by apostate on 2007-10-03
Odd as it sounds, I wonder if it is a permissions issue with her CD_ROM mount point?

---

### Post by Tessea on 2007-10-04
bump : /

---

### Post by geoffBEAM on 2007-10-04
I get the exact same error message that you have in gnomebaker.

In K3b I get: 

> DCOPClient::attachInternal. Attach failed Could not open network socket

Whats up? I want to burn CDs too this sucks.

---

### Post by steve.horsley on 2007-10-04
Two things:

Firstly, I notice that there is a line in the debug output that says something about (write protected). This makes me wonder if it's that particular make of CD burner that you have a problem with. Trying a different drive would be a good idea.

Secondly, I notice that you have the CD size set to 80 minutes in Serpentine. I wonder if it's just that the CD you have inserted can't hold 80 minutes. Gnome/Serpentine don't seem to put much effort into their error messages sometimes. Try setting a smaller capacity like 56 or 72 minutes and see if it's happy then.

---

### Post by Tessea on 2007-10-04
a) I only have one drive. My DVD/CD drive stopped ejecting about a year ago. 

b) Nah, the CDs I have used have all been set correctly. I've used about 5 different kinds of CDs and CDRWs... :(

---

### Post by geoffBEAM on 2007-10-05
bump <Again>

---

### Post by Tessea on 2007-10-06
and again

---

### Post by tenjin1 on 2007-10-06
Sorry

At this point the next step would be to try to burn a cd in Windows ( I think u mentioned u are not dual-booting with windows?) to see if it works. If you are not dual-booting with Win...can you install it? then install ubuntu, in-turn setting up a dual-boot machine? Since these are your only steps now:

1- try to burn cd in windows
2- re-install ubuntu
3- try another cd burner
4- see if it works in livecd
5- see if it works in another linux distro
6- wait for someone else's input 

When u put a blank CD in the drive is it being mounted?(i.e. can see blank cd in *Places* menu) or put a cd in drive with data on it, like a music cd and it is reading it? (i.e. can see it mounted once again in *Places* menu) If not try to mount it with code in termial **sudo mount -a**  
 I would be curious to see if it works in Windows...I think u said it did before, but I wonder if it does now. If you need help with getting a ubuntu cd/livecd or win cd PM me.

---

### Post by Tessea on 2007-10-07
1 - Yeah, unfortunately...I am not dual-booting nor do I have my XP install CD or anything of the sort. 
2 - no windows
3 - if I can get my hands on an external burner or at some point just get a new internal burner, I totally will
4 - I only have one working drive so using the live CD is out =(
5 - can give this a try, what's your recommendation
6 - ready and waiting

The drive is fully able to be mounted, I've had absolutely no problem ripping CDs and recognizing blanks.

---

