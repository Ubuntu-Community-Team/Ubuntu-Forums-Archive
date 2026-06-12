---
title: "Screen resolution issues"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-07-19
Hello there 

I am new to this Lunx , so bear with me here.

I have a fujitsu life book which I think runs the 815 chipset ( intel?)

The problem is the display ..there is a whooping big line down the middle of the screen , and I can see only 1/2 the screen in a very large resolution 640 x 480 at 60 hz

I tried sudo dpkg-reconfigure xserver-org

but it say command not found 

I tried to install 915 but the reposittories in settings say I need an internet connection 

I cant see the screen to set that up 


Need VERY simple clear instructions on how to fix this problem 

Kind regards 

Stephen Watson

---

### Post by Perfect Storm on 2006-07-19
> I tried sudo dpkg-reconfigure xserver-org

I don't know if it's a spelling error.


```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
(change gdm with kdm if you are using kubuntu)


also remember that linux is case sensitive.

If it doesn't work, please post your xorg.conf:
```
nano /etc/X11/xorg.conf
```

---

### Post by basilwatson on 2006-07-19
ok will do , When I type these commands I can oly see upto the g in reconfigure  as the screen is real weird 

will post back in a few min with results 

Btw I am typing all this in terminal , hope that is the place to type !!!

Stephen

---

### Post by basilwatson on 2006-07-19
worked a treat great stuff, now all I have to do is get the mp3 working and I am set!!! 
happy camper here !!!:) :D :D :D :D :D 

Stephen

---

### Post by richbarna on 2006-07-19
You need to read about "[restricted formats]("https://help.ubuntu.com/community/RestrictedFormats")" basically mp3 etc don't come as standard with Ubuntu, but the codecs are easy enough to install. ;)

You could also check out Automatix in my sig:
|
|
v

---

### Post by Perfect Storm on 2006-07-19
my pleasure ^^

Is it a mp3 player or just playing mp3 files on ubuntu?

---

### Post by basilwatson on 2006-07-19
Just downloading the codecs  mp3 mpeg mpeg4 

I assume to read restricted formats then download the codecs , use terminal to install as in sudo apt-get install xyz

if they are compressed in a tarball which directory  if any do they get put in ??

Stephen

---

### Post by Perfect Storm on 2006-07-19
Easist is to save it to your Desktop and unpack it there. You have to check what it contains first, before we can give a concreate answer to your question.

---

### Post by basilwatson on 2006-07-19
:(  ok sorry bout this , have read  restriced formats  downlowed automatix 

cant install anything 

the automatix is a .deb file so is the win32 codec

 I tried  sudo apt-get install automatix    and all i get is cant find package automatix

is there anything I am missing ?? 

How do I do this ???](*,) 

I made a folder called codecs and extracted everything I could into that , then inthe terminal windo tried  sudo/apts-get/install/desktop/codecs/gst-plugins-ugly-0.9.1

and as may combination as I can think off 

Please where am I going wrong 

Kind regards Stephen ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Perfect Storm on 2006-07-19
How's your sourcelist looks like?

```
sudo nano /etc/apt/sources.list
```

---

### Post by basilwatson on 2006-07-19
Sorry I completly stuffed everything up, , I tried this and that , found  easy ubuntu , installed that , mp3 worked  but movies didnt so I ran easy ubuntu zaand stuff up the resolution again , tried what you suggested  before this time it didnt work , so am re installing everything 

all I want is to play  me music ](*,) ](*,) 

Thanks for your kind support 

7 hours I have been trying to get this thing to work !

Stephen 

I will look at sources when its  back to being normal again

---

### Post by Perfect Storm on 2006-07-19
When you have reinstalled ubuntu and sset the res again take a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by basilwatson on 2006-07-19
yes I read that and have downloaded all the required files ,  win32 codecs I am not sure about , I could find them and when I did m the file has .deb.part on the end 

they were sitting on the ubuntu desktop ,  ( I am using another machine connected to the internet , not the machine I am trying to set ubuntu  up on )  I opened them up then doulle clicked on compile , or anything that looked like it was going to open 

Sorry but there is no clear way of getting the info ,   I have booked marked , and read anything that even looked like it was going to help !!!!:-D 

Ill get it back to where I had it , try again to install codecs and if I cant , I ll think about it ](*,) 

once again , your support has been fantastic 


Kind regards Stephen

---

### Post by Perfect Storm on 2006-07-19
```
cd Desktop
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

```

Should do it. On Dapper you can double-click .deb packages instead.

---

