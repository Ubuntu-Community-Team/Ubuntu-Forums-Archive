---
title: "XMMS not playing mp3 from a network server"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by snowman69 on 2007-05-22
Hello,

I successfully installed XMMS. It plays mp3 files perfectly as long as the files are on the PC. If I tried to play a file from my music server, it does not work. I see the file name in XMMS but it is not playing it.

Would there be a configuration issue?

Thanks!

snowman69

---

### Post by Pragmatist on 2007-05-24
Pick a particular file and give us a long listing of it:
```
ls -l filename
```

---

### Post by ciamele on 2007-06-07
I'm having the same problem:

```
chris@skywalker:~/My Music/Amorphis/Tuonela$ ls -l 05-Tuonela-Greed.mp3
-rw-r--r-- 1 chris chris 4116517 2005-07-27 21:42 05-Tuonela-Greed.mp3

```

Can you help? Thanks!

---

### Post by ciamele on 2007-06-08
bump

---

### Post by Pragmatist on 2007-06-08
> **ciamele said:**
> I'm having the same problem:


So, if your having the same problem, that means you can play this file in XMMS, except when this file is located in another location?  That was the OP's problem I think.

As for the OP, did you solve your problem?  If so, please post what happened here so that you can help others.  If your problem hasn't been resolved, have you tried this:

Pick a particular sound file and put a copy on your PC and a copy on the sound server.  It is a good test to use the same exact file in both places.

---

### Post by ciamele on 2007-06-09
> Pick a particular sound file and put a copy on your PC and a copy on the sound server. It is a good test to use the same exact file in both places.

I have tried that. The mp3 I copied to my client plays, the file on the sound server does not. I'm not sure if this is a clue to anyone, but when the song is on the sound server, XMMS doesn't know how long the song is (listed as "0:00/?"), but the song is listed in the playlist editor.

---

### Post by Pragmatist on 2007-06-09
Here are a few individual tests to try (please post the results):

1.) Try running XMMS as root and see if the file plays
2.) Try a different file format (like a WAV file for instance)
3.) Try a different player than XMMS

---

### Post by ciamele on 2007-06-09
> **Pragmatist said:**
> Here are a few individual tests to try (please post the results):

1.) Try running XMMS as root and see if the file plays
2.) Try a different file format (like a WAV file for instance)
3.) Try a different player than XMMS

1. I tried running from root, but I have the same problem.

2. I can't seem to load the wav file from my server to XMMS on my client. I try right-clicking the file in the shared folder and choose "open with xmms", but it just brings up a window to search for files to load. I can't seem to find the path to my shared folder in the directories. I can't find anything that says something like "smb://skywalker/My_Music". When I copy the wav file to my client, it plays without any problems.

3.  Rhythmbox loads the mp3 from my server, shows me it's length, acts like it's going to play it, but doesn't (same thing happens when I load it from the client). It loads the wav from my server, appears to play it, but I hear nothing with the volume turned all the way up (same result when loaded from client).

---

### Post by Pragmatist on 2007-06-09
Ok, so the Rhythmbox didn't work in the client or the server, so it was not a good test.  You might want to find another player that works in the client and then test if it works in the server.

Also, you gave the permissions for this file in an earlier post:
> -rw-r--r-- 1 chris chris 4116517 2005-07-27 21:42 05-Tuonela-Greed.mp3



However, what are the permissions for the file on the server?

---

### Post by ciamele on 2007-06-10
Those are the permissions for the mp3 on the server.

---

### Post by Pragmatist on 2007-06-10
This probably won't matter, but while we're still working this out anyway, try making the file executable:

```
chmod a+x 05-Tuonela-Greed.mp3
```

---

### Post by n3azz on 2007-06-18
I am having exactly the same issues, any audio file that is on my PC will play in xmms, rythmbox etc. but if the audio file is on another computer xmms wont play it. rythmbox does so, but i wanna use xmms.

any body got any suggestions?

all permissions are fine, is there some plugin we have to download or some lib file need tweaking?

help :(

---

### Post by eli_d on 2007-07-22
i have had this problem before.  XMMS will stream your mp3s through a windows network share, but you need to mount it first.  see this thread: [http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently) for specific instructions.

it's a bit overwhelming at first (considering how much you have to do, just to play mp3s, but it's worth it in the end).

basically:

1) use synaptic to make sure you have the smbfs / smbmount command package.  search for samba, you'll probably already have samba installed, but you will need the smbfs command.
2) create a directory on your desktop that will be the share mounting point
3) create a file in your root directory for your password / username information (gedit .smbpasswd... see instructions in link above for more detail)
4) mount the drive by entering something along the lines of:
```

sudo smbmount //elidesk/backup /home/eli/Desktop/elidesk -o credentials=/home/eli/.smbpasswd 0 0
```
5) open the directory on your desktop and your files should now be accessible and playable in xmms


this will not be saved when you restart your computer.  so an additional step is to add your mount command line from #4 to /etc/fstab (the file that mounts all your drives when you start the computer) is necessary.  see the link above for more specific instructions.

---

