---
title: "a lot of question for a first time Ubuntu"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by kdragon on 2007-04-23
1-Sound looks crazy,it's noise extreme noisy when i increase (they recorgnize sound chipset)

2-I cant play any mp3 by Rhythmbox  players,neither video format

3-some FN keys dont work such as Wireless,Lock Touchpad however FN Brightness work fine (my laptop is Toshiba M100)

4-How to install more widget such as wealther,news Rss.... I found some in the Panels

5-Which folder to save file in order to be read when i use Windows

6-Using desktop effect will kill battery time, is it true or false

---

### Post by earobinson on 2007-04-23
1. Not sure I understand you.

2. Feisty should be able to double click the mp3 and video to install mp3/video support if not check this out: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

3. chances are you are stuck like this you can try using synaptic to search for Toshiba and see if there is any extra support

4. again search synaptic for gnome applet and whatever youw ant eg weather to install them then you can right click on the panels to add them. (also I recomend using lifera for for rss)

5. ubuntu should have been able to auto mount your windows dir could you run the df command in the terminal and paste the output for us

6. This sounds true since it would be using the 3d gfx card and that uses more power.

Hope this helps

Edit: your english is great!

---

### Post by kdragon on 2007-04-23
2-> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the U**buntu restricted extras package**. Click OK.
i cant find this package

3

---

### Post by nickpaton on 2007-04-23
Touchpad:

[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

---

### Post by az on 2007-04-23
> **kdragon said:**
> 

5-Which folder to save file in order to be read when i use Windows


[http://www.fs-driver.org/](http://www.fs-driver.org/)

Install that in windows and your linux partition will be used as if it were a native windows filesystem.  Very stable.

---

### Post by nickpaton on 2007-04-23
Your question 5:

A neat thing to do is to add an extra partition which can be shared by both Windows and Ubuntu

Make sure it's FAT32 - have a look at this HOWTO:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Note that it does describe how to make a separate /Home folder but the idea is very similar.

NOTE:

1. Change the partition to be logical, but choose the partition to be filesystem FAT32 rather than ext3.

2. Once you have clicked Apply and rebooted, the new partition should be present.

3. Ignore the end section 'Using the new partition'.  This is to configure a new ext3 /Home partition.

Make sure you back up any data before doing this.

---

### Post by kdragon on 2007-04-23
> **earobinson said:**
> 1. Not sure I understand you.

2. Feisty should be able to double click the mp3 and video to install mp3/video support if not check this out: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)



1-i solved first problem by switching realtek chipset to Intel HD chipset :) 

2-No need to download,just double click audio/video format,Ubuntu will ask for installing add-on,just select all and everything is ok :guitar: 

Ubuntu rocks :lolflag: 

No3 is really difficult for a bad english speaker for me
:confused::confused::confused::confused:

Thanks to you,i really switch to Ubuntu now and forever :lolflag:

---

### Post by nickpaton on 2007-04-23
Question 3

Have a look at this (out of date) information on your laptop:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM100]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM100")

---

### Post by lucia_engel on 2007-04-23
Question 1:

I think you need to turn PCM down. Find the volume properties and turn it down to around 50%. 

I don't quite remember the exact location of the volume setting program, you can also open up a terminal and type:
```
alsamixer
```
Use your arrow keys to navigate to PCM and then press down arrow to turn it down. Esc to exit.

---

### Post by kdragon on 2007-04-23
another noob question: may i import my firefox configuration in windows to Linux because the windows direction is different from Linux

i'm using firefox portable

---

### Post by nickpaton on 2007-04-24
> **kdragon said:**
> another noob question: may i import my firefox configuration in windows to Linux because the windows direction is different from Linux

i'm using firefox portable

I'm not sure what Firefox portable is, but I use Firefox version 2 - not Swiftfox. 

Congratulations on your progress so far!

The following link from the Mozilla Firefox site describes the locations of the profile folders in Windows and Linux:

[http://www.mozilla.org/support/firefox/edit#profile]("http://www.mozilla.org/support/firefox/edit#profile")

If you are importing your Firefox settings from Windows on a another partition on the same PC:

1. On Ubuntu Desktop click on 'Windows XP' icon.

2. Navigate and click on 'Documents and Settings' folder.

3. Follow the rest of the instructions for XP in the link above.  
    (On my PC, my Firefox profile was not under 'Nick' but under 'Administrator'.)

4. Find the 'Profile' folder.  You will find that aaaaaaaa.default folder is inside it.

5. Copy the aaaaaaaaa.default folder into your Ubuntu Home folder.

6. In Ubuntu click on Places > Home Folder

7. The /.Mozilla folder is hidden.  
     To unhide it click on 'View' and then 'Show Hidden Files'.  This will now reveal all hidden files including the .Mozilla folder.

8. Click on .Mozilla > Firefox and look for a xxxxxxxxxxx.default folder.  Replace this with the contents of the aaaaaaaaa.default folder you saved in your Home folder.

If you only want to import your bookmarks, from Windows open Firefox > Bookmarks > Organise Bookmarks > File > Export.

Save the exported file on in My Documents in Windows, and then copy across to Ubuntu Home folder.
Then import the settings, navigating to where you saved the file in your Home folder.

Good luck!

---

### Post by kdragon on 2007-04-24
i appreciate you too much for useful detailed information

i have so much question which may be available in forum but i cant search exactly what i want to find...So pls help me more times :D

1-Do you have any recommendation for audio player that i can manage my library by tab.An example of this is my favorite windows application :" Foobar" [http://www.foobar2000.org/](http://www.foobar2000.org/)

2-How to type vietnamese and chinese character 

In windows i can type vietnamese by Unikey,there is a Linux version. I installed successfully but cant type although i choose correct type of Unicode ??? [http://linux.softpedia.com/get/Programming/Localization/X-Unikey-9749.shtml](http://linux.softpedia.com/get/Programming/Localization/X-Unikey-9749.shtml)

I dont have any idea ab typing chinese in Linux because in windows i use the availble windows keyboard

Ps:Linux,especially Ubuntu run cool,i think it (sure) better than XP at all side (speed,stable,free...) a thousand time :D,but it's quite different for the first time user like me.I'm waiting for learning a lot from forum in order to switch to Ubuntu

---

