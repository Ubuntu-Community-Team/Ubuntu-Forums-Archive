---
title: "Problem to install Xubuntu on iBook G3"
date: 2011-07-31
forum: Apple Hardware Users
---

### Post by Pseudogod on 2011-07-31
Hello,

I would like to install Xubuntu on my old iBook, but I have some problems :
I have downloaded and burnt an alternate PPC Xubuntu 7.10 image and have booted on it. I have installed Xubuntu correcty, but I fail to boot Xubuntu for the fist time : I have a black frozen screen and nothing else happens (exactly like here : [http://www.youtube.com/watch?v=ESA7r4kCd4I&feature=related](http://www.youtube.com/watch?v=ESA7r4kCd4I&feature=related)). I can't access to the terminal, so I don't know how to change my xorg.conf or whatever else.  I have tried to use "Linux video=ofonly", nothing better.

Please help me, otherwise I will commit suicide...
Thanks



PS : I apologize for any mistakes in my English

---

### Post by linuxopjemac on 2011-08-01
There are so many installation guides out there, use the search button ;)

You can also have a look at my general website for a lot of information on this:

[http://mac.linux.be](http://mac.linux.be)

---

### Post by Pseudogod on 2011-08-01
Thank you for your answer. I've spent two or three hours to find a solution, using every guide I found. But my main problem is that I can't access to the terminal. I've seen your website and I will try to use the rescue mode to change my xorg.conf. Re-installation of Xubuntu in process...

---

### Post by linuxopjemac on 2011-08-01
Startup into single user mode, then you can alter X.

---

### Post by rsavage on 2011-08-01
There are at least two other neighbouring threads on similar themes.  Have you had a look at those? Also, there is the powerpc sticky - have you had a look at that?  On the last page is a link which will tell you how to install Xubuntu 11.04.
 
The hardest thing about Linux/ubuntu is finding the right documentation.

---

### Post by rsavage on 2011-08-01
I've thought about updating the power pc FAQ wiki, but does anybody actually find it when they need it?

---

### Post by Pseudogod on 2011-08-01
I've read hundreds of threads about iBook G3 installation problems, but in most cases you should use a keyboard shortcut to access to the terminal. With [this]("http://mac.linux.be/content/black-screen-or-missing-gui") page, I can edit now my xorg.conf (but Ithe dpkg-reconfigure xserver-xorg command doesn't work)...

I will try again tomorrow or after.

---

### Post by rsavage on 2011-08-01
That is an old command.  You need
 
sudo Xorg -configure
 
Like I said the difficulty is finding the right guide.  I have pointed you in the right direction of the threads I think you should read.  That is all I can do.

---

### Post by rsavage on 2011-08-01
Sorry, ignore that last post.  Forgot you are trying to install an old version of ubuntu.  Perhaps this is your problem?  Are you sure that is the version you want to install?

---

### Post by Pseudogod on 2011-08-01
At the beginning I found a howto about installing Xubuntu on an iBook G3 clamshell on the french Ubuntu Website.

Here : [http://doc.ubuntu-fr.org/ibook_g3_palourde](http://doc.ubuntu-fr.org/ibook_g3_palourde)  

On this page they recommand to use this version of Xubuntu and to upgrade to a newer version after.
So, I thought that it was the best way to install correctly Xubuntu, this is why I use Xubuntu 7.10

Thank you for your help.

---

### Post by rsavage on 2011-08-01
I'm sorry I can't be more help.  My knowledge of ubuntu is only a few months old, it does not stretch back to 7.10!
 
My french has also slipped since school so I can't read the page you've linked either!
 
I wrote my lubuntu howto guide (linked to on the last sticky page) in the hope that it would help new users like yourself find eveything.  I know how frustrating and tiring it can be installing ubuntu.  I've been in your position.  
 
I have no personal experience of the clamshell/G3 so don't know what it is capable of.  Lubuntu is the lightest of the ubuntus so it maybe the best for you?  xubuntu is better looking though.
 
Hope you get it sorted soon.

---

### Post by trellis2 on 2011-08-21
I cannot get xServer working. I get 11.04 splash screen then boots to a terminal. xorg -configure does not work. Have tried iBook1.txt file only to get..
"(EE) Unable to find a valid framebuffer device
 (EE) R128(0): Failed to open framebuffer device, consult warnings    and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
 (EE) Screen(s) found, but none have a usable configuration. "

---

### Post by rsavage on 2011-08-21
You need a capital 'X' on Xorg.  Also you need sudo in front.  It may still give you an error, but it should have generated an xorg.conf.new file.

---

