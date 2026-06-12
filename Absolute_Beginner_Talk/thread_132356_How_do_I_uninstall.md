---
title: "How do I uninstall?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-02-18
I'm getting better I've only crashed my  computer twice so far today :) 

At the moment I need to know three things and I would be grateful if anyone can help.

a) How do I uninstall software that I have instaled wrongly and remove the icons from the Applications menu?

b) How do I remove my previous version of Ubuntu from my OS list at start up.  Using Breezy but I've still got Hoary on the system.

c) Is there anything else that can be used to listen to online radio other than RealPlayer as I'm not able to make it work.

Many thanks

---

### Post by cronholio on 2006-02-18
a) System->Administration->Synaptic

Search for Application name, mark for complete removal and apply changes. To remove something from the Application menu manually, go to Applications->System Tools->Application Menu Editor. That will not uninstall the software though.

b) Do this:

```
sudo gedit /boot/grub/menu.lst
```

Edit out the old release(s). Be careful not to mess up the file. Better make a copy of it first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

c) You can use VLC Player, Rythmbox or XMMS.

---

### Post by s6dalane on 2006-02-18
If you compiled the program yourself, then you just need to do:

> sudo make uninstall In the folder, where the source code is located.

---

### Post by KeyboardJockey on 2006-02-18
[QUOTE=cronholio]a) System->Administration->Synaptic

Search for Application name, mark for complete removal and apply changes. To remove something from the Application menu manually, go to Applications->System Tools->Application Menu Editor. That will not uninstall the software though.[/QUOTE]

OK I've done this and monitored the situation in the terminal window and did this.
[QUOTE=cronholio]
b) Do this:

```
sudo gedit /boot/grub/menu.lst
```

Edit out the old release(s). Be careful not to mess up the file. Better make a copy of it first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` [/QUOTE]

I'm going to do that later when I finished my session.  Just in case I mess up.

[QUOTE=cronholio]
c) You can use VLC Player, Rythmbox or XMMS.[/QUOTE]

Will they read RealPlayer rtms ?? (I think that this is what they are called ) from British Public Radio?  And if so how do I set this up?

Many thanks.

---

### Post by cronholio on 2006-02-18
> Just in case I mess up.

What you should do while editing the file is: Go to the end. You should see several entries reffering to your various kernels, like that:

```
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot
```

Delete all those that you don't want, from "title" to "boot". Save and Quit.

> Will they read RealPlayer rtms ??

I have no clue. Search Google or try it. If not, there is a RealPlayer version for Linux, I think.

> And if so how do I set this up?

System->Administration->Synaptic

Search for name of the software, mark for installation, apply changes.

---

### Post by KeyboardJockey on 2006-02-18
[QUOTE=s6dalane]If you compiled the program yourself, then you just need to do:

 In the folder, where the source code is located.[/QUOTE]

Tried that it just gives me.........


marc@ubuntu:~$  sudo make uninstall /home/marc/RealPlayer
Password:
Sorry, try again.
Password:
make: *** No rule to make target `uninstall'.  Stop.
marc@ubuntu:~$  sudo make uninstall ./home/marc/RealPlayer
make: *** No rule to make target `uninstall'.  Stop.
marc@ubuntu:~$

---

### Post by KeyboardJockey on 2006-02-18
Well it is time to admit defeat with RealPlayer10.  I'm resigned to having to boot up Windows XP to listen to online radio.

There must be an easy way to do stuff on here.

Its a bad comparison when it takes 15 hours to get a non working Real Player install and five mins for a working XP install :( 

I know I'm doing something wrong its just identifying just what.

---

### Post by cronholio on 2006-02-19
```
marc@ubuntu:~$ sudo make uninstall /home/marc/RealPlayer
```

This will not work. You are supposed to run that from the directory the soureces are in, usually. Only I assume you didn't install RealPlayer from source because it is closed-source. So, can you remember how you installed it?

And why do you want to uninstall it anyway? I think you want to USE it to listen to this certain radio station?

NB: RealPlayer uses a proprietary protocol for streaming which is not a good thing, generally speaking. Does that radio station offer an MP3 or AAC stream as well? There are thousands of very good stations that do. If you want to, try [www.radioparadise.com](www.radioparadise.com) for a start. Works like a charm in Ubuntu using VLC.

---

### Post by KeyboardJockey on 2006-02-19
[QUOTE=cronholio]```
marc@ubuntu:~$ sudo make uninstall /home/marc/RealPlayer
```

This will not work. You are supposed to run that from the directory the soureces are in, usually. Only I assume you didn't install RealPlayer from source because it is closed-source. So, can you remember how you installed it?

And why do you want to uninstall it anyway? I think you want to USE it to listen to this certain radio station?

NB: RealPlayer uses a proprietary protocol for streaming which is not a good thing, generally speaking. Does that radio station offer an MP3 or AAC stream as well? There are thousands of very good stations that do. If you want to, try [www.radioparadise.com](www.radioparadise.com) for a start. Works like a charm in Ubuntu using VLC.[/QUOTE]


I managed to get round the problem of using real player.  I found a command line on LinuxExpress tht I adapted to point to the station I wanted and voila it works :) I'm using VLC to listen to my fave station.  I'm going to leave the realplayer file on the drive for the moment as it doesn't seem to be doing any harm.  Besides that it is a 'locked' folder.  

I'm not sure if this locked folder is providing codecs for VLC but as it doesn't seem to be causing me any problems I'm going to leave it where it is.

I installed it via the command line and appeared to be mostly successful in unpacking the files but there was  a .bak format file that it wouldn't put in the RP folder.

---

