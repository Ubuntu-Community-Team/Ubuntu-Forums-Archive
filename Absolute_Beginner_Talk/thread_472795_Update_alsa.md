---
title: "Update alsa"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-06-13
Can someone give me simple instructions to update alsa on ubuntu fiesty?
I want to use my laptop and I found this:
[http://www.linlap.com/wiki/Toshiba+Satellite+L35](http://www.linlap.com/wiki/Toshiba+Satellite+L35)

It says if I have rc4 alsa then my sound should work. I found a ubuntu guide on how to update it but I couldn't understand it. I must have been doing something wrong because the computer wouldn't boot when I was done.

Please please please(I'm begging) will someone give me some simple step by step for idiots instructions?
A THOUSAND THANK YOUS. :)

---

### Post by dannyboy79 on 2007-06-13
wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install 
OR 
sudo checkinstall
NOTE: BUT you need checkinstall installed first, this will create a .deb that you can install/uninstall with the package manager instead of having to leave the directory there in case you need to remove it which I don't know how to remove stuff you installed using sudo make install that's why I use checkinstall but sometimes checkinstall does NOT work. not sure why.

Then REBOOT. 

that should be it.
__________________

---

