---
title: "Quick question about the iso"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-05-22
Hello, I read both of the tutorials (see my crimesaucer thread 'xubuntu...' posted about 35 minutes ago) and thanks for the info. Now I'm still confused which folder is the .iso file.

When my WinRAR unpacked and extracted the original xubuntu 6.0.6 beta flight 7 i386.iso torrent file, it had 8 different folders and 2 files and a text file making 11 different options. And with-in the 8 folders, are more folders and files. I have un-packed and extracted all files with my WinRAR to the exact same file that they are in.

I just haven't seen the iso image file. There is a folder labeled isolinux, is that the one? Most of the folder has .tr files in it, and I see a boot security log in there, do I burn this folder to CD? or do I burn the whole download onto CD?

And does it matter if I unpacked the CD and left the packed part (with the WinRAR books icon) still in the folder next to the unpacked version?

Thanks for the help,
-crimesaucer

---

### Post by user1397 on 2006-05-22
[quote=crimesaucer]Hello, I read both of the tutorials (see my crimesaucer thread 'xubuntu...' posted about 35 minutes ago) and thanks for the info. Now I'm still confused which folder is the .iso file.

When my WinRAR unpacked and extracted the original xubuntu 6.0.6 beta flight 7 i386.iso torrent file, it had 8 different folders and 2 files and a text file making 11 different options. And with-in the 8 folders, are more folders and files. I have un-packed and extracted all files with my WinRAR to the exact same file that they are in.

I just haven't seen the iso image file. There is a folder labeled isolinux, is that the one? Most of the folder has .tr files in it, and I see a boot security log in there, do I burn this folder to CD? or do I burn the whole download onto CD?

And does it matter if I unpacked the CD and left the packed part (with the WinRAR books icon) still in the folder next to the unpacked version?

Thanks for the help,
-crimesaucer[/quote]
i had a lot of trouble with winrar and ubuntu.  what i ended up doing is uninstalled winrar, and then downloaded the iso image, (it's supposed to be one file that ends in .iso)
i then burned it using sonic by selecting "burn image to disc"

---

### Post by 5-HT on 2006-05-22
You need to burn the iso itself as a disc image, not extract the iso and burn something contained within it.

When you downloaded the file, did you get something like xubuntu*.iso?
That is the file that you need to burn as a disc image.

Hope that helps.

---

### Post by crimesaucer on 2006-05-22
Yeh, I was thinking that my problem might have had to do with the WinRAR. I'll do what you suggested, should I use the torrent or the download manager on my Firefox?

edit to second question: No I downloaded the xubuntu file twice today, once on the standard i86 option that said it was a live CD with the option of install off of the xubuntu/ubuntu page, and once off of osdir.com's list of torrent downloads that was the torrent:
 xubuntu 6.0.6 beta2-live-i386.iso.torrent

Should I download the torrent that I saw on the xubuntu/ubuntu page that was: xubuntu 6.0.6 beta-install-i386.iso.torrent  ??

or is that an older version on this page: [http://cdimage.ubuntu.com/xubuntu/releases/dapper/beta/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/beta/)

the other page of osdir.com's was:[http://linuxtracker.org/torrents-details.php?id=1915](http://linuxtracker.org/torrents-details.php?id=1915)
link from this list: [http://linuxtracker.org/index.php?page=2](http://linuxtracker.org/index.php?page=2)

---

### Post by ProjectGod on 2006-05-22
i think... after you download any ISO file. you need software like nero to burn the "image" onto a CD / DVD... don't worry about not finding the iso file. the iso is the original file that holds within it the necessary components.

i find it easier on a windows machine to use DAEMON Tools (free software) to mount a virtual drive of any ISO image file... then use any cd burning tool to copy the mounted drive / image files onto a blank disk!

hope this helps.

---

### Post by crimesaucer on 2006-05-22
I have Daemon tools, how would I mount the image. I know how to mount a .bin file, is it just as easy?

---

### Post by ProjectGod on 2006-05-22
i'm assuming youre on a windows machine.. open up daemon tools. there should be a little icon in the ash tray (near the system cock / time) now right click on it and select some like "mount" or "mount virtual drive"... select an available drive letter e.g. F: Y: Z:... locate the *.ISO file and double click on it.

depending on the size of the iso and the hardware of your machine... it may take a little while. after this... open up my computer... then there should be another virtual CD Drive... double click on it and it should open up your "extracted" ISO image.

now select everything in this virtual CD drive and copy... pop a blank CD / DVD into your CD / DVD burner. open up another windows explorer. open up the ACTUAL CD DRIVE... (not the virtual mount)... and paste. 


i'm assuming its a windows XP so after you do a paste... you can select "write these files to CD". as you would do with normal files / folders when burning cds / dvds. 

when the files have been permanently burned onto the cd / dvd... you can use it to install ubuntu linux gentoo etc etc...(assuming the original ISO was a linux distribution)

hope this helps.

---

### Post by crimesaucer on 2006-05-22
Thanks for the details, now...One of my problems is that I can't find a folder or a document that has a .iso attached to it??? I have unpacked every thing with WinRAR and someone earlier said I would have to dis-able the WinRAR and download again because it does something to the actual .iso file that shouldn't be done... is that true?

---

### Post by confused57 on 2006-05-22
I have winRAR on my computer and all iso files I download appear as a winRAR file when they're actually iso files(this is due to file association).  Don't extract the iso(winRAR) file, as suggested earlier...just burn the entire file "as an image" using your CD burning software.  Just look for the option "image" for burning.

---

### Post by crimesaucer on 2006-05-22
Cool, I'm going to re-download the iso file now and do what you said. Before I do another download, should I download the Text-mode install if I'm going to be installing a dual boot and have my Windows Xp in ntfs file format and plan on having a Fat32 swap file. I've read the install tutorial here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

and here: [http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

psychocats tutorial didn't explain as much about the dual boot of a ntfs Windows Xp OS so I thought I would go with the Text-mode download that the other tutorial went into great detail on. What do you think?

---

### Post by confused57 on 2006-05-22
Sounds like you're on your way...good luck.

First of all, are you downloading the Breezy 5.10 or the Dapper Beta?

A bit of advice, if I may, download both the LiveCD and Install CD for the version of Ubuntu that you plan on using.   It's pretty important to run the Live CD first, it doesn't install to your HD, you can "play" with it; but, most importantly, you'll find out if Ubuntu is compatible with your system hardware and learn how do system "tweaks" to get it running properly, as well as, learn how to navigate around the OS.

As far as I know there is just the install CD, not a different text-based install CD.  Breezy is a text-based install, follow the Hermanzone link for that;  Dapper uses espresso(think that's what it's called) installer, which is a Graphical installer as described in the psychocats link...Dapper has an option to select text installation.  You can opt to install from the Dapper Live CD, but not the Breezy Live CD.

Installation isn't really hard, just look over the links several times until you're relatively familiar with the install steps...don't rush into it and by all means, try the Live CD first...you'll be glad you did.

Just a thought...when you extract files from the iso(RAR), doesn't it just make copies of the files contained in the RAR file and the iso(RAR) file is still intact and could be copied to CD...you could right click the file and check properties for size in Mb...would save re-downloading...on second thought, probably best to download again, just to be sure.

---

### Post by crimesaucer on 2006-05-23
All the Linux ninjas seem to think the WinRAR messes something up...I'm so new to this I'm just going with logical popular consent and trial and error.

I'm actually going for the xubuntu 6.0.6 beta, and it has passed the check of hp pavilion dv4000's on the compatible lap top chart. I ran the 5.10 live breezy for a day but I feel like jumping into it with both feet so it will become my new project/hobby and by the time I get comfortable with Linux from toying around on it as a hobby, I can start to use it as my main OS.

---

