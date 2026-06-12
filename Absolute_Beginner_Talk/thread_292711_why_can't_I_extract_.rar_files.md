---
title: "why can't I extract .rar files ?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-11-04
my almost ONLY reason for keeping windows is that ubuntu Linux don't extract well archive files like .rar 
I've installed 4 archive programs and none of them extract .rars good.

why ? what can I do ?

---

### Post by localuser on 2006-11-04
Have you tried Automatix?  I believe that one of the utilities that it has as an optional install is a rar archiving tool.

---

### Post by spinflick on 2006-11-04
If you dont tell us which one's you have already tried how can anyone help?:rolleyes:

---

### Post by den benne on 2006-11-04
just install "rar", it's in the repositories
or else install via [automatix](www.getautomatix.com)

then, you can simply extract rar-files using file-roller or through the command line

---

### Post by _simon_ on 2006-11-04
It's VERY easy to add .rar support.

Download the latest rar [http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz](http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz)

Extract the contents.

Then copy the file "rar" to /usr/bin

Note - you ONLY need that one file.

You will now find that the archive manager can open rar files

---

### Post by MaximB on 2006-11-04
thanks - the automatrix did the trick.

---

### Post by Cynical on 2006-11-22
Next time, just do

```

sudo apt-get install unrar-nonfree

```

---

### Post by Roofie on 2006-12-01
I have been having same problems cannot extract any rar files?
Sounds easy enough

[COLOR="Red"]It's VERY easy to add .rar support.
Download the latest rar 
```
http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz
```
Extract the contents.
Then copy the file "rar" to /usr/bin
Note - you ONLY need that one file.
You will now find that the archive manager can open rar files[/COLOR]

Only problem i have now when i try to add the rar it says i dont have permission?

So i tried this to

[COLOR="Red"]Next time, just do

Code:

sudo apt-get install unrar-nonfree
[/COLOR]

Still not happening, this is what i get..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar-nonfree has no installation candidate

Can anyone explain to me this i have no idea what im doing but do want to learn](*,)

---

### Post by LLRNR on 2006-12-01
No problem, let's get back to that .tar.gz you downloaded. You extracted a file called (let's say) *NameOfFile*, ok? You only need to open a terminal and type in (*assuming that file is placed on your desktop*):
```
sudo cp ~/Desktop/NameOfFile /usr/bin
```type in your password and you'll have it there :)

LLRNR

---

### Post by Ben Sprinkle on 2006-12-01
> **Roofie said:**
> I have been having same problems cannot extract any rar files?
Sounds easy enough

[COLOR="Red"]It's VERY easy to add .rar support.
Download the latest rar 
```
http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz
```
Extract the contents.
Then copy the file "rar" to /usr/bin
Note - you ONLY need that one file.
You will now find that the archive manager can open rar files[/COLOR]

Only problem i have now when i try to add the rar it says i dont have permission?

So i tried this to

[COLOR="Red"]Next time, just do

Code:

sudo apt-get install unrar-nonfree
[/COLOR]

Still not happening, this is what i get..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar-nonfree has no installation candidate

Can anyone explain to me this i have no idea what im doing but do want to learn](*,)

Do this:
```

sudo wget http://rarlabs.com/rar/rarlinux-3.6.b6.tar.gz
sudo cd /usr/bin
sudo tar -xvf /pathto/rarlinux-3.6.b6.tar.gz
sudo rm /pathto/rarlinux-3.6.b6.tar.gz
sudo unrar e rarfile.rar

```
Last line is to extract an archive in current directory.

---

### Post by Bachstelze on 2006-12-01
You just need to enable the universe repository ;) please paste the contents of */etc/apt/sources.list*

---

### Post by CatKiller on 2006-12-01
> **Roofie said:**
> sudo apt-get install unrar-nonfree

E: Package unrar-nonfree has no installation candidate


That sounds like you haven't enabled the Universe and Multiverse [repositories]("https://help.ubuntu.com/community/Repositories"), although I think that the name has changed - it's **unrar** and **unrar-free** now, I think.

Personally, I'd do ```
sudo aptitude install rar
``` since that integrates with File Roller.

---

### Post by Roofie on 2006-12-01
Thank you for the help...
Now i can get into the rar files!
Some day ill figure out this:)

---

