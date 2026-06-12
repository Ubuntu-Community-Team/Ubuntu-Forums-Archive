---
title: "Adding fonts to Open Office 2.2"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by STUMPOFWAR on 2007-05-17
The Open Office help sections states this:

To integrate additional fonts in the OpenOffice.org software, proceed as follows:
1.Go to the {install_path}/program directory.
2.Enter: ./spadmin
3.Click Fonts.
4.The dialog lists all fonts added for the OpenOffice.org software. You can select and remove fonts using the Remove button or add new fonts with the Add button.
5.Click Add. The Add Fonts dialog appears.
6.Enter the directory from which you want to add the fonts. Press the ... button and select the directory from the path selection dialog or enter the directory directly.
7.A list of the fonts from this directory appears. Select the fonts you want to add. To add all the fonts, click Select All.
8.With the Create soft links only check box you can determine whether the fonts are to be copied into the OpenOffice.org directory or only symbolic links are to be created there. If the fonts to be added are on a data medium that is not always available (such as a CD-ROM), you must copy the fonts.
9.Click OK. The fonts will now be added.


Seems clean cut.....but I don't understand steps 1 & 2 ...............could someone explain it to me?

---

### Post by thayerw on 2007-05-17
Are you just trying to make more fonts available when editing documents, etc.?  If so, there is a much easier way of doing things.

Open your file manager (nautilus or konqueror) and make sure you can view Hidden Files/Folders.  Then simply create a folder in your home directory called .fonts (it may already be there) and copy your fonts to that directory.  Voila!  These fonts should be visible to all applications now, including OpenOffice.org.

You may need to restart X, but personally I always refresh the font config with this command whenever I add new fonts:

```
sudo dpkg-reconfigure fontconfig
```

Hope this helps...

---

### Post by STUMPOFWAR on 2007-05-17
I am a teacher and I downloaded and installed some fonts into Microsoft Office over the years to use in my Elementary school classroom. I have shared my fonts with other teachers before I have always just copied the Fonts folder on to a jumpdrive and put them into the same folder on my colleagues computer

OK.....in  ETC there is a fonts folder with 2 folders ( conf.avail & conf.d) and 2 files ( fonts.conf & fonts.dtd)

I tried to drag my font files to etc/fonts but I got a permission error. When I tried to change the permissions so that I could write to the folder it said that I was not the owner....which is odd since I only have one user (ever) on this machine. I have no alternate logins or usernames. 

Am I in the right place at least?

Shawn

---

### Post by STUMPOFWAR on 2007-05-17
I created .fonts in my home folder and I out the font files into that folder. I ran the fontconfig command. When I was done I opened up OO and the fonts weren't in the pull down menu.

So you know......I pulled these fonts from Microsoft Office 2004 on a PPC Mac...... Are they compatible?

---

### Post by thayerw on 2007-05-17
Ah ha... a mac.  Well, that's a wee bit different!

Assuming these are TrueType Mac fonts, this solution should work for ya:

[LIST=1]
[*]Move the fonts you placed in .fonts to a different folder (e.g. "~/fontsmac")
[*]Open a terminal window and browse to this new folder: [FONT="Courier New"]cd ~/fontsmac[/FONT]
[*]Install fondu, a mac font converter: [FONT="Courier New"]sudo apt-get install fondu[/FONT]
[*]Then in the terminal type: [FONT="Courier New"]fondu *[/FONT]
[/LIST]

This should convert the mac fonts to a usable TrueType format for linux.  Once completed, I think you can just copy them back into your .fonts directory.

---

### Post by STUMPOFWAR on 2007-05-18
got this error message with each font

"Can't find an appropriate resource fork in Stencil"


Stencil is one of the fonts I want to keep...... (it is a dotted line tracing font)

---

### Post by Najand on 2007-05-18
Put your fonts in .fonts folder in your home and run:
```
 sudo fc-cache -fv 
```
Then restart X by pushing Ctrl+Alt+BackSpace and login again.

---

### Post by Najand on 2007-05-18
Tell me about the errors if you get ANY!

---

### Post by STUMPOFWAR on 2007-05-21
no errors....worked perfectly! many thanx......

I felt lost without my crazy teacher fonts for homework.

.......I may thank you, but my students might egg your houses on mischief night! ;)

Shawn

---

### Post by lyceum on 2007-06-24
> **Najand said:**
> Put your fonts in .fonts folder in your home and run:
```
 sudo fc-cache -fv 
```
Then restart X by pushing Ctrl+Alt+BackSpace and login again.

Worked great. Thank you!

:popcorn:

---

### Post by Georgeiger on 2007-07-16
Thank you. It worked like a dream. Best regards. Georgeiger

This comment was supposed to be with regard to message #2 on this thread but I didn't know how to do that. Georgeiger

---

### Post by steve_4802 on 2007-12-04
Nargand, thanks mate your method worked a treat for me. 

Very much starting to like this whole ubuntu thing!

---

