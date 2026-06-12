---
title: "JSpeak - The Ultimate in Linux Text-to-Speach Software"
date: 2012-05-12
forum: Assistive Technology &amp; Accessibility
---

### Post by go_beep_yourself on 2012-05-12
[SIZE=4]**JSpeak Demo**[/SIZE] 

[http://www.youtube.com/embed/raEUJraXvwY](http://www.youtube.com/embed/raEUJraXvwY)

 
[SIZE=4]**Installation and Usage**[/SIZE]

**[SIZE=3]Ubuntu/Debian/Mint:[/SIZE]**


***Note:*** There is a bug in Mint with it's espeak and pulseaudio, not the app itself. However these bugs do not affect the program, and it still copperplates just fine and good. 

```
sudo apt-get install espeak mbrola
```  Choose your voices. There are many, but for all english ones, do 
```
sudo apt-get install mbrola-us1 mbrola-us2 mbrola-us3 mbrola-en1
```  Many mbrola voices can be installed through apt-get in Ubuntu/Mint. Some such as mbrola-mx1 are not available through apt. If you wish to install those. Follow the manual installation below for them. 

**[SIZE=3]Fedora/Suse:[/SIZE]** 
```
yum install espeak
```  Fedora and other rpm based systems do not have mbrola and mbrola packages afaik. However this is not a problem. Continue to follow the manual installation for them.  [B][SIZE=2]

Manual installation of mbrola and mbrola voices (From the espeak/mbrola docs)[/SIZE][/B]

*Linux Installation*

From eSpeak version 1.44 onwards, eSpeak calls the mbrola program directly, rather than passing phoneme data to it using a pipe.    1. To install the Linux Mbrola binary, download: [http://www.tcts.fpms.ac.be/synthesis/mbrola/bin/pclinux/mbr301h.zip](http://www.tcts.fpms.ac.be/synthesis/mbrola/bin/pclinux/mbr301h.zip) Unpack the archive, and copy and rename the file from: mbrola-linux-i386 to mbrola somewhere in your executable path (eg. /usr/bin/mbrola ).    2. Get the en1 voice from: [http://www.tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html](http://www.tcts.fpms.ac.be/synthesis/mbrola/mbrcopybin.html) Unpack the archive, and copy the *en1* data file (not the whole "en1" directory) to /usr/share/mbrola/en1.  eSpeak will look for mbrola voices firstly in espeak-data/mbrola and then in /usr/share/mbrola[B]

*Note:*[/B] Get as many voices as you like. Each will show in the voice selection combo box.  3. If you use the eSpeak voice such as "*mb-en1*" then eSpeak will use the mbrola "en1" voice, eg:  ```
espeak -v mb-en1 "Hello world"
```  [B]

*Note:*[/B] This step is just for testing that everything is setup and working correctly. 

[SIZE=3]**Obtaining and running the app.**[/SIZE]  ```
wget https://github.com/downloads/BullShark/JSpeak/JSpeak.tbz  tar -xf JSpeak.jar  cd JSpeak  java -jar JSpeak.jar
```[SIZE=3]**OR Obtain the app from git and run.**[/SIZE]  ```
git clone git://github.com/BullShark/JSpeak.git  cd JSpeak/dist  java -jar JSpeak.jar
```**[SIZE=3]Usage[/SIZE]** 

1. Toggle on the scan button (has a diamond icon). Hover your mouse over other buttons for descriptions. 

2. (Optional) Change the voice from the drop down menu of the combo box to set a better sounding mbrola voice. 

3. Start copying text from your favourite ebook, the web, email, etc. to begin having the text read to you. 

**[SIZE=3]Windows Users:[/SIZE]**


**Install Linux** 


[SIZE=4]**Help/Support**[/SIZE] 
If you enjoy this software, please consider making a small donation to the programmer, so he can continue to maintain and create new software to help everyday users. That can be done at my blog, [http://linuxinnovations.blogspot.com](http://linuxinnovations.blogspot.com) Thank you.

---

