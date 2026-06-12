---
title: "Need help installing file, please."
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-12-26
I have download Flashplayer to my desktop but I'm not sure what these instructions mean:-

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

What I'm stuck with is, "Navigate to this directory"  I don't know how to do this.

I'm comfortable with the rest of it.

Thanks.

---

### Post by taurus on 2006-12-26
Why would you want to install flash 7 since most sites are requiring at least flash 8?  You can install flash 9 by using automatix2...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by halitech on 2006-12-26
It means to open a terminal and go to the directory where the files are, extract them and then run the ./command. depending on where you are installing to, you may need to run sudo ./command

better option would be do as taurus suggested, grab automatix and install flash 9.

---

### Post by L Campbell on 2006-12-26
> **taurus said:**
> Why would you want to install flash 7 since most sites are requiring at least flash 8?  You can install flash 9 by using automatix2...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Thanks.

There is a movie from Metacafe.com that I want to play and it directed me to the site to get this version.

I have Automatix but it requires that (under penalty of death) you will not use certain files if you reside in USA, so I don't want to use it.

---

### Post by halitech on 2006-12-26
the files it doesn't want you to use are more the non free codecs. flash is fine to install, along with probably 90% of the other programs.

---

### Post by L Campbell on 2006-12-26
> **halitech said:**
> It means to open a terminal and go to the directory where the files are, extract them and then run the ./command. depending on where you are installing to, you may need to run sudo ./command

better option would be do as taurus suggested, grab automatix and install flash 9.

Thanks.

If I understand this, then, I should change directory to Desktop (the location of the file) and enter the command?

1234@1234-desktop:~$ cd Desktop
1234@1234-desktop:~/Desktop$ install_flash_player_7_linux
bash: install_flash_player_7_linux: command not found
1234@1234-desktop:~/Desktop$

I don't think it worked.

When I enter  ' about:plugins ' in the browser, it says 'No plugins are installed'

---

### Post by taurus on 2006-12-26
What's the output of 

```
ls -la ~/Desktop
```

---

### Post by L Campbell on 2006-12-26
> **taurus said:**
> What's the output of 

```
ls -la ~/Desktop
```

1234@1234-desktop:~$ ls -la ~/Desktop
total 713404
drwxr-xr-x  4 1234 1234      4096 2006-12-26 11:33 .
drwxr-xr-x 25 1234 1234      4096 2006-12-26 12:28 ..
drwx------  2 1234 1234      4096 2006-12-21 15:00 .disk
-rw-r--r--  1 1234 1234      6423 2006-04-10 04:32 hadjaha-001a0ab1b9.desktop
drwxr-xr-x  2 1234 1234      4096 2006-12-04 18:09 install_flash_player_7_linux
-rw-r--r--  1 1234 1234   1017790 2006-12-26 11:29 install_flash_player_7_linux. tar.gz
-rw-r--r--  1 1234 1234 728760320 2006-12-22 12:15 LinuxMint-2.1.iso
1234@1234-desktop:~$

Thanks.

---

### Post by christhemonkey on 2006-12-26
I think you need to do a:
```
**./**install_flash_player_7_linux 
```
after "cd Desktop" as opposed to:
```
install_flash_player_7_linux 
```
as the second command will try and execute an item in your path which ~/Desktop isnt.

---

### Post by neowolf on 2006-12-26
Open the Terminal and run this,

```

cd $HOME/Desktop; ./install_flash_player_7_linux

```

---

### Post by halitech on 2006-12-26
wouldn't this be a folder? size of 4096 seems awful small to me.

drwxr-xr-x 2 1234 1234 4096 2006-12-04 18:09 install_flash_player_7_linux

---

### Post by L Campbell on 2006-12-26
> **christhemonkey said:**
> I think you need to do a:
```
**./**install_flash_player_7_linux 
```
after "cd Desktop" as opposed to:
```
install_flash_player_7_linux 
```
as the second command will try and execute an item in your path which ~/Desktop isnt.


1234@1234-desktop:~$ cd Desktop ./install_flash_player_7_linux
1234@1234-desktop:~/Desktop$

I'm not sure about this.   :-(

About:plugins is still saying I don't have anything

---

### Post by christhemonkey on 2006-12-26
I meant after executing the cd Desktop like this:
```
cd Desktop
./install_flash_player_7_linux 
```

My apologies for my inacuraccy in the instructions.

---

### Post by L Campbell on 2006-12-26
> **christhemonkey said:**
> I meant after executing the cd Desktop like this:
```
cd Desktop
./install_flash_player_7_linux 
```

My apologies for my inacuraccy in the instructions.

No problem.  I appreciate you taking the time to help me.

1234@1234-desktop:~$ cd Desktop
1234@1234-desktop:~/Desktop$ ./install_flash_player_7_linux
bash: ./install_flash_player_7_linux: is a directory
1234@1234-desktop:~/Desktop$

---

### Post by christhemonkey on 2006-12-26
halitech was right its a directory so you not to get inside it...

```
cd ~/Desktop/install_flash_player_7_linux 
```
Then list the contents of that folder:
```
ls -la ./ 
```

---

### Post by L Campbell on 2006-12-26
> **christhemonkey said:**
> halitech was right its a directory so you not to get inside it...

```
cd ~/Desktop/install_flash_player_7_linux 
```
Then list the contents of that folder:
```
ls -la ./ 
```

1234@1234-desktop:~/Desktop/install_flash_player_7_linux$ ls -la ./
total 2160
drwxr-xr-x 2 1234 1234    4096 2006-12-04 18:09 .
drwxr-xr-x 4 1234 1234    4096 2006-12-26 11:33 ..
-r-xr-xr-x 1 1234 1234   23614 2006-10-27 15:42 flashplayer-installer
-r--r--r-- 1 1234 1234     856 2006-10-27 15:42 flashplayer.xpt
-rwxr-xr-x 1 1234 1234 2158864 2006-10-27 15:42 libflashplayer.so
-rw-r--r-- 1 1234 1234    5255 2006-12-04 18:09 Readme.txt
1234@1234-desktop:~/Desktop/install_flash_player_7_linux$

I think we're on a roll now.   :-0

---

### Post by taurus on 2006-12-26
```
./flashplayer-installer
```

---

### Post by L Campbell on 2006-12-26
> **taurus said:**
> ```
./flashplayer-installer
```

1234@1234-desktop:~$ cd Desktop
1234@1234-desktop:~/Desktop$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
1234@1234-desktop:~/Desktop$ cd
1234@1234-desktop:~$ cd Desktop./flashplayer-installer
bash: cd: Desktop./flashplayer-installer: No such file or directory
1234@1234-desktop:~$


No luck here.

---

### Post by taurus on 2006-12-26
```
cd ~/Desktop/install_flash_player_7_linux
./flashplayer-installer
```

---

### Post by L Campbell on 2006-12-26
> **taurus said:**
> ```
cd ~/Desktop/install_flash_player_7_linux
./flashplayer-installer
```

THAT WAS IT !!!!!

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r69

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Thanks very much, I really appreciate it.

Kind regards.

---

### Post by taurus on 2006-12-26
Well, have fun with it.

---

