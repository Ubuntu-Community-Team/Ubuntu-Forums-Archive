---
title: "Burning Packages on CD?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-12
Since my computer has internet access only via dial-up, downloading packages and their dependencies can take a very long time.

My question is this: I have access to a Windows machine with a broadband connection. Is it possible to download packages and burn them to CD, and then install them from the CD on my Ubuntu box?

---

### Post by Denis on 2006-07-12
Yes you can. 

If you want some specific packages, you can use synaptic. 
Open synaptic and mark the packages you want, just like you would do it otherwise. Now instead of clicking apply (to download and install the packages), you chose "File" > "Generate package download script". This generates a script that contains the URLs to the packages you want. 

Download the packages listed in the script with the computer that has internet access. You can burn these on a CD e.g.

On your Ubuntu computer insert the CD and double click on the package you want to install. The package installer will install this package if you want so. Because of dependencies you may have to install these packages in the right order. (When package A depends on package B, you need to install package B first) 

Installing all the downloaded packages will have the same result as doing the marked operation in synapic. Open Synaptic and you will see that the packages are installed.

---

### Post by Hexx on 2006-07-12
> **Denis said:**
> Yes you can. 

If you want some specific packages, you can use synaptic. 
Open synaptic and mark the packages you want, just like you would do it otherwise. Now instead of clicking apply (to download and install the packages), you chose "File" > "Generate package download script". This generates a script that contains the URLs to the packages you want. 

Download the packages listed in the script with the computer that has internet access. You can burn these on a CD e.g.

On your Ubuntu computer insert the CD and double click on the package you want to install. The package installer will install this package if you want so. Because of dependencies you may have to install these packages in the right order. (When package A depends on package B, you need to install package B first) 

Installing all the downloaded packages will have the same result as doing the marked operation in synapic. Open Synaptic and you will see that the packages are installed.

Thanks for telling me about how to generate a download script! I didn't even notice that option before. Beats hunting down URLs for each .deb!

About installing: Instead of installing each package one-by-one, couldn't I make the CD I've burned act as a local repository in Synaptic? That way it would install a package as well as all its dependencies all at once, right?

Thanks for your help!

---

### Post by Denis on 2006-07-12
I'm not sure you can make the CD a repository. 

Maybe performing "dpkg -i /media/cdrom/*" is a more easy way to install all these packages.

---

### Post by Hexx on 2006-07-12
> **Denis said:**
> I'm not sure you can make the CD a repository. 

Maybe performing "dpkg -i /media/cdrom/*" is a more easy way to install all these packages.

Alright, I'll try that then. Thanks again.

---

### Post by aysiu on 2006-07-12
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by Bino on 2006-07-12
I opened the package manager to mark some codecs and such for download for totem so I can view media files and dvd´s. However, I can´t select new files for download (1031 files listed, 1031 files installed). Any idea why and how I can fix that?

Note, I also don´t have an internet connection on the pc with ubuntu.

These should be the packages I should need (not found in the Synaptic package manager):
[SIZE="1"]multimedia:
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
sudo apt-get install w32codecs
gst-register-0.8

dvd:
sudo apt-get install libdvdcss2[/SIZE]

---

