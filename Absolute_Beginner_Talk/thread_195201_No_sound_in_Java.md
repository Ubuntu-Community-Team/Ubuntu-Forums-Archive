---
title: "No sound in Java"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by goodmore on 2006-06-12
I installed Jva thru Automatix. I have sound everywhere but Java. No sound in Pokerroom. Please help

---

### Post by G.Kirkham on 2007-08-06
I too have that issue of no sound from Java on every PC I build. The sun java test runs but no sound.
[http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/index.ht](http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/index.ht)

Animated coffee beans, with a soundtrack and per-frame sound effects.
file:///usr/lib/jvm/java-1.5.0-sun-1.5.0.10/demo/applets/Animator/example1.html

/usr/lib/jvm/java-1.5.0-sun-1.5.0.10/demo/applets/Animator

/home/user1/.java/deployment/log/plugin150_10.trace is not showing any errors.


I have installed sun-java 1.5.

Flash plugin (non-free does have sound).

The only web site I can test sound on is Runescape logon screen.

I wonder what the following means ([http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html](http://java.sun.com/j2se/1.5.0/docs/guide/sound/programmer_guide/appendix2.html)) ?

To use MyDeviceProvider as the default for SourceDataLine lines, set the following key:

    javax.sound.sampled.SourceDataLine=com.xyz.MyDeviceProvider

To specify the default Synthesizer by its name InternalSynth, set the following key:

    javax.sound.midi.Synthesizer=#InternalSynth

To specify the default Receiver by provider and name, set the following key:

    javax.sound.midi.Receiver=com.sun.media.sound.MidiProvider#SunMIDI1


My file has 
#
# Example 1:
# Use MyDeviceProvider as default for SourceDataLines:
# javax.sound.sampled.SourceDataLine=com.xyz.MyDeviceProvider
#
# Example 2:
# Specify the default Synthesizer by its name "InternalSynth".
# javax.sound.midi.Synthesizer=#InternalSynth
#
# Example 3:
# Specify the default Receiver by provider and name:
# javax.sound.midi.Receiver=com.sun.media.sound.MidiProvider#SunMIDI1
#

should these be un-commented ?

This was an interesting site but still did not help me, [http://www.vsj.co.uk/java/display.asp?id=370](http://www.vsj.co.uk/java/display.asp?id=370)

I found this comment but what does it mean ?
[http://forum.java.sun.com/thread.jspa?messageID=9450488&tstart=0#9450488](http://forum.java.sun.com/thread.jspa?messageID=9450488&tstart=0#9450488)
JavaSound supports ALSA on Linux since Java 1.5.
You can select the "plughw" devices of ALSA.

[http://72.14.253.104/search?q=cache:KFYuyA4l5oIJ:www.jsresources.org/apps/3196_InternetPhone.pdf+java+linux+ALSA+%22plughw%22&hl=en&ct=clnk&cd=10&gl=au&lr=lang_en](http://72.14.253.104/search?q=cache:KFYuyA4l5oIJ:www.jsresources.org/apps/3196_InternetPhone.pdf+java+linux+ALSA+%22plughw%22&hl=en&ct=clnk&cd=10&gl=au&lr=lang_en)
# Use MyDeviceProvider as default for SourceDataLines:
javax.sound.sampled.SourceDataLine=#AudioPCI [plughw:1,0]

Well, after trying the above, still no sound from a java applet.

If anyone out there knows what is stopping so many of us from getting sound out of sun java under linux, please let us know.

Thanks,

George.

---

### Post by G.Kirkham on 2007-08-09
Hi,

Should anyone be visiting this page, I have found solutions to getting Sound working under Java and Flash. 
Previously I had been frustrated because sound was not working in Runescape or other internet based Java 

aplications. I had not tested local java for sound until I downloaded the JavaSoundDemo 

([http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/](http://java.sun.com/products/java-media/sound/samples/JavaSoundDemo/)) to test Java sound, and then found 

that sound was not working.

When I first was trying to solve my sound issue, I did have working sound from Linux GNome via ALSA and the 

pacakge alsa-oss was loaded, therefore I was able to hear sound from music CDs and from system sounds. The  

(Desktop -> Preferences -> Sound (Sound Preferences), Sounds tab and "Enable software sound mixing (ESD)", 

"Play system sounds" were both checked. Of course I also had installed sun-java5-jre, sun-java5-plugin and 

flashplugin-nonfree.

However Flash and Java were not providing sound. 

After many days of searching, I finally found someone who gave the required information "by default 'libesd' 

is installed but you need to install 'libesd-alsa0' for ALSA sound to work", and after selecting and 

installing 'libesd0-alsa0' sound for flash worked (eg youtube and other flash video clips). 

Please note: installing libesd-alsa0 will uninstall libesd0, this is not a problem.

However Java sound was still not working. After much more researching I found something very simple that I 

had previous tried but decided did not work as I had not at that time been using 'libesd-alsa0'. What I found 

was that many linux programs are designed to use OSS, well thought I knew this, I had believed that alsa-oss 

was to allow APIs for OSS to work from caling programs, so that any OSS program would be able to work, but 

this assumption was wrong, to have sound working for programs what were designed for OSS, I needed to prefix 

the program with 'aoss', for example, from a terminal window, run 'aoss /usr/bin/epiphany' and then I had 

sound in epiphany web browser. For sound in Sun's JavaSoundDemo, 'aoss java -jar JavaSoundDemo.jar'. If 

anyone reading this knows of an easier way that to use to get epiphany sound to work with ASLA without using  

'aoss', please reply to this post.

Getting "iceweasle" Java sound to work was very easy (once I knew what to do), it was to edit the file 

'/etc/iceweasel/iceweaselrc' to change the line 'ICEWEASEL_DSP="none"' to 'ICEWEASEL_DSP="aoss"'. Please 

note, you will need to edit this file as root (ie the administrator) to be able to make changes (I run the 

command 'nautilus --no-desktop --browser' from a terminal window so I get a file browser with 'root' access 

and then it can easy find the file, right click, then select 'Open with "Text Editor").

Well with these few simple steps, I have sound working for Java and Flash. Very pleasing. And I must say, I 

do like Linux.

Summary: 
Tips for Ubuntu/Debian ALSA Sound:

1) Edit the file '/etc/apt/sources.list' and modify 
deb [http://ftp.au.debian.org/debian/](http://ftp.au.debian.org/debian/) etch main non-free
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free

2) Ensure that you have alsa and alsa-oss installed and working (if you have installed ALSA and don't have 

sound, don't forget to run 'alsaconf' as root (ie administrator) if you have not done so).

3) Install 'libesd0-alsa0'

4) run programs that use OSS by using 'aoss' in front of the command, eg 'aoss /usr/bin/epiphany'

5) for Iceweasel, change 'ICEWEASEL_DSP="none"' to 'ICEWEASEL_DSP="aoss"' in the file 

'/etc/iceweasel/iceweaselrc'

Other Tips


In the file /etc/apt/sources.list, add the line"
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

You may also want to add the line (Hey, someone respond, please, is there a better site to use?):
deb [http://mirror.home-dn.net/debian-multimedia/](http://mirror.home-dn.net/debian-multimedia/) etch main

Install w32codecs for video decoding (ie displaying various video of various formats)

Install libdvdplay0, libdvdread3, dvd+rw-tools, gnomebaker, gstreamer0.8-mpeg2dec, libdvdcss2, libdvdnav4.

I use VLC for playing videos (in both Linux and in Windows), is there a better DVD/Video Player ?


One thing I would request of anyone reading this, if you know of other simple tips for sound, video, USB 

Video cameras, Fire Wire, USB memory drives, Digital Still cameras DVD writers or other devices to help with 

configuration or installation which does not happen with a standard installation, please post back here for 

me and others to pick up, as I would not like to say how long it took me to find the above simple points 

amongst the strange 'recompile your kernnel', and 'rebuild your ALSA drivers' type of suggestions. 
 


Well I am posting these points that helped me,  up here in this thread, in the hopes it helped you. If it 

did, please post back, it will give me an idea of the number of others who would benefit from a list of 

simple good tips to make your Ubuntu/Debian installation more complete.

---

