---
title: "quicktime video???"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-14
Now that I got sound working...

[http://www.ubuntuforums.org/showthread.php?t=129246](http://www.ubuntuforums.org/showthread.php?t=129246)

I have lots of video questions...but as per this thread, how can I watch quicktime format videos in ubuntu?  I have googled, and ran into the phrase "compile from source" and am wondering if there is a simpler way.  I have the basic breezy install and have not tweaked it or added anything.

---

### Post by kairu0 on 2006-02-14
Please see:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bountonw on 2006-02-14
Thank you for the link.

"If it is legal for you to play these formats..."

I live in Thailand and have just migrated from windows.  Used to point and click and it just works.  I am happy to learn and appreciate the patience of the forum here.  But it is a whole new world for me.

I know this is a dumb question (please restrain yourself from commenting on that one:) )...but I don't listen to much music or watch many videos, just point and click.  I thought MP3 and Quicktime were free.  If they are free, why aren't they legal.  Or under what circumstances are they legal or illegal?  When leaving microsoft, I had the choice of apple or linux.  I chose linux and with that decision, I wanted to be legal. So would appreciate advice on this.

---

### Post by anirban.sam on 2006-02-14
install libquicktime

---

### Post by bountonw on 2006-02-14
Installed.  Now what?  When I click on the movie trailer that I want to watch, I am instructed to manually install a plugin.  Not sure what to do as the link says that there are no quicktime plugins for firefox.

https://pfs.mozilla.org/plugins/?action=missingplugins&mimetype=video/quicktime&appID={ec8030f7-c20a-464f-9b0e-13a3a9e97384}&appVersion=2006012415&clientOS=Linux%20i686&chromeLocale=en-US

---

### Post by holomorph on 2006-02-14
bountonw,
not sure about quicktime specifically, but i assume it's similar to MP3 as far as the legalities go.  So, as I understand it, the deal with mp3 is, it's patented technology, and if you write any software that plays mp3s you have to (in the US at least) pay a small licence fee to the patent holders for each copy of the software you distribute.  When you buy a copy of windows, for example, the fee for using mp3 and several other proprietary formats is included in the cost.  Since Ubuntu is distributed for free, obviously they can't afford to pay for a licence for each person that installs Ubuntu.  That's why a lot of multimedia doesn't work "out of the box" with ubuntu.  

In some contries, the law does not require such a fee, so you should check the laws for your contry and see.  Also, as I understand it, if you own a copy of windows (that you are not using on a different computer), you are allowed to install the 'win32codecs' and use them legally.

If any of that is not accurate, :I hope someone corrects me.

Bjorn

---

### Post by holomorph on 2006-02-14
btw, I've found the mozilla-mplayer package (mplayer plugin for mozilla/firefox) works best.

---

### Post by nanotube on 2006-02-15
yea, to play quicktime in firefox, mplayer-plugin is the best.

for more info on getting various formats to play on ubuntu, try this link:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#DVD.2C_Video.2C_and_Audio_playback)

also the restricted formats link provided before is useful.

---

