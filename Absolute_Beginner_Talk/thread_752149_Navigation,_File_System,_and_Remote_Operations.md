---
title: "Navigation, File System, and Remote Operations"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by DianeHelen on 2008-04-11
I never really know what part of these forums to post stuff in, so forgive me if Im kinda all over the place.

OK, so after my very exciting day yesterday, I am NOW able to do Remote Access from my Ubunto box, to my XP Box. That is going to be a KEY feature for my new Asus EEEPC to be able to accomplish. So thats a good thing.

So, when I am in a remote session, and please forgive me for making windows like analogies, its the only way I can describe what I need, if Remote from Xp to XP, the host hard drive, shows up as a shared drive in the clients machine when in session. With this I can share and drag, and update files on the host, and copy files from the host , to the client.

When I am in a term session from U to XP, is there a way I can accomplish that same thing.

Also, back on the U box, when I start mucking around to see what I can see,  IF I go to Places >>> Computer, I can see a list of my CD, and then there are 2 other entires. Filesystem which shows the whole file system from my Linux install , and then there is another item, that says SQ003642. Now when I go into that, I am seeing all my Windows file system.  (side ?, what does the SQ003642 stand for)

But, when I open a terminal window, and draw on my 20+ year old Unix BAsic command memory, and do a ls or ls -a, I only see like. Documents, Examples, Public, Desktop, etc.. (ok NEVER MIND ABOVE, dawned on AGED brain, have to move UP directories to see whole filesystem) 



Can somebody help my aged brain, and shed some light on some of this.

The remote stuff is NEEDED, the otehr stuff, is just info, that Id love to have.

TIA
Diane

:)

---

### Post by njparton on 2008-04-11
To mount a remote (XP) folder in ubnutu you can mount it using cifs.  Make sure you have samba and smbfs installed first.
 
Search this forum for cifs how to's.

---

### Post by DianeHelen on 2008-04-11
> **njparton said:**
> .  Make sure you have samba and smbfs installed first.
 
Search this forum for cifs how to's.

and how would I make sure of the above?

I assume I have Samba, as I think I set that up, when I set up the networking to access my files across my lan

But what is smbfs  and what is cifs?

---

### Post by njparton on 2008-04-11
to be sure:
 
```
sudo apt-get install samba smbfs
sudo /etc/init.d/samba restart
```
 
To mount with cifs:
 
[LEFT]```
sudo mount -t cifs -o username=someone //localhost/share /mnt
```

where "someone" is your windows username.

but all of this information already exists in the forum so please search for it.[/LEFT]

---

### Post by herbster on 2008-04-11
What did you mean a term session from Ubuntu to XP? Are you trying to transfer files to/from the machines in a shell as well as a GUI (like the file browser, places>network) ??

---

### Post by DianeHelen on 2008-04-12
Ummm well I mean logged into my XP desktop thru a remote session from the U box. I get  there thru the Terminal Server Client . ONce connnected I see my XP desktop, and was wondering how I could temporarily I guess, mount my hard drive on that XP box, to the current session, so I could bring files from XP box to U box.

---

### Post by herbster on 2008-04-12
> **DianeHelen said:**
> Ummm well I mean logged into my XP desktop thru a remote session from the U box. I get  there thru the Terminal Server Client . ONce connnected I see my XP desktop, and was wondering how I could temporarily I guess, mount my hard drive on that XP box, to the current session, so I could bring files from XP box to U box.

Why would you want to mount the linux filesystem on the XP box if you want to transfer files from the XP box to the linux box? I think what you want to do here is simply mount the XP shared folder(s) on your linux system, so you can access them from Ubuntu. Correct?

---

### Post by DianeHelen on 2008-04-13
yes thats what I dd mean, guess I did not explain it well

HOW would I DO that, once in the session

---

### Post by njparton on 2008-04-13
Scroll down the manual mount bit of this thread:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by herbster on 2008-04-13
You don't need to be in a remote session to do that. You can just mount the filesystem and have it appear as a normal folder on your Ubuntu system.

Make a directory that you will mount your XP share to, for example:

```
sudo mkdir /media/xpshare
```

Now edit the fstab:

```
sudo gedit /etc/fstab
```

Paste the following on a new line, with the changes applicable to you:

```
//192.168.x.x/path/to/windows/share /media/xpshare cifs user=username,pass=password
```

Replace the IP with your XP computer's IP, the path of course with the path to your Windows share that you want to mount, and the username/password with the user/pass you use to get into the Windows box. Then to test, do

```
sudo mount -a
```

And cd to your xpshare, see if it mounted:

```
cd /media/xpshare && ls
```

See files/folders being shown? Then it mounted.

---

