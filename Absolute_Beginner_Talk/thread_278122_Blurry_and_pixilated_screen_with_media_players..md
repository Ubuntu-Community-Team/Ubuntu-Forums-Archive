---
title: "Blurry and pixilated screen with media players."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-15
Hello, I'm wondering if any of you had pixelated and blurred screen resolution with you media players compared to WMP10?

I'm wondering if I need to configure my internal hardware in a way that I don't know yet. I have xubuntu installed on my 

HP pavilion dv4230us 1.6 GHz Intel® Celeron® M Processor 380, with an internal Intel Graphics Media Accelerator 900, and a 
15.4” WXGA High-Definition BrightView Widescreen (1280 x 800) Display with an internal sound card made from Altec Lansing.

I love the quickness of my new desktop and really love the concept of ubuntu/xubuntu, but I'm just seeing a definite decline in my streaming video, wmv, and DVD's playback quality.

I also get a freezing during playback that says buffering, even on DVD. 

I'm sure there is an easy answer, but I've searched all over and can't seem to find and help other than suggestions for codecs, which I have installed along with firefox plug-ins.

Thanks,
-c.

---

### Post by crimesaucer on 2006-10-15
I love this xubuntu, but for real, the media players and there picture quality is making me miss windows, and I don't want to have to re-install Xp because I was hoping to use only xubuntu because it's MUCH faster than windows.

Everything about xubuntu/ubuntu is better so far, except the media players and their screen quality, and the way they freeze and sometimes don't play.

Am I the only one with this problem?

I would love some help from a "media player" expert because streaming video is a major part of my web browsing.

I have another related question: If there is no way to fix the quality of picture in my VLC, Xine, and totem-Xine movie player, then would it be possible to use G-parted to add my Windows Xp and a fat32 file, and then use wine to run WMP10 or WMP11 (I feel like a WiMP for asking. lol) so as to have the clear and perfectly focused screen picture I used to have on the exact same wmv files and DVDs that I've been trying to view with my xubuntu 6.0.6 1 LTS Dapper.

thanks,
-c.

---

### Post by ComplexNumber on 2006-10-15
use an application called VLC instead. let me  know what you think. its the best media player out there on linux.

---

### Post by crimesaucer on 2006-10-15
I have VLC and I installed as this code in terminal:

 How to install Multimedia Player (VLC) with plug-in for Mozilla Firefox

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc

    * Inorder to stream video via vlc, you also need to install the following packages. 

sudo apt-get install avahi-daemon
sudo apt-get install avahi-utils

    Applications -> Sound and Video -> VLC Media Player 

...then it sort of worked at first, and then it only worked for like 1 site, and not for any other streaming video, and now it won't even work for downloaded wmv movie clips.

Maybe I don't have it configured correctly. I have all the codecs suggested in the ubuntu wiki, and the xubuntu desk top manual, and I'm still having problems with freezes, buffering stalls, breaking of stream, buffering stalls during DVD playback, and of course, a really blurry and pixelated screen image and bad lighting and shadow views.

---

### Post by crimesaucer on 2006-10-15
I also read this in a tutorial for configuring xine, this is the address:
[http://nongeeksight.blogspot.com/2006/07/multimedia-in-xubuntu-made-easy.html](http://nongeeksight.blogspot.com/2006/07/multimedia-in-xubuntu-made-easy.html)


To edit ~/.xine/config just type this in a terminal window:

mousepad .xine/config

then look for a block that seems like this:

# path to RealPlayer codecs
# string, default: /usr/lib/codecs
# decoder.external.real_codecs_path:/usr/lib/codecs

# path to Win32 codecs
# string, default: /usr/lib/codecs
# decoder.external.win32_codecs_path:/usr/lib/codecs

and change it to say (you can use copy and paste):

# path to RealPlayer codecs
# string, default: /usr/lib/codecs
decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/codecs
decoder.external.win32_codecs_path:/usr/lib/win32

...is this correct. I haven't done this yet because I really was wanting the VLC to work as my default mp.

I also read that maybr I need the VLC 8.5 with the nightly builds for certain streaming video websites that play only the audio, with no picture which is what happens with my attempt to watch surfing videos from Surfline.com.

---

### Post by ComplexNumber on 2006-10-15
> then it sort of worked at first, and then it only worked for like 1 site
hmmm thats seems odd.

i had the ame blurriness as you from time to time when i used mplayer/totem/kaffeine. then i switched to VLC and it was gone.

---

### Post by crimesaucer on 2006-10-15
would it be from having multiple media players? I have read a post saying that I should only have one media player, was that correct. Maybe I'll try and lose all of my media players.

I did try to unistall all of my media players once before, (with no luck), because my xfmedia (default) media player that comes preinstalled with the xfce xubuntu 6.0.6 1 LTS said in the synaptic manager that if I uninstalled xfmedia that I had to uninstall related packages xubuntu desktop. And I don't want to uninstall xubuntu.

well, I uninstalled totem-xine, and xine-ui, and the VLC still didn't play clear video, and still didn't work for certain streaming video.

so who knows...

---

### Post by crumja on 2006-10-19
Go to vlc settings, preferences, video, output modules.
Highlight output modules and check advanced options.
Set the video output module to OpenGL video.

---

### Post by crimesaucer on 2006-10-19
Thanks, I'll try that.

---

