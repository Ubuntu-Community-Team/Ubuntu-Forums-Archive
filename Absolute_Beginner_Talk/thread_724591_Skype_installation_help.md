---
title: "Skype installation help"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by bigggnick on 2008-03-14
Hey all,

So I was extatic when I first saw that Skype was going to be avalable for linux. I use skype a lot, mostly for video chats. But, Skypes website says its avalable for 7.10+. I have 6.06. I tried downloading it anyway, hoping it might work. It keeps giving me this error:
Error: Dependancy tree is not satisfiable: libasound2

Can I some how make libasound2 satisfiable? Is it even possible to get Skype on 6.06 or do I need to upgrade?  Is there some other program that I could use to video chat (preferably compatable with AIM and Skype)?

Thanks for your help,

Nick

---

### Post by taurus on 2008-03-14
Maybe this would help.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by crjackson on 2008-03-14
> **bigggnick said:**
> Hey all,

So I was extatic when I first saw that Skype was going to be avalable for linux. I use skype a lot, mostly for video chats. But, Skypes website says its avalable for 7.10+. I have 6.06. I tried downloading it anyway, hoping it might work. It keeps giving me this error:
Error: Dependancy tree is not satisfiable: libasound2

Can I some how make libasound2 satisfiable? Is it even possible to get Skype on 6.06 or do I need to upgrade?  Is there some other program that I could use to video chat (preferably compatable with AIM and Skype)?

Thanks for your help,

Nick

This is for 6.04.  I think it may work on 6.06

```
sudo apt-get install libsigc++-2.0-0c2a libdbus-1-2
wget http://www.skype.com/go/getskype-linux-static
tar -xvjf skype_static*.tar.bz2
cd skype_static*
sudo mv skype /usr/bin/
sudo mkdir /usr/share/skype
sudo mv sounds /usr/share/skype/
sudo mv icons /usr/share/skype/
sudo mv skype.desktop /usr/share/applications/
cd ..
sudo rm -rf skype_static*
```

---

### Post by ajgreeny on 2008-03-14
> This is for 6.04.  I think it may work on 6.-6
There was no 6.04, so I don't know what this means, but anyway go for the medibuntu repos and install it in the usual manner.

---

### Post by crjackson on 2008-03-14
> **ajgreeny said:**
> There was no 6.04, so I don't know what this means, but anyway go for the medibuntu repos and install it in the usual manner.

I'm sorry you don't know what it means.  Try google or wiki.  There was a 6.04
[http://philbull.livejournal.com/8994.html](http://philbull.livejournal.com/8994.html)
[http://librenix.com/?inode=5421](http://librenix.com/?inode=5421)
[http://www.tuxmachines.org/node/3502](http://www.tuxmachines.org/node/3502)
[http://www.tatanka.com.br/ies4linux/news/11](http://www.tatanka.com.br/ies4linux/news/11)
[http://kerneltrap.org/node/6050](http://kerneltrap.org/node/6050)
[http://linuxrevolution.blogspot.com/2006/03/ubuntu-604-dapper-drake-preview-part-i.html](http://linuxrevolution.blogspot.com/2006/03/ubuntu-604-dapper-drake-preview-part-i.html)
[http://www.niraj.info/node/5](http://www.niraj.info/node/5)
[http://www.braggtown.com/qubuntu.html](http://www.braggtown.com/qubuntu.html)

---

### Post by Sef on 2008-03-14
> I'm sorry you don't know what it means. Try google or wiki. There was a 6.04

There was not a Dapper Drake 6.04.  Dapper Drake was supposed to be released in April 06; however, it was delayed to June 06. (Hence 6.06, and not 6.04.)   Articles released before the announcement of the delay will say 6.04.

---

### Post by crjackson on 2008-03-14
> **Sef said:**
> There was not a Dapper Drake 6.04.  Dapper Drake was supposed to be released in April 06; however, it was delayed to June 06. (Hence 6.06, and not 6.04.)   Articles released before the announcement of the delay will say 6.04.

Very well, I stand corrected.  However the original question was about the new Skype for 6.06.  I found and posted code that was listed for 6.04 and thought it MAY be helpful.  I wasn't starting a debate about 6.04 vs 6.06.  The other poster said he didn't know what I was talking about.  Since there are many screen shots of 6.04 (released to public or not), one can see that the build must have existed at some point.  But as you have pointed out it didn't, so never mind.

To the original poster, please disregard my 1st post.  I was trying to help but it turns out I made it all up...

---

### Post by bigggnick on 2008-03-14
Thank you all for you help. I got Skype successfully installed and am quite please. HOWEVER, somehow my updater got messed up. I took a screen shot:
[http://img210.imageshack.us/img210/5889/screenshot2ug6.png]("http://img210.imageshack.us/img210/5889/screenshot2ug6.png")

So... ya... why?

---

### Post by taurus on 2008-03-14
You need to shutdown the Software Update first before you can run apt-get from a terminal.

---

### Post by bigggnick on 2008-03-14
Ahh ok, thanks again. Still getting used to this :)

---

