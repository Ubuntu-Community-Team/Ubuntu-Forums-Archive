---
title: "I installed msword with WINE, but now can't find word"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-23
Using WINE, I installed MS Word 2000 from the cd. The problem is I can't find Word anywhere on my system. When I installed it, I got a message that said that something like "Word was complete installed successfully. " But I can't find the application. I tried to reinstall Word from the cd, and it got a window that asked me If I wanted to Repair, Reinstall, or Remove word, so it would seem Word is in there somewhere, but I can't find it to access it. Is there some additional step I need to do to get Word to come up? I currently have Ubuntu 6.0.6 installed as my O/S. I would be grateful for any help.

---

### Post by harishg on 2007-04-24
Did you do a quick search for word.exe or something similar.? That would give you the location of the file.Turn on your hidden files.I think it goes somewhere under ~/.wine/... or something.

---

### Post by orwellus on 2007-04-24
Thanks for the reply. I'm still new to ubuntu, could you tell me how to turn on my hidden files.

---

### Post by xcat442 on 2007-04-24
Hello,

Ok this may be a little long winded but here we go. Thank you for your patients.

1. Go to Applications > Accessories > Terminal and open up a new terminal window.
2. In the terminal window type in the word **notepad** and press enter.
3. Wine will configure itself and start notepad.

As wine starts notepad you will see something like /home/yourusername/.wine  Your username being your unix account. Remember this you will use it a little later.

When wine started notepad it made a new directory in your home directory called .wine and inside this folder is some files needed to run word.exe. This directory may already exist since word.exe was installed previously. And the .wine directory is hidden.

Now we will get into this folder and find word.exe

4. Go to Places > Home Folder and click the Paper & Pencil icon next to the Location address bar. What you want to see is similar to /home/yourusername and not the buttons.

5. Now after your username put a forward slash and type out .wine like so
**/home/yourusername/.wine** and press enter. Now you should see **drive_c** open this folder and your should see **Program Files** and in this folder should be word.exe click on word.exe and it should launch.

Now a neat trick you can to is drag and drop the program folder into the side panel of the home file browser window, this will create a link to the windows programs folder for future access. Most of the time as you install windows programs using wine they would show up under Applications under a Wine entry, but sometimes they will just not and you will have to do the above. This little tutorial will take you under the hood a little and show you where Ubuntu keeps your program settings. It's also good to backup these hidden folders when doing your backups.

Hope this works, let me know.
Blessings

---

### Post by Noah0504 on 2007-04-24
CTRL-H will also show your hidden files under Nautilus.

---

### Post by orwellus on 2007-04-24
Thanks for your help. I was able to get it work. xcat442 your steps worked until step 4 and 5 but following Noah050 suggestion I hit CTRL + H in my home file to reveal the hidden files, and then with a bit of searching was able to fine the .wine file and with a bit more search the Winword.exe file and I got it to work. Then following your suggestion xcat442 I dragged the .wine and program files folder to the side of my home page. Thanks again.

---

