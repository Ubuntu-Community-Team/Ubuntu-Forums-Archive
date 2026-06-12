---
title: "Please help. Sound stopped working, anyway to cure?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by marco123 on 2007-05-24
My sound just stopped working.  :(

It could be linked to me ripping a dvd, because thats the only thing I've tried out that I haven't before.

The error message I get from xmms says to make sure that another application isn't using it?

 How do I do that? (In winblows for example you press Ctrl-Alt-Del to see whats running, then you can right click and choose end process/task.  Is there an equivalent  in Linux?)
Theres nothing visibly running.

Also it asks if my output settings are fine, I think they are. (I haven't changed them anyways.)

---

### Post by ggaaron on 2007-05-24
Check gnome-system-monitor or ksysguard.

Are you using oss? I think that alsa supports multiple programs using it at once, anyway restarting computer should turn off all programs using it.

---

### Post by marco123 on 2007-05-24
Is there somewhere I can see all running programs, to maybe fix it without a reboot?

---

### Post by dbott67 on 2007-05-24
The command 'ps' displays all running processes.  The command below will display all running processes & CPU/Mem % (there will be lots):
```
ps -aux
```
From here, you could grep for a specific process.  Suppose I only want to see process that I'm running (user=dbott):
```
dbott@feisty:~$ ps aux | grep dbott
root      4945  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Music /home/dbott/music -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
root      4956  0.0  0.1   6100  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Data /home/dbott/data -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
root      4959  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Archive /home/dbott/archive1 -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
dbott     5345  0.0  1.2  30852 11696 ?        Ssl  May22   0:00 /usr/bin/gnome-session
dbott     5384  0.0  0.0   4256   532 ?        Ss   May22   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5387  0.0  0.0   2660   636 ?        S    May22   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5388  0.0  0.1   2852  1064 ?        Ss   May22   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
dbott     5390  0.0  0.4   6940  4432 ?        S    May22   0:01 /usr/lib/libgconf2-4/gconfd-2 6
dbott     5393  0.0  0.1   2752  1008 ?        S    May22   0:00 /usr/bin/gnome-keyring-daemon
dbott     5395  0.0  1.1  29928 10228 ?        Sl   May22   0:05 /usr/lib/control-center/gnome-settings-daemon
dbott     5402  0.0  0.0   1716   484 ?        Ss   May22   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5403  0.0  0.3   4688  2992 ?        S    May22   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5408  0.0  0.3  39716  3220 ?        Ssl  May22   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
dbott     5413  0.0  0.6  15844  5468 ?        S    May22   0:01 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
dbott     5414  0.0  1.1  17568 10420 ?        S    May22   0:58 /usr/bin/metacity --sm-client-id=default0
dbott     5417  0.0  2.6  66108 24340 ?        S    May22   1:17 gnome-panel --sm-client-id default1
dbott     5423  0.0  3.3 102740 30232 ?        S    May22   0:08 nautilus --no-default-window --sm-client-id default2
dbott     5428  0.0  0.3   8512  3540 ?        S    May22   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
dbott     5429  0.0  0.5  19068  4896 ?        Ss   May22   0:00 gnome-volume-manager --sm-client-id default4
dbott     5431  0.0  1.4  53824 12884 ?        S    May22   0:01 update-notifier
dbott     5440  0.0  1.0  84032  9504 ?        S    May22   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
dbott     5456  0.0  1.1  68472 10064 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
dbott     5475  0.0  1.5  53136 13744 ?        S    May22   0:00 nm-applet --sm-disable
dbott     5478  0.0  0.9  49500  8380 ?        S    May22   1:54 gnome-cups-icon --sm-client-id default3
dbott     5479  0.0  0.6  50896  6296 ?        Ss   May22   0:01 gnome-power-manager
dbott     5492  0.0  0.0   2460   888 ?        S    May22   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
dbott     5496  0.0  1.0  51000  9568 ?        S    May22   0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activate-iid=OAFIID:GNOME_DriveMountApplet_Factory --oaf-ior-fd=22
dbott     5504  0.0  1.0  36672  9620 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=30
dbott     5507  0.0  1.4  54848 13052 ?        S    May22   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=33
dbott     5531  0.0  0.6  58384  6296 ?        Sl   May22   0:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=31
dbott     5569  0.0  1.1  49476 10532 ?        S    May22   0:03 /usr/lib/notification-daemon/notification-daemon
dbott     5573  0.0  0.2  16112  2452 ?        Ss   May22   1:08 gnome-screensaver
dbott     8506  0.0  2.0  78172 18136 ?        Sl   May22   0:06 gnome-terminal
dbott     8510  0.0  0.0   2464   736 ?        S    May22   0:00 gnome-pty-helper
dbott     8511  0.0  0.3   5688  3260 pts/0    Ss   May22   0:00 bash
dbott    30370 18.5 11.4 251148 103336 ?       Sl   10:58   7:39 /usr/lib/firefox/firefox-bin
dbott    31905  4.4  3.4  86452 31436 ?        Sl   11:38   0:03 mono /usr/lib/tomboy/Tomboy.exe
dbott    31960  0.0  0.1   2560   996 pts/0    R+   11:39   0:00 ps aux
dbott    31961  0.0  0.0   2880   748 pts/0    R+   11:39   0:00 grep dbott

```

You could also grep for the name of the process.

Anyhow, if you can't get your sound working properly, I've listed my experience below.

After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by marco123 on 2007-05-24
I created a new user account and switched to that, the only thing that wasn't running in that one that was in mine was something called "sm-disable" or something like that(in Preferences>Sessions>Current Session), so I switched back to my account and removed that process and the sound works again now. :D :D

I'll have to keep an eye out for that process I think.  Maybe the dvd ripping program started it?:confused:

Thank you very much for your help.  :)

---

### Post by ggaaron on 2007-05-24
If you want a graphic utility for killing processes then as I've written:
- gnome-system-monitor (for gnome)
- ksysguard (for KDE)

Just in case you'll need them again=)

---

### Post by Happy_Man on 2007-05-24
Have you tried the command
```
alsamixer
```?

---

