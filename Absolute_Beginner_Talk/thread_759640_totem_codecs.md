---
title: "totem codecs"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-04-19
i installed totem-xine to replace totem-gstreamer or whatever because gstreamer doesnt support the dvd menu "and never will"... but now it says that i lack the codecs to play the dvd... how do i get them?

---

### Post by freduardo on 2008-04-19
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

This should help you install the necessary stuff ;)

---

### Post by Tatty on 2008-04-19
```
sudo apt-get install libdvdcss2
```  should do it I think.  You need the medibuntu repo enabled.

---

### Post by manicmailman on 2008-04-19
> **Tatty said:**
> ```
sudo apt-get install libdvdcss2
```  should do it I think.  You need the medibuntu repo enabled.

what do you mean have the medibuntu repo enabled?...
im pretty sure i installed the css2 librarys already but ill check now...
and i have restricted drivers... er formats...

---

### Post by Tatty on 2008-04-19
> **manicmailman said:**
> what do you mean have the medibuntu repo enabled?...
im pretty sure i installed the css2 librarys already but ill check now...
and i have restricted drivers... er formats...

The link in Freduardo's post should explain everything :)

---

### Post by manicmailman on 2008-04-19
yeah i just checked and i already got libdvdcss2

---

### Post by manicmailman on 2008-04-19
k thanks for the referral to that site... i have done it before to get it working (gstreamer) before.. i didnt know i had to do it again..

side note now... (im using my south park dvds to try it out).... there are horizontal lines on the things that are moving... is there a preference i can tweak to enhance playback?

---

### Post by crjackson on 2008-04-19
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by manicmailman on 2008-04-19
> **crjackson said:**
> Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

k... now i still have the "lines" problem, but 3 different movie players to showcase them with.. haha... although xine is nice...

---

### Post by mc4man on 2008-04-19
I don't have that title but it may be interlaced - try (for xine) view> check deinterlace

---

