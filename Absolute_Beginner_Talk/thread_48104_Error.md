---
title: "Error"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-11
I've had this error come up a couple of times now while in Synaptic:

"E: /cdrom//pool/main/s/sane-backends/libsane_1.0.15-4ubuntu2_i386.deb:  corrupted filesystem tarfile - corrupted package archive: Success"

I thought Synaptic resolved all dependency issues itself. Can someone translate and give me the meaning of the above statement with perhaps a remedy to accompany the problem,

As always, very grateful for all input,

sophtpaw

---

### Post by manicka on 2005-07-11
It looks to me like you haven't got your ubuntu install cd in the drive or it is damaged in some way

---

### Post by Leif on 2005-07-11
If you've got a working internet connection, you might want to remove the cdrom from your sources as you'll get the most up to date versions online. Do "sudo gedit /etc/apt/sources.list", and put #s in front of the lines about the cdrom. Then do a "sudo apt-get update"

---

### Post by sophtpaw on 2005-07-11
[QUOTE=manicka]It looks to me like you haven't got your ubuntu install cd in the drive or it is damaged in some way[/QUOTE]

I have got my ubuntu install cd in the drive (inserted upon request) but i don't see how it can be damaged, but, yes, it is a possibility agues. 
I made the cd off the disc that came with Linux Format magazine

I love the quote!

regards,

sophtpaw

---

### Post by sophtpaw on 2005-07-11
[QUOTE=Leif]If you've got a working internet connection, you might want to remove the cdrom from your sources as you'll get the most up to date versions online. Do "sudo gedit /etc/apt/sources.list", and put #s in front of the lines about the cdrom. Then do a "sudo apt-get update"[/QUOTE]


Hi Leif,

I've taken the cd out and when i put "sudo gedit /etc/apt/sources.list" sure enough i get a list: 


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


........but i don't understand your next instruction, ' put #s in front of the lines about the cdrom.'

I did do the final instruction, 'sudo apt-get update' but nothing happens, which presumably only works if the second one has been done properly.

Can you slowly and clearly take me through the steps for doing an update, please?

thank you

sophtpaw

---

### Post by Leif on 2005-07-11
OK,  what you need to do is replace the line

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

with 

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

I'd suggest you end up with a file that looks like this :

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by sophtpaw on 2005-07-11
Sorry, i'm a real newbie. I don't get what i have to do, or how  :? 

[QUOTE=Leif]OK,  what you need to do is replace the line

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

with 

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


You say to replace one line with the other, but to me they look just the same?! 
Perhaps you could be more specific about  what, where and how. I need you to walk me through this,

thank you very much

sophtpaw


I'd suggest you end up with a file that looks like this :

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/QUOTE]

---

### Post by sophtpaw on 2005-07-11
[QUOTE=Leif]OK,  what you need to do is replace the line

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

with 

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

I'd suggest you end up with a file that looks like this :

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/QUOTE]


I found the error of my ways. I put the '#' in front of the top line to make it look: #deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

i think everything looks like you are suggesting; but now what?


thx

sophtpaw

---

### Post by Leif on 2005-07-11
Now you do a "sudo apt-get update" followed by a "sudo apt-get dist-upgrade" to make sure everything is up to date, and after that everything should work fine.

---

### Post by sophtpaw on 2005-07-11
[QUOTE=Leif]Now you do a "sudo apt-get update" followed by a "sudo apt-get dist-upgrade" to make sure everything is up to date, and after that everything should work fine.[/QUOTE]
 Hello Leif,

thanks so much. After sudo apt-get dist-upgrade the following transcript appears:


sophtpaw@x1-6-00-0b-6a-16-78-f0conrad:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libsane-dev: Depends: libsane (= 1.0.15-4ubuntu2) but it is not installed
  python2.4-imaging-sane: Depends: libsane (>= 1.0.11-3) but it is not installed  sane-utils: Depends: libsane (>= 1.0.11-3) but it is not installed
  xsane: Depends: libsane (>= 1.0.11-3) but it is not installed 


...what do i do about all these libsanes? versions 1.0.11-3 and 1.0.15-4ubuntu2? do i do a google search and try to install them that way. Do we use rpm's in debian?

mille grazie

sophtpaw

---

### Post by Leif on 2005-07-11
Try the `apt-get -f install' that's suggested

---

### Post by az on 2005-07-11
If you have a currupted package database, tyou may need to do:

sudo dpkg --clear-avail

If you keep getting the errror about currupted package.

---

### Post by sophtpaw on 2005-07-11
[QUOTE=Leif]Try the `apt-get -f install' that's suggested[/QUOTE]


thanks for your patience,

I think that's sorted now. Synaptic update manager says i'm all done, so...

thank you Leif,

sophtpaw

---

