---
title: "Where is the wine directory"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-09-18
Hello, i am a complete nub to linux systems. i read that i needed to install wine , so i did. then i tried to download a few things, like xfire, steam, wow, etc...  
I had expected they would create a desktop item, but they didnt. i know roughly that wine creates a fake "c" directory to install the games, but i do not know how to get there.
Could somebody please show me how to get to the windows programs i have put onto this computer?


P.S. I would also like to play silkroad online, but when i go to the website, it gives this message: 

  Web page of Silkroad Online is optimized under below condition.
Windows Operation Systems ( Microsoft Windows 9X/Me/NT/2000/XP/2003 )
Microsoft Internet Explorer 4.0 and above.

I assume that getting internet explorer would solve this problem. but is there any way i can acces it on firefox?  Here is website link [http://www.silkroadonline.net]("http://www.silkroadonline.net")

---

### Post by Brunellus on 2006-09-18
WINE directory is at

~/.wine

the 'fake c:' is at 

~/.wine/drive_c

---

### Post by Poeffie on 2006-09-18
The previous post is correct

If you work graphically, try pressing Ctrl+H in your /home/$USER folder to disply the hidden items
[hidden means it has a dot before its name]

---

### Post by Cardmaster91 on 2006-09-18
thankyou poffie

---

### Post by Brunellus on 2006-09-18
> **Cardmaster91 said:**
> um... remember im a total noob.
the wine directory is a hidden directory in your home directory.  it is located at 

/home/YOURUSERNAME/.wine

In Nautilus, go to your home directory, hit CTRL + H to see the hidden directories and files, and you will find one named .wine

---

### Post by Cardmaster91 on 2006-09-18
Ok, i see the .wine directory, and all my programs. some of them will open with wine windows emulator, and some of them want me to select a program, but wine is not in the list. pls help


also, do you know if wine suppports xfire? b/c i try to open it, it will get to the pint where i have just logged in. the login window doesnt close, and xfire client window opens, but it is small, i cant see anything, and it cant get larger

---

### Post by Poeffie on 2006-09-18
does it have an option to input your own program? (at the bottom of that screen)
try typing "wine" (without the quotes) in there
perhaps there is something else you have to do before it works 100%

Other question: does the file you selected have to be opened with wine? Perhaps you can open that file type without wine.

---

### Post by Cardmaster91 on 2006-09-18
> **Poeffie said:**
> does it have an option to input your own program? (at the bottom of that screen)
try typing "wine" (without the quotes) in there
perhaps there is something else you have to do before it works 100%



ok, this worked to open the program, but now when i open it, it gives me this meesage. "Fatal Error: Could not load module "bin/vgui2.dll"" the program is team, if you need to know. I belive this is getting a little off topic tho. And i cheked the /bin directory, the file was indeed there.


> **Poeffie said:**
> 
Other question: does the file you selected have to be opened with wine? Perhaps you can open that file type without wine.

I believe you meant to answer my xfire question. but no other program can open it, its a .exe

---

### Post by Poeffie on 2006-09-18
hmm.. Remeber that wine isnt able to do everything
I dont think I'll be able to help you any further.

---

### Post by Brunellus on 2006-09-18
it bears mentioning here that WINE IS NOT PERFECT.  Many, if not most applications still dont' work properly in WINE.

---

### Post by Cardmaster91 on 2006-09-18
ok, about steam, i wat i did was copy the .exe to my desktop, and it had to update, so it updated on my desktop (i think). but i put it bak in the steam directory, and now it tries to update, but gets to 26% and just disapears.

---

### Post by Cardmaster91 on 2006-09-18
> **Brunellus said:**
> it bears mentioning here that WINE IS NOT PERFECT.  Many, if not most applications still dont' work properly in WINE.

I am fairly certain that you c an play counter strike on wine. now why would you be able to play cs, but not the program that allows you to acces the servbers?

---

### Post by Poeffie on 2006-09-18
I'm not sure, but I think you should search for steam using the search button.

My guess is that wine cant work with steam, becouse it has to connect to other servers trough wine. [I'm not sure, I hardly use it]

---

### Post by Cardmaster91 on 2006-09-19
um, i had to wipe my hd today, so i reinstalled wine. (i know its there). But now the directory is not there.

---

### Post by Brunellus on 2006-09-20
> **Cardmaster91 said:**
> um, i had to wipe my hd today, so i reinstalled wine. (i know its there). But now the directory is not there.
~/.wine

---

