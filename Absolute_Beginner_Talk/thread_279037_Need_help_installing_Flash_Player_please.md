---
title: "Need help installing Flash Player please"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-10-17
I'm trying to install Flash Player on Dapper.

I downloaded the file ' install_flash_player_7_linux ' and it appeared in my .tmp files, so I dragged it to my Home folder.

The instructions say'
"A directory called ' install_flash_player_7_linux ' will be created.  Navigate to this directory and from the command line type ./flashplayer-installer "

Assuming I haven't done anything wrong yet, what should I type in my terminal?

I ask this because if I type  ./flashplayer-installer  it returns "no such file or directory"

Thanks.

Lewis.

*****

---

### Post by Perfect Storm on 2006-10-17
```
cd /to/the/downloaded/package
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer
```

---

### Post by deadgobby on 2006-10-17
Or you can install Automatix or Easyubuntu
[http://www.getautomatix.com/](http://www.getautomatix.com/)
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
 Please know that flash 8 is not avail to linux/unix. Some time in 2007 that FP 9 will be avail. So if you go to like Ebaums World and want to see vids. Not going to happen. Thus installing Firefox for windows by using Wine.
Gobby

---

### Post by aysiu on 2006-10-17
This will show you how to install Flash:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by L Campbell on 2006-10-17
> **Artificial Intelligence said:**
> ```
cd /to/the/downloaded/package
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer
```

Hi, thanks for your help.

Here is what happened:-

four@four-desktop:~$ cd Desktop/install_flash_player_7_linux
four@four-desktop:~/Desktop/install_flash_player_7_linux$ tar -zxf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
four@four-desktop:~/Desktop/install_flash_player_7_linux$

It seems like I found the downloaded package OK but the 'unzip' part didn't work.

Am I doing something wrong here?

Kind regards.

Lewis.

*****

---

### Post by Perfect Storm on 2006-10-17
You have unpacked it so you don't need to tar -zxf (it's a command to unpack)

---

### Post by L Campbell on 2006-10-17
> **Artificial Intelligence said:**
> You have unpacked it so you don't need to tar -zxf (it's a command to unpack)

OK.

So I tried this:-

four@four-desktop:~$ cd Desktop/install_flash_player_7_linux
four@four-desktop:~/Desktop/install_flash_player_7_linux$ sudo sh flashplayer-installer
Password:
sh: flashplayer-installer: No such file or directory
four@four-desktop:~/Desktop/install_flash_player_7_linux$

Did I do something wrong here?

Kind regards.

---

### Post by james.gornall on 2006-10-17
I'm kind of new but I just used the Synaptic Application manager.

Sure its in there.  Use the search and install.

Sorry if I'm on the wrong lines.

---

### Post by aysiu on 2006-10-17
I believe you can just visit a webpage that requires Flash and then install the missing plugin using the Firefox dialogue.

There are other methods, too, described on the page I linked to earlier:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by Matodo on 2006-10-17
Are you sure that the 'install_flash_player_7_linux' file exists in this folder ?
Here is how to install it, first you have to [download it]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz") and save it in your home folder
```
matodo@box:~$ tar xzvf install_flash_player_7_linux.tar.gz
install_flash_player_7_linux/
install_flash_player_7_linux/flashplayer.xpt
install_flash_player_7_linux/flashplayer-installer
install_flash_player_7_linux/Readme.htm
install_flash_player_7_linux/Readme.txt
install_flash_player_7_linux/libflashplayer.so
matodo@box:~$ cd install_flash_player_7_linux/
matodo@box:~/install_flash_player_7_linux$ ls
flashplayer-installer  libflashplayer.so  Readme.txt
flashplayer.xpt        Readme.htm
matodo@box:~/install_flash_player_7_linux$ sudo sh flashplayer-installer
```

Good luck

> I believe you can just visit a webpage that requires Flash and then install the missing plugin using the Firefox dialogue.
It didn't work for me, I had to install it manually.

---

### Post by aysiu on 2006-10-17
> **Matodo said:**
> 
It didn't work for me, I had to install it manually. There are several ways to install Flash player more easily than the OP is doing right now.

---

### Post by L Campbell on 2006-10-17
> **james.gornall said:**
> I'm kind of new but I just used the Synaptic Application manager.

Sure its in there.  Use the search and install.

Sorry if I'm on the wrong lines.

Hi, thanks for your interest.

What you say is exactly right but when I had looked at that it appeared that it was 'non-free'.  I'm certainly no whiz at this but I read somewhere that some of the Linux files are not legal to use in America, or something to that effect.

The link to this file that I am trying to install came from this website:-

[http://www.youtube.com/watch?v=lRRDzFROMx0](http://www.youtube.com/watch?v=lRRDzFROMx0)

There was no mention of it being anything but free, so I thought I would try it.

Instead, IT is trying me, as I have vet to figure out to install it.   :-)

Kind regards.

---

### Post by L Campbell on 2006-10-17
> **aysiu said:**
> I believe you can just visit a webpage that requires Flash and then install the missing plugin using the Firefox dialogue.

There are other methods, too, described on the page I linked to earlier:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)


Thanks, you are correct.  I got this file that I'm trying to install from:-

[http://www.youtube.com/watch?v=lRRDzFROMx0](http://www.youtube.com/watch?v=lRRDzFROMx0)

It appeared that to install it would be easier than falling off a log but it hasn't been that way for me, SO FAR.  I'm not giving up yet.

Kind regards.

---

### Post by aysiu on 2006-10-17
non-free just means it's not open source. It doesn't mean it's illegal or that it costs money.

---

