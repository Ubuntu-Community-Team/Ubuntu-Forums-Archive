---
title: "I dont have permission to my own folder"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by snikkar on 2007-10-27
Hi,

im a noob to linux. 

I want to copy some files from one folder to another but it says that im not the owner. Root is the owner. Who is that? How can I fix it?

---

### Post by stomponthis on 2007-10-27
Root is like the Administrator account.  You can change the permissions in the terminal by:
Applicaions - Accessories - Terminal

Then type in 

```
sudo chmod 777 filename
```

NOTE: 777 will give read,write and execute permissions to anyone for the file.  And you need to be in the directory with the file in it. 
Hope that helps :-)

---

### Post by philinux on 2007-10-27
Open a terminal and type gksudo nautilus. This gives you a root (ie full admin rights file browser) which you can then use to copy and paste anything.

Be careful though.

---

### Post by proalan on 2007-10-27
what is it your trying to copy? 

The permission system is there for your own good to prevent breaking the system.

chmod 777 works of course but is bad practice as will grant read,write,executable access of the file to anyone (owner,group,others)

chown changes the ownership of the file

---

### Post by snikkar on 2007-10-27
Im trying to copy files to install open ttd. (transport tycoon deluxe)
Need to copy the files into this folder /usr/share/games/openttd .
I think think im copying the graphics files to this folder. For some reason you cant download a fully complete open ttd game. So I have to use files from the windows open ttd.

---

### Post by snikkar on 2007-10-27
isnt it possible to just log in as root and copy the files and log out again. I dont want to crash my system doing something I have no clues about. Im afraid to use the sudo function. :)

---

### Post by proalan on 2007-10-27
It should be alright if you know what you are doing

typing 'gksudo nautilus' in a terminal is easiest way to do it if your not comfortable with using the terminal.

/usr/share/games/

is just the location of where the games are kept so that every user has access to the common games directory. 

I'm not familiar with 'ttd' but unless it says explicitly in the 'readme' instructions i see no reason why you couldn't just put it in your home folder.

---

### Post by snikkar on 2007-10-27
will gksudo nautilus make my computer "open" forever, or can I change it back? Or will it change back when I restart?

---

### Post by snikkar on 2007-10-27
btw

I did this in terminal  sudo chmod 777 /usr/share/games/openttd

Nothing happened

---

### Post by proalan on 2007-10-27
> **snikkar said:**
> will gksudo nautilus make my computer "open" forever, or can I change it back? Or will it change back when I restart?

no you only have access to root privileges until you close the nautilus window.

>  I did this in terminal  sudo chmod 777 /usr/share/games/openttd

Your not copying anything in this command, your only changing privileges to the directory.

you want the command
```
sudo cp 'current_location_of_ttd' /usr/share/games/openttd
``` 
where current_location_of_ttd is the location of the files you want to copy from.

---

### Post by steve.horsley on 2007-10-27
gksudo nautilus will open a nautllus file manager that has root priviledge - the power to read and write anywhere. That power ramains with that window (and any other windows it creates with File->Open New Window) until it is closed. The rest of your windows do not get elevated power. 

An equivalent soe the command line is to put the word sudo in front of any command that you want to run with extra priviledge. think of sudo as SuperUserDO, and gksudo as GraphicalSuperUserDO.

P.S.
Logging in as root is a terrible idea - it is a bad security risk. Don't even try.
And changing permissions of files and directories outside your home is an even worse idea. It can lead to having to do a complete re-install.

---

### Post by markharding557 on 2007-10-27
If you prefer a gui you can set permissions in the properties tab by right clicking on a file in  nautilus.
you need run it as root of course

---

### Post by stomponthis on 2007-10-27
> **proalan said:**
> The permission system is there for your own good to prevent breaking the system.

chmod 777 works of course but is bad practice as will grant read,write,executable access of the file to anyone (owner,group,others)

Yeah I know... bad practice!

---

### Post by Crafty Kisses on 2007-10-27
> **snikkar said:**
> Hi,

im a noob to linux. 

I want to copy some files from one folder to another but it says that im not the owner. Root is the owner. Who is that? How can I fix it?
Do the following command to gain root:
```
sudo -i
```

---

