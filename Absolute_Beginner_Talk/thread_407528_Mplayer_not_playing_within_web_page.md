---
title: "Mplayer not playing within web page"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Gif on 2007-04-12
Hi,

I have installed mplayer and mozilla-mplayer plugin from Synaptic Manager, but when going to the BBC site and watching a clip within the news page the mplayer logo appears in the media box, underneath it says initialising for a while but no video or sound ever starts then it says stopped!

Does anybody know what I have done wrong here? 

Many Thanks

---

### Post by Paul41 on 2007-04-12
Have you installed the packages for restricted formats?

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

---

### Post by Gif on 2007-04-12
Hi,

yes have tried that along with the information [COLOR="DarkRed"] < [here]("http://www.cs.cornell.edu/~djm/ubuntu/") > [/COLOR] but no luck in playing media on bbc!

---

### Post by Gif on 2007-04-12
I have now tried Automatix, but still can't get a player to play media (BBC news etc) within firefox!

Is anybody that is running Xubuntu able to view media clips on the BBC site? if so what are you using for this what would seem to me a great great achievement - please advise...](*,) 

Many Thanks

---

### Post by Paul41 on 2007-04-12
I could be that the stuff on bbc is DRM protected. If that is the case you won't be able to play it. I am away from my Ubuntu computer right now, but I can try when I get home to see if I have the same problem.

---

### Post by Paul41 on 2007-04-12
Just to be sure I am looking at the same thing when I try it can you give me the url to the page with the clip?

---

### Post by pissedoffdude on 2007-04-12
Try opening up mplayer and right clicking so you can get to the preferences. Then go to the video tab, and select the second option. If it still doesnt work then when you are watching a firefox stream right click and click configure and a configuration window will appear, the first option is video and it has a drop down list. From that list choose X11

---

### Post by Gif on 2007-04-12
Ok - Thanks

The BBC site changes all the time, but as an example if you follow this link to the news section: [COLOR="Purple"][NEWS LINK,]("http://news.bbc.co.uk/")[/COLOR] then just look out for the little WATCH> logos which are dotted around in various places, the window should open and hopefully play!!!

---

### Post by Paul41 on 2007-04-12
Out of curiosity I just went to the site on a Windows computer and when I clicked the watch button it asked if I want to use Windows Media Player or Real Player. It says that Windows Media Player is not always available. Have you tried using Real Player?

---

### Post by Gif on 2007-04-12
Yes - I also tried that method through Automatix - Then when trying it, it went to play with the Real player appearing etc and........ It stopped

I also tried right clicking on the mplayer and the real player to change preferences without success!

---

### Post by Paul41 on 2007-04-12
I just tried and I can watch the windows media files with no problem. I am using Totem instead of mplayer. I don't know if that would make any difference for you but it might be worth a try.

---

### Post by Gif on 2007-04-13
Thanks

Yesterday with all the changes and installs that I've been doing I decided to re-install using the guidelines on this page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It says Totem is installed by default, but it would seem not in Xubuntu so I installed it from Synaptic, 

I then ensured relevant repositories were enabled and ran the Terminal code: 

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Next I went to the Streaming Video page:

[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)

Here it says, install the Windows Codecs, then install the totem-plugin. Went to follow this link (Windows Codecs) and found it did not work. Does anybody now the correct address for these"Codecs"?

---

### Post by Paul41 on 2007-04-13
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28windows%29%7C%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28windows%29%7C%28codecs%29)

---

### Post by Gif on 2007-04-13
Media still not playing after installing the codecs and reinstalling the Totem_Xine Firefox Plugin!

---

### Post by Gif on 2007-04-21
Finally it's up and running!

This is the method / order I used to get it all going:

1, > Installed mplayer via synaptic

2, > Installed the codecs as per [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28windows%29%7C%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28windows%29%7C%28codecs%29) (had a job to find these - link broken! so thanks Paul41)

3, > Installed the mozilla-mplayer plugin via synaptic

4, > When clicking to watch a BBC site clip, select Real Player in the preferences and mplayer should start

5, > mplayer appeared in another window, which I did not want - I wanted it in the web page so found that by right clicking on player and configure video output to X11 got it playing in the page as required (thanks pissedoffdude for putting me on the right track for that).

Thanks all
\\:D/

---

### Post by jasidog on 2007-04-21
Thanks for that comprehensive walk through there Gif. Got things up and running beautifully on my new fiesty install. Thanks!:)

---

### Post by bagguley on 2007-08-25
Hey,

sorry for rehashing an old thread, but whatever I do I cant get bbc video streams to work. Can anyone help me? (PLEASE) 

I have m-player, codecs and m-player pluggin for forefox install. The window opens when I click on video but thats as far as it get.

Cheers

---

### Post by philinux on 2007-08-25
Mine works fine but i'm damned if I can remember what I did. 

Have you installed the win32 codecs?

---

### Post by bagguley on 2007-08-25
yeah codecs are all installed, just wont work..dammit!!!

---

### Post by alienexplorers on 2007-08-25
In Firefox have you tried the add-on > MediaPlayerConnectivity along with the VLC media player.  This setup works for me.
BTW- I do have all codecs installed for VLC and mplayer.

---

### Post by Gif on 2007-08-28
Have you selected Real Player in the preferences?

---

### Post by bagguley on 2007-08-28
Right, thats worked (cheers) but i now have video but no sound now,

---

### Post by WebSiteGuru on 2007-08-28
> **alienexplorers said:**
> In Firefox have you tried the add-on  along with the VLC media player.  This setup works for me.
BTW- I do have all codecs installed for VLC and mplayer.

I concur with you on that. Use VLC/MediaPlayerConnectivity and load all the codecs to include restrict ones too. It will work with video and sound.

---

### Post by RKCole on 2007-08-28
I had this problem with some sites as well.  I do not know why or how this worked, but I installed the [MediaPlayerConnectivity plugin](https://addons.mozilla.org/en-US/firefox/addon/446) for Firefox, and things, for some reason, seem to work now.  It is a plugin, apparently, to launch streams in an external player.

Hope this may help.

Take care.

---

### Post by Gif on 2007-08-29
If I can remember correctly I had no sound too at one stage - try right clicking on player and configure video output to X11...

---

### Post by geovino on 2008-02-26
> **Gif said:**
> Hi,

I have installed mplayer and mozilla-mplayer plugin from Synaptic Manager, but when going to the BBC site and watching a clip within the news page the mplayer logo appears in the media box, underneath it says initialising for a while but no video or sound ever starts then it says stopped!

Does anybody know what I have done wrong here? 

Many Thanks

Just installed the package... but BBC videos still don't play. What else is needed?

---

### Post by backflip on 2008-02-26
I had exactly the same reaction as geovino and I just solved it by removing the mozilla plugin through synaptics and I can now view perfectly. The 'realplayer' option is blanked out and when I click on windows mediaplayer, it works with no problems.

---

