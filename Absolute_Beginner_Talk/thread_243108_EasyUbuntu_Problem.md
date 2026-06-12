---
title: "EasyUbuntu Problem"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by neotrumatrix on 2006-08-24
I installed easyubuntu using the below and ran it

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in

then i selected the Codecs option in Multimedia and clicked ok this is what i get
attached image of the screenshot below

Can any 1 help me plz...](*,)

---

### Post by Metacarpal on 2006-08-25
Hi there

The website that the files are drawn from changed their directory structure.  The EasyUbuntu program has been updated to reflect those changes, but it looks like you're using the old version.

Try again, but change all references to "3.021" to "3.022" in your code, as such:

```
wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in
```

That should get you going.

---

### Post by neotrumatrix on 2006-08-25
I did as you told me to but got the same error msg as osted in the previous post :(

one thing was I upgraded my version of easyubuntu :)

Plz help me with this i can't live without music(n none of my mp3's play)
 !!!!!!!!!!
or pla suggest how i can install an mp3 compatible player as of now

Awaiting replies...

---

### Post by Crosbie on 2006-08-25
I prefer EasyUbuntu but you could try [Automatix]("http://www.getautomatix.com/") instead...

---

### Post by dca on 2006-08-25
I don't know if this'll do any good but this is what was in the 'readme' of the post-install of 'easyubuntu':
 
  ------------------------------------------
== To download and install EasyUbuntu ==

= Subversion =

Open a terminal (in GNOME Applications -> Accessories -> Terminal ) and type the following commands (one command per line)
sudo apt-get install subversion
svn checkout svn://freecontrib.org/easyubuntu
cd easyubuntu/trunk
sudo python easyubuntu.in
Enter YOUR password, and press <enter>.

= Nightly snapshot archive =

Open a terminal (in GNOME Applications -> Accessories -> Terminal ) and type the following commands (one command per line)
wget [http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2](http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2)
tar -xjf current.tar.bz2
cd EasyUbuntu<tab>
sudo python ./easyubuntu.in
Enter YOUR password, press <enter>.
  --------------------------------------

 
The one thing I'd like to know is if after install, can I remove the folder created in my 'home' folder???

---

### Post by neotrumatrix on 2006-08-25
> **Crosbie said:**
> I prefer EasyUbuntu but you could try [Automatix]("http://www.getautomatix.com/") instead...


Went thru the guide and installed it properly then at last this is wt i get (attached screen shot)   :( :( :( :( 

some1 help plz...

---

### Post by dca on 2006-08-25
This is gonna' sound bad but is there a problem with your network connection???

---

### Post by neotrumatrix on 2006-08-25
> **dca said:**
> This is gonna' sound bad but is there a problem with your network connection???

Well i m in a network with password protected proxy but i dunt think there is a problem with it coz i was able to wget (install all the files without any problem)

---

