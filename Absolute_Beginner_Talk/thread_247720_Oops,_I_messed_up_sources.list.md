---
title: "Oops, I messed up sources.list"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Hoary on 2006-08-31
Or I think I did.

It was only after I installed Kubuntu Dapper-64 yesterday that I could use the computer to send a password to get onto my employer's LAN. So of course the installation procedure failed to find any software repository. No surprise or shock there, and [help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu") gave me hints on what to do. I found that all the repositories had been commented out by the installer, so for each of the entries for main/restricted stuff, I deleted the explanation of the commenting-out and "enabled" (deleted "#" from the start of) the line. Then I hit "Apply" and "Fetch updates". I didn't actually get any upgrades, but I didn't get any error message either.

Actually my purpose was to download stuff for Japanese input. The method (for Ubuntu users, perhaps not Kubuntu users) is explained at  [ubuntulinux.jp/download]("http://www.ubuntulinux.jp/download") (in Japanese). It tells me to use 

> gksudo gedit /etc/apt/sources.list

to add a couple of lines, but that didn't work and I thought I'd try editing sources.list in some foolproof way, suitable for a fool such as myself.

So I added
 
> deb *space* [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) *space* dapper/
deb *space* [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) *space* dapper-ja/

figuring that if tabs were needed instead of spaces, I'd be warned.

No warning, and I clicked "Apply"; again no warning.

But now when I clicked "Fetch updates", I read:

> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

. . . or instead does the reverse and totally screws up the database, perhaps? I thought I shouldn't do this blindly and should instead read the manpages. But I can't see anything relevant in them.

Would it be safe to reboot in terminal mode and use nano to fix this file? Or what should I do instead?

+++++

Incidentally, after installing Kubuntu for Athlon 64 I've read hints here and there that the 386 version is more stable or more complete. I have an Athlon 64 CPU. I don't care if I don't get all possible speed from this (I don't intend to play games or work on humongous graphics). Should I cut my losses, wipe out this system, and install the 386 version instead?

---

### Post by grte on 2006-08-31
> **Hoary said:**
> Or I think I did.

It was only after I installed Kubuntu Dapper-64 yesterday that I could use the computer to send a password to get onto my employer's LAN. So of course the installation procedure failed to find any software repository. No surprise or shock there, and [help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu") gave me hints on what to do. I found that all the repositories had been commented out by the installer, so for each of the entries for main/restricted stuff, I deleted the explanation of the commenting-out and "enabled" (deleted "#" from the start of) the line. Then I hit "Apply" and "Fetch updates". I didn't actually get any upgrades, but I didn't get any error message either.

Actually my purpose was to download stuff for Japanese input. The method (for Ubuntu users, perhaps not Kubuntu users) is explained at  [ubuntulinux.jp/download]("http://www.ubuntulinux.jp/download") (in Japanese). It tells me to use 



to add a couple of lines, but that didn't work and I thought I'd try editing sources.list in some foolproof way, suitable for a fool such as myself.

So I added
 


figuring that if tabs were needed instead of spaces, I'd be warned.

No warning, and I clicked "Apply"; again no warning.

But now when I clicked "Fetch updates", I read:



. . . or instead does the reverse and totally screws up the database, perhaps? I thought I shouldn't do this blindly and should instead read the manpages. But I can't see anything relevant in them.

Would it be safe to reboot in terminal mode and use nano to fix this file? Or what should I do instead?

+++++

Incidentally, after installing Kubuntu for Athlon 64 I've read hints here and there that the 386 version is more stable or more complete. I have an Athlon 64 CPU. I don't care if I don't get all possible speed from this (I don't intend to play games or work on humongous graphics). Should I cut my losses, wipe out this system, and install the 386 version instead?

I'd just look around the forums for a sources.list to use, completely delete yours, and replace it with the new one.

Then, before anything else, make sure you open a terminal and type 

```
sudo apt-get update
```

Which should resolve your issue.

As to the kernel, it's true 32-bit dapper is more stable than 64-bit.  Don't use the 386 kernel, though, use the k7 kernel.

---

### Post by deadgobby on 2006-08-31
You'll need to edit the source list agian. Do not use tabs if all possible. You can just use the copy and paste method to add to the sources list.

deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper/
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper-ja/

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

Gobby

---

### Post by angkor on 2006-08-31
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) comes in very handt in situations like this.

---

### Post by Hoary on 2006-08-31
Thank you for all your replies. I'll work on it from now.

Incidentally, I notice that "hoary" seems to have some meaning in an Ubuntu context. My username isn't intended to confuse; it's merely one I use in (K)ubuntu-irrelevant places and so I more or less automatically registered it here too.

---

### Post by grte on 2006-08-31
That's not something that's likely to confuse, considering Hoary is two versions old.  Ancient history.

---

### Post by Hoary on 2006-08-31
Good, there are no worries that I'm asking about something that's two versions old, then. 

Thank you all again for your advice. I built myself a new sources.list at [source-o-matic](http://www.ubuntulinux.nl/source-o-matic). Two more questions, though (and yes, I do realize that I may be an idiot):

1. About what to do with GPG keys.

Source-o-matic does warn:

> When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID) 
      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

Sure enough, I need to enter the GPG key for the Kubuntu repositories. Source-o-matic does provide it: DD4D5088. Do I just type in 

> gpg --keyserver subkeys.pgp.net --recv DD4D5088
      gpg --export --armor DD4D5088 | sudo apt-key add -

-- don't I have to specify what it is that this key is for? 

2. GPG key for the Japanese repository

I need this too. However, it's not mentioned on the [download page](http://www.ubuntulinux.jp/download) (where I'd expect to see it), and [search results for that site](http://www.ubuntulinux.jp/search?SearchableText=gpg) don't seem to say anything useful about a GPG key.

Yes, I know, I'm overlooking something that's stunningly obvious. . . .

---

