---
title: "Tidy Desktop and bin files"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-02-27
Hello
Wishing to keep a tidy desktop, I have read round the subject, including the wonderful post:

["http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+ubuntu"]http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+ubuntu]()

I have an ancillary query:

If I want to use and download a bin file, I am always asked to download it to the desktop.
Do I *have* to download it to the desktop before running it, or can I download it to a folder of my choice? 
If a bin file is already downloaded to the desktop, can I subsequently move it to a more convenient folder for the sake of tidiness/

I ask because in Windows I was afraid of moving anything.

Kind regards

John

---

### Post by Cloudy on 2008-02-27
If you're using Firefox you can specify where files are downloaded by going to the "Downloads" tab (or just pressing Ctrl + J), and then where it says "All Files Downloaded To:" click on the directory. You ought to be able to choose where files are stored when downloaded in Firefox.

Hope my post helps. :)

---

### Post by glennric on 2008-02-27
Are you downloading in firefox?  If so go to Edit->Preferences, and under the main tab select "Always ask me where to save files."  Then you can select where to save your files.  There is no need to save to desktop.  You can use files in any directory.  The same is true in Windows.

---

### Post by kellemes on 2008-02-27
Never be afraid, you're using GNU/Linux now, no need to fear, just relax and you'll be fine. ;-)

You can have the bin-file downloaded in any folder you like, personally I have a folder called "down" in my /home-folder
.
You can setup Firefox to put downloaded files into your preferred folder.
Edit -> Preferences -> Maintab -> Save files to..

And obviously you can move the file using Nautilus "your file manager" or using the terminal like so..
```
mv /home/myname/Desktop/myfile.bin /home/myname/mydirectory/
```
myfile.bin is now moved from Desktop to mydirectory.

---

### Post by SOULRiDER on 2008-02-27
You can download stuff to wherever you want, dont be afraid to do so. But remember, if youre asked to execute something and in the example theya re using the desktop as the example you will have to change commands accordingly.

---

### Post by Andavane on 2008-02-28
> **kellemes said:**
> Never be afraid, you're using GNU/Linux now, no need to fear, just relax and you'll be fine. ;-)

You can have the bin-file downloaded in any folder you like, personally I have a folder called "down" in my /home-folder
.
You can setup Firefox to put downloaded files into your preferred folder.
Edit -> Preferences -> Maintab -> Save files to..

And obviously you can move the file using Nautilus "your file manager" or using the terminal like so..
```
mv /home/myname/Desktop/myfile.bin /home/myname/mydirectory/
```
myfile.bin is now moved from Desktop to mydirectory.

Thank you; this is comforting to hear. More than a decade in Windows can result in states of paranoia. Will certainly take time to study and practise the commands you suggest. My  further query on this is:

When I dragged the file called 'paz_install.bin' onto the desktop as per the instructions, it generated more files ('Personal_Account_Linux.bin', 'Converter.jar', 'pa6Config.txt' [this stores the settings and preferences] and 'PAZ_Rapid_Start_Video.html' which doesn't seem to anything when you double click on it.)

Now, using the command you gave, do you think it would be Ok to move all those files to the folder of my choice? Can you move more than one file by writing one command? I guess I ought to spend some hours studying this.

Another thing on the desktop:

In Windows this is a place with special qualities and some of the things HAVE to be done there, and things can get very upset if one is not careful. Do I take it that in Linux the Desktop is just another folder, not essentially different from any other?

Kind regards

john

---

### Post by Andavane on 2008-02-28
> **SOULRiDER said:**
> You can download stuff to wherever you want, dont be afraid to do so. But remember, if youre asked to execute something and in the example theya re using the desktop as the example you will have to change commands accordingly.
 Beginning to understand. so:
"Put it on the desktop" could read:
"Put it on the desktop, or destination folder of your choice"?
Thanks again.

---

### Post by roscal on 2008-02-28
Yes , it is a new philosophy.
You are dealing with a system.
Not a A drive, C drive, etc. , as in windows.
You have a system.
Try right clicking on your target file,
You might see an option to save...the file,
anywhere you want on your system.:guitar:

---

