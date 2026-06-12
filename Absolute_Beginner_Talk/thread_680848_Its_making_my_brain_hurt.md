---
title: "Its making my brain hurt"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by lemon_duck on 2008-01-28
I'm not finding it at all easy to understand Ubuntu or Firefox. 'Fortunately' I decided to overwrite XP on one computer and to leave it untouched on another so at present have GG on the desktop and a .pdf format Ubuntu guide running on Acrobat on a tablet. The problem is compounded by the information in the 'guide' being based on FF and an earlier version of Firefox so performing the exercises in the guide is very hit and miss.

What I would like to do for the moment is download .avi files and play them on the Movie Player, but trying to play existing avi files does not work since it appears the required codecs are not installed. Attempting to use the links to codec providers does not work either. Gstreamer simply does not download or if it does download I do not understand how to enable Movie Player to 'see' the codecs.

I have also attempted to install Acrobat Reader but while the download succeeds and a copy has been saved the format .rpm is apparently unknown to Ubuntu or the package being used and I cannot 'unzip' it for installation. In this instance Adobe has instructed me to use a proceedure in Firefox permitting Adobe to become a 'favoured' site.

All very confusing to a geriatric.](*,)

---

### Post by taurus on 2008-01-28
Try installing ubuntu-restricted-extras for all your multimedia stuff.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by rax_m on 2008-01-28
Hi, 

I hope I can help a little bit. 

Firefox is a web  browser "just like" Internet Explorer on Windows. However, in some versions of Linux (Ubuntu is a type of Linux)  you need to installed the restricted codecs in order to access things like AVI and MP4 etc. 

This link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) gives instructions on how to do that. Essentially you need to do the following: 

    * Go to Applications &#8594; Add/Remove...
    * Set Show: to All available applications
    * Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras and kubuntu-restricted-extras.

I hope that helps get your issues sorted out. 

On another note, in different version of Linux you get different formats of files to install. RPM's are used in some Linux versions. While DEB files are used in others. Ubuntu uses DEB files. 

Hope that helps 

Rax

---

### Post by mikeyphi on 2008-01-28
You will get the required codecs by reading here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

.RPM is a different Linux flavor!!! Can be converted to Ubuntu using a package called Alien....but perhaps better if you use Firefox to install the Adobe plugin...will only work if you click on a web-based pdf.....Ubuntu has its own default PDF reader.

Hope this has provide a crumb of comfort!!

---

### Post by rax_m on 2008-01-28
I got these instructions for installing Adobe Reader from the guide. Wherever you see the Code section, you need to enter those commands into a terminal window. You can just copy and paste them. Find the terminal application at Applications->Accessories->Terminal

 Adobe Reader Gutsy amd64/i386

    * Acrobat Reader 8 with firefox plugins step by step installation guide 

First
```

echo "deb http://packages.medibuntu.org/ gutsy free non-free" | sudo tee -a /etc/apt/sources.list

```
Second

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
Third we add plug ins and Reader
```

sudo aptitude install acroread acroread-plugins acroread-escript

```
You can also install the plug-in for Firefox
```

sudo aptitude install mozilla-acroread

```
If you get "Unable to find the HTML rendering library (libgtkembedmoz)..."

Specifiy the folder location in Edit -> Prefences -> Internet

    * Browser Executable: /usr/bin/firefox
    * libgtkembedmoz Folder: /usr/lib/firefox/ 

Enjoy Adobe Reader

---

### Post by Mitchlb on 2008-01-28
Ok. You want to play .avi files... Get vlc media player. The codecs are included, and you can play anything. Firefox is more customizable then internet explorer, but most people just use it like internet explorer. Open seperate tabs (ctrl + t) and type in your url. Presto.

---

### Post by lemon_duck on 2008-01-28
Thanks for the help. I'll MRD (Mark, read & digest) ASAP.

M$ asked me for an additional £95 two days ago because I had installed a vertual CD-ROM and they reckoned my XP had been reinstalled on a new computer. Stuff 'em.

---

### Post by lemon_duck on 2008-01-28
Many thanks.

I'll get there. I'm a bit worrried about Linux and the Tablet tho'.

---

### Post by lemon_duck on 2008-01-28
More good help. Many thanks

---

### Post by lemon_duck on 2008-01-28
I didn't know AVI was available for Linux. Thanks for the tip. It's my default player in XP.

---

### Post by JoshuaRL on 2008-01-28
> **lemon_duck said:**
> Many thanks.

I'll get there. I'm a bit worrried about Linux and the Tablet tho'.

So you have a tablet pc?  I haven't worked with them, but I've heard they have support.  I'll see what I can dig up.

---

### Post by bumanie on 2008-01-28
> I have also attempted to install Acrobat Reader but while the download succeeds and a copy has been saved the format .rpm is apparently unknown to Ubuntu or the package being used and I cannot 'unzip' it for installation. In this instance Adobe has instructed me to use a proceedure in Firefox permitting Adobe to become a 'favoured' site.
I would just use the native ubuntu pdf reader, you don't have to agree for it to be 'favoured' or anything. As for .rpm files, they are for other distributions - there is a program called alien that can convert .rpm into .deb files, but I would not advise trying this unless at this stage. It is only necessary if there is no equivalent .deb programs.

---

### Post by JoshuaRL on 2008-01-28
Mmmm, I'm not sure anymore.  Supposedly there are some working on Ubuntu, but it may be a hit-and-miss thing to get a tablet pc working.  Your best bet if you have one may be to search Google with "site:ubuntuforums.org [make and model of tablet]".  That may pull up something for you.

---

### Post by lemon_duck on 2008-01-28
Thanks to everyone. I've tried must of the suggestions even opening a .pdf on mozilla to find out what repositories and universal repositories are. As introduced by the VLC site (without any explanation).
It does appear that if Gates could produce an OS that had the efficiency of Ubuntu with the user friendliness of XP (or Vista) then you could kiss Linux goodbye.

Anyway enough brain pain for today I'm off to do some old fashioned and easy reading from a real book.

---

