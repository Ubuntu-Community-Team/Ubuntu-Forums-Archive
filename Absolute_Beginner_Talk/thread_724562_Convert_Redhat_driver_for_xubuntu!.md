---
title: "Convert Redhat driver for xubuntu??!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-14
Hi,

I've got a realtek 8180L wireless card that I need to install.

I've tried to use Ndiswrapper but have come accross problems installing that. Realtek provied a Redhat driver at :

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L)

can this be installed on Xubuntu????

If so how??

Thanks

---

### Post by taurus on 2008-03-14
You can use alien to convert .rpm to .deb and install it, .deb, with dpkg -i.

```
sudo apt-get update
sudo apt-get install alien
alien **filename**.rpm
sudo dpkg -i **filename**.deb
```

---

### Post by the beak on 2008-03-14
Thanks

I dont have internet access so can I download the alien package and transfer it over to my other machine?

---

### Post by taurus on 2008-03-14
You need to grab alien and all the necessary dependencies that it needs.

[http://packages.ubuntu.com/gutsy/alien](http://packages.ubuntu.com/gutsy/alien)

---

### Post by the beak on 2008-03-14
If you look at the link the driver doesn't contain any .rpm files???

---

### Post by taurus on 2008-03-14
It's a .zip file so you need to unzip it.  Then, you need to run 

```
make 
sudo make install
-or-
sudo checkinstall
```
to build and install it.

And of course, you first need to install the build-essential package and checkinstall.  Both should be on your installer CD so insert it into a drive and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential checkinstall
```

---

### Post by the beak on 2008-03-14
Thanks,

But I don't have access to the interenet on that machine (or ethernet) so anything I download has to be transfered by USB. What is the simple alternative to apt-get?

---

### Post by taurus on 2008-03-14
Do you still have the installer CD that you used to install Ubuntu on that machine?  Build-essential should be on the installer CD.

---

### Post by the beak on 2008-03-14
Yep. 

What do I do now?

Thanks by the way!

---

### Post by taurus on 2008-03-14
Insert the CD into a drive and run

```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential checkinstall

```
Then, unzip the file and change to that new directory and build & install it.

```

make
sudo checkinstall
```

---

### Post by the beak on 2008-03-14
It's Xubuntu I'm using and it says it cant find package build-essential???

---

### Post by the beak on 2008-03-14
actually, I'v double clicked on the Alien package and its installing successfully.

Do I use this as youve said before on the driver package?

---

### Post by taurus on 2008-03-14
You don't use alien in this case.  You need to build it from source since that is what you get when you unzip the download.  Do you have the LiveCD or the alternate CD?

---

### Post by the beak on 2008-03-14
I've got the alternate CD

---

### Post by taurus on 2008-03-14
It should be on the CD.  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by the beak on 2008-03-14
I'm having trouble moving over text files.

I have the output on the other screen. I can tell you if there is anything specific to report on it?

What should I be looking for?

---

### Post by taurus on 2008-03-14
What does the first line look like, exactly?

---

### Post by the beak on 2008-03-14
deb cdrom :(Xubuntu 7.04 _feisty Fawn_ - release i386 (20070415) / feisty main restricted

---

### Post by the beak on 2008-03-14
that was meant to be :  ( not :(

---

### Post by taurus on 2008-03-14
Are you running Fiesty?  

Can you post the outputs of these two commands?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by the beak on 2008-03-14
I've ran that and it seems to work.

Yep I'm using Feisty.

---

### Post by the beak on 2008-03-14
What's the next step?

Thanks

---

### Post by joshrobinson on 2008-03-14
> **taurus said:**
> It's a .zip file so you need to unzip it.  Then, you need to run 

```
make 
sudo make install
-or-
sudo checkinstall
```
to build and install it.



as he said earlier

---

### Post by the beak on 2008-03-14
It comes up *** No rule to make target 'install'. stop            ????

---

### Post by the beak on 2008-03-14
Sorry to bother you folks on this but I feel pretty close to getting this driver on and I'm at a loss as what to do?

---

### Post by joshrobinson on 2008-03-14
i checked into that driver, its pretty old. it said its for kernel 2.6.15 and for fedora core 2
i think your better off working with ndiswrapper to get things going

i also had the same problem trying to build the driver, whenever i run make, all the files in the folder are gone.. weird

---

### Post by the beak on 2008-03-14
After : sudo apt-get install build-essential checkinstall

the log has :

E: Couldn't find package checkintall



I gues it's not on the disk.

The other comand make install prodcess the error that is posted earlier  !!??

thanks

---

### Post by the beak on 2008-03-15
Yep i get the sme wth the dissapearing files. I'll try the ndiswrapper route.

---

