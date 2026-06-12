---
title: "How do I get permission to modify a system folder, Im trying to install a skin formsn"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by rodami on 2007-07-02
Im trying too install a skin for aMSN and I have to copy paste the folder I got to do this

To install a skin just download it, and extract the files for the .zip file (.zip, .tar.gz, or similar). Then copy the extracted skin folder to one of the following locations:
"/usr/share/amsn/skins"
"/home/YOUR_USER_NAME/.amsn/skins" 

But every time I try, it says I don't have permission, whats sup?

---

### Post by rodami on 2007-07-02
please help, Ive been trying for a while and noothing works...

---

### Post by ugashia on 2007-07-02
Just download the skin to your desktop and extract it, then go into your terminal and type 
```
 sudo nautilus
```
Then go into the usr folder, then into the share folder, and then into the amsn folder, and then skins. Then all you have to do is drag and drop from your desktop.

---

### Post by Golyadkin on 2007-07-02
I would do that with gksudo instead of sudo, but sudo will work as well  :)

---

### Post by the1andonlytjs on 2008-05-01
i still cant do it it still says i dont have permission

---

### Post by spdf on 2008-05-02
Open up a terminal and type "nautilus ~/.aMSN/skins" (without quotes).

Note: The tilde "~" is a shortcut for your home folder. When you type it, it will likely expand to the full path of your home directory.

If the directory exists, it will launch a nautilus window for you to drag the extracted skin directory into.

---

