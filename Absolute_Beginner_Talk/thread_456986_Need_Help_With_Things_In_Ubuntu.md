---
title: "Need Help With Things In Ubuntu"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by zubair4148 on 2007-05-28
Hello I Am Using Ubuntu 5.10

1.
I Need To Install Gftp manually, I Don't Have Net At Home So I Downloaded This App And How To Intall It.

2.
After Starting Terminal su command asks Password and I Only Setted Up The PC With xxxxxxx this Pasword It Is Not Excepting It.

3.
I Want To Run Some Commands in a saved File and run it in terminal howto

Please Help Me Do I Have To Download New Version Of Ubuntu

---

### Post by justifier on 2007-05-28
how is Gftp packaged? 

in terminal with thepassword it doesnt look like its typing but it is, is the password saying that it is incorrect or does it just look like its not going in? 

what sort of file is it? 
try running 
sh /path/to/file

---

### Post by darklemming54 on 2007-05-28
if you are still using version 5.10, then you should upgrade to 7.04 if you can, because it will make things alot easier.  if you can't, the following should still work in 5.10

1.  if you download the source, you can do 
```

./configure
make
make install

```or if you have the deb, 
```

dpkg -i [filename].deb

```
2 if you use "sudo" instead of "su" then you can use the password that you set, but if you want to do "su" then you need to set a password for root by doing 
```

passwd root

```and type in the password you want



3 i dont understand the question

---

### Post by endersshadow on 2007-05-28
1. Run these commands:
```
wget http://gftp.seul.org/gftp-2.0.18.tar.gz
tar xzf gftp-2.0.18.tar.gz
cd gftp-2.0.18
./configure
make
sudo make install
```
And pray you don't come across dependency errors.  If you do, put the Ubuntu CD in and try using that to find the packages you need.  They should all be on there.

2. Use sudo, not su. And never ever post your password in a public forum.

3. If it's a list of commands, put this at the top:
```
!#/bin/sh
```
Then, run these commands:
```
chmod +x /path/to/file/of/commands
/path/to/file/of/commands
```

4. You don't have to download the new version of Ubuntu, but it's very much suggested.

5. Also, why do you need gftp if you don't have the internet at home?

---

### Post by starcraft.man on 2007-05-28
1) I assume you mean your home computer is not connected to the net at all. Did you have trouble setting up the connection? Or do you simply not have internet in the house where your Ubuntu machine is? If you don't have internet at all going to your Ubuntu machine, I recommend you not use Ubuntu, its an internet based distribution (where as windows can work without the internet long as you buy CDs). Ubuntu really requires net access for the large and frequent amount of updates and quick install access via apt/synaptic.

That said, I don't know what you downloaded to install. If its a deb, then you just double click. If its a tar.gz, then you'd have to compile. [URL="http://www.psychocats.net/ubuntu/installingsoftware"]Look here. 
[/URL]
2) Ubuntu uses Sudo, not su by default. [This explains it and why.]("https://help.ubuntu.com/community/RootSudo") There is only one password sudo expects by default and that is the same as your user pass unless you specifically changed it after install, then it would be whatever you changed it to.

3) [How to use terminal.]("https://help.ubuntu.com/community/UsingTheTerminal")

Once again, I'll just reiterate, Ubuntu may not be for you if you lack a net connection to it most of the time. It will be a pain to get new apps, updates and other modifications.

Edit: *grumbles that got out posted*

---

### Post by Lucifiel on 2007-05-28
Edit: You guys beat me to it! :D 


Errrr... if I may advise, could you remove your password from your post, please?

Also, did you download the .deb or the .tar.gz version? I advise downloading the .deb version as it is easier to install and remove. 

If you want to use Terminal to install the .deb file, use :

> dpkg -i <application.deb>

If not, just double-click on the .deb file to install it.

---

### Post by starcraft.man on 2007-05-28
> **Lucifiel said:**
> Edit: You guys beat me to it! :D 


Ya no kidding, me too.... are we getting slow? Noooooooooooooooooooooooooooooooooooo *cries*

At least I got there just a sec before ya :p

---

### Post by Lucifiel on 2007-05-28
Huh... the topic had no replies when I hit the reply button but I was reading something else at that time, so... lol. :D

---

### Post by dasunst3r on 2007-05-28
1. If you have some time to play around, also try connecting to your FTP site using Nautilus.  To add a server, go to File -> Connect to Server.  The FTP site will then look and feel like a drive to you.  Also, you may want to change the password -- "123456" may not be the best choice.

2. In Ubuntu, use the *sudo* command.  Type in the password you use to log into your computer.

3. Sorry... don't know

I do not think that you will have to get a new version of Ubuntu.

---

### Post by PhloxyFlowers on 2007-05-28
I'm absolutely terrified about installing it!! I hate windows with a passion and I want desperately to loose it all together.. BUT I see where people have installed it into a different partition !! Scared, scared, scared!!
But intrigued as well. Talk about your sitting on a fence7
):P

---

### Post by zubair4148 on 2007-05-28
> **endersshadow said:**
> 
5. Also, why do you need gftp if you don't have the internet at home?

I Have DreamBox And I Need To Connet To It To Edit The File's In IT. (Using Router and Hub)

Thanks For The Responce I Will Tty It At Home.

Little Experiment On Linux,

!#/bin/sh
I Will Try This And Reply Tommorow For List Of Commands

Gftp Downloaded The "gftp_2.0.18-16ubuntu2_all.deb" One

I Want Terminal To Ask Password On The Starting And Not After.


Thank's Guys. This Was Great Responce.

---

### Post by zubair4148 on 2007-05-29
sudo dpkg -i gftp.deb
(Reading database ... 56665 files and directories currently installed.)
Preparing to replace gftp 2.0.18-16ubuntu2 (using gftp.deb) ...
Unpacking replacement gftp ...
dpkg: dependency problems prevent configuration of gftp:
 gftp depends on gftp-gtk (>= 2.0.18-16ubuntu2); however:
  Package gftp-gtk is not installed.
 gftp depends on gftp-text (>= 2.0.18-16ubuntu2); however:
  Package gftp-text is not installed.
dpkg: error processing gftp (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gftp


Does This Mean Gftp is already installed.
So from where Can I Start It.

---

### Post by endersshadow on 2007-05-29
You can try starting it via the command "gftp" (sans quotes).

---

