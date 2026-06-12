---
title: "first experience with ubuntu/using as server"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by badperson on 2007-10-12
Hi,
I've been lurking here for a little while sorting through all the information, and I just wanted to get a sense of whether or not I'm going in the right direction. 


I have a desktop, a laptop and an older desktop that I want to use as a server. I want to do a LAMP install so I can do some java and xml programming, and I want to get my feet wet with networking. 

I want a setup where both the other machines can get at files on the server (the laptop will be connected via wireless), I'd like to print from the ubuntu server. 

I'd also like to be able to get at it remotley at least with ftp, and if possible play around using a remote desktop. 

Lots of great info on this site, still going through it, but wanted to see if others use a setup like I described. 

thanks, 
bp:guitar:

---

### Post by jgrabham on 2007-10-12
> **badperson said:**
> Hi,
I've been lurking here for a little while sorting through all the information, and I just wanted to get a sense of whether or not I'm going in the right direction. 


I have a desktop, a laptop and an older desktop that I want to use as a server. I want to do a LAMP install so I can do some java and xml programming, and I want to get my feet wet with networking. 

I want a setup where both the other machines can get at files on the server (the laptop will be connected via wireless), I'd like to print from the ubuntu server. 

I'd also like to be able to get at it remotley at least with ftp, and if possible play around using a remote desktop. 

Lots of great info on this site, still going through it, but wanted to see if others use a setup like I described. 

thanks, 
bp:guitar:

Remote access is easy if you have a gui installed, there is a program called VNC already installed, just open a terminal, and type
 [PHP]vnc viewer[/PHP].

Otherwise good setup, but beware sharp increase on your electricity costs!!

---

### Post by jvc26 on 2007-10-12
As an idea, try to get ssh up and running for remote admin; also means you can run a headless (without screen) server and then it can be left somewhere on its own and you don't need to worry about it. ssh will also offer you the ability to use sftp, which is much more secure than ftp.
Il

---

### Post by Bliepo32 on 2007-10-12
[The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

---

### Post by getaboat on 2007-10-12
> **Bliepo32 said:**
> [The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

Wow - thanks - just what I want!

---

