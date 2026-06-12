---
title: "Root password problem"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by gewitty on 2006-10-16
I recently installed Ubuntu Desktop and am now trying to install Xampp, which needs to be extracted into the /opt directory. To do this requires me to log in as administrator. However, when I enter 'su' and then enter my password, I get rejected:

dave@Linux-desktop:~$ su
Password:
su: Authentication failure
Sorry.
dave@Linux-desktop:~$

I'm using the password I entered during setup, so can't think what else to use. Can anyone tell me how to overcome this problem?

---

### Post by an.echte.trilingue on 2006-10-16
Ubuntu sets a random root password by default.  sudo is the usual way of doing things.  If you want a root terminal, you can type "sudo su", but I would really recommend that you try to find a program in the repositories that does what you want; it makes life much easier that way.  Be sure to enable universe and multiverse.

---

### Post by Bachstelze on 2006-10-16
```
sudo -i
```

(and **not** sudo su) will get you a root terminal. Be **very** careful on what you type in there, a single mistyped command could break the whole system !

---

### Post by jd65pl on 2006-10-16
You may find [this page]("http://www.psychocats.net/ubuntu/sudo") useful

---

### Post by an.echte.trilingue on 2006-10-16
> **HymnToLife said:**
> ```
sudo -i
```

(and **not** sudo su) will get you a root terminal. Be **very** careful on what you type in there, a single mistyped command could break the whole system !

Not to be rude, but yes it will get you a root terminal.  It does the exact same thing as sudo -i;  Try it if you don't beleive me.

---

### Post by chirayu on 2006-10-16
> **gewitty said:**
> I recently installed Ubuntu Desktop and am now trying to install Xampp, which needs to be extracted into the /opt directory. To do this requires me to log in as administrator. However, when I enter 'su' and then enter my password, I get rejected:

dave@Linux-desktop:~$ su
Password:
su: Authentication failure
Sorry.
dave@Linux-desktop:~$

I'm using the password I entered during setup, so can't think what else to use. Can anyone tell me how to overcome this problem?


```
sudo -s
```

When asked, enter your own password (the one you setup when you were installing)

Also, have you simply tried installing Xampp by doing this?

```
sudo apt-get install xampp
```

Hope this solves your issue

---

### Post by Bachstelze on 2006-10-16
I never said it didn't work. I said not to use it because people far more knowledgeable than me told me it could break things very badly.

---

### Post by an.echte.trilingue on 2006-10-16
Trust me, there is nothing that can happen with sudo su that can't happen with sudo -i.  Nothing.  If anything it is safer because you cannot open new windows in your Xserver as you can with sudo.

---

### Post by Netherwolf on 2006-10-16
Ah, sudo. That's the nice thing about Linux. It still ensures you know what you're doing, as opposed to the peace, love, and venereal diseases mindset of Windows default admin rights. And the Vista double-confirmation is annoying.

I'm still very much a noob in the Ubuntu and web-server fields, but I've learned the basics. As far as Xampp? Synaptic-ing apache2 and the appropriate mysql, perl, and php mods would have worked too, but hey, whatever gets you by.
EDIT: Does xampp have an APT package? Didn't know that. Oh well. If it does, do a search (after enabling the right repositories) for xampp and just install it and its dependencies.
Learn to love Synaptic and the other APT tools. They won't let you down. And they have Super Cow Powers. Remember that. XD

Furthermore, don't forget that XAMPP is not locked down, security-wise. Check the [READ ME]("http://www.apachefriends.org/en/xampp-linux.html#381"). Having a blank MYSQL root password is BAD. Especially if you try to run a bulliten service like phpBB. Also, don't use it for anything other than general database management things like account and database creation. Use a secondary account with a strong password to do the real work. Otherwise, you're asking (getdownonyoukneesandbeg) for trouble.
[MySQLAdmin]("http://www.mysql.com/products/tools/administrator/") is good for managing your databases.
If you move to a dedicated web-server, phpMyAdmin and phpSysInfo are your friends, just so long as no one else knows how to get into them. 

Check at a Half-Price book store for good books on PHP and Perl programming.
[http://www.zend.com/]("http://www.zend.com/") is a god-send.

Sorry if I'm just vomiting information like some noob poster (I AM), but this is just the tip of the iceberg. Be safe, and secure and, most importantly, Happy XAMPPing!
-NW

EDIT: Mangeek covers the security issue nicely on his [blog]("http://www.mangeek.com/blogc/18.html").

---

### Post by TheWizzard on 2006-10-16
**sudo su** gives you the same powers as **sudo -i**, as far as i know. nevertheless, the latter is more 'elegant' and takes you to the root's home folder. 

good info can be found here: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gewitty on 2006-10-16
Wow! I'm somewhat overwhelmed with information. Thanks to everyone who replied.

Picking up on some of the points raised:

"Ubuntu sets a random root password by default. sudo is the usual way of doing things. If you want a root terminal, you can type "sudo su", but I would really recommend that you try to find a program in the repositories that does what you want; it makes life much easier that way. Be sure to enable universe and multiverse."

If a random password is set, how do you know what it is? As for universe and multiverse, the only time I've encountered these before was on Discworld. What are they?

The reason I'm trying to install Xampp is that I have been using it some time on a Windows box to develop Joomla sites, so I know it fairly well and would like to keep on using it.


"When asked, enter your own password (the one you setup when you were installing)

Also, have you simply tried installing Xampp by doing this?

Code:

sudo apt-get install xampp "

I tried this and it looked as if was going to work, but it couldn't find the Xampp package, which is currently sitting on my desktop. Where should it be so that the install routine can find it?

---

### Post by aysiu on 2006-10-16
You can't *apt-get* xampp, since it's not in the repositories, not even the Universe or Multiverse ones. Just paste these commands into the terminal: ```
wget -c http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz
sudo tar xvfz xampp-linux-1.5.4a.tar.gz -C /opt
sudo ln -s /opt/lampp/lampp /usr/bin/lampp
``` I based those off of the instructions on the xampp website--just put *sudo* in the appropriate places.

---

### Post by gewitty on 2006-10-17
> **aysiu said:**
> You can't *apt-get* xampp, since it's not in the repositories, not even the Universe or Multiverse ones. Just paste these commands into the terminal: ```
wget -c http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz
sudo tar xvfz xampp-linux-1.5.4a.tar.gz -C /opt
sudo ln -s /opt/lampp/lampp /usr/bin/lampp
``` I based those off of the instructions on the xampp website--just put *sudo* in the appropriate places.

Tried that, but got an error, as follows:

dave@Linux-desktop:~$ wget -c [http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz](http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz)
--07:34:13--  [http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz](http://www.apachefriends.org/download.php?xampp-linux-1.5.4a.tar.gz)
           => `download.php?xampp-linux-1.5.4a.tar.gz'
Connecting to 192.168.1.100:80... connected.
Proxy request sent, awaiting response... 404 Not Found
07:34:13 ERROR 404: Not Found.

I've also tried substituting the download address from a couple of the Xampp mirror sites, but still get an ERROR 404, even though a normal Windows download works OK from these locations.

---

### Post by aysiu on 2006-10-17
If you're able to get ahold of the .tar.gz, just paste in the second two commands. The first command just fetches it off the server.

---

### Post by gewitty on 2006-10-17
> **aysiu said:**
> If you're able to get ahold of the .tar.gz, just paste in the second two commands. The first command just fetches it off the server.

The reason the file did not download appears to be a problem within Ubuntu. Although my network and browser are working OK, and I can use Firefox to download files, command line download instructions always fail. This also happened when I enabled Universe and Multiverse. After doing this, Ubuntu tried to update it's channel information, but the requests failed. Is this a permissions problem, or another setting somewhere?

Having downloaded the file via Firefox, I have the tar.gz file sitting on the desktop, so presumably I need to tell Ubuntu where it is as part of the commands. As far as I know, the default location it looks in is the archive repository. Do I need to move the file there (moving seems to be a problem as I keep running into admin rights errors), or can I run from the Desktop?

---

### Post by aysiu on 2006-10-17
```
cd ~/Desktop
``` and then those two last commands.

---

### Post by gewitty on 2006-10-17
> **aysiu said:**
> ```
cd ~/Desktop
``` and then those two last commands.

That appears to have worked. Many thanks. I've obviously got a lot of learning to do before I'm deprogrammed from MS!

---

