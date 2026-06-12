---
title: "Some newbie questions :)"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-02-02
Hi, I just recently switched from Windows-Ubuntu 6.10. I know my way around Windows very well but not Linux(this is one of the main reasons I switched). Anyways, I have a few questions for you guys. 

1)How do I go by updating my drivers(such as my Nvidia Geforce Go 9900 GS and my audio drivers)?

2)I dont know if this is the right place to ask this and I doubt it will work but I currently have a MSI VOX USB 2.0 TV Tuner Card. Is there any software made for linux that works with TV tuner cards? I'm currently using WinDVR for Windows, but I dont know of any others.

3)This is a very newbie question and I'm sorry, but where is your Program Files folder? I've looked just about everywhere and I cant seem to find it, if there is one..

Thanks for the help guys, its much appreciated!!

---

### Post by meng on 2007-02-02
1. Most likely you'll be lucky and everything will be recognized out of the box without you having to install drivers. After installing Ubuntu, you can install proprietary drivers for your video card that will improve performance (especially 3d acceleration).

2. I don't know much about tuner cards.

3. Your documents generally get saved in the /home/username folder, e.g. if you have a username bofur, your home folder is /home/bofur (although you can save documents almost anywhere you wish to, that's one of the key features of Linux, customizable). Now you asked a different question I know, which is where the programs get installed to and the answer is that it varies, but often somewhere with the /usr folder (but usually a few levels lower down).

---

### Post by compwiz18 on 2007-02-02
I can answer the third one: there isn't any.  When you install an application, it dumps file all over the hard drive (edit: *meng is correct too - it does put _most_ of the program's files in /usr, but some go in the place below*).  But some places of interest:
[LIST]
[*]/etc - configuration files
[*]/usr/bin - where most executables go
[*]/usr/share/pixmaps - where program icons live
[*]/home/your-username - where your configuration files live, although most are hidden.  In the file browser, press ctrl+h to see the hidden files
[/LIST]

---

### Post by 23meg on 2007-02-02
> 1)How do I go by updating my drivers(such as my Nvidia Geforce Go 9900 GS and my audio drivers)?Drivers in Linux are provided as part of the kernel and are mostly maintained by the kernel developers and the surrounding community rather than the vendors themselves. Unless you're having issues, it's generally recommended to keep what you have, especially if you're a beginner. An exception may be video drivers; nvidia do provide a closed source driver which will give you extra features; do a forum search for "Envy" if you need a script that will let you install it.

> 2)I dont know if this is the right place to ask this and I doubt it will work but I currently have a MSI VOX USB 2.0 TV Tuner Card. Is there any software made for linux that works with TV tuner cards? I'm currently using WinDVR for Windows, but I dont know of any others.I did a web search for "MSI VOX USB linux" and it seems to be supported. I'm not familiar with TV cards so I can't help you with the specifics.> 
3)This is a very newbie question and I'm sorry, but where is your Program Files folder? I've looked just about everywhere and I cant seem to find it, if there is one..There's no single folder where program files go; typically, when you install a package, files from it get installed into different directories all over your system. To figure out where files from a certain package are installed, right click the package in Synaptic, click "Properties" and go to the "Installed Files" tab.

---

### Post by shareMenaPeace on 2007-02-02
You can also use ther terminal command

> locate NAME
to find a folder path/file.

---

### Post by chr on 2007-02-02
hi there

and an overviw of the installed programms you can get under usr/share/applications.

brgds

chr

---

### Post by Zzl1xndd on 2007-02-02
The best thing for TV tuner cards IMHO is MythTV theres lots of info in the forum about it. It'll give you a Windows Media Centre like set up.

---

### Post by Bofur on 2007-02-02
Wow, thanks for the quick responses and the great help!

---

