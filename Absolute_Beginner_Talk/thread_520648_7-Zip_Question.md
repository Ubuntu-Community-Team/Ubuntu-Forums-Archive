---
title: "7-Zip Question"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-08-08
On Windows I recently started using 7-Zip because it is open-source and I can also use the same program on Ubuntu. 

My question is would it be beneficial to compress using the 7-zip format over the tar format or vice versa, or maybe a different format is better? I've had to unpack/uncompress (I'm not sure about the terminology) packages on Ubuntu and they were all in the  tar.gz format (or something along those lines) 

Any opinion on this would be appreciated :-)

---

### Post by stchman on 2007-08-08
> **SilverDragon said:**
> On Windows I recently started using 7-Zip because it is open-source and I can also use the same program on Ubuntu. 

My question is would it be beneficial to compress using the 7-zip format over the tar format or vice versa, or maybe a different format is better? I've had to unpack/uncompress (I'm not sure about the terminology) packages on Ubuntu and they were all in the  tar.gz format (or something along those lines) 

Any opinion on this would be appreciated :-)

On Windows 7zip is a GUI based program.  On Ubuntu it is a CLI app.  I recommend you stay with either .zip or .tar.gz format.  If you need to do .rar stuff do a:

sudo apt-get install unrar

This will allow Archive Manager to unpack .rar files.

---

### Post by FuturePilot on 2007-08-08
> **stchman said:**
> On Windows 7zip is a GUI based program.  On Ubuntu it is a CLI app.  
You can use 7zip from the Archive Manager. As long as you have p7zip and p7zip-full installed, the .7z file extension becomes an option to create an archive. 
I believe 7zip has a higher compression ratio than tar or tar.gz

---

### Post by stchman on 2007-08-08
> **FuturePilot said:**
> You can use 7zip from the Archive Manager. As long as you have p7zip and p7zip-full installed, the .7z file extension becomes an option to create an archive. 
I believe 7zip has a higher compression ratio than tar or tar.gz

So to get .7z I need to do the following:

```

sudo apt-get install p7zip p7zip-full

```

---

### Post by Daedalus on 2007-08-08
.7z is a great file format for compressing stuff. I love it, and it is open source.

It compresses data at better ratios than .zip or even .rar formats.

---

### Post by SilverDragon on 2007-08-08
> **stchman said:**
> On Windows 7zip is a GUI based program.  On Ubuntu it is a CLI app.

What is the difference between a GUI based program and CLI. i know GUI is graphical User Interface but CLI I have no idea.


Thanks for the fast responses.

Besides better compression ratios is there any other benefit to using the .7z format, because it seems as if tar.gz would be a better alternative since it is more widely used. Winzip I was trying not to use because I am trying to get away from Windows :-)

---

### Post by BlueNoteExpress on 2007-08-08
CLI = Command Line Interface

---

### Post by psusi on 2007-08-08
You are doing a bit of comparing apples to oranges.  winzip and 7zip are compressed archiving utilities.  A 7z file is an archive which contains compressed data.  tar is ONLY an archive utility, and gzip is ONLY a compression utility.  You use tar to make an archive containing multiple files, and then you can use gzip, bzip2, or whatever to compress the archive.  

Now, back to comparing 7z with tar.gz.  7z with max lzma compression options in solid mode will get a better compression ratio than tar.gz, but it requires a lot more memory to compress or decompress, and a LOT more time to compress.  Also the 7z archive format does not store unix file permissions and ownership, which makes it unsuitable for backing up a system.  To work around this, you can use tar to archive, and 7z to compress the tar.

---

### Post by David Mulligan on 2007-09-17
> **FuturePilot said:**
> and p7zip-full

Thank you.  I had p7zip installed but did not realize that I needed the p7zip-full package installed too in order for Archive Manager (aka file-roller) to be able to work with 7z files.

---

### Post by saravanan.marimuthu on 2008-03-24
Hi,

I want p7zip to be installed in my UNIX AIX Version 5.3, I have copied following files to my AIX.

p7zip_4.57_src_all.tar
p7zip_4.57_x86_linux_bin.tar.bz2

HOw to proceed in installing p7zip now. Anticipating your reply....

Thanks in advance,
Saravanan

---

