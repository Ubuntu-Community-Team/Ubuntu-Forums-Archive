---
title: "Help me,bt5 tools in ubuntu"
date: 2012-07-26
forum: Any Other OS
---

### Post by GrandMast3r on 2012-07-26
HI all,i'm trying to install bt5 tools in ubuntu..
i read this thread :
[http://ubuntuforums.org/showthread.php?t=1882653](http://ubuntuforums.org/showthread.php?t=1882653)

when i write in terminal :

wget -q [http://all.repository.backtrack-linux.org/backtrack.gpg](http://all.repository.backtrack-linux.org/backtrack.gpg) -O- | sudo apt-key add -

It show me :

```
W: Failed to fetch http://32.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://all.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://source.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Can anyone help me ?  Sorry for my bad english !

---

### Post by Cheesemill on 2012-07-26
This is a very bad idea.

It only has a small chance of working if you are using 10.04, and even then it is likely to break your system.
[http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F](http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F)

If you want to use BackTrack tools then run Backtrack, not Ubuntu. You can either run it from a Live DVD, dual boot or run it from a VM but I wouldn't attempt what you are suggesting.

---

### Post by GrandMast3r on 2012-07-26
> **Cheesemill said:**
> This is a very bad idea.

It only has a small chance of working if you are using 10.04, and even then it is likely to break your system.
[http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F](http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F)

If you want to use BackTrack tools then run Backtrack, not Ubuntu. You can either run it from a Live DVD, dual boot or run it from a VM but I wouldn't attempt what you are suggesting.


i'm using 12.4 !

---

### Post by Cheesemill on 2012-07-26
> **GrandMast3r said:**
> i'm using 12.4 !
In that case it's definitely not going to work.
It's also why you are getting those errors.

---

### Post by nothingspecial on 2012-07-26
I would take the advice already given. If you want to run backtracks stuff use backtrack.

---

### Post by GrandMast3r on 2012-07-26
ok brothers,
If anyone know the solution reaply here :)

---

### Post by Cheesemill on 2012-07-26
> **GrandMast3r said:**
> ok brothers,
If anyone know the solution reaply here :)
There isn't one.

The BackTrack tools are all specifically compiled and packaged to work with BackTrack (which is based on Ubuntu 10.04). There is a small chance that you could install them on a plain Ubuntu 10.04 installation but if you read the link I posted earlier it is not recommended or supported and even the BackTrack developers say that it will probably break your installation.

Because 12.04 uses such different versions of the kernel, shared libraries and applications  than 10.04 it just isn't going to work. Really.

For the times that I need to use BackTrack I just fire it up in a VM, it's by far the easiest way to do it.

Also if you only need a few of the tools then just install them from the standard Ubuntu repositories, a large number of them are in there.

---

### Post by Zvlwab on 2012-07-26
I wrote that guide.
It did work fine when I was still running Ubuntu 10.10, but since I upgraded to 12.04 it doesn't work anymore.

---

### Post by GrandMast3r on 2012-07-26
when i run backtrack my adapter is off,,and when i try to open WICD,it show me some wireless connections,,when i try connect it say : Unable to get ip Address...it doesnt work :(  
this is the reason that i'm trying to install bt5 tools in ubuntu... :(

---

### Post by miguelpires on 2012-07-26
I think you going to install them manually from the site of the programs, or from ubuntu repositoirs.

I've BT5 install in 2 machines and have "major" problems, if you need some help let me Know!
Best Regards
Miguel

---

### Post by Cheesemill on 2012-07-26
Try asking for help with your particular wireless adapter on the BackTrack forums.
[http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

---

### Post by GrandMast3r on 2012-07-26
In BT-Linux.org/F they didn't aprove my thread :(

---

### Post by nothingspecial on 2012-07-27
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Mr.Plex on 2012-07-27
Could you illiterate the purpose of these tools? You want to hack a wifi? download aircrack-ng tools. Want more tools but BT5 not working? Open up backtrack 5, physically write down names of tools you want, jump back into Ubuntu and Download/Install/Repeat.

---

### Post by GrandMast3r on 2012-07-28
> **Mr.Plex said:**
> Could you illiterate the purpose of these tools? You want to hack a wifi? download aircrack-ng tools. Want more tools but BT5 not working? Open up backtrack 5, physically write down names of tools you want, jump back into Ubuntu and Download/Install/Repeat.

Brother i want all bt5 tool pack.... :(

---

### Post by nothingspecial on 2012-07-28
Then install backtrack

---

### Post by GrandMast3r on 2012-07-28
> **nothingspecial said:**
> Then install backtrack

i post in this thread what problem i have with bt :(

---

### Post by nothingspecial on 2012-07-28
> **GrandMast3r said:**
> i post in this thread what problem i have with bt :(

you did :)

my appologies

---

### Post by Zvlwab on 2012-07-30
> **GrandMast3r said:**
> HI all,i'm trying to install bt5 tools in ubuntu..
i read this thread :
[http://ubuntuforums.org/showthread.php?t=1882653](http://ubuntuforums.org/showthread.php?t=1882653)

when i write in terminal :

wget -q [http://all.repository.backtrack-linux.org/backtrack.gpg](http://all.repository.backtrack-linux.org/backtrack.gpg) -O- | sudo apt-key add -

It show me :

```
W: Failed to fetch http://32.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://all.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://source.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Can anyone help me ?  Sorry for my bad english !

I think you're getting these messages, because you haven't unchecked/removed the source repo's in the Software Sources window.
```
W: Failed to fetch http://32.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://all.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://source.repository.backtrack-linux.org/dists/revolution/Release  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

The following is probably caused because you are running something like for example running Synaptic Package Manager, close it before trying this.
```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by chamber on 2012-08-02
If you can't get wireless working in BackTrack what hope do you have with the rest of the tools?

---

### Post by dodo3773 on 2012-08-12
Build the stuff you want / need. If you want it all then build it all. They are just scripts and applications. Don't see why most / all of them won't work in Ubuntu. The problem is you are trying to find an easy way to do this. Just go through the tools one at a time and build, compile, and test them yourself.

---

