---
title: "how to make zip deflate64"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2008-02-19
Message:
i can not find out how to use your p7zip-full for ubuntu linux. i like 7zip for windows and it has a gui but the linux does not have a gui. so how do i make zip files using the deflate64? on my windows i only change the compression to the deflate64 and it makes the smallest compressed files out of the other opions. how do i then open the file in ubuntu linux?

---

### Post by Origin415 on 2008-02-19
Once you install the p7zip package, Gnome's File Roller archiver will automatically gain support for it, so try using that as your gui. The command is file-roller, and it should be the default application for any archive, including .7z

---

### Post by lance bermudez on 2008-02-20
i wnat to know how to make zip files using the deflate64 option what you told me to look at only makes zip flies but i do not know if they are using deflate or deflate64. and i want to use the deflate 64

---

### Post by lance bermudez on 2008-02-24
the command is 
7z a -t=zip -mm=deflate64 archive.zip file

for the command line but if you could use peazip you can have a gui for 7zip just search google for peazip. it comes in .deb format.

---

