---
title: "Why are changes in Ubuntu Sooooo difficult  ???????????"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-04-30
I was trying to connect to a Live Web Cam in Canada (streaming video) and could not.
I login into my Windows OS and gee it worked great and was able to watch a Mother Bald Eagle sitting on her nest of two eggs.

So I looked on the Form and found I needed to change a variable in Mplayer .config (vo)
so I changed the vo=x11  to  vo=xv then rebooted and Mplayer would not show the Eagle nest.

I also noticed that now I can no longer run old  movie files with Mplayer  that worked before the change. ](*,) 

So I edited the mplayer config file to the original vo=x11 and Mplayer still won't run my old movie file that use to work. 
It look like Ubuntu applications are like when you take you car in the garage to get 1 thing fixed the car comes out of the garage with 3 new problems, Why is this the case ? I gave up on trying to get Firestarter not to ask for a password and after a few weeks it went away by itself.

I am trying very hard to stay  and use Ubuntu but it is so difficult to make simple things work.  I have had problems in the past so I have not made any changes for one month.  All I now use Ubuntu for is going on the net but it looks like that is not usable either.  I used Synaptic Manager to reinstall Mplayer but I still am unable to run my old video file that I could run 1 hour ago, WHY.

If anyone has any suggestions on how to get Mplayer to work I would appreciate it. Thanks for any help.](*,)

---

### Post by halitech on 2006-04-30
don't have any fast answers for you as I'm new to ubuntu myself but if you could post the link it may help someone else help you better so we know whats going on (that and I wouldn't mind seeing the eagles myself ;) )

---

### Post by aysiu on 2006-04-30
I've never heard of having to edit some MPlayer config file to see streaming videos. Where did you read that?

In any case, if you like stuff done for you, try [Automatix](http://www.ubuntuforums.org/showthread.php?t=138405).

---

### Post by kent41 on 2006-04-30
[QUOTE=aysiu]I've never heard of having to edit some MPlayer config file to see streaming videos. Where did you read that?

In any case, if you like stuff done for you, try [Automatix](http://www.ubuntuforums.org/showthread.php?t=138405).[/QUOTE]

This is what I found it was posted 15 hr ago.
And as to Automatix I tried several times but could not get it to download and e@!x  LOL

Try using this procedure:

    * Find this line 

...
vo=x11,         # To specify default video driver (see -vo help for
...

    * Replace with the following line 

vo=xv,         # To specify default video driver (see -vo help for

    * Save the edited file

---

### Post by aysiu on 2006-04-30
[QUOTE=kent41]This is what I found it was posted 15 hr ago.
And as to Automatix I tried several times but could not get it to download and .


Try using this procedure:
[http://easylinux.info/wiki/Ubuntu#Ho...ozilla_Firefox](http://easylinux.info/wiki/Ubuntu#Ho...ozilla_Firefox)[/QUOTE] Well, I have the MPlayer plugin, and I've never edited that file, and I haven't had any problems. Then again, I've never had trouble downloading Automatix, either.

I think you should probably see why you can't download Automatix. What happens when you try to download it?

You may also want to consider trying another distro. Ubuntu doesn't come with any proprietary multimedia codecs and such. PCLinuxOS and Mepis do, however. If everything seems "Sooooo difficult," you may need a Linux distro that has more of that stuff set up for you out-of-the-box.

---

### Post by kent41 on 2006-04-30
[QUOTE=aysiu]Well, I have the MPlayer plugin, and I've never edited that file, and I haven't had any problems. Then again, I've never had trouble downloading Automatix, either.

I think you should probably see why you can't download Automatix. What happens when you try to download it?

You may also want to consider trying another distro. Ubuntu doesn't come with any proprietary multimedia codecs and such. PCLinuxOS and Mepis do, however. If everything seems "Sooooo difficult," you may need a Linux distro that has more of that stuff set up for you out-of-the-box.[/QUOTE]

The URL posted did not go to the correct place. so i listed the code.
as to Automatix I had problems with the the server or where ever it is located.
Part of the code would be downloaded then the host would not connect.
Just a little history i have been working in computers since 1969 and had systems I was responsible for including Unix, Dec, IBM and wrote applications in Fortran, C++, Assembler, Cobal, etc and never had the frustrations i have seen with this OS.

---

### Post by aysiu on 2006-04-30
For the record, I have five years' experience teaching English to high school students. I now work in an admissions office. I've been using Linux for one year and Ubuntu for almost one year.

And I've never experienced the problems you're having with Ubuntu. I don't think they're very common either. There may have been a few days when the server for downloading Automatix was down, but other than that people have had no problems downloading it. And I've never heard of this editing the MPlayer config file or that causing any problems.

I'm not trying to say you *aren't* experiencing these problems--you obviously are, but I don't think this is the typical Ubuntu experience. Nevertheless, for whatever reasons, Ubuntu isn't working for you. If you're still interested in desktop Linux, once again, I'd encourage you to take a peek at PCLinuxOS or Mepis.

---

### Post by kent41 on 2006-04-30
Ok now we have said what we wanted to say how do i get Mplayer to work?
As I said , I would like to use Mplayer in Ubuntu. At this point I don't think i want to quit , I want to get Mplayer to work.

---

### Post by aysiu on 2006-04-30
[QUOTE=kent41]Ok now we have said what we wanted to say how do i get Mplayer to work?
As I said , I would like to use Mplayer in Ubuntu. At this point I don't think i want to quit , I want to get Mplayer to work.[/QUOTE] Unfortunately, I don't know.

I basically just installed MPlayer via apt-get, and it worked for me.
I know if you need certain codecs, Automatix will install it for you.
Having never heard of this problem, I don't even know where to point you to fix it...

---

### Post by SavageBeginner on 2006-04-30
If you can't get Automatix to work, here's a howto for installing the codecs:  [https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba)

---

### Post by aktiwers on 2006-04-30
When I ran this script, I have never had any problems with any formats at all.
[http://ubuntuforums.org/showthread.php?t=157589](http://ubuntuforums.org/showthread.php?t=157589)

I know Patrick made another post, with some updates, but I cant find it, and this one works great for me! :)

---

### Post by kent41 on 2006-04-30
[QUOTE=SavageBeginner]If you can't get Automatix to work, here's a howto for installing the codecs:  [https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba)[/QUOTE]

Thanks for the suggestion but when I try to execute the code
```

wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
```

The ftp starts but stops at  **PASV** line




 wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
--13:34:24--  [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
           => `w32codecs_20050412-0.0_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat/pool/main/w/w32codecs ... done.
==> PASV ... 


any suggestions ?

---

### Post by aysiu on 2006-04-30
That's odd. That *same* command gives me this: ```
 wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
--11:43:48--  ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
           => `w32codecs_20050412-0.0_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat/pool/main/w/w32codecs ... done.
==> PASV ... done.    ==> RETR w32codecs_20050412-0.0_i386.deb ... done.

    [                <=>                  ] 13,228,654   145.54K/s

11:45:25 (136.49 KB/s) - `w32codecs_20050412-0.0_i386.deb' saved [13228654]
``` You also mentioned you were unable to download Automatix? Maybe there's some kind of internet connection problem...?

---

### Post by nalmeth on 2006-04-30
easy ubuntu is another option.

you don't have to edit that config file by the way, just open mplayer, and go to preferences. You can change the video driver there.

Perhaps the webcam isn't supported with linux. Totally possible.
Or maybe it doesn't work because you don't have the codecs required to play the file. Once you get those, it may work.

---

