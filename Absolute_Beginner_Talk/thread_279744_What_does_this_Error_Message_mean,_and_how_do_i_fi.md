---
title: "What does this Error Message mean, and how do i fix it?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by badboybrody on 2006-10-18
Started up my linux today and there was this little starburst next the speakers on the title bar. When I clicked on it I was shown the error message I pasted below. What does this mean, and how do I fix it? Thank you very much.
E: Malformed line 33 in source list /etc/apt/sources.list (absolute dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by Anonii on 2006-10-18
Please, post the output of
**cat /etc/apt/sources.list**

---

### Post by raul_ on 2006-10-18
do what anonii told OR, open your sources.list file, go to line 33 and see what's wrong with it. compare that line with the others and try to see what's wrong =)

---

### Post by jd65pl on 2006-10-18
You could get your self a new sources list from [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") and replace the one with the errornous line.

---

### Post by badboybrody on 2006-10-18
Hopefully this what you are looking for. I wasn't even sure were to begin. Thank you. I will also try to track it down now that I have a starting point. 

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

---

### Post by kingjere on 2006-10-18
I don't get it, where is line 33?
The only thing I see wrong is that it is desperatly incomplete.

---

### Post by Anonii on 2006-10-18
You better off creating another sources.list, I cant find your error there.
Try this: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
The instructions are short, easy and fast to complete.

---

### Post by badboybrody on 2006-10-18
Thanks, followed the directions amd made a new list. Now what? Do I copy Paste it into the repository or what? Sorry but I'm still trying to figure this linux stuff out. Thanks.

---

### Post by jd65pl on 2006-10-18
do this in the terminal

```
sudo gedit /etc/apt/sources.list
```Copy the list you got and paste it over the information already there

Save the file with the new list in place

---

### Post by raul_ on 2006-10-18
And save it =D lol...now open synaptic, and do "reload" ...it should be working now

---

### Post by Mimsy on 2006-10-18
But do **gksudo** gedit /etc/apt/sources.list instead. Always gksudo when you want to open something that has a graphical interface. [Aysiu says it makes life easier.]("http://www.psychocats.net/ubuntu/graphicalsudo") :)

/Mimsy

---

### Post by badboybrody on 2006-10-18
Ok did that and that part all went fine. I saved everything.(Thanks Raul)
I made a source list bygoing down the selections and checking waht I thought was needed. Its 2 pages long so I won't post it. I received an error message about missing keys. So I went back and remove those items that had no keys, programs such as Opera and some Kubunta stuff, still received error messages. So I just checked the Top 2 offerings and and the list generated still gave me an error meesage when I tried to install it.
This is the error message I keep receiving. Now what? Thanks
[ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg:](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg:) Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '

---

### Post by badboybrody on 2006-10-18
Thank you, I"m giving that a try too. Some day I will get these programing commands figured out.](*,) Reminds me of DOS from the 80's and early 90's.

---

### Post by Anonii on 2006-10-18
Mimsy's advice wont change anything.

I'm wondering if its the server that causes the error. Could you try different country's mirrors? Like gb? Or in the worst, gr, which is Greece, I'm using right now, and they work.

Thank you.
(When we fix your problem, I'll try to provide you info on what you changed, why, and how they work.)

---

### Post by Mimsy on 2006-10-18
> **Anonii said:**
> Mimsy's advice wont change anything.

No, not really, and for gedit, I don't think it matters. But since it does in other cases, it's a good habit to have... I'd hate to have to reinstall again. Setting things up the way I want them after an install takes forever.

/Mimsy

---

### Post by Anonii on 2006-10-18
> **Mimsy said:**
> No, not really, and for gedit, I don't think it matters. But since it does in other cases, it's a good habit to have... I'd hate to have to reinstall again. Setting things up the way I want them after an install takes forever.

/Mimsy


True, but he said that he "would give it a try, too", which wouldnt change anything in this particular situation.

---

### Post by Mimsy on 2006-10-18
Not the least. I should probably have been a bit more clear on that; sorry about that.

/Mimsy

---

### Post by badboybrody on 2006-10-18
Well I tried gb and gr. I also went and made sure all the keys listed were isnstalled per the directions. Now I get this error message. So were would I find the public keys I need? As a note of interest I did a Google search and found out I am not the only one this has happened to. Thanks for all your help. I will keep seeing what I can come up with.
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following

---

### Post by badboybrody on 2006-10-18
Ok Folks, I am not sure what worked but something did. Plus I received notice of 2 updates and they installed fine. Also even tho I received an Opera error, Opera installed no problem. So thank you for everything I greatly appreciate it. Hopefully someday I will get all this linux language figured out. Have a good evening.:D

---

### Post by raul_ on 2006-10-18
That someday will come sooner than u think :)

---

### Post by Mimsy on 2006-10-18
And what is really cool about Ubuntu is that once you have set things up the way you want them, they stay that way. The system is stable. After over ten years in Windows, this "stability" concept is deeply fascinating to me.

/Mimsy

---

### Post by picpak on 2006-10-18
> **badboybrody said:**
> Well I tried gb and gr. I also went and made sure all the keys listed were isnstalled per the directions. Now I get this error message. So were would I find the public keys I need? As a note of interest I did a Google search and found out I am not the only one this has happened to. Thanks for all your help. I will keep seeing what I can come up with.
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following

What's going on is that you haven't installed any public keys. Basically, they authenticate that your repositories are safe. Run these commands to fix the problem with Opera:

```
sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
sudo gpg --fingerprint 6A423791
sudo gpg --armor --export  6A423791| sudo apt-key add -
```

And for Kubuntu.org:

```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
rm kubuntu-packages-jriddell-key.gpg
```

---

### Post by badboybrody on 2006-10-19
Thanks, I will take care of that right away. I am slowly getting the hang of this. I have to admit, overall this is at least more fun than what I used to have to do in DOS and seems much more rewarding. Thanks.

---

### Post by TheGrinch on 2006-11-11
Purfect. I had the same problem. Replacing the source list worked a treat for me. 

Thanks guys

---

