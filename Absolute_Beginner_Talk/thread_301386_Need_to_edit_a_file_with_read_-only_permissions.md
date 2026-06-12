---
title: "Need to edit a file with read -only permissions"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-11-17
Even as root, the file is set to read only. I don't know how it switched to this.

I was trying to create a Reboot/Shutdown button for my XGL session. I tried to edit my /etc/sudoers file.

[[IMG]http://img88.imageshack.us/img88/2779/screenshotsudoersproperbh5.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshotsudoersproperbh5.png)

Also, I see this error in terminal...
(yelp:4983): Yelp-WARNING **: Cannot find dbus bus

---

### Post by bodhi.zazen on 2006-11-17
```
visudo
```

BE CAREFULL !!

---

### Post by Bachstelze on 2006-11-17
root can edit anything, even files CHMODed to 000, given that they're on a writable filesystem of course. How are you trying to edit the file ?

---

### Post by jaboua on 2006-11-17
```
sudo visudo
```

---

### Post by bodhi.zazen on 2006-11-17
> **HymnToLife said:**
> root can edit anything, even files CHMODed to 000, given that they're on a writable filesystem of course. How are you trying to edit the file ?

Not always.

And not sudoers.

---

### Post by bodhi.zazen on 2006-11-17
> **jaboua said:**
> ```
sudo visudo
```

No sudo

---

### Post by bodhi.zazen on 2006-11-17
Do you know how to vi ?

If not, hit "i" to edit.

Move with arrow keys.

Esc to exit edit mode, shift : to enter command mode

w to write

wq to write and exit

q! to exit without saving changes.

---

### Post by Charco on 2006-11-17
I'm trying to add this to the end:

charco localhost= NOPASSWD: /sbin/shutdown -h 0
charco localhost= NOPASSWD: /sbin/reboot

So that my Shutdown/Reboot shortcut will work without me having to enter a password (I lost those buttons because I installed Beryl on a separate XGL session).

 I'm using this
```

  #!/bin/sh

action=`zenity --list \
          --title="Reboot or Shut Down?" \
	  --text="Please select one or 'Cancel' to Exit"\
          --radiolist \
          --column="Select" \
          --column="Action" \
            True Reboot \
            FALSE Shutdown `
           
      if [ $action = "Reboot" ]
then
        exec `sudo /sbin/reboot`

elif [ $action = "Shutdown" ]
then
      exec `sudo shutdown -h now`

fi

```

And get this error when I run the launcher.
[[IMG]http://img136.imageshack.us/img136/9992/screenshotcannotlaunchafc1.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotcannotlaunchafc1.png)

---

### Post by bodhi.zazen on 2006-11-17
%admin ALL=(root) NOPASSWD: /sbin/reboot 
%admin ALL=(root) NOPASSWD: /sbin/halt 
%admin ALL=(root) NOPASSWD: /sbin/shutdown 

%admin is the group with shutdown powers. You can change this to %users or what have you.

---

### Post by Charco on 2006-11-17
You guys are amazing! Thanks!

---

### Post by anaconda on 2006-11-17
I dont use visudo.. 

It is easy to understand that any sudoer cant modify the sudoers file. Only root can.
That is why I use 
```
sudo su
```
to really became root -user. Then you can edit also those files. 
When you use just sudo you still are the same user, but you have root rights for the next command.

---

### Post by bodhi.zazen on 2006-11-17
> **anaconda said:**
> I dont use visudo.. 

It is easy to understand that any sudoer cant modify the sudoers file. Only root can.
That is why I use 
```
sudo su
```
to really became root -user. Then you can edit also those files. 
When you use just sudo you still are the same user, but you have root rights for the next command.

Like OMG, you're right :shock: . I always thought visudo was hardwired into the OS to protect sudoers file from random ignorance ;).

I can even sudo vi /etc/sudoers

Thank you anaconda for the tip :p

---

