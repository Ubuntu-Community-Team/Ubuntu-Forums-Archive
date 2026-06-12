---
title: "i need a command"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-07
Hey there,

I just downlaoded real player off the website

i was wondering if anyone can give me the line i need to type in the terminal to activate it.  

Thanx

---

### Post by scxtt on 2006-07-07
what type of file is it?

---

### Post by IrishGangsta on 2006-07-07
Do u mean like if its a plug in?

Or do u mean is it Binary executable?

B/c its binary but when i click it, it doesnt open b/c its binary

---

### Post by scxtt on 2006-07-07
what is the full name of the file ... ?

---

### Post by IrishGangsta on 2006-07-07
RealPlayer10GOLD.bin

---

### Post by IrishGangsta on 2006-07-07
RealPlayer10GOLD.bin****

---

### Post by coderboi on 2006-07-07
> **IrishGangsta said:**
> Do u mean like if its a plug in?

Or do u mean is it Binary executable?

B/c its binary but when i click it, it doesnt open b/c its binary

Hi

I installed it over the holiday weekend. You need to make the file executable.  There should be installation instructions from the website where you downloaded it.  

If I remember correctly do this... 

chmod a+x <insert file name>

then you can execute it like this
./<insert file name>

---

### Post by scxtt on 2006-07-07
it's probably an installer ... try:
[indent]./RealPlayer10GOLD.bin[/indent]i'm thinking it'll supply you w/ an install screen ... older versions did ...

[size=5]&#8593;[/size] yup, make sure it's executable ...

---

### Post by IrishGangsta on 2006-07-07
i tried both ways u guys said and it said file or directory not found

---

### Post by scxtt on 2006-07-07
it'd be helpful if you copy/paste the output from your terminal in here ...

---

### Post by IrishGangsta on 2006-07-07
mike@Finnegan:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
mike@Finnegan:~$ sudo -i
root@Finnegan:~# chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
root@Finnegan:~# ./RealPlayer10GOLD.bin
-bash: ./RealPlayer10GOLD.bin: No such file or directory
root@Finnegan:~#

---

### Post by scxtt on 2006-07-07
are you in the same directory that the file is located in?

if you're not sure, do **sudo slocate -u**, wait til it returns, then do **slocate RealPlayer** ... make sure you're running the other commands where slocate tells you the file is ...

---

### Post by coderboi on 2006-07-07
are you typing these commands in the same directory that the file is in?

if not then you have to provide the full path to the file

---

### Post by IrishGangsta on 2006-07-07
root@Finnegan:~# sudo slocate -u
root@Finnegan:~# slocate RealPlayer
/home/mike/Desktop/RealPlayer10GOLD.bin

---

### Post by scxtt on 2006-07-07
chmod a+x /home/mike/Desktop/RealPlayer10GOLD.bin
cd /home/mike/Desktop/
./RealPlayer10GOLD.bin

---

### Post by IrishGangsta on 2006-07-07
ok that code seems to be working
Where should i put the real player file
any suggestions what would be the best choice?

---

### Post by scxtt on 2006-07-07
are you asking where you should install it to? -- if i were you, i'd just use the defaults, it should supply you with some ...

---

### Post by IrishGangsta on 2006-07-07
well the default i guess is my desktop
I'd rather not save it to desktop
And i am not that familair with linux file system
So a push in the proper direction would be much appreciated.

---

### Post by scxtt on 2006-07-07
if you are indeed seeing an installer when doing **./RealPlayer10GOLD.bin** it shouldn't install on the desktop, if it does (and i seriously doubt it), real player needs to get their act together ... it should install to typical directories like /usr/lib or /bin or /sbin -- all the normal places, and put config files in ~/.real or somewhere in your ~ directory ... none of which requires you to specify anything out of the ordinary ... you can move it to your home dir. but it shouldn't matter ...

something tells me you should have just installed the Helix player from the repos ...

---

### Post by catlett on 2006-07-07
Why don't you just install real player from synaptic package manager? I don't think you have to enable extra repositories but if it isn't in your synaptic you will have to,
Go to the top panel and navigate the menu to synaptic....System<Administration<Synaptic Package Manager
When it opens, enter realplayer into the search field and it will come up. Select it and choose "mark for installation". Then choose apply.

P.S Here is a screenshot of synaptic

---

### Post by IrishGangsta on 2006-07-07
im not sure what helix player is
But i tried using real player on a website and it gave me this message

Could not find an appropriate  HxPlay or a RealPlay in the system path to use an embedded player.

---

### Post by IrishGangsta on 2006-07-07
There is a RealPlay and a RealPlayer
RealPlayer can not be installed it told me but i do have RealPlay running

Is it because i need to add real player multi w/e to my source list?
If so how do i do that?

---

### Post by catlett on 2006-07-08
If you don't have extra repositories enabled, the easiest way is for me to just give you my list and let you copy it over into yours.
So open a terminal and enter this first ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```This will make a backup of your list. If you ever want your list back just enter this command ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```Now to edit. Enter this command ```
sudo gedit /etc/apt/sources.list
```This will bring up your list. Erase the entire page. Replace it with this. Just cut and paste it in.
> # 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free Once you copy it over save the document and close. Just make sure to refresh your apt cache with ```
sudo apt-get update
```Then you will have access to everything.

P.S. This is the guide I use when I setup a new install. Basically you now have the source list that they say to use, so just go there and cut/paste in the commands [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by IrishGangsta on 2006-07-08
Ummm, I believe my source list is good.
I added sum things to my source list i think i need.
This list is just for making it multi w/e
Can anyone look at this list and tell me that it is ok? 
please
thank you

------------------------------------------------------------------------
--------------------------------------------------------------------------


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by catlett on 2006-07-08
Your list looks fine. Just run ```
sudo apt-get update
``` and then run ```
sudo apt-get install realplay 
```to install realplayer.

---

### Post by IrishGangsta on 2006-07-08
i did all that
and it said done and successful
so is that it?
i have real player?

---

### Post by catlett on 2006-07-08
Yes. It will be under Applications<Sound & Video. If it isn't showing up, restart the menu with ```
killall gnome-panel
``` And it will appear

---

### Post by IrishGangsta on 2006-07-08
it's there!!!
thank you for all your help

Now that real player works, wanna help me with windows media player?

I did all the codes to make totem work, but on websites things that need windows media player do not work.

Have any spare time to help me with this problem?

---

### Post by catlett on 2006-07-08
```
sudo apt-get install mplayer
```
```
sudo apt-get install mozilla-mplayer
```Mplayer is the best for internet media playing. You should have mp[layer with those repositories.

---

### Post by IrishGangsta on 2006-07-08
ok catlett, 
On websites it shows the media player playing, it has to rejections against playing...BUT
The movie doesnt actually show, its a blank screen
But it acts like its playing.

and on other websites it says i need flash player 8, i believe i used Wine to downlaod firefox which downlaoded flash player 8 but i dont know how to acess that.

---

### Post by catlett on 2006-07-08
Mplayer should load and run. Did you install all the multi media codecs?
I never did the flash8 thing with wine. But I view everything with flash7 through my Linux Firefox. If you want linux flash 7 run this
```
sudo apt-get install flashplugin-nonfree
``` ```
sudo update-flashplugin
```



P.S. Lets check your plugins for firefox and see if anything is missing. Open firefox and clear the address box. Enter > about:pluginsin the field and hit go. This takes you to yopur firefox plugin page. Make sure you have a plugin for every category first and then we'll see if codecs are needed.

---

### Post by IrishGangsta on 2006-07-08
I ran your codes it says everything is up to date.

But i didnt do anything with mplayer.
How would i go about installing codecs?

---

### Post by catlett on 2006-07-08
It may be the need for win32codecs because it is windows media files your trying to play. (I am not positive but I have them and mplayer plays everything)
Anyways install them with these 2 commands 
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

---

### Post by IrishGangsta on 2006-07-08
can you tell me if video's play and u can hear music on this site?

[www.myspace.com/wast3ddays](www.myspace.com/wast3ddays)

i can not.

---

### Post by coderboi on 2006-07-08
yes, i can hear it

---

### Post by catlett on 2006-07-08
Now I see the issue. Myspace is pretty much windows only. It relies on you having the latest for flash and such.
Linux is still a small segment of the computer world. Companies like adobe (they make flash) think it is a waste of money to create software for linux.
To view myspace you will either have to dual boot with windows or run a windows virtual machine with vmware player from inside of linux.

Anyways, this is what I get on that site.

---

### Post by IrishGangsta on 2006-07-08
ok thats good to know now, that its not just my computer.  Right now i only have linux, but i used to dual boot windows, i am going to reinstall windows xp soon. I have an 80 Gb HD, so i'll use 40 Gb's for linux and 40 for windows.

But i did install flash player 8 using Wine, i just dont know how to access my Wine Firefox.

But thanks for all your help.

---

### Post by user1397 on 2006-07-08
> **IrishGangsta said:**
> ok thats good to know now, that its not just my computer.  Right now i only have linux, but i used to dual boot windows, i am going to reinstall windows xp soon. I have an 80 Gb HD, so i'll use 40 Gb's for linux and 40 for windows.

But i did install flash player 8 using Wine, i just dont know how to access my Wine Firefox.

But thanks for all your help.try lookin in /home/mike/.wine/drive_c/Program Files (you'll have to enable hidden folders, CTRL+H)
btw, the totem xine version works much better as a firefox plugin than the mplayer one.  try installing this: ```
sudo aptitude update && sudo aptitude install totem-xine-firefox-plugin
```then restart firefox

---

### Post by IrishGangsta on 2006-07-08
ok i did that code
where do you guys get these codes from? lol

---

### Post by 3rdalbum on 2006-07-08
Once you become familiar with Linux, you'll be able to construct terminal commands on your own, and understand what other's commands do. For instance, that last command tells a program called Aptitude to update the package list, and then to install a package called "totem-xine-firefox-plugin" from repositories.

Congratulations for getting so much working!

---

### Post by IrishGangsta on 2006-07-08
So then thats pretty kool, is there a code for quicktime.  Is quicktime in the respatories list?

also, is there any kool gdesklets i could put on my desktop
Like a penguin?!?!

haha
thanx for the help every one

---

### Post by user1397 on 2006-07-11
> **IrishGangsta said:**
> So then thats pretty kool, is there a code for quicktime.  Is quicktime in the respatories list?

also, is there any kool gdesklets i could put on my desktop
Like a penguin?!?!

haha
thanx for the help every onethe toem plugin will play most quicktime videos online, plus windows media player videos, and a lot of other ones.  but there are certain videos that it just can't play, yahoo movies comes into mind :-k

---

### Post by IrishGangsta on 2006-07-11
ohh ok thank you for the input

But i need help with another command

I know Ubuntu is Debian Based, And i know in debian u can click a window and throw it to the right of the screen and it moves it to a diff workspace.

Is there a command or anything to enable this for ubuntu?

---

