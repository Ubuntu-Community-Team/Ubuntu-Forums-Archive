---
title: "Ubuntu Questions"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by Struck on 2005-09-29
Totall Newb here>.< and ex Windows User so yeah>.<
My 1st Question is How do I copy files from another PC which is still using WINDOWS into the PC which is using UBUNTU.. see I tried to copy my media from Local Disk D:\ and I dont know where to paste them>.< I tried making a new folder in the desktop but  it wasnt able to copy all. 
Mozilla downloads.. when I download it asks me to Save to Disk or Open.. I always choose Save to Disk but when I look at the Download window it says All Files Downloaded to  MY DOWNLOADS..  the problem is when I need to install it I have to change directory/location to where the file/s are lying/downloaded so I would search for files (Computer>Search for file..) and type the location/folder, E.g > cd/home/andrea/My Downloads but it says No such file or directory>.<

Any help would be really appreciated

---

### Post by Borusa on 2005-09-29
Accessing files on a Windows computer.

I assume that the computers are on the same network. In Windows, create a shared directory - let's call it Share. Put the files you want to access here (or share the folder that they're in)

Then

Follow these directions :
[http://www.ubuntuguide.org/#accessnetworkfolderswihoutmount](http://www.ubuntuguide.org/#accessnetworkfolderswihoutmount)

---

### Post by davmac on 2005-09-29
First one - I think you need to look at samba. This allows you to share information across a network between windows and linux boxes. It is well covered in the Starter Guide.

Have a look at [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver), which covers installing samba and sharing directories from your ubuntu box.

Have a look at [http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway) for more information about sharing info between boxes.

Not sure about the 2nd question although I suspect it works similarly to Firefox. Have a look at the preferences and see if you can specify where to save all the downloads.

HTH,

Dave Mac

---

### Post by Struck on 2005-09-29
I looked on Edit>Preferences>Downloads and it has a check on Save all files to this folder: My Downloads and I clicked on Show Folder and it has all the files I downloaded. But how do I change location on terminal to that folder>.< I've tried cd/home/andrea/My Downloads, cd/home/andrea/My_Downloads but it still says No such file or directory; these are the files Iv'e currently downloaded and I'm planning to install but I dont know how to change to this location T_T

/home/andrea/My Downloads/xine-lib-1.1.0.tar.gz
/home/andrea/My Downloads/WineCVS.sh
/home/andrea/My Downloads/RealPlayer10GOLD.bin
/home/andrea/My Downloads/Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm
/home/andrea/My Downloads/Gyach-Enhanced-Media-Package-0.2-1.i586.rpm
/home/andrea/My Downloads/gyach_enhanced_fonts2.tar.bz2
/home/andrea/My Downloads/gyach_enhanced_fonts1.tar.bz2

This is what I get =(

root@pc12:/home/andrea # cd/home/andrea/My Downloads
bash: cd/home/andrea/My: No such file or directory

---

### Post by xmastree on 2005-09-29
Easiest way is to use tab auto-completion.

type cd /h<TAB>/and<TAB>/My<TAB> and it will fill in the blanks automagically.

edit: That's pressing the **tab** key, not typing the word... And if you hear a bleep when you press it, either nothing matches, or there's more than one. Press it again to see other possible matches. example, /home/and... would not be unique enough if there wre users caller andrea and andrew.

Otherwise, I think characters like spaces have to be preceeded by \
co cd /home/andrea/My\ Downloads

but the tab thing is the eaier option.

---

### Post by Struck on 2005-09-29
[QUOTE=xmastree]Easiest way is to use tab auto-completion.

type cd /h<TAB>/and<TAB>/My<TAB> and it will fill in the blanks automagically.

edit: That's pressing the **tab** key, not typing the word... And if you hear a bleep when you press it, either nothing matches, or there's more than one. Press it again to see other possible matches. example, /home/and... would not be unique enough if there wre users caller andrea and andrew.

Otherwise, I think characters like spaces have to be preceeded by \
co cd /home/andrea/My\ Downloads

but the tab thing is the eaier option.[/QUOTE]

Kuya, I tried that and after pressing TAB nothing happened and I cant hear the beep sound caz I dont have any speakers installed on this PC>.<
root@pc12:/home/andrea # cd/h/and/My
bash: cd/h/and/My: No such file or directory

---

### Post by xmastree on 2005-09-29
[QUOTE=Struck]bash: cd/h/and/My: No such file or directory[/QUOTE]
Try it with a space after cd.

Type cd<space>/h<tab> and see what happens.

---

### Post by PsyberOneZero on 2005-09-29
```
 # cd "/home/andrea/My Downloads"
```

Linux doesn't recognize spaces automatically. Make sure you use quotes around any file or folder with spaces.

EDIT: After playing around with autocomplete xmastree is right (see next post) BUT even using autocomplete it won't put quotes around directory so it's probably best to just type out the extra 8 characters

---

### Post by xmastree on 2005-09-29
[QUOTE=PsyberOneZero]
```
#cd /My<TAB>
```
nothing
```
#cd /MyP<TAB>
```
/MyPilot[/QUOTE]I get a beep from the PC speaker in such cases, either nothing matches or more than one match is available. Pressing tab once more will display all matches available, if there are any. Otherwise it'll just beep again.

---

### Post by Struck on 2005-09-29
It Worked! Thank you so much! ^______________________________^

---

