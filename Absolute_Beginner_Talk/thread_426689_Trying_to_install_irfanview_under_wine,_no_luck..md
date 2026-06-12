---
title: "Trying to install irfanview under wine, no luck."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-04-28
I tried sudo and it still did nothing, not even ask for password. I did get it working though, found a thread that told to copy the irfanview folder from a Windows box into the wine folder and run it. It works. I am also going to try some of the other programs recommended as I would prefer to go native Linux if possible. Thanks to all who replied.



I am trying to install irfanview under wine. When I go to the terminal I type:

wine ~/iview_400.exe

It goes away for a couple of seconds, then comes back. No action, no errors, no nothing. Any idea what is happening? 

Also, is there an Ubuntu application that is similar to irfanview? All I want is a simple photo editor. I could use Gimp, but for much of what I do, it is overkill and more complex than I want to mess with for just simple resizing, compression, and possibly redeye reduction.

---

### Post by SendDerek on 2007-04-28
How about Krita?

---

### Post by orb9220 on 2007-04-28
> wine ~/iview_400.exe


Try: sudo wine ~/iview_400.exe

Picasa works.
gwenview
gthumbs
digaKam
F-spot phot manger

all but Picasa are in the repo's

---

### Post by TheReaperD on 2007-05-01
Ok, I found a solution.  Aparently, you need the file mfc42.dll to be in your wine Windows directory.

I've uploaded a bzip2 compressed copy of the file.  The original came from Windows XP Pro.  Feel free to check it for viruses.

To get Irfanview to install:

1) Download mfc42.dll.bz2 to your Desktop
2) Use your favorite utility to unbzip2 the file
3) Open a terminal window
4) cp ~/Desktop/mfc42.dll ~/.wine/drive_c/windows/system32

Then try running the windows installer for Irfanview.  If it does not work, complete the following steps:

1) Open Wine Configuration
  - On KDE (Kubuntu): K -> Settings -> Wine Configuration
2) Click on the "Libraries" tab
3) In the box labeled "New override for library" type "mfc42.dll" (without quotes)
4) Click "Add"
5) Click "Apply"
6) Click "Ok"

Now, try the Irfanview installer again, it should now work.  Note, I did not need to use the sudo command for any of this.

---

### Post by sataylor56 on 2007-11-09
I ran into some of these same problems and could never get the IrfanView installer file to run under wine. I finally copied over the entire IrfanView folder from my windows machine and tried running IrfanView from that. It worked first time without any hitches. Now I don't know if any of the other tweaks with xorg.conf and such were really necessary or not. I don't think I'll try to go back to the way it was. Everything seems to be working fine now.

---

### Post by michael37 on 2007-12-11
OK here is definitive guide to installing Irfanview on Gutsy.

Works perfectly for me with 64-bit Gutsy and 64-bit Wine which is by far the most challenging combination.

I make an assumption that you are running Gutsy -- if not, upgrade.

[LIST=1]
[*]Update Wine to the latest version.  A brief synopsis from [wine homepage]("http://winehq.org/site/download-deb") is posted below:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```
[*]```
sudo apt-get update
```
Make sure apt-get doesn't produce any errors, for example, Synaptic Package Manager must be closed.
[*]```
sudo apt-get install wine
```
The new version should be **0.9.51** as of December 28, 2007.
[*]```
sudo apt-get install cabextract
```
[*]Download mfc42.cab from Microsoft into /tmp using this link: [http://activex.microsoft.com/controls/vc/mfc42.cab](http://activex.microsoft.com/controls/vc/mfc42.cab)
[*]```
cd /tmp
```
[*]```
cabextract mfc42.cab
```
[*]```
wine /tmp/mfc42.exe
```
[*]Download Irfanview into /tmp
[*]```
wine /tmp/IrfanView.exe
```
[/LIST]

---

### Post by njaneardude on 2007-12-21
[QUOTE=TheReaperD;2575492]Ok, I found a solution.  Apparently, you need the file mfc42.dll to be in your wine Windows directory.

Thanks!

~n

---

### Post by njaneardude on 2007-12-21
OOH OOH, I plugged my mike in the front panel and did a Skype test call and actually very fainly heard my voice!

Now to tweak.

~n

---

### Post by michael37 on 2007-12-29
Added a wiki page on the subject.  

[https://help.ubuntu.com/community/Wine/IrfanView](https://help.ubuntu.com/community/Wine/IrfanView)

---

### Post by michlt on 2008-07-09
I had already placed the mfc42.dll in the /window32 folder but still had no luck.

What made everything run perfectly smoothly was ReaperD's advice to add the mfc42.dll to the wine configuration library tab. 

That is all that it took! 

Thanks ReaperD -- I've been using and loving Iview on Windows for years and now I have it on Linux.
Plus, I learned that new dll files have to be copied to /window32 THEN added in the config to the library. Good tip for future installs.

---

