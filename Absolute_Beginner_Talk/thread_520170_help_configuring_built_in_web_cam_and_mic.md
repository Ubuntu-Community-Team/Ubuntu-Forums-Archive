---
title: "help configuring built in web cam and mic"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-08-07
help me out here plz

I have just installed Ubuntu 7.04 on my hp pavilion dv6000 series laptop and I want to know how to configure the web cam, and if you could help me out installing the built in microphones 

thanks

---

### Post by Rul on 2007-08-08
I had problems with my webcam with ubuntu 6.10 that were solved installing the v4l2 driver, however when I installed ubuntu 7.04 this driver was installed by default. On which programs are you trying to use your webcam? 

Also in ubuntu 7.04 I obtained support for my built-in mic, but normally alsa mixer's default value for capture is 0/100 so you may need to adjust this

---

### Post by skidkid87 on 2007-08-13
I wanna use my web cam normally like for example video chat and taking pictures

and no I turned mic volume gain to 100% and it still didn't capture anything

---

### Post by amireldor on 2007-08-14
I got a dv6282ea laptop and managed to get half-way in the process of making it all work.

For webcam - I installed a v4l2 driver that i had found somewhere on the web (nothing like that was installed on my feisty). With this I could capture video on ekiga softphone and I was very happy but, I haven't found any still-image or webcam capture application that knows to talk with v4l2 drivers (any help here?)
link to driver [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

As for the mic, Nothing work until I searched these forums like hell and realized that HP's (at least these dv stuff) got some Intel HDA thing. After I added a strange command that does *something* to some alsa configuration file, It started capturing audio from the mic (after reboot) but it still captures it very bad. Under skype i sound as if i'm in a german submarine in world war 2.
i can't find the original link, but maybe this will help (will also try it myself) [http://ubuntuforums.org/showthread.php?t=314383&highlight=hda+hp+intel](http://ubuntuforums.org/showthread.php?t=314383&highlight=hda+hp+intel)
YAY microphone now working very good with skype after i did this  to the end of /etc/modprobe.d/alsa-base
```

>>> tail /etc/modprobe.d/alsa-base 
# trying option for microphone
## this worked submarine style
##options snd-hda-intel model=ref
options snd-hda-intel model=hp

```

maybe check out this also [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

---

### Post by skidkid87 on 2007-08-14
ok I got the webcam driver but I don't know how to install it, I used the ./configure command in the terminal at while at the extracted folder and it didn't work and I have the essentials package, I'm currently confused :confused:

and I have no idea what I have to do to get the mic working, but there's something wierd it seems to work on skype and not in the voice recorder I don't know why :confused:

forgive my ignorance but I'm new here.

---

### Post by manco1911 on 2008-06-29
try doing "sudo ./config"  
 what do you mean you "HAVE" the webcam drivers?

please post a link or a name, share. 


still trying to make the webcam and mic work on ubuntu 8.04

---

### Post by starcannon on 2008-06-29
The website that lousygarua referred to is offline, but I found an archive of it in the wayback machine, [http://web.archive.org/web/20070810221634/http://lsb.blogdns.net/ry5u870/](http://web.archive.org/web/20070810221634/http://lsb.blogdns.net/ry5u870/)

I'm having an HP webcam issue as well but mines the Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd one, if anyone knows how to get this camera working correctly please shoot me a PM and we can start a separate thread (I don't wanna hijack this one)

GL and hope that wayback link works for you.

---

### Post by sanjrockz on 2008-07-07
I'm a newbie running Ubuntu 8.04 in my HP Pavilion dv6745. I had the same problem but I was able to fix it. I found this topic is discussed [here]("http://ubuntuforums.org/archive/index.php/t-789245.html") and it redirects you to another page that describes how to configure the inbuilt mic on a think pad. I followed the same steps and was able to configure my front mic (inbuilt) to capture a sound using sound recorder but it didn't work for skype straight. I then configured skype using 
skype > options > sound devices and setting up sound in box for HDA Intel (hw:intel,0) where it was previously default device (default). That worked for me and hope it will work for urs as well.

Thankx

---

