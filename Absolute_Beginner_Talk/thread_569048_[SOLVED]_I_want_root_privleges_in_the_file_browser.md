---
title: "[SOLVED] I want root privleges in the file browser !"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by larry19l on 2007-10-06
Hi Folks,
I would like root privileges in the file browser !
There is some useless junk in /Examples.
I would like to recover the drive turf.

Secondary issue: where are all these packages and updates going ?
I would like to back them up [to another drive]. This is the SECOND time I'm installing feisty (don't ask:mad:)! So I'm hunting them down but it ain't easy without filenames.

Eye candy department: in WinXP I use a utility called wallpaperchanger.
And that's what it does. I set the interval to about 2 minutes. Best screensaver ever:
I have another drive (usb) that has about 60gig of Sci-Fi Fantasy Art images.

Is there a wallpaperchanger for feisty ?

LBNL: Why is the online documentation not searchable ?
And I still haven't found the section in 'man bash' that lists the
basic commands (for terminal mode) to delete files.
Yes, I know . . .:lolflag:
...We've all been spoiled since the debut of Sweep21 and DC108 for CP/M & MSdos.
And the cheat card(?) for Unix has long since disappeared (all 8 panels of it!)
so I'm lucky I remember ls and cat !

And, how come there is no wine?
[:guitar: I recommend Yellowtail but only the reds, and Little Penguin is good too! Them Aussies make good stuff! And cheap too!)
I found a set of compile/install instructions:
not adequately maintained, so I could not install GrabIt 1.71b or Joost. 
Is there an adequate newsreader ? I'm using Newsbin 5 so I'm gonna check with them
if they have a port. And Xnews too but Xnews limits connections to 4, even if you use GIGAnews (allows 10).

Can anyone recommend a VMware or Parallels type of pkg for WinXP/feisty on
an AMD64 4000+ single-core ? RAM is adequate @ 2gig HD turf ok at 700gig total.
WinXP takes forever to boot. Be nice to be able to switch back and forth...

Now it's on to looking at all the software ...

---

### Post by elliotjreed on 2007-10-06
To get root priviliges in filesystem:

```
gksudo nautilus
```

---

### Post by AlexenderReez on 2007-10-06
i prefer krusader....but it is kde appication...nerveless just
> sudo apt-get install krusader
gksudo krusader

---

### Post by mivo on 2007-10-06
The downloaded packages are in /var/cache/apt/archives.

---

### Post by mgmiller on 2007-10-06
> Secondary issue: where are all these packages and updates going ?
I would like to back them up [to another drive]. This is the SECOND time I'm installing feisty (don't ask)! So I'm hunting them down but it ain't easy without filenames.

Try this for backup and restore of all post installed packages:

backup both your /home and /etc folders. all system settings are stored in the /etc folder. all user settings are stored in hidden files in the user's home folder.  (When viewing the folder in Nautilus hit ctrl h to make them visible)

it's also good to make a list of installed software. you can do this with this command:

```
dpkg --get-selections | grep -v deinstall > /media/backup/installed-software.log
```

This will create a plain text file in /media/backup called installed-software.log
You can view it with the text editor of your choice.

if you really messed up your system and need to do a reinstallation, you can put everything back in place with this command:


```
sudo dpkg --set-selections < /media/backup/installed-software.log
```

Easy, Fun, Ubuntu!  :popcorn:

---

### Post by talby on 2007-10-06
>WinXP I use a utility called wallpaperchanger
"ChangeWallpaper" 
[http://www.gnomefiles.org/app.php?soft_id=938](http://www.gnomefiles.org/app.php?soft_id=938)

>Why is the online documentation not searchable ?
apropos / man -k / man -kr

>how come there is no wine?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_and_run_Wine_.28Open_Source_version_of_CrossOver_Linux.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_and_run_Wine_.28Open_Source_version_of_CrossOver_Linux.29)

>Is there an adequate newsreader ?
I use "Pan" for smaller groups, but once you hit 1M+ headers you're better off sticking w/ newsbin, I think it works great under wine (have not tried in a while...)

---

### Post by NT4usB on 2007-10-06
> **larry19l said:**
> Hi Folks,
I would like root privileges in the file browser !
There is some useless junk in /Examples.
I would like to recover the drive turf.
Use the terminal. ```
cd /to/the/directory/
 sudo rm [filename]
```
cding is not so bad if you remember to use Tab autocomplete. Type cd /h [Tab] and it will complete /home, etc.
Tab twice will show you all options that begin with the letter(s) you typed.
> ...
Eye candy department: in WinXP I use a utility called wallpaperchanger.
And that's what it does. I set the interval to about 2 minutes. Best screensaver ever:
I have another drive (usb) that has about 60gig of Sci-Fi Fantasy Art images.

Is there a wallpaperchanger for feisty ?

System>Preferences>Screensaver
Choose GLSlideshow
> 
LBNL: Why is the online documentation not searchable ?
And I still haven't found the section in 'man bash' that lists the
basic commands (for terminal mode) to delete files.
try```
 apropos[and a keyword: remove, etc...]
``` in a  terminal. 
Don't forget Tab autocomplete since you can never remember how to spell apropos...
>  ...

Did someone say [Yellowtail?]("http://home.pacbell.net/clayt/TZH6_017.jpg")

---

### Post by trak87 on 2007-10-06
The Examples directory is actually a symbolic link in your home directory to another system directory. I think it links to /user/share or something. The point is, all you have to do is delete the symbolic link (~/Examples) in your home directory. You don't need root access to do this. The only reason you'd need root access is to delete the content the symbolic link is pointing to at /usr/share/...

mgmiiller: that's a great tip on restoring a system. Thanks.

---

### Post by mgmiller on 2007-10-06
You're welcome....:guitar:

As far as the wallpaper changer, someone suggested glscreensaver.  This is not what the OP wanted.  I believe he wants his desktop wallpaper to change every x minutes.  The glscreensaver, just puts up different images when the screensaver is active.

AFAIK, gnome doesn't do this.  KDE does.  For gnome, try looking for a program called wallpapoz.

Here is a link to an Ubuntu forum discussion on it:
[http://ubuntuforums.org/showthread.php?t=344639&highlight=wallpapoz]("http://ubuntuforums.org/showthread.php?t=344639&highlight=wallpapoz")

Here is a link to the authors homepage:
[http://wallpapoz.akbarhome.com/]("http://wallpapoz.akbarhome.com/")

Fun, Easy, Ubuntu! :popcorn:

---

### Post by larry19l on 2007-10-06
Many Thanks !!!

---

### Post by NT4usB on 2007-10-06
> **mgmiller said:**
> You're welcome....:guitar:

As far as the wallpaper changer, someone suggested glscreensaver.  This is not what the OP wanted.  I believe he wants his desktop wallpaper to change every x minutes.  The glscreensaver, just puts up different images when the screensaver is active...:

oops... You're right. I misundertook the OP.
I'm not big on eyecandy anyway. Here's the desktop on my [work box]("http://home.pacbell.net/clayt/moz-screenshot-74.jpg")

---

### Post by MarkieB on 2007-10-07
```
~$ sudo dpkg --get-selections | grep -v deinstall > /media/backup/installedsoftware.log
bash: /media/backup/installedsoftware.log: Permission denied

```

---

### Post by dfreer on 2007-10-07
> **larry19l said:**
> Can anyone recommend a VMware or Parallels type of pkg for WinXP/feisty on
an AMD64 4000+ single-core ? RAM is adequate @ 2gig HD turf ok at 700gig total.
WinXP takes forever to boot. Be nice to be able to switch back and forth...


ummm... VMWare.
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#VMWare_Server_.2F_Workstation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#VMWare_Server_.2F_Workstation)

Haven't used virtualbox yet, but I hear it's quite good as well.

---

### Post by MarkieB on 2007-10-11
Although it seems to work perfectly well when I put the backup file on the desktop..

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

---

### Post by dfreer on 2007-10-11
If you don't have a /media/backup/ folder, then it's probably not going to work. If you do, and it's an external USB drive, make sure that you can write to it (folder file permissions need to be set to 755, and NTFS filesystems can only be written to using NTFS3G)

---

### Post by ThrobbingBrain66 on 2007-10-11
```
sudo apt-get install nautilus-gksu
```

This will add an option to the right-click menu that allows you to open a file or folder as root.

---

### Post by drbob07 on 2007-10-11
To get root access I normally just do
gksu nautilus

(Or I suppose Konqueror if you're using Kubuntu)

---

### Post by santy_kushwaha on 2007-10-11
i read tthe question and some other opinion i will suggest that go to the system>administration>loginwindow. and under the security enalbe the administration login and then login as a root and u can do everything from there without any more passwords

---

### Post by mivo on 2007-10-11
> **ThrobbingBrain66 said:**
> ```
sudo apt-get install nautilus-gksu
```

This will add an option to the right-click menu that allows you to open a file or folder as root.

Will it still ask for the root password when you use this option to open a file or a folder as root? (If it doesn't, it's too risky to install for me.)

---

### Post by celticbhoy on 2007-10-11
Yes still requires password.

---

### Post by stchman on 2007-10-11
> **larry19l said:**
> Hi Folks,
I would like root privileges in the file browser !
There is some useless junk in /Examples.
I would like to recover the drive turf.

Secondary issue: where are all these packages and updates going ?
I would like to back them up [to another drive]. This is the SECOND time I'm installing feisty (don't ask:mad:)! So I'm hunting them down but it ain't easy without filenames.

Eye candy department: in WinXP I use a utility called wallpaperchanger.
And that's what it does. I set the interval to about 2 minutes. Best screensaver ever:
I have another drive (usb) that has about 60gig of Sci-Fi Fantasy Art images.

Is there a wallpaperchanger for feisty ?

LBNL: Why is the online documentation not searchable ?
And I still haven't found the section in 'man bash' that lists the
basic commands (for terminal mode) to delete files.
Yes, I know . . .:lolflag:
...We've all been spoiled since the debut of Sweep21 and DC108 for CP/M & MSdos.
And the cheat card(?) for Unix has long since disappeared (all 8 panels of it!)
so I'm lucky I remember ls and cat !

And, how come there is no wine?
[:guitar: I recommend Yellowtail but only the reds, and Little Penguin is good too! Them Aussies make good stuff! And cheap too!)
I found a set of compile/install instructions:
not adequately maintained, so I could not install GrabIt 1.71b or Joost. 
Is there an adequate newsreader ? I'm using Newsbin 5 so I'm gonna check with them
if they have a port. And Xnews too but Xnews limits connections to 4, even if you use GIGAnews (allows 10).

Can anyone recommend a VMware or Parallels type of pkg for WinXP/feisty on
an AMD64 4000+ single-core ? RAM is adequate @ 2gig HD turf ok at 700gig total.
WinXP takes forever to boot. Be nice to be able to switch back and forth...

Now it's on to looking at all the software ...

Using root for graphical programs is not recommended.  You may delete something important by complete accident.  you could also execute a script that could damage your system.  If you need to delete a file or folder that you cannot normally delete use the terminal:

```
sudo rm -r -f <file or folder>
```

---

### Post by larry19l on 2007-12-19
You have all been verrrrrrrrrrry helpful and I've been trying lotsa this stuff !
Learning curves are not the most pleasant of curves but one does progress:
Thank you all for smoothing out some of the bumps !

Now it's time to end this thread, perhaps to start another...

As to that pic of a yellowtail (it was a small one anyway), If raw, I really prefer blue fin.
Just find a better white to wash it down (nah, don't like saki, warm or cold).

As to eyecandy: my universe is a graphic one: photographer, [licensed] projectionist***,
X-ray tech, artist [Watercolor but NR4PT] and [hopefully] soon to be a Frame store owner providing large-format (48") digital printing.
You'll probably find me back here  in the forums on graphics images & software, but not to the exclusion of anything else !

If you want to see the sort of images I like, google: "Richard Powers" or "Hubert de Lartigue"
or Jim Burns
or David Hardy
or Frank Kelly Freas
or Rodney Matthews
or John Berkey
or Brom
or Moebius
or Paolo Serpieri
or the Grand Master: Frank Frazetta

and Sci-Fi or goto the NASA Hubble image gallery

lotsa and lotsa eyecandy !  

No, Sci-Fi didn't start with Star Trek/W.Shatner, Try Hugo Gernsback and the pulp fiction of the 1940's: Edgar Rice Borroughs (Tarzan, John Carter of Mars, Carson on Venus) and Francis W. Nolan's Buck Rogers and don't forget Flash Gordon, Superman, Rocketman and more ... 

next is cube ontopa cube ontopa cube: more space for eyecandy !

(when are we gonna get those quad quad quad cores ? 64 cores: I want it yesterday !)
:lolflag:

***I know where I was 30 years ago (since the debut of Sat.Night.Fever) I was the first New Yorker to see Travolta in a white (polyester?) leisure suit on a dance floor! -> in the screening room on the 30th floor of the Gulf Western Building at Columbus Circle (59th st and Central Park West) ! When it hit theaters, I'd run it almost 20 times (in a week). Now, 30 years later, the music still gives me a headache ! And now Travolta is two of him ! (But so am I ! LOL !)

So let's have fun with our toys, Let the games (and graphics) never end  ! :biggrin:

---

