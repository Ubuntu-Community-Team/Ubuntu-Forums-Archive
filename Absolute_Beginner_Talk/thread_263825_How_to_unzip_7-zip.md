---
title: "How to unzip 7-zip"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-23
what application can I use to unzip 7-zip files?

---

### Post by Orestes on 2006-09-23
p7zip - install it by typing:

```
sudo apt-get install p7zip
```

You've got to activate universe repositories (probably easiest to do it in synaptic) first though.

then to unzip stuff you use the command:

```
7z x my7Zzipfile
```

It's funny, I had to download and use this myself for the first time today.

Anyway, HTH

---

### Post by WalmartSniperLX on 2006-09-23
ok thanks :D

---

### Post by spockrock on 2006-09-23
lol never mind, beaten to it, 

7z -h 

will give you the full options.

---

### Post by WalmartSniperLX on 2006-09-23
wait when I try to extract it it says there is no such archive

EDIT nvm i know whats wrong

---

### Post by WalmartSniperLX on 2006-09-23
Thanks again :D

---

### Post by spockrock on 2006-09-23
hahhaha beaten to it again.... >_<

---

### Post by Orestes on 2006-09-23
Sure it's a 7zip file? 
Sure you're in the right directory? (:D happens to me all the time)

Glad you've got it sussed!

---

### Post by WalmartSniperLX on 2006-09-23
> **Orestes said:**
> Sure it's a 7zip file? 
Sure you're in the right directory? (:D happens to me all the time)

Glad you've got it sussed!

:D wasnt in the right dir.

---

### Post by dimeotane on 2007-02-10
When I try to extract files from a 7z archive using file roller I get this error:

v: cannot stat `/tmp/fr-LTKqeR/Photo/Customer Satisfaction Survey.doc': No such file or directory


I have an archive I've made using 7zip v 4.42 on windows2000, which has a few dozen folders of files I need to extract  :confused: 

I managed to get my files extracted by installing 7zip under wine.  I'd like to use 7z in file roller natively in ubuntu.  7z is a great compression format which is increasingly popular.  

Anyone else have this problem?  I need an archiving method which is cross compatible with secure password encryption.  I'm guessing that .rar is my best option currently?


Another archive which is password protected gives the error:

7-Zip (A) 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14
p7zip Version 4.42 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive:  /home/dell/Desktop/filecollection.7z
Enter password (will not be echoed) :
Error: /home/dell/Desktop/filecollection.7z is not supported archive

---

### Post by Kabamaru on 2007-03-24
Just wanted to update the command for extracting with 7zip, as I followed the instructions listed above and received error messages (saying that command 7z wasn't found).  Here's what worked for me:
```
p7zip -d nameofmycompressedfile.7z
```
All in all, this thread was very helpful - thanks all!

---

### Post by sn4cks on 2007-08-12
> **Kabamaru said:**
> Just wanted to update the command for extracting with 7zip, as I followed the instructions listed above and received error messages (saying that command 7z wasn't found).  Here's what worked for me:
```
p7zip -d nameofmycompressedfile.7z
```
All in all, this thread was very helpful - thanks all!

The reason the 7z command didn't work is because instead of apt-getting p7zip you have to apt-get p7zip-full. After that the 7z command should work just fine for you. I guess it's kind of pointless at this point, but if you wanted to try it the information is there!

Here's the apt-get code to make copy&paste easier.

```
sudo apt-get install p7zip-full
```

---

### Post by davidsrsb on 2007-08-12
The Windows version of 7zip works very well under Wine

---

### Post by motin on 2008-02-04
> **Orestes said:**
> 
then to unzip stuff you use the command:

```
7z x my7Zzipfile
```

It's funny, I had to download and use this myself for the first time today.

Anyway, HTH

At least in Gutsy - filerolling can handle this format as long as p7zip is installed - no need for use of the terminal.

---

### Post by Vadi on 2008-02-04
"sudo apt-get install p7zip-full", then right-click on the file and extract here.

---

### Post by anoxan on 2008-07-19
> **davidsrsb said:**
> The Windows version of 7zip works very well under Wine

I'm resurrecting this thred to say that this is by far the easiest route to unzip 7z files! no gui for nix = fail. wine rocks! :D

---

### Post by Sockerdrickan on 2008-07-19
use file-roller

---

### Post by ad_267 on 2008-07-19
> **anoxan said:**
> I'm resurrecting this thred to say that this is by far the easiest route to unzip 7z files! no gui for nix = fail. wine rocks! :D

No. If you install p7zip you can use file roller as you would for any archive like zip or tar.gz. You don't need wine people!!!!

---

### Post by Vadi on 2008-07-19
Yeah...

---

