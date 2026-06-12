---
title: "Zip Folders On Ubuntu?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-29
Is There A Way To Reduce a files size (like a zip folder)  on my Windows Computer So It Can Fit On A Floppy To Be Used In Ubuntu???:confused:

---

### Post by siralphred on 2007-08-29
yeh there is unrar    sudo apt-get install unrar

---

### Post by n.aggel on 2007-08-29
yes windows, can create zip files...or you can download one program to do this like 7zip....

if you want to do the zipping from ubuntu... you can do it by right clicking to the folder you want to zip and select create archive

---

### Post by redfox1160 on 2007-08-29
and how do i unzip these in ubuntu? the same way i do in windows?(my computer with ubuntu isnt connected to the internet)

---

### Post by viciouslime on 2007-08-29
You can right click the new zip file and click extract here or you can double click it to get an extraction program called file roller.

There is a better format (.tar.gz) a gzipped tarball. Nautilus will probably default to this though so you won't have to worry about it. It will work just like .zip but with better compression.

---

### Post by MobileDev on 2007-08-29
I am assuming you want to compress it on windows, put it on the floppy, and then uncompress the file in Ubuntu. The best tool to do the compression is 7-Zip. It has the best compression ratio of any archiver I've tried, as long as you use the 7z format, which produces smaller files then .tar.gz, but it depends on what you're compressing. There is a problem with this though. Ubuntu doesn't come with anything to open 7z archives, so will have to use something with a lower compression ratio. If you absolutely must have the highest possible compression ratio, and be able to use it on Ubuntu, you could try getting p7zip from the Ubuntu repos. It works just like 7-Zip on windows, but it uses a command-line interface instead of a graphical one. If anyone knows of a package to implement a GUI for p7zip, please post it here. Another downside to p7zip is that it can't extract RAR archives, like it's Windows cousin. This is because RAR is a proprietary format used exclusively on Windows. Why they allow decompression in one port and not the other, I have no idea, nor can I think of a good one. Anyway, sharing archives back and forth with Windows and any Linux distro requires the use of 7-Zip on the Windows side, mainly because it's free, fast, and produces compatible archives that can be used on Linux without modification.

---

