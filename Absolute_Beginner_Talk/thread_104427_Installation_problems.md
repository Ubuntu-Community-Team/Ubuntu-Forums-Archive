---
title: "Installation problems"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by J_P on 2005-12-16
I was starting to get the hang of installing programmes,So far i have installed the firewall and a few other apps without to much problem then all of a sudden im having probs........I have ben using the command line to install my apps using the sudo apt-get commands eg sudo apt-get install libdvdcss2,After issuing the command it will run through its process and tells me how much disk space the app needs and asks if i want to continue,Even after typiny Y and hitting enter it aborts the install,Can anyone help me on this one please?

Also while i am posting this i may aswell ask you this question to save starting another new thread:p  I am having problems with the totem media player,I have installed the codecs but totem will still not play for me,Here is the command i used to install them: 

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

The install ran correctly and said was complete yet totem will still not play.

Sorry if these questions seem a little easy to you but i am struggling and need a little help.

Thanks people:)

---

### Post by Perfect Storm on 2005-12-16
This may not answer your problem, but you might prefer trying mplayer or VLC instead. I find them superior compared to Totem IMHO. :)

---

### Post by bscbrit on 2005-12-16
I agree with 'AI' - I have not found totem to be very reliable but I'm sure that there are many thousands of users out there that will disagree with me.  I also use mplayer.

---

### Post by bscbrit on 2005-12-16
When you say that totem will not play - what happens?  Does the program not load, does it load but simply refuse to play the file, or does it also show an error message?

---

### Post by J_P on 2005-12-16
Ok here goes: totem and mplayer will play dvd's for me totem skips alot but thats not bothering me at the mo,The problem i am having is playing movie clips etc from the internet,If i click a weblink in WINXP it auto opens WMP and plays that clip right ?
Now on ubuntu while browsing the web i try to open a video file and everytime i get an error message saying totem wont open the file because of missing codecs,As said earlier i installed the codecs with this command: 

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

But has made no difference at all,I have added xmms & VLC but these wont play them either,Please help!

---

### Post by linbetwin on 2005-12-16
sudo apt-get install totem-xine

---

### Post by J_P on 2005-12-16
ok added that command and then get this:

Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies

Sorry to be a pain people :confused:

Could it just be the type of file i am trying to play?

---

### Post by J_P on 2005-12-16
Anyone? Please? :)

---

### Post by Perfect Storm on 2005-12-16
If you install mplayer then you can install mplayer-plugin which allow you to see movies on your browser. I'm sure xine have one similiar, I guess a xine competent can guide you there.

---

