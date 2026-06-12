---
title: "M-Player error"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by J_P on 2005-12-17
I am still having problems playing video files from the web so installed M-Player with no problems until now,When a link is clicked to start playing a video file now i am getting a error message (New_face failed,Maybe the font path is wrong,Please supply the text font file ~/.mplayer/subfont.tff) :confused: 

What players do most of you use with ubuntu ? I have three installed and still have problems playing any videofiles from the web :confused: 

I have been doing well with ubuntu till now and have figured out most things but this is screwing me up,PLEASE HELP!

---

### Post by sterrac on 2005-12-17
I get the same message when I start M-player, but after I click ok it works. At least it plays my video. Not that that fixes your problem.

Shane

---

### Post by J_P on 2005-12-17
I get the error message every time i open M-Player,Even totem will not play video files from the web,Even though codecs have been installed, I'm sure this is a very simple error i am missing somewhere.

---

### Post by kaamos on 2005-12-17
As posted by bored2k in here [http://ubuntuforums.org/showthread.php?t=85190&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=85190&highlight=mplayer)
> 
4. Assuming that you've downloaded the Microsoft core fonts (by installing msttcorefonts), do this:

```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
```

This just creates a link to a font to the location where mplayer is looking for it.
If you still get the error, try this:
```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /home/**username**/.mplayer/subfont.tff
```

---

### Post by endangst on 2006-01-09
Hi, I tried what you said after installing the fonts, but this is the error I get:

endangst@ubuntu:~$ sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
ln: creating symbolic link `/usr/local/share/mplayer/subfont.ttf' to `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf': No such file or directory

Thanks in advance for any help.

---

### Post by Perfect Storm on 2006-01-09
Try first:

(require multiverse enable in your sourcelist)
```

sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v

```

Then what kaamos suggested.

---

### Post by endangst on 2006-01-09
```
endangst@ubuntu:~$ sudo fc-cache -f -v
fc-cache: "/usr/share/fonts": caching, 0 fonts, 2 dirs
fc-cache: "/usr/share/fonts/truetype": caching, 0 fonts, 18 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-devanagari-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bitstream-vera": caching, 10 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/freefont": caching, 12 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/openoffice": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-arabeyes": caching, 39 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/arphic": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/baekmuk": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bengali-fonts": caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gujarati-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-kannada-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-malayalam-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-oriya-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-punjabi-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-tamil-fonts": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-telugu-fonts": caching, 2 fonts, 0 dirsfc-cache: "/usr/share/fonts/truetype/kochi": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-mgopen": caching, 16 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/msttcorefonts": caching, 60 fonts, 0 dirs
fc-cache: "/usr/share/fonts/type1": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/type1/gsfonts": caching, 35 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts": caching, 0 fonts, 5 dirs
fc-cache: "/usr/share/X11/fonts/encodings": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/encodings/large": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/100dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/75dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/misc": caching, 55 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/misc/misc": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/Type1": caching, 44 fonts, 0 dirs
fc-cache: "/usr/local/share/fonts": caching, 0 fonts, 0 dirs
fc-cache: "/home/endangst/.fonts": skipping, no such directory
fc-cache: succeeded
endangst@ubuntu:~$ sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
ln: creating symbolic link `/usr/local/share/mplayer/subfont.ttf' to `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf': No such file or directory
endangst@ubuntu:~$

```

Hi again.  I did what you said and it is still giving me the "no such file or directory" message unfortunately.

---

### Post by greenstar on 2006-01-10
endangst:

I had the same error msg.

I found that the directory in which we're trying to create a symlink (/usr/local/share/mplayer) didn't exist, so:

1. ```
sudo mkdir /usr/local/share/mplayer
```

creates the necessary directory.

2. Check this by going to: Places->Computer->Filesystem and browsing to: /user/local/share/mplayer. Leave this File Browser window open, we'll be checking this again in a minute.

3. Then we try:

> As posted by bored2k in here [http://ubuntuforums.org/showthread.p...hlight=mplayer](http://ubuntuforums.org/showthread.p...hlight=mplayer)
Quote:
Assuming that you've downloaded the Microsoft core fonts (by installing msttcorefonts), do this:

Code:

sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf



4. Now look in the /user/local/share/mplayer directory we left open in step 2. You should see a file named subfont.ttf in this directory now.

5. Try MPlayer now.

6. If you still get the "New_face failed" error, click OK, then click the little wrench icon (Settings) on the left edge of the mplayer control window (The one whose titlebar says only *MPlayer*, not *MPlayer-Video*), click OK on the "...you need to restart playback for some options to take effect." message, then click the Font tab. We have to tell MPlayer where to look for the symlink to the font file.

7. In the empty line for the font directory (Font:), paste the following: 

/usr/local/share/mplayer/subfont.ttf

The easiest way is to highlight the above line, then click in the empty line with both mouse buttons at the same time.

8. Click OK on the MPlayer Preferences window, then close MPlayer.

9. Reopen MPlayer and see if it's fixed.

Hope this helps.

Greenstar

---

### Post by greenstar on 2006-01-10
endangst:

I had the same error msg.

I found that the directory in which we're trying to create a symlink (/usr/local/share/mplayer) didn't exist, so:

1. ```
sudo mkdir /usr/local/share/mplayer
```

creates the necessary directory.

2. Check this by going to: Places->Computer->Filesystem and browsing to: /user/local/share/mplayer. Leave this File Browser window open, we'll be checking this again in a minute.

3. Then we try:

> As posted by bored2k in here [http://ubuntuforums.org/showthread.p...hlight=mplayer](http://ubuntuforums.org/showthread.p...hlight=mplayer)
Quote:
Assuming that you've downloaded the Microsoft core fonts (by installing msttcorefonts), do this:

Code:

sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf



4. Now look in the /user/local/share/mplayer directory we left open in step 2. You should see a file named subfont.ttf in this directory now.

5. Try MPlayer now.
If you still get the "New_face failed" error, click OK on the error message.

6. We have to tell MPlayer where to look for the symlink to the font file. Next click the little wrench icon (Settings) on the left edge of the mplayer control window (The one whose titlebar says only *MPlayer*, not *MPlayer-Video*), click OK on the "...you need to restart playback for some options to take effect." message, then click the Font tab. 

7. In the empty line for the font directory, paste the following: 

/usr/local/share/mplayer/subfont.ttf

The easiest way is to highlight the above line, then click in the empty line with both mouse buttons at the same time.

8. Click OK on the MPlayer Preferences window, then close MPlayer.

9. Reopen MPlayer and see if it's fixed.

Hope this helps.

Greenstar

Edit: Correct typos & clarification.

---

### Post by kewl1uk on 2006-02-01
Thanks greenstar. That worked for me.

---

### Post by kpurcell on 2006-02-01
Thanks greenstar.  Your suggestion also worked for me except for one thing.  For some reason when I cut and paste it did not work.  But when I browsed to the subfont.ttf file it did.

---

### Post by gerdjan on 2006-09-17
Thanks a lot greenstar, you helped me fix a truly annoying little bugger!

---

