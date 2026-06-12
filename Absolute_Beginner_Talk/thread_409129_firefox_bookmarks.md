---
title: "firefox bookmarks"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by obxeye on 2007-04-14
how can i transfer my bookmarks.html from winxp pro sp2 to ubuntu.  i know how to copy and paste.  i just can't paste it into the firefox folder/profiles on ubuntu.  thanks,
obxeye

---

### Post by caffienefree on 2007-04-14
Bookmarks>organize bookmarks>file>export.

Then come to ubuntu, copy the file, follow the same process, and import.

---

### Post by speeves on 2007-04-14
You can actually move all of your firefox settings to linux by copying your:

c:\Documents and Settings\myuser\Application Data\Mozilla\Firefox\Profiles\*.default

folder to your linux box at:

~/.mozilla/firefox

Then start close firefox, then start firefox like this:

firefox -ProfileManager

When the profile window starts up, click on create profile:

Next->Choose Folder...

and browse to the location of the *.default folder which you have copied, then give the profile a name and hit "Finish".   You then highlight the new profile, click "Don't ask at startup", and then hit "Start Firefox".  

All of your settings should be there now, including add-ons, and search engines.

BTW, this works going from Linux to Windows as well.  Just reverse the process :)

NOTES:
1. To see the Application Data folder, you need to change Windows Explorer's options:

Tools->Folder Options...

Choose the View tab, then click on "Show hidden files and folders". Finally, click on "Apply" and "OK".  You should now see all of your hidden folders in your user's "home" directory.

2. *.default - * is just a meta-character to match whatever mozilla named your folder.  They are random strings, similar to "cjdphc6b.default".  Just choose the folder which you would prefer to use.

---

### Post by obxeye on 2007-04-14
thanks for the reply.  what folder do i save the file.  ?mozilla ?c:/  and how do i get it into ubuntu?  my ubuntu installation is on a separate hard drive that i can enter after restart. thanks.
obxeye

---

### Post by speeves on 2007-04-14
> **obxeye said:**
> thanks for the reply.  what folder do i save the file.  ?mozilla ?c:/  and how do i get it into ubuntu?  my ubuntu installation is on a separate hard drive that i can enter after restart. thanks.
obxeye

Hi,

You would save the *.default folder found in your Application Data\Mozilla directory, to:

/home/<myuser>/.mozilla/firefox/

You can do this using Nautilus or Terminal.  I would recommend saving the file on a USB drive, (a jump or external hard drive).  Ubuntu will automatically mount the external harddrive to /media/usbdisk (I think).  Then you can copy and paste the folder.

---

### Post by wataboutbob on 2007-04-14
actually, the easist way to copy bookmarks from your windows Firefox to linux is to install the add-on Foxmarks for firefox. Create a free account with them, and then install that addon in every machine you want your bookmarks sync'd.

After that, its only a question of giving your username and password that you've created with Foxmarks and voila! your bookmarks are sync'd

An added bonus is that you can access your bookmarks from any machine by going directly to the Foxmarks website - useful at internet cafe's and such.

---

### Post by obxeye on 2007-04-14
thanks for all the help.  figured out what my main problem was.  i had installed the amd64 version of ubuntu because i have that processor in my mother board.  that particular installation is crippled as far as i am concerned.  reformatted and installed ubuntu 6.1 i386 and everything is working beautifully.  was able to import bookmarks using "organize bookmarks" which was not present in the amd64 version and could also copy my default profile using helpful instructions from the forum. bravo!
obxeye

---

