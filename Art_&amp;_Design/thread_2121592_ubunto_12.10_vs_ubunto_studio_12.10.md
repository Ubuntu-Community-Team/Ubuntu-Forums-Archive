---
title: "ubunto 12.10 vs ubunto studio 12.10"
date: 2013-03-02
forum: Art &amp; Design
---

### Post by brianv7 on 2013-03-02
I'm new to ubuntu but loving every second of it so far.  Question: I am into the arts, video,music etc. and i see there is a "studio" version of ubunto. I've looked at and found that the programs on Studio i can also get in just the regular version on ubunto. I'm loving 12.10, and getting used to it. should I go ahead make the change to "studio"? what is the big difference? :guitar:

---

### Post by tgalati4 on 2013-03-02
You could take standard Ubuntu and add these packages:

tgalati4@Mint14-Extensa ~ $ apt-cache search ubuntu studio
plymouth-theme-ubuntustudio - Ubuntu Studio Plymouth theme
ubiquity-slideshow-ubuntustudio - Ubiquity slideshow for Ubuntu Studio
ubuntustudio-audio - Transitional Package for the Audio Seed
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-controls - Ubuntu Studio Controls is a small app that changes A/V settings.
ubuntustudio-default-settings - default settings for the Ubuntu Studio desktop
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-font-meta - Ubuntu Studio fonts Package
ubuntustudio-generation - Ubuntu Studio Audio Generation Package
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-icon-theme - Ubuntu Studio Icon Theme
ubuntustudio-lightdm-theme - UbuntuStudio LightDM theme
ubuntustudio-live-settings - configuration for the Ubuntu Studio live-dvd
ubuntustudio-look - Ubuntu Studio look
ubuntustudio-menu - Menu for Ubuntu Studio
ubuntustudio-photography - Ubuntu Studio Photography Package
ubuntustudio-publishing - Ubuntu Studio Publishing Package
ubuntustudio-recording - Ubuntu Studio Audio Recording Package
ubuntustudio-screensaver - Ubuntu Studio screensaver
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers

And that would get you 99% of Ubuntu studio.  I don't know if there are kernel tweaks (like smaller increment clock slices, or real-time kernel capability enabled).  There is a subforum for Ubuntu Studio:  [http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)  Spend some time reading the forum posts so you get a feel for the differences.  If you are serious about artistic creation, then you should simply install Ubuntu Studio.  If you are a dabbler, then you can simply add the programs that you want to dabble with on standard Ubuntu.  For instance if you want to dabble in digital photography, but don't care about music or publishing, then you could simply install the photography package:

In a terminal:

```
sudo apt-get install ubuntustudio-photography
```

That will pull in the following packages:

tgalati4@Mint14-Extensa ~ $ apt-cache depends ubuntustudio-photography
ubuntustudio-photography
  Depends: argyll
  Depends: darktable
  Depends: gimp
  Depends: gimp-data-extras
  Depends: gimp-gap
  Depends: gimp-plugin-registry
  Depends: gimp-resynthesizer
    gimp-plugin-registry
  Depends: gimp-ufraw
  Depends: gnome-color-manager
  Depends: icc-profiles-free
  Depends: phatch
  Depends: rapid-photo-downloader
  Depends: rawtherapee
  Conflicts: ubuntustudio-photography:i386

---

### Post by brianv7 on 2013-03-02
tanX! :)

---

