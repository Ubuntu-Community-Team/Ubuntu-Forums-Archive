---
title: "PDF hyperlinks, need solution please ;-)"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Shrike01 on 2006-04-10
Hi there all

I have created computer literacy curriculum for learners at South African schools using PDF hyperlinks. The problem I am having is that I cannot find an easy solution for the educators at the school to install to use the hyperlinks.

The default document reader can open and read the PDF documents fine but the hyperlinks do not work.

I have tried acroread but the installation process is so far beyond the majority of educators that there is no way I can expect them to install it and use my documents.

Is there an easy installation option for ubuntu? Some kind of script maybe that installs a PDF reading application easily so that the learners can use the PDF hyperlinks?

thanks!

---

### Post by nanotube on 2006-04-10
ubuntu comes by default with a pdf reader, called "evince". so when you click on a pdf link in firefox, and it asks you what to do with it, just tell it to "open with" and search for /usr/bin/evince to open the pdf file with.

---

### Post by trent dillman on 2006-04-10
Well, how are you installing acroread?
Maybe you could write a script?

---

### Post by Shrike01 on 2006-04-10
Thanks for the info but the documents are opened in evince and the hyperlinks open other documents (if they work).

So when a learner clicks on a link saying "click here to see how to bold text in Writer" it then opens another document that has this info in it.

When you hover your cursor over the link it changes to the clickable link hand cursor but when you click nothing happens.

As for writing the script, I have almost no knowledge of Ubuntu at all and installed it via instructions given on the web. I am convinced however that if the same instructions were followed by an educators that they would get hopelessly lost.

---

### Post by trent dillman on 2006-04-10
What site did you get the instructions from?

---

### Post by Shrike01 on 2006-04-10
Ok, I was mistaken, it seems the application was never really installed. Here is what I did:

1.I double clicked on the acroread-5.09 install file
2.I then chose "Run in Terminal"
3.I went through the package notes
4.I typed in accept.
5.The installation script asked me where the package must be installed to.
6.I pressed enter
7.It told me it could not create the folder
7.I remembered something about a command called sudo and did the whole installation thing again and typed in the word "sudo" in the terminal before the default folder structure.
8. Yeay! The package installed.
9. When opening PDF documents now it still didnt open in acroread, still in evince.
10.Went onto the web looking for answers and found a few sites that gave me these 
instructions:

How to install PDF Reader (Adobe Reader) with Plug-in for Mozilla Firefox?
sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins
Start Adobe Reader

11. typed in sudo apt-get install acroread
12. Got this message


user@ubuntu:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package acroread
And now I am stuck. I run apt-get update but of course the computer is not connected to the Internet.

Now look at it from my perspective: I am technically sound and was able to go through all those steps. Imagine a teacher who is going to teach basic computer literacy to a class of learners having to go through all that. It is just not going to happen.

My personal experience tells me that most computer literacy teachers are just part timer enthusiasts themselves stuck with teaching it because of an interest. As such they have VERY little experience on the technical side of Linux and Ubuntu and can usually just use open office etc.

What am I to do? I cannot assume that every teacher out there is going to know what to do when faced with the situation above.

All I am asking for is for someone to tell me:


1. Is it possible to create a "double click on me and all will be installed" package that will enable this acrobat reader to be installed, application added etc?
2. When installed will this acrobat reader allow learners to click on PDF hyperlinks that will open up other PDF documents? (note that nowhere are they going to open firefox, the hyperlinks are all in acrobat)

---

### Post by trent dillman on 2006-04-10
Here, test this out. Then see if your teachers can handle

```
sudo bash ./adobe.install
```

```
#!/bin/bash
cd /opt
wget -nc http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz
tar zxf AdobeReader_enu-7.0.5-1.i386.tar.gz
AdobeReader/INSTALL --install_path=/usr/local/Adobe/Acrobat7.0
cp /usr/local/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so /usr/lib/mozilla/plugins
cd /usr/lib/mozilla-firefox/plugins
ln -sf ../../mozilla/plugins/nppdf.so ./
ln -sf /usr/local/Adobe/Acrobat7.0/bin/acroread /usr/bin
cp /usr/share/mime-info/gnome-vfs.keys ./
sed -e 's/evince/acroread/g' /usr/share/mime-info/gnome-vfs.keys > new.keys
mv new.keys /usr/share/mime-info/gnome-vfs.keys
```

Or even better, do up a .desktop file for them with 'gksu /path/to/adobe.install'...
And, they have to log out/in for the mime type to refresh (I think)...

---

