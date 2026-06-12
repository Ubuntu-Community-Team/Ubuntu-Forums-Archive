---
title: "Something weird with KDE leftovers, simple problem, please help (READ)"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-26
Hey, I thought I would try out Kubuntu and the KDE desktop, so I typed into the terminal:

```
sudo aptitude install kubuntu-desktop
```

After waiting a VERY long time, it finally finished, giving me a load of junk programs with stupid names like Konquerer and KAte. I tried the KDE out, and whilst liking it, I preferred GNOME, so switched back immediately.

```
sudo aptitude remove kubuntu-desktop
```

After waiting another long period of time, it was done. All the programs had gone, and KDE was gone. Small problem, there was a few leftovers. Here are the ones I know of.

Konsole (KDE Terminal)
Konqueror Web Browser
When I turn the computer on and it loads, the Kubuntu logo and loading bar appears, but when I turn the computer off, the standard Ubuntu one appears.

How can I get rid of these annoying leftovers so I will be back exactly like how it was before installing KDE? The commands to change these individual things would be OK, but there may be something I have missed, so if there was a general command, that would also be great.

Thanks in advance,

Camz

---

### Post by camz on 2007-03-26
Please?

---

### Post by camz on 2007-03-26
I thought this problem would be easy to solve :(

---

### Post by igknighted on 2007-03-26
I'm sure that it is, but please, wait 24 hours before you bump a post.  Begging like that will not encourage people to respond.

---

### Post by camz on 2007-03-26
OK sorry, however it was on page 2 and I wasn't getting a reply...

---

### Post by igknighted on 2007-03-26
> **camz said:**
> OK sorry, however it was on page 2 and I wasn't getting a reply...

I, like many others, make use of the unanswered post button, and also go back several pages to read (I also have it set to show more threads per page).  It is tough for threads to slip through.  Ironically by bumping you wont be found by that "Unasnwered Posts" button.

I looked into your issue a little.  I use KDE so I haven't tried to get rid of it like this, but just for kicks try:
```
sudo apt-get remove konqueror konsole kdm
```
BE VERY CAREFUL HERE!!! READ EVERYTHING THAT APT WILL REMOVE!!!  It is possible that this could remove some very important packages, so if you see anything that looks important (anything gnome based, or relating to Xorg, or anything else you are unsure of) post it here and others can tell you if its OK to remove.  Don't say yes to the remove until you are sure.

After you run this it will probably tell you certain programs are un-needed.  Run "sudo apt-get autoremove" to remove them as well.

---

### Post by camz on 2007-03-26
Thank you it is doing it now I will post if anything weird happens

---

### Post by camz on 2007-03-26
Forum@Linux:~# sudo apt-get remove konqueror konsole kdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdm is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kcontrol kdebase-data kicker konsole kfind konqueror
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  konqueror konsole
0 upgraded, 0 newly installed, 2 to remove and 137 not upgraded.
Need to get 0B of archives.
After unpacking 7651kB disk space will be freed.
Do you want to continue [Y/n]? 

They all seem to be KDE programs, so shall I continue, and then use auto remove to get rid of the other "K" programs that are not wanted?

---

### Post by igknighted on 2007-03-26
> **camz said:**
> Forum@Linux:~# sudo apt-get remove konqueror konsole kdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdm is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kcontrol kdebase-data kicker konsole kfind konqueror
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  konqueror konsole
0 upgraded, 0 newly installed, 2 to remove and 137 not upgraded.
Need to get 0B of archives.
After unpacking 7651kB disk space will be freed.
Do you want to continue [Y/n]? 

They all seem to be KDE programs, so shall I continue, and then use auto remove to get rid of the other "K" programs that are not wanted?

Yup.  Run the autoremove command it gave and reboot, all the kde stuff should be gone.

---

### Post by camz on 2007-03-26
thank you very much

---

### Post by Lexyboy on 2007-03-26
You should be fine with ignkighted's suggestion - it doesn't remove anything non-kde related.

For the boot logo, I *think* it's something like
```
sudo dpkg-reconfigure usplash
```
but the answer is knocking around the forums somewhere, so you should be able to find it.

BTW, I wouldn't call Konqueror 'junk' till you've tried it a bit longer than you seem to.  It's really pretty powerful - one of the main reasons I use KDE on my work computer (though slightly irritating to wait ages for it to load when I just want to open my home dir).

---

### Post by mikewhatever on 2007-03-31
> **camz said:**
> Hey, I thought I would try out Kubuntu and the KDE desktop, so I typed into the terminal:

```
sudo aptitude install kubuntu-desktop
```

After waiting a VERY long time, it finally finished, giving me a load of junk programs with stupid names like Konquerer and KAte. I tried the KDE out, and whilst liking it, I preferred GNOME, so switched back immediately.

```
sudo aptitude remove kubuntu-desktop
```

After waiting another long period of time, it was done. All the programs had gone, and KDE was gone. Small problem, there was a few leftovers. Here are the ones I know of.

Konsole (KDE Terminal)
Konqueror Web Browser
When I turn the computer on and it loads, the Kubuntu logo and loading bar appears, but when I turn the computer off, the standard Ubuntu one appears.

How can I get rid of these annoying leftovers so I will be back exactly like how it was before installing KDE? The commands to change these individual things would be OK, but there may be something I have missed, so if there was a general command, that would also be great.

Thanks in advance,

Camz
That was exactly my own experience. Thought I'd search the forums to see if there was anyone else. The issue in very well phrased Camz. I also found out that Kmail was lurking in the system not showing in the menues, and that the home folder is full of hidden folders of KDE programs. Just open your home folder and hit Ctrl+h. Many users seem to wrongly believe that uninstalling in Ubuntu leaves no leftovers contrary to Windows. I was rather surprised. Even more leftover junk is found if you type locate kde in the terminal. I don't know how to get rid of it.
You can disable the spalsh screen in grub menu.lst. Change the following
> title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,6)
[COLOR="Blue"]kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet splash[/COLOR]
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


to the following
> title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,6)
[COLOR="#0000ff"]kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet[/COLOR]
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


---

### Post by Dual Cortex on 2007-04-03
nvm...

---

### Post by mikewhatever on 2007-04-03
DualCortex, just for fun, I've actually followed your suggestion. It freed 250 MB of disk space, but also removed the following programs I had installed long before KDE: vlc player, opera browser, skype, wireshark, totem player. Also, it's been mentioned above, that KDE has been installed and uninstalled with aptitude.
Update: After rebooting, the gnome nm didn't work and had to be reinstalled, and also, every time the screen saver starts working, the screen gets black and I get logged out of gnome session.

---

### Post by finferflu on 2007-04-03
Actually there's a good tutorial about getting back to pure Gnome/KDE/Xfce [here]("http://www.psychocats.net/ubuntu/puregnome").
Hope it helps.

---

### Post by Dual Cortex on 2007-04-03
That's what I had linked him to... but then I noticed he had actually used aptitude instead of apt-get.
Though it seems the manual list actually got him rid of many things... some unwanted, though.

---

### Post by finferflu on 2007-04-03
Yes, that's why I have posted that link, I've seen him removing packages manually, so at this point it's better having the full list of KDE apps.

---

### Post by mikewhatever on 2007-04-03
Thats the link I've followed. I am not quite sure why the programs mentioned had beed removed, I do not see them among KDE packages, however that was another supprise. The good point is, the system is cleaner now.

---

### Post by strabes on 2007-04-08
Here's how to get rid of or change your usplash theme: [http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

---

