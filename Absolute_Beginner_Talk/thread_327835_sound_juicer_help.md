---
title: "sound juicer help"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by calebjohnson77 on 2006-12-29
I am having a problem with sound juicer.  I set up the mp3 profile as it said in the help file, but when I try to extract files to the mp3 format, I get this message:

"Sound Juicer could not extract this CD.

Reason: Could not create GStreamer encoder ((null))"

Both GStreamer and LAME are installed on my computer. What am I doing wrong?

---

### Post by Ziggy72 on 2006-12-29
I had problems with this too.

What I *think* I did to get this working.....

1) I installed and ran EasyUbuntu via Automatix to install the codecs.

2) I made sure Sound Juicer was installed properly - using Symantic.

3) I made sure I had gstreamer0.10-ffmpeg installed - using Synaptic - I think this is necessary.

4) I made sure I had gstreamer-lame installed - using Synaptic

5) Check with Synaptic that all of the following plugins are installed:
	gstreamer0.10-plugins-bad, bad-multiverse, base, base-apps, good, ugly

6) Set up a new Sound Juicer profile - the Sound Juicer help file has the following information:
> 
	"If you need to store tracks in the MP3 format (for example,
       	 if your portable music player only supports MP3 and not Ogg Vorbis),
        	you will need to create a new profile.  To do this, click on
       	 Edit Profiles, click New, and name the profile MP3.
        
	Select the MP3 profile and click the Edit button.  Set GStreamer Pipeline to
     
	audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

	Set the File Extension to  mp3, and select the Active  check box.  You will have to 	restart Sound Juicer to see the new  audio profile
        
	This profile uses the LAME MP3 encoder, so you will need to have the GStreamer 	LAME plugin installed.  ¨ 
    
----------------
Some of the following may help - (or they may add to your confusion):

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
[http://ubuntuforums.org/showthread.php?t=216108&highlight=mp3%2Btotem](http://ubuntuforums.org/showthread.php?t=216108&highlight=mp3%2Btotem)

I hope this helps:)

---

### Post by bingobingo on 2007-01-07
I am having problems too with gstreamer, in it is not encoding mp3 right if any at all. The size of the resulting file is the same size as the original and no player will play it and get hung up on it. 

I know you stated lame was installed, but in my case I have Edubuntu 6.06 on PowerMate Eco and lame was also not pre-installed, you would think the plug-in would require it, causing one headache after another. The only reason I am even trying to do mp3s on one of my computers is because my niece received a new ipod (boo, no ogg) and needs to rip cds. And any program (amarok, banshee) that uses gstreamer have similar results. I do not know what is going on. Audacity loads it but it sounds like a ethernet line.

I finally loaded grip and was able to rip mp3's. Debian only has gstreamer 0.8, I would think 0.10.11 would be a better version. When will they up date it?????

---

