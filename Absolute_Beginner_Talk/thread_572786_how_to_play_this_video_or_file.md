---
title: "how to play this video or file?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ubunter1 on 2007-10-10
hi,i dont know what kind of file or how to play it the link is here- [http://www.hgtvpro.com/hpro/pac_ctnt/text/0,2595,HPRO_20196_55073,00.html?c=486&videoid=66923](http://www.hgtvpro.com/hpro/pac_ctnt/text/0,2595,HPRO_20196_55073,00.html?c=486&videoid=66923)
also,i cant watch videos from bbc website or sometimes im prompted to download the macromedia plugins which i already did. what should i do ive tried all the combos of codecs and players,i have vlc,xine,real,mplayer and its codecs.i run firefox as well so maybe the problem is the embedded player. what to do?,thanks for your time.

---

### Post by Gun_Smoke on 2007-10-10
Do you have the NoScript add-on for FireFox?  It will stop a lot of videos from playing unless you have allowed the site.

---

### Post by ubunter1 on 2007-10-10
i just unchecked the box,or i guess i can add the url of the site or video?,will try now.
it still wont work.

---

### Post by Gun_Smoke on 2007-10-10
If you do have NoScript installed in the bottom right corner of the browser you should see a white circle with a blue S in the center of it.  Look in tools>add-ons.

I'm betting you do, right click the S and choose allow hgtvpor.com then try again.

---

### Post by ubunter1 on 2007-10-10
> **Gun_Smoke said:**
> If you do have NoScript installed in the bottom right corner of the browser you should see a white circle with a blue S in the center of it.  Look in tools>add-ons.

no i definitely don't have that then,any thing else i can try?. thanks for the help too.

---

### Post by srt4play on 2007-10-10
I'm able to play the video in firefox with the mozilla-mplayer plugin.

You could make sure totem-mozilla is uninstalled and install mozilla-mplayer.  Other than that just make sure you have w32codecs installed and all of the gstreamer0.10-plugins packages installed (bad, ugly, etc.).

---

### Post by Incense on 2007-10-10
What plug in do you have in firefox for handling video? Maybe you should try the mplayer-mozilla plug in from the repos. Seems to handle most web video without a hitch.  

EDIT: srt4play beat me to it.

---

### Post by ubunter1 on 2007-10-10
thanks for the replys i just reinstalled the plugins which i already had except for the gstreamer ugly,bad, ones which i put in now.

edit-- i just tried to play it again but it will not play,so i went to the video tips and they have 2 sections- # Update Windows Media player to the most recent version.

# Update Flash Player to the most recent version.

---

### Post by kerry_s on 2007-10-10
yeap, it plays in mplayer. pic->

---

### Post by gigaferz on 2007-10-10
[http://ubuntuforums.org/showthread.php?t=432873&highlight=divx+xvid](http://ubuntuforums.org/showthread.php?t=432873&highlight=divx+xvid)

---

### Post by ubunter1 on 2007-10-10
> **kerry_s said:**
> yeap, it plays in mplayer. pic->

in synaptic it list me as having mplayer and mozilla, is there a directory to firefox that maybe says what player its using? for embedded videos?

---

### Post by steveneddy on 2007-10-10
> **srt4play said:**
> I'm able to play the video in firefox with the mozilla-mplayer plugin.

You could make sure totem-mozilla is uninstalled and install mozilla-mplayer.  Other than that just make sure you have w32codecs installed and all of the gstreamer0.10-plugins packages installed (bad, ugly, etc.).

Plays for me in Firefox with mplayer plugin and all the codecs installed.

:popcorn:

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> in synaptic it list me as having mplayer and mozilla, is there a directory to firefox that maybe says what player its using? for embedded videos?

Do you have the package "mozilla-mplayer" installed?

---

### Post by ubunter1 on 2007-10-10
> **srt4play said:**
> Do you have the package "mozilla-mplayer" installed?
yes and the codecs,i think maybe the path of which player might be the problem?,but dont know how to check.

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> yes and the codecs,i think maybe the path of which player might be the problem?,but dont know how to check.

Have you removed totem-mozilla?

---

### Post by ubunter1 on 2007-10-10
> **srt4play said:**
> Have you removed totem-mozilla?
yes,it was already gone.

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> yes,it was already gone.

How about mozilla-plugin-vlc?

---

### Post by ubunter1 on 2007-10-10
> **srt4play said:**
> How about mozilla-plugin-vlc?
remove that one?

i had that installed ,just removed it.

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> remove that one?

yes.

---

### Post by Frak on 2007-10-10
sudo aptitude install mozilla-mplayer

In Applications->Accessories->Terminal

---

### Post by ubunter1 on 2007-10-10
when i removed the vlc mozillamplayer plugin then restarted the video-mplayer buffers now but wont play video,so its closer than before.--

---

### Post by Frak on 2007-10-10
sudo aptitude install ubuntu-restricted-extras

In the terminal and try again

---

### Post by ubunter1 on 2007-10-10
> **Frak said:**
> sudo aptitude install ubuntu-restricted-extras

In the terminal and try again

robert@robert-desktop:~$ sudo aptitude install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  flashplugin-nonfree 
The following NEW packages will be installed:
  flashplugin-nonfree ubuntu-restricted-extras 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1920B/17.6kB of archives. After unpacking 143kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
robert@robert-desktop:~$

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> when i removed the vlc mozillamplayer plugin then restarted the video-mplayer buffers now but wont play video,so its closer than before.--

Close out and reopen firefox.  If that doesn't work try clicking the play button to get it to retry the video.

---

### Post by Frak on 2007-10-10
> **ubunter1 said:**
> robert@robert-desktop:~$ sudo aptitude install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  flashplugin-nonfree 
The following NEW packages will be installed:
  flashplugin-nonfree ubuntu-restricted-extras 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1920B/17.6kB of archives. After unpacking 143kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
robert@robert-desktop:~$
Make sure you don't still have Synaptic open.

Ubuntu doesn't allow more than one package manager to be open for Security reasons.

---

### Post by ubunter1 on 2007-10-10
> **srt4play said:**
> Close out and reopen firefox.  If that doesn't work try clicking the play button to get it to retry the video.
i did that and now it plays the commercial but not the video itself ??:confused: thats screwey.

---

### Post by ubunter1 on 2007-10-10
> **Frak said:**
> Make sure you don't still have Synaptic open.

Ubuntu doesn't allow more than one package manager to be open for Security reasons.

it wasnt open,so i tried it again and the same dialog box popuped up in terminal.

---

### Post by Frak on 2007-10-10
> **ubunter1 said:**
> it wasnt open,so i tried it again and the same dialog box popuped up in terminal.
Logout and log back in and see if that fixes it. Apt has problem where it hangs sometimes.

---

### Post by srt4play on 2007-10-10
> **ubunter1 said:**
> i did that and now it plays the commercial but not the video itself ??:confused: thats screwey.

Ok for one thing you don't need to worry about installing any more packages, it's working now in mplayer just not perfectly for some reason.  Is it going back to the mplayer screen that says "stopped" after the commercial?

---

### Post by ubunter1 on 2007-10-10
> **srt4play said:**
> Ok for one thing you don't need to worry about installing any more packages, it's working now in mplayer just not perfectly for some reason.  Is it going back to the mplayer screen that says "stopped" after the commercial?
yes it is. i will restart too as recommend by frak.  thank you both for the help.

---

### Post by FuturePilot on 2007-10-10
For some odd reason the Mplayer divx plugin doesn't get linked into the Firefox plugins directory.
Try this and then restart Firefox.
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/

```

---

### Post by ubunter1 on 2007-10-10
> **FuturePilot said:**
> For some odd reason the Mplayer divx plugin doesn't get linked into the Firefox plugins directory.
Try this and then restart Firefox.
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/

```

i just tried that quote and it didn't do anything but at the end of it it said file exists.retried the video but only the ad works.

robert@robert-desktop:~$ sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/
ln: creating symbolic link `/usr/lib/firefox/plugins/mplayerplug-in-dvx.so' to `/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so': File exists
robert@robert-desktop:~$ sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/
ln: creating symbolic link `/usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt' to `/usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt': File exists
robert@robert-desktop:~$

---

### Post by ubunter1 on 2007-10-10
it just worked,so now i will try my other pages that it usually doesnt play from,bbc and tv-links. thank you all for the help,hopefully it doesnt screw up :guitar:

---just tried to watch another video and it did not work,then went back to original video and it didnt work again.

---

