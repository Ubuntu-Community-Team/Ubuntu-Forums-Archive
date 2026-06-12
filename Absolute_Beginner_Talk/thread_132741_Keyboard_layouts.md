---
title: "Keyboard layouts"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by dazhboh on 2006-02-18
I am mostly a WinXP user who wants to switch to Ubuntu, and so far I have loved what I have seen; even failing at getting something to work has forced me to learn some things that I never would have learned just sitting there with a brand spanking new OS that is a control freak (Mr. Gates..)

However, I am a webmaster for a page that is in the Ukrainian language, and as of right now still use MS Frontpage to update the site. I can type in Ukrainian in WinXP having the Ukrainian keyboard language bar thing installed and the keyboard is phonetic when I use a program from [www.brama.com](www.brama.com) called Ukrainian Keyboard. These programs have proven useful.

However, I have a laptop that is old and I would like to install Ubuntu on it so that I can just type out some updates for the site (i.e. just the text part). My problem is that I have no idea what program I should use that would allow me to switch to a Ukrainian keyboard layout that is Unicode. I would need the layout and programs and whatnot to show up the same in OpenOffice.org in Ubuntu as they would in MS Word in WinXP.

I looked at some xwitch program, but that proved to just give me errors saying that something wasn't working or wasn't copying, even though I was using sudo; though this program still doesn't suit my needs as it gives a Russian keyboard layout.

I have looked in several program lists, but the programs all seem to be for Russian layouts or I can't figure the programs out.

Any help/suggestions/anything? I hope I posted this in the right spot, I really have barely any clue as to what I'm doing other than doing copy/paste into the terminal.

---

### Post by nalmeth on 2006-02-18
found this on brama.com under unix/linux:
[koi8 and cp1251 phonetic keyboard mappings]("http://www.brama.com/compute/unix.html")

To install this .gz source package, download it somewhere (for example I will use the home folder, known in the terminal as '/home/yourusername', or simply '~/' ), and extract the package in the same folder (use nautilus to browse to this folder, and right click the folder) 
first open up a terminal (APPLICATIONS --> ACCESSORIES --> TERMINAL) 
and type the following
```
sudo apt-get install build-essential*_**s**_*
cd ~/
ls
cd name_of_extracted_folder
./configure
make
sudo make install
```
If any errors come up, or steps fail, post the output here.

If this is the wrong program, however, I can't do much for ya! You'll have to keep looking around.

_*CORRECTION:*_ THE PACKAGE IS build-essential NOT build-essentials

EDIT: I'm a little confused, becuase right next to that, says "xruskb-1.9.3-1 RPM for i386"
You likely have the i386 kernel (unless you are 64-bit user), but the other package does not specify architecture.
If you want to install the rpm (again with the package saved in home folder), again open the terminal and type:
```
sudo apt-get install alien
cd ~/
sudo alien name_of_rpm.rpm
sudo dpkg -i name_of_created_deb.deb
```

alien converts an .rpm into a .deb, which you install with dpkg

---

