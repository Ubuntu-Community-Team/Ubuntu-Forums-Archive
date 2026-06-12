---
title: "[SOLVED] CODECS, Libdvdcss, and Gstreamers for Ubuntu Gutsy"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-07
hello everyone,

first of all, many thanks to those who replied to the post at [http://ubuntuforums.org/showthread.php?t=716614](http://ubuntuforums.org/showthread.php?t=716614) (focus on: DVD playback). At this moment, some DVDs play, some other don't, VCDs don't play, but .avi extension video files do. Among data and music CDs, I've come across only one that doesn't work (all the DVDs, VCDs, and CDs I tested work perfectly on another machine - Acer Travelmate - under Ubuntu Feisty). 

It'd be great if anyone could advise me on what else I should do to have all the DVDs, CDs, VCDs fully function under Ubuntu Gutsy, on an HP Pav. dv2530, and on the basis of the following:  

1) I installed Automatix for Ubuntu 7.10 Gutsy i386 (found at [http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.10_.28Gutsy_i386.29)). After starting it, I ticked the options (there are three of them) for CODECS for download. The download failed altogether ("fatal error"). 

2) I then run *sudo aptitude install ubuntu-restricted-extras* . At some stage, during what looked like a Java installation, I was asked to agree on a user legal statement, except that the "OK" at the end of the statement on the Terminal seemed to be disabled (when I press enter nothing happened). I eventually closed Terminal, and some ten minutes later the Update Manager popped up re: some updates, among which I found the Java user legal statement (and agreed on it). 

3) Not knowing exactly what and why I'm doing it, I run again * sudo aptitude install ubuntu-restricted-extras*. The Terminal asked me to correct an error due to my interrupting the previous attempt (I suppose for closing Terminal), and then a 3-minute installation process began, during which I didn't notice any error message, although I wasn't given any "installation successful" message either at the end. 

4) At this stage, I checked  [http://www.medibuntu.org/](http://www.medibuntu.org/) and I followed the directions at the page Repositories. The process seemed to complete successfully. I'm not quite sure I downloaded everything, though. I didn't check the page "Packages", for instance. Also I was a bit afraid I'd download stuff that's not for Gutsy. 

5) I then went to [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy), got to the section "DVD playback", and run the codes given under that section. The process seemed to complete successfully. 

6) At [http://packages.ubuntu.com/gutsy/ubu...tricted-extras](http://packages.ubuntu.com/gutsy/ubu...tricted-extras) (not knowing exactly whether I should or shouldn't do this) I thought I'd  run the commands given at [http://packages.ubuntu.com/gutsy/i386/gstreamer0.10-ffmpeg/filelist](http://packages.ubuntu.com/gutsy/i386/gstreamer0.10-ffmpeg/filelist). None of them seemed to lead anywhere: for each of them I got a "permission denied" error. 

7) I then went to [http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html](http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html) and run the commands on CODECS at paragraph 3 down the page. The process seemed to complete successfully. Except for *sudo apt-get install mpg123*, for which I only got "unable to fetch", "could not resolve" messages. 

8) Some of my DVDs now work. Some other don't, and Totem gives me a link to [http://www.gnome.org/projects/totem/#code](http://www.gnome.org/projects/totem/#code) for the latter. I used my imagination and complete lack of knowledge of Linux and run *sudo apt-get install gst-plugins-base* but nothing happened. I then went to [http://gstreamer.freedesktop.org/download/](http://gstreamer.freedesktop.org/download/) and got kind of worried about what I'm doing when I read (top of the page): "In general, you should find packages that were specifically made for your distribution...". 

9) I run again *sudo apt-get install libdvdcss2* and it looked like it went through (please noticed that I'd run this before, as the command is included in the "medibuntu" pages (see item 4 above).

10) I run Automatix once more, and this time only ONE of the two CODECS files for download gave a "fatal error" message. 

I'm now wondering: 

1) if there's a way to check what Codecs, libdvd, and Gstreamers I still need in my system to be able to play all kinds of DVDs and VCDs. On my previous machine, I had Ubuntu Feisty installed, and all the necessary DVD software came through Automatix, and never had any problem whatsoever in watching films on DVD or VCD, not to mention I didn't have to spend a whole day collecting pieces of software here and there without knowing what I'm doing;
2) if Totem might be at issue here, and if it is, maybe there are better video players for Linux? Even if the DVD plays, none of the option under "Go" (like DVD menu and the like) work. 
3) why Totem refuses to play some DVDs but plays others;
4) why Totem refuses to play VCDs altogether unless the files on them have a .avi extension. 
4) why all the options under "GO" at the TOTEM menu are not enabled; 
5) why TOTEM - both when it doesn't like the DVD or when I try to play it by clicking "Movie" > "Play disc XXX" (that is, I don't let Totem start up the video automatically) - gives the error message "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc";
5) why - If I play any video through MPlayer instead of TOTEM, I get as far as seeing the DVD's menu for a tiny moment and an error message (which I can't see as it disappear right away together with the DVD's menu) and another error message saying: "gnome_screensaver_control()". 

I also checked [http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html](http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html) and I think it's an excellent guide (except that some of the commands to run in Terminal given there don't seem to lead anywhere), and I wonder if anyone who really  knows Ubuntu Gutsy inside out could come up with something like that with a specific and comprehensive section on DVD + CVD playback guide for Ubuntu Gutsy first-time users? 

Thanks for taking the time to read this.

---

### Post by jan quark on 2008-03-07
to play dvd  follow this guide:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28restricted%29)

[B]and please remove automatix
it is known to cause severe compatibility problems[/B]

---

### Post by hyper_ch on 2008-03-07
automatix IS NOT RECOMMENDED TO USE.

---

### Post by al.adab on 2008-03-07
MANY THANKS JAN QUARK!!!
DVDs are working fine now. 

VCDs are now, though. Totem gives me the following message: 

"Totem could not play 'vcd:///media/cdrom0 - There is no input plugin to handle the location of this movie". Any idea? Also is there anything I wrongly installed (see my previous long post) I should now remove?

---

