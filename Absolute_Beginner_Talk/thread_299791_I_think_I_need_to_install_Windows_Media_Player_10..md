---
title: "I think I need to install Windows Media Player 10. What do you think?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Tamacracker on 2006-11-14
What's up guys, I have a Toshiba Gigabit F10, which is a Mp3 player. 

The only way it can install is if Windows Media Player 10+ is also installed. This is the way it is with Windows at least. 

If I can get rid of the MP3 issue, I will no longer use Windows again. 

The thought the popped into my head is, download and install Windows Media Player 10 with CrossOver Office. Then attempt to install my MP3 player's sync software. If I try to install it with CrossOver Office without the Windows Media Player already installed, program for my mp3 player will NOT even attempt to install. 
:-k 

What do you guys think? I really need this MP3 player to be compatible with Kubuntu Edgy... if it is, bye bye to Microsoft Windows FOREVER!

---

### Post by aysiu on 2006-11-14
It's too bad you didn't read [this review](http://www.mobilewhack.com/reviews/toshiba_gigabeat_meg-f10_digital_audio_player.html) before you bought it: > Not recommended, clumsy to use. Software is not intuitive. No drag-and-drop. It would be okay if Toshiba updates the software which is not likely to happen. For future reference, I know Sandisk players (I have one) are drag-and-drop; no extra program needed.

I know that doesn't help you *now*, but.. for the future.

---

### Post by szf on 2006-11-14
> **Tamacracker said:**
> What's up guys, I have a Toshiba Gigabit F10, which is a Mp3 player. 

The only way it can install is if Windows Media Player 10+ is also installed. This is the way it is with Windows at least.

Aye. There appears to be a broken-by-design idea-virus with `iPod alternative` [mp3 players]("http://ubuntuforums.org/showpost.php?p=1738413&postcount=24") sold in the U.S. (at least).

> **Tamacracker said:**
> If I can get rid of the MP3 issue, I will no longer use Windows again.

I fear you may have consigned yourself to the Windows camp with this investment. :(

---

### Post by 3rdalbum on 2006-11-14
I doubt it would work with Crossover, maybe with VmWare. The MP3-player-loading programs generally require direct access to the USB, and I've had no success running my MP3 player's loading software on WINE. It runs, but it doesn't detect the MP3 player.

There are three ways that MP3 players work:

1. Drag and drop, no database involved.
2. Database on the same partition as the music.
3. Database on a kind of hidden partition.

An iPod uses Number 2, so some Linux developers reverse-engineered the database format and developed programs to create and modify the database on the iPod - this work has resulted in GTKpod and Amarok. Hopefully, if you're lucky, the Gigabeat uses this method too; so you could try working out how the database works and then modifying the file directly or writing a Python program to do it for you.

My MP3 player, and possibly yours, uses Number 3 - I don't even know if it's possible to gain access to the hidden partition. I've not had success in it yet.

---

### Post by Tamacracker on 2006-11-15
When you say Database in the same partition as the music, do you mean the installation of the files that belong to the MP3 player's software is on the same partition as the MP3 files?



With Windows, I used to have my Gigabeat program on my C: Drive and I kept my music/pics/movies etc.. on the D: Drive. It was still accessable, and able to upload the songs onto my MP3 player via Gigabeat software.

This is my MP3 player by the way: [http://www.bizrate.com/mp3_mediaplayers/toshiba-gigabeat-f10-10-gb-mp3-player--pid319232893/](http://www.bizrate.com/mp3_mediaplayers/toshiba-gigabeat-f10-10-gb-mp3-player--pid319232893/)

Anyways, I haven't attempted to download Windows Media Player until I got some opinions. I guess I'm out of luck then.

---

### Post by macdo on 2006-11-15
It seems to me that [this]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.gigabeat.net%2Fmobileav%2Faudio%2Feula%2F&langpair=ja%7Cen&hl=en&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") page talks about the firmware of the Gigabeat being based on linux; if that's so, I can't imagine that there isn't some way to get it to talk to your Ubuntu. 

You *have* tried plugging it in, I take it. Have you tried syncing it using Amarok (a KDE player)?

---

### Post by Tamacracker on 2006-11-15
Yeah when I plug my MP3 player into the dock, (dock is connected to PC via USB) it automatically mounts my MP3 player as a drive, just like how windows does it. I can access the the mp3 player (hard drive) but the thing is, it's the MP3's software that does all the uploading and deleting of files in my mp3 player. So if I can get Linux and Gigabeat to recognize each other then I'm in the clear. 

You mentioned to use Amarok, you know that's funny, because I haven't taken the time to try it. When I get home (currently at work) I'll plug my MP3 player into my dock, open Amarok and see if I can get Amarok to recognize my mp3 player, if so.. that'd be sweet and a lot easier on me than having to install two "Windows" application just to be able to upload and delete files with my MP3 player.

Oh and yes, the software is linux based... and also supposedly the GUI (something like that) of the MP3 player is also Linux based.

---

### Post by echo $USER on 2006-11-15
[http://www.jetaudio.com/](http://www.jetaudio.com/)

All cowon's devices are linux compatible, PnP.  Even has it printed on their boxes, got to love that.

---

### Post by avihappy on 2006-11-15
Make sure you tell amarok to treat it like an Ipod. Thats how got some other WMP10 only player working.

---

### Post by Tamacracker on 2006-11-15
Thanks for the info avihappy and to you all. 

I'll be back home and will test it in 2 hours or so. If this is successful I'll make sure to to make another thread on a "How To" for the Toshiba Gigabeat F10 MP3 Player :D

---

### Post by jimmygoon on 2006-11-15
LOL.

LibMTP

---

### Post by Tamacracker on 2006-11-15
OK I have an update.

I opened Amarok and then hooked up my MP3 player. Amarok popped up a window askin to name the device and mount the device.
So I entered in the mount box: /media/GIGABEAT

After that it's askin me to enter the pre-connect command and the post disconnect command.

This is where I'm stuck. 

Also I picked the option of "Generic Audio Player".
I don't know if I should have done that or picked something else... can you guys help me out?

I forgot to mention, that the Gigabeat program converts the file to .SAT

---

### Post by Phalangees on 2006-11-25
I'm trying to figure this out because I too have a F10. I recently got the firmware updates which fix all the little issues. You can drag and drop when it is in the docking station which is very easy to hook up.

Is their anyone else who has tried to mount their gigabeats? or any mp3 player for that matter in amarok.

---

### Post by chimay1 on 2006-11-25
> **Tamacracker said:**
> What's up guys, I have a Toshiba Gigabit F10, which is a Mp3 player. 

The only way it can install is if Windows Media Player 10+ is also installed. This is the way it is with Windows at least. 

If I can get rid of the MP3 issue, I will no longer use Windows again. 

The thought the popped into my head is, download and install Windows Media Player 10 with CrossOver Office. Then attempt to install my MP3 player's sync software. If I try to install it with CrossOver Office without the Windows Media Player already installed, program for my mp3 player will NOT even attempt to install. 
:-k 

What do you guys think? I really need this MP3 player to be compatible with Kubuntu Edgy... if it is, bye bye to Microsoft Windows FOREVER!

I was just on Media Player 10 and I hated it.  That is why I have come to linux, and so far I love it.

---

### Post by jackfrost132 on 2006-12-11
I've been using songbird for a bit now and it seems to work great, I believe it has syncing options, but I don't really have a device I want to sync with it to find out. A guide for installing it can be found at [Ubuntu Guide]("http://www.ubuntuguide.org") and there is also the [Songbird Website]("http://www.songbirdnest.com").

---

### Post by ed_d on 2006-12-11
> **Tamacracker said:**
> Also I picked the option of "Generic Audio Player".
I don't know if I should have done that or picked something else... can you guys help me out?

Like someone said before, use the ipod instead of generic audio. Then just drag and drop into the playlist folder

---

### Post by macdo on 2006-12-12
Tamacracker: try mounting it first - or maybe ```
mount /media/F10
``` as a preconnect command, if your /etc/fstab is set up correctly...

---

### Post by szf on 2006-12-12
> **Tamacracker said:**
> 
I opened Amarok and then hooked up my MP3 player. Amarok popped up a window askin to name the device and mount the device.
So I entered in the mount box: /media/GIGABEAT

After that it's askin me to enter the pre-connect command and the post disconnect command.


Lazyweb: Are possible pre-connect an disconnect commands such as ```
sudo /sbin/modprobe <some GIGABEAT module>
``` and ```
sudo /sbin/rmmod <some GIGABEAT module>
``` applicable?

---

### Post by sgamer on 2006-12-15
[http://amarok.kde.org/wiki/Media_Device:MTP]("http://amarok.kde.org/wiki/Media_Device:MTP")

that should give you some help. libmtp is not in the repos, you'll have to compile it from source, but it should be easy to work with. i'm working on doing this now with my gigabeat and i will post again if it goes well. :)

---

