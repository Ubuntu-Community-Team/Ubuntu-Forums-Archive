---
title: "I know this sounds stupid, but...."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-18
[COLOR=Black]I am trying to copy a firmware file (dvb-usb-wt220u-2.fw) from my home directory to /lib/firmware/2.6.20-15-generic. In the terminal i have changed the working directory to the destination and issued the command :-

sudo cp /home/dvb-usb-wt220u-2.fw.

-and I get the message " missing destination file operand after `/home/dvb-usb-wt220u-2.fw."

What am I doing wrong ? I know that this should be pretty basic and I thought I had followed the example quoted in the thread[/COLOR]    [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners).

---

### Post by taurus on 2007-05-18
You missed a space before the last dot.  Otherwise, include the whole path.

```
sudo cp /home/dvb-usb-wt220u-2.fw  /lib/firmware/2.6.20-15-generic
```

---

### Post by freebeer on 2007-05-18
You're just missing the destination portion of the command.  

try:

```


sudo cp /home/dvb-usb-wt220u-2.fw /lib/firmware/2.6.20-15-generic


```

sudo grants you "superuser" rights, so that you can write to the destination folder, cp is the copy command, /home/dvb.... is the source file and /lib/firm.... is the destination folder.

HTH

---

### Post by linuxnooby on 2007-05-18
Thanks, guys but I had already tried those commands (and have just copied/pasted to try again) and got the following error message :-

cannot stat `/home/dvb-usb-wt220u-2.fw': No such file or directory

I can assure you that the source file does exist - in fact I have tried copying other files from /home, with the same resulting error message.

Most strange !

---

### Post by taurus on 2007-05-18
Is it in your $HOME (/home/username) or /home?

```
ls -la ~
-or-
find /home -name dvb-usb-wt220u-2.fw -print
```

---

### Post by shen-an-doah on 2007-05-18
It needs to be /home/<your username>/dvb-usb-wt220u-2.fw

/home is where the folders for your user accounts are stored. So all my files are in /home/andy.

---

### Post by linuxnooby on 2007-05-19
If I click on PLACES and select HOME FOLDER, then enter the terminal and enter PWD the output I get is :-

brian@brian-desktop:/home$ 

I would have thought that from that location I would only need to issue the command:

 sudo cp dvb-usb-wt220u-2.fw /lib/firmware/2.6.20-15-generic

ie , ignoring the full path of source - Maybe I have become too entrenched in Msdos:lolflag:[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

Can't understand why my home folder shows-up in a different format from yours and I still have not managed to copy the file. Is there any way to obtain owner rights to enable me to copy/paste ?

---

### Post by linuxnooby on 2007-05-19
The penny has finally dropped ! Iv'e been missiing-out my username from the path - Doh !

---

