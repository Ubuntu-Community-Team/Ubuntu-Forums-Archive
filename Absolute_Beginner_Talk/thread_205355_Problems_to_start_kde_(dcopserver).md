---
title: "Problems to start kde (dcopserver)"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2006-06-28
Hi,

After changing  the state of "udev" on System Services (was in stop state and I set it YES to start at boot time) I started to have problems to login. 
When I put my username and password, the kde starting up fails in the firts stage, and after a timeout I get the following error:

[COLOR="Red"]"There was an error setting up interprocess communication for KDE. The message returned by the system connection was:
could not read network connection list.
/home/nhaddad/.DCOPServerInspiron6400__0

pls check that the "dcopserver" program is running. "[/COLOR]

I logged in in console mode and there is no file .DCOPServerInspiron6400__0, also I check and "dcopserver" is not running. if I start it as a root, it creates the files:
.DCOPserver_Inspiron6400__0  (-rw-r--r-- root root)
.DCOPserver_Inspiron6400_:0 which is a simbolic link to the above file and also belongs to roor:root
and finally 
.DCOPserver_Inspiron6400_NODISPLAY with the same permisions as above but belongs to nhaddad:nhaddad

Note: if I issue sudo startx from terminal mode, the kde starts fine, but I'm logged as root....

Any idea on how to solve this?

Thanks,
calvin

---

### Post by raffytaffy on 2006-06-28
youre lucky i read this..:)) i had this like a gazillion times on suse...ok heres what  u can do...go into failsafe term or as sudo under term with x off...and type this in:
sudo chown (user) ~/.ICEauthority
sudo chmod 777 ./.ICEauthority
^^those two change the ICEauthority permision..so u can remove it
next u can either restart "sudo /etc/initd/gdm restart"
if the problem persists..change persmission on ICEa agan and 
sudo rm ~/.ICEauthority and sudo rm ~./Xauthority ...then restart gdm

BTW this problem is caused by runing graphical KDE programs using sudo in gnome...thou there are other possibilities..the cause of d_cop server failing is the file ICEauthority and Xauthority change its permision to root only..and cant be read by user...thus d_cop cant initialize...the trick is to remove them both..restart

---

### Post by CalvinChile on 2006-06-28
Hi raffytaffy,

Thanks for the reply.  I tried it but still have the same problem. 
I guess that when you write  restart "sudo /etc/initd/gdm restart", you meant to say "sudo /etc/init_d/kdm restart" ?

If I remove both of them, and restart kde, I found them created with the following permissions:
-rw------- 1 nhaddad nhaddad 0 (date) (hr) .Xauthority
and .ICEauthority is not created !


any other idea?

Thanks
calvin

[QUOTE=raffytaffy]youre lucky i read this..:)) i had this like a gazillion times on suse...ok heres what  u can do...go into failsafe term or as sudo under term with x off...and type this in:
sudo chown (user) ~/.ICEauthority
sudo chmod 777 ./.ICEauthority
^^those two change the ICEauthority permision..so u can remove it
next u can either restart "sudo /etc/initd/gdm restart"
if the problem persists..change persmission on ICEa agan and 
sudo rm ~/.ICEauthority and sudo rm ~./Xauthority ...then restart gdm

BTW this problem is caused by runing graphical KDE programs using sudo in gnome...thou there are other possibilities..the cause of d_cop server failing is the file ICEauthority and Xauthority change its permision to root only..and cant be read by user...thus d_cop cant initialize...the trick is to remove them both..restart[/QUOTE]

---

### Post by raffytaffy on 2006-06-28
ow youre using kde...i had this issue under gnome..ok..u can try removing both from failsafe term...reboot puter and hope for best

---

### Post by CalvinChile on 2006-06-28
I create a new user, and if I login as the new user, everything is fine, I don't get any error on dcopserver.

Once I'm in the new sesion, I can see that dcopserver is running, which of course, is not the case for my normal account.

---

### Post by CalvinChile on 2006-06-28
OK, I think I solved it!!

comparing the .kde directories in my normal account and the new I created, I found that the directory socket-Inspiron6400 was owned by root instead of nhaddad. 
So I did:
sudo chown nhaddad:nhaddad socket-Inspiron6400  

after that, I could login in kde without problems!

---

### Post by vladdythephotogeek on 2006-07-10
> **CalvinChile said:**
> Hi,

After changing  the state of "udev" on System Services (was in stop state and I set it YES to start at boot time) I started to have problems to login. 
When I put my username and password, the kde starting up fails in the firts stage, and after a timeout I get the following error:

[COLOR="Red"]"There was an error setting up interprocess communication for KDE. The message returned by the system connection was:
could not read network connection list.
/home/nhaddad/.DCOPServerInspiron6400__0

pls check that the "dcopserver" program is running. "[/COLOR]

I logged in in console mode and there is no file .DCOPServerInspiron6400__0, also I check and "dcopserver" is not running. if I start it as a root, it creates the files:
.DCOPserver_Inspiron6400__0  (-rw-r--r-- root root)
.DCOPserver_Inspiron6400_:0 which is a simbolic link to the above file and also belongs to roor:root
and finally 
.DCOPserver_Inspiron6400_NODISPLAY with the same permisions as above but belongs to nhaddad:nhaddad

Note: if I issue sudo startx from terminal mode, the kde starts fine, but I'm logged as root....

Any idea on how to solve this?

Thanks,
calvin

Greetings!
I am having a very similar problem except that when I look at the /.kde folder it is owned by root and I can't access it and hence (I believe) KDE won't start. When I do try to log on to KDE it come back almost immediately and says "KDEconfigstartup can't be accessed" or something like it. 

So: How do I change permissions and ownership of the /.kde folder? I have tried without luck:

pjv@pjv-desktop:~$ sudo chown pjv /.kde
Password:
chown: cannot access `/.kde': No such file or directory

First: Is my context of the command correct? I'm really new at this but I would like to think I catch on quick.

I'm going to try to sudo startx from terminal and see if I can change to permission that way. I'll post my results.

sudo chown pjv /.kde but it returns



EDIT:

I was able to do a chown -R pjv ~/.kde in terminal and it (you guys no doubt know where this is going) and it changed ownership of all the files and folders in the /.kde folder to PJV instad of root and it works.

So... no help needed here. THanks for the thread though. :)

---

