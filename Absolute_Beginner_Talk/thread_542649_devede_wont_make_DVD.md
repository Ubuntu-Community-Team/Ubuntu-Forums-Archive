---
title: "devede wont make DVD"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-09-04
ive got avi files. it looks like i can fit around 12 of them on a DVD but after i let devede do it thing the window with the progress thing never closes and when i look where the movie should be it show up as the clips i started with how do i get them onto a dvd? or is this beyond what devede will do. i get a folder also with audio_ts and video_ ts files in them.
it looks like the clips have been joined there at least down to 3 from the 12 but still theres no way to right click to the burn to dvd option

---

### Post by bumanie on 2007-09-04
Feisty has a bug in devede and even if you managed what you are trying, you find that they burn with a hiss over the audio. But for future reference (when the bug is fixed) I think you  right click on the iso file compiled by devede and choose burn from the menu.

---

### Post by trucker33377 on 2007-09-04
there is no burn there. it never closes the creating window. guess ive got to find another way to do this

---

### Post by -SpaZ on 2007-09-04
Do you have the DVD codecs installed?  If not, then install libdvdread3 and libdvdcss2.

---

### Post by trucker33377 on 2007-09-05
ya i think they are

---

### Post by Amazona aestiva on 2007-09-05
See the first link in my signature.

---

### Post by kelvin spratt on 2007-09-05
I use DeVeDe all the time in feisty go to [http://www.getdeb.net/](http://www.getdeb.net/) down load the latest version and the patch for Feisty, load your files do a 10 sec preview if ok. proceed add your menu you  can choose any png you like write to a ISO then burn the ISO to disc i have a 100% succes rate using DeVeDe. if you still have probs, just post back.

---

### Post by trucker33377 on 2007-09-05
ok i went to that link

---

### Post by trucker33377 on 2007-09-05
> **kelvin spratt said:**
> I use DeVeDe all the time in feisty go to [http://www.getdeb.net/](http://www.getdeb.net/) down load the latest version and the patch for Feisty, load your files do a 10 sec preview if ok. proceed add your menu you  can choose any png you like write to a ISO then burn the ISO to disc i have a 100% succes rate using DeVeDe. if you still have probs, just post back.

i dont see a patch for devede there

---

### Post by trucker33377 on 2007-09-05
> **Amazona aestiva said:**
> See the first link in my signature.

went to that link still not sure i have the codec
heres what i did

lonnie@lonnie-desktop:~$ sudo apt-get install gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-audiofile gstreamer0.8-cdio gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-misc gstreamer0.10-alsa gstreamer0.10-doc gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x gstreamer-tools irb1.8 liba52-0.7.4 libbreakpoint-ruby1.8 libcdaudio1 libcmdparse2-ruby1.8 libdaemonize-ruby1.8 libdvdnav4 libdvdread3 libdvdplay0 libfaac0 libfaad2-0 libfreebob0 libgems-ruby1.8 libglib2-ruby libgsm1 libgstreamer0.8-0 libgstreamer0.8-ruby libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-ruby1.8 libgstreamer-gconf0.8-0 libgstreamer-perl libgstreamer-plugins0.8-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-pulse0.10-0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 liblog4r-ruby1.8 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf libxine-extracodecs libxine1-ffmpeg libxine1 libdvdcss2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-esd is already the newest version.
gstreamer0.10-gnomevfs is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-base-apps is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
liba52-0.7.4 is already the newest version.
liba52-0.7.4 set to manual installed.
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
libfaac0 is already the newest version.
libfaac0 set to manual installed.
libgsm1 is already the newest version.
libgsm1 set to manual installed.
libgstreamer0.10-0 is already the newest version.
libgstreamer-plugins-base0.10-0 is already the newest version.
libid3tag0 is already the newest version.
libid3tag0 set to manual installed.
liblame0 is already the newest version.
liblame0 set to manual installed.
libmad0 is already the newest version.
libmad0 set to manual installed.
libmjpegtools0c2a is already the newest version.
libmjpegtools0c2a set to manual installed.
libmp4v2-0 is already the newest version.
libmp4v2-0 set to manual installed.
libmpcdec3 is already the newest version.
libmpcdec3 set to manual installed.
libmpeg2-4 is already the newest version.
libmpeg2-4 set to manual installed.
libpulse0 is already the newest version.
libpulse0 set to manual installed.
libquicktime0 is already the newest version.
libquicktime0 set to manual installed.
libsidplay1 is already the newest version.
libsidplay1 set to manual installed.
libxvidcore4 is already the newest version.
libxvidcore4 set to manual installed.
ffmpeg is already the newest version.
mencoder is already the newest version.
mplayer is already the newest version.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
lonnie@lonnie-desktop:~$

---

### Post by Amazona aestiva on 2007-09-05
I modified the Code...try it again, but I think every codecs are installed...
You can find DeVeDe in the middle of my page.(first link) There is the fix too.

---

### Post by ponchuk on 2007-09-05
there is no patch. where can u find it. also would converting the avi bitrate to 128 help the noise problem when burning the dvd.  thanks in advance

---

### Post by kelvin spratt on 2007-09-06
when you download DeVeDe from [http://www.getdeb.net/](http://www.getdeb.net/) click on DeVeDe home page at the bottom of the DeVeDe home page you will see the patch for Feisty mencoder  download and follow the instructions it is elementary the warning is in red writing on get deb site. once you do that audio bitrate will be sorted. i must stress this is a Ubuntu bug not DeVeDe as it works perfect on all other Distros I've tried with no modification, but saying that i personally have never had the problem With Feisty and always use 128 bitrate for all my videos. as i convert from Mp4 not Mp3, and they all play perfect in any standalone player.

---

### Post by trucker33377 on 2007-09-06
ok heres the deal now if i use DeVeDe with 1 file its working i get an iso file in my home folder to burn but if i add files to fill a DVD disk they all show up in my home folder as clips with a movie folder that has 2 more folders in it . 
its making 10 mpg clips then inside the next folder there are  3 more .VOB files

ive not tried to burn yet so i dont know if the sound is ok or not i did do the fix for it but until i figure out this frist thing i dont want to used a DVD for 300 or 400 MB clips.

---

### Post by kelvin spratt on 2007-09-06
Devede does not join files if you add all your Clips in the right hand pane ie 10 clips you will get a slight pause between each one apr 2sec. if you write to ISO you end up with one ISO, to burn with all you clips on its the same as  with convertxtodvd in windows, except you write to ISO which they tell me is more accurate when burning than vob files. ive done 150 home movies with no problems at all.

---

### Post by trucker33377 on 2007-09-06
> **kelvin spratt said:**
> Devede does not join files if you add all your Clips in the right hand pane ie 10 clips you will get a slight pause between each one apr 2sec. if you write to ISO you end up with one ISO, to burn with all you clips on its the same as  with convertxtodvd in windows, except you write to ISO which they tell me is more accurate when burning than vob files. ive done 150 home movies with no problems at all.

guess i dont understand this. i am adding all the clips in the right hand pane. but it never gets done. it hangs on the creating window all thats there is this with nothing on it blank.. bars are gone. in my home folder has no iso file there to burn. ive uninstalled and reinstalled DEVEDE with the same out come. i did do a 433mb file and got the iso file to burn

---

### Post by kelvin spratt on 2007-09-07
you are converting to DVD aren't you? this all seems strange if you can convert 1 file i do enough to fill a DVD click that's it, you could check in the setting as you add each file  that they are coming up ok and the settings are the same,

---

### Post by trucker33377 on 2007-09-07
dont matter at this point i deleted the files DEVEDE  made last night and got the files i was trying to copy with them over 6 gigs. took awhile to download those ill put the new download on windows. i hate to say this but this has just not worked out very well for me at all.

guess i need to look at things alittle closer

---

### Post by trucker33377 on 2007-09-13
ok thanks for all the help so far. ive had pretty good luck with DEVEDE using 1 file or title. ive got a 2 disk movie i want to use and have followed dir  from this link [http://www.my-guides.net/en/content/view/75/](http://www.my-guides.net/en/content/view/75/)
but where it says to check 'Properties'  from the title side( left pane) i dont have that option. Properties only appears on the files side. it looks like thats the last check before converting so burn can start. any idea's on this thxs

---

### Post by kelvin spratt on 2007-09-16
their is a tiny button on the right hand side of the left panel press and you will find properties.

---

### Post by trucker33377 on 2007-09-16
> **kelvin spratt said:**
> their is a tiny button on the right hand side of the left panel press and you will find properties.

well if there is its soooo small i dont see it got one on the right hand side of the right pane but not on the left pane

---

### Post by kelvin spratt on 2007-09-17
the screenshot you supplied is a old version  use the latest version  i use 3.01 .

---

### Post by trucker33377 on 2007-09-19
humm not sure how i did that but ill look for the new one and update thxs alot

---

