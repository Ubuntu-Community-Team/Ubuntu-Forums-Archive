---
title: "A total n00b, yep that's me."
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by platinumstarr on 2005-05-19
Alrighty.

I can't update anything in Firefox without actually updating the browser.

So, I click the little link to update it at the page that says "YOU HAVE NOT UPDATED AND YOU CAN'T DO ANYTHING UNTIL YOU UPDATE!"

It's a .tar.gz package.  I did what it said, it opened it.

...what do I do from there?  I have a list of package contents in Nautilus.

Obviously, I've never used Ubuntu or Linux before.

Thanks in advance,
- Starr

---

### Post by Xian on 2005-05-19
Paste this in the navigation window:
about:config

Search for this line:
general.useragent.vendorSub

Change it to 1.0.4
You should be able to access the websites now.

---

### Post by Pusherman on 2005-05-19
I'm having the same problem that platinumstarr is having. I can download the file from [www.getfirefox.com](www.getfirefox.com) but once I have downloaded it to my machine what do I do from there?  :? 

I can extract the file to a folder on my system and run the firefox-installer, and it even goes through the motions of installing but when I run firefox again the patch number still says 1.0.2.  ](*,) 

Thanks for any help 
Pusherman.

---

### Post by bored2k on 2005-05-19
[QUOTE=Pusherman]I'm having the same problem that platinumstarr is having. I can download the file from [www.getfirefox.com](www.getfirefox.com) but once I have downloaded it to my machine what do I do from there?  :? 

I can extract the file to a folder on my system and run the firefox-installer, and it even goes through the motions of installing but when I run firefox again the patch number still says 1.0.2.  ](*,) 

Thanks for any help 
Pusherman.[/QUOTE]
 Try flushing/emptying your cache and all system information/passwords then do the general.useragent.vendorSub trick again.

On a small sidenote, we moderators are really interested in filtering denigrating words like n00b from the forums. So if we could all please make an effort to avoid using these, the forums would be a bit more friendlier :D.

---

### Post by Arthemys on 2005-05-20
When you do manage to run the install script, make sure to do run it in sudo and to install to: /usr/lib/mozilla-firefox

Hope that helps some.

---

### Post by platinumstarr on 2005-05-20
See, I don't know how to run a script.  I have absolutely no idea on how to do any of this.

I went to the ubuntu guide site and found something that should help me - if it would work.  Yet, here's my post on another forum.

> [It](http://www.ubuntuguide.org/#extrarepositories) tells me to do a command, exit the file, and save and close. I'm trying to install Flash Player in Firefox and it says to do this first.

Thing is, the part of the file it tells me to find isn't present. Instead, mine just says:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by digby on 2005-05-21
OK... I think that I can help you. You will have to use a little bit of command line stuff for this, but I'll walk you through it. I'm assuming that you already have the .tar.gz file downloaded to your home directory, so I think the first thing you want to do is remove the old version of firefox.
```
$sudo apt-get remove mozilla-firefox
```
Now we get to the actuall installing part.  From the directory where the file is stored (I assume /home/your username/ -
```
$tar -xvzf firefox-1.0.4.installer.tar.gz
```
You can probably just type that through "firef" and hit tab to autocomplete the rest of the filename. This will unzip the archive and place all the files into a new directory inside your home directory. Now we have to go into that directory to run the actual installer.
```
$cd firefox-installer/
```
And now we get to run the installer:
```
$sudo sh firefox-installer
```
From here out, it's pretty much point and click. When it asks where you want to install to, I recommend /opt since that is the place in the filesystem for user installed programs. A lot of people will install their stuff to /usr/share or /usr/local, but technically, that is only for stuff installed by the system (if I remember correctly). Let us know if you have any trouble with this.

---

### Post by platinumstarr on 2005-05-21
It says that the -xvzf part of $tar -xvzf firefox-1.0.4.installer.tar.gz is not a valid command.

---

### Post by digby on 2005-05-21
Hmm... you aren't typing the '$' are you?  The standard prompts are $ for normal user and # for root user.  I just put them in so you would know that I wasn't expecting you to run anything as root.

---

### Post by bored2k on 2005-05-21
[QUOTE=digby]Hmm... you aren't typing the '$' are you?  The standard prompts are $ for normal user and # for root user.  I just put them in so you would know that I wasn't expecting you to run anything as root.[/QUOTE]
 And also just why are you running the installer as sudo ..

---

