---
title: "VLC for Movie Trailers"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-05
When I use to use Mandriva I had a way to set up mplayer to view just about any kind of video on the Internet, although some MS Media files were a bit of a problem. This set up involved not only the installation of mplayer, but also libdvdcss, Win32 Codecs, mozilla-plugger and stuff like that. When I finally got it working it seemed to work great. It also allowed me to view DVD movies and made my machive quite and all around machine. Needless to say the set up of this didn't always go all that smooth at times.

Anyhow, I was reading on about a program called VLC as an option to what I was doing with Mplayer. I downloaded a package from the VLC website which included a plugin for Firefox, etc. Something happened because instead of getting the typical little green puzzle piece telling you there was a plugin missing the portion of the screen where the video would normally play went black and the words "no picture" appeared in the center of that, but the video never did play.

Just wondering if:

1. I am missing something that is keeping VLC from doing what I want and if so, does anyone know what that is?

2. If there is a better way to accomplish what I want using ubuntu.

Cheers!

---

### Post by gkiller on 2006-09-05
Yes, VLC is quite a good media player. I use it as my standard player. But it does not play every possible media file. For example it cannot play most of the WMV files. For those I use mplayer.

I am not familiar with the VLC browser plugin, so I don't know how good it is compared to mplayer (which is IMHO the best at the moment, when all codecs are installed)

If you want the best multimedia format compatibility, the way is about the same as you described for Mandriva.

But there is a good wiki page that explains everything. By following these instructions you should have everything set up quite easily:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I have the following media players installed: totem-gstreamer, gxine, mplayer, vlc. One of them works almost always for a video file.

The browser plugins are the most difficult to get to work correctly. I use the mplayer plugin with firefox, described here:
[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

You should know that having multiple video plugins installed at the same time can cause problems, so before installing a new one, uninstall the last one. But you can have the players installed at the same time, that's no problem.

BTW, vlc is also available in the universe repository, so you should not need to download it from the website. Just type 'sudo apt-get install vlc' in the Terminal, or select vlc in Synaptic or "Add/Remove..." from the menu.

---

### Post by Bigguy2468 on 2006-09-05
> **gkiller said:**
> Yes, VLC is quite a good media player. I use it as my standard player. But it does not play every possible media file. For example it cannot play most of the WMV files. For those I use mplayer.

I am not familiar with the VLC browser plugin, so I don't know how good it is compared to mplayer (which is IMHO the best at the moment, when all codecs are installed)

If you want the best multimedia format compatibility, the way is about the same as you described for Mandriva.

But there is a good wiki page that explains everything. By following these instructions you should have everything set up quite easily:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I have the following media players installed: totem-gstreamer, gxine, mplayer, vlc. One of them works almost always for a video file.

The browser plugins are the most difficult to get to work correctly. I use the mplayer plugin with firefox, described here:
[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

You should know that having multiple video plugins installed at the same time can cause problems, so before installing a new one, uninstall the last one. But you can have the players installed at the same time, that's no problem.

BTW, vlc is also available in the universe repository, so you should not need to download it from the website. Just type 'sudo apt-get install vlc' in the Terminal, or select vlc in Synaptic or "Add/Remove..." from the menu.

Thanks, I'll look into it.

---

