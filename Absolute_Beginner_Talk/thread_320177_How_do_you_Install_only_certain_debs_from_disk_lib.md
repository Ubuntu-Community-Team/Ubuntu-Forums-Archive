---
title: "How do you Install only certain debs from disk library"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by skew on 2006-12-16
I have a question regarding the installing deb packages that i can't find an answer for, I hope someone here can help out.

I only have a dialup connection to the net so everytime i download a package(deb) from a repository I save it to a dvd. 
I've now got hundreds of them on disk, the accumulation of hundred of hours of downloading.  I'm now trying to install 
a package to a new system using these files which requires dependencies upon dependencies, etc,etc be installed first. 

  My Question is what command or series of commands can I use to have the dpkg program or some other installation program 
look for these required dependences in the same folder that the package i'm installing came from.  It seems ridiculous to 
have to have to go on line to download a required dependancy that I've already got it on disk.  ](*,) 


Stephen

---

### Post by az on 2006-12-16
> **skew said:**
> I have a question regarding the installing deb packages that i can't find an answer for, I hope someone here can help out.

I only have a dialup connection to the net so everytime i download a package(deb) from a repository I save it to a dvd. 
I've now got hundreds of them on disk, the accumulation of hundred of hours of downloading.  I'm now trying to install 
a package to a new system using these files which requires dependencies upon dependencies, etc,etc be installed first. 

  My Question is what command or series of commands can I use to have the dpkg program or some other installation program 
look for these required dependences in the same folder that the package i'm installing came from.  It seems ridiculous to 
have to have to go on line to download a required dependancy that I've already got it on disk.  ](*,) 


Stephen
Offhand, here is how you turn your directory into a local repostory:

Install dpkg-dev and cd into the directory where you have all these debs.

Run

dpkg-scanpackages . /dev/null > Pakcages

Then add the line

deb file:/wherever/your/directory/is/ 
and the 
sudo apt-get update
sudpa apt-get install whatever.


I am not in front of an ubuntu box right now, but that's pretty much it.  You can also make a cd using the AptMoveHowto wikipage.

help.ubuntu.com

---

### Post by skew on 2006-12-17
Thanks azz, that did the trick! 

I also used the *"AptMoveHowTo/simple"* page as well to create a Cd.  Once again a very hearty thanks!!:D

---

