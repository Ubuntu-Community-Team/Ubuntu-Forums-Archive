---
title: "change from gnome to KDE"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by edifuzzy on 2006-05-11
I am a dapper user using gnome......is there any way to easily change to KDE so that I can try it out..

If the easiest way is a new install then that will have to be the way!....

I can always run a live CD if I have to...

---

### Post by waldorf on 2006-05-11
Use synaptic to install kubuntu-desktop.

Then log out.

Click on sessions and choose KDE and away you go.

Be aware that when you install this you will get all sorts of stuff installed and it will be hard (if not impossible) to uninstall it if you decide you do not want it on your machine.

---

### Post by Iarwain ben-adar on 2006-05-11
If you have an Kubuntu live cd, you can (but you probably don't). 
I just downloaded KDE via apt-get 
>  sudo apt-get install kubuntu-desktop 

But i don't know any other way (exept with synaptic :-) )

Hope it was helpful


Iarwain

---

### Post by niviche on 2006-05-11
[QUOTE=waldorf]Be aware that when you install this you will get all sorts of stuff installed and it will be hard (if not impossible) to uninstall it if you decide you do not want it on your machine.[/QUOTE]

No, there are several threads about this hear. If you then remove some of the base KDE libraries, most of Kubuntu will get uninstalled. A bit of Deborphan / GTKorphan after this can do the trick.

---

### Post by aysiu on 2006-05-11
**Do not use apt-get or Synaptic to install KDE**

It will make KDE difficult to remove later.

Use aptitude instead: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by edifuzzy on 2006-05-12
Thanks for your replies guys. I may download the Live CD to have a play around first if there are problems getting rid of KDE. I have plenty spare HD space and am no computer Noob (I am a linux noob though) so may just make another partition and play around.

The install CD for Ubuntu took less than 15 minutes to download from Bit-torrent so downloading CD's is not a problem...

Excuse my Noobyness for a moment please.... I know Apt-get and synaptic are practically one and the same (one with GUI, one without)... but what is the difference with using aptitude...

Thanks again for your help...

---

### Post by Obor on 2006-05-12
[QUOTE=edifuzzy]
Excuse my Noobyness for a moment please.... I know Apt-get and synaptic are practically one and the same (one with GUI, one without)... but what is the difference with using aptitude...
[/QUOTE]
When you install something like KDE a lot of dependent files will get installed as well.

When you install/uninstall with apt-get (or synaptic) only the main KDE will be removed leaving the dependent files behind. 

If you install and uninstall using aptitude it will remember all dependencies and remove them as well.

---

### Post by RAV TUX on 2006-05-12
[QUOTE=edifuzzy]Thanks for your replies guys. I may download the Live CD to have a play around first if there are problems getting rid of KDE. I have plenty spare HD space and am no computer Noob (I am a linux noob though) so may just make another partition and play around.

The install CD for Ubuntu took less than 15 minutes to download from Bit-torrent so downloading CD's is not a problem...

Excuse my Noobyness for a moment please.... I know Apt-get and synaptic are practically one and the same (one with GUI, one without)... but what is the difference with using aptitude...

Thanks again for your help...[/QUOTE]

This is the best way and exactly what I did. Actually I have done both ways, but I find burning a copy of the Kubuntu dapper beta is the best way to start, I skipped the Live CD and set up a dual boot of Ubuntu/Kubuntu.

I prefer the Gnome desktop of Ubuntu. After much trying of many different Linux distros, BSD, and the HURD. 

I am now running a dual boot of Ubuntu/Yoper

Even though I prefer the Gnome desktop of Ubuntu, I have finally found a KDE distro that I like; Yoper is out of New Zealand and is a very classy KDE Linux distro, if you like KDE I have found this is the way to go.

[http://www.yoper.com/](http://www.yoper.com/)

I have surprised myself because I didn't think I would use KDE but I like having these two:

Ubuntu (my ultimate favorite OS)
Yoper (very refined and intelligent Linux OS)
:mrgreen:

---

### Post by RAV TUX on 2006-05-12
I just had a little trouble posting to this thread, my apologies about the multiple post. I will edit the last two duplicate post.

---

### Post by RAV TUX on 2006-05-12
If anyone who reads this thread and trys out Yoper as a dual boot to Ubuntu. This is what I did to avoid any possible trouble. I installed Yoper but opted out of the lilo boot, and instead choose the GRUB boot when installing Ubuntu. 

In the Yoper forum they have a bug with lilo, and I experienced trouble with lilo when using PC-BSD. I find it best to stick with GRUB.

---

### Post by edifuzzy on 2006-05-13
Ended up just chucking myself in head first....I like Kubuntu....I personally think it is easier to configure than Ubuntu....but then that is just my opinion.

---

### Post by catlett on 2006-05-13
I though you just liked the name (yosef/yoper) until I followeed your link. Any distro with a page like this right up front is alright in my book.[http://www.yoper.com/forum/index.php?showtopic=7556](http://www.yoper.com/forum/index.php?showtopic=7556)
Yosef you're becoming quite the multiple distro man. Just a little tip I now use when adding OS's to my distro. I don't allow any new installs to overwrite the mbr. I keep everything in it's partition. Then I open up the grub menu.lst and add the new distro by chainloading. It's the way grub boots to windows. You can use it for any os, you just need to know the partiton.     
Just like the window entry in your list you add your new distro using the chainloader to boot it (for an example I'll use Yoper on hda6)
```
title   Yoper
rootnoverify   (hd0,5)
chainloader +1
```
When you choose Yoper in the grub menu,  yoper's grub menu will appear and boot yoper. I have it 2 ways. One with no grub for the new OS,  it boots the kernel. The other has grub and it boots to the OSs grub menu on its partition.
I like it this way because new installs don't always identify all my OSs and I would have to enter them all again. This way it is one new entry and I know the partition because I made it before and I know the grub entry already. 
Just a note back to you. It seems I'm following you around. I just added Mepis because of your thread and the discussion between you and Aysiu. Now looks like I have to make another partiton to try your next referral.:-D 
I know I'm going way off post but (the ugly interface aside) Mepis was the fastest,easiest install ever. Plus everything so far is working out of the box. (It must be it's Ubuntu base):KS

P.S. Well it's installed. First impression is it is very nice looking and polished but looks can be deceiving. Off to try it out, thanks for the referral. One thing I have noticed is how many different fonts there are and how I can hate an OS because of it. Mepis hurts my eyes after a while and Yoper's are very thin (for lack of a better word). Ubuntu is still my personal; favorite but OS hunting is my hobby.

---

