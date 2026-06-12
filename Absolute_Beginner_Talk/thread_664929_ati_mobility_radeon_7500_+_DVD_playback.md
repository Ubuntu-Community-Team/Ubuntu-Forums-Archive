---
title: "ati mobility radeon 7500 + DVD playback"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by mikeylikesit on 2008-01-11
Hi all i have a thinkpad r40 that has a broken LCD so im using as frontend as a media center using the external video output, i am having a hard time getting dvd's to play correctly if at all. i have done alot of research and it turns out that the thinkpad has a ati mobility radeon 7500 which i guess is almost impossible to get to work with DVDs i have installed all the plugins (libdvdcss2) and many others, but none of them seem to work, if any one has had any luck getting this to work could you please help me out, this is driving me nuts! :mad:

---

### Post by nikoPSK on 2008-01-11
For dvd playback do this... here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. (if in gutsy replace the section of the top code 'fiesty" to "gutsy".

Hope that helps,
Niko

---

### Post by mikeylikesit on 2008-01-11
Well that helped, but now when it "opens" the dvd all i get is a solid blue screen, ive done some searching and apparently its the video card, any more ideas, 

Thanks for the help 
-Mike

---

### Post by nikoPSK on 2008-01-11
well, I don't think they video card is the issue (or is it :confused:) So you get a blue freeze when you pop in a dvd? 

Best,
nikoPSK

---

### Post by nikoPSK on 2008-01-11
did you replace the code to gutsy rather than fiesty? maybe using the wring repo? 

nikoPSK

---

### Post by mikeylikesit on 2008-01-11
it does not freeze the screen just goes to a solid color

---

### Post by nikoPSK on 2008-01-11
hrm, have you tried mulitple dvd's?

nikoPSK

---

### Post by mikeylikesit on 2008-01-11
ive done some more searching and apparently the ATI card does not like linux dvd playback, so im going to put it aside for now thanks for all the help

---

### Post by nikoPSK on 2008-01-11
No problem. Hope you issues get resolved. It's okay I had to wait 3 months to find out an answer to one thing and had to figure a few things out myself.

---

### Post by johnno31 on 2008-03-24
this fix worked for me with ATI Radeon x1270 graphics card on dell 1521. running amd64 edition of gutsy. cheers

---

