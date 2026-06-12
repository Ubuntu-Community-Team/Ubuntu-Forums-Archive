---
title: "download ubuntu thru ftp ....."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by soultang on 2007-03-20
Im on a mac and want to run ubuntu in parallels ... to try out. How can I download ubuntu thru ftp so if it stops i can resume it instead of starting the download all over again? Is there a ftp sight i can get it from ... the iso i mean.

---

### Post by Kamu on 2007-03-20
You can get the complete list of mirrors at:
[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)

Any mirror, like the one listed in Europe/Belgium/Ftp.easynet.be, which has a name that starts with Ftp is an ftp mirror.  Don't forget to try to get a mirror as geographically close as possible to try to get the best download speed.

---

### Post by steve.horsley on 2007-03-20
I use a program called **wget** which can resume downloads after interruption - it seems pretty bomb-proof to me. It can get from FTP and HTTP servers. Since there are versions for Linux, Solaris, BSD and Windows, I guess there is a Mac version too.

---

### Post by Miguellint on 2007-03-20
> **steve.horsley said:**
> I use a program called **wget** which can resume downloads after interruption - it seems pretty bomb-proof to me.

Slightly OT sorry:

Hello Steve....I'm using wget at the moment but whenever the download is interrupted, which is pretty often cos I've got a cr*p internet connection, there's no automatic resumption of download once the connection is remade. After ten minutes or so of inactivity I have to manually re-start wget.

 Are you using any special command options when you run wget or is it just $wget URL

Thanks
Miguel

---

### Post by zvacet on 2007-03-21
Why don´t you download it with torrent?

---

### Post by dptxp on 2007-03-21
Download Bittorrent. Click on corresponding torrent file.

---

### Post by steve.horsley on 2007-03-21
I don't use any special options - just **wget url**. It seems to retry after 20 minutes or so normally. Don't interrupt it. Just leave trying it overnight.

It is possible for it to give up eventually, but that's raren and it clearly says it's given up. In this case, you can do **wget -c url** and it will continue where it left off.

---

### Post by Miguellint on 2007-03-21
> **zvacet said:**
> Why don´t you download it with torrent?

I was looking at it more as an exercise in using wget than in actually downloading something (if that makes sense).

I'm wget'ing a SuSE DVD iso, which I may one day use. I could quite easily torrent it but I decided to use wget and learn a few new things.

As Steve says in his reply to my post (and I noticed after a day or so) it tends to take 20 minutes or so for wget to remake the connection. A big nuisance, cos if I manually restart wget  the download resumes straightaway. 

Thanks all for replying :-)

Regards
Miguel

---

### Post by haroldatterbury on 2007-03-21
I downloaded my copy from ftp.ale.org it worked pretty well.

---

### Post by steve.horsley on 2007-03-22
> A big nuisance, cos if I manually restart wget the download resumes straightaway. 
There are options to change the timeouts and  retry time etc. Use **man wget** to see the gory details. On reading that, I see that the the default timeout is 15 mins, not 20. 

**wget -T 120 url **
might suit impatient people.

---

