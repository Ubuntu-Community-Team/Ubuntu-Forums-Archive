---
title: "unreal on ubuntu[want to ask]"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-04
can ubuntu run unreal?
can it be mirc server with the unreal?
if yes....can anybody explain how?

---

### Post by _simon_ on 2006-07-04
which version are you asking about?

Unreal Tournament 2004 can be installed natively under linux (there is an installer included on the DVD) you do need 3D enabled graphics drivers though.

---

### Post by Darko8472 on 2006-07-04
I believe he's talking about the Unreal ircd. In which case, it should be able to... I don't see why not. As for how, have a look at the readme that no doubt comes with the ircd package. It'll have an installation section that explains it all.

---

### Post by penguinKabuki on 2006-07-04
how can i install  Unreal ircd?

---

### Post by Darko8472 on 2006-07-04
Download it, extract it from the console using:

tar -xzvf unreal.filename

and have a look at the readme. It'll explain the rest from there.

---

### Post by penguinKabuki on 2006-07-04
ok...when im trying to download it....

its come like this...

========

ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz](http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz)

The following error was encountered:

    * The request or reply is too large.

      If you are making a POST or PUT request, then your request body (the thing you are trying to upload) is too large. If you are making a GET request, then the reply body (what you are trying to download) is too large. These limits have been established by the Internet Service Provider who operates this cache. Please contact them directly if you feel this is an error. 

Your cache administrator is webmaster.
Generated Tue, 04 Jul 2006 14:42:36 GMT by Network-Box (squid/2.5.STABLE11) 

=================

hermm.....how can i solve this type of problems?

---

### Post by Darko8472 on 2006-07-04
That's a problem on their end, not yours. :) Just a matter of waiting til they resolve it, or contact them to let them know.

---

### Post by penguinKabuki on 2006-07-04
can i download unreal with command n the terminal?

---

### Post by Darko8472 on 2006-07-04
Yup.

Change to the directory you want it in, then:

wget [http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz](http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz)

will download it.

---

### Post by penguinKabuki on 2006-07-04
root@root:/home# wget [http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz](http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz)
--11:27:39--  [http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz](http://unrealircd.alert-net.com/Unreal3.2.5.tar.gz)
           => `Unreal3.2.5.tar.gz'
Resolving unrealircd.alert-net.com... 207.58.131.219
Connecting to unrealircd.alert-net.com|207.58.131.219|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
11:27:40 ERROR 403: Forbidden.

ayyooo...
forbidden~

---

### Post by Darko8472 on 2006-07-04
Try one of these alternate download locations:

[http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz](http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz)
[http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz](http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz)

If neither of those work, I'll put it on my personal site and PM you the URL.

---

### Post by penguinKabuki on 2006-07-04
emm....

-------------
penguin@root:~$ wget [http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz](http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz)
--11:36:58--  [http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz](http://www.blurryfox.com/unreal//Unreal3.2.5.tar.gz)
           => `Unreal3.2.5.tar.gz'
Resolving [www.blurryfox.com](www.blurryfox.com)... 82.165.250.112
Connecting to www.blurryfox.com|82.165.250.112|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
11:36:58 ERROR 403: Forbidden.

penguin@root:~$ wget
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
penguin@root:~$ http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz
bash: http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz: No such file or directory
penguin@root:~$ wget http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz
--11:37:52--  http://www.secureirc.org/unrealircd/Unreal3.2.5.tar.gz
           => `Unreal3.2.5.tar.gz'
Resolving www.secureirc.org... 65.110.52.160
Connecting to www.secureirc.org|65.110.52.160|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
11:37:52 ERROR 403: Forbidden.

----------------------

cannot also...
i think....if i can use rootshell....it will work right?
how can i connect to rootshell.be in the terminal?

---

### Post by Darko8472 on 2006-07-04
Hmmm, this is starting to sound like a problem from your end afterall. I can access all those fine, even through work's firewall (where I am at the moment). I'm not so technically minded with Ubuntu yet, anyone else got any ideas?

---

### Post by penguinKabuki on 2006-07-04
if only i can bypass this demm firewall..
erm...ubuntu allow the user to use your freedom?
or....i odnt know....im blur~~

---

### Post by penguinKabuki on 2006-07-04
so i find the solution...
the solution is.....i ask my friend to donlod it from his place...and send it to me thorugh email...now i have the installer...thx~~

---

### Post by Fingolfin on 2006-07-19
Unreal Tournament 2004 can be installed natively under linux (there is an installer included on the DVD) you do need 3D enabled graphics drivers though.[/QUOTE]

I have just been looking on Amazon.com to buy UT 2004 DVD but all the product info suggested the available versions were only for MS Windows and Mac.
Is the installer you mentioned here included on the DVD edition of UT 2004 for Mac OS-X maybe?

---

### Post by pbaehr on 2006-07-19
I have the Unreal Tournament 2004 DVD (Editor's Choice Edition) for Windows. It has a Linux installer on it as well.

---

### Post by Fingolfin on 2006-07-20
Thank you, your reply was most helpful :-)

---

### Post by A2A on 2006-07-20
Hi Penguin,
I was going to recommend you upload the file via FTP (WSFTP Pro is a nice win32 based client that supports SSH connections via port 22).  But since you already managed to get the source you should be fine.
A couple things to point out though:  
If you're running the IRCd off your home connection (cable/DSL) watch out for the BW.  It's a hog on BW depending on your userload and if you run services as well.  It could also show some lag on your servers performance depending on your CPU/RAM.
Secondly, if it's a home line, you're vulnerable to DDoS attacks, which could knock you offline for a bit, and result in your ISP issuing you a warning.
If you need any help configuring it, etc, let me know.

Cheers!

---

