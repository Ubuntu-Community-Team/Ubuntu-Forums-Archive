---
title: "Ubuntu and cameras"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by agger on 2005-11-13
Okay, so I just got myself a new digital camera - my first one, ever. No, not a very expensive top-of-the-line one, more like an inexpensive 80€ 2 megapixels one which i can afford to always have in my pocket :-).

So to put the pics on my computer I just plugged in the USB cable, and immediately I got a prompt asking if I want to import the pictures or not. Great.
So it asks where I want the pictures, and I conveniently created a folder called "fotos".

But it always imports them to a folder called "fotos/<<timestamp>>",
where <<timestamp>> might, e.g.,  be  2005-11-13--15.06.36.

This is good and bad: Sometimes I might want this to happen to separate the photos in batches, other times I might want the photos to go to a designated directory with no time stamp (like "Home" or "Vacation in Rome"), or I might want them to go to an undistinguished "Miscellaneous" pool. 

Does anybody know if it's possible to configure this in the import, and which other tools does Ubuntu have to control the interaction with digital cameras?

---

### Post by Kyral on 2005-11-13
While I do have the same "issue" I usually forget it by using a program like F-Spot which allows you to organize pics based on whatever criteria you want. Also if you import via F-Spot it will dump them all into a directory called ~/Photos/<year>/<month>/<day>/

---

### Post by tammyf on 2008-01-01
I can't say that I know what to tell you about the issue you are having but I am having a problem with downloading my pictures at all. I have no clue as to what I am doing. Can anyone help me?

---

### Post by steveneddy on 2008-01-01
To the OP - either let the OS DL the pics to the default folder and then move them, or remove the storage card, put the card in the PC and then put the pics where you want them.

---

### Post by xeth_delta on 2008-01-01
> **tammyf said:**
> I can't say that I know what to tell you about the issue you are having but I am having a problem with downloading my pictures at all. I have no clue as to what I am doing. Can anyone help me?

Many cameras can use several different transfer protocols. Browse through the options in your camera. I would recommend you to try connecting the cammera as a USB mass storage device. You would be able to access the pictures in your camera as if they were on an external hard-disk.

Xeth

---

### Post by tammyf on 2008-01-01
Thank you for your response but I am completely no good when it comes to using a computer at all. Is there an easire way to tell me what to do,like a step by step program. Sorry and thank you. This entire Ubuntu forum is new to me also.

---

### Post by LowSky on 2008-01-01
> **tammyf said:**
> Thank you for your response but I am completely no good when it comes to using a computer at all. Is there an easire way to tell me what to do,like a step by step program. Sorry and thank you. This entire Ubuntu forum is new to me also.

Way to bring an old thread back from the dead...LOL.

First connect your camera to the computer using a usb cable or use a card reader.
An icon on the desktop should appear, named disk. Open that and your files should be there.

---

### Post by xeth_delta on 2008-01-01
> **tammyf said:**
> Thank you for your response but I am completely no good when it comes to using a computer at all. Is there an easire way to tell me what to do,like a step by step program. Sorry and thank you. This entire Ubuntu forum is new to me also.

Welcome to the Ubuntu forums! If you are still having problems don't hesitate to ask here.

---

### Post by tammyf on 2008-01-01
O.k. so I know to plug in the camera with the usb cord and then it shows a box that says camera detected. It says that it is importing the pics. and shows the pics. in a box on the screen but then what? I have done it before and the pics. would go to a folder automatically but now I can't find them once they say they are downloaded. I hope this makes some sense. Thank you very much.

---

### Post by tammyf on 2008-01-01
> **xeth_delta said:**
> Welcome to the Ubuntu forums! If you are still having problems don't hesitate to ask here.HELP!! Thank you!

---

### Post by xeth_delta on 2008-01-01
I am not sure where the images would be saved in Gnome (the graphical interface / desktop you are using), since I use KDE (another graphical interface). Try opening Nautilus (a file manager) and look for them in your home directory/folder and in its subdirectories/folders. Otherwise, in the meantime, maybe a Gnome user will coome along to tell you where the files are saved.

---

### Post by LowSky on 2008-01-02
it should be in you *home/*username*/pictures*

if not dont auto import
open the disk to the files and manually import them

---

### Post by philinux on 2008-01-02
If you like a gui to help you, run Applications>Graphics>gThumb

Nice app.

---

### Post by inverseroom on 2008-02-09
I'm bringing this back because nobody ever answered the original question.  I love the simple import-photos utility, and don't feel like opening anything else...I want all new photos to go into my "New Pics" desktop folder WITHOUT the import utility creating a datestamped subfolder.  Seems like a simple thing...how can I do it?

---

