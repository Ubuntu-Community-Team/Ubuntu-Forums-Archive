---
title: "Looking for FTP file send program"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Cz-David on 2008-04-20
I'am used to FTP plugin from miranda-im and I use it a >LOT< until ubuntu. So... Is there any simple enought one-purpose program where i can select a file and it'll give me direct link to a predefined ftp server and uploaded file... :confused:

---

### Post by lemuriaX on 2008-04-20
Filezilla works well for basic FTP
could also try gFTP or the FireFTP addon for Firefox

---

### Post by Cz-David on 2008-04-20
I know these but this is not exactly what i'am looking for... i'am looking for really simple app...
1) start - select file
2) upload
3) copy link into clipboard or show link
aka let's learn python and build it myself :D but if there was anything

---

### Post by lemuriaX on 2008-04-20
Hmmm...okay i have to confess I don't know anything about Miranda. I did look at the page for it a Wikipedia and read this: "There are no plans for an official Linux edition[3], but the windows version was reported to work well in Linux with the Wine compatibility layer.[4]"

Maybe could try running it in Wine, I'm not experienced with Wine either but many of the folks here at the forums are.

---

### Post by Cz-David on 2008-04-20
then again :) thanks for your trying but if i wanted to run miranda under wine i would ... of course i have a perfect miranda plugins in windows but in linux i'am getting used to not using them... but that simple ftp plugin i miss ... iam sending a lot of files to a lot of people who are not online and moving files manually and then writing link and then testing link it's real timewaster...

---

### Post by lemuriaX on 2008-04-20
ok just checking to see if you'd considered Wine
sorry I can't be of more help - perhaps someone else here knows if such an app exists already
it does seem to be quite simple, maybe you could use a command line script to accomplish this

good luck!

---

### Post by Fedz on 2008-04-20
Can't you just get a domain/hosting eg: [One.com](http://one.com) and use that - you couldn't get it any easier in all honesty :)

---

### Post by Cz-David on 2008-04-20
i have extremely slow php script on w w w.skoron.ic.cz/ which i use for out of home purposes but i realy need something fast and simple ...

---

### Post by scorp123 on 2008-04-20
> **Cz-David said:**
> I'am used to FTP plugin from miranda-im and I use it a >LOT< until ubuntu. So... Is there any simple enought one-purpose program where i can select a file and it'll give me direct link to a predefined ftp server and uploaded file... :confused: Why not use Nautilus ... that's GNOME's file manager.

Go to your menu bar:

**Places > Connect to Server >** ... and a new window should have opened ...

Now fill in the details. e.g. If the server you want to connect to requires a login then select e.g.:

Service type: **FTP with Login**
Server: IP address or the remote **hostname**
Port: (can be left alone unless you have to use a non-standard port for FTP)
Folder: Location on the remote file system, e.g.  **/home/myremoteaccount/data/whatever**
User Name: your **remote login** name
Name to use for connection: The name the icon will have on your desktop, e.g. **"MyFTP"**

Click onto the **"Connect"** button.

Now you should have an icon on your desktop that is called **"MyFTP"** (following my example above). So you can now just open that remote location as if it were a local folder and transfer files via drag & drop.

---

### Post by Cz-David on 2008-04-20
That's actually very good idea thanks ... now how to easily extract link to the file from that

---

### Post by scorp123 on 2008-04-20
> **Cz-David said:**
>  ... now how to easily extract link to the file from that Sorry, I didn't understand that part.

---

### Post by Cz-David on 2008-04-20
oukey ... let's say i put some file in [www.skoron.ic.cz/randomdir/](www.skoron.ic.cz/randomdir/) file named 123.test ... and then i want adress [www.skoron.ic.cz/randomdir/123.test](www.skoron.ic.cz/randomdir/123.test) copied in my clipboard or shown for copy

---

