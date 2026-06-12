---
title: "command line/ script questions"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by nikku_neko on 2006-08-05
i've begun trying to use the command line reguarly, and i also am delving into writing little scipts.  all is well, but i have two silly questions:


1.  when i want to eject a removable drive (i.e. flash drive, external hd, etc), should i use **umount** [whichever file extension] (in my case, /media/usbdisk) or another command?

2.  i wrote a silly script that pipes **iwilist** scan into a **grep** and then a word count so that it will display the number of various types of wireless networks nearby.

an example of a line (please don't laugh):

**echo there are `iwlist eth1 scan | grep 802.11a | wc -l` wireless a networks available.**

this works perfectly on my desktop, but when i took the script over to the laptop, i found out that the iwlist scan command on here does not display the wireless type (a,b,g,etc) and the grep->wc output is zero for each printed statement.

does anyone know a way to make the command display the network type?
i feel so silly, but i'd like to know.


thanks,


nick

---

### Post by Tomosaur on 2006-08-05
What is the actual output of 'iwlist eth1 scan'?

---

### Post by nikku_neko on 2006-08-05
on my laptop, it gives me this output:

neko@neko-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:03:63:36
                    ESSID:"garciahome"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:49/153  Noise level:7/153
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

on my desktop, there is an additional line, "protocol", which displays IEEE 802.11 type, upon which mr. grep relied for his list output

---

### Post by kerry_s on 2006-08-05
Since your just getting into writing scripts, i thought you might want to know about nautilus-scripts. Nautilus-scripts is a little hidden feature of nautilus. It's a folder where you can put your scripts and access them through the right click menu. A very handy feature when you don't need a launcher.My pic->[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13840&d=1154770753[/IMG]

---

### Post by nikku_neko on 2006-08-05
> **kerry_s said:**
> Since your just getting into writing scripts, i thought you might want to know about nautilus-scripts. Nautilus-scripts is a little hidden feature of nautilus. It's a folder where you can put your scripts and access them through the right click menu. A very handy feature when you don't need a launcher. 


wonderful,  thank you for the tidbit.  i'll try that next time i'm perusing my files.:)

---

### Post by kerry_s on 2006-08-05
I also forgot there are lots people who share the scripts they made, you can google(nautilus-scripts) for them, then just select the ones you want and copy them to the nautilus-scripts folder(make sure you hit reload so they show up). I sometimes like to look at the scripts other people make,you will see alot of different styles for scripts. example: i noticed just to launch a terminal they'll have like 3 lines of code, where i on the other hand just opened a text document typed> exec gnome-terminal < saved, then made it executable by right clicking and changing the permission to execute, that's it. woops rambling, Take care

---

### Post by Tomosaur on 2006-08-05
> **nikku_neko said:**
> on my laptop, it gives me this output:

neko@neko-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:03:63:36
                    ESSID:"garciahome"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:49/153  Noise level:7/153
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

on my desktop, there is an additional line, "protocol", which displays IEEE 802.11 type, upon which mr. grep relied for his list output

Unfortunately it looks like you're just going to have to re-write your script. It's fairly common that this kind of thing happens - different machines see different hardware in different ways. Your new grep search expression should probably be 'Cell', since it looks like that is how iwlist reports wireless connections on your laptop.

---

### Post by nikku_neko on 2006-08-05
thank you for the help, tomosaur.  

actually, the first code line did have a '**grep Cell** line

**echo There are `iwlist eth1 scan | grep Cell | wc -l` wireless networks in range.**

and then the details:

**echo There are `iwlist scan | grep 802.11a |wc -l` wireless a networks in range.**
**echo There are**... 
...etc, etc

scripts are fun!  i hope to learn more.  is there a good place to learn more of the basics on this subject?

also, does anyone have an answer to my **umount** question?

thanks,



nick

---

