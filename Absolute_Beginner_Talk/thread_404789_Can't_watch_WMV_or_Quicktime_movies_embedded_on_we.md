---
title: "Can't watch WMV or Quicktime movies embedded on web pages."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-08
What do I need to do to be able to watch Quicktime clips on webpages like on the bottom of [this](http://www.csiro.au/promos/ozadvances/Series6FishWalk.html) page? I tried installing MPlayer and Automatix and that didn't work.

---

### Post by moffa on 2007-04-08
I use vlc.

Install it with ```
 sudo apt-get install vlc mozilla-plugin-vlc 
```

You have to remove the default totem plugin for firefox by running
```
 sudo apt-get remove totem-mozilla 
```

---

### Post by x-ray vision on 2007-04-08
That didn't work.

---

### Post by moffa on 2007-04-08
I went to the webpage and clicked the link.  It worked for me.  Do you have all the codecs installed?

(a shameless rip-off from ubuntuguide.org)

```
 sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs  
```

---

### Post by x-ray vision on 2007-04-08
Still not working. :(

---

### Post by moffa on 2007-04-08
Is it installing those programs or is it giving you an error?  Also, could you elaborate on  "Still not working" is it freezing, a black screen?

Edit: You have to close firefox and reopen it before it can reload the plugins.  You might have to also restart after installing the codecs

---

### Post by x-ray vision on 2007-04-08
All the installations seemed to go okay.

It just says "no video" when I click on a quicktime link. I'll restart the pc now.

---

### Post by moffa on 2007-04-08
Just try waiting a few seconds for the video to buffer and start playing.  I guess it depends on your internet connection speed.

---

### Post by x-ray vision on 2007-04-08
Still getting (no video).

Sometimes it crashes my Firefox session.

---

### Post by x-ray vision on 2007-04-08
When I try to watch the Quicktime movie [here](http://www.csiro.au/promos/ozadvances/Series6FishWalk.html), I get a black screen and it says "(no video)".

I get the same message when I try to watch the WMV clip on [this](http://www.liufangmusic.net/samples/) page. However, I can click on the WMV clips that requires a download to watch [here](http://www.agschools.com/humor.htm), and I can watch the clips fine with both Totem player (my default) or VLC player.

Sometimes when trying to watch an embedded Quicktime or WMV clip, my Firefox session crashes.

Any ideas on what to try next?

---

### Post by doobit on 2007-04-08
> **x-ray vision said:**
> When I try to watch the Quicktime movie [here](http://www.csiro.au/promos/ozadvances/Series6FishWalk.html), I get a black screen and it says "(no video)".

I get the same message when I try to watch the WMV clip on [this](http://www.liufangmusic.net/samples/) page. However, I can click on the WMV clips that requires a download to watch [here](http://www.agschools.com/humor.htm), and I can watch the clips fine with both Totem player (my default) or VLC player.

Sometimes when trying to watch an embedded Quicktime or WMV clip, my Firefox session crashes.

Any ideas on what to try next?

If you are familiar with Synaptic (the package manager in Ubuntu) then the solution is to enable the universe repositories and install mplayer and the mplayer plugin for mozilla. Then you need to get the gxine extra codecs which you can also install using Synaptic. Synaptic can be found in the system menu.

---

### Post by strabes on 2007-04-08
First you want to remove any totem player plugins from firefox and install the mplayer ones since mplayer is much better than totem:

```
cd /usr/lib/firefox/plugins/ && sudo rm libtotem* && cd && sudo apt-get install mplayer mozilla-mplayer
```

Then you'll want to read this page on how to enable proprietary format support: 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by nudnik on 2007-04-08
> **x-ray vision said:**
> When I try to watch the Quicktime movie [here](http://www.csiro.au/promos/ozadvances/Series6FishWalk.html), I get a black screen and it says "(no video)".

I get the same message when I try to watch the WMV clip on [this](http://www.liufangmusic.net/samples/) page. However, I can click on the WMV clips that requires a download to watch [here](http://www.agschools.com/humor.htm), and I can watch the clips fine with both Totem player (my default) or VLC player.

Sometimes when trying to watch an embedded Quicktime or WMV clip, my Firefox session crashes.

Any ideas on what to try next?

Make sure every necessary codec is installed, then make sure "totem-xine" is installed as opposed to the default "totem". 

Stop looking at the walking fish! Its unnatural! Aeeeiiiii!

---

### Post by x-ray vision on 2007-04-08
Okay, I did everything suggested above except get the mplayer plugin for mozilla (where do I get that) and "Make sure every necessary codec is installed" (which ones are necessary?

---

### Post by Maestro23 on 2007-04-08
After you have all your sources enabled:

mozilla-mplayer

> sudo aptitude install mozilla-mplayer

w32codecs

> sudo aptitude install w32codecs

---

### Post by x-ray vision on 2007-04-08
Should I download the totem-gstreamer and the totem mozilla plug-in?

---

### Post by Maestro23 on 2007-04-08
> **x-ray vision said:**
> Should I download the totem-gstreamer and the totem mozilla plug-in?

When it comes to your plugins for FF, use one or the other: mplayer or totem.  Have seen too many posts on the boards about conflicts when both are installed.

Maybe some who has had success with both, will chime in on this thread.

Just my 2 cents.:)

---

### Post by x-ray vision on 2007-04-08
> **Maestro23 said:**
> When it comes to your plugins for FF, use one or the other: mplayer or totem.
Does that mean I screwed up by following all of the advice above because it was conflicting? What should I do now?

---

### Post by Maestro23 on 2007-04-08
> **x-ray vision said:**
> Does that mean I screwed up by following all of the advice above because it was conflicting? What should I do now?

I'm partial to mplayer and its plugin.  They work for **me**.  I can play any embedded video I come across on the web.  Plays apple quicktime trailers with no problems. I had both installed once before and the totem plugin would kick in thru FF and just sit there and try to play the vid.  Discovered the conflict on my own one night. 

Other people live/die by totem.  Once I uninstalled totem and its plugin, I have had smooth sailing ever since. To each his/her own.  Pick one that works/you can get working for you.

---

### Post by x-ray vision on 2007-04-08
Can you tell me how I can make things work now that I've done what I've done?

---

### Post by Famicommie on 2007-04-08
[www.getautomatix.com](www.getautomatix.com)

Install the multimedia codecs, and the MPlayer for Firefox plug-in through Automatix.

---

### Post by x-ray vision on 2007-04-08
> **Famicommie said:**
> [www.getautomatix.com](www.getautomatix.com)

Install the multimedia codecs, and the MPlayer for Firefox plug-in through Automatix.

Do I have to undo anything I already did first?

---

### Post by x-ray vision on 2007-04-08
That didn't work either. :(

Does anyone think it might be a good idea to reistall Ubuntu and start from scratch?

---

### Post by Mets on 2007-04-09
If you are getting No Video then your problem is that you have the mozilla VLC plugin installed.  You first need to remove the mozilla VLC plugin with Synaptic.  That plugin does not yet work, even though you can play any media file perfectly in VLC.  So first remove that.

I had a similar problem.  Here's my thread:
[http://ubuntuforums.org/showthread.php?t=396620](http://ubuntuforums.org/showthread.php?t=396620)

Basically, you can't yet remove mozilla-totem plugin without removing all of the Ubuntu Desktop so you basically need to trick Ubuntu into thinking that it is there while actually removing that one component.  There is no need to run around removing random files.  Just go here:
[https://launchpad.net/ubuntu/+source/ubuntu-meta/+bug/68874](https://launchpad.net/ubuntu/+source/ubuntu-meta/+bug/68874)

Once there, click on Bug Attachments.  Then download the "fake" .deb file that was made to fix this problem.

Ok, with that all set you have successfully removed mozilla VLC and mozilla totem plugins without ruining your system and getting in trouble deleting files!  With that finished, repeat the steps in this thread to install mozilla mplayer plugin and mplayer features.

Done!  Should work.

EDIT:  DO NOT reinstall Ubuntu.  That will actually make it worse in your case, since Totem is the default media player :)  So reinstalling is effectively going in a circle.  

The work around .deb file is just a dummy file.  Firefox will first try to play the movie with Totem now that the VLC plugin is out, and that will fail since the plugin is fake (intentionally).  When that fails, Firefox will resort to using mplayer and you will be streaming sweet media.

---

### Post by x-ray vision on 2007-04-09
Didn't work. :(

Should I have removed VLC and VLC-nox also? I just removed VLC-plugin-esd.

---

### Post by x-ray vision on 2007-04-09
Doh! Mozilla-plugin-vlc. I'll go over the steps again and report back.

---

### Post by TheRingmaster on 2007-04-09
The ubuntu desktop package is just a metapackage. It is safe to remove.

---

### Post by x-ray vision on 2007-04-09
Okay, I'm half way there. 

Some clips ask me to open it with a player, and when I choose Totem or the mplayer, I get audio and no video.

Other clips open with the xgine plug-in, and they take forever to buffer and stop halfway through. When I press play after it's done playing, it replays an earlier clip and not the one I was just watching.

Also, about 25% of the time, trying to watch a clip crashes my Firefox session.

---

### Post by x-ray vision on 2007-04-09
I already installed MPlayer for Firefox plug-in and I still can't watch WMV clips with mplayer. Is there anything else I need?

---

### Post by Swab on 2007-04-09
You'll need to correct codec.  See here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jakev383 on 2007-04-09
> **x-ray vision said:**
> I already installed MPlayer for Firefox plug-in and I still can't watch WMV clips with mplayer. Is there anything else I need?
It's in a non-free codec. Best advice would be to download Automatix ([www.getautomatix.com](www.getautomatix.com)) and install the non-free codecs from there. Not legal to do so in all countries, so check your laws.

---

### Post by x-ray vision on 2007-04-09
Do you know how I can get the correct ones for mplayer?

---

### Post by x-ray vision on 2007-04-09
getautomatix.com isn't working. :(

---

### Post by siciliancasanova on 2007-04-09
The automatix site is not always up and running.

---

### Post by lluisanunez on 2007-04-09
Follow  this:
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by x-ray vision on 2007-04-09
> **lluisanunez said:**
> Follow  this:
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

I tried that earlier and it didn't work. Maybe it's not for mplayer?

---

### Post by Perfect Storm on 2007-04-09
Have you read:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If it doesn't work with mplayer use xine instead more reliable when it comes to internet/browser movies/clip, just make sure you havn't mplayer plugin installed aythe same time.

```
sudo aptitude install gxine gxineplugin libvcdinfo0 libxine-extracodecs
```

(requires you have both universe and multiverse enabled)

---

### Post by x-ray vision on 2007-04-09
> **Artificial Intelligence said:**
> Have you read:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If it doesn't work with mplayer use xine instead more reliable when it comes to internet/browser movies/clip, just make sure you havn't mplayer plugin installed aythe same time.

```
sudo aptitude install gxine gxineplugin libvcdinfo0 libxine-extracodecs
```

(requires you have both universe and multiverse enabled)

I tried xgine before and it was horrible. If you know of a way I could get the correct codecs for mplayer it would be much appreciated. I'm pretty new at this and I'm not sure what to do at this point except wait for the automatix site to come back up.

---

### Post by Perfect Storm on 2007-04-09
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

That's the codecs Mplayer uses.

---

### Post by x-ray vision on 2007-04-09
Tried that earlier. Didn't work for me.

---

### Post by Perfect Storm on 2007-04-09
Well, my experience is that newer/some/latest WMV aren't working. Does other formats works?

---

### Post by x-ray vision on 2007-04-09
Yeah, I can watch Quicktime clips.

---

### Post by krussell on 2007-04-09
Hello :-)
Best if you go to mplayer web page ([www.mplayerhq.hu](www.mplayerhq.hu)) and download the ALL the codecs (can be Found in Download page) you can find. After download, copy all the codecs (unzip the downloaded files) in /usr/lib/codecs. (if the 'codecs' directory doesn't exist, create it). Then open console and "cd" to /usr/lib and give command "ln -s codecs win32"
Now try running the WMV files. If that doesnot work, try to install mplayer from source. Its always better to compile mplayer from source (IMO).

To compile mplayer:
./configure --enable-gui
make
make install (super user)

---

### Post by nudnik on 2007-04-09
> **x-ray vision said:**
> Yeah, I can watch Quicktime clips.

Hey...remember me? You don't sleep do you? All the best people are insomniacs anyway:) 

Have you tried totem-xine yet? It may not be as horrible as gxine.

sudo apt-get install totem-xine

If it is as horrible or doesnt work at all, feel free to slap me around a bit.

---

### Post by maxim1 on 2007-04-09
Use synaptic package manager its all there. I have only been running Linux for 3 days and every thing is there.

or you can use easyubuntu

---

### Post by Akkara on 2007-04-09
I used the above code to install the codecs, but got some installation errors:

> Couldn't find package " gstreamer0.10-plugins-good".  However, the following
packages contain " gstreamer0.10-plugins-good" in their name:
  gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg 
  gstreamer0.10-plugins-good-doc 
Couldn't find any package whose name or description matched "gstreamer0.10-plugins-bad-multiverse"
Couldn't find package " gstreamer0.10-plugins-ugly".  However, the following
packages contain " gstreamer0.10-plugins-ugly" in their name:
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg 
  gstreamer0.10-plugins-ugly-doc 
Couldn't find any package whose name or description matched "gstreamer0.10-plugins-ugly-multiverse"
No candidate version found for libxine-extracodecs
No candidate version found for w32codecs
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


and i am getting the "no video" problem as well. Any help would be appreciated :)

---

### Post by Mets on 2007-04-10
DO NOT remove the Ubuntu Desktop package.  It will remove Gnome :)

Please recap what steps you have done.  Did you install the dumby .deb file?  First you need to do that, it will force firefox to use mplayer always.

Then, you need to repeat the steps to install all the goodies with mplayer.

I actually haven't done this all the way but I know the gist of what needs to happen.
Also note, if you get sick of doing this, both totem and mplayer will give you url of the file they are trying to play in firefox.  If you want, you can just copy the url and then open up VLC and open the stream.  VLC will literally play almost anything fresh out of the box even though the plugin won't work.  That's what I do and why I didn't bother with mplayer.  It will play BBC, CNN, etc. However beefing up mplayer will work in the end if all of the steps are followed.  Let us know what's going on.

---

### Post by moffa on 2007-04-10
Do you have the universe, multiverse repositories enabled under Settings > Repositories in Synaptic?

x-ray: try launching firefox using the terminal to see if any errors popup.

---

### Post by TheRingmaster on 2007-04-10
> **Mets said:**
> DO NOT remove the Ubuntu Desktop package.  It will remove Gnome :)

Please recap what steps you have done.  Did you install the dumby .deb file?  First you need to do that, it will force firefox to use mplayer always.

Then, you need to repeat the steps to install all the goodies with mplayer.

I actually haven't done this all the way but I know the gist of what needs to happen.
Also note, if you get sick of doing this, both totem and mplayer will give you url of the file they are trying to play in firefox.  If you want, you can just copy the url and then open up VLC and open the stream.  VLC will literally play almost anything fresh out of the box even though the plugin won't work.  That's what I do and why I didn't bother with mplayer.  It will play BBC, CNN, etc. However beefing up mplayer will work in the end if all of the steps are followed.  Let us know what's going on.
Like I said before, the ubuntu-desktop package is just a meta-package. It is safe to remove it. It will not remove anything.

---

### Post by ubunter1 on 2007-04-11
now that i use edgy im having the same problem ,tried all the codecs of gxine and the like, now i tried all the mplayer codecs and does not work,im trying to watch a video from here(screen attached) but to no avail.any ideas?.thanks.

---

### Post by ubunter1 on 2007-04-11
i replaced all the mplayer stuff with the totem gstreamer,and it plays other videos but not the one at the site im trying to view,so closer but...

error reads as- Totem could not play 'http://wms.scripps.com/library/HGTV_Pro/66923.wmv?site=hpro=HGTV Pro=UP HGTV Pro - Best Practices=Framing'.

---

### Post by Mets on 2007-04-12
Well if the mplayer ways talked about in this post don't work then I have no idea.  Don't waste your time with Totem, it's well regarded by most as quite useless.  I've noticed that there are some things linux is great at and there are other things it's terrible at.  Getting all the different media to work is one of those things, partly do to the fact that people try to make software that is entirely open source, partly because we're dealing with proprietary formats.  Like I said earlier, if there is a video that doesn't work, just right click on it, get the link, and open up VLC and play it in that.  It plays HGTV video, CNN video, ESPN, etc.  It's not the most convenient thing, but it's better than nothing.

---

### Post by FrancoNero on 2007-05-01
using Mplayer instead of Totem works a lot better. but stil not able to watch anything above 480HD... any tips?
and when i set mediaconnectivity plugin to use Mplayer for quicktime embedded stuff, it doesn't really embed it, it opens a little windows, which is fine, but i have no control buttons or anything

---

### Post by Melhisedek on 2007-05-02
> **FrancoNero said:**
> but i have no control buttons or anything

same problem here, mostly when I want to pause some podcast or FF, REW :(

---

