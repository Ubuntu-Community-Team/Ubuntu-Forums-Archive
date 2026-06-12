---
title: "Reading files in Windows."
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2006-12-29
First of all: I'm very happy that Ubuntu is a free operating system. It works very well, I think it is more user friendly than the other Linux distributions I have tried Fedora Core (3) and SuSE (8.0). I hope development continues, and that Ubuntu will become even more user friendly :) I am very new to Linux, so if I have to do anything, could you please descrbe even the most idiotic minimal step to me?

I'm having some problems getting the OpenAL libaries installed on my system because of dependancy problems, so I thought I'd make a screenshot of my screen so I can see exactly what file I need, but when I put the screenshot on a memorystick, it wouldn't open in windows  (I tried Irfanview), but it didn't work. I saved it as a .png. The same thing happened when I tried to copy some text to a textfile with the texteditor, and then open it in Windows.

Can I solve this problem?

Thank You.

---

### Post by Ramses de Norre on 2006-12-29
Did you unmount the usb stick before you took it out? (this is the same as save removal in windows, you can do it by right clicking the icon in nautilus and choosing unmount or eject).

---

### Post by OmnificienT on 2006-12-29
No I didn't actually. Should I always use:
umount /media/usbdisk
or click around in the gui to open them in Windows? I just pulled it out all the time because it didn't seem to make a diffirence.

I just did manage to open a textfile made in Ubuntu in Windows, but it did not save the enters (I don't really know the correct term for this)  which was very annoying.

---

### Post by meng on 2006-12-29
Right click the icon in Ubuntu, choose unmount.

---

### Post by Ramses de Norre on 2006-12-29
That's the classical newline difference between DOS and Unix unicode standards... You can change the format to dos with nano but I'm not sure how to do it. Opening the file with word instead of notepad on windows will also show the right newlines.

---

