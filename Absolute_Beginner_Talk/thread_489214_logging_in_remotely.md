---
title: "logging in remotely?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-07-01
So I will be away from home for a week. I need access to my computer from where I will be.

How do I set this up?

I know there are risks involved, they are worth it to me.

I have serached the forums to no avail... not sure what it is called so I do not find threads that will help me.

I have ot have this set up and over the next 2 days.

Thanks

robi

---

### Post by PhatBoy on 2007-07-01
Will just terminal access and access to files do or do you want to be able to see the gui?

For the former the package you need is openssh-server for the later it is vncserver.

---

### Post by Raineer on 2007-07-01
ssh works wonderfully for me, I had some difficulties getting VNC working (seems to want to always pop up a msg on my linux box asking if it's ok to allow me.......remotely) lol

All it did was make me look for more command-line based apps, and it's very surprising how many are out there.

---

### Post by bsawler on 2007-07-01
Robi,

I am a true beginner at Linux, so everything is a real issue for me, unless everything is explicitly spelled out, I am lost.  With that said, I got remote connection working with relatively ease.  It took me awhile until I found this website from one of the threads:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

I followed this with Fiesty 7.04, and it works well.  The only hitch I had was in step 4, I could not find my way around this command sudo vi /etc/xinetd.d/Xvnc  so I used 

```
sudo gedit /etc/xinetd.d/Xvnc
``` 

and it worked fine.

Once completed I could connect, to VNC but when I tried entering my username and password, it would not work, cause I missed a point (not a step) in the site where you go to your Login and disable the multiple connections. 

There is alot of text, but really there is only a few steps, very quick.  

My issue now is, that I want to be able to 'see' the current 'screen' that is loaded when I remote connection. (Same as connecting to a Windows machine) cause I need to connect to the Linux machine and explain on the phone what I am doing and the other person can see.  I'm sure this is an easy one, but haven't figured it out yet. 

Cheers,
Bradley

---

### Post by Scorpuk on 2007-07-01
> **bsawler said:**
> 
My issue now is, that I want to be able to 'see' the current 'screen' that is loaded when I remote connection. (Same as connecting to a Windows machine) cause I need to connect to the Linux machine and explain on the phone what I am doing and the other person can see.  I'm sure this is an easy one, but haven't figured it out yet. 



Goto :

System -> Prefereces -> Remote Desktop


check : Allow other users to view your desktop

uncheck : Ask you for confirmation

check : Require the user to enter this password

Then type in a password


Now click close


With vncviewer goto the ip address of your linux box like this:

192.168.1.1:0

or with the internet IP address, but you may need to forward some ports. This I am not sure as I keep my linux box in the DMZ (All ports open)


Hope this helps.

---

### Post by beanco on 2007-07-02
thanks everybody, I too am a newbie and confused if things are not spelled out clearly.

I will look at those links.


I am stil lon dapper for what it's worth... and not sure if I will have time to install feisty before I leave...


the ppl i will be staying with all are still MS slaves.... 

I really need access to my files and to my bookmarks... so i suppose the book mark access will mean i need gui....


now for the really embarassing, bnoob quesiton... my computer at home has to be on, right> I mean will I have to leave it on the whole tim eI am gone or is there some way to remotley boot her up?

robi

---

### Post by eternalsword on 2007-07-02
typically you'll have to leave it on.  If you had a customized setup with more powerful power management, you could set it up so that you could send power up signals remotely, but in your case, yes you'll have to leave it on.  If for some reason your power goes out, well, you'll be left without a connection I'm afraid.  as far as I know, you must also be currently logged in for the remote desktop to work correctly.

---

### Post by PhatBoy on 2007-07-03
Just a suggestion but you could use [ http://del.icio.us]("http://del.icio.us") or similar to allow you to access your bookmarks. You could then do without the gui and access files via ssh.
[http://en.wikipedia.org/wiki/Ssh]("http://en.wikipedia.org/wiki/Ssh")

Another thing you may need to looking into is port forwarding and firewall rules for your router otherwise an attempt to connect from the Internet will not even get as far as your machine.
[URL="http://en.wikipedia.org/wiki/Port_forwarding"]
http://en.wikipedia.org/wiki/Port_forwarding[/URL]

---

### Post by bodhi.zazen on 2007-07-03
This is a very cool solution :

[http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by pbaumgar on 2007-07-03
If you just need shell access, you need to have sshd runnning (ssh daemon).  On your router you'll need to have it forward traffic on port 22 to the IP address of your linux box.  Most likely you can change the external port to connect to from 22 to something like 8853 or something.  Just don't use a port that is already in use or a well know port.  Here's a list of common ones:  [http://www.governmentsecurity.org/articles/CommonPorts.php](http://www.governmentsecurity.org/articles/CommonPorts.php)

I assume you have an external static IP?  If so, you would just ssh to your external IP/Port number and your router will direct your linux box on port 22.  If you'll be accessing your linux machine from a windows box, you can use a program like Putty ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) to open a shell on your linux box.

---

