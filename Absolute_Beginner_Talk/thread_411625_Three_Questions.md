---
title: "Three Questions"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-17
I wondered is someone could tell me what folder contains the basic selection of wallpapers available with 6.06? I wanted to store a digital camera image there so it always was on my desktop when Ubuntu boots up.

My soundcard is a fairly generic 5.1 card with the C Media 8738/C3DX chip.
Can I enable the full features of the card in Ubuntu? I get basic sound, but no output to the subwoofer.

Can I import Tru Type fonts for use by Open Office and Ubuntu?
I particularly wanted to do this so Web pages  and documents display properly when they used the Times New Roman and Arial fonts.

---

### Post by igknighted on 2007-04-17
> **Neil Purling said:**
> I wondered is someone could tell me what folder contains the basic selection of wallpapers available with 6.06? I wanted to store a digital camera image there so it always was on my desktop when Ubuntu boots up.

My soundcard is a fairly generic 5.1 card with the C Media 8738/C3DX chip.
Can I enable the full features of the card in Ubuntu? I get basic sound, but no output to the subwoofer.

Can I import Tru Type fonts for use by Open Office and Ubuntu?
I particularly wanted to do this so Web pages  and documents display properly when they used the Times New Roman and Arial fonts.

All Ubuntu fonts are true type.  There is a package called mstruetype or msttf in the repos if you want MS's specific fonts.

---

### Post by Bachstelze on 2007-04-17
1) What exactly do you mean by "when Ubuntu boots up" ?

2) Don't know about that one, sorry.

3) Yes, Ubuntu can use TTF fonts but I can't tell you how to install them graphically in Gnome as I use KDE. To install them from the command line, copy the ttf files in ~/.fonts if you want them installed just for yourself or in /usr/share/fonts to install them system-wide.

igknighted : The package with those MS fonts is *msttcorefonts*.

---

### Post by msak007 on 2007-04-17
> **Neil Purling said:**
> I wondered is someone could tell me what folder contains the basic selection of wallpapers available with 6.06? I wanted to store a digital camera image there so it always was on my desktop when Ubuntu boots up.
Maybe a Gnome user can chime in here since I'm not sure where those are stored in Ubuntu. I know in KDE the default wallpapers are stored in /usr/share/wallpapers, and in XFCE they're stored in /usr/share/xfce4/backdrops. But when I want to specify a custom image (not included by default, such as in your case a picture from a camera), I can point it to that file and it imports it as a background and stores in in my home folder. You don't need to put the picture you want to use as a wallpaper in the default folder for it to show up, you should be able to just select the file and it'll do the rest for you.

> **Neil Purling said:**
> My soundcard is a fairly generic 5.1 card with the C Media 8738/C3DX chip.
Can I enable the full features of the card in Ubuntu? I get basic sound, but no output to the subwoofer.
Just a stab in the dark here, but can you type "alsamixer" in the terminal? This should bring up an audio tweaking tool for ALSA. Check for anything that has "MM" under it or is turned all the way down, and report back. Even better if you can take a screenshot of that output, we might be able to determine if anything is muted.

---

### Post by Neil Purling on 2007-04-17
If I am opening a document written with *Word* or Lotus *Word Pro* I wanted to have a selection of their native fonts. I can extract them from my Windows partition.
I wanted to install them so Firefox Web pages and all sorts of documents display naturally if they were written with the imported fonts.

---

### Post by WakkiTabakki on 2007-04-17
Wallpapers:
1. Create a folder in your home directory
2. Copy all the wallpapers into that folder
3. Right-click on your desktop and choose 'Change Desktop Background'
4. Click 'Add wallpaper'
5. Choose the images from step 2
6. Now those images are available as wallpapers


Fonts:
1. Start a terminal
2. Type
```
sudo nautilus /usr/share/fonts/ttf
```
3. Copy your ttf-fonts into that folder
4. Run
```
sudo dpkg-reconfigure fontconfig
```
5. The new fonts should now be available

Sound card:
Yup, I'd suggest you bring up the mixer and open the preferences. Here you can add a lot of tracks, and one of them may be the subwoofer... 


Cheers 
/N

---

### Post by Neil Purling on 2007-04-17
With the sound issue I took a screenshot of AlsaMixer. What do you make of it?

---

### Post by Neil Purling on 2007-04-18
With respect to my sound problem: Does the driver not support 5 channel (front pair, rear pair & centre/subwoofer)

---

### Post by WakkiTabakki on 2007-04-18
1. On your panel, there's a speaker (picture), doubleclick this.
2. Make sure it's showing the Alsa-device (not OSS). You can change devices under the File-menu
3. Start the preferences from the Edit menu
4. Choose all the tracks 
5. Play around with the mixer until it works...

The alsamixer you found is basically the same, only the non-graphical one (got that '80:s-feel).

Good luck
/N

---

### Post by Neil Purling on 2007-04-18
Nope, it doesn't make any difference whatsoever.
I know the soundcard & subwoofer are OK because I re-boot into windows and it booms away fine.

---

### Post by rillip on 2007-04-18
I'd suggest going to the media forum here and trying out the ultimate sound guide, it's very thorough and may at least get you started in the right direction

---

