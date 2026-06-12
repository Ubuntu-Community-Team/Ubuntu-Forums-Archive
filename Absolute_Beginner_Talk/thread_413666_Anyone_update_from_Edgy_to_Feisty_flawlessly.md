---
title: "Anyone update from Edgy to Feisty flawlessly?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-04-19
I am wondering how many were able to update from Edgy to Feisty (not
fresh install, but using update manager) without flaws and without having
to reconfigure hardware, mainly network, modem, monitor and printer.

Thanks,
Michl

---

### Post by Seisen on 2007-04-19
I have done it, I even did before they released Feisty and upgraded when it was still in beta.

---

### Post by PriceChild on 2007-04-19
For upgrading, see the instructions at [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Please always keep backups.

---

### Post by solracarevir on 2007-04-19
My upgrade wen't almost flawlesly, everything works, but i lost my ability to put my laptop on sleep, that was while feisty was still on beta, when i arrive home today I will run the update manager to see if the last minutes fixes solved the issue, i will let you know. But everything else worked fine for me, lcd, network, wireless, aplications... all

---

### Post by TimelessRogue on 2007-04-19
Absolutely flawlessly via the 'apt-get update, change sources.list, apt-get upgrade' method on both an HP n5000 laptop and my home-built desktop (with AMD processor, ATI graphics, Creative sound, Linksys wireless, etc) and the only thing not working is the wireless (a Linksys problem, not Ubuntu).

---

### Post by Old Pink on 2007-04-19
[LIST=1]
[*]Hold alt
[*]Hit F2
[*]Enter:
```
gksudo "update-manager -c -d"
```
[*]It'll tell you Feisty is available. Hit "Upgrade Now"[/LIST]Upgraded to the BETA around a week ago, running final now, flawless/perfect upgrade and no problems since. :D

---

### Post by cas1834 on 2007-04-19
After much pulling of hair and gnashing of teeth, I was finally able to have Beryl up and running almost perfectly.  I then updated to Feisty Beta and lost my Beryl (which I love).  The upgrade went flawlessly and I really liked some of the new stuff in Feisty...the integration of Windows settings and contacts, etc. was especially cool. But I missed Beryl.  Does anyone know, as I am poised with my finger on the Upgrade button again, if I will still be able to use Beryl if I make the new upgrade?
Thanks in advance for any response.

---

### Post by old_geekster on 2007-04-19
I upgraded last Sunday.  It went great.  Beryl is even performing like a champ.  I have had only three updates in the past three days.  Feisty feels rock-solid at this point.

The only component that isn't fully setup is my Logitech Mx700 Duo (wireless Kbd/Mouse) Keyboard.  It has several special keys that I have never been able to configure since moving to Ubuntu.  Some of the problem is I am not proficient with the OS at this point.  When I have a bit more knowledge, I will attempt to configure them.

Welcome, Feisty Fawn!!

Here is the link that I used to setup Beryl correctly:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method)

---

### Post by PartisanEntity on 2007-04-19
> **Old Pink said:**
> [LIST=1]
[*]Hold alt
[*]Hit F2
[*]Enter:
```
gksudo "update-manager -c -d"
```
[*]It'll tell you Feisty is available. Hit "Upgrade Now"[/LIST]Upgraded to the BETA around a week ago, running final now, flawless/perfect upgrade and no problems since. :D

Just out of interest, why not go to System > Administration > Update Manager and clicking on Upgrade ?

---

### Post by kpkeerthi on 2007-04-19
I did.. [http://ubuntuforums.org/showthread.php?t=412790](http://ubuntuforums.org/showthread.php?t=412790)
I think Beryl feels and runs better in Feisty. So far I'm happy. No issues.

---

### Post by cas1834 on 2007-04-19
It's good to see that everything went so well for all of you.  I probably should have told you that I have an ATI XPRESS 200 vid card...that was what gave me the trouble initially getting Beryl/XGL up and running.  Now that I have it, I'm reluctant to lose it and have to start from scratch.  Then again...that's why I love Linux, all the learning while playing.  Here goes nothin'!

---

### Post by jpaint1021 on 2007-04-19
I just updated from Edgy to Feisty using the update manager and it was a piece of cake.  The only hitch was that when opening the update manager from the System --> Admin menus, it didn't display the update as being available.  This was solved by opening it through the terminal, explained elsewhere in this thread.  Otherwise, it went like a champ, and even auto-mounted my windows drive (I run a dual boot).

---

### Post by chakkaradeep on 2007-04-19
Me too in the list of successful upgrades from edgy to feisty !

---

### Post by Calash on 2007-04-19
I had no issues with my upgrade (using update-manager -c -d).

Ran it over night last night and by this morning it was ready to reboot.  Everything is working fine on it, including Beryl.

---

### Post by Old Pink on 2007-04-19
> **PartisanEntity said:**
> Just out of interest, why not go to System > Administration > Update Manager and clicking on Upgrade ?

I always use: gksudo "update-manager -c -d" in order to check for BETA software too (-d) as I get releases before they come out to mess around with. :) 

I just removed the BETA check and posted the remainder, didn't know it worked that simply, never upgraded to a final before. :)

---

### Post by berserker on 2007-04-19
I've upgraded from Hoary to Dapper to Edgy to Feisty without reinstalling.  This was the smoothest upgrade of them all.  No problems except for having to run synaptic and rebooting several times.  Other than that I didn't have to fix anything.  AMAZING!

---

### Post by Michl on 2007-04-24
Did a clean reinstall of Feisty at work -- no problem.  But just tried upgrading via
the upgrade button on the update manager as recommended but I keep getting
this error:

failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/Sources.gz) Sup-process gzip
returned an error code (1)

Not sure what is going on.  Maybe I should just bring the CD home and upgrade from it.  I don't
want to do a clean reinstall at home.

(Yes, do have the appropriate update manager and all security updates are installed.)

Michael

---

### Post by brennydoogles on 2007-04-24
When I tried to upgrade I was unsuccessful. My X broke (but I was able to reconfigure it), and I still am unable to get updates to work in Edgy the way they should (*NOTE* It's finals week and I have not had time to try very hard). If anyone has any suggestions I would love to hear them!!

---

### Post by wersdaluv on 2007-04-24
When I upgraded, I had to uninstall OO.o 2.2 that I installed in Edgy and reinstall it from Feisty's Synaptic. Also, I had to reinstall K3b before I was able to run it again.

I do not know if reinstalling those apps were necessary but reinstalling made them work.

---

### Post by crimesaucer on 2007-04-24
> **Old Pink said:**
> [LIST=1]
[*]Hold alt
[*]Hit F2
[*]Enter:
```
gksudo "update-manager -c -d"
```
[*]It'll tell you Feisty is available. Hit "Upgrade Now"[/LIST]Upgraded to the BETA around a week ago, running final now, flawless/perfect upgrade and no problems since. :D


I did that and it stopped right at the beginning, something to do with my Beryl repository.

So I updated the repositories to Feisty, then used tty to upgrade using the apt-get way in the wiki, and it went really fast.

The only thing that I had to do afterwards was re-install Beryl and restart it in Terminal:

```
sudo apt-get install beryl beryl-manager
```

```
beryl-manager
```

Now everything was perfect like before since all of my configurations and beryl-startup scripts were still installed, plus xfce4.4 is even faster and more stable now. I'm loving xfce4.4!

I have had a little issue with the Windows NTFS drive icon not working on my xubuntu desktop, but the sda1 is mounted in my /media/hda1 file from from the way it had been set to umask 0222 in edgy. 

I think xubuntu has issues with the windows partition drive icons. At least that was the way it was for edgy and dapper. I was hoping it would be fixed.

---

