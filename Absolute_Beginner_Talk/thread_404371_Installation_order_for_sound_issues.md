---
title: "Installation order for sound issues"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by citaworvk on 2007-04-08
I've been wondering what would be the best installation order to get the fewest sound conflicts between my applications and getting everything installed properly. I know it is possible for everything to work together, because at one point I could use any application on Edgy and the sound would work fine regardless of the file type, and there was no issue with streaming media with firefox. It took a while to get it all to work together but eventually it did. I upgraded to Feisty and now I have started the process over, but I've found it to be a little more difficult to get everything to work sound wise. Since I use USB speakers, the amount of info is slightly less detailed. So I have questions regarding these issues:
 

     1) Would the installation order of the applications and codecs really make a difference?
     2) would the installtion order of my media player vs firefox make a difference?
    
 I think the first 2 *answers* should be no, but since I don't know which configuration 
files to tamper with or what the option list I should select from to test, Its like searching for something in the dark, but I don't know what to look for. I guess I should point out I know little to nothing about about how OS's work but I know considerably more now than when I started, which is a definite plus. This is a great OS but any tips or help would be appreciated.

---

### Post by ComplexNumber on 2007-04-08
i would say that the answer to both of those questions would be "no". i've not noticed any difference. 
it would be quite difficult for me to go through synaptic and list all the main relevant packages to install, but i usually just do a search for "alsa" and "esd" and install the ones that seems relevant after reading the description.

other files that it may help you to install include the following:

timidity
esound
libsndfile1
transcode
flac
gstreamer0.10
libesd
libmusicbrainz
libportaudio
libsamplerate


codecs may include:

faad
faac
lame
fame
ffmpeg
ogg
mp3
vorbis
quicktime
libmad0
libmpeg

---

