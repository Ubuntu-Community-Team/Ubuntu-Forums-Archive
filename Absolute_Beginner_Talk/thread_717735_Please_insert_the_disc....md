---
title: "Please insert the disc..."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Aleks67 on 2008-03-07
Hi -

I have access to a remote server running Ubuntu.  I am using Putty on my windows machine as the SSH client.

I want to use a GUI and have run the command:

sudo aptitude install ubuntu-desktop

It works ok until a message appears:

Please insert the disc labeled 'Ubuntu-Server 6.06.1 Dapper Drake - Release i386 (20060807.1)' in the drive '/cdrom/' and press enter

Obviously I can't do that because this is a remote server. Is there a way round the problem?

Thank you.

---

### Post by taurus on 2008-03-07
Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and put a # in front of the first line, cdrom, to comment it out.  Then, make sure there is no # in front of all the lines that start with **deb** & **deb-src**.  Save it with <Ctrl>o and exit with <Ctrl>x.  

Now run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Hospadar on 2008-03-07
You can also just go to System->Administration->Software Sources and uncheck the cd on the first tab

---

### Post by taurus on 2008-03-07
> **Hospadar said:**
> You can also just go to System->Administration->Software Sources and uncheck the cd on the first tab

1.  He is running a server.

2.  He connects to his server with ssh.

---

### Post by seventhc on 2008-03-07
@ taurus: I was just curious..what is that -Bw for, is that only b/c it's a server or what does it do...I've never seen it before so was curious. :)
Thanks

---

### Post by taurus on 2008-03-07
B tells nano to make a copy of the file first and w is so that a long line won't be break into the next line.

---

### Post by Dr Small on 2008-03-07
I read this from the nano man page:
>  -B (--backup)
              When  saving  a  file, back up the previous version of it to the
              current filename suffixed with a ~.
 -w (--nowrap)
              Disable wrapping of long lines.


---

### Post by Aleks67 on 2008-03-07
Thank you taurus. It seemed to work, how do I now bring up the desktop with my SSH client Putty or DataFreeway?

Thank you.

---

### Post by seventhc on 2008-03-09
Thanks for the explanation, I didn't realize it was specific for nano. :)
@Aleks67 once you ssh in, try the command ```
startx
```

---

