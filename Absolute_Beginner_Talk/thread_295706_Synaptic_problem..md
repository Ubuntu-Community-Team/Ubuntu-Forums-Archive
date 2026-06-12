---
title: "Synaptic problem."
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Neoito on 2006-11-08
Hi all, I'm completely new to Linux and although I'm slowly getting there I've already manged to break something.

I typed the wrong thing in the wrong place and now get this message when I try to start Synaptic.

"E: Type &#8216;sudo&#8217; is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem."

Synaptic then opens but with nothing in any of the windows, when I go to reload I get.

"E: Type &#8216;sudo&#8217; is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory"

If anyone can help I wouold be very grateful.

Also while I'm here, I'm having trouble finding the win32 codecs, anywhere I've tried (including the forums) they don't seem to be available when I try to download if anyone can point me in the right direction or even send me the files that would be great.

---

### Post by Kateikyoushi on 2006-11-08
Show us your sources.list

```
cat /etc/apt/sources.list
```

---

### Post by Henry Rayker on 2006-11-08
You've borked your /etc/apt/sources.list file one way or another. Please run:

cat /etc/apt/sources.list

and give us the output.

buuuuuu. Kateikyoushi beat me.

---

### Post by Neoito on 2006-11-08
Here ya go.

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiversedeb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.canonical.com/ubuntu dapper-commercial main
sudo gedit /etc/apt/sources.list

```

---

### Post by Kateikyoushi on 2006-11-08
Remove the last line from your sources list, that is used to edit the file it should not be IN it.

```
gksudo gedit /etc/apt/sources.list
```
Then just remove the sudo line.

---

### Post by dbott67 on 2006-11-08
Delete the last line of your sources.list file:
```
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.canonical.com/ubuntu dapper-commercial main
[COLOR="Red"]sudo gedit /etc/sources.list[/COLOR] *<--- remove this line*
```

---

### Post by Neoito on 2006-11-08
That's done it.

Thanks guys, next time you're in town I owe you a drink.

And while I have your attention, upon running easy Ubuntu or reloading the list in add/remove I'm getting this.

```
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
```

---

### Post by dwblas on 2006-11-08
That means that you are downloading software that hasn't been "verified" as safe.

---

### Post by Neoito on 2006-11-09
That's what I thought, but I figured since I was doing it through easyUbuntu it would be OK.

---

### Post by 3rdalbum on 2006-11-09
Oh yes, it will be OK, it's just that the repositories usually have a security key which is identified against, to make sure that you're really contacting the repository (and not a hacker who is breaking in on your transmission). If you haven't added information about the key, then the transmission can't be verified.

Don't worry about it, but if the website lists the repo's key, you should add that just to be safe (the site should tell you how to do that).

---

