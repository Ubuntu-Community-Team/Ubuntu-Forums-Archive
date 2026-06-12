---
title: "have extracted now what!?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Ale 4 sexy Lexi on 2006-10-12
I have instaled ubuntu a while ago and now i am starting to look at other programs not found in "add and remove" like quake 3 arena, xfire for gaim,
but as soon as i have extracted files like this i come to a BRICK WALL.

I know exe.files dont exist in linux and have tried looking at "add and remove" advanced and non, but still dont know how to get the files installing,

please help.

---

### Post by Ben Sprinkle on 2006-10-12
Go in terminal:
```

sudo aptitude

```
Search for your product and fool around, or you can do:
```

sudo dpkg -u productname

```
I think -u is uninstall. Someone correct me if wrong.
You can also search for it in synaptic.

---

### Post by PriceChild on 2006-10-12
You can always try [http://gaming.gwos.org/](http://gaming.gwos.org/) for guides on getting many games going.

---

### Post by tommcd on 2006-10-12
Are you trying to install a program from source code (.tar.gz, .tar.bz)? If so, see this:
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)
See the section on .tar files.

---

### Post by deadgobby on 2006-10-12
> **Ale 4 sexy Lexi said:**
> I have instaled ubuntu a while ago and now i am starting to look at other programs not found in "add and remove" like quake 3 arena, xfire for gaim,
but as soon as i have extracted files like this i come to a BRICK WALL.

I know exe.files dont exist in linux and have tried looking at "add and remove" advanced and non, but still dont know how to get the files installing,

please help.
 GAIM is and should be in Synaptic, or you can install Automatix or Easy Ubie too. 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
[https://wiki.ubuntu.com/EasyUbuntu](https://wiki.ubuntu.com/EasyUbuntu)
 Synaptic has loads of programs. So check Synaptic before compile from source or installing a RPM or Debian package.

---

### Post by Ale 4 sexy Lexi on 2006-10-12
ok let me just show you what i mean and how far i got,

i have just a little while ago tried to install xfire for linux

[http://www.linux-gamers.net/modules/news/article.php?storyid=841](http://www.linux-gamers.net/modules/news/article.php?storyid=841)

i downloaded it then extracted it,

now what.

---

### Post by picpak on 2006-10-12
I did a bit of searching, and found a .deb file of gaim-xfire:

[gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb](http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/g/gf/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb)

Hope that helps.

---

### Post by Ale 4 sexy Lexi on 2006-10-12
ok now do i have to buy this coz i cant find the download button on the Automatix webpage.

---

### Post by Ale 4 sexy Lexi on 2006-10-12
it dose pikpack but i whant to know how to install everyfile i get.

---

### Post by deadgobby on 2006-10-12
You can open up the foler after you extract it. Look for the INSTALL. It will give you instructions how to compile it. If you are not certian how to compile from source. Some one gave you a link to Monkeyblog, it pretty simple, there is all so
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
 Since you extracted it all ready. You can skip to
cd File NAME
./configure
make
sudo make install
 It may be some what confusing, like if you are not use to compile from source. Yea, it would be great if it was like a exe in windoz. 

gobby

---

### Post by picpak on 2006-10-12
It's right here:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

The one you're looking for is:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386.2C_AMD64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386.2C_AMD64_.28Dapper.29)

Hope that helps!

---

### Post by deadgobby on 2006-10-12
> **Ale 4 sexy Lexi said:**
> ok now do i have to buy this coz i cant find the download button on the Automatix webpage.

Here you go champ.
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_PowerPC_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_PowerPC_.28Dapper.29)

---

### Post by Ale 4 sexy Lexi on 2006-10-12
ok im understand it more but i cant find Automatix2

---

### Post by deadgobby on 2006-10-12
Did you open up your new friend the Terminal? It can be found at
Appilcations>Accerories>Terminal. Read the directions on Automatix web site. You can copy and paste the commands. When the termianl ask you for a password. It is your password that you login to Ubie at the splash screen.
 Installing on (K,X)Ubuntu 6.06 PowerPC (Dapper)

Edit your sources.list:

sudo gedit /etc/apt/sources.list

Add the following to your sources.list:
 ( A window will open and you can see your sources list. Scroll down and next just copy and paste the below text that starts with "deb"
Once you have copy and paste. Click on save and continue)

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Next you must get our GPG key in order to authenticate our repository:
 ( Copy and paste the first line, then the secoudn line, and finally the 3rd line )

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:
 ( Copy and past at one at a time, the first line of text below and then after the terminal does it mojo of updating. Copy and paste the secound line of text.)

sudo apt-get update
sudo apt-get install automatix
 Either you can type Automatix in the terminal or do what the secound line of text is instructing to do. 

run Automatix either with the command "automatix" or by its launcher in Applications>System Tools>Automatix.


Gobby

---

