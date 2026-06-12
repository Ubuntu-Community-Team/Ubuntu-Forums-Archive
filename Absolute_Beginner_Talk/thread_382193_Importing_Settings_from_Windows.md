---
title: "Importing Settings from Windows"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-03-11
What's the easiest way to import stuff from windows?
I want to get my Outlook mail and address book, and my IE favourites into evolution and firefox.
They are on my laptop ATM but its networked to my linux pc.

---

### Post by AndyCooll on 2007-03-11
For Evolution, there is an import function enabling you to import Outlook stuff (File >Import > Forward > Import a single file)

For Firefox, select Bookmarks >Organise Bookmarks > File > Import

:cool:

---

### Post by Fidelio on 2007-03-15
My outlook stuff is all pst files, which evolution won't import.
I suppose I could download Thunderbird onto my windows PC, import the files from Outlook,
then copy these files onto my Linux machine. It's a bit longwinded, but I can't think of anything else.

---

### Post by lamalex on 2007-03-15
yes outlook to t-bird to evolution is the only way to do it, unfortunately.

---

### Post by Svento on 2007-09-19
But what if I want to import my XP Firefox settings to the Firefox on the Ubuntu installation? Or from XP Thunderbird to Ubuntu Thunderbird?

---

### Post by nb123 on 2007-09-19
Svento, I've never used Thunderbird before, but I recently imported my Firefox profile from XP to ubuntu, so I think I can help you there. 

Go to 'My documents' in XP, and first of all change your options so that you can see the hidden files. You'll see a folder called Application Data. Open it and find the firefox folder (maybe under mozilla) and then within it your profiles folder. Now, you should see a profile.ini file as well. Don't touch that, just copy the folder that says something like '8sdf20fas', just a bunch of random characters onto a USB drive or something. 

Then once in ubuntu, go to /home/Desktop, folder and once again unhide all folders. You should see a folder entitled .Mozilla , open it, then open the firefox folder and you should see the profiles. Now, copy your XP firefox profile there. Now,  I hope I'm remembering this correctly, because I remember editing the profile.ini file manually, but I think all you need to do is type this in your terminal: ---

firefox -ProfileManager

which will launch the firefox profile manager, and then just create a profile and point to your folder, make that your default profile , and you're done! Yup, pretty sure that's it.

---

