---
title: "total noob question"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by janneman on 2005-05-30
hi, I'm trying to run ubuntu on my compaq armada 1700 laptop.

I have severall questions:

1. after some textbased install, i can login with my pass and login, but then nothing happens only thing that happens is: jan@..... you have revieved 1 new e-mail or something like that, it's still text base, i can't get into gui or what u guys call it.
please take note i am a total rook.

2. there is another problem, sometimes, while booting, my laptop says: fatal temperature 94 degrees, shutting down, but it isn't warm at all, i've read on some websites that it's typicle for this laptop, check this site plz: [http://linux.is-a-geek.net/laptop/armada-1700-ubuntuHoary.html](http://linux.is-a-geek.net/laptop/armada-1700-ubuntuHoary.html)


thx for the help, very much appreciated.

Also take notice, that I'm from Belgium, so my English isn't that well. :)


edit: now, i just reinstalled it, but now it gives me this screen: there was a problem installing the selected software. One or more packages failed to install.

this might be because of lack of hd space, but with the install options i chose for total reformatting of my hd, or would it only use the rest of the space there was??

greetz, Jan

---

### Post by mveers on 2005-05-30
1. 
You can try

 ```
startx
``` 

If this fails:

 ```
sudo dpkg-reconfigure xserver-xorg
``` 

or

 ```
sudo dpkg-reconfigure gdm
/etc/init.d/gdm start
``` 

Hope this helps

---

