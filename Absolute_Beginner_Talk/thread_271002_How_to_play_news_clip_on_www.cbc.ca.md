---
title: "How to play news clip on www.cbc.ca"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by johanchangid on 2006-10-04
Hi everyone,

I am a new user of Ubuntu. I have installed Real Player in order to run news clips on [www.cbc.ca](www.cbc.ca) (I did that in Windows XP). However, when I tried to play this video clip ([http://archives.cbc.ca/IDC-1-69-97-793/life_society/religion_classroom/clip5)](http://archives.cbc.ca/IDC-1-69-97-793/life_society/religion_classroom/clip5)), my Real Player didn't work. The website showed me "Additional plugins are required to display all the media on this page". If I click "Install Missing Plugins" on my browser, the pop-up menu will be showed up, saying that "No suitable plugins were found". And if I then click on "Manual Install", this will direct me to microsoft website to download Windows Media Player which is impossible for Ubuntu. Could anybody help me? Thanks in advance.

Johan

---

### Post by arochester on 2006-10-04
There is a video about this on Robin "Roblimo" Miller's Personal Website at [http://roblimo.com/](http://roblimo.com/) - scroll down to "Watching Sarasota Herald-Tribune videos in Linux".

In essence he says 
1) Look at >View>Page Source
2) Look at >Edit>Find
3) Search for ".wmv"
4) You will then see the URL for the video

... which happens to be [http://ms.radio-canada.ca/archives/2002/en/wmv/religion19880927et1.wmv](http://ms.radio-canada.ca/archives/2002/en/wmv/religion19880927et1.wmv)
in this case

---

### Post by johanchangid on 2006-10-04
Thanks Arochester for your input.

However, there is another error appeared.
Once I copied and pasted the url (..wmv) into a new browser, then I selected a player, totem(default), this error popped up "Totem could not play 'mmsh://wm.world.mii-streaming.net/media/nytreg/SH/SH7616103.WMV?MSWMExt=.asf'." . Could you tell me how to solve this problem? Thanks in advance.

---

### Post by arochester on 2006-10-04
Have you got the Windows Codecs installed? 

See "Ubuntu Restricted Formats" in general at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and probably "Play streaming video from the Internet" in particular at [https://help.ubuntu.com/community/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267](https://help.ubuntu.com/community/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267)

---

### Post by dragonfyre13 on 2006-10-04
Install the Mplayer Plugin for Firefox, and uninstall the Totem Plugin for Firefox. It will only affect embedded multimedia, but as long as you have that, and the restricted formats installed as mentioned above, you won't have any problems.

Oh, and if you do that, you don't have to grab the page source, and go through all that.

---

### Post by johanchangid on 2006-10-14
Sorry, I haven't got back to forum for many days. 

Now, I even have a problem with my synaptic package manager. I can't download mplayer. The synaptic package manager seems like unable to download anything.
This is the error message:
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-18_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2-common_1.2.10-18_all.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdvdread/libdvdread3_0.9.4-5.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libd/libdvdread/libdvdread3_0.9.4-5.1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.24clean-0ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.24clean-0ubuntu4_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libgii/libgii0-target-x_0.9.1-0.1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libgii/libgii0-target-x_0.9.1-0.1ubuntu1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libgii/libgii0_0.9.1-0.1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libgii/libgii0_0.9.1-0.1ubuntu1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libggi/libggi2_2.0.5-1.1ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/libg/libggi/libggi2_2.0.5-1.1ubuntu2_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.0-final-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.0-final-0ubuntu1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.1-0ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxvmc/libxvmc1_1.0.1-0ubuntu4_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-6_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer-skins/mplayer-skins_2-6_all.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/xmmplayer/xmms-xmmplayer_0.3.3-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/x/xmmplayer/xmms-xmmplayer_0.3.3-1_i386.deb)
  Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out

My internet connection is fine. Do you have any suggestions? Thanks in advance.

---

### Post by johanchangid on 2006-10-17
Thanks a lot for your information. Now, I can play news clip of cbc.ca

---

