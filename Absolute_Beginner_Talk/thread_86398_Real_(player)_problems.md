---
title: "Real (player) problems"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2005-11-05
HI all
I'm trying to install Realplayer, an apt-get install got me to a screen that said :
[HTML]This is the Real Player installer package, it does not actually contain   &#9474;
 &#9474; Real Player. You will need to go download Real Player by hand. Once you   &#9474;
 &#9474; have downloaded it you can proceed and tell the installer which           &#9474;
 &#9474; directory you put it in. [/HTML]
the next screen said :
 [HTML]Please visit http://scopes.real.com/real/player/unix/unix.html Select    &#9474;
  &#9474; 'Linux 2.x (libc6 i386) RPM'. Download it, and ensure permissions are    &#9474;
  &#9474; appropriate. It should be called rp8_linux20_libc6_i386_cs2_rpm. When    &#9474;
  &#9474; prompted, enter the directory you downloaded it to (defaults to /root).  &#9474;
  &#9474;                                                                          &#9474;
  &#9474; Real Player has been downloaded to where?   [/HTML]

. I downloaded put it in /root (i logged in as root and used the command ls to make sure it is actually there) and changed the name to rp8_linux20_libc6_i386_cs2_rpm . but after i pressed ok it said :
  [HTML]                         &#9474;
 &#9474;                                                                           &#9474;
 &#9474; The file /root/rp8_linux20_libc6_i386_cs2_rpm does not exist, or it is    &#9474;
 &#9474; corrupt. You may have downloaded the wrong file, or put it in the wrong   &#9474;
 &#9474; location. Please try again.                                               &#9474;
 &#9474;                                                                           &#9474;
 &#9474; If the file you downloaded has a different name, the filename may have    &#9474;
 &#9474; changed since this installer was last updated. You can still try to use   &#9474;
 &#9474; the installer; just rename the file you downloaded to                     &#9474;
 &#9474; /root/ . Note that if you do this, there    &#9474;
 &#9474; is no guarantee the installer will work. [/HTML]
I erased the file ,rebooted and started all over but ended up with the same results.
Any suggestions??

---

### Post by adwait on 2005-11-05
That package is for real player 8, and the version now available at the real website is 10. So just download the file (binary NOT rpm). Run the file as root using
```
sudo ./<filename>
```

Enter the install location etc. and you are done. To start realplayer, you will have to type
```
/<install location/realplayer 
```

---

### Post by paddyg on 2005-11-05
also, you can take a look at this thread

[http://www.ubuntuforums.org/showthread.php?t=80935](http://www.ubuntuforums.org/showthread.php?t=80935)

---

### Post by seshomaru samma on 2005-11-05
Thanks for the detailed replies.
I followed the instructions in both this thread and the link that paddyg gave and everything seemed OK. I now have the RealPlayer icon in my Applications>Sound &Video, it's just that when i click on it -nothing happens. As if its not there at all, very mysterious...
Any suggestions?

---

### Post by adwait on 2005-11-05
Try starting it from the command line and look at the errors it gives. Try disabling your sound server before starting realplayer.

---

### Post by seshomaru samma on 2005-11-05
i tried to run it from the terminal 
here is the result

> kitty@zhou:/usr/share$ ./RealPlayer
bash: ./RealPlayer: is a directory
kitty@zhou:/usr/share$ sudo ./RealPlayer
Password:
sudo: ./RealPlayer: command not found

I don't know how to disable the sound server...

---

### Post by adwait on 2005-11-05
That means you aren't entering the correct path to the executable. Where did you install realplayer? try
```
/usr/share/RealPlayer/./realplay
```

---

### Post by seshomaru samma on 2005-11-05
> That means you aren't entering the correct path to the executable. Where did you install realplayer? try
Code:

/usr/share/RealPlayer/./realplay


I suspected that..
thanks

here are the results :
> kitty@zhou:~$ /usr/share/RealPlayer/./realplay
/usr/share/RealPlayer/./realplay: line 75: 10121 Segmentation fault      $REALPLAYBIN "$@"

---

### Post by adwait on 2005-11-05
Hmm......not much idea here. But try turning the sound server off, by going to System>Multimedia and unchecking "start sound server on start up" or something like that can' t be too sure because I am using KDE.

---

### Post by thinhlegolas on 2005-11-06
I installed mine in /usr/local

Try /usr/local/RealPlayer/realplay

---

### Post by cletusbaird on 2005-11-06
Finally resolved methodolgy for incorporating RealPlayer 10 in Breezy:
Sudo apt-get install libstd C++5
Download RealPlayer 10 Binary
Change permissions to complete r-w and execute for all users
Cut and Paste to Home directory
From Terminal  sudo ./Real*
follow the bouncing ball when installation starts and answer questions
Real Player will be installed to applications found on start bar
Double click on Real Player and It is set up
 I knew problems resolved around libstdC++6 vs libstdc++5
It works first and everytime.....:cool:

---

### Post by hjansen on 2006-08-28
I (embrionic Ubuntu beginner). Have a different problem. I successfully installed Real Player Gold. Now I can't download any rpm files any more because clicking the download link opens real player. Any idea how to overcome? I know that Real Audio may see an rpm as a RA file.

---

