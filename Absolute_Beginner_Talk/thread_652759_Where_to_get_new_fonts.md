---
title: "Where to get new fonts??"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2007-12-29
Well i am starting to use The Gimp a lot so i need more fonts. I have googled for ".TTF fonts" and every site that comes up is full of ads ans stuff so i thought maybe the great people here would tell me some real good sites where i can get fonts. also are different font types ( i mean like .tff and so on) installed the same way?

thanks :)

---

### Post by eternicode on 2007-12-29
Lots of good stuff at [searchfreefonts.com]("http://www.searchfreefonts.com/")

---

### Post by Hallvor on 2007-12-29
> **rockinlinux said:**
> Well i am starting to use The Gimp a lot so i need more fonts. I have googled for ".TTF fonts" and every site that comes up is full of ads ans stuff so i thought maybe the great people here would tell me some real good sites where i can get fonts. also are different font types ( i mean like .tff and so on) installed the same way?

thanks :)

```
sudo apt-get install msttcorefonts
```

---

### Post by rjmdomingo2003 on 2007-12-29
dafont.com

---

### Post by Abu_Dayya on 2007-12-29
> **eternicode said:**
> Lots of good stuff at [searchfreefonts.com]("http://www.searchfreefonts.com/")

How can I install and use the font after downloading it

---

### Post by eternicode on 2007-12-29
Under Ubuntu, I'm not sure.

In Kubuntu, we have a Font Installer on the KControl app.  Check out whatever app you use to modify system preferences (wallpapers, font size/color/etc, stuff like that)

EDIT:
If you don't have anything in your "control panel" as it were, you may have to install them manually:

[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

---

### Post by Abu_Dayya on 2007-12-29
So there is no specific folder to put the downloaded fonts in?

---

### Post by MalfunctioningMartian on 2007-12-29
/usr/share/fonts/truetype/

Create a new folder there e.g. Custom and copy the font into the folder.

You need to start the file browser as root to copy stuff there. In a terminal > sudo nautilus

---

### Post by hugmenot on 2007-12-29
A few hand-picked free fonts listed here: [http://praegnanz.de/essays/](http://praegnanz.de/essays/)

---

### Post by billgoldberg on 2007-12-29
Download the fonts from dafonts.com (the best free one).

To use them in gimp, go to the home folder, press "ctrl+h". Go to the ".gimp" folder and then paste the fonts in the fonts folder. (be sure to unzip/untar them before pasting there).

Reset the gimp and you can use the fonts.

To use them in the whole ubuntu. Go to the home folder, then press a the little icon so you can type. Enter "fonts:///" and paste them there.
(for this it could be that you need to be root, if so do this: go to a terminal window, type "sudo nautilus")

---

### Post by JillSwift on 2007-12-29
> **MalfunctioningMartian said:**
> /usr/share/fonts/truetype/

Create a new folder there e.g. Custom and copy the font into the folder.

You need to start the file browser as root to copy stuff there. In a terminalCareful, it's best to use gksudo for GUI apps. It properly loads the GUI settings for root. On occasion, using sudo for gui apps can change the ownership of your setting files, and that's a PITA to correct.

so:```
gksudo nautilus
```
_____________________________EDIT__
Oh, and to be on topic: Try this page for really fun display fonts:
[http://moorstation.org/typoasis/designers/shyfonts/shy01.htm](http://moorstation.org/typoasis/designers/shyfonts/shy01.htm)

---

### Post by rockinlinux on 2007-12-31
good job JillSwift :)

and thanks guys, now i have to many fonts and i dont know what do to with them all. :)

I hope this thread was also helpful for someone else.

happy new year!!

---

### Post by kathryn on 2008-01-16
This site's great for fun comic book fonts:

[http://www.blambot.com/fonts.shtml](http://www.blambot.com/fonts.shtml)

Quite a few are free to download and use for non-commercial purposes.
Enjoy! :)

---

