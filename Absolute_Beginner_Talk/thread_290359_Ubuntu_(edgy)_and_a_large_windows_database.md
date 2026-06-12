---
title: "Ubuntu (edgy) and a large windows database"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by davesmith on 2006-11-01
Hello
I took the plunge, reformatted my H/D and installed the new Ubuntu 6.10 (Edgy)on a Toshiba Satellite A30 laptop, 3.05Ghz and 1G of RAM. It was running XP SP2 Home Edition with all the patches. So far I'm genuinely impressed with Ubuntu, except with one problem. I have a large database of astronomical information and files (JPEG, GIF, pdf, TIFF) about 29000 files. For all it's faults Windows NTFS handled large numbers of files well, I could sort, update, add to and search to find what I wanted with ease. However, having created a directory using the mkdir command with the terminal and loaded the database, Ubuntu slows right down and I can't sort or find anything. Is this an inherent problem with Linux or is there a solution? Any suggestions?

---

### Post by Jussi Kukkonen on 2006-11-01
Some details about the slowness would be nice... What commands are you using to sort/find?

EDIT: if you can't solve this in another way, you could try creating a reiser filesystem on one partition -- it should be very good for lots of small files. But try to describe the problem first.

---

### Post by davesmith on 2006-11-01
Well thanks for replying.
Using the Ubuntu file explorer, when I click on the directory it opens the database, but it seems to take a couple of minutes to load the file headings even though i disabled large icons. Once loaded I tried to locate files alphabetically by pressing the relevant key (eg "N" or "S" etc) and waited for it to find the start of that alphabetic section, which took ages. Many of the images are quite large (5meg) high definition Hubble pics of galaxies (eg NGC300), and the Edgy image viewer has problems loading and displaying them. It seems much slower than windows, but maybe I've not yet configured Edgy correctly yet. Does this help you diagnose the problem?

---

### Post by Jussi Kukkonen on 2006-11-01
Well, in a way... The problems are probably not general linux problems , but  Nautilus (the file browser) and image viewer related. You could try other programs (since e.g. nautilus might not be optimized for tens of thousands of files in a directory). Some examples of file managers are gentoo, thunar and mc (midnight commander), all available from your package manager.

Hmm, you do have the files on some linux filesystem, not NTFS or FAT, right?

By the way, a directory is not a database even if it has a lot of files in it ;) Using a real database would probably solve your problems too...

---

### Post by davesmith on 2006-11-01
Yes, I loaded the files into the Astronomy directory in my Home directory. I created it using the mkdir command, and loaded them from an external NTFS H/D by using copy/paste. Just being able to do that impressed me! Ubuntu "saw" the external H/D immediately.

OK, I'll try another file manager. Do you know which one of gentoo, thunar or mc works best with large numbers of files, and is there a proper database app available? 

Thanks for your advice and suggestions

---

### Post by Jussi Kukkonen on 2006-11-01
> OK, I'll try another file manager. Do you know which one of gentoo, thunar or mc works best with large numbers of files, and is there a proper database app available?
I don't know file managers very well, I don't normally use one myself (I prefer command line mostly). There are several databases available, but I have no idea if there's something with simple GUI for this kind of use...

---

### Post by davesmith on 2006-11-01
For those of you who want to manipulate a large collection of files, Konqueror is the business, much faster, smoother, sorts, searches, easy to update and has other functions too. 

sudo apt-get install konqueror

Thanks to Jussi tho, have a nice day

---

### Post by louieb on 2006-11-01
[LIST]
[*]29 thousand files is not a large number for any file manager to sort or search by name.  
[*]The speed lag is due to the file system you are using. It takes quit a while for the file manager to read the disk and collect the file names.
[*]The file system used has more to do with how long it takes to search or sort by file name.
[*]My guess is that you are using the EXT2 file system or its journaling offspring the ext3 file system. These are the most common and the slowest of the file systems used on Linux systems. 
[*]EXT2/EXT3 speed wise don't compare to NTFS with indexing turned on. All though they they are very reliable file systems.
[*]Linux has two such file systems available that I know of. There are probably more. The two that I think would give NTFS a run for the speed money are:
[*]ReiserFS: is quite stable and is very fast, depending on a balanced tree structure instead of the traditional blocks.
[*]JFS: One of the most recent additions to Linux's journaling file system is IBM's JFS - a file system developed for its high-end servers.
[*]For more information look here: [http://www.linux.org.mt/article/filesystems]("http://www.linux.org.mt/article/filesystems")

[*]BTW I know of no ease way to convert to one of the high performance file systems. But the basics are back data up, convert partition to new file system, restore data.   
[/LIST]

---

### Post by Daremo on 2006-11-01
you could try turning the "preview" options off in Nautilus. Open a file manager window and click Edit, Preferences. This will bring up the Preferences dialog box. There is a tab for Preview. Here you can set which files are previewed. You can set them to Never. This may speed up the file manager for you...

If these are set to preview files then Nautilus has to check what each file is and then generate a small preview thumbnail for each file in the folder being opened, especially with all the image files you seem to have. Hope this helps.

---

### Post by louieb on 2006-11-02
One other thing to try is to build a spreadsheet of file names and any other info you might want. I'm sure there is some way to capture the info and place it in a file. Then import the file into the spreadsheet. It is bound to be the fastest way to sort and search. haven't done this with open office. But the times I've used excel I've found it faster that windows explorer but it still not that fast. Hope open office is better.

---

