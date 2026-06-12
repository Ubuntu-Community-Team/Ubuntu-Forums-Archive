---
title: "A few problems"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Bruno Silva on 2006-02-19
Hi everyone,

I've recently installed Dapper Drake to try XGL out, and turns out I liked it so much that I want to keep it :), but I have some problems:

1 – I can't play any audio/video file, Movie Player and Rythmbox Music Player say that can't read the stream that it might be related to codecs.

2 – Is there any way I can write to my NTFS partitions?

3 – I have a TV Tuner PixelView Play TV Pro 2 and I wanted to watch TV, what software do I have to use?

4 – I want to install Dapper Drake on my laptop and using the same cd I used to install on my desktop isn't working, after I select the install option it freezes sometimes after showing the text: loading kernel. Just to be sure it isn't caused by the CD what other ways can I install it?


I know I'm probably asking too much but I'm really new to this :)

Thanks in advance

Bruno Silva

---

### Post by unbutuju on 2006-02-19
[QUOTE=Bruno Silva]...
1 – I can't play any audio/video file, Movie Player and Rythmbox Music Player say that can't read the stream that it might be related to codecs.

2 – Is there any way I can write to my NTFS partitions...

Bruno Silva[/QUOTE]

Hi Bruno!
What you mean with write to your NTFS parts, could you be more specific about what you want to do?
Regarding the audio / video files, I assume its mp3? or avi? or similar kinds?

have you made any updated to your ubuntu after installing it?

let us know a bit more and by parts he he!

---

### Post by Bruno Silva on 2006-02-19
[QUOTE=unbutuju]Hi Bruno!
What you mean with write to your NTFS parts, could you be more specific about what you want to do?
Regarding the audio / video files, I assume its mp3? or avi? or similar kinds?

have you made any updated to your ubuntu after installing it?

let us know a bit more and by parts he he![/QUOTE]

Hi, :)

the files are avi and mp3 yes, the avi files I think I need for some xvid or ogg and ac3 decoder I think.

Yes, I've updated everything as soon as I installed. :)

I'm trying to write files to my NTFS Partition where I have Windows XP installed, I was able already to mount it, but I can only read files from there.

---

### Post by nalmeth on 2006-02-19
Unfortunately, MS's ntfs filesystem can only be written to by the MS operating system... 

you can only read an ntfs filesystem with non MS operating systems. MS does actually support fat32 filesystems, to which you can read/write. If this is really a problem for you, you can go as far as changing your windows filesystem to fat32, or creating a new partition solely for your personal data.

Did you upgrade from breezy, or just install dapper from a flight cd?

The codecs you're trying to use are restricted format, and I'm not exactly sure what the packages are called for dapper. Go to the dapper forum here: [http://ubuntuforums.org/forumdisplay.php?f=111](http://ubuntuforums.org/forumdisplay.php?f=111) and they should be able to help you out

---

### Post by jpkotta on 2006-02-19
NTFS:
There is no Linux write support for NTFS.  Microsoft will not release the specs, and the read support we do have is reverse engineered.  I think there is unstable write support but it it can lead to fs corruption.

TV card:
Did a google search and found [this]("http://www.linuxquestions.org/hcl/showproduct.php/product/3040").

Multimedia:
By "updated everything" I assume you mean you installed the [restricted]("https://wiki.ubuntu.com/RestrictedFormats")formats.  I guess you could try changing the output plugins.  Personally, I use xine, and use the OpenGL output plugin, which I would guess MPlayer has and XGL supports.  Can you play other sounds?

---

### Post by Bruno Silva on 2006-02-19
I just made a clean install of Dapper, I had only windows before (I guess I made the right choice up until now, lets see :D)

the updates I did where the ones that showed up when I booted into Dapper, I didn't add any Repos. I just added 1 Repository when I was trying to install XGL, Universal Dapper I think.

---

### Post by nalmeth on 2006-02-19
Some quick searching showed me that you can use [tvtime]("http://tvtime.sourceforge.net/") mythTV, totem, xine, and mplayer to watch tv, but you have to have your video card driver setup, and make sure the card is supported. I have no idea how to set them up. Go to the dapper forum, and they will have the most relevant info for you.

---

### Post by Bruno Silva on 2006-02-19
[QUOTE=nalmeth]Some quick searching showed me that you can use [tvtime]("http://tvtime.sourceforge.net/") mythTV, totem, xine, and mplayer to watch tv, but you have to have your video card driver setup, and make sure the card is supported. I have no idea how to set them up. Go to the dapper forum, and they will have the most relevant info for you.[/QUOTE]


Ok, thanks :)

---

### Post by Netisan on 2006-02-19
I'm quite non-experienced ubuntuser, but I already performed some study on these questions. 

Generally, visit [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) to enable more software sources and get written help on many topics. 
[COLOR="Plum"]Ubuntu Linux Resources
Site FAQ
Basic ways to install software
Enabling extra repositories
Editing Files that Belong to Root
Mounting Windows Partitions
A PDF Ubuntu Beginner's Guide
Great Linux Bookmarks[/COLOR] - the site sections. 

Writing to windows ntfs is not imposible on theory. There is a package called [COLOR="Plum"]captive[/COLOR] which enables it. I've got this tool but still not need it. Really, why should I mess with NTFS in Linux??

Configuring codecs for media: 
   
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

This is concerning your first two requests. About the third I have no idea. 
About the laptops - I know that they are different from desktops in hardware interfaces meaning (like the old branded PCs-absolutely incompatible with anything else as model) and so they are inpredictable with new installations. You know-laptops always come with everything ready-installed (which ever works ;). This is IMHO.

---

### Post by Bruno Silva on 2006-02-19
[QUOTE=Netisan]I'm quite non-experienced ubuntuser, but I already performed some study on these questions. 

Generally, visit [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) to enable more software sources and get written help on many topics. 
[COLOR="Plum"]Ubuntu Linux Resources
Site FAQ
Basic ways to install software
Enabling extra repositories
Editing Files that Belong to Root
Mounting Windows Partitions
A PDF Ubuntu Beginner's Guide
Great Linux Bookmarks[/COLOR] - the site sections. 

Writing to windows ntfs is not imposible on theory. There is a package called [COLOR="Plum"]captive[/COLOR] which enables it. I've got this tool but still not need it. Really, why should I mess with NTFS in Linux??

Configuring codecs for media: 
   
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

This is concerning your first two requests. About the third I have no idea. 
About the laptops - I know that they are different from desktops in hardware interfaces meaning (like the old branded PCs-absolutely incompatible with anything else as model) and so they are inpredictable with new installations. You know-laptops always come with everything ready-installed (which ever works ;). This is IMHO.[/QUOTE]


Ok, thank you, I got everything working now :)

I still haven't found solution for my laptop :( It just freezes after the loading kernel :(

---

### Post by Netisan on 2006-02-19
[QUOTE=Bruno Silva]Ok, thank you, I got everything working now :)

I still haven't found solution for my laptop :( It just freezes after the loading kernel :([/QUOTE]
Evidently, machine-related problem (see next post - Ubuntu/Kbuntu Freezing- Any Alternaitves ). 
Try reading some vendor info rather than Linux help.

---

### Post by Bruno Silva on 2006-02-19
I found out what is my problem, is the acpi, I've disabled it to install adding the acpi=off in the command before installing. But now I can't boot, I think I have to disable it in Grub, but I don't know how.

Edit: just found out that it already has de command acpi=off in grub, and it boots ok until it was supossed to show the login, I hear the sound, be the monitor stays turned off. I haven't installed anything yet, I think it might be something related to drivers or graphics card, I'm not sure. Any Ideas?

Bruno SIlva

---

### Post by Bruno Silva on 2006-02-19
Sorry to bump this again, but I think I know what the problem is, I have to change a config in xorg.conf, but I have to boot in the recovery console, how can I open and edit it? I can't use gedit since gnome isn't running

thanks

---

### Post by nalmeth on 2006-02-19
you can use nano in the terminal

sudo nano xorg.conf

or this might help too:

sudo dpkg-reconfigure xserver-xorg

try picking the vesa driver if it isn't selected already, or do whatever you found out you need to do
My laptop had the acpi problem, I just reinstalled with the command at startup: linux acpi = off. Sorry, I don't know how to do it from the inside. Good luck

---

