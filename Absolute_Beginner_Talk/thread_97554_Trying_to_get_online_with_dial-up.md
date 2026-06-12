---
title: "Trying to get online with dial-up"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2005-12-01
I have recently loaded Ubuntu 5.10 onto my computer as a dual boot system with Win98.

So far, I have been unable to get online with my dial-up modem, or even 'find' the modem.  (an internal Smartlink with SL1900 chipset)

I now have  scanModem.gz  on both a floppy and a CD but have been unable to copy  it into my ‘home folder’.

When I boot up, the light on my floppy drive flashes on and I have been able to format a floppy  disk.  However, when I insert a disk into the floppy drive and try to open it, all I get is the message, ‘ERROR: given UDI is not a mountable volume’.

If I try to copy the file from the CD, it is not visible and a ‘file search’ indicates that I don’t have any such file.

I would appreciate it if someone would give me a suggestion as to how to get going here.

Thanks.

---

### Post by towsonu2003 on 2005-12-01
[QUOTE=L Campbell]If I try to copy the file from the CD, it is not visible and a &#8216;file search&#8217; indicates that I don&#8217;t have any such file.
[/QUOTE]

possibly you forgot to mount the cd? ```
sudo mount /media/cdrom
``` then copy the file ```
cp /media/cdrom/scanModem.gz ~/Desktop/
``` and now it should be on your desktop (unless I mistyped something).

---

### Post by L Campbell on 2005-12-01
>>>
possibly you forgot to mount the cd?

Code: sudo mount /dev/cdrom

then copy the file

Code: cp /media/cdrom/scanModem.gz ~/Desktop/

and now it should be on your desktop (unless I mistyped something).
<<<<

Thank you very much for your help.

I hope you're not receiving this message twice but it vanished last time I tried to send it.

I wasn't completely successful, as it turned out that the file ' scanModem.gz ' was not on the CD after all.

However, I have a game plan which I would like to run by you:-

A) If I use sudo mount /dev/floppy

then

cp /media/floppy/scanModem.gz ~/Desktop/

would this be likely to work?

B) If I were to open the file ' scanModem ', type the code from it into a file in my 'home folder' and name it ' scanModem.gz ', would this be likely to work?

Also, should I copy this to the 'forums', so that others may benefit from you help?

Kind regards.

---

### Post by towsonu2003 on 2005-12-01
(repeating my pm briefly for others)
for cd mounting-> if mounting the cd was successful, I believe you should be able to see a shortcut to the cd in your desktop in gnome... then you can just double click it (the cd icon on the desktop) and copy-paste as in windows...
for A-> (don't have floppy, searched forum on how to mount floppy) try ```
sudo mount /media/floppy
``` and then copying should work... 
for B-> did not understand what you wanted, but it is an archive and you'll need to 'unzip' it... so you better copy the file altoghether (I am very bad at linux-type unzipping :P )...

regarding the scanModem.gz (googled)-> 
```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

then go to the (newly created) directory called Modem and read, starting with read1st.txt and then ModemData.txt. ModemData.txt says what you have to do to make your
modem work but it is full of details some of which, case by case, are very
important ... and may seem frightening to a beginner... if you need help, you mail the modemdata.txt **following the e-mail instructions** (which are either in read1st.txt or in modemdata.txt) after making sure that you read everything you needed to read but still could not understand what to do... 
(my source while writing this was: [http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278](http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278))

PS. goodluck

---

### Post by L Campbell on 2005-12-01
[QUOTE=towsonu2003](repeating my pm briefly for others)
for cd mounting-> if mounting the cd was successful, I believe you should be able to see a shortcut to the cd in your desktop in gnome... then you can just double click it (the cd icon on the desktop) and copy-paste as in windows...
for A-> (don't have floppy, searched forum on how to mount floppy) try ```
sudo mount /media/floppy
``` and then copying should work... 
for B-> did not understand what you wanted, but it is an archive and you'll need to 'unzip' it... so you better copy the file altoghether (I am very bad at linux-type unzipping :P )...

regarding the scanModem.gz (googled)-> 
```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

then go to the (newly created) directory called Modem and read, starting with read1st.txt and then ModemData.txt. ModemData.txt says what you have to do to make your
modem work but it is full of details some of which, case by case, are very
important ... and may seem frightening to a beginner... if you need help, you mail the modemdata.txt **following the e-mail instructions** (which are either in read1st.txt or in modemdata.txt) after making sure that you read everything you needed to read but still could not understand what to do... 
(my source while writing this was: [http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278](http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278))

PS. goodluck[/QUOTE]

THANKS.

This time I put the CD in the 'regular' CDRom drive, as opposed to the one with the 'burner' and things functioned very well, except for the fact that the ' scanModem.gz ' file was definitely not on it.

The CD appeared on my desktop and I accessed it from there.

I did try   ' 1s /media/cdrom ' and got:-

bash: 1s: command not found

So, onward to the floppy (BTW, scratch my 'B' idea)

Here I typed  sudo mount /mdia/floppy and I'm asked for my password BUT, when I type, NO password appears.

I have tried re-booting but to no avail.

YIKES !!!  I'll be SO happy when I get this all resolved.

I'll have so much free time I won't know what to do.   :-)

Kind regards.

---

### Post by L Campbell on 2005-12-01
[QUOTE=towsonu2003][QUOTE=L Campbell]Quote:
Originally Posted by towsonu2003
(repeating my pm briefly for others)
for cd mounting-> if mounting the cd was successful, I believe you should be able to see a shortcut to the cd in your desktop in gnome... then you can just double click it (the cd icon on the desktop) and copy-paste as in windows...
for A-> (don't have floppy, searched forum on how to mount floppy) try
Code:

sudo mount /media/floppy

and then copying should work...
for B-> did not understand what you wanted, but it is an archive and you'll need to 'unzip' it... so you better copy the file altoghether (I am very bad at linux-type unzipping :P )...

regarding the scanModem.gz (googled)->
Code:

gunzip scanModem.gz chmod +x scanModem ./scanModem


then go to the (newly created) directory called Modem and read, starting with read1st.txt and then ModemData.txt. ModemData.txt says what you have to do to make your
modem work but it is full of details some of which, case by case, are very
important ... and may seem frightening to a beginner... if you need help, you mail the modemdata.txt following the e-mail instructions (which are either in read1st.txt or in modemdata.txt) after making sure that you read everything you needed to read but still could not understand what to do...
(my source while writing this was: [http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278](http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/16278))


PS. goodluck

THANKS.

This time I put the CD in the 'regular' CDRom drive, as opposed to the one with the 'burner' and things functioned very well, except for the fact that the ' scanModem.gz ' file was definitely not on it.

The CD appeared on my desktop and I accessed it from there.

I did try ' 1s /media/cdrom ' and got:-

bash: 1s: command not found

So, onward to the floppy (BTW, scratch my 'B' idea)

Here I typed sudo mount /mdia/floppy and I'm asked for my password BUT, when I type, NO password appears.

I have tried re-booting but to no avail.

YIKES !!! I'll be SO happy when I get this all resolved.

I'll have so much free time I won't know what to do.

Kind regards.[/QUOTE]

It's okay for it not to show the password. just type in and press enter after sudoing. also, not 1s but ls (as in "**l**is**t** the contents". 

don't forget to unmount the floppy (sudo umount /media/floppy) before taking it out after you're done with it... 

so:
1. get scanModem.gz to floppy somehow
2. mount floppy: sudo mount /media/floppy
3. copy content to Desktop: cp /media/floppy/scanModem.gz ~/Desktop
4. sudo umount /media/floppy
5. double click the scanModem.gz on the desktop and start reading :)

Also, please post to your threat  as well when you succeed / fail...[/QUOTE]

Thanks again.

I did make some progress this evening.

After getting a new CD and burning the ' scanModem.gz ' file onto it, I was able to transfer the file to my Home Folder.

Then I ran the ' gunzip ' thing and I think it worked but I'm not sure how to verify that.

Anyway, I went to networking and tried to set up my online connection but, still, my modem didn't show up, despite me trying ' sudo wvdialconf ' and also
' sudo apt-get install gnome-ppp '.

Anyway, I feel like  I took a step forward again.

Kind regards.

---

### Post by towsonu2003 on 2005-12-02
Hi,

gunzip will only 'unzip' the archive file (scanModem.**gz**). After that, you will have to make it an executable (an .exe file in windows terms) by doing chmod u+x scanModem while you are in the directory where scanModem file is. than, again from the directory where scanmodem is, you have to execute (i.e. run, in windows terms again) the file by calling its name: ./scanModem

This will execute it and result in a number of new directories being created by it. If scanModem was on your desktop (i.e. ~/Desktop), than you should be able to see those directories. Navigate to the folder Modem (I think) and read 'read1st.txt' and 'modemdata.txt'. You can use 'nautilus' (type nautilus from terminal) to navigate. It is the default file manager of Ubuntu. Just double click on files you want to read if you are using nautilus and they will be opened by 'gedit'... 

scanmodem cannot and will not configure your modem. It will only detect what modem you have and will spit out information about how to configure it. Once you are done configuring the modem (which takes some considerable time), you will be able to dial up... 

PS. if you cannot find a particular file, do the following: 
```
sudo updatedb
``` -> wait until it finishes the process, which may take a while (it will update a local search database) -> then do ```
locate filenamehere
``` you don't need to do sudo updatedb everytime you search unless the file you are looking for was created after you (or the system) last run updatedb (and I believe the system runs it everyday or so automatically).

---

### Post by L Campbell on 2005-12-03
[QUOTE=towsonu2003]Hi,

gunzip will only 'unzip' the archive file (scanModem.**gz**). After that, you will have to make it an executable (an .exe file in windows terms) by doing chmod u+x scanModem while you are in the directory where scanModem file is. than, again from the directory where scanmodem is, you have to execute (i.e. run, in windows terms again) the file by calling its name: ./scanModem

This will execute it and result in a number of new directories being created by it. If scanModem was on your desktop (i.e. ~/Desktop), than you should be able to see those directories. Navigate to the folder Modem (I think) and read 'read1st.txt' and 'modemdata.txt'. You can use 'nautilus' (type nautilus from terminal) to navigate. It is the default file manager of Ubuntu. Just double click on files you want to read if you are using nautilus and they will be opened by 'gedit'... 

scanmodem cannot and will not configure your modem. It will only detect what modem you have and will spit out information about how to configure it. Once you are done configuring the modem (which takes some considerable time), you will be able to dial up... 

PS. if you cannot find a particular file, do the following: 
```
sudo updatedb
``` -> wait until it finishes the process, which may take a while (it will update a local search database) -> then do ```
locate filenamehere
``` you don't need to do sudo updatedb everytime you search unless the file you are looking for was created after you (or the system) last run updatedb (and I believe the system runs it everyday or so automatically).[/QUOTE]


Hi, just to let you know I haven't given up.   :-)

I did make a 'dramatic' discovery.  The reason I had been unable to access my floppy drive was that I did not 'space' between 'sudo mount' and '/media/floppy'.  (DUH!!!)

Anyway, this is a great learning experience and I am really enjoying it.

Thanks for all your help and patience.

---

