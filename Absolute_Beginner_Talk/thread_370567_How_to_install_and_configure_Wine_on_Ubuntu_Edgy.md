---
title: "How to install and configure Wine on Ubuntu Edgy"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-25
This is not my handy work but I guide I found :)

[B]
Installing WINE[/B]

- Make sure your backports repository is enabled in the Software Sources dialog.
- You will also need a Windows box with a correctly installed and registered version of PS.

**- Open a terminal and type**

$ sudo apt-get update
$ sudo apt-get install wine wine-dev recode

**- Test the installation by downloading a small and simple Windows program (WinRAR) and download the installer in your home directory:**

$ wget [http://www.rarlab.com/rar/wrar362.exe](http://www.rarlab.com/rar/wrar362.exe)
$ wine wrar362.exe


**[COLOR="Red"]Installing Windows Software[/COLOR]**

**- Installing them is easy, follow the same steps as for WinRar. Download the executable and type:**

$ wine /path/to/executable.exe


**- After installation, change directory to wine virtual Program Files:**

$ cd "/home/your-user/.wine/drive_c/Program Files/program-name"


**- Run the installed program by typing:**

$ wine program-name.exe -winver winxp

[B]
Keep in mind that not all Windows programs will work with Wine. Moreover, some programs won't work or will look ugly without the Windows fonts. There is however a way to install Windows fonts in Ubuntu by typing:[/B]

$ sudo apt-get install msttcorefonts


**Have fun!**

---

### Post by linuxfanatic1024 on 2007-02-26
When I use Wine, I almost never use the terminal--I can just double-click the exe's from Konqueror or the KDE desktop.

---

### Post by undertakingyou on 2007-02-26
Chrome307,

Good post.  I think most new users have a difficult time with wine.  And I think you have it quite concise here.

---

### Post by Ek0nomik on 2007-02-26
Thanks.  I'm looking at installing Wine one of these days.  I'll bookmark this thread.  :)

---

### Post by crunchyfox on 2007-02-26
everthign went fine till about here......


**- After installation, change directory to wine virtual Program Files:**

$ cd "/home/your-user/.wine/drive_c/Program Files/program-name"

it seems that i cant change to a dir that has a space in it..... 
i even tried to creat a launcher 
Here is the error i got....

"Details: Failed to execute child process "/home/crunchyfox/.wine/drive_c/Program" (No such file or directory)"

no other errors when installing winrar 

thank for any input 
peace

---

### Post by eduardoeltortuga on 2007-02-26
I was having the same problem. Make sure and use the quotation marks. It was case sensitive as well! 
     Hope this helps!

---

### Post by energiya on 2007-02-26
Use the TAB key. Its so easy. Type the first few letters of the directory/file and press TAB and (if there are no other similar words) it should auto-complete.
So it should be 
```

cd /home/your-user/.wine/drive_c/Program\ Files/program-name

```

---

### Post by Dyrre on 2007-02-26
I get an error when I try to run a .exe with wine, Im running Ubuntu Edgy by the way:

root@joe-desktop:/# wine wrar362.exe 
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Im sort-of new to ubuntu and don't know what to do with this =)

Thanks

---

### Post by eduardoeltortuga on 2007-02-28
Wine shows up in the application pull down menu. When I scroll down, I see Wrar, but not any of the other apps I installed. I followed all the same steps for the Wrar example. No big deal, just curious.
      I also installed gDesklets and was able to create application launchers for my windows programs. Too cool:)

---

