---
title: "pack. A depends from pack.B and pack. Bdepends from pack.A: how ti install them ???"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Poliseno on 2006-10-17
Hi people!
I was intalling VLC media player on my Ubuntu Dapper Drake 6.06. I've downloaded the VLC package and all the necessary packages indicated in the installation (all the dependencies...). There is a problem: the VLC package depends from the wxvlc package, and the wxvlc package depends from the VLC package! So I cannot install vlc. How can I solve this problem ? Ah, consider that I've no internet connection on Ubuntu (I've it only on windows).

Thanks

---

### Post by petersjm on 2006-10-17
I'm not sure about wxvlc, but is there a dummy package for it? I had a problem with xlibs last week until I found a dummy package for it.

PS - Did you get VLC from the repos? That should surely sort out any dependency issues...?

---

### Post by Marsolin on 2006-10-17
You probably downloaded the Debian version. It contains a wxvlc dependency. The [VLC]("http://linuxappfinder.com/package/vlc") available from the Ubuntu repositories does not.

---

### Post by Poliseno on 2006-10-17
I'm sure that I've downloaded the ubuntu/drapper-drake version of VLC ! wxvlc requires vlc and vlc requires wxvlc.

Is there a method to install them contemporanealy ???????????

Thanks

---

### Post by Bachstelze on 2006-10-17
Why not just typing *sudo apt-get install vlc* ?

---

### Post by Poliseno on 2006-10-17
Hiiiiiiiiiiii !
I've a problem of dependencies while installing a programm (it's a .deb):
package A depends from package B and package B depends from package A. Is there a method, a command or other to installing them ???

Thank

---

### Post by Poliseno on 2006-10-17
atp-get requires internet connection, doesn't it ? Unfortunately I've not it on Ubuntu (for a driver problem...)

---

### Post by Bachstelze on 2006-10-17
Have you tried installing al your packages at once with sudo dpkg -i *.deb instead of installing them one at a time ?

---

### Post by PriceChild on 2006-10-17
eDIT

Much more sensible: [http://ubuntuforums.org/showpost.php?p=1627792&postcount=11](http://ubuntuforums.org/showpost.php?p=1627792&postcount=11)

> **Poliseno said:**
> Ah, consider that I've no internet connection on Ubuntu (I've it only on windows).
```
sudo dpkg--ignore-depends=wxvlc  -i vlc-whatever.deb
sudo dpkg -i wxvlc-whatever.deb
```Should work... i think :) never tried myself :)

---

### Post by Bachstelze on 2006-10-17
Please don't post more than one thread for the same problem.

---

### Post by CatKiller on 2006-10-17
You'd need to install them both with the same command. Something like ```
sudo dpkg -i packA packB
```

---

### Post by Poliseno on 2006-10-17
Ah, I didn't know that it was possible! Please write the command...

thanks a lot  :)

---

### Post by PriceChild on 2006-10-17
*merges*

---

### Post by Bachstelze on 2006-10-17
basically, you put all your DEBs in one single folder, browse to it in a terminal and do

```
sudo dpkg -i *.deb
```

---

### Post by Poliseno on 2006-10-17
Thanks to all, the command:

[FONT="Courier New"]sudo dpkg -i packA packB[/FONT]

works perfectly !

---

