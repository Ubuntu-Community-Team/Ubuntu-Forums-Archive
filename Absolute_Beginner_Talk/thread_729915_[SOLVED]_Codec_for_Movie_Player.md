---
title: "[SOLVED] Codec for Movie Player"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-03-20
I've just bought I Am Legend and i put it into my cd drive and i was not able to view it on Movie player cause i get an error like i need a codec. I will upload a pic of my error.

---

### Post by Tews on 2008-03-20
search for libdvdcss in syaptic package manager and install it...I think :confused:

---

### Post by sayakb on 2008-03-20
Search for all gstreamer plugins, plus at a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gecko113 on 2008-03-20
Still nothing i trying looking up libdvdcss in the manger and nothing i installed all of them and still won't run :( i installed gxine to and still nothing once i run it in that it comes back as missing Nav package

---

### Post by gecko113 on 2008-03-20
here is the exact error i get

---

### Post by wolfen69 on 2008-03-20
open terminal, copy and paste the following.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your movie.

---

### Post by CJ56 on 2008-03-20
For what it's worth -

Make sure you have the medibuntu repository enabled in Synaptic, then search for libdvdcss2 & install it

Then try downloading the VLC media player (also in the repositories) which I find plays just about anything without undue fuss....

---

### Post by photonian on 2008-03-20
:-({|= :
I had the same problem.

](*,) 
And after trying many things that did not fix it.

KS
I decided NOT to fix it but to use another program:
And even though I am using [SIZE="4"]Gnome[/SIZE] and Love it, I found that for playing "PROTECTED" DVD MOVIES automaticly and Correctly AS IF you put it in a DVD player **[SIZE="4"]Kaffeine[/SIZE]** (a **KDE** Media Player) does the job just about perfectly.

Instructions:
Goto: Menu > Applications > Accessories > Terminal
In the terminal window do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP):

**F**irst Step:

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" | sudo tee -a /etc/apt/sources.list

**S**econd Step:

 wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

**T**hird Step:

 gpg --import automatix2.key

**F**ourth Step:

gpg --export --armor E23C5FC3 | sudo apt-key add -

**F**ifth Step:

 sudo apt-get update

**S**ixth Step:

 sudo apt-get install automatix2

**S**eventh Step:

 sudo apt-get install kaffeine

**E**ighth Step:

exit

-------------------------------------------------------------
**T**hen goto:
Menu: System > Preferences > Removable Drives and Media

**I**n the window that pops up:
Click on the Multimedia Tab

**O**n the Command line under Video DVD Discs:
Enter: 
kaffeine -f DVD
if you want the DVD to play automaticly in full screen mode 
**OR** Enter:
kaffeine DVD
If you want the DVD to Start out Playing the Movie  in Windowed Mode

**NOTE**: Kaffeine seems to have a problem going back to Windowed Mode sometimes, when it is started in full screen mode as of this date; 3,20,08.
To work around this just hit 'Alt and F4' at the same time, this will close it out.

---

### Post by photonian on 2008-03-20
Sorry I didn't till you what to do with Automatix:
Goto:
Menu Applications > System Tools > Automatix
Depending on legalities of your government, the ability to actually play any Copyrighted DVD Movies is available by installing the restricted Codecs from within  Automatix

Sorry, although some things might be free they are not free as in Freedom.
:(

---

### Post by gecko113 on 2008-03-20
Well i did both of thoes methods and yet i can't watch the movie still, i get the same Nav packet error on Kaffeine as well here it is the error

---

### Post by justin whitaker on 2008-03-20
Try VLC instead. It's like a swiss army knife: dependable, can run anything, gets you out of those McGuyver moments.

---

### Post by billgoldberg on 2008-03-20
> **photonian said:**
> :-({|= :
I had the same problem.

](*,) 
And after trying many things that did not fix it.

KS
I decided NOT to fix it but to use another program:
And even though I am using [SIZE="4"]Gnome[/SIZE] and Love it, I found that for playing "PROTECTED" DVD MOVIES automaticly and Correctly AS IF you put it in a DVD player **[SIZE="4"]Kaffeine[/SIZE]** (a **KDE** Media Player) does the job just about perfectly.

Instructions:
Goto: Menu > Applications > Accessories > Terminal
In the terminal window do the following (ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP):

**F**irst Step:

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" | sudo tee -a /etc/apt/sources.list

**S**econd Step:

 wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

**T**hird Step:

 gpg --import automatix2.key

**F**ourth Step:

gpg --export --armor E23C5FC3 | sudo apt-key add -

**F**ifth Step:

 sudo apt-get update

**S**ixth Step:

 sudo apt-get install automatix2

**S**eventh Step:

 sudo apt-get install kaffeine

**E**ighth Step:

exit

-------------------------------------------------------------
**T**hen goto:
Menu: System > Preferences > Removable Drives and Media

**I**n the window that pops up:
Click on the Multimedia Tab

**O**n the Command line under Video DVD Discs:
Enter: 
kaffeine -f DVD
if you want the DVD to play automaticly in full screen mode 
**OR** Enter:
kaffeine DVD
If you want the DVD to Start out Playing the Movie  in Windowed Mode

**NOTE**: Kaffeine seems to have a problem going back to Windowed Mode sometimes, when it is started in full screen mode as of this date; 3,20,08.
To work around this just hit 'Alt and F4' at the same time, this will close it out.

I would advise **strongly** against the method this user suggest to view dvd's.

Just enable the medibuntu repo, download vlc afterwards, open up vlc and choose to "open disc". If you have vlc installed from the normal repo's, remove it first, then reinstall it after adding the medibuntu repo.

---

### Post by gecko113 on 2008-03-20
Well seems that Mplayer Movie player plays it but it doesnt allow me to show the menu

---

### Post by billgoldberg on 2008-03-20
Have you tried vlc?

Or try the dvd program called "ogle", it's in the repo's.

---

### Post by gecko113 on 2008-03-20
Well i have VLC installed but it won't allow me to open the DVD :S like i dunno its weird i have it on my other computer on XP but Microsoft sucks so

---

### Post by justin whitaker on 2008-03-20
> **gecko113 said:**
> Well i have VLC installed but it won't allow me to open the DVD :S like i dunno its weird i have it on my other computer on XP but Microsoft sucks so

Sounds like you are having issues not with the codec, but with the menus. When you go into VLC, there are a bunch of options. One is to load the Movie at the Menu, the other is to go directly into play. Try that.

---

### Post by gecko113 on 2008-03-20
Well with VLC i click open disc and it goes and then it loads it and then quits and it kicks out and loads nothing

---

### Post by philinux on 2008-03-20
Follow this you can't go wrong.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

