---
title: "Help with bittorrent"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by ArmadaEnder on 2005-12-18
Hello everyone,

I just installed Ubuntu 5.10 on an old computer of mine and I must say that it's a ton better than playing with it off the live cd. However, here in lies my problem:

Whenever I try to download a file using bittorrent, I get the error message box:

Problem connecting to tracker....timeout exceeded

Then the torrent continues to run yet I don't download anything. I tried with firestarter both on and off and I can't get it to work, any suggestions?

PS. I'm an ultra noobie when it comes to linux and the way it runs so anything having to do with code will have to be explained to the fullest extent. I'm sorry about this and I'm trying to learn everything as quickly as possible (reading whatever literature I can get my hands on, and simply diving into the OS). Again, thank you so much for your time in helping me with this.

---

### Post by ArmadaEnder on 2005-12-18
Also, I was trying to install alien through the *sudo apt-get* way and the following error message comes up:

*E: dpkg was interrupted, you must manually run 'dpkg  - - configure -a' to correct the problem.*

I tried to simply copy and paste this into the teminal and this comes up:

*dpkg: requested operation requires superuser privilege*

I don't know how this is possible because I am the superuser, the only user in fact, of this system. From here, I have no idea where to go. Any ideas? 

Thank you guys and gals for your time.

---

### Post by neoltlink on 2005-12-18
Well, for the 'dpkg -- configure -a' I think you need to type in sudo before it, like:
```
sudo dpkg - - configure -a
```
Not sure if you tried that. Sorry I couldn't be of more help, just started myself :P

---

### Post by bionnaki on 2005-12-19
what happens if you use a different bittorrent client?

does this problem still exist if you apt-get remove firestarter?

---

### Post by tabinin on 2005-12-19
[QUOTE=ArmadaEnder]Whenever I try to download a file using bittorrent, I get the error message box:

Problem connecting to tracker....timeout exceeded

Then the torrent continues to run yet I don't download anything. I tried with firestarter both on and off and I can't get it to work, any suggestions?
[/QUOTE]

Do you have a router between your internet connection and your Ubuntu box?  If you do, you will need to forward the ports for BT in the router to your PC.  6881-6889 are the standard ports for Bit Torrent, but you might want to add some "non-standard" ports as well, maybe 10001-10010.  I am not too sure of the security implications of that, but It get good results.

---

### Post by ArmadaEnder on 2005-12-19
Thank you very much for your responses

[QUOTE=neoltlink]Well, for the 'dpkg -- configure -a' I think you need to type in sudo before it, like:
```
sudo dpkg - - configure -a
```
Not sure if you tried that. Sorry I couldn't be of more help, just started myself :P[/QUOTE]

I tried that and this is what I got:

[I]chris@ubuntu:~$ sudo dpkg -- configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' ![/I]

Then after following the help guide, I tried:

[I]chris@ubuntu:~$ dpkg -r|--remove | -P|--purge <firestarter>
bash: syntax error near unexpected token `newline'[/I]

Frankly I have no idea what the heck is going on and why this is so hard to do something so simple. If anyone can do this step by step I would GREATLY appreciate it. I've spent all day on this and frankly I'm about ready to just give up and go back to xp...as horrifying as that sounds. Again, thank you so much for your time.

---

### Post by ArmadaEnder on 2005-12-19
[QUOTE=tabinin]Do you have a router between your internet connection and your Ubuntu box?  If you do, you will need to forward the ports for BT in the router to your PC.  6881-6889 are the standard ports for Bit Torrent, but you might want to add some "non-standard" ports as well, maybe 10001-10010.  I am not too sure of the security implications of that, but It get good results.[/QUOTE]


How would one do that? 

Again thank you so much for your time.

---

### Post by LoclynGrey on 2005-12-19
I use Ubuntu and Azureus bit torrent of which I installed via automatrix, I also run firestarter firewall.

To get the torrent system to work I had to open a port (6881) and port forward through my adsl modem, which is a horrible Dlink DSL-302G. (a very poor Dlink attempt at a modem/router)
In firestarer I added the port as an "allowed service" (so that firewall allows the port to be open)
You can also test your ports using [http://www.grc.com/](http://www.grc.com/) and do a port check ensuring the port is open.

---

### Post by ArmadaEnder on 2005-12-19
I downloaded bittornado and that seems to be working the best thus far. I know I have a few port problems with my router and I have yet to figure those out but so far  I'm happy with the results. Again, thank you all who helped me. Your kind work was GREATLY appreciated.

---

### Post by tabinin on 2005-12-20
[QUOTE=ArmadaEnder]How would one do that? 

Again thank you so much for your time.[/QUOTE]


It depends on the make of your router.  Which one do you have?  If it is a D-Link, open a browser and go to [http://192.168.0.1](http://192.168.0.1)

Every router should have a web-based config page where you can tell it which ports to forward to which IP address on your local network (e.g. your PC).

---

