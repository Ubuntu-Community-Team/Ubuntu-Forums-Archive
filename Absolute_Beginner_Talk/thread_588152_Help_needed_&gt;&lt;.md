---
title: "Help needed &gt;&lt;"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by FusionAura on 2007-10-23
Hello all,

I am very new to Ubuntu, but i basically have been using Windows for quite a while and i am very comfortable with the system...However, recently my computer has gained quite a number of malware and i have decided to switch to Ubuntu/Linux...This being the first time that i have used Linux, alot seems new to me and i need great help in finding my way around...I have tried looking through the help files...and i find that the ones online are all 7.04, i am currently using 7.10...


Questions:
1) Is it possible to use the same commands from 7.04 in 7.10? 
I am currently trying to access my backup in my NTFS Hard disk...only to find that Linux does not support it...as a result i look to running a virtual system of Windows to open/access /transfer it to my Ubuntu now.

2) I am currently 15...I still play runescape...i have tried installing Java...But FAILED, the normal Firefox way of installing via Plugins does now work...I am running an Intel i386 System type...

3) Is there a need for an Anti Virus?
I have surfed to web for some Anti Viruses...is there a need for it? or am i perfectly safe without one...

4) After multiple downloading of several Linux installations, i find that most of them are in .bin, or a install-sh file name...may i know how do i actually install these type of file names?



Thank You for your time spent on reading my thread,
FusionAura...


P.S. Hope you can answer it !

---

### Post by Qwerty_ on 2007-10-23
Question 1

To use NTFS drives in Ubuntu you must firstly install some software and set it up.

You can do this by opening a terminal Applications>Accessories>Terminal

And use the following code.

```
sudo apt-get install ntfs-config
```
Once it has downloaded and installed run

```
sudo ntfs-config
``` and select your required settings.

Q2 You can download the java stuff from sunmicrosystems. Then just run in the installer.

Q4

To install applications you generally have to type sudo ./ file name.

(There is another proper command someting like .sh but it elludes me at the present)

Hope that helps.

---

### Post by FusionAura on 2007-10-23
The main problem for installing java is that when i actually run it...it opens up GEDit, and says that it cannot find the file...


Edit: As for the sudo is it 

```

sudo "File Name"
```

Or 
```

sudo ./ "Filename"
```


Also do we have to specific where the file is?

---

### Post by Wobedraggled on 2007-10-23
Questions:
1) Is it possible to use the same commands from 7.04 in 7.10? 
I am currently trying to access my backup in my NTFS Hard disk...only to find that Linux does not support it...as a result i look to running a virtual system of Windows to open/access /transfer it to my Ubuntu now.

**The commands remain the same, go get automatix this will install many of the things you need, such at ntfs support and java,.** Edit: the NTFS support is no longer there, go with the user comment above.

[**http://www.getautomatix.com/**](**http://www.getautomatix.com/**)



2) I am currently 15...I still play runescape...i have tried installing Java...But FAILED, the normal Firefox way of installing via Plugins does now work...I am running an Intel i386 System type...

**See above.**

3) Is there a need for an Anti Virus?
I have surfed to web for some Anti Viruses...is there a need for it? or am i perfectly safe without one...

**You are pretty safe, there is clamAV if you are paranoid. also in Automatix**

4) After multiple downloading of several Linux installations, i find that most of them are in .bin, or a install-sh file name...may i know how do i actually install these type of file names?

**You should only be installing .deb packages either from the synaptic package manager or Automatix, or a downloaded .deb file One step at a time ;)**


Hopefully this helps.

---

### Post by Qwerty_ on 2007-10-23
I just did a quick search and found this article.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by FusionAura on 2007-10-24
I decided to follow Wobe's suggestion and install Automatrix...but i came up with this error...

[IMG]http://i189.photobucket.com/albums/z68/FusionAura/Screenshot-PackageInstaller-automat.png[/IMG]

---

### Post by sujoy on 2007-10-24
well i am not too sure on the use of automatix........its buggy and i guess we are better off using synaptic and aptitude or download .deb

by the way you can install alien
just type

sudo apt-get install alien

and then you can use rpm packages as well .......

type 

alien --scripts -k <filename.rpm>

this produces a debian package, like something.deb

so install it using 

dpkg -i something.deb

---

### Post by FusionAura on 2007-10-24
If i try that...i get this problem i have tried it with the CD inside, and without the CD inside...

[IMG]http://i189.photobucket.com/albums/z68/FusionAura/Screenshot-izaciZac.png[/IMG]

---

### Post by Maestro23 on 2007-10-24
Just some FYI:

Installing Software In Ubuntu: 
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by sujoy on 2007-10-24
what is th error message that you are getting? 

might sound silly, but did you enable all the repos?

---

### Post by FusionAura on 2007-10-24
> **sujoy said:**
> what is th error message that you are getting? 

might sound silly, but did you enable all the repos?


1) Refer to Picture

2) What is repos?


Edit: I have enabled repos...

---

### Post by Maestro23 on 2007-10-24
> **FusionAura said:**
> If i try that...i get this problem i have tried it with the CD inside, and without the CD inside...

[IMG]http://i189.photobucket.com/albums/z68/FusionAura/Screenshot-izaciZac.png[/IMG]

Check and see if Universe and Multiverse are enabled in your Sources.

System>> Admin>> Software Sources

---

### Post by FusionAura on 2007-10-24
I think a even more serious problem propped up...After i did what you said...i went to type in back the command...i came back with this error message


[IMG]http://i189.photobucket.com/albums/z68/FusionAura/Screenshot-izaciZac-1.png[/IMG]


I followed what was on the screen and came back with this...

[IMG]http://i189.photobucket.com/albums/z68/FusionAura/Screenshot-izaciZac-1-1.png[/IMG]


If i am not wrong, Superuser privellege refers to root access...i was told that logging into root access is actually a big no-no for newbies in Linux...If so...do i try to login? and if i do...how do i login...User=Root Pass=?

---

### Post by sujoy on 2007-10-24
when you need to run anything as root just add "sudo" at the beginning
it would just promt for your password , so enter the password you used to log in.

so type in 

sudo dpkg --configure -a
<enter your password if asked for>

follow the instructions............ 

AND ENABLE ALL THE REOSITORIES for use with aptitude, synaptic,

---

### Post by Richardinel on 2007-10-24
[QUOTE=Qwerty_;3609926]Question 1

To use NTFS drives in Ubuntu you must firstly install some software and set it up.

You can do this by opening a terminal Applications>Accessories>Terminal

And use the following code.

```
sudo apt-get install ntfs-config
```
Once it has downloaded and installed run

```
sudo ntfs-config
``` and select your required settings.

This does not work for me, when done I still cannot "mount the volume" of the USB NTFS HDD

---

