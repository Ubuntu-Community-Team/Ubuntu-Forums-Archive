---
title: "7zip, p7zip; need help using it."
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-12-02
Hi

I am trying to use a program called 7zip, witch can be found in synaptic. Here are more info: [http://packages.ubuntulinux.org/breezy/utils/p7zip](http://packages.ubuntulinux.org/breezy/utils/p7zip)

Is this a command based application - how can you see that? 

If it only can run via the terminal, witch command can I use to unpack a file? 

Thanks:-)

---

### Post by Oki on 2006-12-02
To answer my own question: 7z is supported in file-roller when the p7zip package is installed.

Then my question are;
I tried to unpack a file with file-roller, but it couldnt. So why cant p7zip unpack this file(chm format) when the windows version can:-( [http://www.7-zip.org/](http://www.7-zip.org/)
I can se that you can download 7-zip from that site for Debian Linux - will that version support chm?

---

### Post by Oki on 2006-12-02
Do you know of a program that supports CHM files like 7zip for windows do? I am not looking for a program to view.

---

### Post by Oki on 2006-12-02
Strange, p7zip under Suse 10.1 can open CHM files with no problems at all, but p7zip from Synaptic cant?

---

### Post by Kulgan on 2006-12-12
is it just me, or did you have a conversation with your self?

I'm also looking for a way to use p7zip, other than file-roller, which doesn't seem to compress the files - just group them. :-?

---

### Post by Oki on 2006-12-12
he he I guess I did – I really wanted to get help for this.

You se, a lot of people want to convert there chm files to PDF files (I like this format better, and some mp3 players can read PDF and not CHM). In Windows there are programs that can do this for you, not in Linux. I have found other threads where people ask for the same, but never get any answers (only; “we dont know”). One way is to uncompress the chem file with p7zip and make a PDF from the html files with htmldoc (a great program btw).

Could you use this file?
[http://sourceforge.net/project/downloading.php?groupname=p7zip&filename=p7zip_4.43_x86_linux_bin.tar.bz2&use_mirror=mesh](http://sourceforge.net/project/downloading.php?groupname=p7zip&filename=p7zip_4.43_x86_linux_bin.tar.bz2&use_mirror=mesh)

You can start it after installing with 7z in the terminal.

---

### Post by Kulgan on 2006-12-12
7-zip is in Synaptic (as "p7zip"), and its command line binary is called "7z". issuing 'man 7z' should give you an overview, but I will definitely take a while about decoding that...

---

### Post by Oki on 2006-12-12
I know, but as I said, p7zip from Synaptic cant open chm files, even though p7zip for SuSE can. p7zip can include 7z, 7za and 7z, and only the 7z can open chem files.

---

### Post by Kulgan on 2006-12-12
Ok, I think I have it... 

What I used is 
```
$ 7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on Dest.7z Src

```

But that is to compress a package. 

For decompression, it should be enough to double click the .7z file, and it will open in the archive manager, then there is a button along the top that says depackage or something, and guess what - that's what it does. But make sure you have "p7zip" installed in Synaptic.

---

### Post by Kulgan on 2006-12-12
oh, I see... 

I have never even heard of that format... I would say try looking through synaptic for anything that had to do with that extemsion, then install it and see if it makes a difference. 

might it be that p7zip for ubuntu requires plugins that it comes with by defualt in suse?

Good luck!

-K

---

### Post by Oki on 2006-12-12
Have you nevner heard about chm files?

---

### Post by Kulgan on 2006-12-12
nope!

what are they used for?

---

### Post by meng on 2006-12-12
If you mean the Microsoft Help files, then you should install xchm to read these. Otherwise I'm not sure what you're talking about.

---

### Post by Oki on 2006-12-12
Yes, I am talking about CHM files(Microsoft help files) which is a format that are very often used for ebooks, and manuals when you buy hardware. Meaning; if you buy or download a ebook they are often in this format, witch is a compressed format. 

In Linux you can use xchm to read them as meng said, or and perhaps better GnoCHM([http://gnochm.sourceforge.net/](http://gnochm.sourceforge.net/)) and KchmViewer([http://www.kchmviewer.net/)](http://www.kchmviewer.net/)).

But I am not talking about reading them, but convert them into PDF format since I like it better, and since some mp3 players only can read PDF and not CHM. This is easy to do in MS, and I am trying to do the same under Linux – witch turned out to be a pain...

---

### Post by meng on 2006-12-12
Thanks for the link to gnochm, I'll try it out.

---

### Post by Oki on 2006-12-12
Sorry, my link to KchmViewer didnt work, here is one that works; [http://kde-apps.org/content/show.php?content=25125](http://kde-apps.org/content/show.php?content=25125) I think you will find them both in Synaptic. They are "better" becase they have more futers, like adding favoritts/bookmarks.

I have been using Google and found a new way to convert CHM files into HTML files(meaning; uncompressing them). Take a look here; [http://madphilosopher.ca/2006/09/how-to-convert-chm-files-under-linux/](http://madphilosopher.ca/2006/09/how-to-convert-chm-files-under-linux/)

I have tried this myself now and it works like a dream:-D This programs works evene faster then the programs for Windows that do the same!

---

