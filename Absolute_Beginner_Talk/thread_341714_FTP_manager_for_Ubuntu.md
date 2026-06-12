---
title: "FTP manager for Ubuntu?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2007-01-19
I would like to browse my data in a server via ftp connection. In Windows I used FileZilla. But in Ubuntu?

---

### Post by aysiu on 2007-01-19
How about FileZilla for Linux?
[http://superb-east.dl.sourceforge.net/sourceforge/filezilla/FileZilla_3.0.0-beta5_i586-linux-gnu.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/filezilla/FileZilla_3.0.0-beta5_i586-linux-gnu.tar.bz2)

---

### Post by Zdravko on 2007-01-19
Nope - it is not in the repo's:
> There is no matching application available.

---

### Post by nrwilk on 2007-01-19
I use gftp, and it's pretty good.
```
sudo aptitude install gftp
```

Also, I recently have been liking the nifty firefox extension which lets it act as an ftp client, fireftp.  Just install it at Mozilla's extension site like any other extension.  It's getting better and better pretty quickly.

Also, If you'd prefer a KDE (QT) client, then try Kbear.  I do like KDE apps better, but I've found Kbear to be a little bloated, and also just a tad unstable.
```
sudo aptitude install kbear
```

Hope this helps!

nrwilk

---

### Post by frolle on 2007-01-19
Get ssl running and use SFTP. Amazing combination :):p

---

### Post by Zdravko on 2007-01-19
[nrwilk]("http://ubuntuforums.org/member.php?u=41765"), thanks - I installed gftp and so far it seems working pretty well :)

---

### Post by DirtDawg on 2007-01-19
You can also use Nautilus. Places>Connect-to-server -> Service-type:FTP w/ login.

---

### Post by Zdravko on 2007-01-19
[DirtDawg]("http://ubuntuforums.org/member.php?u=5319"), yepp! It works, but... it doesn't have the specialized options a real ftp manager can have!

---

### Post by Fundi on 2007-01-19
I use gftp and it does the job well.

---

### Post by Quillz on 2007-01-19
I prefer just using the built-in FTP functions of Konqueror and Nautilus as opposed to having to download a specialized app.

---

### Post by mcduck on 2007-01-19
> **DirtDawg said:**
> You can also use Nautilus. Places>Connect-to-server -> Service-type:FTP w/ login.

I second this. Why use extra programs when all needed is already there..

Besides I love how I can just drag&drop files to icon on my desktop to upload stuff to server :)

---

### Post by Quillz on 2007-01-19
> **mcduck said:**
> I second this. Why use extra programs when all needed is already there..

Besides I love how I can just drag&drop files to icon on my desktop to upload stuff to server :)
As do I. It's simple and to-the-point.

---

### Post by aysiu on 2007-01-19
I use the FireFTP extension for Firefox and am pretty happy with it.

---

### Post by davebgimp on 2007-01-19
> **nrwilk said:**
> I use gftp, and it's pretty good.
```
sudo aptitude install gftp
```

Also, If you'd prefer a KDE (QT) client, then try Kbear.  I do like KDE apps better, but I've found Kbear to be a little bloated, and also just a tad unstable.
```
sudo aptitude install kbear
```

Hope this helps!

nrwilk


I second gftp. I use it to manage all ftp and ssh as well, when a gui is preferred.

Kbear... is a nightmare.

---

### Post by Old Pink on 2007-01-19
Another vote for the previously mentioned gFTP! :)

---

### Post by dannyboy79 on 2007-01-19
yeah but does gftp use SSL or TLS???? I use FireFTP, it's an extra for Firefox and it use's encryption so no one can scoop your clear text password you're using to sign into your ftp server!

---

### Post by davebgimp on 2007-01-19
> **dannyboy79 said:**
> yeah but does gftp use SSL or TLS???? I use FireFTP, it's an extra for Firefox and it use's encryption so no one can scoop your clear text password you're using to sign into your ftp server!

Gftp can use several protocols. I generally use it for SSH when I'm moving a bunch of files and SCP via terminal is too time consuming.

---

### Post by dannyboy79 on 2007-01-19
SSH is Secure Shell, what do you mean you use GFTP for SSH????

---

### Post by iluminate on 2007-01-19
> **mcduck said:**
> I second this. Why use extra programs when all needed is already there..

Besides I love how I can just drag&drop files to icon on my desktop to upload stuff to server :)

Sorry if I hijack this thread, but what if you select SSH login?
Then this does not work, at least not for me.
I loging to the remote server with my username and pass, but whenever I try to change or edit a file I get permisson denied.
Also when checking the filepermission on the file I am trying to edit, the group is displayed wrong.

The problem is that I am trying to SSH in my way and edit and upload files - via a gui.
Tired of using SCP and gedit ssh2 always adds my localaccount as fileowner...
Then I have to ssh in via terminal and chown and chmod the files manually.
Should it be like this?

---

### Post by dannyboy79 on 2007-01-19
testing updated signature, sorry.

---

### Post by davebgimp on 2007-01-19
> **dannyboy79 said:**
> SSH is Secure Shell, what do you mean you use GFTP for SSH????

GFTP can give you a gui for scp and other ssh functions.

---

### Post by iluminate on 2007-01-19
> **dannyboy79 said:**
> SSH is Secure Shell, what do you mean you use GFTP for SSH????

Try it works! Instead of FTP in the dropdown menu, use SSH2......
Or am I wrong here?

---

### Post by davebgimp on 2007-01-19
> **iluminate said:**
> Try it works! Instead of FTP in the dropdown menu, use SSH2......
Or am I wrong here?

You're not wrong. Pretty handy, right?

Also, if you're a Kubuntu user, try pointing Konqueror to:

**fish://user@yourserver.com**

then, for added fun, hit CTRL-SHIFT-L to split the window, set one to display local stuff and the other remote. Drag and drop SSH madness! :D

---

### Post by Zdravko on 2007-01-19
[dannyboy79]("http://ubuntuforums.org/member.php?u=108777"), you're not excused, because I am subscribed to all the threads I participate in. Now I recieve an email for every thing you post in this topic!

---

### Post by dannyboy79 on 2007-01-19
> **Zdravko said:**
> [dannyboy79]("http://ubuntuforums.org/member.php?u=108777"), you're not excused, because I am subscribed to all the threads I participate in. Now I recieve an email for every thing you post in this topic!

Your statement, "Now I recieve an email for every thing you post in this topic!"
is not my fault, if you don't want to receive an email everytime I post something here than turn the setting off!!!! Also, it's not just when I post, it's when anyone posts! 

So you guys are saying that within GFTP, you can change it somehow use the SSH protocol instead of the FTP protocol which will giv eyou a gui??? That sounds cool. It's got to be hell-a-slow transferring files doesn't it??? Since all the traffic is encrypted? All I would want is my username and password encrypted hence why I asked about GFTP being able to use TLS or SSL?

---

### Post by dannyboy79 on 2007-01-19
Hey Zdravko, what does your signature say? I can't read whatever langauge that is?

---

### Post by davebgimp on 2007-01-19
> **dannyboy79 said:**
> Hey Zdravko, what does your signature say? I can't read whatever langauge that is?

It's called Latin.

---

### Post by dannyboy79 on 2007-01-19
thank you for the langauge, can you translate it?

---

### Post by davebgimp on 2007-01-19
Roughly:
Time changes all things
I only count the sunny hours.
A sleeping dragon [is] never to be tickled/poked

---

### Post by Zdravko on 2007-01-19
Ok, let's continue with the off-topic:
There are 3 Latin phrases - which are also independent in their meanings from each other.
"tempora mvtantvr et nos mvtamvr in illis" = "Time is changing and we are changing with it", said King Lothar I.
"horas non nvmero nisi serenas" = "I don't count the hours unless they are sunny", a common inscription on sun dials.
"draco dormiens nvnqvam titillandvs" = "Never tickle a sleeping dragon", the motto of Hogwarts school from "Harry Potter".
As you can see there is no visible connection between these phrases - I just like them as wise proverbs. I was inspired in Latin after reading the book "The name of the rose" from Umberto Eco. Further more I replaced every 'u' with a 'v', so that the original Latin alphabet is also reflected (it has one and the same sign for different vowels, like in "Clavdivs", which reads "Claudius").

---

### Post by dannyboy79 on 2007-01-19
Cool, i wish I knew latin.

---

### Post by Zdravko on 2007-01-19
BTW, that gFTP is very buggy. It crashes often, when I try to delete some folder on the server...

---

### Post by davebgimp on 2007-01-19
Weird I've used it solidly for over 2 years under KDE and Gnome and I don't think I've ever had it crash once that I can think of, but oh well.
Deliriant isti Romani.

---

### Post by Zdravko on 2007-01-19
"They are mad, those Romans!"
Strangely, the whole Edgy distributions is very unstable for me. Most of the apps crash when they want...

---

### Post by benthegreat on 2007-01-27
is there a server version of gftp?

---

### Post by moredhel on 2007-01-27
if you find gftp buggy, then you could try kasablanca or kftpgrabber

---

### Post by dannyboy79 on 2007-01-27
what do you mean server version? why would there be a seperate version for an ftp client? maybe some that have different forms of authentification. gftp is not a ftp server if that's what you think. maybe you could explain what you mean?

---

### Post by miceagol on 2007-04-21
I'm trying to find a ssh client with the following features:
[LIST]
[*]Save connection profiles so that I don't have to enter them every time
[*]Support for servers with public/private key
[/LIST]

gFTP doesn't cover these two requirements. Any clients that does? It must support ssh!

---

### Post by GálGeri on 2007-04-21
I use a small file manager called **[BSCommander]("www.beesoft.org/bsc.html")** for FTP. It has two panel for the list of the files like Total Commander under Windows, so it's easy to move files among the server and your computer.

---

### Post by dashman on 2007-05-14
I see there is filezilla client for ubuntu but is there also [B]filezilla [U]server
[/U][/B]I need a ftp server with graphical interface for ubuntu...any suggestions ? I tried gproftpd but didn't like it...

---

