---
title: "gksudo nautilus to use as backup tool?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by anthonie on 2007-12-31
Hi all,

I screwed up badly, trying to get a nice Gentoo installed on my system that already had way to much OS'es on it in the first place.

So, it did not work and worse, in the process I screwed up a NTFS partition containing all of my music and so much more. Simply by doing one little thing so wrong. However, before I am going to try and get it back, a project in itself one might say, I would like to backup all my important Ubuntu files. I suppose my home directory and /etc/apt/ should be sufficient for that. After that I plan to use the Gparted Live or Rescue CD.

Now, the directory to backup is on a local hdd with NTFS partition, my Vista Drive. It contains a map called Ubuntu backup. Trying to cp the whole thing from command line did not work for some reason, so I used gksudo nautilus, ht Ctrl H to unhide hidden files and then copied the whole map. 

What I would like to know is if I missed something here, before logging of and getting into the whole recovery process. I want to make absolutely sure I still have all my mail and the likes. So the question boils down to: Is gksudo nautilus (+Ctrl H) equivalent to sudo cp -a -r -p?

---

### Post by OffHand on 2007-12-31
backup /home and /etc

that's all your config files

---

### Post by OffHand on 2007-12-31
You could try this application: [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

pretty straight forward

---

### Post by anthonie on 2007-12-31
Thanks, both for your info. I looked at the backup tool and it looks nice. But I have to say, not for me, I'm afraid. It was my lack of knowledge that got me in trouble in the first place. By getting away from the CLI, I feel strongly I will make things just getting worse, for it is the Command Line, I believe wherein lies the real understanding of working with a Linux Flavor. 

By the way, using Nautilus, I did get into some trouble copying files that I had no permission to copy. So I guess Nautilus is not really the way to go than. The reason why I wanted to use Nautilus and not the CL, is that the label of the backup folder contains spaces, and somehow I could not get through using the command line. What do I type for a space in the name, using CL?

PS: If I have some questions about moving partitions, would I have to start a new thread or is it allowed to be done here?

---

### Post by OffHand on 2007-12-31
> **anthonie said:**
> Thanks, both for your info. I looked at the backup tool and it looks nice. But I have to say, not for me, I'm afraid. It was my lack of knowledge that got me in trouble in the first place. By getting away from the CLI, I feel strongly I will make things just getting worse, for it is the Command Line, I believe wherein lies the real understanding of working with a Linux Flavor. 

By the way, using Nautilus, I did get into some trouble copying files that I had no permission to copy. So I guess Nautilus is not really the way to go than. The reason why I wanted to use Nautilus and not the CL, is that the label of the backup folder contains spaces, and somehow I could not get through using the command line. What do I type for a space in the name, using CL?

PS: If I have some questions about moving partitions, would I have to start a new thread or is it allowed to be done here?
What's wrong with the backup tool? It's got a GUI and it does the job...

---

### Post by OffHand on 2007-12-31
BTW: Space for the cli would be a \ so 'home folder' would be "home\ folder"

---

### Post by anthonie on 2007-12-31
No, there is nothing wrong with the tool. It's just not good for me, because when I start using GUI while I actually can use CLI I tend to get lazy and that is how I screwed up in the first place. :rolleyes: 

Being agnostic but looking at both my christian parents, I must admit it's probably just some sort of punishment... the command line, that is! :D

Thanks for the space advice (wow, what a sentence) on command line!

---

### Post by mcduck on 2007-12-31
One thing to notice is that NTFS won't be able to keep the ownerships/permissions of your files (As it's Windows filesystem it doesn't understand Unix-style permissions). But if you compress the files/directories into a .tar.gz archive it will keep the premissions/ownerships of the files..

---

### Post by anthonie on 2007-12-31
> **mcduck said:**
> One thing to notice is that NTFS won't be able to keep the ownerships/permissions of your files (As it's Windows filesystem it doesn't understand Unix-style permissions). But if you compress the files/directories into a .tar.gz archive it will keep the premissions/ownerships of the files..

I was on full speed. Now I'm full on the breaks. Thanks, did not realise that and it would've been a real big annoyance to restore all these ownerships. It would've probably left me reinstalling the whole thing anyway. Kind of stupid because if you think about it, it is so logical that NTFS won't be able to do that. If they could, they would have a different FS in the first place!

Apart from that, I removed all other linx partitions and I do not plan on a reinstall of Ubuntu since that runs very smoothly. But I have been experimenting with some distro's/*NIX flavors and screwed things up badly. What I'd like to do now, before attending to the lost partition (which used to be a NTFS but now is being seen as a EXT3) is to seperate some stuff, like /HOME and so. I read some things about it being wise to create a seperate /boot partition as well, especially if you plan to run more than one *NIX flavor. Any pointers for read-ups about this topic?

---

### Post by capink on 2007-12-31
To get around the problem of windows filesystems not preserving premissions and ownerships, you can backup to a tar file. Here is a simple [script]("http://ubuntuforums.org/showthread.php?t=652307") that might help.

---

