---
title: "Install Songbird?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2006-12-30
I downloaded Songbird media player to my desktop.
Can someone please tell me how to get it installed?
Thanks

---

### Post by taurus on 2006-12-30
What is the name of the file exactly?

---

### Post by Milt888 on 2006-12-30
The package is    songbird_0_2_1_linux-i686.tar.gz

---

### Post by taurus on 2006-12-30
I assume you've saved it to ~/Desktop.  Open a terminal and do

```
cd ~/Desktop  <-- change to where you've downloaded songbird
sudo aptitude update  <-- updating the list
sudo aptitude install build-essential  <-- you need to package before you can build anything from souce
tar xvzf songbird_0_2_1_linux-i686.tar.gz  <-- unpack it
cd songbird_0_2_1_linux-i686  <-- change into the new directory 
./configure  <-- configure songbird
make  <-- build it
sudo make install  <-- install it with sudo since it will be written to /usr/local...
songbird  <-- to run it!!!
```

---

### Post by haiku99 on 2006-12-30
if it doesn't work out Automatix2 says it will do it....have not tried that personally though

---

### Post by Milt888 on 2006-12-30
Taurus, I got an error..could not find file, or something like that, when I got to the line..tar xvzf songbird_0_2_1_linux-i686.tar.gz  <-- unpack it.
I'm probably in over my head but thanks for the help.
I extracted it to a folder, also on my desktop.
Don't guess that means much though.

---

### Post by taurus on 2006-12-30
What's the output of this command, from a terminal, then?

```
ls -la ~/Desktop
```

---

### Post by mrphd on 2006-12-30
> **Milt888 said:**
> I downloaded Songbird media player to my desktop.
Can someone please tell me how to get it installed?
Thanks

Try looking at this [http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird). This gives instructions and a script for installation.

---

### Post by Milt888 on 2006-12-30
Tarus this is it.

milton@milton-desktop:~$ ls -la ~/Desktop
total 17748
drwxr-xr-x  3 milton milton     4096 2006-12-30 15:10 .
drwxr-xr-x 22 milton milton     4096 2006-12-30 15:19 ..
drwxr-xr-x  8 milton milton     4096 2006-12-30 15:10 Songbird
-rw-r--r--  1 milton milton 18133995 2006-12-30 12:30[COLOR="Red"] Songbird_0_2_1_linux-i686.tar.gz[/COLOR]

---

### Post by Milt888 on 2006-12-30
Thanks mrphd. I'll give that a shot if this other doesn't work.

---

### Post by taurus on 2006-12-30
Okay, it's a capital **S**, not s.  Unix/Linux is case sensitive so you need to be careful with that.  

```
cd Songbird
./configure
make
sudo make install
```
Or paste the output of this command here then!

```
ls -la ~/Desktop/Songbird
```

---

### Post by Milt888 on 2006-12-30
OK taurus.
Hate to be so dense, but I don't quite understand your last instructions.

---

### Post by taurus on 2006-12-30
Just want to see the output of this command to see if you need to run the ./configure!

```
ls -la ~/Desktop/Songbird
```

---

### Post by Milt888 on 2006-12-30
OK

milton@milton-desktop:~$ ls -la ~/Desktop/Songbird
total 124
drwxr-xr-x  8 milton milton  4096 2006-12-30 15:10 .
drwxr-xr-x  3 milton milton  4096 2006-12-30 15:10 ..
-rw-r--r--  1 milton milton   223 2006-11-29 15:57 application.ini
drwxr-xr-x  3 milton milton  4096 2006-12-30 15:10 chrome
drwxr-xr-x  2 milton milton  4096 2006-12-30 15:10 components
drwxr-xr-x  3 milton milton  4096 2006-12-30 15:10 defaults
-rw-r--r--  1 milton milton 17996 2006-11-29 15:57 gpl.txt
-rw-r--r--  1 milton milton 18649 2006-11-29 15:57 LICENSE.txt
drwxr-xr-x  2 milton milton  4096 2006-12-30 15:10 plugins
drwxr-xr-x  2 milton milton  4096 2006-12-30 15:10 scripts
-rwxr-xr-x  1 milton milton 41365 2006-11-29 15:57 Songbird
-rw-r--r--  1 milton milton   241 2006-11-29 15:57 TRADEMARK.txt
drwxr-xr-x 11 milton milton  4096 2006-12-30 15:43 xulrunner

---

### Post by taurus on 2006-12-30
Looks to me like you just run it directly from there, no need to build anything!

```
cd ~/Desktop/Songbird
./Songbird
```

---

### Post by Milt888 on 2006-12-30
Well, I had run it by clicking the MIME type: application/x-executable icon in the songbird folder right after I downloaded it but thought it needed to be added to the applications some way.
Will it be necessary to leave that folder on the desktop and open it everytime to run the program?
Thanks for the help

---

### Post by taurus on 2006-12-30
You can move that directory anywhere you want.  Personally, I would move it to ~/bin and put ~/bin in your PATH so you can run it from anywhere you want without putting in the whole path...

---

### Post by Milt888 on 2006-12-30
I gotcha.
Thanks much for your help.

---

### Post by taurus on 2006-12-30
You're welcome.

---

