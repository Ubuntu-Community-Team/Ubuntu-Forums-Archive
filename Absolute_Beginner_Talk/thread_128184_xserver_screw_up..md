---
title: "xserver screw up."
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-02-10
i was fooling around in the kde login setup screen and messed up xserver tab.  i think i put it on chooser and now when i boot up i get a message "cannot find host" and get an option to add a host.  i'm using the live cd to post this.  can i fix this from the live cd???????
please help.  i finally have my system perfect and don't want to start from a new install.
thanks,
rich

---

### Post by Mustard on 2006-02-10
Whats the contents of your /etc/hosts file?

```
cat /etc/hosts
```

---

### Post by Malac on 2006-05-30
I've just done exactly the same thing except with the GDM login screen.
Chose "Chooser" now it's asking me to add a hostname.
I can't login at all so can't access files to change them.
Even boot in "Safe Mode" does this.
Is there a particular syntax for the hostname this form expects.
I've tried the I.P. for my machine and the localhost name.
Does it need any (back/forward) slashes or anything an example would be cool.
Help Me please I don't want to do a full re-install. I've only just got my ADSL USB Modem working.

Thanks in advance.

---

### Post by shutupimpoor on 2006-05-30
is it the failed to start x server your graphical interface?

in that case I just reset the config: 

```
 sudo dpkg-reconfigure xserver-xorg 
```
I hope this helps, I'm an ubuntu newb, but I think thats a way to fix it. is the screen all blue with random characters every where? thats when i use this

---

### Post by Malac on 2006-05-30
Found another thread about a similar problem and so thought I would pass it on.

When you get to window asking for host, keep Ctrl-Alt-Backspacing until XServer crashes and says that it won't restart until the problem is fixed. (Just "OK" through all the prompts.)

Then :
Do login and password.

Then :
```
sudo nano /etc/gdm/gdm.conf
```  Enter password.
Scroll all the way to the bottom and you should see a line saying ```
chooser=true
``` Change this to ```
chooser=false
``` 
And press Ctrl-O to Write the file hit enter and Ctrl-Z to finish. (Takes me back to my DOS "edlin" days).

Then ```
startx
``` 
It went a bit (graphically)strange at this point but eventually I got in to my Ubuntu Desktop where I could use the "System->Administration->Login Window" applet to change it all back to defaults.

Hope this helps.

---

