---
title: "many problems"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by marli2 on 2007-01-18
Right where do i start

I have 2 pcs 1x laptop () 1 desktop.
I have Kubuntu on the desktop with win2k(they are very happy living with each other)

My laptop has 64mb of memory so i installed kubuntu, it slowere than XP(i cant install 2k as it cant see any drives!?!)

so i tried to install Xubuntu got a hdd error?

tried deli-linux kernal panic or boot fail

its a beta so i gave up.

back to xubuntu went to write down the error and it eventully started to install but got stuck configering somthing beginning with A(sorry didnt not it was RATHER aNNOYED AT THAT POINT.

found out you could install Xubuntu from kubuntu :-)

did that. Sort of works ??

now here the fun bit... cant get apt to allow me to install xine extras??
its all greyed out, ive un edited the sorces.list file in etc/apt/
no difference!

same on my desktop??

tried easyubuntu failed!!!
will get some more prisise info but im really desperate aTM.

---

### Post by Garyu on 2007-01-18
The thing to start with is to say what your hardware is.

After that you really should try to be more specific about your problems. What kind of error messages you get and when you get them. Try to write things down on paper when something happens, and try to recall what you were doing prior to that.

Now, if your computer only has 64MB of RAM memory... That is one fourth of what I have on my graphics card (i.e. A LOT less than what my RAM is). This will probably mean that your processor is slower than a turtle without legs, no offence. Modern operatingsystems are not the best choice to run on such old hardware because it will first of all be really slow and secondly might hang because of lack of system resources. 

Maybe you should try to install older versions of Ubuntu, like Breezy, or even better, Hoary. They are constructed to be run on older and slower systems with less resources.

One thing to note also. Laptops usually have weird hardware configurations. You should try to find a list of supported laptops and make sure yours is listed. There is a linux hardware compatibility guide somewhere, but I don't have the adress right now. If your system is only partially supported you might face a lot of work to get it functional.

Good luck!

---

### Post by marli2 on 2007-01-21
OK!

I dont have ONE problem.
I have lots.

1) my latptop is a toshiba, I seem to have that working(ish) now 3 reboots seem to have done the trick.
Yes 64mb is why I installed Xubuntu.(any suggestion of better please say so AFTER solving No.4 as all my 200+ password emails are on my laptop!)

However. Desktop.

 1)cant get apt to allow me to install xine extras??
 its all greyed out, ive un edited the sorces.list file in etc/apt/
 no difference!

2)I down load the deb file for easy ubuntu and automatix.
doulbe click them and i get:
> ARK: Error - The utility is not in your path. Please install it or contact you system adminstrator(that would be me then :P)
Note: this works fine on the laptop.

3)went to the automatix site and followed the command line install.
Worked fine except i followed the guide for Edgy ](*,) 
When I run it i get an error message. then it quits.
Since I simply copy-pasted some lines from the site I have NO idea how to uninstall.
I noticed running the deb file gives you an uninstall option.

4)is there a way of putting my mail back up on the server? Firebird stripped all my mail before I could set it to "leave mail on server".

5)Is there a program that allows me to edit php and save directly via FTP? there is an ace little prog on 'doze called notepad++ i use. it dont ftp though.
6) tried this:
simon@Jami-dodja:~$ sudo apt-get install mozilla-mplayer
Password:

got this!!!
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) but it is not installableor
                            mplayer-nogui (>= 1.0-pre5) but it is not installableor
                            mplayer-powerpc (>= 1.0-pre5) but it is not installableor
                            mplayer-g4 (>= 1.0-pre5) but it is not installable
E: Broken packages
simon@Jami-dodja:~$

7)CDs wont play??(I have sound)


lynix(its my OS i'll mis-pronunce if I want to)could replace windows if I could get around the problems.

---

### Post by Garyu on 2007-01-21
First of all, you still haven't said ANYTHING about your hardware. What processor, what motherboard, how much RAM, what graphics card, how big harddrive, and so on... Are things you will need to know.

[http://old-releases.ubuntu.com/releases/5.04/](http://old-releases.ubuntu.com/releases/5.04/)
Get a Hoary installation CD from this adress and start over would be my recommendation with your old hardware. Alternately, if you want to use some newer software:
[http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/)
Still, don't expect anything to be better just because you choose a newer version. On old hardware it is probably better with an old version. Just like it would be better to run Win95 than to install Windows Vista (because Vista probably wouldn't even start).

As for your e-mails... I have never heard of a way to put them back on your POP-server. Unless you forward them to yourself. But you can copy your /home and save your e-mails that way. I would guess they are in some directory like /home/.thunderbird/ if you only want to save your e-mails and discard the rest of your home directory.

---

### Post by marli2 on 2007-01-21
OK.
Laptop wise im quite happy, so i can wait for installing a new OS.

However the problems I NEED solving people are just aviolding
THEY DONT SEEM TO BE HARDWARE???

but i'll post my hard ware
What processor,AMD athalon 2500+
 what motherboard, SiS 8A(somthing will need to restsrt to find out exact )
how much RAM, 1Gig ram
what graphics card, nvidaia 5200
how big harddrive,80 gig HDD split into 6 partitions(Win/Ext3/Swap/games/data/apps)

---

### Post by Garyu on 2007-01-21
OK, finally we know that your desktop is actually quite alright hardware wise. That was quite important information as we can be sure that both Dapper and Edgy should work fine on your hardware for the desktop computer. 

As for your errors, I can only begin to guess without specific error messages or logs. What you have provided seem very strange and I have never seen anything like that before. If I were in your position, with a newly installed system, I would just wipe the partition and start over with a fresh install. Yes, you will loose some time, but it might work better. From your english I gather that you are not from an english-speaking country. Are you installing in a different language? This has caused some strange errors for me sometimes. Make sure you install your system in english, and then change to your local language (swedish in my case) afterwards when everything is installed and functioning (what I usually do is search for "swedish" in synaptic and install those things I see fit). This is the best suggestion I can come up with right now.

---

### Post by marli2 on 2007-01-21
FAR!!!!
FAR!!!
thats your answer!
Sorry about my english. I am english but I'm really frustrated so my typing is a bit erretic.
>  I can only begin to guess without specific error messages or logs.
so here goes.
1)cant get apt to allow me to install xine extras??
 its all greyed out, ive un edited the sorces.list file in etc/apt/
 no difference!
what more do you want?
2)I printed the error and how I get it.
3)I didnt mention I am using Drake thats why the instruction for edgy would be a problem.
I need to uninstall Automatix and install the drake version. the error message is:
> Alert. This version is for Ubuntu version 6.10 only
6)Its all there! straight out of Konsole

Format And Reinstall?!?!? 
Sorry but i'm getting frustrated.I seem to be thwated at every turn](*,) ](*,)

---

### Post by marli2 on 2007-03-17
hello bump.
sorted the email problem. so looking for a new distro for my laptop.
(currently runnig XP but is sloooooooo....)
Heres what I need.
will install on a toshiba portage 3480CT with 64mb(and run smoothly)
will have an idiots guide install instructions OR a idiots install(aka windows)
will allow me to browse tinternet.
will have FTP s/w installed as spec.
has good email S/w installed or easily added.
will allow(in future) mp3 playback.

As you can see spec wise im not asking for much, however it seems highspec=usable while lowspec=fast=hard to use.

oh yeah still got the problems on the desktop

---

