---
title: "Limewire"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by captk3570 on 2006-10-20
Can anyone tell me how to install limewire in ubuntu I've installed Alien and have downloaded the Limewire rpm thanks David

---

### Post by Rule on 2006-10-20
just type "sudo alien <type package name>"

or your can try frostwire [www.frostwire.com/](www.frostwire.com/) which is the opensource version of limewire, they even have a ubuntu package.

---

### Post by captk3570 on 2006-10-20
How do I install the frostwire could you walk me through it? thanks Dave

---

### Post by captk3570 on 2006-10-20
I've installed frostwire but it will not run for some reason appreciate the help Dave

---

### Post by taurus on 2006-10-20
> **captk3570 said:**
> I've installed frostwire but it will not run for some reason appreciate the help Dave

Did you remember to install java first?  You can use Automatix to install java...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by seijuro on 2006-10-20
the fastest way for me I just download limewire basic (other os) version from limewire's website unzip it and run the bin.

---

### Post by captk3570 on 2006-10-20
I'm too new to this can you provide some more help thanks David

---

### Post by Apotheosis on 2006-10-20
Go to Add/Remove programs and click Frostwire.  From there click Apply and boom, you got it.

---

### Post by captk3570 on 2006-10-20
I have done that and it does not show up?? Am I missing something because it shows as installed but does nothing when I click on it thanks again Dave

---

### Post by taurus on 2006-10-20
Again, you NEED to install java first before you can run limewire or frostwire!!!  The easiest way is to use Automatix from the link that I've provided...

---

### Post by captk3570 on 2006-10-21
I've installed automatix but when I start it it says it is for edgy and does nothing can you help did I get the wrong version?? Thanks Dave

---

### Post by r4ik on 2006-10-21
Wrong version.
Try,

Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper) 
Edit your sources.list: 

sudo gedit /etc/apt/sources.list 
from terminal 

Substitute gedit with the text editor of your choice. 

Add the following to your sources.list: 

NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository. 

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
Now save the file and close it. 

Now from terminal do the following: 

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
To finish off: 

sudo apt-get update
sudo apt-get install automatix2

Good luck!

---

### Post by joshgtv6 on 2006-10-21
hello everyone, i'm 100% new to a Linux based OS and i'm loving it.  Ubuntu is amazing.  I am having a few issues which i'm sure i can figure out on my own once I get this main one solved.  When I click the add/remove to install programs i'm not seeing a lot of the ones that you guys are saying should be there like frostwire.  Do i need to add commands or text to a certain area in order to gain access to the entire repository or to access multiple ones?  very sorry if this has been answered elsewhere. I also followed the directions on the Ubuntu website for adding the universe repositories. I searched for about 20 minutes and I can't find the info i'm looking for.

OH, and being rid of windows was a refreshing breath of fresh air.

---

### Post by r4ik on 2006-10-21
Here's is a guide,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

You might want to give it a read. :)

Good luck !

---

### Post by captk3570 on 2006-10-21
Got it thanks alot this prog is amazing thanks guys I was able to install frostwire and java and lots of other programs again thanks David

---

