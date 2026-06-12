---
title: "Networking Ubuntu with Windows XP"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-04-22
I've already posted once in this section but I feel I need to make another in order to have somebody explain the following guide to me:  [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) .  I've followed the directions all the way to the end but I'm getting confused on one point.  On XP, I've created a home network title MSHOME.  The guide asks me to add the following line to my fstab file:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpassword,gid=GIDFromAbove 0 0

What do I put for the servername and the sharename?  Is that just my windows id?  Is the server name just MSHOME?  

I am obviously very new to Linux, so please be very detailed in any answers.

Thank you,

Helixed

---

### Post by jiminycricket on 2007-04-22
servername  = what your windows computer is called, eg., find out from going into System Properties - > computer name.  I think an IP address (one that starts with 192.168.*.*) from that windows computer also works.

Sharename = name of the folder you're trying to mount

Remember that you have to create the directory in that second column before mounting.  I think smbfs should also be changed to "cifs" instead.
You could also look at fusesmb if you want to browse all your shares on a local drive, there's a nice howto on the forums here: [http://grumpymole.blogspot.com/2006/12/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/12/xubuntu-browsing-samba-shares-with.html)

---

### Post by RobsterUK on 2007-04-22
> **helixed said:**
> 

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpassword,gid=GIDFromAbove 0 0



servername - the name of the windows PC which has the share

sharename - the name you gave the share on the windows PC when you shared the folder/drive

mountdirectory - the name of the folder on your ubuntu machine where you want the files to appear. As the tutorial says, whatever name you pick here you need to create a folder with that name

if thats still unclear, post back

---

### Post by helixed on 2007-04-22
I couldn't get it to work.  I tried editing the fstab file through the graphic interface, but it wouldn't give me permission, so I went into the command line and typed:

sudo nano -w /etc/fstab/

I added the following line to the end of the file:

//helixed-port/c://Documents and Settings/All Users/Documents/My Documents/ /home/helixed/test share/ smbfs credentials=/home/helixed/.smbpassword,gid=GIDFromAbove 0 0

I then followed the rest of the directions in the guide until I completed it.  When I restarted the computer I lost my graphical interface, and I had to go back through the console and reedit the text file.  Am I way off on what I was supposed to do here?  Is this guide even what I'm looking for in order to accomplish what I'm trying to do?

Thanks,

Helixed

---

### Post by RobsterUK on 2007-04-22
> **helixed said:**
> 

//helixed-port/c://Documents and Settings/All Users/Documents/My Documents/ /home/helixed/test share/ smbfs credentials=/home/helixed/.smbpassword,gid=GIDFromAbove 0 0



What you have done there, is instead of the name of the network share you've typed in the path of the folder on the windows machine, which will mean nothing to Ubuntu. It looks like you are trying to share your my documents folder. If you go to your windows computer, right click on your my documents folder and select sharing, you will be able to see what name it has for the purposes of sharing. That's what you need to type in place of sharename mentioned earlier

apart from that you are getting there

---

### Post by helixed on 2007-04-22
I tried adding the following line to fstab:

//helixed-port/My Documents/ /home/helixed/test share/ smbfs credentials=/home/helixed/.smbpassword,gid=GIDFromAbove 0 0

When I restarted the computer X Server refused to start again, so I had to go back into command line and reedit fstab.  Any ideas of why this is happening?

Thanks,

Helixed

---

### Post by helixed on 2007-04-23
bump

---

### Post by jiminycricket on 2007-04-23
Hmmm..I don't know enough about mounting smb file systems.  Maybe Python-SMBmount can help generate one, just read that page and substitute the IP address of the target computer for "192.168.0.1" (the example they gave)

[http://www.gnomefiles.org/app.php/python-smbmount](http://www.gnomefiles.org/app.php/python-smbmount)

PyNeighborhood is another one that generates them: [http://www.gnomefiles.org/app.php/pyNeighborhood](http://www.gnomefiles.org/app.php/pyNeighborhood)

---

### Post by Helmi on 2007-04-24
@helixed: You shouldn't use spaces in your shares - if you have to use \040 to escape them in fstab.
```

//helixed-port/My\040Documents/ /home/helixed/test_share/ smbfs credentials=/home/helixed/.smbpassword,gid=1000,uid=1000 0 0
```

you also noticed i changed the local dir to a _ underscore instead of the space and the gid/uid-part as it would probably look better ;)

On unix based operating systems it's most of time better if you only user lower case, no spaces no special chars in dir names. it's less error productive.

---

