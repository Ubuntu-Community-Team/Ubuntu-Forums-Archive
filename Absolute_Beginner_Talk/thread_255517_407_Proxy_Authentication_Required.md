---
title: "407 Proxy Authentication Required"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by cocotu on 2006-09-11
This is the error that I get when I try to do: apt-get install build-essential or try to install anything using apt-get.

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1
407 Proxy Authentication Required ( The 
> ISA Server requires authorization to fulfill the request. Access to the 
> Web Proxy service is denied. )

---

### Post by Najand on 2006-09-11
Are you behind a proxy?

---

### Post by cocotu on 2006-09-11
Yes Najand, I'm at work right now. We installed a LAMP server and I needed to get the compilers so we can do ./configure. How can I configure the proxy? I don't have any GUI only the terminal.  
Thanks

---

### Post by Najand on 2006-09-11
try to edit /etc/apt/apt.conf (If there is no file available make new file)
Add the following lines to the file

```

Acquire::http::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";
Acquire::ftp::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";

```

---

### Post by cocotu on 2006-09-11
Thanks, I have to go, we are closing now. Can we keep in contact? I'll be here at 9AM New York time

---

### Post by cocotu on 2006-09-12
Ok Najand, now after doing those changes I get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1
  Could no resolve 'RGuisbert@10.0.3.4'

Does this means I have entered the wrong user name/password or something else?

Thanks....

---

### Post by Najand on 2006-09-12
Hmm, check the proxy address with your system administration.
About "RGuisbert@10.0.3.4": Most of the time proxy servers does not need a username and password, so just enter address and port. The port must be something like 80 or 8080 or something similar. Reply me when you checked these up.

---

### Post by cocotu on 2006-09-13
Najand I believe I got pass the Proxy without using username:pass. For some reason its asking me to insert the CD, I thought I was going to get the packages from the Internet. What should I do?

---

### Post by Najand on 2006-09-13
Hmm, maybe the packages you need is also available on the cd too. So, If youi have the cd, insert it inside your CD-ROM, if not, try to edit:
```

sudo vim /etc/apt/sources.list

```
And comment(put a "#" sign before) the UBUNTU CD-ROM line.

---

### Post by cocotu on 2006-09-13
What should I change in the sources.list?

---

### Post by Najand on 2006-09-13
In sources.list, just put a "#" sign before the line starts with "deb cdrom" and save it.
Then run:
```

sudo apt-get update

```

---

### Post by cocotu on 2006-09-13
Najand, I'M GOING CRAZY!! Now I get this error:

Failed to fefch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  407 Proxy Authentication Required  ( The ISA Server requires authorization to fulfill the request.  Access to the Web Proxy service is denied.)

Also I tried to include a username/password for the Proxy server (the one we use for the windows machines) and I get same message as above, but at the end I get: 

Could not resolve 'password@10.0.3.1'

I though I fix this, but I was asked to insert the CD.

Thanks...

---

### Post by Najand on 2006-09-13
Hmm, if you have entered the right proxy address and proxy port, it must work fine... Can you check the proxy address with another computer at your office... You  can find it in Mozilla Firefox (Edit > Prefrences) or Internet Explorer (Tools > Options). And check your /etc/apt/apt.conf
file to see if its format matches with:
> Acquire::http::Proxy "http://xxx.xxx.xxx.xxx:yyyy";
which [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx) is your proxy address and yyyy is your port address.
Also, if you are using https proxy, check if you have not forgotten "s".

---

### Post by cocotu on 2006-09-14
Every time I do changes in apt.conf do I have to do this??

```
export http_proxy=user:pass@server:port
```

---

### Post by Najand on 2006-09-14
Well, apt does not use the proxy you use as environment proxy. when you set the proxy address in apt.conf,  there is no need to change your environment proxy. There is a manual page for apt.conf; use it for reference:
```

man apt.conf

```
I checked it again, to proxy format should be something like:
"http://[[user][:pass]@]host[:port]/"

I am also behind proxy, I usually use textbase terminal too and it works just fine for me... I am so sorry I couldn't help you fix the problem.

---

### Post by cocotu on 2006-09-14
"http://[[user][***]@]host[ort]/"
Do I need the "[]"?
Now that I found the CD I get: Failed to fetch cdrom, please use apt-cdrom to make this CD-ROM recognized by APT.  When I do that I get: Failed to mount the cdrom. I am almost giving up!!

Thanks for your help Najand!!

---

### Post by Najand on 2006-09-14
Hmm, go back to sources.list, remove the "#" you editted before "deb cdrom: ...." and let apt-get install.

---

### Post by Najand on 2006-09-14
[...] means optional....

---

### Post by cocotu on 2006-09-14
Ok Najand this is my sources.list: (I think it should be fine)

# 
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


 deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Najand on 2006-09-14
It seems fine to me too. "#" means comment, so if you remove "#" from the begining of lines with deb, deb-src, deb cdrom you would have more repositories to use, including sources repositories, an example is like:
> 

deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by cocotu on 2006-09-14
I'm still getting  Failed to fetch cdrom, please use apt-cdrom to make this CD-ROM recognized by APT. When I do that I get: Failed to mount the cdrom.

---

### Post by Najand on 2006-09-14
Try putting CD-ROM in the drive.
Run:
```

sudo umount -a

```
and then run:
```

sudo apt-cdrom add

```
When it prompts put CDROM in the drive, do that and continue.

---

