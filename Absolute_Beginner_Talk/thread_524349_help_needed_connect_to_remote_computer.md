---
title: "help needed connect to remote computer"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-08-13
i just installed ubuntu in  a friends computer,

I would like to be able to control his computer just in case if he needs something, he is not good at all with computers so even if he calls me it would not do anygood....

 i tried to set up as much as possible, but i just could do much, especially with the  frostwire /java/azureus thing.....ive been reading a lot this last couple of days,, and honestly im exhausted,,,,


and i still to get the networking stuff in good shape (to share files) well...

  i can control my other computer using, vncviewer, but i just dont remember how i did it...
  
   can anybody help me at least providing some links.

  thank you

---

### Post by eentonig on 2007-08-13
Install an ssh server on his computer and test if you can connect via ssh locally.

> sudo apt-get install openssh-client openssh-server
(The client part is only needed to test the connection from his own pc. But you'll need it on your personal box.

Make sure (if applicable) that his router forwards the ssh requests to the correct LAN ip. Test this by using ssh externally to his public ip to see if you can still connect.

Install ddclient to get a reliable way of knowing his current public ip address.
> sudo apt-get install ddclient

---

### Post by MenZa on 2007-08-13
> **eentonig said:**
> Install an ssh server on his computer and test if you can connect via ssh locally.


(The client part is only needed to test the connection from his own pc. But you'll need it on your personal box.

Make sure (if applicable) that his router forwards the ssh requests to the correct LAN ip. Test this by using ssh externally to his public ip to see if you can still connect.

Install ddclient to get a reliable way of knowing his current public ip address.

While I agree that SSH is probably the best solution, you should know that SSH won't give you a graphical user interface (unless you forward X, which you probably don't want anyway). Just a little heads-up.

---

### Post by sysikon on 2007-08-13
Try using FreeNX, I used that for awhile. (Google it)

---

### Post by eentonig on 2007-08-13
If it is to manage a remote computer, I hardly ever need to fall back on a GUI. I learn the CLI commands I need to achieve something (basically, managing a remote PC will installing programs and configuring them. Both of which can easily be done on a CLI base.).

In the event that he does need a GUI, he can still (and I'll be more then happy to show how) forward vnc or even X over his ssh tunnel. But the at least it will be done safely. 

But my experience with VNC or X over the internet, is that it's so slow that I'm always happy if I can fall back to the CLI. I only use GUI if I want to show to the remote user how to do something

---

### Post by MenZa on 2007-08-13
> **eentonig said:**
> If it is to manage a remote computer, I hardly ever need to fall back on a GUI. I learn the CLI commands I need to achieve something (basically, managing a remote PC will installing programs and configuring them. Both of which can easily be done on a CLI base.).

In the event that he does need a GUI, he can still (and I'll be more then happy to show how) forward vnc or even X over his ssh tunnel. But the at least it will be done safely. 

But my experience with VNC or X over the internet, is that it's so slow that I'm always happy if I can fall back to the CLI. I only use GUI if I want to show to the remote user how to do something

I agree 100% on this one, but I still felt I wanted to inform gigaferz that he wouldn't get a flashy interface by using SSH by default. :)

---

### Post by lintoon on 2007-08-13
I highly recommend installing FreeNX Server.  Follow these instructions.  

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

It is easy to set up and works a treat.  It's also very fast.  Almost as fast as sitting in front of the machine.  Don't forget to set up his router to forward the port 8888 to his PCs IP address.

---

### Post by bodhi.zazen on 2007-08-13
+1 ssh. You can forward X through ssh if you like.

I advise you learn how to secure a ssh server though.

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
	See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...

	[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

If you would like you might be interested in VNC.

There is a technique coined "reverse VNC" by the author. The advantage is it allows you to easily set up a vnc server without having to know too much about routers and ports.

[http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)


	And, last FreeNx is popular as well ...  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by gigaferz on 2007-08-13
hey guys!

Thank you all, now at least im not lost , Ill head on to learn more

 Actually , when I told this guy, listen, I could give a last try to fix windows,but it might end up being unusable, I have this ubuntu software..blah..blah,... and also you will never get viruses or any spyware or anything like that...he said, "go for it due, i just want a computer running for internet and music..."...

I heard he is all happy enjoying his surround system... by the way what media player comes close to windows media player?

Thanks again...

---

### Post by gigaferz on 2007-09-03
im trying to make freenx to work...

i do need a gui....

i  did all the steps on the server machine, and on my side i installed the seveas packages...

my friends computer name is  ben (ben-desktop)?
his username is bennythug  

  "sudo nxserver --adduser <username> 
sudo nxserver --passwd <username>
sudo nxserver --restart "

i did this too, with his own username & password....

  i ve been trying the wizard but it always says host not found

any ideas, am I missing a package??

---

### Post by bodhi.zazen on 2007-09-04
Well, I can not get freenx to work either :(

Try [uwiki]VNC[/uwiki]

The defaults work out of the box 

Server : System -> Preferances -> Remote desktop

Client :  Applications -> Internet -. Terminal Server Client

If you do not know how to forward ports, try the "Reverse VNC" method.

---

### Post by gigaferz on 2007-09-07
thanks,,,what happened with udsf???

---

### Post by bodhi.zazen on 2007-09-07
> **gigaferz said:**
> thanks,,,what happened with udsf???

We (UDSF) moved ...

[http://doc.gwos.org/newdoc/doku.php/wiki:syntax?do=index](http://doc.gwos.org/newdoc/doku.php/wiki:syntax?do=index)

Still under construction a little, changed wiki format & colors

---

