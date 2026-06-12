---
title: "Unable To Activate MP3 Support In KUBUNTU..!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by 7mm on 2008-01-18
Hi There, I've JUst Installed KUBUNTU 7.10. As I Used Previous Versions of UBUNTU & KUBUNTU, I've Tried To Enable MP3 & Other Codec Support By Just Playing Them In 'Amarok', & Allowing To It To Enable It Self When Asked. It Shows Installation Complete MSG In Just 10-30 Seconds & Ask To Restart The 'Amarok'. Even After Restarting 'Amarok', Still Ask To Enable The Codecs...:confused:. Done That 3-5 Time & Situation Just Doesn't Change. Please Help :( !

---

### Post by Christmas on 2008-01-18
I'm not sure if enabling MP3 support has the same effect as the command below, but try it anyway:
```
sudo apt-get install kubuntu-restricted-extras
```
Then restart Amarok.

[Wiki Page for Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by 7mm on 2008-01-18
It Returned MSG As "Couldn't find package kubuntu-restricted-extras"..., Have I Done / Typed Wrong..?

---

### Post by Christmas on 2008-01-18
It looks like you don't have all the repositories activated.

Follow [this](https://help.ubuntu.com/community/InstallingSoftware). Basically, you have to edit the file /etc/apt/sources.list and make sure you have the 'universe' and 'multiverse' repositories activated:
```
sudo nano /etc/apt/sources.list
```
Then make sure what you have in it is something like:
```
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```
Note the 'universe' and 'multiverse' repositories. Also, replace 'us' with your country's TLD (top level domain, ie de for Germany, gb for Great Britain etc).
After that, update the list of packages:
```
sudo apt-get update
```
Now install it:
```
sudo apt-get install kubuntu-restricted-extras
```
Hope I didn't forget anything, I'm using Debian with KDE for a while.

---

### Post by Sami_Sdata on 2008-01-18
Check in Adept and make sure you have the restricted source repositories enabled.

---

### Post by 7mm on 2008-01-18
Thank You "Christmas" & "Sami_Sdata" For Your Help. Though, I've Did It With Adept Manager. Tried The Simple Way First, As "Sami_Sdata" Suggested. It Has Trigger The Download & Running Now, Might Take More Time On Dial-Up. I'll Post Next, Whatever The Outcome It'll Be :popcorn:.

---

### Post by 7mm on 2008-01-19
That's Is Boys, I've Got My TuxBox Singing :guitar:  With MP3 & Other Codec. Thanx Again For The Help, "Christmas" & "Sami_Sdata".

---

### Post by Sami_Sdata on 2008-01-19
Glad it worked for you.  Still puzzling out some of Kubuntu's quirks myself.  Recently switched over to it after a long history of RPM based Linuxes and BSD systems.

---

