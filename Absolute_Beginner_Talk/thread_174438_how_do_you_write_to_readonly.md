---
title: "how do you write to readonly"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by the_guy1 on 2006-05-11
I was going to write a coustom change to the /etc/apt/sources.list file and the computer wouldent let me write to the file how can I write to the file and the others that are locked in the filesystem

---

### Post by johnc4510 on 2006-05-11
sudo gedit (then the path to the file)
Enter password
BE VERY CAREFUL, NOT RECOMMENDED IF YOU DON'T KNOW WHAT'S GOING ON.
Sorry, Not screaming, just trying to get your attention

---

### Post by ZiLOG_Z80 on 2006-05-11
you need to have super user privilages (use the command *sudo*) to write to the file. if you are using ubuntu breezy I'm sure you can use gedit```
sudo gedit /etc/apt/sources.list
``` if you dont have gedit try substitute it for another text editor eg nano

---

### Post by ComplexNumber on 2006-05-11
[quote=johnc4510]sudo gedit (then the path to the file)
Enter password
BE VERY CAREFUL, NOT RECOMMENDED IF YOU DON'T KNOW WHAT'S GOING ON.
Sorry, Not screaming, just trying to get your attention[/quote] yes, i agree about the highlighted  bit. it is better to put 'gksudo nautilus' because this allows the user to have more control.


oh, and one more thing. MAKE A BACKUP COPY TO ANYTHING THAT YOU DECIDE TO CHANGE IN THE /etc DIRECTORY. similarly, i'm not screeming, but such advice neds to be highlighted unless you want to risk leaving your system unusable :).

---

### Post by Clay85 on 2006-05-11
If you want to change the permission to the file I think you can type this in your terminal 
```
 sudo chmod -R 777 Folder/File_Name
```

The -R makes it recurrent, so you can tackle a whole bunch of files. You may not need that. But if I remember correctly it allows you to read, write, and execute the files. I'm new to ubuntu so I'm probably not one to take advice from (especially when using SUDO).

I thought I had to do that to a whole bunch of my files, but it turns out those weren't the right files. They were protected for a reason. >_< haha! Just make sure you know what you're doing.

---

### Post by catlett on 2006-05-11
Just to clarify a bit. Gedit is a text application. It opens a blank text page or opens a text file you specify.
That is what they are telling you to do. Open the file /etc/apt/sources.list in gedit and edit it. But because of the way linux runs security in the system you can't change anything outside of your home folder as a user.
To change things you have to be a "superuser". You become a superuser by entering the term "sudo" before a command. This invokes your superuser status. It will ask for your user password (the one you log on with) and then it will open the text. Once you use sudo you can change the sources.list file.
 THE OTHER THING THEY ARE SAYING IS, BE CAREFUL. YOU NOW HAVE THE POWER TO DO ANYTHING. INCLUDING ERASING THAT WHOLE FILE.
Anytime you run a command and some kind of permission error comes up or a cannot open error, that is usually a sign you need to enter sudo before the command. Good luckl.

---

### Post by aysiu on 2006-05-11
*chmod*ing or *chown*ing a file in the /etc directory is a really bad idea. As people have said before, back up any system files first before editing them: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
``` [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by DSn0wMan on 2006-05-12
[QUOTE=Clay85]If you want to change the permission to the file I think you can type this in your terminal 
```
 sudo chmod -r 777 Folder/File_Name
```
[/QUOTE]

For security reasons I would avoid granting full permissions (777) to this file. sudo will work just fine.

---

