---
title: "AVG Free Edition for Linux"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2006-02-24
Hiyas

I've recently downloaded AVG Free Edition for linux, but there wasn't an option for Debian. I downloaded the Red Hat RPM option instead and used "alien" on it. I now have a working .deb file. It installs fine and everything else seems to run okay. The only problem i have now is updating. It tells me i don't have permission seeing as i'm not the owner of the file, even if i sudo it.

Running the avgupdate file from the terminal i get this error.

avgupdate: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Can someone shed some light on this for me? It looks like an interesting problem, so i'd like to sort it out for the experience.

Regards
SW

---

### Post by Perfect Storm on 2006-02-24
```
sudo apt-get install libstdc++2.10-glibc2.2
```

Though I havn't any luck running AVG Free Edition for linux.

---

### Post by suRoot on 2006-02-24
You're just missing a package.

Make sure you have universe enabled in apt-get (search around here if you don't know how to) & then run:

```
sudo apt-get install libstdc++2.10-glibc2.2
```

...that should fix the problem.

---

### Post by Stone_Wolf on 2006-02-24
Thanks

That sorted out the problem...sorta. Now when i start avg it tells me it wasn't registered with a valid license number. 

AVG update seems to want to work, but i just need to figure out how to use the switches. 

I'm going to go back to the site and look around for anything mentioning a key. I don't see why i need a key if it's the free edition.

Regards
SW

---

### Post by Perfect Storm on 2006-02-24
Also got stuck where you are, Stone_Wolf. If you find a solution please post it. But I've checked their homepage in vein :-/

You might check this: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by suRoot on 2006-02-24
I think you just need to run the license update script

```
/opt/grisoft/avggui/bin/avggui_update_licinfo.sh
```

then start AVG

```
avggui &
```

---

### Post by Perfect Storm on 2006-02-24
Tried that, but it still ask for registration number which shouldn't be there as it's the free version.

---

### Post by suRoot on 2006-02-24
Got me then... I just ran across their free FAQ, too, and that's all it says to do:

[http://free.grisoft.com/doc/5649/lng/us/tpl/v5](http://free.grisoft.com/doc/5649/lng/us/tpl/v5)

---

### Post by Stone_Wolf on 2006-02-24
Hiyas

I got it working. You have to run "avgscan -register" as root.

But before you do that you have to use

"rpm -qip --scripts your_package.rpm | grep"

your_package.rpm being the file you downloaded.

This'll give you the key you need to enter when you run the avgscan -register.

Slap it in there and it works fine. I still have a problem with permissions when i try update through the gui. Running avgupdate using sudo works fine, it's busy updating as i write this. 

I hope this helps.

Regards
SW

---

### Post by ngms27 on 2006-02-24
The rpm command just brings up 

rpm -qip --scripts /home/ngms27/Desktop/avglinux-7.1-23_free_rh_avi0676.i386.rpm | grep
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

Any ideas?

---

### Post by Perfect Storm on 2006-02-24
try without 
```
| grep
```

worked for me.

---

### Post by Perfect Storm on 2006-02-24
Updated, scanned....I'm not impressed. F-prot is more advanced and works better.

---

### Post by Deathmoon on 2006-10-14
I'm really a noob to Linux and this is my first post on how to get AVG to work.  Between this thread and others I finally put everything together and got AVG working on Ubuntu 6.06...

1.  launch terminal
2.  sudo apt-get install alien
3.  sudo alien -k avg_file_name_here.rpm
4.  this will create the deb package
5.  sudo dpkg -i avg_file_name_here.deb (the file name slightly changed from the rpm file name --- replaced some of the hyphens with underscores)
6.  at this time AVG is installed but not working due to a license file
7.  rpm -qip --scripts avg_file_name_here.rpm
8.  after the command has completed executing scroll up and copy the serial #
9.  sudo avgscan -register
10. paste/type the license number in
11. from there you are all set... ('sudo avggui' to launch the gui)

Please let me know if I did too many steps and if there is an easier way, but this worked and I've got AVG working now.  :-D

---

### Post by fazza on 2006-10-16
cheers D/m that just worked! didn't even need to register - it actually said something like 'free version no code neede'. Thanks :)

---

### Post by Chazthesinger on 2007-02-12
I am a complete and utter Linux beginner, so new I'm not even a newbee !

I am trying to load AVG Free. Downloaded it and it dissapeared somewhere :confused: 
Can you repost the instructions being more explicit? Sorry I know I'm thick but any help is appreciated.
I assume that the insructions are to be entered in "terminal" but just can't get the syntax right.

Help!

---

### Post by Chazthesinger on 2007-02-12
Oh crikey. . .from the fat to the fire.

I've just tried to load mplayer, at least i managed to download it to the desktp ! What do i do now?:confused:

---

### Post by irish_flu on 2007-02-12
The easiest way to download "common" software such as mplayer isn't to download it with your web browser.

The easiest way is to use either "Synaptic Package Manager" or "Add/Remove Programs".

These access what are called "repositories" of software.  

"Add/Remove Programs" is located at the bottom of your "Applications" menu in Gnome.  It's a smallish list of "recommended" or often-used programs.

Synaptic is also easy to use, it's located in the System --> Administration menu.

I suggest looking here;
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

I promise it's pretty easy to use either one, and mplayer is in there.  Installing it using these package-management applications will also automatically get you updates for it.

---

### Post by Chazthesinger on 2007-02-13
Thanks for that, much appreciated. . . I used both the synaptic and terminal ways to load mplayer but although it appears under applications/ sound and video. . when opened it is "Totem" which says "sorry you couldn't open the file ****** but you do not have the correct codec etc etc. I have added to the list of repositories with no joy finding the missing bits.

Oh yeah, and when I added mplayer under synaptic it said re-install ! so it must have tried before?

Any idea what next?

---

### Post by JBA2337 on 2008-04-10
To allow you to update AVG Antivirus using the AVG for Linux Workstation GUI, click on System>Administration>Users and Groups. You should see avg listed as a login name. Click on the Manage Groups button. Scroll down the list until you see avg. Cick on avg and then on Properties. Under Group Members you will see a check box next to your name (or the name you logged in with). Click on the check box next to your name. Scroll down some more, and repeat this procedure if you see any other "avg's". Finally, click on OK, and then close the program. Reboot your computer. Now when you click on the AVG Antivirus Update button, it will update the program. This procedure worked for me.

JBA2337

---

### Post by Helios1276 on 2008-04-10
Dont mean to hijack here but as a noob...I need antivirus on linux?

---

### Post by Tatty on 2008-04-10
> **Helios1276 said:**
> Dont mean to hijack here but as a noob...I need antivirus on linux?

No you dont.  In short, there are no viruses for linux.

There have been less than 100 viruses ever made for linux, most of them were simply made as proof of concept viruses and were never released into the wild.  However, none of these viruses can still affect a modern linux system as they have been patched out of existance.

All any linux virus checker will scan for are windows viruses.

---

### Post by EverettGMartin on 2008-06-28
well there is a way i got the avg update to work because in ubuntu 8.04 hh it says i dont have permission when i click on the update gui button.

- Open Terminal
- Type '**sudo avgupdate -o**'
- From there it will download the updates and anything it needs, and apply them.


Preview

[SIZE="1"]everett@EGM-LNXdesktop:~$ **sudo avgupdate -o**
Preparing to download files from 'http://www.grisoft.cz/softw/70/update/'.
Downloading file: avginfo.ctf          [   7271B]
Downloading file: u7avi13305e.bin      [6194824B]                               
Downloading file: u7iavi15245e.bin     [25133048B]                              
Updating...                                                                     
Online update finished successfully.[/SIZE]

---

### Post by mab55 on 2008-07-06
Thanks this work great!!!!

---

