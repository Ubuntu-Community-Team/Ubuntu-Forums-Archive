---
title: "mp3's not saved"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by azurehi on 2007-03-03
Using frostwire, I downloaded and mp3 music file as a test to see where they are saved, played and stored.  Mp3 was saved in /home/(my name/Shared.  Open Rhythmbox music player, added file to playlist - it played.  Closed rhythmbox, reopened, file was gone from playlist and gone from /shared.  I read something about mp3 files not being supported, got some codecs from automatix, also gstreamer set from synaptic.  I am very confused about why the files just disappear, never to be found.  Obviously, I need to study how to use music in ubuntu 6.10.  Comments/suggestions appreciated.

---

### Post by steve101101 on 2007-03-03
Im not sure why the file is 'Missing'. I use Ubuntu and RhythmBox to play mp3s and it works great. try redownloading.

---

### Post by Cobikegeek on 2007-03-03
Check out this link for info on playing mp3's in Ubuntu.  

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Here's the basic how to:

Install MP3 support for Soundjuicer (ripper) and Rhythmbox (player)

1. Install Lame codecs

2. Open rhythmbox)

Select edit-preferences and click on the edit profiles box at the bottom of the window.   Click on "New" and create a profile named MP3.  Paste this code into the Gstreamer Pipeline text box:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

Enter mp3 for file extension.  Click on the Active box and close.  From the profiles list select MP3 and close.  That sets up rhythmbox.  

Now open soundjuicer and select edit-preferences.  Select the library tab and click the drop down list box for preferred format and select the MP3 profile.  Close the window and you are done.

---

### Post by azurehi on 2007-03-04
Thank you both, steve101101 and cobikegeek.  Issue seems solved.  I am a newbie to linux in general, ubuntu in particular.  Thanks to these forums and all who post, I am learning to configure ubuntu - my goal is to leave W$ in the dust.  :)

---

