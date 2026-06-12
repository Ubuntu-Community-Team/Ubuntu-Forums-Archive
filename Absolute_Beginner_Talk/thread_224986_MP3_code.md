---
title: "MP3 code"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-28
can anyone give me the sudu coode to type into terminal to get MP3 Codecs

---

### Post by ovimunt on 2006-07-28
Check this out:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Captain Kirk76 on 2006-07-28
Okay i asked for the code, not a link to a manual.

And besides when i type gstreamer0.10-plugins-ugly into the terminal, it dooesnt do ought

---

### Post by mattisking on 2006-07-28
Assuming you are running Dapper and have Universe repositories enabled and are using Banshee or Rhythmbox:
sudo apt-get install gstreamer0.10-fluendo-mp3

---

### Post by Captain Kirk76 on 2006-07-28
I get this error

Building dependency tree... Done
E: Couldn't find package gstreamer0.10-fluendo-mp3

---

### Post by mattisking on 2006-07-28
> **Captain Kirk76 said:**
> Okay i asked for the code, not a link to a manual.

And besides when i type gstreamer0.10-plugins-ugly into the terminal, it dooesnt do ought
That link is the link to use. It will also help you get DVD's playing and support for lots of other formats. It's very likely you simply need to enable universe repositories. If you installed Dapper recently, if you:
sudo gedit /etc/apt/sources.list

and then remove the # before the lines talking about universe at the end, save, exit gedit, sudo apt-get update, sudo apt-get dist-upgrade, and then follow the instructions you should be good.

---

### Post by Captain Kirk76 on 2006-07-28
Well that went over my head.....

Er...basic dummy talk please :)

---

### Post by T700 on 2006-07-28
> **Captain Kirk76 said:**
> Well that went over my head.....

Er...basic dummy talk please :)

If you'd rather not understand the process, click on the Automatix link in my sig and follow the instructions there.  It will take care of the codecs, as well as some other things that you will likely need.  Please do read the instructions.  Automatix is simple and safe--when taken as directed.

Paul

---

### Post by Captain Kirk76 on 2006-07-28
Now get this error

E: Type &#8216;Uncomment&#8217; is not known on line 10 in source list /etc/apt/sources.listE: The list of sources could not be read.

---

### Post by Qrk on 2006-07-28
You may find these links usefull when trying to figure out Ubuntu...
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Also System->Help->System Documentation->Desktop Guide is a great tool.

---

### Post by Captain Kirk76 on 2006-07-28
> **T700 said:**
> If you'd rather not understand the process, click on the Automatix link in my sig and follow the instructions there.  It will take care of the codecs, as well as some other things that you will likely need.  Please do read the instructions.  Automatix is simple and safe--when taken as directed.
Paul

Id rather not do that, i am famous for cocking up windows from not understanding things, and Linux seems even worse....

---

### Post by T700 on 2006-07-28
> **Captain Kirk76 said:**
> Id rather not do that, i am famous for cocking up windows from not understanding things, and Linux seems even worse....

This may seem harsh, but to my eye you have three choices:

1.  Take the time to learn how do these things on your own.  You do not need "dummy talk," as these are simple processes that any literate adult should be able to complete.

2.  Use something like Automatix or Easy Ubuntu to do the work for you.

3.  Pay someone to do the work for you.

Your choice.

Paul

---

### Post by Captain Kirk76 on 2006-07-28
I cannot believe i have to learn something just too use a friggin operating system.

---

### Post by T700 on 2006-07-28
> **Captain Kirk76 said:**
> I cannot believe i have to learn something just too use a friggin operating system.

Do you have a driver's license?  If so, were you upset that you had to learn something "just to use a friggin" car?  Does it bother you that you had to learn how to read to "just to use a friggin" book?

This may not be the operating system for you.  

Paul

---

### Post by Captain Kirk76 on 2006-07-28
I do not have a driving license, nor do i intend to pollute by getting one.

---

### Post by Captain Kirk76 on 2006-07-28
Now, does anyone know a simple way of getting these extra repositries.

---

### Post by nalmeth on 2006-07-28
From first page of a google search: "enable extra repositories ubuntu"
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
This is a great site, you'll figure it out from here
[ ]("http://www.psychocats.net/linux/sources.php")

---

### Post by Captain Kirk76 on 2006-07-28
thankyou nalmeth, i have it workin now

---

### Post by mattisking on 2006-07-28
Well, I took the time to make it on my way out the door. Too late, but since I made it, here it is. I'll take it back down tomorrow:

[http://www.mattisking.com/explain.gif]("http://www.mattisking.com/explain.gif")

---

### Post by Captain Kirk76 on 2006-07-28
Thanks for that mattisking, it is appreciated ;)

---

