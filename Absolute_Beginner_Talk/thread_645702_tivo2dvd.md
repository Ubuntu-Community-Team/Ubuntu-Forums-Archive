---
title: "tivo2dvd"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by unipsycho on 2007-12-20
I am trying to connect to my TiVo and ran across tivo2dvd. But compiling/configuring/resolving dependancies for this app has frustrated me endlessly. Is there another app anyone has used that is less painful to install?

---

### Post by Afkpuz on 2007-12-24
Well, I don't know about tivo2dvd, but I do have a different route you can take if you're interested.

Turns out that your tivo can be accessed over the network that its connected to.  Open up your web browser and enter in this address.  Note that it's "https", not "http".

[https://192.168.0.190](https://192.168.0.190)

You should see some messages about certificates.  These are all right.  Then, it will ask you for a user name and password.  

username: tivo
password: [your MAK]

MAK=media access key.  To find this, get on your tivo system and push the tivo button.  Goto messages and settings>Account and System info>Media Access Key.  That will tell you your MAK.

Once in the web server version of tivo, you should see a folder system with all your recorded programs.  Click the download button to download.  However, these files are in tivos proprietary format.  Here's a link to a command line based converter.

[http://downloads.sourceforge.net/tivodecode/tivodecode-0.1.4.tar.gz?modtime=1165505116&big_mirror=0]("http://downloads.sourceforge.net/tivodecode/tivodecode-0.1.4.tar.gz?modtime=1165505116&big_mirror=0")

to install, extract the tarball to a good spot.  I made a folder in my home folder called "Installs".

Open a terminal and goto that location.  
```
./configure
Make
sudo make install
```

Then finally, to use this program, download those .tivo files from the above mentioned method, and put them into the objects.dir folder within the "tivodecode-0.1.4" folder.  Put the .tivo files into the objects.dir folder and then run this command to convert.  Make sure you're in the objects.dir folder when you run this.
```
./tivodecode -m XXXXXXXXXX -o output.mpg input.TiVo 
```

Replace XXXXXXXX with your MAK.  output is the name you want to call the converted file.  Input is obviously the name of the .tivo file.  Hope this helps

---

