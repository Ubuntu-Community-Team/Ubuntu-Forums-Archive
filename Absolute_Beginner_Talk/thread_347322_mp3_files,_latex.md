---
title: "mp3 files, latex"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-01-27
Dear friends, I can't play mp3 files in Ubuntu. Nor can I find a full LaTeX environment. Kindly advise me.
Thanks for any help.
Regards,
Saurav

---

### Post by Iarwain ben-adar on 2007-01-27
Here you go:
[http://ubuntuforums.org/search.php?searchid=13482210](http://ubuntuforums.org/search.php?searchid=13482210)

[http://ubuntuforums.org/search.php?searchid=13482224](http://ubuntuforums.org/search.php?searchid=13482224)

Try searching first :wink:


Iarwain

---

### Post by irish_flu on 2007-01-27
Howdy friend.

I don't know jack about LaTex, so I can't help you there, but I do have a link which you should read to learn all about how you can play mp3s and such in Ubuntu.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sauravbhaumik on 2007-01-27
Thanks friends, I've found some codec for mp3's and by them I am successfully playing mp3 files.
But for LaTeX, I've installed TeXmaker, but by it, I can't view dvi files. But in order to do it, I've to install some more than 120mb; and I've only 1,2gb left in my root. What should I do?
I use windows and there I successfully work with LaTeX. Is there anything special in linux regarding  LaTeX? If not, I'll not go for LaTeX in linux.
Regards,
Saurav

---

### Post by Iarwain ben-adar on 2007-01-27
Just sent you the pm :D


Good you have mp3 support,
but alas: i do not know anything about LaTeX.

Btw, to free some space for your root, clean out your /var/cache/apt/archives :wink:


Iarwain

---

### Post by IYY on 2007-01-27
> Dear friends, I can't play mp3 files in Ubuntu.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

>  Nor can I find a full LaTeX environment. Kindly advise me.

```
sudo apt-get install tetex-base tetex-extra tetex-nonfree
```

I don't know what you call a ``full' LaTeX environment. With these packages, you can type your LaTeX code in any text editor (editors like gedit should even have syntax highlighting for LaTeX), and then compile it with a command like

```
latex mydoc.tex
```

or
```

pdflatex mydoc.tex
```

if you want a PDF instead of a DVI.

If you want a GUI editor, you could use something like lyx:
```

sudo apt-get install lyx
```

---

### Post by montes.c on 2007-01-31
I'm trying to install Ubuntu on a pc that has no internet connection so I'm going to need to download all the relevant packages and do an dpkg -i *.deb for mp3 playback

How can I access the universe and multiverse repositories to find all the necessary gstreamer .deb packages to download?

If it is relevant, it will be a amd64 desktop installation.

---

### Post by Brunellus on 2007-01-31
> **montes.c said:**
> I'm trying to install Ubuntu on a pc that has no internet connection so I'm going to need to download all the relevant packages and do an dpkg -i *.deb for mp3 playback

How can I access the universe and multiverse repositories to find all the necessary gstreamer .deb packages to download?

If it is relevant, it will be a amd64 desktop installation.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by montes.c on 2007-01-31
> **Brunellus said:**
> [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

No offense but that site is stupid to navigate, who were the designers?

How are new users supposed to distinguish what version belongs to these retarded 'names'?

They NEED to list the ubuntu number versions along with the name.

Example: This entire page doesn't mention Dapper as this release version's name

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

So I head over the package link you gave me and how the hell am I supposed to find out which one is 6.10 ?

I swear people dont know how to create informative websites anymore.

---

### Post by Iarwain ben-adar on 2007-02-01
Well, it does..

> Ubuntu 6.06 LTS is codenamed Dapper Drake

And for the names, you might be right, but is it that hard to find out yourself?


Iarwain

---

### Post by montes.c on 2007-02-01
> **Iarwain ben-adar said:**
> Well, it does..



And for the names, you might be right, but is it that hard to find out yourself?


Iarwain

I did find out for myself, but it's annoying that such trivial information isn't correctly labeled on the site itself.

Going soley by names is kinda dumb in my opinion, especially when other pages on the site are labeling with version numbers and others are labeling with 'names'.  Which is the problem here.

How is an end-user going to figure this out? Do we have to search for every stupid little thing? Especially when a webmaster can simply get his lazy fat fingers and type a couple extra characters.

---

