---
title: "file sharing???"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-01-26
OK I have never tried this before.  So if I am asking dumb questions, sorry.  I was wanting to set up a way for my girlfriend to be able to pull files from my computer.  She is halfway across the US.  I wanted her to be able to dial into my IP address and be abe to take what she wants from some select folders.  How do I do that?

---

### Post by NapsterX on 2008-01-26
hmm i think your best bet might be a web server not really to sure tho
I have the kind up setup that you are asking about runing at home but it's all done threw a lan connection so to share with freinds over the web i just got myself a server up and running and it was all pretty simple to do

---

### Post by scxtt on 2008-01-26
what interface is she most comfortable with?

web?
(s)ftp?

both should be easy to accomplish ... what kinda files are you going to be sharing?

---

### Post by nynoah on 2008-01-26
mainly music and pictures with her.  Its too hard to send stuff back and forth.  She is out on the east coast for work for 6 months.  I thought it would be a good way to share between us.

SO what is the best way to do something like this?

---

### Post by taurus on 2008-01-26
Are you on a dial-up or DSL?

---

### Post by NapsterX on 2008-01-26
it's your personal choice between an ftp and web server they both do good but it's going to come down to which one is easier for the both of you

---

### Post by kamasabi on 2008-01-26
the way I personally do stuff like that is just use samba and hamachi (quick and easy to set up vpn).  Only problem with the hamachi linux version is that it does not support relaying and a couple of other features YET, however, that will come in due time :).

---

### Post by nynoah on 2008-01-26
I am on cable  so my speed is decent
 
its not a T1 ( I wish.........)

---

### Post by nynoah on 2008-01-26
and of all those options you all were talking about.  what is the easiest for me.  This is my first time with something like this.  I am a decent ubuntu user.  But this will be a learning experience.

Noah

---

### Post by taurus on 2008-01-26
Personally, I would install vsftpd (from synaptic or with apt-get).  Then, open port 21 on your router if you have a router for incoming traffic.  Then, create and account for her so she can just ftp to your machine anytime she wants and she can download/upload whatever she wants.

---

### Post by NapsterX on 2008-01-26
my opion is ftp is the way to go, thats what i use and it was pretty easy to setup

---

### Post by nynoah on 2008-01-26
Ok I will check that out.........any other suggestions from others?

Thanks you all so much for helping me

---

### Post by NapsterX on 2008-01-26
here's where i started
[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by nynoah on 2008-01-26
How do I set up   vsftpd  does it have a gui?

---

### Post by nynoah on 2008-01-26
OK I have proftp coming down from synaptic now.   Thanks so much

---

### Post by taurus on 2008-01-26
If you want a nice little GUI screen to configure it, then perhaps proftpd and gproftpd is what you need.  As for vsftpd, you just need to edit /etc/vsftpd.conf if you want to turn off the anonymous login.

---

### Post by nynoah on 2008-01-26
I guess I am lame.........but I like GUIs better.

---

### Post by taurus on 2008-01-26
Then don't forget to install gproftpd if you install proftpd.

---

### Post by nynoah on 2008-01-26
got it installed now.  But where is it to configure it?

---

### Post by nynoah on 2008-01-26
OK got it open but how do I configure Gproftpd?  Is there an online tutorial for this program?

I have searched but have not found one yet

---

### Post by taurus on 2008-01-26
Here's the grand-daddy of them all.

[http://www.proftpd.org/](http://www.proftpd.org/)

---

### Post by nynoah on 2008-01-26
Thanks  Taurus........I will go through that.......god where do I start....ha ha

another question.  will I run into a problem with her using a windows computer.  issues such as NTFS and Ext3

---

