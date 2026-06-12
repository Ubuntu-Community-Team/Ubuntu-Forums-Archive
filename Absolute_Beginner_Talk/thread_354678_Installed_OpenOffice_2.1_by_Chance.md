---
title: "Installed OpenOffice 2.1 by Chance"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-02-06
Hello.
I installed openoffice 2.1 by using this [link]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml").

However, after doing all that it told me to do, I still didnt see it in my office submenu in the applications drop down menu though i guess it did got installed. Searched the forums and looked at some results and installed the debian menu. Still it didnt even show up there :| .

Then from the folder where all the rpm to deb conversion took place, I happened to click a certain .deb file guess it was some form of a debian package file. That opened up the package manager and it asked me if id like to install the software which i granted the permission and now i see it in the applications menu. So can someone generalise what exactly is the meaning of converting from RPM to Debian and why if at all is this neccesary for ubuntu?(looks like it is in 'most' cases :) ).

Additionally, looking at others having the similar problems, i thought of installing the automatix tool but how do i use that tool to check which are the currently installed softwares as all it shows is a list (categorized) of software which can be installed by a single click...

Hope to hear from  you,

Aijaz.

---

### Post by keithpeter on 2007-02-06
Hello aijazbaig1

I think something must have gone wrong with the last command, the 

```
sudo dpkg -i *deb ~/OOE680_m6_native_packed-1_en-US.9095/RPMS/desktop-integration/openoffice.org-debian-menus_2.1-5_all.deb
```

command. That is the one that should install the software from the .deb files once you have them. When you double clicked on a .deb file, the graphical installer started up and took over.

To answer the second question, I'm no expert, but there appear to be several ways of 'packaging' software as binary files. The Alien software converts the Fedora Core/Red Hat style RPMs to Debian style .deb files. OpenOffice probably want to issue their work in just one format to save resources.

Now, *my* problem is that once I install OpenOffice this way on Xubuntu running under Dapper 6.06, every time I try to install more software, or run an update, the aptitude system uninstalls half of OpenOffice and I have to install it again. 

Does anyone know how to 'pin' the OpenOffice packages so they just stay put? Or how to tell aptitude to just ignore them?

Cheers

---

### Post by aijazbaig1 on 2007-02-07
Hello,
Now it seems that though I see those icons under my office sub category, they dont seem to respond even after i try to open them..
is it that the binaries that im tryin to click into are not responding...??

---

### Post by keithpeter on 2007-02-08
Hello

I am no expert on this at all, but, did you uninstall the version of OpenOffice that comes in the repositories before installing OpenOffice from the debs? (Assuming you installed Ubuntu or Kubuntu)

---

### Post by aijazbaig1 on 2007-02-08
Hello.
Thnks for replying...I got the whole thing working due to the following excellent [advice]("http://bodmas.org/blog/?p=523").

The only thing it lacked was showing how does one go abt enabling universe and multiverse repos which I found from [here]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list").

After that, it seems to be working fine and so is the desktop integration,

Now I know how its done and im gonna help any other ubuntu newbie to fix this :).

---

### Post by Mike Daniels on 2007-03-14
Absolute newbie here as well. I am following the advice on bodmasblog about upgrading OpenOffice 2.1 and need to know what I need to type to cd into the RPMS directory after downloading OpenOffice 2.1 from OpenOffice.

THanks in advance

Mike

---

### Post by Mike Daniels on 2007-03-14
Ok, Didn't start from bodmas post of 18th Feb. I have got to th epart where I have to type alien --keep-version *.rpm but this is what I get:

mike@mike-desktop:~/Desktop/OOE680_m6_native_packed-1_en-US.9095/RPMS$ alien --keep-version *.rpm
Must run as root to convert to deb format (or you may use fakeroot).

I don't know what to do next. I have got to root directory and entered again but get:

mike@mike-desktop:/root$ alien --keep-version *.rpm
Cannot write to current directory. Try moving to /tmp and re-running alien.
mike@mike-desktop:/root$ cd /
mike@mike-desktop:/$ sudo -i
Password:
root@mike-desktop:~# alien --keep-version *.rpm
File "*.rpm" not found.

Can anyone help, please?

Thanks

Mike

---

### Post by aijazbaig1 on 2007-03-14
Hi there dennis.

Good that u found that stuff useful.

However if u read that page carefully, it says that there is a directory within that subdirectory called RPMS.
U have to change ur current directory to that directory.

I suppose that u might have downloaded and extracted the openoffice dir on ur desktop..

then u just use a terminal to go to the RPMS directory inside the extracted directory..

Like in my case i downloaded that compressed file on the desktop and then extracted it on the desktop aswell..and renamed the extracted folder as Openoffice..(mind that linux is case sensitive so that Openoffice isnt the same as openoffice)

so once uve done that,

Just open a terminal and then do

```

cd /Desktop/Openoffice/RPMS

```

remember that page assumes u already have alien installed..if u dont u can get that using the following command ..do this before u use the alien command anywhere.

```

sudo apt-get install alien

```

After thats done u cud continue from step 9

Hope that would help,

Aijaz

---

### Post by aijazbaig1 on 2007-03-14
by root they mean that u shud be logged as the administrator...

which u can very easily do just by doing a ```
 sudo su
``` command after opening the terminal..


i guess it would be better for u to follow the instructions from the same post...they needed u to be the root because some of the things mentioned there..like doing the apt-get for the alien and other things like installing the open office package itself needs u to be the administrator ..

Did it help??

Aijaz

---

### Post by Michaelt74 on 2007-03-14
I followed this link and got it working fine.

[http://www.ossgeeks.co.uk/index.php?s=open+office](http://www.ossgeeks.co.uk/index.php?s=open+office)

---

### Post by Mike Daniels on 2007-03-15
Thanks for your he:guitar: lp guys. Thanks to the OSSGeeks advice I have now gor 2.1 up and running.

Thanks

Mike

---

