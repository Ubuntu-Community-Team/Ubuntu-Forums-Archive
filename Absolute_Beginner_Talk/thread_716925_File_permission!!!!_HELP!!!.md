---
title: "File permission?!?!?!?! HELP!!!"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by bbc on 2008-03-06
I'm having quite the bit of trouble here. I can't update or download files from nicotine + I keep getting file permission error 13 when I download anything to anywhere else except the home folder. And when I update I get "E: Could not open lock file var/lib/apt/lists/lock - open(13 permission denied)
E:Unable to lock the list directory" I've read and read and read for hours, my eyeballs are burning I can't even find anything related to this so all my reading is in vain. please help me.](*,)](*,)](*,)

---

### Post by Vadi on 2008-03-06
Hrm. What is nicotine?

---

### Post by bbc on 2008-03-06
Nicotine + is like soulseek(a windows program) Pretty much a file sharing program.

Also I can't delete the windows folder,  Because it's on a read only disk. >.<

---

### Post by justin whitaker on 2008-03-06
> **bbc said:**
> Nicotine + is like soulseek(a windows program) Pretty much a file sharing thing.

Also I can't delete the windows folder,  Because it's on a read only disk. >.<

If you have not set up a root password, use the following:

sudo passwd

Become root.

There are two ways you can do this: console or graphically. 

For console, you can chmod 1000 (change mod permissions) or chown 1000 (change ownership permissions) the folder that has the files you downloaded via Nicotine. 

Graphically, you can pass the nautilus command while logged into a terminal as root, and manage the permissions on the drive or the folder by right clicking on it.

---

### Post by Vadi on 2008-03-06
Try alt+f2, "gksudo nautilus", then find the offending folder, right-click, and poke about in properties - change the owner to yourself, maybe anything else if needed.

I'd recommend Deluge for file-sharing though, that seems to work fine for me.

---

### Post by kayvortex on 2008-03-06
The stuff about the lock file means that there is already an apt-based program running (aptitude, synaptic etc.) -- you can only have one instance of it running at any time (unless you want a big headache).

---

### Post by bbc on 2008-03-06
> **justin whitaker said:**
> If you have not set up a root password, use the following:

sudo passwd

Become root.

There are two ways you can do this: console or graphically. 

For console, you can chmod 1000 (change mod permissions) or chown 1000 (change ownership permissions) the folder that has the files you downloaded via Nicotine. 

Graphically, you can pass the nautilus command while logged into a terminal as root, and manage the permissions on the drive or the folder by right clicking on it.

That's great and everything, do you mind explaining it a little more detailed. The sudo passwd thing did nothing and when i click on permissions I get this "You are not the owner, so you can not change these permissions"

---

### Post by bbc on 2008-03-06
> **Vadi said:**
> Try alt+f2, "gksudo nautilus", then find the offending folder, right-click, and poke about in properties - change the owner to yourself, maybe anything else if needed.

I'd recommend Deluge for file-sharing though, that seems to work fine for me.

When I do that I can't see my slave harddrive in the list and that's where the files are that I'm dealing with.

---

### Post by justin whitaker on 2008-03-06
> **bbc said:**
> That's great and everything, do you mind explaining it a little more detailed. The sudo passwd thing did nothing and when i click on permissions I get this "You are not the owner, so you can not change these permissions"

First, Kayvortex is right: make sure that apt isn't running.

Next:

When you opened a terminal and entered sudo password should have prompted you for a root password to enter, twice.

Now: 

1. open up a terminal, or a terminal tab, or just go to the command prompt
2. type in SU
3. type in your root password.
4. You are now root. 

Once you are root, type in nautilus, and it will give you a warning, then open the program. 

1. Navigate to the Nicotine folder
2. Find where it saved the files
3. Right click on it, selecting the last option, Permissions. 
4. Change the permissions from root to your user name.
5. Make sure you give yourself read and write on both drop downs on owner.
6. Do the same thing with the Group. 
7. Open up another file browser, and see if you can manipulate the files. 

If everything went right, you should be able to do what you want with the folder.

---

### Post by kayvortex on 2008-03-06
"sudo passwd" will set (or change) the password of the "root" account. BUT, I wouldn't advise messing about with that stuff without understanding what's going on first.

You said you couldn't update the program: (dumb question, but...) you mean via apt, right?

---

### Post by justin whitaker on 2008-03-06
> **kayvortex said:**
> "sudo passwd" will set (or change) the password of the "root" account. BUT, I wouldn't advise messing about with that stuff without understanding what's going on first.

Amen to that. 

I am just trying to help with the file permissions issue. The rest of it is unclear.

---

### Post by kayvortex on 2008-03-06
@justin: I think we'll end up stepping on each other's toes, so i'll sit back...

---

### Post by bbc on 2008-03-06
Just forget it, I'm so aggravated right now I'm not explaining what I'm trying to do properly. I don't care I'll just go back to windows.

---

### Post by kayvortex on 2008-03-06
If you're *that* frustrated, then do what you need to do. From the sounds of it though, I think your problems with this are solvable (without too much effort ... hopefully!).

---

### Post by bbc on 2008-03-06
> **kayvortex said:**
> If you're *that* frustrated, then do what you need to do; but, from the sounds of it, I think your problems with this are solvable (without too much effort ... hopefully!).

Okay, lets see if I can explain this is great detail.

I have a master harddrive, which is named filesystem. 120 gigs. This is the harddrive ubuntu is installed on. When I check the file permissions They're read only, and the owner is unknown.

How do I make my username the owner and skip the root? or is there a way to login as root? I'm looking for the easiest way to deal with that. If I'm able to change the file permissions on the harddrive then, I'll be able to delete anything from it correct?

Now my slave drive is 120 gig, partitioned into 70 and 50 gigs the owner is root. I want to chyanged that. Because when I type the nautilus command, it only shows the 'filesystem' drive, not my slave. So therefore all this work is null and void because the drive I need to change doesn't show up.

The soulseek issue is fine if I save the files to the Home folder. And that's alright with me. I'll tackle that another day. So I hope I cleared myself up a little bit in what I'm trying to do. I know I'm a tad bit flustered so it was making me a little retarded.

---

### Post by kayvortex on 2008-03-06
I promised justin that I wouldn't be rude and make suggestions over his, so let me just try and clear some stuff up.

Also, I have a feeling that I'm going to have to be a bit annoying (and so will probably get on your tits a bit) and ask exactly what files you checked permissions on (e.g. "/", "/mnt", "/media" etc.). Sorry...!

Edit: Can I ask if you can do things through the command line, or would prefer not to? We can sort it out either way, but I should at least do it the way you'd prefer.

---

### Post by bbc on 2008-03-06
> **kayvortex said:**
> I promised justin that I wouldn't be rude and make suggestions over his, so let me just try and clear some stuff up.

Also, I have a feeling that I'm going to have to be a bit annoying (and so will probably get on your tits a bit) and ask exactly what files you checked permissions on (e.g. "/", "/mnt", "/media" etc.). Sorry...!

Edit: Can I ask if you can do things through the command line, or would prefer not to? We can sort it out either way, but I should at least do it the way you'd prefer.

All I want is the hard drive permissions changed so I can download and delete on them.

---

### Post by kayvortex on 2008-03-06
Ok. Your slave drive won't appear in the list of files displayed when you type "gksudo nautilus". What you need to do is this: type

```
gksudo nautilus /
```

Every folder on your system should be contained in the files that show up here somewhere. You need to enter the "media" (and if not there, then the "mnt") folder. In this "media" (or "mnt") folder should be further folders for every disk on your system: your slave disk should be one of them (but it could be named anything, so you need to poke around). Tell me if you have got this far, and if you can't find your slave disk, we'll have to "mount" it.

Edit: actually, all you need to do after this is to find the folder whose permissions you want to change, right-click on that folder, go to the permissions tab and change them!

---

### Post by bbc on 2008-03-06
> **kayvortex said:**
> Ok. Your slave drive won't appear in the list of files displayed when you type "gksudo nautilus". What you need to do is this: type

```
gksudo nautilus /
```

Every folder on your system should be contained in the files that show up here somewhere. You need to enter the "media" (and if not there, then the "mnt") folder. In this "media" (or "mnt") folder should be further folders for every disk on your system: your slave disk should be one of them (but it could be named anything, so you need to poke around). Tell me if you have got this far, and if you can't find your slave disk, we'll have to "mount" it.

Edit: actually, all you need to do after this is to find the folder whose permissions you want to change, right-click on that folder, go to the permissions tab and change them!

Well I messed up bad and have to reinstall ubuntu, but it's a learning experience...I suppose. I'll try this, and see where I get. Thanks for being patient with me.

---

### Post by bbc on 2008-03-06
> **kayvortex said:**
> Ok. Your slave drive won't appear in the list of files displayed when you type "gksudo nautilus". What you need to do is this: type

```
gksudo nautilus /
```

Every folder on your system should be contained in the files that show up here somewhere. You need to enter the "media" (and if not there, then the "mnt") folder. In this "media" (or "mnt") folder should be further folders for every disk on your system: your slave disk should be one of them (but it could be named anything, so you need to poke around). Tell me if you have got this far, and if you can't find your slave disk, we'll have to "mount" it.

Edit: actually, all you need to do after this is to find the folder whose permissions you want to change, right-click on that folder, go to the permissions tab and change them!

This is the furthest I've gotten but it won't save the permissions I set....so I don't know what the problem with that is.

---

### Post by kayvortex on 2008-03-07
Right, it's just occurred to me that the reason that the permissions won't stick is because the permissions are set to default values every time the disk is mounted (like every time you boot). Unless something freaky is going on, these default permissions are read from a file, which you can change. So, can you post the contents of the file /etc/fstab please.

---

