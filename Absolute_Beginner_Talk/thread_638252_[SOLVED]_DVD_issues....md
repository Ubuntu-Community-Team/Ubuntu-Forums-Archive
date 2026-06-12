---
title: "[SOLVED] DVD issues..."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by 1ZERO1 on 2007-12-11
I'm new to Linux/Ubuntu so bear with me...


I'm running a Compaq c500 laptop with integrated cd/dvd burner.
It burns fine and reads CD and Data DVDs fine but will not play or rip regular DVD movies.

I've got a flight tomorow and would love to watch a movie on it.

thanks in advance for all the help, the community thing is awesome.

J

---

### Post by taurus on 2007-12-11
Maybe this helps, [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).

---

### Post by 1ZERO1 on 2007-12-11
I looked for libdvdcss2 in the package manger (synaptic) but did not find it. 

The description was for terminal but when I typed it in as written I got an "unknown command" error.

---

### Post by taurus on 2007-12-11
Which release are you running?  Maybe you don't have enough repos in your /etc/apt/sources.list.

On the top menu, click System -> Administration -> Synaptic Package Manager.  Then, click Settings -> Repositories and make sure you have a check mark for all the repos except Source code and Cdrom.  Click Close and then Reload.  Now, look for those packages again.

p.s.  If you want to install libdvdcss2, you need to follow this guide, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by rsambuca on 2007-12-11
You have to either add the medibuntu repositories, or grab the packge from there.  [Details here]("https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3").

---

### Post by crjackson on 2007-12-11
> I looked for libdvdcss2 in the package manger (synaptic) but did not find it. 

The description was for terminal but when I typed it in as written I got an "unknown command" error.


If you are running Gutys 7.10 do this in a terminal session...

1) Add the medibuntu repository for Ubuntu 7.10 "Gutsy Gibbon"

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

2)Add the GPG Key.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

3) To play Encrypted DVD's.

```
sudo apt-get install libdvdcss2
```

---

### Post by 1ZERO1 on 2007-12-11
I'm totally lost on adding repositories....

Medibuntu sounds good but I've no idea how to add it.

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> I'm totally lost on adding repositories....

Medibuntu sounds good but I've no idea how to add it.

Are you using Gutsy?

If yes, then just cut and paste what I posted above in a terminal screen session...

---

### Post by 1ZERO1 on 2007-12-11
I'm on gutsy... when I try to paste in terminal I get ^v instead of anything pasting...

Is there another paste command than ctrlv?

---

### Post by rsambuca on 2007-12-11
All of the information you require is either in that page, or linked to from that page.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by taurus on 2007-12-11
Cut what you want with the left button of your mouse and paste it with the middle button or the wheel track.

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> I'm on gutsy... when I try to paste in terminal I get ^v instead of anything pasting...

Is there another paste command than ctrlv?

Use Your Mouse, Right CLick menu....>cut  Right Click Menu >Paste

---

### Post by crjackson on 2007-12-11
> **taurus said:**
> Cut what you want with the left button of your mouse and paste it with the middle button or the wheel track.

I think you ment RIGHT not LEFT.

---

### Post by 1ZERO1 on 2007-12-11
I've pasted the three lines in the terminal but The DVD still won't play. Is there a final step?

---

### Post by taurus on 2007-12-11
> **crjackson said:**
> I think you ment RIGHT not LEFT.

Cut what you want with the left button = highlight

---

### Post by 1ZERO1 on 2007-12-11
ctrlp instead of ctrlv... got it.

I feel slow. I'm not a computer idiot but sometimes the little changes are the biggest.

---

### Post by crjackson on 2007-12-11
Now that you have added the medibuntu repositories, read the docs in the links posted above and install codecs if needed...

Also did you add the "restricted extras" from either the ADD/REMOVE menu under applications, or from Synaptic?  If not then do that too.

You may need to go to the menus SYSTEM>ADMINISTRATION>SOFTWARE SOURCES  from there enable the univers and multi-verse repositories.  I usually enable everything except proposed updates.

---

### Post by 1ZERO1 on 2007-12-11
j@JGRIMM:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
j@JGRIMM:~$ 



I'm lost...

---

### Post by rsambuca on 2007-12-11
Redo the commands from post #6 of this thread.

---

### Post by 1ZERO1 on 2007-12-11
I've re-done post 6... everything seems cool.

when I put in a DVD there is an awful noise and then the sound starts playing without video.
I'm using totem...

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> j@JGRIMM:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B][SIZE="4"]Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate[/SIZE][/B]j@JGRIMM:~$ 



I'm lost...

Everything is not cool unless you don't get this error anymore...

There's no point in me going forward until this is working...

---

### Post by 1ZERO1 on 2007-12-11
I redid 6 and all went as expected...

I needed to change my totem to the xine (spelling?) version...

I'm now watching old boy in style!!!

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> I've re-done post 6... everything seems cool.

when I put in a DVD there is an awful noise and then the sound starts playing without video.
I'm using totem...

If you are in 32-bit Gutsy do this...

```
sudo apt-get install w32codecs
```

If you are in 64-bit Gutsy do this...

```
sudo apt-get install w64codecs
```

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> I redid 6 and all went as expected...

I needed to change my totem to the xine (spelling?) version...

I'm now watching old boy in style!!!

Good.  If all is working for you, then please go to the thread tools and mark this thread as solved...

While you are at it you might like this too...
```
sudo apt-get install gxine
```
```
sudo apt-get install xine-ui
```

---

### Post by 1ZERO1 on 2007-12-11
Thanks everyone for all the help.

I'm loving Unbuntu!!

---

### Post by crjackson on 2007-12-11
> **1ZERO1 said:**
> Thanks everyone for all the help.

I'm loving Unbuntu!!

You're welcome...  Enjoy!

---

