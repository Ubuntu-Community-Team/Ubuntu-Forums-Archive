---
title: "Music Player Question"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Linux_Nooblet on 2007-05-24
I just installed Ubuntu a couple of days ago. 
here is my situation.  I keep my music on a network drive.  
I am looking for a good music player that allows me to play my music directly from my network drive.
The music path is smb://networkdrive/music
I can not get many of these programs to accept this path to my music.
Any help would be great.
Thanks

---

### Post by Detonate on 2007-05-24
If you mount the drive you should be able to access it from any of your programs.  Mount the drive and try that.

---

### Post by Hobo Joe on 2007-05-24
Amarok. I've had no trouble accessing different drives/paritions with it.

---

### Post by Linux_Nooblet on 2007-05-24
Well originally i browsed the network drive under "Places" and the "windows Network"  I then rught clicked on the drive file and clicked on "Connect to the server"  

Is this the way I should have mounted the drive?
How should I di it if not?
Thanks everyone

---

### Post by Hobo Joe on 2007-05-24
As far as I know(not all that far though, sadly) that should be fine. LIke I said, you can use Amarok to scan folders for music, and it will consistantly keep them updated.

But I've never done it with a network drive before, but it should still work.

---

### Post by Linux_Nooblet on 2007-05-24
Well in Amarok  Settings, Configure Collection, I do not see any listing of my network drive.  I see the / root directory and many files under that.  Is there a perticular place that linux mounts the network/smb drives?

---

### Post by Detonate on 2007-05-24
To permanently mount your network drive see this:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

In your media programs, you might also try to open your music by using stream, where you put the URL to your music in instead of the file.

In Amarok, click on Playlist, Add Stream, and enter smb://networkdrive/music and see if that works.  Never tried this, but it's worth a shot.  If it works in Amarok, will probably work in other apps also.

---

### Post by Hobo Joe on 2007-05-24
Also, under 'files' in Amarok, you can enter 'smb://<computer name>' to get all it's files in Amarok.

---

### Post by tgalati4 on 2007-05-24
Banshee, LSongs, Rhythmbox all work, but setting up the network share can be fiddly.  The dialog box will not show the network share unless you mount it to a local directory.

For instance, on LSongs, create a local directory called LSongs then used the mount command to create an smb mount to that local directory.  Then it will show up in the music library dialog box.  I had to install smbfs from Synaptic on Dapper.

Expect some music skips if your network is busy.

---

### Post by Linux_Nooblet on 2007-05-24
Ok i got it mounted to a local drive in my /home folder now.  I had to edit the /etc/fstab file to make it mount the drive every time the system is loaded.  Thanks everyone for their help.
:popcorn:

---

### Post by Detonate on 2007-05-24
That's the best way to do it, and now you know how to mount a folder.  That's probably going to come in handy again for you.

---

