---
title: "I cannot install anything from &quot;sudo apt-get update&quot;"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by shankhs on 2007-08-25
I am a complete newbie to Linux and to Ubuntu so I have no idea whatsoever that after reading the articles here I tried "sudo apt -get update" its giving error like this:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Sources
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages
  407 Proxy Authentication Required
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages
  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.gz)  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I am lost.Plz help me I need instant help as I have to learn basic of Linux (As an assignment) in my college till September end.Can you plz suggest me from where online I can learn the basics of Linux?:confused:

---

### Post by A$h X on 2007-08-25
To install packages simply goto applications > add/remove. Then a list will appear in the right-hand window of all the programs you can install.
These forums are pretty good if you want to learn more about ubuntu and linux in general.

---

### Post by shankhs on 2007-08-25
Thanx A$H X I tried Add/remove BUT it said
<b>Could not Download all repository index</b>
I am connected to Internet and writing from Mozilla,from where I can browse 'Successfully'.
Any Comments???

---

### Post by graigsmith on 2007-08-25
perhaps your internet connection isn't working right.   are you behind some kind of firewall?

---

### Post by shankhs on 2007-08-25
There is the college lan ahich requires authentication whenever I have to open any site,else I dont think I have any problem as far as internet is concerned.
 I am writing to you because there is Internet running smoothly.
I think installation can only be done if there is no authentication requirement.
Do you  have any means so that I can make installation procedure bypass the authentication stage?Or any other way?

---

### Post by meierfra on 2007-08-25
Check out this link:

[http://ubuntuforums.org/showthread.php?t=63496&highlight=apt.conf+http+proxy]("http://ubuntuforums.org/showthread.php?t=63496&highlight=apt.conf+http+proxy")

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by Tiger-Smith on 2007-09-10
It cant connect to the repo servers, this means either the internet your running this of isnt allowing it to check for applications/updates, or the repo is corrut, assuming your using gnome try "gksudo gedit /etc/apt/sources.list" without the quotes and post what you see..

---

