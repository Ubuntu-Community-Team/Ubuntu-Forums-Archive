---
title: "Sound issue on K3B"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-16
It seems now that everytime i use K3B i get the following message:

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.

Does anyone know what this means and how to correct it?

many thanks,

--
sophtpaw



i would dearly like this issue resolved, because it means a reboot to reset everything everytime i finsish using K3B.

Also, launch  k3b from command line everytime and would prefer to be able to run it straight from Applications/Sound and Video (maybe?)

thx folks   [-o<     (why has this icon not worked?)

--
sophtpaw

---

### Post by sophtpaw on 2005-08-16
[QUOTE=sophtpaw]It seems now that everytime i use K3B i get the following message:

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.

Does anyone know what this means and how to correct it?

many thanks,

--
sophtpaw




i would dearly like this issue resolved, because it means a reboot to reset everything everytime i finsish using K3B.

Also, launch  k3b from command line everytime and would prefer to be able to run it straight from Applications/Sound and Video (maybe?)

thx folks   [-o<     (why has this icon not worked?)

--
sophtpaw[/QUOTE]



Help! Pleeeze!   ](*,)

---

### Post by mo_x on 2005-08-16
Are you using kde?
You can disable the sounds in k3b.

---

### Post by sophtpaw on 2005-08-16
[QUOTE=mo_x]Are you using kde?
You can disable the sounds in k3b.[/QUOTE]

i don't want to disable the sounds in k3b. And anyways, i don't have sounds in k3b as it is. And i miss the trumpet at the end to announce completion, as it used to when i used k3b in SuSE's KDE.

But the real issue is that it seems to affect at least some if not all my other music applications. When i'm emusic.com and i want to listen to samples like i used to with xine, i can't and i have to reboot in order to reset as it were, i dunno what, and then i can listen to samples again.

Any further questions or suggestions?

many thx,

--
sophtpaw

---

### Post by mo_x on 2005-08-17
The soundcard is probably used by some other application, can you check for that?

---

### Post by Kapre on 2005-08-17
I have the same problem when I use K3B. I'm also sure that no application is using the soundcard. This error will only popout all of a sudden (when I try to burn ISOs).

Will it be due to the fact that I am using Gnome and not KDE as my desktop?

K

---

### Post by sophtpaw on 2005-08-17
[QUOTE=mo_x]The soundcard is probably used by some other application, can you check for that?[/QUOTE]

thx mox,

can you or someone tell me how to check whether the soundcard is being used by another application?

sorry, i'm a GNU/LInux babe
i need clear, precise, step by step instructions, so i can stick with you


--
sophtpaw

---

### Post by mo_x on 2005-08-18
I need some more information.
Are you using GNOME or KDE?
You can show the running processes by entering the following command in a console window::
> ps -e
Post the output here.

---

### Post by sophtpaw on 2005-08-18
Are you using GNOME or KDE?

Gnome is my default gui. Sometimes i switch into KDE to play and have a look.

You can show the running processes by entering the following command in a console window::

Post the output here.

conrad@x1-6-00-0b-6a-16-78-f0kernel:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
   22 ?        00:00:00 kacpid
   99 ?        00:00:00 kblockd/0
  137 ?        00:00:00 pdflush
  138 ?        00:00:00 pdflush
  140 ?        00:00:00 aio/0
  139 ?        00:00:00 kswapd0
  727 ?        00:00:00 kseriod
 1099 ?        00:00:00 kjournald
 1125 ?        00:00:00 udevd
 2404 ?        00:00:00 kjournald
 2405 ?        00:00:00 kjournald
 2406 ?        00:00:00 kjournald
 3812 ?        00:00:00 shpchpd_event
 4540 ?        00:00:00 khubd
 5066 ?        00:00:00 dhclient3
 5432 ?        00:00:00 syslogd
 5447 ?        00:00:00 dd
 5449 ?        00:00:00 klogd
 5476 ?        00:00:00 gdm
 5486 ?        00:00:00 gdm
 5524 ?        00:00:57 Xorg
 5527 ?        00:00:00 cupsd
 6042 ?        00:00:00 acpid
 6152 ?        00:00:00 freshclam
 6155 ?        00:00:00 dbus-daemon-1
 6167 ?        00:00:01 hald
 6625 ?        00:00:00 gdomap
 6630 ?        00:00:00 inetd
 6646 ?        00:00:00 nscd
 6705 ?        00:00:00 master
 6725 ?        00:00:00 qmgr
 6876 ?        00:00:00 atd
 6887 ?        00:00:00 cron
 6909 tty1     00:00:00 getty
 6910 tty2     00:00:00 getty
 6911 tty3     00:00:00 getty
 6912 tty4     00:00:00 getty
 6913 tty5     00:00:00 getty
 6914 tty6     00:00:00 getty
 7011 ?        00:00:00 x-session-manag
 7056 ?        00:00:00 ssh-agent
 7059 ?        00:00:00 dbus-launch
 7060 ?        00:00:00 dbus-daemon-1
 7062 ?        00:00:00 gconfd-2
 7065 ?        00:00:00 gnome-keyring-d
 7067 ?        00:00:00 esd
 7069 ?        00:00:00 bonobo-activati
 7071 ?        00:00:00 gnome-settings-
 7074 ?        00:00:00 gam_server
 7082 ?        00:00:00 xscreensaver
 7109 ?        00:00:00 gnome-smproxy
 7111 ?        00:00:01 metacity
 7119 ?        00:00:01 gnome-panel
 7121 ?        00:00:01 nautilus
 7123 ?        00:00:00 gnome-volume-ma
 7166 ?        00:00:00 update-notifier
 7168 ?        00:00:00 gnome-cups-icon
 7171 ?        00:00:00 gnome-vfs-daemo
 7177 ?        00:00:01 wnck-applet
 7179 ?        00:00:00 trashapplet
 7183 ?        00:00:00 mapping-daemon
 7198 ?        00:00:00 clock-applet
 7202 ?        00:00:00 notification-ar
 7204 ?        00:00:00 mixer_applet2
 7896 ?        00:00:00 mozilla-thunder
 7930 ?        00:00:00 run-mozilla.sh
 7935 ?        00:00:09 mozilla-thunder
 8704 ?        00:00:00 pickup
 8818 ?        00:00:00 netstat <defunct>
 9040 ?        00:00:03 firefox-bin
 9076 ?        00:00:00 gnome-terminal
 9078 ?        00:00:00 gnome-pty-helpe
 9079 pts/0    00:00:00 bash
 9089 pts/0    00:00:00 ps


that was a long transcript!
thx for the help again,

--
sophtpaw

---

### Post by sophtpaw on 2005-08-18
By the way, i have to run K3B from terminal. Not that it has anything to do with the problem, but just thought you should know. I don't know if it is the same for everyone in Gnome?

I would prefer to run it from Applications/Sound & Video, if possible

cheers,

--
sophtpaw

---

### Post by mo_x on 2005-08-18
This is quite a complex issue. You have esd running which is the sound deamom used in GNOME I think. I also see mixer_applet2 in the list that might keep your soundcard busy. For k3b you need to run artsd which is the sound deamon for kde.
To have them both is a bit problematic but maybe it can be done. Maybe you can run esd and artsd at the same time and mix them together through de alsa dmix plugin (you might want to do some searching on this).
First try the following:
- close the mixer applet and kill the esd process (I guess GNOME has some sort of taskmanager to do that)
- start artsd with the following command:
> artsd -a alsa
Now try if you get sound from k3b or some other kde application.

---

### Post by sophtpaw on 2005-08-18
[QUOTE=mo_x]This is quite a complex issue. You have esd running which is the sound deamom used in GNOME I think. I also see mixer_applet2 in the list that might keep your soundcard busy. For k3b you need to run artsd which is the sound deamon for kde.
To have them both is a bit problematic but maybe it can be done. Maybe you can run esd and artsd at the same time and mix them together through de alsa dmix plugin (you might want to do some searching on this).
First try the following:
- close the mixer applet and kill the esd process (I guess GNOME has some sort of taskmanager to do that)
- start artsd with the following command:

Now try if you get sound from k3b or some other kde application.[/QUOTE]

I got this back:
conrad@x1-6-00-0b-6a-16-78-f0kernel:~$ artsd -a alsa
unix_connect: can't connect to server (unix:/tmp/mcop-conrad/localhost_localdomain-2d06-4304e148)
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)

cheers,
--
sophtpaw

---

### Post by sophtpaw on 2005-08-18
[QUOTE=sophtpaw]I got this back:
conrad@x1-6-00-0b-6a-16-78-f0kernel:~$ artsd -a alsa
unix_connect: can't connect to server (unix:/tmp/mcop-conrad/localhost_localdomain-2d06-4304e148)
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)

cheers,
--
sophtpaw[/QUOTE]
 I also want to add that i have an error message that shows when i reboot or shutdown, if you will.

However, it runs by me so quick that i can't get the whole message. Is there a way i can stop the screen from scrolling on, so i can get the error message in full?
thx
this is part of the error message:

/etc/init.d/also:Warning alsactl store failed with error message alsactl control c:2234 snd_ctl_elem_value_get_integer Assertion idx, ......................................and more

maybe it gives you an idea already though,

thx again,

--
sophtpaw

---

### Post by mo_x on 2005-08-19
Create a file called .asoundrc in your home directory (don't forget the dot) and put the follwing text in it.
```
pcm.!default {
   type plug
   slave.pcm "dmixer"
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,0"
      period_time 0
      period_size 1024
      buffer_size 4096
    }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
}

```
Now restart GNOME and try again to start artsd.
```
artsd -a alsa
```

---

### Post by sophtpaw on 2005-08-19
[QUOTE=mo_x]Create a file called .asoundrc in your home directory (don't forget the dot) and put the follwing text in it.
```
pcm.!default {
   type plug
   slave.pcm "dmixer"
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,0"
      period_time 0
      period_size 1024
      buffer_size 4096
    }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
}

```
Now restart GNOME and try again to start artsd.
```
artsd -a alsa
```[/QUOTE]


sorry, i need to remind you that you are dealing with a complete noob. I went to Places/Home Folder and created a folder called .asoundrc like you said and it is in /home/conrad - correct?
Now how do i put the code in?

thx for your patience

--
sophtpaw

---

### Post by mo_x on 2005-08-19
It is not a foler but a file. Remove the .asoundrc folder. Start a console window and type ```
gedit .asoundrc
``` then just copy and paste the text in the editor and save the file.

---

### Post by sophtpaw on 2005-08-19
[QUOTE=mo_x]It is not a foler but a file. Remove the .asoundrc folder. Start a console window and type ```
gedit .asoundrc
``` then just copy and paste the text in the editor and save the file.[/QUOTE]
 Thx Mo_x  for bearing with me. 

I've sent the .asoundrc folder to the wastebasket
2. i've done the gedit .asoundrccommonad in command line 
3 cut and pasted the script and saved it in teh whatever popped up as a consequence of gedit command.

4. done killall gnome-panel and rebooted for good measure

5. artsd -a alsa

This is the result:

conrad@x1-6-00-0b-6a-16-78-f0kernel:~$ artsd -a alsa
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)

Sorry. Can i ask you again, whether there is a way of being able to freeze the screen as it were to get a good look at that error message i mentioned?

--
sophptaw

---

### Post by mo_x on 2005-08-20
I don't know how to freeze the screen, I am also not aware of any log file containing the error.
The sound device still seems occupied by another process, enter the following command and post the output:
```
fuser -va /dev/snd/*
```

---

### Post by sophtpaw on 2005-08-20
```
fuser -va /dev/snd/*
```[/QUOTE]


transcript:

conrad@x1-6-00-0b-6a-16-78-f0kernel:~$ fuser -va /dev/snd/*

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0
/dev/snd/pcmC0D0c
/dev/snd/pcmC0D0p
/dev/snd/pcmC0D1c
/dev/snd/timer


cheers,

--
sophtpaw

---

### Post by mo_x on 2005-08-21
I actually installed GNOME to try if I can get it working for myself. I am a Kubuntu user  :)
I had the same problems you had. I could not manage to get esd and artsd to be mixed together through the alsa dmix plugin ](*,) . I then tried a different approach and let artsd output to esd. This worked :) I will give you some instructions on how to set it up.

1. Create a shell script to start artsd.
From a terminal window type:
```
gedit startartsd
```
Put the following text in it and save the file:
```
#!/bin/bash
artsd -a esd -F 10 -S 4096 -m artsmessage -l3 &

```
Make the script executable with the command:
```
chmod u+x startartsd
```

2. The script must be run on GNOME startup.
From the menu choose *System->Preferences->Sessions*.
Select the *Startup Programs* tab. Click *Add* and browse for the startartsd script.

3. Log out and then log back in.
You should now be able to play sound from KDE applications.

You can remove the .asoundrc file if you want.

---

### Post by sophtpaw on 2005-08-21
[QUOTE=mo_x]I actually installed GNOME to try if I can get it working for myself. I am a Kubuntu user  :)
I had the same problems you had. I could not manage to get esd and artsd to be mixed together through the alsa dmix plugin ](*,) . I then tried a different approach and let artsd output to esd. This worked :) I will give you some instructions on how to set it up.

1. Create a shell script to start artsd.
From a terminal window type:
```
gedit startartsd
```
Put the following text in it and save the file:
```
#!/bin/bash
artsd -a esd -F 10 -S 4096 -m artsmessage -l3 &

```
Make the script executable with the command:
```
chmod u+x startartsd
```

2. The script must be run on GNOME startup.
From the menu choose *System->Preferences->Sessions*.
Select the *Startup Programs* tab. Click *Add* and browse for the startartsd script.

3. Log out and then log back in.
You should now be able to play sound from KDE applications.

You can remove the .asoundrc file if you want.[/QUOTE]

Hi Mo,

Thx for going through all the trouble (installing Gnome just to work it out)
I don't know if i followed your instructions right.
The first part of 1 was easy. and i copied and pasted into the file. I then exited! (having saved) and put the chmod  x+u command in the command line (shell) 
I don't know if i got that right. The only other alternative was to have put it into the file, but the fact that you already asked me to put something in and save told me that i was done in there.

2 This was also straightforward and i found the startartsd in /home 

3. This was going to be the moment of truth. Unfortunately i don't think the issue is resoved. Just as a real quick test i started Frozen bubbles which under kde has music accompaniment but doesn't in Gnome. I tired to play something in k3B and it didn't. I can't think of any other kde programms right now. I hope i followed the instructions bad otherwise back to the drawing board...  :roll: 

Please just let me know if i've follwed your instructions right or not for a start and then we can go from there,

cordially,

--
sophtpaw

---

### Post by sophtpaw on 2005-08-22
Hi Everyone,

so far only mo_x is been either willing or able to help me on this problem. However, he seems only to be able to come by once a day and help. Hence its been  a few days but i'm still essentially where i was. (or so it feels -maybe we're not only 1 meter away from striking gold!)  but it does feel like this problem is dragging on.

While i appreciate that anyone at all has been willing to get involved with this problem, i wonder if someone could not step in and give additional advice /help and give it a final push. This appears it could be a common experience so maybe i could benefit from someone else's solution?

As always grateful for all the help, and thanking you in advance,

cordially,

conrad

---

### Post by mo_x on 2005-08-25
Hello sophtpaw,

I have been away for a couple of days.
I think you have done everything right. The only thing I can think of why it is not working is that already another instance of artsd is running. I thing in the GNOME taskmanager you can see the command line by which the program is started. Please check if that matches the line in the script. If not so then kill all artsd processes and restart GNOME. You can install a kde music player like juk to do some testing. It is working here for me. Did you remove the .asoundrc file?
I am able to come by more than once a day but I think we are from different time zones. I am from the Netherlands,

Mo X

---

### Post by sophtpaw on 2005-08-25
[QUOTE=mo_x]Hello sophtpaw,

I have been away for a couple of days.
I think you have done everything right. The only thing I can think of why it is not working is that already another instance of artsd is running. I thing in the GNOME taskmanager you can see the command line by which the program is started. Please check if that matches the line in the script. If not so then kill all artsd processes and restart GNOME. You can install a kde music player like juk to do some testing. It is working here for me. Did you remove the .asoundrc file?
I am able to come by more than once a day but I think we are from different time zones. I am from the Netherlands,

Mo X[/QUOTE]

Hi Mo X,

Am i glad to see you back! i thought you abandoned me  :roll: 
I am in London (u.k) so only 1 hr difference. 

Things have gone from bad to worse as i've tried to follow other and conflicting wikis, with the consequence that i had lost all sound all together! both in kde and Gnome. Now i have some sound back in Gnome but it is very poor. 

One of the things i have done is create an .asoundrc i think. You are saying i should remove that, huh? ok, and then just follow your instructions again, restart and it should work? I will try again, but i thought i did that once already and it didn't work. 
Remember any instructions you give have to be clear in every part. Anything you assume is a given is not for me because i'm new to all this,

thx buddy,

--
sophtpaw

P.S

i don't know where .asoundrc would be but i can't find it. Maybe i don't have it after all, so my mistake - sorry. I did Home Folder and then View hidden files and they were not there. And they are not in /etc/esound 

cheers

---

### Post by sophtpaw on 2005-08-25
[QUOTE=mo_x]Hello sophtpaw,

I have been away for a couple of days.
I think you have done everything right. The only thing I can think of why it is not working is that already another instance of artsd is running. I thing in the GNOME taskmanager you can see the command line by which the program is started. Please check if that matches the line in the script. If not so then kill all artsd processes and restart GNOME. You can install a kde music player like juk to do some testing. It is working here for me. Did you remove the .asoundrc file?
I am able to come by more than once a day but I think we are from different time zones. I am from the Netherlands,

Mo X[/QUOTE]

MO X,

Please tell me where the Gnome taskmanager is? 

--
sophtpaw

---

### Post by mo_x on 2005-08-26
It is called system monitor you can find it in the menu *Applications->System Tools->System Monitor*. You can also use this command in a terminal window:
```
ps -ef | grep artsd
```
I asked to remove the .asoundrc file because it is not needed when letting artsd output to esd. I don't expect it to cause a problem but you never know.
When you tried something that didn't work it is better to go back to the starting situation before you try something new.

---

