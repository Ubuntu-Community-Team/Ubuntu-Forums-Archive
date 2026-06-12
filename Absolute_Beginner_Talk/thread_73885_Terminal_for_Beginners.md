---
title: "Terminal for Beginners"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Kyral on 2005-10-10
I've seen time and time again ( and have done it myself ) people give beginners advice that basically is terminal based. Thing is, half the time we forget that to many of these people the Terminal is a scary, unknown thing. So since I have some free time ( yea classes being cancelled! ) I decided that I would write a quick intro to the terminal.

The terminal. Also called "command-line" or Bash (because Bash is the default shell on 90% of distros). Considered an ancient relic of the DOS days by the Windows community, the terminal in Linux is still strong and kicking in the present day. Why? Well because in most cases its just more powerful. You can do tons of things faster in a terminal than you can in a GUI. Its also very customizable. Ask any Guru and chances are they have a huge .bash_aliases file that allows them shorten a string of commands into a few keystrokes, I know I do. But that isn't the aim of this thing. The aim is to give a primer to the terminal.

So how do you fire this thing up? In GNOME its under either accessories or system tools. Clicking on it will bring up a window with a prompt, which looks something like this:

```
kyral@GNUGeneration:~$
```  
Now let me take a second to decipher this, because it does look like code sometimes. The part before the "@" is your username, in my case kyral. The part after it but before the : is your machine name, in my case its my home machine called "GNUGeneration". Last but prolly most importantly is the part between the : and the $. That is your working directory, or in other words what directory you are currently "in". More on that in a sec, but in my case I'm in ~, which is an alias for your home directory. So I'm really in /home/kyral. Keep that in mind, its useful. The $ means you are a user. If you are in a root terminal it will be a #. I don't know why so don't ask me ;P So lets put this together. It means that I am logged in as kyral at the machine called GNUGeneration and I'm in my home directory. Got it? Cool!

Now how do we work this thing? Well my friend its easy. Frankly very easy. I have a directory in my /home called anime. How do I change to it? With the cd (Change Directory) command. Instead of giving an elaborate explination, I'll just show an example and then explain it.

```
kyral@GNUGeneration:~$ cd anime
kyral@GNUGeneration:~/anime$
``` 
Whoa, what just happened? Well the prompt is almost the same, except now it says ~/anime. Thats what I mean by working directory. I changed directory to anime in ~ and the prompt tells me this so I don't forget. Cool huh? Now what if I want to see what is in there? Well its easy as well. Check out the ls (list) command.

```
kyral@GNUGeneration:~/anime$ ls
After War Gundam X                     Mobile Suit Gundam MS IGLOO
Ah! My Goddess                         Mobile Suit Gundam SEED
Ai Yori Aoshi                          Mobile Suit Gundam SEED Destiny
Ai Yori Aoshi Enishi                   Mobile Suit Turn-A Gundam
Azumanga Daioh                         Mobile Suit Victory Gundam
Bleach                                 New Mobile Suit Report Gundam Wing
Cowboy Bebop                           Outlaw Star
DearS                                  Rurouni Kenshin
Full Metal Panic!                      Samurai Champloo
Full Metal Panic Fumoffu and Specials  School Rumble
Full Metal Panic! The Second Raid      S-CRY-ed
Furi Kuri(FLCL)                        SDF Macross
Love Hina                              Speed Grapher
Love Hina Again                        Trigun
Macross 7                              Viewtiful Joe
Macross Zero

``` 
Please withhold comments about me being a fanboy....
Anyway the ls command shows you what is in your working directory. Now do you get the concept? Speaking of working directory, what if you forget? Yah I know the prompt is there, but sometimes you overlook that. Well its easy, its called the pwd(Print Working Directory) command

```
kyral@GNUGeneration:~/anime$ pwd
/home/kyral/anime
``` 
Neat huh? But wait, the prompt and the pwd say different things! Or do they? Remember I said that ~ is an alias to your /home. So they are basically the same things. No matter where you are in the file system, cding to ~ will always bring you back to your /home, so remember that if you get lost. Watch.

```
kyral@GNUGeneration:~/anime$ cd /usr/bin/
kyral@GNUGeneration:/usr/bin$
``` 
Whoa wait a minute, where am I? Well the prompt tells me I'm in /usr/bin. Now I know where that is, but you may not. So how do you get back? You may have guessed it, but I'm gonna show you anyway.

```
kyral@GNUGeneration:/usr/bin$ cd ~
kyral@GNUGeneration:~$ pwd
/home/kyral
``` 
See? Back at /home. That reminds me, there are two ways to specify where you want to go. You can specify a relative location, or an absolute one. Yah, confusing. But wait! I shall explain. Remember when I cd'd to anime? That was relative to my current working directory. anime was a directory in my working directory, even though its really /home/kyral/anime, but the shell knew where I was and just sent me there. Now when I changed to /usr/bin, it was outside my home, so I had to use an absolute location (path is frequently used in place of location BTW) notice the leading /. That tells the terminal to start looking at the "root" of the filesystem (not to be confused with the superuser Root). Maybe this will clear it up..

```
kyral@GNUGeneration:~$ cd /
kyral@GNUGeneration:/$ ls
anime  cdrom        etc     initrd.img  media  proc  srv  usr
bin    debootstrap  home    lib         mnt    root  sys  var
boot   dev          initrd  lost+found  opt    sbin  tmp  vmlinuz

``` 
Welcome to the base of your filesystem. The location of every other file on your Linux computer is defined in relation to this. Yes there is an anime there, but thats because I have another HD mounted there and symlinked into my ~/anime (Symlinks and mounting are another topic, this is terminal time!). Anyway back to home! Do I really need an example here? :D

Now some final words before we jump to copying and moving files and whatnot. There are another pair of alias I forgot to mention. ".." refers to the directory directly "above" the working directory.

```
kyral@GNUGeneration:~/anime$ cd ..
kyral@GNUGeneration:~$
``` 
See what happened? I was in ~/anime and I jumped "up" one level. Very nice and useful if you happen to be in one directory and want to change to another thats in the same directory above you. Like..

```
kyral@GNUGeneration:~/anime$ cd ../workspace
kyral@GNUGeneration:~/workspace$

``` 
See that? I changed from /home/kyral/anime to /home/kyral/workspace. Also notice that its an example of a relative location. Relative to ~/anime, ~/workspace is up one. Get it? Cool.

Last alias. "." refers to your working directory. Now you may be thinking why do I need that? Well, if you are asked to run an executable, you are going to have to specify the absolute path to it, otherwise its going to go looking in /usr/bin, /usr/sbin, and a bunch of other predefined places. By sticking a ./ infront of the filename, you just did give it the absolute path. Oh, this shouldn't be confused with files and dirs that are named with a . in front, like .bash_aliases. A . in front of the file name means its hidden and won't show up with a normal ls command. You have to use the ls -a command for that.

Well this part is done, ON TO PART TWO!

Quick Links to the Guide: 
[Part 2: Playing with Files, Tab Completion, Bash Aliases]("http://www.ubuntuforums.org/showpost.php?p=399109&postcount=4")
[Part 3: Advanced File Ops]("http://www.ubuntuforums.org/showpost.php?p=401159&postcount=16")
[Part 4: Harnessing the Power of Apt]("http://www.ubuntuforums.org/showpost.php?p=468342&postcount=33")
[Part 5: Permissions]("http://www.ubuntuforums.org/showpost.php?p=502685&postcount=48")
__[Part 6: Input/Output Redirection and a bit of Sed]("http://www.ubuntuforums.org/showpost.php?p=609651&postcount=62")

---

### Post by frodon on 2005-10-10
I like your anime directory ;)

---

### Post by Strangerdave on 2005-10-10
Hey man, thanks for the info.  Being new to all this, the terminal is a bit of a scary thing.  I know for me, one of the biggest problems in my understanding is what can be done with the terminal and keeping all the commands either in memory or written down.

-SD-

---

### Post by Kyral on 2005-10-10
Terminal for Beginners: PART TWO: File fun!

Well, you know how to move about in the terminal, and hopefully it isn't as scary anymore. But all you know how to do is move around. Thats no fun! I also told you that the terminal can be very powerful, but again I haven't shown it. Well file operations are very fun in the terminal. And powerful as well. Here we go again!

I assume you remember how to naviagate, so I won't go over that again. There are three basic commands for file operations. cp (Copy), mv (Move), and rm (Remove, basically Delete). cp and mv function pretty much the same way, so I'll cover those first.

Okay I'm at home. Time to ls.

```
kyral@GNUGeneration:~$ ls
14560-firefox-thunderbird.tar.gz
19506-pinux's-tux-cursors-theme-0.3-cur.tar.bz2
2005-08-03--10.05.26
2005-08-03--10.07.23
2005-09-25--20.15.58
20178-Ambidexter.Silver.tar.gz
ABC Exams
anime
Crystalcursors.tar.bz2
cs142
DarkFirePic.png
debpacks
Desktop
document.png
ffmpeg-0.4.8-2.rh80.dag.i386.rpm
ffmpeg_0.4.8-3_i386.deb
Final Fantasy 3.zip
finddeps.sh
firefox-thunderbird
flash
freenx-0.4.2.tar.gz
GDM-InThisWorld.tar.bz2
gftp_2.0.18-1_all.deb
gftp-common_2.0.18-1_i386.deb
gftp-gtk_2.0.18-1_i386.deb
gftp-text_2.0.18-1_i386.deb
gnome-clipboard-daemon-1.0.bin.tar.bz2
GNOME-GNOMEInSilk_1280x1024.png
hallelujah.mp3
imacgirl_v3_1280x1024.jpg
is400
Jeko_xchat.png
keitaroanimeICON.jpg
keitaroanime.jpg
Manga
MCity-Aero-ng-default-1.1.tar.gz
mozilla-firefox.png
mozilla-thunderbird.xpm
mygraph.php
MyMusic
NVIDIA-Linux-x86-1.0-7667-pkg1.run
ONR_Meeting_10052005.doc
Oral Presentation Proposal.abw
Parallel_Dimensions.jpg
pi
pics_Full_Metal_Panic_Full_Metal_Panic_fmetalp00.jpg
PI.DAT
Presentation Proposal.abw
programs_sourcecode
public.key
Purposed ITL Build Software List.pdf
q2pres2day2.doc
Readme.txt
Resume.odt
Screenshot-1.png
Screenshot.png
sdsf.txt
Sealab 2021 - 101 - 20021008 - Radio Free Sealab.avi
Splash-GNOMEInSilkEvolving2Blurred.png
Splash-Linux_splash.png
StepMania-3.9-rc3
StepMania-3.9-rc3-linux.tar
super_pi
super_pi.tar
System_Stats_3.0
System_Stats_3.0.tar
The_Calling_-_Anime_Wallpaper.jpg
thunderbird_icon2.png
torrents
TransGaming_Drive
UbuntuCodeofConduct-1.0.txt
UbuntuCodeofConduct-1.0.txt.asc
ubuntu-logo.png
Ubuntu-tan_01-1280x1024.jpg
ut2004
web_sketch.xls
wget-log
wget-log.1
workspace
```

Yah I have a lot of stuff here, but then again its mounted on a 285 GB partition, so its not like I'm strapped. But I can clean it out. So lets play with those two screenshot files I have laying around from when I uploaded them to the UbuntuForums Gallery.

Copy time!

The syntax for cp is 

```
cp [options] <location of file> <where you want the copy to be made>
``` 

Now the locations can either be relative or absolute paths (remember those?) . Now wait a second? What are "options". Well those are optional! (*groan I can't believe I pulled that*). No those are options that affect how cp goes about its business and are prefaced with a "-". Common options are -i (interactive, it asks you to confirm every action), -r (Recurses into directories, means it basically grabs everything in there. Needed for copying directories), -v (Verbose, tells you everything its doing). You stick'em where I put [options] in the syntax. Well, enough talking. You want an example? Good 'cause I was getting bored. Lets copy Screenshot.png to Screenshot2.png

```
kyral@GNUGeneration:~$ cp -v Screenshot.png Screenshot2.png
`Screenshot.png' -> `Screenshot2.png'

```

Noticed I used the -v option. If I hadn't the second line would not have showed up. It just told me that it copied Screenshot.png to Screenshot2.png. A ls will confirm this
```

kyral@GNUGeneration:~$ ls
14560-firefox-thunderbird.tar.gz
19506-pinux's-tux-cursors-theme-0.3-cur.tar.bz2
2005-08-03--10.05.26
2005-08-03--10.07.23
2005-09-25--20.15.58
20178-Ambidexter.Silver.tar.gz
ABC Exams
anime
Crystalcursors.tar.bz2
cs142
DarkFirePic.png
debpacks
Desktop
document.png
ffmpeg-0.4.8-2.rh80.dag.i386.rpm
ffmpeg_0.4.8-3_i386.deb
Final Fantasy 3.zip
finddeps.sh
firefox-thunderbird
flash
freenx-0.4.2.tar.gz
GDM-InThisWorld.tar.bz2
gftp_2.0.18-1_all.deb
gftp-common_2.0.18-1_i386.deb
gftp-gtk_2.0.18-1_i386.deb
gftp-text_2.0.18-1_i386.deb
gnome-clipboard-daemon-1.0.bin.tar.bz2
GNOME-GNOMEInSilk_1280x1024.png
hallelujah.mp3
imacgirl_v3_1280x1024.jpg
is400
Jeko_xchat.png
keitaroanimeICON.jpg
keitaroanime.jpg
Manga
MCity-Aero-ng-default-1.1.tar.gz
mozilla-firefox.png
mozilla-thunderbird.xpm
mygraph.php
MyMusic
NVIDIA-Linux-x86-1.0-7667-pkg1.run
ONR_Meeting_10052005.doc
Oral Presentation Proposal.abw
Parallel_Dimensions.jpg
pi
pics_Full_Metal_Panic_Full_Metal_Panic_fmetalp00.jpg
PI.DAT
Presentation Proposal.abw
programs_sourcecode
public.key
Purposed ITL Build Software List.pdf
q2pres2day2.doc
Readme.txt
Resume.odt
Screenshot-1.png
Screenshot2.png
Screenshot.png
sdsf.txt
Sealab 2021 - 101 - 20021008 - Radio Free Sealab.avi
Splash-GNOMEInSilkEvolving2Blurred.png
Splash-Linux_splash.png
StepMania-3.9-rc3
StepMania-3.9-rc3-linux.tar
super_pi
super_pi.tar
System_Stats_3.0
System_Stats_3.0.tar
The_Calling_-_Anime_Wallpaper.jpg
thunderbird_icon2.png
torrents
TransGaming_Drive
UbuntuCodeofConduct-1.0.txt
UbuntuCodeofConduct-1.0.txt.asc
ubuntu-logo.png
Ubuntu-tan_01-1280x1024.jpg
ut2004
web_sketch.xls
wget-log
wget-log.1
workspace
```

Its there! Now lets remove it. rm uses syntax like this

```
rm [options] <path to file>
```

Again options are to be found. Practically EVERY command has options. Anyway, common options for rm are, -i (Interactive, same as cp, more important in this case), -v (same as cp), -f (force, make it delete. Needed for directories), -r (Recurse, again same as cp). Now look at those options and think about something people tell you about not running as root. Guess what THIS command would do (DON'T DO IT!) if you ran it as root.

```
rm -rf /
```

Yah, kiss your system goodbye, if you didn't hit CTRL+C fast enough. CTRL+C kills any command in progress and brings you back to the prompt. Anyway lets get rid of that screenshot copy.

```
kyral@GNUGeneration:~$ rm -v Screenshot2.png
rm: remove regular file `Screenshot2.png'? y
removed `Screenshot2.png'

```

Wait, it went interactive. Well thats because I overrode rm's default behavior in my alias' file so it always goes interactive unless I use -f. Nifty safeguard ;P

Now for mv. Again mv behaves just like cp, but it moves the files instead of copy. It also renames them. Yah what? It RENAMES? Think about it. When you rename you basically move the file to one of a different name. Oh I forgot the syntax.

```
mv [options] <location of file> <place where you want to put it>
```

It looks like cp! Thats because its almost the same thing. It has most of cp's options (-i, -v) and it also has rm's -f option. And they work the same way! Example time again! This time rename!

```
kyral@GNUGeneration:~$ mv -v Screenshot-1.png Screenshot2.png
`Screenshot-1.png' -> `Screenshot2.png'
```

It was renamed. Coooool. This means that the file known as Screenshot-1.png is now called Screenshot2.png.

Keep in mind you can also do this with directories, but chances are you'll need to use the -r option if you are using rm and cp.

Now on to a couple other things. I have been keeping a really awesome terminal secret from you, one that makes the terminal really powerful. Its called tab completetion. Now what is that?! Well, if you just type out the first few characters of a file or command or directory and hit tab, the terminal will try to complete the name for you. If its obvious what you want it will instantly complete it for you, saving you a load of typing. If its not, either type a few more characters and try again, OR hit tab once more and it will call up a list of possible completions. Keep in mind for files it will only work for whats in the path you are typing. Confusing. Yah I didn't word it good. Example time.

Okay I'm trying to get to /etc/apt/ from ~. So I start typing cd /e and hit tab. Well, from / there is only one thing that starts with e, /etc, so it would fill in. Now I have cd /etc/. I add a to get cd /etc/a and hit tab. Ooops, That isn't unique enough. There must be more than one thing in /etc that starts with a. So I hit tab again. Behold

```
kyral@GNUGeneration:~$ cd /etc/a
acpi/         adjtime       alsa/         anacrontab    apt/
adduser.conf  aliases       alternatives/ apm/          at.deny
kyral@GNUGeneration:~$ cd /etc/a

```

Notice that on the tab complete list directories are shown by having a trailing "/" Also keep in mind that I haven't hit return yet to enter the command. So it looks like I have to finish and type "pt" to get to /etc/apt. So see what I mean? When I tried to tab complete /etc/a it only looked in /etc for possible completions. Keep it in mind. And tab completion works with 99% of commands in the terminal for filenames. It also works with commands. Watch.

```
kyral@GNUGeneration:~$ ca
caesar         calibrate_ppa  canfield       cardinfo       cat
cal            caller         captoinfo      cardmgr        catchsegv
calendar       cancel         cardctl        case           catman
```

I typed in ca and hit tab. It gave me all the commands that start with ca. Nice!

Okay there is one more trick. You wanna see what a file contains? There is a command for that! Assuming you have read permissions, you can do it! (Permissions are another thing entirely). Remember I mentioned something called aliases? Well, I have a file that defines them. You wanna see it? The cat command is your friend.

```
kyral@GNUGeneration:~$ cat .bash_aliases
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
#alias ls='ls -Cha --color=auto'
alias df="df -h"
alias h=history
alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias aptsource='sudo gedit /etc/apt/sources.list'
alias aptUI='sudo apt-get update && sudo apt-get dist-upgrade'
alias aptI='sudo apt-get install'
alias aptR='sudo apt-get remove'
alias aptS='apt-cache search'
alias aptSh='apt-cache show'
alias debI='sudo dpkg -i'
alias sourcebuild='sudo apt-get source -b'
alias depbuild='sudo apt-get build-dep'

```

Cool huh? It will display ANYTHING! Even stuff that isn't text. Case in point...

Well there isn't a case in point because when I did it on a png a bunch of nonsense characters flew past and messed up my terminal. 

Last thing. You see those sudo commands? Sudo is how we do things in Ubuntu. It grants you Root power for the command that follows it, and then it puts you back as your normal login. Use it, love it.

---

### Post by Kapre on 2005-10-10
Kyral - thanks for this very informative info. Can we make this a sticky and also place this in the index of HOW TOs (paging mods)?

K

---

### Post by KeithO on 2005-10-10
thanks for the great write up.

---

### Post by BLTicklemonster on 2005-10-10
This needs to be stickied. Great Job, Kyral! For all us newbies, I say THANK YOU. :KS

---

### Post by Kyral on 2005-10-10
[quote=BLTicklemonster]This needs to be stickied. Great Job, Kyral! For all us newbies, I say THANK YOU. :KS[/quote]

Actually my experiance with your thread led me to make this...

---

### Post by BLTicklemonster on 2005-10-10
I know, lol. Thanks for doing this!!!

---

### Post by Kyral on 2005-10-10
I'll do a Part 3 if there is anything else general like symlinks, which are REALLY cool, or stuff specific to Bash. Actually....I have an idea. I'll put it out after I am done with homework and whatnot.

Preview of Part 3:

- Advanced File Ops (Mkdir and Symlinks!)
- Bourne Again Fun (I can hear the groans from the experianced people with this one)
- Aliases

---

### Post by simple1 on 2005-10-10
I just want to thank you.
This is an excellent example of the finest form of - posting.
thanks

---

### Post by Kyral on 2005-10-10
Can we sticky this thing?

---

### Post by Kapre on 2005-10-10
[QUOTE=Kyral]Can we sticky this thing?[/QUOTE]

I already asked earlier and now rated it so that it will catch the eye of the mods. Again, great info.
:KS 
K

---

### Post by matthew on 2005-10-10
kyral: good job, man!

---

### Post by benplaut on 2005-10-10
i've been using linux for half a year and i didn't know some of that stuff :???: 

you might want to add something in Part 3 (or whatever part) about executing programs from the shell, most people don't realize that clicking a link is just typig the command into a shell you don't see...

in advanced file management, make sure you include file permissions, chmod, etc ;)

<<edit>>

new smiley! :KS

---

### Post by Kyral on 2005-10-11
Terminal For Beginners

[B]PART 3.1
Advanced File Ops!

[/B]Welcome to another edition of Terminal For Beginners. By now you should know the basics of moving around and basic file operations. I also hope that you are beginning to realize why us Gurus love the terminal. In this edition I will cover Advanced File Ops. Fun stuff that allows you gain so much power over your filesystem and shows you the real power under the hood of the terminal. So fire up the terminal, here we go

[I]mkdir

[/I]This one is pretty basic, its more like something I forgot to mention in Part 2. Mkdir, well, makes directories. Watch

```
kyral@GNUGeneration:~/torrents$ ls
[BakaKozou]Full_Metal_Panic_TSR_-_07_[77801E7A].avi.torrent
[H-S]_Final_Fantasy_VII_-_Advent_Children_[8DC34783].avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 44.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 45.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 46.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 47.avi.torrent

``` 
As you can see I'm sitting in my torrents directory. What if I wanted to make a directory to store my Gundam SEED Destiny torrents? Easy.

```
kyral@GNUGeneration:~/torrents$ mkdir Gundam\ SEED\ Destiny
kyral@GNUGeneration:~/torrents$ ls
[BakaKozou]Full_Metal_Panic_TSR_-_07_[77801E7A].avi.torrent
Gundam SEED Destiny
[H-S]_Final_Fantasy_VII_-_Advent_Children_[8DC34783].avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 44.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 45.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 46.avi.torrent
[SEED-Fansubs] Gundam SEED Destiny - 47.avi.torrent

``` 
See? Its there ready and waiting. Ignore the fact that in order to get a space I needed to escape it with a "\". We will get to escaping things later, promise!

[I]Symbolic Links (Symlinks)

[/I]Symlinks are cool. They are basically aliases to different parts of the filesystem. Again an example shows the way.

```
kyral@GNUGeneration:~/anime$ ls -lah
total 16K
drwxr-xr-x   9 kyral kyral 1.2K 2005-08-21 11:07 .
drwxr-xr-x  86 kyral kyral 6.4K 2005-10-10 22:59 ..
lrwxrwxrwx   1 kyral kyral   26 2005-07-26 13:06 After War Gundam X -> /anime/After War Gundam X/
lrwxrwxrwx   1 kyral kyral   22 2005-07-26 13:07 Ah! My Goddess -> /anime/Ah! My Goddess/
drwxr-xr-x   2 kyral kyral 1.6K 2005-08-15 10:16 Ai Yori Aoshi
drwxr-xr-x   2 kyral kyral 1.1K 2005-08-15 10:17 Ai Yori Aoshi Enishi
drwxr-xr-x   2 kyral kyral 1.2K 2005-08-08 00:29 Azumanga Daioh
drwxr-xr-x   2 kyral kyral 2.5K 2005-08-20 20:41 Bleach
lrwxrwxrwx   1 kyral kyral   20 2005-07-26 13:07 Cowboy Bebop -> /anime/Cowboy Bebop/
lrwxrwxrwx   1 kyral kyral   13 2005-08-07 10:16 DearS -> /anime/DearS/
lrwxrwxrwx   1 kyral kyral   25 2005-07-26 13:08 Full Metal Panic! -> /anime/Full Metal Panic!/
lrwxrwxrwx   1 kyral kyral   45 2005-07-26 13:09 Full Metal Panic Fumoffu and Specials -> /anime/Full Metal Panic Fumoffu and Specials/
lrwxrwxrwx   1 kyral kyral   41 2005-07-27 15:47 Full Metal Panic! The Second Raid -> /anime/Full Metal Panic! The Second Raid/
lrwxrwxrwx   1 kyral kyral   23 2005-07-26 13:11 Furi Kuri(FLCL) -> /anime/Furi Kuri(FLCL)/
lrwxrwxrwx   1 kyral kyral   17 2005-07-26 13:12 Love Hina -> /anime/Love Hina/
lrwxrwxrwx   1 kyral kyral   23 2005-08-18 15:51 Love Hina Again -> /anime/Love Hina Again/
lrwxrwxrwx   1 kyral kyral   17 2005-07-26 13:12 Macross 7 -> /anime/Macross 7/
drwxr-xr-x   2 kyral kyral  456 2005-09-18 11:52 Macross Zero
lrwxrwxrwx   1 kyral kyral   35 2005-07-26 13:13 Mobile Suit Gundam MS IGLOO -> /anime/Mobile Suit Gundam MS IGLOO/
lrwxrwxrwx   1 kyral kyral   31 2005-07-26 13:13 Mobile Suit Gundam SEED -> /anime/Mobile Suit Gundam SEED/
lrwxrwxrwx   1 kyral kyral   39 2005-07-26 13:20 Mobile Suit Gundam SEED Destiny -> /anime/Mobile Suit Gundam SEED Destiny/
lrwxrwxrwx   1 kyral kyral   33 2005-07-26 13:20 Mobile Suit Turn-A Gundam -> /anime/Mobile Suit Turn-A Gundam/
lrwxrwxrwx   1 kyral kyral   34 2005-07-26 13:23 Mobile Suit Victory Gundam -> /anime/Mobile Suit Victory Gundam/
lrwxrwxrwx   1 kyral kyral   42 2005-07-26 13:24 New Mobile Suit Report Gundam Wing -> /anime/New Mobile Suit Report Gundam Wing/
lrwxrwxrwx   1 kyral kyral   19 2005-07-26 13:24 Outlaw Star -> /anime/Outlaw Star/
lrwxrwxrwx   1 kyral kyral   23 2005-07-26 13:25 Rurouni Kenshin -> /anime/Rurouni Kenshin/
lrwxrwxrwx   1 kyral kyral   24 2005-07-26 13:25 Samurai Champloo -> /anime/Samurai Champloo/
lrwxrwxrwx   1 kyral kyral   21 2005-07-26 13:25 School Rumble -> /anime/School Rumble/
lrwxrwxrwx   1 kyral kyral   16 2005-07-26 13:26 S-CRY-ed -> /anime/S-CRY-ed/
drwxr-xr-x   2 kyral kyral 2.1K 2005-08-16 10:13 SDF Macross
drwxr-xr-x   2 kyral kyral 1008 2005-08-05 17:25 Speed Grapher
lrwxrwxrwx   1 kyral kyral   14 2005-07-26 13:26 Trigun -> /anime/Trigun/
lrwxrwxrwx   1 kyral kyral   21 2005-07-26 13:26 Viewtiful Joe -> /anime/Viewtiful Joe/

``` 
Yah a lot of stuff, but pay attention to the entries that have -> in them. Those are Symlinks. Notice that they point to places in /anime (NOT /home/kyral/anime). Lets try to cd there and see what happens.

```
kyral@GNUGeneration:~/anime$ cd After\ War\ Gundam\ X
kyral@GNUGeneration:~/anime/After War Gundam X$ pwd
/home/kyral/anime/After War Gundam X
``` 
Whoa wait a second, didn't I just suggest that I would end up in /anime if I cd'd there? Well yes and no. I AM currently in /anime/After War Gundam X, but because of the symlink, I'm in /home/kyral/anime/After War Gundam X. They are one and the same, but its not a copy. The files in the directory are on the /anime hard drive. But I can delete the symlink /home/kyral/anime/After War Gundam X without deleting the directory on /anime. 

Couple of Examples are needed.

Watch. I'm going to ls both /home/kyral/anime/After War Gundam X and /anime/After War Gundam X
```

kyral@GNUGeneration:~/anime$ ls After\ War\ Gundam\ X
[Hero Legends] Gundam X 01v2.avi  [Hero Legends] Gundam X 20v2.avi
[Hero Legends] Gundam X 02v2.avi  [Hero Legends] Gundam X 21v2.avi
[Hero Legends] Gundam X 03v2.avi  [Hero Legends] Gundam X 22v2.avi
[Hero Legends] Gundam X 04v2.avi  [Hero Legends] Gundam X 23v2.avi
[Hero Legends] Gundam X 05v2.avi  [Hero Legends] Gundam X 24v2.avi
[Hero Legends] Gundam X 06v2.avi  [Hero Legends] Gundam X 25v2.avi
[Hero Legends] Gundam X 07v2.avi  [Hero Legends] Gundam X 26v2.avi
[Hero Legends] Gundam X 08v2.avi  [Hero Legends] Gundam X 28v2.avi
[Hero Legends] Gundam X 09v2.avi  [Hero Legends] Gundam X 29v2.avi
[Hero Legends] Gundam X 10v2.avi  [Hero Legends] Gundam X 30v2.avi
[Hero Legends] Gundam X 11v2.avi  [Hero Legends] Gundam X 31v2.avi
[Hero Legends] Gundam X 12v2.avi  [Hero Legends] Gundam X 32v2.avi
[Hero Legends] Gundam X 13v2.avi  [Hero Legends] Gundam X 33v2.avi
[Hero Legends] Gundam X 14v2.avi  [Hero Legends] Gundam X 34v2.avi
[Hero Legends] Gundam X 15v2.avi  [Hero Legends] Gundam X 35v2.avi
[Hero Legends] Gundam X 16v2.avi  [Hero Legends] Gundam X 36v2.avi
[Hero Legends] Gundam X 17v2.avi  [Hero Legends] Gundam X 37v2.avi
[Hero Legends] Gundam X 18v2.avi  [Hero Legends] Gundam X 38v2.avi
[Hero Legends] Gundam X 19v2.avi  [Hero Legends] Gundam X 39v2.avi
``` 
```
kyral@GNUGeneration:~/anime$ ls /anime/After\ War\ Gundam\ X/
[Hero Legends] Gundam X 01v2.avi  [Hero Legends] Gundam X 20v2.avi
[Hero Legends] Gundam X 02v2.avi  [Hero Legends] Gundam X 21v2.avi
[Hero Legends] Gundam X 03v2.avi  [Hero Legends] Gundam X 22v2.avi
[Hero Legends] Gundam X 04v2.avi  [Hero Legends] Gundam X 23v2.avi
[Hero Legends] Gundam X 05v2.avi  [Hero Legends] Gundam X 24v2.avi
[Hero Legends] Gundam X 06v2.avi  [Hero Legends] Gundam X 25v2.avi
[Hero Legends] Gundam X 07v2.avi  [Hero Legends] Gundam X 26v2.avi
[Hero Legends] Gundam X 08v2.avi  [Hero Legends] Gundam X 28v2.avi
[Hero Legends] Gundam X 09v2.avi  [Hero Legends] Gundam X 29v2.avi
[Hero Legends] Gundam X 10v2.avi  [Hero Legends] Gundam X 30v2.avi
[Hero Legends] Gundam X 11v2.avi  [Hero Legends] Gundam X 31v2.avi
[Hero Legends] Gundam X 12v2.avi  [Hero Legends] Gundam X 32v2.avi
[Hero Legends] Gundam X 13v2.avi  [Hero Legends] Gundam X 33v2.avi
[Hero Legends] Gundam X 14v2.avi  [Hero Legends] Gundam X 34v2.avi
[Hero Legends] Gundam X 15v2.avi  [Hero Legends] Gundam X 35v2.avi
[Hero Legends] Gundam X 16v2.avi  [Hero Legends] Gundam X 36v2.avi
[Hero Legends] Gundam X 17v2.avi  [Hero Legends] Gundam X 37v2.avi
[Hero Legends] Gundam X 18v2.avi  [Hero Legends] Gundam X 38v2.avi
[Hero Legends] Gundam X 19v2.avi  [Hero Legends] Gundam X 39v2.avi
``` 
Well no surprise I've been telling you this would happen. But watch what happens when I delete the symlink /home/kyral/anime/After War Gundam X

```
kyral@GNUGeneration:~/anime$ rm After\ War\ Gundam\ X
rm: remove symbolic link `After War Gundam X'? y
kyral@GNUGeneration:~/anime$ ls
Ah! My Goddess                         Mobile Suit Gundam MS IGLOO
Ai Yori Aoshi                          Mobile Suit Gundam SEED
Ai Yori Aoshi Enishi                   Mobile Suit Gundam SEED Destiny
Azumanga Daioh                         Mobile Suit Turn-A Gundam
Bleach                                 Mobile Suit Victory Gundam
Cowboy Bebop                           New Mobile Suit Report Gundam Wing
DearS                                  Outlaw Star
Full Metal Panic!                      Rurouni Kenshin
Full Metal Panic Fumoffu and Specials  Samurai Champloo
Full Metal Panic! The Second Raid      School Rumble
Furi Kuri(FLCL)                        S-CRY-ed
Love Hina                              SDF Macross
Love Hina Again                        Speed Grapher
Macross 7                              Trigun
Macross Zero                           Viewtiful Joe
``` 
Its gone! Crap! What did I do! Wait..it was just a symlink! The data is intact! Don't believe me? Watch

```
kyral@GNUGeneration:~/anime$ ls /anime/After\ War\ Gundam\ X/
[Hero Legends] Gundam X 01v2.avi  [Hero Legends] Gundam X 20v2.avi
[Hero Legends] Gundam X 02v2.avi  [Hero Legends] Gundam X 21v2.avi
[Hero Legends] Gundam X 03v2.avi  [Hero Legends] Gundam X 22v2.avi
[Hero Legends] Gundam X 04v2.avi  [Hero Legends] Gundam X 23v2.avi
[Hero Legends] Gundam X 05v2.avi  [Hero Legends] Gundam X 24v2.avi
[Hero Legends] Gundam X 06v2.avi  [Hero Legends] Gundam X 25v2.avi
[Hero Legends] Gundam X 07v2.avi  [Hero Legends] Gundam X 26v2.avi
[Hero Legends] Gundam X 08v2.avi  [Hero Legends] Gundam X 28v2.avi
[Hero Legends] Gundam X 09v2.avi  [Hero Legends] Gundam X 29v2.avi
[Hero Legends] Gundam X 10v2.avi  [Hero Legends] Gundam X 30v2.avi
[Hero Legends] Gundam X 11v2.avi  [Hero Legends] Gundam X 31v2.avi
[Hero Legends] Gundam X 12v2.avi  [Hero Legends] Gundam X 32v2.avi
[Hero Legends] Gundam X 13v2.avi  [Hero Legends] Gundam X 33v2.avi
[Hero Legends] Gundam X 14v2.avi  [Hero Legends] Gundam X 34v2.avi
[Hero Legends] Gundam X 15v2.avi  [Hero Legends] Gundam X 35v2.avi
[Hero Legends] Gundam X 16v2.avi  [Hero Legends] Gundam X 36v2.avi
[Hero Legends] Gundam X 17v2.avi  [Hero Legends] Gundam X 37v2.avi
[Hero Legends] Gundam X 18v2.avi  [Hero Legends] Gundam X 38v2.avi
[Hero Legends] Gundam X 19v2.avi  [Hero Legends] Gundam X 39v2.avi
``` 
Safe and sound! Cool dontcha think?

Now lets put it back. The ln command allows us to make links, both hard and symbolic. Hard links are an exact copy of a file and are rather obsolete by now, but its still ln's default behavior, so we have to add the -s option to ln. Enough talking, lets do it!

```
kyral@GNUGeneration:~/anime$ ln -s /anime/After\ War\ Gundam\ X/ After\ War\ Gundam\ X
kyral@GNUGeneration:~/anime$ ls
After War Gundam X                     Mobile Suit Gundam MS IGLOO
Ah! My Goddess                         Mobile Suit Gundam SEED
Ai Yori Aoshi                          Mobile Suit Gundam SEED Destiny
Ai Yori Aoshi Enishi                   Mobile Suit Turn-A Gundam
Azumanga Daioh                         Mobile Suit Victory Gundam
Bleach                                 New Mobile Suit Report Gundam Wing
Cowboy Bebop                           Outlaw Star
DearS                                  Rurouni Kenshin
Full Metal Panic!                      Samurai Champloo
Full Metal Panic Fumoffu and Specials  School Rumble
Full Metal Panic! The Second Raid      S-CRY-ed
Furi Kuri(FLCL)                        SDF Macross
Love Hina                              Speed Grapher
Love Hina Again                        Trigun
Macross 7                              Viewtiful Joe
Macross Zero

```

Very cool. You can also symlink files as well :D

I think I only have enough time for one more topic before I have class so I'll make it a short one.

*Escape Sequences*

Programmers will be familier with this one. You noticed that in order to make a space I needed to type "\ ". Thats because normally a space is a separator in files, and the filename would end if I didn't escape it. To escape a character, place a \ in front. Now that means that if you actually want to print a \, you need to escape it, so it would be \\. Wierd huh? Characters that need to be escaped, off the top of my head, are " ' (space) and \. This is another area where TabComplete rules. If you try to tab complete something that has escaped characters, it will automatically escape them for you when it completes the name! I told you it rocked :D

Anyway thats it for now, I have class. Look for Part 3.2 sometime this afternoon (EST that is)

---

### Post by KeithO on 2005-10-11
I gave this a 5 star rating and a courteous bump to get stickied!

Thanks so much for this info.

---

### Post by BLTicklemonster on 2005-10-11
[QUOTE=Kyral]

Anyway thats it for now, I have class. [/QUOTE]

Pray tell it's not Elementary School?

:rolleyes:

---

### Post by Kyral on 2005-10-11
College ;P

---

### Post by qiezi! on 2005-10-11
What a ripper thread! Thanks Kyral, your info on aliases was great and now I _actually_ understand how symbolic links work, not just how to enter one in when a HOWTO says to.

---

### Post by Kyral on 2005-10-11
Wait until tomarrow for more. Tonight I'm bushed ;P

---

### Post by benplaut on 2005-10-11
[QUOTE=Kyral]Wait until tomarrow for more. Tonight I'm bushed ;P[/QUOTE]
okey... we can wait :D

---

### Post by Storyman on 2005-10-19
What are some of the reasons for creating symbolic links?  How are they used?  Thanks for the great tutorials.

---

### Post by Sutekh on 2005-10-21
Man what a thread!  Love your work Kyral!  

I thought I'd share something I found in a Linux book.  
If you type ```
history | grep <command>
``` replacing command with a search word the terminal will spit out all the instances where you have used that particular command.  For example, if I want to know all the times I've used gedit to edit a particular file I'd type ```
liam@sutekh:~$ history | grep gedit
    5  sudo gedit /usr/share/applications/NVIDIA-settings.dekstop
   10  sudo gedit NVIDIA\ Settings
   47  sudo gedit /etc/apt/sources.list
   88  sudo gedit /etc/gdm/gdm.conf
  103  sudo gedit kmenuedit.desktop
  119  history | grep gedit
liam@sutekh:~$

```

This could also be added as an alias ```
alias h="history | grep"
```
then to get the history of gedits, I'd type ```
liam@sutekh:~$ h gedit
    5  sudo gedit /usr/share/applications/NVIDIA-settings.dekstop
   10  sudo gedit NVIDIA\ Settings
   47  sudo gedit /etc/apt/sources.list
   88  sudo gedit /etc/gdm/gdm.conf
  103  sudo gedit kmenuedit.desktop
  119  history | grep gedit
  120  h gedit
liam@sutekh:~$

```

I've find this pretty neat.

---

### Post by heimo on 2005-10-22
[quote=Sutekh]
I've find this pretty neat.[/quote]

One way to search commands from command line history is to hit ctrl+R and start typing part of the line you're searching for (doesn't have to be beginning). If anything is found, it's shown on the command line, if it's not the line you're looking for, you can hit ctrl+R again to find other hits. Then just edit the line or accept as is by hitting enter.

---

### Post by steviecee on 2005-10-22
Thanks Kyral - Just the sort of thing I need.:KS 

One question:

Is there anything online which lists the commands and explains what they do?

---

### Post by doclivingston on 2005-10-22
[QUOTE=steviecee]Is there anything online which lists the commands and explains what they do?[/QUOTE]

If there is a particular command you want help on, type```
man *command*
``` which will bring up the man page (manual) for that particular command. You can move up and down with the arrow keys or page up/down, and 'q' will exit. For a more detailed description, enter "man man".

---

### Post by kjcon on 2005-10-22
Or, if you're in a mood to go exploring, you could try

```
ls /bin
```

and 

```
ls /usr/bin
```

and look up the man pages for any of the commands that look interesting.

Another good place to find information on the basic commands is the info pages.Try

```
info coreutils
```

info itself is not a very intuitive program to use so you might like to run

```
info info
```

and type 'h' which will bring up a tutorial on how to use it.

IMO the man pages are great for simple commands, like
ls or cp, and commands, or commands that you already know 
how to use and just need a reminder of the possible options. 
For more complicated commands like find, or grep however, the info 
pages go into more detail and are much easier for an absolute newbie 
to understand.

---

### Post by bluemuffin on 2005-11-01
Hey!

Finally, somebody understood our main problem. Thanks a lot Kyral and I hope you won't mind if I printed-out your tutorial.

:KS

---

### Post by Kyral on 2005-11-01
Whoa I had almost forgotten about this thing (Wait a sec...its in my sig, well I've been busy with school, yanno how it gets :D)

Anyway symlinks are kinda useful for all sorts of things. I know they are used within' the lib and /usr directories to make things simple (anyone who has compiled a kernel the old fashioned way will remember having to symlink the current kernel sourcedir to /usr/src/linux).

I use them in my /home to link my /anime into ~/anime so its all in one spot. Also I use it on my college AFS space to link project
 directories into my homedir there.

And thanks to whoever pointed out the man command. Its incredibly useful if you need a reminder on what does what. Heck I use it all the time because I can never remember exactly how tar works ;P

---

### Post by Kyral on 2005-11-01
Well, since there seems to be a picked up interest in the thread, and I'm fresh out of ideas, anyone have anything that they would like me to explain? Perhaps how to harness the power of Apt-Get?

---

### Post by RSX311 on 2005-11-04
[QUOTE=Kyral]Well, since there seems to be a picked up interest in the thread, and I'm fresh out of ideas, anyone have anything that they would like me to explain? Perhaps how to harness the power of Apt-Get?[/QUOTE]

YES! keep them coming :)

Need some tutorials for chmod and chown

---

### Post by Kyral on 2005-11-04
Okay, well since I don't fully understand chmod and chown myself without consulting the manpages, and I'm not at my home computer, I guess its time to show you how to harness what makes Debian-based distros so awesome.

Its time for....

Apt-Get For Beginners!!

Now, all of you have used Apt-Get, you just don't realize it. Synaptic and Adept(For you Kubuntu folks) are frontends to this awesome tool. That means that every thing you do in them actually gets translated into an apt-get command. Now why would you want to use the command line over a GUI. C'mon look at the topic! Anyway I think its faster than Synaptic and also most instructions on the Forums will use apt-get over Synaptic, because as I pointed out before, its easier to type a line of code then it is to say "Click here, here, here".

Basic tasks.

Updating the cache:
This is equivilent to refreshing the package list in Synaptic.

```
sudo apt-get update
``` 
Pretty simple huh? If all goes well you will see a bunch of text fly by saying that its connecting to the repositories.

Now by itself that command is kinda useless. I mean updatingg the cache is good and all, but you usually combine it with something else like..

```
sudo apt-get upgrade
``` 
This command should pretty much go hand in hand with update. Why? Well because it upgrades all the packages on your system if they have updates, and is quite useless without updating the cache beforehand, which is why I usually combine it into a single command like so

```
sudo apt-get update && sudo apt-get upgrade
``` 
Wait a second, whats that && doing there? Anyone who has programmed knows that means "and" so in this case it tells the computer to execute those commands one after another without input from me. Also useful in combining them into an alias, like I do (I went over those right?).

Oh for you people who are trying Dapper or want to (I advise against it unless you know what you are doing, or don't mind things breaking) you want to use upgrade's cousin

```
sudo apt-get dist-upgrade
``` 
Where upgrade will play things safe and hold back packages unless its 100% safe, dist-upgrade will do pretty much anything to get the upgrade, even if it means removing packages that conflict with one another.

So upgrading is all well and fine, what about INSTALLING?! Well, its easy!

```
sudo apt-get install <package>
``` 
This is self-explanitory, but I'll do it anyway. It goes to the cache, looks for the package named "package" and if it finds it, it checks its list of depends to make sure they are installed, installs them if they aren't, and then installs the package. Very nice no?

As we install we also remove. How do we remove? I thought you'd never ask.

```
sudo apt-get remove <package>
``` 
Now its safe to note that this DOES NOT remove its depends. However if something else depends on the package and would break if its removed, then its also removed. Kinda fun!

Now what if you don't know the name of the package? Well, there is a tool for this, and guess what?! Doesn't require sudo! Cool!!!

```
apt-cache search <string>
``` 
Searches the Apt-Cache for anything that matches "string". Now you guessed it this can be very big. But, you know what to do right? Yep!

```
apt-cache search <string> | less
``` 
Its our old friend less! Remember this useful function?

Now you have your package, what if you want to know all about it? Apt-Cache has you covered.

```
apt-cache show <package>
``` 
This will show you all the data that Apt knows about it. Who made it, the arch, the section, the depends, suggests, everything! I'd also use less on this one.

Now some of you wonder where the packages are stashed. They are stashed in /var somewhere....but you don't need to know this, because you can delete it via apt! 

```
sudo apt-get autoclean
``` 
This thing removes all the debfiles that can still be downloaded from the repos. Yanno, 'cause you wouldn't wanna nuke packages that you cannot find anymore!

Oh, a very quick reminder. If you ever wanna see what an apt operation is gonna do, tag "-s" onto the command to make apt simulate it. An example is needed no?

```
sudo apt-get install k3b -s
``` 
This will display what WOULD be done if you wanted to install k3b.

Oh last thing. Closely related to, heck even responsible for Apt being around, is the Debian package, or basically a file that ends with .deb

If you ever looked in the cache, you'd know that all the packages are .deb files. Well, how do you install one that you downloaded from the net? EASY! First get into the directory where the debpack is, then

```
sudo dpkg -i <file>
``` 
If it has depend problems it will complain and you will have to use Apt-Get to resolve them, but if it didn't, it will install and you can use the tools above to manipulate it.

So there is how use the most supreme package tool, Apt! Any questions? :D

EDIT:
Sorry guys, I forgot one VERY important thing. Its how to edit that thing what we like to call the Sources.list

Now what is the sources.list? Well yanno how when you update Apt you see a bunch of URLs fly by? Well, Apt looks in a file located at /etc/apt/sources.list, or commonly referred to as just the sources.list

Now what does this file look like? Well, I can't show you mine because its heavily modified and also contains some sketchy repos that I don't want you guys using and breaking your system with. But, I can show you a good sources.list! Actually Aysiu has a really good one in his signature so I'm use it to demonstrate (Hope you don't mind Aysiu!)

```

 ## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted  ## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe 
 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 
 deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 
 deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

```


Thats what your sources.list SHOULD look like in Breezy. Now I know the stock one has Backports there, but Backports isn't open yet, so comment it out until later (Commenting?! What? All in good time Padawan!)

So the basic format starts with either a "deb" or "deb-src". This tells apt what to expect. "deb" is a binary repository, "deb-src" is a source code repository, which is something primarily used by Developers. If there is enough demand to know how to use the DebSource repos I'll explain. Anyway, the next part is the URL of the repository. You see that they all end in "/ubuntu". Well that is for the Master Archive and local archives (us.archive, ca.archive, etc). Others use something different (I personally sync to my on campus mirror, and I have to use a different syntax). After that is the release, in this case breezy. THIS is what you change whenever you want to go from one release to another. Hoary users will have "hoary" here, Warty users "warty" etc. The last part is the "section". When we tell you to enable Universe and Multiverse, this is what we mean. In Ubuntu there are 5 Sections. Main, Restricted, Universe, Multiverse, and Backports. (Remember Breezy Backports are not open yet).

So how do you edit this? Easy! Pop open a terminal and hit this

```
sudo gedit /etc/apt/sources.list
```

For the Kubuntu folks the command is SLIGHTLY different

```
sudo kwrite /etc/apt/sources.list
```

Then just edit it like a text file and save when you are done. Don't forget to update Apt afterward!

---

### Post by ebonysurfer on 2005-11-07
How d u say thank u without gushing all over the page. Well written and insightful, without being insulting it gave a much needed primer:KS I surf the universe and rarerly get this

---

### Post by Logic* on 2005-11-09
Great thread Kyral. I now understand symlinks better, and I've borrowed parts of your bash alias files too :D

---

### Post by richieboy on 2005-11-09
WOW!!!!!  thanks a lot.  this is going to help tons.  please do more!!!!!!!!!

---

### Post by Kathleen M on 2005-11-09
Hello Ubuntu Community.  And a special thanks to Kyral.  I'm very new to the terminal and just learned how to do the most elementary and necessary of tasks:  change from home to desktop directory!  Kathleen M

---

### Post by holiday on 2005-11-09
A little bit on bash scripting would be fun.

---

### Post by Rykhaard Damian on 2005-11-10
:D 

The amount of 'thanks' / gratitude that I feel, Kyral - I'm at a loss as to figuring how to type! ;)   (For all of the wonderful tutorial typing that you've done in this thread, thus-farly. :)

Reading some of what you writ (man man; cp; mv and more) brought back wonderful memories of my 1st days on the Net, in 1991, touring around my 'online directory' at my service provider - in Unix.  It's wonderful to be BACK in this seat of 'power', that just never seemed to be equated in that 'other OS' world. :o :razz:

Funny as well - a co-worker had recommended Ubuntu, and gave me the installation copy of 5.04.  Coming back to this site for the 1st time in months, last night, reading in the Stickies and a few messages in this 'Newbie' area - I 'knew' that Ubuntu was my new 'home'. :)  Your tutorial's here Kyral, are a wonderful addition to that!

Many grand thankees, beyond comprehendable measurements! :D

"So much to learn, and so little time." LOL ;)
Ryk

---

### Post by Kyral on 2005-11-10
[QUOTE=holiday]A little bit on bash scripting would be fun.[/QUOTE]
Bash scripting huh?

Uhh, as soon as I master it myself sure!

---

### Post by Maverick911 on 2005-11-10
Hi everyone,

Here are some useful links for anyone new to Linux who wants to learn more:\\:D/ 

**Introduction to Linux - A Hands on Guide**
[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)
This guide was created as an overview of the Linux Operating System, geared toward new users as an exploration tour and getting started guide, with exercises at the end of each chapter. For more advanced trainees it can be a desktop reference, and a collection of the base knowledge needed to proceed with system and network administration. This book contains many real life examples derived from the author's experience as a Linux system and network administrator, trainer and consultant. We hope these examples will help you to get a better understanding of the Linux system and that you feel encouraged to try out things on your own.

**Bash For Beginners:**
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
The Bash Guide for Beginners gets you started with Bash scripting and bridges the gap between the Bash HOWTO and the Advanced Bash Scripting Guide. Everybody who wants to make life easier on themselves, power users and sysadmins alike, can benefit from reading this practical course. The guide contains lots of examples and exercises at the end of each chapter, demonstrating the theory and helping you practice. Bash is available on a wide variety of UNIX, Linux, MS Windows and other systems.

**Link to The Linux Documentation Project main page where these guides and many others are located:**
[http://www.tldp.org/](http://www.tldp.org/)

Happy Computing!:)

---

### Post by HJThis on 2005-11-10
Hey,All

Kyral you the man great work keep them coming

Best of luck ;)

---

### Post by HJThis on 2005-11-10
Hi,Maverick911

Cool links thanks

BOL

---

### Post by holiday on 2005-11-10
Oh come on! It's pretty easy once you start. Mastering it is another issue, but a little bit on it would be good. You started this thread without any claim of mastery, just an urge to share. So good on you. Go on. 

I'm not a linux hotshot by any means but I do a lot of repetitive stuff in a bash script. 

Look into it and give it your treatment. 

You're good at treatments.  Making things simple. 

Go at it. 

Go on!

---

### Post by D1G1T4L on 2005-11-11
this is a good thread

---

### Post by Kyral on 2005-11-11
[quote=holiday]Oh come on! It's pretty easy once you start. Mastering it is another issue, but a little bit on it would be good. You started this thread without any claim of mastery, just an urge to share. So good on you. Go on. 

I'm not a linux hotshot by any means but I do a lot of repetitive stuff in a bash script. 

Look into it and give it your treatment. 

You're good at treatments.  Making things simple. 

Go at it. 

Go on![/quote] Jeez you make it seem like I can make learning assembly seem easy :D

---

### Post by bonjun on 2005-11-18
Great Info!!!
I have rated this!

---

### Post by Kyral on 2005-11-18
Its been a long time coming but it looks like I get to cover this topic now. Aided by my trusty copy of O'Reilly's *Linux In A Nutshell: 4th Edition *(which is a really AWESOME reference guide, I mean literally everything is in there)

Its time to cover another core part of the Unix-type OS's

***Permissions For Beginners!***

I have to preface this whole thing by explaining it so you will understand how much power the following commands will give you and to impress upon you how CAREFUL you have to be. I cannot stress this enough, BE CAREFUL here. You'll get sick of me saying it, but I don't care, it cannot be said enough. Okay? 

I know you have all heard about "root" and "permissions" and "sudo" and all that stuff, but what is it all about? Well to understand that you have to understand something about Unix. You see, Unix was designed to be a true multiuser OS, so you could have multiple people logged in at once. Now it wouldn't be a good idea to give all these people free reign over the system right? Yah, I don't have to tell you how sketchy that would get. So in came the concept of permissions and limited user accounts. Each user would only be able to affect files and directories that they had permission to. Even the permissions could be different. You know you can cat just about any file on the filesystem, but you cannot change the majority of them as you are. Thats because you only have Read permission. Anyway back to the story. Every user when created only has write access to thier home directories and possibly things like CDs, and external hard drives. However there is still a need to administer the system. Which is where the concept of the SuperUser comes into play, more commonly known as Root. The root account can touch any file, do anything they want. Can you see where this can be a *bad* thing yet? I already gave the example of 

```
sudo rm -rf /
``` 

EDIT: I guess someone went and did sudo rm -rf / WITHOUT reading this beforehand. I apologize for this one. Now here is a big FAT warning.

_***[SIZE=5]SUDO RM -RF / WILL ERASE YOUR HD! DON'T DO IT![/SIZE]***_

*Begin opinion block, skip if you like*
Ironically its this restricted permissions system that, in my mind, keeps Unix based OS's from getting hammered by virii. Think about it, if you get infected while you are using your normal user account, the virus can only mess with what you would normally be able to mess with. Makes sense no? In my opinion, this is one of the MAJOR weaknesses of XP. XP puts you in Admin mode by default right? And its a major pain in the rear to try and do anything in an XP Limited account right? And so most people sit in Admin mode all the time, right? Seeing as Admin Mode == Root on XP, its no surprise its blasted left and right by virii, because they have full access to the computer. Anyway thats my rant, back to the educational stuff
[I]End Opinion Block, start paying attention again!

[/I]Sorry about that :D

Anyway, you are going to have to access root to setup your system. On most Linux distros you setup both a root account and a user account, but as many of you have noticed, thats not the case in Ubuntu/Kubuntu/Edubuntu/Xubuntu (I'm just gonna start calling it "*buntu" from now on..sheesh!). You setup a user account only. Well, in a sense, that first user account becomes something between Root and a normal user. Its because only that first user can use the sudo command to gain root power. Try it! Create another user account and try to sudo from it, you can't! Its also why the first user account should have a VERY good password, because it is the same password you use to use sudo with. The ramifications of this are discussed more on wiki.ubuntu.com/RootSudo

Anyway, enough rambling and backstory. You want to know how to utilize these things right? Okay. But remember, as Stan Lee said

> With Great Power comes Great Responsiblity 
So be on the ball when wielding these commands! Think of it as driving! Don't Drink and be Root! Okay?! Promise me! Cool! Lets have fun now.

[I]Chown

[/I]Chown is the way you directly change ownership of files and directories. [I][B]

Don't chown anything in /etc, /var, /bin, /usr (except /usr/local), /boot, or /sbin to your normal user. THIS WILL SCREW UP YOUR SYSTEM!

[/B][/I]One of those warnings I told you I would POUND into your head. So how do we use this command? Easy my friend

As the user that owns it NOW(or root/sudo)
```
chown <option> newuser file
``` 
Kinda self explainitory, except for the option. There are a couple options, but the only one that gets used often enough to mention here is the -R option, which makes chown recursive, meaning it goes down through the directory and applies the same ownership change to everything in it 
(***DON'T CHOWN -R YOU /***)

Sorry about all the warnings :D Just want you to be safe.

Now Chown was easy. The way to play with permissions is trickier, which is why I have my Linux In A Nutshell with me.

The permissions on ANYTHING have 9 settings (well, 12, but the last 3 aren't important alot). Read/Write/Execute permission for the Owner, Read/Write/Execute for the Group, and Read/Write/Execute for everyone else. 9 Settings. And they pretty much explain themselves. If the Execute permission for Other is set, then anyone can run the file. Got it? Cool. Lets realize the command for this one.

```
chmod <options> [MODE] file
``` 
Now options again there are only two that get used, -R for recursive and -v for verbose. Now what is "MODE" you ask? Well that is the permissions you want to apply to the file or directory. This is where chmod gets tricky, because there are multiple ways to set this. Personally I find the Octal way to be easier. In this MODE takes the form of 3 digits. The first digit represents the Owner's permissions, the second digit represents the Group's permissions, and the third number represents the Other's permissions. Now to actually set the permissions you are going to have to do some math to get the number. But its easy. If you want to set read for one of the settings, you add 4. If you want Write, you add 2. And if you want Execute, you add 1. Maybe an example is better. Say I wanted to give all permissions to the Owner, only Read + Execute to the Group, and no permission at all to Others. My Octal would come out like this.

750

Lets take it apart. First digit is the Owner's permissions, right? So...

7 = 4 (Read) + 2 (Write) + 1 (Execute)

That was easy, what about the Group permissions. Well...

5 = 4 (Read) + 1 (Execute)

And the Other's permission comes out to 0 because I'm not giving any permissions :D

Now I'm gonna quickly spit out a cheatsheet you can use. Watch this

7 = ALL (Read/Write/Exec) permissions
6 = Read + Write Permissions
5 = Read + Exec permissions
4 = Read Only
3 = Write + Exec (How would that work if you can't read it...)
2 = Write
1 = Exec
0 = No Permissions

Understand? Niiiice

Okay someone on IRC pointed this out, I don't have a command example. Well oversight on my part and I apologize. Well here we go then. 

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ ls -lah xmaslist.txt
-rw-r--r-- 1 kyral kyral 1.9K 2005-11-30 23:51 xmaslist.txt

``` 
We can see that this file is 644 permissions. Well I feel like letting everyone write to it. So...

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ chmod 666 xmaslist.txt
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ ls -lah xmaslist.txt
-rw-rw-rw- 1 kyral kyral 1.9K 2005-11-30 23:51 xmaslist.txt
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$

``` 
Cool huh?

Well, I think I covered permissions nicely. Oyah....I have to do this but....

[I][B]BE CAREFUL!!!

[/B][/I]Keep giving me more terminal related topics you want covered and I'll keep adding on!

---

### Post by exciliado on 2005-11-18
Thank you very much Kyral for you effort we appreciate it =D>

---

### Post by l0c0dantes on 2005-11-18
So this is how you turn files in to .exe files, right?

---

### Post by RSX311 on 2005-11-18
[QUOTE=l0c0dantes]So this is how you turn files in to .exe files, right?[/QUOTE]

not technically an .exe file, which is only in windows, but a file that is executable.

---

### Post by MighMoS on 2005-12-09
[QUOTE=Kyral]
3 = Write + Exec (How would that work if you can't read it...)
[/QUOTE]

I'm honestly too lazy to figure out how this would work for files, but for directories I would think it'd create a place similar to a public mail box.  You can put anything in, but can't get it out.  Interesting way to file share, I guess.

---

### Post by cro.smiley on 2005-12-21
Great job Kyral! 
I realy like your way of explaining things.

In my case i learned everything about terminal in terminal, "man intro" is all I needed. But the problem was that in the beginning i didn't know anything so it took my a lot time to acctually find that command.

I don't know why is so hard to print a short help when you run your konsole for the first time. For example: "Type: 'man intro' for introduction to user commands".
It would just make things so easyer.

I hope you will continue with a great job. :)

---

### Post by TheCyrus on 2005-12-21
Great thread Kyral!

I don't feel completely stupid anymore!
Keep 'em coming!

---

### Post by nobd7979 on 2005-12-25
Hello Guys,
140 Million Bulk Email List Bulk Email List for Email Advertisers! Download Opt-In Email List Database
Here is the Screenshot of the software: [http://www.buytargetedemaillist.com/screenshot.php](http://www.buytargetedemaillist.com/screenshot.php)
[Click here for more info]("http://www.buytargetedemaillist.com/moreinfo.php")

---

### Post by bscbrit on 2005-12-26
MOD / ADMIN

Can someone remove the spam post immediately preceding this one please? #55.

Thanks

**Offending post has now been removed - Don't blame TheCyrus**

---

### Post by eriqk on 2005-12-26
Very cool, Kyral! I never really understood chmod- until now. Thanks!

Groet, Erik

---

### Post by oldgoat on 2005-12-26
Beautiful - especially the permissions:cool:

---

### Post by dueY on 2005-12-26
Great thread \\:D/

---

### Post by TheCyrus on 2005-12-27
[QUOTE=bscbrit]MOD / ADMIN

Can someone remove the spam post immediately preceding this one please? #55.

Thanks[/QUOTE]

I hope you're not referring to my post. 

I don't see how I'm spamming if you are.

If you're not referring to mine, i said nothing.

---

### Post by Gray. on 2005-12-27
Great thread. Copied some of your aliases as well. Hehehe.

---

### Post by bscbrit on 2005-12-27
[QUOTE=TheCyrus]I hope you're not referring to my post. 

I don't see how I'm spamming if you are.

If you're not referring to mine, i said nothing.[/QUOTE]

TheCyrus

No - the offending post has now been removed.  It was #55, now I am #55 but that leaves you just before me.

FYI It was an email advertising millions of active addresses for spammers to use.  I didn't think that it should be left in place because I didn't want even one more spammer to exist on the web.  Probably a futile gesture - but it made me feel a little better :D :D

I have edited my original post to absolve you from blame ....... :D

---

### Post by Kyral on 2005-12-28
Well, its been a long time coming, but here is a New Year's (okay I'm off by a couple days...) edition of Terminal For Beginners. This time I'll make a couple quick mentions about input and output redirection, then touch on sed, an uber powerful stream editor that once harnessed makes life A LOT easier. This could be considered a prelude to "Bash Scripting For Beginners"

**Input and Output Redirection**

To understand this concept you should try to think of the data as a stream. You can redirect it almost at will through different programs. In fact you have already done this with the

```
cat filename | less
``` 
trick. The | "connects" the output from cat to the input of less so it flows right from cat to less. Here is another example. Say you wanted to know how many files you have in a directory. Well ls you know can help with that, but so can the wc command, specifically is -l option which counts lines. So...

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~/anime/School Rumble$ ls
[SHRIMPS]_School_Rumble_22.avi*
SHRIMPS_School_Rumble_23.avi*
SHRIMPS_School_Rumble_24.avi*
SHRIMPS_School_Rumble_25.avi*
SHRIMPS_School_Rumble_26.avi*
[WF-KAA]_School_Rumble_01.DVD(XviD.AAC)[2465C4A1].mkv*
[WF-KAA]_School_Rumble_02.DVD(XviD.AAC)[55F08DB6].mkv*
[WF] School Rumble - 03 [0C9A290E].avi*
[WF]_School_Rumble_-_04_[02D25233].avi*
[WF]_School_Rumble_-_05_[9B6176D5].avi*
[WF]_School_Rumble_-_06_[495C6F46].avi*
[WF]_School_Rumble_-_07_[C3DCAEFD].avi*
[WF]_School_Rumble_-_08_[D19C182E].avi*
[WF]_School_Rumble_-_09_[20A083A2].avi*
[WF]_School_Rumble_-_10_[E9F2C62E].avi*
[WF]_School_Rumble_-_11_[2A6EC1B7].avi*
[WF]_School_Rumble_-_12_[FE58A6A3].avi*
[WF]_School_Rumble_-_13_[749A20DF].avi*
[WF]_School_Rumble_-_14_[29732A21].avi*
[WF]_School_Rumble_-_15_[6E0E43D7].avi*
[WF]_School_Rumble_-_16_[A89B2EBB].avi*
[WF]_School_Rumble_-_17_[23880F52].avi*
[WF]_School_Rumble_-_18_[67399B31].avi*
[WF]_School_Rumble_-_19_[3D0F58D0].avi*
[WF]_School_Rumble_-_20_[6EF54D2B].avi*
[WF]_School_Rumble_-_21_[E5C7B004].avi*
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~/anime/School Rumble$ ls -l | wc -l
27

``` 
See what happened? The first command I used ls. The second time I used ls -l | wc -l. I piped the output from ls into wc -l for wc to use as its arguement. This can also be combined with grep to find things. Say I wanted to find the package that contains the Emacs Python mode? Well you should know that apt-cache search can help, but check this out.

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ apt-cache search emacs | grep python
python-mode - Emacs-lisp python-mode and doctest-mode for the Python language
python2.4-pymacs - interface between Emacs Lisp and Python [built for python2.4]python2.3-pymacs - interface between Emacs Lisp and Python [built for python2.3]
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$

``` 
Anything that outputs to the terminal can have its output piped into something else, which is just about anything. You can pipe multiple times. Say I wanted to see how many packages matched that grep return? Well, we know that its one package to a line..so

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ apt-cache search emacs | grep python | wc -l
3
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$

``` 
So in case you missed it. I piped the output from the apt-cache search into grep, then piped it's output into wc. Nice huh? I'm sure you can think of MANY more uses for this one.

Now there is more to this beast that piping. You can send stuff to files as well, as well as from files. First

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ echo "python" > test
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ cat test
python

``` 
See? Normally echo just literally prints whatever you gave it to the screen (called Standard Output btw), but this time I used >> to send it to a file instead. There is something to be noted. > and >> both send output to a file. However > will completely overwrite anything in the file if it exists, wheras >> will append to the file if it exists. Both will create the file if it doesn't exist. Perhaps an example is needed.

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ echo "perl" > test
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ cat test
perl
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ echo "python" >> test
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ cat test
perl
python

``` 
Got it? Here is a nicer and more useful example, that also shows off sed

First off the file we are working with. My sources.list (only a part of it, I have sketchy repos commented out in it that I don't wanna expose)

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ cat /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
#deb-src http://archive.ubuntu,com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#deb-src http://archive,ubuntu.com/ubuntu dapper-security main restricted universe multiverse

``` 
As you can see its setup for Dapper. But what if (why I don't know) I wanted to change it over to Breezy? Well normally you'd have to open it up and manually change every instance. But WHY?! Sed can do it for us!

```
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ sudo sed s/dapper/breezy/ /etc/apt/sources.list > example.sources
kyral@UltimateInsaneFreedomDestinyDarknessAndLight:~$ cat example.sources 
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu,com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#deb http://archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
#deb-src http://archive,ubuntu.com/ubuntu breezy-security main restricted universe multiverse
``` 
Yah, you just saw right. With ONE command I changed it all. Keep in mind I redirected to a file in my homedir. sed would have just output to standard out otherwise. But yah, all in one command. Nice don't you think? An equivelent command to jump from Hoary to Breezy would be

```
sudo sed s/hoary/breezy/ /etc/apt/sources.list >> /etc/apt/sources.list
``` 
Then you would do the sudo apt-get update && sudo apt-get dist-upgrade dance.

Now sed is very powerful, and has MANY more options and things than I comprehend right now (in fact this substitution thing is one of the ONLY things I grasp right now) but the general command for the string matching and replace is like this

```
sed s/<string to find>/<string to replace it with>/ <file to act on>
``` 
Like I said, sed outputs to standard out by default, so just running that will spitout the change to the screen. Use >> to send it to a file.

Pretty cool eh? ```
man sed
``` to find out more :D

Oh I almost forgot input directtion. Well...I couldn't find a example on my computer, but I did have to use it recently. I had used a shell script to generate a bunch of SQL commands so I didn't have to do it by hand. So I uploaded the file to the server and simply

```
 mysql -p <my password> < file
``` 
mysql processed the file (which contained the quit statement at the end) and happily quit leaving me back at the prompt without me doing anything beyond running that command. < is used more often for testing programs and scripts anyway :D

So thats all I have. Happy Holidays!

---

### Post by heimo on 2005-12-29
[quote=Kyral]
**Input and Output Redirection**

To understand this concept you should try to think of the data as a stream. You can redirect it almost at will through different programs.[/quote] 
Not time to read through your excellent contribution, but as this is actual topic to myself... Redirection is not limited to local system. Just used it to make backup through insecure network (using encryption and compression), like this:
```
tar czvf - /path/to/files | ssh user@host dd of=/path/to/backup.tar.gz
``` This creates backup file on remote system (host) over ssh "pipe". Very, very convenient. :)

---

### Post by Kyral on 2005-12-30
Wow....dude that trick is hot......thanks for revealing it!

---

### Post by Kyral on 2006-01-03
[B]Fun with Screen

[/B]Okay, this was supposed to be the intro to Bash Scripting, but I found a very NICE utility that I have to share. By now you know that I'm a console fanboy. This means I use things like the very powerful console IRC Client Irssi. But these things "die" when you close the terminal. Plus whenever I SSH into my machine from the computer labs, I have to kill Irssi before I load another instance or else I get multiple nicks on servers and ick.

But I finally (I say finally because a lot of people have been telling me about it) played with and learned how to use a very useful app. This is called Screen. What is so awesome about it? Well, recall that I told you to think of data as a stream that you can direct and redirect almost at will. Screen helps you do this. You start an app with screen, and screen takes care of those pipes for you. So if I start Irssi with screen on my Desktop in my dorm room and then head up to the computer labs and SSH in from there, I can tell screen to disconnect Irssi's output and input (called detaching) from my Desktop's monitor and keyboard and connect them to the SSH session (called attaching). All this happens without disrupting Irssi. Very nice. Now how do we USE this? Glad you asked. Screen is installed by default, so nothing to Apt-Get

Fire up screen with the app
```
screen <app>
```

<app> is the command to start the application you want to run in screen, complete with any options you would use. Screen activates and immeadiatly gets out of the way of the app. So it looks like you started the app normally. Now what if you want to start another app? Easy. Hit CTRL-A C to open another console in screen and run the command normally (w/o the screen. Screen is already running). Jump between terminals in Screen with CTRL-A N to cycle through terminals and use CTRL-A A to jump to the one you last viewed. By now you should be getting that Screen is something like a Window Manager. All terminals you spawn with CTRL-A C are within' the screen session. This is kinda important to note. Now to detach the screen session (and all terminals within it) hit CTRL-A D. The prompt will look something like this.

```
kyral@PacificNebula:~$ screen -r
[detached]

```

Wait...wait was screen -r? Well thats how you reattach a detached screen. Hit that command and screen sends the session to whatever terminal you are at. Very cool no? This is very useful for me and I'm sure you will find ways to play with it :D And the best part is that the applications keep running even while detached. They keep doing whatever. So you can detach a BitTornado screen overnight and assuming nothing goes wrong with the computer that its on, it will keep downloading and doing its thing.

Well, thats a short one! Post questions, new topics, or anything else!

---

### Post by cvcaelen on 2006-01-06
Thanks a million for this tutorial

extremely usefull

Keep up the good works=D> 

Christiaan

---

### Post by diggs on 2006-01-06
Yes, killer thread indeed. Looking at all this code makes me thankful for things like windows, right clicking and copy and pasting...

---

### Post by ernie on 2006-01-12
i was looking at this thread and found it amazing. it really helped me out in learnig the terminal. but i was wondering if there is a way to download files with the terminal. i am asking this because that is pretty much all i can use on my computer and to get it to work i need to download something from the internet but i dont know how to do this any help would be nice

---

### Post by frvw on 2006-01-12
hey ernie, there's this nice program "wget". haven't used it myself, but i've seen some installers use it. guess "man wget" or "wget --help" would be a nice place to start.

---

### Post by mscman on 2006-01-14
Great work Kyral!

I just wanted to point out another very useful command to check if something has installed correctly (or if it was installed in the first place).  The 'which' command will tell you the directory that a program is installed in.  You can use it with the '-a' argument to list all directories in which the program appears.  For example:

```
andy@ahoward:~$ which gnuplot
/usr/bin/gnuplot

```

```
andy@ahoward:~$ which -a gnuplot
/usr/bin/gnuplot
/usr/bin/X11/gnuplot
```

I use this in the labs I work in at school to see if students have removed the files they were supposed to ;)

---

### Post by v1ckey on 2006-01-21
hi Kyral,
that a real nice piece of work up here .i appriciate your helping hand to all of us newbies.
i Have just installed ubuntu 5.10 and i badly need to install anjuta for my college work can you please helpout.I would be very greatful.I do not have an internet conection on my desktop.
i would be still thankful if you expain in the same way as above.
Thankyou.
You made my day.

---

### Post by RaiSuli on 2006-01-21
This is an excellent guide. Thank you!

---

### Post by terrukallan on 2006-01-23
[QUOTE=v1ckey]hi Kyral,
that a real nice piece of work up here .i appriciate your helping hand to all of us newbies.
i Have just installed ubuntu 5.10 and i badly need to install anjuta for my college work can you please helpout.I would be very greatful.I do not have an internet conection on my desktop.
i would be still thankful if you expain in the same way as above.
Thankyou.
You made my day.[/QUOTE]
Assuming you have access to a computer you can use to download a file to a floppy/cd/usb drive this can be done relatively easily (in theory).

1) Download [http://archive.ubuntu.com/ubuntu/pool/universe/a/anjuta/anjuta_1.2.4-1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/a/anjuta/anjuta_1.2.4-1_i386.deb") which is the Breezy version of anjuta from universe.  (I am assuming i386 is your platform.  If this is not the case replace i386 with amd64 or powerpc in the URL.  You can run "dpkg --print-architecture" to find out which one is correct.)

2) Run the following command on the computer you want to install on with "/path/to" replaced with the actual path to the anjuta deb package.
```
sudo dpkg -i /path/to/anjuta_1.2.4-1_i386.deb
```
You should end up looking something like this:
```
terrukallan@sosuke:~$ sudo dpkg -i ./anjuta_1.2.4-1_i386.deb
Password:
Selecting previously deselected package anjuta.
(Reading database ... 90735 files and directories currently installed.)
Unpacking anjuta (from ./anjuta_1.2.4-1_i386.deb) ...
terrukallan@sosuke:~/Downloads$
```

3) Assuming the previous command doesn't give you any errors anjuta should now be installed.

---

### Post by kennethb on 2006-02-07
Nice intro on the Terminal for beginners!

---

### Post by bountonw on 2006-02-09
Every guide and tutuorial I read has the same thing.

> <Tab>
(In a text terminal) Autocomplete the command  if there is only one option, or else show all the available options.
THIS SHORTCUT IS GREAT! It even works at LILO prompt!

But for me, if there is more than one option, the computer beeps when I hit tab.  It doesn't show the other available options.  Otherwise it works great.  Do I have something set wrong?

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=bountonw]Every guide and tutuorial I read has the same thing.



But for me, if there is more than one option, the computer beeps when I hit tab.  It doesn't show the other available options.  Otherwise it works great.  Do I have something set wrong?[/QUOTE]
Just tap TAB twice.  I think the beep is telling you there are going to be a lot of choices.

---

### Post by bountonw on 2006-02-09
Thanks.  Tab Tab, Twice works.

---

### Post by bountonw on 2006-02-09
I don't know where I read it, but someone said that cat was my friend.  using the Ctrl>Alt>F1 key I logged on to a separate terminal wanting to explore the vast jungle of information on my computer.  (Ctrl>Alt>F7 gave me my GUI back.)

Anyway, I used cat for xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb

(I would appreciate someone helping me loading the fonts, I got stuck in a combo of the wiki and this thread.  My thread is [http://www.ubuntuforums.org/showthread.php?p=717694&posted=1#post717694](http://www.ubuntuforums.org/showthread.php?p=717694&posted=1#post717694))

The cat is out of the bag.  Space invaders to the max. All kinds of garblygook went flying accross the screen and the computer began beeping wildly.

I hit Ctrl>C to stop everything.  The problem is that my computer screen in this terminal is a combination of Russian and computer symbols.  I jumped back to the GUI and tried the terminal there and it is normal.  When I peeked back at the Ctrl>Alt>F1 terminal, it was still garbled.  In case I am ever stuck like this, is there a command to turn my terminal back to English?

---

### Post by Mustard on 2006-02-09
[QUOTE=bountonw]I don't know where I read it, but someone said that cat was my friend.  using the Ctrl>Alt>F1 key I logged on to a separate terminal wanting to explore the vast jungle of information on my computer.  (Ctrl>Alt>F7 gave me my GUI back.)

Anyway, I used cat for xfonts-thai-ttf_0.cvs.20030411-0.2ubuntu1_all.deb

(I would appreciate someone helping me loading the fonts, I got stuck in a combo of the wiki and this thread.  My thread is [http://www.ubuntuforums.org/showthread.php?p=717694&posted=1#post717694](http://www.ubuntuforums.org/showthread.php?p=717694&posted=1#post717694))

The cat is out of the bag.  Space invaders to the max. All kinds of garblygook went flying accross the screen and the computer began beeping wildly.

I hit Ctrl>C to stop everything.  The problem is that my computer screen in this terminal is a combination of Russian and computer symbols.  I jumped back to the GUI and tried the terminal there and it is normal.  When I peeked back at the Ctrl>Alt>F1 terminal, it was still garbled.  In case I am ever stuck like this, is there a command to turn my terminal back to English?[/QUOTE]

Is this persisting after a reboot of your system?  I would imagine its only a temporary problem that would dissappear next boot.  You still have ctrl + alt + f2  right through to ctrl + alt +f6 to use for terminal for now.

---

### Post by bountonw on 2006-02-09
Yes.  But I wondered how to rectify the problem in the current terminal.  I hadn't thought of rebooting, though.  Thanks.

I know I will get to it sooner or later in all of this reading of posts and tutorials, but I was wondering how to reboot from terminal.  Will it damage the programs that I have open in Gnome?

Was  'cat'ing a .deb package damaging to my system?

---

### Post by heimo on 2006-02-09
[quote=bountonw]Yes.  But I wondered how to rectify the problem in the current terminal.  I hadn't thought of rebooting, though.  Thanks.
[/quote]
Using command:
```
reset
```

[quote=bountonw]
I know I will get to it sooner or later in all of this reading of posts and tutorials, but I was wondering how to reboot from terminal.  Will it damage the programs that I have open in Gnome?
[/quote]
```
sudo reboot
```
It's always nice to end applications before rebooting, programs itself won't get damaged (99.99% of the time), but you may want to save any unsaved work.

[quote=bountonw]Was  'cat'ing a .deb package damaging to my system?[/quote]
No. It just showed garbish (binary data) on your terminal window (maybe also beeped couple times). cat is ok to show text files or redirect binary files to programs which understand the file format in question.

---

### Post by bountonw on 2006-02-09
I had just found reset here

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

Good list of linux commands.

But hadn't gotten to reboot yet.  Thank you for the info on reboot and cat.  I am going to close my programs and trying to reboot now.

---

### Post by centy on 2006-02-09
When deciding on which distro to try next, it was said that the community for ubuntu was one of its strong points. I never expected people to put quite this much effort into their posts though!! An excellent primer which I'm sure will help many many people. Thankyou very much for all the effort made thus far :) 

We appreciate it

---

### Post by cmallard79 on 2006-02-26
Wow, great terminal primer!  :)

My only experience similar to the terminal is with MS-DOS almost 15 years ago, and even then, I felt the command line was far more flexible and powerful than the "idiot-proof" GUI.  I'm very pleased to see Linux hasn't forgotten that fact over the years.  :D

Looks like my next step is to get myself a copy of "Linux in a Nutshell", since it has such a strong recommendation.  :)

---

### Post by dralaroc on 2006-02-26
Thank you, thank you & THANK YOU :D !  Helped me big time!

laroc

---

### Post by motubuntu on 2006-03-14
Kyral thanks for the tutorial.  It saved me from a lot of headaches and beginner angst.  Also very cool anime collection.

Cheers,
motubuntu

---

### Post by cara on 2006-06-28
can i carry you around in my pocket?

thanks for writing that up

---

### Post by champ_rock on 2006-07-07
gr8 job... helped me definately

---

### Post by Jjohn on 2006-07-15
Kyral,
      Many thanks for sharing your infomation. My only wish is that I found this thread much earlier.
Regards John:)

---

### Post by smokeysaysno on 2006-07-15
Like the other ubuntu noobs in this thread, I am extremely grateful.  THANKS!!  

A mod definately needs to sticky this!:-D

---

### Post by Breeegz on 2006-09-04
<--first post

this is exactly what I needed (installed Ubuntu two days ago), thank you very much...

---

### Post by Kyral on 2006-09-30
Well people. Its been a long time since I started this thread, even longer since I posted (Hey I have been busy). I no longer use Ubuntu, but I still help out. I am touched that people still reference this and post thanks. So now as a final gift, I present the (probably) last chapter in Terminal For Beginners. Are you ready? Its...

**Shell Scripting For Beginners!**

As you have most likely realized, and I have seen links on this thread from others, the Shell is scriptable. Well, time for a nice intro. Keep in mind that the Advanced Bash-Scripting Guide linked earlier in the thread is pretty much the best guide going, but if you have never programmed at or just want my personal spin on it, hold on for the ride.

What is the purpose of a shell script? A shell script is basically for when you are too lazy to type in the commands to a procedure over and over again and you need things like logic control (think if-then-else). They are basically shell aliases on steroids. Enough talk, lets get writing one!

**HelloWorld.sh**
```
#!/bin/bash -
# HelloWorld.sh
# The most basic shell script..ever!

echo "Hello World!"
exit 0
```

This is our first script. As someone (I forgot) said, you have to do Hello World because its tradition and something bad will most likely happen if you don't. So whats going on? Well all shell scripts have to start with this line ```
#!/bin/bash
``` This is called the "shabang". It tells the kernel that this is a shell script and to call /bin/bash in order to run it. The "-" after it is merely saying there are no special options to pass to the interpreter, and makes it more secure. After the shabang you see this ```
# HelloWorld.sh
``` This is a comment, meaning it will be ignored completely. Infact anything AFTER a # on a line is taken as a comment. Why would you want it to be ignored? Well comments are for the programmers. They are used to explain what the HELL you were thinking at the time. Just comment things :D Its also good practice to put the name of the file in a comment right below the shabang. The next comment is describing the purpose of the script. Again this is good practice. Now normally you would also put your name, email, and what license the script is under in a comment below this, but it isn't needed for tiny scripts like this. 

So finally we reach ```
echo "Hello World!"
``` This is the first real instruction. It merely prints out "Hello World!" to the screen. echo prints whatever is in the "" to the screen. Quite simple. Finally we get to ```
exit 0
``` This tells the script to quit and return an exit status of 0 (C and C++ programmers, this is exactly like return 0; in main). However this isn't mandatory. The script would have quit anyway, but its good practice to return an exit code to the system. 0 means everything is happy and everything worked. 1 typically means something went wrong. There are other codes but they are program dependent. Don't worry about them yet, I'll tell you what they are useful for later.

So how do we run this sucker? Easy! Save it, then do ```
bash ./HelloWorld.sh
``` If you want to be able to run it without the "bash" in front just make it executable. You remember how right? Here is a reminder. ```
chmod a+x HelloWorld.sh
```

If all went well then the output should look something like this
```
[kyral@HyperDream ~]$ bash ./HelloWorld.sh
Hello World!
[kyral@HyperDream ~]$ 
```

Now a small note on naming conventions. You notice that I named it with a .sh extension. This is the normal convention for shell scripts. I however only use it for my personal scripts. If its a system shell script, then I drop off the .sh. Remember, Unix systems don't use the extension as the primary means of determining filetype! Ready for more? Here is the next example!

```
#!/bin/bash -
# HelloWorld.sh
# A Shell Hello World

HELLO="Hello World!"
echo ${HELLO}
exit 0
```

Looks kinda the same, but different no? Like mainly that big HELLO. Thats called a variable, and any programmer knows about them, but if you don't its no biggie. Variables are merely containers for data. So what I do with this line ```
HELLO="Hello World!"
``` is to tell the shell that in this script until I say otherwise, HELLO means "Hello World!". Now an important note, Bash is picky about whitespace on this one. So it HAS to be ```
VARIABLE=VALUE
``` with no spaces between VARIABLE, the =, or the VALUE. This is one of Bash's little gotcha's. Got it? Good. On to the next line. ```
echo ${HELLO}
``` The echo looks different no? What is it gonna spit out? Well, its gonna spit out the value of HELLO. But whats with the ${} around it? Well, thats how you reference a variable after you have given it a value, so ${HELLO} tells Bash "Whatever is in HELLO, put here". Now people will say "You can also do $HELLO", and they are right, but ${HELLO} is the newer style and recommended over the old style. Just a note. Anyway run this new version and it will do the same thing as the old version. Kinda fun no? Okay get ready we are jumping to a new topic..

```

#!/bin/bash

DATE=`date`
HELLO="Hello World!"
echo -e "${HELLO}\nToday is ${DATE}"
exit 0

```

Yea I'm getting lazy..notice I dropped off most of the header lines :D Anyway there are a couple new things going on in here. Lets take a look! ```
DATE=`date`
``` Whoa! Whats going on?! What are those weird characters in the value? Those are called backticks and are on the same key that the ~ is on. They signal *command substitution*, which is basically replacing the whole thing (the `date` thing) with the output of the command between the backticks. So in this case it means that DATE gets set to the output of the date command. This is very useful. You notice one more line is different. ```
echo -e "${HELLO}\nToday is ${DATE}"
``` Whats that -e option to echo?! Its related to the \n in the echo string. \n is an escape sequence (I went over those right?) that represents a newline. Now, echo is dumb. It will just spit out escape sequences without making them mean their special meaning (Meaning it would print out literally "\n"). The -e option makes echo respect the escape sequences, so when you run this, "Today" (and everything that follows) will appear on a newline. Cool no? Oh one more note. We could have used Command Substitution in the echo as well. So this would work too ```
echo -e "${HELLO}\nToday is `date`"
``` Got it? Cool... time for the next part..

---

### Post by ritcey on 2006-09-30
Just scanned this thread, Kyral - well done, we old-timers can forget how intimidating the shell can be to newcomers.  One tidbit from your first post -- the root shell uses '#' instead of '$' as a visual clue that you are, indeed, root so you should think twice before doing anything hugely destructive...

---

### Post by xpod on 2006-09-30
GULP.......:shock: 
Im still trying to comprehend the commands..;) 
Good stuff m8

---

### Post by Kyral on 2006-09-30
We aren't done yet. We still have a bunch to cover! What language doesn't have logic flow?!

**Decisions and Arguing**

Consider the following

```

#!/bin/bash

if [ $1 -eq 1 ]
then
     echo "Its ONE!"
else
     echo "Its NOT ONE!"
fi

exit 0

```

Weird things are happening! Lets break it DOWN! ```
if [ $1 -eq 1 ]
``` This one looks really weird no? Well, this is the beginning of an if-then-else-fi block (obviously named). The if says "if the thing in [] (actually a command called "test") is true, then do the thing below me (after the then). Now lets break apart the []!. You should be able to spot that $1 is the short form of a variable call, but wait, we never gave a variable called 1 a value! Or did we? You see the variables $1 - $9 represent the so called "positional parameters", better known as command line arguments. So if you run the script with "./scriptname 2" then $1 is given the value 2. And if you are curious, $0 is always given the filename of the script as its value. You can echo it out if you want in the script. So now that we know what $1 means, what does -eq mean? Easy! It means "equals"! And the 1 is a literal number 1. So put it all together it means "Whatever is in $1 equals 1". THIS IS NOT A VALUE ASSIGNMENT!! There is a reason we use -eq and not = :D (Also programmers from other languages should note that -eq works mostly like ==). And the [] around it means "Tell me if this is true or false". So the ENTIRE line means "if whatever is in $1 equals 1". The next line is simply a then statement, and yes you can combine the if-then into one line like this ```
if [ $1 -eq 1 ]; then
``` but I don't like to and I'm the one giving the tutorial :P. The next line is a standard echo and only gets run if the thing in the if is true, and don't mind the indent, I just do it as a programming habit. The line after that is the else statement. It's purely optional, but its a good habit (and also VERY handy). It says "Well, if the thing up there in the if statement isn't true, do the thing below me". In this case its another echo. Also notice that else doesn't use a then keyword. Subtle but keep it in mind! Skipping the echo we see something odd, "fi". fi is if backwards and tells Bash that we are FINALLY done with this if-then-else statement. Its mandatory so don't forget!

Didja catch all that? Got it? Well, try this one on for size
```

#!/bin/bash

if [ $1 -eq 1 ]
then
        echo "Its ONE!"
elif [ $1 -eq 2 ]
then
        echo "Its TWO!"
elif [ $1 -eq 3 ]
then
        echo "Its THREE!"
else
        echo "Its...not anything I know"
fi

exit 0

```

We see new things! Like what is this "elif" thing?! It means "Else if" and is a way to test for multiple things. It basically says "Well, if the thing in the if isn't true...is this true? If it is then run whats below me". Its a compound statement! (And yes you can write it "else if") So what happens is that the program checks to see if $1 equals 1, if it does it spits out whats below it. If it isn't it then checks to see if $1 equals 2, and acts accordingly. Notice that elif needs a then keyword. Also notice that else is still sitting there at the bottom. Else is basically saying "If NONE of these are true, then do this". Its important to note that only ONE of these 4 echos will occur. As soon as it finds a truth in the if-else chain it bails out and jumps to whatever is after the fi. Note that if you didn't have the elifs and just normal ifs all the possiblities could occur. Something to keep in mind. Oh, and you can chain elifs as long as you want, but eventually they will get really nasty. This is why we have a new testing structure, called a "switch case". Check it out

```

#!/bin/bash

case "$1" in
        "1")
        echo "Its ONE!"
        ;;
        "2")
        echo "Its TWO!"
        ;;
        "3")
        echo "Its THREE!"
        ;;
        *)
        echo "Nada!"
        ;;
esac
exit 0

```

Looks like greek no? Don't worry, I'll help! The first line ```
case "$1" in
``` sets this entire thing up. It says "Okay, we are gonna start testing whatever is in $1 against a bunch of things until we hit the esac keyword (esac is to case what fi is to if)". The next block 
```
"1")
        echo "Its ONE!"
        ;;
```
is the test structure. "1") says "I want to see if whatever value we are testing is equal to whatever is before the )" Keep in mind Qouting is optional here, but its a good idea. If its true then it runs whatever is below it and jumps to whatever is after the esac. The ;; tells Bash that this is the end of the code for this test. So you can figure out what the rest means right? Well, with one exception. The last one. We are testing against *, but what is *? This last test is like an else. Its the catchall. It is saying "If none of these match, do this!". Got it? Good!

**Loopy Loops**

Decision making isn't the only thing we can do. We can repeat something over and over again. Its loop time!

For this one, please look at the example (horrible pun...)
```

#!/bin/bash

for num in 0 1 2 3 4 5 6 7 8 9 10
do
        echo ${num}
done

exit 0

```

Odd looking? Lets look at it. ```
for num in 0 1 2 3 4 5 6 7 8 9 10
``` This is most likely the most confusing part of the entire thing. This says "For every thing in the list after "in" assign that as the value of num in order and do whats between the do and the done". Jeez thats really confusing now. For loops are always hard to teach. I'll just step through it. Okay on the first time though, num gets the value 0, and then it jumps to the code between the do and the done and runs it. Then it goes back to the top, looks to see if there is anything more in the list, sees that 1 is sitting there, and assigns num to 1 and jumps to the statement between do and done again and to the top again and so on until it has gone through the entire list. Only then does it jump to the stuff after done. Did that make sense? I hope it did. It'll make sense if you run it! Oh here is something else. You can use command substitution to generate the list. So something like this 
```
for i in `ls`
do
echo ${i}
done
```

This will spit out all the files and dirs in your current directory (Yah I know that ls does this anyway, but you get the idea :D)

Okay you all still with me? We are ALMOST DONE! Just one more loop! Its the cousin of the for loop, the simpler while loop

```

#!/bin/bash

num=0
limit=10

while [ ${num} -lt ${limit} ]
do
        echo ${num}
        num=$((${num}+1))
done
exit 0

```

This also shows another sign of Bash's pickyness. Anyway we have already seen variable declarations and assignment. But whats up with the while? ```
while [ ${num} -lt ${limit} ]
``` You should recognize the test construct from our talk on if-else. The -lt means "less than" so what the line is saying is "while whatever is in num is less than whatever is in limit, do whats between the do and done". Makes sense. It goes into the loop body, runs the code, then checks to see if the while condition is false yet. If it isn't to repeats the whole process. Now one thing to note is this line ```
num=$((${num}+1))
``` Thats NASTY looking and one of the things I honestly hate about shell scripting. In a nutshell that adds one to the value in num and makes it the new value of num. Notice that we are both referencing a value in num and modifying at the same time. The shell evaluates whats on the right side of the = first, so we don't get a loop going (within a loop lol). The $(()) is an arithmetic evaluation construct. It says "I am the value of the expression inside the (())" Now here comes the thing I hate. Practically every other language would let you do something like "$num = $num + 1;" (This is Perl in this example) but Bash doesn't. Pain in the tush. (In case you want to know, almost every other language has an even BETTER shortcut for this. Again in Perl it would be "$num += 1;" and in the case of just adding or subtracting 1 from something it gets even more compact "$num++;" or "$num--;", and almost every other language has pretty much identical things, but this is WAY offtopic :D) Sorry for the rant :P Anyway do you get it? Good. Also I have to talk about the danger of infinite loops. Everyone does it, even the best of programmers. And they are quite easy to do accidently. What if we incremented limit instead of num? Then the while condition would never become false and the loop would run endlessly. In that case you'd have to CTRL-C your program to kill it. If you really wanted to do an infinite loop intentionally you could just do something like ```
while true
``` I know I have done it. In this case whenever you wanted to break out of it you'd use the word "break". Just thought you'd like to know.

Well thats the end folks. I hope I made sense. I *really* suggest reading the [Advanced Shell Scripting Guide]("http://tldp.org/LDP/abs/html/index.html"). Its far better written than I can pull.

Well, this is the most likely end to Terminal For Beginners. I enjoyed it, I hope you all find it useful, and keep exploring, keep learning, and don't be afraid to break some things :D

---

### Post by handy on 2006-10-02
Great Tute's Kyral... :KS

---

### Post by Tamil on 2006-10-07
Thanks **Kyral**.

---

### Post by gromag on 2006-11-10
Just registered on this forum, and few hours that I'm running Ubuntu. I spent all night trying to install my wireless card and finally I managed. :-D Thanks to your tutorial I could get myself around the Terminal. 
Thank you very much! :eek:

---

### Post by brennydoogles on 2007-03-19
I am brand new to Linux, and I really like this tutorial. However, I still don't understand the concept of Symlinks. Is it similar to a windows shortcut in the linux terminal?? Thank you all so much for all of your help!!

---

### Post by heimo on 2007-03-22
> **brennydoogles said:**
> I am brand new to Linux, and I really like this tutorial. However, I still don't understand the concept of Symlinks. Is it similar to a windows shortcut in the linux terminal?? Thank you all so much for all of your help!!

Let me selectively quote this page:
[URL="http://en.wikipedia.org/wiki/Symbolic_link"]http://en.wikipedia.org/wiki/Symbolic_link
[/URL]
> 
In [computing]("http://en.wikipedia.org/wiki/Computing"), a **symbolic link** (often shortened to ***symlink*** and also known as a ***soft link***) consists of a special type of [file]("http://en.wikipedia.org/wiki/Computer_file") that serves as a reference to another file or directory. [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") [operating systems]("http://en.wikipedia.org/wiki/Operating_system") in particular often feature symbolic links.
> 
For people familiar with the [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") [operating system]("http://en.wikipedia.org/wiki/Operating_system"), a symbolic link resembles a [shortcut]("http://en.wikipedia.org/wiki/Computer_shortcut"). Windows versions previous to Windows Vista, however, do not build general symbolic links into the filesystem; instead, they use a standardized shortcut file format (*.lnk) which many programs recognize at application-level. Thus, a program accessing a shortcut with the standard Windows API will end up reading, writing and querying information for the shortcut file itself (.lnk) rather than the file the shortcut points to. So, unlike symbolic links, Windows shortcuts lack transparency for [I/O]("http://en.wikipedia.org/wiki/Input/output") functions. Windows supports symbolic links directly beginning with Vista. The local system processes all symbolic links even when the symlink refers to a remote file location, whereas directory links are processed on the server.[[1]]("http://en.wikipedia.org/wiki/Symbolic_link#_note-VistaSymbolicLink").

---

### Post by Dirty_Jose on 2007-04-01
Hey, thanks for your help.  I'm new to this thing called xubuntu, and it's so easy to get lost in terminal!

Oh, and sport your anime love like a badge!

---

### Post by chaits on 2007-04-21
Thanks Kyral for all your lessons

---

### Post by tyboon on 2007-05-05
Kyral that was great...Thnax a lot...giving such an info for terminal...A wide world is just opened in front of me..
Thanx again...
Freetings from Athens Greece...
:guitar:

---

### Post by UFF on 2007-07-14
Just what I needed! Thank you so very much :D

---

### Post by Schenley on 2007-07-14
Best thread on the forum!  Thanks...I've cut and pasted the whole thing into a document.

---

### Post by The Scientist on 2007-07-19
You ARE a fanboy, kyral ;)

Thanks a lot for this tutorial,VERY HANDY, very good written and very humorous.

---

### Post by Kooya Kurt on 2007-08-15
Man, Kyral. you sure know what the (ubuntu/linux) world needs! I'm printing all of this. Thanks! Can't wait to see more of your how-tos. :KS

---

### Post by ThyDarken on 2007-09-11
Your anime directory lacks of Death note :p
But great job on this guide, really really helped me a lot!

---

### Post by DerMeister on 2007-09-13
I registered to Ubuntu Forums just to post a thank you to Kyral (I'm not quite sure why I haven't registered earlier...). I have been using K/Ubuntu for almost a year now, and am familiar with most of the stuff contained in your posts, but there are always those quirky details you miss.

THANKS A LOT man! a trully helpful and get-to-the-point tute! I mind the unwitty jokes though. :)

just kidding, man. keep it up!

---

### Post by combatwombat_nz on 2007-09-20
Thanks Kyral, you've inspired me...
here is a script I wrote to change the directories in a Samba HOMES folder to be owned by the name of the directory (eg jsmith is owned by jsmith)

```

#!/bin/bash
for i in $( ls);
do 
chown $i:root $ -hRf
chmod 700 $i -Rf
done

``` 

create the above code in the main directory concerned, using nano; eg:
sudo nano chperms
type the code
CTRL-X, Y
then type 
sudo chmod +x chperms
then
sudo ./chperms
will run it.
it obviously throws an error when it tries to change chperms' owner to chperms, but that's okay, the rest are done.
:)

---

### Post by Abhimanyu on 2007-09-28
> **Kyral said:**
> Terminal for Beginners: PART TWO: File fun!

Well, you know how to move about in the terminal, and hopefully it isn't as scary anymore. But all you know how to do is move around. Thats no fun! I also told you that the terminal can be very powerful, but again I haven't shown it. Well file operations are very fun in the terminal. And powerful as well. Here we go again!

I assume you remember how to naviagate, so I won't go over that again. There are three basic commands for file operations. cp (Copy), mv (Move), and rm (Remove, basically Delete). cp and mv function pretty much the same way, so I'll cover those first.

Okay I'm at home. Time to ls.

```
kyral@GNUGeneration:~$ ls
14560-firefox-thunderbird.tar.gz
19506-pinux's-tux-cursors-theme-0.3-cur.tar.bz2
2005-08-03--10.05.26
2005-08-03--10.07.23
2005-09-25--20.15.58
20178-Ambidexter.Silver.tar.gz
ABC Exams
anime
Crystalcursors.tar.bz2
cs142
DarkFirePic.png
debpacks
Desktop
document.png
ffmpeg-0.4.8-2.rh80.dag.i386.rpm
ffmpeg_0.4.8-3_i386.deb
Final Fantasy 3.zip
finddeps.sh
firefox-thunderbird
flash
freenx-0.4.2.tar.gz
GDM-InThisWorld.tar.bz2
gftp_2.0.18-1_all.deb
gftp-common_2.0.18-1_i386.deb
gftp-gtk_2.0.18-1_i386.deb
gftp-text_2.0.18-1_i386.deb
gnome-clipboard-daemon-1.0.bin.tar.bz2
GNOME-GNOMEInSilk_1280x1024.png
hallelujah.mp3
imacgirl_v3_1280x1024.jpg
is400
Jeko_xchat.png
keitaroanimeICON.jpg
keitaroanime.jpg
Manga
MCity-Aero-ng-default-1.1.tar.gz
mozilla-firefox.png
mozilla-thunderbird.xpm
mygraph.php
MyMusic
NVIDIA-Linux-x86-1.0-7667-pkg1.run
ONR_Meeting_10052005.doc
Oral Presentation Proposal.abw
Parallel_Dimensions.jpg
pi
pics_Full_Metal_Panic_Full_Metal_Panic_fmetalp00.jpg
PI.DAT
Presentation Proposal.abw
programs_sourcecode
public.key
Purposed ITL Build Software List.pdf
q2pres2day2.doc
Readme.txt
Resume.odt
Screenshot-1.png
Screenshot.png
sdsf.txt
Sealab 2021 - 101 - 20021008 - Radio Free Sealab.avi
Splash-GNOMEInSilkEvolving2Blurred.png
Splash-Linux_splash.png
StepMania-3.9-rc3
StepMania-3.9-rc3-linux.tar
super_pi
super_pi.tar
System_Stats_3.0
System_Stats_3.0.tar
The_Calling_-_Anime_Wallpaper.jpg
thunderbird_icon2.png
torrents
TransGaming_Drive
UbuntuCodeofConduct-1.0.txt
UbuntuCodeofConduct-1.0.txt.asc
ubuntu-logo.png
Ubuntu-tan_01-1280x1024.jpg
ut2004
web_sketch.xls
wget-log
wget-log.1
workspace
```

Yah I have a lot of stuff here, but then again its mounted on a 285 GB partition, so its not like I'm strapped. But I can clean it out. So lets play with those two screenshot files I have laying around from when I uploaded them to the UbuntuForums Gallery.

Copy time!

The syntax for cp is 

```
cp [options] <location of file> <where you want the copy to be made>
``` 

Now the locations can either be relative or absolute paths (remember those?) . Now wait a second? What are "options". Well those are optional! (*groan I can't believe I pulled that*). No those are options that affect how cp goes about its business and are prefaced with a "-". Common options are -i (interactive, it asks you to confirm every action), -r (Recurses into directories, means it basically grabs everything in there. Needed for copying directories), -v (Verbose, tells you everything its doing). You stick'em where I put [options] in the syntax. Well, enough talking. You want an example? Good 'cause I was getting bored. Lets copy Screenshot.png to Screenshot2.png

```
kyral@GNUGeneration:~$ cp -v Screenshot.png Screenshot2.png
`Screenshot.png' -> `Screenshot2.png'

```

Noticed I used the -v option. If I hadn't the second line would not have showed up. It just told me that it copied Screenshot.png to Screenshot2.png. A ls will confirm this
```

kyral@GNUGeneration:~$ ls
14560-firefox-thunderbird.tar.gz
19506-pinux's-tux-cursors-theme-0.3-cur.tar.bz2
2005-08-03--10.05.26
2005-08-03--10.07.23
2005-09-25--20.15.58
20178-Ambidexter.Silver.tar.gz
ABC Exams
anime
Crystalcursors.tar.bz2
cs142
DarkFirePic.png
debpacks
Desktop
document.png
ffmpeg-0.4.8-2.rh80.dag.i386.rpm
ffmpeg_0.4.8-3_i386.deb
Final Fantasy 3.zip
finddeps.sh
firefox-thunderbird
flash
freenx-0.4.2.tar.gz
GDM-InThisWorld.tar.bz2
gftp_2.0.18-1_all.deb
gftp-common_2.0.18-1_i386.deb
gftp-gtk_2.0.18-1_i386.deb
gftp-text_2.0.18-1_i386.deb
gnome-clipboard-daemon-1.0.bin.tar.bz2
GNOME-GNOMEInSilk_1280x1024.png
hallelujah.mp3
imacgirl_v3_1280x1024.jpg
is400
Jeko_xchat.png
keitaroanimeICON.jpg
keitaroanime.jpg
Manga
MCity-Aero-ng-default-1.1.tar.gz
mozilla-firefox.png
mozilla-thunderbird.xpm
mygraph.php
MyMusic
NVIDIA-Linux-x86-1.0-7667-pkg1.run
ONR_Meeting_10052005.doc
Oral Presentation Proposal.abw
Parallel_Dimensions.jpg
pi
pics_Full_Metal_Panic_Full_Metal_Panic_fmetalp00.jpg
PI.DAT
Presentation Proposal.abw
programs_sourcecode
public.key
Purposed ITL Build Software List.pdf
q2pres2day2.doc
Readme.txt
Resume.odt
Screenshot-1.png
Screenshot2.png
Screenshot.png
sdsf.txt
Sealab 2021 - 101 - 20021008 - Radio Free Sealab.avi
Splash-GNOMEInSilkEvolving2Blurred.png
Splash-Linux_splash.png
StepMania-3.9-rc3
StepMania-3.9-rc3-linux.tar
super_pi
super_pi.tar
System_Stats_3.0
System_Stats_3.0.tar
The_Calling_-_Anime_Wallpaper.jpg
thunderbird_icon2.png
torrents
TransGaming_Drive
UbuntuCodeofConduct-1.0.txt
UbuntuCodeofConduct-1.0.txt.asc
ubuntu-logo.png
Ubuntu-tan_01-1280x1024.jpg
ut2004
web_sketch.xls
wget-log
wget-log.1
workspace
```

Its there! Now lets remove it. rm uses syntax like this

```
rm [options] <path to file>
```

Again options are to be found. Practically EVERY command has options. Anyway, common options for rm are, -i (Interactive, same as cp, more important in this case), -v (same as cp), -f (force, make it delete. Needed for directories), -r (Recurse, again same as cp). Now look at those options and think about something people tell you about not running as root. Guess what THIS command would do (DON'T DO IT!) if you ran it as root.

```
rm -rf /
```

Yah, kiss your system goodbye, if you didn't hit CTRL+C fast enough. CTRL+C kills any command in progress and brings you back to the prompt. Anyway lets get rid of that screenshot copy.

```
kyral@GNUGeneration:~$ rm -v Screenshot2.png
rm: remove regular file `Screenshot2.png'? y
removed `Screenshot2.png'

```

Wait, it went interactive. Well thats because I overrode rm's default behavior in my alias' file so it always goes interactive unless I use -f. Nifty safeguard ;P

Now for mv. Again mv behaves just like cp, but it moves the files instead of copy. It also renames them. Yah what? It RENAMES? Think about it. When you rename you basically move the file to one of a different name. Oh I forgot the syntax.

```
mv [options] <location of file> <place where you want to put it>
```

It looks like cp! Thats because its almost the same thing. It has most of cp's options (-i, -v) and it also has rm's -f option. And they work the same way! Example time again! This time rename!

```
kyral@GNUGeneration:~$ mv -v Screenshot-1.png Screenshot2.png
`Screenshot-1.png' -> `Screenshot2.png'
```

It was renamed. Coooool. This means that the file known as Screenshot-1.png is now called Screenshot2.png.

Keep in mind you can also do this with directories, but chances are you'll need to use the -r option if you are using rm and cp.

Now on to a couple other things. I have been keeping a really awesome terminal secret from you, one that makes the terminal really powerful. Its called tab completetion. Now what is that?! Well, if you just type out the first few characters of a file or command or directory and hit tab, the terminal will try to complete the name for you. If its obvious what you want it will instantly complete it for you, saving you a load of typing. If its not, either type a few more characters and try again, OR hit tab once more and it will call up a list of possible completions. Keep in mind for files it will only work for whats in the path you are typing. Confusing. Yah I didn't word it good. Example time.

Okay I'm trying to get to /etc/apt/ from ~. So I start typing cd /e and hit tab. Well, from / there is only one thing that starts with e, /etc, so it would fill in. Now I have cd /etc/. I add a to get cd /etc/a and hit tab. Ooops, That isn't unique enough. There must be more than one thing in /etc that starts with a. So I hit tab again. Behold

```
kyral@GNUGeneration:~$ cd /etc/a
acpi/         adjtime       alsa/         anacrontab    apt/
adduser.conf  aliases       alternatives/ apm/          at.deny
kyral@GNUGeneration:~$ cd /etc/a

```

Notice that on the tab complete list directories are shown by having a trailing "/" Also keep in mind that I haven't hit return yet to enter the command. So it looks like I have to finish and type "pt" to get to /etc/apt. So see what I mean? When I tried to tab complete /etc/a it only looked in /etc for possible completions. Keep it in mind. And tab completion works with 99% of commands in the terminal for filenames. It also works with commands. Watch.

```
kyral@GNUGeneration:~$ ca
caesar         calibrate_ppa  canfield       cardinfo       cat
cal            caller         captoinfo      cardmgr        catchsegv
calendar       cancel         cardctl        case           catman
```

I typed in ca and hit tab. It gave me all the commands that start with ca. Nice!

Okay there is one more trick. You wanna see what a file contains? There is a command for that! Assuming you have read permissions, you can do it! (Permissions are another thing entirely). Remember I mentioned something called aliases? Well, I have a file that defines them. You wanna see it? The cat command is your friend.

```
kyral@GNUGeneration:~$ cat .bash_aliases
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
#alias ls='ls -Cha --color=auto'
alias df="df -h"
alias h=history
alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias aptsource='sudo gedit /etc/apt/sources.list'
alias aptUI='sudo apt-get update && sudo apt-get dist-upgrade'
alias aptI='sudo apt-get install'
alias aptR='sudo apt-get remove'
alias aptS='apt-cache search'
alias aptSh='apt-cache show'
alias debI='sudo dpkg -i'
alias sourcebuild='sudo apt-get source -b'
alias depbuild='sudo apt-get build-dep'

```

Cool huh? It will display ANYTHING! Even stuff that isn't text. Case in point...

Well there isn't a case in point because when I did it on a png a bunch of nonsense characters flew past and messed up my terminal. 

Last thing. You see those sudo commands? Sudo is how we do things in Ubuntu. It grants you Root power for the command that follows it, and then it puts you back as your normal login. Use it, love it.

Nice demo...:KS

---

### Post by rock-hopper on 2007-09-28
I would like to thank Kyral and all the other members who have contributed to this incredibly detailed work.

As a poorly-skilled novice with Ubuntu, this stuff is the absolute mother-lode.  It is gold dust.  It is the answer to a noob's prayer.

I'm beginning to run out of superlatives here, so I will just say, once again, thank you - Ubuntu rocks and so does Kyral

Best regards,

rock-hopper.

---

### Post by Hoonakwa on 2007-09-28
Much thanks for the short tutorial. I can remember some DOS from years ago. I want to give up window$ as soon as possible but its going to take some time to learn this stuff. I think installing programs is the most intimitating task in Linux, for me anyway. This tutorial has helped me a lot to understand where my files are and how to manipulate them some. 
 I think the thing I like the most about the Linux comunity is the willingness of everyone to provide help where they can.

Long Live Linux

---

### Post by mekon on 2007-09-28
Thanks for this tutorial. Your effort is appreciated.

---

### Post by aceboy on 2007-10-12
that was awsome tuts dude...

installed ubuntu yes'day.... n i wud say learnt so many things this nite while goign thru this thread..... 
 
nw i can feel da power of linux...

thanks a lot newyz....:):cool:

---

### Post by jimmywu013 on 2007-10-12
> **Kyral said:**
> 

So how do you edit this? Easy! Pop open a terminal and hit this

```
sudo gedit /etc/apt/sources.list
```

For the Kubuntu folks the command is SLIGHTLY different

```
sudo kwrite /etc/apt/sources.list
```

Then just edit it like a text file and save when you are done. Don't forget to update Apt afterward!

Just want to point out that you should never use sudo to start graphical apps.
See: 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

For gnome, use gksu
for KDE, use kdesu

Great tutorial!

Jimmy

---

### Post by cristovaum on 2008-03-17
Thanks a LOT!!!!!!!!!!!

---

### Post by The Beast. on 2008-05-06
The best quick guide ever....................
Thanks..................................

---

### Post by The Beast. on 2008-05-06
I just have a doubt though. I can use the "screen" command to open a player like vlc. But I cant use "screen" to open an image file. Is there any command that does this?

Also amarok does open with the "screen" command, but it also terminates immediately without me having to close it down. Is there a reason for this???

Thanks!!!!!!!!!!!!!!!!!!!!!

---

### Post by mkrahmeh on 2008-05-12
starting an application (like amarok) from the terminal means that the application is a child process of the terminal, so closing the terminal will close its child processes..

thx kyral for the gr8 efforts..

---

### Post by ZabiGG on 2008-05-12
Many thanks ;)

You should definitely ask that this thread be appended to the General installation guide sticky in the Absolute Beginners section.

I wrote a quick start for newbies too. I'll add your thread as a reference also.

---

### Post by mkrahmeh on 2008-05-13
kyral
can you make my life happier and post another tutorial here about *fstab* stuff and mounting concepts??
thx again :)

---

### Post by eddVRS on 2008-05-20
Kyral,

you are a legend. Thanks for your time and effort, it's been a huge help.
Since reading this, I've managed to set up an ftpserver and administer it via command line from my laptop!!
Thanks again,
Ted

---

### Post by digitalvectorz on 2008-05-20
> ```
kyral@GNUGeneration:~$ rm -v Screenshot2.png
rm: remove regular file `Screenshot2.png'? y
removed `Screenshot2.png'

```

Wait, it went interactive. Well thats because I overrode rm's default behavior in my alias' file so it always goes interactive unless I use -f. Nifty safeguard ;P



While setting an alias to make rm interactive by default is a nifty little safeguard, if you're starting to get familiar and used to the terminal, I wouldn't recommend it.

While the safeguard me work on your system, if you work on someone else's system that doesn't have that alias set up for rm, you run the potential of possibly removing a file(s) that you weren't intending on (and you won't have any confirmation dialogues for "check and balances").

Just keep that in mind.

---

### Post by digitalvectorz on 2008-05-20
> **Hoonakwa said:**
> Much thanks for the short tutorial. I can remember some DOS from years ago. I want to give up window$ as soon as possible but its going to take some time to learn this stuff. I think installing programs is the most intimitating task in Linux, for me anyway. This tutorial has helped me a lot to understand where my files are and how to manipulate them some. 
 I think the thing I like the most about the Linux comunity is the willingness of everyone to provide help where they can.

Long Live Linux


The best thing about making the transition from windows to linux is the rewarding experience of 'understanding' and the knowledge, in my opinion.  Just keep the ambition to push yourself to the linux-limits (numits?, heh) and don't be afraid to break things.

I'm going through the same task.  Learning about the installation process, setting things up, and it can be overwhelming and daunting, but the excitement comes from persevering and overcoming that task.

Good luck and never give up!

---

### Post by dragonpac on 2008-06-08
Just installed Ubuntu 8.04 on a thinkpad T42 and this is helping me a lot to get used to the terminal. My goal is not use the gui at all sooo thanks a lot for these tips, I really appreciate it!

---

### Post by ST47 on 2008-07-10
Noticed a few things I hadn't seen before. You have an alias:
...=cd...
What does that do?

---

### Post by reilus on 2008-07-11
This is really nice.  I grew up on DOS, so terminal wasn't that intimidating, but bash is different.  This is a great set of tutorials, and I'm going to check them out to make sure I didn't miss anything.  

One of the things that attracts me to Ubuntu is the terminal.  I like it.  Windoze is too sterile for my tastes.

---

