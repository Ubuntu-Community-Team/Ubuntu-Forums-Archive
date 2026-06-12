---
title: "ran xine-check and got quickly out of my depth."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-05-15
DVD works in toem but not in Xine so I set about tracking the problem down. I ran xine-check on command line and got a bucket full of problems. Ive been fixing them but at each corner that I turn I seem to find more and more i dont understand. 

One of the issues it told me I had was that i have no plugins at all! Advised me to re install xine-lib. I reinstalled libxine1-plugins and ran xine-check, plugin issue went away. This was the new output for plugins in the check:

> [ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins


However when  I tried to run DVD in xine it gave me>  "input plugin failed to open mrl '/media/mydvdname' together with another error>  "The specified file or mrl is not found. Please check it twice. (/media/mydvdname)

Ok so the plugin issue isnt sorted???? Ok this is a puzzle for a newbie!

Moving on down the xine-check output I find this:

> multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use..

What do I pull out? A lot of  xine files on system in synaptic manager, what do I leave and what do I take out?

lastly xine-check gives me this:
> 
[ good ] /dev/cdrom points to /dev/scd1
[ good ] /dev/dvd points to /dev/scd1
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)

Er where do I check this? Pretty sure I havent got any scsi. Well I tried this > fdisk -l and hey I got a shock! No hda no hdb which are my windows and ubuntu IDE hard drives........there all listed as sdx ?????????????? 

Now im so puzzled I feel like crying. :confused:

---

### Post by meborc on 2007-05-15
don't worry... with introduction of new kernel some time ago, all hdx is now recognized as sdx... it is normal... it got us all as a surprise... search this forum and you will see information about this change

can't help you with the dvd problem though - have no dvd's at home... :)

---

### Post by darkworld on 2007-05-15
does ubuntu come with xine installed? I installed after installation because it wasnt in menu. Now I realize that doesnt mean it wasnt there! Hence I could of caused the double installation but i dont know how to undo it?

i also discovered that only one of my dvd rw drives tries to play DVD's do i need symbolic links to both dvd players? 

xine-check is only seeing one.

>  [ good ] /dev/cdrom points to /dev/scd1
[ good ] /dev/dvd points to /dev/scd1

---

### Post by klytu on 2007-05-15
I'm not sure the output of xine-check you got is going to lead you to a solution. Here's the output from my xine installation which plays DVDs flawlessly: > Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.20-15-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[ good ] found unknown plugin: *.so
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdb
[ good ] /dev/dvd points to /dev/hda
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  RGBA RGBT RGB2 YUY2 UYVY YV12 I420
 I don't think you have anything doubly installed despite the confusing output you got from xine-check. If you installed xine through synaptic, apt, or aptitude none of those would do a double install anyway. What caught my eye in your first post is that the error message you got from xine referred to /media/mydvdname not /dev/dvd or /dev/cdrom. How are you trying to play your DVD? Did you just insert the DVD into the drive then xine automatically launched and gave you that error? Or did you launch xine first, then insert the DVD and ... then what? Try lauching xine without any DVD in your drives and hit <ALT>s (press the ALT key and the s key at the same time) on your keyboard - this should take you to the xine settings menu. Click the gui tab and under ¨Configuration experience level¨ select ¨Expert¨ then apply; then go to the media tab and examine what is listed under "device used for DVD playback" (you can change that in order to use your other DVD drive if you want) - if it's not /dev/dvd or /dev/cdrom, that might be the problem.

---

### Post by darkworld on 2007-05-15
Thanks for the reply. I did the alt+s and clicked media tab. **There is no such setting????** see screen shot attached.

I checked the other tabs and no luck.

After your prompt im wondering about sybolic links to my dvd drives. Getting a tad out of depth again on that. I understand a symbolic link but I aint got a clue how to interigate sym links to find out where they point.

Going back to what you ask. If I boot xine then insert dvd and click dvd in xine dvd controls I get two errors.

> -xine engine error- there is no input plugin available to handle 1dvd:/' maybe MRL syntax wrong or file/stream source doesnt exist. 

the other error is.

> 
Thes source cant be read. Maybe you dont have enough rights for this, or source doesnt contain data (eg. not disc in drive). (dev/dvd).

Ok so im getting the feeling that its not finding /dev/dvd .... looking at the main window header bar it has 

> xine: dvd:/

Ok now if I go into system>preferences>removable drives and media preferences> multimedia and put > xine %m In the Video DVD discs commandline. Then put dvd in drive, it faults immediately when xine opens with same error except its looking in different location /media/'mydvdname'

The header in main window shows path > xine: /media/'mydvdname'

If i go More on the error it gives:

> 
lots of video_out: throwing away image with pts ...... because its too old.
xine found demuxer plugin: Elemetary stream demux plugin
xine found input plugin
input_file not found  (so this is the actual problem????)
xinefound input plugin :file input plugin


If I put totem %m the no probs so how does totem find the drive if links are wrong. Im thinking its either a missing link or xine for some reason doesnt know where to look. Thanks in advance, im sure its staring me in the face but I havent got all the skills as yet to sort.

its either a setting missing or a link to hardware ...is it?

---

### Post by darkworld on 2007-05-15
whoops I missed what you actually said about the expert level. sorry, checking now.

No its ok its says.

> /dev/dvd

so the puzzle deepens.

---

### Post by darkworld on 2007-05-15
ok xine is pointing to /dev/dvd

I go into /dev and>  ls -al dvd and get this > lrwxrwxrwx 1 root root 4 2007-05-15 13:21 dvd -> scd0

so dvd is symbolic link is to scd0 

so why cant xine find the file? This is hell !!! goin to give it 10 more mins then xine is history. What really does my head in is that I had no problems running xine in mandriva! Is this a ubuntu thing?

---

### Post by darkworld on 2007-05-15
ok im just trying to make sense of the linking now.

dvd is sym link to sd0 so xine goes to /dev/dvd which pushes it through to the hardware sd0

now if I go and find where the dvd is opening in the system i find it in /media as a directory. In media I have cdrom and cdrom1 and cdrom0

so to understand this I did > ls -la cdrom* this tells me thst cdrom is a sym link to cdrom0, ok but the dvd opens as its own directory which doesnt appear to be sym limked to anything! Im very puzzled but I must be near to solving this! am i?

somebody chuck me a line in drowning!

heres my outputs:

> root@dark-desktop:/media# ls
cdrom  cdrom0  cdrom1  floppy  floppy0  hda1
root@dark-desktop:/media# ls -al cdrom*
lrwxrwxrwx 1 root root    6 2007-05-04 11:46 cdrom -> cdrom0

cdrom0:
total 8
drwxr-xr-x 2 root root 4096 2007-05-04 11:46 .
drwxr-xr-x 6 root root 4096 2007-05-15 14:39 ..

cdrom1:
total 8
drwxr-xr-x 2 root root 4096 2007-05-04 11:46 .
drwxr-xr-x 6 root root 4096 2007-05-15 14:39 ..

then i put dvd in drive


> root@dark-desktop:/media# ls
cdrom  cdrom0  cdrom1  floppy  floppy0  hda1  LWW0EXW1
       
root@dark-desktop:/media# ls -la LWW0EXW1\ \ \ \ \ \ \ /
total 12
dr-xr-xr-x 4 dark 4294967295  136 2006-01-21 09:08 .
drwxr-xr-x 7 root root       4096 2007-05-15 14:41 ..
dr-xr-xr-x 2 dark 4294967295   40 2006-01-21 09:08 AUDIO_TS
dr-xr-xr-x 2 dark 4294967295 2328 2006-01-21 09:08 VIDEO_TS

---

### Post by klytu on 2007-05-15
> Ok so im getting the feeling that its not finding /dev/dvd .... looking at the main window header bar it has [QUOTE]xine: dvd:/ [/QUOTE] 

If I recall correctly the correct command for xine to play a DVD inserted in whatever drive is linked to /dev/dvd  is:
```
xine dvd://
``` If you actually entered the command as ```
xine: dvd:/
``` as indicated in your post above, I think you'd get errors.

---

### Post by klytu on 2007-05-15
> Ok now if I go into system>preferences>removable drives and media preferences> multimedia and put 
Quote:
[QUOTE]xine %m [/QUOTE] Try using instead > xine dvd:// there.

---

### Post by darkworld on 2007-05-15
Ok I tried xine dvd:// and bang errors again but looking at the errors in the more tab. Its saying something new now. 
> 
Cannot find input plugin for MRL [dvd://] 
Input plugin cannot open MRL [dvd://]

Is this all about a missing xine plugin? If so I havent got a clue which one. I thought I had them all!

> dark@dark-desktop:~$ ls /usr/lib/xine/plugins/1.1.4/
post                           xineplug_dmx_mng.so
xineplug_ao_out_alsa.so        xineplug_dmx_mpeg_block.so
xineplug_ao_out_arts.so        xineplug_dmx_mpeg_elem.so
xineplug_ao_out_esd.so         xineplug_dmx_mpeg_pes.so
xineplug_ao_out_file.so        xineplug_dmx_mpeg.so
xineplug_ao_out_none.so        xineplug_dmx_mpeg_ts.so
xineplug_ao_out_oss.so         xineplug_dmx_nsv.so
xineplug_ao_out_pulseaudio.so  xineplug_dmx_ogg.so
xineplug_decode_a52.so         xineplug_dmx_pva.so
xineplug_decode_bitplane.so    xineplug_dmx_qt.so
xineplug_decode_dts.so         xineplug_dmx_rawdv.so
xineplug_decode_dvaudio.so     xineplug_dmx_real.so
xineplug_decode_dxr3_spu.so    xineplug_dmx_slave.so
xineplug_decode_dxr3_video.so  xineplug_dmx_sputext.so
xineplug_decode_faad.so        xineplug_dmx_yuv4mpeg2.so
xineplug_decode_ff.so          xineplug_dmx_yuv_frames.so
xineplug_decode_gsm610.so      xineplug_flac.so
xineplug_decode_image.so       xineplug_inp_cdda.so
xineplug_decode_lpcm.so        xineplug_inp_dvb.so
xineplug_decode_mad.so         xineplug_inp_dvd.so
xineplug_decode_mpc.so         xineplug_inp_file.so
xineplug_decode_mpeg2.so       xineplug_inp_gnome_vfs.so
xineplug_decode_nsf.so         xineplug_inp_http.so
xineplug_decode_qt.so          xineplug_inp_mms.so
xineplug_decode_real_audio.so  xineplug_inp_net.so
xineplug_decode_real.so        xineplug_inp_pnm.so
xineplug_decode_rgb.so         xineplug_inp_pvr.so
xineplug_decode_speex.so       xineplug_inp_rtp.so
xineplug_decode_spucc.so       xineplug_inp_rtsp.so
xineplug_decode_spucmml.so     xineplug_inp_smb.so
xineplug_decode_spudvb.so      xineplug_inp_stdin_fifo.so
xineplug_decode_spu.so         xineplug_inp_v4l.so
xineplug_decode_sputext.so     xineplug_inp_vcdo.so
xineplug_decode_theora.so      xineplug_inp_vcd.so
xineplug_decode_vorbis.so      xineplug_vo_out_aa.so
xineplug_decode_w32dll.so      xineplug_vo_out_caca.so
xineplug_decode_yuv.so         xineplug_vo_out_dxr3.so
xineplug_dmx_asf.so            xineplug_vo_out_fb.so
xineplug_dmx_audio.so          xineplug_vo_out_none.so
xineplug_dmx_avi.so            xineplug_vo_out_opengl.so
xineplug_dmx_fli.so            xineplug_vo_out_sdl.so
xineplug_dmx_flv.so            xineplug_vo_out_syncfb.so
xineplug_dmx_games.so          xineplug_vo_out_xshm.so
xineplug_dmx_iff.so            xineplug_vo_out_xvmc.so
xineplug_dmx_image.so          xineplug_vo_out_xv.so
xineplug_dmx_matroska.so       xineplug_vo_out_xxmc.so

---

### Post by darkworld on 2007-05-15
one other thing. I dont give the command dvd:/ this is the command generated by xine when I click on DVD button on control panel.

---

### Post by klytu on 2007-05-15
OK. You might just need to install some additional multimedia codecs. Just to be sure, follow[[COLOR="Red"]_**the instructions here**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=413624") and install all the multimedia codecs and libdvdcss2.

EDIT: 

Also make sure you have done this:```
sudo aptitude install libxine-extracodecs
``` Sorry for the edited post, but I am away from my computer at home.  I am posting stuff as I remember it.

---

### Post by crimesaucer on 2007-05-15
I use Xine-ui, and my DVD works, sort of.

I installed Xine-ui from the wiki page with this code [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28xine-ui.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28xine-ui.29) :

```
sudo aptitude install xine-ui libxine-extracodecs
```

and I then installed DVD playback with this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability) :

```
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine

```

```
sudo aptitude install libdvdcss2
```

Now, my problem with it is that it doesn't play continuously (I only have one DVD with chapters so maybe there is a way to properly configure it to play continuously, but I haven;t tried to learn it yet), but using the User Interface, I can click the " :// " button, and select through my directories for: 

/media/061006_1925/Keeping the Faith/Video_TS

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-121-1.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-121.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-121.png)

Now I can play the different chapters with out having to open the chapters up individually from my Thunar (xubuntu's file system).  

... I can use the hot key " g ", so that the menu will pop up and I can just select the next file and press the play button in the lower left hand corner in the small :// pop up file box. And it plays instantly. Then I can press " g ", and it hides the menu until I need to forward to the next chapter.

Now, once again, I'm pretty sure there is a setting to make it play through in a continuous mode, but I haven't learned it yet and haven't needed to because I don't have any other DVD's with chapters.

I hope this might helps a bit.

---

### Post by darkworld on 2007-05-15
this is all a familiar path it seems....

[http://ubuntuforums.org/showthread.php?t=205467&highlight=libdvdcss]("http://ubuntuforums.org/showthread.php?t=205467&highlight=libdvdcss")

Ive got everything all the packages etc...... but I just see one thing that spooked me. After setting to expert in xine and trying different things I opened a version of xine that was set to begginer ....there are two seperate xines opening on my system.

Thats it now! Thanks for all the help much appreciated. im leaving it until another week when I have time to reinstall the lot. Thanks again

---

### Post by klytu on 2007-05-15
> **darkworld said:**
> this is all a familiar path it seems....

[http://ubuntuforums.org/showthread.php?t=205467&highlight=libdvdcss]("http://ubuntuforums.org/showthread.php?t=205467&highlight=libdvdcss")

Ive got everything all the packages etc...... but I just see one thing that spooked me. After setting to expert in xine and trying different things I opened a version of xine that was set to begginer ....there are two seperate xines opening on my system.

Thats it now! Thanks for all the help much appreciated. im leaving it until another week when I have time to reinstall the lot. Thanks again

Now home, I re-read all of your posts and thought about the outputs and error messages you posted.  It appears to me that you have all the necessary plug-ins and codecs installed. I think the key issue to solve is in this comment from one of your posts: > ... but the dvd opens as its own directory which doesnt appear to be sym limked to anything! I think if we can figure out why this is happening, it may solve your problem. What is the output of:```
cat /etc/fstab
```

---

### Post by darkworld on 2007-05-16
Im convinced it either doesnt no how to handle the DVD or it cant find it.



> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=f44a3f1a-f7f6-422c-8c2e-a490b3eacd8c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3f04d06d-271b-4889-a9fd-7e1ac3260fc7 /home           ext3    defaults        0       2
# /dev/hda1
UUID=A0B04CA3B04C8230 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb8
UUID=660774af-02d4-435e-9dfe-2bfaaf50576f /opt            ext3    defaults        0       2
# /dev/hdb7
UUID=8bba1451-bb49-42de-bb79-cc22d859e174 /tmp            ext3    defaults        0       2
# /dev/hdb9
UUID=0d83f38c-226b-483d-9f48-3e38bb4fa3fd /usr            ext3    defaults        0       2
# /dev/hdb6
UUID=72424b79-5a83-4c71-a0c7-c00926cdac13 /var            ext3    defaults        0       2
# /dev/hdb2
UUID=1530d4cc-f1af-4ef5-af1f-68330e16cb92 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by klytu on 2007-05-16
I think these two lines in your fstab are the culprits:> /dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0Backup your current fstab: ```
sudo cp /etc/fstab /etc/fstab.old
``` Then```
 sudo gedit /etc/fstab
```and change those two lines to  > /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0save and close the file. I think this will work, based on your previous posts. Did you upgrade to Feisty from an older Ubuntu version?

---

### Post by darkworld on 2007-05-16
A hundred thank you's. That sorted it! I dont understand why fstab was configured that way. 

Could it of been done another way without changing fstab only wondering in case the change to fstab would mess up anything else?.

Dont really understand where a symbolic link is correct and where it isnt. Could you symbolic link cdrom0 to sd0. Would that do the same?

I noticed earlier in this problem that /dev/dvd is symbolic linked to sd0 is this the reason why only one of my dvd drives plays DVD's. Is it possible to symbolic link /dev/dvd to sd1 as well????  

Hey anyway its fixed and I learnt quiet a lot in the process. Many thanks again. (I was nearly ready to reload Mandriva)

---

### Post by klytu on 2007-05-16
> A hundred thank you's. That sorted it! I dont understand why fstab was configured that way. You are welcome! I asked if you had upgraded from a previous Ubuntu version because, for example, Dapper uses the /dev/hdx form in fstab for IDE hard drives, cdrom drives, and dvd drives. In Feisty almost all drives are seen as SCSI drives. 

> Could it of been done another way without changing fstab only wondering in case the change to fstab would mess up anything else?. I think you could do this in xine by changing /dev/dvd in xine's settings>media tab to either /dev/scdo or /dev/scd1 depending on which drive you had inserted the dvd. By default, gnome is using the symbolic links to your dvd drives so the only way I could think of to automatically mount your DVDs at the areas referenced by the default sym links was to edit your fstab file. 

> Dont really understand where a symbolic link is correct and where it isnt. Could you symbolic link cdrom0 to sd0. Would that do the same? Yes, I think so - assuming you mean to scd0.

> I noticed earlier in this problem that /dev/dvd is symbolic linked to sd0 is this the reason why only one of my dvd drives plays DVD's. Is it possible to symbolic link /dev/dvd to sd1 as well????  I don't think you can have the same link pointing to two different drives at the same time, no. But /dev/dvd could be linked to either one or the other.

---

### Post by darkworld on 2007-05-16
Well many thanks for the help. Next time something doesnt find something I will be much clearer as to what to look for.

---

