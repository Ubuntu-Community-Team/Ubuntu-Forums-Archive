---
title: "Plug-ins for video playback"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-10-02
I have been trying to find what I need to play video. I have Realplayer, VLC, Mplayer and various other players, but none will play avi or wmv.
What do I need to play pretty much anything thrown at it?
Larry:confused:

---

### Post by sonny on 2006-10-03
Yeap... that is because you don't have the codecs to play those files, you can install it by hand using the wiki [wiki.ubuntu.com]("http://www.ubuntuforums.org/wiki.ubuntu.com") go to documentation, and then to restricted formats. The other way is to install EasyUbuntu, look at this thread [http://www.ubuntuforums.org/showthread.php?t=84742](http://www.ubuntuforums.org/showthread.php?t=84742)

And check the multimedia part, and some other things you may want.

---

### Post by HareBall on 2006-10-03
> **sonny said:**
> Yeap... that is because you don't have the codecs to play those files, you can install it by hand using the wiki [wiki.ubuntu.com]("http://www.ubuntuforums.org/wiki.ubuntu.com") go to documentation, and then to restricted formats. The other way is to install EasyUbuntu, look at this thread [http://www.ubuntuforums.org/showthread.php?t=84742](http://www.ubuntuforums.org/showthread.php?t=84742)

And check the multimedia part, and some other things you may want.

OK, I downloaded EasyUbuntu. When I opened the ReadMe file it told me to double click EasyUbuntu. I did that and a open files dialog box opened. What next? It didn't open a run box like the ReadMe said it would. I typed in EasyUbuntu and nothing happened when I did that.
Larry

---

### Post by sonny on 2006-10-03
> **HareBall said:**
> OK, I downloaded EasyUbuntu. When I opened the ReadMe file it told me to double click EasyUbuntu. I did that and a open files dialog box opened. What next? It didn't open a run box like the ReadMe said it would. I typed in EasyUbuntu and nothing happened when I did that.
Larry

If it doesn't work, you can always install them manually, [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But it should work, or you can try this: [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by i-m-p on 2006-10-03
I had a similar problem. Did you try Automatix? It worked much better than easyubuntu for me.
> [http://www.getautomatix.com/](http://www.getautomatix.com/)

Sincerely.

---

### Post by HareBall on 2006-10-03
> **i-m-p said:**
> I had a similar problem. Did you try Automatix? It worked much better than easyubuntu for me.


Sincerely.
Yes, I used Automatix, but I still wasn't able to view the videos I was trying to watch. A couple were avi and a couple were wmv. Neither codec would run.
I haven't had a chance to try them since I loaded EasyUbuntu.
Let you know tomorrow.:D 
Later,
Larry

---

### Post by HareBall on 2006-10-03
Well, I haven't tried an avi file yet, but wmv seems to be working.

---

### Post by glenduncanscott on 2006-10-03
> **HareBall said:**
> Well, I haven't tried an avi file yet, but wmv seems to be working.

I've found the following applications get most video apps working. I prefer using System>Administration>Synaptic Package Manager to install rather than Automatix or EasyUbuntu, which has sometimes proved problematic, maybe it's just my system. Anyway here they are:

libdvdcss2 - DVD Decryption
libxine-extracodecs - Multimedia Codecs i.e. Quicktime
totem-xine - Media Player and Firefox plugin
vlc - Media Player for unusual formats
w32codecs - Multimedia audio and video codecs

Incidently never needed Realplayer or Mplayer installed.

Hope this helps...:grin:

---

### Post by HareBall on 2006-10-03
> **glenduncanscott said:**
> I've found the following applications get most video apps working. I prefer using System>Administration>Synaptic Package Manager to install rather than Automatix or EasyUbuntu, which has sometimes proved problematic, maybe it's just my system. Anyway here they are:

libdvdcss2 - DVD Decryption
libxine-extracodecs - Multimedia Codecs i.e. Quicktime
totem-xine - Media Player and Firefox plugin
vlc - Media Player for unusual formats
w32codecs - Multimedia audio and video codecs

Incidently never needed Realplayer or Mplayer installed.

Hope this helps...:grin:

I'll try these. Some of them were already installed.
I played a DVD earlier and it didn't play correctly. It looked like it was set for 8 bit color. Only a few different colors came through. Mostly red and blue.
Larry

---

### Post by HareBall on 2006-10-04
> **HareBall said:**
> I'll try these. Some of them were already installed.
I played a DVD earlier and it didn't play correctly. It looked like it was set for 8 bit color. Only a few different colors came through. Mostly red and blue.
Larry

I went and loaded the few of the files I didn't have and it did not seem to help. I have horrible replays of wmv and it still will not play avi files.
Any more ideas?
Larry:confused:

---

### Post by thoeng on 2006-10-04
Hello i am trying to follow ur suggestion but it seems i cant find the file below on my synaptic other than totem-xine & vlc
any idea ??

> **glenduncanscott said:**
> I've found the following applications get most video apps working. I prefer using System>Administration>Synaptic Package Manager to install rather than Automatix or EasyUbuntu, which has sometimes proved problematic, maybe it's just my system. Anyway here they are:

libdvdcss2 - DVD Decryption
libxine-extracodecs - Multimedia Codecs i.e. Quicktime
totem-xine - Media Player and Firefox plugin
vlc - Media Player for unusual formats
w32codecs - Multimedia audio and video codecs

Incidently never needed Realplayer or Mplayer installed.

Hope this helps...:grin:

---

### Post by bobpur on 2006-10-04
I'm going out on a limb here, but have you tried a different video driver?

---

### Post by HareBall on 2006-10-04
> **bobpur said:**
> I'm going out on a limb here, but have you tried a different video driver?
How do I find out what driver I have now? The only thing I know about my video is that it is an Integrated Intel Graphics Media Accelator 950. It is onboard a Dell motherboard. I went to the Intel site once, but couldn't figure out what I needed to do to update the driver, if anything.
Larry:confused:

---

### Post by HareBall on 2006-10-04
Can't anybody help me? Maybe I should already know how to find this, but I don't:( 
Larry

---

### Post by glenduncanscott on 2006-10-05
> **thoeng said:**
> Hello i am trying to follow ur suggestion but it seems i cant find the file below on my synaptic other than totem-xine & vlc
any idea ??

Have you updated your [respositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")? Might explain why you not seeing all the files suggested.:eek:

---

### Post by thoeng on 2006-10-05
Thanks i have downloaded and installed automatix2 beta and it work wonderfully.

---

