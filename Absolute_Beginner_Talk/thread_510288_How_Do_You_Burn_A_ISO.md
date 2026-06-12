---
title: "How Do You Burn A ISO???"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-26
How do you burn a ISO?

I download Puppy Linux...
The file is in WinRar
I click it but it says The Archive is either in unknown format or damaged...
It doesn't work!!!! :mad::mad::mad:

---

### Post by FleetAdmiral74 on 2007-07-26
...where did you download the file from?

And in Ubuntu, just right click the iso and click burn to disk.

---

### Post by 4Real on 2007-07-26
I got it from the main site.

[http://www.puppylinux.org/user/news.php?readmore=43](http://www.puppylinux.org/user/news.php?readmore=43)

---

### Post by thefoolisme on 2007-07-26
Must have come from a torrent, because Puppy has ISO files on their site.  To get to the ISO, you'd need an unzipping program that recognizes the RAR format.  RAR is like a .zip or other compressed file.  Un-rar it, and you probably will have the ISO.

---

### Post by thefoolisme on 2007-07-26
Must have come from a torrent, because Puppy has ISO files on their site.  To get to the ISO, you'd need an unzipping program that recognizes the RAR format.  RAR is like a .zip or other compressed file.  Un-rar it, and you probably will have the ISO.  Or just go back to puppy and download the ISO instead of getting the torrent.

---

### Post by 4Real on 2007-07-26
I have WinRar Archiver... And the format is ISO.  it says WinRar is recommended to open the file

---

### Post by FleetAdmiral74 on 2007-07-26
7zip will do WinRAR, plus its FOSS.

---

### Post by deadlikeoscar on 2007-07-26
You don't need to unrar it once it is at the .iso stage. You need a program that will burn image files. Imgburn is easy to use and free.

---

### Post by Majorix on 2007-07-26
Wait why not the default archiver? You can download unrar from the repos and then use it to unrar the file you got:
```
sudo apt-get install unrar
```

Then right click and select "extract here" or similar.

---

### Post by 4Real on 2007-07-26
Ok i'll download that program but i used other ISO burning programs such as

MagicISO , BurnCDCC , Deepburner , but they all say please enter a empty CD. But my cd is empty...

Im using CD-R Memorex 723 mb

---

### Post by LMP900 on 2007-07-26
I think he means that the file named "filename.iso", however, it is incorrectly suggesting that WinRAR is the application for it.

You need Imgburn (as suggested above) or DeepBurner Free to burn the ISO as an image on a disc.

[Edit] Replied too late...

---

### Post by Majorix on 2007-07-26
Are you on Windows? Why don't you say that in the first place? :confused:

You can use WinRAR combined with PowerISO to unrar the file and then burn it. PowerISO is not free though. I don't know of any good free alts.

---

### Post by 4Real on 2007-07-26
its working ImgBurn ts burning it and it recognizes the empty cd and the file formats. Yay ... I'll post later to tell how it went...

---

### Post by 4Real on 2007-07-26
> **Majorix said:**
> Are you on Windows? Why don't you say that in the first place? :confused:

You can use WinRAR combined with PowerISO to unrar the file and then burn it. PowerISO is not free though. I don't know of any good free alts.


I have two computers XP and 98.... I making my 98 Puppy Linux.

---

### Post by AJB2K3 on 2007-07-26
The pre installed archive tool extracts .rar normally you just need to read the man pages to find the right code.
i think it was eather
tar xvvf file.rar
or 
tar xcvf file. rar
But i can't remeber without looking at the man page.

---

### Post by misfitpierce on 2007-07-26
Can use GnomeBaker on a linux pc or PowerISO for windows.

---

### Post by 4Real on 2007-07-26
Thanks for All the help all heres how it worked....

I archived it then extracted it...
I downloaded MagicISO so it was able to read the file
I downloaded ImgBurn and burned on disc

Thanks All Again get ready for more questions next time :-P

---

### Post by MrFSL on 2007-07-26
> **4Real said:**
> How do you burn a ISO?

Get a match or lighter or blow-torch and hold the flame up the the little CD/DVD picture on your computer monitor...

OR

You can read the MILLION different answers on this forum. 

OR

Since your talking WinRar and therefore using Windows.... you can post your question on a Windows forum.)

OR

You can ask the people over at puppylinux... since that seems to be the software you are interested in using.

---

### Post by Majorix on 2007-07-26
> **MrFSL said:**
> Get a match or lighter or blow-torch and hold the flame up the the little CD/DVD picture on your computer monitor...

OR

You can read the MILLION different answers on this forum. 

OR

Since your talking WinRar and therefore using Windows.... you can post your question on a Windows forum.)

OR

You can ask the people over at puppylinux... since that seems to be the software you are interested in using.

Haha I couldn't agree more :D

---

### Post by aktiwers on 2007-07-26
On WIndows ISO files sometimes shows as Rar files.. or they get the WinRar Icon when you have WInrar installed, because Winrar knows how to open ISO files.

Just burn it as Image:
[http://www.psychocats.net/ubuntu/iso#burning](http://www.psychocats.net/ubuntu/iso#burning)

---

### Post by FleetAdmiral74 on 2007-07-26
723 mb eh? Are these standard? Look for a 700mb even one, should be 80min.

---

