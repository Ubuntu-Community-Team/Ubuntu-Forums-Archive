---
title: "I still can't play mp3's"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by nydadx1x on 2007-09-12
Hi, I'm new to linux and ubuntu.  I have had it installed for about a week now and after searching and downloading, working thru synaptic, using this website [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and asking friends, as well as searching this forum, mp3s, mpegs, avi's, and anything I was used to seeing/hearing in windows still doesn't play.  I am at my wits end with this.  I have probably 10 players installed and the best I've achieved is to get the little lock icons off of the music file icons.  Some of the things like kmplayer that are supposed to work don't even show up and I have no idea how  to access them.  Can anyone provide a simple solution?  I will try anything again, but this is getting frustrating.  Thanks for your time.

---

### Post by marco123 on 2007-09-12
Did you copy and paste the command on that webpage into the terminal?

---

### Post by Terl on 2007-09-12
all I used to get the mp3 support (and other good stuff) is:

```
sudo apt-get install ubuntu-restricted-extras
```

This also gets TT Fonts, Flash, java along with your mp3 support

---

### Post by Skrypt on 2007-09-12
> **Terl said:**
> all I used to get the mp3 support (and other good stuff) is:

```
sudo apt-get install ubuntu-restricted-extras
```

This also gets TT Fonts, Flash, java along with your mp3 support
This should work as it installs the gstreamers. If it doesn't, make sure you have them installed. Go to applications>add/remove programs. Make sure your showing all 'available applications' and not just 'supported applications'. search "gstreamer" and install the packages named as such.

---

### Post by stchman on 2007-09-12
> **nydadx1x said:**
> Hi, I'm new to linux and ubuntu.  I have had it installed for about a week now and after searching and downloading, working thru synaptic, using this website [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and asking friends, as well as searching this forum, mp3s, mpegs, avi's, and anything I was used to seeing/hearing in windows still doesn't play.  I am at my wits end with this.  I have probably 10 players installed and the best I've achieved is to get the little lock icons off of the music file icons.  Some of the things like kmplayer that are supposed to work don't even show up and I have no idea how  to access them.  Can anyone provide a simple solution?  I will try anything again, but this is getting frustrating.  Thanks for your time.

Try this:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

This will install the codecs you need.

---

### Post by nydadx1x on 2007-09-12
Thanks guys. Skript you rock.  mp3s and wmvs are playing great. Now I need to get avi's to play.  Thanks everyone for your help.

---

### Post by p_quarles on 2007-09-12
I had thought that AVI support was included in the restricted extras, but if not, you can run this command:
```
sudo apt-get install libavifile avifile-divx-plugin avifile-win32-plugin avifile-xvid-plugin
```
Be sure to use the "thread tools" button to mark this thread as solved when you get everything working.

---

### Post by Polemistis on 2007-09-12
> **nydadx1x said:**
> Hi, I'm new to linux and ubuntu.  I have had it installed for about a week now and after searching and downloading, working thru synaptic, using this website [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and asking friends, as well as searching this forum, mp3s, mpegs, avi's, and anything I was used to seeing/hearing in windows still doesn't play.  I am at my wits end with this.  I have probably 10 players installed and the best I've achieved is to get the little lock icons off of the music file icons.  Some of the things like kmplayer that are supposed to work don't even show up and I have no idea how  to access them.  Can anyone provide a simple solution?  I will try anything again, but this is getting frustrating.  Thanks for your time.


try using VLC.. works for me.. and plays almost all media types.

---

### Post by mcduck on 2007-09-12
> **p_quarles said:**
> I had thought that AVI support was included in the restricted extras, but if not, you can run this command:
```
sudo apt-get install libavifile avifile-divx-plugin avifile-win32-plugin avifile-xvid-plugin
```
Be sure to use the "thread tools" button to mark this thread as solved when you get everything working.

Well, actually avi-files work out-of-the-box, in theory at least. The problem is that avi is not a video format, just a container that can include video and audio in almost any format.. So you still need to install the codec that was used to compress the video inside the avi file..

Most of the time installing gstreamer plugins and w32codecs should do the job.

You can get w32codecs from the Medibuntu repository: [http://medibuntu.sos-sts.com/]("http://medibuntu.sos-sts.com/")

---

### Post by Midwest-Linux on 2007-09-12
Yea I had issues trying to get the player to stream audio on the net. For Ubuntu 7.04 it is extra steps involved. First Off delete Rhythum Box, its useless. Then download the restricted G Streamers, use Totem to listen to audio stream...but even then one must type in the listen now link into totem for it to stream.

 Try instead Linux Mint 3.0 Cassandra, it does streaming audio, mp3 and video "out of the box" with no extra steps. Same for Freespire 2.0. Linux Mint is based from Ubuntu 7.04 and in my opinion the best of the Linux variants.

 While you are at it, do a search for LiNsta3, it is a theme that makes your Ubuntu look like Vista. You should see it in Puppy linux!

---

### Post by nydadx1x on 2007-09-12
Sorry, nothing so far has worked for the avi's.  

Midwest, how do I download and install the programs you mentioned?

Thanks for the help so far.

---

### Post by nydadx1x on 2007-09-12
McDuck I found the codecs you mentioned, but I don't know what to do with them.  Copying them to 'terminal' hasn't worked...I'm not sure what to do with them.

---

### Post by Midwest-Linux on 2007-09-12
In Ubuntu 7.04, go to add/remove programs. After that opens up, on the very top you will see a menu click that and it should give you options for Ubuntu suported programs and inclucing all available. Select all available, then look under media on the menu window to the left. Select it and it should give you a whole list of programs to install. Click the G-Streamer restricted modules. Also click Rythumbox (to get rid of it..since it comes already installed), try to download VLC player too.

 As you click off each one, it will say something including like the G-Streamer disclaimers. Ignore the disclaimers and click them..(there is a slight lag as you do this). When you are finished, click apply and (MAKE SURE YOU ARE CONNECTED TO THE INTERNET AS YOU DO THIS). It will download and install it.

 Hopefully then it should be able to let you do MP3's. Ironically as great as Ubuntu 7.04 ....and it is great...it suffers from not doing basics like mp3's and streaming. Linux Mint Cassandra which is based on Ubuntu 7.04 already takes care of that issue out of the box. Its a enhanced Ubuntu thats feature rich. You might want to go and just install Linux Mint instead.

---

### Post by p_quarles on 2007-09-12
It's not "ironic" so much as it satisfies legal requirements. Ubuntu doesn't distribute MP3 and other codecs because they are the subject of patent disputes. Likewise, Mint politely asks that you not download their distro from a country which recognizes software patents (which includes the US). It's inconvenient, but Ubuntu is just covering their behinds. 

Also, the original command I gave for the .avi plugins omitted the version number of the main file.  This is the corrected version:
```
sudo apt-get install libavifile-0.7c2 avifile-divx-plugin avifile-win32-plugin avifile-xvid-plugin
```

---

### Post by nydadx1x on 2007-09-12
p_quarles, I put that in and got:

Package avifile-divx-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avifile-divx-plugin has no installation candidate

Mpegs and mp3's are playing fine in totem, avi's aren't.  

Btw everyone, I'm running 6.06

---

### Post by p_quarles on 2007-09-12
> **nydadx1x said:**
> p_quarles, I put that in and got:

Package avifile-divx-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avifile-divx-plugin has no installation candidate

Mpegs and mp3's are playing fine in totem, avi's aren't.  

Btw everyone, I'm running 6.06
I know others have already mentioned this, but have you enabled the Medibuntu repositories? If not, the following two commands will do so:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
After you've entered those, update your cache:
```
sudo apt-get update
```
and then try to install the avi plugins again.

---

### Post by nydadx1x on 2007-09-12
Getting the same error message:

Package avifile-divx-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avifile-divx-plugin has no installation candidate


Midwest, it won't let me delete rythumbox.

---

### Post by p_quarles on 2007-09-12
I guess it's possible that those packages just aren't available for 6.06. They are definitely available for 7.04, so I'd recommend you upgrade to that unless you have a good reason not to. The long-term support editions are mainly useful for servers and for desktops with slow internet connections.

---

### Post by jjalocha on 2007-09-12
I would second the use of VLC, too. it seems to have the best support of different formats:
[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)
And you don't have to upgrade to a newer Linux version.

---

### Post by nydadx1x on 2007-09-13
Ok, I got avi's to play sound, but no video.

---

### Post by Terl on 2007-09-13
Open synaptic and search for avi.  You will see the packages you need there.  It  worked for me last night.

---

### Post by nydadx1x on 2007-09-13
Ok thanks Terl, I'll give it a shot.

---

### Post by nydadx1x on 2007-09-13
I went in and found the avi files in Synaptic, installed them, and I still have no video..just sound.  Everything else seems to work fine.  Does anyone know why music or video that doesn't work on anything defaults to noatun?  Just wondering, it's really not that important.

---

