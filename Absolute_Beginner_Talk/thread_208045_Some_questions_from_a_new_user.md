---
title: "Some questions from a new user"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Deathcab on 2006-07-02
Hey all! First post here.

Anyway I have just installed ubuntu onto my system as well as Win XP. Got it installed all great everything works find except I have no clue how to "install" programs.  I cannot get plugins for firefox to work eaither.  I have google'd numerouse amounts of times and I still cannot figure it out. I found out I had to use the command line.. But i cant even find that.  Also how do I know where to put things? Like I dont know I am just a complete beginner. Any help would be appreciated. Oh and I cant get the programs in the Add/remove thing to install. 

Thanks!

---

### Post by IYY on 2006-07-02
> Also how do I know where to put things?

Your home folder. 

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by aysiu on 2006-07-02
You don't have to use the command-line most of the time:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by joshrobinson on 2006-07-02
[QUOTE=Deathcab]Hey all! First post here.

Anyway I have just installed ubuntu onto my system as well as Win XP. Got it installed all great everything works find except I have no clue how to "install" programs.  I cannot get plugins for firefox to work eaither.  I have google'd numerouse amounts of times and I still cannot figure it out. I found out I had to use the command line.. But i cant even find that.  Also how do I know where to put things? Like I dont know I am just a complete beginner. Any help would be appreciated. Oh and I cant get the programs in the Add/remove thing to install. 

Thanks![/QUOTE]

welcome to the community and ubuntu

first things first.. the command line used in an application called terminal.. its in applications > accesories

you can install applications through command line, edit files, move then rename replace delete.. pretty much everything

now onto the installing applications.. the easiest way for a beginner is to use synaptic. it is in system > administration > synaptic.. you just search for what you want, check it. and click apply

for flash and java websites (firefox plugins) some of them you have to manually install but they arent too bad.. automatix would be the easiest way for you to get up and running.. i just have to find you a link for it

---

### Post by meng on 2006-07-02
The link above is very good, by the way.

Well it sounds like you want to set up several things, programs and plugins, and you should be able to find help here. Give us a starting point - the first one or two things you want to do, then you can get help that way, although most likely the answer already exists in a previous thread.

The common plugins/codecs/alternative media players can also be set up using easyubuntu or automatix, but my preference is to "do it myself" using synaptic or apt-get.

---

### Post by aysiu on 2006-07-02
If you are one of those "when I remove it, I don't want all the other programs that came with it to stay behind" people, always use *aptitude* to install things instead of using *apt-get*.

If that last sentence confuses you, always use Synaptic Package Manager, then. Even if you use Kubuntu, it's worth installing Synaptic to use instead of Adept.

---

### Post by Deathcab on 2006-07-02
Thanks for the great response. How do I know what I have as to "drapper" or "breezy"? I have no idea what that is. Can I change it? Is one better than the other? Also say I have a .rpm file. I want to install it. How do I do that? I tried the Synaptic and searched for the .rpm file and couldnt find it.

---

### Post by aysiu on 2006-07-02
Dapper was released on June 1, 2006.
Breezy was released on October 13, 2005.

So, you probably want Dapper, as that's the latest version. You wouldn't install Windows ME if you had XP available, right?

Also, .RPM files are not native to Ubuntu. Those should be installed only as a last resort. The links posted above will help you out for that, especially the Psychocats one.

---

### Post by Deathcab on 2006-07-02
So where could I get drapper? Also is it an ISO? How do I know if i dont have it. And all the automatix things i found were for breezy and not for anyother one.

---

### Post by aysiu on 2006-07-02
Yes, Dapper's an ISO.

This will explain how to get it:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

This will explain how to install it:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

Automatix for Dapper:
[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by Deathcab on 2006-07-02
Hmm I think I already have drapper because thats where I got it from. Now just for this autimatix thing. I do it in the command line right? Just follow the directions from that link that you just gave me.

---

### Post by aysiu on 2006-07-02
Yeah, follow those instructions, and if you have questions, ask as they come up.

If you press Control-Alt-F1, you'll see if you have Dapper or Breezy. Then press Control-Alt-F7 to get back to the normal graphical mode.

---

### Post by Deathcab on 2006-07-02
I just read over the directions for automatix. Can anyone explain that more to me?


Edit. it said Ununtu 6.06

---

### Post by Deathcab on 2006-07-02
Hmm im trying this and I am trying to add the "deb URL" thing and it says cannot save.

---

### Post by aysiu on 2006-07-02
6.06 = Dapper (June 2006)
5.10 = Breezy (October 2005)
5.04 = Hoary (April 2005)
4.10 = Warty (October 2004)

Paste in the following commands into the terminal. First back up your sources.list ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit it as root ```
gksudo gedit /etc/apt/sources.list
``` Add this line to the end of the file: ```
deb http://www.beerorkid.com/automatix/apt dapper main
``` Save the file.

Get the keys for it: ```
wget http://www.beerorkid.com/automatix/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
``` Install Automatix: ```
sudo aptitude update
sudo aptitude install automatix
``` Run Automatix: ```
automatix
```

---

### Post by Deathcab on 2006-07-03
IS there anyway to get music from my XP HD onto my HD with linux on it?

---

### Post by aysiu on 2006-07-03
Yes. [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) will help you.

---

### Post by Deathcab on 2006-07-03
I have absoluitly no clue what that link was talking about. I tried it. And Im pretty sure thats for two partions not two harddrives. I have a whole seperate harddrive.  Any input?

---

### Post by learning on 2006-07-03
That link should work for you.  You have to mount your partition to swap the files.

Post your output from sudo fdisk -l

and someone may be able to help give you more detailed instructions.

---

### Post by aysiu on 2006-07-03
[QUOTE=Deathcab]I have absoluitly no clue what that link was talking about. I tried it. And Im pretty sure thats for two partions not two harddrives. I have a whole seperate harddrive.  Any input?[/QUOTE]
The instructions are for partitions, but the same principle applies for hard drives.

A partition will most likely be /dev/hda1 or /dev/hda5 something, and a second hard drive will most likely be /dev/hdb1, but it's the same idea--just a different location name.

---

### Post by Deathcab on 2006-07-03
It says i dont have permission to do some stuff? How do I login as root? Can I set it so Im always logged in as root?

---

### Post by Jagot on 2006-07-03
[QUOTE=Deathcab]It says i dont have permission to do some stuff? How do I login as root? Can I set it so Im always logged in as root?[/QUOTE]

Put 'sudo' before the commands.

There's a section that explains it here, and also about how to set up a root account properly:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Deathcab on 2006-07-03
Ahh Im sorry for all these questions. I do search before I ask though. Anyway Is there anyway to make my icons smaller besides the strech icon? They are HUGE. Do i get new icons?

---

### Post by Deathcab on 2006-07-03
Heres a SS of my desktop. Sorry for the HUGE file size. I dont know how to make the image a JPG or GIF.

[IMG]http://img287.imageshack.us/img287/1893/screenshot0iz.png[/IMG]

---

### Post by Jagot on 2006-07-03
[QUOTE=Deathcab]Ahh Im sorry for all these questions. I do search before I ask though. Anyway Is there anyway to make my icons smaller besides the strech icon? They are HUGE. Do i get new icons?[/QUOTE]

In a Nautlilus window, like when you go to your Home directory or something, click Edit, the Preferences.  In the middle you'll see Icon View Defaults, and here you can change the default zoom level - I have mine set at 75%.

---

