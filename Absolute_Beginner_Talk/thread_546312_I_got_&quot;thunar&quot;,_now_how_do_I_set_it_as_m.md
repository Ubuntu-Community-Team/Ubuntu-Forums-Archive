---
title: "I got &quot;thunar&quot;, now how do I set it as my default instead of Natauls?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-08
Hey,

I like thunar because it is fast. anytime I open a folder it opens with nautalius. How do I make my favorite file browser the default?

StaticVoid

---

### Post by felicity on 2007-09-08
Here's a link:
[http://www.psychocats.net/ubuntu/nonautilusplease]("http://www.psychocats.net/ubuntu/nonautilusplease")

---

### Post by PsycoGeek on 2007-09-08
Script did not work for me.  Any other suggestions?

---

### Post by walkerk on 2007-09-08
thats strange.. I used the script to replace nautilus w/ thunar and it worked wonderfully..

---

### Post by felicity on 2007-09-08
Same here, worked fine for me.

---

### Post by staticvoid on 2007-09-09
Hhhmmm...
I did not work for me even thogh after executing the script it gave me 
"Thunar should now be your new default file manager in Gnome"
I install Thunar wirth "Add/Remove..." It's in my Accesories list under applications, could that be the problem?
How did you install thunar, walkerk?

thanks for the link felicity, I checked out some other portions of the site :)

staticvoid

---

### Post by Telecaster72 on 2007-09-09
I installed it through Synaptic and it works Ok it opens folders with Thunar if i open them through "places" on the panel, but the folders on the desktop opens with Nautilus still...so i am following this tread with great interest.

---

### Post by staticvoid on 2007-09-09
Hi Telecaster72,
Now that I try opening a folder on the dektop the same thing happens. Hmm... I tried goin to properties of the folder and select "open with" and then choos "thunar" but, I could get it to select!  huh? Anyway, you read about that .sh file, right? you might wanna try that, I'll try synaptic package manager...there might be some package I am missing.

sv

---

### Post by Telecaster72 on 2007-09-09
hmmm .sh file? I downloaded the "defaultthunar.sh" to my desktop and ran the script, is there any other sh files??
Btw i cant change the "open with" either...

---

### Post by HereInOz on 2007-09-09
I have run the script after installing Thunar and if I click on Places > Home Folder it will still open with Nautilus.  However, if I open the Home folder with Nautilus, and then right click on a folder, I have the Open folder with Thunar option, rather than with Nautilus.

Interesting.  Perhaps this is the "default" action to which the How-to referred.

---

### Post by PsycoGeek on 2007-09-09
I can right-click on folders on the desktop and open with Thunar.  Music and Shares (two mounted locations on my network) open with Nautaulis.  There is no way to open them with Thunar.  

The following also open with Thunar on the "Places" menu: 

Home Folder, Desktop, Computer, Music and Shares (two mounted locations on my network).

The following open with Nautaulis on the "Places" menu: 

CD/DVD Creator, Network

---

### Post by staticvoid on 2007-09-09
yeah...
on my dock I edit the command it executes to "thunar" it works, but still, not everything will open with thunar :(

sv

any other good high speed file managers out there?

---

### Post by felicity on 2007-09-09
Rox-Filer is "very" fast, and super-customizable. But it takes awhile to set it up the way you want it since there's so many options.

---

### Post by Aishiko on 2007-09-09
> **felicity said:**
> Here's a link:
[http://www.psychocats.net/ubuntu/nonautilusplease]("http://www.psychocats.net/ubuntu/nonautilusplease")

I tried the link only to get a blank screen, I was hoping to mod the script for my chosen file manager, but alas I cna't get the script!  can anyone share the script in the forum in some way?

---

### Post by felicity on 2007-09-09
Here's a download link for the script: [link]("http://rapidshare.com/files/54586323/defaultthunar.sh.html")

---

### Post by aysiu on 2007-09-09
As far as I know (being the creator of the script), even if the script works, it won't affect how folders on the desktop are opened. I don't know how to fix that. If you actually can modify it (to clean up the bad coding, as I am not a programmer, or to make it so desktop icons open in Thunar), please do! Here's the original code: ```
#!/bin/bash
echo '
Making sure Thunar is installed
'
sudo aptitude update
sudo aptitude install thunar
echo '
Downloading new .desktop files
'
mkdir temp
cd temp
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-computer.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-folder-handler.desktop
wget -c http://www.psychocats.net/ubuntu/defaultthunar/nautilus-home.desktop
sudo chown root:root *.desktop
echo '
Making backup copies of old .desktop files
'
sudo cp /usr/share/applications/nautilus-computer.desktop /usr/share/applications/nautilus-computer.desktop.backup
sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.backup
sudo cp /usr/share/applications/nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop.backup
sudo cp /usr/share/applications/nautilus-home.desktop /usr/share/applications/nautilus-home.desktop.backup
echo '
Replacing old .desktop files with new .desktop files
'
sudo mv nautilus-computer.desktop /usr/share/applications/nautilus-computer.desktop
sudo mv nautilus.desktop /usr/share/applications/nautilus.desktop
sudo mv nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop
sudo mv nautilus-home.desktop /usr/share/applications/nautilus-home.desktop
cd ..
rmdir temp
echo '
Thunar should now be your new default file manager in Gnome
'
```

---

### Post by Aishiko on 2007-09-09
so to use say dolphin or PCman I just replace thundar with the name of the file manager we want to use?

---

### Post by capink on 2007-09-10
The desktop in gnome is managed by nautilus, so it will only open folders using nautilus. Gnome is not exactly modular.

---

### Post by staticvoid on 2007-09-10
oh. so much for choice then ;)

---

### Post by PsycoGeek on 2007-09-10
> **capink said:**
> The desktop in gnome is managed by nautilus, so it will only open folders using nautilus. Gnome is not exactly modular.

Would another interface be better for options then (Xfce, KDE)?  Like gettin one file manager to work for everything?  Setting up one music player to handle all of the files/playlists/media keys on a keyboard/etc... ?

---

### Post by capink on 2007-09-10
> **PsycoGeek said:**
> Would another interface be better for options then (Xfce, KDE)?  Like gettin one file manager to work for everything?  Setting up one music player to handle all of the files/playlists/media keys on a keyboard/etc... ?

I have had better luck with xfce when it comes to choosing different components. [Here]("http://ubuntuforums.org/showpost.php?p=2026930&postcount=70") is how I did it. I actually now use gnome-panel instead of xfce4-panel within xfce and it opens folders with thunar. But I don't have nautilus installed.

---

### Post by nutter78 on 2007-11-15
Great thx guys - i'm going to try this

---

### Post by staticvoid on 2007-11-16
looks like a good tutorial :D

sv

---

