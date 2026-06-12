---
title: "Trash on disks"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Sordelka on 2008-02-20
Um you know that ubuntu has a kind of .trash folder on media drives (usb keys, etc). How to access it? I tried viewing invisible files....doesnt work

---

### Post by oedha on 2008-02-20
go to places - the media/drive
ctrl+h  to see hidden files

---

### Post by koleoptero on 2008-02-20
Yeap it does create it when deleting files, and won't at least empty it when emptying the trash. In one occasion it did ask me if I want to empty the trash when I unmounted a drive, but only once.

To see this folder, click on the icon in nautilus that enables the address bar instead of the buttons, so that you can type the address, and then go to the subfolder named .Trash-username

Then delete it's contents. Or to delete the entire folder, open a terminal, go to the root dir of the drive (e.g. cd /media/disk1/) and do: rm -fr ./Trash-username

You can verify the name of the folder in the terminal too, by going there and typing: ls -a
which will show you all the folders, hidden and not.

Hope this helps.

---

### Post by Sordelka on 2008-02-21
I tried the simple ctrl+h and it did not show up. Now a question is to be ask: in what cases is this file created?

---

